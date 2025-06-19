# Research Prompt: Investigating Framework Adoption in AI Coding Agents

## 1. Objective

To conduct a deep-dive investigation into why prominent open-source AI coding agents (such as Aider, OpenHands, Devin, etc.) often choose to build bespoke, custom frameworks instead of adopting established general-purpose agentic frameworks like LangGraph, Google ADK, or Agno. The goal is to identify the specific technical, performance, or philosophical reasons that drive this decision.

## 2. Key Questions to Answer

1.  **Technical Justifications:** What are the primary technical reasons cited by the developers of major open-source coding agents for building their own frameworks? Look for discussions around:
    *   The need for tight integration with IDEs and local file systems.
    *   Specialized state management requirements for long-running, iterative coding tasks.
    *   The necessity for fine-grained control over the agent's execution loop and tool interactions.

2.  **Performance and Control:** Do general-purpose frameworks introduce unacceptable performance overhead (latency, memory) for the rapid feedback loops required in coding (e.g., linting, testing, debugging)?

3.  **Limitations of General Frameworks:** What specific limitations or architectural constraints in LangGraph, ADK, or Agno make them less suitable for building a production-grade coding agent?

4.  **Counter-Examples:** Are there any notable open-source coding agents that *are* successfully built on top of LangGraph, ADK, or Agno? If so, how do they address the potential limitations?

5.  **Historical Context:** Did the development of these custom frameworks pre-date the maturity of the major general-purpose agentic frameworks? Is this a trend that is likely to change as frameworks like LangGraph and ADK evolve?

## 3. Methodology

1.  **Primary Source Analysis:**
    *   Search the official blogs, personal websites, and social media (e.g., Twitter, LinkedIn) of the creators and core contributors of prominent coding agents (Aider, OpenHands, Cognition AI's Devin, etc.).
    *   Review conference talks, podcast interviews, and published papers from these development teams.

2.  **Community and Code Analysis:**
    *   Analyze GitHub issues, pull requests, and discussion forums for these projects. Search for keywords like "architecture," "framework," "refactor," "LangChain," "ADK," "performance," and "state management."
    *   Look for any early-stage branches or discussions where the use of a general-purpose framework was considered and later abandoned.

3.  **Comparative Analysis:**
    *   Search for articles, blog posts, or academic papers that explicitly compare the trade-offs of using general-purpose agent frameworks versus building custom solutions for specialized domains like software engineering.

## 4. Deliverables

1.  **A Summarized Report:** A document that synthesizes the findings and provides a clear list of the top 3-5 reasons why developers of coding agents opt for custom frameworks.
2.  **A List of Limitations:** A bulleted list of specific, cited limitations of general-purpose frameworks when applied to coding tasks.
3.  **A List of Counter-Examples:** A list of any open-source coding agents that *do* use LangGraph, ADK, or Agno, with links to their repositories and any relevant documentation.
4.  **Annotated Bibliography:** A collection of links to all source materials (blog posts, talks, GitHub discussions) with a brief one-sentence summary of the key insight from each source.