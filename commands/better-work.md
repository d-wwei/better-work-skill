---
description: "Better Work command surface. Use /better-work for the core protocol, or add verify, unstick, handoff, or review."
argument-hint: "[verify|unstick|handoff|review] [task description]"
---

Load the `better-work` core skill and apply it to the current task.

## Command Routing

- No subcommand -> activate the full Better Work protocol
- `verify` -> focus on verification, evidence, and close-the-loop checks
- `unstick` -> focus on recovery method, alternate hypotheses, and changing direction
- `handoff` -> produce a structured boundary report with verified facts and next steps
- `review` -> inspect sibling issues, edge cases, and upstream/downstream impact after a fix

## Execution Rules

1. Load the `better-work` skill
2. Follow the behavior protocol in `SKILL.md`
3. If `$ARGUMENTS` contains text beyond the subcommand, treat it as the task description
4. Use the subcommand to bias the output:
   - `verify`: prioritize evidence, tests, build output, runtime checks
   - `unstick`: prioritize diagnosis, search, assumption checks, and a new approach
   - `handoff`: prioritize verified facts, eliminated possibilities, and problem boundaries
   - `review`: prioritize related-pattern checks and follow-on risks

## Example Invocations

### `/better-work`

- `/better-work Fix this failing CI test end to end.`
- `/better-work Investigate why staging works but production fails.`
- `/better-work Implement this API change and verify the result.`

### `/better-work verify`

- `/better-work verify I think the auth fix is done.`
- `/better-work verify this config change before we merge it.`
- `/better-work verify the smallest end-to-end path for this bugfix.`

### `/better-work unstick`

- `/better-work unstick We have tried two fixes and still get ECONNREFUSED.`
- `/better-work unstick The migration keeps failing in the same way.`
- `/better-work unstick Stop tweaking and find a fundamentally different angle.`

### `/better-work handoff`

- `/better-work handoff If this still cannot be reproduced locally, write a clean boundary report.`
- `/better-work handoff Summarize verified facts and eliminated possibilities.`
- `/better-work handoff Prepare the next engineer to continue from here.`

### `/better-work review`

- `/better-work review Check this module for sibling issues after the fix.`
- `/better-work review Look for upstream/downstream impact before we call this done.`
- `/better-work review Inspect edge cases and similar patterns in nearby files.`
