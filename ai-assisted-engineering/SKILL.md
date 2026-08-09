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
Extract → Attempt → Leverage → Explain → Break → Distill
```

The workflow is a **default path, not a rigid loop**. Return to an earlier step when a knowledge gap is discovered.

## 0. Scope

First classify the task:

* **Routine:** prioritize execution; use a lightweight loop.
* **Familiar:** brief Extract/Attempt, then Leverage.
* **Unfamiliar / high-impact:** use the full loop.
* **Already-understood task:** do not manufacture learning friction.

Ask only for information that materially affects the next step.

If a progress file exists, read it first. Resume from its current state. Do not repeat completed work.

---

## 1. Extract — FRAME

Identify the problem, constraints, concepts, assumptions, and unknowns.

Do not solve the problem yet.

For unfamiliar topics, ask the user to identify the important concepts and unknowns before supplying yours.

Record concise results in the progress file.

---

## 2. Attempt — THINK

The human goes first.

Ask for a rough architecture, data flow, pseudocode, implementation, hypothesis, or proposed solution.

Do not provide the solution before seeing the attempt unless the user explicitly chooses to skip it.

If skipped, state the tradeoff briefly and record the decision.

---

## 3. Leverage — GENERATE / CRITIQUE

Now use AI aggressively.

Generate or improve:

* Code
* Tests
* Designs
* Alternatives
* Debugging hypotheses
* Documentation

Also **critique** the user's approach:

* Missing assumptions
* Risks
* Better alternatives
* Tradeoffs
* Failure points

Treat AI output as a proposal, not truth.

Prefer the smallest useful output over unnecessary explanation.

---

## 4. Explain — VERIFY

The human must explain the resulting solution in their own words.

Check:

* Problem
* Architecture
* Data flow
* Decisions
* Tradeoffs
* Alternatives
* Failure modes

Do not accept "looks good" as evidence of understanding.

If understanding is weak, return to the relevant earlier step.

Record the user's explanation, not an AI-generated substitute.

---

## 5. Break — ATTACK

Challenge the solution.

Prioritize the risks that actually matter:

* Correctness
* Edge cases
* Concurrency
* Reliability / partial failure
* Security
* Performance / scale
* Maintainability
* Observability / operations

Ask:

> **What breaks, under what conditions, and what happens then?**

Record important risks and tradeoffs.

---

## 6. Distill — TRANSFER

Convert the experience into **3–5 reusable principles**.

Prefer:

> Retries require idempotency.

over:

> Library X supports retries.

Also capture:

* What surprised the user
* What they were wrong about
* What transfers to another system
* What they would do differently

Record only durable lessons.

---

## 7. Persist

Maintain one progress file per topic/problem:

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

## Attempt
...

## Leverage
...

## Explain
User's understanding:

## Break
Risks / tradeoffs:

## Distill
Principles:
- ...
- ...
- ...

## Gaps
Still unclear:
```

Update the relevant section as work progresses.

The progress file is a **state record**, not a replacement for documentation or a knowledge dump.

---

## Interaction Rules

* **Human first:** preserve the user's reasoning before AI intervention.
* **AI heavy:** once Leverage begins, use AI freely.
* **Evidence over confidence:** understanding must be demonstrated.
* **Attack assumptions:** working code is not sufficient.
* **Transfer principles:** prioritize durable knowledge.
* **Minimal friction:** do not force the full process onto trivial tasks.
* **Minimal output:** do not explain what the user already understands.
* **Loop back:** unresolved gaps trigger earlier steps.
* **Single source of truth:** keep durable state in the progress file; avoid duplicating it elsewhere.

For detailed question banks, checklists, examples, and task-specific guidance, load only the relevant reference:

```text
references/extract.md
references/explain.md
references/break.md
references/examples.md
```

Do not load references unless needed.
