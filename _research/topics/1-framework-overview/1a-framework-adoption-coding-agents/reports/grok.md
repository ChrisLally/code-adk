Research Report: Why Open-Source AI Coding Agents Build Custom Frameworks
Objective
This report investigates why prominent open-source AI coding agents, such as Aider, OpenHands, and Devin, opt to develop bespoke frameworks rather than adopt established general-purpose agentic frameworks like LangGraph, Google ADK, or Agno. It explores technical, performance, and philosophical reasons driving these decisions, identifies limitations of general-purpose frameworks, and examines counter-examples.
Key Findings: Top 3-5 Reasons for Custom Frameworks

Tight Integration with Development Environments:

AI coding agents require seamless integration with IDEs (e.g., VS Code), local file systems, and development tools like linters, compilers, and testing frameworks. Custom frameworks allow developers to tailor the agent’s execution loop to interact directly with these environments, minimizing latency and ensuring compatibility. For example, OpenHands (formerly OpenDevin) runs code in isolated Docker containers for safety and integrates with IDE-like interfaces, a level of control difficult to achieve with general-purpose frameworks like Agno, which lacks native IDE-specific workflows.


Specialized State Management for Iterative Coding:

Coding tasks involve long-running, iterative processes with complex state management, such as tracking file changes, maintaining context across edits, and handling incremental feedback from tests or linters. Custom frameworks provide fine-grained control over state persistence and context management, optimized for coding workflows. Aider’s diff-based state management is purpose-built for real-time file editing, unlike Agno’s generic memory drivers (e.g., Pinecone, LanceDb), which are better suited for conversational or knowledge-based tasks.


Performance Optimization for Rapid Feedback Loops:

Coding agents demand low-latency feedback for tasks like code generation, linting, and debugging. General-purpose frameworks introduce overhead due to their abstractions. While Agno boasts ~2μs agent instantiation and ~3.75 KiB memory usage (10,000x faster and 50x lighter than LangGraph), its multi-agent abstractions and lack of coding-specific primitives still add unnecessary complexity for single-agent coding tasks. Developers of Aider and OpenHands prioritize lightweight, custom architectures to ensure rapid iteration, avoiding the overhead of frameworks like Google ADK or LangGraph.


Philosophical Preference for Simplicity and Control:

Open-source coding agent developers favor minimal, transparent architectures over the heavy abstractions of frameworks like LangGraph, Google ADK, or Agno. This aligns with the “pure code” approach, avoiding framework lock-in and maintaining full control over agent behavior. Reddit discussions highlight frustration with LangChain’s complexity (a precursor to LangGraph), and Agno’s multi-agent paradigm is seen as overkill for linear coding workflows, driving developers toward custom solutions.


Historical Timing and Framework Maturity:

The development of coding agents like Aider (2023) and OpenHands (2024) predates the maturity of LangGraph (2024), Google ADK (2025), and Agno (general availability March 2025). Early projects required custom solutions due to the absence of robust general-purpose frameworks. Despite Agno’s recent performance advantages, the momentum of custom architectures and community familiarity with them slows adoption.



Limitations of General-Purpose Frameworks for Coding Tasks

Overhead from Abstractions:

LangGraph’s graph-based architecture and Agno’s multi-agent orchestration add computational overhead for single-agent coding tasks. Agno’s Agent and Team classes, while lightweight (~2μs instantiation), introduce complexity unsuitable for real-time code editing or rapid iteration compared to custom frameworks.


Steep Learning Curve:

Frameworks like LangGraph, Google ADK, and Agno have steep learning curves due to complex APIs and documentation gaps. Agno’s cookbook examples have been criticized as poorly written, deterring developers who prioritize rapid development with clear, coding-specific guides.


Limited IDE and File System Integration:

General frameworks lack native support for deep IDE and local file system integration, critical for coding agents. Google ADK focuses on cloud-based workflows, and Agno’s tool ecosystem (e.g., DuckDuckGoTools) does not include coding-specific primitives like linters or build systems, unlike OpenHands’ Docker-based execution.


Inflexible State Management:

LangGraph’s directed acyclic graph (DAG) model and Agno’s generic memory drivers (e.g., vector stores) are rigid for the dynamic, iterative nature of coding tasks. Custom frameworks like Aider’s offer specialized state handling for file edits and test recovery, which general frameworks cannot replicate efficiently.


Performance Bottlenecks:

Google ADK and LangGraph, optimized for multi-agent or cloud systems, introduce latency and memory overhead. While Agno’s performance (~3.75 KiB memory) is superior, its general-purpose design still requires customization for coding workflows, which developers avoid by building tailored solutions.


Lack of Coding-Specific Primitives (Agno-Specific):

