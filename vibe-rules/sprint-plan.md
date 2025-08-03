---
description: Guide for generating a sprint plan with goals, selected tasks, and timeframe
globs:
alwaysApply: false
---

# Rule: Creating a Sprint Plan

## Goal

Generate a **Sprint Plan** for the next 1–2 weeks of development. The sprint plan should define what will be worked on, which tasks or PRDs are in scope, any goals or themes, and estimated timeline.

## When to Use

At the beginning of each sprint or dev cycle.

## Inputs

- A roadmap or list of high-priority features.
- PRDs and/or task files.
- (Optional) retrospective or pending tasks from the last sprint.

## Process

1. **Review Inputs**:
   - Look at the current roadmap or backlog.
   - Identify PRDs or task files likely to be tackled in this sprint.
   - Review any leftover tasks from the previous sprint (if any).

2. **Define Sprint Scope**:
   - Choose 1–3 feature PRDs or bugfix groups to focus on.
   - For each, include task filenames or summaries.

3. **Set Sprint Goals**:
   - Write 2–5 measurable goals for this sprint (see `sprint-goals.md`).

4. **Create Sprint Timeline**:
   - Define the start and end date of the sprint.
   - Estimate rough timing for each main task (e.g., Feature A: 4 days).

5. **Link Related Artifacts**:
   - Include references to `@prd-*`, `@tasks-*`, or bugs.
   - Add links or paths to `.md` files being worked on.

## Output Format

```markdown
# Sprint Plan: Sprint 6 (Aug 5–Aug 16, 2025)

## Goals
- Launch user profile editing (Feature A)
- Fix all remaining onboarding bugs
- Prepare release notes for v0.3

## Tasks
- [ ] @tasks-user-profile-editing.md
- [ ] @tasks-onboarding-bugs.md

## Timeline
- Aug 5–8: Finish Feature A UI and backend
- Aug 9–11: Testing and QA
- Aug 12–14: Bug fixes
- Aug 15–16: Final polish, prepare changelog

## Notes
- Related PRDs: @prd-user-profile-editing.md
- Carry-over from Sprint 5: 2 onboarding bugs
