---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting Segmentation Fault in font-manager on Arch Linux

Created: 2024-11-04 22:43:33 UTC
Updated: 2024-11-04 22:59:29 UTC
UUID: b0bb244a-0389-4c70-bf0b-bc4f25fc52bb
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-04 22:43:40 UTC

font-manager 
fish: Job 1, 'font-manager' terminated by signal SIGSEGV (Address boundary error)

any idea what might be causing this? 

up to date system, arch linux, hyprland, kitty and fish as terminal.

---

**Assistant** - 2024-11-04 22:43:40 UTC

 This SIGSEGV (Segmentation Fault) error with font-manager typically occurs due to memory access issues. On Arch Linux, there are a few common causes and potential solutions:

1. First, try clearing your font cache:
```bash
rm -rf ~/.cache/fontconfig
fc-cache -f -v
```

2. Check if you have all the required dependencies:
```bash
sudo pacman -S --needed gtk3 webkit2gtk libxml2 libsoup json-glib
```

3. If you're using the AUR version, try rebuilding it:
```bash
yay -S --rebuild font-manager
# or
paru -S --rebuild font-manager
```

4. The issue might also be related to Hyprland's handling of GTK applications. You could try:
   - Ensuring you have `xdg-desktop-portal-hyprland` installed
   - Setting the appropriate environment variables in your Hyprland config:
```bash
env = GDK_BACKEND=wayland
env = GTK_THEME=your-theme-name
```

If none of these work, you could try:
1. Running it from a different terminal to rule out kitty-specific issues
2. Using the flatpak version instead: `flatpak install flathub org.gnome.FontManager`

Would you like me to help you debug this further with any of these approaches?

---

**Human** - 2024-11-04 22:45:09 UTC

rm -rf ~/.cache/fontconfig
     fc-cache -f -v
Font directories:
	/home/blake/.local/share/fonts
	/home/blake/.local/share/flatpak/exports/share/fonts
	/var/lib/flatpak/exports/share/fonts
	/usr/local/share/fonts
	/usr/share/fonts
	/var/lib/snapd/desktop/fonts
	/home/blake/.fonts
	/usr/share/fonts/OTF
	/usr/share/fonts/TTF
	/usr/share/fonts/adobe-source-code-pro
	/usr/share/fonts/cantarell
	/usr/share/fonts/encodings
	/usr/share/fonts/gnu-free
	/usr/share/fonts/inter
	/usr/share/fonts/liberation
	/usr/share/fonts/misc
	/usr/share/fonts/noto
	/usr/share/fonts/noto-cjk
	/home/blake/.fonts/FontBase
	/usr/share/fonts/encodings/large
/home/blake/.local/share/fonts: skipping, no such directory
/home/blake/.local/share/flatpak/exports/share/fonts: skipping, no such directory
/var/lib/flatpak/exports/share/fonts: skipping, no such directory
/usr/local/share/fonts: skipping, no such directory
/usr/share/fonts: caching, new cache contents: 0 fonts, 11 dirs
/usr/share/fonts/OTF: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/TTF: caching, new cache contents: 1003 fonts, 0 dirs
/usr/share/fonts/adobe-source-code-pro: caching, new cache contents: 30 fonts, 0 dirs
/usr/share/fonts/cantarell: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/gnu-free: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/inter: caching, new cache contents: 56 fonts, 0 dirs
/usr/share/fonts/liberation: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/misc: caching, new cache contents: 36 fonts, 0 dirs
/usr/share/fonts/noto: caching, new cache contents: 613 fonts, 0 dirs
/usr/share/fonts/noto-cjk: caching, new cache contents: 80 fonts, 0 dirs
/var/lib/snapd/desktop/fonts: skipping, no such directory
/home/blake/.fonts: caching, new cache contents: 0 fonts, 1 dirs
/home/blake/.fonts/FontBase: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/OTF: skipping, looped directory detected
/usr/share/fonts/TTF: skipping, looped directory detected
/usr/share/fonts/adobe-source-code-pro: skipping, looped directory detected
/usr/share/fonts/cantarell: skipping, looped directory detected
/usr/share/fonts/encodings: skipping, looped directory detected
/usr/share/fonts/gnu-free: skipping, looped directory detected
/usr/share/fonts/inter: skipping, looped directory detected
/usr/share/fonts/liberation: skipping, looped directory detected
/usr/share/fonts/misc: skipping, looped directory detected
/usr/share/fonts/noto: skipping, looped directory detected
/usr/share/fonts/noto-cjk: skipping, looped directory detected
/home/blake/.fonts/FontBase: skipping, looped directory detected
/usr/share/fonts/encodings/large: skipping, looped directory detected
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/blake/.cache/fontconfig: cleaning cache directory
/home/blake/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded
 ~ 

