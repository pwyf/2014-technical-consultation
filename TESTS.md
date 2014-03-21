# Consolidated tests for the 2014 Aid Transparency Index

## Overarching issues

### Current data

* ongoing activities; OR
* planned end dates within the previous 12 months; OR
* actual end dates within the previous 12 months; OR
* commitment, disbursement or expenditure transaction dates within the previous 
12 months. 

(Activities that ended more than 12 months ago, but are still receiving loan or 
interest repayments, will not be counted as "current".)

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/1)

### Frequency

* frequency of publication will be scored on a more graduated basis;
* monthly publication will receive marginally more points than quarterly publication;
* quarterly publication will receive more points than publication that is less than quarterly.

We are consulting with our peer reviewers on the exact score that should be applied to each frequency.

We are considering the exact methodology for calculating frequency, but we will 
again rely on IATI Registry logs. As in 2013, timeliness will not be captured 
separately this year, as we want to do some more work in investigating possible 
methodologies before including such a measure.

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/2)

### Sampling

A total of 14 indicators refer to documents. These documents are manually checked to verify that they contain the required information to score for the indicator. For IATI publishers, the documents may be located via links in their XML files. 

In 2014, 10 documents will be randomly sampled from organisations’ IATI files, with a minimum of five documents needing to meet the criteria for the indicator. 

For organisation level documents covered by indicators 5, 6, 7 and 11, where only a single document is expected, the document will be checked to see if it contains the required information to score on the indicator. 

We will also be sampling data on results, sub-national location and conditions.

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/39)

## Indicators

### Commitment-level

*The three commitment-level indicators will remain unchanged; they are not tested by data quality tests as they rely on secondary sources of data.*

### Organisation-level

#### 4. Organisation Strategy

Unchanged from 2013 Index.

Test:

        document-link/category[@code='B02'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/3)

#### 5. Annual Report

Unchanged from 2013 Index.

Test:

        document-link/category[@code='B01'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/4)

#### 6. Allocation Policy

Unchanged from 2013 Index.

Test:

        document-link/category[@code='B04'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/5)

#### 7. Procurement Policy

Unchanged from 2013 Index.

Test:

        document-link/category[@code='B05'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/6)

#### 8. Country Strategy

Unchanged from 2013 Index.

Test:

        the percentage of countries for which there is a current country 
        budget, which have a country strategy paper

Organisations should use the same name in the title of their country strategy 
papers, as they use in the recipient country budget. If they are using only 
ISO-country codes, they should use an English-language name of the country in 
the title of the country strategy paper document-link.

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/7)

#### 9. Total Organisation Budget

Unchanged from 2013 Index.

Points are awarded for providing a budget for each year forward, for the next 
three years

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/8)

#### 10. Disaggregated Budget

Unchanged from 2013 Index. 

Disaggregated budgets are scored for each of the three years ahead for which 
they are available. We assess the value of all recipient country budgets 
available for the relevant year as a percentage of 50% of the average of Country 
Programmable Aid (CPA), multiplied by the total budget for the relevant year. If 
the relevant year is not available, the current year will be used instead. We 
will use the same fraction for all donors (21.36%). The total points available 
will be distributed equally among the three years.

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/9)

#### 11. Audit

Unchanged from 2013 Index.

Test:

        document-link/category[@code='B04'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/10)

### Activity-level

#### 12. Implementer

Unchanged from 2013 Index.

Test:

        participating-org[@role='Implementing'] exists (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/11)

#### 13. Unique ID

In addition to the 2013 test, we will add a new test to assess whether the 
`reporting-org/@ref` occurs in the `iati-identifier/text()`.

Tests:

        iati-identifier exists?
        iati-identifier/text() contains reporting-org/@ref?

*Explanation of second test*

If the reporting-org is `44000` then the following would pass this test:

    <iati-identifier>44000-P126875</iati-identifier>

While this example would not pass the test:

    <iati-identifier>P126875</iati-identifier>

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/12)

#### 14. Title

Unchanged from 2013 Index.

Tests:

        title/text() exists?
        title/text() has more than 10 characters?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/13)

#### 15. Description

Unchanged from 2013 Index.

