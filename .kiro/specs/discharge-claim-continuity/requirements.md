# SwasthyaSeva: Discharge → Claim Continuity Engine — Requirements

## Executive Summary

The Discharge → Claim Continuity Engine transforms hospital discharge from a fragmented, error-prone handoff into a verified, multilingual, claim-ready workflow. It bridges the gap between clinical documentation and insurance reimbursement while ensuring patient comprehension and safety. This system generates patient-safe discharge instructions in English and Hindi, produces claim-ready evidence packets with completeness checks, provides explainable readiness scores, and maintains comprehensive audit trails with mandatory human signoffs for all consequential outputs.

Unlike siloed "AI note generators" or "claims trackers," this wedge delivers end-to-end workflow continuity with verification, governance, and safety boundaries—designed specifically for India's multilingual, low-bandwidth, multi-stakeholder healthcare reality.

## Why This Wedge Matters in India

India's healthcare system faces a critical continuity gap at discharge: patients receive complex medical instructions they cannot understand (language barriers, medical jargon), while hospitals struggle with incomplete claim documentation leading to denials and delayed reimbursements. Rural patients often lack follow-up access, and schemes like PM-JAY require extensive documentation that overwhelms district hospitals. This wedge addresses the reality that discharge is not an endpoint but a critical handoff requiring verification, translation, and structured evidence—turning a moment of maximum vulnerability into a moment of maximum clarity and financial readiness.


## 1. Problem Statement (India-Specific) & Why Unsolved

### The Real-World Friction

**Discharge comprehension gaps:**
- Patients receive discharge summaries in English with medical terminology they cannot understand
- Rural and semi-urban patients (70%+ of India) face language barriers—Hindi, regional languages needed
- Low health literacy means medication instructions, follow-up care, and warning signs are misunderstood
- Result: poor adherence, preventable readmissions, delayed complications, family confusion

**Claims paperwork gaps:**
- Hospitals submit incomplete claim packets to insurers/TPAs, leading to denials, rework, and delayed reimbursements
- Missing documents: discharge summary, investigation reports, consent forms, procedure notes
- Unstructured clinical notes make it hard to extract ICD-10/CPT codes and justify procedures
- District hospitals and PHCs lack dedicated RCM staff, so claims are delayed or abandoned
- PM-JAY and state schemes have strict documentation requirements that overwhelm small facilities

**The continuity break:**
- Clinical teams focus on medical accuracy; billing teams focus on reimbursement codes
- No single system validates "is this discharge packet complete for both patient safety AND claim success?"
- Translation happens ad-hoc (if at all); claim prep happens separately; no verification layer
- Audit trails are weak—who generated what, who approved what, what was the source data?

### Why Existing Tools Are Siloed

- **Clinical documentation tools** (EMRs, note-taking apps): focus on medical records, ignore patient comprehension and claim readiness
- **Billing/RCM tools**: focus on coding and submission, ignore clinical context and patient communication
- **Translation services**: generic, not safety-aware, no medical context, no verification
- **AI note generators**: produce unverified outputs, no audit trail, no human-in-the-loop governance, hallucination risks

**What's missing:** A workflow system that treats discharge as a multi-stakeholder handoff requiring verification, translation, completeness checks, and governance—not just document generation.


## 2. Personas & Beneficiaries

### Patient (Rural + Urban)
**Goals:**
- Understand discharge instructions in their language (Hindi, English, regional)
- Know what medications to take, when, and why
- Recognize warning signs that require immediate care
- Access instructions on low-bandwidth channels (WhatsApp, SMS, PDF)

**Constraints:**
- Limited health literacy; medical jargon is incomprehensible
- Connectivity issues (rural areas, intermittent mobile data)
- Language barriers (English-only documents unusable)
- Time pressure (discharge happens quickly, information overload)

**What the wedge improves:**
- Receives simplified, translated discharge instructions with safety-checked language
- Gets instructions via WhatsApp/PDF in preferred language
- Clear medication schedule, follow-up dates, warning signs in plain language

### ASHA / ANM (Frontline Health Worker)
**Goals:**
- Support post-discharge follow-up and adherence monitoring
- Identify patients needing escalation or re-admission
- Provide counseling and health education in local language

**Constraints:**
- Limited medical training; needs structured guidance
- Serves 1000+ population with minimal resources
- Relies on mobile-first tools, often offline

**What the wedge improves:**
- Receives structured follow-up task lists and counseling scripts (Phase 2)
- Gets patient discharge summary in actionable format
- Clear escalation criteria and contact points

### PHC/CHC Medical Officer
**Goals:**
- Provide quality discharge care with limited time per patient
- Ensure patient comprehension and safety
- Complete documentation for referrals and claims

**Constraints:**
- High patient load (50-100 OPD patients/day)
- Limited support staff for documentation
- Pressure to discharge quickly to free beds

**What the wedge improves:**
- Auto-generated discharge summary draft from clinical notes
- Verification checklist ensures nothing critical is missed
- One-click generation of patient instructions + claim packet


### District Hospital Billing / PM-JAY Desk
**Goals:**
- Submit complete, accurate claims to insurers/TPAs
- Minimize denials and rework
- Track claim status and manage appeals

**Constraints:**
- Limited RCM expertise (1-2 staff for entire hospital)
- Manual document collection from multiple departments
- Scheme-specific requirements (PM-JAY, state schemes, private insurers)
- Time pressure (claims must be submitted within 15-30 days)

