---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Configuring Kitty Terminal for Fish Shell

Created: 2024-10-29 21:09:24 UTC
Updated: 2024-11-19 14:24:12 UTC
UUID: e7cf2402-e07e-495c-8f5d-375b9057f0a9
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-10-29 21:09:30 UTC

seems i may need to reformat my kitty.conf for use with fish?


Attachments:
- {'file_name': 'paste.txt', 'file_size': 4957, 'file_type': 'txt', 'extracted_content': '~ ➜ source .config/kitty/kitty.conf\nfish: Unknown command: font_size\n.config/kitty/kitty.conf (line 5): \nfont_size 16.0\n^~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: include\n.config/kitty/kitty.conf (line 7): \ninclude $HOME/repos/dots/gruvbox-material-kitty/colors/gruvbox-material-dark-hard.conf\n^~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: remember_window_size\n.config/kitty/kitty.conf (line 9): \nremember_window_size no\n^~~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: initial_window_width\n.config/kitty/kitty.conf (line 10): \ninitial_window_width 1080\n^~~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: initial_window_height\n.config/kitty/kitty.conf (line 11): \ninitial_window_height 600\n^~~~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: window_margin_width\n.config/kitty/kitty.conf (line 12): \nwindow_margin_width 15\n^~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: confirm_os_window_close\n.config/kitty/kitty.conf (line 13): \nconfirm_os_window_close 2\n^~~~~~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: tab_bar_edge\n.config/kitty/kitty.conf (line 14): \ntab_bar_edge top\n^~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: tab_bar_style\n.config/kitty/kitty.conf (line 15): \ntab_bar_style powerline\n^~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: tab_powerline_style\n.config/kitty/kitty.conf (line 16): \ntab_powerline_style angled\n^~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: cursor_shape\n.config/kitty/kitty.conf (line 18): \ncursor_shape beam\n^~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: cursor_blink_interval\n.config/kitty/kitty.conf (line 19): \ncursor_blink_interval 0\n^~~~~~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: disable_ligatures\n.config/kitty/kitty.conf (line 20): \ndisable_ligatures never\n^~~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: url_style\n.config/kitty/kitty.conf (line 24): \nurl_style curly\n^~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 29): \nmap ctrl+shift+c copy_to_clipboard\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 30): \nmap cmd+c copy_and_clear_or_interrupt\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 31): \nmap ctrl+t new_tab\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 32): \nmap ctrl+shift+1 goto_tab 1\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 33): \nmap ctrl+shift+2 goto_tab 2\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 34): \nmap ctrl+shift+3 goto_tab 3\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 35): \nmap ctrl+shift+4 goto_tab 4\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 36): \nmap ctrl+shift+5 goto_tab 5\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 37): \nmap ctrl+shift+6 goto_tab 6\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 38): \nmap ctrl+shift+7 goto_tab 7\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 39): \nmap ctrl+shift+8 goto_tab 8\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 40): \nmap ctrl+shift+9 goto_tab 9\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: map\n.config/kitty/kitty.conf (line 41): \nmap ctrl+shift+0 goto_tab 0\n^~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: include\n.config/kitty/kitty.conf (line 47): \ninclude current-theme.conf\n^~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: font_family\n.config/kitty/kitty.conf (line 52): \nfont_family      family="MesloLGLDZ Nerd Font Mono"\n^~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: bold_font\n.config/kitty/kitty.conf (line 53): \nbold_font        auto\n^~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: italic_font\n.config/kitty/kitty.conf (line 54): \nitalic_font      auto\n^~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\nfish: Unknown command: bold_italic_font\n.config/kitty/kitty.conf (line 55): \nbold_italic_font auto\n^~~~~~~~~~~~~~~^\nfrom sourcing file .config/kitty/kitty.conf\n~ ✗ '}
- paste.txt

---

**Assistant** - 2024-10-29 21:09:30 UTC

 I can see the issue - you're trying to `source` the kitty config file directly in fish, but that's not how kitty's configuration works. The kitty.conf file uses kitty's own configuration syntax and should not be sourced as a shell script.

Kitty reads its configuration file directly - you don't need to source it. The errors you're seeing are because fish is trying to interpret kitty's config syntax as fish commands, which they're not.

To fix this:

1. Remove the `source` command - you don't need it
2. Make sure your kitty config is in the right location:
```bash
~/.config/kitty/kitty.conf
```

