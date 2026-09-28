---
title: ISA Returns API service guide
weight: 1
---

# ISA Returns API service guide

**Version 0.3** issued 30 September 2026

***

## Overview

This guide explains how HMRC-approved ISA managers can use the ISA Returns API to submit monthly reports containing 
cumulative current-year subscription data to HMRC.

It is intended for anyone involved in preparing or submitting monthly reports. This might include:

- compliance teams preparing or reviewing monthly reports
- operations teams submitting monthly reports
- software developers building systems to submit monthly reports using the API

This guide includes general guidance for all users and technical instructions for developers.

## Monthly reports

As part of new legislation HMRC has introduced changes to how ISAs are reported. As well as the annual statistical 
return, ISA managers will be required to report subscription changes on a monthly basis. This is primarily to improve 
data accuracy, detect oversubscriptions in real-time, and enforce the overall £20,000 annual ISA limit more effectively.

Each monthly report must include cumulative current-year ISA subscription activity for the reporting period, including 
subscription changes, transfers and withdrawals where applicable.

Each monthly report must be generated to cover for all ISA subscription activity between the 6th of each month and the 
5th of the following month. You must submit this report between the 6th of the month and the 19th (by 23:59) of the month
in which the reporting period ends.

Each monthly report submitted must contain the previous month’s data.

## API overview

The ISA Returns API is a REST API for submitting monthly ISA subscription reports. It supports HMRC’s digital ISA 
reporting service by enabling secure, standardised and frequent digital reporting. This helps HMRC detect errors quickly 
and improve oversight throughout the tax year.

You can use the API to:

- submit monthly reports containing cumulative current-year subscription data, including transfers and withdrawals
- submit a declaration confirming that data for the current reporting window has been submitted
- retrieve validation results in batches

Each monthly report contains the previous month’s data and must be submitted between the 6th of a month and the 19th 
(by 23:59) of the month in which the reporting period ends.

To use the API, your organisation must be approved by HMRC as an ISA manager and enrolled for digital ISA reporting. 
If you are not yet approved, you can apply through the 
[Manage ISAs registration process](https://www.tax.service.gov.uk/obligations/enrolment/isa).

The API is designed for integration into internal systems or third-party software, reducing manual data handling and 
enabling programmatic access to results.

This diagram shows how ISA managers or third-party organisations use application software to submit monthly reports to 
HMRC using the ISA Returns API.

<img src="documentation/images/isa-returns-overview.png" alt="Diagram showing a user from an ISA manager or 
third-party organisation submitting a monthly report via application software to HMRC using the ISA Returns API.
A developer from the same organisation builds and maintains the software." style="width:600px; max-height:489px"/>

This diagram shows the full monthly reporting cycle, from preparing data to reviewing reconciliation results. ISA 
managers or third-parties prepare and submit data, HMRC validates the report, and the results are retrieved and acted 
on by the submitting organisation.

<img src="documentation/images/isa-returns-api-monthly-reporting-cycle.png" alt="Diagram showing five steps in 
the monthly reporting cycle. The ISA manager or third-party prepares and submits a report. HMRC validates it. 
The ISA manager or third-party retrieves the results and takes any required action." style="width:523px; max-height:410px" />

## ISA Returns API behaviour

<img src="documentation/images/isa-returns-submission-flow.png" alt="Diagram showing the full flow of the API." 
style="width:924px; max-height:1905px"/>

The whole lifecycle via ISA Returns API consists of five main stages:

1. API subscription (one-time) - The developer subscribes to the ISA Returns API through the Developer Hub and preferably
registers with a TPA callback URL.

2. ISA Returns submission flow - During the ISA Returns data submission, there are four possible scenarios as listed below:

    a. Submission not allowed - if the ISA Returns is submitted outside of the reporting window period or if a declaration
has already been submitted for that specific month, then a submission failure occurs and an error response is returned.

    b. Structural or schema validation error - if the submitted ISA returns data fails due to structural validation error, 
then the API returns an error response.

    c. Successful submission - if the ISA returns data is submitted and the structural validation is successful, then the 
API returns a success response.
3. The declaration submission flow is similar to the ISA Returns submission flow mentioned in Step 2 which can lead to a 
declaration submission failure or a successful response. The success response is returned together with the Push Pull 
Notifications Service (PPNS) box ID. 
4. Reconciliation flow - once the monthly report is complete and the reporting window is closed, your submissions will 
be processed. PPNS will then notify you via the callback URL, if a reconciliation report is available which is a 
compilation of the rejected records.
5. Download reconciliation report - once notified, you can retrieve the reconciliation results for the monthly report 
using cursor pagination.

## End-to-end user journeys

These journeys show examples of use.

- [Before you start](documentation/before-you-start.html)
- [Get started with the API](documentation/get-started-with-api.html)
- [Use the API for monthly reports](documentation/use-api-for-monthly-reports.html)
- [Submit monthly report](documentation/submit-monthly-report.html)
- [Get report reconciliation results](documentation/get-report-reconciliation-results.html)

Depending on your role, you might not need to follow every journey:

- administrative, compliance, and operations teams can skip API-specific content
- developers can focus on learning how the API works and getting started with it

## Terms of use

Before HMRC grants production access, your organisation must accept and comply with our 
[terms of use](https://developer.service.hmrc.gov.uk/api-documentation/docs/terms-of-use).

## Versioning

When an API changes in a way that is backwards-incompatible, we increase the version number of the API. For more 
information on versioning, see the [reference guide](/api-documentation/docs/api/service/disa-returns).

Users should test and validate against the appropriate API version before deploying to production environments.

Refer to the [ISA Returns API change log](https://github.com/hmrc/disa-returns/blob/main/CHANGELOG.md) for all important 
changes and release information listed in a reverse chronological order with the latest updates being listed at the top of the page.

## Support

Before contacting us, find out if there is planned API downtime or a technical issue by checking 
[HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk/).

For support with onboarding, the API access, or the
[HMRC Developer sandbox queries](https://developer.service.hmrc.gov.uk/api-documentation/docs/testing), submit your 
request using the [online support form](https://developer.service.hmrc.gov.uk/devhub-support/start) or email your queries 
to SDSTeam@hmrc.gov.uk.

When submitting a request, users should provide details of any available error information to help with the troubleshooting 
and resolution of the issue.

