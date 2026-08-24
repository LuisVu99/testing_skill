**BUSINESS REQUIREMENTS & KNOWLEDGE BASE**

**Employee Leave Management System**

  --------------------------------------------------------------------------
  **Document     **Version**    **Status**     **Effective    **Owner**
  ID**                                         Date**         
  -------------- -------------- -------------- -------------- --------------
  ELMS-BA-001    2.0            Approved       01 Jan 2026    People
                                                              Operations

  --------------------------------------------------------------------------

Purpose: This document defines the business rules, workflows, data,
policies, permissions, and FAQs for the Employee Leave Management System
(ELMS). It is intentionally structured as a realistic enterprise
knowledge base suitable for testing Retrieval-Augmented Generation (RAG)
systems.

# 1. Document Information

  -----------------------------------------------------------------------
  **Item**                            **Value**
  ----------------------------------- -----------------------------------
  System                              Employee Leave Management System
                                      (ELMS)

  Business Owner                      People Operations

  Primary Users                       Employee, Manager, HR Admin, System
                                      Admin

  Supported Regions                   Vietnam (VN), Singapore (SG),
                                      United States (US)

  Current Policy Version              Leave Policy 2026.1

  Previous Policy Version             Leave Policy 2025.3

  Default Time Zone                   Asia/Ho_Chi_Minh

  Document Classification             Internal
  -----------------------------------------------------------------------

## 1.1 Change History

  -----------------------------------------------------------------------
  **Version**             **Date**                **Change**
  ----------------------- ----------------------- -----------------------
  1.0                     01 Jan 2025             Initial policy and
                                                  workflow

  1.5                     01 Jul 2025             Added carry-over rules
                                                  and probation
                                                  restrictions

  2.0                     01 Jan 2026             Updated annual
                                                  entitlement,
                                                  cancellation window,
                                                  regional rules, and
                                                  approval SLA
  -----------------------------------------------------------------------

# 2. Business Context

ELMS allows employees to view leave balances, submit leave requests,
cancel eligible requests, and receive notifications. Managers review
requests for their direct reports. HR Admin maintains policy
configuration and resolves exceptional cases.

## 2.1 Business Goals

- Reduce manual leave administration.

- Provide a single source of truth for leave entitlement and approval
  status.

- Apply policy rules consistently by employment type, region, and leave
  type.

- Maintain an auditable history of leave requests and approvals.

- Prevent employees from exceeding available entitlement unless an
  approved exception applies.

# 3. Scope

## 3.1 In Scope

- Leave balance

- Leave request and validation

- Manager approval/rejection

- Cancellation

- Carry-over

- Holiday calendar

- Notifications

- Role-based access

- Audit history

- Regional policy rules

## 3.2 Out of Scope

- Payroll calculation

- Expense reimbursement

- Performance management

- Recruitment

- Medical diagnosis or storage of detailed medical records

# 4. User Roles & Permissions

  -------------------------------------------------------------------------------------
  **Role**   **View Own **Submit**   **Approve**   **Configure   **View     **Audit**
             Leave**                               Policy**      Team**     
  ---------- ---------- ------------ ------------- ------------- ---------- -----------
  Employee   Yes        Yes          No            No            No         Own history

  Manager    Yes        Yes          Yes           No            Yes        Team
                                                                            history

  HR Admin   Yes        Yes          Yes           Yes           Yes        All

  System     Limited    No           No            Yes           No         System logs
  Admin                                            (technical)              
  -------------------------------------------------------------------------------------

# 5. Leave Types

  ------------------------------------------------------------------------------
  **Leave Type**  **Code**       **Paid**       **Default         **Notes**
                                                Entitlement**     
  --------------- -------------- -------------- ----------------- --------------
  Annual Leave    AL             Yes            12 days/year      Standard
                                                                  planned
                                                                  vacation

  Sick Leave      SL             Yes            10 days/year      Medical
                                                                  evidence
                                                                  required for
                                                                  \>2
                                                                  consecutive
                                                                  working days

  Special Leave   SP             Yes            Case-based        Marriage,
                                                                  bereavement,
                                                                  or other
                                                                  approved
                                                                  events

  Unpaid Leave    UL             No             No fixed limit    Requires HR
                                                                  approval

  Parental Leave  PL             Yes            Region-specific   Subject to
                                                                  local
                                                                  statutory
                                                                  rules

  Compassionate   CL             Yes            3 days/event      Death of
  Leave                                                           eligible
                                                                  family member
  ------------------------------------------------------------------------------

