# Computer Use Safety

## What this skill does

This skill defines the safety layer for browser and computer-use agents.

It is not mainly about how to click faster.
It is about how to avoid unsafe action, false completion, and silent drift during execution.

The core loop is simple:
- observe
- choose one action
- execute
- verify progress
- stop when risk or uncertainty is too high

## Why it matters

Computer-use systems often fail in ways that look successful from the outside.

Typical failure modes include:
- continuing past an unexpected state change
- treating partial progress as completion
- acting inside a sensitive flow without clear authorization
- retrying blindly after a repeated failure

This skill exists to make those systems more cautious and more auditable.

## Best use cases

Use this skill when you need to:
- automate browser tasks
- define stop conditions for desktop agents
- add completion checks to screenshot-driven workflows
- design safe execution rules for human-in-the-loop systems

## Core ideas

### One step, one action

Avoid long unverified action chains.

### Stop conditions matter

The system must stop for login walls, credential entry, captcha, payment, destructive actions, or high-sensitivity environments without explicit approval.

### Completion must be evidenced

A task is complete only when the final state supports the claim.

### Logs are part of safety

Execution should leave behind a step log that can be reviewed later.

## Poor fit

Do not use this skill as-is for:
- sensitive financial operations
- personal account management
- credential-dependent workflows
- irreversible actions with high downside

## Files

- `SKILL.md` - compact instructions for agent use
- `README.md` - public explanation for human readers
