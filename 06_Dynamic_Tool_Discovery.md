# Dynamic Tool Discovery

## What is Dynamic Tool Discovery?

Dynamic Tool Discovery is the process where an MCP Client automatically discovers all tools exposed by an MCP Server.

The client does **not** need to know tool names beforehand.

---

# Why is it Needed?

Without Dynamic Discovery:

- Client must hardcode every tool.
- Every new tool requires client updates.
- Difficult to maintain.

With Dynamic Discovery:

- Client automatically finds available tools.
- New tools become available without changing client code.

---

# How It Works

```
Client

↓

Connects to Server

↓

Asks:
"What tools do you have?"

↓

Server sends Tool List

↓

Client loads tools

↓

LLM can use them
```

---

# Example

Server:

```python
@mcp.tool()
def add(a: int, b: int):
    return a + b

@mcp.tool()
def subtract(a: int, b: int):
    return a - b
```

When the client connects, it automatically discovers:

```
add()

subtract()
```

No manual registration is needed on the client.

---

# load_mcp_tools()

```python
tools = await load_mcp_tools(session)
```

## Purpose

- Connects to the MCP Server.
- Fetches all available tools.
- Converts them into LLM-compatible tools.

---

# What Information is Discovered?

For every tool, the client receives:

- Tool name
- Description
- Parameters
- Parameter types
- Return type

Example:

```
Tool Name:
add

Description:
Adds two numbers.

Parameters:
a (int)
b (int)
```

---

# What Happens Next?

After discovery:

```python
llm.bind_tools(tools)
```

The LLM now knows:

- Which tools exist
- What each tool does
- Which parameters are required

---

# Dynamic Discovery Flow

```
Server Starts

↓

Registers Tools

↓

Client Connects

↓

Discovers Tools

↓

LLM Learns Tools

↓

User Requests Tool

↓

LLM Chooses Tool
```

---

# Advantages

- No hardcoding
- Easy to add new tools
- Automatic updates
- Better scalability
- Less maintenance

---

# Standard vs Changeable

## Standard

- Discovery process
- Tool metadata
- Tool registration
- MCP protocol

---

## Changeable

- Tool names
- Number of tools
- Parameters
- Descriptions
- Business logic

---

# Common Mistakes

❌ Forgetting `@mcp.tool()`

Result:
Tool won't be discovered.

---

❌ Assuming the client knows tools automatically

The client must perform Dynamic Tool Discovery first.

---

❌ Calling tools before discovery

Result:
LLM doesn't know available tools.

---

# Interview Questions

### What is Dynamic Tool Discovery?

The automatic process of discovering tools exposed by an MCP Server.

---

### Why is Dynamic Tool Discovery useful?

It removes the need to hardcode tool information in the client.

---

### What function is commonly used for Dynamic Tool Discovery?

```python
load_mcp_tools()
```

---

### Does the client need to know tool names beforehand?

No.

The server provides the tool information automatically.

---

# Revision

- Client automatically discovers tools.
- No hardcoding required.
- `load_mcp_tools()` loads all tools.
- Only `@mcp.tool()` functions are discoverable.
- Discovery happens before tool execution.
