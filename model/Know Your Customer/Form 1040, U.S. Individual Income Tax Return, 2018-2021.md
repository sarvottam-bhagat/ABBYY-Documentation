# Know Your Customer  
**Form 1040, U.S. Individual Income Tax Return, 2018-2021**

The Form 1040 model extracts data from U.S. Individual Income Tax Returns for tax years 2018-2021.

---

## Usage

Copy the code block, replace `YOUR_API_KEY` with your API key, then process documents quickly.

### Python Example

```python
from abbyy_document_ai import DocumentAi
import time

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
| **Dependents (repeating group)** | Information about the dependents. |
| &nbsp;&nbsp;Full Name | The dependent’s full name. |
| &nbsp;&nbsp;SSN | The dependent’s social security number. |
| &nbsp;&nbsp;Relationship | The dependent’s relationship to the taxpayer. |
| &nbsp;&nbsp;Child Tax Credit | Indicates if the dependent qualifies for the Child Tax Credit. |
| &nbsp;&nbsp;Credit for Other Dependents | Indicates if the dependent qualifies for Credit for Other Dependents. |
| **Wages Salaries Tips** | Information about wages, salaries, and tips. |
| **Tax-Exempt Interest Group** | Interest income information. |
| &nbsp;&nbsp;Tax-Exempt Interest | Tax-exempt interest income. |
| &nbsp;&nbsp;Taxable Interest | Taxable interest income. |
| **Dividends Group** | Dividend income information. |
| &nbsp;&nbsp;Qualified Dividends | Qualified dividend income. |
| &nbsp;&nbsp;Ordinary Dividends | Ordinary dividend income. |
| **IRAs Pensions and Annuities Group (outdated)** | IRA, pension, and annuity information (outdated). |
| &nbsp;&nbsp;IRAs Pensions and Annuities (outdated) | IRA, pension, and annuity amounts (outdated). |
| &nbsp;&nbsp;Taxable Amount (outdated) | Taxable amount of IRA, pension, and annuity distributions (outdated). |
| **IRA Distributions Group** | IRA distribution information. |
| &nbsp;&nbsp;IRA Distributions | IRA distribution amounts. |
| &nbsp;&nbsp;Taxable Amount | Taxable amount of IRA distributions. |
| **Pensions and Annuities Group** | Pension and annuity information. |
| &nbsp;&nbsp;Pensions and Annuities | Pension and annuity amounts. |
| &nbsp;&nbsp;Taxable Amount | Taxable amount of pensions and annuities. |
| **Social Security Benefits Group** | Social security benefits information. |
| &nbsp;&nbsp;Social Security Benefits | Social security benefit amounts. |
| &nbsp;&nbsp;Taxable Amount | Taxable amount of social security benefits. |
| **Capital Gain or Loss Group** | Capital gains information. |
| &nbsp;&nbsp;Capital Gain or Loss | Capital gain or loss amount. |
| &nbsp;&nbsp;Schedule D Not Required | Indicates if Schedule D is not required. |
| **Amount from Schedule 1 Line 22 (outdated)** | Amount from Schedule 1 Line 22 (outdated). |
| **Other Income from Schedule 1** | Other income reported on Schedule 1. |
| **Total Income** | Total income from all sources. |
| **Adjustments to Income Group** | Income adjustment information. |
| &nbsp;&nbsp;From Schedule 1 | Adjustments from Schedule 1. |
| &nbsp;&nbsp;Charitable Contributions (outdated) | Charitable contribution adjustments (outdated). |
| &nbsp;&nbsp;Total Adjustments to Income (outdated) | Total income adjustments (outdated). |
| **Adjusted Gross Income** | Adjusted gross income amount. |
| **Taxable Income Group** | Information for calculating taxable income. |
| &nbsp;&nbsp;Standard Deduction or Itemized Deductions | Standard or itemized deduction amount. |
| &nbsp;&nbsp;Charitable Contributions | Charitable contribution deductions. |
| &nbsp;&nbsp;Partial Sum | Partial sum in tax calculation. |
| &nbsp;&nbsp;Qualified Business Income Deduction | Qualified business income deduction amount. |
| &nbsp;&nbsp;Total Deduction | Total deduction amount. |
| &nbsp;&nbsp;Taxable Income | Final taxable income amount. |
| **Tax Group** | Tax calculation information. |
| &nbsp;&nbsp;Tax | Tax amount. |
| &nbsp;&nbsp;Form 8814 | Indicates if Form 8814 is used. |
| &nbsp;&nbsp;Form 4972 | Indicates if Form 4972 is used. |
| &nbsp;&nbsp;Other Form | Indicates if another form is used. |
| &nbsp;&nbsp;Other Form Name | Name of other form used. |
| &nbsp;&nbsp;Amount from Schedule 2 Check (outdated) | Amount from Schedule 2 verification (outdated). |
| &nbsp;&nbsp;Amount from Schedule 2 | Amount from Schedule 2. |
| &nbsp;&nbsp;Group Total | Total tax amount. |
| **Child Tax Credit Group** | Child tax credit information. |
| &nbsp;&nbsp;Child Tax Credit | Child tax credit amount. |
| &nbsp;&nbsp;Amount from Schedule 3 Check (outdated) | Amount from Schedule 3 verification (outdated). |
| &nbsp;&nbsp;Amount from Schedule 3 | Amount from Schedule 3. |
| &nbsp;&nbsp;Group Total | Total credit amount. |
| **Tax minus Child Tax Credit** | Tax amount after subtracting child tax credit. |
| **Other Taxes Including Self-Employment Tax** | Additional tax amounts including self-employment tax. |
| **Total Tax** | Total tax liability. |
| **Federal Income Tax Withheld from Forms W-2 and 1099 (outdated)** | Federal income tax withholding (outdated). |
| **Federal Income Tax Group** | Federal income tax withholding information. |
| &nbsp;&nbsp;Form W-2 | Tax withheld from Form W-2. |
| &nbsp;&nbsp;Form 1099 | Tax withheld from Form 1099. |
| &nbsp;&nbsp;Other Forms | Tax withheld from other forms. |
| &nbsp;&nbsp;Group Total | Total federal income tax withheld. |
| **This Year Estimated Tax Payments and Amount Applied from Last Year Return** | Current year estimated tax payments and prior year credit. |
| **Earned Income Credit** | Earned income credit information. |
| &nbsp;&nbsp;Earned Income Credit | Earned income credit amount. |
| &nbsp;&nbsp;Qualified to Claim the EIC | Eligibility for earned income credit. |
| &nbsp;&nbsp;Combat Pay Election | Combat pay election for EIC calculation. |
| &nbsp;&nbsp;Prior Year Earned Income | Prior year income for EIC calculation. |
| **Additional Child Tax Credit (Schedule 8812)** | Additional child tax credit amount. |
| **American Opportunity Credit from Form 8863** | Education credit amount. |
| **Recovery Rebate Credit** | Recovery rebate credit amount. |
| **Amount from Schedule 5 (outdated)** | Amount from Schedule 5 (outdated). |
| **Amount from Schedule 3** | Amount from Schedule 3. |
| **Total Other Payments and Refundable Credits** | Total of additional payments and credits. |
| **Total Payments** | Total payments made. |
| **Overpaid Amount** | Amount overpaid. |
| **Refund Group** | Refund information. |
| &nbsp;&nbsp;Form 8888 Attached | Indicates if Form 8888 is attached. |
| &nbsp;&nbsp;Refundable Amount/Refunded | Amount to be refunded. |
| &nbsp;&nbsp;Routing Number | Bank routing number. |
| &nbsp;&nbsp;Type | Account type (Checking or Saving). |
| &nbsp;&nbsp;Account Number | Bank account number. |
| **Overpaid Amount to be Applied to Next Year Estimated Tax** | Amount of overpayment to apply to next year’s estimated tax. |
| **Owed Amount** | Amount owed to IRS. |
| **Estimated Tax Penalty** | Estimated tax penalty amount. |
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
| &nbsp;&nbsp;Third Party Designee (outdated) | Third party designee information (outdated). |
| &nbsp;&nbsp;Self-Employed | Indicates if the preparer is self-employed. |

---

## Supported Languages

| Countries | Languages |
|-----------|-----------|
| Global    | English   |