# Problems with MCP at Scale

## Section I: The Expanding Attack Surface: A Deep Dive into MCP Security

The Model Context Protocol does not merely introduce new features; it introduces a new and expansive attack surface. Security within the MCP ecosystem is not an afterthought that can be fixed with patches but a fundamental, systemic weakness stemming from the protocol's core design. This design inverts traditional trust models, delegates critical security functions to developers, and creates numerous, often subtle, vectors for attack.

### 1.1 Systemic Flaw: The Inverted Trust Model and the Confused Deputy

MCP's greatest security failure is its inversion of the traditional API trust model. In a conventional REST API interaction, a client interacts with a static, well-defined contract. The client is in control. In the MCP model, this relationship is flipped: the client must dynamically trust the server to provide its own capabilities, descriptions, and even authentication endpoints at runtime. This creates a classic "confused deputy" problem, a long-standing security vulnerability where a program with legitimate authority (the MCP client, or "deputy") is tricked by an external entity (a malicious MCP server) into misusing its authority.

The protocol lacks a sufficient trust boundary, effectively asking clients to execute code and follow natural language instructions from potentially untrusted remote sources. This raises critical and often unanswerable questions for any developer implementing the protocol: "Who's running your MCP server? Can you trust it? Should your model trust it?". The entire premise of the catastrophic CVE-2025-6514 vulnerability rests on an MCP client blindly trusting and executing a server-provided OAuth endpoint, perfectly illustrating the real-world consequences of this flawed trust model.

## Section II: Tool Bloat and Performance Degradation

Beyond the stark architectural and security failures lies a more subtle but equally critical failure mode: the degradation of AI performance as the number of available tools increases. This phenomenon, termed "tool bloat," is not a simple bug but a fundamental limitation of current LLM architectures when applied within the MCP paradigm. It reveals that the protocol's approach to tool integration is conceptually unscalable.

## 2.1 Defining "Tool Bloat": More Tools, Less Intelligence

The core of the tool bloat problem is that every tool added to an AI agent's working context consumes valuable resources and increases the complexity of its decision-making process. Each tool's name, description, and parameters must be injected into the LLM's context window, leading to several negative consequences:

**Token Bloat:** LLM context windows are a finite and expensive resource. Loading descriptions for dozens or hundreds of tools can quickly exhaust this limit, increasing API costs and making it impossible to include other necessary information for the task at hand. Users have reported their context limits being maxed out simply by loading their available tools, rendering the agent unusable before a conversation even begins.

**Relevance Decay and Declining Accuracy:** More information is not always better. As the number of tools increases, the LLM's attention is spread thinly across many options, diluting the signal of the user's actual intent and increasing the probability of incorrect tool selection or parameter hallucination. Industry wisdom and empirical evidence suggest a practical limit of around 20 tools before performance degrades significantly.

**Latency:** The process of fetching, processing, and injecting the context for a large number of tools becomes a performance bottleneck, slowing down the agent's response time.

This problem is a direct consequence of the "obvious MCP approach," which encourages developers to create a granular tool for each individual action or API endpoint. While this seems simple at the micro level, it creates unmanageable complexity at the system level, resulting in agents that are slow, expensive, and unreliable.

## 2.2 The "Future Models" Fallacy: Why Cognitive Load is Not a Solvable Problem

A common counterargument to the problem of tool bloat is that it is a temporary technical limitation that will be solved by future models with larger context windows and more powerful reasoning capabilities. This has been identified as a fallacy that fundamentally misunderstands the nature of the problem.

The issue is not merely one of context window size but of cognitive load. Just as a human expert is less effective when forced to choose from a list of 100 subtly different options versus a curated set of 10 powerful ones, an LLM's decision-making quality degrades with excessive choice. This is a fundamental principle of information processing and decision theory that applies to both biological and artificial intelligence. Packing more tools into an even larger context window could actually worsen the problem by overloading the model's attention mechanism with even more distractors.

Therefore, better models will not solve tool bloat; they will simply be more effective when paired with a smaller, more thoughtfully designed set of tools. The analogy of a skilled carpenter is apt: they are more effective with a curated toolbox of essential, high-quality instruments, not by carrying the entire inventory of a hardware store.

## 2.3 Emerging Solutions: Workarounds for a Flawed Paradigm

The severity of the tool bloat problem has spurred the development of several sophisticated workarounds. It is crucial to recognize that these are not native features of MCP but rather external systems built to compensate for the protocol's conceptual scaling limitations.

**Elegant Tool Design:** This approach involves moving away from a one-to-one mapping of API endpoints to tools. Instead, developers build fewer, more powerful, and more abstract tools in-house that correspond to complete human tasks. For example, instead of separate tools for creating, updating, and sending an email draft, a single send_email tool with optional parameters can handle the entire workflow more efficiently.

**Context Engineering:** This strategy treats the context provided by MCP servers as raw material that must be processed through a data transformation pipeline before reaching the model. Techniques include deduplicating redundant information, using LLMs to summarize verbose outputs, prioritizing and truncating context to fit a token budget, and quarantining context for subtasks into separate threads.

**Multi-Agent Routing:** This architectural pattern involves a top-level "router" agent whose sole purpose is to receive a user query and delegate it to one of several specialized sub-agents, each equipped with a much smaller, domain-specific toolset.

**Retrieval-Augmented Generation for MCP (RAG-MCP):** This is the most advanced solution, adapting the RAG technique used for knowledge retrieval. Instead of loading all tools into the context, a RAG-MCP system first uses semantic retrieval to search a large external index of all available tools. It identifies the small subset of tools most relevant to the user's query and provides only those to the LLM. This drastically reduces prompt size, cuts cognitive load, and has been shown to more than triple tool selection accuracy in stress tests.

The very existence of these complex workarounds reveals a deep-seated issue. To make the MCP paradigm work at scale, one must build a second, sophisticated AI system (a retriever or a router agent) whose job is to manage the tools for the primary AI agent. This fundamentally undermines MCP's original promise of simplification. It indicates that a more intelligent mechanism for tool discovery and composition needs to be a first-class citizen of any future protocol, not a bolt-on fix for a paradigm that is otherwise unscalable.