3. To apply changes to kitty's configuration, either:
- Restart kitty
- Or use the hot-reload shortcut: `ctrl+shift+f5`
- Or send the reload command:
```bash
kill -SIGUSR1 $(pidof kitty)
```

Your actual kitty.conf syntax looks correct - it's just that you shouldn't be trying to source it as a shell script. Kitty will read and apply this configuration automatically when it starts up.

---

**Human** - 2024-10-29 21:12:05 UTC

ah, i see.. i was trying to get it so that it would prompt me if i was trying to close the window with a process running (nvim typically) 

i thought that the confirm_os_window_close 2 line configured that.

---

**Assistant** - 2024-10-29 21:12:05 UTC

 Yes, `confirm_os_window_close 2` is the correct setting for that behavior! The issue isn't with your configuration - it's just that the changes weren't being applied correctly because of the sourcing attempt.

Here's what the values mean for `confirm_os_window_close`:
- `0`: Never prompt
- `1`: Prompt only if there are background processes
- `2`: Always prompt (what you want)

Your config line is correct:
```
confirm_os_window_close 2
```

Just make sure the config file is saved, then either:
1. Restart kitty
2. Or hit `ctrl+shift+f5` to reload the config

You should then get the prompt when trying to close windows with active processes. You can test it by opening nvim in kitty and trying to close the window.

If for some reason it's still not working after a reload, you can verify kitty is reading your config by running:
```bash
kitty --debug-config | grep confirm_os_window_close
```

---

**Human** - 2024-10-29 21:12:20 UTC

───────┬────────────────────────────────────────────────────────────────────────
       │ File: .config/kitty/kitty.conf
───────┼────────────────────────────────────────────────────────────────────────
   1   │ # font_family      IosevkaTerm Nerd Font
   2   │ # bold_font        auto
   3   │ # italic_font      auto
   4   │ # bold_italic_font auto
   5   │ font_size 16.0
   6   │ #theme start
   7   │ include $HOME/repos/dots/gruvbox-material-kitty/colors/gruvbox-material
       │ -dark-hard.conf
   8   │ #theme end
   9   │ remember_window_size no
  10   │ initial_window_width 1080
  11   │ initial_window_height 600
  12   │ window_margin_width 15
  13   │ confirm_os_window_close 2
  14   │ tab_bar_edge top
  15   │ tab_bar_style powerline
  16   │ tab_powerline_style angled
  17   │ #Cursor config
  18   │ cursor_shape beam
  19   │ cursor_blink_interval 0
  20   │ disable_ligatures never
  21   │ 
  22   │ #url customization
  23   │ 
  24   │ url_style curly
  25   │ 
  26   │ 
  27   │ 
  28   │ #keybinds 
  29   │ map ctrl+shift+c copy_to_clipboard
  30   │ map cmd+c copy_and_clear_or_interrupt
  31   │ map ctrl+t new_tab
  32   │ map ctrl+shift+1 goto_tab 1
  33   │ map ctrl+shift+2 goto_tab 2
  34   │ map ctrl+shift+3 goto_tab 3
  35   │ map ctrl+shift+4 goto_tab 4
  36   │ map ctrl+shift+5 goto_tab 5
  37   │ map ctrl+shift+6 goto_tab 6
  38   │ map ctrl+shift+7 goto_tab 7
  39   │ map ctrl+shift+8 goto_tab 8
:

apologies.

---

**Assistant** - 2024-10-29 21:12:20 UTC

 Here's what I'm noticing in your config:

1. Line 7 - your `include` path has a line break in it which will cause issues. Let's fix that first:
```bash
include $HOME/repos/dots/gruvbox-material-kitty/colors/gruvbox-material-dark-hard.conf
```

2. You have the setting `confirm_os_window_close 2` correctly set on line 13, but if you're not seeing the prompt, let's verify kitty is actually using this config:

```bash
kitty --debug-config | grep -A 1 confirm_os_window_close
```

Also, there's no font family actively set (they're all commented out). If you want to use IosevkaTerm Nerd Font, uncomment line 1:
```bash
font_family      IosevkaTerm Nerd Font
```

Try fixing the include path first, save, reload with `ctrl+shift+f5`, and let me know if you're still not getting the confirmation prompt when closing windows with active processes.

---

**Human** - 2024-10-29 21:13:51 UTC

