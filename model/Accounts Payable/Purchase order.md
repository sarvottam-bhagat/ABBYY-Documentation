# Accounts Payable - Purchase Order

The Purchase Order model extracts data from US, French, German, and Spanish purchase orders.

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.purchase_order.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.purchase_order.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.purchase_order.meta.status == "Processed"

    print(res.purchase_order.fields)
```

## Extracted Fields

| Field Name | Description |
|------------|-------------|
| **Order Number** | The number of the purchase order. |
| **Order Date** | The date when the purchase order was created. |
| **Buyer** | Information about the buyer. |
| ↳ Name | The name of the buyer. |
| ↳ Address | The address of the buyer. |
| ↳ Country | The country of the buyer. |
| ↳ Tax ID | The tax identification number of the buyer. |
| ↳ Buyer ID | The buyer ID. |
| ↳ Bank Code | The bank code of the buyer. |
| ↳ Bank Account | The bank account number of the buyer. |
| ↳ Street | The street part of the buyer's address. |
| ↳ ZIP Code | The ZIP code part of the buyer's address. |
| ↳ City | The city part of the buyer's address. |
| ↳ State | The state part of the buyer's address. |
| **Supplier** | Information about the supplier. |
| ↳ Name | The name of the supplier. |
| ↳ Address | The address of the supplier. |
| ↳ Country | The country of the supplier. |
| ↳ Tax ID | The tax identification number of the supplier. |
| ↳ Supplier ID | The supplier ID. |
| ↳ Street | The street part of the supplier's address. |
| ↳ ZIP Code | The ZIP code part of the supplier's address. |
| ↳ City | The city part of the supplier's address. |
| ↳ State | The state part of the supplier's address. |
| **Ship to** | Information about the delivery address. |
| ↳ Name | The name of the delivery recipient. |
| ↳ Address | The delivery address. |
| **Bill to** | Information about the billing address. |
| ↳ Name | The name of the billing recipient. |
| ↳ Address | The billing address. |
| **Line Items** | Information about the ordered items. |
| ↳ Position | The position number of the line item. |
| ↳ Description | The description of the ordered item. |
| ↳ Quantity | The quantity of items ordered. |
| ↳ Unit | The unit of measurement for the quantity. |
| ↳ Price | The price per unit. |
| ↳ Discount | The discount applied to the line item. |
| ↳ Total Price | The total price of the line item. |
| ↳ Currency | The currency used for the line item. |
| **Taxes** | Information about taxes. |
| ↳ Total Tax Amount | The total amount of tax. |
| ↳ Total Net Amount | The total amount before tax. |
| **Currency** | The currency used for the purchase order. |
| **Total** | The total amount of the purchase order. |
| **Delivery Date** | The date when the goods should be delivered. |

## Validation Rules

| Rule | Description |
|------|-------------|
| **Total: Amount check** | Checks that: Line Items/Total Price equals Total, Line Items/Total Price + Taxes/Total Tax Amount equals Total, Line Items/Total Price equals Taxes/Total Net Amount. If none of the conditions are fulfilled, returns an error and suggests corrected values. If the Taxes/Total Tax Amount and Taxes/Total Net Amount fields are empty, and the Total field is not empty, fills the Taxes/Total Net Amount field with the value of the Total field. Suggests calculated values for Taxes/Total, Taxes/Total Tax Amount, or Taxes/Total Net Amount, if any of these fields is not detected. |
| **Check item amount** | Multiplies the number of units ordered in the line item by the price of one unit, applies the discount, and suggests a value if the result is not equal to the total price of the line item. |
| **Quantity is required** | Checks that the quantity of goods has been detected on the document. |
| **Delivery date must be later than order date** | Checks that the delivery date is later than the date of the purchase order. |
| **Copy PO and Line Items currency** | If the Currency field is empty, fills it in using the value of the Line Items/Currency field. This rule also applies to the Line Items/Currency field, which is filled in using the value of the Currency field. Only the values that correspond to the ISO format are copied. If the currency is marked using the "$" sign, the value is still copied, but is then formatted to be the standard "USD" value. If the Currency fields are empty, checks the value of the Supplier/Country field. If the country of the supplier is the US, fills the Currency field with the value "USD". |
| **Separate currency from amount in Line Items money field** | Splits the amount and the currency in the amount fields and copies the currency into the Currency field if it is empty. |
| **Separate currency from amount in Total field** | Splits the amount and the currency in the amount fields and copies the currency into the Currency field if it is empty. |
| **Check currency value** | Checks that the value of the Currency field in the order corresponds to a currency format. Adds a list of suggested values if the field is empty or if its value does not correspond to any currency code. |
| **Check Line Items currency value** | Checks that the value of the Currency field in Line Items corresponds to a currency format. Adds a list of suggested values if the field is empty or if its value does not correspond to any currency code. |
| **Set Default Country** | If the Country fields in the Supplier and Buyer groups are not filled in, fills them in using the default value (US). |
| **Supplier DB lookup** | Checks information about the supplier against the corresponding data catalog. If the data catalog contains information about that supplier, but the values are either different or incomplete, fills in the appropriate fields using data from the data catalog. If the supplier was not detected correctly, the operator may select a different supplier from the data catalog manually during manual review. The Supplier ID, Name, Street and Country fields should be filled in in the Suppliers data catalog. |
| **Buyer DB lookup** | Checks information about the buyer against the corresponding data catalog. If the data catalog contains information about that buyer, but the values are either different or incomplete, fills in the appropriate fields using data from the data catalog. If the buyer was not detected correctly, the operator may select a different buyer from the data catalog manually during manual review. The Buyer ID, Name, Street, Country, and Company Correlation ID (Supplier ID) fields should be filled in in the Buyers data catalog. |

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| USA, France, Germany, Spain | English, French, German, Spanish |
