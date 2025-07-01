# Accounts Payable: Remittance Advice

The **Remittance Advice** model extracts data from remittance advice documents.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.remittance_advice.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.remittance_advice.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.remittance_advice.meta.status == "Processed"

    print(res.remittance_advice.fields)
```

---

## Extracted Fields

| Field Group                | Field Name         | Description                                      |
|----------------------------|-------------------|--------------------------------------------------|
| **Payer Information**      | Name              | The name of the payer.                           |
|                            | Address           | The payer’s address.                             |
|                            | Tax ID            | The payer’s tax identification number.           |
|                            | Contact           | The payer’s contact information.                 |
| **Payee Information**      | Name              | The name of the payee.                           |
|                            | Address           | The payee’s address.                             |
|                            | Tax ID            | The payee’s tax identification number.           |
|                            | Account Number    | The payee’s account number.                      |
| **Payment Details**        | Remittance Number | The remittance advice number.                    |
|                            | Date              | The date of the remittance advice.               |
|                            | Payment Method    | The method of payment.                           |
|                            | Payment Date      | The date when the payment was or will be made.   |
|                            | Currency          | The currency of the payment.                     |
|                            | Total Amount      | The total amount being paid.                     |
| **Invoice Details**        | Invoice Number    | The invoice number.                              |
| (repeating group)          | Invoice Date      | The date of the invoice.                         |
|                            | Invoice Amount    | The original invoice amount.                     |
|                            | Payment Amount    | The amount being paid for this invoice.          |
|                            | Discount Taken    | Any discount taken on the invoice.               |
|                            | Adjustment Amount | Any adjustments applied to the invoice.          |
| **Bank Information**       | Bank Name         | The name of the bank.                            |
|                            | Account Number    | The bank account number.                         |
|                            | Routing Number    | The bank routing number.                         |
|                            | SWIFT Code        | The bank’s SWIFT/BIC code.                       |
|                            | IBAN              | The International Bank Account Number.           |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
