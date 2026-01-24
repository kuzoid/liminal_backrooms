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

## Local Modifications (2026-01-23)
Changes from upstream, tracked in `CHANGELOG_SESSION.md`:

| Change | File | Notes |
|--------|------|-------|
| Streaming delay | `config.py` | `STREAMING_DELAY = 0.02` — slows AI output for readability |
| Wider chat | `gui.py` | 80:20 splitter ratio (was 70:30) |
| Desktop launcher | `~/Desktop/Liminal Backrooms.app` | Double-click to launch |
| Custom icon | `icon_liminal.png` | Backrooms aesthetic |

**To adjust streaming speed:** edit `STREAMING_DELAY` in `config.py` (0 = instant, 0.05 = slower)

**Upstream is 1 commit ahead** (PR #2: free models, dev tools, UI cleanup). Big diff — merge later if needed.

## Launch
```bash
# Double-click app on Desktop, or:
/Users/Lillian/.local/bin/poetry run python main.py
```

---
See ~/Projects/work/CLAUDE.md for work context.
