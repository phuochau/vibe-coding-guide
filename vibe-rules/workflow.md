# 📊 Vibe Coding Workflow Diagram (Solo Developer + AI Editor)

This Mermaid diagram shows how all `.md` rule files connect across the solo dev workflow — from planning and PRD creation to execution, releases, and retrospectives.

```mermaid
flowchart TD

  subgraph Planning
    ROADMAP["🛣️ roadmap.md<br/>Define high-level phases (MVP, Beta, etc.)"]
    SPRINTPLAN["📆 sprint-plan.md<br/>Plan sprint scope and timeline"]
    SPRINTGOALS["🎯 sprint-goals.md<br/>Define 2–5 measurable sprint goals"]
    RELEASEPLAN["📦 release-plan.md<br/>Group tasks for milestone (v0.1, v1.0)"]
  end

  subgraph Definition
    CREATEPRD["📝 create-prd.md<br/>Write a Product Requirements Document"]
    RESEARCH["🔍 write-research-summary.md<br/>Summarize technical or market research"]
  end

  subgraph Execution
    GENTASKS["📝 generate-tasks.md<br/>Turn PRD into step-by-step task list"]
    PROCESSTASKS["🛠️ process-task-list.md<br/>Execute tasks one at a time"]
    API["📡 write-api-spec.md<br/>Define REST or GraphQL API"]
    SCHEMA["🗄️ write-data-model.md<br/>Describe DB schema or migration"]
    ARCH["🏗️ write-architecture.md<br/>Document high-level system design"]
    BUG["🐞 fix-bug.md<br/>Fix and document issues"]
  end

  subgraph Review
    RETRO["🔁 retrospective.md<br/>Reflect on sprint and list improvements"]
  end

  VISION["💡 Idea or Product Vision"]

  %% Relationships
  VISION --> ROADMAP
  ROADMAP --> SPRINTPLAN
  SPRINTPLAN --> SPRINTGOALS
  SPRINTPLAN --> CREATEPRD
  SPRINTPLAN --> RELEASEPLAN

  CREATEPRD --> GENTASKS
  RESEARCH --> CREATEPRD
  RESEARCH --> GENTASKS

  GENTASKS --> PROCESSTASKS
  PROCESSTASKS --> API
  PROCESSTASKS --> SCHEMA
  PROCESSTASKS --> ARCH
  PROCESSTASKS --> BUG

  PROCESSTASKS --> RETRO
  SPRINTPLAN --> RETRO
  SPRINTGOALS --> RETRO