**What the wedge improves:**
- Receives claim-ready packet with all required documents
- Completeness checklist highlights missing items before submission
- Readiness score provides confidence level and next actions
- Structured extraction of codes and procedures from clinical notes

### Doctor / Nurse (Discharging Clinician)
**Goals:**
- Provide safe, comprehensive discharge instructions
- Complete documentation efficiently
- Ensure patient understands critical information

**Constraints:**
- Time pressure (multiple discharges per day)
- Documentation burden (discharge summary, prescriptions, instructions)
- Liability concerns (patient safety, medicolegal)

**What the wedge improves:**
- AI-generated discharge summary draft from case notes
- Patient instruction generation with safety verification
- Human signoff workflow ensures clinical accountability
- Audit trail for medicolegal protection

### TPA / Insurer (Claims Adjudication)
**Goals:**
- Process claims efficiently with complete documentation
- Verify medical necessity and appropriateness
- Minimize fraud and abuse

**Constraints:**
- High volume of claims with variable quality
- Incomplete or inconsistent documentation
- Need for clinical context to assess appropriateness

**What the wedge improves:**
- Receives structured claim packets with consistent format
- Complete documentation reduces back-and-forth queries
- Structured extraction makes adjudication faster
- Audit trail provides transparency


## 3. Scope

