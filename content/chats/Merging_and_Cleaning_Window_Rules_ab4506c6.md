---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Merging and Cleaning Window Rules

Created: 2024-12-08 16:56:29 UTC
Updated: 2024-12-08 16:57:57 UTC
UUID: ab4506c6-cf8e-4070-bb86-5a5df61d5265
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-12-08 16:56:37 UTC

looking to merge and clean up these keybind configs: 

# Window rules
windowrule = float, calendar
windowrule = float, Todoist
windowrule = size 1000 600, calendar
windowrule = center, calendar
windowrule = float, file_progress
windowrule = float, confirm
windowrule = float, dialog
windowrule = float, download
windowrule = float, notification
windowrule = float, error
windowrule = float, splash
windowrule = float, confirmreset
windowrule = float, title:Open File
windowrule = float, title:branchdialog
windowrule = float, Lxappearance
windowrule = opacity 0.96, fuzzel
windowrule = opacity 0.96 override 0.78 override 0.86 override, ^(obsidian)$ # set opacity to 1.0 active, 0.5 inactive and 0.8 fullscreen for obsidian
windowrule = opacity 0.96 override 0.78 override 0.86 override, ^(kitty)$ # set opacity to 1.0 active, 0.5 inactive and 0.8 fullscreen for kitty
windowrule = opacity 0.96 override 0.78 override 0.86 override, ^(kitty)$ # set opacity to 1.0 active, 0.5 inactive and 0.8 fullscreen for kitty
windowrule = float, Rofi
windowrule = float, kitty
windowrule = float, Alacritty
windowrule = float, thunar
windowrule = animation none, Rofi
windowrule = norounding, kitty
windowrule = float, viewnior
windowrule = float, feh
windowrule = float, pavucontrol-qt
windowrule = float, pavucontrol
windowrule = float, file-roller
windowrule = fullscreen, wlogout
windowrule = float, title:wlogout
windowrule = fullscreen, title:wlogout
windowrule = idleinhibit focus, mpv
windowrule = workspace 2, zen
windowrule = workspace 2, firefox
windowrule = workspace 3, Beeper
windowrule = workspace 4, nvim
windowrule = workspace 5, spotify
windowrule = idleinhibit fullscreen, firefox
windowrule = opaque, firefox
windowrule = opaque, zen
windowrule = opacity 0.96, Rofi
windowrule = float, title:^(Media viewer)$
windowrule = float, title:^(Volume Control)$
windowrule = float, title:^(Picture-in-Picture)$
windowrule = size 800 600, title:^(Volume Control)$
windowrule = move 75 44%, title:^(Volume Control)$


