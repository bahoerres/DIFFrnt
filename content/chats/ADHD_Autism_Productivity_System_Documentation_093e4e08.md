---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# ADHD/Autism Productivity System Documentation

Created: 2024-10-30 14:10:41 UTC
Updated: 2024-10-31 20:53:20 UTC
UUID: 093e4e08-3a09-48f1-afb6-1c374ef5a8db
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-30 14:10:55 UTC

# Context Setting
We've been developing a comprehensive ADHD/autism-focused productivity and executive function support system, documented in an Obsidian vault. The system emphasizes energy-aware task management, pattern recognition, and sustainable maintenance practices.
# Current Progress
- Created core system architecture including Emergency Protocol, Energy States, Quick Wins, Task Menus
- Developed Pattern Recognition framework split into interconnected notes
- Established maintenance protocols for both system and personal sustainability
- Created mobile-friendly quick reference cards
- Actively working on expanding state transition protocols
# Active Discussion
Currently detailing the Zombie Mode state, which requires:
- Deeper explanation of characteristics
- Practical management strategies
- Integration with other system components
- Specific tooling and support needs
# Core System Philosophy
- Energy-state awareness drives task selection
- Pattern recognition enables system optimization
- Quick wins build momentum
- Flexible, sustainable approaches prevent burnout
- Integration between components maintains usability
# Knowledge Base Links
Key documentation includes [[Energy States]], [[Pattern Recognition]], [[Quick Wins List]], [[Task Menus]], [[System Maintenance]], with linked mobile reference cards and transition protocols.
# Continuation Goals
1. Complete Zombie Mode detailed explanation
2. Develop remaining state transition protocols
3. Enhance system integration documentation
4. Expand practical implementation guides
# Format Preferences
- Maintain existing note structure and linking conventions
- Continue using mermaid diagrams for workflows
- Keep mobile reference cards concise and actionable
- Preserve integration points between system components

---

**Assistant** - 2024-10-30 14:10:55 UTC

 Let me focus on developing the Zombie Mode state documentation, integrating it with your existing system while maintaining consistency with established patterns.

<antThinking>This requires a comprehensive document that will serve as a core reference, making it ideal for an artifact. It needs to integrate with existing documentation while maintaining consistent formatting and linking structure.</antThinking>

<antArtifact identifier="zombie-mode-documentation" type="text/markdown" title="Zombie Mode State Documentation">
# Zombie Mode

## Characteristics
- Severely depleted executive function
- Minimal task initiation capacity 
- Reduced decision-making ability
- Time blindness intensification
- Difficulty with complex instructions
- Increased sensory sensitivity

## Recognition Patterns
- Task paralysis despite urgency
- Circular thinking without action
- Basic self-care challenges
- Environmental overwhelm
- Difficulty articulating needs
- Screen hyperfocus without productivity

## Management Strategies

### Immediate Actions
1. Activate Emergency Protocol
2. Implement minimum viable routine
3. Use pre-prepared task menu
4. Enable Do Not Disturb
5. Access comfort items list

### Recovery Path
1. Basic needs check
   - Water
   - Food
   - Temperature
   - Sensory load
2. Environment scan
   - Reduce visual noise
   - Adjust lighting
   - Minimize sounds
3. Energy preservation
   - Cancel non-critical commitments
   - Activate support network
   - Use prepared responses

## System Integration

### Links to Core Components
- [[Emergency Protocol]] - First response activation
- [[Energy States]] - Transition protocols
- [[Quick Wins List]] - Accessible momentum builders
- [[Task Menus]] - Pre-filtered options
- [[Pattern Recognition]] - Early warning signs

### State Transitions
```mermaid
stateDiagram-v2
    [*] --> ZombieMode
    ZombieMode --> EmergencyProtocol: Activation
    EmergencyProtocol --> BasicNeeds: Stabilization
    BasicNeeds --> LowEnergy: Recovery
    LowEnergy --> [*]: Gradual Return
```

## Mobile Reference Card
```markdown
# 🧟‍♂️ Zombie Mode Quick Reference

1. STOP - Don't make decisions
2. ACTIVATE - Emergency Protocol
3. CHECK - Basic needs list
4. USE - Prepared responses
5. REST - Until baseline returns

Emergency Contacts: [List]
Safe Spaces: [List]
Comfort Items: [List]
```

