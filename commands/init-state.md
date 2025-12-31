Initialize project documentation structure for: $ARGUMENTS

## Instructions

1. Create directory structure:
```bash
   mkdir -p docs/plans
   mkdir -p docs/architectures
```

1. Create `docs/STATE.md`:
```markdown
   # State

   **Updated:** [today's date]
   **Focus:** $ARGUMENTS

   ## Status
   - [ ] Define initial tasks

   ## Blockers
   None

   ## Recent
   [New project]

   ## Next
   [Define scope and first steps]

   ## Questions
   → docs/OPEN_QUESTIONS.md
```

1. Create `docs/BACKLOG.md`:
```markdown
   # Backlog

   ## Overview
   $ARGUMENTS

   ---

   ## Features

   ### [Feature 1]
   **Status:** 🔲 Not Started

   **Description:**
   [To be defined]

   **Requirements:**
   - [ ] [Requirement]

   **Acceptance Criteria:**
   - [Criterion]

   ---
```

1. Create `docs/DECISIONS.md`:
```markdown
   # Decisions

   [Append new decisions at top]

   ---
```

1. Create `docs/OPEN_QUESTIONS.md`:
```markdown
   # Open Questions

   - [ ] [Question] — [context]

   ---
```

1. Create `docs/OPERATIONS.md`:


2. Report what was created.


If $ARGUMENTS is empty, prompt: "What's the project focus?"


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