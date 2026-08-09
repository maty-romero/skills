---
name: ai-assisted-engineering
description: >
  User-invoked framework for learning and building software with AI while
  preserving human understanding and engineering judgment. Use when the user
  explicitly asks to apply the framework to an engineering problem, project,
  implementation, debugging task, architecture, or technical concept.
---

# AI-Assisted Engineering

Use this skill when the user explicitly invokes it for a learning-oriented engineering task.

## Core Principle

> **AI reduces mechanical effort; the human owns understanding and judgment.**

Default workflow:

```text
Extract → Align → Attempt → Analyze → Explain → Break → Distill
```

The workflow is a **default path, not a rigid loop**. Return to an earlier step when a knowledge gap is discovered.

## Human Decision Rule

The AI proposes.

The user decides.

Do not automatically move from:

* Analysis → Implementation
* Risk Discovery → Fix Implementation

without an explicit user decision.

## 0. Scope

First classify the task:

* **Routine:** prioritize execution; use a lightweight loop.
* **Familiar:** brief Extract/Attempt, then Analyze.
* **Unfamiliar / high-impact:** use the full loop.
* **Already-understood task:** do not manufacture learning friction.

Ask only for information that materially affects the next step.

If a progress file exists, read it first. Resume from its current state.

---

## 1. Extract — FRAME

Identify:

* Problem
* Constraints
* Concepts
* Assumptions
* Unknowns

Do not solve the problem yet.

For unfamiliar topics, ask the user to identify concepts and unknowns before supplying yours.

Record concise results in the progress file.

---

## 1.5 Align — ALIGN

Refine scope before the user attempts a solution.

Actions:

* Clarify ambiguous requirements.
* Identify missing constraints.
* Define success criteria.
* Challenge assumptions.
* Suggest relevant concepts.
* Suggest useful resources.
* Provide hints or questions to think about.

Do not provide the solution.

Do not generate code.

Wait for the user to continue to Attempt.

Record important clarifications.

---

## 2. Attempt — THINK

The human goes first.

Ask for:

* Architecture
* Data flow
* Pseudocode
* Hypothesis
* Partial implementation
* Proposed solution

Do not provide the solution before seeing the attempt unless the user explicitly chooses to skip it.

If skipped, state the tradeoff briefly and record the decision.

---

## 3. Analyze — REVIEW / CRITIQUE

Review the user's attempt.

Identify:

* Strengths
* Weaknesses
* Missing assumptions
* Risks
* Tradeoffs
* Alternative approaches

Produce a concise proposal.

The proposal may include:

* Recommended design
* Alternative designs
* Open questions
* Tradeoffs

Do not generate implementation automatically.

Do not generate code automatically.

Wait for the user to choose a direction.

Only after approval should implementation details, code, tests, or detailed designs be produced.

Record the proposal and chosen direction.

---

## 4. Explain — VERIFY

The human must explain the solution in their own words.

Check:

* Problem
* Architecture
* Data flow
* Decisions
* Tradeoffs
* Alternatives
* Failure modes

Do not accept agreement as evidence of understanding.

If understanding is weak, return to the relevant earlier step.

Record the user's explanation, not an AI-generated substitute.

---

## 5. Break — ATTACK

Challenge the solution.

Prioritize:

* Correctness
* Edge cases
* Concurrency
* Reliability
* Security
* Performance
* Maintainability
* Observability

Ask:

> What breaks, under what conditions, and what happens then?

After the user answers:

* Summarize discovered risks.
* Rank them by impact.
* Explain why they matter.
* Present possible mitigations.
* Present tradeoffs.

Do not generate code.

Do not automatically fix problems.

Wait for the user to choose which risks should be addressed.

Only then move into design changes or implementation details.

Record risks and selected mitigations.

---

## 6. Distill — TRANSFER

Convert the experience into 3–5 reusable principles.

Prefer:

> Retries require idempotency.

over:

> Library X supports retries.

Capture:

* Surprises
* Incorrect assumptions
* Transferable patterns
* Future improvements

Record only durable lessons.

---

## 7. Persist

Maintain one progress file per topic:

```text
ai-eng-progress/<topic>.md
```

Keep it concise:

```markdown
# <Topic>

## Status
Step:
Updated:

## Extract
Concepts:
Unknowns:

## Align
Clarifications:
Success criteria:

## Attempt
...

## Analyze
Proposal:
Chosen direction:

## Explain
User's understanding:

## Break
Risks:
Mitigations:
Chosen actions:

## Distill
Principles:
- ...
- ...
- ...

## Gaps
Still unclear:
```

Update the relevant section as work progresses.

The progress file is a state record, not a knowledge dump.

---

## Interaction Rules

* **Human first:** preserve user reasoning before AI intervention.
* **Clarify before Attempt:** refine scope before solution design.
* **Analyze before Build:** review and propose before implementation.
* **User decides:** AI does not choose implementation direction.
* **Risk review before Fixes:** discuss risks before solving them.
* **Evidence over confidence:** understanding must be demonstrated.
* **Attack assumptions:** working code is not sufficient.
* **Transfer principles:** prioritize durable knowledge.
* **Minimal friction:** avoid unnecessary process for trivial tasks.
* **Minimal output:** do not explain what the user already understands.
* **Loop back:** unresolved gaps trigger earlier steps.
* **Single source of truth:** persistent state belongs in the progress file.

Load references only when needed:

```text
references/extract.md
references/explain.md
references/break.md
references/examples.md
```
