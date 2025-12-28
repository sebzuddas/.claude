# My Claude Agents

This repo sets up my claude agents in a given way... 


#TODO:
1. implement engineering standards in `CLAUDE.md`

# NOTES:
- Frontier thinking LLMs can handle approx 150-200 instructions consistently. Programming LLMs already contain 50 instructions, hence agents must have a maximum of 100 instructions. 
- Context tradeoffs:
  - Sub-agents contain only the context they are given. They miss out on the larger-order thinking and holistic approaches. 


# Conventions:
## Naming
*Functions* represent departments, whereas specialisms represent what might be considered individuals who would work in said departments. 

Agents follow the convention: `[department]-[specialism]-[function].md`. EG `engineer-python-reviwer.md`.
In the case there is no specialism, the convention becomes `agent-[function].md`.

## Colours
- engineers: cyan
- quality: green
- architects: red
- agents: blue



# AI Org Structure
┌─────────────────────────────────────────────────────────────┐
│  ~/.claude/CLAUDE.md                                        │
│  Your personal "management style" - how YOU work            │
│  Applied to every session, every project                    │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  ~/.claude/agents/                                          │
│  Your "departments" - specialists you delegate to           │
│                                                             │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐       │
│  │ Research │ │ Architect│ │ Engineer │ │ QA/Review│       │
│  │   Dept   │ │   Dept   │ │   Dept   │ │   Dept   │       │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘       │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Project-level ./CLAUDE.md + ./.claude/agents/              │
│  Project-specific context and specialists                   │
└─────────────────────────────────────────────────────────────┘

