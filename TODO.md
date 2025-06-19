# How to use TODO.md

This file tracks the tasks for our research and development of an AI coding agent. It is structured to provide a clear overview of our objectives and progress.

## Structure

The `TODO.md` file is organized as follows:

1.  **Main Goal:** A single, high-level objective that defines the overall purpose of the project for the current phase.
2.  **Sections (Sub-Goals):** The main goal is broken down into smaller, manageable sections. Each section represents a significant sub-goal or milestone.
3.  **Questions:** Below the sub-goal, list any blocking questions that must be answered before the tasks in that section can be completed.
4.  **Tasks:** Within each section, there is a checklist of specific, actionable tasks. These tasks should be checked off as they are completed.

### Example

```markdown
# Goal: Build a prototype AI coding agent

## Phase 1: Research and Scaffolding

- [x] Define research goals
- [ ] Define project goals
- [ ] Set up project structure

### Questions
- Which framework should we start with for the initial prototype, Agno or Google ADK?


## Phase 2: Framework Evaluation

- [ ] Build a simple agent with Agno
- [ ] Build a simple agent with Google ADK
- [ ] Compare performance and developer experience
```

This structure helps us stay organized and focused on delivering value incrementally.

---

# Goal: Determine the Optimal Architecture for an AI Coding Agent

## Phase 1: Define Goals and Research (Completed)

- [x] Define research goals in `_research/README.md`
- [x] Define project goals
- [x] Synthesize research findings from existing documents.

### Questions
- [x] What are the primary research and project goals? (Answered in `_research/README.md`)

## Phase 2: Coding Agent Analysis

- [x] Analyze the architecture of Aider to determine if it is single-agent or multi-agent.
- [x] Analyze the architecture of Cline/Roo-Code to determine if it is single-agent or multi-agent.
- [x] Analyze the architecture of OpenHands to determine if it is single-agent or multi-agent.
- [x] Create the summary document `_research/topics/2-coding-agent-architectures/summary.md` with the findings.

## Phase 3: Framework Adoption Research

- [x] Generate research prompt to investigate framework adoption trends.
- [ ] Execute external research using the generated prompt.
- [ ] Create a new summary document `_research/topics/1-framework-overview/summary.md` with the findings.

### Questions
- (No questions yet)