Attachments:
- {'file_name': 'paste.txt', 'file_size': 8325, 'file_type': 'txt', 'extracted_content': '# -----------------------------------------------------\n# Key bindings\n# name: "Default"\n# -----------------------------------------------------\n\n# SUPER KEY\n$mainMod = SUPER\n$HYPRSCRIPTS = ~/.config/hypr/scripts\n$SCRIPTS = ~/.config/ml4w/scripts\n\n# Applications\nbind = $mainMod, RETURN, exec, ~/.config/ml4w/settings/terminal.sh # Open the terminal\nbind = $mainMod, B, exec, ~/.config/ml4w/settings/browser.sh # Open the browser\nbind = $mainMod, E, exec, ~/.config/ml4w/settings/filemanager.sh # Open the filemanager\nbind = $mainMod CTRL, E, exec, ~/.config/ml4w/settings/emojipicker.sh # Open the emoji picker\nbind = $mainMod CTRL, C, exec, ~/.config/ml4w/settings/calculator.sh # Open the calculator\n\n# Windows\nbind = $mainMod, Q, killactive # Kill active window\nbind = ALT, RETURN, fullscreen, 1 # Maximize Window\nbind = CTRL ALT, RETURN, fullscreen, 0 # Set active window to fullscreen\nbind = $mainMod, F, togglefloating # Toggle active windows into floating mode\nbind = $mainMod SHIFT, F, exec, $HYPRSCRIPTS/toggleallfloat.sh # Toggle all windows into floating mode\nbind = $mainMod, J, togglesplit # Toggle split\nbind = $mainMod, left, movefocus, l # Move focus left\nbind = $mainMod, right, movefocus, r # Move focus right\nbind = $mainMod, up, movefocus, u # Move focus up\nbind = $mainMod, down, movefocus, d # Move focus down\n\n# New conditional movement bindings\n# For tiled windows: swap with the window in the given direction\nbind = $mainMod SHIFT, left, swapwindow, l\nbind = $mainMod SHIFT, right, swapwindow, r\nbind = $mainMod SHIFT, up, swapwindow, u\nbind = $mainMod SHIFT, down, swapwindow, d\n\n# For floating windows: move by 50 pixels\nbind = $mainMod SHIFT, left, moveactive, -50 0\nbind = $mainMod SHIFT, right, moveactive, 50 0\nbind = $mainMod SHIFT, up, moveactive, 0 -50\nbind = $mainMod SHIFT, down, moveactive, 0 50\n\n# Updated resize bindings for both tiled and floating windows\nbinde = $mainMod CTRL, right, resizeactive, 50 0\nbinde = $mainMod CTRL, left, resizeactive, -50 0\nbinde = $mainMod CTRL, down, resizeactive, 0 50\nbinde = $mainMod CTRL, up, resizeactive, 0 -50\n\n# Mouse bindings\nbindm = $mainMod, mouse:272, movewindow # Move window with the mouse\nbindm = $mainMod, mouse:273, resizewindow # Resize window with the mouse\n\nbind = $mainMod, G, togglegroup # Toggle window group\nbind = $mainMod, K, swapsplit # Swapsplit\n\n# Move focused window to other monitor\nbind = $mainMod, A, movecurrentworkspacetomonitor, -1\nbind = $mainMod, F, movecurrentworkspacetomonitor, +1\n\n# Alternative resize bindings (MOD+ALT+arrows)\nbinde = $mainMod ALT, right, resizeactive, 50 0\nbinde = $mainMod ALT, left, resizeactive, -50 0\nbinde = $mainMod ALT, down, resizeactive, 0 50\nbinde = $mainMod ALT, up, resizeactive, 0 -50\n\n# Actions\nbind = $mainMod SHIFT, SPACE, togglefloating\nbind = $mainMod SHIFT, A, exec, $HYPRSCRIPTS/toggle-animations.sh # Toggle animations\nbind = $mainMod, PRINT, exec, $HYPRSCRIPTS/screenshot.sh # Take a screenshot\nbind = $mainMod SHIFT, S, exec, $HYPRSCRIPTS/screenshot.sh # Take a screenshot\nbind = $mainMod, ESCAPE, exec, wlogout # Start wlogout\nbind = $mainMod SHIFT, W, exec, waypaper --random # Change the wallpaper\nbind = $mainMod CTRL, W, exec, waypaper # Open wallpaper selector\nbind = $mainMod ALT, W, exec, $HYPRSCRIPTS/wallpaper-automation.sh # Start random wallpaper script\nbind = $mainMod, SPACE, exec, rofi -show drun -replace -i # Open application launcher\nbind = $mainMod CTRL, K, exec, $HYPRSCRIPTS/keybindings.sh # Show keybindings\nbind = $mainMod SHIFT, B, exec, ~/.config/waybar/launch.sh # Reload waybar\nbind = $mainMod CTRL, B, exec, ~/.config/waybar/toggle.sh # Toggle waybar\nbind = $mainMod SHIFT, R, exec, $HYPRSCRIPTS/loadconfig.sh # Reload hyprland config\nbind = $mainMod, V, exec, $SCRIPTS/cliphist.sh # Open clipboard manager\nbind = $mainMod CTRL, T, exec, ~/.config/waybar/themeswitcher.sh # Open waybar theme switcher\nbind = $mainMod CTRL, S, exec, ~/.config/ml4w/apps/ML4W_Dotfiles_Settings-x86_64.AppImage # Open ML4W Dotfiles Settings app\nbind = $mainMod SHIFT, H, exec, $HYPRSCRIPTS/hyprshade.sh # Toggle screenshader\nbind = $mainMod ALT, G, exec, $HYPRSCRIPTS/gamemode.sh # Toggle game mode\nbind = $mainMod, Z, exec, missioncenter # Open Mission Center\n\n# Workspaces\nbind = $mainMod, 1, workspace, 1 # Open workspace 1\nbind = $mainMod, 2, workspace, 2 # Open workspace 2\nbind = $mainMod, 3, workspace, 3 # Open workspace 3\nbind = $mainMod, 4, workspace, 4 # Open workspace 4\nbind = $mainMod, 5, workspace, 5 # Open workspace 5\nbind = $mainMod, 6, workspace, 6 # Open workspace 6\nbind = $mainMod, 7, workspace, 7 # Open workspace 7\nbind = $mainMod, 8, workspace, 8 # Open workspace 8\nbind = $mainMod, 9, workspace, 9 # Open workspace 9\nbind = $mainMod, 0, workspace, 10 # Open workspace 10\n\nbind = $mainMod SHIFT, 1, movetoworkspace, 1 # Move active window to workspace 1\nbind = $mainMod SHIFT, 2, movetoworkspace, 2 # Move active window to workspace 2\nbind = $mainMod SHIFT, 3, movetoworkspace, 3 # Move active window to workspace 3\nbind = $mainMod SHIFT, 4, movetoworkspace, 4 # Move active window to workspace 4\nbind = $mainMod SHIFT, 5, movetoworkspace, 5 # Move active window to workspace 5\nbind = $mainMod SHIFT, 6, movetoworkspace, 6 # Move active window to workspace 6\nbind = $mainMod SHIFT, 7, movetoworkspace, 7 # Move active window to workspace 7\nbind = $mainMod SHIFT, 8, movetoworkspace, 8 # Move active window to workspace 8\nbind = $mainMod SHIFT, 9, movetoworkspace, 9 # Move active window to workspace 9\nbind = $mainMod SHIFT, 0, movetoworkspace, 10 # Move active window to workspace 10\n\nbind = $mainMod, Tab, workspace, m+1 # Open next workspace\nbind = $mainMod SHIFT, Tab, workspace, m-1 # Open previous workspace\n\nbind = $mainMod CTRL, 1, exec, $HYPRSCRIPTS/moveTo.sh 1 # Move all windows to workspace 1\nbind = $mainMod CTRL, 2, exec, $HYPRSCRIPTS/moveTo.sh 2 # Move all windows to workspace 2\nbind = $mainMod CTRL, 3, exec, $HYPRSCRIPTS/moveTo.sh 3 # Move all windows to workspace 3\nbind = $mainMod CTRL, 4, exec, $HYPRSCRIPTS/moveTo.sh 4 # Move all windows to workspace 4\nbind = $mainMod CTRL, 5, exec, $HYPRSCRIPTS/moveTo.sh 5 # Move all windows to workspace 5\nbind = $mainMod CTRL, 6, exec, $HYPRSCRIPTS/moveTo.sh 6 # Move all windows to workspace 6\nbind = $mainMod CTRL, 7, exec, $HYPRSCRIPTS/moveTo.sh 7 # Move all windows to workspace 7\nbind = $mainMod CTRL, 8, exec, $HYPRSCRIPTS/moveTo.sh 8 # Move all windows to workspace 8\nbind = $mainMod CTRL, 9, exec, $HYPRSCRIPTS/moveTo.sh 9 # Move all windows to workspace 9\nbind = $mainMod CTRL, 0, exec, $HYPRSCRIPTS/moveTo.sh 10 # Move all windows to workspace 10\n\nbind = $mainMod, mouse_down, workspace, e+1 # Open next workspace\nbind = $mainMod, mouse_up, workspace, e-1 # Open previous workspace\nbind = $mainMod CTRL, down, workspace, empty # Open the next empty workspace\n\n# Passthrough SUPER KEY to Virtual Machine\n# bind = $mainMod, P, submap, passthru # Passthrough SUPER key to virtual machine\n# submap = passthru\n# bind = SUPER, Escape, submap, reset # Get SUPER key back from virtual machine\n# submap = reset\n\n# Fn keys\nbind = , XF86MonBrightnessUp, exec, brightnessctl -q s +10% # Increase brightness by 10%\nbind = , XF86MonBrightnessDown, exec, brightnessctl -q s 10%- # Reduce brightness by 10%\nbind = , XF86AudioRaiseVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ +5% # Increase volume by 5%\nbind = , XF86AudioLowerVolume, exec, pactl set-sink-volume @DEFAULT_SINK@ -5% # Reduce volume by 5%\nbind = , XF86AudioMute, exec, wpctl set-mute @DEFAULT_AUDIO_SINK@ toggle # Toggle mute\nbind = , XF86AudioPlay, exec, playerctl play-pause # Audio play pause\nbind = , XF86AudioPause, exec, playerctl pause # Audio pause\nbind = , XF86AudioNext, exec, playerctl next # Audio next\nbind = , XF86AudioPrev, exec, playerctl previous # Audio previous\nbind = , XF86AudioMicMute, exec, pactl set-source-mute @DEFAULT_SOURCE@ toggle # Toggle microphone\nbind = , XF86Calculator, exec, ~/.config/ml4w/settings/calculator.sh # Open calculator\nbind = , XF86Lock, exec, hyprlock # Open screenlock\nbind = , XF86Tools, exec, alacritty --class dotfiles-floating -e ~/.config/ml4w/apps/ML4W_Dotfiles_Settings-x86_64.AppImage # Open ML4W Dotfiles Settings app\n\nbind = , code:238, exec, brightnessctl -d smc::kbd_backlight s +10\nbind = , code:237, exec, brightnessctl -d smc::kbd_backlight s 10-'}
- paste.txt