# font_family      IosevkaTerm Nerd Font
# bold_font        auto
# italic_font      auto
# bold_italic_font auto
font_size 16.0
#theme start
include $HOME/repos/dots/gruvbox-material-kitty/colors/gruvbox-material-dark-hard.conf
#theme end
remember_window_size no
initial_window_width 1080
initial_window_height 600
window_margin_width 15
confirm_os_window_close 2
tab_bar_edge top
tab_bar_style powerline
tab_powerline_style angled
#Cursor config
cursor_shape beam
cursor_blink_interval 0
disable_ligatures never
#url customization
url_style curly
#keybinds 
map ctrl+shift+c copy_to_clipboard
map cmd+c copy_and_clear_or_interrupt
map ctrl+t new_tab
map ctrl+shift+1 goto_tab 1
map ctrl+shift+2 goto_tab 2
map ctrl+shift+3 goto_tab 3
map ctrl+shift+4 goto_tab 4
map ctrl+shift+5 goto_tab 5
map ctrl+shift+6 goto_tab 6
map ctrl+shift+7 goto_tab 7
map ctrl+shift+8 goto_tab 8
map ctrl+shift+9 goto_tab 9
map ctrl+shift+0 goto_tab 0
# BEGIN_KITTY_THEME
# Gruvbox Material Dark Soft
include current-theme.conf
# END_KITTY_THEME
# BEGIN_KITTY_FONTS
font_family      family="MesloLGLDZ Nerd Font Mono"
bold_font        auto
italic_font      auto
bold_italic_font auto
# END_KITTY_FONTS

it cut off funny because i pasted output from bat. here's the buffer from nvim

---

**Assistant** - 2024-10-29 21:13:51 UTC

 I see a couple of potential issues in your config:

1. The font family line has an incorrect syntax - `family=` shouldn't be there:
```bash
# Change this line:
font_family      family="MesloLGLDZ Nerd Font Mono"
# To this:
font_family      MesloLGLDZ Nerd Font Mono
```

2. You have two theme includes that might be conflicting:
```bash
# At the top:
include $HOME/repos/dots/gruvbox-material-kitty/colors/gruvbox-material-dark-hard.conf
# Later in the file:
include current-theme.conf
```

Let's verify your config is being read correctly:
```bash
kitty --debug-config
```

And we can also check if kitty is running with the expected settings:
```bash
ps aux | grep kitty
```

Try fixing the font family syntax first, then reload with `ctrl+shift+f5`. The window close confirmation should work after that. If not, we can dig deeper into the debug output.

---

**Human** - 2024-10-29 21:26:40 UTC

i mean, everything else seems to work fine, it's the os confirm function, maybe this'll shed some light? 

confirm_os_window_close
confirm_os_window_close -1
Ask for confirmation when closing an OS window or a tab with at least this number of kitty windows in it by window manager (e.g. clicking the window close button or pressing the operating system shortcut to close windows) or by the close_tab action. A value of zero disables confirmation. This confirmation also applies to requests to quit the entire application (all OS windows, via the quit action). Negative values are converted to positive ones, however, with shell_integration enabled, using negative values means windows sitting at a shell prompt are not counted, only windows where some command is currently running. Note that if you want confirmation when closing individual windows, you can map the close_window_with_confirmation action.

---

**Assistant** - 2024-10-29 21:26:40 UTC

 Ah, that documentation adds some clarity! The `confirm_os_window_close` behavior is more nuanced than I initially explained.

Since you're using Hyprland (a window manager), you might need a different approach. Try this instead:

1. First, remove or comment out the current setting:
```bash
# confirm_os_window_close 2
```

2. Add this keybinding to your config:
```bash
map ctrl+shift+w close_window_with_confirmation
```

The `close_window_with_confirmation` action is specifically designed to prompt for confirmation when closing individual windows, which is what you want when closing nvim sessions.

If you want both behaviors (OS window closing confirmation AND individual window confirmation), you can keep both:
```bash
confirm_os_window_close 1
map ctrl+shift+w close_window_with_confirmation
```

This way, you'll get prompts when:
1. Closing individual windows with `ctrl+shift+w`
2. Closing OS windows with background processes (if you keep `confirm_os_window_close 1`)

---

**Human** - 2024-10-29 21:27:27 UTC

what's this shell integration all about?

---

**Assistant** - 2024-10-29 21:27:27 UTC

 Shell integration in kitty is a powerful feature that enables better terminal functionality. It works by injecting some special scripts into your shell's initialization (fish in your case) to enable features like:

1. Detecting running commands vs shell prompt state
2. Command output marking/navigation
3. Better directory tracking
4. Enhanced keyboard shortcuts

