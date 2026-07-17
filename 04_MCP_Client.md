# MCP Client

## What is an MCP Client?

An **MCP Client** connects to one or more MCP Servers, discovers available tools, sends requests, and receives responses.

It acts as the communication bridge between the LLM and the MCP Server.

---

# Responsibilities

- Connect to MCP Server
- Start communication
- Discover available tools
- Send tool requests
- Receive responses

---

# Main Components

## 1. StdioServerParameters

```python
server_params = StdioServerParameters(
    command="python",
    args=["calculator_server.py"]
)
```

### Purpose

Stores information required to start the server.

### Parameters

- `command` → Program to execute
- `args` → Arguments passed to the program

Equivalent terminal command:

```bash
python calculator_server.py
```

---

## 2. stdio_client()

```python
async with stdio_client(server_params) as (read, write):
```

### Purpose

- Starts the server
- Creates communication pipes
- Returns:
  - `read`
  - `write`

---

## 3. ClientSession

```python
async with ClientSession(read, write) as session:
```

### Purpose

Creates a communication session between the client and server.

Without `ClientSession`, the client cannot communicate with the server.

---

## 4. initialize()

```python
await session.initialize()
```

### Purpose

Performs the MCP handshake.

Must be called before any tool request.

---

## Client Flow

```
Create Server Parameters

↓

Start Server

↓

Create read/write pipes

↓

Create Client Session

↓

Initialize Session

↓

Discover Tools

↓

Call Tool

↓

Receive Result
```

---

# Components

| Component | Purpose |
|-----------|---------|
| StdioServerParameters | Server startup information |
| stdio_client() | Starts server & creates communication |
| read | Receives data |
| write | Sends data |
| ClientSession | Creates communication session |
| initialize() | Performs MCP handshake |

---

# Standard vs Changeable

## Standard

- ClientSession
- initialize()
- StdioServerParameters
- stdio_client()

---

## Changeable

- command
- args
- Server file
- Transport

---

# Common Mistakes

❌ Forgetting `initialize()`

Result:
No communication with the server.

---

❌ Wrong command or args

Result:
Server won't start.

---

❌ Creating ClientSession without read/write

Result:
Session cannot be established.

---

# Interview Questions

### What is the role of an MCP Client?

Connects to MCP Servers, discovers tools, sends requests, and receives responses.

---

### What is ClientSession?

A communication session between the client and server.

---

### What does StdioServerParameters store?

The information required to start the server.

---

### What does stdio_client() do?

Starts the server and creates read/write communication streams.

---

### What does initialize() do?

Performs the handshake between the client and server.

---

# Revision

- `StdioServerParameters` → Server startup info
- `stdio_client()` → Starts server
- `read/write` → Communication pipes
- `ClientSession` → Communication session
- `initialize()` → Handshake
- Client → Communicates, Server → Executes
