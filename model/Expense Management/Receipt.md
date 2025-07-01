# Expense Management: Receipt

The **Receipt** model extracts data from receipts.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.receipt.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.receipt.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.receipt.meta.status == "Processed"

    print(res.receipt.fields)
```

---

## Extracted Fields

| Field Group                | Field Name         | Description                                           |
|----------------------------|-------------------|-------------------------------------------------------|
| **Merchant Information**   | Name              | The merchant’s name.                                  |
|                            | Address           | The merchant’s address.                               |
|                            | Phone             | The merchant’s phone number.                          |
|                            | Tax ID            | The merchant’s tax identification number.             |
|                            | Store Number      | The store or branch number.                           |
| **Receipt Details**        | Number            | The receipt number.                                   |
|                            | Date              | The date of the transaction.                          |
|                            | Time              | The time of the transaction.                          |
|                            | Register Number   | The register or terminal number.                      |
|                            | Employee ID       | The ID of the employee who processed the transaction. |
| **Payment Information**    | Method            | The payment method used (cash, credit card, etc.).    |
|                            | Card Type         | The type of card used for payment (if applicable).    |
|                            | Card Last 4       | The last 4 digits of the card used (if applicable).   |
|                            | Authorization Number | The payment authorization number (if applicable). |
| **Amounts**                | Subtotal          | The subtotal amount before taxes and tips.            |
|                            | Tax               | The total tax amount.                                 |
|                            | Tip               | The tip amount (if applicable).                       |
|                            | Total             | The total amount including taxes and tips.            |
|                            | Currency          | The currency used in the transaction.                 |
| **Line Items** (repeating) | Description       | The description of the item.                          |
|                            | Quantity          | The quantity of items.                                |
|                            | Unit Price        | The price per unit.                                   |
|                            | Amount            | The total amount for the line item.                   |
|                            | Tax Amount        | The tax amount for the line item.                     |
|                            | Tax Rate          | The tax rate applied to the line item.                |
|                            | Discount          | Any discount applied to the line item.                |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
