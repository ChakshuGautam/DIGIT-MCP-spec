# Problems with MCP at Scale

## Section I: Security - The Inverted Trust Model

MCP inverts traditional API trust models. Instead of clients controlling static contracts, they must dynamically trust servers to provide capabilities, descriptions, and even authentication endpoints at runtime. This creates a "confused deputy" vulnerability where the MCP client can be tricked by malicious servers into misusing its authority.

The protocol lacks sufficient trust boundaries, asking clients to execute instructions from potentially untrusted sources. CVE-2025-6514 exemplifies this: MCP clients blindly trusting server-provided OAuth endpoints.

## Section II: Tool Bloat - Performance Degradation

### The Problem
Every tool added to an AI agent consumes context window resources and increases decision complexity:

**Token Bloat:** Loading dozens of tool descriptions exhausts context limits, increases costs, and leaves no room for actual conversation.

**Accuracy Decay:** More tools = diluted attention. LLMs spread focus across too many options, increasing incorrect selections. Practical limit: ~20 tools.

**Latency:** Fetching and processing many tools creates performance bottlenecks.

### The "Future Models" Fallacy
Larger context windows won't solve cognitive load. Like humans, LLMs perform worse with 100 choices vs 10 curated ones. This is fundamental information theory, not a technical limitation.

Better models will still need smaller, thoughtfully designed toolsets. A carpenter needs essential tools, not a hardware store inventory.

### Workarounds Revealing Deeper Issues

**Elegant Tool Design:** Combine multiple API endpoints into single, task-oriented tools.

**Context Engineering:** Process and compress MCP context before feeding to models.

**Multi-Agent Routing:** Router agents delegate to specialized sub-agents with smaller toolsets.

**RAG-MCP:** Use semantic retrieval to dynamically select relevant tools instead of loading all.

## The Core Issue

These workarounds expose MCP's fundamental flaw: to scale, you need sophisticated AI systems just to manage tools for your primary AI. This contradicts MCP's simplification promise.

Intelligent tool discovery and composition must be built-in, not bolted-on. The protocol's one-tool-per-API approach creates unmanageable complexity at scale.

## Bottom Line

MCP faces two critical failures:
1. **Security:** Inverted trust model creates systematic vulnerabilities
2. **Scalability:** Tool bloat makes the system unusable beyond ~20 tools

Both are architectural flaws, not bugs. They reveal that MCP's approach to tool integration is conceptually unscalable.