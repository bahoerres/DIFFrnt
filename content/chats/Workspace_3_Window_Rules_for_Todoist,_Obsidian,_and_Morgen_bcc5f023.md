---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Workspace 3 Window Rules for Todoist, Obsidian, and Morgen

Created: 2024-11-16 21:36:54 UTC
Updated: 2024-11-16 22:04:15 UTC
UUID: bcc5f023-f2d8-4f52-b9ab-f224f901f7cd
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-16 21:37:01 UTC

please write me windowrules for this: 

windows to always open in workspace 3: todoist (floating), obsidian, morgen

workspace 3: workspace wide: intial (except specified otherwise, aka. todoist): tiling, no gaps (in or out), no rounding, no transparency, no waybar

---

**Assistant** - 2024-11-16 21:37:01 UTC

 I'll help you set up those workspace rules for your Hyprland config. Here's a concise set of rules that accomplishes what you want:

```bash
# Assign apps to workspace 3
windowrulev2 = workspace 3, class:^(obsidian)$
windowrulev2 = workspace 3, class:^(Morgen)$
windowrulev2 = workspace 3, class:^(todoist)$

# Make todoist floating
windowrulev2 = float, class:^(todoist)$

# Workspace 3 general rules (except todoist)
windowrulev2 = nofloat, workspace:3, not:class:^(todoist)$
windowrulev2 = nogaps, workspace:3
windowrulev2 = rounding 0, workspace:3
windowrulev2 = opacity 1.0 override 1.0 override, workspace:3

# Hide waybar on workspace 3
bind = $mainMod, 3, exec, hyprctl keyword monitor eDP-1,addreserved,0,0,0,0
```

To verify the window classes, you can use `hyprctl clients`. If any apps aren't matching, run:
```bash
hyprctl clients | grep -i "class\|title"
```

Add these rules to `~/.config/hypr/hyprland.conf` or your rules config file if you split your configs.

---

**Human** - 2024-11-16 21:37:33 UTC

~  hyprctl clients | grep -i "class\|title"
	class: kitty
	title: ~
	initialClass: kitty
	initialTitle: kitty
	class: Morgen
	title: Morgen Calendar
	initialClass: Morgen
	initialTitle: Morgen Calendar
	class: obsidian
	title: 2024-11-16 - nDIFFrnt - Obsidian v1.7.6
	initialClass: obsidian
	initialTitle: nDIFFrnt - Obsidian v1.7.6
	class: zen-alpha
	title: Workspace 3 Window Rules for Todoist, Obsidian, and Morgen - Claude — Zen Browser
	initialClass: zen-alpha
	initialTitle: Zen Browser
	class: kitty
	title: hyprctl clients | gr ~
	initialClass: kitty
	initialTitle: kitty
 ~ 

---

**Assistant** - 2024-11-16 21:37:33 UTC

 Thanks for sharing the output. I notice Todoist isn't currently running, but we can use this information to refine the rules. Here's the updated version with the correct window classes:

```bash
# Assign apps to workspace 3
windowrulev2 = workspace 3, class:^(Morgen)$
windowrulev2 = workspace 3, class:^(obsidian)$
windowrulev2 = workspace 3, class:^(Todoist)$ # Note: Verify this class when you run Todoist

# Make Todoist floating
windowrulev2 = float, class:^(Todoist)$

# Workspace 3 general rules (except Todoist)
windowrulev2 = nofloat, workspace:3, not:class:^(Todoist)$
windowrulev2 = nogaps, workspace:3
windowrulev2 = rounding 0, workspace:3
windowrulev2 = opacity 1.0 override 1.0 override, workspace:3

# Disable reserved space for waybar on workspace 3
workspace = 3, rounding:0, gapsin:0, gapsout:0, border:1
```

When you launch Todoist, you might want to run:
```bash
hyprctl clients | grep -i "todoist"
```
to verify its exact class name and adjust if needed.

The window rules are case-sensitive, so I kept the casing from your output (`Morgen` and `obsidian`). Let me know if you need any adjustments after testing.

---

**Human** - 2024-11-16 21:38:18 UTC

~  hyprctl clients | grep -i "class\|title"
	class: kitty
	title: ~
	initialClass: kitty
	initialTitle: kitty
	class: Morgen
	title: Morgen Calendar
	initialClass: Morgen
	initialTitle: Morgen Calendar
	class: obsidian
	title: 2024-11-16 - nDIFFrnt - Obsidian v1.7.6
	initialClass: obsidian
	initialTitle: nDIFFrnt - Obsidian v1.7.6
	class: Todoist
	title: Today
	initialClass: Todoist
	initialTitle: Todoist
	class: zen-alpha
	title: Workspace 3 Window Rules for Todoist, Obsidian, and Morgen - Claude — Zen Browser
	initialClass: zen-alpha
	initialTitle: Zen Browser
	class: kitty
	title: hyprctl clients | gr ~
	initialClass: kitty
	initialTitle: kitty

---

**Assistant** - 2024-11-16 21:38:18 UTC

 Perfect, now I can see Todoist's actual class. Here's the final, verified configuration with the correct window classes:

