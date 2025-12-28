# Conway's Game of Life Implementation Plan

## Summary

The Grid2D spatial environment and cellular automata update system are **already implemented**. This task only requires creating a demo file and integrating it into the UI.

## Existing Infrastructure (No Changes Needed)

| Component | Location | Status |
|-----------|----------|--------|
| `Grid2DSpatialIndex` | `src/lib/abm/core/ecs.ts:285-406` | Complete - Moore neighborhood support |
| `executeGridUpdateSystem` | `src/lib/abm/core/simulation.ts:641-692` | Complete - GoL rules hardcoded |
| Process schedule | `simulation.ts:456-458` | Supports `{ system: 'GridUpdate' }` |
| Renderer grid drawing | `pixiRenderer.ts:177-198` | Complete - draws grid lines for grid2D |

## Implementation Steps

### Step 1: Create Demo File
**File:** `src/app/abm/demos/gameOfLife.ts`

Define `GAME_OF_LIFE_MODEL: ABMModelDefinition` with:
- **Components:** `Position`, `CellState` (with `alive: boolean`)
- **Archetype:** `Cell` with colorByState based on `CellState.alive`
- **Spatial:** `grid2D` with cellSize (e.g., 10px), toroidal boundary
- **Process Schedule:** `[{ system: 'GridUpdate', order: 'parallel' }]`
- **Initialization:** All grid cells spawned, ~30% random alive

### Step 2: Integrate into UI
**File:** `src/app/abm/page.tsx`

1. Add import: `import { GAME_OF_LIFE_MODEL } from './demos/gameOfLife'`
2. Add to demoModels map: `gameOfLife: GAME_OF_LIFE_MODEL`
3. Add dropdown option: `<option value="gameOfLife">Conway's Game of Life</option>`

### Step 3: Update Documentation
**Files:** `docs/STATE.md`, `docs/BACKLOG.md`

Mark feature as complete, update demo count to 5.

## Key Implementation Details

### CellState Component
```typescript
{
  name: 'CellState',
  properties: {
    alive: { type: 'boolean', default: false }
  }
}
```

### Visual Configuration
```typescript
visual: {
  shape: 'square',
  size: 10,  // Matches cellSize
  colorByState: {
    property: 'CellState.alive',
    colorMap: {
      'true': '#ffffff',   // Alive = white
      'false': '#1a1a1a'   // Dead = dark gray (nearly invisible on black)
    }
  }
}
```

### Grid Initialization
Spawn one cell entity per grid position:
```typescript
initialization: {
  entities: [{
    archetype: 'Cell',
    count: gridWidth * gridHeight,  // e.g., 60x40 = 2400 cells
    position: { type: 'grid', spacing: cellSize },
    propertyVariation: {
      'CellState.alive': { distribution: 'uniform', min: 0, max: 1 }  // ~50% alive
    }
  }]
}
```

## Verified Implementation Details

1. **Grid position type:** Already implemented at `simulation.ts:282-290` - places entities in grid pattern based on `spacing` parameter.

2. **Boolean colorMap:** Will use string keys `'true'`/`'false'` - needs testing. Fallback: use numeric `alive: 1/0` with color interpolation.

3. **Grid sizing:** For 60x40 grid with 10px cells = 2400 entities. Within performance targets.

## Files to Modify

| File | Change |
|------|--------|
| `src/app/abm/demos/gameOfLife.ts` | Create new demo file |
| `src/app/abm/page.tsx` | Import + add to demoModels + dropdown |
| `docs/STATE.md` | Update completion status |
| `docs/BACKLOG.md` | Mark feature complete |

## Complexity Assessment

- **Estimated:** Low-Medium (demo creation only)
- **Reason:** All core infrastructure already exists
- **Risk:** Grid initialization pattern needs verification
