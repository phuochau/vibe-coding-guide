---
description: Guide for creating a Product Requirements Document from a feature idea
globs:
alwaysApply: false
---

# Rule: Generating a Product Requirements Document (PRD) from a Feature Idea

## Goal

To guide an AI assistant in creating a comprehensive Product Requirements Document (PRD) in Markdown format based on an initial feature idea from the user. The PRD should clearly define the feature's purpose, scope, and requirements, in a way that is actionable and easy for a developer (especially a junior developer) to understand and implement.

## Process

1. **Receive Initial Prompt:** The user provides a description of a new feature or functionality they want. This might be a few sentences or a short paragraph outlining the idea.
2. **Ask Clarifying Questions:** Before drafting the PRD, the AI **must** ask the user clarifying questions to gather more detail. The goal is to understand the **what** and **why** of the feature (the problem it solves and the objectives), rather than the exact **how** (implementation approach). Ensure you have clarity on the feature's purpose, target users, and any specific requirements or constraints. Wait for the user's answers before proceeding.
3. **Generate PRD:** Using the initial prompt and the answers to the clarifying questions, create a PRD document following the structure outlined in the **PRD Structure** section below. Write the content in clear, concise language. Focus on what the feature should do and why, not how to code it.
4. **Save PRD:** Save the completed PRD as a new Markdown file named `prd-[feature-name].md` inside the `/tasks/` directory (for example, if the feature is "user profile editing", the file could be `prd-user-profile-editing.md`).

## Clarifying Questions (Examples)

The AI should tailor its questions to the feature idea provided. Here are some common areas to cover with clarifying questions:
- **Problem/Goal:** “What user problem are we trying to solve with this feature?” or “What is the main goal we want to achieve?”
- **Target User:** “Who will be the primary user of this feature?” (e.g., new customers, admins, etc.)
- **Core Functionality:** “What key actions should a user be able to perform with this feature?”
- **User Stories:** “Can you provide a couple of user stories? (For example: ‘As a [type of user], I want to [do something] so that [benefit].’)”
- **Success Criteria:** “How will we know this feature is successful? What are the key metrics or criteria you expect?”
- **Scope and Boundaries:** “Are there things this feature will explicitly **not** do or handle (to help define scope)? Any assumptions or constraints we should note?”
- **Data Requirements:** “What data does this feature handle or require? Will it create, read, update, or delete any specific data?”
- **Design/UI:** “Are there any design guidelines, mockups, or specific UI preferences for this feature?”
- **Edge Cases:** “Can you think of any edge cases or unusual situations that we should consider for this feature?”

Gather as much information as possible from the user’s answers to ensure the PRD is detailed and accurate.

## PRD Structure

The generated PRD should include the following sections (use Markdown headings for each section):

1. **Introduction / Overview:** A brief description of the feature and the problem it solves. Explain the context and the primary goal of the feature.
2. **Goals:** A bullet list of the specific objectives or outcomes for this feature. These should be measurable or verifiable (e.g., improve conversion rate by X%, enable users to do Y).
3. **User Stories:** A list of user stories that describe how different users will interact with the feature and what benefit they get. For example: “As a *[user role]*, I want to *[perform an action]* so that *[desired outcome]*.”
4. **Functional Requirements:** A numbered list of the specific functionalities and behaviors the feature must have. Each requirement should be a single, testable statement (e.g., “1. The system **must allow** users to reset their password via email link.”). Focus on *what* the system should do.
5. **Non-Goals / Out of Scope:** A clear list of things that this feature will **not** address. This helps manage scope (e.g., “This feature will not handle payment processing”). If everything in the feature idea is in scope, you can state that there are no explicit non-goals.
6. **Design and UX Considerations (Optional):** Describe any known design or user experience details. This could include references to wireframes, expected layout or workflow, or visual requirements. If the feature must align with existing style guidelines or if certain UI components will be reused, note that here.
7. **Technical Considerations (Optional):** Mention any technical constraints, decisions or dependencies that are relevant. For example, note if the feature should use an existing API or module, performance considerations, security requirements, or any limitations (such as “must support offline mode” or external integrations).
8. **Success Metrics:** Explain how success will be measured once the feature is launched. For instance, key performance indicators or metrics (e.g., “Increase user engagement by 20% on the profile page” or “Reduce load time to under 2 seconds for search results”). These should correlate with the Goals.
9. **Open Questions:** List any open issues or unanswered questions that came up while defining the feature. These might include decisions that need feedback or things to be determined (e.g., “Should we allow login with Google for this feature?”). If there are no outstanding questions, you can state "None at this time."

## Target Audience

Assume the primary reader of this PRD is a **junior developer** who will implement the feature. Therefore, the document should be explicit and unambiguous. Avoid unnecessary jargon and clearly explain the feature’s intent and requirements. The goal is that a developer reading this PRD would understand exactly what to build and why.

## Output

- **Format:** Markdown (`.md`) document, well-formatted with proper headings, lists, and emphasis where needed.
- **Location:** Save under the `/tasks/` directory.
- **Filename:** `prd-[feature-name].md` (e.g., if the feature is "Profile Editing", the file could be `prd-profile-editing.md`).

## Final Instructions

1. **Do NOT** start writing any code or implementation details in the PRD. The PRD is a planning document, not a place for code.
2. Always begin by asking clarifying questions if the feature idea is not fully clear. Do not proceed to writing the PRD until all necessary details are gathered from the user.
3. Use the information from the user’s answers to refine the PRD content. If new details emerge during drafting, incorporate them and, if needed, ask additional questions.
4. Ensure the PRD is thorough but concise. It should contain all relevant information about *what* needs to be built and *why*, without delving into *how* to build it (that will come in the design and implementation stages).