---

**Assistant** - 2024-11-04 22:45:09 UTC

 Based on the output, the font cache was successfully rebuilt, but there are a few potential issues to note:

1. Several font directories are listed but don't exist:
   ```
   /home/blake/.local/share/fonts: skipping, no such directory
   /home/blake/.local/share/flatpak/exports/share/fonts: skipping, no such directory
   /var/lib/flatpak/exports/share/fonts: skipping, no such directory
   /usr/local/share/fonts: skipping, no such directory
   ```

2. The warning about "looped directory detected" isn't usually harmful but indicates some potential filesystem configuration issues.

Let's try launching font-manager again to see if clearing the cache fixed the issue. If it still crashes, let's verify your package dependencies:

```bash
pacman -Q gtk3 webkit2gtk libxml2 libsoup json-glib
```

Also, which version of font-manager are you using? You can check with:
```bash
pacman -Q font-manager
```

This will help us determine if this might be a version-specific issue or if we need to try other approaches.

---

**Human** - 2024-11-04 22:46:16 UTC

pacman -Q gtk3 webkit2gtk libxml2 libsoup json-glib
gtk3 1:3.24.43-4
error: package 'webkit2gtk' was not found
libxml2 2.13.4-1
error: package 'libsoup' was not found
json-glib 1.10.0-1

---

**Assistant** - 2024-11-04 22:46:16 UTC

 Ah, there's the likely issue - you're missing some required dependencies. The package names have changed in recent Arch updates:

1. `webkit2gtk` is now `webkit2gtk-4.1`
2. `libsoup` is now `libsoup3`

Let's install the missing dependencies:

```bash
sudo pacman -S webkit2gtk-4.1 libsoup3
```

After installing these dependencies, try running font-manager again. These libraries are crucial for font-manager's GUI functionality, and their absence could definitely cause a segmentation fault.

If it still crashes after installing these dependencies, let me know and we can try other troubleshooting steps.

---

**Assistant** - 2024-11-04 22:48:43 UTC

 Let's try a few more troubleshooting steps:

1. First, let's try running font-manager from the terminal with debug output:
```bash
font-manager --debug
```

2. We can also try checking if there are any relevant errors in your system logs:
```bash
journalctl -b | grep font-manager
```

3. Since you're using Hyprland, let's verify your portal settings. Check if you have these packages installed:
```bash
pacman -Q xdg-desktop-portal-hyprland xdg-desktop-portal-gtk
```

4. Another option would be to try the Flatpak version to see if it's a packaging issue:
```bash
flatpak install flathub org.gnome.FontManager
```

Could you try the debug command and share any output before the crash? This would help pinpoint exactly where it's failing.

Also, what version of font-manager are you running? 
```bash
pacman -Q font-manager
```

---

**Human** - 2024-11-04 22:48:43 UTC

rebuilt, and still crashing

---

**Human** - 2024-11-04 22:50:43 UTC




