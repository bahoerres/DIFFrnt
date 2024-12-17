---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting Duplicate Rofi Launcher Entries

Created: 2024-11-14 20:28:11 UTC
Updated: 2024-11-14 20:53:04 UTC
UUID: 6255fa0b-3c6f-478a-b246-280e3ce72253
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-14 20:28:16 UTC

i use rofi as my launcher and i've noticed that it's got a couple of duplicate listings, or some that persist after removal. obsidian, specifically. 

could you help me troubleshoot this?

---

**Assistant** - 2024-11-14 20:28:16 UTC

 As a fellow Arch user, I know exactly what you're dealing with. This typically happens because rofi is finding desktop entries from multiple locations.

First, let's check where these duplicate entries are coming from:

```bash
find {/usr,~/.local}/share/applications -name "*obsidian*.desktop"
```

If you see entries that shouldn't be there anymore, you can remove them. Common locations to check:
- ~/.local/share/applications
- /usr/share/applications
- /usr/local/share/applications

You can also clear rofi's cache:
```bash
rm ~/.cache/rofi-3.runcache
```

If you want to check what rofi is actually reading, you can run:
```bash
rofi -dump-config | grep desktop
```

Want me to help you track down the specific duplicates based on what the `find` command shows?

---

**Human** - 2024-11-14 20:28:27 UTC

2z

---

**Assistant** - 2024-11-14 20:28:27 UTC

 Let's check those locations:

```bash
find {/usr,~/.local}/share/applications -name "*obsidian*.desktop" -ls
```

This will show us the files with timestamps and permissions. My guess is you might have a stale desktop entry in ~/.local that's conflicting with the system one.

If you copy/paste what you see, I can help you clean it up. Sometimes these persist after uninstalling via paru because the local desktop entry doesn't get cleaned up properly.

---

**Human** - 2024-11-14 20:31:29 UTC

~  find {/usr,~/.local}/share/applications -name "*obsidian*.desktop"
find: ‘~/.local/share/applications’: No such file or directory

 ~  rofi -dump-config | grep desktop
/*	drun-use-desktop-cache: false;*/
/*	drun-reload-desktop-cache: false;*/

---

**Assistant** - 2024-11-14 20:31:29 UTC

 Ah, interesting - so you don't have any user-level desktop entries, but you're still seeing duplicates. Let's check the system-wide entries:

```bash
find /usr/share/applications -name "*obsidian*.desktop" -ls
```

Also, since we see your rofi isn't using desktop cache, let's check what rofi actually sees:

```bash
rofi -show drun -dump
```

This will show us all entries rofi is picking up. We can then track down where these duplicates are coming from. Since ~/.local/share/applications doesn't exist, the issue might be in how the application is registering itself with your system.

---

**Human** - 2024-11-14 20:32:40 UTC

~  find /usr/share/applications -name "*obsidian*.desktop" -ls
 ~  rofi -show drun -dump
 ~  Debug: Will run Obsidian with the following arguments: 
