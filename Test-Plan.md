# Coffee Kiosk POS - Customer Frontend

## Test Plan

<style>
@media print {
  body { font-family: Arial, sans-serif; font-size: 10.5pt; line-height: 1.45; color: #1f2937; }
  h1, h2, h3 { break-after: avoid-page; page-break-after: avoid; }
  table, img, blockquote { break-inside: avoid-page; page-break-inside: avoid; }
  table { width: 100%; border-collapse: collapse; font-size: 9pt; }
  th, td { padding: 6px; vertical-align: top; overflow-wrap: anywhere; }
  img { display: block; max-width: 100%; height: auto; margin: 12px auto; }
  code { white-space: pre-wrap; overflow-wrap: anywhere; }
  a { color: inherit; text-decoration: none; }
  .page-break { break-after: page; page-break-after: always; }
}
</style>

| Document field | Value |
|---|---|
| Project | Coffee Kiosk POS |
| Module | Customer - Frontend |
| Reference documents | FRS v1.0 and Test Estimation Report v1.0 |
| Prepared by | Kushagra Sinha (QA Engineer) |
| Version | 1.0 |
| Date | 25 September 2026 |
| Status | Draft - pending approval |

## Table of Contents

- [1. Purpose](#1-purpose)
- [2. Test Objectives](#2-test-objectives)
- [3. Scope](#3-scope)
  - [3.1 Features to Test](#31-features-to-test)
  - [3.2 Features Not to Test](#32-features-not-to-test)
- [4. Test Approach and Strategy](#4-test-approach-and-strategy)
  - [4.1 Overall Approach](#41-overall-approach)
  - [4.2 Test Types](#42-test-types)
  - [4.3 Manual Versus Automation](#43-manual-versus-automation)
  - [4.4 Test Evidence and Traceability](#44-test-evidence-and-traceability)
- [5. Test Environment](#5-test-environment)
- [6. Roles and Responsibilities](#6-roles-and-responsibilities)
- [7. Test Schedule](#7-test-schedule)
- [8. Entry and Exit Criteria](#8-entry-and-exit-criteria)
  - [8.1 Entry Criteria](#81-entry-criteria)
  - [8.2 Exit Criteria](#82-exit-criteria)
- [9. Suspension and Resumption Criteria](#9-suspension-and-resumption-criteria)
  - [9.1 Suspension Criteria](#91-suspension-criteria)
  - [9.2 Resumption Criteria](#92-resumption-criteria)
- [10. Defect Management Process](#10-defect-management-process)
- [11. Tools](#11-tools)
- [12. Risks and Mitigation](#12-risks-and-mitigation)
- [13. Test Deliverables](#13-test-deliverables)
- [14. Approvals and Sign-off](#14-approvals-and-sign-off)

<div class="page-break"></div>

> This plan becomes the active QA baseline after the referenced FRS and this Test Plan are approved. Material requirement changes require impact analysis and plan updates.

## 1. Purpose

This Test Plan defines the scope, objectives, approach, resources, schedule, controls, and completion criteria for manual testing of the Coffee Kiosk POS customer-facing frontend.

## 2. Test Objectives

- Verify all 48 requirements defined in the customer-frontend FRS.
- Confirm that customers can complete the flow from menu browsing to receipt generation.
- Validate order items, quantities, taxes, coupon discounts, and payable totals.
- Verify customer-visible UPI and Card payment outcomes and recovery paths.
- Confirm session timeout, privacy, usability, reliability, and role-access requirements.
- Identify and report defects before release approval.

## 3. Scope

### 3.1 Features to test

| Feature | Main coverage |
|---|---|
| Food Catalog | Categories, item details, availability, item options, adding items, and cart updates |
| Cart | Item display, quantity changes, removal, totals, empty cart, and navigation |
| Checkout | Locked order, dine-in/takeaway, coupon validation, totals, and payment-method selection |
| Payment Gateway | UPI/Card navigation, amount and order reference, processing, success, failure, timeout, cancellation, and retry |
| Confirmation and Receipt | Order details, bill calculation, emailed receipt, and starting a new session |
| Non-functional behaviour | Touch usability, accessibility basics, privacy, session security, reliability, and kiosk compatibility |

### 3.2 Features not to test

- Brew Crew and IT Admin interfaces.
- Direct API, database, AWS, and backend component testing.
- Internal functionality of the third-party payment provider.
- Load, stress, and full performance testing.
- Penetration testing or security certification.
- Test automation.
- KDS, thermal printer, cash payment, and physical card-terminal functionality.
- Devices, resolutions, and browsers not approved for the kiosk release.

## 4. Test Approach and Strategy

### 4.1 Overall approach

Testing will use a manual, black-box, requirement-based approach. Each FRS requirement will be mapped to test scenarios and test cases through the Requirement Traceability Matrix (RTM).

Test design will include:

- Positive and negative scenarios.
- Boundary and validation checks.
- Navigation and end-to-end customer flows.
- Integration failure and recovery paths.
- Error messages and prevention of duplicate actions.

### 4.2 Test types

| Test type | Purpose |
|---|---|
| Smoke testing | Confirm that the build and main order flow are ready for detailed testing. |
| Functional testing | Validate behaviour against the FRS. |
| Integration testing | Validate customer-visible interaction with backend, payment, coupon, and email services. |
| UI and usability testing | Check touch controls, labels, feedback, readability, and navigation consistency. |
| Basic security and privacy testing | Validate role protection, session clearing, and handling of payment and email data. |
| Compatibility testing | Validate the approved landscape kiosk resolution and supported Chromium-based browser. |
| Retesting | Verify that reported defects have been fixed. |
| Regression testing | Confirm that fixes have not affected the main customer order flow. |

### 4.3 Manual versus automation

All planned test design and execution will be manual. Automation assessment and implementation are outside this release scope.

### 4.4 Test evidence and traceability

- Each test case will record expected result, actual result, status, and supporting evidence where needed.
- Allowed execution statuses are **Pass**, **Fail**, **Blocked**, and **Not Executed**.
- RTM links will follow: `FRS Requirement → Test Scenario → Test Case → Result → Defect`.

## 5. Test Environment

| Area | Requirement |
|---|---|
| Customer device | Touchscreen kiosk or representative landscape test device |
| Browser | Supported modern Chromium-based kiosk browser |
| Frontend | ReactJS QA build |
| Supporting services | Spring Boot test backend and AWS-managed test data services |
| Payment | Approved UPI and Card payment sandbox with test credentials |
| Test data | Available/unavailable items and valid, invalid, expired, and inapplicable coupons |
| Email | Controlled test inbox for receipt delivery |
| Network | Stable connection to required QA services |

## 6. Roles and Responsibilities

| Role | Responsibility |
|---|---|
| Project Manager | Approves schedule, coordinates release decisions, and resolves project-level blockers. |
| QA Lead | Reviews the Test Plan, scenarios, cases, risks, defects, and closure recommendation. |
| QA Engineer | Prepares test data and documents; executes tests; logs defects; performs retesting and regression; maintains RTM and reports. |
| Developer / Integration Team | Provides testable builds, investigates defects, supplies fixes, and supports integrations. |
| Product / Business Stakeholder | Clarifies requirements, confirms expected business behaviour, and accepts residual risk. |

## 7. Test Schedule

The schedule follows the approved Test Estimation Report and assumes one full-time QA Engineer.

| Phase | Planned duration |
|---|---:|
| Requirement analysis and test planning | 1-2 working days |
| Test scenario and test-case design | 3-4 working days |
| Review, environment validation, and smoke testing | 1 working day |
| Test execution and defect reporting | 4-5 working days |
| Retesting, regression, RTM, and closure | 2-3 working days |
| **Total planned duration** | **Approximately 14 working days** |

The schedule may change if builds, fixes, approvals, or third-party services are delayed.

## 8. Entry and Exit Criteria

### 8.1 Entry criteria

- FRS, Test Plan, scenarios, and test cases are reviewed and approved.
- The QA build is deployed and release notes or known limitations are available.
- Required environment, menu data, coupon data, payment sandbox, and email inbox are ready.
- Unit and integration checks owned by the development team are completed.
- Smoke testing confirms that the main customer order flow is testable.

### 8.2 Exit criteria

- All planned test cases are executed or formally dispositioned.
- All FRS requirements have traceable test coverage.
- All P0 and P1 test cases pass.
- No open Critical or High defect remains unless formally accepted by stakeholders.
- Planned defect retesting and regression testing are complete.
- RTM, execution report, defect report, and test closure report are updated.
- Residual risks are documented and accepted before release recommendation.

## 9. Suspension and Resumption Criteria

### 9.1 Suspension criteria

Testing may be suspended when:

- Smoke testing fails on a release-blocking customer flow.
- The QA environment, backend, payment sandbox, or essential test data is unavailable.
- Order or payment results are unreliable and cannot be verified.
- A Critical defect prevents meaningful continuation of planned testing.
- The build differs materially from the approved requirements.

### 9.2 Resumption criteria

Testing may resume when:

- A corrected build or restored service is available.
- The blocking issue has been validated through smoke testing.
- Required test data and dependencies are usable.
- The QA Lead confirms the revised execution sequence and schedule impact.

## 10. Defect Management Process

1. Reproduce the issue and collect clear evidence.
2. Log the defect in Jira with summary, environment, steps, expected result, actual result, severity, priority, and attachments.
3. Review defects during triage with QA, development, and project stakeholders.
4. Assign the defect for correction or an approved disposition.
5. Retest the supplied fix and update the result.
6. Perform regression testing where the change may affect related flows.
7. Close, reopen, defer, or reject the defect with documented justification.

Defect workflow:

`New → Assigned → In Progress → Fixed → Retest → Closed / Reopened / Deferred`

| Severity | Meaning |
|---|---|
| Critical | Payment, order completion, or the application is unusable with no workaround. |
| High | A major customer feature fails or produces incorrect order/payment behaviour. |
| Medium | Functionality is affected, but a reasonable workaround exists. |
| Low | Minor UI, wording, or low-impact usability issue. |

## 11. Tools

| Purpose | Tool or format |
|---|---|
| Test documentation | Markdown and spreadsheet files |
| Defect tracking | Jira |
| Browser inspection | Chromium DevTools |
| Payment testing | Approved gateway sandbox |
| Version control | GitHub |
| Communication and approval | Email / Jira |

## 12. Risks and Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| Payment sandbox is unstable | Payment cases become blocked | Confirm access before execution and coordinate approved simulated outcomes if available. |
| Menu, coupon, or email data is unavailable | Related scenarios cannot be completed | Prepare and verify test data before the test cycle. |
| QA build is unstable | Execution is delayed and results become unreliable | Apply entry criteria and return failed builds for correction. |
| FRS changes after approval | Existing coverage and schedule become incomplete | Perform change impact analysis and update estimates, cases, and RTM. |
| High defect density or slow fixes | Retesting exceeds the planned schedule | Prioritise P0/P1 flows and communicate when contingency is consumed. |

## 13. Test Deliverables

### Before execution

- Approved FRS.
- Test Estimation Report.
- Test Plan.
- Test Scenarios and Test Cases.
- Test data and environment-readiness confirmation.

### During execution

- Test execution results and evidence.
- Defect reports.
- Updated RTM.
- Test progress updates.

### After execution

- Final Test Execution Report.
- Final Defect Report.
- Completed RTM.
- Test Summary and Closure Report.
- Release recommendation with residual risks.

## 14. Approvals and Sign-off

| Stakeholder | Representative | Approval method | Date | Status |
|---|---|---|---|---|
| Prepared by | Kushagra Sinha (QA Engineer) | Email | 25 September 2026 | Completed |
| QA Lead | To be assigned | Email / Jira | - | Pending |
| Project Manager | To be assigned | Email / Jira | - | Pending |
| Product / Business Stakeholder | To be assigned | Email / Jira | - | Pending |
