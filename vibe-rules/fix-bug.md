---
description: Guide for diagnosing and fixing a reported software bug
globs:
alwaysApply: false
---

# Rule: Fixing a Reported Bug

## Goal

To guide an AI assistant through the systematic process of diagnosing and resolving a reported bug in the codebase. The aim is to understand the bug fully, identify the root cause, apply a fix in code, and verify that the issue is resolved, all while documenting the changes. This ensures bugs are handled methodically and the risk of introducing regressions is minimized.

## Process

1. **Receive Bug Report:** The user or tester describes a bug. This might include a problem description, steps to reproduce, expected vs actual behavior, and any error messages or logs. Begin by reading and understanding this bug report thoroughly.
2. **Ask Clarifying Questions:** If any details are unclear or missing, ask the user targeted questions to gather more information. Your goal is to be able to consistently reproduce the bug (or at least pinpoint where in the system it occurs). Common questions might include details about the environment, specific inputs that trigger the bug, version of the software, etc. (See **Clarifying Questions** below for examples.)
3. **Reproduce the Issue (Analysis):** Based on the information, simulate or walk through the steps to reproduce the bug. This could involve running a part of the code (if possible in the environment) or mentally tracing the code's logic with the given scenario. Identify which module, function, or section of code is likely causing the issue. Pay attention to any error messages or stack traces provided; they often point to the file/line of origin.
4. **Identify Root Cause:** Once you've isolated the general area of the bug, dig into the code to find the exact cause. This could be a logical error, an unhandled edge case, a regression from a recent change, etc. Examine relevant variables, conditions, and flows. For example, if there's a crash, what is `null` or unexpected at that point? If data is wrong, where did it come from?
5. **Plan the Fix:** Before writing code, outline how to fix the problem. Determine what needs to change in the code to resolve the issue. Consider if the fix will have side effects elsewhere. If there are multiple ways to fix it, choose the simplest approach that solves the root cause without breaking other functionality. (If unsure, you might present the plan to the user briefly for confirmation.)
6. **Implement the Fix:** Apply the code changes needed to fix the bug. Modify or add code in the appropriate files. Keep the changes as minimal as possible to solve the issue (this reduces the risk of affecting other parts of the system). Ensure to also update or write **unit tests** or **regression tests** for this bug if applicable, to prevent it from recurring.
7. **Test the Solution:** After code changes, verify that the bug is indeed fixed. Re-run the reproduction steps or affected use-case to confirm the issue no longer occurs. Run the test suite (or at least relevant tests) to ensure nothing else broke. If possible, add a new test case specifically for this scenario to assert the bug is resolved.
8. **Document the Fix:** Provide a brief explanation of the bug and the fix, either in the code (as a comment near the change), in the commit message, or an update to a CHANGELOG or bug tracker. For example, note what the root cause was (“Fixed off-by-one error in date calculation causing end date to be omitted”) so there is historical context.
9. **Follow Up:** Check if there are similar parts of the code that could suffer from the same type of bug (for example, if the bug was a misused function, ensure no other place does the same mistake). If found, consider fixing those as well or at least flagging them to the user.

## Clarifying Questions (Examples)

When the bug report is initially provided, consider asking some of the following to make sure you have all necessary information:
- **Reproduction Steps:** “Can you provide the exact steps to reproduce the issue from a fresh start?” (Including any specific data or conditions needed.)
- **Environment:** “What environment are you running this in? (e.g., OS, browser, device, software version)” Sometimes bugs are environment-specific.
- **Expected Behavior:** “What was the expected outcome in this scenario?” to clarify the correct behavior.
- **Actual Behavior Details:** “What exactly happened vs what you expected? Do you have screenshots or error logs?”
- **Error Messages/Logs:** “If there are any error messages or logs, could you share them? They can be very helpful for pinpointing the issue.”
- **Frequency:** “Does this happen every time or intermittently? If intermittent, any pattern you’ve noticed?”
- **Recent Changes:** “Did this bug start happening after a recent change or deployment? (If known)” – This can hint at which part of the code might be involved.
- **Related Functionality:** “Are other features or parts of the app affected, or is it isolated to this one scenario?”

Collecting answers to these will give you a clearer picture and help confirm when the bug is fixed.

## Output

- **Code Changes:** The primary output of this process will be the code modifications that fix the bug. These changes should be presented clearly, typically as a diff or specified by file and line number, so the user can review them. Include enough context around the changes.
- **Testing Evidence:** If applicable, mention how you verified the fix (e.g., “All unit tests passed” or “Manually verified the form now submits without error”). If you added a new test, mention that (and include the test code in the diff if relevant).
- **No New File unless Necessary:** Usually fixing a bug doesn’t involve creating new markdown files or documentation, except perhaps an update to a CHANGELOG or similar. Focus on the code. If the fix is complex, you might write a short summary in a comment or commit message.
- **Location of Fix:** Specify which files/functions were changed so the user knows where the fix has been applied (if it's not obvious from the diff).

## Final Instructions

1. **Verify Understanding Before Fixing:** Ensure you understand the bug and its context completely before attempting a fix. If anything is still uncertain (e.g., you cannot reproduce it), do not guess – ask for more information or find another way to confirm the behavior.
2. **Minimal Impact:** Implement the simplest viable fix that addresses the root cause. Avoid “hacking around” the symptom; fix the underlying problem. Also, avoid widespread changes—limit modifications to the scope of the bug.
3. **Preserve Functionality:** Make sure your fix doesn’t break any related features. Run relevant parts of the application or tests to confirm.
4. **Communication:** After proposing the fix (i.e., presenting the code changes), clearly explain what was wrong and how the fix addresses it, in a concise manner. This helps the user (founder) understand the change and builds trust in the solution.
5. **Await Confirmation:** Once you provide the fix and explanation, wait for the user’s review. Be prepared to make adjustments if the user tests the fix and finds issues, or if they have follow-up questions.
