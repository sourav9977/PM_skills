---
name: release_notes
description: "Takes a PRD, changelog, or list of shipped changes as input and generates polished, audience-specific release notes across three formats: user-facing (in-app / blog), internal (CS, support, sales), and technical (developer / API consumers). Handles features, improvements, bug fixes, breaking changes, deprecations, and known issues."
trigger: "/release_notes"
version: 1.0
author: sourav5.nayak
output_format: markdown
inputs:
  - name: changes
    required: true
    description: "PRD, changelog, git log, Jira/Linear export, or a plain list of what was shipped in this release"
  - name: version
    required: false
    description: "Version number or release name (e.g. v3.2.0, 'Spring 2025 Release'). If not provided, will be inferred or left as a placeholder."
  - name: audience
    required: false
    description: "Target audience: 'all' (default), 'user-facing', 'internal', or 'technical'. If 'all', all three variants are generated."
  - name: product_name
    required: false
    description: "Name of the product or feature area. Used to personalize tone and framing."
release_types:
  - major
  - minor
  - patch
  - hotfix
change_categories:
  - whats_new
  - improvements
  - bug_fixes
  - breaking_changes
  - deprecations
  - known_issues
  - migration_notes
audience_variants:
  - user_facing
  - internal
  - technical
---

# Release Notes Skill

## Purpose
Transform a raw list of shipped changes — from a PRD, git log, Jira export, or bullet list — into polished, publication-ready release notes tailored to three distinct audiences: end users, internal teams (CS, support, sales), and technical consumers (developers, API users). Each variant uses the right tone, depth, and framing for its audience.

---

## Steps to Follow

### Step 1 — Request Inputs

Say exactly:

> "Please share the following to generate your release notes:
>
> 1. **What shipped** *(required)* — paste a PRD, changelog, git log, Jira/Linear export, or a plain bullet list of changes
> 2. **Version number or release name** *(optional)* — e.g. `v3.2.0` or `'May 2025 Update'`; I'll use a placeholder if not provided
> 3. **Audience** *(optional)* — `user-facing`, `internal`, `technical`, or `all` (default: all three)
> 4. **Product or feature area name** *(optional)* — helps me get the tone right
>
> I'll wait until you've shared everything before proceeding."

---

### Step 2 — Classify and Categorize Changes

Once inputs are provided, parse every change and classify it into one of the following categories. A single change may appear in multiple audience variants with different framing:

| Category | Definition |
|---|---|
| **What's New** | Net-new features or capabilities that did not exist before |
| **Improvements** | Enhancements to existing features — faster, easier, more capable |
| **Bug Fixes** | Corrections to broken or incorrect behavior |
| **Breaking Changes** | Changes that alter existing behavior, APIs, or contracts in a way that requires action from users or developers |
| **Deprecations** | Features or APIs that still work but will be removed in a future release |
| **Known Issues** | Bugs or limitations present in this release that are acknowledged and being tracked |
| **Migration Notes** | Step-by-step guidance required to upgrade from the previous version |

Rules for classification:
- If a change touches UX and also changes an API contract, it appears in both user-facing and technical variants
- Breaking changes and deprecations must always be included in technical notes, and surfaced in user-facing notes if they affect end-user workflows
- Bug fixes that were high-visibility user issues should appear in user-facing notes; purely backend fixes belong in technical notes only
- Do not silently omit any change — if uncertain which category fits, choose the closest and flag with `[Confirm category]`

---

### Step 3 — Generate Release Notes

Produce all requested audience variants. Each variant is a complete, standalone document.

---

## Variant A — User-Facing Release Notes

*Audience: end users reading an in-app changelog, blog post, or help centre article. Tone: warm, plain language, benefit-first. No jargon, no internal ticket references, no implementation detail.*

---

## Release Notes — [Product Name] [Version / Release Name]

