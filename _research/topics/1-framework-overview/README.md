# 1. Framework Overview

This research topic focuses on analyzing and comparing different agentic frameworks to determine the best fit for our AI coding agent.

## Research Structure

This directory is organized into sub-topics, each with its own set of research notes, prompts, and summaries.

- **[1a-framework-adoption-coding-agents](1a-framework-adoption-coding-agents):** Analysis of framework adoption in existing coding agents.
A central finding of this research is that the most prominent and capable AI coding agents, such as Aider and OpenHands, are built on custom, bespoke frameworks rather than adopting mature, general-purpose agentic frameworks. This section explores the technical, philosophical, and historical reasons for this trend.

### 1.1 Key Reasons for Custom Frameworks

The decision to "build" is a calculated engineering choice driven by the unique demands of the software development domain. Five primary factors were identified:

1.  **Fine-Grained Execution Control:** Coding is an iterative, non-linear process. Custom frameworks provide precise control over the execution loop, error handling, and context management. Aider's **Architect/Editor model**, which separates high-level planning from low-level code editing, is a prime example of a specialized pipeline that is difficult to implement efficiently in a generalist framework.

2.  **Specialized State Management:** Software development requires tracking a complex state across thousands of steps, including file versions, test outcomes, and strategic plans. Custom solutions, like the **event stream architecture** in OpenHands, are purpose-built for this, whereas general frameworks offer more generic state models ill-suited to the domain.

3.  **Deep Environmental Integration:** Agents need a tight, low-level connection to the developer's environment (filesystem, Git, shell). Custom frameworks treat this as a first-class component, enabling seamless, low-latency interactions that are fundamental to the workflow, such as Aider's "Git-native" approach.

4.  **Performance and Latency Sensitivity:** The rapid **edit-test-debug cycle** is critical to developer productivity. General-purpose frameworks can introduce a "framework tax" in latency and memory. Bespoke solutions are optimized for the minimal resource footprint required for a fluid pair-programming experience.

5.  **Historical Timing and Framework Maturity:** The development of today's leading coding agents largely predates the maturity of frameworks like LangGraph (relaunched early 2024), Google ADK (released March 2025), and Agno. Building a custom solution was initially the only viable path.

### 1.2 The Hybrid Future: A Role for General Frameworks

Despite the dominance of custom builds for generalist agents, a clear trend shows general-purpose frameworks being adopted for more constrained, auxiliary coding tasks.

-   **Uber's "AutoCover"** uses **LangGraph** to orchestrate a multi-agent system for automated unit test generation.
-   **Replit** uses **LangGraph** to power its AI code generation agent within its controlled IDE environment.

This suggests a future hybrid ecosystem where conversational, generalist agents remain on custom frameworks, while specialized, workflow-driven agents (for test generation, dependency updates, etc.) are built on general frameworks and integrated into CI/CD pipelines.

## Section 2: The Architectural Foundations of Modern Coding Agents

The design and operation of advanced coding agents are governed by a set of core conceptual pillars. These architectural principles have emerged in response to the inherent limitations of early, monolithic agent designs, providing the necessary modularity, extensibility, and reliability required for complex software development tasks.

### 2.1 The Planner-Executor Paradigm: Separating Thought from Action

A foundational architectural pattern transforming agent design is the decomposition of agentic workflows into two distinct cognitive layers: a high-level "Planner" and a low-level "Executor." This paradigm moves beyond single-model systems, where one LLM is tasked with the entire cognitive load of understanding a complex goal, breaking it down, creating a plan, and executing each step. Instead, it advocates for a separation of concerns that mirrors specialized human teams.

The Planner, often powered by a sophisticated and powerful reasoning model, is responsible for strategic, high-level thinking. Its primary functions include interpreting the user's overall objective, decomposing the complex task into a sequence of smaller, manageable sub-tasks, and orchestrating the overall workflow.

The Executor, conversely, is focused on the tactical execution of these discrete, well-defined sub-tasks. This layer can be implemented using one or more specialized agents, each potentially powered by a different model optimized for a specific function, such as generating a block of Python code, running a terminal command, or analyzing a test result.

### 2.2 The Model Context Protocol (MCP): A Universal Language for Tools

As agents become more capable, their need to interact with the external world—to read files, access databases, call APIs, and run commands—becomes paramount. The Model Context Protocol (MCP) has emerged as a critical open standard designed to solve this problem by decoupling AI agents from the tools they use.

At its core, MCP is an open protocol that standardizes how LLM-powered applications discover and interact with external capabilities. It functions as a universal adapter, eliminating the need for bespoke integrations and fostering a more modular and interoperable ecosystem.

### 2.3 Achieving Model Agnosticism with Abstraction Layers

The rapid proliferation of Large Language Models presents both an opportunity and a challenge. To address this, the concept of a model abstraction layer has become a critical component of modern agentic architectures. **LiteLLM** stands out as a key open-source Python library embodying this principle. It acts as a lightweight middleware layer that provides a single, unified, and OpenAI-compatible API for interacting with over 100 different LLM providers, allowing developers to switch between models with minimal to no code changes.

## Section 3: Framework Deep Dive: Agno, LangGraph, and Google ADK

This section provides a detailed analysis of the core architectural principles of three leading agentic frameworks.

### 3.1 Google ADK: The Enterprise-Grade Orchestrator

The Google Agent Development Kit (ADK) is a comprehensive, event-driven framework designed for building sophisticated, production-ready AI agents.

-   **Core Philosophy:** Emphasizes modularity, extensibility, and a clear separation of concerns through its `Runner` (orchestration) and `Flow` (execution logic) architecture.
-   **State Management:** Implements a robust state model that tracks committed and pending changes, ensuring predictable state management.
-   **Key Strengths:** Well-suited for enterprise applications requiring structured, observable, and maintainable agentic systems.

[**Read the full Google ADK analysis here &raquo;**](1b-framework-analysis/adk.md)

### 3.2 Agno: The High-Performance Library

Agno is a lightweight, library-based framework that prioritizes developer control, flexibility, and high-performance execution.

-   **Core Philosophy:** Provides a collection of configurable components (`Agent` and `Team` dataclasses) that can be assembled to create highly customized multi-agent systems.
-   **State Management:** Features a pluggable `Storage` system, allowing developers to choose the right backend for their needs.
-   **Key Strengths:** Ideal for performance-sensitive applications and developers who require fine-grained control over the agent's lifecycle.

[**Read the full Agno analysis here &raquo;**](1b-framework-analysis/agno.md)

