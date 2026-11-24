 FoundIt
PRODUCT REQUIREMENT DOCUMENT (PRD) AND MASTER SPECIFICATION

PRODUCT NAME : FoundIt
DOCUMENT VERSION : 4.1 (SMALL-SCALE ARCHITECTURE)
STATUS : FINAL ARCHITECTURAL SPECIFICATION
AUTHOR : Team Kooq



1. PRODUCT OVERVIEW
 FoundIT is a centralized, campus focused lost-and-found registry, custody ledger and blind ownership verification platform built for university ecosystems. It is designed as a lightweight, mobile and web responsive and RESTful backend service. FoundIT replaces fragmented peer-to-peer social media broadcasts (such as departmental Whatsapp groups and 224-hour status updates) with a persistent, searchable and tamper-evident database connecting item finders, custodians(hostel porters and campus security), and rightful owners.
 To prevernt fraudulent claims. FoundIT enforces a Blind Verification and Custody Tracking Workflow. Publis listings redact sensitive item identifiers and the claimants must pass secret challenge questions set by the finder or custodian before exact pickup coordinates / a single-use handover PIN/QR pass are unlocked.

 2. PROBLEM STATEMENT
 Across university campuses, particularly within student hostels, lecture halls and faculty complexes, the recovery of high value items (student IDs, keys, powerbanks, earbuds and mobile devices) relies on informal social broadcasts. This creates four systematic failures:
   A. Channnel Fragmentation: Lost-and-found notices are scattered across dozens of isolated departmental, level and hostel Whatsapp/Telegram groups, making comprehensive searching impossible.

   B. Information Ephemerality: Whatsapp Status updates expire after 24 houes, and group chat messgaes are rapidly buried under hundreds of unrelated texts.

   C. Custody Blind Spots : Even when a good Samaritan returns an item in, owners have no visibility into which specific hostel, faculty office, or campus security post currently holds the property.

   D. Fraudulent Claims and Privacy Exposure  Posting unredacted photos of found items (e.g dislaying full matric numbers, bank card detials or distinct physical marks) enables bad actors to falsely claim valuables and exposes students personally identifiable information (PII).


3. BUSINESS OBJECTIVES AND SUCCESS METRICS
  FoundIT aims to establish institutional trust as the offical digital lost-and-found utility for the univeristy before scaling to multi-campus and transit verticals.

  Objective 1:
  Centralize Campus Recovery 
  Monthly Active Users and Registry Listing 
  MVP target - > 500 registered student/staff accounts, >150 logged items

  Objective 2:
  Accelerate Item Return
  Median Times-to-Recovery
  MVP Target: less than 48 hours for determinstic items,
  less than 72 houes for general items

  Objective 3: 
  Eliminate Fraudulent Claims
  False-Claim Dispute Rate post-handover
  MVP Target : 0% verified custody dispites, less than 5% rejected claims flagged for abuse.

  Objective 5 :
  Drive Institutional Adoption
  Active Custodian Desks(Hostel and Security)
  MVP Target : more than 80% of cmapus hostel porter posts onboarded.

  Objective 6:
  StreamLine Intake UX
  Median Item Logging Duration
  MVP Target: less than 60 seconds from login to published listing


4. TARGET USERS
  FoundIT serves three primary user roles, enforced via Rola-Based-Access Control (RBAC)

   A. The Owner(CLAIMANT) : Students or staff who have lost an item on campus. They need fast, filtered search capabilities, automated alerts when matching items are logged, and a secure way to prove ownership without exposing details publicly.

   B. The Finder: Students, faculty or campus workers who discover an unattended item. They neeed a sub-60-second logging flow, automated claimant screening so they are not spammed with fake DMs, and the option to offload physical custody to a verified campus drop-off-hub.

   C. The Custodian(Hostel Porter / Campus Security Officer) :   Institutional staff amnaging physical lost-and-found desks.They need a shared desk dashboard to log dropped-off items, track custody transfers, and execute zero-dispute physical handovers backed by a cryptographic/PIN audit log.


