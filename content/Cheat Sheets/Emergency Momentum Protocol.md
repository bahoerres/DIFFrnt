---
created: 2024-10-30T07:53
updated: 2024-12-26T16:30
---

# ⚡ Emergency Momentum Protocol

## State Monitor
```dataview
TABLE WITHOUT ID
  state as "State",
  energy as "Energy",
  momentum_streak as "Streak",
  current_points as "Points"
FROM "states/current"
```

## Active Buffs
```mermaid
mindmap
  root((ACTIVE))
    Quick
      Move+2
      Water+1
      Stand+2
    Focus
      Timer+2
      Zone+3
      Single+2
    Power
      Chain+3
      Stack+2
      Flow+2
```

## PROTOCOL ACTIVATE
1. MOVE → ACTION
   - Physical shift required
   - Use visible triggers
   - [[Catch Spark|Spark Protocol]]

2. SET BOUNDS
   - ![[Timer Widget]]
   - One clear target
   - Current location
   - Available tools

## Point Stream
```dataview
LIST
FROM "momentum/points"
WHERE date = date(today)
SORT time DESC
LIMIT 3
```

## Chain Effects
```mermaid
graph TD
    A[Move] --> B[Action]
    B --> C[Points]
    C --> D[Chain]
    D --> E[Power State]
    style E fill:#f96
```

## Quick Stats
- Chain Level: `= this.chain_level`
- Power Zone: `= this.location`
- Flow State: `= this.flow_time`
- Next Target: `= this.next_win`

## Emergency Reset
```mermaid
flowchart LR
    A[Stuck] --> B{Move}
    B --> C[New Zone]
    B --> D[Body Reset]
    B --> E[Timer Reset]
```