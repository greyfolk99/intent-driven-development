---
name: intent-driven-development
description: Develop software from the user's current intent rather than treating existing code, plans, specifications, documentation, or tests as authority. Use when discovering what to build, implementing or revising behavior, resolving consequential product or technical choices, or checking whether a result matches what the user meant.
---

# Intent-Driven Development

Treat current human intent as the direction of the work. Code, plans, specifications, documentation, and tests are implementations or evidence of that intent; their age or existence does not make them authoritative.

## 1. Keep one current intent

Maintain the project's intent in `INTENT.md`, using [assets/INTENT.template.md](assets/INTENT.template.md) unless the project already has an equivalent format.

Organize it around four questions:

- **Why** — whose problem matters, what outcome is sought, and how the underlying belief can be checked;
- **What** — observable behavior, user flows, and important cases;
- **Not** — boundaries, exclusions, and quality or risk limits;
- **Learnings** — concise evidence that changes confidence or the current direction.

Record whether the intent is a `seed`, `exploring`, `clarified`, or `dropped`. Unknowns stay explicit; do not manufacture certainty merely to advance the status.

`INTENT.md` describes the current position, not the conversation that produced it. When understanding changes, rewrite the affected Why, What, or Not. Keep only the evidence still needed to understand the current position in Learnings; version history preserves the path.

Do not put architecture, code structure, or a task plan into intent unless it is itself a user-retained constraint. Derive implementation artifacts from intent when they are useful. A long-lived specification is optional: create one when coordination, assurance, or handoff benefits exceed its maintenance cost.

## 2. Reconstruct the intent tree before summarizing

An intent contribution usually combines an opinion about the situation with a direction it suggests. Do not flatten a conversation into independent requirements sentence by sentence. First build a temporary semantic tree that relates each statement to the decision it addresses.

Distinguish among:

- a root opinion or proposed direction;
- a reason, observation, or evidence supporting it;
- an explanation or restatement of the same point;
- an example or counterexample;
- an expected consequence or inference;
- a competing alternative;
- a correction or replacement of an earlier view;
- a durable boundary the result must respect.

When several opinions appear, place them as branches under the relevant question, compare what each direction would produce, and determine which branch represents the current intent. A later sentence may explain an earlier statement rather than add another rule. A correction may replace its parent rather than coexist with it.

Classify a statement by its role in context, not by its grammatical form. Negative wording belongs in **Not** only when it expresses a durable prohibition, exclusion, or limit. A phrase such as “X seems better; in other words, we should not do Y” may be a contrast or rationale supporting X, not a second independent constraint. Do not duplicate one idea as both a positive direction and a negative rule.

If two plausible trees would lead to materially different outcomes, present the interpretations and ask which is intended. Otherwise, synthesize the supported direction without preserving conversational scaffolding. The tree is a working model; `INTENT.md` holds the resolved current intent, not the raw tree or transcript.

## 3. Turn a request into consequences before code

Before committing to an approach, carry it forward into a plausible implementation. Consider the observable behavior, business rules, state and data changes, permissions, failure paths, external effects, operating burden, and future change cost that are relevant to the request.

Use that projection to find decisions the user may not have realized they were making. A proposed solution is evidence about the desired result, not an architecture to copy uncritically. Surface a choice when materially different implementations would produce consequences the user may care about.

Do not ask about incidental choices whose consequences fall within already delegated judgment.

## 4. Interview around judgment, not ceremony

For each consequential unresolved choice, explain in language the user can judge:

- the likely outcome if the current direction is implemented;
- the meaningful alternatives;
- the advantages, costs, and risks of each;
- the recommended choice and the reason for it.

The user decides which judgments to retain. The agent investigates technical facts, challenges proposals when their implementation consequences conflict with the desired result, and owns the decisions the user delegates.

Adapt the interview to the user and the change:

- go deeper when a choice has substantial business, security, safety, data, operational, or future-change consequences;
- go broader when it affects several actors, workflows, components, services, or external systems;
- ask less where the user has delegated the choice and the consequences are contained.

Neither a command nor a tentative idea is automatically complete intent. Interpret it in context, project its consequences, and ask only where a missing judgment could materially change the result.

## 5. Let discovery and implementation interleave

Do not require the entire project to reach `clarified` before learning through prototypes or implementing a coherent part whose important choices are understood.

Work in bounded units. Implement resolved portions, then revisit intent when repository evidence or concrete implementation reasoning reveals a new consequential choice. Continue unrelated resolved work when doing so does not pre-empt that choice.

Implementation is allowed to teach; it is not allowed to silently decide newly visible user-owned judgments.

## 6. Make changed intent replace old authority

When current intent differs from an earlier decision:

1. State the difference between the old and current intent.
2. Rewrite `INTENT.md` so only the current direction remains active.
3. Inspect broadly for code, tests, documentation, data assumptions, and workflows coupled to the old intent.
4. Explain the affected surface, risks, and unresolved judgments.
5. Change every relevant artifact, rather than preserving the old design because it already exists or is cheaper to patch around.

Use independent read-only inspection when it helps reveal hidden impact, but synthesize its findings against the current intent before acting.

## 7. Verify at three levels

Keep three questions distinct:

1. **Mechanical** — does the result build, type-check, run, and pass applicable automated checks?
2. **Behavioral** — do observable behavior, important failures, state changes, and side effects match the current rules?
3. **Intent** — does the result match what the user meant, including assumptions and tradeoffs that automation cannot decide for them?

Tests are evidence for selected behavior, not frozen intent. When a test conflicts with changed intent, determine whether the implementation is wrong or the recorded expectation is obsolete.

For human review, present a temporary business-level view generated from the current implementation: what actors can do, what state or side effects change, what is deliberately absent, and which claims are verified versus inferred. Do not preserve this report as a competing source of truth unless the user explicitly wants a maintained artifact.

Finish only when the implementation and its supporting artifacts reflect the current intent, automated evidence is proportionate to the risk, and remaining uncertainty is visible to the user.
