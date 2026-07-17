# Resources & Prompts in MCP

## Resources

### What are Resources?

Resources provide **read-only information** to the LLM.

They are used to **retrieve data**, not perform actions.

---

### Purpose

- Share documentation
- Read files
- Access database records
- Provide reference information

---

### Example

```python
@mcp.resource("docs://guide")
def guide():
    return "Welcome to the MCP Guide."
```

---

## Prompts

### What are Prompts?

Prompts are **predefined reusable instructions** that help the LLM perform a task consistently.

Instead of writing the same prompt repeatedly, you create it once and reuse it.

---

### Purpose

- Standardize instructions
- Save prompt-writing time
- Improve consistency
- Guide the LLM

---

### Example

```python
@mcp.prompt()
def summarize(text: str):
    return f"Summarize this:\n{text}"
```

---

# Tool vs Resource vs Prompt

| Feature | Tool | Resource | Prompt |
|---------|------|----------|--------|
| Purpose | Perform action | Provide data | Provide instruction |
| Read-only | ❌ | ✅ | ✅ |
| Executes code | ✅ | ❌ | ❌ |
| Returns | Result | Information | Prompt template |

---

# When to Use

### Tool

Use when you want to:

- Send email
- Search Wikipedia
- Create GitHub issue
- Update database

---

### Resource

Use when you want to:

- Read documentation
- Get configuration
- Access FAQs
- Retrieve knowledge

---

### Prompt

Use when you want to:

- Summarize text
- Translate content
- Review code
- Generate emails

---

# Flow

```
User

↓

LLM

↓

Need Action?
↓

Tool

----------------

Need Information?
↓

Resource

----------------

Need Instructions?
↓

Prompt
```

---

# Standard vs Changeable

## Standard

- `@mcp.tool()`
- `@mcp.resource()`
- `@mcp.prompt()`

---

## Changeable

- Names
- Parameters
- Returned content
- Business logic

---

# Interview Questions

### What is a Resource?

Read-only information exposed by an MCP Server.

---

### What is a Prompt?

A reusable instruction template for the LLM.

---

### Difference between Resource and Prompt?

- **Resource** → Gives information.
- **Prompt** → Gives instructions.

---

### Difference between Tool and Resource?

- **Tool** → Performs an action.
- **Resource** → Only provides information.

---

# Revision

- **Tool** → Action ✅
- **Resource** → Information 📖
- **Prompt** → Instruction 📝

**Easy Memory Trick:**

- **Tool = Do**
- **Resource = Know**
- **Prompt = Tell**