---

**Assistant** - 2024-12-08 16:56:37 UTC

 I'll help you merge and clean up these window rules with the existing keybind configurations. Let me create a clean, organized version that combines both.

<antThinking>This is a good case for an artifact since it's a configuration file that will be referenced and used separately, and it's longer than 20 lines.</antThinking>

<antArtifact identifier="hyprland-config" type="application/vnd.ant.code" language="conf" title="Merged Hyprland Configuration">
# -----------------------------------------------------
# Key bindings and Window Rules
# name: "Default"
# -----------------------------------------------------

# SUPER KEY
$mainMod = SUPER
$HYPRSCRIPTS = ~/.config/hypr/scripts
$SCRIPTS = ~/.config/ml4w/scripts

# Window Rules
# Floating windows
window

---

**Human** - 2024-12-08 16:57:57 UTC

ah crap.. one moment. i wanted all windowrules and for whatever reason i gave you keybinds.. ummm. orignal pasted text and the additional here: 

# -----------------------------------------------------
# Window rules
# -----------------------------------------------------
windowrule = tile,^(Microsoft-edge)$
windowrule = tile,^(Brave-browser)$
windowrule = tile,^(Chromium)$
windowrule = float,^(pavucontrol)$
windowrule = float,^(blueman-manager)$
windowrule = float,^(nm-connection-editor)$
windowrule = float,^(org.gnome.Nautilus)$
windowrule = float,^(Todoist)$
# windowrule = float,^(empty)$
# Browser Picture in Picture
windowrulev2 = float, title:^(Picture-in-Picture)$
windowrulev2 = pin, title:^(Picture-in-Picture)$
windowrulev2 = move 69.5% 4%, title:^(Picture-in-Picture)$
# Kitty Specific Rules
windowrule = float,^(kitty)$
windowrule = size 800 600,^(kitty)$
windowrule = rounding 0,^(kitty)$

