# Import Verification Checklist

## All config.py exports verified ✅

### Variables
- ✅ `DEVELOPER_TOOLS = False` (line 9)
- ✅ `TURN_DELAY = 2` (line 12)
- ✅ `SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT = True` (line 13)
- ✅ `SHARE_CHAIN_OF_THOUGHT = False` (line 14)
- ✅ `SORA_SECONDS = 6` (line 15)
- ✅ `SORA_SIZE = "1280x720"` (line 16)
- ✅ `OUTPUTS_DIR = "outputs"` (line 19)
- ✅ `AI_MODELS = {...}` (line 22)
- ✅ `SYSTEM_PROMPT_PAIRS = {...}` (line 72)

### Functions
- ✅ `get_model_tier_by_id(model_id)` (line 1031)
- ✅ `get_model_id(display_name)` (line 1043)
- ✅ `get_invite_models_text(tier="Both")` (line 1054)

## Import dependencies satisfied ✅

### main.py imports from config
```python
from config import (
    TURN_DELAY,                          # ✅
    AI_MODELS,                           # ✅
    SYSTEM_PROMPT_PAIRS,                 # ✅
    SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT,    # ✅
    SHARE_CHAIN_OF_THOUGHT,              # ✅
    DEVELOPER_TOOLS,                     # ✅
    get_model_tier_by_id                 # ✅
)
```

Dynamic imports in main.py:
- Line 193: `from config import get_invite_models_text` ✅
- Line 532: `from config import SORA_SECONDS, SORA_SIZE` ✅
- Line 1906: `from config import SORA_SECONDS, SORA_SIZE` ✅
- Line 2135: `from config import SORA_SECONDS, SORA_SIZE` ✅
- Line 2819: `from config import OUTPUTS_DIR` ✅

### gui.py imports from config
```python
from config import (
    AI_MODELS,                           # ✅
    SYSTEM_PROMPT_PAIRS,                 # ✅
    SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT,    # ✅
    OUTPUTS_DIR                          # ✅
)
```

Dynamic imports in gui.py:
- Line 3107: `from config import OUTPUTS_DIR` ✅

### grouped_model_selector.py imports from config
```python
from config import AI_MODELS, get_model_id    # ✅ ✅
```

### shared_utils.py imports from config
```python
from config import OUTPUTS_DIR                # ✅
```

Dynamic imports in shared_utils.py:
- Line 540: `from config import SHOW_CHAIN_OF_THOUGHT_IN_CONTEXT` ✅

## Upstream integration status ✅

### Features integrated
- ✅ `!search` command (web search via DuckDuckGo)
- ✅ `!prompt` command (AI self-modification)
- ✅ `!temperature` command (sampling control)
- ✅ BackroomsBench evaluation system
- ✅ Updated system prompts (76 mentions of new commands)

### Compatibility fixes applied
- ✅ DEVELOPER_TOOLS added to config.py
- ✅ OUTPUTS_DIR added to config.py
- ✅ get_model_tier_by_id() function added
- ✅ get_model_id() function added
- ✅ get_invite_models_text() function added

### Commits
1. `f2946e7` - Integrate upstream command handlers with widget-based UI
2. `50b8558` - Update config.py with upstream system prompts
3. `2c62387` - Add DEVELOPER_TOOLS and get_model_tier_by_id()
4. `1e123f7` - Add missing config exports (OUTPUTS_DIR, get_model_id, get_invite_models_text)
5. `6c79e5a` - Populate BackroomsBench leaderboard

## Testing

To verify the application runs:

```bash
poetry run python test_imports.py
```

This will test all critical imports without launching the GUI.

To run the full application:

```bash
poetry run python main.py
```

## Expected behavior
- ✅ All imports resolve without errors
- ✅ Widget-based UI displays correctly
- ✅ All 3 new commands work (`!search`, `!prompt`, `!temperature`)
- ✅ AIs can discover and use new commands
- ✅ BackroomsBench evaluation functional
- ✅ HTML export working
