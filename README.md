# Agent-skills
## Slop reduction


Detailed instructions for AI coding agents. Load a skill only when the task
matches its description. Do not load every skill into every turn.

| Skill | Path | When to read |
| --- | --- | --- |
| Minimal code | [minimal-code/SKILL.md](minimal-code/SKILL.md) | Default for every code change. Read once per coding task. |
| Simple English | [simple-english/SKILL.md](simple-english/SKILL.md) | Docs, READMEs, error copy, or when the user asks for plain English. |
| Interface design | [interface-design/SKILL.md](interface-design/SKILL.md) | Product UI design, review, or polish. Not for landing pages. |

[AGENTS.md](../AGENTS.md) at the repo root is the always-on contract. It points
here so agents keep these files out of context until they are needed.
