---
description: Guide for writing a high-level architecture overview document
globs:
alwaysApply: false
---

# Rule: Writing an Architecture Overview Document

## Goal

To guide an AI assistant in creating a high-level **Architecture Overview** for a project or a major feature. The architecture document should describe the system’s overall design, the key components or services, and how they interact. It should provide technical stakeholders (including future team members or collaborators) a clear understanding of the structure of the system without digging into code. The tone should be informative and the content structured for easy navigation.

## Process

1. **Determine Scope and Context:** Clarify what the architecture overview should cover. Is it the architecture of the entire product, a specific module, or a new feature’s integration into an existing system? Ask the user for scope details if not specified (e.g., “Do you want a full system architecture or just the backend component?”). Also, gather any existing documentation or diagrams that might be relevant.
2. **Identify Major Components:** List out the major components of the system within the scope. Components could be things like front-end client, backend server (or multiple microservices), database(s), external APIs/services, middleware, third-party integrations, etc. Essentially, determine the building blocks of the system.
3. **Outline the Document Structure:** Plan the sections of the document. A typical architecture overview may include sections such as: Introduction, System Components, Data Flow, Deployment Diagram/Infrastructure, and possibly Technology Stack and Design Decisions. (See **Suggested Outline** below for details.) Create a skeleton with these sections as Markdown headings.
4. **Describe Each Component and Interaction:** For each major component identified:
   - Define what the component is and its responsibilities. For example, “**Frontend Web Application:** A React single-page app that allows users to ...”.
   - Explain how it interacts with other components (e.g., “It communicates with the backend via REST API calls to the XYZ Service”).
   - Mention key technologies or frameworks used in that component (e.g., “Node.js + Express” for a backend API, or “PostgreSQL” for a database).
   - If helpful, include a simple diagram (using text or Mermaid markdown) to visualize relationships (optional but very useful for complex systems).
5. **Data Flow and Communication:** Describe how data moves through the system. For example, outline a typical request lifecycle: user clicks a button -> front-end calls backend API -> backend processes and interacts with database -> returns result to front-end -> front-end updates UI. If multiple systems are involved (like message queues, background workers), explain those interactions as well.
6. **Highlight Key Design Decisions:** If there are important architectural decisions or patterns (e.g., using an event-driven architecture, a microservice approach vs monolith, specific design patterns like MVC or MVVM, etc.), explain them briefly. Also note any known trade-offs (for instance, “We chose MongoDB for flexibility, at the cost of complex transaction support”).
7. **Review for Clarity:** Go through the draft and ensure that someone unfamiliar with the system can follow the description. Remove overly specific technical jargon if it's not widely known, or add brief explanations for those terms. The document should be understandable to any developer with general knowledge.
8. **Update Diagrams (if any):** If you included architecture diagrams (Mermaid, etc.), check that they correctly reflect the written description and are easy to read.
9. **Finalize the Document:** Fill in all sections with the appropriate details. Make sure the formatting is clean (headings for sections, bullet points where appropriate, bold for component names, etc.).

## Suggested Outline

Consider structuring the architecture overview as follows:

- **Introduction:** A brief description of the system or feature, and the purpose of this document. You might include context like “This document provides an overview of the architecture for the XYZ application, including its main components and how they interact.”
- **High-Level Diagram:** *(Optional)* A simple diagram illustrating the components and their relationships at a glance. This could be a Mermaid diagram or an ASCII art diagram embedded in the Markdown.
- **Components:** For each major component or layer, have a subsection:
  - **Frontend:** Describe client-side apps (web, mobile, etc.), what they’re built with, and their role.
  - **Backend/Application Server(s):** Describe the server-side component(s), frameworks, and responsibilities.
  - **Database/Data Storage:** Describe the databases or storage systems used, their type (SQL, NoSQL, etc.), and what they store.
  - **External Services/Integrations:** If the system integrates with external APIs, authentication providers, third-party services, message queues, etc., list them and describe the integration.
- **Data Flow:** Describe one or two primary workflows in the system to illustrate how components interact. For example, “User Authentication Flow” or “Data Processing Flow,” describing step-by-step how data and calls move through the system for that use case.
- **Infrastructure/Deployment:** Optionally, describe how the system is deployed or hosted (e.g., “The application is containerized with Docker and hosted on AWS, with a load balancer distributing traffic to two backend instances...”). Include any pertinent info on scalability (multiple instances, microservices communication, etc.).
- **Technology Stack:** A summary of the technologies, frameworks, and languages used for each component (this can be a bullet list or table for quick reference).
- **Design Decisions & Trade-offs:** Highlight any significant choices made in the architecture and why. For example, “Using a NoSQL database for flexibility in storing user data schema” or “Monolithic architecture chosen initially for simplicity; may refactor to microservices later.”
- **Security & Performance (Optional):** Note any important security considerations (encryption, auth mechanisms) or performance optimizations (caching layers, CDN usage).
- **Future Considerations (Optional):** Mention if there are known areas that might change or plans for future improvements (e.g., “Considering moving to a microservice for the reporting module as it grows”).
- **Conclusion (Optional):** End with any closing remarks, or a short summary of how the architecture meets the needs of the project.

## Target Audience

Assume the reader is a developer or technical team member (possibly new to the project) who needs to quickly understand how the system is put together. The architecture overview should thus be **accessible to someone with general software knowledge but no prior familiarity with this specific project**. It should provide enough detail to orient them, without being as low-level as code documentation.

Use clear, declarative language. For example, prefer “The mobile app communicates with the server via a REST API” over “There is a possibility of interaction between client and server.” Be specific and factual.

## Output

- **Format:** Markdown (`.md`) document with appropriate headings, subheadings, bullet points, and diagrams (if applicable).
- **Location:** Typically in a `/docs/` directory or similar in the repository (since this is documentation). For example, `/docs/architecture-overview.md` or `/docs/architecture-[feature].md`.
- **Filename:** Use a descriptive name like `architecture-overview.md` or if specific to a feature, `architecture-[feature-name].md`.
- **Diagrams:** If using Mermaid for diagrams, include them in a Markdown code block with `mermaid` syntax. Ensure any such diagrams render correctly.

## Final Instructions

1. **High-Level Focus:** This document should avoid deep dive details (like code snippets or algorithm internals). Keep it high-level. Do not include actual source code unless it’s absolutely necessary to illustrate a point (usually it isn’t).
2. **Consistency:** Make sure the architecture described aligns with any existing documentation or the actual state of the codebase. If the user has provided a PRD or other docs, ensure no contradictions.
3. **Clarity and Brevity:** Aim for clarity. Use diagrams or bullet points to break up complex sections. Prefer shorter paragraphs and simple sentences over long-winded explanations.
4. **Review with User:** After drafting, the AI should ideally ask the user to review the architecture summary to confirm accuracy (especially if some assumptions were made). Any feedback should be incorporated.
5. **No Implementation Work:** This task is purely documentation. Do not modify any code or attempt to “fix” architecture issues in this step. If gaps or issues in the architecture are noticed, you can note them in the “Future Considerations” or discuss with the user, but do not deviate into coding.
