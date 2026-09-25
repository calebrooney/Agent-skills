---
name: minimal-code
description: Write minimal, simple code by default. Avoid production-grade structure unless explicitly requested.
---

# Minimal Code

When writing or modifying code, prefer the smallest simple implementation that clearly solves the task.

## Default
- Minimize code, files, abstractions, dependencies, and indirection.
- Prefer functions and straightforward procedural code.
- Optimize for readability only when it conflicts with minimalism.
- Reuse existing code instead of introducing architecture.
- Implement only what the prompt requires.
- Do not add speculative extensibility or "best practice" scaffolding.

## Avoid by default
Unless required by the existing codebase or explicitly requested, do not add:
- Classes or OOP
- Type annotations
- Dedicated test modules
- Interfaces, factories, wrappers, or abstraction layers
- Excessive validation, error handling, logging, or security checks
- Configuration systems for values that can be simple constants
- Helper functions used only once when inline code is clearer
- Docstrings/comments that merely restate obvious code
- Production-grade project structure

## Production mode
Only apply production-grade engineering practices when the user's prompt contains the word **"productionize"**.

When triggered, use appropriate production practices such as stronger validation, error handling, tests, logging, typing, security considerations, maintainability, and architecture.

Otherwise, simplicity wins.