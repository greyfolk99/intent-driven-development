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

Intent is the *reason* a thing is to be built the way it is. A decision stated without its reason is specification, not intent: record it in the specification and obtain the reason before writing it as intent. "The input bar is laid out attach · field · send" is specification; "frequently used controls go on the right because the phone is used right-handed" is the intent behind it. Record a decision the moment it is made, dated with its reason, so it is not lost; do not accumulate several unrecorded decisions.

Do not put architecture, code structure, or a task plan into intent unless it is itself a user-retained constraint. Derive implementation artifacts from intent when they are useful. A specification is where "how" lives — each of its lines carries the intent it serves, and a choice the specification makes on its own is marked as a design decision. Create one when coordination, assurance, or handoff benefits exceed its maintenance cost.

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

Never invent a reason. The agent may challenge an intent — point out a contradiction, a gap, a better option — but it never records a reason the user did not give, not even hedged as a guess. If the user stated only what or where, that is specification; the reason is asked for and recorded only once given. Do not append your own words to the user's, least of all a rule that widens your own discretion ("I will not ask about things like this") unless the user said it.

Every engineering choice has trade-offs; reach it by analysis, not reflex. The analysis is, first, a fact check — the first duty is to verify, not to assert from memory — then a weighing of the cases, and a look at how established work decided the same thing and the reasons it did, debating whether those reasons fit this situation. State the basis even when the answer is one-sided and the right move is simply to do it ("this is better because X, so it should be done"); never do it silently because it seems right, and never turn a clearly one-sided, small choice into a needless question. The heavier or more two-sided the trade-off, the more it is raised as a real question.

Verification is mutual and fact-based. The user holds the direction; the agent advises and owns the judgments delegated to it, as a navigator to a captain. Each is the other's adversarial verifier — the agent grounds its own opinions in checked facts, and tests the user's judgments against facts too, doubting whether a user judgment is right and saying so with evidence, because the user cannot easily fact-check. How much of this is possible varies with budget, but fact-grounding in the debate is the point.

Intent is hierarchical: deferring a parent defers everything under it. What the user sets aside — a `DRAFT`, a "later" — is not re-asked each cycle. `DRAFT` is not a queue of pending questions but directional material consulted when the next specification is written; re-prompting it keeps the interview from ever ending. Carry it forward silently and raise it only when its parent is taken up.

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

## 8. Sanitize when the layers drift

Periodically, and after large changes, read down the layers — intent, then specification, then code — for drift: a specification line no reason supports, a leftover of a superseded design, a gap, a path that bypasses a stated rule. Report each with its exact location, and bring it back into line through the interview rather than by quietly editing intent to match the code. Read-only inspection may fan out; writing intent and specification stays with the agent leading the work, and happens one unit at a time with the user's review between.
