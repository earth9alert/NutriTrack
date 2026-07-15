---
kind: error_handling
name: No Error Handling System — Single-File Vanilla JS App
category: error_handling
scope:
    - '**'
source_files:
    - index.html
---

This repository contains a single-file Thai-language calorie and macro tracker (`index.html`) with no dedicated error handling infrastructure. There are no `errors/` directories, no custom error types, no sentinel errors, no middleware, and no `panic`/`recover` equivalents (it is plain browser JavaScript). The codebase uses only the most basic defensive patterns:

- **HTML form validation**: `<input required>` attributes and `e.preventDefault()` in `handleAddFood` prevent empty submissions.
- **Coercion to defaults**: `parseFloat(...) || 0` silently converts invalid inputs to zero rather than raising errors.
- **User-facing feedback via toast**: `showToast(msg)` displays success messages; there is no equivalent failure/toast for unexpected conditions.
- **One explicit user confirmation**: `resetAll()` uses `confirm(...)` before clearing data.
- **No try/catch blocks** around `localStorage.getItem`/`setItem`, so storage failures would surface as unhandled exceptions.
- **No global error handler** (`window.onerror`, `unhandledrejection`) is registered.

In short, this project has no structured error handling system — it relies on HTML5 input constraints and silent coercion, which is appropriate for a small demo SPA but provides no meaningful error propagation or recovery.