# Agent Office

Personal "agent office": Claude Code subagents that handle different areas of my life. Each agent belongs to a **room**. The **General Manager** agent coordinates all rooms. It will later be visualized as rooms in a web dashboard.

- Agents do not run 24/7; they run **only when the user asks**.
- When adding a new agent, use the `templates/agent-template.md` template.

## Rooms
| Room | Folder |
|---|---|
| School | `vault/school/` |
| Teknofest | `vault/teknofest/` |
| TUBITAK | `vault/tubitak/` |
| Kaggle | `vault/kaggle/` |
| English | `vault/english/` |
| Research | `vault/research/` |
| Personal | `vault/personal/` |
| General Manager | `vault/general-manager/` |

Folder names: lowercase, ASCII only, `-` instead of spaces.

## Folder structure
```
.claude/agents/   → subagent definitions (<agent-name>.md)
vault/            → agent outputs (to be linked to an Obsidian vault) — NOT in git
logs/             → agent logs (<agent-name>.jsonl) — NOT in git
templates/        → new agent template
examples/         → fake sample data (for dashboard development)
```

## Shared rules (all agents follow)

### 1. Task format (Obsidian compatible)
```
- [ ] Task | category | deadline: YYYY-MM-DD | priority: high/medium/low
```
Completed task: `- [x] ...`
No deadline: `deadline: none`

### 2. Log format
When an agent finishes a task it appends a **single line** to `logs/<agent-name>.jsonl` (JSON Lines, one JSON object per line):
```json
{"timestamp": "2026-11-19T14:30:00+03:00", "agent": "school-assistant", "room": "School", "task": "short summary", "status": "success", "note": "..."}
```
- `timestamp`: ISO 8601
- `status`: only `"success"` or `"error"`
- Never change/delete existing lines; only append.

#### Legacy names
Logs created before the English migration were moved to their new file names byte-for-byte; their lines were not rewritten. Lines before the migration line in `logs/task-assistant.jsonl` use `"agent": "gorev-asistani"` and `"room": "Kişisel"`; treat them as `task-assistant` / `Personal`. Never rewrite them.

### 3. Outputs
- All outputs are **Markdown**, under `vault/<room-folder>/`.
- An agent writes only to its own room's folder (except the General Manager, which can read all rooms).

### 4. Date format
`YYYY-MM-DD` everywhere.

### 5. Language and style
- All files (agent definitions, outputs, logs, field values) are in English.
- Agents reply in the language the user writes in.
- Short, bullet-point answers.
- User-written content (e.g. task titles) is kept as written, not translated.

### 6. Privacy
- `vault/` and `logs/` contain personal data and are not pushed to git.
- Only **fake** data goes into `examples/`.
- Never read files like API keys, `.env`, `kaggle.json` or write them into outputs.