## Tooling Requirements
- Simplified task interface
- One-click protocol activation
- Pre-written communication templates
- Environment adjustment checklist
- Recovery tracking minimal metrics
- Support network quick access

## Maintenance Notes
- Update Emergency Protocol monthly
- Review comfort items quarterly
- Validate contact information
- Adjust recovery metrics
- Document pattern variations
- Update mobile card
</antArtifact>

Would you like me to focus on any specific aspect of this documentation for further development or integration with other system components?

---

**Human** - 2024-10-30 14:12:34 UTC

I really like that context for the mobile reference: my previous efforts produced some that look like: YOU ARE HERE IF:
- Brain foggy
- Body heavy
- Can't start
- Sensory ow
QUICK ACTIONS:
1. Water + protein
2. 2min movement
3. One tiny task
4. Comfort tool
USE:
- Quick Wins only
- Physical tasks
- Known routines

think we could combine the two?

---

**Assistant** - 2024-10-30 14:12:34 UTC

 <antThinking>This is an update to the existing mobile reference card, integrating the best elements of both versions for maximum utility during low-function states.</antThinking>

<antArtifact identifier="zombie-mode-documentation" type="text/markdown" title="Updated Zombie Mode Documentation">
# 🧟‍♂️ Zombie Mode Card

YOU ARE HERE IF:
- Brain foggy/scattered
- Body feels heavy
- Can't start anything
- Sensory overload
- Time feels weird
- Basic tasks hard

FIRST ACTIONS:
1. Water + protein 
2. 2min gentle movement
3. One tiny known task
4. Use comfort item
5. Activate support if needed

USE ONLY:
- Quick Wins list
- Physical/routine tasks
- Prepared responses
- Emergency contacts
- Safe spaces list

AVOID:
- New tasks
- Decisions
- Screens (except tools)
- People (except support)

Track: Time/Date noticed | Basic needs met | Support used
</antArtifact>

Would you like me to adjust any part of this integrated format?

---

**Human** - 2024-10-30 14:13:07 UTC

mm. your initial version was formatted in a way that appealed to me a little bit more.

---

**Assistant** - 2024-10-30 14:13:07 UTC

 <antThinking>Refining the mobile reference card to use more visually clear formatting while maintaining quick scanability.</antThinking>

<antArtifact identifier="zombie-mode-documentation" type="text/markdown" title="Updated Zombie Mode Documentation">
# 🧟‍♂️ Zombie Mode Quick Reference

## You Are Here If
- Brain foggy
- Body heavy
- Can't start
- Sensory ow
- Time blind
- Basic tasks hard

## Quick Actions
1. Water + protein
2. 2min movement
3. One tiny task
4. Use comfort tool
5. Get support if needed

## Use Only
- Quick Wins
- Physical tasks
- Known routines
- Emergency contacts
- Safe spaces

## Avoid
- New tasks
- Big decisions
- Screen rabbit holes
- People (except support)

Track: State entered [time/date] | Needs met [x] | Support used [x]
</antArtifact>

Want to refine the sections or adjust formatting further?

---

**Human** - 2024-10-30 14:18:40 UTC

let's flesh out (hah, zombies, flesh.. ) a Emergency Momentum Protocol for that link. I've just got this real basic framework currently. 


```markdown
CATCH THE SPARK:
1. DON'T PREP MORE - START NOW
2. Set timer for 10 minutes
3. Pick ONE thing only
4. Give yourself points
5. Record what worked
WHEN STUCK:
- Change one constraint
- Move to a different spot
- Pick a smaller chunk
- Add novelty/game element
MAINTAIN MOMENTUM:
- Keep timer visible
- Stack small wins
- Note energy level
- Prep next task while motivated
```

---

**Assistant** - 2024-10-30 14:18:40 UTC

 <antThinking>This needs to be expanded into a comprehensive protocol while maintaining the quick-action nature. It's a core system component that deserves artifact treatment.</antThinking>