```bash
# Assign apps to workspace 3
windowrulev2 = workspace 3, class:^(Morgen)$
windowrulev2 = workspace 3, class:^(obsidian)$
windowrulev2 = workspace 3, class:^(Todoist)$

# Make Todoist floating
windowrulev2 = float, class:^(Todoist)$

# Workspace 3 general rules (except Todoist)
windowrulev2 = nofloat, workspace:3, not:class:^(Todoist)$
windowrulev2 = nogaps, workspace:3
windowrulev2 = rounding 0, workspace:3
windowrulev2 = opacity 1.0 override 1.0 override, workspace:3

# Workspace 3 layout settings
workspace = 3, rounding:0, gapsin:0, gapsout:0, border:1
```

All class names now match exactly what's in your system. Add these to your Hyprland config and reload (`hyprctl reload`) to apply the changes.

---

**Human** - 2024-11-16 21:41:49 UTC

apologies, it's actually workspace 4. and  i figure it wouldnt hurt to give you my current rules to make sure everything is going to work together. 

# Application Window Behaviors
windowrulev2 = float, class:^(calendar|Todoist|Lxappearance|Rofi|kitty|Alacritty|thunar|viewnior|feh|pavucontrol-qt|pavucontrol|file-roller)$
windowrulev2 = float, class:^(org.kde.polkit-kde-authentication-agent-1)$
windowrulev2 = norounding, class:^(kitty)$
# Dialog and Utility Windows
windowrulev2 = float, title:^(Open File|branchdialog|confirm|dialog|download|notification|error|splash|confirmreset)$
windowrulev2 = float, class:^(file_progress)$
windowrulev2 = float, title:^(Media viewer|Volume Control|Picture-in-Picture)$
windowrulev2 = size 800 600, title:^(Volume Control)$
windowrulev2 = move 75 44%, title:^(Volume Control)$
# Calendar Specific
windowrulev2 = size 1000 600, class:^(calendar)$
windowrulev2 = center, class:^(calendar)$
# Opacity Rules
windowrulev2 = opacity 0.96, class:^(fuzzel|Rofi)$
windowrulev2 = opacity 0.96 override 0.78 override 0.86 override, class:^(obsidian|kitty)$
# Animation Rules
windowrulev2 = animation none, class:^(Rofi)$
# Workspace Assignments
windowrulev2 = workspace 2, class:^(zen|firefox)$
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 6, class:^(Beeper)$
windowrulev2 = workspace 8, class:^(spotify)$
# Browser Specific
windowrulev2 = opaque, class:^(firefox|zen)$
windowrulev2 = idleinhibit fullscreen, class:^(firefox)$
# Media Player
windowrulev2 = idleinhibit focus, class:^(mpv)$
# System UI
windowrulev2 = fullscreen, class:^(wlogout)$
windowrulev2 = float, title:^(wlogout)$
windowrulev2 = fullscreen, title:^(wlogout)$
# Gaming Rules
windowrulev2 = immediate, class:^(steam_app_1086940)$  # For BG3
windowrulev2 = noanim, class:^(steam_app_1086940)$
windowrulev2 = noshadow, class:^(steam_app_1086940)$
windowrulev2 = opaque, class:^(steam_app_1086940)$
windowrulev2 = float, class:^(.*.exe)$
windowrulev2 = float, class:^(steam_app_.*)$
windowrulev2 = float, class:^(steam_proton)$

---

**Assistant** - 2024-11-16 21:41:49 UTC

 Thanks for sharing your current rules. I'll update the previous configuration for workspace 4 and integrate it with your existing rules, ensuring there are no conflicts:

```bash
# Existing rules remain unchanged until workspace assignments section

# Workspace Assignments (updated)
windowrulev2 = workspace 2, class:^(zen|firefox)$
windowrulev2 = workspace 4, class:^(obsidian|Morgen|Todoist)$
windowrulev2 = workspace 6, class:^(Beeper)$
windowrulev2 = workspace 8, class:^(spotify)$

# Workspace 4 specific rules
windowrulev2 = nofloat, workspace:4, not:class:^(Todoist)$  # Everything tiling except Todoist
windowrulev2 = nogaps, workspace:4
windowrulev2 = rounding 0, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4  # Overrides your default opacity rules

# Workspace 4 layout settings
workspace = 4, rounding:0, gapsin:0, gapsout:0, border:1

# Rest of your existing rules remain unchanged
```

Key changes:
1. Moved apps to workspace 4
2. Todoist will still be floating due to your existing float rule
3. Added specific workspace 4 rules that override general settings
4. Added opacity override for workspace 4 that will take precedence over your existing opacity rules

Let me know if you want to adjust anything about this integration.

---

**Human** - 2024-11-16 21:47:27 UTC

this one is going to turn into a bit of a project, i think .. 

i'd like to set something up in such a way that a keybind ($mainMod + N, for example) will open a terminal (kitty) running tmux, with three panes open, neovim on the left, full height, about 60% width, and then the right split between two terminal panes. and have this all be pinned to window 3 (which would also be nice to have the clean setup, but transparency would be okay). 

feel free to offer  other suggestions for layouts, workflows, etc. i also take notes, journal etc using neovim integrated with obsidian, environements/languages at the moment are obviously lua, bash (sh or whatever for scripting), configs, dotfiles etc,.

---

**Assistant** - 2024-11-16 21:47:27 UTC

 This is an interesting project that we can approach in a few steps. Let's start with a basic script and then we can refine it based on your needs.

```bash
#!/bin/bash
# Save as ~/.local/bin/dev-workspace
# Don't forget: chmod +x ~/.local/bin/dev-workspace

# Start kitty with tmux
kitty tmux new-session -d -s dev \; \
    send-keys 'nvim' C-m \; \
    split-window -h -p 40 \; \
    split-window -v \; \
    select-pane -t 0

# Move to workspace 3
hyprctl dispatch workspace 3
```

