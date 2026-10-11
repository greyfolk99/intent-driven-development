# Intent-Driven Development

Intent-Driven Development is a Codex skill for building software from the user's current intent instead of treating existing code, specifications, plans, documentation, or tests as permanent authority.

It keeps one current `INTENT.md`, reconstructs the relationships among raw opinions before summarizing them, interviews the user around consequential judgments, and makes changed intent propagate through implementation and verification.

## Core model

- **Why / What / Not / Learnings** describe the current direction. Intent is the *reason* a thing is built the way it is; a decision stated without its reason is specification, recorded separately.
- Raw conversation is interpreted as a tree of directions, reasons, examples, alternatives, corrections, and durable boundaries before it becomes intent.
- Negative wording is not automatically a `Not`; its role is determined from context.
- Implementation and interviewing can proceed together in bounded units.
- Current intent supersedes conflicting code, tests, documents, and earlier decisions.
- The agent may challenge an intent but never invents a reason the user did not give; an obvious choice is stated as obvious and taken, neither decided silently nor asked about.
- A sanitize pass reads intent → specification → code for drift and brings it back through the interview, not by editing intent to match the code.
- Verification separates mechanical correctness, behavioral correctness, and human intent alignment.

## Install

Clone the repository into your Codex skills directory:

```sh
git clone https://github.com/greyfolk99/intent-driven-development.git ~/.codex/skills/intent-driven-development
```

The skill can then be selected automatically when its description matches a software planning, implementation, revision, or intent-alignment task.

## Contents

- `SKILL.md` — the operating instructions
- `assets/INTENT.template.md` — a starting point for a project's current intent

## License

MIT. See [LICENSE](LICENSE).
