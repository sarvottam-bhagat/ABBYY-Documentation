# Expense Management – Hotel Invoice

Extracts data from hotel invoices or bills, including details such as the date of stay, room rates, additional charges, and the total amount due.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, and process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.hotel_invoice.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.hotel_invoice.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.hotel_invoice.meta.status == "Processed"

    print(res.hotel_invoice.fields)
```

---

## Extracted Fields

| Field Group         | Field Name         | Description                                 |
|---------------------|-------------------|---------------------------------------------|
| **Hotel Information** | Name              | The name of the hotel                       |
|                     | Address           | The hotel’s address                         |
|                     | Phone             | The hotel’s phone number                    |
|                     | Email             | The hotel’s email address                   |
|                     | Tax ID            | The hotel’s tax identification number       |
| **Guest Information** | Name              | The guest’s name                            |
|                     | Address           | The guest’s address                         |
|                     | Phone             | The guest’s phone number                    |
|                     | Email             | The guest’s email address                   |
|                     | Loyalty Number    | The guest’s loyalty program number          |
| **Stay Information** | Check-in Date      | The check-in date                           |
|                     | Check-out Date    | The check-out date                          |
|                     | Number of Nights  | The total number of nights stayed           |
|                     | Room Number       | The room number                             |
|                     | Room Type         | The type of room                            |
|                     | Number of Guests  | The number of guests                        |
| **Charges**          | Room Rate          | The daily room rate                         |
|                     | Room Charges      | The total room charges                      |
|                     | Resort Fee        | Any resort fees charged                     |
|                     | Parking Fee       | Any parking fees charged                    |
|                     | Internet Fee      | Any internet service fees                   |
|                     | Mini Bar Charges  | Any mini bar consumption charges            |
|                     | Room Service Charges | Any room service charges                  |
|                     | Other Charges     | Any additional charges                      |
| **Taxes and Fees**   | Room Tax           | The tax on room charges                     |
|                     | Sales Tax         | Any sales tax applied                       |
|                     | City Tax          | Any city or local tax applied               |
|                     | Tourism Fee       | Any tourism or bed tax applied              |
| **Payment Information** | Subtotal         | The subtotal before taxes and fees          |
|                     | Total Tax         | The total of all taxes                      |
|                     | Total             | The total amount including all charges, taxes, and fees |
|                     | Payment Method    | The method of payment                       |
|                     | Card Type         | The type of card used (if paid by card)     |
|                     | Card Last 4       | The last 4 digits of the card (if paid by card) |
|                     | Folio Number      | The folio or invoice number                 |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
