# Coding Opinions & Architecture Rules

## 1. Model Agnosticism
- Never use vendor-specific SDKs (e.g., do not import `anthropic` or `openai` directly into app scripts).
- Always use `liteLLM` for model completions to ensure the backend model can be swapped seamlessly.
- Read the active model dynamically from the `ACTIVE_MODEL` environment variable.

## 2. Tool & Execution Standards
- All integrations (TickTick, Gmail, Home Assistant) must be written as clean, standalone Python functions.
- Functions must accept standard data types (strings, ints, dicts) and return strings or JSON.
- Never hardcode credentials. Always look up tokens via `os.environ.get()`.

## 3. Financial & Guardrail Standards
- Every autonomous loop or multi-step execution block must implement a hard execution cap (`max_iter=4`).
- Prefer fast, cost-optimized models (like Claude Haiku or GPT-4o-mini) for data parsing or routine scheduling tasks.
- Restrict premium models solely to complex code generation or final output synthesis.