<antArtifact identifier="emergency-momentum" type="text/markdown" title="Emergency Momentum Protocol">
# Emergency Momentum Protocol

## CATCH THE SPARK
1. START IMMEDIATELY
   - No prep, no lists
   - Use what's in front of you
   - Perfection hostile to momentum

2. SET CONSTRAINTS
   - 10min timer visible
   - One task only
   - Physical > Digital
   - Location matters

3. POINTS SYSTEM
   - +1 per tiny step
   - +2 body movement
   - +3 completing anything
   - +5 chain reactions

## STUCK? CHANGE ONE THING
### Environment
- Move to different room
- Change lighting/sound
- Stand vs. sit
- Face different direction

### Task
- Halve the scope
- Switch to physical
- Add playful element
- Race the timer

### Energy
- 30sec movement
- Water/snack
- Temperature change
- Quick sensory tool

## MAINTAIN MOMENTUM
### Track
- Current points
- Energy shifts
- Time awareness
- Location effects

### Stack
- Chain small wins
- Note patterns
- Prep next while strong
- Document discoveries

## Emergency Overrides
- Zombie Mode → Physical only
- Overwhelm → Tiny steps
- Time blind → Timer essential
- Analysis freeze → Just move

Remember: Momentum > Perfection
</antArtifact>

Want to adjust the balance between structure and quick-action elements?

---

**Human** - 2024-10-30 14:19:33 UTC

I think we can definitely spruce that up a bit.

---

**Assistant** - 2024-10-30 14:19:33 UTC

 <antThinking>Let's refine the protocol to be more engaging while maintaining quick usability, integrating game elements more thoroughly.</antThinking>

<antArtifact identifier="emergency-momentum" type="text/markdown" title="Emergency Momentum Protocol">
# 🎯 Emergency Momentum Protocol

## CATCH THE SPARK! 🔥
1. START NOW (NO PREP!)
   - Use whatever's visible
   - First thought = best thought
   - Perfect = momentum killer

2. SET THE STAGE (10 MIN)
   - Timer visible = +2 points
   - One clear target = +3 points
   - Physical task = +5 points
   - New location = +4 points

3. QUEST REWARDS
   - Tiny step complete: +1
   - Body movement: +2
   - Task finished: +3
   - Chain reaction: +5
   - Boss level (hard task): +10

## STUCK? POWER-UPS! ⚡
### Switch Scene
- New room (+3)
- Light change (+1)
- Stand up (+2)
- Face reset (+1)

### Quest Modify
- Half-size task (+2)
- Physical convert (+3)
- Add game rule (+2)
- Speed challenge (+4)

### Energy Boost
- 30sec dance (+2)
- Quick fuel (+1)
- Temp shift (+1)
- Sensory tool (+2)

## COMBO STREAKS! 🔄
### Score Track
- Points this round: ___
- Energy level: [🔋____]
- Time flows: [🕒____]
- Location bonus: [📍___]

### Power Chain
- Stack wins (2x multiplier)
- Log successful spells
- Prep next quest
- Record level-ups

## EMERGENCY COMMANDS
```
IF [Zombie] → PHYSICAL ONLY
IF [Overwhelm] → TINY STEPS
IF [Time Blind] → TIMER REQUIRED
IF [Brain Freeze] → JUST MOVE
```

🎮 SECRET: Movement = Momentum
</antArtifact>

---

**Assistant** - 2024-10-30 14:20:34 UTC

 <antThinking>Let's enhance this with Obsidian-specific features including dataview, charts, and proper linking structure.</antThinking>

<antArtifact identifier="emergency-momentum" type="text/markdown" title="Emergency Momentum Protocol">
# 🎯 Emergency Momentum Protocol

## Quick Stats
```dataview
TABLE WITHOUT ID
  state as "Current State",
  points as "Points Today",
  streaks as "Active Streaks",
  locations as "Power Spots"
FROM "states"
WHERE contains(file.name, "momentum")
```

## Active Power-Ups
```mermaid
mindmap
  root((POWER))
    Environment
      Location+3
      Light+1
      Stance+2
    Task
      Physical+3
      Mini-scope+2
      Game-mod+2
    Energy
      Move+2
      Fuel+1
      Sense+2
```

