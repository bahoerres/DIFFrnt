---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Collecting Highlighted Therapy Thoughts with Dataview

Created: 2024-11-20 16:02:05 UTC
Updated: 2024-11-20 16:06:58 UTC
UUID: 39fd6caa-4f99-4e96-b2d5-0e2a1cbdb65f
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-20 16:02:13 UTC

Id like to explore the use of data view and I think another complementary plugin called highlights? 

Essentially, if I use a certain tag, or I think in this case is was ::highlight it would show up in a specific dataview. 

For example, thoughts that I want to track specifically for therapy sessions. I can add them to daily notes, sure, but then having them all be collected in a single note to then parse through the list and sort the thoughts would be great.

---

**Assistant** - 2024-11-20 16:02:13 UTC

 I'll help you understand how to use Dataview alongside the Highlights plugin in Obsidian for tracking therapy-related thoughts.

The Highlights plugin (officially called "Highlightr") lets you create custom highlights using the syntax `::highlight text::` or `==highlight text==`. When combined with Dataview, you can collect and organize these highlights across your notes.

Here's how you could set this up:

1. First, use highlights in your daily notes like this:
```markdown
## Daily Note 2024-11-20

Regular note content...
::therapy Today I noticed I felt anxious when thinking about the upcoming presentation::
More content...
::therapy I used the breathing technique and it helped::
```

2. Then create a note called "Therapy Thoughts Collection" where you can gather all these highlights using Dataview:
```dataview
LIST
FROM "Daily Notes"
WHERE contains(file.content, "::therapy")
FLATTEN file.content
WHERE contains(this, "::therapy")
```

This query will:
- Search through your Daily Notes folder
- Find all instances of the "therapy" highlight
- List them in one place

You could also make it more sophisticated:
```dataview
TABLE 
date as "Date",
therapy-thought as "Thought"
FROM "Daily Notes"
FLATTEN file.content as therapy-thought
WHERE contains(therapy-thought, "::therapy")
SORT date DESC
```

Would you like me to explain how to:
1. Set up different highlight colors for different types of thoughts
2. Create more complex Dataview queries for filtering/organizing your thoughts
3. Or something else?

---

**Human** - 2024-11-20 16:04:33 UTC

And that I can use line by line, right? Like I have a space for add-ins for tasks that come up over the day. Just use the :: syntax at the beginning of the line?

---

**Assistant** - 2024-11-20 16:04:33 UTC

 Yes, exactly! You can use it line by line, which is especially useful for task lists or quick thoughts. Here's how it would look:

```markdown
## Daily Note

Regular notes here...

### Tasks/Thoughts that came up:
::therapy Need to discuss work boundaries next session::
::therapy Noticed pattern of procrastination when stressed::
::task Follow up with dental appointment::
::task Order new journal::
Regular task without highlight
::therapy Used grounding technique during meeting - worked well::
```

The syntax is flexible - you can:
1. Start the line with :: (as shown above)
2. Use it ::inline:: within sentences
3. Even combine it with other Obsidian syntax like:
   - ::therapy #therapy-topic Need to explore this more::
   - ::therapy - [ ] Bring this up next session::

This makes it really easy to quickly jot down thoughts throughout the day while keeping them trackable via Dataview. Would you like to see how to query specifically for these line-by-line entries?

---

**Human** - 2024-11-20 16:05:33 UTC

Here's my template.. 

---
tags:
  - DailyNote
  - 2024
  - 12
---
# Collecting_Highlighted_Therapy_Thoughts_with_Dataview_39fd6caa

<< [[2039-05-31]] | [[2039-06-02]]>>

## Achievements
>[!multi-column]
>> [!summary]+ Overdue
>> ```todoist  
>> filter: overdue & !today
>> sorting:  
>> - date  
>> - priority  
>> ```
>
>> [!summary]+ Due Today
>> ```todoist  
>> filter: today
>> sorting:  
>> - date  
>> - priority  
>> ```

#### New Today
- [ ]  <% tp.file.cursor() %> 🆔 10al4i

## Quest Log
> [!multi-column]
>
>> [!tip]+ Main Quest
>> - [ ] 
>
>> [!success]+ Side Quest
>> - [ ] 
>> - [ ] 
>> - [ ] 
>  
>> [!example]+ Dailies
>> - [ ] 
>> - [ ] 
>> - [ ] 
>> - [ ] 
>> - [ ] 

## Daily flows
>[!multi-column]
>> [!morning] Start of Day
>> - [ ] Fendi Outside: Short 🆔 N3zd0K
>> - [ ] Small Breakfast/Vitamins 🆔 MBQWMS
>> - [ ] Make Bed 🆔 qc41aG
>> - [ ] Wash face/Brush teeth 🆔 laQx8L
>
>> [!noon] Midday Reset
>> - [ ] Full Breakfast 🆔 4fu4fu
>> - [ ]  Fendi Outside: Full walk 🆔 LXQQPV
>> - [ ] Plan Day 🆔 0sCw9V
>> - [ ] Stretch/Meditate 🆔 Hcs7ga
>
>> [!evening] End of Day
>> - [ ] Fendi Outside: Pre-Bed 🆔 BksT94
>> - [ ] Review Day | Check tomorrow's calendar 🆔 Kq5mFS
>> - [ ] Bedtime Playlist & Set Alarm 🆔 K23o9J
>> - [ ] Stretch/Meditate 🆔 YB8Spm
>> - [ ] Wash face/brush teeth 🆔 bvMFjG

## Other Tasks
>[!multi-column]
>> [!summary]+ Pull the Thread
>> ```todoist  
>> filter:  no date & !/*
>> sorting:  
>> - date  
>> - priority  
>> ```
>
>> [!summary]+ Next 7 Days
>> ```todoist  
>> filter: all & 7 days
>> sorting:  
>> - date  
>> - priority  
>> ```

---

**Assistant** - 2024-11-20 16:05:33 UTC

 I see you have a nicely structured template with Todoist integration and callouts. To add highlight tracking, you could add a section specifically for capturing thoughts/items throughout the day. Here's how you could modify it (I'll just show the new section to add, since your existing template is working well):

```markdown
[Your existing template content...]

## Daily Captures
>[!multi-column]
>> [!note]+ Therapy Thoughts
>> ::therapy Add thoughts here::
>
>> [!note]+ Task Add-ins
>> ::task Add tasks here::
>
>> [!note]+ General Notes
>> ::note Add notes here::
```

Or if you prefer a simpler format without the callouts:

```markdown
## Daily Captures
### Therapy Notes
::therapy::
::therapy::

### Task Add-ins
::task::
::task::

### Quick Notes
::note::
::note::
```

Then you could create a Dataview query in another note to collect all therapy thoughts:

```dataview
TABLE file.name as "Date", rows.therapy-thought as "Thoughts"
FROM "Daily Notes"
FLATTEN file.content as therapy-thought
WHERE contains(therapy-thought, "::therapy")
GROUP BY file.name
SORT file.name DESC
```

Would you like me to suggest where in your existing template this might fit best? Or would you prefer a different organization method for capturing these thoughts?

---

**Human** - 2024-11-20 16:06:14 UTC

I mean, therapy notes and general notes can be in the same area if I'm using the highlights, right?

---

**Assistant** - 2024-11-20 16:06:14 UTC

 Yes, exactly! Since you're using the highlight syntax, you can mix them together and Dataview will still be able to sort them separately based on the highlight type. You could simply add a "Daily Captures" or "Notes & Thoughts" section to your template like this:

```markdown
[Your existing template sections...]

## Notes & Thoughts
::therapy First session reflection::
::note Need to buy dog food::
::therapy Anxiety spike during meeting::
::note Remember to call mom::
```

Then in your Dataview collection note, you can sort them by type:

For therapy notes:
```dataview
TABLE file.name as "Date", rows.thought as "Therapy Notes"
FROM "Daily Notes"
FLATTEN file.content as thought
WHERE contains(thought, "::therapy")
GROUP BY file.name
SORT file.name DESC
```

For general notes:
```dataview
TABLE file.name as "Date", rows.thought as "General Notes"
FROM "Daily Notes"
FLATTEN file.content as thought
WHERE contains(thought, "::note")
GROUP BY file.name
SORT file.name DESC
```

This keeps your daily template cleaner while still maintaining the ability to collect and organize different types of thoughts separately. Would you like help deciding where to place this section in your existing template?

---

**Human** - 2024-11-20 16:06:58 UTC

The general notes would make a great addition to my monthly (also where I think it would be most useful) review/note.

---

**Assistant** - 2024-11-20 16:06:58 UTC

 Ah yes, that's a great idea! You could create a Monthly Review template that uses Dataview to automatically collect all your highlighted notes from that month. Here's how you could structure it:

```markdown
# Monthly Review - [[2024-12]]

## Therapy Journey
```dataview
TABLE WITHOUT ID
file.link as "Date",
thought as "Reflection"
FROM "Daily Notes"
WHERE contains(file.name, "2024-12")
FLATTEN file.content as thought
WHERE contains(thought, "::therapy")
SORT file.name DESC
```

## General Notes & Observations
```dataview
TABLE WITHOUT ID
file.link as "Date",
thought as "Note"
FROM "Daily Notes"
WHERE contains(file.name, "2024-12")
FLATTEN file.content as thought
WHERE contains(thought, "::note")
SORT file.name DESC
```

## Monthly Overview
- Key Events:
- Challenges:
- Wins:
- Focus for Next Month:

Would you like me to show you how to:
1. Add more categories of highlights to track
2. Create different views of the data (like grouping by weeks)
3. Add summary statistics (like number of therapy insights or general notes per week)?

---

