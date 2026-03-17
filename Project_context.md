# Project Context Skill

## Purpose
Synthesize uploaded project documents to produce a structured project context summary — without making assumptions or implicit connections beyond what the documents explicitly state.

## Steps to Follow

### Step 1 — Request Documents
Ask the user to upload any relevant project documents. Accepted formats include:
- Email threads
- PRD (Product Requirements Documents)
- Internal memos, briefs, or strategy docs
- Meeting notes, research summaries, or any other supporting materials

Say: "Please share the relevant files for this project — emails, PRDs, internal documents, or any other materials you have. I'll wait until you've uploaded everything before proceeding."

### Step 2 — Synthesize Documents
Once the user confirms they've shared all documents:
- Read and process each uploaded document carefully
- Cross-reference information across documents where it appears explicitly
- Do NOT infer, assume, or make implicit connections that are not directly supported by the text

### Step 3 — Generate Output
Produce a structured project context summary using the following format:

---

## Project Context Summary

### Project Overview
[High-level description of the project based solely on the documents]

### Key Problem Statements
[List the core problems the project is trying to solve, as stated in the documents]

### Key Users
[List the end users or target audience identified in the documents]

### Key Stakeholders
[List the individuals, teams, or organizations identified as stakeholders]

### Key Metrics
[For each problem statement, list the success metrics or KPIs mentioned in the documents]

| Problem Statement | Key Metrics |
|---|---|
| [Problem 1] | [Metrics from documents] |
| [Problem 2] | [Metrics from documents] |

---

### Step 4 — Data Integrity Rules
- Only use information explicitly stated in the provided documents
- Do not make assumptions, inferences, or draw connections not present in the source material
- If a section cannot be populated from the documents, write: `Data not found in provided documents`
- If information is partial, include what was found and note: `Incomplete — further documentation may be needed`