And add to your hyprland config:
```bash
# Dev workspace binding
bind = $mainMod, N, exec, ~/.local/bin/dev-workspace

# Workspace 3 rules
windowrulev2 = workspace 3, class:^(kitty)$ title:^(dev)$
workspace = 3, rounding:0, gapsin:0, gapsout:0, border:1
windowrulev2 = opacity 0.90 override 0.90 override, workspace:3
```

Some suggestions for enhancement:

1. **Session Management**:
```bash
# Enhanced version with session handling
#!/bin/bash

SESSION="dev"

# Check if session exists
tmux has-session -t $SESSION 2>/dev/null

if [ $? != 0 ]; then
    # Create new session
    kitty tmux new-session -d -s $SESSION \; \
        send-keys 'nvim' C-m \; \
        split-window -h -p 40 \; \
        split-window -v \; \
        select-pane -t 0
else
    # Attach to existing session
    kitty tmux attach -t $SESSION
fi

# Move to workspace 3
hyprctl dispatch workspace 3
```

2. **Project-based Setup**:
```bash
#!/bin/bash
# Save as ~/.local/bin/dev-workspace

PROJECT_DIR=${1:-$HOME/projects/current}
SESSION="dev"

if [ ! -d "$PROJECT_DIR" ]; then
    notify-send "Error" "Project directory doesn't exist: $PROJECT_DIR"
    exit 1
fi

tmux has-session -t $SESSION 2>/dev/null

if [ $? != 0 ]; then
    kitty tmux new-session -d -s $SESSION -c "$PROJECT_DIR" \; \
        send-keys "nvim ." C-m \; \
        split-window -h -p 40 -c "$PROJECT_DIR" \; \
        split-window -v -c "$PROJECT_DIR" \; \
        select-pane -t 0
else
    kitty tmux attach -t $SESSION
fi

hyprctl dispatch workspace 3
```

Additional workflow suggestions:

1. **Neovim Integration**:
   - Consider using telescope-tmux.nvim for tmux integration
   - Setup tmux.conf to use vi keybindings for consistency
   - Use tmux-sessionizer (popularized by ThePrimeagen) for quick project switching

2. **Directory Structure**:
```bash
~/
├── .config/
│   ├── hypr/
│   │   ├── hyprland.conf
│   │   └── windowrules.conf  # Separate window rules
│   ├── nvim/
│   │   └── lua/
│   │       └── user/
│   └── tmux/
│       └── tmux.conf
└── .local/
    └── bin/
        └── dev-workspace
```

3. **Enhanced Window Rules**:
```bash
# In windowrules.conf
windowrulev2 = workspace 3, class:^(kitty)$ title:^(dev)$
windowrulev2 = tile, workspace:3
windowrulev2 = opacity 0.90 override 0.90 override, workspace:3
windowrulev2 = nofloat, workspace:3
windowrulev2 = nogaps, workspace:3
```

Would you like me to expand on any of these aspects or explore other workflow improvements? For instance, we could:
1. Add auto-saving tmux sessions
2. Create project-specific layouts
3. Integrate with your Obsidian workflow
4. Set up automatic workspace loading on startup

---

**Human** - 2024-11-16 21:50:55 UTC

i'll get you set up with this while we're at it too: nogaps and nofloat are popping errors in your original snippet.


