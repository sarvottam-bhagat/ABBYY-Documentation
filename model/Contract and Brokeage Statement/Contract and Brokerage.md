# Contract and Brokerage Statement

## Basic Contract

Extracts data from contract documents of different types: lease agreements, loan applications, loan agreements, service agreements, supply contracts, etc.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

**Languages:** Python | TypeScript | C# | Java | API

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.basic_contract.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.basic_contract.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.basic_contract.meta.status == "Processed"

    print(res.basic_contract.fields)
```

## Brokerage Statement

Extracts data from brokerage statements, documents that are provided by a brokerage firm detailing the transactions and holdings in a client's investment account. The statement typically includes information such as the value of the account, the individual investments held, any changes in the value of those investments, and any fees or charges associated with the account. Brokerage statements are typically provided on a regular basis, such as monthly or quarterly, and are an important tool for investors to track the performance and activity of their investments.

### Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

**Languages:** Python | TypeScript | C# | Java | API

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.brokerage_statement.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
            time.sleep(3)  # Wait 3 seconds between checks
            res = document_ai.models.brokerage_statement.get_extracted_fields(
                    document_id=doc_id
            )
            processed = res.brokerage_statement.meta.status == "Processed"

    print(res.brokerage_statement.fields)
```