Attachments:
- {'file_name': 'paste.txt', 'file_size': 11172, 'file_type': 'txt', 'extracted_content': "\n ~ \ue0b0 font-manager --debug\n\nFont Manager 0.9.0\n\n(process:117633): [font-manager]-DEBUG: 16:48:50.770: Fontconfig version : 21500\n(process:117633): [font-manager]-DEBUG: 16:48:50.771: Freetype version (compile-time) : 2.13.3\n(process:117633): [font-manager]-DEBUG: 16:48:50.771: Freetype version (run-time) : 2.13.3\n(process:117633): [font-manager]-DEBUG: 16:48:50.771: Harfbuzz version (compile-time) : 9.0.0\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: Harfbuzz version (run-time) : 10.0.1\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: JSON-GLib version : 1.10.1\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: Pango version (compile-time) : 1.54.0\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: Pango version (run-time) : 15400\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: libxml2 version : 21303\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: SQLite version (compile-time) : 3.46.1\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: SQLite version (run-time) : 3.46.1\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: GLib version (compile-time\n) : 2.80.5\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: GLib version (run-time) : 2.82.2\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: GTK version (compile-time) : 4.14.5\n(process:117633): [font-manager]-DEBUG: 16:48:50.772: GTK version (run-time) : 4.16.5\n(font-manager:117633): [font-manager]-DEBUG: 16:48:50.811: Using schema with id com.github.FontManager.FontManager from default source\n(font-manager:117633): [font-manager]-DEBUG: 16:48:50.833: Adding icons from resource path : /com/github/FontManager/FontManager/icons/\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.177: Loading custom css from resource path : /com/github/FontManager/FontManager/ui/FontManager.css\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.790: Database version is current, skipping initialization\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.871: Database version is current, skipping initialization\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.883: Database version is current, skipping initialization\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.887: Restoring state : Window size : 950 x 700\n(font-manager:117633): [font-manager]-DEBUG: 16:48:51.887: Restoring state : Window is maximized : FALSE\nfish: Job 1, 'font-manager --debug' terminated by signal SIGSEGV (Address boundary error)\n\n ~ \ue0b0 journalctl -b | grep font-manager\nNov 04 10:40:59 zen-arch kernel: font-manager[1716]: segfault at 0 ip 00007e9499e51c10 sp 00007fffe98d3d30 error 4 in libfontconfig.so.1.14.0[29c10,7e9499e30000+2d000] likely on CPU 2 (core 1, socket 0)\nNov 04 10:40:59 zen-arch systemd-coredump[1769]: Process 1716 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 10:41:00 zen-arch systemd-coredump[1774]: Process 1716 (font-manager) of user 1000 dumped core.\n                                                 #2  0x000055923157a6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                 #3  0x000055923157a9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                 #4  0x0000559231533402 font_manager_application_reload (font-manager + 0x2f402)\n                                                 #5  0x00005592315334dd n/a (font-manager + 0x2f4dd)\n                                                 #10 0x000055923152a35f main (font-manager + 0x2635f)\n                                                 #13 0x000055923152a3f5 _start (font-manager + 0x263f5)\nNov 04 16:25:53 zen-arch kernel: font-manager[52966]: segfault at 0 ip 00007f1fc12e8c10 sp 00007ffe3f5ba820 error 4 in libfontconfig.so.1.14.0[29c10,7f1fc12c7000+2d000] likely on CPU 5 (core 2, socket 0)\nNov 04 16:25:53 zen-arch systemd-coredump[53005]: Process 52966 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:25:54 zen-arch systemd-coredump[53006]: Process 52966 (font-manager) of user 1000 dumped core.\n                                                  #2  0x0000557107cdd6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                  #3  0x0000557107cdd9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                  #4  0x0000557107c96402 font_manager_application_reload (font-manager + 0x2f402)\n                                                  #5  0x0000557107c964dd n/a (font-manager + 0x2f4dd)\n                                                  #10 0x0000557107c8d35f main (font-manager + 0x2635f)\n                                                  #13 0x0000557107c8d3f5 _start (font-manager + 0x263f5)\nNov 04 16:42:19 zen-arch kernel: font-manager[113793]: segfault at 0 ip 000071ea7e4e8c10 sp 00007ffc33051d30 error 4 in libfontconfig.so.1.14.0[29c10,71ea7e4c7000+2d000] likely on CPU 2 (core 1, socket 0)\nNov 04 16:42:19 zen-arch systemd-coredump[113833]: Process 113793 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:42:20 zen-arch systemd-coredump[113834]: Process 113793 (font-manager) of user 1000 dumped core.\n                                                   #2  0x00005c4df117e6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                   #3  0x00005c4df117e9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                   #4  0x00005c4df1137402 font_manager_application_reload (font-manager + 0x2f402)\n                                                   #5  0x00005c4df11374dd n/a (font-manager + 0x2f4dd)\n                                                   #10 0x00005c4df112e35f main (font-manager + 0x2635f)\n                                                   #13 0x00005c4df112e3f5 _start (font-manager + 0x263f5)\nNov 04 16:45:39 zen-arch kernel: font-manager[115736]: segfault at 0 ip 00007327e6c50c10 sp 00007ffef7b1c690 error 4 in libfontconfig.so.1.14.0[29c10,7327e6c2f000+2d000] likely on CPU 11 (core 5, socket 0)\nNov 04 16:45:39 zen-arch systemd-coredump[115770]: Process 115736 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:45:40 zen-arch systemd-coredump[115771]: Process 115736 (font-manager) of user 1000 dumped core.\n                                                   #2  0x000063f2c7b7e6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                   #3  0x000063f2c7b7e9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                   #4  0x000063f2c7b37402 font_manager_application_reload (font-manager + 0x2f402)\n                                                   #5  0x000063f2c7b374dd n/a (font-manager + 0x2f4dd)\n                                                   #10 0x000063f2c7b2e35f main (font-manager + 0x2635f)\n                                                   #13 0x000063f2c7b2e3f5 _start (font-manager + 0x263f5)\nNov 04 16:46:59 zen-arch kernel: font-manager[116457]: segfault at 0 ip 000072cb81d7ec10 sp 00007fff373bcbe0 error 4 in libfontconfig.so.1.14.0[29c10,72cb81d5d000+2d000] likely on CPU 2 (core 1, socket 0)\nNov 04 16:46:59 zen-arch systemd-coredump[116515]: Process 116457 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:46:59 zen-arch systemd-coredump[116516]: Process 116457 (font-manager) of user 1000 dumped core.\n                                                   #2  0x00005b11291226b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                   #3  0x00005b11291229d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                   #4  0x00005b11290db402 font_manager_application_reload (font-manager + 0x2f402)\n                                                   #5  0x00005b11290db4dd n/a (font-manager + 0x2f4dd)\n                                                   #10 0x00005b11290d235f main (font-manager + 0x2635f)\n                                                   #13 0x00005b11290d23f5 _start (font-manager + 0x263f5)\nNov 04 16:47:51 zen-arch sudo[116989]:    blake : TTY=pts/3 ; PWD=/home/blake ; USER=root ; COMMAND=/usr/bin/pacman -S --config /etc/pacman.conf -- extra/font-manager\nNov 04 16:47:54 zen-arch sudo[117042]:    blake : TTY=pts/3 ; PWD=/home/blake ; USER=root ; COMMAND=/usr/bin/pacman -D -q --asexplicit --config /etc/pacman.conf -- font-manager\nNov 04 16:48:05 zen-arch kernel: font-manager[117135]: segfault at 0 ip 0000768caa651c10 sp 00007fffdabc3b60 error 4 in libfontconfig.so.1.14.0[29c10,768caa630000+2d000] likely on CPU 2 (core 1, socket 0)\nNov 04 16:48:05 zen-arch systemd-coredump[117172]: Process 117135 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:48:05 zen-arch systemd-coredump[117173]: Process 117135 (font-manager) of user 1000 dumped core.\n                                                   #2  0x00005895b638d6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                   #3  0x00005895b638d9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                   #4  0x00005895b6346402 font_manager_application_reload (font-manager + 0x2f402)\n                                                   #5  0x00005895b63464dd n/a (font-manager + 0x2f4dd)\n                                                   #10 0x00005895b633d35f main (font-manager + 0x2635f)\n                                                   #13 0x00005895b633d3f5 _start (font-manager + 0x263f5)\nNov 04 16:48:52 zen-arch kernel: font-manager[117633]: segfault at 0 ip 0000791be6c27c10 sp 00007ffd0f6e3a20 error 4 in libfontconfig.so.1.14.0[29c10,791be6c06000+2d000] likely on CPU 2 (core 1, socket 0)\nNov 04 16:48:52 zen-arch systemd-coredump[117662]: Process 117633 (font-manager) of user 1000 terminated abnormally with signal 11/SEGV, processing...\nNov 04 16:48:53 zen-arch systemd-coredump[117663]: Process 117633 (font-manager) of user 1000 dumped core.\n                                                   #2  0x000061c6962ef6b7 font_manager_load_user_font_resources (font-manager + 0x766b7)\n                                                   #3  0x000061c6962ef9d9 font_manager_get_sorted_font_list (font-manager + 0x769d9)\n                                                   #4  0x000061c6962a8402 font_manager_application_reload (font-manager + 0x2f402)\n                                                   #5  0x000061c6962a84dd n/a (font-manager + 0x2f4dd)\n                                                   #10 0x000061c69629f35f main (font-manager + 0x2635f)\n                                                   #13 0x000061c69629f3f5 _start (font-manager + 0x263f5)\n\n ~ \ue0b0 pacman -Q xdg-desktop-portal-hyprland xdg-desktop-portal-gtk\nxdg-desktop-portal-hyprland 1.3.8-1\nxdg-desktop-portal-gtk 1.15.1-2\n\n ~ \ue0b0 "}
- paste.txt

