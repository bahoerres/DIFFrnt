---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Customizing Obsidian Keybindings

Created: 2024-11-01 23:02:26 UTC
Updated: 2024-11-03 00:04:20 UTC
UUID: b3029361-74a3-4620-ae12-0ee4cdbe17fb
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-01 23:02:31 UTC

i feel like i'm getting pretty deep in all of this.. 

is it possible to include keybinds in an obsidian configuration? like a vimrc or a zshrc with aliases and what not?

---

**Assistant** - 2024-11-01 23:02:31 UTC

 Yes! Obsidian supports custom hotkeys/keybindings, and there are a few ways to set them up:

1. Built-in Hotkeys:
   - Go to Settings → Hotkeys
   - You can modify existing hotkeys or add new ones for any command
   - This is the simplest method, no coding required

2. Custom JavaScript via Community Plugins:
   - "Customizable Sidebar" plugin allows custom keybinds
   - "Vimrc Support" plugin specifically lets you use Vim-style keybindings
   - "Hot-keys for templates" for template-specific shortcuts

3. Advanced Configuration:
   You can create a custom hotkeys.json file in your .obsidian config folder. The settings sync between your devices if you use Obsidian Sync.

Would you like me to show you some examples of custom keybindings or explain more about any of these methods?

---

**Human** - 2024-11-01 23:03:48 UTC

i guess my Settings  > Hotkeys is a bit of an overwhelming blank canvas

---

**Assistant** - 2024-11-01 23:03:48 UTC

 Ah yes, the blank Hotkeys panel can be daunting! Let me suggest some useful starter hotkeys that make common actions faster:

1. Note Navigation/Creation:
- Quick switcher (like VS Code's Cmd+P): Default is Cmd/Ctrl + O
- Create new note: Cmd/Ctrl + N
- Navigate back: Cmd/Ctrl + Alt + LeftArrow
- Toggle edit/preview mode: Cmd/Ctrl + E

2. Formatting:
- Toggle bullet list: Cmd/Ctrl + - (hyphen)
- Toggle checkbox: Cmd/Ctrl + L
- Toggle bold: Cmd/Ctrl + B
- Toggle italics: Cmd/Ctrl + I

3. Workspace Management:
- Split right: Cmd/Ctrl + \
- Focus on next pane: Cmd/Ctrl + Tab
- Toggle left sidebar: Cmd/Ctrl + Shift + L

To set any of these:
1. Search for the command in the Hotkeys panel
2. Click the + button next to it
3. Press your desired key combination

Start with just a few that match your workflow - maybe quick switcher, new note, and toggle edit mode. You can gradually add more as you discover what actions you do frequently.

What kinds of actions do you find yourself doing most often? That might help narrow down which hotkeys to set up first.

---

**Human** - 2024-11-03 00:04:20 UTC

here's an interesting one. the vault template that i used to set my vault up initially is in a github repo. 

how can i go about keeping template items up to date from the repo without overwriting my local files and settings?

---

**Assistant** - 2024-11-03 00:04:20 UTC

 This is a great question about managing upstream template updates! There are a few approaches you could take:

1. Selective Git Integration:
- Keep the template as a separate git remote
- Selectively pull and merge specific template updates
- Use .gitignore to protect your personal content
- Store your personal notes in a different directory than template content

2. Using symbolic links:
- Keep template materials in a separate directory that's git-tracked
- Symlink shared resources (like CSS, snippets, templates) into your vault
- This way you can `git pull` template updates without touching your content

3. Manual but structured approach:
- Keep template repo cloned separately
- Use a specific directory structure like:
  ```
  vault/
    personal/  (your notes)
    shared/    (template content)
    .obsidian/ (your settings)
  ```

The most maintainable approach would probably be:
1. Clone the template repo outside your vault
2. Create symbolic links for shared resources you want to track
3. Set up a .gitignore that excludes personal content
4. Pull template updates to the separate clone
5. Review and copy over specific updates you want

Would you like me to elaborate on implementing any of these approaches? The exact method might depend on how the template is structured and what parts you want to keep in sync.

---