# 6. Leave Entitlement Policy

## 6.1 Annual Leave Entitlement

  -----------------------------------------------------------------------
  **Employee        **VN**            **SG**            **US**
  Category**                                            
  ----------------- ----------------- ----------------- -----------------
  Full-time         12 days/year      14 days/year      15 days/year
  employee                                              

  Part-time         Prorated by       Prorated          Prorated
  employee          contracted                          
                    working days                        

  Probation         0 days available  0 days available  0 days available
  employee          during probation; during probation  during probation
                    accrued                             
                    entitlement                         
                    starts after                        
                    confirmation                        

  Contractor        Not eligible      Not eligible      Not eligible
  -----------------------------------------------------------------------

Important: Entitlement is associated with the employee's employment
category and region. A change of region takes effect from the effective
transfer date and does not retroactively recalculate approved leave
already taken.

## 6.2 Accrual

- Annual Leave is accrued monthly.

- Full-time Vietnam employees accrue 1.0 day per completed month.

- An employee joining after the first calendar day of a month starts
  accrual from the next complete month unless HR records an approved
  exception.

- Accrued balance cannot be negative.

- Unused balance from the previous year may be carried over only when
  the carry-over rule is satisfied.

## 6.3 Carry-over

  -----------------------------------------------------------------------
  **Condition**                       **Rule**
  ----------------------------------- -----------------------------------
  Standard employee                   Maximum 5 unused Annual Leave days
                                      may be carried to the next year.

  Carry-over expiry                   Carried days expire on 31 Mar of
                                      the following year.

  Probation employee                  No carry-over is created during
                                      probation.

  Employee leaving company            Unused carried-over days are not
                                      automatically converted to cash by
                                      ELMS.

  HR exception                        HR Admin may grant an exception and
                                      must record an audit reason.
  -----------------------------------------------------------------------

# 7. Leave Request Requirements

  -----------------------------------------------------------------------
  **Field**               **Required**            **Rule**
  ----------------------- ----------------------- -----------------------
  Leave Type              Yes                     Must be active and
                                                  available to the
                                                  employee

  Start Date              Yes                     Cannot be after End
                                                  Date

  End Date                Yes                     Cannot be before Start
                                                  Date

  Duration                Calculated              Based on working days
                                                  excluding configured
                                                  holidays

  Reason                  Conditional             Required for Special
                                                  Leave and Unpaid Leave

  Attachment              Conditional             Required for Sick Leave
                                                  longer than 2
                                                  consecutive working
                                                  days

  Approver                Calculated              Based on employee
                                                  reporting line
  -----------------------------------------------------------------------

## 7.1 Validation Rules

- An employee cannot submit a request for dates that are entirely in the
  past.

- Annual Leave requests must be submitted at least 1 calendar day before
  the start date.

- Sick Leave may be submitted after the start date if the employee was
  unable to submit earlier.

- A request cannot overlap another approved or pending request for the
  same employee.

- The requested duration must not exceed the available balance for the
  selected leave type unless the leave type explicitly allows it.

- Weekends and configured public holidays are excluded from working-day
  duration.

# 8. Approval Workflow

Employee submits request → ELMS validates policy → Request enters
Pending Approval → Assigned Manager receives notification → Manager
Approves or Rejects → Employee receives notification → Balance is
committed after approval.

## 8.1 Approval Rules

- Requests are routed to the employee's current direct manager.

- If the employee has no active manager, the request is routed to HR
  Admin.

- Managers cannot approve their own leave requests.

- If the manager is absent, delegation can be configured by HR Admin.

- Approval SLA is 2 business days.

- An overdue request remains Pending; ELMS does not auto-approve it.

## 8.2 Rejection

- Manager must provide a rejection reason.

- Rejected requests do not reduce the employee's balance.

- The employee can submit a new request after rejection.

# 9. Cancellation Policy

- Pending requests may be cancelled by the employee at any time before a
  decision.

- Approved Annual Leave may be cancelled until 17:00 local time on the
  business day before the leave starts.

- Approved Sick Leave cannot be cancelled by the employee after it has
  started.

- HR Admin may cancel an approved request for exceptional operational
  reasons and must provide an audit reason.

- After cancellation, any committed balance is returned automatically.

