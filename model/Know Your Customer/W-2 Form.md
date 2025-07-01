# Know Your Customer: W-2 Form

The **W-2 Form model** extracts data from IRS Form W-2 (Wage and Tax Statement).

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.us_form_w2.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.us_form_w2.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.us_form_w2.meta.status == "Processed"

    print(res.us_form_w2.fields)
```

---

## Extracted Fields

| Field Group                | Field Name                | Description                                                         |
|----------------------------|---------------------------|---------------------------------------------------------------------|
| **Employee Information**   | Name                      | The employee’s name.                                                |
|                            | SSN                       | The employee’s Social Security Number.                              |
|                            | Address                   | The employee’s address.                                             |
| **Employer Information**   | Name                      | The employer’s name.                                                |
|                            | EIN                       | The employer’s Identification Number.                               |
|                            | Address                   | The employer’s address.                                             |
| **Wages and Compensation** | Wages and Tips            | Wages, tips, and other compensation.                                |
|                            | Social Security Wages     | Social Security wages.                                              |
|                            | Medicare Wages            | Medicare wages and tips.                                            |
|                            | Social Security Tips      | Social Security tips.                                               |
|                            | Allocated Tips            | Allocated tips.                                                     |
| **Tax Withholding**        | Federal Income Tax        | Federal income tax withheld.                                        |
|                            | Social Security Tax       | Social Security tax withheld.                                       |
|                            | Medicare Tax              | Medicare tax withheld.                                              |
|                            | State Income Tax          | State income tax withheld.                                          |
|                            | Local Income Tax          | Local income tax withheld.                                          |
| **State and Local Info**   | State                     | The state code.                                                     |
|                            | State ID Number           | The state identification number.                                    |
|                            | State Wages               | State wages, tips, etc.                                             |
|                            | Local Wages               | Local wages, tips, etc.                                             |
|                            | Locality Name             | The name of the locality.                                           |
| **Other Information**      | Dependent Care Benefits   | Dependent care benefits.                                            |
|                            | Nonqualified Plans        | Nonqualified plans.                                                 |
|                            | Box 12 Items              | Items reported in Box 12 (code and amount).                         |
|                            | Box 13 Items              | Items checked in Box 13 (Statutory employee, Retirement plan, Third-party sick pay). |
|                            | Box 14 Items              | Other items reported in Box 14.                                     |
| **Control Information**    | Control Number            | The form control number.                                            |
|                            | Tax Year                  | The tax year for the W-2.                                           |

---

## Supported Languages

| Country        | Language |
|----------------|----------|
| United States  | English  |