To enable it:

```bash
# For fish shell
echo "source (kitty +kitten shell-integration/fish/vendor_conf.fish)" >> ~/.config/fish/config.fish
```

Some useful features you get:
- Jump between command prompts with `ctrl+shift+up/down`
- Click to jump to directory paths
- Better detection of running processes (which improves that window closing behavior we were discussing)
- Improved window titles showing current command/directory

You can test if it's working with:
```bash
echo $KITTY_SHELL_INTEGRATION
```

Should output something like `enabled` if it's working.

Want to try it out? We can enable it and see if it improves the window closing behavior you were looking for.

---

**Assistant** - 2024-10-29 21:28:47 UTC

 Ah, I provided outdated info. The correct way to set up shell integration in kitty is:

```bash
# First, get the integration script
kitty +kitten shell-integration install_fish

# Or for a manual setup, add this to ~/.config/fish/config.fish
if test -n "$KITTY_INSTALLATION_DIR"
    set --global KITTY_SHELL_INTEGRATION enabled
    source "$KITTY_INSTALLATION_DIR/shell-integration/fish/vendor_conf.fish"
end
```

The `kitty +kitten shell-integration install_fish` command will automatically set up the integration for fish shell. After running it:

1. Restart your shell/kitty
2. Verify it's working:
```bash
echo $KITTY_SHELL_INTEGRATION  # Should output "enabled"
```

This should give you better process detection for window closing prompts, among other features. Want to give it a try?

---

**Human** - 2024-10-29 21:28:47 UTC

Available builtin kittens:
broadcast
icat
show_key
pager
query_terminal
remote_file
themes
choose_fonts
hyperlinked_grep
notify
unicode_input
hints
clipboard
resize_window
panel
ssh
transfer
diff
ask
No kitten named shell-integration/fish/vendor_conf.fish
Welcome to fish, the friendly interactive shell
Type help for instructions on how to use fish

---

**Human** - 2024-10-29 21:31:29 UTC

out of curiosity i just tried the value -1. it worked the way i had hoped.

---

**Assistant** - 2024-10-29 21:31:29 UTC

 Ah, perfect! The negative value is actually the more intelligent option here. Let me explain why `-1` works better than `2`:

```bash
confirm_os_window_close -1
```

With `-1`, kitty only prompts for confirmation when there's an actual running process (like nvim) but NOT when you're just sitting at a shell prompt. This is more useful because:

1. You get prompted when closing windows with active work (nvim, running programs)
2. No annoying prompts when closing empty terminal windows or shells at prompt
3. It leverages kitty's process detection to make smart decisions

This is definitely the better setting than the positive values I suggested earlier. Thanks for experimenting with it - I learned something too! Want to try other smart kitty features now that we've got this sorted?

---

**Human** - 2024-10-29 21:50:56 UTC

i'd like for a program to run upon terminal opening to dress things up a bit.. specifically pokemon-colorscripts -rs --no-title what's that syntax and where's it go?

---

**Assistant** - 2024-10-29 21:50:56 UTC

 For fish shell, there are a couple of ways to run pokemon-colorscripts on terminal launch. The most straightforward is to add it to your fish config:

```bash
# Add to ~/.config/fish/config.fish
if status is-interactive
    pokemon-colorscripts -rs --no-title
end
```

The `if status is-interactive` check ensures it only runs for interactive sessions (not scripts).

First, make sure you have it installed:
```bash
paru -S pokemon-colorscripts
```

If you want to avoid the command affecting shell startup time, you could also use fish's event system:
```bash
# Alternative approach in config.fish
function display_pokemon --on-variable PWD
    pokemon-colorscripts -rs --no-title
    functions -e display_pokemon  # Remove the function after first run
end
```

Try the first simpler approach and if you notice any startup lag, we can switch to the event-based method.

---

**Human** - 2024-10-29 22:07:45 UTC

ooh, id love if there was some way that the size of the output could scale independently of the font size of the terminal..

---

**Assistant** - 2024-10-29 22:07:45 UTC

 Unfortunately, ASCII/ANSI art (which pokemon-colorscripts uses) is tied to character cells, so it can't scale independently of the font size in a traditional sense. However, we can try a few approaches:

1. Use kitty's built-in window resizing to maintain a consistent view:
```bash
# Add to your kitty.conf
initial_window_width 80c  # c means characters
initial_window_height 24c # adjust these numbers as needed
```

