---
created: 2024-10-30T07:55
updated: 2024-11-01T17:24
---
# Executive Function Support System
A personal knowledge management system for managing ADHD/Autism executive function challenges.

## Quick Access
- [[Emergency Task Start Protocol]]
- [[Energy States]]
- [[Active Projects]]
- [[Quick Wins List]]

## Core Systems
- [[Energy Management]]
- [[Task Management Systems]]
- [[Motivation Frameworks]]

## Support Networks
- [[Environmental Support]]
- [[Crisis Management]]
- [[Pattern Recognition]]

## DataviewJS Query Examples
```dataviewjs
// Show tasks by energy level
dv.table(["Task", "Energy", "Points"], 
  dv.pages("#task")
    .sort(t => t.energy)
    .map(t => [t.file.link, t.energy, t.points]))