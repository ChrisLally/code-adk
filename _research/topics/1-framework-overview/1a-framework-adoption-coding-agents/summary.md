# Summary: Framework Adoption in AI Coding Agents

## Objective

This report synthesizes findings on why prominent AI coding agents like Aider, OpenHands, and Devin are built on bespoke frameworks, despite the availability of mature general-purpose agentic frameworks such as LangGraph, Google ADK, and Agno.

## Key Findings: Why Custom Frameworks Dominate

The decision to build custom frameworks is a calculated engineering necessity driven by the unique demands of the software development domain. Five primary factors were identified:

1.  **Fine-Grained Execution Control:** Coding is an iterative, non-linear process. Custom frameworks provide precise control over the execution loop, error handling, and context management. Aider's **Architect/Editor model**, which separates high-level planning from low-level code editing, is a prime example of a specialized pipeline that is difficult to implement efficiently in a generalist framework.

2.  **Specialized State Management:** Software development requires tracking a complex state across thousands of steps, including file versions, test outcomes, and strategic plans. Custom solutions, like the **event stream architecture** in OpenHands, are purpose-built for this, whereas general frameworks offer more generic state models ill-suited to the domain.

3.  **Deep Environmental Integration:** Agents need a tight, low-level connection to the developer's environment (filesystem, Git, shell). Custom frameworks treat this as a first-class component, enabling seamless, low-latency interactions that are fundamental to the workflow, such as Aider's "Git-native" approach.

4.  **Performance and Latency Sensitivity:** The rapid **edit-test-debug cycle** is critical to developer productivity. General-purpose frameworks can introduce a "framework tax" in latency and memory. Bespoke solutions are optimized for the minimal resource footprint required for a fluid pair-programming experience.

5.  **Historical Timing and Framework Maturity:** The development of today's leading coding agents largely predates the maturity of frameworks like LangGraph (relaunched early 2024), Google ADK (released March 2025), and Agno. Building a custom solution was initially the only viable path.

## Limitations of General-Purpose Frameworks

-   **Abstraction Overhead:** General frameworks introduce abstractions that add complexity and performance overhead for the specific, often linear, tasks of a coding agent.
-   **Inflexible Primitives:** They lack native, coding-specific primitives for tasks like syntax-aware diffing, code parsing, or deep IDE integration.
-   **Generic State Models:** Their state management is not optimized for the file-centric and history-dependent nature of software development.

## The Hybrid Future: A Role for General Frameworks

Despite the dominance of custom builds for generalist agents, a clear trend shows general-purpose frameworks being adopted for more constrained, auxiliary coding tasks.

-   **Uber's "AutoCover"** uses **LangGraph** to orchestrate a multi-agent system for automated unit test generation.
-   **Replit** uses **LangGraph** to power its AI code generation agent within its controlled IDE environment.

This suggests a future hybrid ecosystem where conversational, generalist agents remain on custom frameworks, while specialized, workflow-driven agents (for test generation, dependency updates, etc.) are built on general frameworks and integrated into CI/CD pipelines.

## Conclusion

The preference for custom frameworks in AI coding agents is a deliberate choice driven by the need for performance, control, and deep integration with the developer environment—requirements that general-purpose frameworks are not currently optimized to meet. While this trend will likely continue for generalist agents, a parallel trend of using frameworks like LangGraph for specialized, automatable coding tasks is emerging, pointing toward a more diverse and hybrid future.