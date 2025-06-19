# Project Goal: Build a Hybrid AI Coding Agent Prototype

## 1. Vision

To construct a functional prototype of an AI coding agent that embodies the principles of modularity, reliability, and security. This agent will serve as a proof-of-concept for a "best-of-all-worlds" architecture, combining the strengths of leading agentic frameworks and design patterns identified during our research.

## 2. Core Architectural Blueprint

The prototype will be built upon a hybrid architecture with the following key components:

- **Orchestration Core (LangGraph):** We will use LangGraph as the central orchestrator to manage the agent's workflow. Its stateful, graph-based nature is critical for ensuring reliability, fault tolerance, and implementing robust Human-in-the-Loop (HITL) checkpoints.

- **Standardized Tooling (MCP):** All external capabilities will be integrated via the Model Context Protocol (MCP). We will develop and use custom MCP servers for essential developer tasks, starting with:
  - A **GitHub MCP Server** for reading repositories, committing files, and managing pull requests.
  - A **pytest MCP Server** for executing tests in a secure, sandboxed environment.

- **Architectural Pattern (Planner-Executor):** The agent will implement the Planner-Executor model. A central "Planner" agent, powered by a high-capability reasoning model, will decompose tasks and delegate them to specialized "Executor" agents.

- **Model Flexibility (LiteLLM):** All model interactions will be routed through LiteLLM to maintain model agnosticism, allowing us to easily swap models for cost and performance optimization.

- **Performance Scaling (Agno - Optional Extension):** As an advanced goal, we will explore integrating Agno for highly parallelizable sub-tasks (e.g., running linters across many files) to combine LangGraph's control with Agno's performance.

## 3. Key Features and Capabilities

The prototype must successfully demonstrate the following capabilities:

- **Task Comprehension:** The agent must be able to understand a high-level coding task described in natural language.
- **Code Navigation:** It must be able to read and understand an existing codebase within a given repository.
- **Test-Driven Development (TDD) Loop:** The agent must be able to:
  1. Write a failing test for a new feature.
  2. Run `pytest` via its MCP tool and analyze the failure.
  3. Write the necessary implementation code to make the test pass.
  4. Re-run the tests to confirm success.
- **Secure Git Workflow:**
  1. Commit the changes with a descriptive message.
  2. **Wait for mandatory human approval** before proceeding.
  3. Create a pull request for human review.

## 4. Success Criteria

The project will be considered a success when the agent can autonomously complete a simple, end-to-end development task, such as:

> "In the target repository, create a new function `calculate_area(length, width)` in `utils.py`. Write a corresponding test in `tests/test_utils.py` to ensure it works correctly. Once the test passes, commit the changes and open a pull request."

This will validate that our chosen hybrid architecture is viable and provides the necessary foundation for building a more advanced and capable AI coding agent.