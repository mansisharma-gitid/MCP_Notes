# Building an MCP Client

## Step 1: Import Libraries

```python
from mcp import ClientSession, StdioServerParameters
from mcp.client.stdio import stdio_client
```

Imports the required client components.

---

## Step 2: Configure Server

```python
server_params = StdioServerParameters(
    command="python",
    args=["calculator_server.py"]
)
```

Specifies **how to start the MCP Server**.

---

## Step 3: Start Communication

```python
async with stdio_client(server_params) as (read, write):
```

- Starts the server
- Creates `read` and `write` communication streams

---

## Step 4: Create Session

```python
async with ClientSession(read, write) as session:
```

Creates a communication session with the server.

---

## Step 5: Initialize Session

```python
await session.initialize()
```

Performs the MCP handshake.

Must be called before using tools.

---

## Step 6: Discover Tools

```python
tools = await load_mcp_tools(session)
```

Loads all tools exposed by the server.

---

## Step 7: Bind Tools

```python
llm.bind_tools(tools)
```

Makes the LLM aware of available tools.

---

# Complete Flow

```
Import Libraries

↓

Server Parameters

↓

stdio_client()

↓

ClientSession()

↓

initialize()

↓

load_mcp_tools()

↓

bind_tools()

↓

LLM Uses Tools
```

---

# Standard vs Changeable

## Standard

- ClientSession
- StdioServerParameters
- stdio_client()
- initialize()
- load_mcp_tools()
- bind_tools()

## Changeable

- Server file
- Command
- Arguments
- LLM
- Transport

---

# Common Mistakes

❌ Forget `initialize()`

→ Session isn't ready.

❌ Forget `load_mcp_tools()`

→ Client doesn't discover tools.

❌ Forget `bind_tools()`

→ LLM can't use tools.

---

# Interview Questions

**What creates the client session?**

`ClientSession()`

**What starts communication?**

`stdio_client()`

**Why is `initialize()` required?**

To establish the MCP session.

**What does `load_mcp_tools()` do?**

Discovers available tools.

**What does `bind_tools()` do?**

Makes tools available to the LLM.

---

# Revision

- `StdioServerParameters` → Server config
- `stdio_client()` → Start communication
- `ClientSession()` → Create session
- `initialize()` → Handshake
- `load_mcp_tools()` → Discover tools
- `bind_tools()` → LLM can use tools