Attachments:
- {'file_name': 'Window Rules – Hyprland Wiki.md', 'file_size': 14503, 'file_type': 'text/markdown', 'extracted_content': 'Window rules (both V1 and V2) are **case sensitive**. (e.g. `firefox` ≠ `Firefox`)\n\n## Window Rules V1[](https://wiki.hyprland.org/Configuring/Window-Rules/#window-rules-v1)\n\nYou can set window rules to achieve different behaviors from the active container.\n\n### Syntax[](https://wiki.hyprland.org/Configuring/Window-Rules/#syntax)\n\n-   `RULE` is a [rule](https://wiki.hyprland.org/Configuring/Window-Rules/#rules) (and a param if applicable)\n-   `WINDOW` is a [RegEx](https://en.wikipedia.org/wiki/Regular_expression), either:\n    -   plain RegEx (for matching a window class);\n    -   `title:` followed by a regex (for matching a window’s title)\n\n### Examples[](https://wiki.hyprland.org/Configuring/Window-Rules/#examples)\n\n## Window Rules V2[](https://wiki.hyprland.org/Configuring/Window-Rules/#window-rules-v2)\n\nIn order to allow more flexible rules, while retaining compatibility with the above rule system, window rules V2 were implemented.\n\nIn V2, you are allowed to match multiple variables.\n\nthe `RULE` field is unchanged, but in the `WINDOW` field, you can put regexes for multiple values like so:\n\nIn the case of dynamic window titles such as browser windows, keep in mind how powerful regex is.\n\nFor example, a window rule of: `windowrule = opacity 0.3 override 0.3 override,title:(.*)(- Youtube)$` will match _any_ window that contains a string of “- Youtube” after any other text. This could be multiple browser windows or other applications that contain the string for any reason.\n\nFor the `windowrulev2 = float,class:(kitty),title:(kitty)` example, the `class:(kitty)` `WINDOW` field is what keeps the window rule specific to kitty terminals.\n\nFor now, the supported fields for V2 are:\n\n| Field | Description |\n| --- | --- |\n| class:\\[regex\\] | Windows with `class` matching `regex`. |\n| title:\\[regex\\] | Windows with `title` matching `regex`. |\n| initialClass:\\[regex\\] | Windows with `initialClass` matching `regex`. |\n| initialTitle:\\[regex\\] | Windows with `initialTitle` matching `regex`. |\n| tag:\\[name\\] | Windows with matching `tag`. |\n| xwayland:\\[0/1\\] | Xwayland windows. |\n| floating:\\[0/1\\] | Floating windows. |\n| fullscreen:\\[0/1\\] | Fullscreen windows. |\n| pinned:\\[0/1\\] | Pinned windows. |\n| focus:\\[0/1\\] | Currently focused window. |\n| fullscreenstate:\\[internal\\] \\[client\\] | Windows with matching `fullscreenstate`. `internal` and `client` can be `*` - any, `0` - none, `1` - maximize, `2` - fullscreen, `3` - maximize and fullscreen. |\n| workspace:\\[w\\] | Windows on matching workspace. `w` can be `id` or `name:string`. |\n| onworkspace:\\[w\\] | Windows on matching workspace. `w` can be `id`, `name:string` or `workspace selector`. |\n\nKeep in mind that you _have_ to declare at least one field, but not all.\n\nTo get more information about a window’s class, title, XWayland status or its size, you can use `hyprctl clients`.\n\n## Rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#rules)\n\n### Static rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#static-rules)\n\nStatic rules are evaluated once when the window is opened and never again. This essentially means that it is always the `initialTitle` and `initialClass` which will be found when matching on `title` and `class`, respectively.\n\nIt is not possible to `float` (or any other of the static rules) a window based on a change in the `title` after the window has been created. This applies to all static rules listed here.\n\n| Rule | Description |\n| --- | --- |\n| float | floats a window |\n| tile | tiles a window |\n| fullscreen | fullscreens a window |\n| maximize | maximizes a window |\n| fullscreenstate \\[internal\\] \\[client\\] | sets the focused window’s fullscreen mode and the one sent to the client, where internal and client can be `0` - none, `1` - maximize, `2` - fullscreen, `3` - maximize and fullscreen |\n| move \\[x\\] \\[y\\] | moves a floating window (x,y -> int or %, e.g. 20% or 100. You are also allowed to do `100%-` for the right/bottom anchor, e.g. `100%-20`. In addition, the option supports the subtraction of the window size with `100%-w-`, e.g. `100%-w-20`. This results in a gap at the right/bottom edge of the screen to the window with the defined subtracted size). Additionally, you can also do `cursor [x] [y]` where x and y are either pixels or percent. Percent is calculated from the window’s size. Specify `onscreen` before other parameters to force the window into the screen (e.g. `move onscreen cursor 50% 50%`) |\n| size \\[x\\] \\[y\\] | resizes a floating window (x,y -> (</>)int or (</>)%, < -> maximum size, > -> minimum size, e.g. >20%, 100 or <500) |\n| center (\\[opt\\]) | if the window is floating, will center it on the monitor. Set opt as 1 to respect monitor reserved area |\n| pseudo | pseudotiles a window |\n| monitor \\[id\\] | sets the monitor on which a window should open. `id` can be either id or name (either e.g. `1` or e.g. `DP-1`) |\n| workspace \\[w\\] | sets the workspace on which a window should open (for workspace syntax, see [dispatchers->workspaces](https://wiki.hyprland.org/Configuring/Dispatchers#workspaces)). You can also make \\[w\\] to `unset`, will unset all previous workspace rules applied to this window. You can also add `silent` after the workspace to make the window open silently. |\n| noinitialfocus | disables the initial focus to the window |\n| pin | pins the window (i.e. show it on all workspaces) _note: floating only_ |\n| unset | removes all previously set rules for the given parameters. Please note it has to match EXACTLY. |\n| nomaxsize | removes max size limitations. Especially useful with windows that report invalid max sizes (e.g. winecfg) |\n| stayfocused | forces focus on the window as long as it’s visible |\n| group \\[options\\] | set window group properties. See the note below. |\n| suppressevent \\[types…\\] | ignores specific events from the window. Events are space separated, and can be: `fullscreen` `maximize` `activate` `activatefocus` |\n\n### Dynamic rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#dynamic-rules)\n\nDynamic rules are re-evaluated every time a property changes.\n\n| Rule | Description |\n| --- | --- |\n| animation \\[style\\] (\\[opt\\]) | forces an animation onto a window, with a selected opt. Opt is optional. |\n| bordercolor \\[c\\] | force the bordercolor of the window. Options for c: `color`/`color ... color angle` -> sets the active border color/gradient OR `color color`/`color ... color angle color ... color [angle]` -> sets the active and inactive border color/gradient of the window. See [variables->colors](https://wiki.hyprland.org/Configuring/Variables#variable-types) for color definition. |\n| idleinhibit \\[mode\\] | sets an idle inhibit rule for the window. If active, apps like `hypridle` will not fire. Modes: `none`, `always`, `focus`, `fullscreen` |\n| opacity \\[a\\] | additional opacity multiplier. Options for a: `float` -> sets an overall opacity OR `float float` -> sets activeopacity and inactiveopacity respectively, OR `float float float` -> sets activeopacity, inactiveopacity and fullscreenopacity respectively. |\n| tag \\[name\\] | apply tag to the window, use prefix `+`/`-` to set/unset flag, or no prefix to toggle the flag |\n| maxsize \\[x\\] \\[y\\] | sets the maximum size (x,y -> int) |\n| minsize \\[x\\] \\[y\\] | sets the minimum size (x,y -> int) |\n\nThe following rules can also be set with [`setprop`](https://wiki.hyprland.org/Configuring/Dispatchers#setprop):\n\n| Rule | Description |\n| --- | --- |\n| bordersize \\[int\\] | sets the border size |\n| rounding \\[int\\] | forces the application to have X pixels of rounding, ignoring the set default (in `decoration:rounding`). Has to be an int. |\n| allowsinput \\[on\\] | forces an XWayland window to receive input, even if it requests not to do so. (Might fix issues like e.g. Game Launchers not receiving focus for some reason) |\n| dimaround \\[on\\] | dims everything around the window . Please note this rule is meant for floating windows and using it on tiled ones may result in strange behavior. |\n| decorate \\[on\\] | whether to draw window decorations or not |\n| focusonactivate \\[on\\] | whether Hyprland should focus an app that requests to be focused (an `activate` request) |\n| keepaspectratio \\[on\\] | forces aspect ratio when resizing window with the mouse |\n| nearestneighbor \\[on\\] | forces the window to use the nearest neigbor filtering. |\n| noanim \\[on\\] | disables the animations for the window |\n| noblur \\[on\\] | disables blur for the window |\n| noborder \\[on\\] | disables borders for the window |\n| nodim \\[on\\] | disables window dimming for the window |\n| nofocus \\[on\\] | disables focus to the window |\n| nomaxsize \\[on\\] | disables max size for the window |\n| norounding \\[on\\] | disables rounding for the window |\n| noshadow \\[on\\] | disables shadows for the window |\n| noshortcutsinhibit \\[on\\] | disallows the app from [inhibiting your shortcuts](https://wayland.app/protocols/keyboard-shortcuts-inhibit-unstable-v1) |\n| opaque \\[on\\] | forces the window to be opaque |\n| forcergbx \\[on\\] | makes Hyprland ignore the alpha channel of all the window’s surfaces, effectively making it _actually, fully 100% opaque_ |\n| syncfullscreen \\[on\\] | whether the fullscreen mode should always be the same as the one sent to the window (will only take effect on the next fullscreen mode change) |\n| immediate \\[on\\] | forces the window to allow to be torn. See [the Tearing page](https://wiki.hyprland.org/Configuring/Tearing). |\n| xray \\[on\\] | sets blur xray mode for the window |\n| renderunfocused | forces the window to think it’s being rendered when it’s not visible - see also [Variables - Misc](https://wiki.hyprland.org/Configuring/Variables/#Misc) for setting `render_unfocused_fps` |\n\nWhen using window rules, \\[on\\] can be set to `0` for off, `1` for on or not set for default.\n\nWhen using `setprop`, \\[on\\] can be set to `0` for off, `1` for on, `toggle` to toggle the state or `unset` to unset previous values.\n\nWhen using `setprop`, \\[int\\] can also be `unset` to unset previous values.\n\n### `group` window rule options[](https://wiki.hyprland.org/Configuring/Window-Rules/#group-window-rule-options)\n\n-   `set` \\[`always`\\] - Open window as a group.\n-   `new` - Shorthand of `barred set`.\n-   `lock` \\[`always`\\] - Lock the group that added this window. Use with `set` or `new` (i.e. `new lock`) to create a new locked group.\n-   `barred` - Do not automatically group the window into the focused unlocked group.\n-   `deny` - Do not allow window to be toggled as or added to group (see `denywindowfromgroup` dispatcher).\n-   `invade` - Force open window in the locked group.\n-   `override` \\[other options\\] - Override other `group` rules, e.g. You can make all windows in a particular workspace open as a group, and use `group override barred` to make windows with specific titles open as normal windows.\n-   `unset` - Clear all `group` rules.\n\nThe `group` rule without options is a shorthand for `group set`.\n\nBy default, `set` and `lock` only affect new windows once. The `always` qualifier makes them always effective.\n\n### Tags[](https://wiki.hyprland.org/Configuring/Window-Rules/#tags)\n\nWindow may have several tags, either static or dynamic, dynamic tag will have a suffix of `*`. You may check window tags with `hyprctl clients`.\n\nUse `tagwindow` dispatcher to add a static tag to a window:\n\nUse `tag` rule to add a dynamic tag to a window:\n\nOr with keybind for convenience:\n\nThe `tag` rule can only manipulate dynamic tags, and the `tagwindow` dispatcher only work with static tags (as once the dispatcher is called, dynamic tags will be cleared).\n\n### Example Rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#example-rules)\n\n### Notes[](https://wiki.hyprland.org/Configuring/Window-Rules/#notes)\n\nRules that are marked as _Dynamic_ will be reevaluated if the matching property of the window changes. For instance, if a rule is defined that changes the `bordercolor` of a window when it is floating, then the `bordercolor` will change to the requested color when it is set to floating, and revert to the default color when it is tiled again.\n\nRules will be processed from top to bottom, where the _last_ match will take precedence. i.e.\n\nHere, all non-fullscreen kitty windows will have `opacity 0.8`, except if they are floating. Otherwise, they will have `opacity 0.5`. The rest of the non-fullscreen floating windows will have `opacity 0.5`.\n\nHere, all kitty windows will have `opacity 0.8`, even if they are floating. The rest of the floating windows will have `opacity 0.5`.\n\nOpacity is a PRODUCT of all opacities by default. For example, setting `activeopacity` to 0.5 and `opacity` to 0.5 will result in a total opacity of 0.25. You are allowed to set opacities over 1, but any opacity product over 1 will cause graphical glitches. For example, using `0.5 * 2 = 1` is fine, but `0.5 * 4 = 2` will cause graphical glitches. You can put `override` after an opacity value to override it to an exact value rather than a multiplier. For example, to set active and inactive opacity to 0.8, and make fullscreen windows fully opaque regardless of other opacity rules:\n\n## Layer Rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#layer-rules)\n\nSome things in Wayland are not windows, but layers. That includes, for example: app launchers, status bars, or wallpapers.\n\nThose have specific rules separate from windows:\n\nwhere `rule` is the rule and `namespace` is the namespace regex (find namespaces in `hyprctl layers`) or `address` is an address in the form of `address:0x[hex]`.\n\n### Rules[](https://wiki.hyprland.org/Configuring/Window-Rules/#rules-1)\n\n| rule | description |\n| --- | --- |\n| unset | removes all layerRules previously set for a select namespace regex. Please note it has to match _exactly_. |\n| noanim | disables animations |\n| blur | enables blur for the layer |\n| blurpopups | enables blur for the popups |\n| ignorealpha \\[a\\] | makes blur ignore pixels with opacity of `a` or lower. `a` is float value from 0 to 1. `a = 0` if unspecified. |\n| ignorezero | makes blur ignore fully transparent pixels. Same as `ignorealpha 0`. |\n| dimaround | dims everything behind the layer |\n| xray \\[on\\] | sets the blur xray mode for a layer. 0 for off, 1 for on, unset for default. |\n| animation \\[style\\] | allows you to set a specific animation style for this layer |\n| order \\[n\\] | sets the order relative to other layers. Higher means closer to the edge of the monitor. Can be negative. `n = 0` if unspecified. |'}
- Window Rules – Hyprland Wiki.md

