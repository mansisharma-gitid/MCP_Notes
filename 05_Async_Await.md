# Async & Await in MCP

## What is Asynchronous Programming?

Asynchronous programming allows a program to perform other tasks while waiting for a slow operation (e.g., API call, file read).

It improves efficiency by avoiding unnecessary waiting.

---

# Why is Async Used in MCP?

Operations like:

- Starting a server
- Calling APIs
- Reading files
- Waiting for responses

take time.

Instead of blocking the program, async allows other tasks to continue.

---

# async

```python
async def main():
```

### Purpose

Marks a function as asynchronous.

Inside an async function, you can use `await`.

---

# await

```python
await session.initialize()
```

### Purpose

Pauses the current function until the awaited task finishes.

Other asynchronous tasks can continue running.

---

# async with

```python
async with ClientSession(read, write) as session:
```

### Purpose

- Opens a resource.
- Automatically closes it when finished.
- Prevents resource leaks.

Used for:

- ClientSession
- stdio_client
- File handling
- Database connections

---

# Event Flow

```
Start async function

↓

Open resource

↓

Wait for operation

↓

Continue execution

↓

Close resource automatically
```

---

# Why Not Use Normal Functions?

Normal functions:

```
Start Task

↓

Wait...

↓

Continue
```

Everything stops while waiting.

---

Async functions:

```
Start Task

↓

Wait...

↓

Other tasks continue

↓

Resume when ready
```

More efficient.

---

# Where is Async Used in MCP?

- stdio_client()
- ClientSession()
- initialize()
- Tool calls
- API requests

---

# Standard vs Changeable

## Standard

- async
- await
- async with

These are Python keywords.

---

## Changeable

- Function names
- Awaited operations
- Resources being managed

---

# Common Mistakes

❌ Using `await` outside an async function

Result:
SyntaxError

---

❌ Forgetting `await`

Result:
Returns a coroutine instead of executing it.

---

❌ Forgetting `async with`

Result:
Resources may not close properly.

---

# Interview Questions

### What does `async` do?

Declares an asynchronous function.

---

### What does `await` do?

Waits for an asynchronous operation to complete.

---

### Why use `async with`?

To automatically manage opening and closing of resources.

---

### Why does MCP use async?

To efficiently handle I/O operations like server communication and API calls.

---

# Revision

- `async` → Creates async function
- `await` → Waits for task
- `async with` → Opens & closes resources safely
- Async improves efficiency
- Widely used for I/O operations in MCP
