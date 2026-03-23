---
name: forum-debate
description: A structured multi-agent debate pattern for surfacing disagreement, testing assumptions, and converging on a usable decision.
---

# Forum Debate

Use this skill when a problem has multiple plausible answers and simple aggregation would hide important disagreement.

## Core Idea

Most multi-agent systems collect independent responses and concatenate them.
That misses contradiction, weak assumptions, and hidden blind spots.

Forum Debate uses a different flow:
- independent research
- first-round positions
- disagreement mapping
- bounded debate
- consensus synthesis

The point is not to create noise.
The point is to force useful collision before a decision is made.

## Roles

### Research Agents

Each agent studies the problem from a distinct perspective.
Examples:
- architecture
- security
- product
- design
- operations

### Moderator

The moderator does not argue for a solution.
The moderator:
- identifies agreement
- highlights contradiction
- enforces debate rules
- decides when enough evidence has been exchanged
- produces the final synthesis

### Reporting Agent

The reporting agent turns the final synthesis into the required artifact.
Examples:
- decision memo
- review report
- recommendation list
- implementation plan

## Standard Flow

### Phase 1. Parallel Research

Each agent researches independently and returns:

```text
{
  agent,
  key_findings,
  confidence,
  evidence,
  likely_disagreements
}
```

### Phase 2. First-Round Statements

Each agent states:
- core conclusion
- top supporting evidence
- uncertainty
- expected points of conflict

### Phase 3. Disagreement Mapping

The moderator classifies results into:
- agreement zone
- disagreement zone
- uncovered zone
- next debate topics

### Phase 4. Bounded Debate

Debate only the high-value disagreements.

Rules:
- Use evidence, not status
- Agents may revise their own view
- Repeated claims without new evidence are cut off
- Unresolved issues remain unresolved and are labeled as such
- Limit debate rounds to avoid infinite loops

### Phase 5. Consensus Synthesis

The moderator outputs:
- final conclusion
- retained disagreements
- action recommendations
- risks
- assumptions requiring validation

### Phase 6. Report Output

Convert the synthesis into the requested format.

## When to Use It

Use this skill for:
- architecture reviews
- roadmap choices
- product strategy discussions
- high-stakes code review
- evaluating competing implementation options

## When Not to Use It

Do not use this skill when:
- the task is simple and factual
- one specialist already owns the answer
- the decision depends on missing external data that no agent can obtain
- time pressure makes debate overhead unjustified

## Quality Rules

- Use 2 to 5 agents, not more
- Preserve minority views when evidence remains mixed
- Separate facts from interpretations
- Label blind spots explicitly
- End with a usable decision, not a wall of opinions