---

**Assistant** - 2024-11-16 21:50:55 UTC

 Ah, good catch on the Hyprland rules. Let's correct the workspace rules first, then proceed with the tmux setup.

```bash
# Workspace 3 rules (corrected)
windowrulev2 = workspace 3, class:^(kitty)$ title:^(dev)$
windowrulev2 = tile, workspace:3  # Instead of nofloat
workspace = 3, rounding:0  # Combined workspace settings
windowrulev2 = opacity 0.90 override 0.90 override, workspace:3
windowrulev2 = noblur, workspace:3
windowrulev2 = norounding, workspace:3
```

Now for the dev workspace script:

```bash
#!/bin/bash
# Save as ~/.local/bin/dev-workspace

SESSION="dev"
WINDOW_NAME="dev"

# Function to create new session
create_session() {
    kitty --title "$WINDOW_NAME" tmux new-session -d -s "$SESSION" \; \
        rename-window "$WINDOW_NAME" \; \
        send-keys 'nvim' C-m \; \
        split-window -h -p 40 \; \
        split-window -v \; \
        select-pane -t 0
}

# Check if session exists
tmux has-session -t $SESSION 2>/dev/null

if [ $? != 0 ]; then
    create_session
else
    # If session exists but detached, reattach
    if [ -z "$(pgrep -f "kitty.*$WINDOW_NAME")" ]; then
        kitty --title "$WINDOW_NAME" tmux attach -t "$SESSION"
    else
        notify-send "Dev Workspace" "Session already running"
    fi
fi

# Move to workspace 3
hyprctl dispatch workspace 3
```

