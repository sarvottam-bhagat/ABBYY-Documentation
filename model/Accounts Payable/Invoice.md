# Invoice

The Invoice model extracts data from invoices from approximately 30 countries, most of them European.

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.invoice.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.invoice.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.invoice.meta.status == "Processed"

    print(res.invoice.fields)
```

## Extracted Fields

| Field Name | Description |
|------------|-------------|
| **Invoice Number** | The number of the invoice. |
| **Invoice Date** | The date when the invoice was issued. |
| **Total** | The total cost of goods or services. |
| **Currency** | The currency of the invoice. |

### Vendor
Information about the vendor.

| Field Name | Description |
|------------|-------------|
| Name | The vendor's name. |
| Tax ID | The official company ID of the vendor. |
| Address | The vendor's address. The address will be extracted into this field, if no Vendors data catalog is used or if the vendor has not been found in a data catalog. |
| State | The vendor's state. |
| City | The vendor's city. |
| Street | The vendor's street address. |
| Postal Code | The vendor's postal code. |
| Country | The vendor's country. |
| ID | The vendor's unique identifier in the catalog used by the customer. This field can only be obtained from the Vendors data catalog. |
| Bank Account | The vendor's bank account. |
| Bank Code | The vendor's bank code. |
| SWIFT Code | The SWIFT code of the vendor. Spanish invoices only. |
| National Tax ID | The TAX payer registration number inside the origin country. Ukrainian invoices only. |
| IBAN | The vendor's international bank account number. Ukrainian invoices only. |

### Bank Information
Information about the vendor's bank account.

| Field Name | Description |
|------------|-------------|
| Account Number | The vendor's account number. |
| Account Type | The vendor's account type. |
| Bank Name | The name of the bank used by the vendor. |
| Branch Name | The name of the bank branch used by the vendor. |

### Date Fields

| Field Name | Description |
|------------|-------------|
| **Delivery Date** | The date the goods were delivered or services performed. |
| **Due Date** | The date by which the invoice should be paid. |

### Taxes
Information about taxes.

| Field Name | Description |
|------------|-------------|
| Total Net Amount | The total cost of goods and services without tax. |
| Total Taxes | The total tax amount. |
| Non Taxable Amount | The amount on which no tax is payable. |

#### Tax Rates (repeating group)
For each tax group:

| Field Name | Description |
|------------|-------------|
| Net Amount | Cost of goods or services without tax. |
| Tax Amount | Tax charged. |
| Tax Rate | Tax rate. |

### Invoice Type
Information about the type of invoice.

| Field Name | Description |
|------------|-------------|
| Invoice | Specifies the Invoice type of the invoice. |
| Credit Note | Specifies the Credit Note type of the invoice. |

### Purchase Order
Information about the purchase order.

| Field Name | Description |
|------------|-------------|
| Order Number | The number of the purchase order. |
| Order Checked | Specifies whether the order number is verified. The value of the field can be True or False. |
| Total | The cost of the goods or services listed in the purchase order. |

> **Note:** This field can only be obtained from the PurchaseOrders data catalog.

### Line Items (repeating group)
Information about individual line items.

| Field Name | Description |
|------------|-------------|
| Order Number | The number of the purchase order. |
| Is Valid | Specifies whether the order number in the Line Item group matches any checked order number in the Purchase Order group. The value of the field can be True or False. |
| Order Date | The date when the purchase order was created. |
| Position | The number of the line item in the list. |
| Article Number Vendor | The article number or code in the vendors's database. |
| Article Number BU | The article number or code in the business unit's database. |
| Description | A description of the line item. |
| Quantity | The number of units purchased. |
| Unit of Measurement | The unit of measurement used for the goods. |
| Unit Price | The price of one item of goods. |
| Discount Percentage | The discount percentage on the initial line item price. |
| Discount | Discount applicable to the line item. |
| Net Price | The price of the line item without tax. |
| Tax Rate | The tax rate for the line item. |
| Tax Amount | The amount of tax payable on the line item. |
| Tax Code | The code of the tax. |
| Total Price | The price of the line item including tax. |
| Currency | The currency of the line item. |
| Order Item ID | The unique line item identifier. |

> **Note:** This field can only be obtained from the PurchaseOrderItems data catalog.

### Business Unit (BU)
Information about the business unit (invoice recipient).

| Field Name | Description |
|------------|-------------|
| Name | The name of the business unit (invoice recipient). |
| Tax ID | The tax payer registration number. |
| Address | The address of the business unit (invoice recipient). The address will be extracted into this field, if no BusinessUnits data catalog is used or if the business unit has not been found in a data catalog. |
| Country | The country of the business unit (invoice recipient). |
| State or Province | The state or province of the business unit (invoice recipient). |
| City | The city of the business unit (invoice recipient). |
| Street | The street address of the business unit (invoice recipient). |
| Postal Code | The postal code of the business unit (invoice recipient). |
| ID | The unique identifier of the business unit in the catalog used by the customer. This field can only be obtained from the BusinessUnits data catalog. |

## Supported Languages

| Country | Language |
|---------|----------|
| Austria | German |
| Australia | English |
| Belgium | Dutch, French |
| Bulgaria | Bulgarian |
| Canada | English |
| China | English |
| Croatia | Croatian |
| Cyprus | English |
| Czech Republic | Czech |
| Denmark | Danish |
| Estonia | Estonian |
| Finland | Finnish |
| France | French |
| Germany | German |
| Hungary | Hungarian |
| India | English |
| Ireland | English |
| Italy | Italian |
| Japan | Japanese |
| Latvia | Latvian |
| Lithuania | Lithuanian |
| Moldova | English |
| Netherlands | Dutch |
| New Zealand | English |
| Norway | Norwegian (Bokmal) |
| Poland | Polish |
| Portugal | Portuguese |
| Romania | Romanian |
| Slovakia | Slovak |
| Slovenia | English |
| Spain | English |
| Sweden | Swedish |
| Switzerland | German |
| Turkey | Turkish |
| Ukraine | English |
| United Kingdom | English |
