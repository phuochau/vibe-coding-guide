# Vibe Coding Workflow Diagram

This diagram shows how all `.md` rule files relate to each other in a solo + AI Editor development workflow.

```mermaid
flowchart TD
    VISION[Vision / Idea]
    VISION --> CREATE_PRD["📝 create-prd.md<br/>Write a Product Requirements Document"]

    CREATE_PRD --> GEN_TASKS["📝 generate-tasks.md<br/>Break PRD into step-by-step tasks"]
    GEN_TASKS --> PROCESS_TASKS["🛠️ process-task-list.md<br/>Work through tasks one at a time"]

    PROCESS_TASKS -->|If backend/API| API_SPEC["📡 write-api-spec.md<br/>Define API contracts"]
    PROCESS_TASKS -->|If DB changes| DATA_MODEL["🗄️ write-data-model.md<br/>Define schema or migrations"]
    PROCESS_TASKS -->|If design impact| ARCH["🏗️ write-architecture.md<br/>Describe high-level system design"]

    PROCESS_TASKS -->|Anytime there's a bug| FIX_BUG["🐞 fix-bug.md<br/>Fix and document bugs"]

    RESEARCH["🔍 write-research-summary.md<br/>Summarize technical or market research"] --> CREATE_PRD
    RESEARCH --> GEN_TASKS

    PROCESS_TASKS --> RETRO["🔁 retrospective.md<br/>Reflect on sprint and improve"]

    classDef rule fill:#fef3c7,stroke:#f59e0b,stroke-width:1px,color:#92400e;
    classDef doc fill:#f0fdf4,stroke:#34d399,stroke-width:1px,color:#064e3b;

    class CREATE_PRD,GEN_TASKS,PROCESS_TASKS,API_SPEC,DATA_MODEL,ARCH,FIX_BUG,R
