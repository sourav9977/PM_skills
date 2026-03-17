---
name: prd_critique
description: "Takes a PRD as input and produces a structured critique across 10 dimensions: structural soundness, reasonable assumptions, edge case oversights, dependencies, clarity & testability, prioritization & trade-offs, user research grounding, feasibility signals, stakeholder & alignment gaps, and rollout & risk."
trigger: "/prd_critique"
version: 1.0
author: sourav5.nayak
output_format: markdown
inputs:
  - name: prd
    required: true
    description: Product Requirements Document to be critiqued
rating_scale:
  - label: Strong
    meaning: Dimension is well-addressed; no material gaps
  - label: Adequate
    meaning: Covered but could be sharper; specific improvements noted
  - label: Weak
    meaning: Partial or vague coverage; significant gaps that could cause downstream problems
  - label: Missing
    meaning: Not addressed at all; likely to cause misalignment or rework
critique_dimensions:
  - structural_soundness
  - reasonable_assumptions
  - edge_case_oversights
  - dependencies
  - clarity_and_testability
  - prioritization_and_tradeoffs
  - user_research_grounding
  - feasibility_signals
  - stakeholder_and_alignment_gaps
  - rollout_and_risk
---

# PRD Critique Skill

## Purpose
Evaluate a Product Requirements Document against a rigorous 10-dimension rubric. Surface structural gaps, flawed assumptions, missing edge cases, and hidden risks — producing a critique that is specific to the PRD's content, not generic advice. The output should help a PM significantly strengthen the document before it is handed to engineering or used as a basis for design.

---

## Steps to Follow

### Step 1 — Request the PRD

Say exactly:

> "Please share the PRD you'd like me to critique. Paste the text directly or upload the document. Once I have it, I'll evaluate it across 10 dimensions and give you a detailed, evidence-based critique with specific gaps and recommendations."

---

### Step 2 — Read and Extract Key Signals

Once the PRD is provided, parse it for:

- **Problem framing** — how the problem is defined, for whom, and why now
- **Goal and objective statements** — what success looks like at a strategic and tactical level
- **User definitions** — who the users are, how segmented, and what their stated pain points are
- **Metrics** — both input/leading and output/lagging metrics; success criteria
- **Scope** — current state, future state, and explicit out-of-scope boundaries
- **Assumptions** — explicit and implicit assumptions about users, market, technology, or constraints
- **Requirements** — functional and non-functional, and how precisely they are stated
- **Prioritization** — whether requirements are tiered or ranked in any way
- **Dependencies** — technical, product, team, and external dependencies named in the document
- **Evidence** — whether claims about user needs, market size, or feasibility are backed by data or research
- **Stakeholders** — who is named as owner, reviewer, or decision-maker
- **Rollout** — any phasing, launch strategy, or risk mitigation described

Use these signals to produce a critique that is grounded in the specific text of the PRD — not a generic checklist.

---

### Step 3 — Generate the PRD Critique

Output the critique in the following format:

---

## PRD Critique — [Document Title]

