---
name: launch-checklist
description: "Takes a PRD as input and generates a comprehensive, severity-rated launch checklist covering product, engineering, design, data, legal, marketing, and ops readiness."
trigger: "/launch-checklist"
version: 1.0
author: sourav5.nayak
output_format: markdown
inputs:
  - name: prd
    required: true
    description: Product Requirements Document for the feature or product being launched
severity_levels:
  - label: P0
    meaning: Launch blocker — must be resolved before go-live
  - label: P1
    meaning: High priority — should be resolved before go-live; exceptions need sign-off
  - label: P2
    meaning: Medium priority — can be resolved in the first week post-launch
  - label: P3
    meaning: Low priority — nice to have; can be tracked as follow-up
checklist_areas:
  - product
  - engineering
  - design
  - data_and_analytics
  - legal_and_compliance
  - marketing_and_comms
  - support_and_ops
  - post_launch
---

# Launch Checklist Skill

## Purpose
Read a PRD and generate a tailored, severity-rated launch checklist across all key functions. Each checklist item is derived from the specific scope, risks, and requirements described in the PRD — not a generic template.

---

## Steps to Follow

### Step 1 — Request the PRD

Say exactly:

> "Please upload the PRD for the feature or product you're launching. I'll generate a tailored launch checklist with severity ratings based on its scope and requirements."

---

### Step 2 — Read and Extract Key Signals

Once the PRD is uploaded, parse it for:

- **Feature scope** — what is being built and what it touches
- **User-facing changes** — UI, flows, notifications, emails
- **Backend / infrastructure changes** — new services, APIs, data models, migrations
- **Integrations** — third-party tools, internal dependencies
- **Data collection or usage** — new events, PII, analytics requirements
- **Legal or compliance flags** — consent, data retention, regulated industries
- **Rollout plan** — phased, flag-gated, full release, A/B test
- **Success metrics** — what needs to be instrumented and monitored

Use these signals to generate checklist items that are specific to this launch — not boilerplate.

---

### Step 3 — Generate the Launch Checklist

Output the checklist in the following format:

---

## Launch Checklist — [Feature / Product Name]

**PRD:** [Title or brief description from the PRD]
**Generated:** [Today's date]

---

### Severity Key

| Severity | Meaning |
|---|---|
| 🔴 P0 | Launch blocker — must be resolved before go-live |
| 🟠 P1 | High priority — should be resolved before go-live; exceptions need explicit sign-off |
| 🟡 P2 | Medium priority — can be resolved within the first week post-launch |
| 🟢 P3 | Low priority — nice to have; track as follow-up |

---

### 1. Product Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 1.1 | [Item derived from PRD] | 🔴 P0 | PM | ☐ |
| 1.2 | [Item derived from PRD] | 🟠 P1 | PM | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Acceptance criteria met and signed off
- Edge cases and error states defined and handled
- Feature flag / rollout configuration confirmed
- Rollback plan documented
- UAT completed with representative users
- PM sign-off obtained

---

### 2. Engineering Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 2.1 | [Item derived from PRD] | 🔴 P0 | Eng | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- All PRD requirements implemented and code reviewed
- Unit, integration, and regression tests passing
- Performance benchmarks met (latency, load)
- Database migrations tested and reversible
- API contracts versioned and backward-compatible
- Security review completed (auth, input validation, data exposure)
- Secrets and configs set in production environment
- Monitoring, alerting, and on-call runbook in place
- Feature flag targeting confirmed in production

---

### 3. Design Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 3.1 | [Item derived from PRD] | 🟠 P1 | Design | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Final designs implemented to spec (pixel QA)
- Responsive / multi-device behaviour verified
- Accessibility standards met (WCAG AA minimum)
- Empty states, loading states, and error states designed and implemented
- Copy finalized and approved
- Design sign-off obtained

---

### 4. Data and Analytics Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 4.1 | [Item derived from PRD] | 🟠 P1 | Data / PM | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- All tracking events from the PRD instrumented and verified in production
- Dashboards and success metric views set up
- Baseline metrics captured pre-launch
- A/B test configured correctly (if applicable) — assignment, exposure logging, holdout
- PII handling reviewed; no sensitive data logged in plain text
- Data pipeline tested end-to-end

---

### 5. Legal and Compliance Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 5.1 | [Item derived from PRD] | 🔴 P0 | Legal / PM | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Legal review completed for new data collection or usage
- Privacy policy / terms of service updated if required
- User consent flows implemented for new data types
- GDPR / CCPA compliance confirmed
- Any regulated industry requirements (HIPAA, PCI, etc.) addressed
- IP / licensing review completed for third-party integrations

---

### 6. Marketing and Comms Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 6.1 | [Item derived from PRD] | 🟠 P1 | Marketing / PM | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Launch announcement drafted and approved (internal + external)
- In-app messaging or onboarding tooltips live
- Email / push notification copy finalized and tested
- Help centre / documentation updated
- Sales and CS teams briefed with talk track
- Social / PR assets ready (if applicable)

---

### 7. Support and Ops Readiness

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 7.1 | [Item derived from PRD] | 🟠 P1 | Support / Ops | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Support team briefed on new feature and likely user questions
- FAQ and support macros written
- Escalation path defined for launch-day issues
- Ops runbook updated for any new operational processes
- Internal tools / admin panel updated to support new feature

---

### 8. Post-Launch Plan

| # | Checklist Item | Severity | Owner | Status |
|---|---|---|---|---|
| 8.1 | Success metrics review scheduled (D+1, D+7, D+30) | 🟠 P1 | PM | ☐ |
| 8.2 | Launch retro scheduled | 🟢 P3 | PM | ☐ |
| ... | | | | |

*Items to cover (as applicable from the PRD):*
- Monitoring cadence agreed and owner assigned
- Rollback trigger criteria defined (what metric threshold = rollback)
- Follow-up backlog items logged
- Launch retro scheduled

---

### Summary

| Area | Total Items | P0 | P1 | P2 | P3 |
|---|---|---|---|---|---|
| Product Readiness | | | | | |
| Engineering Readiness | | | | | |
| Design Readiness | | | | | |
| Data & Analytics | | | | | |
| Legal & Compliance | | | | | |
| Marketing & Comms | | | | | |
| Support & Ops | | | | | |
| Post-Launch | | | | | |
| **TOTAL** | | | | | |

**Launch Recommendation:** [Ready to launch / Conditional — resolve P0s first / Not ready — significant gaps remain]

---

### Step 4 — Generation Standards

- Derive every checklist item from the specific content of the PRD — do not output a generic template
- Assign severity based on launch risk: user-facing breaks and data/legal issues are P0; missing instrumentation or docs are P1–P2
- Omit entire sections that are clearly not applicable to the PRD scope (e.g. no legal section if no new data collection)
- Mark any item as `[Confirm with team]` if the PRD is ambiguous on whether it applies
- Keep item descriptions action-oriented and specific enough for an owner to action without further context
