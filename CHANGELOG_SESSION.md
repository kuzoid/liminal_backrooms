# Session Changelog - 2026-01-23

Tracking changes made during this session in case rollback is needed.

---

## Change 1: Added STREAMING_DELAY config option
**File:** `config.py`
**Lines:** 9-10

**Before:**
```python
# Runtime configuration
TURN_DELAY = 2  # Delay between turns (in seconds)
```

**After:**
```python
# Runtime configuration
TURN_DELAY = 2  # Delay between turns (in seconds)
STREAMING_DELAY = 0.02  # Delay between streaming chunks in seconds (0.02 = 20ms for readable pace)
```

**Purpose:** Allow configurable delay between streaming chunks so AI responses appear at a readable pace instead of all at once.

---

## Change 2: Widened chat window splitter ratio
**File:** `gui.py`
**Lines:** 3362-3364

**Before:**
```python
# Set initial splitter sizes (70:30 ratio - more space for conversation)
total_width = 1600  # Based on default window width
self.splitter.setSizes([int(total_width * 0.70), int(total_width * 0.30)])
```

**After:**
```python
# Set initial splitter sizes (80:20 ratio - more space for conversation)
total_width = 1600  # Based on default window width
self.splitter.setSizes([int(total_width * 0.80), int(total_width * 0.20)])
```

**Purpose:** Make chat window wider (80% instead of 70%).

---

## Change 3: Updated fallback splitter ratio
**File:** `gui.py`
**Line:** 3932

**Before:**
```python
self.splitter.setSizes([int(total_width * 0.7), int(total_width * 0.3)])
```

**After:**
```python
self.splitter.setSizes([int(total_width * 0.8), int(total_width * 0.2)])
```

**Purpose:** Consistent fallback ratio when restoring splitter state fails.

---

## Change 4: Import STREAMING_DELAY in main.py
**File:** `main.py`
**Lines:** 17-23

**Before:**
```python
from config import (
    TURN_DELAY,
    AI_MODELS,
    SYSTEM_PROMPT_PAIRS,
    SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT,
    SHARE_CHAIN_OF_THOUGHT
)
```

**After:**
```python
from config import (
    TURN_DELAY,
    STREAMING_DELAY,
    AI_MODELS,
    SYSTEM_PROMPT_PAIRS,
    SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT,
    SHARE_CHAIN_OF_THOUGHT
)
```

---

## Change 5: Modified on_streaming_chunk for delayed display
**File:** `main.py`
**Lines:** ~1249-1272 (now ~1249-1303)

**Before:**
Simple immediate display of chunks as they arrive.

**After:**
Queue-based approach with QTimer that:
- Buffers incoming chunks in a deque
- Displays chunks at intervals defined by STREAMING_DELAY
- Falls back to immediate display if STREAMING_DELAY <= 0

**Purpose:** Allow readable pacing of AI responses during streaming.

---

## Change 6: Created desktop launcher
**Files created:**
- `launch_liminal.command` - Double-clickable shell script in project folder
- `~/Desktop/Liminal Backrooms.app` - macOS app bundle on Desktop

**Contents of launcher script:**
```bash
#!/bin/bash
cd "/Users/Lillian/Projects/2-work/liminal_backrooms"
/opt/homebrew/bin/poetry run python main.py
```

**Purpose:** Double-click to launch the app without opening terminal manually.

**To remove:**
```bash
rm -rf ~/Desktop/"Liminal Backrooms.app"
rm /Users/Lillian/Projects/2-work/liminal_backrooms/launch_liminal.command
```

---

## Change 7: Created custom app icon
**Files created:**
- `icon_liminal.png` - Source 512x512 PNG in project folder
- `~/Desktop/Liminal Backrooms.app/Contents/Resources/icon.icns` - macOS icon

**Design elements:**
- Sickly yellow backrooms wallpaper aesthetic
- Recursive corridor descending into void/darkness
- Flickering fluorescent lights at top
- Creepy =) entity faces lurking in corners
- Glitchy scan lines and RGB displacement artifacts
- "AI" text at bottom with chromatic aberration effect

---

## Rollback Instructions

To revert all changes:
```bash
cd /Users/Lillian/Projects/2-work/liminal_backrooms
git checkout config.py gui.py main.py
```

Or revert individual files:
```bash
git checkout config.py  # Reverts STREAMING_DELAY
git checkout gui.py     # Reverts splitter ratio
git checkout main.py    # Reverts streaming delay logic
```