Tests:

        description/text() exists?
        description/text() has more than 40 characters?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/14)

#### 16. Planned Dates

Unchanged from 2013 Index.

Tests:

        activity-date[@type='start-planned'] exists?
        activity-date[@type='end-planned'] exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/15)

#### 17. Actual Dates

Unchanged from 2013 Index.

Tests:

        activity-date[@type='start-actual'] exists (if activity-status/@code is at least 2)?
        activity-date[@type='end-actual'] exists (if activity-status/@code is at least 3)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/16)

#### 18. Current Status

In addition to the 2013 test, we will add a new test, to assess whether the 
`activity-status/@code` is on the IATI `ActivityStatus` codelist.

Tests:

        activity-status exists?
        activity-status/@code is on list ActivityStatus?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/17)

#### 19. Contact Details

Unchanged from 2013 Index.

Tests:

        contact-info exists?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/18)

#### 20. Collaboration Type

In addition to the 2013 test, we will add a new test, to assess whether the 
`collaboration-type/@code` is on the IATI `CollaborationType` codelist.

Tests:

        collaboration-type exists (if activity-status/@code is at least 2)?
        collaboration-type/@code is on list CollaborationType (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/19)

#### 21. Flow Type

In addition to the 2013 test, we will add a new test, to assess whether the 
`default-flow-type/@code` or `transaction/flow-type/@code` is on the IATI 
`FlowType` codelist.

Tests:

        default-flow-type or transaction/flow-type exists (if activity-status/@code is at least 2)?
        default-flow-type/@code or transaction/flow-type/@code is on list FlowType (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/20)

#### 22. Aid Type

In addition to the 2013 test, we will add a new test, to assess whether the 
`default-aid-type/@code` or `transaction/aid-type/@code` is on the IATI 
`AidType` codelist.

Tests:

        default-aid-type or transaction/aid-type exists (if activity-status/@code is at least 2)?
        default-aid-type/@code or transaction/aid-type/@code is on list AidType (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/21)

#### 23. Finance Type

In addition to the 2013 test, we will add a new test, to assess whether the 
`default-finance-type/@code` or `transaction/finance-type/@code` is on the 
IATI `FinanceType` codelist.

Tests:

        default-finance-type or transaction/finance-type exists (if activity-status/@code is at least 2)?
        default-finance-type/@code or transaction/finance-type/@code is on list FinanceType (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/22)


#### 24. Sectors

The second test used in the 2013 Index will be amended. It will will now assess 
whether at least one DAC sector code is used per activity, and whether the 
`sector[@vocabulary="DAC"]/@code` or `sector[not(@vocabulary)]/@code` is on the 
DAC `Sector` codelist.

Tests:

        sector exists?
        at least one `sector[@vocabulary="DAC"]/@code` or `sector[not(@vocabulary)]/@code` is on list Sector?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/23)

#### 25. Sub-national location

The tests will be altered from the 2013 Index to exclude activities where the 
`recipient-region/@code` is `998` (bilateral/unspecified). Sub-national
locations passing the test will then be sampled.

        location exists (if activity-status/@code is at least 2 and recipient-region/@code is not 998)?
        location/coordinates exists (if activity-status/@code is at least 2 and recipient-region/@code is not 998)?

The sample frame for manual sampling is: 10 activities that pass the test. At 
least 5 will need to be assessed as "appropriate", in order to score IATI data 
quality points for this indicator. We will assess whether sub-national locations 
are "appropriate"", "inappropriate", or "indeterminate". Appropriateness will be 
defined by the extent to which the location conforms to the description and 
other documentation provided. 

*Examples*

  * if the description states that the project is active in five villages in the west of the country, and the sub-national location only states the capital city, the sub-national location will be assessed as **inappropriate**.
  * if the activity `aid-type` is budget support (`A01`), and the sub-national location states the country or the capital city, the sub-national location will be assessed as **appropriate**.

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/24)

#### 26. Tied Aid Status

In addition to the 2013 test, we will add a new test, to assess whether the 
`default-tied-status/@code` or `transaction/tied-status/@code` is on the IATI 
`TiedStatus` codelist.

