---
name: step-signal
description: Signal task completion or gate decisions to the AI Workflow engine
---

# Step Signal

You are running inside an **ai-workflow** managed step. Use the HTTP API below to signal your result when you finish.

## Your Context

- **Server**: `http://127.0.0.1:8084`
- **Step ID**: `1`
- **Issue ID**: `1`
- **Step Type**: `exec`
- **Execution ID**: `1`

## After Completing Your Task

**Signal completion** (do this BEFORE ending your response):

```bash
curl -s -X POST "http://127.0.0.1:8084/api/steps/1/decision" \
  -H "Authorization: Bearer 98343122936d6b7f679d46a0c98bf7c69587970fefb88c2fe676fb3d4a502183" \
  -H "Content-Type: application/json" \
  -d '{"decision":"complete","reason":"<one sentence summary of what you did>"}'
```

**If you are stuck and need human help:**

```bash
curl -s -X POST "http://127.0.0.1:8084/api/steps/1/decision" \
  -H "Authorization: Bearer 98343122936d6b7f679d46a0c98bf7c69587970fefb88c2fe676fb3d4a502183" \
  -H "Content-Type: application/json" \
  -d '{"decision":"need_help","reason":"<why you are stuck>"}'
```

## Rules

1. **Always signal before ending your response.** The engine needs your signal to proceed.
2. Only call the decision endpoint **once** per execution.
