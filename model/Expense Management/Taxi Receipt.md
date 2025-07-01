# Expense Management: Taxi Receipt

The **Taxi Receipt** model extracts data from taxi and ride-sharing service receipts.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.taxi_receipt.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.taxi_receipt.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.taxi_receipt.meta.status == "Processed"

    print(res.taxi_receipt.fields)
```

---

## Extracted Fields

| Field Group         | Field Name         | Description                                         |
|---------------------|-------------------|-----------------------------------------------------|
| **Service Provider**| Company Name      | The name of the taxi company or ride-sharing service.|
|                     | Driver Name       | The name of the driver.                             |
|                     | Driver ID         | The driver’s identification number.                 |
|                     | Vehicle Number    | The taxi or vehicle identification number.          |
|                     | License Plate     | The vehicle’s license plate number.                 |
| **Trip Information**| Date              | The date of the trip.                               |
|                     | Time              | The time of the trip.                               |
|                     | Pickup Location   | The pickup location or starting point.              |
|                     | Dropoff Location  | The dropoff location or destination.                |
|                     | Distance          | The distance traveled.                              |
|                     | Duration          | The duration of the trip.                           |
| **Fare Details**    | Base Fare         | The base fare for the trip.                         |
|                     | Distance Charge   | The charge based on distance traveled.              |
|                     | Time Charge       | The charge based on time.                           |
|                     | Waiting Charge    | Any charges for waiting time.                       |
|                     | Toll Charges      | Any toll charges incurred.                          |
|                     | Airport Fee       | Any airport surcharges or fees.                     |
|                     | Other Charges     | Any additional charges.                             |
|                     | Subtotal          | The subtotal before taxes and tips.                 |
|                     | Tax               | The tax amount.                                     |
|                     | Tip               | The tip amount.                                     |
|                     | Total             | The total amount including all charges, taxes, and tip.|
| **Payment Information**| Receipt Number | The receipt or transaction number.                  |
|                     | Payment Method    | The method of payment (cash, credit card, etc.).    |
|                     | Card Type         | The type of card used (if paid by card).            |
|                     | Card Last 4       | The last 4 digits of the card (if paid by card).    |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
