# Agent Office

A personal **Claude Code subagent** office that manages different areas of my life. Each agent works in a "room"; a **General Manager** agent coordinates them all. Agents do not run continuously; they are called only on demand.

## Rooms
School · Teknofest · TUBITAK · Kaggle · English · Research · Personal · General Manager

## Folder structure
```
.claude/agents/   Subagent definitions
templates/        New agent template
vault/            Agent outputs (Markdown, Obsidian compatible)
logs/             Agent logs (JSON Lines)
examples/         Fake sample data
CLAUDE.md         Project rules (all agents follow)
```

## Real data vs sample data
- `vault/` and `logs/` contain **personal data** and are kept out of the repo via `.gitignore` (only the `.gitkeep` files are committed).
- `examples/` contains **fake data** in the same format; it is used to document the formats and to develop the dashboard.

## Roadmap
- [x] Skeleton
- [ ] Room agents
- [ ] General Manager agent
- [ ] Web dashboard (rooms view)
