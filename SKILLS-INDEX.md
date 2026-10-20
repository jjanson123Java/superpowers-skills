# Superpowers Skills — Guide and Index

> **Start here:** This page explains what each of the 15 skills is for, when to choose it, and where to read its full instructions. It is a navigation guide, not a replacement for the instructions in each `SKILL.md`.

**Repository:** [jjanson123Java/superpowers-skills](https://github.com/jjanson123Java/superpowers-skills)  
**All skills:** [Browse the `skills/` folder](skills/)  
**Original project:** [obra/superpowers](https://github.com/obra/superpowers)  
**License:** [MIT](LICENSE) — original copyright and attribution retained.

## First, what is a skill?

A **skill** is a set of written instructions that teaches an AI coding agent *how to approach a task*. The main file is named **`SKILL.md`** and lives inside its own folder. Some skills include extra reference documents, example prompts, templates, or runnable scripts.

**Important:** These are not 15 standalone programs, buttons on GitHub, or models. Storing the files in this repository does **not** automatically activate them in ChatGPT, Claude Code, Codex, or any other coding tool. The tool must be configured to load the relevant skills, and features involving subagents or worktrees require agent/runtime support.

## Quick guide: which skill should I use?

| # | Skill (open its instructions) | Purpose in plain English | Use it when… |
|---:|---|---|---|
| 1 | **[Using Superpowers](skills/using-superpowers/SKILL.md)** | Teaches the agent how to discover and invoke the right skills. | Starting a coding session or setting up skill-driven work. |
| 2 | **[Brainstorming](skills/brainstorming/SKILL.md)** | Clarifies the goal, requirements, and proposed design before building. | Planning a new feature, UI, project, or substantial behavior change. |
| 3 | **[Writing Plans](skills/writing-plans/SKILL.md)** | Turns an approved design into small, testable implementation tasks. | You know *what* to build and need an exact, executable plan. |
| 4 | **[Using Git Worktrees](skills/using-git-worktrees/SKILL.md)** | Creates or checks an isolated development workspace so changes do not disturb your main working tree. | Starting implementation that should be kept separate until verified. |
| 5 | **[Executing Plans](skills/executing-plans/SKILL.md)** | Implements a plan in the current agent session, task by task, with tests and a final review. | You want lower-overhead inline execution or have no subagent tool available. |
| 6 | **[Subagent-Driven Development](skills/subagent-driven-development/SKILL.md)** | Gives implementation tasks to fresh subagents with task-level reviews and a final overall review. | Implementing a plan with independent tasks and available subagent support. |
| 7 | **[Dispatching Parallel Agents](skills/dispatching-parallel-agents/SKILL.md)** | Investigates or processes independent problems concurrently through separate agents. | Multiple tasks or failures truly do not depend on each other. |
| 8 | **[Test-Driven Development](skills/test-driven-development/SKILL.md)** | Requires a failing test before the minimal code change, followed by passing tests and refactoring. | Implementing a new feature, correcting a bug, or changing behavior. |
| 9 | **[Systematic Debugging](skills/systematic-debugging/SKILL.md)** | Investigates reproducible evidence and root cause before proposing a fix. | An error, failing test, unexpected output, or production defect appears. |
| 10 | **[Requesting Code Review](skills/requesting-code-review/SKILL.md)** | Gets an independent review of work against requirements and code quality. | Finishing a task, major feature, or preparing to merge. |
| 11 | **[Receiving Code Review](skills/receiving-code-review/SKILL.md)** | Checks whether review feedback is technically correct before applying it. | A reviewer suggests changes that must be evaluated and tested. |
| 12 | **[Verification Before Completion](skills/verification-before-completion/SKILL.md)** | Demands fresh test, build, or inspection evidence before saying work is done. | Preparing to claim a fix, patch, migration, or release is complete. |
| 13 | **[Finishing a Development Branch](skills/finishing-a-development-branch/SKILL.md)** | Verifies tests and guides merge, pull-request, keep-branch, and cleanup decisions. | Implementation is complete and you need to integrate the changes. |
| 14 | **[Diagnosing Superpowers](skills/diagnosing-superpowers/SKILL.md)** | Analyzes a Superpowers agent session with transcript-based evidence to explain repeated work, ignored instructions, or other workflow problems. | The *skill system or agent session itself* seems to have malfunctioned. |
| 15 | **[Writing Skills](skills/writing-skills/SKILL.md)** | Helps create, modify, and test your own reusable agent instructions. | Customizing this library or adding a new domain-specific skill. |

## Common workflows

### A. Build a feature

1. **Brainstorming** → agree on requirements and design.
2. **Writing Plans** → define files, steps, tests, and acceptance criteria.
3. **Using Git Worktrees** → isolate the work.
4. **Executing Plans** *or* **Subagent-Driven Development** → implement the plan.
5. **Test-Driven Development** → applies while changing code.
6. **Requesting Code Review** + **Receiving Code Review** → inspect and act on findings.
7. **Verification Before Completion** → demonstrate that acceptance criteria and tests pass.
8. **Finishing a Development Branch** → decide whether to merge, open a PR, or retain the branch.

**Choosing between the two implementation skills:** *Executing Plans* uses one agent session and a final review. *Subagent-Driven Development* uses separate agents and reviews for individual tasks; it generally needs more agent capacity.

### B. Fix a defect

1. **Systematic Debugging:** reproduce the problem and identify root cause.
2. **Test-Driven Development:** write a regression test that fails for the observed defect.
3. Apply the smallest justified fix and rerun relevant tests.
4. **Verification Before Completion:** confirm the defect and related tests pass.
5. **Requesting Code Review** when appropriate.

**Example:** A generated chapter violates validation rules. First determine which stage introduced the wrong content or verdict; do not immediately alter the validation policy to make the error disappear.

### C. Investigate multiple independent failures

Use **Dispatching Parallel Agents** only when failures are demonstrably independent. If two visible symptoms have the same underlying cause, use **Systematic Debugging** across the whole dependency chain instead of splitting prematurely.

**Example:** Independent failures in a UI test and a report-export test may be parallelizable. A TLS failure and an HTTP 502 caused by that TLS failure should be investigated together.

### D. Diagnose the agent itself

Use **Diagnosing Superpowers** when the agent repeated steps, ignored an approved plan, failed to invoke a skill, or consumed unexpected time or tokens. This is distinct from **Systematic Debugging**, which investigates the software being built.

### E. Create your own skills

Use **Writing Skills** for reusable processes you want coding agents to follow. Put a new skill in `skills/<your-skill-name>/SKILL.md`, test it in the intended agent environment, and add a link to this index. Preserve original author attribution and the [MIT license](LICENSE).

## Practical examples

| You want to… | Start with… | Then consider… |
|---|---|---|
| Design an Italus author-profile feature | [Brainstorming](skills/brainstorming/SKILL.md) | Writing Plans → implementation → tests |
| Find the root cause of a failing API or GUI test | [Systematic Debugging](skills/systematic-debugging/SKILL.md) | Test-Driven Development → Verification |
| Split a large patch into controlled, testable changes | [Writing Plans](skills/writing-plans/SKILL.md) | Using Git Worktrees → Executing Plans |
| Check whether a patch is truly finished | [Verification Before Completion](skills/verification-before-completion/SKILL.md) | Requesting Code Review |
| Understand why an AI coding session went off plan | [Diagnosing Superpowers](skills/diagnosing-superpowers/SKILL.md) | Correct the workflow after reviewing evidence |
| Write a reusable troubleshooting or code-review policy | [Writing Skills](skills/writing-skills/SKILL.md) | Test the new skill |

## What you see in GitHub

Click any skill link in the table above. Each link opens the **actual `SKILL.md` instructions**, not merely the folder. Other files in that folder are supporting material.

For example:

```text
skills/
├── systematic-debugging/
│   ├── SKILL.md              <-- Core instructions
│   └── ...                   <-- Supporting references and examples
├── test-driven-development/
│   └── SKILL.md
└── writing-plans/
    └── SKILL.md
```

## Independence, installation, and provenance

This repository was created as a **one-time independent mirror**. Its files and imported Git history remain in your account even if the original repository changes or disappears. The initial import and backup are documented in [INDEPENDENT-MIRROR.md](INDEPENDENT-MIRROR.md).

Some original README installation commands and supporting links still point to the original project's marketplace, package URL, community, or other external resources. **Using such commands may install or retrieve the original upstream package rather than your independent copy.** To use your own version, configure your chosen coding tool to load the skills or plugin from **this repository** according to that tool's supported installation mechanism. Verify the installed source and skill availability before relying on it.

This page is an explanatory navigation guide. The `SKILL.md` files remain authoritative for each skill's exact procedure and prerequisites.

---

**Go back:** [Repository home](README.md) · [Browse all 15 skill folders](skills/) · [Mirror details](INDEPENDENT-MIRROR.md) · [License](LICENSE)
