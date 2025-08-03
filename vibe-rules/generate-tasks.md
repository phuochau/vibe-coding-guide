---
description: Guide for generating an implementation task list from a PRD
globs:
alwaysApply: false
---

# Rule: Generating a Task List from a PRD

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list (with sub-tasks) in Markdown format, based on an existing Product Requirements Document (PRD). The resulting task list should serve as an actionable implementation plan, guiding a developer through building the feature outlined in the PRD.

## Output

- **Format:** Markdown (`.md`) document containing the task list.
- **Location:** `/tasks/[feature-name]/` (e.g. a subfolder named after the feature or PRD file, if using a folder per feature).
- **Filename:** `tasks-[feature-name].md` (for example, if the PRD file is `prd-user-profile-editing.md`, the task list file could be `tasks-user-profile-editing.md`).
- The task list file will be stored in the tasks directory (or a subdirectory named for the feature) alongside the PRD.

## Process

1. **Receive PRD Reference:** The user will invoke this rule by referencing a specific PRD file (e.g., `@prd-user-profile-editing.md`). Ensure you have access to and have read the content of that PRD before proceeding.
2. **Analyze the PRD:** Thoroughly read the PRD’s content, including the feature description, user stories, functional requirements, and any technical or design considerations. Extract the key elements that need to be implemented. Pay special attention to each functional requirement and any implicit tasks (such as updating documentation or writing tests).
3. **Phase 1 - Generate High-Level Tasks:** Identify the major high-level tasks required to implement the PRD. These are the parent tasks that represent broad parts of the work (for example: *“Front-end UI for Profile Editing”*, *“Back-end API endpoints for Profile Data”*, *“Database migration for new fields”*, *“Testing & QA”* etc.). Use your judgment on how many top-level tasks are appropriate; typically this may be on the order of 5±2 main tasks, depending on complexity. 
    - Create a new markdown file for the task list (if not already created) and list these high-level tasks in order. Use a checklist format (e.g., `- [ ] Task description`). **Do not** list sub-tasks yet.
    - Present the high-level task list to the user for review **before** expanding sub-tasks. After listing them, output a prompt such as: *“Generated the high-level tasks based on the PRD. Please review these tasks. If everything looks good, respond with 'Go' to expand into sub-tasks.”*
4. **Wait for Confirmation:** Pause and wait for the user’s confirmation. The user should explicitly respond with “Go” (or an equivalent approval) to proceed. This step ensures the user agrees with the high-level breakdown before diving into details.
5. **Phase 2 - Generate Sub-Tasks:** Once the user approves, take each high-level parent task in turn and break it down into a set of smaller, actionable sub-tasks. Each sub-task should be as granular as necessary for a developer or AI agent to implement in a single step or short session. Use a hierarchical numbering or indentation to clearly indicate which sub-tasks belong to which parent task. For example:
    - `[ ] 1.0 Parent Task A`
        - `[ ] 1.1 Sub-task for A`
        - `[ ] 1.2 Another sub-task for A`
    - `[ ] 2.0 Parent Task B`
        - `[ ] 2.1 Sub-task for B`
        - etc.
   Ensure that the sub-tasks collectively cover all aspects of the parent task’s requirement. Sub-tasks should be in logical order (e.g., setup tasks before implementation, implementation before testing).
6. **Identify Relevant Files:** As you generate tasks (especially sub-tasks), determine which files (existing or new) are likely to be created or modified for each task. Maintain a section called **Relevant Files** in the document that lists these files. For each file, provide a brief description of its purpose in the context of this feature. Include test files as well if applicable. (For example, if a sub-task is to create a new API endpoint, relevant files might include `api/profile.js` and `api/profile.test.js`).
7. **Generate Final Output:** Populate the task list document with all sections: the Relevant Files section, any additional Notes, and the complete list of tasks with sub-tasks. Ensure the format is clean and easy to read (headings, subheadings, and checkboxes properly used).
8. **Save Task List:** Save the updated task list document in the designated location. The file name should follow the pattern `tasks-[feature-name].md` matching the PRD’s feature name.

## Output Format

The generated task list **must** follow this general structure:

```markdown
## Relevant Files

- `path/to/important/file1.ts` – *Brief description of this file’s role in the feature (e.g., main component or module for the feature).*  
- `path/to/important/file1.test.ts` – *Tests for the above file, ensuring its functionality.*  
- `path/to/another/file.js` – *Another relevant file to be created or modified (e.g., API route or backend service).*  
- `path/to/another/file.test.js` – *Test file for the above, if applicable.*  

### Notes

- *Include any general notes or assumptions here.* For example: “Ensure unit tests are co-located with implementation files.”  
- *Testing:* Outline how to run tests (e.g., “Run `npm test` to execute all new tests” or specific commands if relevant).

## Tasks

- [ ] **1.0 Setup Project/Environment**  
  - [ ] 1.1 Initialize any required configurations or environment variables for the feature  
  - [ ] 1.2 Update dependencies or include libraries if needed  

- [ ] **2.0 Frontend: Profile Editing UI**  
  - [ ] 2.1 Create the profile editing form component (HTML/CSS/JS or React component)  
  - [ ] 2.2 Implement client-side validation for the form inputs  
  - [ ] 2.3 Connect the form to backend API (submit changes)  

- [ ] **3.0 Backend: Profile API Endpoints**  
  - [ ] 3.1 Design the API endpoint for updating profile data (`PATCH /api/profile`)  
  - [ ] 3.2 Implement the endpoint in the server (controller/service logic)  
  - [ ] 3.3 Write unit tests for the profile update logic  

- [ ] **4.0 Database**  
  - [ ] 4.1 Add new database fields for additional profile info (if any)  
  - [ ] 4.2 Write a migration script for the database changes  
  - [ ] 4.3 Test the migration with sample data  

- [ ] **5.0 Testing & Verification**  
  - [ ] 5.1 Run all tests and ensure they pass  
  - [ ] 5.2 Perform manual testing for edge cases (e.g., invalid input, network failure)  