Agno lacks syntax-aware diffing, code parsing, or IDE event handling, essential for coding agents. Its focus on multimodal inputs and multi-agent teaming (Agent Teams 2.0) is better suited for non-coding tasks like finance or logistics.



Counter-Examples: Coding Agents Using General-Purpose Frameworks

Replit’s AI Coding Agent (LangGraph):

Replit leverages LangGraph’s graph-based workflows for complex code generation and multi-agent coordination, using LangSmith for monitoring and persistence. Repository: langchain-ai/langgraph.


Qodo’s Coding Assistant (LangGraph):

Qodo (formerly Codium) uses LangGraph for its coding assistant, citing its flexibility for structured and open-ended workflows. Documentation: Qodo Blog.


Experimental Projects with Agno:

No major open-source coding agents (e.g., Aider, OpenHands, Devin) use Agno. Experimental projects include:
A GitHub-based docstring generator using Agno with GPT-4o and custom tools (AI-Agents/agno).
Proof-of-concept multi-agent code analysis systems leveraging Agno’s Team API for code review and test generation.





No coding agents were found using Google ADK, likely due to its recent release (April 2025) and cloud-centric design.
Historical Context and Future Trends

Historical Context:

Early coding agents like Aider (2023) and OpenHands (2024) predated LangGraph (2024), Google ADK (2025), and Agno (March 2025). The lack of mature general-purpose frameworks necessitated custom solutions. Agno’s late entry limited its influence on established projects.


Future Trends:

LangGraph and Agno’s evolving ecosystems may increase adoption for enterprise coding agents. Agno’s performance (~2μs instantiation, 23.9k GitHub stars) and tool decorators (e.g., human-in-the-loop) show promise, but its lack of coding-specific primitives and documentation gaps hinder uptake. Custom frameworks are likely to persist in open-source communities due to preferences for simplicity and performance.



Conclusion
Open-source AI coding agents like Aider, OpenHands, and Devin build custom frameworks for tight IDE integration, specialized state management, and performance optimization. General-purpose frameworks like LangGraph, Google ADK, and Agno introduce overhead, complexity, and limitations in coding-specific workflows. Agno’s lightweight design (~2μs instantiation, ~3.75 KiB memory) is promising, but its general-purpose abstractions and lack of coding primitives deter adoption. While Replit and Qodo successfully use LangGraph, and experimental projects explore Agno, historical timing and philosophical preferences for minimalism sustain custom frameworks. As general frameworks mature, adoption may grow, but custom solutions will likely dominate performance-critical coding tasks.
Annotated Bibliography

Modal Blog: Open-source AI agents (2025-03-15):

Insight: Discusses OpenHands’ Docker-based execution and Aider’s terminal-based code generation, highlighting custom architectures for IDE integration.


Qodo Blog: Why we chose LangGraph to build our coding agent (2025-02-10):

Insight: Explains Qodo’s adoption of LangGraph for its flexible, node-based architecture suitable for coding workflows.


APIpie: Top 10 Open-Source AI Agent Frameworks of May 2025 (2025-05-01):

Insight: Compares Agno’s lightweight performance (~2μs instantiation, ~3.75 KiB memory) to LangGraph’s heavier architecture.


Reddit: r/LangChain - OpenAI’s new framework for Agents (2024-12-20):

Insight: Community frustration with LangChain’s complexity drives preference for custom frameworks in coding agents.


Firecrawl: The Best Open Source Frameworks For Building AI Agents in 2025 (2025-04-10):

Insight: Notes LangGraph’s enterprise adoption but highlights its 2024 release, postdating early custom frameworks.


Composio: OpenAI Agents SDK vs LangGraph vs Autogen vs CrewAI (2025-03-01):

Insight: Highlights LangGraph’s steep learning curve, less ideal for rapid coding iterations.


Ida Silfverskiöld: Agentic AI: Comparing New Open-Source Frameworks (2025-04-05):

Insight: Criticizes LangGraph’s complexity, favoring lightweight frameworks like Agno for general tasks but not coding.


getstream.io: Best 5 Frameworks To Build Multi-Agent AI Applications (2025-02-25):

Insight: Details LangGraph’s enterprise use by Replit for stateful coding agents.


GitHub - agno-agi/agno (2025-05-21):

Insight: Describes Agno’s multi-agent framework with ~2μs instantiation, but lacks coding-specific features.


Analytics Vidhya: How to Build MultiModal AI Agents Using Agno (2025-03-24):

Insight: Highlights Agno’s performance (10,000x faster than LangGraph) but focuses on non-coding tasks like finance.


Reddit: r/AI_Agents - What frameworks are you using? (2025-04-17):

Insight: Criticizes Agno’s Agent class complexity and poor documentation, explaining custom framework preference for coding.


X Post by @ashpreetbedi (2025-03-27):

Insight: Announces Agno’s general availability with 22k GitHub stars, but no coding agent adoption mentioned.