---

**Assistant** - 2024-12-08 16:57:57 UTC

 Now I'll help merge and clean up both sets of window rules, removing duplicates and organizing them logically.

<antThinking>This is a good case for an artifact since it's a configuration file that needs to be maintained separately and is longer than 20 lines. We'll organize the rules by categories for better maintainability.</antThinking>

<antArtifact identifier="hyprland-window-rules" type="application/vnd.ant.code" language="conf" title="Merged Hyprland Window Rules">
# -----------------------------------------------------
# Window Rules Configuration
# -----------------------------------------------------

# Browsers and Web Apps
windowrule = tile, ^(Microsoft-edge)$
windowrule = tile, ^(Brave-browser)$
windowrule = tile, ^(Chromium)$
windowrule = workspace 2, firefox
windowrule = workspace 2, zen
windowrule = opaque, firefox
windowrule = opaque, zen
windowrule = idleinhibit fullscreen, firefox

# Picture-in-Picture
windowrulev2 = float, title:^(Picture-in-Picture)$
windowrulev2 = pin, title:^(Picture-in-Picture)$
windowrulev2 = move 69.5% 4%, title:^(Picture-in-Picture)$
windowrule = float, title:^(Picture-in-Picture)$

# Terminal Emulators
windowrule = float, kitty
windowrule = size 800 600, ^(kitty)$
windowrule = rounding 0, ^(kitty)$
windowrule = norounding, kitty
windowrule = opacity 0.96 override 0.78 override 0.86 override, ^(kitty)$
windowrule = float, Alacritty

