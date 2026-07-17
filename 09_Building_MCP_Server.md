# Building an MCP Server

## Step 1: Import SDK

```python
from fastmcp import FastMCP
```

Imports the FastMCP library.

---

## Step 2: Create Server

```python
mcp = FastMCP("Calculator")
```

Creates an MCP Server.

---

## Step 3: Register Tools

```python
@mcp.tool()
def add(a: int, b: int):
    return a + b
```

Registers `add()` as an MCP Tool.

---

## Step 4: Add More Tools

```python
@mcp.tool()
def subtract(a: int, b: int):
    return a - b
```

One server can have multiple tools.

---

## Step 5: Start Server

```python
mcp.run(transport="stdio")
```

Starts the server and waits for requests.

---

# Complete Flow

```
Import FastMCP

↓

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

# Standard vs Changeable

## Standard

- FastMCP
- @mcp.tool()
- mcp.run()

## Changeable

- Server name
- Tool names
- Parameters
- Business logic
- Transport

---

# Common Mistakes

❌ Forget `@mcp.tool()`

→ Tool won't be discoverable.

❌ Forget `mcp.run()`

→ Server won't start.

---

# Interview Questions

**What creates an MCP Server?**

`FastMCP()`

**How do you expose a function?**

`@mcp.tool()`

**How do you start the server?**

`mcp.run()`

---

# Revision

- `FastMCP()` → Create server
- `@mcp.tool()` → Register tool
- `mcp.run()` → Start server
- One server → Multiple tools
