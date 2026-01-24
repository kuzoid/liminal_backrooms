# Project: liminal_backrooms

## Overview
AI conversation/benchmarking tool — multiple AI models talking to each other with PyQt6 GUI.

## Tech Stack
- Python with PyQt6
- Multiple AI APIs: Claude, OpenRouter, OpenAI, Replicate, DeepSeek

## Key Files
| File | Purpose |
|------|---------|
| `main.py` | Entry point, Qt application |
| `gui.py` | PyQt6 interface |
| `config.py` | Model configs, system prompts |
| `backroomsbench.py` | Benchmarking logic |
| `command_parser.py` | Command parsing |

## Directories
- `backroomsbench_reports/` — Benchmark outputs
- `docs/` — Documentation
- `exports/` — Conversation exports
- `logs/` — Runtime logs
- `memory/` — Conversation memory/state

## Setup
```bash
# Requires .env with API keys
cp .env.example .env
# Add your API keys
```

## Status
Ongoing — both personal interest and professional relevance.

---
See ~/Projects/work/CLAUDE.md for work context.
