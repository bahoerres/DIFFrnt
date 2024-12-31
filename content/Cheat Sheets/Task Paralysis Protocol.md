---
created: 2024-11-02T02:36
updated: 2024-12-26T16:30
---
# Task Paralysis Protocol

## Quick Check
```dataview
TABLE WITHOUT ID
  state as "Current State",
  paralysis_type as "Type",
  last_override as "Last Override"
FROM "states"
WHERE contains(file.name, "paralysis")
```

## Recognition Patterns
```mermaid
mindmap
  root((PARALYSIS))
    Decision Loop
      Too Many Options
      Fear of Wrong Choice
      Future Threading
    Perfectionism
      Setup Spiral
      Research Hole
      Tool Tweaking
    Energy Mismatch
      Wrong State
      Task Too Big
      Environment Block
```

## Emergency Override System
1. PHYSICAL FIRST
   - Stand up
   - Change rooms
   - Move anything
   - [[Emergency Momentum|Catch Spark]]

2. SCOPE KILL
   - 2-minute version
   - Visible only
   - Single surface
   - One tool only

3. CHOICE DESTROY
   - First visible item
   - Current location
   - Existing tools
   - No research

## Pattern Breaking
```mermaid
graph TD
    A[Notice Loop] --> B[Physical Interrupt]
    B --> C[Tiny Action]
    C --> D[Document Win]
    D --> E[Chain Effect]
```

## Quick Wins Database
```dataview
LIST
FROM "momentum/wins"
WHERE contains(file.tags, "paralysis-breaker")
SORT date desc
LIMIT 5
```

## State Tracking
- Current Loop Type: `= this.loop_type`
- Override Used: `= this.override`
- Success Pattern: `= this.pattern`
- Chain Trigger: `= this.trigger`

Remember: Motion > Direction