# Know Your Customer: Bank Statement

Extracts data from bank statements—documents banks send to account holders at the end of a reporting period (usually monthly). A bank statement contains information about the account, its holder, transactions, and balances.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, and process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.bank_statement.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.bank_statement.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.bank_statement.meta.status == "Processed"

    print(res.bank_statement.fields)
```

---

## Extracted Fields

| Field Group         | Field Name         | Description                                         |
|---------------------|-------------------|-----------------------------------------------------|
| **Bank Information**| Name              | The name of the bank                                |
|                     | Address           | The bank’s address                                  |
|                     | State             | The bank’s state                                    |
|                     | City              | The bank’s city                                     |
|                     | Street            | The bank’s street address                           |
|                     | Postal Code       | The bank’s postal code                              |
|                     | Country           | The bank’s country                                  |
| **Account Information** | Account Number | The account number                                  |
|                     | Account Type      | The type of account (e.g., checking, savings)       |
|                     | Account Name      | The name on the account                             |
|                     | Currency          | The currency of the account                         |
| **Statement Information** | Statement Date | The date of the statement                        |
|                     | Statement Period Start | The start date of the statement period         |
|                     | Statement Period End   | The end date of the statement period           |
| **Balance Information** | Opening Balance | Balance at the start of the statement period        |
|                     | Closing Balance   | Balance at the end of the statement period          |
|                     | Total Credits     | Total credits during the statement period           |
|                     | Total Debits      | Total debits during the statement period            |
| **Transactions** (repeating group) | Transaction Date | Date of the transaction                    |
|                     | Value Date        | Date when the transaction was processed             |
|                     | Description       | Description of the transaction                      |
|                     | Reference Number  | Reference number for the transaction                |
|                     | Amount            | Amount of the transaction                           |
|                     | Type              | Type of transaction (e.g., credit, debit)           |
|                     | Balance           | Account balance after the transaction               |
|                     | Category          | Category of the transaction (e.g., utilities)       |
|                     | Notes             | Additional notes or details                         |

---

## Validation Rules

| Rule                   | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Required Fields Check  | Validates that these fields are not empty: Account Owner Name, Account Owner Address, Ending Balance of the Period, Ending Balance Date. |

---

## Supported Languages

| Country | Language |
|---------|----------|
| USA     | English  |