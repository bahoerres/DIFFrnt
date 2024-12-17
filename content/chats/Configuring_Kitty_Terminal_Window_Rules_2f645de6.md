---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Configuring Kitty Terminal Window Rules

Created: 2024-10-20 20:20:35 UTC
Updated: 2024-10-20 20:32:53 UTC
UUID: 2f645de6-52ac-4292-8e81-d52ee621ef98
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-20 20:20:45 UTC

can you pull up windowrules from all of our conversation on this project? i'm specifically looking for some regarding kitty and making sure it's floating, a certain size and no rounding on the corners

---

**Assistant** - 2024-10-20 20:20:45 UTC

 I apologize, but I don't have access to any previous conversations or context about this project. Each interaction I have starts fresh, without any memory of past conversations. 

However, I can provide some general information about window rules for Kitty terminal that might be helpful:

To make Kitty floating, set a certain size, and remove corner rounding, you would typically use window rules in your window manager or compositor configuration. The exact syntax depends on your specific setup (e.g., i3, Sway, Hyprland), but here's a general idea of what those rules might look like:

For i3/Sway:
```
for_window [app_id="kitty"] floating enable, resize set 800 600, border pixel 0
```

For Hyprland:
```
windowrule = float,^(kitty)$
windowrule = size 800 600,^(kitty)$
windowrule = rounding 0,^(kitty)$
```

These rules would:
1. Make Kitty float
2. Set its size to 800x600 pixels
3. Remove corner rounding (for Hyprland) or set a borderless window (for i3/Sway)

If you need more specific help, please provide details about your window manager or compositor, and I'll be happy to assist further.

---

**Assistant** - 2024-10-20 20:30:40 UTC

 The syntax for a keybind to change focus between floating and tiling windows depends on the specific window manager or compositor you're using. Since you haven't specified which one you're working with, I'll provide examples for a few common ones:

1. For i3/Sway:
```
bindsym $mod+Space focus mode_toggle
```

2. For Hyprland:
```
bind = $mainMod, Space, cyclenext, floating
```

3. For bspwm:
```
bspc config pointer_follows_focus true
super + space
    bspc node -f {next,prev}.local.!hidden.window
```

4. For Awesome WM:
```
awful.key({ modkey }, "space", function()
    awful.client.focus.toggle_floating()
end, {description = "toggle focus between tiling and floating", group = "client"})
```

These keybinds typically use the `Super` (Windows) key as the modifier, represented by `$mod`, `$mainMod`, or `modkey`, depending on the window manager. The `Space` key is a common choice for this action, but you can change it to any key you prefer.

If you're using a different window manager or need a more specific configuration, please let me know which one you're using, and I can provide a more tailored answer.

---

**Human** - 2024-10-20 20:30:40 UTC

what's the syntax for a keybind to change focus between floating and tiling?

---

**Human** - 2024-10-20 20:32:53 UTC

i am using hyprland. either we have different thoughts about what i'm trying to say, or the syntax is different. that one doesnt seem to do anything

---

**Assistant** - 2024-10-20 20:32:53 UTC

 I apologize for the confusion. You're right, and I appreciate you pointing that out. Let's clarify what you're trying to achieve and provide the correct Hyprland syntax.

For Hyprland, if you want to switch focus between floating and tiled windows, the correct syntax is:

```
bind = $mainMod, Space, togglefloating,
```

This command toggles the floating state of the currently focused window. However, if you specifically want to change focus between floating and tiled windows (rather than toggling the state), you would use:

```
bind = $mainMod, Space, cyclenext, floating 
bind = $mainMod SHIFT, Space, cyclenext, 
```

The first line cycles focus through floating windows, while the second line (with SHIFT) cycles through all windows.

If you want a single keybind to switch focus between the most recently focused floating and tiled windows, you might need to use a custom script or dispatcher, as Hyprland doesn't have a built-in command for this specific action.

Thank you for the clarification. Could you please describe exactly what behavior you're looking for when you press the keybind? This will help me provide the most accurate solution for your Hyprland setup.

---

