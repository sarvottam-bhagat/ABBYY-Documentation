# Know Your Customer  
## Form 1040, U.S. Individual Income Tax Return, 2022

The Form 1040 model extracts data from U.S. Individual Income Tax Returns for tax year 2022.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi

with DocumentAi(api_key_auth=YOUR_API_KEY) as document_ai:
    res = document_ai.models.us_form1040.begin_field_extraction(input_source={
        "url": "https://example.com/document.pdf",
    })

    assert res.documents is not None
    doc_id = res.documents[0].id

    processed = False
    while not processed:
        time.sleep(3)  # Wait 3 seconds between checks
        res = document_ai.models.us_form1040.get_extracted_fields(
            document_id=doc_id
        )
        processed = res.us_form1040.meta.status == "Processed"

    print(res.us_form1040.fields)
```

---

## Extracted Fields

| Field Name | Description |
|------------|-------------|
| **Filing Information** | Information about the tax return filing. |
| &nbsp;&nbsp;Tax Year | The tax year for which the return is being filed. |
| &nbsp;&nbsp;Filing Status | The filing status selected on the return. |
| **Form** | Specifies whether the form is 1040 or 1040-SR. |
| **Name of MFS Spouse or HOH or QW Child** | The name of the taxpayer’s spouse or child. |
| **First Name** | The taxpayer’s first name. |
| **Last Name** | The taxpayer’s last name. |
| **SSN** | The taxpayer’s social security number. |
| **Spouse** | Information about the taxpayer’s spouse (if filing jointly). |
| &nbsp;&nbsp;First Name | The spouse’s first name. |
| &nbsp;&nbsp;Last Name | The spouse’s last name. |
| &nbsp;&nbsp;SSN | The spouse’s social security number. |
| **Address** | The taxpayer’s address information. |
| &nbsp;&nbsp;Home Address | The street address. |
| &nbsp;&nbsp;Apartment Number | The apartment or unit number. |
| &nbsp;&nbsp;City Town or Post Office | The city, town, or post office. |
| &nbsp;&nbsp;State | The state or province. |
| &nbsp;&nbsp;ZIP Code | The ZIP or postal code. |
| &nbsp;&nbsp;Foreign Country Name | The foreign country name (if applicable). |
| &nbsp;&nbsp;Foreign Province or State | The foreign province or state (if applicable). |
| &nbsp;&nbsp;Foreign Postal Code | The foreign postal code (if applicable). |
| **Presidential Election Campaign** | Indicates whether payments have been made to a Presidential election campaign fund. |
| &nbsp;&nbsp;You | The taxpayer’s election campaign contribution. |
| &nbsp;&nbsp;Spouse | The spouse’s election campaign contribution (if filing jointly). |
| **Digital Assets** | Indicates whether there was any income related to virtual currencies. |
| **Standard Deduction** | Information about the taxpayer’s standard deduction eligibility. |
| &nbsp;&nbsp;Someone Can Claim | Indicates whether the taxpayer and/or their spouse can be claimed as dependents. |
| &nbsp;&nbsp;&nbsp;&nbsp;You as a Dependent | Whether the taxpayer can be claimed as a dependent. |
| &nbsp;&nbsp;&nbsp;&nbsp;Your Spouse as a Dependent | Whether the spouse can be claimed as a dependent. |
| &nbsp;&nbsp;Separate Return or Dual-Status Alien | Whether filing separate returns or is a dual-status alien. |
| &nbsp;&nbsp;Age or Blindness | Age and blindness information for the taxpayer and spouse. |
| &nbsp;&nbsp;&nbsp;&nbsp;You | Taxpayer’s age and blindness status. |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;65 or Over | Whether taxpayer is 65 or older as of January 2 of current year. |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Blind | Whether taxpayer is blind. |
| &nbsp;&nbsp;&nbsp;&nbsp;Spouse | Spouse’s age and blindness status. |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;65 or Over | Whether spouse is 65 or older as of January 2 of current year. |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Blind | Whether spouse is blind. |
| **More than Four Dependents** | Indicates whether the taxpayer has more than four dependents. |
| **Dependents (repeating group)** | Information about the taxpayer’s dependents. |
| &nbsp;&nbsp;Full Name | The dependent’s full name. |
| &nbsp;&nbsp;SSN | The dependent’s social security number. |
| &nbsp;&nbsp;Relationship | The dependent’s relationship to the taxpayer. |
| &nbsp;&nbsp;Child Tax Credit | Indicates if the dependent qualifies for the Child Tax Credit. |
| &nbsp;&nbsp;Credit for Other Dependents | Indicates if the dependent qualifies for Credit for Other Dependents. |
| **Box 1 Group** | Information about wages, salaries, and tips. |
| &nbsp;&nbsp;Box 1a | Total Amount from Form W-2 Box 1. |
| &nbsp;&nbsp;Box 1b | Household Employee Wages. |
| &nbsp;&nbsp;Box 1c | Tip Income. |
| &nbsp;&nbsp;Box 1d | Medicaid Waiver Payments. |
| &nbsp;&nbsp;Box 1e | Taxable Dependent Care Benefits from Form 2441. |
| &nbsp;&nbsp;Box 1f | Employer-Provided Adoption Benefits from Form 8839. |
| &nbsp;&nbsp;Box 1g | Wages from Form 8919. |
| &nbsp;&nbsp;Box 1h | Other Earned Income. |
| &nbsp;&nbsp;Box 1i | Nontaxable Combat Pay Election. |
| &nbsp;&nbsp;Box 1z | Group Total. |
| **Box 2 Group** | Interest income information. |
| &nbsp;&nbsp;Box 2a | Tax-Exempt Interest. |
| &nbsp;&nbsp;Box 2b | Taxable Interest. |
| **Box 3 Group** | Dividend income information. |
| &nbsp;&nbsp;Box 3a | Qualified Dividends. |
| &nbsp;&nbsp;Box 3b | Ordinary Dividends. |
| **Box 4 Group** | IRA distribution information. |
| &nbsp;&nbsp;Box 4a | IRA Distributions. |
| &nbsp;&nbsp;Box 4b | Taxable Amount. |
| **Box 5 Group** | Pension and annuity information. |
| &nbsp;&nbsp;Box 5a | Pensions and Annuities. |
| &nbsp;&nbsp;Box 5b | Taxable Amount. |
| **Box 6 Group** | Social security benefits information. |
| &nbsp;&nbsp;Box 6a | Social Security Benefits. |
| &nbsp;&nbsp;Box 6b | Taxable Amount. |
| &nbsp;&nbsp;Box 6c | Use the Lump-Sum Election Method. |
| **Box 7 Group** | Capital gains information. |
| &nbsp;&nbsp;Schedule D Not Required | Indicates if Schedule D is not required. |
| &nbsp;&nbsp;Box 7 | Capital Gain or Loss. |
| **Box 8** | Other Income from Schedule 1. |
| **Box 9** | Total Income. |
| **Box 10** | Adjustments to Income from Schedule 1. |
| **Box 11** | Adjusted Gross Income. |
| **Box 12** | Standard Deduction or Itemized Deductions. |
| **Box 13** | Qualified Business Income Deduction. |
| **Box 14** | Total of Boxes 12 and 13. |
| **Box 15** | Taxable Income. |
| **Box 16 Group** | Tax calculation information. |
| &nbsp;&nbsp;Form 8814 | Indicates if Form 8814 is used. |
| &nbsp;&nbsp;Form 4972 | Indicates if Form 4972 is used. |
| &nbsp;&nbsp;Other Form | Indicates if another form is used. |
| &nbsp;&nbsp;Other Form Name | Name of the other form used. |
| &nbsp;&nbsp;Box 16 | Tax amount. |
| **Box 17** | Amount from Schedule 2. |
| **Box 18** | Total of Boxes 16 and 17. |
| **Box 19** | Child Tax Credit. |
| **Box 20** | Amount from Schedule 3. |
| **Box 21** | Total of Boxes 19 and 20. |
| **Box 22** | Tax Minus Child Tax Credit. |
| **Box 23** | Other Taxes Including Self-Employment Tax. |
| **Box 24** | Total Tax. |
| **Box 25 Group - Federal Income Tax** | Federal income tax withholding information. |
| &nbsp;&nbsp;Box 25a | Form W-2 withholding. |
| &nbsp;&nbsp;Box 25b | Form 1099 withholding. |
| &nbsp;&nbsp;Box 25c | Other Forms withholding. |
| &nbsp;&nbsp;Box 25d | Group Total. |
| **Box 26** | 2022 Estimated Tax Payments and Amount Applied from 2021 Return. |
| **Box 27** | Earned Income Credit. |
| **Box 28** | Additional Child Tax Credit from Schedule 8812. |
| **Box 29** | American Opportunity Credit from Form 8863. |
| **Box 31** | Amount from Schedule 3. |
| **Box 32** | Total Other Payments and Refundable Credits. |
| **Box 33** | Total Payments. |
| **Box 34** | Overpaid Amount. |
| **Box 35 Group - Refund information** |  |
| &nbsp;&nbsp;Box 35a - Form 8888 Attached | Specifies whether Form 8888 is attached. |
| &nbsp;&nbsp;Box 35a - Refundable Amount | The refund amount. |
| &nbsp;&nbsp;Box 35b - Routing Number | The bank’s routing number. |
| &nbsp;&nbsp;Box 35c - Type | Account type (Checking or Saving). |
| &nbsp;&nbsp;Box 35d - Account Number | The bank account number. |
| **Box 36** | Overpaid Amount to be Applied to 2023 Estimated Tax. |
| **Box 37** | Amount Owed. |
| **Box 38** | Estimated Tax Penalty. |
| **Third Party Designee** | Third party representative information. |
| &nbsp;&nbsp;Another Person Can Discuss with IRS | Permission for third party to discuss with IRS. |
| &nbsp;&nbsp;Designee’s Name | Name of the designated representative. |
| &nbsp;&nbsp;Phone Number | Phone number of the representative. |
| &nbsp;&nbsp;PIN | Personal Identification Number. |
| **Signature** | Taxpayer signature information. |
| &nbsp;&nbsp;Date | Date of signature. |
| &nbsp;&nbsp;Occupation | Taxpayer’s occupation. |
| &nbsp;&nbsp;Identity Protection PIN | Identity Protection PIN. |
| **Spouse’s Signature** | Spouse’s signature information (if filing jointly). |
| &nbsp;&nbsp;Date | Date of spouse’s signature. |
| &nbsp;&nbsp;Occupation | Spouse’s occupation. |
| &nbsp;&nbsp;Identity Protection PIN | Spouse’s Identity Protection PIN. |
| &nbsp;&nbsp;Phone Number | Spouse’s phone number. |
| &nbsp;&nbsp;Email Address | Spouse’s email address. |
| **Preparer** | Tax preparer information. |
| &nbsp;&nbsp;Preparer’s Name | Name of the tax preparer. |
| &nbsp;&nbsp;Date | Date prepared. |
| &nbsp;&nbsp;PTIN | Preparer Tax Identification Number. |
| &nbsp;&nbsp;Firm’s Name | Name of the preparation firm. |
| &nbsp;&nbsp;Firm’s Address | Address of the preparation firm. |
| &nbsp;&nbsp;Phone Number | Firm’s phone number. |
| &nbsp;&nbsp;Firm’s EIN | Firm’s Employer Identification Number. |
| &nbsp;&nbsp;Self-Employed | Indicates if the preparer is self-employed. |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |