# BeastMode

**Pressure-test your idea, then build it — carefully.**

BeastMode is a small family of portable agent skills for people who build real
software. Each skill is a single markdown file. They work with Claude Code,
Cursor, opencode, and any agent that reads an instruction file — no setup, no API
key, no dependencies that can silently break.

The skills share one philosophy: **direct, honest, and simple.** They push back
when you're about to make a mistake, decide the small stuff for you, and stay out
of your way. They're equally useful whether you're new or senior — each one reads
how you answer and adapts on its own, with no modes to configure.

## The skills

| Skill | Role | Status |
| --- | --- | --- |
| **BeastMode** (`beastmode`) | **Planning** — sharpen a rough idea into a plan worth building | available |
| **BeastMode Build** (`beastmode-build`) | **Build** — read the plan, build it slice by slice, test it | available |
| **BeastMode Review** (`beastmode-review`) | **Review** — check the implementation, find real bugs, security holes and regressions | available |

The split is the point: understand the idea → settle the decisions → write the
plan → build it → review it, each with a clear responsibility. Nothing tries to do
everything at once.

## Why

Most software goes wrong before and during the build: it gets started before the
problem, the risks and the scope are clear, and then it drifts off the plan while
being built. **BeastMode** spends focused time up front so the build doesn't waste
hours. **BeastMode Build** then builds that plan one working slice at a time,
tested, without running ahead or breaking what already works.

## Install (30 seconds)

Each skill is one file under [`skills/`](./skills). Install only the ones you
want, where your agent looks for skills.

**Claude Code** — drop a skill in as a personal (all projects) or project skill:

```bash
# BeastMode (planning)
mkdir -p ~/.claude/skills/beastmode && curl -sL https://raw.githubusercontent.com/diestelkampconsulting/beastmode/main/skills/beastmode/SKILL.md -o ~/.claude/skills/beastmode/SKILL.md

# BeastMode Build
mkdir -p ~/.claude/skills/beastmode-build && curl -sL https://raw.githubusercontent.com/diestelkampconsulting/beastmode/main/skills/beastmode-build/SKILL.md -o ~/.claude/skills/beastmode-build/SKILL.md

# BeastMode Review
mkdir -p ~/.claude/skills/beastmode-review && curl -sL https://raw.githubusercontent.com/diestelkampconsulting/beastmode/main/skills/beastmode-review/SKILL.md -o ~/.claude/skills/beastmode-review/SKILL.md
```

Then type `/beastmode`, `/beastmode-build` or `/beastmode-review` in your agent.

**Cursor** — save a skill as a rule. Create `.cursor/rules/beastmode.mdc` with
this header, then paste the body of the skill's `SKILL.md` below it:

```md
---
description: Pressure-test an idea before building it, then write a short plan.
alwaysApply: false
---

<paste the body of skills/beastmode/SKILL.md here>
```

Do the same for `beastmode-build` in its own `.mdc` rule.

**opencode and other agents** — anything that reads `AGENTS.md` can use them:
reference or paste a skill's `SKILL.md` into your project's `AGENTS.md`, or into
that agent's skill/command directory.

**Any agent at all** — paste a skill's `SKILL.md` into the chat and say
"follow this."

## How to use it

1. Run **`/beastmode`** on purpose when you have an idea worth taking seriously —
   a feature, a product direction, even a decision. You don't need a worked-out
   plan; producing one is the point. Answer honestly, push back when a question is
   off, and say "I don't know" when you don't. It writes a short plan.
2. Run **`/beastmode-build`** when you have that plan. It reads the plan, confirms
   the slices, then builds them one at a time — testing each slice and protecting
   what already works, checking in with you between slices.
3. Run **`/beastmode-review`** on a built change before it ships. It reviews the
   change against the plan, finds the real bugs, security holes and regressions,
   and ranks them by what actually matters.

## It's working if

- You disagree with something it says. A session with zero pushback from you is a
  session you didn't need.
- You end up somewhere you didn't expect, because a question showed you a decision
  you'd been making without noticing.
- The build grows in small, tested steps you can actually review — not one giant
  untested drop.

## What it deliberately doesn't do

- **BeastMode** plans; it doesn't write production code, and it won't invent an
  architecture document for a small script.
- **BeastMode Build** builds the plan; it doesn't re-plan it (that's BeastMode)
  and it doesn't skip tests to look fast.
- **BeastMode Review** reviews the change; it reports findings and applies a fix
  only when you ask, and it won't pad a review with manufactured concerns.
- None of them settles a question you can only answer by looking at something
  real — for those, they tell you to prototype first.

## License

MIT — see [`LICENSE`](./LICENSE). Hack around with it, adapt it, make it your own.
