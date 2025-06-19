# Analysis of Coding Agent Architectures

This document summarizes the architectural analysis of three open-source coding agents: Aider, Cline/Roo-Code, and OpenHands. The primary goal was to determine whether each tool operates as a single-agent or a multi-agent system.

## 1. Aider: Single-Agent Architecture

**Conclusion:** Aider is definitively a **single-agent** system.

**Evidence:**
- **Unified Core Logic:** The application's execution flow, managed by `aider/main.py`, centers around a single `Coder` object.
- **Strategy Pattern:** The `aider/coders/` directory implements a strategy pattern, where the single agent selects a "coder" behavior (e.g., `editblock_coder`, `patch_coder`) based on the task. This is an internal state change, not a delegation to another agent.
- **No Orchestration:** The codebase lacks any features for agent delegation, supervision, or inter-agent communication. The workflow is linear and self-contained within one agent.

## 2. Cline/Roo-Code: Single-Agent Architecture

**Conclusion:** Cline/Roo-Code is a **single-agent** system.

**Evidence:**
- **Linear Task Flow:** The architecture illustrates a linear process where a central `Task` object manages the interaction with APIs and the MCP Hub.
- **Modal Operation:** The "Plan & Act" feature is a modal shift within a single agent. The agent changes its capabilities (read-only vs. write-enabled) but remains a single entity. It does not delegate the "Act" phase to a separate executor agent.
- **No Delegation Mechanism:** The architecture does not include any components for orchestrating or communicating between multiple agents.

## 3. OpenHands: Multi-Agent Architecture

**Conclusion:** OpenHands is a **multi-agent** system.

**Evidence:**
- **Explicit Delegation:** The `AgentDelegateAction` is a core part of the system, allowing one agent to formally delegate tasks to another.
- **Hierarchical Control:** The `AgentController` is designed to manage a hierarchy of agents, with explicit methods to `start_delegate` and `end_delegate`. It creates new controller instances for sub-tasks, demonstrating a clear supervisor/worker pattern.
- **Specialized Agent Hub:** The `agenthub` directory contains a variety of specialized agents (e.g., `CodeActAgent`, `ReadOnlyAgent`) that can be invoked by the main controller to handle specific parts of a larger task.

## Summary Table

| Agent | Architecture | Key Indicators |
| :--- | :--- | :--- |
| **Aider** | Single-Agent | Unified `Coder` object, strategy pattern for behavior, no orchestration. |
| **Cline/Roo-Code** | Single-Agent | Linear task flow, "Plan & Act" is a modal shift, no delegation. |
| **OpenHands** | Multi-Agent | `AgentDelegateAction`, hierarchical `AgentController`, hub of specialized agents. |

## 4. Framework Usage

A key finding from this analysis is that **none of the reviewed coding agents (Aider, Cline/Roo-Code, OpenHands) are built on top of the major agentic frameworks we are researching (Agno, LangGraph, or Google ADK).**

Each project has developed its own bespoke framework to meet its specific architectural and product needs. This indicates that the domain of AI-driven software development may have unique requirements that are not fully addressed by general-purpose agentic frameworks, leading teams to invest in custom-built solutions.