# Model Context Protocol (MCP) - Basics

> Beginner-friendly notes covering the fundamentals of MCP.

---

# Table of Contents

1. What is MCP?
2. Why was MCP introduced?
3. Problems without MCP
4. API vs MCP
5. How MCP Works
6. Key Terminologies
7. MCP Ecosystem
8. MCP vs RAG
9. Advantages of MCP
10. Important Takeaways
11. Interview Questions

---

# 1. What is MCP?

**MCP (Model Context Protocol)** is an **open standard** that allows AI applications (LLMs) to communicate with external tools, applications, and data sources using a common protocol.

Instead of teaching an AI how every API works, developers only need to teach the AI how MCP works.

---

# 2. Why was MCP introduced?

Before MCP:

Every application exposed its own API.

Examples:

- GitHub API
- Slack API
- Google Drive API
- Notion API

Each API had:

- Different authentication
- Different request format
- Different response format
- Different documentation

Every AI had to learn every API separately.

This created a fragmented (broken into many incompatible pieces) ecosystem.

---

# Problem Without MCP

```
                AI

      ↙       ↓       ↘

 GitHub API  Slack API  Drive API

Different rules for every integration
```

Each integration had to be built separately.

---

# Solution With MCP

```
              AI

               │

          MCP Client

               │

        MCP Standard

               │

   ┌────────┬────────┬────────┐

 GitHub   Slack   Drive   Notion

       MCP Servers
```

The AI only understands MCP.

Each application exposes an MCP Server.

---

# 3. Why is MCP Better?

Instead of:

```
AI → GitHub API

AI → Slack API

AI → Drive API
```

We now have:

```
AI

↓

MCP Client

↓

MCP Server

↓

External API
```

One communication standard.

Many applications.

---

# 4. What is an API?

API (Application Programming Interface)

An API allows one software application to communicate with another.

Example:

```
Weather App

↓

Weather API

↓

Temperature Data
```

API = Communication interface between software systems.

---

# 5. API vs MCP

| API | MCP |
|------|-----|
| Connects software to software | Connects AI to tools |
| Different for every application | One common standard |
| Application-specific | AI-specific protocol |
| Different documentation | Same communication protocol |

---

# 6. Open Standard

An **Open Standard** is a publicly available specification that anyone can implement.

Examples:

- HTTP
- HTML
- USB
- MCP

Benefits:

- No vendor lock-in
- Interoperability (different systems working together)
- Easy adoption

---

# 7. MCP Ecosystem

Main Components:

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
```

Each component has a specific responsibility.

---

# 8. What is an LLM?

LLM = Large Language Model

Examples:

- GPT
- Claude
- Gemini
- Llama

Responsibilities:

- Understand natural language
- Reason
- Generate responses
- Decide whether tools are needed

An LLM **does not directly execute APIs**.

---

# 9. What is Agentic AI?

Agentic AI refers to AI systems that can:

- Plan tasks
- Break problems into smaller steps
- Use external tools
- Make decisions
- Execute multi-step workflows

Example:

```
Book a flight

↓

Search flights

↓

Compare prices

↓

Book ticket

↓

Send confirmation
```

---

# 10. What is an SDK?

SDK = Software Development Kit

A collection of libraries and utilities that help developers build applications.

Example:

Python MCP SDK

Provides:

- ClientSession
- FastMCP
- stdio_client

Without writing everything from scratch.

---

# 11. What is an Adapter?

Adapter = Translator

It converts one interface into another.

Example:

```
GitHub API

↓

GitHub MCP Server

↓

MCP Client
```

The GitHub MCP Server acts as an adapter.

---

# 12. What is a Sandbox?

Sandbox = An isolated (separate and safe) environment where code runs without affecting the real system.

Purpose:

- Security
- Safe testing
- Prevent damage

---

# 13. MCP vs RAG

## MCP

Purpose:

Perform actions.

Examples:

- Push GitHub commit
- Send Email
- Search Wikipedia

Uses:

- Tools
- Resources
- Prompts

---

## RAG

Purpose:

Retrieve information before answering.

Example:

```
Question

↓

Search Documents

↓

Relevant Information

↓

LLM

↓

Answer
```

RAG improves knowledge.

It does **not** execute actions.

---

# MCP + RAG

They work together.

Example:

```
User

↓

LLM

↓

RAG

↓

Retrieve Company Docs

↓

MCP

↓

Create Jira Ticket

↓

Answer User
```

---

# 14. Advantages of MCP

- One protocol for many tools
- Dynamic tool discovery
- Standard communication
- Easier integrations
- Better scalability
- Vendor independent
- Extensible (easy to add new tools)

---

# 15. Key Terms

| Term | Meaning |
|------|---------|
| API | Interface for software communication |
| MCP | Standard protocol for AI-tool communication |
| SDK | Developer toolkit |
| Adapter | Converts one interface into another |
| LLM | Large Language Model |
| Agentic AI | AI capable of planning and using tools |
| Sandbox | Safe isolated environment |
| Integration | Connecting different systems |
| Fragmented | Broken into incompatible pieces |
| Autonomy | Ability to act independently |
| Orchestrating | Managing the sequence of tasks |

---

# 16. Key Takeaways

✅ MCP is a communication standard.

✅ MCP does not replace APIs.

✅ MCP sits between AI and APIs.

✅ AI learns MCP once instead of learning every API.

✅ MCP makes AI integrations easier and scalable.

---

# 17. Interview Questions

### What is MCP?

An open standard that allows AI applications to communicate with external tools through a common protocol.

---

### Why do we need MCP?

To eliminate the need for AI to integrate separately with every API.

---

### Does MCP replace APIs?

No.

It standardizes access to APIs.

---

### What is the difference between API and MCP?

API connects software to software.

MCP connects AI to tools using a common standard.

---

### Can MCP work with RAG?

Yes.

RAG retrieves information.

MCP performs actions.

They complement each other.

---

# Revision (30 Seconds)

- MCP = Standard protocol for AI.
- API = Interface between software.
- LLM understands language.
- Agentic AI plans tasks.
- SDK provides libraries.
- Adapter translates APIs into MCP.
- Sandbox provides safe execution.
- RAG retrieves knowledge.
- MCP executes actions.
