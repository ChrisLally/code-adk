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
-   **Example:** The file [`topics/1-framework-overview/prompt.md`](code-adk/_research/topics/1-framework-overview/prompt.md) is the canonical example of a well-structured research prompt.

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
3.  **Synthesize and Document:** The findings are documented in a dedicated analysis file within the `research` directory (e.g., `topics/2-coding-agent-architectures/summary.md`).

This dual-track approach allows us to leverage powerful external tools for broad information gathering while using direct, hands-on analysis for understanding local code.

---
# Research Goal: Determine the Optimal Architecture for an AI Coding Agent

## 1. Objective

The primary objective of this research is to conduct a comprehensive analysis of existing agentic frameworks and architectural patterns to determine the most effective, reliable, and scalable approach for building an advanced AI coding agent. We will investigate the trade-offs between different philosophies, focusing on single-agent versus multi-agent systems, and identify best practices for tool integration, model orchestration, and security.

## 2. Key Research Areas

Our investigation will be centered around the following key areas:

### 2.1. Framework Analysis

- **Comparative Study:** Conduct a deep-dive comparison of **Google ADK**, **Agno**, and **LangGraph**.
  - **Performance:** Benchmark instantiation speed, memory footprint, and overall latency.
  - **Architecture:** Analyze the core design philosophies (e.g., minimalist vs. stateful graph vs. enterprise system).
  - **Capabilities:** Evaluate native support for multi-modality, multi-agent patterns, and persistence.

### 2.2. Architectural Patterns

- **Single-Agent vs. Multi-Agent:** Critically evaluate the two dominant architectural philosophies.
  - **Cognition.ai's Argument:** Investigate the "shared context" principle and the potential pitfalls of multi-agent systems where context is not fully shared.
  - **Anthropic's Approach:** Analyze the benefits of the "Planner-Executor" and "Supervisor" models for parallelizing complex research and coding tasks.
  - **Hybrid Models:** Explore architectures that combine the strengths of both approaches, such as using a primary orchestrator (LangGraph) to manage ephemeral, high-performance agents (Agno) for specific parallelizable tasks.

### 2.3. Integration and Tooling

- **Model Context Protocol (MCP):** Assess MCP as a standard for decoupling agents from their tools.
  - Design and blueprint custom MCP servers for essential developer tools, specifically **GitHub** and **pytest**.
- **IDE & Git Integration:** Analyze how existing agents (OpenHands, Cline/Roo-Code, Aider) integrate with the developer's local environment, including Git workflows and IDE feedback loops.

### 2.4. Security and Reliability

- **Human-in-the-Loop (HITL):** Define non-negotiable checkpoints for human approval, especially for file modifications and code commits.
- **Sandboxing:** Establish best practices for executing code and running tests in isolated environments (e.g., Docker).
- **Observability:** Evaluate tools and techniques for tracing and debugging agent behavior to ensure reliability and auditability.

## 3. Guiding Questions

- What are the definitive trade-offs between a single, long-context agent and a collaborative multi-agent system for software development?
- Is it more effective to build agents from a low-level, high-control framework (LangGraph) or a high-level, feature-rich framework (Google ADK)?
- Where does a performance-oriented framework like Agno fit into the architecture? Is it a primary framework or a specialized tool for parallel tasks?
- How critical is a standardized protocol like MCP for building an extensible and future-proof agent ecosystem?

## 4. Deliverables

- A detailed report summarizing the findings of the framework and architectural analysis.
- A recommended hybrid architecture that specifies the optimal combination of framework(s), patterns, and integration protocols.
- Functional blueprints for building MCP servers for GitHub and pytest.