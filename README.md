# BeastMode

**Pressure-test your idea before you build it.**

BeastMode is a small, portable agent skill. You give it a rough idea; it asks the
sharp questions, proposes sensible defaults, pushes back where you're about to
make a mistake, and writes a short, honest plan you can build from. Then it stops.

It works with Claude Code, Cursor, opencode, and any agent that reads a markdown
instruction file. One file, no setup, no API key, no dependencies that can
silently break.

## Why

Most software goes wrong before the first line of code: it gets built before the
problem, the risks, and the scope are clear. BeastMode spends thirty focused
minutes up front so the build doesn't waste thirty hours. It is deliberately
**not** an architect, a project manager, a QA engineer, or a code generator — it
plans, and hands off to build.

## What makes it different

- **Equally useful for beginners and pros.** It reads how you answer and adapts
  on its own — more explanation when you're unsure, more speed when you're not.
  No modes to configure.
- **Highest-stakes questions first**, 2–3 at a time. Never a wall of questions.
- **Decides the small stuff for you** and says so, so you only spend attention on
  choices that are hard to reverse.
- **Knows when talking won't help** and tells you to build a throwaway instead.
- **Honest.** It challenges over-engineering, feature creep, and bloated stacks —
  and agrees in one line when you're right.
- **Simple by design.** A weekend script gets a checklist, not a five-phase
  process.

## Install (30 seconds)

BeastMode is a single file: [`SKILL.md`](./SKILL.md). Put it where your agent
looks for skills.

**Claude Code** — drop it in as a personal or project skill:

```bash
# personal (all projects)
mkdir -p ~/.claude/skills/beastmode && curl -sL https://raw.githubusercontent.com/diestelkampconsulting/beastmode/main/SKILL.md -o ~/.claude/skills/beastmode/SKILL.md

# or per project
mkdir -p .claude/skills/beastmode && cp SKILL.md .claude/skills/beastmode/SKILL.md
```

Then type `/beastmode` in your agent.

**Cursor** — save the skill as a rule. Create
`.cursor/rules/beastmode.mdc` with this header, then paste the body of
`SKILL.md` below it:

```md
---
description: Pressure-test an idea before building it, then write a short plan.
alwaysApply: false
---

<paste the body of SKILL.md here>
```

Invoke it by asking Cursor to "use the beastmode rule" or by referencing it with
`@beastmode`.

**opencode and other agents** — anything that reads `AGENTS.md` can use it:
reference or paste the contents of `SKILL.md` into your project's `AGENTS.md`,
or into that agent's skill/command directory.

**Any agent at all** — paste the contents of `SKILL.md` into the chat and say
"follow this."

## How to use it

Start it on purpose, in a fresh conversation, when you have an idea worth taking
seriously — a feature, a product direction, even a decision. You don't need a
worked-out plan; producing one is the point. Answer honestly, push back when a
question is off, and say "I don't know" when you don't. The quality of the plan
depends on the quality of your answers.

## It's working if

- You disagree with something it says. A session with zero pushback from you is a
  session you didn't need.
- You end up somewhere you didn't expect, because a question showed you a decision
  you'd been making without noticing.
- You could defend every choice in the final plan to someone who wasn't there.

## What it deliberately doesn't do

- It doesn't write production code. It plans, then hands off.
- It doesn't invent an architecture document for a small script.
- It can't settle questions you can only answer by looking at something real —
  for those it tells you to prototype first.

## The family

BeastMode is the planning step of a clean, three-part workflow with clear
responsibilities. Each is a separate skill, so nothing gets muddled.

| Skill | Role | Status |
| --- | --- | --- |
| **BeastMode** | Planning — sharpen the idea, surface risks, write the plan | available |
| **BeastMode Build** | Read the plan, build it slice by slice, test it | planned |
| **BeastMode Review** | Check the implementation, find security and regression issues | planned |

## License

MIT — see [`LICENSE`](./LICENSE). Hack around with it, adapt it, make it your own.