**Released:** [Today's date]

[One sentence that captures the headline theme of this release — what is the most exciting or important thing that changed?]

---

### ✨ What's New

[For each new feature: lead with the user benefit, not the technical implementation. Use second-person ("You can now…"). Keep each entry to 1–3 sentences. Add a sub-bullet if a brief how-to is useful.]

- **[Feature name]** — [Benefit-first description. What can the user do now that they couldn't before?]
- **[Feature name]** — [Same format]

*(Omit this section if no net-new features shipped)*

---

### Improvements

[Focus on what got better from the user's perspective — speed, reliability, ease of use.]

- **[Area or feature]** — [What improved and why it matters to the user]

*(Omit this section if no improvements)*

---

### Bug Fixes

[Only include fixes that users would have noticed. Frame as what was wrong and what is now correct — not as an internal ticket description.]

- Fixed an issue where [what was happening] when [condition]. [Brief impact: "This affected users who…"]

*(Omit this section if no user-visible bug fixes)*

---

### Heads Up

[Include only if there are breaking changes or deprecations that affect user workflows. Write in plain language with clear action required.]

- **[Change]** — [What changed, who it affects, and what the user needs to do (if anything)]

*(Omit this section if no user-facing breaking changes)*

---

### Known Issues

- **[Issue]** — [Brief description and any workaround available]

*(Omit this section if no known issues)*

---

---

## Variant B — Internal Release Notes

*Audience: customer success, support, sales, and operations teams. Tone: direct and factual. Focus on what changed, what questions customers will ask, what the team needs to know to do their jobs, and any operational impacts.*

---

## Internal Release Summary — [Product Name] [Version / Release Name]

**Released:** [Today's date]
**Release type:** [Major / Minor / Patch / Hotfix]
**Prepared by:** [Author placeholder]

---

### TL;DR for the Team

[3–5 bullet points summarizing the release for someone who has 30 seconds. What shipped, what broke, what customers will ask about, and what the team needs to action.]

---

### What Shipped

| Change | Category | Customer Impact | Likely Support Volume |
|---|---|---|---|
| [Change description] | [New / Improvement / Fix / Breaking] | [High / Medium / Low / None] | [High / Medium / Low] |

---

### Anticipated Customer Questions

For each high-impact change, provide the question customers are likely to ask and the answer the team should give:

**Q: [Customer question]**
> **A:** [Suggested response — accurate, clear, and non-technical enough for CS to use verbatim]

---

### Operational Notes

- **Known issues in this release:** [List any bugs or limitations CS should be aware of, with workarounds]
- **Rollout status:** [Is this a full release, phased rollout, or flag-gated? Who has access?]
- **Escalation path:** [Who to contact if a critical issue is discovered post-launch]

---

### What's Not in This Release

[Brief list of things customers or the team might expect that deliberately did not ship, to prevent confusion]

---

---

## Variant C — Technical Release Notes

*Audience: developers, API consumers, or technical integrators. Tone: precise, complete, no marketing language. Covers API changes, schema changes, performance characteristics, deprecations, and migration paths.*

---

## Technical Release Notes — [Product Name] [Version / Release Name]

**Released:** [Today's date]
**Version:** [Version string, e.g. v3.2.0]
**Previous version:** [Previous version string if known]

---

### Summary of Changes

[2–4 sentences covering the technical scope of this release: what systems were touched, what the net change is for integrators, and whether action is required.]

---

### ⚠️ Breaking Changes

*Action required before upgrading.*

**[Change title]**
- **What changed:** [Exact description of what is different — old behavior vs. new behavior]
- **Affected:** [Which API endpoints, SDK methods, config fields, or data structures are affected]
- **Migration:** [Step-by-step instructions to update integrations. Include code snippets if useful.]
- **Deadline:** [If this is a deprecation being enforced, when does the old behavior stop working?]

*(Omit this section if no breaking changes)*

---

### New APIs and Capabilities

**[Feature or endpoint name]**
- **Description:** [What it does]
- **Endpoint / method:** `[e.g. POST /v2/resource]`
- **Request / response schema:** [Brief description or example]
- **Notes:** [Rate limits, auth requirements, edge cases, or caveats]

*(Omit this section if no new APIs)*

---

### Improvements

- **[Component or API]** — [What changed technically, e.g. p99 latency reduced from Xms to Yms, index added to query Z]

---

### Bug Fixes

| Issue | Affected versions | Fix description |
|---|---|---|
| [Brief issue description] | [e.g. v3.0.0 – v3.1.4] | [What was wrong and how it was resolved] |

---

### Deprecations

*These features still work in this release but will be removed in a future version.*

| Deprecated item | Replacement | Removal target |
|---|---|---|
| [Feature / endpoint / field] | [What to use instead] | [e.g. v4.0.0 or Q3 2025] |

---

### Known Issues

| Issue | Severity | Workaround |
|---|---|---|
| [Description] | [High / Medium / Low] | [Available workaround, or "None — fix targeted for vX.Y.Z"] |

---

### Migration Guide

*(Include only if this is a major or breaking release)*

**Upgrading from [previous version] to [this version]**

1. [Step 1]
2. [Step 2]
3. [Step 3]

---

---

### Step 4 — Generation Standards

- **Audience-first:** every word in each variant must serve its intended reader. Never bleed technical detail into user-facing notes or marketing language into technical notes.
- **Benefit-first for users:** lead with what the user can do, not what was built. "You can now export to CSV" not "CSV export functionality has been added."
- **Evidence-based for internal:** if rollout is phased or limited, say so explicitly — CS teams get burned by giving customers inaccurate access information.
- **Precise for technical:** every breaking change must include old behavior, new behavior, affected surface, and migration path. Incomplete breaking change documentation is a high-severity gap.
- **Omit empty sections:** do not render section headings for categories with no changes (e.g. no "Bug Fixes" section if nothing was fixed).
- **No internal references in user-facing or technical variants:** strip ticket numbers, internal project names, and team-internal jargon.
- **Flag ambiguities:** if a change is too vague to classify or describe accurately, output `[Needs clarification: <specific question>]` rather than guessing.
- **Version placeholder:** if no version is provided, use `[Version TBD]` throughout — do not invent a version number.
