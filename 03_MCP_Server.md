# MCP Server

## What is an MCP Server?

An **MCP Server** exposes tools, resources, and prompts that AI applications can discover and use.

It acts as a bridge between the MCP Client and external systems (APIs, databases, files, etc.).

---

# Responsibilities

- Expose Tools
- Expose Resources
- Expose Prompts
- Execute business logic
- Connect to external APIs
- Return results to the client

---

# Creating an MCP Server

```python
from fastmcp import FastMCP

mcp = FastMCP("Calculator")
```

### Explanation

- `FastMCP` → Class used to create an MCP Server.
- `"Calculator"` → Server name (can be anything).

---

# Registering a Tool

```python
@mcp.tool()
def add(a: int, b: int):
    return a + b
```

### Purpose

Registers the function as an MCP Tool.

Without `@mcp.tool()`, the client cannot discover or call the function.

---

# Multiple Tools

```python
@mcp.tool()
def add(a, b):
    return a + b

@mcp.tool()
def subtract(a, b):
    return a - b
```

Each decorated function becomes a separate tool.

---

# Helper Functions

```python
def calculate(a, b):
    return a + b
```

Normal functions are **private**.

They help other tools but are **not exposed** to clients.

---

# Starting the Server

```python
mcp.run(transport="stdio")
```

### Purpose

- Starts the MCP Server.
- Begins listening for client requests.

Without `run()`, the server never starts.

---

# Server Flow

```
Create Server

↓

Register Tools

↓

Run Server

↓

Wait for Requests

↓

Execute Tool

↓

Return Result
```

---

# Components

| Component | Purpose |
|-----------|---------|
| FastMCP | Creates the server |
| @mcp.tool() | Registers a tool |
| Function | Business logic |
| mcp.run() | Starts the server |

---

# Standard vs Changeable

## Standard

- `FastMCP`
- `@mcp.tool()`
- `mcp.run()`

These are part of the MCP SDK.

---

## Changeable

- Server name
- Tool names
- Parameters
- Return values
- Business logic
- External APIs used

---

# Common Mistakes

❌ Forgetting `@mcp.tool()`

Result:
Tool won't be discoverable.

---

❌ Forgetting `mcp.run()`

Result:
Server never starts.

---

❌ Assuming every function becomes a tool

Only functions with `@mcp.tool()` are exposed.

---

# Interview Questions

### What is FastMCP?

A Python class used to create an MCP Server.

---

### What does `@mcp.tool()` do?

Registers a Python function as an MCP Tool.

---

### Can helper functions be called by the client?

No.

Only decorated functions are discoverable.

---

### What does `mcp.run()` do?

Starts the MCP Server and waits for client requests.

---

### Can a server have multiple tools?

Yes.

Every function decorated with `@mcp.tool()` becomes a separate tool.

---

# Revision

- `FastMCP` → Creates server
- `@mcp.tool()` → Registers tool
- Helper function → Private
- `mcp.run()` → Starts server
- One server → Many tools
- Only decorated functions are discoverable
