# Coffee Kiosk POS - Customer Frontend

## Test Estimation Report

| Document field | Value |
|---|---|
| Project | Coffee Kiosk POS |
| Module | Customer - Frontend |
| Reference | Coffee Kiosk POS Customer Frontend FRS v1.0 |
| Prepared by | Kushagra Sinha (QA Engineer) |
| Version | 1.0 |
| Date | 25 September 2026 |
| Status | Provisional - pending FRS approval |

## Table of Contents

- [1. Purpose](#1-purpose)
- [2. Estimation Basis](#2-estimation-basis)
  - [Estimation Technique](#estimation-technique)
- [3. Testing Scope](#3-testing-scope)
  - [In Scope](#in-scope)
  - [Out of Scope](#out-of-scope)
- [4. Assumptions and Dependencies](#4-assumptions-and-dependencies)
  - [Assumptions](#assumptions)
  - [Dependencies](#dependencies)
- [5. WBS Estimation Matrix](#5-wbs-estimation-matrix)
- [6. Effort and Duration Summary](#6-effort-and-duration-summary)
  - [Indicative Schedule](#indicative-schedule)
- [7. Resource Requirements](#7-resource-requirements)
  - [Human Resources](#human-resources)
  - [Environment and Tools](#environment-and-tools)
- [8. Risks and Mitigation](#8-risks-and-mitigation)
- [9. Cost and Change Control](#9-cost-and-change-control)
- [10. Approval](#10-approval)

> The referenced FRS is currently marked "Draft for review" with sign-off pending. This estimate becomes the planning baseline after FRS approval. Material scope changes require re-estimation.

## 1. Purpose

This report estimates the manual QA effort, duration, resources, dependencies, and risks required to test the Coffee Kiosk POS customer-facing frontend. It is intended to support project planning before detailed test cases are prepared.

## 2. Estimation Basis

The estimate covers all 48 requirements in FRS v1.0:

| Requirement group | Count |
|---|---:|
| Food Catalog | 7 |
| Cart | 6 |
| Checkout | 8 |
| Payment Gateway | 7 |
| Order Confirmation and Receipt | 5 |
| Non-functional requirements | 15 |
| **Total** | **48** |

### Estimation technique

- **Work Breakdown Structure (WBS):** Used to estimate each QA activity separately.
- **Expert judgement:** Used to estimate design and execution effort based on feature complexity.
- **Three-point estimation:** Applied to uncertain work, especially payment testing and defect retesting.

Three-point formula:

`Estimated effort = (Optimistic + 4 × Most Likely + Pessimistic) ÷ 6`

Example for payment execution: `(6 + 4 × 8 + 12) ÷ 6 = 8.3 hours`, rounded to 8 planning hours.

## 3. Testing Scope

### In scope

- Manual functional testing of Food Catalog, Cart, Checkout, Payment, and Receipt features.
- Positive, negative, boundary, navigation, and error-handling scenarios.
- Customer-visible UPI and Card payment integration behaviour.
- Coupon validation, totals, taxes, and discount calculations.
- Touchscreen UI, usability, and basic accessibility checks.
- Customer-session timeout, privacy, and protected-role access checks.
- Supported Chromium-based kiosk browser and approved landscape resolution.
- Defect reporting, retesting, regression testing, RTM, and test summary reporting.

### Out of scope

- Brew Crew and IT Admin interfaces.
- Direct API, database, and AWS service testing.
- Internal testing of the third-party payment provider.
- Load, stress, and full performance testing.
- Penetration testing or formal security certification.
- Test automation.
- KDS, thermal printer, cash payment, or physical card-terminal testing.

## 4. Assumptions and Dependencies

### Assumptions

- FRS v1.0 is approved without major functional changes.
- One manual QA Engineer is assigned full-time, supported by a QA Lead for review.
- One person-day equals 7 productive QA hours.
- A stable QA build is provided before execution.
- Defect fixes are supplied without long external delays.
- One approved kiosk resolution and Chromium-based browser are used.

### Dependencies

- Working Spring Boot backend and test environment.
- Stable UPI and Card payment sandbox.
- Test menu data containing available and unavailable items.
- Valid, invalid, expired, and inapplicable coupon data.
- Test email inbox for receipt delivery.
- Approved test UPI IDs and Card test credentials.
- Jira or an equivalent defect-management tool.

## 5. WBS Estimation Matrix

| WBS ID | QA activity | Main output | Effort (hours) |
|---|---|---|---:|
| WBS-01 | FRS review and requirement analysis | Clarification list and coverage notes | 4 |
| WBS-02 | Test planning and estimation | Approved test approach and estimate | 4 |
| WBS-03 | Test scenario, test case, and test-data design | Review-ready test suite | 20 |
| WBS-04 | Test review and rework | Approved scenarios and test cases | 4 |
| WBS-05 | Environment validation and smoke testing | Test-ready build confirmation | 4 |
| WBS-06 | Food Catalog execution | Catalog results and evidence | 3 |
| WBS-07 | Cart execution | Cart results and evidence | 4 |
| WBS-08 | Checkout and coupon execution | Checkout results and evidence | 6 |
| WBS-09 | UPI and Card payment execution | Gateway integration results and evidence | 8 |
| WBS-10 | Confirmation, receipt, and session execution | Receipt and session results | 4 |
| WBS-11 | UI, accessibility, privacy, security, and reliability checks | Non-functional results | 5 |
| WBS-12 | Defect investigation, reporting, and triage | Logged and tracked defects | 4 |
| WBS-13 | Defect retesting and regression | Fix validation and regression results | 10 |
| WBS-14 | RTM, execution report, and test closure | Final QA reports | 4 |
|  | **Base effort** |  | **84** |
|  | **Contingency - 15%** | Gateway, defect, and minor clarification uncertainty | **13** |
|  | **Total estimated effort** |  | **97 hours** |

## 6. Effort and Duration Summary

| Measure | Estimate |
|---|---:|
| Base QA effort | 84 hours |
| Contingency | 13 hours |
| Total QA effort | 97 hours |
| Productive hours per person-day | 7 hours |
| Estimated effort in person-days | Approximately 14 person-days |
| Planned duration with 1 QA Engineer | Approximately 14 working days |

The duration assumes prompt environment access and defect turnaround. Waiting time for builds, approvals, or external services is not included in QA effort and may extend calendar duration.

### Indicative schedule

| Phase | Expected duration |
|---|---:|
| Requirement analysis and planning | 1-2 days |
| Scenario and test-case design | 3-4 days |
| Review, environment validation, and smoke test | 1 day |
| Test execution and defect reporting | 4-5 days |
| Retesting, regression, RTM, and closure | 2-3 days |
| **Total** | **Approximately 14 working days** |

## 7. Resource Requirements

### Human resources

| Role | Allocation | Responsibility |
|---|---|---|
| QA Engineer | 1 full-time | Test design, data preparation, execution, defects, regression, and reporting |
| QA Lead | Part-time | Review, risk decisions, estimate approval, and test closure review |
| Developer / Integration support | As required | Build support, defect clarification, and fixes |

### Environment and tools

- One touchscreen kiosk or representative landscape test device.
- Supported Chromium-based kiosk browser.
- QA environment connected to test backend services.
- UPI and Card sandbox access.
- Test email inbox.
- Test-document repository and defect-management tool.

## 8. Risks and Mitigation

| Risk | Possible impact | Mitigation |
|---|---|---|
| Payment sandbox is unstable or unavailable | Payment cases become blocked and schedule slips | Confirm sandbox access before execution and prepare approved simulated outcomes where permitted. |
| Coupon, menu, or email test data is unavailable | Related scenarios cannot be completed | Prepare and verify test data before the test cycle begins. |
| QA build fails smoke testing | Detailed execution cannot start | Apply entry criteria and return an unstable build for correction. |
| FRS changes after approval | Existing scenarios and estimates become incomplete | Use change control and re-estimate affected requirements. |
| High defect density or slow fix turnaround | Retesting and regression exceed the estimate | Prioritise P0/P1 flows, track blocked cases, and revise the schedule when contingency is consumed. |

## 9. Cost and Change Control

No monetary cost is stated because approved resource rates were not provided.

`Estimated QA cost = 97 hours × approved blended QA hourly rate`

The estimate shall be reviewed when any of the following changes:

- FRS scope or requirement count.
- Supported kiosk devices, resolutions, or browsers.
- Payment methods or payment provider.
- Required test levels, automation, or non-functional coverage.
- Team size, environment readiness, or delivery schedule.

## 10. Approval

| Stakeholder | Representative | Approval method | Date | Status |
|---|---|---|---|---|
| Prepared by | Kushagra Sinha (QA Engineer) | Email | 25 September 2026 | Completed |
| QA Lead | To be assigned | Email / Jira | - | Pending |
| Project Manager | To be assigned | Email / Jira | - | Pending |
| Product / Business Stakeholder | To be assigned | Email / Jira | - | Pending |
