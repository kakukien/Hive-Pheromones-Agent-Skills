---
name: agent-orchestration
description: Reusable patterns for routing, decomposition, parallel execution, chaining, and evaluator loops in multi-agent systems.
---

# Agent Orchestration

Use this skill when a task is too large, too mixed, or too uncertain for a single agent pass.

## Core Patterns

### 1. Routing

Route the task to the best role before execution starts.

Use routing when:
- The request could belong to different specializations
- The cost of using the wrong agent is high
- You need clear ownership for each task

Suggested rule:
- If the task is narrow and well scoped, assign one specialist
- If the task spans multiple domains, split it first
- If intent is unclear, clarify before routing

### 2. Orchestrator-Workers

One orchestrator breaks the task into subproblems, assigns workers, then synthesizes the result.

Use this pattern when:
- Multiple files or domains can be analyzed independently
- Research can run in parallel
- A final integrated answer is still required

Suggested flow:
1. Define the goal and output format
2. Split into parallelizable work units
3. Assign one owner per work unit
4. Run workers independently
5. Merge outputs into one final artifact

### 3. Chaining

The output of one step becomes the input of the next.

Use this pattern when:
- Steps depend on prior outputs
- You need transformation across stages
- Later work should not start before earlier work stabilizes

Common examples:
- Research -> outline -> draft -> review
- Trace bug -> isolate cause -> patch -> verify
- Extract data -> normalize -> analyze -> summarize

### 4. Evaluator-Optimizer Loop

One agent generates. Another scores and critiques. The generator revises until the result passes a threshold or the retry budget is exhausted.

Use this pattern when:
- Quality matters more than first-pass speed
- Output can be scored against explicit criteria
- A weak draft can be improved through iteration

Suggested loop:
1. Generate candidate output
2. Evaluate against rubric
3. Identify defects
4. Revise
5. Stop when threshold is met or retry limit is reached

## Operating Rules

- Define the final output before decomposing work
- Keep each worker focused on one clear responsibility
- Do not run dependent steps in parallel
- Preserve provenance so synthesis can trace each claim back to a worker
- Mark uncertainty explicitly instead of smoothing it away

## Minimal Output Contract

Each worker should return:

```text
{
  owner,
  task,
  findings,
  confidence,
  open_questions,
  artifacts
}
```

## Failure Modes

Watch for these problems:
- Premature decomposition before the goal is clear
- Too many workers for a small task
- Parallelizing steps that are actually dependent
- Synthesis that erases disagreement or uncertainty
- Infinite optimize loops without a clear stop rule

## Best Fit

Use this skill for:
- Codebase investigations
- Multi-file reviews
- Technical design work
- Long-form generation pipelines
- Agent systems that need explicit task ownership
