---
name: brainstorming
description: "Mandatory pre-implementation design workflow. Must be fully completed before any implementation skill is invoked."
---

# Brainstorming Design Protocol (State-Driven)

## CORE RULE

This is a strict state machine workflow.

The process MUST reach the terminal state:
→ Invoke writing-plans

It is illegal to:
- Skip a state
- Reorder states
- Exit early
- Implement anything
- Invoke any skill other than writing-plans

---

# STATE MACHINE

Current state must always be explicit internally.

States:

S1 → Explore project context
S2 → Ask clarifying questions
S3 → Propose 2–3 approaches
S4 → Present design sections (incremental validation)
S5 → Write/Update design doc
S6 → Invoke writing-plans (TERMINAL)

Transitions are strictly linear.

You cannot:
- Go to S3 without completing S2
- Go to S4 without S3
- Go to S5 without explicit user approval
- Skip S5
- End in S4

Terminal state is S6 only.

---

# HARD GATE

Until state S6:

- No code
- No scaffolding
- No configs
- No partial implementation
- No frontend-design
- No mcp-builder
- No writing-plans early

If the user tries to implement early:
→ You must redirect back to the current state.

---

# EXECUTION RULES PER STATE

## S1 – Explore Context
- Check files, docs, existing architecture
- Summarize relevant findings
- Then move to S2

---

## S2 – Clarifying Questions
- Exactly ONE question per message
- Prefer multiple choice
- Focus on:
  - Purpose
  - Constraints
  - Success criteria
- Remain in S2 until:
  - All ambiguity resolved
  - You explicitly decide clarity is sufficient

Then transition to S3.

---

## S3 – Propose 2–3 Approaches
- Always present 2–3 viable approaches
- Include:
  - Trade-offs
  - Risks
  - Complexity level
  - Scalability
- Lead with recommended option
- Ask user to choose

Do NOT present final design here.

After user selects → transition to S4.

---

## S4 – Present Design (Sectional)

Design must include sections:

1. Requirements
2. Architecture
3. Components
4. Data Flow
5. Error Handling
6. Testing Strategy

Each section:
- 50–300 words depending on complexity
- After each section:
  Ask: “Does this look correct so far?”

If user says no:
→ Revise and remain in S4

If user says yes to ALL sections:
→ Transition to S5

You must never exit S4 without full approval.

---

## S5 – Write Design Document

Mandatory:

Write to:
docs/plans/YYYY-MM-DD-<topic>-design.md

Design doc must include:
- Context
- Decision rationale
- Chosen approach
- Rejected alternatives
- Final architecture
- Open questions (if any)

No summary-only shortcut allowed.

After writing:
→ Transition to S6

---

## S6 – Invoke writing-plans (TERMINAL)

This is the ONLY allowed skill invocation after brainstorming.

No other skill may be called.

After invoking writing-plans:
Brainstorming is complete.

---

# FAILURE PREVENTION RULES

If:
- User requests code early
- User says “just implement”
- User says “skip design”

You must respond:

"This workflow requires design approval before implementation. Let's continue the current stage."

No exceptions.

---

# Anti-Pattern Prevention

It is forbidden to skip this workflow because a project appears simple.

Even:
- A config tweak
- A helper function
- A rename
- A one-line change

Must complete S1–S6.

---

# END CONDITION

The ONLY valid completion of brainstorming is:

→ writing-plans invoked