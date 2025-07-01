# Customs Clearance

## Air Waybill

The Air Waybill model extracts data from air waybills, which are documents issued by air carriers listing the goods being shipped along with details of the sender, recipient, and carrier.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.air_waybill.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.air_waybill.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.air_waybill.meta.status == "Processed"

    print(res.air_waybill.fields)
```

## Arrival Notice

The Arrival Notice model extracts key data from arrival notices in English. An arrival notice is a document sent to a consignee by a carrier, informing them about the shipment's arrival date at a specific location.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.arrival_notice.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.arrival_notice.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.arrival_notice.meta.status == "Processed"

    print(res.arrival_notice.fields)
```

## Bill of Lading

A bill of lading is a legal document used in both national and international trade. Bills of lading are issued to the shipper by the carrier as confirmation that the goods have been received and are as described, with the carrier undertaking to deliver it to the consignee in appropriate condition. This document should accompany the shipped goods along their entire freight route, regardless of the transport used.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.bill_of_lading.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.bill_of_lading.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.bill_of_lading.meta.status == "Processed"

    print(res.bill_of_lading.fields)
```

## Certificate of Origin

The Certificate of Origin model is designed to extract data from certificates of origin, which are trade documents used for customs-related procedures.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.certificate_of_origin.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.certificate_of_origin.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.certificate_of_origin.meta.status == "Processed"

    print(res.certificate_of_origin.fields)
```

## Commercial Invoice

Extracts data from commercial invoices, a customs declaration document that contains information about the parties involved in the transaction, the goods being transported (including their value), and the terms of delivery.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.commercial_invoice.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.commercial_invoice.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.commercial_invoice.meta.status == "Processed"

    print(res.commercial_invoice.fields)
```

## Customs Declaration (EU)

Extracts data from customs declarations for goods transported across the borders of EU countries. A customs declaration is a document that contains information about the consignor, the consignee, the declarants, as well as the goods being transported and their means of transport. This model can be used to process customs declarations for goods both entering and leaving EU countries.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.customs_declaration.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.customs_declaration.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.customs_declaration.meta.status == "Processed"

    print(res.customs_declaration.fields)
```

## Dangerous Goods Declaration

Extracts data from Dangerous Goods Declarations (DGD's), which are transport documents compiled by the shipper of dangerous goods. Dangerous Goods Declarations serve to confirm that the goods in question have been packed, marked, and declared in accordance with IATA (International Air Transport Association) Dangerous Goods Regulations.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.dangerous_goods_declaration.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.dangerous_goods_declaration.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.dangerous_goods_declaration.meta.status == "Processed"

    print(res.dangerous_goods_declaration.fields)
```

## Delivery Note

A delivery note is a transport document that accompanies transported goods. This document contains information about the transported goods, as well as about the vendor and the buyer. Information specified in delivery notes may be required for electronic transportation records and other customs-related transport documents such as bills of lading.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.delivery_note.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.delivery_note.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.delivery_note.meta.status == "Processed"

    print(res.delivery_note.fields)
```

## International Consignment Note (CMR)

Extracts data from international consignment notes, documents put together and filled out by the shipper, consignee, and carrier for internationally sent goods. It contains a list of items being transported, their characteristics, shipping details, and information about the shipper and consignee.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.international_consignment_note.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.international_consignment_note.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.international_consignment_note.meta.status == "Processed"

    print(res.international_consignment_note.fields)
```

## Packing List

The Packing List model extracts data from packing lists.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.packing_list.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.packing_list.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.packing_list.meta.status == "Processed"

    print(res.packing_list.fields)
```

## Sea Waybill

The Sea Waybill model extracts data from sea waybills.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.sea_waybill.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.sea_waybill.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.sea_waybill.meta.status == "Processed"

    print(res.sea_waybill.fields)
```
