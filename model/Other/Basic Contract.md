# Basic Contract

## Overview
Extracts data from contract documents of different types: lease agreements, loan applications, loan agreements, service agreements, supply contracts, etc.

## Usage
Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

### Code Examples

**Python**
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

## Extracted Fields

### Contract Information
Basic information about the contract.

| Field | Description |
|-------|-------------|
| Title | The title or name of the contract |
| Number | The contract number or reference number |
| Date | The date when the contract was signed or executed |
| Start Date | The date when the contract becomes effective |
| End Date | The date when the contract expires or terminates |

### Party Information
Information about the parties involved in the contract.

| Field | Description |
|-------|-------------|
| First Party Name | The name of the first party to the contract |
| First Party Address | The address of the first party |
| First Party Tax ID | The tax identification number of the first party |
| Second Party Name | The name of the second party to the contract |
| Second Party Address | The address of the second party |
| Second Party Tax ID | The tax identification number of the second party |

### Financial Terms
Information about the financial aspects of the contract.

| Field | Description |
|-------|-------------|
| Contract Value | The total value of the contract |
| Currency | The currency used in the contract |
| Payment Terms | The terms and conditions for payment |
| Payment Schedule | The schedule or timeline for payments |

### Legal Information
Legal aspects of the contract.

| Field | Description |
|-------|-------------|
| Governing Law | The jurisdiction or law governing the contract |
| Dispute Resolution | The method for resolving disputes |
| Termination Clause | The conditions under which the contract can be terminated |

### Signatures
Information about the signatures on the contract.

| Field | Description |
|-------|-------------|
| First Party Signature | The signature of the first party |
| First Party Name | The printed name of the first party signatory |
| First Party Title | The title or position of the first party signatory |
| First Party Date | The date when the first party signed |
| Second Party Signature | The signature of the second party |
| Second Party Name | The printed name of the second party signatory |
| Second Party Title | The title or position of the second party signatory |
| Second Party Date | The date when the second party signed |

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global | English |