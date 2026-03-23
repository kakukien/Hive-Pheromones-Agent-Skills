---
name: computer-use-safety
description: Safety and completion patterns for screenshot-driven browser or desktop agents.
---

# Computer Use Safety

Use this skill when an agent performs browser or desktop actions on behalf of a user.

The public version focuses on safety and execution discipline, not on any specific model or framework.

## Mental Model

A computer-use agent should behave like a cautious operator.
It observes, acts once, checks the result, and stops when risk rises above the allowed threshold.

## Execution Loop

Recommended loop:
1. Observe the current state
2. Infer what changed since the last step
3. Pick one action
4. Execute the action
5. Wait for the environment to settle
6. Verify whether progress was made
7. Stop if success, blocked state, or risk threshold is reached

## Action Discipline

- One step, one action
- Prefer high-leverage actions over long low-level sequences
- Re-observe after navigation, modal changes, or major layout shifts
- Do not continue blindly after an unexpected state change

## Stop Conditions

Immediately stop and request user intervention when any of the following appears:
- login wall
- password entry
- captcha
- two-factor authentication
- payment flow
- irreversible deletion
- legal confirmation screens
- access to high-sensitivity domains without explicit approval

## Safety Boundaries

Never do these by default:
- enter credentials
- submit payment details
- approve destructive actions
- grant permissions blindly
- operate on government, medical, or financial systems without clear authorization

## Completion Checks

A task is complete only when success is supported by evidence.
Use three separate checks whenever possible:

### 1. Intent Check

Did the action sequence stay aligned with the user goal?

### 2. Rubric Check

Did the agent satisfy every required completion criterion?

### 3. State Check

Does the final page, screenshot, or application state show completion clearly?

If any check fails, do not declare success.

## Retry Policy

- Retry only when the failure is local and reversible
- Cap retries with a small fixed budget
- If the same failure repeats, stop and summarize the blockage

## Logging

Keep a step log with:
- timestamp
- observed state
- chosen action
- reason for action
- result
- completion status

This makes the run auditable and easier to debug.

## Best Fit

Use this skill for:
- browser automation
- repetitive web workflows
- screenshot-driven task execution
- product QA flows
- controlled data collection from web interfaces

## Poor Fit

Do not use this skill as-is for:
- sensitive financial operations
- personal account management
- workflows requiring hidden credentials
- environments where failure is costly and non-reversible
