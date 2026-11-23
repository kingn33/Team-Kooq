 FoundIt
PRODUCT REQUIREMENT DOCUMENT (PRD) AND MASTER SPECIFICATION

PRODUCT NAME : FoundIt
DOCUMENT VERSION : 3.0 (SMALL-SCALE ARCHITECTURE)
STATUS : FINAL ARCHITECTURAL SPECIFICATION
AUTHOR : Team Kooq

1. Executive Summary and Market Vision
   Foundit is a centralized, working-focused lost and found registry and ownership verification platform designed for universities.
   It replaces the traditional fragmented social media broadcasts (such as Whatsapp groups and 24 hour statuses) with a searchable, persistent and secure database that cinnects finders, item custodians, and rightful owners


2. The Core Problem 
    In university, particularly across hostel networks and faculties, lost items (student IDs, keys, powerbanks, wallets, gadgets) currently rely on informal peer-to-peer broadcasting. This creates four systematic failures:

    A. Fragmentation - Posts are scattered across dozens of departmental and hostel Whatsapp groups.

    B. Emphemerality - Status updates disappear after 24 hours, and group messages are quickly buried by chat noise.

    C. Custody Blind Spots - Even when an item is found, owners rarely know which specific hostel, porter or security post is holding it.

    D. Fraudulent Claims : Publicly posting full photos of found items allows bad actors to falsely claim valuables that do not belong to them.

3. The Solution
    Foundit introduces a Blind Verification and Custody Tracking workflow.
       A. Persistent Centralized Registry - A single categorized feed where anyone on campus can log  a  lost or found item with permanent visibility until resolved.

       b. Challenge-Based Ownership Verification - Finders or custodians log hidden, identifying attributes(e.g wallpaper on a phone, unique scratch on powerbank, matriculation number digits). Claimants must pass three verification prompts before sensitive details or pickup instructions are unlocked.

       c. Custody and Handoff Ledger - Every logged item tracks its exact physical location and updates in real time if transferred.


4. Target Audience and Primary Value Proposition
    A. Student/Owners - Eliminates the panic of scrolling through dozends of group chats by offering on searchable source of truth with exact pickup coordinates.

    B. Finders - Removes the adminstrative burden of fielding dozends of fake DMs by automating claimant screening.

    C. Hostel Porters and Campus Security - Digitizes physical lost-and-found logbooks, reducing desk congestion and liablilty around high-value-items



5. Maket Vision and Strategic Opportunity
    University campuses represents the ideal wedge market for a trust-based recovery network. Features including...
     A. High foot traffic and daily item loss rates

     B. High smartphone penetration and digital fluency

     C. Existing physical trust anchors that can serve as verified dorp hubs.

     D. Organic viral loops - Every recovered high- value item creats a two highly brand advocates (the finder and the owner).


6.  Long-Term Vision (2-5 Years)
    While starting as a campus utility solving student ID and power bank recovery, the underlying Verified Custody and Micro-Escrow Engine scales naturally into broader commercial verticals.
  
     PHASES:
     Phase 1 - Campus Wedge
     Target Segment- Universities and Student hostels
     
     Phase 2 - Institutional Expansion 
     Target Segment - Multi-Campus Rollout and Event Venues

     Phase 3 -Transit and Civic Infrastructur
     Target Segemnt - Airport, Bus Terminals and Ride-Hailing
     

7.   Market Analysis and Competitive Advantage
    ​Generic social platforms (WhatsApp, Telegram) optimize for broadcast reach, which actively undermines item security. Generic classifieds optimize for transactions, not custody. This product builds a defensible moat through:
    ​   A. Verified Campus Identity: Restricting access via institutional emails or student matriculation verification builds baseline community trust.
    ​   B. Custodian Network Effects: Once hostel porters and campus security desks adopt the platform as their official digital logbook, students are structurally compelled to use the app to retrieve their property.
    ​   C. Structured Verification Data: Proprietary matching algorithms that pair "Lost" reports with "Found" entries using structured metadata rather than unsearchable chat text.