Tests:

        default-tied-status or transaction/tied-status exists (if activity-status/@code is at least 2)?
        default-tied-status or transaction/tied-status exists is on list TiedStatus (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/25)

#### 27. Memorandum of Understanding

Unchanged from 2013 Index.

Test:

        document-link/category[@code='A09'] exists (if activity-status/@code is at least 2 and (default-aid-type or transaction/aid-type is not C01))?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/26)

#### 28. Evaluations

Unchanged from 2013 Index.

Test:

        document-link/category[@code='A07'] exists (if activity-status/@code is at least 3)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/27)

#### 29. Objectives

The test used in the 2013 Index will be amended. It will will now accept either 
objectives in documents (category code `A02`, "Objectives / Purpose of 
activity") or objectives in the description element (`description[@type="2"]`, 
"Objectives").

Test:

        document-link/category[@code='A02'] or description[@type="2"] exists (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/28)

#### 30. Budget documents

Unchanged from 2013 Index.

Test:

        document-link/category[@code='A05'] exists (if activity-status/@code is at least 2 and (default-aid-type or transaction/aid-type is not A01))?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/29)

#### 31. Contracts

The tests used in the 2013 Index will be amended. There will now be a single 
test that will accept either the contract (`A11`) or summary information about 
the contract (`A06`).

Test:

        document-link/category[@code='A06'] or document-link/category[@code='A11'] exists (if activity-status/@code is at least 2 and (default-aid-type or transaction/aid-type is not A01))?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/30)

#### 32. Tenders

Unchanged from 2013 Index.

Test:

        document-link/category[@code='A10'] exists (if activity-status/@code is at least 2 and (default-aid-type or transaction/aid-type is not A01))?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/31)

#### 33. Budget

The tests used in the 2013 Index will be amended. The first half of the points 
will be available for having a forward budget running at least until December 
2014, or until the end of the activity, whichever is earlier. The second half of 
the points will be available for providing this information broken down by 
quarter.

Tests:

        budget or planned-disbursement is available forward (if activity-status/@code is at least 2)?
        budget or planned-disbursement is available forward by quarters (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/32)

#### 34. Commitments

Unchanged from 2013 Index.

Test:

        transaction/transaction-type[@code='C'] exists (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/33)

#### 35. Disbursements and expenditures

Unchanged from 2013 Index.

Test:

        transaction/transaction-type[@code='D'] or transaction/transaction-type[@code='E'] exists (if activity-status/@code is at least 2)?

[[full discussion...]](https://github.com/pwyf/index-data-quality-tests/issues/34)

#### 36. Budget identifier

The second test used in the 2013 Index will be amended (for 
`country-budget-items`). It will now assess whether the 
`country-budget-items[@vocabulary="1"]/budget-item/@code` is on the IATI 
`BudgetIdentifier` codelist.

Tests:

        capital-spend exists (if activity-status/@code is at least 2 and (default-aid-type or transaction/aid-type is not A01))?
        at least one country-budget-items[@vocabulary="1"]/budget-item/@code is on list BudgetIdentifier?

[[full discussion]](https://github.com/pwyf/index-data-quality-tests/issues/35)

#### 37. Results

The tests used in the 2013 Index will be amended. There will now be a single 
test that will accept either results data (`result`) or a results document (`A08`).

Test:

        document-link/category[@code='A08'] or result exists (if activity-status/@code is at least 2)?

[[full discussion]](https://github.com/pwyf/index-data-quality-tests/issues/36)

#### 38. Impact appraisals

Unchanged from 2013 Index.

Test:

        document-link/category[@code='A01'] exists (if activity-status/@code is at least 2)?

[[full discussion]](https://github.com/pwyf/index-data-quality-tests/issues/37)

#### 39. Conditions

The tests used in the 2013 Index will be amended. There will now be a single 
test that will accept either results data (`conditions`) or a results document 
(`A04`). Furthermore, conditions will not be expected to exist if it is
explicitly stated that no conditions are attached.

Test:

        conditions or document-link/category[@code='A04'] exists (if activity-status/@code is at least 2 and conditions/@attached is not 0)?

[[full discussion]](https://github.com/pwyf/index-data-quality-tests/issues/38)