5. Stakeholders
  Beyond daily end-users, the following institutional anad technical stakeholders govern deployment, compliance, and adoption:

  A.University Students Affairs Division: Sponsors campus-wide rollout, mandates official usage across students halls of residence, and mediates unresolved ownership disputes.

  B.Campus Security and Patrol Directorate: Operates the central lost and found holding vault, handles escalated/locked out claims (after failed serl-servie attempts), and audits high value gadget recoveries.

  C.Hostel Porters: Manage day to day physical intake and release at residential lodges.

  D.University ICT/Identity Management unit: Provides Institutional email domain validation or matriculation format verification rules.

  E.Product and Engineering Team: Responsible for backend architecture, datbase integrity, data privacy compliance (NDPR), and system maintenance.

6. USER STORIES
      FoundIT has three user stories,
      A. The Owner(CLAIMANR)
         i. Filtered Discvoery: As an owner, I want to filter the active registy by item category(ID card, Electronics, keys, wallet, clothing, other), date found, and campus zone so that i can quickly verify if my item has been logged.

         ii. Proactive Lost Alerts: As an owner, I want to submit a structured "Lost Item" report with tags and zone details so that the backend automatically notifies me via email/in-app alert when a matching "Found Item" is logged

         iii. Blind Claim Submission: As an owner, I want to answer the finder's secret challenge questions and optionally upload corroborating proof(e.g purchase receipt or photo) so that i can prove ownership privately.

         iv. Pickup Pass and Location Unlock : As an approved claimant, I want to view the exact custodian desk, operating hours, and a single 4-digit PIN/QR code so that i can retrieve my item smoothly.
       
       B. The Finder
         i. Rapid Privacy Masked Intake : As a finder, I want to log a found item in under 60 seconds with predefined tags, campus zones, and an uploaded photo  so that i can list an item without exposing sensitive details

         ii. Challenge Prompt Configuration : As a finder, I want to ser 1 to 3 hidden verification questions and wxpected answers when logging an item so that unauthorized users are filtered out automatically.

         iii. Custody Transfer to Desk: As a finder, I want to drop an item at a verified hostel porter's post and transfer digital custody in the app so that i am relieved of personal holding responsibility

       C. The Custodian
         i. Desk Intake and Custody Logging :As a custodian, I want to log items surrendered at my desk directly into my station's digital ledger and accept incoming custody transfers from students.

         ii.PIN/QR Handover Verification: As a custodia, I want to validate a claimant 4-digit pickup PIN before releasing an item so that the system record an immutable audit log of the handover.

         iii. Escalation Resolution : As a campus security officer, I want to review locked claims and mauanlly override approval after inspecting physical ID in person. (where a studnt failed 2 automated finder attempts).

