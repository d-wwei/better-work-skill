# Installing Better Work for Codex

Install the professional `better-work` skill via native skill discovery (`~/.codex/skills/`).

## Prerequisites

- Git

## Installation

### macOS / Linux

```bash
# 1. Clone the repo
git clone https://github.com/d-wwei/better-work-skill.git ~/.codex/better-work-skill

# 2. Create skill symlink
mkdir -p ~/.codex/skills
ln -s ~/.codex/better-work-skill/codex/better-work ~/.codex/skills/better-work

# 3. Install prompt trigger
mkdir -p ~/.codex/prompts
ln -s ~/.codex/better-work-skill/commands/better-work.md ~/.codex/prompts/better-work.md

# 4. Restart Codex
```

### Windows (PowerShell)

```powershell
# 1. Clone the repo
git clone https://github.com/d-wwei/better-work-skill.git "$env:USERPROFILE\.codex\better-work-skill"

# 2. Create skill junction
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills"
cmd /c mklink /J "$env:USERPROFILE\.codex\skills\better-work" "$env:USERPROFILE\.codex\better-work-skill\codex\better-work"

# 3. Install prompt trigger
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\prompts"
cmd /c mklink "$env:USERPROFILE\.codex\prompts\better-work.md" "$env:USERPROFILE\.codex\better-work-skill\commands\better-work.md"

# 4. Restart Codex
```

## Verify

Type `$better-work` in a Codex conversation. If the skill is loaded, it should activate.

Or check directly:

```bash
# macOS / Linux
ls ~/.codex/skills/better-work/SKILL.md

# Windows PowerShell
Test-Path "$env:USERPROFILE\.codex\skills\better-work\SKILL.md"
```

## Trigger Methods

| Method | Command | Requires |
|--------|---------|----------|
| Auto trigger | No action needed, matches by description | SKILL.md |
| Direct call | Type `$better-work` in conversation | SKILL.md |
| Manual prompt | Type `/prompts:better-work` in conversation | SKILL.md + prompts/better-work.md |

## Update

```bash
cd ~/.codex/better-work-skill
git pull
```

The symlink or junction automatically picks up the latest version.

## Uninstall

### macOS / Linux

```bash
rm ~/.codex/skills/better-work
rm ~/.codex/prompts/better-work.md
rm -rf ~/.codex/better-work-skill
```

### Windows (PowerShell)

```powershell
Remove-Item "$env:USERPROFILE\.codex\skills\better-work"
Remove-Item "$env:USERPROFILE\.codex\prompts\better-work.md"
Remove-Item -Recurse "$env:USERPROFILE\.codex\better-work-skill"
```