---

**Assistant** - 2024-11-04 22:50:43 UTC

 From the logs and debug output, we can see that the crash consistently occurs in `font_manager_load_user_font_resources` when trying to load the font list. This appears to be a fontconfig-related crash, possibly due to some corrupt font files or font cache issues.

Let's try a more thorough approach:

1. First, backup and remove your existing font configuration:
```bash
mv ~/.config/fontconfig ~/.config/fontconfig.bak
```

2. Check for and remove any broken symlinks in your font directories:
```bash
find ~/.fonts /usr/share/fonts -xtype l
```

3. Rebuild fontconfig completely:
```bash
sudo rm -rf /var/cache/fontconfig/*
sudo fc-cache -rfsv
```

4. Since you're using Hyprland, let's also make sure your environment variables are set correctly. Add these to your Hyprland config if they're not already there:
```bash
env = GDK_BACKEND,wayland
env = GTK_USE_PORTAL,1
env = XDG_CURRENT_DESKTOP,Hyprland
env = XDG_SESSION_DESKTOP,Hyprland
```

5. As a last resort, we could try the Flatpak version which might avoid these system-level font issues:
```bash
flatpak install flathub org.gnome.FontManager
```

Let me know if you want to try any of these approaches, and we can work through them step by step.

Also, what's the output of:
```bash
pacman -Q fontconfig
```

