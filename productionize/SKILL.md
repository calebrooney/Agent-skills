---
name: productionize
description: Upgrade code to production-grade quality. Use when the user invokes /productionize, says "productionize" (e.g. "productionize this script"), or asks to harden, hardening, or make code production-ready. Applies strong validation, error handling, tests, logging, typing, security, maintainability, and architecture. Opposite of the minimal-code skill.
---

# Productionize

Apply production-grade engineering practices to the specified code. This overrides the minimal-code skill's defaults for the current task.

## When to Use

- User invokes `/productionize` (optionally with a target: file, module, feature).
- User's prompt contains "productionize", "production-ready", "harden", or "make this production grade".
- User explicitly asks for tests, typing, logging, monitoring, or security hardening of existing code.

## Process

1. **Scope first.** Identify what is being productionized (whole file/project, or the target given as an argument). Don't productionize code outside that scope.
2. **Read the codebase conventions** before changing anything: existing lint/type-check/test configs, error-handling patterns, logging libraries, and dependency choices. Match them instead of introducing new tooling.
3. **Apply the checklist below** as appropriate — not every item applies everywhere. Skip what the codebase already does or what genuinely doesn't apply, and say what you skipped.
4. **Verify.** Run the project's type check, linter, tests, and build if they exist. Report results honestly.

## Checklist

### Validation & boundaries
- Validate external inputs (user input, API payloads, env vars, file contents) at the boundary.
- Fail fast with clear errors; never silently swallow failures.

### Error handling
- Handle failure modes explicitly: missing files, network errors, bad data, timeouts.
- Wrap low-level errors with context (what operation failed, on what input).
- Use typed/expected errors where the language or codebase supports them.

### Typing
- Add type annotations to public functions and non-obvious code.
- Prefer precise types over `any`/`object`; eliminate type suppressions where possible.

### Tests
- Add unit tests for core logic and edge cases; integration tests for external boundaries.
- Cover failure paths, not just happy paths.
- Place tests where the project already puts them; use the project's test runner.

### Observability
- Log significant state transitions and failures with enough context to debug.
- Use the project's logger — never bare `print`/`console.log` in production paths.
- Include identifiers (request IDs, job IDs) in log lines where applicable.

### Security
- Handle secrets via environment/config — never hardcode or commit them.
- Sanitize/escape data crossing trust boundaries (shell, SQL, HTML, paths).
- Check authorization at the point of use, not just at login.
- Pin dependency versions; avoid adding dependencies without need.

### Robustness
- Handle concurrency, retries, and timeouts where the code touches the network or shared state.
- Ensure resources are cleaned up (files, connections, locks).
- Consider idempotency for operations that can be retried.

### Maintainability & architecture
- Keep modules cohesive; separate orchestration from business logic where it aids testing.
- Document public APIs and non-obvious decisions (why, not what).
- Remove dead code and unused dependencies introduced or found along the way.

## Output

Summarize changes by checklist category, note anything skipped and why, and list verification commands run with their results.
