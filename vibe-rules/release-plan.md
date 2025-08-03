
---

### 📄 `.vibe-rules/release-plan.md` (optional)

```markdown
---
description: Rule for generating a scoped release plan (e.g., v1.0)
globs:
alwaysApply: false
---

# Rule: Writing a Release Plan

## Goal

Prepare a clear plan for an upcoming release (e.g. v0.1, v1.0), including scope, tasks, testing, and release criteria.

## When to Use

When preparing for a milestone or public version.

## Process

1. **Define Version and Deadline**: Name the release (e.g., v1.0) and target date.
2. **Scope Features**: List PRDs and task files that must be completed.
3. **Test Criteria**: Define what must be tested or reviewed.
4. **Release Checklist**:
   - QA complete
   - Regression tests
   - Changelog
   - Version bump
   - Deployment verified
5. **Fallback Plan**: Note what can be cut/delayed.

## Output Format

```markdown
# Release Plan – v0.3 (Aug 20, 2025)

## In Scope
- [ ] Feature A (@tasks-feature-a.md)
- [ ] Bug Fixes (@tasks-onboarding-bugs.md)

## QA Checklist
- [ ] Manual test: onboarding flow
- [ ] E2E tests pass
- [ ] Version bump in `package.json`

## Success Criteria
- ✅ No critical bugs in staging
- ✅ New features deployed and tested
- ✅ Release notes published