## CATCH THE SPARK! 🔥
1. START NOW (NO PREP!)
   - First thought → action
   - Visible = viable
   - [[Task Paralysis|Forget Perfect]]

2. SET THE STAGE
   - ![[Timer Widget]] (+2)
   - Single target (+3)
   - Physical task (+5)
   - Location shift (+4)

## Quest Log
```dataview
LIST points
FROM "momentum/wins"
WHERE date = date(today)
SORT points DESC
```

## COMBO SYSTEM
```mermaid
graph LR
    A[Basic Win +1] --> B[Chain x2]
    B --> C[Streak x3]
    C --> D[Power State]
    style D fill:#f9f,stroke:#333
```

## Emergency Overrides
```dataview
TABLE WITHOUT ID
  trigger as "State",
  action as "Command",
  file.link as "Protocol"
FROM "emergency"
WHERE contains(file.tags, "momentum")
SORT trigger ASC
```

## Power Chain Stats
- Today's Points: `= this.points`
- Streak Count: `= this.streaks`
- Peak Hours: `= this.peak_times`
- Power Locations: `= this.power_spots`
</antArtifact>

Want to enhance any specific sections with more Obsidian features?

---

**Human** - 2024-10-30 14:20:34 UTC

Moving in the right direction. feel free to use charts and diagrams and even dataview queries when applicable. i'm pretty competent with obsidian

---

**Assistant** - 2024-10-30 14:22:33 UTC

 Which link would you like to develop first? We can build out:

1. [[Timer Widget]]
2. [[Task Paralysis]]
3. Power locations tracking
4. State transitions
5. Points/streaks system

Or we could focus on the dataview queries needed to make the dashboard functional.

---

**Human** - 2024-10-30 14:22:33 UTC

this is fantastic. i'm going to add this to the project files for reference material. wonderful! thank you! let's get some of these other links put together!

---

**Human** - 2024-10-30 14:23:02 UTC

Task paralysis would be a great one

---

**Assistant** - 2024-10-30 14:23:02 UTC

 <antThinking>Task paralysis needs comprehensive documentation while maintaining accessibility during low executive function states. This will integrate with existing momentum system components.</antThinking>

<antArtifact identifier="task-paralysis" type="text/markdown" title="Task Paralysis Protocol">
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
</antArtifact>

Want to focus on any specific aspect of paralysis patterns or override systems?

---

**Human** - 2024-10-30 14:24:56 UTC

Seems catch spart would be a logical next step

---

**Assistant** - 2024-10-30 14:24:56 UTC

 <antThinking>Let's build the Catch Spark protocol with clear success tracking and momentum building elements.</antThinking>

<antArtifact identifier="catch-spark" type="text/markdown" title="Catch Spark Protocol">
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
</antArtifact>

---

**Human** - 2024-10-30 14:25:15 UTC

and emergency momentum

---

**Assistant** - 2024-10-30 14:25:15 UTC

 <antThinking>Building on the emergency momentum framework with Obsidian-specific features while maintaining quick accessibility.</antThinking>

<antArtifact identifier="emergency-momentum" type="text/markdown" title="Emergency Momentum Protocol">
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
</antArtifact>

---

**Human** - 2024-10-30 14:25:51 UTC

looks like we're gonna need that timer widget, eh?

---

**Assistant** - 2024-10-30 14:25:51 UTC

 <antThinking>Building a React component for the timer widget that integrates with the momentum system. It needs to be visually striking but simple to use.</antThinking>

<antArtifact identifier="timer-widget" type="application/vnd.ant.react" title="Momentum Timer Widget">
import { useState, useEffect } from 'react';
import { Play, Pause, RotateCcw } from 'lucide-react';

