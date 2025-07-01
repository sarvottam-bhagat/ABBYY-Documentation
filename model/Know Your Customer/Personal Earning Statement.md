# Know Your Customer  
## Personal Earnings Statement

The **Personal Earnings Statement** model extracts data from personal earnings statements.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.personal_earnings_statement.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.personal_earnings_statement.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.personal_earnings_statement.meta.status == "Processed"

    print(res.personal_earnings_statement.fields)
```

---

## Extracted Fields

| Field Group               | Field Name         | Description                                      |
|---------------------------|-------------------|--------------------------------------------------|
| **Employee Information**  | Name              | The employee’s name.                             |
|                           | ID                | The employee’s identification number.            |
|                           | Department        | The employee’s department.                       |
|                           | Position          | The employee’s job title or position.            |
| **Pay Period Information**| Start Date        | The start date of the pay period.                |
|                           | End Date          | The end date of the pay period.                  |
|                           | Pay Date          | The date when the payment was or will be made.   |
| **Earnings**              | Regular Hours     | The number of regular hours worked.              |
|                           | Regular Rate      | The hourly rate for regular hours.               |
|                           | Regular Pay       | The total pay for regular hours.                 |
|                           | Overtime Hours    | The number of overtime hours worked.             |
|                           | Overtime Rate     | The hourly rate for overtime hours.              |
|                           | Overtime Pay      | The total pay for overtime hours.                |
|                           | Bonus             | Any bonus payments.                              |
|                           | Commission        | Any commission payments.                         |
|                           | Gross Pay         | The total gross pay before deductions.           |
| **Deductions**            | Federal Tax       | Federal income tax withheld.                     |
|                           | State Tax         | State income tax withheld.                       |
|                           | Local Tax         | Local tax withheld.                              |
|                           | Social Security   | Social Security tax withheld.                    |
|                           | Medicare          | Medicare tax withheld.                           |
|                           | Health Insurance  | Health insurance premium deductions.             |
|                           | Dental Insurance  | Dental insurance premium deductions.             |
|                           | Vision Insurance  | Vision insurance premium deductions.             |
|                           | Life Insurance    | Life insurance premium deductions.               |
|                           | 401k              | 401(k) retirement plan contributions.            |
|                           | Total Deductions  | The total amount of all deductions.              |
| **Net Pay**               |                   | The final take-home pay after all deductions.    |
| **Year-to-Date Totals**   | Gross Pay         | Year-to-date gross pay.                          |
|                           | Federal Tax       | Year-to-date federal tax withheld.               |
|                           | State Tax         | Year-to-date state tax withheld.                 |
|                           | Social Security   | Year-to-date Social Security tax withheld.       |
|                           | Medicare          | Year-to-date Medicare tax withheld.              |
|                           | Net Pay           | Year-to-date net pay.                            |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |
