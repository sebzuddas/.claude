Create project state file for: $ARGUMENTS

## Instructions

1. Create `docs/` directory if it doesn't exist:
```bash
   mkdir -p docs
```

2. Create `docs/STATE.md` with this structure:
```markdown
# State

**Updated:** [today's date]
**Focus:** $ARGUMENTS

## Status
- [ ] [First task to define]

## Blockers
None

## Recent
[No history yet]

## Next
[To be defined]

## Questions
→ docs/OPEN_QUESTIONS.md
```

3. Create `docs/DECISIONS.md` if it doesn't exist:
```markdown
# Decisions

[Append new decisions at top]

---
```

4. Create `docs/OPEN_QUESTIONS.md` if it doesn't exist:
```markdown
# Open Questions

[Format: - [ ] Question — context]

---
```

5. Confirm what was created.

If $ARGUMENTS is empty, use "New project" as the focus and note that it should be updated.
```

---

**Usage:**
```
> /init-state Spatial indexing for ABM framework
```

Creates:
```
docs/
├── STATE.md           # Focus set to "Spatial indexing for ABM framework"
├── DECISIONS.md
└── OPEN_QUESTIONS.md