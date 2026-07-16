# Task 5 — Skill or agent?

The three tasks the team repeats every week (from `README.md`), sorted.

## The sort

| # | Repeated task | Verdict | Why |
|---|---------------|---------|-----|
| 1 | **Clean & summarise the dataset** | **Skill** | Same recipe every week — drop empty rows, recompute totals, flag outliers, write the house format. The steps don't change based on what the data says, so it just needs to be written down once and followed. |
| 2 | **Build the weekly bar chart** | **Skill** | One fixed output, same shape every week, straight from the cleaned numbers. No judgment calls — nothing to decide. |
| 3 | **Produce the full report pack** (clean → chart → write-up → email) | **Agent** | Chains the other steps *and* has to decide as it goes: is this flagged row minor enough to note and move on, or big enough to stop and ask a human? Should this email go out? Decisions mid-task are what make it an agent rather than a recipe. |

## The rule of thumb

A **skill** is a recipe: fixed steps, same every time, no branching on what you find.
An **agent** is a worker: it chains steps together and makes judgment calls in the middle, so it needs goals and guardrails rather than just instructions.

Test: *"Does this task need to make a decision partway through that changes what it does next?"* No → skill. Yes → agent.

## What was built

**The agent** — [`.claude/agents/report-pack.md`](.claude/agents/report-pack.md).

Picked the agent over a skill because it's the harder and more instructive of the two, and because the skill half of the sort was already built for Task 4
([`.claude/skills/clean-and-summarise-dataset/SKILL.md`](.claude/skills/clean-and-summarise-dataset/SKILL.md)) — so the two together demonstrate both sides of the distinction.

Two guardrails were written into it deliberately, both at the points where judgment is actually required:

- **A flagged row it can't recompute** — it must decide whether to note it and proceed or stop and escalate, and must state which it chose and why. It may not silently drop or guess the row.
- **Sending the email** — it drafts, but never sends. Sending is visible to other people and hard to undo, so a human confirms first.

Note that the agent *calls* the Task 4 skill for its first stage rather than restating those steps. The recipe lives in one place; the agent supplies only the judgment.