**PRD:** [Title or brief description]
**Critique date:** [Today's date]
**Overall assessment:** [One sentence: the single most important thing to fix before this PRD is ready to ship to engineering]

---

### Rating Summary

| # | Dimension | Rating |
|---|---|---|
| 1 | Structural Soundness | [Strong / Adequate / Weak / Missing] |
| 2 | Reasonable Assumptions | [Strong / Adequate / Weak / Missing] |
| 3 | Edge Case Oversights | [Strong / Adequate / Weak / Missing] |
| 4 | Dependencies | [Strong / Adequate / Weak / Missing] |
| 5 | Clarity & Testability | [Strong / Adequate / Weak / Missing] |
| 6 | Prioritization & Trade-offs | [Strong / Adequate / Weak / Missing] |
| 7 | User Research Grounding | [Strong / Adequate / Weak / Missing] |
| 8 | Feasibility Signals | [Strong / Adequate / Weak / Missing] |
| 9 | Stakeholder & Alignment Gaps | [Strong / Adequate / Weak / Missing] |
| 10 | Rollout & Risk | [Strong / Adequate / Weak / Missing] |

---

### 1. Structural Soundness

*Does the document contain all the elements a well-formed PRD should have? Are they clearly and specifically defined, or present in name only?*

**Rating:** [Strong / Adequate / Weak / Missing]

Evaluate the presence and quality of each structural element. For each, state whether it is present, partially present, or absent — and if present, whether it is specific enough to be actionable:

| Element | Status | Assessment |
|---|---|---|
| Goal (strategic intent) | [Present / Partial / Absent] | [One-line assessment] |
| Objective (measurable outcome) | [Present / Partial / Absent] | [One-line assessment] |
| Context (why now, what has changed) | [Present / Partial / Absent] | [One-line assessment] |
| Problem statement (what is broken) | [Present / Partial / Absent] | [One-line assessment] |
| Importance (why this matters to the business or user) | [Present / Partial / Absent] | [One-line assessment] |
| Value proposition (metrics or goodness it drives) | [Present / Partial / Absent] | [One-line assessment] |
| User definition & pain points | [Present / Partial / Absent] | [One-line assessment] |
| Success metrics | [Present / Partial / Absent] | [One-line assessment] |
| Current state | [Present / Partial / Absent] | [One-line assessment] |
| Future state | [Present / Partial / Absent] | [One-line assessment] |
| Out of scope | [Present / Partial / Absent] | [One-line assessment] |
| Stated assumptions | [Present / Partial / Absent] | [One-line assessment] |

**Top gaps:** [2–4 sentences summarizing the most consequential structural gaps, citing specific sections or language from the PRD]

---

### 2. Reasonable Assumptions

*What assumptions does this document make, explicitly or implicitly? Are they valid? Which ones are most at risk of being wrong, and what would happen if they were?*

**Rating:** [Strong / Adequate / Weak / Missing]

**Explicit assumptions found:**
List each assumption the document explicitly states. For each, assess whether it is reasonable or challengeable:

| Assumption | Reasonable? | How it could be wrong |
|---|---|---|
| [Assumption text] | [Yes / Questionable / Unlikely] | [1–2 sentences on the risk] |

**Implicit assumptions detected:**
List assumptions the document relies on but never states. These are often the most dangerous:

| Implicit assumption | Where it appears in the PRD | Risk if wrong |
|---|---|---|
| [Assumption] | [Section or claim] | [1–2 sentences] |

**Most critical assumption to validate before building:** [1–2 sentences identifying the single assumption whose failure would most undermine the initiative]

---

### 3. Edge Case Oversights

*What critical edge cases does the document fail to address? Focus on cases that would cause user-facing failure, data integrity issues, or engineering rework if discovered late.*

**Rating:** [Strong / Adequate / Weak / Missing]

For each edge case identified, explain why it matters and what the downstream risk is if it is not addressed now:

**Edge case 1: [Short title]**
> *Description:* [What scenario is not handled]
> *Why it matters:* [User or business impact if this hits production unhandled]
> *Suggested resolution:* [What the PRD should specify to close this gap]

**Edge case 2: [Short title]**
> *(same format)*

**Edge case 3: [Short title]**
> *(same format)*

*(Add more if warranted by the PRD's scope — omit this section only if the PRD explicitly and thoroughly addresses edge cases)*

---

### 4. Dependencies

*What dependencies does the document surface, and what critical ones does it fail to mention? Evaluate technical, product, team, and external dependencies.*

**Rating:** [Strong / Adequate / Weak / Missing]

**Dependencies the PRD calls out:**

| Dependency | Type | Assessment |
|---|---|---|
| [Dependency name] | [Technical / Product / Team / External / Data] | [Is it adequately described? Owner named?] |

**Dependencies the PRD fails to call out:**

| Missing dependency | Type | Why it matters |
|---|---|---|
| [Dependency name] | [Technical / Product / Team / External / Data] | [What breaks if this is not coordinated] |

**Dependency risk summary:** [2–3 sentences on the overall dependency risk and the most dangerous unaddressed dependency]

---

### 5. Clarity & Testability

*Are requirements written precisely enough that an engineer can implement them and a QA analyst can verify them? Are acceptance criteria defined?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Ambiguous requirements:** List any requirements that use vague language ("should", "fast", "easy to use", "handle gracefully") without quantification or definition. Quote the exact text.
- **Missing acceptance criteria:** Note where the PRD states what should be built without defining what "done" or "correct" looks like.
- **Conflicting requirements:** Flag any places where two requirements appear to be in tension or contradiction.
- **Non-functional requirements:** Assess whether performance, reliability, scalability, accessibility, and security requirements are addressed — or absent.

[3–5 sentences of specific, evidence-based assessment with direct quotes from the PRD where relevant]

---

### 6. Prioritization & Trade-offs

*Does the PRD make clear what is most important? Does it acknowledge the trade-offs made, and why certain choices were made over alternatives?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Requirements prioritization:** Are requirements tiered (e.g. must-have vs. nice-to-have, P0 vs. P1)? If not, what is the risk of everything being treated as equally important?
- **Explicit trade-offs:** Does the document acknowledge what was deliberately not done, and why? Are the trade-offs reasoned or unexplained?
- **Alternative approaches:** Were alternatives considered? If so, is the rationale for the chosen approach clear?
- **Scope creep risk:** Are there areas where the scope is likely to expand if not explicitly bounded?

[3–5 sentences of specific assessment]

---

### 7. User Research Grounding

*Are user pain points and needs backed by evidence, or are they asserted without support? Does the document reflect a genuine understanding of the user?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Evidence cited:** What user research, data, interviews, or behavioral signals are referenced to support the problem definition and user needs?
- **Assumed vs. validated pain points:** Which pain points are stated as fact without evidence? Which are supported?
- **User segmentation quality:** How specifically are users defined? Are different user segments distinguished, or is "the user" treated as monolithic?
- **Voice of the user:** Is there any direct evidence of users articulating the problem in their own words (quotes, survey data, support tickets)?

[3–5 sentences of specific assessment]

---

### 8. Feasibility Signals

*Has the PRD considered whether the proposed solution is technically and operationally feasible? Are there red flags about scope, complexity, or resource availability?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Technical feasibility:** Is there evidence that engineering has been consulted on the approach? Are there requirements that appear technically risky or under-specified?
- **Scope and complexity:** Does the scope feel proportionate to the timeline and team? Are there hidden complexity sinks?
- **Operational feasibility:** Can the product be supported, monitored, and maintained as described? Are there new operational burdens not accounted for?
- **Constraint acknowledgment:** Are resource, timeline, or technology constraints named, or does the PRD assume infinite capacity?

[3–5 sentences of specific assessment]

---

### 9. Stakeholder & Alignment Gaps

*Are the right people named as owners and decision-makers? Is there evidence of cross-functional alignment, or are there functions likely to be surprised at launch?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Ownership:** Is there a clear DRI (directly responsible individual) for the initiative?
- **Reviewers and approvers:** Are legal, data, security, support, and other relevant functions named where their involvement is required?
- **Missing stakeholders:** Which functions are likely affected by this PRD but not mentioned? (e.g., a feature that affects billing but has no mention of finance)
- **Alignment evidence:** Is there any indication that the PRD has been reviewed or signed off by the key stakeholders, or is it a PM-only document?

[3–5 sentences of specific assessment]

---

### 10. Rollout & Risk

*Does the PRD address how the feature will be launched? Are risks identified and mitigated? Is there a rollback plan?*

**Rating:** [Strong / Adequate / Weak / Missing]

- **Rollout strategy:** Is there a phased rollout, feature flag, or A/B test described? Or does the PRD assume a big-bang launch?
- **Launch risk:** Are the key risks to a successful launch identified (technical, user adoption, operational)?
- **Rollback plan:** If things go wrong post-launch, is there a defined mechanism to revert or mitigate?
- **Communication plan:** Is there a plan for informing users, internal teams, or support of the change?
- **Post-launch monitoring:** Is there a stated plan for observing the feature in production and evaluating success?

[3–5 sentences of specific assessment]

---

### Top 5 Recommendations

The five highest-leverage changes the author should make before this PRD is ready for engineering handoff, in priority order:

**Recommendation 1: [Short title]**
> *Issue:* [Specific gap or problem, with reference to the PRD text]
> *Why it matters:* [What downstream problem this will cause if not fixed]
> *What to do:* [Concrete, specific action to resolve it]

**Recommendation 2: [Short title]**
> *(same format)*

**Recommendation 3: [Short title]**
> *(same format)*

**Recommendation 4: [Short title]**
> *(same format)*

**Recommendation 5: [Short title]**
> *(same format)*

---

### Critique Standards to Follow

- Root every finding in the specific text of the PRD — quote directly when identifying a gap, ambiguity, or flaw
- Do not apply the rubric generically — if a dimension is genuinely well-handled, say so and explain why
- Rate "Strong" only when the dimension is substantively addressed, not just when a section heading exists
- Distinguish between gaps that will cause engineering rework (high severity) and gaps that are nice-to-haves (low severity)
- Where the PRD is ambiguous rather than silent, flag the ambiguity and suggest the specific question to resolve
- Recommendations must be actionable by the PM — not vague advice like "add more detail"
- If a section of the PRD is entirely absent, rate that dimension "Missing" and explain the consequence of that absence
