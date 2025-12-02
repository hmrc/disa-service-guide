---
title: ISA Returns API service guide
weight: 1
---

# ISA Returns API service guide

**Version 0.1** issued 25 November 2025

***

This guide explains how HMRC-approved ISA managers can use the ISA Returns API to submit monthly reports about current-year ISA subscription data to HMRC.

It is intended for anyone involved in preparing or submitting monthly reports. This might include:

- compliance teams preparing or reviewing monthly reports
- operations teams submitting monthly reports
- software developers building systems to submit monthly reports using the API

This guide includes general guidance for all users and technical instructions for developers.

## API overview

The ISA Returns API is a REST API for submitting monthly ISA subscription reports. It supports system-to-system integration and enables ISA managers to meet HMRC's digital reporting obligations securely and efficiently.

Use this API to:

- submit monthly reports with a cumulative total made up of current-year subscription data, including transfers and withdrawals
- check the status of submitted reports to confirm processing
- retrieve validation results in batches using pagination

Each report must cover ISA subscription activity from the 6th of one month to the 5th of the next, and be submitted between the 6th and 23:59 on the 19th.

To use the API, your organisation must be approved by HMRC as an ISA manager and enrolled for digital ISA reporting. If you are not yet approved, you can apply through the [Manage ISAs registration process](http://b).

The API is designed for integration into internal systems or third-party software. It enables organisations to reduce manual data handling and retrieve results programmatically.

This diagram shows how ISA managers or third-party organisations use application software to submit monthly reports to HMRC using the ISA Returns API.

<img src="documentation/images/isa_returns_api_overview.svg" alt="Diagram showing a user from an ISA manager or third-party organisation submitting a monthly report via application software to HMRC using the ISA Returns API. A developer from the same organisation builds and maintains the software." style="width:600px; max-height:300px; " />

This diagram shows the full monthly reporting cycle, from preparing data to reviewing reconciliation results. ISA managers or third parties prepare and submit data, HMRC validates the report, and the results are retrieved and acted on by the submitting organisation.

<img src="documentation/images/isa_returns_api_monthly_reporting_cycle.svg" alt="Diagram showing five steps in the monthly reporting cycle. The ISA manager or third party prepares and submits a report. HMRC validates it. The ISA manager or third party retrieves the results and takes any required action." style="width:600px; max-height:325px; " />

## End-to-end user journeys

These journeys show examples of use.

- [Before you start](documentation/before-you-start.html)
- [Get started with the API](documentation/get-started-with-api.html)
- [Use the API for monthly reports](documentation/use-api-for-monthly-reports.html)
- [Submit monthly report](documentation/submit-monthly-report.html)
- [Get report summary](documentation/get-report-summary.html)
- [Get report reconciliation results](documentation/get-report-reconciliation-results.html)

Depending on your role, you might not need to follow every journey:

- administrative, compliance, and operations teams can skip API-specific content
- developers can focus on learning how the API works and getting started with it

## Terms of use

Before HMRC grants production access, your organisation must accept and comply with our [terms of use](https://developer.service.hmrc.gov.uk/api-documentation/docs/terms-of-use).

## Related API documentation

- [ISA Returns API changelog](https://github.com/hmrc/disa-returns) (on GitHub)

## Support

Check the [HMRC API Platform Status](https://api-platform-status.production.tax.service.gov.uk/) page and [ISA Returns service availability](http://a) page for planned downtime or current issues.

If you need help, use the [support form](https://developer.service.hmrc.gov.uk/developer/support) to contact us. HMRC's Software Developer Support Team will reply within two working days.

## Changelog

To see updates to this guide, check the changelog in the [ISA Returns API service guide](https://github.com/hmrc/disa-service-guide) repository on GitHub.