# ABBYY Document AI API Documentation

## Document Management

### List Documents

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.documents.list(cursor="xyz")

    while res is not None:
        # Handle items
        res = res.next()
```

### Delete Document

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.documents.delete(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res is not None

    # Handle response
    print(res)
```

## Document Conversion

### Begin Document Conversion

```python
import abbyy_document_ai
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.document_conversion.begin_conversion(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
        "options": {
            "format_": abbyy_document_ai.DocumentConversionOutputFormat.PDF,
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Conversion

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.document_conversion.get_conversion(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.conversion_results is not None

    # Handle response
    print(res.conversion_results)
```

### Download Converted Document

```python
import abbyy_document_ai
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.document_conversion.download_converted_document(document_id="wh23anb5xjf0ntw5taase5qz", format_=abbyy_document_ai.PathParamDocumentConversionOutputFormat.HTML)

    assert res.response_stream is not None

    # Handle response
    print(res.response_stream)
```

## Image to Text Extraction

### Begin Image To Text Extraction

```python
import abbyy_document_ai
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.image_to_text.begin_text_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
        "options": {
            "languages": abbyy_document_ai.BeginImageToTextTextExtractionRequestBodyLanguages.EN,
            "handwriting": True,
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Extracted Text

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.image_to_text.get_extracted_text(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.extracted_text is not None

    # Handle response
    print(res.extracted_text)
```

## Receipt Processing

### Begin Receipt Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.receipt.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Receipt Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.receipt.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.receipt is not None

    # Handle response
    print(res.receipt)
```

## Invoice Processing

### Begin Invoice Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.invoice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Invoice Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.invoice.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.invoice is not None

    # Handle response
    print(res.invoice)
```

## Purchase Order Processing

### Begin Purchase Order Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.purchase_order.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Purchase Order Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.purchase_order.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.purchase_order is not None

    # Handle response
    print(res.purchase_order)
```

## Remittance Advice Processing

### Begin Remittance Advice Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.remittance_advice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Remittance Advice Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.remittance_advice.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.remittance_advice is not None

    # Handle response
    print(res.remittance_advice)
```

## Delivery Note Processing

### Begin Delivery Note Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.delivery_note.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/delivery_note.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Delivery Note Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.delivery_note.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.delivery_note is not None

    # Handle response
    print(res.delivery_note)
```

## Hotel Invoice Processing

### Begin Hotel Invoice Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.hotel_invoice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/hotel_invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Hotel Invoice Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.hotel_invoice.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.hotel_invoice is not None

    # Handle response
    print(res.hotel_invoice)
```

## Taxi Receipt Processing

### Begin Taxi Receipt Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.taxi_receipt.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/taxi_receipt.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Taxi Receipt Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.taxi_receipt.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.taxi_receipt is not None

    # Handle response
    print(res.taxi_receipt)
```

## Utility Bill Processing

### Begin Utility Bill Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.utility_bill.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/utility_bill.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Utility Bill Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.utility_bill.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.utility_bill is not None

    # Handle response
    print(res.utility_bill)
```

## US Form 1040 Processing

### Begin US Form 1040 Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.us_form_1040.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/form_1040.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get US Form 1040 Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.us_form_1040.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.us_form_1040 is not None

    # Handle response
    print(res.us_form_1040)
```

## US Form W2 Processing

### Begin US Form W2 Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.us_form_w2.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/form_w2.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get US Form W2 Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.us_form_w2.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.us_form_w2 is not None

    # Handle response
    print(res.us_form_w2)
```

## Personal Earnings Statement Processing

### Begin Personal Earnings Statement Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.personal_earnings_statement.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/earnings_statement.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Personal Earnings Statement Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.personal_earnings_statement.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.personal_earnings_statement is not None

    # Handle response
    print(res.personal_earnings_statement)
```

## Bank Statement Processing

### Begin Bank Statement Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.bank_statement.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/bank_statement.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Bank Statement Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.bank_statement.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.bank_statement is not None

    # Handle response
    print(res.bank_statement)
```

## Air Waybill Processing

### Begin Air Waybill Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.air_waybill.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/air_waybill.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Air Waybill Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.air_waybill.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.air_waybill is not None

    # Handle response
    print(res.air_waybill)
```

## Arrival Notice Processing

### Begin Arrival Notice Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.arrival_notice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/arrival_notice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Arrival Notice Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.arrival_notice.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.arrival_notice is not None

    # Handle response
    print(res.arrival_notice)
```

## Bill Of Lading Processing

### Begin Bill Of Lading Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.bill_of_lading.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/bill_of_lading.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Bill Of Lading Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.bill_of_lading.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.bill_of_lading is not None

    # Handle response
    print(res.bill_of_lading)
```

## Certificate Of Origin Processing

### Begin Certificate Of Origin Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.certificate_of_origin.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/certificate_of_origin.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Certificate Of Origin Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.certificate_of_origin.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.certificate_of_origin is not None

    # Handle response
    print(res.certificate_of_origin)
```

## Commercial Invoice Processing

### Begin Commercial Invoice Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.commercial_invoice.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/commercial_invoice.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Commercial Invoice Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.commercial_invoice.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.commercial_invoice is not None

    # Handle response
    print(res.commercial_invoice)
```

## Dangerous Goods Declaration Processing

### Begin Dangerous Goods Declaration Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.dangerous_goods_declaration.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/dangerous_goods_declaration.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Dangerous Goods Declaration Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.dangerous_goods_declaration.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.dangerous_goods_declaration is not None

    # Handle response
    print(res.dangerous_goods_declaration)
```

## Customs Declaration Processing

### Begin Customs Declaration Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.customs_declaration.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/customs_declaration.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Customs Declaration Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.customs_declaration.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.customs_declaration is not None

    # Handle response
    print(res.customs_declaration)
```

## Packing List Processing

### Begin Packing List Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.packing_list.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/packing_list.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Packing List Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.packing_list.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.packing_list is not None

    # Handle response
    print(res.packing_list)
```

## Sea Waybill Processing

### Begin Sea Waybill Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.sea_waybill.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/sea_waybill.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Sea Waybill Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.sea_waybill.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.sea_waybill is not None

    # Handle response
    print(res.sea_waybill)
```

## International Consignment Note Processing

### Begin International Consignment Note Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.international_consignment_note.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/international_consignment_note.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get International Consignment Note Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.international_consignment_note.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.international_consignment_note is not None

    # Handle response
    print(res.international_consignment_note)
```

## Basic Contract Processing

### Begin Basic Contract Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.basic_contract.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/basic_contract.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Basic Contract Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.basic_contract.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.basic_contract is not None

    # Handle response
    print(res.basic_contract)
```

## Brokerage Statement Processing

### Begin Brokerage Statement Field Extraction

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.brokerage_statement.begin_field_extraction(request={
        "input_source": {
            "url": "https://example.com/documents/brokerage_statement.png",
        },
    })

    assert res.documents is not None

    # Handle response
    print(res.documents)
```

### Get Brokerage Statement Fields

```python
from abbyy_document_ai import DocumentAi
import os

with DocumentAi(
    api_key_auth=os.getenv("DOCUMENTAI_API_KEY_AUTH", ""),
) as document_ai:

    res = document_ai.models.brokerage_statement.get_extracted_fields(document_id="wh23anb5xjf0ntw5taase5qz")

    assert res.brokerage_statement is not None

    # Handle response
    print(res.brokerage_statement)
```
