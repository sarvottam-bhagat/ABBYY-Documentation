# Other
## Brokerage Statement

Extracts data from brokerage statements, documents that are provided by a brokerage firm detailing the transactions and holdings in a client's investment account. The statement typically includes information such as the value of the account, the individual investments held, any changes in the value of those investments, and any fees or charges associated with the account. Brokerage statements are typically provided on a regular basis, such as monthly or quarterly, and are an important tool for investors to track the performance and activity of their investments.

## Usage

Copy the code block, replace YOUR_API_KEY with your API key, then process documents quickly.

**Python**

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

## Extracted Fields

| Field Name | Description |
|------------|-------------|
| **Account Information** | Information about the brokerage account. |
| - Account Number | The brokerage account number. |
| - Account Type | The type of brokerage account (e.g., Individual, Joint, IRA). |
| - Account Name | The name on the account. |
| **Statement Period** | Information about the statement period. |
| - Start Date | The start date of the statement period. |
| - End Date | The end date of the statement period. |
| **Account Value** | Information about account values. |
| - Opening Balance | The account value at the start of the period. |
| - Closing Balance | The account value at the end of the period. |
| - Net Change | The change in account value during the period. |
| **Income Summary** | Information about income earned. |
| - Dividends | Total dividends earned during the period. |
| - Interest | Total interest earned during the period. |
| - Capital Gains | Total capital gains realized during the period. |
| **Transactions** (repeating group) | Information about individual transactions. |
| - Date | The date of the transaction. |
| - Type | The type of transaction (buy, sell, dividend, etc.). |
| - Description | Description of the transaction. |
| - Symbol | The security symbol. |
| - Quantity | The number of shares or units. |
| - Price | The price per share or unit. |
| - Amount | The total amount of the transaction. |
| **Holdings** (repeating group) | Information about securities held in the account. |
| - Symbol | The security symbol. |
| - Description | Description of the security. |
| - Quantity | The number of shares or units held. |
| - Price | The price per share or unit at period end. |
| - Market Value | The total market value of the holding. |
| - Cost Basis | The total cost basis of the holding. |
| - Unrealized Gain/Loss | The unrealized gain or loss on the holding. |

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global | English |
