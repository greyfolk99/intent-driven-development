# Intent-Driven Development

**Build software from what the user means now — not from whatever the code, plans, specs, or tests happen to say.**

Intent-Driven Development (IDD) is a skill an AI coding agent follows. It keeps one current `INTENT.md`,
reconstructs the relationships among raw opinions before summarizing them, interviews the user around
the choices that actually matter, and makes changed intent propagate down through specification,
implementation, and verification. Engine-neutral: it works with any capable coding agent.

## The one idea

Code, plans, specifications, documentation, and tests are *implementations or evidence* of intent.
Their age or existence does not make them the authority. The authority is the user's current intent,
and the work's job is to keep everything below it in line with it.

```
intent   what, and why — only what the user decided; each decision dated, with its reason
  ↓
spec     how — every line carries the intent it serves; a choice the spec makes alone is marked "Design"
  ↓
code     follows the spec; invents no behavior, option, or name the spec does not have
```

When a lower layer disagrees with a higher one, the higher one wins and the lower one is changed.

## What it is, and is not

- **Is:** a way of working — discover intent by interview, record it, derive a spec, build, verify, and
  reconcile when intent changes. A discipline, not a framework or a tool.
- **Is not:** a license to invent. The agent challenges intent (contradictions, gaps, better options)
  but never fabricates a reason the user did not give, and never edits intent to match the code.

## Core model

- **Why / What / Not / Learnings** describe the current direction. Intent is the *reason* a thing is
  built the way it is; a decision stated without its reason is specification, recorded separately.
- Raw conversation is interpreted as a tree of directions, reasons, examples, alternatives,
  corrections, and durable boundaries before it becomes intent.
- Negative wording is not automatically a `Not`; its role is determined from context.
- The agent may challenge an intent but **never invents a reason the user did not give**; an obvious
  choice is **stated as obvious and taken**, neither decided silently nor asked about.
- Decisions are recorded the moment they are made, dated with their reason, so none is lost.
- Implementation and interviewing proceed together in bounded units, one at a time, with review between.
- Current intent supersedes conflicting code, tests, documents, and earlier decisions.
- A **sanitize** pass reads intent → specification → code for drift and brings it back through the
  interview, not by editing intent to match the code.
- Verification separates mechanical correctness, behavioral correctness, and human-intent alignment.

## How it flows

```
interview (challenge + recommend) → record intent → spec → build → verify → report
                 ↑                                                              │
                 └────────────────────── sanitize (find drift) ────────────────┘
```

## Install

It is a plain skill — a `SKILL.md` with a name and description — and barely depends on the harness,
so it drops into any agent that loads skills. Clone it into that agent's skills directory:

```sh
# Claude Code
git clone https://github.com/greyfolk99/intent-driven-development.git ~/.claude/skills/intent-driven-development
# Codex
git clone https://github.com/greyfolk99/intent-driven-development.git ~/.codex/skills/intent-driven-development
```

The skill is selected when its description matches a software planning, implementation, revision, or
intent-alignment task.

## Contents

- `SKILL.md` — the operating instructions
- `assets/INTENT.template.md` — a starting point for a project's current intent

## License

MIT. See [LICENSE](LICENSE).