7. Functional Requirements
   01 Authentication and Role Management
      i.   The system shall restrict registration and login to verified institutional email addresses (or verified matriculation/staff IDs) using JWT-based session authentication.

       ii. The system shall enforce three distinct role based access control roles: STUDENT_STAFF (Owner/Finder capabilities), CUSTODIAN (Hostel Porter/Security desk permissions), and ADMIN (System & Security Supervisor).

    02  Item Registry and Intake
       i.Users shall be able to create LOST or FOUND item records containing: title, category, campus_zone, date_time_found, public_description (sanitized), custody_type (WITH_FINDER or AT_CUSTODIAN_DESK), and custodian_location_id (if applicable)

       ii. For FOUND items, the system shall require 1 to 3 VerificationChallenge objects (question_text, expected_answer, match_type: EXACT_DETERMINISTIC or MANUAL_REVIEW).

       iii. Public API responses (GET /api/items) must strictly strip expected_answer, exact finder contact details, and specific room/desk coordinates until a claim reaches APPROVED status.

       iv. When a FOUND item is created, the backend shall run an asynchronous keyword/category/zone matching job against active LOST reports and trigger notifications for matches scoring less than or equal to 70%.

    03. Custody Ledger and State Machine
       i.    Every FOUND item shall follow a strict lifecycle state machine:AVAILABLE to CLAIM_PENDING to CLAIM_APPROVED to RECOVERED (or ARCHIVED after 90 days unclaimed).

       ii. Finders holding an item (WITH_FINDER) shall be able to initiate a custody transfer to a registered CUSTODIAN station. Digital custody updates only after the Custodian confirms physical receipt via a handoff code or desk confirmation endpoint.

       iii.  Every custody change (Intake, Desk Transfer, Claim Approval, Physical Release) shall write an append-only entry to the CustodyAuditLog table containing item_id, actor_id, action, from_location, to_location, and timestamp.

     04 Blind Verification and Claim Engine   
       i.A verified user may submit a claim against an AVAILABLE item by answering all configured challenge questions and optionally attaching a proof image URL.

       ii. Rate-Limiting & Brute-Force Guardrail: A user is restricted to a maximum of 2 claim attempts per item, with a mandatory 15-minute cooldown after the first failed attempt. Upon 2 failed attempts, the user is locked out of self-service claiming for that item and instructed to visit Campus Security for manual verification.

       iii. Deterministic Auto-Approval: For items marked EXACT_DETERMINISTIC (e.g., Student ID Cards or ATM Cards where the finder logs the matriculation number or full name as the secret attribute), the backend shall normalize (trim/lowercase) and compare the claimant’s input. An exact match immediately transitions the claim to APPROVED.

        iv. Manual Review: For descriptive items (MANUAL_REVIEW), the finder or current holding custodian shall view the claimant’s answers side-by-side with the private reference notes and invoke Approve or Reject.

       05. HandOver and Audit Closure

         i.Upon claim approval, the backend shall generate a cryptographically random, single-use 4-digit Pickup PIN (and corresponding QR payload) valid for 72 hours, and unlock the exact pickup location or masked in-app chat for the claimant.

         ii.  At physical handover, the custodian or finder submits the claimant’s 4-digit PIN to POST /api/items/{id}/handover. Upon validation, the item status permanently updates to RECOVERED, removes the listing from public search, and finalizes the audit trail.

8. Non-Functional Requirements

     01. Performance and Latency: Standard REST API read endpoints (GET /api/items, search/filter queries) shall respond in less than 300 ms at the 95th percentile under a concurrent load of 500 campus users.
     02. Security and Data Privacy
       i. All traffic must be encrypted in transit
       ii. Secret challenge answers and pickup PINs must be stored hashed or encrypted at resta dn never return in public Data Transfer Objects. 
       iii. Uplaoded images must strip EXIF GPS metadata upon ingestion to protect finder/owner privacy


     02. Data Integrity and Concurrency: Item claim approvals and custody handovers must execute within ACID-compliant database transactions with row-level locking to prevent race conditions (e.g., two claimants being approved simultaneously for the same item).

     03. Availability and Reliablility; The system shall maintain 99.5% uptime during academic semesters, with automated daily PostgreSQL database backups and point-in-time recovery.

     04. Auditability : The CustodyAuditLog table must be immutable to guarantee tamper-evident institutional records.

     05. Scability and Portability : The backend shall be stateless and containerized, alowing horizontal scaling from a single univeristy deployment to multi-tenant campus instances without schema rewrites.


9. Scope and Priorities (MVP vs POST -MVP)

    Operational Flow & Alerts (P1 Should-Haves)
    After the core loop works, attention shifts to physical custody and proactive matching. A Custodian Desk & Transfer Ledger gives hostel porters an intake dashboard to record when a finder hands over an item, supported by an immutable audit log that tracks every custody change. At the same time, Automated Lost-to-Found Alerts watch incoming reports and trigger email or in-app notifications when keywords or categories line up, saving students from checking the portal endlessly.

    Privacy Polish (P2 Could-Haves)
    Rounding out the roadmap is a Client-Side Photo Blur Tool that lets users paint a quick blur over ID numbers or faces in the browser before uploading an image. While lower in priority than authentication, search, verification, and handover, redacting sensitive details early reduces privacy risks without slowing down the initial launch.


    Out of Scope for MVP 
     i. Automated OCR / AI Image Redaction: Automatic server-side computer vision blurring of matriculation cards (manual blur brush used in MVP).

     ii. Micro-Escrow / Finder Rewards: Financial tipping or bounty payments via Paystack/Flutterwave.

     iii. Native iOS/Android Apps: MVP will ship as a Progressive Web App (PWA) to eliminate app-store friction.
     
     iv. Multi-Tenant Transit/Airport APIs: External municipal or transit integrations (Phase 3 roadmap).


