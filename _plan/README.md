# MVP Development Plan: AI Coding Agent

This document outlines the proposed plan for developing the Minimum Viable Product (MVP) for our AI coding agent. The plan is based on the foundational research conducted in `../_research`.

## Guiding Principles

Our MVP development will be guided by the following principles, derived from our research into leading agentic frameworks and existing coding agents:

1.  **Start Lean and Iterate:** We will begin with a lightweight, flexible core and add complexity incrementally. This avoids over-engineering and allows us to adapt as we learn.
2.  **Control is Key:** The architecture must provide fine-grained control over the execution loop, state, and environment interactions, a key lesson from agents like Aider.
3.  **Embrace Modularity:** We will build a modular system with a clear separation of concerns, particularly between high-level planning and low-level execution.
4.  **Model Agnosticism:** The architecture will be designed to be independent of any single Large Language Model provider.

---

## Proposed Architecture

Our MVP will be built on a **Planner-Executor** model, a pattern successfully employed by advanced agents.

-   **Planner Agent:** A high-level agent responsible for interpreting the user's request, decomposing it into a logical sequence of steps, and managing the overall task flow.
-   **Executor Agent:** A low-level agent that performs discrete, well-defined actions as instructed by the Planner (e.g., read a file, write a code block, run a command).

## Technology Stack

-   **Primary Framework:** **Agno**. Its lightweight, library-based approach provides the performance and control needed for our MVP. It allows us to build a custom, high-performance core without the overhead of a more opinionated framework.
-   **Model Abstraction:** **LiteLLM**. This will be integrated from the start to ensure we can easily switch between different LLM providers without significant code changes.
-   **Interface:** **Command-Line Interface (CLI)**. A CLI is the most direct and effective interface for an MVP focused on core functionality.

---

## Framework Justification: Agno vs. ADK

The choice to use **Agno** as the primary framework for the MVP is a strategic one based on the core findings of our research. While Google ADK is a powerful, enterprise-grade framework, Agno's characteristics are better aligned with the specific goals of an MVP coding agent.

The decision is based on a fundamental trade-off: **Fine-Grained Control vs. Out-of-the-Box Structure.**

-   **Why Agno for the MVP?**
    1.  **Maximum Control:** Our research highlighted that leading coding agents use custom frameworks to achieve precise control over the execution loop. Agno's library-based, minimalist approach allows us to build a highly custom, performance-sensitive agent core, which is essential for the iterative `edit-test-debug` cycle.
    2.  **Low "Framework Tax":** Agno's lightweight nature ensures minimal performance overhead. This is critical for a responsive user experience, a key factor in developer tool adoption.
    3.  **Simplicity and Speed:** For an MVP, the primary goal is to validate the core agent logic as quickly as possible. Agno allows us to focus on this core logic without the initial complexity of adopting a more comprehensive and opinionated system like ADK.

-   **The Role of ADK:**
    -   Google ADK is an excellent framework, but it is optimized for structured, observable, and maintainable systems in an enterprise context. Its powerful features (e.g., robust state management, clear orchestration flows) would be highly valuable for a mature, production-level version of this agent.
    -   By starting with Agno, we prioritize the flexibility needed to innovate on the core agent experience. We can consider migrating to or integrating with ADK in a later phase when scalability and observability become higher priorities.

---

## Phased Development Plan

### Phase 1: Core Architecture & The "Hello, World" Task

*Objective: Build the foundational agent loop and successfully execute a simple file modification.*

1.  **Setup Agno Project:** Initialize the project with Agno as the core framework.
2.  **Implement Planner-Executor Agents:** Create the basic `Planner` and `Executor` agent classes.
3.  **Implement Model Abstraction:** Integrate `LiteLLM` to handle all interactions with language models.
4.  **First Task:** Implement the ability to perform a simple "read-modify-write" operation on a text file based on a user prompt.

### Phase 2: Environment Integration

*Objective: Connect the agent to the developer's core tools: the filesystem and Git.*

1.  **Filesystem Tools:** Grant the agent the ability to list files and read multiple files to gather context.
2.  **Git-Awareness:**
    -   The agent must be able to identify the current Git branch and status.
    -   All proposed code changes must be presented to the user as a **diff** before being applied.
3.  **Human-in-the-Loop (HITL):** Implement a strict approval gate. The agent **must not** write to any file without explicit user confirmation.

### Phase 3: The Edit-Test-Debug Loop

*Objective: Enable the agent to validate its own work, forming the core of a reliable coding assistant.*

1.  **Testing Capability:** Implement a tool for the agent to run a predefined test command (e.g., `pytest`).
2.  **Output Parsing:** The agent must be able to read the output from the test command to determine if the tests passed or failed.
3.  **Debugging Logic:** If tests fail, the agent should enter a debugging loop: read the error, formulate a fix, apply the fix (with approval), and re-run the tests.

### Phase 4: MVP Release & Future Work

*Objective: Consolidate features into a usable MVP and outline the next steps.*

1.  **Refine CLI:** Improve the command-line interface for a better user experience.
2.  **Documentation:** Write clear documentation on how to install and use the MVP.
3.  **Outline Next Steps:** Based on the MVP's performance, plan for future enhancements, such as:
    -   More advanced state management.
    -   Integration with existing MCP servers for tools like GitHub.
    -   More sophisticated planning and reasoning capabilities.