# 10. Holiday Calendar

The duration calculation uses the employee's assigned regional holiday
calendar.

  -----------------------------------------------------------------------
  **Region**              **Calendar**            **Example 2026
                                                  Holidays**
  ----------------------- ----------------------- -----------------------
  VN                      Vietnam Public Holidays 01 Jan; 30 Apr; 01 May;
                                                  02 Sep

  SG                      Singapore Public        01 Jan; Chinese New
                          Holidays                Year; 01 May; 25 Dec

  US                      United States Company   01 Jan; 04 Jul; 25 Dec
                          Holiday Calendar        
  -----------------------------------------------------------------------

Holiday dates may vary by year and are maintained by HR Admin. ELMS must
use the configured calendar rather than assuming all regions share the
same holidays.

# 11. Special Leave Rules

  -----------------------------------------------------------------------
  **Scenario**            **Entitlement**         **Evidence**
  ----------------------- ----------------------- -----------------------
  Employee's own marriage 3 working days          Marriage registration
                                                  or equivalent document
                                                  if requested by HR

  Death of                3 working days          HR may request
  parent/spouse/child                             supporting document

  Death of sibling        1 working day           HR may request
                                                  supporting document

  Unpaid personal leave   Case-based              Reason required; HR
                                                  approval
  -----------------------------------------------------------------------

Special Leave is not automatically deducted from Annual Leave.

# 12. Notifications

  -----------------------------------------------------------------------
  **Event**         **Recipient**     **Channel**       **Timing**
  ----------------- ----------------- ----------------- -----------------
  Request submitted Employee +        In-app + email    Immediately
                    Manager                             

  Approved          Employee          In-app + email    Immediately

  Rejected          Employee          In-app + email    Immediately

  Request cancelled Manager +         In-app            Immediately
                    Employee                            

  Approval overdue  Manager           Email             After 2 business
                                                        days

  Carry-over expiry Employee          Email             30 days before
  reminder                                              expiry
  -----------------------------------------------------------------------

# 13. Audit & Data Integrity

- Every create, approve, reject, cancel, balance adjustment, and policy
  exception must generate an audit event.

- Audit records contain timestamp, actor, action, request ID, previous
  value where applicable, new value, and reason when required.

- Employees cannot modify audit records.

- HR Admin can view all audit records but cannot delete them.

- System Admin can access technical logs but should not have business
  permission to approve leave.

# 14. Regional Rules

Regional policy is selected from the employee's active work location.
The work location at the time a request is submitted determines the
applicable holiday calendar and entitlement calculation.

  -----------------------------------------------------------------------
  **Rule**          **Vietnam**       **Singapore**     **United States**
  ----------------- ----------------- ----------------- -----------------
  Annual Leave      12                14                15
  baseline                                              

  Sick Leave        10                10                10
  baseline                                              

  Annual Leave      1 calendar day    1 calendar day    1 calendar day
  request lead time                                     

  Carry-over        5 days            5 days            5 days
  maximum                                               

  Carry-over expiry 31 Mar            31 Mar            31 Mar
  -----------------------------------------------------------------------

# 15. Policy Versioning

  -----------------------------------------------------------------------
  **Policy**              **Effective**           **Key Rule**
  ----------------------- ----------------------- -----------------------
  Leave Policy 2025.3     01 Jul 2025             VN annual leave
                                                  baseline = 12 days;
                                                  cancellation allowed
                                                  until 1 business day
                                                  before start

  Leave Policy 2026.1     01 Jan 2026             Same VN baseline;
                                                  explicit regional
                                                  calendars; approval SLA
                                                  = 2 business days;
                                                  carry-over expiry = 31
                                                  Mar
  -----------------------------------------------------------------------

When answering questions about current policy, use Leave Policy 2026.1
unless the user explicitly asks about a historical period. Historical
questions must be answered using the policy version effective during
that period.

# 16. Glossary

  -----------------------------------------------------------------------
  **Term**                            **Definition**
  ----------------------------------- -----------------------------------
  Available Balance                   Approved/accrued entitlement that
                                      can still be used.

  Pending                             Submitted request awaiting
                                      approval.

  Committed Balance                   Balance reserved after a leave
                                      request is approved.

  Carry-over                          Eligible unused entitlement
                                      transferred to the following year.

  Business Day                        Configured working day excluding
                                      weekends and regional holidays.

  HR Exception                        A manually approved deviation from
                                      standard policy.

  Direct Manager                      The active manager assigned to the
                                      employee in the HR hierarchy.
  -----------------------------------------------------------------------

