# Better Work

Apply the Better Work protocol to the current task.

## Modes

- `better-work`
- `better-work rounds`
- `better-work verify`
- `better-work unstick`
- `better-work handoff`
- `better-work review`
- `better-work plan`
- `better-work execute`

## Rules

1. Investigate before asking the user
2. Verify before claiming completion
3. Switch approaches after repeated failure
4. Use lightweight workflow files for multi-step work only when they add leverage
5. End with either verified completion or a structured handoff
6. If the task is complex, multi-stage, high-risk, or multi-agent, activate `round-based-execution`
7. In round mode, each round must follow PDCA and end with a quality gate before the next round starts
8. If the user explicitly invokes `better-work rounds`, force `round-based-execution` instead of waiting for auto-activation

## Workflow Files

Use these only for larger tasks:

- `TASK.md`
- `PLAN.md`
- `STATE.md`
- `HANDOFF.md`
- `ROUND.md`
- `round-state.json`
