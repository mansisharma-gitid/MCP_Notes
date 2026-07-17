# JSON-RPC

## What is JSON-RPC?

JSON-RPC is the communication protocol used by the MCP Client and MCP Server.

It defines **how requests and responses are exchanged**.

---

## Why is it Needed?

- Standard communication
- Structured messages
- Language-independent
- Easy to parse

---

## Request Flow

```
Client

↓

JSON-RPC Request

↓

Server

↓

Execute Tool

↓

JSON-RPC Response

↓

Client
```

---

## Request Example

```json
{
  "method": "add",
  "params": {
    "a": 10,
    "b": 20
  },
  "id": 1
}
```

---

## Response Example

```json
{
  "result": 30,
  "id": 1
}
```

---

## Error Example

```json
{
  "error": "Tool not found",
  "id": 1
}
```

---

## Main Fields

| Field | Purpose |
|--------|---------|
| method | Tool to execute |
| params | Input arguments |
| result | Output |
| error | Failure message |
| id | Matches request & response |

---

## Standard vs Changeable

### Standard

- JSON format
- Request/Response structure
- `method`
- `params`
- `result`
- `error`
- `id`

### Changeable

- Tool name
- Parameters
- Return value

---

## Interview Questions

**What is JSON-RPC?**

A protocol for communication between the MCP Client and MCP Server.

**What does `method` represent?**

The tool/function to execute.

**Why is `id` used?**

To match the response with the correct request.

---

## Revision

- JSON-RPC = Communication protocol
- `method` = Tool name
- `params` = Inputs
- `result` = Output
- `error` = Failure
- `id` = Request identifier