Add to your Hyprland config:
```bash
# Dev workspace binding
bind = $mainMod, N, exec, ~/.local/bin/dev-workspace
```

This setup:
1. Uses specific window title for better rule matching
2. Properly handles session management
3. Notifies if trying to create duplicate session
4. Uses corrected Hyprland rules

You might also want to add this to your `~/.config/tmux/tmux.conf` for better integration:
```bash
# Set terminal
set -g default-terminal "tmux-256color"
set -ag terminal-overrides ",xterm-kitty:RGB"

# Dev layout
bind-key M-n run-shell "~/.local/bin/dev-workspace"

# Better pane navigation
bind-key -n M-h select-pane -L
bind-key -n M-j select-pane -D
bind-key -n M-k select-pane -U
bind-key -n M-l select-pane -R
```

Would you like me to refine any part of this setup or add additional functionality?

---

**Human** - 2024-11-16 21:51:29 UTC

well, we need it for the workspace 4 rules too..

---

**Assistant** - 2024-11-16 21:51:29 UTC

 Let's correct the workspace 4 rules based on the Hyprland documentation:

```bash
# Workspace 4 assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance
workspace = 4, rounding:0  # Base workspace settings

# Everything tiling except Todoist (which is already floating from your global rules)
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = norounding, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4

# Optional: force clear decorations
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
```

This follows the proper Hyprland syntax and should work with your existing rules. Note that Todoist will remain floating because of your existing global float rule:
```bash
windowrulev2 = float, class:^(calendar|Todoist|Lxappearance|Rofi|kitty|Alacritty|thunar|viewnior|feh|pavucontrol-qt|pavucontrol|file-roller)$
```