Debug: Additionally, user gave: 
[13:1114/143201.799376:ERROR:bus.cc(407)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
2024-11-14 20:32:02 Loading main app package /app/resources/obsidian.asar
Ignored: Error: ENOENT: no such file or directory, open '/home/blake/.var/app/md.obsidian.Obsidian/config/obsidian/obsidian.json'
LaunchProcess: failed to execvp:
xdg-settings
[13:1114/143202.035020:ERROR:wayland_connection.cc(198)] Failed to connect to Wayland display: No such file or directory (2)
[13:1114/143202.035050:ERROR:ozone_platform_wayland.cc(264)] Failed to initialize Wayland platform
[13:1114/143202.035063:ERROR:env.cc(258)] The platform failed to initialize.  Exiting.
/app/bin/obsidian.sh: line 61:    13 Segmentation fault      (core dumped) zypak-wrapper /app/obsidian $@ ${EXTRA_ARGS[@]}

---

**Assistant** - 2024-11-14 20:32:40 UTC

 Ah, this is getting interesting. I see you're using the Flatpak version of Obsidian (evident from the `/app` path and `.var` directory), and it seems to be having some issues with Wayland/Hyprland.

Let's first check if the desktop entry is coming from Flatpak:

```bash
flatpak list | grep obsidian
find /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/ -name "*.desktop"
```

Also, let's verify what desktop files rofi is actually finding:

```bash
locate obsidian.desktop
```

If `locate` doesn't find anything, you might need to:
```bash
sudo updatedb
```

The Wayland error suggests we might need to ensure proper Wayland support for Flatpak. Could you also check:
```bash
echo $XDG_RUNTIME_DIR
ls -la /run/user/$(id -u)/
```

This will help us understand if there's a deeper issue with the Flatpak integration that's causing rofi to see phantom entries.

---

**Human** - 2024-11-14 20:35:21 UTC

~  flatpak list | grep obsidian
     find /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/ -name "*.desktop"
Obsidian	md.obsidian.Obsidian	1.7.6	stable	system
/var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop


 ~  locate obsidian.desktop
pread: Short read (file corrupted?)

 ~  echo $XDG_RUNTIME_DIR
     ls -la /run/user/$(id -u)/
/run/user/1000
drwx------    - blake 14 Nov 14:31  .
drwxr-xr-x    - root  12 Nov 16:17  ..
drwxr-xr-x    - blake 14 Nov 14:32  .dbus-proxy
drwxr-xr-x    - blake 14 Nov 14:32  .flatpak
lrwxrwxrwx    - blake 14 Nov 14:21  .flatpak-cache -> /var/tmp/flatpak-cache-7KGAX2
drwx------    - blake 13 Nov 17:09  .flatpak-helper
.rw------- 7.5M blake 12 Nov 16:17  .hyprpaper_4DZAjN
.rw-------  21M blake 12 Nov 16:17  .hyprpaper_jPg6dq
.rw-------  30M blake 12 Nov 16:17  .hyprpaper_TabVHE
srw-------    - blake 12 Nov 16:22  1Password-BrowserSupport.sock
drwxr-xr-x    - blake 13 Nov 17:09  app
drwx------    - blake 12 Nov 16:17  at-spi
srw-rw-rw-    - blake 12 Nov 16:17  bus
drwx------    - blake 13 Nov 17:16  dconf
dr-x------    - blake 31 Dec  1969  doc
|rw-------    - blake 12 Nov 16:18  fish_universal_variables.notifier
drwx------    - blake 12 Nov 22:37  gnupg
dr-x------    - blake 12 Nov 16:17  gvfs
drwx------    - blake 13 Nov 17:16  gvfsd
drwx------    - blake 12 Nov 16:17  hypr
.rw-r--r--    4 blake 12 Nov 16:17  hyprpaper.lock
drwx------    - blake 12 Nov 22:37  keyring
srwxr-xr-x    - blake 13 Nov 17:51  nvim.157288.0
.rw-------    5 blake 12 Nov 16:28  op-daemon.pid
srwxr-xr-x    - blake 12 Nov 16:28  op-daemon.sock
drwxr-xr-x    - blake 12 Nov 16:17  p11-kit
srw-rw-rw-    - blake 12 Nov 16:17  pipewire-0
srw-rw-rw-    - blake 12 Nov 16:17  pipewire-0-manager
.rw-r-----    0 blake 12 Nov 16:17  pipewire-0-manager.lock
.rw-r-----    0 blake 12 Nov 16:17  pipewire-0.lock
drwx------    - blake 12 Nov 16:17  pulse
.rw-------    6 blake 14 Nov 14:31  rofi.pid
srw-------    - blake 12 Nov 16:21  s.sock
drwx------    - blake 12 Nov 22:02  speech-dispatcher
drwxr-xr-x    - blake 14 Nov 14:21  systemd
srwxr-xr-x    - blake 12 Nov 16:17  wayland-1
.rw-r-----    0 blake 12 Nov 16:17  wayland-1.lock

---

**Assistant** - 2024-11-14 20:35:21 UTC

 Your locate database seems corrupted, but we found the Flatpak desktop entry. Let's rebuild the locate database and check where these duplicates might be coming from:

```bash
sudo updatedb
```

In the meantime, let's check exactly what rofi is seeing:

```bash
XDG_CURRENT_DESKTOP=Hyprland dex --list
```

Also, since we know the Flatpak desktop entry location, let's inspect it:

```bash
cat /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
```

The dex command will show us all desktop entries that are being registered with your system. This should help us identify where the duplicates are coming from, since we don't see any obvious duplicate files in the standard locations.

For a quick fix, you could try:
```bash
flatpak update
rm -f ~/.local/share/applications/md.obsidian.Obsidian*.desktop
```

---

**Assistant** - 2024-11-14 20:37:30 UTC

 Ah sorry, my mistake. Let's try a different approach to see what desktop entries rofi is finding:

```bash
# List all desktop files in standard locations
find /usr/share/applications /var/lib/flatpak/exports/share/applications -name "*.desktop" | grep -i obsidian

# And check the Flatpak entry's content
cat /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop
```

Also, let's check if there are any broken symlinks that might be causing this:

```bash
find /usr/share/applications /var/lib/flatpak/exports/share/applications -xtype l
```

This will help us see if there are any stale symlinks that might be confusing rofi.

---

**Human** - 2024-11-14 20:37:30 UTC

~  XDG_CURRENT_DESKTOP=Hyprland dex --list
usage: dex [options] [DesktopEntryFile [DesktopEntryFile ...]]
dex: error: unrecognized arguments: --list

---

**Human** - 2024-11-14 20:37:56 UTC

~  cat /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
[Desktop Entry]
Name=Obsidian
Exec=/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=obsidian.sh --file-forwarding md.obsidian.Obsidian @@u %U @@
Terminal=false
Type=Application
Icon=md.obsidian.Obsidian
StartupWMClass=obsidian
Comment=Obsidian
MimeType=x-scheme-handler/obsidian;
Categories=Office;
X-Flatpak-Tags=proprietary;
X-Flatpak=md.obsidian.Obsidian

---

**Assistant** - 2024-11-14 20:37:56 UTC

 One possible issue is that Flatpak creates entries in multiple locations. Let's check all possible locations:

```bash
# Check both the app-specific and exported locations
ls -l /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop
ls -l /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop

# And check if there are any symlinks
readlink -f /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop
```

If you're seeing duplicates in rofi specifically, we might also want to try:
```bash
# Remove any rofi caches
rm -f ~/.cache/rofi*

# Then run rofi with debug output
rofi -show drun -dump | grep -i obsidian
```

This will help us see exactly what entries rofi is picking up and where they're coming from.

---

**Assistant** - 2024-11-14 20:38:19 UTC

 Interesting - we can see the Flatpak setup has:
1. The main desktop file in the app directory
2. A symlink in the exports directory
3. And it appears there's a third path in the versioned directory

Let's clean this up:

```bash
# First, remove any potential rofi caches
rm -f ~/.cache/rofi*

# Check for any additional symlinks or entries
find /var/lib/flatpak -name "*obsidian*.desktop" -ls

# And verify XDG data dirs
echo $XDG_DATA_DIRS
```

After running these, try launching rofi again. If you still see duplicates, we might need to check if there's an issue with how XDG_DATA_DIRS is being populated in your Hyprland session.

Also, could you show me what entries you're actually seeing in rofi when you search for Obsidian? This will help us understand if it's picking up entries from different paths or if it's the same entry being shown multiple times.

---

**Human** - 2024-11-14 20:38:19 UTC

~  # Check both the app-specific and exported locations
     ls -l /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop
     ls -l /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
     # And check if there are any symlinks
     readlink -f /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop
lrwxrwxrwx - root 12 Nov 16:15  /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop -> ../../../app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
.rwxr-xr-x 370 root 12 Nov 16:15  /var/lib/flatpak/app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
/var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/d3b0657c21559553152f8be3dbe3fc08bf102c636fd77566280c1f1a9af63fc0/export/share/applications/md.obsidian.Obsidian.desktop

---

**Human** - 2024-11-14 20:38:44 UTC

~  # First, remove any potential rofi caches
     rm -f ~/.cache/rofi*
     # Check for any additional symlinks or entries
     find /var/lib/flatpak -name "*obsidian*.desktop" -ls
     # And verify XDG data dirs
     echo $XDG_DATA_DIRS
  3053744      4 -rwxr-xr-x   1 root     root          370 Nov 12 16:15 /var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/d3b0657c21559553152f8be3dbe3fc08bf102c636fd77566280c1f1a9af63fc0/export/share/applications/md.obsidian.Obsidian.desktop
  1800269      4 -rw-r--r--   2 root     root          204 Dec 31  1969 /var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/d3b0657c21559553152f8be3dbe3fc08bf102c636fd77566280c1f1a9af63fc0/files/share/applications/md.obsidian.Obsidian.desktop
  3053750      4 lrwxrwxrwx   1 root     root          103 Nov 12 16:15 /var/lib/flatpak/exports/share/applications/md.obsidian.Obsidian.desktop -> ../../../app/md.obsidian.Obsidian/current/active/export/share/applications/md.obsidian.Obsidian.desktop
/home/blake/.local/share/flatpak/exports/share /var/lib/flatpak/exports/share /usr/local/share /usr/share /var/lib/snapd/desktop

---

**Assistant** - 2024-11-14 20:38:44 UTC

 Now we can see what's happening - there are multiple entries:
1. One in the versioned Flatpak directory
2. A desktop file in the Flatpak files directory
3. The symlink in exports

Also, your XDG_DATA_DIRS includes both Flatpak paths, which might be causing rofi to see multiple entries.

Let's try this fix:

```bash
# Remove the duplicate in the files directory
sudo rm /var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/*/files/share/applications/md.obsidian.Obsidian.desktop

# Clear rofi cache again
rm -f ~/.cache/rofi*
```

If that doesn't work, we could try modifying how rofi searches for applications. Create or edit `~/.config/rofi/config.rasi`:

```bash
configuration {
    drun {
        parse-user false;
        parse-system true;
    }
}
```

This should tell rofi to be more strict about where it looks for desktop entries. Let me know if you still see duplicates after trying these fixes.

---

**Human** - 2024-11-14 20:39:49 UTC

~  # Remove the duplicate in the files directory
     sudo rm /var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/*/files/share/applications/md.obsidian.Obsidian.desktop
     # Clear rofi cache again
     rm -f ~/.cache/rofi*
rm: cannot remove '/var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/d3b0657c21559553152f8be3dbe3fc08bf102c636fd77566280c1f1a9af63fc0/files/share/applications/md.obsidian.Obsidian.desktop': No such file or directory
fish: No matches for wildcard '~/.cache/rofi*'. See `help wildcards-globbing`.
rm -f ~/.cache/rofi*
      ^~~~~~~~~~~~~^
 ~ 

---

**Assistant** - 2024-11-14 20:39:49 UTC

 The errors suggest the files don't exist anymore - let's verify what entries rofi is actually seeing. 

First, let's create the config file:

```bash
mkdir -p ~/.config/rofi
cat > ~/.config/rofi/config.rasi << 'EOF'
configuration {
    drun {
        parse-user false;
        parse-system true;
    }
}
EOF
```

Then let's check exactly what desktop files are being seen:

```bash
# Check if rofi cache directory exists
ls -la ~/.cache/rofi-3.runcache 2>/dev/null

# And verify current Flatpak desktop entries
find /var/lib/flatpak -name "*obsidian*.desktop" -type f
```

When you launch rofi, how many Obsidian entries do you see exactly? And what are their exact names?

---

**Human** - 2024-11-14 20:42:37 UTC

i suppose, it probably would have helped had i shared mine to begin with:


Attachments:
- {'file_name': 'paste.txt', 'file_size': 7566, 'file_type': 'txt', 'extracted_content': ' ~ \ue0b0 cat .config/rofi/config.rasi \n/*\n#  ____        __ _  \n# |  _ \\ ___  / _(_) \n# | |_) / _ \\| |_| | \n# |  _ < (_) |  _| | \n# |_| \\_\\___/|_| |_| \n#                    \n# by Stephan Raabe (2023) \n# ----------------------------------------------------- \n*/\n\n/* ---- Configuration ---- */\nconfiguration {\n    modi:                       "drun,run";\n    font:                       "Fira Sans 11";\n    show-icons:                 true;\n    icon-theme:                 "kora";\n    display-drun:               "APPS";\n    display-run:                "RUN";\n    display-filebrowser:        "FILES";\n    display-window:             "WINDOW";\n\tdrun-display-format:        "{name}";\n    hover-select:               false;\n    scroll-method:              1;\n    me-select-entry:            "";\n    me-accept-entry:            "MousePrimary";\n    window-format:              "{w} · {c} · {t}";\n    \n}\n\n/* ---- Load font ---- */\n@import "~/.config/ml4w/settings/rofi-font.rasi"\n\n/* ---- Load pywal colors (custom wal template) ---- */\n@import "~/.cache/wal/colors-rofi-pywal"\n\n/* ---- Load wallpaper ---- */\n@import "~/.config/ml4w/cache/current_wallpaper.rasi"\n\n/* ---- Load border width ---- */\n@import "~/.config/ml4w/settings/rofi-border.rasi"\n\n/* ---- Window ---- */\nwindow {\n    width:                        900px;\n    x-offset:                     0px;\n    y-offset:                     0px;\n    spacing:                      0px;\n    padding:                      0px;\n    margin:                       0px; \n    color:                        #FFFFFF;\n    border:                       @border-width;\n    border-color:                 #FFFFFF;\n    cursor:                       "default";\n    transparency:                 "real";\n    location:                     center;\n    anchor:                       center;\n    fullscreen:                   false;\n    enabled:                      true;\n    border-radius:                10px;\n    background-color:             transparent;\n}\n\n/* ---- Mainbox ---- */\nmainbox {\n    enabled:                      true;\n    orientation:                  horizontal;\n    spacing:                      0px;\n    margin:                       0px;\n    background-color:             @background;\n    background-image:             @current-image;\n    children:                     ["imagebox","listbox"];\n}\n\n/* ---- Imagebox ---- */\nimagebox {\n    padding:                      18px;\n    background-color:             transparent;\n    orientation:                  vertical;\n    children:                     [ "inputbar", "dummy", "mode-switcher" ];\n}\n\n/* ---- Listbox ---- */\nlistbox {\n    spacing:                     20px;\n    background-color:            transparent;\n    orientation:                 vertical;\n    children:                    [ "message", "listview" ];\n}\n\n/* ---- Dummy ---- */\ndummy {\n    background-color:            transparent;\n}\n\n/* ---- Inputbar ---- */\ninputbar {\n    enabled:                      true;\n    text-color:                   @foreground;\n    spacing:                      10px;\n    padding:                      15px;\n    border-radius:                10px;\n    border-color:                 @foreground;\n    background-color:             @background;\n    children:                     [ "textbox-prompt-colon", "entry" ];\n}\n\ntextbox-prompt-colon {\n    enabled:                      true;\n    expand:                       false;\n    str:                          "\uf002";\n    padding:                      0px 5px 0px 0px;\n    background-color:             transparent;\n    text-color:                   inherit;\n}\n\nentry {\n    enabled:                      true;\n    background-color:             transparent;\n    text-color:                   inherit;\n    cursor:                       text;\n    placeholder:                  "Search";\n    placeholder-color:            inherit;\n}\n\n/* ---- Mode Switcher ---- */\nmode-switcher{\n    enabled:                      true;\n    spacing:                      20px;\n    background-color:             transparent;\n    text-color:                   @foreground;\n}\n\nbutton {\n    padding:                      10px;\n    border-radius:                10px;\n    background-color:             @background;\n    text-color:                   inherit;\n    cursor:                       pointer;\n    border:                       0px;\n}\n\nbutton selected {\n    background-color:             @color11;\n    text-color:                   @foreground;\n}\n\n/* ---- Listview ---- */\nlistview {\n    enabled:                      true;\n    columns:                      1;\n    lines:                        8;\n    cycle:                        false;\n    dynamic:                      false;\n    scrollbar:                    false;\n    layout:                       vertical;\n    reverse:                      false;\n    fixed-height:                 true;\n    fixed-columns:                true;\n    spacing:                      0px;\n    padding:                      10px;\n    margin:                       0px;\n    background-color:             @background;\n    border:0px;\n}\n\n/* ---- Element ---- */\nelement {\n    enabled:                      true;\n    padding:                      10px;\n    margin:                       5px;\n    cursor:                       pointer;\n    background-color:             @background;\n    border-radius:                10px;\n    border:                       @border-width;\n}\n\nelement normal.normal {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement normal.urgent {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement normal.active {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement selected.normal {\n    background-color:            @color11;\n    text-color:                  @foreground;\n}\n\nelement selected.urgent {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement selected.active {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement alternate.normal {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement alternate.urgent {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement alternate.active {\n    background-color:            inherit;\n    text-color:                  @foreground;\n}\n\nelement-icon {\n    background-color:            transparent;\n    text-color:                  inherit;\n    size:                        32px;\n    cursor:                      inherit;\n}\n\nelement-text {\n    background-color:            transparent;\n    text-color:                  inherit;\n    cursor:                      inherit;\n    vertical-align:              0.5;\n    horizontal-align:            0.0;\n}\n\n/*****----- Message -----*****/\nmessage {\n    background-color:            transparent;\n    border:0px;\n    margin:20px 0px 0px 0px;\n    padding:0px;\n    spacing:0px;\n    border-radius: 10px;\n}\n\ntextbox {\n    padding:                     15px;\n    margin:                      0px;\n    border-radius:               0px;\n    background-color:            @background;\n    text-color:                  @foreground;\n    vertical-align:              0.5;\n    horizontal-align:            0.0;\n}\n\nerror-message {\n    padding:                     15px;\n    border-radius:               20px;\n    background-color:            @background;\n    text-color:                  @foreground;\n}\n\n ~ \ue0b0 '}
- paste.txt

---

**Assistant** - 2024-11-14 20:42:37 UTC

 Ah yes - I see you're using a more sophisticated rofi config. Let's modify it to be more strict about desktop entry parsing without breaking your existing setup.

Add these lines in your configuration section (right after `window-format`):

```bash
    drun {
        parse-user false;
        parse-system true;
    }
```

So it would look like:
```bash
configuration {
    modi:                       "drun,run";
    font:                       "Fira Sans 11";
    /* ... your existing config ... */
    window-format:              "{w} · {c} · {t}";
    
    drun {
        parse-user false;
        parse-system true;
    }
}
```

Now let's verify what Flatpak entries exist:
```bash
find /var/lib/flatpak -name "*obsidian*.desktop" -type f -ls
```

Could you also let me know exactly what you see when you search for Obsidian in rofi? Are there identical entries or are they labeled differently?

---

**Assistant** - 2024-11-14 20:51:33 UTC

 I see only one actual file now, which is good. Let's try one more diagnostic step to see exactly what rofi is picking up.

Create a small script to check all possible desktop entry locations:

```bash
#!/bin/bash
echo "=== XDG Data Dirs ==="
echo $XDG_DATA_DIRS | tr ':' '\n'
echo
echo "=== All Obsidian desktop files ==="
for dir in $(echo $XDG_DATA_DIRS | tr ':' ' '); do
    find "$dir/applications" -name "*obsidian*.desktop" 2>/dev/null
done
```

Save this as `check_desktop.sh`, make it executable (`chmod +x check_desktop.sh`), and run it.

This will show us all the paths rofi might be looking at. Could you also confirm:
1. How many Obsidian entries do you see in rofi?
2. Are they identical or different in any way?

---

**Human** - 2024-11-14 20:51:33 UTC

~  find /var/lib/flatpak -name "*obsidian*.desktop" -type f -ls
  3053744      4 -rwxr-xr-x   1 root     root          370 Nov 12 16:15 /var/lib/flatpak/app/md.obsidian.Obsidian/x86_64/stable/d3b0657c21559553152f8be3dbe3fc08bf102c636fd77566280c1f1a9af63fc0/export/share/applications/md.obsidian.Obsidian.desktop

---

**Human** - 2024-11-14 20:52:05 UTC

how about we just clear everything to start with a clean slate?

---

**Assistant** - 2024-11-14 20:52:05 UTC

 Good thinking - let's do a clean sweep:

```bash
# Remove any potential desktop entry caches
rm -rf ~/.cache/rofi* 2>/dev/null
rm -rf ~/.local/share/applications/obsidian* 2>/dev/null

# Update desktop database
sudo update-desktop-database

# For Flatpak specifically
flatpak uninstall --delete-data md.obsidian.Obsidian
flatpak install flathub md.obsidian.Obsidian
```

This will:
1. Clear rofi caches
2. Remove any local desktop entries
3. Completely remove Obsidian including its data
4. Do a fresh install

After this, rofi should only see the single clean Flatpak desktop entry. Want to give that a try?

---

**Human** - 2024-11-14 20:53:04 UTC

~  flatpak uninstall --delete-data md.obsidian.Obsidian
     flatpak install flathub md.obsidian.Obsidian
        ID                                  Branch         Op
 1.     md.obsidian.Obsidian                stable         r
 2.     md.obsidian.Obsidian.Locale         stable         r
Proceed with these changes to the system installation? [Y/n]:

---

**Assistant** - 2024-11-14 20:53:04 UTC

 Yes, proceed with `Y`. This will give us a completely fresh installation of Obsidian, which should resolve the duplicate desktop entries issue. The system will remove both the main application and its locale files, then reinstall them cleanly.

After it's done, try launching rofi and search for Obsidian. You should only see one entry now. Let me know if you still see duplicates.

---

