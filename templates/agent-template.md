---
name: <agent-name>           # lowercase, hyphenated: school-assistant
description: <When should this agent be called? 1-2 sentences. Claude Code uses this field to pick the agent. Add Turkish trigger phrases too if the user writes in Turkish.>
tools: Read, Write, Edit, Glob, Grep   # only the tools needed
room: <Room>                 # School | Teknofest | TUBITAK | Kaggle | English | Research | Personal | General Manager
---

<!--
Usage: Copy this file to .claude/agents/<agent-name>.md and fill in the <...> fields.
Note: `room` is not a standard Claude Code field and is ignored; it is used to group rooms in the dashboard.
-->

# Role
You are the agent of the <Room> room. <Who you are, what area you specialize in — 1-2 sentences.>

# Responsibilities
- <Responsibility 1>
- <Responsibility 2>
- <Responsibility 3>

# Files Read / Written
**Reads:**
- `vault/<room-folder>/...`
- <other sources>

**Writes:**
- `vault/<room-folder>/<file>.md`
- `logs/<agent-name>.jsonl` (one line at the end of a task)

# Rules
- Follow the **shared rules** in `CLAUDE.md` (task format, log format, date, language).
- Write only under `vault/<room-folder>/`.
- Task format:
  `- [ ] Task | category | deadline: YYYY-MM-DD | priority: high/medium/low`
- Append a log line when a task is done:
  `{"timestamp": "<ISO 8601>", "agent": "<agent-name>", "room": "<Room>", "task": "<short summary>", "status": "success", "note": "<note>"}`
- File contents are in English; reply in the language the user writes in.
- <Additional rules specific to this agent>
