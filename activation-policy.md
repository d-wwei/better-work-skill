# Better Work Activation Policy

This file defines how `better-work` activates optional execution modules.

## Default Rule

Use plain `better-work` by default.

Overlay a protocol module only when the task shape justifies extra structure.

## Mode Stack

| Situation | Active modules |
|---|---|
| Small, direct, one-shot task | `better-work` |
| Multi-step task with light structure needs | `better-work` plus workflow templates |
| Complex multi-round task | `better-work` plus `round-based-execution` |
| Complex debugging | `better-work` plus `round-based-execution` plus debugging mode |
| Complex research | `better-work` plus `round-based-execution` plus research mode |
| High-risk work | `better-work` plus `round-based-execution` plus stricter verification/risk mode |

## Activation Checklist For `round-based-execution`

Activate when one or more are true:

- expected to require multiple stages
- spans multiple modules, files, or systems
- contains material unknowns that must be explored before execution
- likely to continue across sessions
- needs multiple agents or worker coordination
- has elevated risk if wrong
- shows scope-creep pressure
- needs stage-by-stage verification
- has enough context load that main-thread memory is no longer reliable

Do not activate when all of these are true:

- the task is a simple Q&A or tiny edit
- there is no meaningful phase dependency
- the task can be completed and verified in one bounded pass
- extra round state would create more overhead than leverage

## Activation Decision Logic

Use this order:

1. Can the task be completed and verified safely in one pass
   If yes, stay in default `better-work`.
2. Will the task likely require exploration, planning, execution, and verification as separate bounded slices
   If yes, activate `round-based-execution`.
3. Does the task need an additional domain-specific operating mode
   If yes, stack that module on top of `round-based-execution` rather than replacing it.

## Escalation Into Round Mode

Even if round mode was not active at the start, enter it when:

- the task has already looped or restarted multiple times
- context is getting noisy and resumability is poor
- later work quality is dropping
- multiple side quests are emerging
- one-shot execution no longer feels trustworthy

## Deactivation Back To Normal Mode

Exit round mode when:

- remaining work is a small bounded closeout
- no meaningful round boundary remains
- the task has reached final synthesis and only final delivery is left
