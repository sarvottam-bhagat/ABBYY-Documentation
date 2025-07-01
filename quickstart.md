# Install the SDK

While you can call the API directly, the Document AI API provides SDKs for several popular programming languages. If you don't have a project already, create one:

**Python**

```bash
# Create a virtual environment
python3 -m venv venv
# On macOS or Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate
# Create a file
touch docai.py
```

Next, install the Document AI API SDK:

**Python**

```bash
pip install abbyy-document-ai
```

## Call the API

Call the API using the documents/invoice endpoint. Provide the path to the invoice file to process (or use the one we've provided) and insert your API key into the Authorization header.

**Python**

```python
from document_ai_sdk import DocumentAi

API_KEY="your-api-key-here"
with DocumentAi(api_key_auth=API_KEY) as document_ai:
    res = document_ai.invoice.extract_invoice_data(input_source={
        "url": "https://raw.githubusercontent.com/dotNetkow/test-cods/6c25fa2e54fb96ecf534903aef0d3cbecd71e987/Invoice%20CA_1.pdf",
    })
    
    docId = res.documents[0].id
    print(res)
```

Run the code using `python3 docai.py`. The API will respond with a document id that we'll need in the next step.

```json
[
  {
    "id": "r23qpmmjsc7f93o3",
    "name": "Invoice%20CA_1.pdf",
    "createdAt": "2025-04-01 20:41:26.510152",
    "status": "Pending",
    "pageCount": 1
  }
]
```

## Retrieve the Results

The Document AI API begins processing the invoice immediately on submission. To retrieve the results, we make one more API call to `/documents/invoice/[document-id]`. Fill in the document-id using the id from the previous API call. The API's processing time varies based on a variety of factors including number of document pages, so we'll keep attempting to retrieve the extracted fields every few seconds until the API's status returns Processed.

**Python**

```python
# import time module at the top of the file for waiting between field checks
import time

processed = False
while not processed:
    time.sleep(3)  # Wait 3 seconds between checks
    res = document_ai.models.invoice.get_extracted_fields(
        document_id=doc_id
    )
    processed = res.invoice.meta.status == "Processed"

print("Invoice number: ", res.invoice.fields.invoice_number)
```

Success! We now have all the fields from the invoice document:

**Invoice fields**

```json
{
  "meta": {
    "id": "r23qpmmjsc7f93o3",
    "name": "Invoice%20CA_1.pdf",
    "createdAt": "2025-04-01 20:41:26.510152",
    "status": "Processed",
    "pageCount": 1
  },
  "fields": {
    "invoiceNumber": "9435435",
    "invoiceDate": "2021-11-11",
    "total": 4620,
    "currency": "CAD",
    "businessUnit": {
      "name": "M GROUP INC.",
      "address": "770-21ST AVENUE N\nSASKATOON SK S1K7R1\nCANADA",
      "country": "CA"
    },
    "vendor": {
      "name": "ANADAYA CANADA",
      "address": "262 Merrier Avenue, Toronto, Ontario Т1Т 3R29"
    },
    "reversedCharged": false,
    "invoiceType": {
      "invoice": true,
      "creditNote": false
    },
    "purchaseOrder": [
      {
        "orderChecked": false
      }
    ],
    "lineItems": [
      {
        "isValid": false,
        "position": 1,
        "articleNumberVendor": "864UW7",
        "description": "RECEIVER (19003)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      },
      {
        "isValid": false,
        "position": 2,
        "articleNumberVendor": "864UW7",
        "description": "RECEIVER (85813)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      },
      {
        "isValid": false,
        "position": 3,
        "articleNumberVendor": "384 UW5",
        "description": "RECEIVER (19053)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      },
      {
        "isValid": false,
        "position": 4,
        "articleNumberVendor": "365UW8",
        "description": "RECEIVER (85583)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      },
      {
        "isValid": false,
        "position": 5,
        "articleNumberVendor": "354UW7",
        "description": "RECEIVER (15003)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      },
      {
        "isValid": false,
        "position": 6,
        "articleNumberVendor": "564UW7",
        "description": "RECEIVER (85513)",
        "quantity": 2,
        "unitPrice": 385,
        "netPrice": 770,
        "currency": "CAD"
      }
    ]
  }
}
```

## Complete Code

Here's the complete code for reference.

**Python**

```python
import time
from document_ai_sdk import DocumentAi

API_KEY="your-api-key-here"
with DocumentAi(api_key_auth=API_KEY) as document_ai:
    res = document_ai.invoice.extract_invoice_data(input_source={
        "url": "https://raw.githubusercontent.com/dotNetkow/test-cods/6c25fa2e54fb96ecf534903aef0d3cbecd71e987/Invoice%20CA_1.pdf",
    })
    
    docId = res.documents[0].id
    print(res)
    
    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.invoice.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.invoice.meta.status == "Processed"
    
    print("Invoice number: ", res.invoice.fields.invoice_number)
```
