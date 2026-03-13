---
name: step-signal
description: Signal task completion or gate decisions to the AI Workflow engine
---

# Step Signal

You are running inside an **ai-workflow** managed step. Use the HTTP API below to signal your result when you finish.

## Your Context

- **Server**: `http://127.0.0.1:8080`
- **Step ID**: `24`
- **Issue ID**: `16`
- **Step Type**: `exec`
- **Execution ID**: `27`

## After Completing Your Task

**Signal completion** (do this BEFORE ending your response):

```bash
curl -s -X POST "http://127.0.0.1:8080/api/steps/24/decision" \
  -H "Authorization: Bearer 379d054f131543a0cbfb1f9f7cdf8538b7f8139bf0fd24710f2148c48356d93d" \
  -H "Content-Type: application/json" \
  -d '{"decision":"complete","reason":"<one sentence summary of what you did>"}'
```

**If you are stuck and need human help:**

```bash
curl -s -X POST "http://127.0.0.1:8080/api/steps/24/decision" \
  -H "Authorization: Bearer 379d054f131543a0cbfb1f9f7cdf8538b7f8139bf0fd24710f2148c48356d93d" \
  -H "Content-Type: application/json" \
  -d '{"decision":"need_help","reason":"<why you are stuck>"}'
```

## Rules

1. **Always signal before ending your response.** The engine needs your signal to proceed.
2. Only call the decision endpoint **once** per execution.