8.   User Stories
        Core User Stories
    ​The platform serves three distinct user personas across the campus ecosystem: The Owner (Claimant), The Finder, and The Custodian (Hostel Porter / Campus Security).
    A.​Persona A -  The Owner (Student who lost an item)
    ​Search & Discovery -  As a student who lost an item, I want to filter the centralized registry by category (e.g., ID Card, Power Bank, Keys), date found, and campus zone so that I can quickly check if my property has been recovered without scrolling through dozens of WhatsApp groups.

    ​Proactive Lost Alerts: As an owner, I want to post a structured "Lost Item" report with automated keyword matching so that I receive an immediate push notification if someone logs a matching found item.
    ​Claim Initiation: As an owner, I want to submit an ownership claim by answering secret verification questions so that I can prove the item belongs to me without publicly exposing my personal details.
    ​Custody Visibility: As an approved claimant, I want to see the exact hostel, porter’s lodge, or security desk holding my item—along with pickup hours and a handover QR/PIN—so that I can retrieve it without confusion.


    ​Persona B: The Finder (Student or staff who found an item)
    ​Frictionless Logging: As a finder, I want to log a found item in under 60 seconds using quick tags and a privacy-masked photo so that I can return it to the owner without dealing with spam messages.
    ​Secret Challenge Creation: As a finder, I want to define 1–3 hidden verification prompts (e.g., "What sticker is on the back?" or "Last 4 digits of matric number") when logging an item so that fake claimants are automatically filtered out.
    ​Custody Transfer (Drop-Off): As a finder who doesn't want to hold onto a stranger's property, I want to drop the item at a verified hostel porter's lodge or security post and transfer digital custody in the app so that I am no longer responsible for coordinating pickup.

    ​Persona C: The Custodian (Hostel Porter / Campus Security)
    ​Intake and Digital Logging: As a hostel porter, I want to log items dropped off at my lodge into a shared hostel dashboard so that students stop crowding the desk asking if their items are there.
    ​Zero-Dispute Handover: As a custodian, I want to verify a student's 4-digit pickup code or QR pass before releasing an item so that I have a timestamped audit trail proving the item went to the rightful owner.



9.  Step-by-Step Ownership Overflow
     To eliminate false claims while keeping sensitive item details hidden from the public feed, every found item goes through a 5-Stage Blind Verification and Handover Pipeline.

            
     A.   Privacy-Masked Intake (Finder or Custodian)
        Public feed hides unique identifiers
        The finder logs the item into the registry by selecting a Category (e.g., Power Bank, Student ID, Keys), Zone Found (e.g., Faculty of Engineering, Jaja Hall), and Current Custody Location (e.g., Held by Finder or Dropped at Mariere Hall Porter’s Lodge).
        a
        Photo Redaction: If an image is uploaded, sensitive text (matriculation numbers, full names, room numbers) is blurred automatically or restricted to a generic silhouette/partial view.
        b
        Verification Prompts: The finder sets 1 to 3 challenge questions based on hidden details only the real owner would know (e.g., "What color is the rubber band wrapped around the power bank?" or "What is the lock-screen wallpaper?").
    B.    Blind Claim Submission (Claimant)
        Rate-limited to 2 attempts per item to prevent brute-forcing
        A student spots a matching listing on the public feed and taps "Claim This Item."
        a - The student is presented with the finder's hidden challenge questions.

        b -   The student submits their text answers (and optionally uploads corroborating proof, such as a receipt, a photo of themselves holding the item, or their matching student ID).
        
        c.  Security Guardrail: Failed attempts trigger a cooldown, and after 2 failed attempts, the claimant is locked out of self-service claiming for that item and must appeal in person at Campus Security.


    C -   Verification Review & Scoring
        Automated exact-match + Custodian/Finder review
        a - Deterministic Items (Student IDs, ATM Cards, Matric-tagged items): If the finder entered the exact matriculation number or full name as a hidden attribute, the system auto-approves the claim immediately upon an exact string match.
        b - Descriptive Items (Keys, Power Banks, Earbuds): The finder or holding custodian reviews the claimant's answers side-by-side against their private notes and taps Approve or Reject.


    D - Custody Unlock & Pickup Pass Generation
        Exact location and contact details remain hidden until this step
        Once the claim is approved:
        a - The item status changes from Available to Claim Approved – Pending Pickup.
        b - The claimant unlocks the exact pickup coordinates (e.g., Moremi Hall Porter's Desk, Ask for Officer Bello) or an in-app masked chat with the finder.
         c -The system generates a single-use 4-Digit Pickup PIN / QR Code for the claimant.


    E - Physical Handover & Audit Closure
        The claimant arrives at the hostel lodge or agreed campus meetup point and presents their 4-Digit PIN / QR Code.
        •
        The custodian or finder enters the PIN in their app to confirm physical release.
        •
        The item is permanently marked Recovered, removed from active search results, and logged in the campus recovery audit trail with timestamps and user IDs.