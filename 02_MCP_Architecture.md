# MCP Architecture

## Complete Architecture

```
User
  │
  ▼
LLM
  │
  ▼
Agent Framework
  │
  ▼
MCP Client
  │
  ▼
MCP Server
  │
  ▼
External API / Database / Service
```

---

# Components

## 1. User

- Gives instructions to the AI.
- Example:
  - "Summarize this PDF."
  - "Create a GitHub issue."

---

## 2. LLM (Large Language Model)

Examples:

- GPT
- Claude
- Gemini
- Llama

Responsibilities:

- Understand user intent
- Reason about the request
- Decide whether a tool is required
- Generate responses

Cannot directly call external APIs.

---

## 3. Agent Framework

Examples:

- LangGraph
- LangChain
- Claude Desktop

Responsibilities:

- Orchestrates workflow
- Breaks complex tasks into steps
- Chooses tools
- Maintains conversation state

---

## 4. MCP Client

Responsibilities:

- Connects to MCP Servers
- Discovers available tools
- Sends requests
- Receives responses

Acts as a bridge between the LLM and MCP Server.

---

## 5. MCP Server

Responsibilities:

- Exposes Tools
- Exposes Resources
- Exposes Prompts
- Executes Python functions
- Communicates with external systems

---

## 6. External Services

Examples:

- GitHub
- Google Drive
- Slack
- Notion
- Wikipedia
- Databases

Perform the actual work.

---

# Request Flow

```
User

↓

LLM

↓

Agent Framework

↓

MCP Client

↓

MCP Server

↓

External API

↓

MCP Server

↓

MCP Client

↓

LLM

↓

User
```

---

# Responsibilities

| Component | Responsibility |
|-----------|----------------|
| User | Gives request |
| LLM | Understands & reasons |
| Agent Framework | Plans execution |
| MCP Client | Communicates with server |
| MCP Server | Executes tools |
| External API | Performs actual task |

---

# Standard vs Changeable

## Always Same

- MCP Client
- MCP Server
- JSON-RPC
- Tools
- Resources
- Prompts

---

## Can Change

- LLM (GPT, Claude, Gemini)
- Agent Framework (LangGraph, LangChain)
- External APIs (GitHub, Slack, Drive)
- Transport (stdio, HTTP)

---

# Key Points

- LLM decides **which tool** to use.
- MCP Client communicates with the server.
- MCP Server executes the requested tool.
- External APIs perform the actual work.
- Results return through the same path.

---

# Interview Questions

### What is the role of an MCP Client?

Connects to MCP Servers, discovers tools, sends requests, and receives responses.

---

### What is the role of an MCP Server?

Exposes tools/resources/prompts and executes requests.

---

### Does the LLM call APIs directly?

No.

It communicates through the MCP Client and MCP Server.

---

### Who chooses the tool?

LLM.

---

### Who executes the tool?

MCP Server.

---

# Revision

- User → Request
- LLM → Reasoning
- Agent Framework → Planning
- MCP Client → Communication
- MCP Server → Execution
- External API → Actual Work