10. Acceptance Criteria
       Each core workflow must pass the following verification tests before MVP sign-off:

       01. Privacy Redaction on Public Feed:

         i.   Given a finder logs a found Student ID card with a secret challenge answer "22/1045",

         ii.  When an unauthenticated or non-approved user queries GET /api/items,

         iii. Then the response payload contains the category, campus zone, and masked description, and does not contain "22/1045", the finder's phone number, or the exact desk room number.

         02. Deterministic Auto-Approval:

         i. Given an AVAILABLE item configured with EXACT_DETERMINISTIC match on "22/1045",

         ii. When a verified student submits a claim with "22/1045",

         iii. Then the claim status immediately updates to APPROVED, the item transitions to CLAIM_APPROVED, and a 4-digit Pickup PIN is returned to the claimant.

        03.Brute-Force Rate Limiting:

         i. Given a claimant submits an incorrect answer on Attempt 1,

         ii. Then the system rejects the claim and blocks Attempt 2 for 15 minutes.

         iii. When the claimant submits a second incorrect answer after the cooldown,

         iv. Then the system locks self-service claiming for that (user_id, item_id) pair (HTTP 429 / 403) and returns Campus Security escalation instructions.

        04.  Custody Transfer Integrity:

         i. Given an item is logged as WITH_FINDER,

         ii. When the finder initiates a transfer to "Samuel Akande Hall Porter's Lodge",

         iii. Then the custody location remains WITH_FINDER (Transfer Pending) until a user with CUSTODIAN role assigned to Samuel Akande Hall confirms receipt, creating an immutable record in CustodyAuditLog.  

        05.  Zero-Dispute Handover Closure:

         i. Given an item is in CLAIM_APPROVED status with PIN 4829,

         ii. When the custodian submits an incorrect PIN 1111, the handover fails (HTTP 400).

         iii. When the custodian submits 4829, the item status changes to RECOVERED, the PIN is invalidated, and the item no longer appears in active search results. 


11. Assumptions and Open Questions
          Key Assumptions
         i. Institutional Cooperation: At least 2–3 major student hostels and the main Campus Security desk will designate staff or student porters to use the Custodian web dashboard during pilot testing.

         ii. Connectivity & Device Access: Students and hostel porters have access to smartphones or desk tablets with basic 3G/4G internet connectivity and modern mobile browsers.

         iii. Good-Faith Finder Baseline: Finders logging descriptive items (MANUAL_REVIEW) will evaluate claimant answers honestly; high-value items (laptops, smartphones) are strongly encouraged to be dropped at Custodian desks rather than held peer-to-peer.

         iv. Email Domain Uniformity: All eligible students and staff possess an active university-issued email address for account verification.

    Open Questions for Stakeholders
         i. Unclaimed Item Retention Policy: What is the exact institutional holding period (e.g., 30, 60, or 90 days) before unclaimed items logged at hostel lodges must be physically transferred to Central Campus Security or auctioned/donated?

         ii. Custodian Device Provisioning: Will hostel porter lodges use personal smartphones with installed PWA shortcuts, or does Student Affairs require shared tablet/desktop terminals at each lodge?

         iii. Matriculation Format Validation: Does the university ICT unit enforce a strict regex pattern for matriculation numbers (e.g., YY/NNNN) that we should validate at signup, or do postgraduate/staff IDs follow separate formats?

         iv. Dispute SLA: When a legitimate owner gets locked out after 2 failed claim attempts (e.g., due to a typo on a descriptive question), what is the target turnaround time for Campus Security to review and resolve the in-person appeal?           