2. Or we could write a small wrapper script that picks different sized pokemon based on your terminal dimensions:

```bash
# ~/.config/fish/functions/pokemon-display.fish
function pokemon-display
    set -l term_height (tput lines)
    
    if test $term_height -lt 20
        pokemon-colorscripts -rs --no-title --small
    else if test $term_height -lt 30
        pokemon-colorscripts -rs --no-title
    else
        pokemon-colorscripts -rs --no-title --large # Note: large option doesn't exist, just showing the concept
    end
end
```

The real scalable alternative would be using kitty's image protocol (icat) with actual PNG images, but that's a different approach entirely. Would you like to explore that option instead?

---

**Human** - 2024-10-29 22:08:34 UTC

no i think i'll just make due. thanks

---

**Assistant** - 2024-10-29 22:08:34 UTC

 Got it! If you ever want to tweak the spacing or layout, you can adjust the `window_margin_width` in your kitty.conf or play with the terminal dimensions. Happy Pokémon displaying!

---

**Human** - 2024-11-19 14:19:24 UTC

i've got a bit of tweaking, but it's on fish. not on kitty.. i'm trying to set up some more robust keybinds/aliases/actions for fzf

---

**Assistant** - 2024-11-19 14:19:24 UTC

 For fzf in fish, here's a starting point with some common bindings and functions:

```fish
# ~/.config/fish/config.fish or ~/.config/fish/functions/fzf_setup.fish

# Set fzf options
set -x FZF_DEFAULT_OPTS '--height 40% --reverse --border'

# Search history
bind \cr '_fzf_search_history'

# File search
bind \cf '_fzf_search_files'

# Directory navigation
bind \co '_fzf_search_directory'

function _fzf_search_history
    history | fzf --no-sort | read -l command
    if test $command
        commandline -f repaint
        commandline -r $command
    end
end

function _fzf_search_files
    fd --type f --hidden --follow --exclude .git | \
    fzf --preview 'bat --style=numbers --color=always {}' | \
    read -l result
    if test $result
        commandline -r "nvim $result"
        commandline -f execute
    end
end

function _fzf_search_directory
    fd --type d --hidden --follow --exclude .git | \
    fzf --preview 'tree -C {} | head -100' | \
    read -l result
    if test $result
        cd $result
    end
end
```

This gives you:
- `Ctrl+R`: History search
- `Ctrl+F`: File search with bat preview
- `Ctrl+O`: Directory navigation with tree preview

Want to expand on any specific functionality?

---

**Human** - 2024-11-19 14:23:09 UTC

far as i can tell, these are the only two lines i had.

---

**Assistant** - 2024-11-19 14:23:09 UTC

 Share those two lines and I can help expand your fzf configuration. FZF is a powerful tool - knowing what you currently have will help me suggest relevant additions.

---

**Human** - 2024-11-19 14:23:21 UTC

# FZF configuration
set -gx FZF_DEFAULT_OPTS "--height 40% --layout=reverse --border --margin=1 --padding=1"
set -gx FZF_DEFAULT_COMMAND 'fd --type f --hidden --follow --exclude .git'

---

**Assistant** - 2024-11-19 14:23:21 UTC

 Those are good base settings. Here's a practical expansion with common fish bindings:

```fish
# Keep your existing settings
set -gx FZF_DEFAULT_OPTS "--height 40% --layout=reverse --border --margin=1 --padding=1"
set -gx FZF_DEFAULT_COMMAND 'fd --type f --hidden --follow --exclude .git'

# History search with Ctrl+R 
bind \cr 'history | fzf | commandline -r'

# File search with Ctrl+F (opens in nvim)
bind \cf 'fd --type f --hidden --follow --exclude .git | fzf --preview "bat --style=numbers --color=always {}" | read -l result; and nvim $result'

# Directory jumping with Ctrl+O
bind \co 'fd --type d --hidden --follow --exclude .git | fzf --preview "tree -C {} | head -100" | read -l result; and cd $result'
```

Want any modifications to these bindings or additional functionality?

---

**Human** - 2024-11-19 14:24:12 UTC

i was just going to cut these lines out.. i had already created a new file in my fish/conf.d/ with your previous response

---

**Assistant** - 2024-11-19 14:24:12 UTC

 Those lines duplicate your settings - feel free to remove them from `config.fish` since you've already put the expanded configuration in `conf.d/`. Having them in both places could cause conflicts.

---

