# better-work-skill

### A verification-first execution protocol for coding agents

**🇺🇸 English** | **[🇨🇳 中文](README.zh-CN.md)**

`better-work-skill` is a lightweight operating protocol for coding agents. It does not add new tools or new model weights. It improves how an agent uses the tools it already has:

- less guessing
- less premature surrender
- less asking the user too early
- less "done" without proof
- more deliberate investigation
- more verification before completion
- better handoff quality when a task is genuinely blocked
- better continuity for multi-step work

This repo packages three layers into one practical system:

- `high-agency` as the behavior core
- `better-work` as the product and command surface
- a lightweight GSD-inspired workflow skeleton for longer tasks

## What Changed

Better Work now has three responsibilities:

1. enforce rigorous execution standards
2. give users a clean command surface
3. keep multi-step work from losing context

In practice, that means:

- more source reading
- more log reading
- more assumption checking
- more build/test/curl/manual verification
- fewer shallow fixes
- lighter but clearer task planning for longer work

## The Workflow Model

Better Work uses a lightweight four-phase model:

1. `intake` -> clarify goal, constraints, and success criteria
2. `plan` -> break work into verifiable slices
3. `execute` -> advance one slice at a time and keep evidence current
4. `closeout` -> end with verified completion or structured handoff

For tiny tasks, skip the written workflow and just execute rigorously.

For larger tasks, use the templates in `templates/`:

- `TASK.md`
- `PLAN.md`
- `STATE.md`
- `HANDOFF.md`

These files are intentionally small. They are execution aids, not long project docs.

## Commands

Use `/better-work` as the normalized command language in docs and examples. Depending on the tool, that may map to:

- `$better-work`
- `/prompts:better-work`
- a native slash command alias

### `/better-work`

Use this when you want the full protocol.

### `/better-work verify`

Bias toward evidence, verification, and closeout quality.

### `/better-work unstick`

Bias toward diagnosis, alternate hypotheses, and path switching.

### `/better-work handoff`

Bias toward structured blocker reports with verified facts and next steps.

### `/better-work review`

Bias toward sibling issues, edge cases, and upstream or downstream impact.

### `/better-work plan`

Bias toward intake, success criteria, task slicing, and whether workflow files are warranted.

### `/better-work execute`

Bias toward continuing from the current task, plan, or state without losing context.

## 3-Minute Quick Start

### Claude Code

```bash
mkdir -p ~/.claude/skills/better-work
curl -o ~/.claude/skills/better-work/SKILL.md \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/skills/better-work/SKILL.md
```

Then in Claude Code, load:

```text
$better-work
```

### Codex CLI

```bash
mkdir -p ~/.codex/skills/better-work
curl -o ~/.codex/skills/better-work/SKILL.md \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/codex/better-work/SKILL.md

mkdir -p ~/.codex/prompts
curl -o ~/.codex/prompts/better-work.md \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/commands/better-work.md
```

Then start a conversation and type:

```text
$better-work
```

### Cursor

```bash
mkdir -p .cursor/rules
curl -o .cursor/rules/better-work.mdc \
  https://raw.githubusercontent.com/d-wwei/better-work-skill/main/cursor/rules/better-work.mdc
```

### VS Code Copilot

```bash
mkdir -p .github/instructions
cp vscode/instructions/better-work.instructions.md .github/instructions/
```

## What To Expect

Once active, the agent should:

- investigate before asking
- verify before claiming completion
- switch approaches after repeated failure
- write compact state only when it adds leverage
- produce a more useful handoff if the task is genuinely blocked

## Why This Version Is Better

Earlier Better Work was strong on execution discipline but thin on workflow.

This version keeps the original rigor while adding:

- a lightweight planning mode
- an execution mode for longer tasks
- compact state templates for work that spans sessions
- clearer separation between small-task and large-task behavior

The result is still lightweight, but less likely to lose context on real engineering work.
