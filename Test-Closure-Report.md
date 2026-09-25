# Test Closure Report

## Coffee Kiosk POS — Customer Frontend

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

## Table of Contents

- [1. Document Control](#1-document-control)
- [2. Project Information](#2-project-information)
- [3. Test Summary](#3-test-summary)
- [4. Defect Summary](#4-defect-summary)
- [5. Test Coverage](#5-test-coverage)
- [6. Test Metrics](#6-test-metrics)
- [7. Risks and Deviations](#7-risks-and-deviations)
- [8. Exit Criteria Assessment](#8-exit-criteria-assessment)
- [9. Release Recommendation](#9-release-recommendation)
- [10. Lessons Learned](#10-lessons-learned)
- [11. Test Deliverables](#11-test-deliverables)
- [12. Sign-Off](#12-sign-off)

<div class="page-break"></div>

### 1. Document Control

| Field | Details |
|---|---|
| Project | Coffee Kiosk POS |
| Test Scope | Customer-facing kiosk frontend |
| Document Version | 1.0 |
| Reporting Date | 25-Sep-2026 |
| Prepared By | Kushagra Sinha, QA Engineer |
| Reference Documents | FRS v1.0, Test Plan v1.0, Test Estimation Report v1.0 |
| Test Cycle Status | Completed with open defects |
| Release Recommendation | **Not recommended until active P1 defects are fixed and retested** |

### 2. Project Information

This test cycle covered the customer ordering journey for the Coffee Kiosk POS frontend: menu browsing, cart management, checkout, coupon handling, UPI/Card payment redirection, receipt handling, session controls, usability, privacy, reliability, and supported-kiosk compatibility.

Testing followed the approved manual, black-box, and requirement-based approach. The Test Estimation Report planned approximately 97 hours across 14 working days for the complete manual testing cycle.

### 3. Test Summary

| Metric | Count |
|---|---:|
| Test Cases Planned | 48 |
| Test Cases Executed | 48 |
| Passed | 45 |
| Failed | 3 |
| Blocked | 0 |
| Not Executed | 0 |

All planned test cases were executed. Three cases failed because of active defects in coupon validation, receipt email validation, and session timeout handling.

### 4. Defect Summary

| Priority | Logged | Active | Closed |
|---|---:|---:|---:|
| P0 | 1 | 0 | 1 |
| P1 | 2 | 2 | 0 |
| P2 | 1 | 1 | 0 |
| **Total** | **4** | **3** | **1** |

| Defect ID | Summary | Priority | Final Status |
|---|---|---:|---|
| CK-BUG-001 | Expired coupon is accepted and reduces the payable amount | P1 | Assigned |
| CK-BUG-002 | Repeated Pay taps create duplicate payment requests | P0 | Closed |
| CK-BUG-003 | Invalid receipt email shows a false sent confirmation | P2 | Ready for Re-Test |
| CK-BUG-004 | Cart is not cleared after two minutes of inactivity | P1 | Opened |

The P0 duplicate-payment defect was fixed, retested, and closed. The two active P1 defects affect checkout accuracy and customer-session security and must be resolved before release.

### 5. Test Coverage

| Feature / Requirement Group | Requirements Covered | Test Cases | Final Result |
|---|---:|---:|---|
| Food Catalog | 7 | 7 | 7 Passed |
| Cart | 6 | 6 | 6 Passed |
| Checkout | 8 | 8 | 7 Passed, 1 Failed |
| Payment Gateway | 7 | 7 | 7 Passed |
| Receipt | 5 | 5 | 4 Passed, 1 Failed |
| Non-Functional Requirements | 15 | 15 | 14 Passed, 1 Failed |
| **Total** | **48** | **48** | **45 Passed, 3 Failed** |

Each FRS requirement is linked to a test scenario, test case, WBS activity, execution status, and defect where applicable in the RTM. Requirement coverage is 100%.

### 6. Test Metrics

| Metric | Calculation | Result |
|---|---|---:|
| Execution Progress | Executed ÷ Planned × 100 | 100% |
| Pass Percentage | Passed ÷ Executed × 100 | 93.75% |
| Fail Percentage | Failed ÷ Executed × 100 | 6.25% |
| Requirement Coverage | Covered Requirements ÷ Total Requirements × 100 | 100% |
| Defect Closure Percentage | Closed Defects ÷ Total Defects × 100 | 25% |
| Defect Density | Defects ÷ Executed Test Cases | 0.08 |

### 7. Risks and Deviations

- **Checkout risk:** An expired coupon can incorrectly reduce the final payable amount (CK-BUG-001, P1).
- **Session-security risk:** Cart and coupon data can remain visible after the specified two-minute inactivity period (CK-BUG-004, P1).
- **Receipt risk:** Invalid email input can produce a misleading sent confirmation (CK-BUG-003, P2).
- **Resolved payment risk:** Duplicate payment requests caused by repeated Pay taps were retested successfully and closed (CK-BUG-002, P0).
- No test cases were blocked, and the planned customer-frontend scope was completed.
- Automation, API/database validation, penetration testing, and high-volume performance testing remained out of scope as defined in the Test Plan.

### 8. Exit Criteria Assessment

| Exit Criterion | Status | Observation |
|---|---|---|
| All planned test cases executed | Met | 48 of 48 executed |
| All P0 defects closed | Met | 1 of 1 closed |
| No release-impacting active defects | Not Met | Two active P1 defects remain |
| RTM updated with final status | Met | All 48 requirements mapped |
| Test results and defects documented | Met | Test workbook and defect report completed |

### 9. Release Recommendation

The customer frontend is **not recommended for release at this stage**. Engineering should resolve CK-BUG-001 and CK-BUG-004, complete retesting of CK-BUG-003, and run focused regression on checkout, session reset, payment initiation, and receipt handling. Release can be reconsidered after those checks pass and the RTM is updated.

### 10. Lessons Learned

- Coupon validity and total recalculation require focused negative testing because they directly affect the amount charged.
- Repeated-touch protection should be verified early on all order and payment actions.
- Session timeout testing should include cart, coupon, email, and previous-customer data together.
- Controlled sandbox data for Card, UPI, coupon, and email scenarios should be prepared before execution begins.

### 11. Test Deliverables

- Test scenarios
- Feature-wise test cases and execution results
- Requirements Traceability Matrix (RTM)
- Defect report
- Test Closure Report

### 12. Sign-Off

| Stakeholder Role | Representative Name & Title | Approval Method | Date Signed | Final Status |
|---|---|---|---|---|
| Quality Assurance | Kushagra Sinha, QA Engineer | Email | 25-Sep-2026 | QA Closure Complete |
| Engineering | Engineering Lead | Email / Jira | — | Action Required |
| Product Management | Product Manager | Email / Jira | — | Pending |
| Business / Store Operations | Operations Representative | Email | — | Pending |

> QA completion confirms that the planned testing was performed and documented. It does not represent release approval while the active P1 defects remain unresolved.
