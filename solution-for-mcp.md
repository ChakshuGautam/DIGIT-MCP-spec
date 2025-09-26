# Solution: Hierarchical Tools and Exploration Agents

## The Core Insight

The solution to MCP's tool bloat problem isn't fighting against scale—it's embracing hierarchy and intelligence. Instead of flat lists of hundreds of tools, we build layers and let agents explore.

[Source: @thdxr](https://x.com/thdxr/status/1969907981329260953)

---

### The Hierarchical Solution
```
✅ Start broad: get_billing_tools()
✅ Progressively refine: get_refund_tools()
✅ Specific action: get_refund_status_for_tx()
```

As @thdxr suggests: Group data models hierarchically. The LLM navigates from general to specific, like a human would browse folders.

---

## Key Insights from the Community

### 1. Operating System Design (@ccssmnn)
Design agents like an OS:
- **Launcher tool** to pick the right domain
- **Show methods** only after tool selection
- **Progressive disclosure** of complexity

### 2. Specialized Subagents (@TJkrusinski, @ken_wheeler)
- Break the system into specialized domains
- Each subagent handles specific use cases
- Orchestrate between agents as needed

### 3. State Machine Interface (@ken_wheeler)
```
State Machine → Operational Flow
   ↓
Subagents → Task-specific contexts
   ↓
Command Interface → Structured actions
```

### 4. Intent Classification (@_colemurray)
- Map use cases to data models
- Classify intent from queries
- Reduce search space with domain knowledge

### 5. Search + Fetch Pattern
A special case of hierarchical design:
- **Layer 1:** Search for relevant data models
- **Layer 2:** Fetch only what's needed
- Model only sees definitions it needs to know

[Source: @__morse](https://x.com/__morse/status/1969755575840874693)

## The Exploration Agent Pattern

Instead of loading all tools upfront, agents explore:

1. **Discovery Phase**
   - Agent asks: "What domains are available?"
   - Returns: Categories like billing, users, workflow

2. **Refinement Phase**
   - Agent selects: "billing"
   - Returns: Subcategories like payments, refunds, invoices

3. **Action Phase**
   - Agent picks specific tool
   - Executes with full context

---