const TimerWidget = () => {
  const [time, setTime] = useState(600); // 10 minutes in seconds
  const [isRunning, setIsRunning] = useState(false);
  const [points, setPoints] = useState(0);

  useEffect(() => {
    let interval;
    if (isRunning && time > 0) {
      interval = setInterval(() => {
        setTime((prevTime) => prevTime - 1);
      }, 1000);
    } else if (time === 0) {
      setPoints(prev => prev + 2);
    }
    return () => clearInterval(interval);
  }, [isRunning, time]);

  const formatTime = (seconds) => {
    const mins = Math.floor(seconds / 60);
    const secs = seconds % 60;
    return `${mins}:${secs.toString().padStart(2, '0')}`;
  };

  const resetTimer = () => {
    setTime(600);
    setIsRunning(false);
  };

  return (
    <div className="flex flex-col items-center p-4 bg-slate-800 rounded-lg shadow-lg">
      <div className="text-6xl font-mono font-bold text-emerald-400 mb-4">
        {formatTime(time)}
      </div>
      
      <div className="flex gap-4 mb-4">
        <button
          onClick={() => setIsRunning(!isRunning)}
          className={`p-2 rounded-full ${isRunning ? 'bg-red-500' : 'bg-emerald-500'} hover:opacity-80`}
        >
          {isRunning ? <Pause size={24} /> : <Play size={24} />}
        </button>
        <button
          onClick={resetTimer}
          className="p-2 rounded-full bg-slate-600 hover:bg-slate-500"
        >
          <RotateCcw size={24} />
        </button>
      </div>

      <div className="text-sm text-slate-400">
        Points: {points} | Streaks Active
      </div>
    </div>
  );
};

export default TimerWidget;
</antArtifact>

Want me to add any specific features to enhance momentum tracking?

---

**Human** - 2024-10-30 14:26:12 UTC

no, but how would i integrate that into my vault?

---

**Assistant** - 2024-10-30 14:26:12 UTC

 To integrate this React component in your Obsidian vault, you'll need:

1. Install the ReactJS View plugin
2. Create a new view file in your vault:
```
{FolderPath}/timer-widget.jsx
```

3. Add this to your Timer Widget note:
```markdown
# Timer Widget

```reactjs
[[timer-widget.jsx]]
```
```

4. Reference it in other notes using:
```markdown
![[Timer Widget]]
```

Want guidance on the ReactJS View plugin setup?

---

**Human** - 2024-10-30 14:28:27 UTC

"React Components" plugin?

---

**Assistant** - 2024-10-30 14:28:27 UTC

 Yes, "React Components" is the correct plugin. You'll need to:

1. Install "React Components" from Obsidian Community Plugins
2. Create `timer-widget.jsx` file
3. Reference with:
```markdown
```react
<MyTimer/>
```
```

The previous artifact formatting would need adjustment to work with this plugin. Would you like me to provide the adapted version?

---

**Human** - 2024-10-31 20:53:01 UTC

i have an issue with a sun that created a number of duplicate files. all of them, actually. 

is there a command that i can wildcard to remove any files with .sync?

---

**Assistant** - 2024-10-31 20:53:01 UTC

 Yes! If you're comfortable with the command line, you can remove all .sync files with:

```bash
rm *.sync
```

If you want to be more specific to only target the location where these files are, you can use:

```bash
rm /path/to/folder/*.sync
```

If you want to see what would be deleted first (recommended), you can list them:

```bash
ls *.sync
```

Or if you're on Windows, using PowerShell:
```powershell
Remove-Item *.sync
```

If you want to do this recursively (including all subdirectories), use:

Unix/Linux/Mac:
```bash
find . -name "*.sync" -type f -delete
```

PowerShell:
```powershell
Get-ChildItem -Path . -Filter *.sync -Recurse | Remove-Item
```

Would you like me to explain any of these commands in more detail?

---

**Human** - 2024-10-31 20:53:20 UTC

fish?

---

**Assistant** - 2024-10-31 20:53:20 UTC

 For fish shell, you can use:

```fish
rm *.sync
```

Or for recursive deletion in subdirectories:

```fish
find . -name "*.sync" -type f -delete
```

Fish is generally compatible with basic Unix commands, so the simple `rm` command works the same way. If you want to test first, you can list the files:

```fish
ls *.sync
```

Or see what would be deleted recursively:

```fish
find . -name "*.sync" -type f
```

(The last command shows what would be deleted without actually deleting - remove the files only after confirming they're the right ones!)

---

