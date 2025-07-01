# Know Your Customer: Utility Bill

The Utility Bill model extracts data from utility bills.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.utility_bill.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.utility_bill.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.utility_bill.meta.status == "Processed"

    print(res.utility_bill.fields)
```

---

## Extracted Fields

| Field Group           | Field Name           | Description                                               |
|-----------------------|---------------------|-----------------------------------------------------------|
| **Service Provider**  | Name                | The name of the utility company.                          |
|                       | Address             | The address of the utility company.                       |
|                       | Phone               | The contact phone number of the utility company.          |
|                       | Website             | The website of the utility company.                       |
| **Customer Information** | Account Number    | The customer’s account number.                            |
|                       | Name                | The customer’s name.                                      |
|                       | Service Address     | The address where the utility service is provided.        |
|                       | Billing Address     | The address where the bill is sent.                       |
| **Billing Period**    | Start Date          | The start date of the billing period.                     |
|                       | End Date            | The end date of the billing period.                       |
|                       | Due Date            | The date by which payment is due.                         |
| **Usage Information** | Current Reading     | The current meter reading.                                |
|                       | Previous Reading    | The previous meter reading.                               |
|                       | Usage               | The total usage for the billing period.                   |
|                       | Unit of Measurement | The unit of measurement for usage (e.g., kWh, gallons).   |
| **Charges**           | Basic Service Charge| The basic service or connection fee.                      |
|                       | Usage Charge        | The charge for actual utility usage.                      |
|                       | Taxes               | The total taxes applied.                                  |
|                       | Other Charges       | Any additional charges or fees.                           |
|                       | Total Amount        | The total amount due.                                     |
| **Payment Information** | Previous Balance  | The balance from the previous bill.                       |
|                       | Payments Received   | Payments received since the last bill.                    |
|                       | Current Charges     | The current charges for this billing period.              |
|                       | Total Due           | The total amount due including any previous balance.      |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