Would you like to modify any of these settings or add additional workspace-specific behaviors?

---

**Assistant** - 2024-11-16 21:54:18 UTC

 Ah, for a true fullscreen workspace setup without any gaps or Waybar, we can use these rules:

```bash
# Workspace 4 assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance and behavior
workspace = 4, gapsin:0, gapsout:0, bordersize:1, rounding:0

# Window specific rules
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = norounding, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4

# Hide reserved space (Waybar) when on workspace 4
windowrulev2 = addreserved top 0, workspace:4
```

The key additions here are:
1. `gapsin:0, gapsout:0` in the workspace definition to remove all gaps
2. `bordersize:1` keeps a minimal border for visual separation
3. `addreserved top 0` removes the reserved space where Waybar would be

You might also want to add a keybind to quickly toggle Waybar visibility when switching to/from workspace 4:

```bash
# In your Hyprland config
bind = $mainMod, 4, workspace, 4; exec, hyprctl keyword monitor eDP-1,addreserved,0,0,0,0
```

This will hide Waybar when switching to workspace 4. If you want to restore Waybar when switching away, you could create a more complex binding using a script, would you like me to show you that?

---

**Human** - 2024-11-16 21:54:18 UTC

yeah, i was hoping for no gaps, in or out and no waybar? think all the way fullscreen, but still tiled.

---

**Human** - 2024-11-16 21:57:04 UTC

workspace 4 is on a second monitor, so a hard/systemwide  on/off for waybar isn't ideal. 

yours seems to have some conditions though..

---

**Assistant** - 2024-11-16 21:57:04 UTC

 Ah, for a multi-monitor setup, we can make the Waybar hiding specific to the monitor that workspace 4 is on. First, let's check which monitor workspace 4 is on:

```bash
hyprctl monitors
```

Then we can modify the rules to be monitor-specific. Assuming workspace 4 is on, say, HDMI-A-1:

```bash
# Workspace 4 assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance and behavior
workspace = 4, gapsin:0, gapsout:0, bordersize:1, rounding:0, monitor:HDMI-A-1

# Window specific rules
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = norounding, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4

# Hide reserved space for specific monitor
windowrulev2 = addreserved top 0, monitor:HDMI-A-1, workspace:4
```

Could you share your monitor configuration (output of `hyprctl monitors`)? That would help me make the rules more specific to your setup.

---

**Human** - 2024-11-16 21:57:38 UTC

for what it's worth: it doesnt like 

# Hide reserved space (Waybar) when on workspace 4
windowrulev2 = addreserved top 0, workspace:4

---

**Assistant** - 2024-11-16 21:57:38 UTC

 Ah yes, you're right - I made a mistake there. `addreserved` isn't actually a window rule, it's a monitor property. Let me correct that.

For monitor-specific Waybar hiding on workspace 4, we'll need to use a different approach. Instead of a window rule, we can utilize a workspace bind:

```bash
# Workspace 4 assignments and rules
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance and behavior
workspace = 4, gapsin:0, gapsout:0, bordersize:1, rounding:0

# Window specific rules
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = norounding, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4

# For the monitor-specific Waybar hiding, you'd use workspace binds:
bind = $mainMod, 4, workspace, 4; exec, hyprctl keyword monitor HDMI-A-1,addreserved,0,0,0,0
```

Could you run `hyprctl monitors` so I can give you the exact monitor name to use in that last bind?

---

**Human** - 2024-11-16 21:59:47 UTC

~  hyprctl monitors 
Monitor HDMI-A-1 (ID 0):
	2560x1440@143.99500 at 0x0
	description: Shenzhen KTC Technology Group M27T20 0x00000001
	make: Shenzhen KTC Technology Group
	model: M27T20
	serial: 0x00000001
	active workspace: 1 (1)
	special workspace: 0 ()
	reserved: 0 59 0 0
	scale: 1.00
	transform: 0
	focused: yes
	dpmsStatus: 1
	vrr: false
	solitary: 0
	activelyTearing: false
	disabled: false
	currentFormat: XRGB8888
	mirrorOf: none
	availableModes: 2560x1440@59.95Hz 3840x2160@59.94Hz 3840x2160@50.00Hz 3840x2160@29.97Hz 3840x2160@25.00Hz 3840x2160@23.98Hz 2560x1440@144.00Hz 2560x1440@120.00Hz 1920x1080@144.00Hz 1920x1080@119.88Hz 1920x1080@60.00Hz 1920x1080@59.94Hz 1920x1080@50.00Hz 1680x1050@59.95Hz 1600x900@60.00Hz 1280x1024@75.03Hz 1280x1024@60.02Hz 1440x900@59.89Hz 1280x720@60.00Hz 1280x720@59.94Hz 1280x720@50.00Hz 1024x768@75.03Hz 1024x768@60.00Hz 800x600@75.00Hz 800x600@72.19Hz 800x600@60.32Hz 720x576@50.00Hz 720x480@59.94Hz 640x480@75.00Hz 640x480@59.94Hz 640x480@59.93Hz 