# System Dialogs and Utilities
windowrule = float, pavucontrol
windowrule = float, pavucontrol-qt
windowrule = float, blueman-manager
windowrule = float, nm-connection-editor
windowrule = float, org.gnome.Nautilus
windowrule = float, thunar
windowrule = float, file-roller
windowrule = float, file_progress
windowrule = float, confirm
windowrule = float, dialog
windowrule = float, download
windowrule = float, notification
windowrule = float, error
windowrule = float, splash
windowrule = float, confirmreset
windowrule = float, title:Open File
windowrule = float, title:branchdialog
windowrule = float, Lxappearance

# Media and Viewers
windowrule = float, viewnior
windowrule = float, feh
windowrule = float, title:^(Media viewer)$
windowrule = idleinhibit focus, mpv

# Applications with Specific Workspaces
windowrule = workspace 3, Beeper
windowrule = workspace 4, nvim
windowrule = workspace 5, spotify

# Volume Control
windowrule = float, title:^(Volume Control)$
windowrule = size 800 600, title:^(Volume Control)$
windowrule = move 75 44%, title:^(Volume Control)$

# Productivity Apps
windowrule = float, calendar
windowrule = float, Todoist
windowrule = size 1000 600, calendar
windowrule = center, calendar
windowrule = opacity 0.96 override 0.78 override 0.86 override, ^(obsidian)$

# System UI Elements
windowrule = float, Rofi
windowrule = opacity 0.96, Rofi
windowrule = animation none, Rofi
windowrule = opacity 0.96, fuzzel
windowrule = fullscreen, wlogout
windowrule = float, title:wlogout
windowrule = fullscreen, title:wlogout
</antArtifact>

I've organized the window rules into logical categories and:
1. Removed duplicate rules
2. Grouped related applications together
3. Standardized the formatting
4. Kept all specific opacity and workspace assignments
5. Maintained special handling for Picture-in-Picture windows
6. Preserved all application-specific behaviors

Would you like me to make any adjustments to this organization or add any additional rules?

---