---

**Assistant** - 2024-11-04 22:53:42 UTC

 Looking at the version and previous logs, this might be related to a known issue with font-manager 0.9.0 and newer versions of fontconfig on GTK4. Let's try the flatpak version which might have better compatibility:

```bash
flatpak install flathub org.gnome.FontManager
```

After installation, you can run it with:
```bash
flatpak run org.gnome.FontManager
```

If you prefer not to use flatpak, there's also an older version (0.8.8) in the AUR that uses GTK3 and might be more stable:
```bash
yay -S font-manager-gtk3
# or
paru -S font-manager-gtk3
```

Would you like to try either of these alternatives? The flatpak version would be the safest bet since it runs in its own container with its own dependencies.

---

**Human** - 2024-11-04 22:53:42 UTC

pacman -Q font-manager 
font-manager 0.9.0-2

---

**Human** - 2024-11-04 22:54:44 UTC

and apologies, this is what you actually asked for (multiple times..)

~  pacman -Q fontconfig
fontconfig 2:2.15.0-2

---

**Assistant** - 2024-11-04 22:54:44 UTC

 Thanks for providing that. With fontconfig 2.15.0 and font-manager 0.9.0, this is likely a version mismatch issue that's causing the segfault. Font-manager 0.9.0 appears to have some compatibility issues with newer versions of fontconfig, particularly on Wayland/Hyprland setups.

Let's try the Flatpak version first since it will come with its own controlled environment and dependencies:

```bash
flatpak install flathub org.gnome.FontManager
flatpak run org.gnome.FontManager
```

