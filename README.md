# Project Plan: ResearchReport-MA

## 1. Project Goal
Build a multi-agent system for collaborative research report generation.
The system should accept a research topic, decompose the task, collect supporting evidence, draft a report, and review the output before final delivery.

## 2. Core Idea
This project is not a simple combination of multiple single agents.
Instead, it is a collaborative multi-agent workflow with:
- shared state
- role specialization
- inter-agent dependency
- revision loop

## 3. System Design

### Agent 1: Planner
Responsibilities:
- understand the user topic
- decompose the topic into sub-questions
- generate report outline
- define task order and success criteria

Outputs:
- outline
- task list
- writing requirements

### Agent 2: Researcher
Responsibilities:
- search for evidence based on sub-questions
- collect source summaries
- organize evidence into structured notes

Outputs:
- evidence list
- source summaries
- keywords / references

### Agent 3: Writer
Responsibilities:
- write the report draft based on outline and evidence
- organize the report into sections
- keep style and structure consistent

Outputs:
- draft report in Markdown

### Agent 4: Reviewer
Responsibilities:
- check whether the draft matches the outline
- identify unsupported claims, weak logic, and missing references
- decide whether to approve or send back for revision

Outputs:
- review result
- revision suggestions
- final approval / rejection

## 4. Workflow

User Topic
-> Planner creates outline and subtasks
-> Researcher collects evidence
-> Writer produces draft
-> Reviewer evaluates draft
-> If rejected: send feedback back to Planner / Researcher / Writer
-> If approved: export final report

## 5. Technical Route
We will use CrewAI as the main framework:
- Crew for agent collaboration
- Flow for orchestration and shared state management
- LLM backend for reasoning and writing
- Search / retrieval tools for evidence collection
- Markdown output for final report generation

## 6. Repository Structure

```text
ResearchReport-MA/
├── README.md
├── PLAN.md
├── requirements.txt
├── .env
├── src/
│   ├── main.py
│   ├── flow.py
│   ├── agents.py
│   ├── tasks.py
│   ├── tools.py
│   └── config.py
├── outputs/
│   ├── drafts/
│   ├── reviews/
│   └── final_reports/
└── docs/
    └── demo_notes.md