Monitor DP-3 (ID 1):
	2560x2880@60.00100 at -1920x-660
	description: Guangxi Century Innovation Display Electronics Co. Ltd 28C1Q 0000000000000
	make: Guangxi Century Innovation Display Electronics Co., Ltd
	model: 28C1Q
	serial: 0000000000000
	active workspace: 4 (4)
	special workspace: 0 ()
	reserved: 0 59 0 0
	scale: 1.33
	transform: 0
	focused: no
	dpmsStatus: 1
	vrr: false
	solitary: 0
	activelyTearing: false
	disabled: false
	currentFormat: XRGB8888
	mirrorOf: none
	availableModes: 2560x2880@60.00Hz 2560x2880@30.00Hz 2560x1440@60.00Hz 1920x1080@60.00Hz 1920x1080@60.00Hz 1920x1080@50.00Hz 1680x1050@59.95Hz 1600x900@60.00Hz 1280x1024@75.03Hz 1280x1024@60.02Hz 1280x960@60.00Hz 1152x864@75.00Hz 1280x720@60.00Hz 1280x720@59.94Hz 1280x720@50.00Hz 1024x768@75.03Hz 1024x768@60.00Hz 800x600@75.00Hz 800x600@60.32Hz 720x576@50.00Hz 720x480@59.94Hz 640x480@75.00Hz 640x480@59.94Hz 640x480@59.93Hz

---

**Assistant** - 2024-11-16 21:59:47 UTC

 Ah perfect! I see workspace 4 is on DP-3. Here's the corrected configuration:

```bash
# Workspace 4 assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance and behavior
workspace = 4, gapsin:0, gapsout:0, bordersize:1, rounding:0, monitor:DP-3

# Window specific rules
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = norounding, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4

# Workspace bind with monitor-specific Waybar handling
bind = $mainMod, 4, workspace, 4; exec, hyprctl keyword monitor DP-3,addreserved,0,0,0,0
```

Since I see you have reserved space currently set (reserved: 0 59 0 0), you might want to create a script to toggle the Waybar visibility specifically for DP-3:

```bash
#!/bin/bash
# Save as ~/.local/bin/toggle-waybar-dp3

current_workspace=$(hyprctl monitors -j | jq '.[] | select(.name == "DP-3") | .activeWorkspace.id')

if [ "$current_workspace" -eq 4 ]; then
    hyprctl keyword monitor DP-3,addreserved,0,0,0,0
else
    hyprctl keyword monitor DP-3,addreserved,0,59,0,0
fi
```

Then you could bind it:
```bash
# Alternative workspace bind using the toggle script
bind = $mainMod, 4, workspace, 4; exec, ~/.local/bin/toggle-waybar-dp3
```

This will handle the Waybar visibility only on DP-3, leaving your other monitor's Waybar untouched.

---

**Human** - 2024-11-16 22:03:36 UTC

i don't think that works the way we want it to.. 

at the very least, it's currently doing nothing aside from the expected mod4 behavior

---

**Assistant** - 2024-11-16 22:03:36 UTC

 You're right. Let me try a different approach. 

First, let's diagnose what we have on workspace 4 by running:
```bash
hyprctl workspacerules
```

And:
```bash
hyprctl getoption monitor
```

Could you share those outputs? This will help us understand how Hyprland is currently handling your workspace 4 settings.

In the meantime, we could try a more direct approach using specific workspace and monitor settings:

```bash
# Workspace 4 specific configuration
monitor=DP-3,2560x2880@60,0x0,1.33
workspace=DP-3,4

# Application assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Workspace 4 appearance
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = bordersize 1, workspace:4
windowrulev2 = rounding 0, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4
```

The key questions are:
1. Are you wanting the Waybar to hide only when workspace 4 is focused?
2. Should it affect only DP-3's Waybar or all Waybars?
3. Should the gaps be removed from the entire workspace or just specific windows?

Let me know the outputs of those commands and your preferences on these questions.

---

**Human** - 2024-11-16 22:04:15 UTC

~  hyprctl workspacerules
Workspace rule 4:
	monitor: DP-3
	default: <unset>
	persistent: <unset>
	gapsIn: 0 0 0 0
	gapsOut: 0 0 0 0
	borderSize: 1
	border: <unset>
	rounding: false
	decorate: <unset>
	shadow: <unset>
	defaultName: <unset>

 ~  hyprctl getoption monitor
no such option

---

**Assistant** - 2024-11-16 22:04:15 UTC

 Thanks for the workspace rules output! It shows that some of our rules are working - we can see the gaps and border settings are applied.

For the monitor info, I apologize - let's try:
```bash
hyprctl getoption monitors
```

In the meantime, since we can see the workspace rules are partially working, let's try to refine the configuration. Here's a revised version:

```bash
# Monitor and workspace assignment
monitor=DP-3,2560x2880@60,0x0,1.33
workspace=4,monitor:DP-3

# Workspace 4 base configuration
workspace = 4, gapsin:0, gapsout:0, bordersize:1, rounding:0

# Application assignments
windowrulev2 = workspace 4, class:^(obsidian)$
windowrulev2 = workspace 4, class:^(Morgen)$
windowrulev2 = workspace 4, class:^(Todoist)$

# Window rules for workspace 4
windowrulev2 = tile, workspace:4,not:class:^(Todoist)$
windowrulev2 = bordersize 1, workspace:4
windowrulev2 = rounding 0, workspace:4
windowrulev2 = noblur, workspace:4
windowrulev2 = noshadow, workspace:4
windowrulev2 = opacity 1.0 override 1.0 override, workspace:4
```

For handling Waybar, we might need to approach this through Waybar's configuration instead. Could you show me your current Waybar config? It might be easier to configure Waybar to hide itself on workspace 4 rather than trying to handle it through Hyprland.

---