If you want to stick with the native package, we can try downgrading fontconfig to an earlier version:
```bash
sudo pacman -U /var/cache/pacman/pkg/fontconfig-2.14.2-1-x86_64.pkg.tar.zst
```

(If the package isn't in your cache, we can find an alternative approach.)

Which approach would you prefer to try first?

---

**Human** - 2024-11-04 22:56:07 UTC

if installing flatpak i can remove font-manager? fontconfig too? or is that still a dependency?

---

**Assistant** - 2024-11-04 22:56:07 UTC

 Don't remove fontconfig - it's a critical system dependency that many other applications rely on. It's used by virtually all GUI applications for font rendering.

You can safely remove the native font-manager package though:

```bash
sudo pacman -R font-manager
```

Then proceed with the Flatpak installation:
```bash
flatpak install flathub org.gnome.FontManager
```

The Flatpak version will use its own contained version of dependencies while running, but won't interfere with your system's fontconfig installation, which needs to stay in place for other applications to work properly.

---

**Human** - 2024-11-04 22:57:08 UTC

oh my.. could this have been the issue all along? this is the end of the flatpak install:

Installation complete.
bwrap: Can't find source path /home/blake/.local/share/fonts: No such file or directory

---

**Assistant** - 2024-11-04 22:57:08 UTC

 Ah, that warning suggests your ~/.local/share/fonts directory doesn't exist, which matches what we saw earlier in the fc-cache output. While this warning itself isn't breaking the Flatpak installation, creating this directory might help with font management in general:

```bash
mkdir -p ~/.local/share/fonts
```

This is actually a standard location for user-installed fonts in Linux, and its absence might have been contributing to the crashes in the native font-manager package.

Try creating the directory and then running the Flatpak version:
```bash
flatpak run org.gnome.FontManager
```

If this works, it suggests the original crashes might have been related to font-manager trying to access a non-existent directory. This is actually a bug in the native package - it should handle missing directories more gracefully rather than segfaulting.

---

**Human** - 2024-11-04 22:59:29 UTC

7 Oct 01:35  dolphin
drwx------    - blake 25 Oct 18:40  firenvim
drwx------    - blake  4 Nov 16:38  fish
drwxr-xr-x    - blake  7 Sep 19:05  flatpak
drwxr-xr-x    - blake  9 Sep 23:41  font-manager
lrwxrwxrwx    - blake  2 Nov 19:30  fonts -> ../../dotfiles/fonts/.local/share/fonts
drwxr-xr-x    - blake  1 Nov 18:10  fonts.bak
drwxr-xr-x    - blake 24 Oct 19:24  gem
drwxr-xr-x    - blake  6 Sep 15:33  gnome-settings-daemon
drwx------    - blake  4 Nov 16:28  gvfs-metadata
drwxr-xr-x    - blake 26 Oct 13:30  icc
lrwxrwxrwx    - blake  2 Nov 19:30  icons -> ../../dotfiles/icons/.local/share/icons
drwxr-xr-x    - blake 18 Sep 17:59  icons.bak
drwxr-xr-x    - blake 27 Oct 10:14  inxi
drwx------    - blake  8 Sep 19:48  iwctl

that's something..

---

**Assistant** - 2024-11-04 22:59:29 UTC

 Ah yes - there's the issue! You have a symlink for your fonts directory pointing to `../../dotfiles/fonts/.local/share/fonts`. If that target directory doesn't exist or isn't properly set up, it would cause the exact kind of segfault we're seeing.

Let's check a few things:

1. Verify if the target directory exists:
```bash
ls -la ~/dotfiles/fonts/.local/share/fonts
```

2. If it doesn't exist, you'll need to either:
   a. Create the target directory:
   ```bash
   mkdir -p ~/dotfiles/fonts/.local/share/fonts
   ```
   OR
   b. Remove the symlink and create a regular directory:
   ```bash
   rm ~/.local/share/fonts
   mkdir ~/.local/share/fonts
   ```

This symlink setup is likely what was causing font-manager to crash - it was following the symlink but finding nothing at the destination, leading to the segfault. fontconfig and font-manager should handle missing directories more gracefully, but they don't always do so.

---

