---
created: 2024-11-02T02:35
updated: 2024-12-26T16:30
---
# 🔥 Catch Spark Protocol

## State Check
```dataview
TABLE WITHOUT ID
  energy_level as "Energy",
  environment_score as "Environment",
  last_win as "Last Win"
FROM "states"
WHERE file.name = "current_state"
```

## Instant Actions
1. PHYSICAL MOVE
   - Stand → Different (+2)
   - Water path (+1)
   - Item relocate (+1)
   - Surface clear (+2)

2. ENVIRONMENT HACK
```mermaid
graph TD
    A[Current Space] --> B[Light Change]
    A --> C[Sound Shift]
    A --> D[Temperature]
    A --> E[New Location]
    style A fill:#f96
```

3. TASK SCOPE
   - Visible only
   - One surface
   - 2min max
   - Current tools

## Win Tracking
```dataview
LIST points
FROM "momentum/quick_wins"
WHERE date = date(today)
LIMIT 5
```

## Power Locations
```mermaid
mindmap
  root((WIN SPOTS))
    Kitchen
      Counter+2
      Sink+1
    Desk
      Standing+3
      Clear+2
    Outside
      Porch+3
      Walk+4
```

## Chain Stats
- Current Streak: `= this.streak`
- Power Location: `= this.location`
- Last Pattern: `= this.pattern`

## Emergency Override
```mermaid
graph LR
    A[Stuck] --> B{Move}
    B -->|Success| C[Chain]
    B -->|Still Stuck| D[Override]
    D --> E[Physical Only]
```