# 17. Frequently Asked Questions

**Q: How many annual leave days does a full-time employee in Vietnam
receive?**

A: Under Leave Policy 2026.1, a full-time Vietnam employee receives 12
Annual Leave days per year.

**Q: Can I carry unused annual leave into next year?**

A: Yes. Up to 5 unused Annual Leave days may be carried into the next
year, and carried days expire on 31 Mar.

**Q: Can a probation employee use annual leave?**

A: No. The employee has 0 available Annual Leave during probation;
accrual begins after confirmation.

**Q: Can I cancel approved annual leave on the morning it starts?**

A: No. Employee cancellation is allowed only until 17:00 local time on
the business day before the leave starts.

**Q: Can Sick Leave be submitted after the leave starts?**

A: Yes, when the employee was unable to submit earlier.

**Q: Who approves my leave if I have no manager?**

A: The request is routed to HR Admin.

**Q: Does ELMS auto-approve overdue leave requests?**

A: No. An overdue request remains Pending.

**Q: Are weekends counted as leave days?**

A: No. Duration is calculated using working days and excludes configured
holidays.

**Q: Is Special Leave deducted from Annual Leave?**

A: No. Special Leave is a separate leave type.

**Q: Can HR change my leave balance?**

A: HR Admin can grant a policy exception or adjustment, but an audit
reason is required.

**Q: Which policy should be used for current questions?**

A: Leave Policy 2026.1, effective from 01 Jan 2026.

**Q: What happens if I transfer from Vietnam to Singapore?**

A: The new regional policy applies from the effective transfer date.
Previously approved leave is not retroactively recalculated.

# 18. RAG Evaluation Notes / Edge Cases

The following facts are intentionally included to support retrieval and
grounding evaluation:

- VN annual leave = 12; SG = 14; US = 15.

- Carry-over maximum = 5 days; expiry = 31 Mar.

- Probation annual leave availability = 0.

- Annual Leave requires at least 1 calendar day lead time.

- Cancellation deadline is 17:00 local time on the business day before
  start.

- Approval SLA is 2 business days and there is no auto-approval.

- Sick Leave may be submitted after start when the employee could not
  submit earlier.

- Special Leave is separate from Annual Leave.

- Historical questions must use the policy version effective during the
  requested period.

- An HR exception requires an audit reason.

Examples of questions that cannot be answered from this document: exact
payroll deduction amounts, an employee's personal balance, the medical
diagnosis required for a specific illness, or a holiday date not
present/configured in the document.

# 19. Sample Records

  ---------------------------------------------------------------------------
  **Employee**   **Region**     **Type**       **Annual        **Manager**
                                               Entitlement**   
  -------------- -------------- -------------- --------------- --------------
  Nguyen An      VN             Full-time      12              Tran Minh

  Le Binh        SG             Full-time      14              Sarah Tan

  John Carter    US             Full-time      15              Emily Reed

  Pham Chi       VN             Probation      0 available     Tran Minh
                                               during          
                                               probation       
  ---------------------------------------------------------------------------

  --------------------------------------------------------------------------
  **Request ID** **Employee**   **Type**       **Dates**      **Status**
  -------------- -------------- -------------- -------------- --------------
  LR-1001        Nguyen An      Annual Leave   10-12 Mar 2026 Approved

  LR-1002        Le Binh        Annual Leave   05-06 Apr 2026 Pending

  LR-1003        John Carter    Sick Leave     14 Mar 2026    Approved

  LR-1004        Pham Chi       Annual Leave   20 Mar 2026    Rejected - not
                                                              eligible
                                                              during
                                                              probation
  --------------------------------------------------------------------------

# 20. Acceptance Criteria

- Leave balance reflects the employee's applicable entitlement, accrual,
  approved usage, and eligible carry-over.

- Invalid date ranges are rejected before submission.

- Overlapping leave requests are rejected.

- Correct regional holiday calendars are used for duration calculation.

- Requests route to the correct manager or HR fallback.

- Approval and rejection actions update request status and balance
  consistently.

- Cancellation returns committed balance when applicable.

- Policy exceptions are auditable.

- Historical policy questions resolve to the correct policy version.

- Users cannot access information outside their permitted scope.