### In-Scope (Primary Wedge MVP)
- Discharge summary generation from clinical notes (structured extraction)
- Patient-safe discharge instructions in English and Hindi with safety verification
- Claim evidence packet builder with document aggregation
- Completeness checklist for claim submission (missing document detection)
- Readiness score with explainability (why this score, what's missing)
- Human-in-the-loop signoff workflow (doctor for clinical, billing for claim)
- Audit trail for all AI outputs, edits, and signoffs
- Low-bandwidth delivery (WhatsApp, PDF, SMS-friendly formats)
- Safety guardrails (no diagnosis, no autonomous decisions, refusal patterns)

### Explicitly Out-of-Scope
- **Autonomous clinical decisions**: system suggests, humans decide
- **Diagnosis generation**: system summarizes existing diagnoses, does not create new ones
- **Treatment recommendations**: system formats existing treatment plans, does not prescribe
- **Real patient data**: demo uses synthetic or publicly available data only
- **Production deployment**: hackathon demo focuses on proof-of-concept
- **ABDM integration**: future roadmap item, not in MVP
- **Regional languages beyond Hindi**: extensible architecture, but MVP is EN/HI only

### Primary Wedge MVP Definition
The MVP must demonstrate end-to-end workflow:
1. Intake of discharge artifacts (synthetic clinical notes, lab reports, prescriptions)
2. Structured extraction and validation
3. Generation of patient instructions (EN/HI) with safety checks
4. Generation of claim packet with completeness analysis
5. Readiness scoring with explainability
6. Human signoff workflow
7. Audit trail persistence
8. Low-bandwidth delivery simulation


## 4. Wedge Features (MVP)

### 4.1 Discharge Summary Extraction & Structuring
**Description:** Extract structured clinical information from discharge artifacts (doctor notes, case records, lab reports, prescriptions) into a standardized discharge summary format.

**Key capabilities:**
- OCR and text extraction from PDF/image documents
- Structured field extraction: diagnosis, procedures, medications, investigations, follow-up
- Validation of extracted data (completeness, consistency checks)
- Handling of missing or ambiguous information (flag for human review)

**Safety boundaries:**
- Does not generate new diagnoses—only extracts existing ones
- Flags uncertain extractions for human verification
- Maintains source document references for traceability

### 4.2 Patient-Safe Discharge Instructions (Multilingual)
**Description:** Generate simplified, patient-friendly discharge instructions in English and Hindi with safety-verified language.

**Key capabilities:**
- Plain language transformation (medical jargon → patient-friendly terms)
- Translation to Hindi with medical context preservation
- Structured sections: medications, diet, activity, warning signs, follow-up
- Safety-checked phrasing (no absolute guarantees, appropriate disclaimers)
- Readability optimization (short sentences, bullet points, clear formatting)

**Safety boundaries:**
- Uses template-based generation with verified safe phrases
- Avoids diagnostic language or treatment recommendations
- Includes mandatory disclaimers ("consult your doctor if...")
- Requires clinician signoff before delivery

### 4.3 Claim Evidence Packet Builder
**Description:** Aggregate and structure all documents required for insurance claim submission with completeness verification.

**Key capabilities:**
- Document aggregation: discharge summary, lab reports, prescriptions, consent forms, procedure notes
- Structured extraction: ICD-10 codes, CPT codes, procedure details, dates, costs
- Missing document detection (checklist against scheme requirements)
- Document quality checks (readability, completeness, signatures)
- Packet generation in standard format (PDF bundle + structured data)

**Safety boundaries:**
- Does not fabricate missing documents
- Flags incomplete or low-quality documents for human review
- Maintains document provenance and timestamps


### 4.4 Readiness Score & Explainability
**Description:** Provide an explainable score indicating claim submission readiness with actionable next steps.

**Key capabilities:**
- Multi-dimensional scoring: document completeness, data quality, coding accuracy, timeline compliance
- Explainability: show which factors contribute to score (missing docs, incomplete fields, etc.)
- Next actions: prioritized list of tasks to improve readiness
- Confidence intervals: indicate uncertainty in scoring
- Historical benchmarking: compare to similar cases (optional)

**Safety boundaries:**
- Score is advisory, not deterministic
- Clearly communicates limitations and assumptions
- Does not guarantee claim approval
- Requires human review before submission

### 4.5 Human-in-the-Loop Signoff Workflow
**Description:** Mandatory human review and approval for all clinically or financially consequential outputs.

**Key capabilities:**
- Role-based signoff: doctor for clinical content, billing staff for claim packet
- Version control: track drafts, edits, and final approved versions
- Edit capability: humans can modify AI-generated content before approval
- Rejection workflow: ability to reject and request regeneration
- Signoff audit: timestamp, user ID, role, IP address

**Safety boundaries:**
- No AI output is delivered without human approval
- Signoff cannot be bypassed or automated
- Audit trail is immutable and tamper-evident
- Liability remains with human signoff, not AI system

### 4.6 Comprehensive Audit Trail
**Description:** Immutable log of all AI operations, human interactions, and system events for accountability and compliance.

**Key capabilities:**
- Event logging: AI requests, outputs, edits, signoffs, deliveries
- User tracking: who did what, when, from where
- Data lineage: source documents → extractions → outputs
- Error logging: failures, refusals, fallback behaviors
- Retention policy: configurable retention with secure archival

**Safety boundaries:**
- Audit logs are write-only (no deletion or modification)
- PII redaction in logs where appropriate
- Access controls on audit log viewing
- Compliance with data retention regulations


### 4.7 Low-Bandwidth Delivery
**Description:** Deliver outputs via channels accessible to patients and frontline workers in low-connectivity environments.

**Key capabilities:**
- WhatsApp-ready delivery: text-based instructions, PDF attachments (send can be simulated in MVP)
- PDF generation: offline-viewable documents
- Progressive loading: essential information first, details later
- Compression: optimized file sizes for mobile data

**Safety boundaries:**
- For MVP demo, delivery can be simulated (preview + “sent” status) with audit logging of what would be delivered
- SMS fallback, delivery confirmations, and retry automation are Phase 2 enhancements
- No sensitive information in plain SMS (Phase 2 uses secure links)

### 4.8 Safety Guardrails & Refusal Patterns
**Description:** Built-in safety mechanisms to prevent unsafe or inappropriate AI outputs.

**Key capabilities:**
- Prompt injection detection and blocking
- Unsafe request refusal (diagnosis, treatment, prognosis requests)
- Hallucination detection (grounding checks against source documents)
- Confidence thresholds (refuse to generate if confidence too low)
- Safe fallback responses (template-based, human escalation)

**Safety boundaries:**
- System refuses requests outside its scope
- Uncertainty is explicitly communicated
- Missing information triggers human review, not fabrication
- All refusals are logged for analysis


## 5. Secondary Features (Phase 2 - Beyond Demo)

### 5.1 ASHA / Frontline Follow-Up Copilot
**Description:** Post-discharge adherence monitoring and counseling support for community health workers.

**Key capabilities:**
- Follow-up task generation from discharge instructions
- Counseling scripts in local language
- Adherence tracking and escalation triggers
- Home visit checklists
- Telemedicine escalation pathways

**Integration:** Reuses core pipeline (document→extract→validate→generate→signoff→audit)

### 5.2 Scheme Navigator (Public Rule Guidance)
**Description:** Guidance on scheme eligibility, documentation requirements, and application processes for PM-JAY and state schemes.

**Key capabilities:**
- Eligibility checking based on public rules
- Document checklist generation
- Application form assistance
- Disclaimers and limitations (not legal advice)
- Referral to official resources

**Integration:** Reuses verification and checklist components from claim packet builder

**Note:** These features are explicitly secondary and will not be part of the hackathon demo MVP. They demonstrate the extensibility of the core wedge architecture.


## 6. User Stories & Acceptance Criteria

> Hackathon focus: the stories below are the **minimum set** needed to demonstrate the wedge end-to-end. Additional “nice to have” stories are listed as a Phase 2 backlog at the end of this section.

### US-1: Generate Hindi Discharge Instructions with Safety Constraints
**As a** discharging doctor  
**I want to** generate patient-friendly discharge instructions in Hindi  
**So that** my patient can understand their care plan in their preferred language

**Acceptance Criteria:**
- AC-1.1: System extracts clinical information from discharge summary (diagnosis, medications, follow-up)
- AC-1.2: System generates plain-language instructions in Hindi with medical context preserved
- AC-1.3: System applies safety templates (no diagnostic language, appropriate disclaimers)
- AC-1.4: System presents draft to doctor for review and edit
- AC-1.5: Doctor can approve, reject, or modify the instructions
- AC-1.6: Approved instructions are delivered via WhatsApp/PDF
- AC-1.7: Audit log records generation, edits, approval, and delivery

### US-2: Produce Claim-Ready Packet with Missing Document Detection
**As a** hospital billing staff member  
**I want to** generate a complete claim packet with all required documents  
**So that** I can submit claims without delays or denials due to missing documentation

**Acceptance Criteria:**
- AC-2.1: System aggregates all discharge-related documents (summary, labs, prescriptions, consents)
- AC-2.2: System extracts structured data (ICD-10, CPT, dates, costs) from documents
- AC-2.3: System checks completeness against scheme requirements (PM-JAY, private insurer)
- AC-2.4: System generates missing document checklist with priority levels
- AC-2.5: System produces claim packet as PDF bundle + structured JSON
- AC-2.6: Billing staff can review, add missing docs, and regenerate packet
- AC-2.7: Audit log records packet generation, modifications, and submission

### US-3: Calculate Readiness Score with Explainability
**As a** billing staff member  
**I want to** see a readiness score for claim submission  
**So that** I can prioritize which claims to submit and what actions to take

**Acceptance Criteria:**
- AC-3.1: System calculates multi-dimensional readiness score (0-100)
- AC-3.2: System provides breakdown by dimension (completeness, quality, coding, timeline)
- AC-3.3: System explains score factors (e.g., "missing consent form reduces score by 15 points")
- AC-3.4: System provides prioritized next actions (e.g., "obtain surgeon signature on procedure note")
- AC-3.5: System shows confidence interval for score
- AC-3.6: Score updates dynamically as documents are added or corrected


### US-4: Create Audit Trail for Every AI Output and Signoff
**As a** hospital administrator  
**I want to** have a complete audit trail of all AI operations and human approvals  
**So that** I can ensure accountability, compliance, and medicolegal protection

**Acceptance Criteria:**
- AC-4.1: System logs every AI request with input parameters and source documents
- AC-4.2: System logs every AI output with timestamp, model version, and confidence
- AC-4.3: System logs every human edit with user ID, role, timestamp, and changes made
- AC-4.4: System logs every signoff with user ID, role, timestamp, IP address
- AC-4.5: System logs every delivery with channel, recipient, timestamp, status
- AC-4.6: Audit logs are immutable (write-only, no deletion)
- AC-4.7: Audit logs are searchable and exportable for compliance reporting

### US-5: Handle Fallback Behavior for Unsafe or Uncertain Requests
**As a** system  
**I want to** refuse unsafe requests and handle uncertainty gracefully  
**So that** I maintain safety boundaries and avoid generating harmful outputs

**Acceptance Criteria:**
- AC-5.1: System detects and blocks prompt injection attempts
- AC-5.2: System refuses requests for diagnosis, treatment, or prognosis
- AC-5.3: System refuses to generate content when confidence is below threshold
- AC-5.4: System provides clear refusal messages explaining why request was denied
- AC-5.5: System escalates to human review when uncertain
- AC-5.6: System uses safe fallback templates when generation fails
- AC-5.7: All refusals and fallbacks are logged for analysis

### US-6: Extract Structured Data from Discharge Documents
**As a** billing staff member  
**I want to** automatically extract ICD-10 codes, CPT codes, and procedure details from clinical notes  
**So that** I don't have to manually read through lengthy documents

**Acceptance Criteria:**
- AC-6.1: System performs OCR on scanned/image documents
- AC-6.2: System extracts diagnosis codes (ICD-10) from discharge summary
- AC-6.3: System extracts procedure codes (CPT) from procedure notes
- AC-6.4: System extracts dates (admission, discharge, procedures)
- AC-6.5: System extracts costs and billing items
- AC-6.6: System flags uncertain extractions for human verification
- AC-6.7: System maintains source document references for each extracted field


### US-7: Deliver Instructions in WhatsApp-ready Format (MVP)
**As a** patient  
**I want to** receive my discharge instructions in a WhatsApp-friendly format  
**So that** I can access them easily on my mobile phone even with limited connectivity

**Acceptance Criteria:**
- AC-7.1: System generates a WhatsApp-ready text version (short sections, bullets, clear dates)
- AC-7.2: System generates an offline-viewable PDF attachment (mobile-friendly size)
- AC-7.3: Demo may simulate sending (preview + “sent” status) without requiring a live WhatsApp integration
- AC-7.4: Audit log records delivery intent and the content version delivered

### US-8: Validate Completeness Against Scheme Requirements
**As a** billing staff member  
**I want to** check if my claim packet meets PM-JAY documentation requirements  
**So that** I can avoid claim denials due to missing documents

**Acceptance Criteria:**
- AC-8.1: System loads scheme-specific requirements (PM-JAY, state schemes, private insurers)
- AC-8.2: System checks for required documents (discharge summary, consent, investigation reports)
- AC-8.3: System checks for required fields (patient ID, procedure codes, dates, signatures)
- AC-8.4: System generates checklist with status (present, missing, incomplete)
- AC-8.5: System prioritizes missing items by impact on claim approval
- AC-8.6: System provides guidance on how to obtain missing items
- AC-8.7: System updates checklist dynamically as documents are added

### Phase 2 backlog (not required for hackathon MVP)
Examples of valuable follow-on stories (intentionally deferred):
- Offline-first queuing/sync, SMS fallback automation, and delivery confirmations
- Deeper lineage visualization and rich provenance UI
- Batch processing and end-of-month workflows
- Template management UI and per-hospital customization workflows
- Advanced outcome tracking and readiness score calibration against real-world claim outcomes


## 7. Non-Functional Requirements

### 7.1 Safety & Grounding Requirements
- **NFR-7.1.1:** All AI outputs must be grounded in source documents with citations
- **NFR-7.1.2:** System must refuse requests outside defined scope (diagnosis, treatment, prognosis)
- **NFR-7.1.3:** System must detect and block prompt injection attempts
- **NFR-7.1.4:** System must provide confidence scores for all extractions and generations
- **NFR-7.1.5:** System must use template-based generation for safety-critical content
- **NFR-7.1.6:** System must require human signoff for all consequential outputs
- **NFR-7.1.7:** System must maintain safe fallback responses for all failure modes

### 7.2 Auditability & Compliance
- **NFR-7.2.1:** All AI operations must be logged with immutable audit trail
- **NFR-7.2.2:** Audit logs must include: timestamp, user, role, input, output, confidence, source documents
- **NFR-7.2.3:** Audit logs must support configurable retention policies (demo retains for hackathon duration; production policies vary)
- **NFR-7.2.4:** Audit logs must be searchable and exportable
- **NFR-7.2.5:** System must provide document lineage and provenance tracking
- **NFR-7.2.6:** System must support compliance reporting (NABH, DPDP Act)
- **NFR-7.2.7:** System must log all access to patient data for audit purposes

### 7.3 Privacy & Security (Privacy-by-Design)
- **NFR-7.3.1:** All patient data must be encrypted at rest (AES-256)
- **NFR-7.3.2:** All patient data must be encrypted in transit (TLS 1.3)
- **NFR-7.3.3:** System must enforce multi-tenant isolation (hospital_id scoping)
- **NFR-7.3.4:** System must redact PII in logs and monitoring
- **NFR-7.3.5:** System must implement data minimization (only collect necessary data)
- **NFR-7.3.6:** System must support data retention policies and secure deletion
- **NFR-7.3.7:** System must enforce role-based access control (RBAC)
- **NFR-7.3.8:** System must implement rate limiting to prevent abuse

### 7.4 Offline & Low-Bandwidth Tolerance
- **NFR-7.4.1:** System must produce outputs that work on low bandwidth (short WhatsApp-ready text + compressed PDFs)
- **NFR-7.4.2:** System should prioritize essential content first (meds, follow-up, warning signs)
- **NFR-7.4.3:** Offline queuing/sync and SMS fallback are Phase 2 enhancements (not required for MVP demo)


### 7.5 Performance & Scalability
- **NFR-7.5.1:** MVP should complete an end-to-end discharge→claim workflow in “seconds to a minute” for typical synthetic cases
- **NFR-7.5.2:** System should support asynchronous processing for heavy document workloads (demo can simulate async status)
- **NFR-7.5.3:** Post-hackathon pilots validate scale targets; MVP emphasizes correctness, safety, and auditability

### 7.6 Reliability & Availability
- **NFR-7.6.1:** MVP should degrade safely (clear errors + fallbacks) when AI/services are unavailable
- **NFR-7.6.2:** AI service failures must trigger safe fallbacks
- **NFR-7.6.3:** System must retry failed operations with exponential backoff
- **NFR-7.6.4:** System must provide graceful degradation when services are unavailable
- **NFR-7.6.5:** System must alert administrators of critical failures
- **NFR-7.6.6:** System must support disaster recovery (backup/restore)
- **NFR-7.6.7:** Multi-region resilience is a future hardening item (beyond demo)

### 7.7 Cost Controls & Resource Management
- **NFR-7.7.1:** System must enforce per-user and per-hospital rate limits (values tuned during pilots)
- **NFR-7.7.2:** System must enforce per-hospital quotas (values tuned during pilots)
- **NFR-7.7.3:** System must track and report token usage and costs
- **NFR-7.7.4:** System must implement caching to reduce AI API calls
- **NFR-7.7.5:** System must use async processing for non-urgent operations
- **NFR-7.7.6:** System must provide cost dashboards and alerts
- **NFR-7.7.7:** System must support cost allocation per hospital (tenant billing)

### 7.8 Multilingual Support
- **NFR-7.8.1:** System must support English and Hindi in MVP
- **NFR-7.8.2:** System architecture must be extensible to additional languages
- **NFR-7.8.3:** System must preserve medical context in translations
- **NFR-7.8.4:** System must validate translation quality (back-translation checks)
- **NFR-7.8.5:** System must support Unicode and Devanagari script
- **NFR-7.8.6:** System must handle mixed-language content (code-switching)
- **NFR-7.8.7:** System must provide language preference settings per user


## 8. Data Policy

### 8.1 Synthetic & Public Data Only (Hackathon Constraint)
- **DP-8.1.1:** Demo must use only synthetic patient data or publicly available datasets
- **DP-8.1.2:** No real patient identifiers (names, IDs, contact info) in demo
- **DP-8.1.3:** Synthetic data must be realistic but clearly marked as synthetic
- **DP-8.1.4:** Public datasets must be properly attributed and licensed
- **DP-8.1.5:** Demo must include disclaimer: "Synthetic data for demonstration only"

### 8.2 Data Retention & Deletion
- **DP-8.2.1:** Audit logs: configurable retention (demo retains for hackathon duration; production may require multi-year retention)
- **DP-8.2.2:** Patient data: retention per hospital policy (configurable)
- **DP-8.2.3:** AI outputs: retain with audit trail for accountability
- **DP-8.2.4:** Temporary data: delete after processing (OCR intermediates)
- **DP-8.2.5:** Support for "right to be forgotten" (secure deletion)
- **DP-8.2.6:** Backup retention: 90 days for disaster recovery
- **DP-8.2.7:** Archived data: encrypted and access-controlled

### 8.3 PII Redaction & Minimization
- **DP-8.3.1:** Redact PII in logs and monitoring (names, IDs, contact info)
- **DP-8.3.2:** Minimize data collection (only collect what's necessary)
- **DP-8.3.3:** Anonymize data for analytics and reporting
- **DP-8.3.4:** Use tokenization for sensitive identifiers where possible
- **DP-8.3.5:** Implement field-level encryption for highly sensitive data
- **DP-8.3.6:** Provide data access controls (who can see what)
- **DP-8.3.7:** Log all access to sensitive data for audit

### 8.4 Data Residency & Sovereignty
- **DP-8.4.1:** Patient data must be stored in India (AWS India regions)
- **DP-8.4.2:** AI processing must occur in India or approved regions
- **DP-8.4.3:** Backups must be stored in India
- **DP-8.4.4:** No cross-border data transfer without explicit consent
- **DP-8.4.5:** Comply with DPDP Act data localization requirements
- **DP-8.4.6:** Document data flows for compliance reporting
- **DP-8.4.7:** Support for on-premises deployment (data never leaves hospital)

### 8.5 Limitations & Disclaimers
- **DP-8.5.1:** System is not a medical device and does not provide medical advice
- **DP-8.5.2:** System outputs require human review and approval
- **DP-8.5.3:** System does not guarantee claim approval or reimbursement
- **DP-8.5.4:** System is not a substitute for professional medical judgment
- **DP-8.5.5:** System accuracy depends on quality of input data
- **DP-8.5.6:** System may make errors—human verification is mandatory
- **DP-8.5.7:** System is subject to AWS service availability and limitations


## 9. Metrics & Evaluation

### 9.1 Operational Metrics
- **M-9.1.1:** Time to generate discharge packet (baseline vs. with system)
- **M-9.1.2:** Time to complete claim packet (baseline vs. with system)
- **M-9.1.3:** Number of discharges processed per day
- **M-9.1.4:** Number of claim packets generated per day
- **M-9.1.5:** System uptime and availability
- **M-9.1.6:** API response times (p50, p95, p99)
- **M-9.1.7:** Error rates and failure modes

### 9.2 Quality Metrics
- **M-9.2.1:** Readiness score accuracy (predicted vs. actual approval rate)
- **M-9.2.2:** Completeness score (% of required documents present)
- **M-9.2.3:** Extraction accuracy (ICD-10, CPT codes vs. ground truth)
- **M-9.2.4:** Translation quality (back-translation BLEU score)
- **M-9.2.5:** Readability score (Flesch-Kincaid grade level)
- **M-9.2.6:** Grounding accuracy (% of claims verified in source docs)
- **M-9.2.7:** Human edit rate (% of AI outputs modified before approval)

### 9.3 Safety Metrics
- **M-9.3.1:** Hallucination detection rate (% of ungrounded claims caught)
- **M-9.3.2:** Guardrail block rate (% of unsafe requests blocked)
- **M-9.3.3:** Red-team success rate (% of adversarial prompts that bypass safety)
- **M-9.3.4:** Refusal rate (% of requests refused due to safety/uncertainty)
- **M-9.3.5:** Fallback trigger rate (% of requests using safe fallbacks)
- **M-9.3.6:** Audit trail completeness (% of operations logged)
- **M-9.3.7:** Security incident rate (unauthorized access attempts)

### 9.4 Outcome Metrics
- **M-9.4.1:** Claim approval rate (with system vs. baseline)
- **M-9.4.2:** Claim denial rate due to missing documents (with system vs. baseline)
- **M-9.4.3:** Average claim cycle time (submission to settlement)
- **M-9.4.4:** Patient comprehension score (survey-based proxy)
- **M-9.4.5:** Patient satisfaction with discharge instructions
- **M-9.4.6:** Readmission rate (30-day, 90-day)
- **M-9.4.7:** Staff satisfaction and adoption rate

### 9.5 Cost Metrics
- **M-9.5.1:** AI API costs per discharge
- **M-9.5.2:** AI API costs per claim packet
- **M-9.5.3:** Total platform costs per hospital per month
- **M-9.5.4:** Cost savings from reduced claim denials
- **M-9.5.5:** Cost savings from reduced staff time
- **M-9.5.6:** ROI calculation (savings vs. platform costs)
- **M-9.5.7:** Token usage and optimization opportunities


## 10. Risks & Mitigations

### 10.1 Hallucination & Accuracy Risks
**Risk:** AI generates incorrect or fabricated information in discharge instructions or claim packets.

**Impact:** Patient safety (wrong medication instructions), claim denials (incorrect codes), medicolegal liability.

**Mitigations:**
- **MIT-10.1.1:** Grounding verification—all outputs must cite source documents
- **MIT-10.1.2:** Confidence thresholds—refuse generation if confidence too low
- **MIT-10.1.3:** Human-in-the-loop—mandatory review and signoff
- **MIT-10.1.4:** Template-based generation for safety-critical content
- **MIT-10.1.5:** Continuous evaluation with synthetic test cases
- **MIT-10.1.6:** Red-team testing for adversarial inputs
- **MIT-10.1.7:** Feedback loop from human corrections

### 10.2 Bias & Fairness Risks
**Risk:** AI exhibits bias in language, recommendations, or processing based on patient demographics.

**Impact:** Inequitable care, discrimination, regulatory violations.

**Mitigations:**
- **MIT-10.2.1:** Diverse synthetic training data (age, gender, language, region)
- **MIT-10.2.2:** Bias testing across demographic groups
- **MIT-10.2.3:** Multilingual support to avoid language-based exclusion
- **MIT-10.2.4:** Human oversight to catch and correct biased outputs
- **MIT-10.2.5:** Regular fairness audits and reporting
- **MIT-10.2.6:** Transparent documentation of known limitations
- **MIT-10.2.7:** Feedback mechanism for bias reporting

### 10.3 Prompt Injection & Security Risks
**Risk:** Malicious users inject prompts to bypass safety guardrails or extract sensitive data.

**Impact:** Data breach, unsafe outputs, system abuse.

**Mitigations:**
- **MIT-10.3.1:** Input sanitization and validation
- **MIT-10.3.2:** Prompt injection detection patterns
- **MIT-10.3.3:** Structured outputs (JSON schema enforcement)
- **MIT-10.3.4:** Rate limiting and abuse detection
- **MIT-10.3.5:** Audit logging of all suspicious requests
- **MIT-10.3.6:** AWS WAF for API protection
- **MIT-10.3.7:** Regular security testing and penetration testing


### 10.4 Operational & Cost Risks
**Risk:** AI API costs spiral out of control; system becomes too expensive to operate.

**Impact:** Financial unsustainability, service disruption.

**Mitigations:**
- **MIT-10.4.1:** Per-user and per-hospital rate limits
- **MIT-10.4.2:** Token budgets and cost tracking
- **MIT-10.4.3:** Caching and result reuse
- **MIT-10.4.4:** Async processing for non-urgent operations
- **MIT-10.4.5:** Cost dashboards and alerts
- **MIT-10.4.6:** Graceful degradation when quotas exceeded
- **MIT-10.4.7:** Pricing model that aligns costs with value

### 10.5 Connectivity & Availability Risks
**Risk:** System unavailable in low-connectivity rural areas; AWS region outages.

**Impact:** Workflow disruption, delayed discharges, staff frustration.

**Mitigations:**
- **MIT-10.5.1:** Offline queuing and sync when online
- **MIT-10.5.2:** Progressive loading and caching
- **MIT-10.5.3:** SMS fallback for critical notifications
- **MIT-10.5.4:** Multi-region deployment (future)
- **MIT-10.5.5:** Graceful degradation to manual workflows
- **MIT-10.5.6:** Clear offline/online status indicators
- **MIT-10.5.7:** On-premises deployment option (future)

### 10.6 Adoption & Change Management Risks
**Risk:** Staff resist using the system; prefer manual workflows.

**Impact:** Low adoption, wasted investment, no outcome improvement.

**Mitigations:**
- **MIT-10.6.1:** User-centered design with staff input
- **MIT-10.6.2:** Training and onboarding programs
- **MIT-10.6.3:** Gradual rollout with pilot hospitals
- **MIT-10.6.4:** Clear value demonstration (time saved, outcomes improved)
- **MIT-10.6.5:** Feedback loops and continuous improvement
- **MIT-10.6.6:** Champion identification and peer support
- **MIT-10.6.7:** Integration with existing workflows (not replacement)

### 10.7 Regulatory & Compliance Risks
**Risk:** System violates DPDP Act, healthcare regulations, or insurance scheme rules.

**Impact:** Legal liability, fines, loss of trust, service shutdown.

**Mitigations:**
- **MIT-10.7.1:** Privacy-by-design architecture
- **MIT-10.7.2:** Data residency in India (AWS India regions)
- **MIT-10.7.3:** Comprehensive audit trails
- **MIT-10.7.4:** Regular compliance audits
- **MIT-10.7.5:** Legal review of disclaimers and terms
- **MIT-10.7.6:** Transparent documentation of data practices
- **MIT-10.7.7:** Engagement with regulators and industry bodies


## 11. USP & Competitive Differentiation

### Why Continuity + Verification + Audit is Disruptive

**Traditional "LLM Note Generator" Approach:**
- Generates discharge summaries or claim forms in isolation
- No verification of completeness or accuracy
- No audit trail or accountability
- No multilingual patient communication
- No integration between clinical and billing workflows
- High hallucination risk, no grounding checks
- No human-in-the-loop governance

**Traditional "Claims Tracker" Approach:**
- Focuses only on claim submission and status
- Ignores clinical documentation quality
- No patient communication component
- No verification of document completeness before submission
- Reactive (tracks problems) rather than proactive (prevents problems)

**SwasthyaSeva Discharge → Claim Continuity Engine:**
- **End-to-end workflow:** Clinical documentation → Patient communication → Claim preparation in one system
- **Verification-first:** Completeness checks, grounding validation, confidence scoring before any output
- **Governance-native:** Human signoff, audit trails, version control built into every step
- **Multilingual & accessible:** Patient-safe instructions in Hindi/English via WhatsApp/SMS
- **Explainable:** Readiness scores with clear reasoning, next actions, source citations
- **India-specific:** PM-JAY/state scheme requirements, low-bandwidth tolerance, rural-urban reality
- **Safety-bounded:** No diagnosis, no autonomous decisions, refusal patterns, template-based safety

### Hard-to-Copy Advantages

1. **Workflow integration depth:** Not a point solution but a continuity engine that bridges clinical, patient, and financial workflows
2. **Verification architecture:** Multi-layer validation (grounding, completeness, confidence, human signoff) is complex to replicate
3. **India-first design:** Multilingual, low-bandwidth, scheme-specific requirements are not afterthoughts but core design
4. **Governance model:** Audit trails, human-in-the-loop, and accountability are built-in, not bolted-on
5. **Synthetic data methodology:** Demonstrates feasibility without real patient data, enabling rapid iteration and testing


## 12. Demo Scope & Beyond Demo

### Demo Scope (Hackathon MVP)

**What will be demonstrated end-to-end:**

1. **Intake & Extraction:**
   - Upload synthetic discharge artifacts (clinical notes, lab reports, prescriptions)
   - OCR and structured extraction (diagnosis, medications, procedures, codes)
   - Validation and missing information detection

2. **Patient Instructions Generation:**
   - Generate plain-language discharge instructions in English
   - Translate to Hindi with medical context preservation
   - Apply safety templates and disclaimers
   - Present for doctor review and signoff

3. **Claim Packet Generation:**
   - Aggregate all discharge documents
   - Extract structured data (ICD-10, CPT, dates, costs)
   - Generate completeness checklist against PM-JAY requirements
   - Calculate readiness score with explainability
   - Present for billing staff review and signoff

4. **Delivery Simulation:**
   - Generate WhatsApp-ready message format
   - Generate PDF for offline viewing
   - Simulate delivery confirmation

5. **Audit Trail:**
   - Display audit log of all operations
   - Show document lineage and provenance
   - Demonstrate signoff tracking

**What will be mocked vs. real:**
- **Real:** AWS Bedrock (LLM), Textract (OCR), Translate, S3, Lambda, Aurora PostgreSQL
- **Real:** Guardrails, structured extraction, validation logic, scoring algorithms
- **Mocked:** WhatsApp delivery (simulated, not actual Twilio integration)
- **Mocked:** Claim submission to insurer (stops at packet generation)
- **Synthetic:** All patient data, clinical notes, documents

**Demo flow:**
1. System admin uploads synthetic discharge case
2. System extracts and validates data
3. Doctor reviews and approves patient instructions (EN/HI)
4. Billing staff reviews and approves claim packet
5. System shows readiness score and next actions
6. System displays audit trail
7. System simulates delivery to patient


### Beyond Demo (Future Roadmap)

**Phase 2: ASHA Follow-Up Copilot (3-6 months post-hackathon)**
- Post-discharge task generation for community health workers
- Counseling scripts in regional languages
- Adherence monitoring and escalation triggers
- Integration with existing ASHA workflows
- Mobile-first, offline-capable interface

**Phase 3: Scheme Navigator (6-9 months post-hackathon)**
- Eligibility checking for PM-JAY and state schemes
- Document checklist generation for scheme applications
- Public rule guidance with disclaimers
- Integration with scheme portals (where APIs available)
- Patient-facing scheme education content

**Phase 4: ABDM Consent & Interoperability Accelerator (9-12 months post-hackathon)**
- ABDM consent workflow automation
- Health record packaging for ABDM sharing
- Consent audit trail and revocation
- Integration with ABDM sandbox and production
- Interoperability testing with ABDM-compliant systems

**Phase 5: Advanced Analytics & Continuous Improvement (12+ months)**
- Claim outcome tracking and denial pattern analysis
- Readiness score calibration based on actual outcomes
- Predictive models for claim approval probability
- Benchmarking across hospitals and schemes
- Feedback loop for continuous quality improvement

**Production Hardening (Parallel Track):**
- Real WhatsApp integration via Twilio
- Multi-region deployment for high availability
- Advanced security hardening (penetration testing, SOC 2)
- Regulatory compliance certification (NABH, ISO 27001)
- On-premises deployment option for large hospitals
- Integration with existing HIS/EMR systems
- Mobile app for doctors and billing staff
- Advanced reporting and analytics dashboards


## 13. Responsible AI & Safety Case

### Safety Boundaries (Non-Negotiable)

**What the system DOES:**
- Extracts and structures existing clinical information
- Generates patient-friendly explanations of existing care plans
- Translates medical content with context preservation
- Aggregates and validates documentation completeness
- Provides decision support (readiness scores, checklists)
- Maintains audit trails and accountability

**What the system DOES NOT DO:**
- Generate new diagnoses or differential diagnoses
- Recommend treatments or medications
- Make autonomous clinical decisions
- Provide prognosis or outcome predictions
- Replace human clinical judgment
- Guarantee claim approval or reimbursement
- Operate without human oversight

### Guardrails & Verification Layers

**Layer 1: Input Validation**
- Sanitize and validate all inputs
- Detect and block prompt injection attempts
- Enforce structured input schemas
- Rate limiting and abuse detection

**Layer 2: Grounding & Confidence**
- Verify all outputs against source documents
- Calculate confidence scores for extractions
- Refuse generation when confidence too low
- Cite sources for all claims

**Layer 3: Safety Templates**
- Use pre-approved templates for patient instructions
- Enforce mandatory disclaimers
- Avoid diagnostic or prescriptive language
- Validate readability and comprehension

**Layer 4: Human-in-the-Loop**
- Mandatory review for all consequential outputs
- Edit capability before approval
- Rejection and regeneration workflow
- Signoff audit trail

**Layer 5: Audit & Monitoring**
- Immutable audit logs
- Anomaly detection and alerting
- Regular safety audits
- Red-team testing

### Escalation to Human

**System escalates to human when:**
- Confidence below threshold (< 70%)
- Missing critical information
- Ambiguous or conflicting data
- Unsafe request detected
- Grounding verification fails
- Unusual pattern detected
- User explicitly requests human review

### Accountability Model

**Liability remains with humans:**
- Doctor is accountable for clinical content (signoff required)
- Billing staff is accountable for claim accuracy (signoff required)
- Hospital is accountable for data quality and compliance
- System provider is accountable for technical reliability and safety guardrails

**System provides:**
- Tools to support human decision-making
- Verification and validation assistance
- Audit trails for accountability
- Transparency and explainability

### Continuous Safety Improvement

**Feedback loops:**
- Human corrections feed back into evaluation
- Denial patterns inform completeness checks
- Safety incidents trigger guardrail updates
- User feedback improves templates and workflows

**Regular testing:**
- Synthetic test cases for regression testing
- Red-team testing for adversarial inputs
- Bias testing across demographics
- Grounding accuracy evaluation
- Hallucination detection testing

---

**End of Requirements Document**
