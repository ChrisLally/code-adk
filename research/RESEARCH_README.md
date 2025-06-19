# Research Process

This document outlines the methodology for conducting research for the AI coding agent project. Our approach is divided into two distinct tracks: **External Research** for gathering new information from public sources, and **Internal Analysis** for examining local codebases and artifacts.

## Track 1: External Research

This track is used when we need to gather information from outside our existing project files, such as web articles, academic papers, blog posts, and documentation. This process involves using specialized external research agents.

### Step 1: Generate a Research Prompt

Before initiating external research, a formal research prompt will be generated. This prompt serves as the "brief" for the research agent.

-   **Purpose:** To clearly define the scope, objectives, and deliverables of the research task.
-   **Structure:** The prompt must include:
    -   **Objective:** A high-level summary of the research goal.
    -   **Key Questions:** Specific questions the research must answer.
    -   **Methodology:** Suggested sources and methods (e.g., "search academic papers," "analyze blog posts," "compare framework documentation").
    -   **Deliverables:** The expected format of the output (e.g., "a summary of findings," "a list of links with annotations," "a comparative table").
-   **Example:** The file [`1-overview/agent-frameworks-and-agents-prompt.md`](code-adk/research/1-overview/agent-frameworks-and-agents-prompt.md) is the canonical example of a well-structured research prompt.

### Step 2: Execute with External Research Agent

The generated prompt is then provided to an external, specialized research agent. This agent is responsible for executing the web searches and information gathering as defined in the prompt.

### Step 3: Synthesize and Document

The raw output from the external research agent is then analyzed and synthesized into a structured, human-readable document. This final document is stored in the `research` directory and serves as the canonical source of truth for that topic.

---

## Track 2: Internal Codebase Analysis

This track is used when the research objective is to understand the architecture, patterns, or implementation details of code within this project (e.g., in the `coding_agent_examples/` directory).

### Process

This process is conducted directly, without the need for an external research agent.

1.  **Define Objective:** A clear goal is set in the main `_tasks/TODO.md` file (e.g., "Analyze the architecture of Aider").
2.  **Code Exploration:** Use internal tools (`list_files`, `read_file`, `search_files`) to explore the relevant codebase.
3.  **Synthesize and Document:** The findings are documented in a dedicated analysis file within the `research` directory (e.g., `2-analysis/coding-agent-architectures.md`).

This dual-track approach allows us to leverage powerful external tools for broad information gathering while using direct, hands-on analysis for understanding local code.