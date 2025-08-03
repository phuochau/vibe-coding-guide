
## process-task-list.md

```markdown
---
description: Guide for processing a task list sequentially with user approval at each step
globs:
alwaysApply: false
---

# Rule: Processing the Task List (Sequential Execution with Approval)

## Purpose

Guidelines for the AI to follow when executing tasks from a task list, ensuring work is done one sub-task at a time with user review and approval after each step. This helps maintain control and allows the user (solo founder) to verify each change before moving on.

## Task Implementation

- **One Sub-task at a Time:** The AI should focus on **only one sub-task** at a time. **Do NOT** start the next sub-task until the current one is fully completed and the user explicitly gives permission (e.g., the user says "yes" or "go ahead" for the next task). This prevents confusion and keeps changes isolated.
- **Completion Protocol:**  
  1. When a sub-task is finished, immediately mark it as completed in the task list by changing its checkbox from `[ ]` to `[x]`. For example, if the sub-task was `- [ ] 2.1 Implement the API endpoint`, it should now be `- [x] 2.1 Implement the API endpoint`.  
  2. If **all** sub-tasks under a parent task are now marked done (`[x]`), also mark the parent task as completed (e.g., change `- [ ] 2.0 Backend API` to `- [x] 2.0 Backend API`). This provides a quick visual of progress.
- **Pause After Each Task:** After completing and marking a sub-task, the AI should stop and await user input. Do not proceed to the next item until the user reviews the changes and explicitly approves moving forward (or provides additional instructions).

## Task List Maintenance

1. **Keep the Task List Updated:**  
   - Continuously update the task list Markdown file as work progresses. Each time a task or sub-task is completed, mark it with `[x]` as described above.  
   - If new tasks or sub-tasks emerge during implementation (for example, the user requests an additional feature or you discover a missing step), add them to the task list under the appropriate section. Preferably, get user confirmation before adding significant new tasks.
2. **Maintain the “Relevant Files” Section:**  
   - Each time you create a new file or modify an existing file as part of a sub-task, ensure that file is listed (if not already) in the **Relevant Files** section of the task list document.  
   - Provide a one-line description for each file in that section so the user knows why that file was touched (e.g., “Added new function to handle password encryption in `auth/utils.js`”).

## AI Instructions

When operating with the task list, the AI must adhere to the following rules:

1. **Start with Next Pending Task:** Always identify the next incomplete sub-task (the first `[ ]` in the list from top to bottom that is not marked done) and focus only on that.
2. **Regularly Update the File:** After finishing a sub-task and making the necessary code changes, update the task list file to mark completion and list any new files or notes. Save this updated file state.
3. **Follow the Completion Protocol:** As detailed above, mark sub-tasks and parent tasks completed appropriately. Do not skip this step—it's important for tracking.
4. **Add Newly Discovered Tasks:** If, during the process of a task, a new to-do or issue is discovered, add it to the task list (either as a new sub-task under the relevant parent task, or as a new parent task if it doesn't fit under existing ones). Highlight it to the user, and proceed only after getting approval.
5. **Keep “Relevant Files” Accurate:** Anytime a file is created or modified for a sub-task, ensure it's reflected in the Relevant Files list. This keeps the user aware of changes to the project structure.
6. **Seek Approval Before Next Step:** Once a sub-task’s code changes are done and documented, pause. Present the diff or summary of changes to the user for review. Only if the user is satisfied (they say "looks good" or "proceed") should you move to the next sub-task.
7. **Error Handling:** If the user points out an issue with the implementation of a sub-task or requests changes, address those before marking the sub-task as complete. Only mark as complete when the work truly meets the requirements.

## Final Instructions

- **No Multi-tasking:** Never attempt to do multiple tasks in one go or batch several sub-tasks together in a single response. Always strictly follow the one-at-a-time approach.
- **Clarity in Diffs:** When showing code changes, make it easy for the user to understand what was changed (e.g., show a diff or clearly indicate the updated sections of code).
- **User Focus:** Remember that the user (solo founder) may be reviewing each change. Provide context if needed, but be concise. After completing a task and providing the changes, it's often helpful to ask, “Is this okay? May I mark this task as completed and proceed to the next one?” to explicitly get approval.
- **Stay Aligned with Task List:** Use the task descriptions as the source of truth for what to do next. If something in the code seems to require work not listed, clarify with the user and add it to the list (with approval) rather than going off-script.
