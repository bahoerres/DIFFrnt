---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting GTK Theme Parsing Errors

Created: 2024-08-31 15:55:50 UTC
Updated: 2024-08-31 15:55:58 UTC
UUID: 8e4e6abb-c95f-4206-8510-f5e4c0a854dc
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Assistant** - 2024-08-31 15:55:56 UTC

 These error messages indicate there are some issues with parsing GTK themes in your application. Let's break down the main points:

1. Theme parsing errors: Both gtk.css and gtk-dark.css files have issues on line 6616, column 68.

2. Invalid pseudo-class: The error suggests there's an attempt to use an invalid pseudo-class named 'glib warning'.

3. File location: The errors are being reported from the file /home/runner/work/desktop/desktop/engine/toolkit/xre/nsSigHandlers.cpp on line 187.

4. Process information: The errors are coming from a process named "zen-alpha" with PID 174047.

To address these issues, you could:

1. Check the GTK theme files (gtk.css and gtk-dark.css) around line 6616. There might be a syntax error or an invalid pseudo-class being used.

2. Ensure that your GTK version is compatible with the theme you're using.

3. Verify if there have been any recent changes to the theme files that might have introduced these errors.

4. Consider updating or reinstalling your GTK libraries and themes if the issue persists.

Would you like me to provide more detailed steps on how to investigate or resolve these theme parsing errors?

---

**Human** - 2024-08-31 15:55:56 UTC

[174047, Main Thread] WARNING: Theme parsing error: gtk-dark.css:6616:68: Invalid name of pseudo-class: 'glib warning', file /home/runner/work/desktop/desktop/engine/toolkit/xre/nsSigHandlers.cpp:187
(zen-alpha:174047): Gtk-WARNING **: 10:54:19.053: Theme parsing error: gtk-dark.css:6616:68: Invalid name of pseudo-class
[Parent 174047, Main Thread] WARNING: Theme parsing error: gtk.css:6616:68: Invalid name of pseudo-class: 'glib warning', file /home/runner/work/desktop/desktop/engine/toolkit/xre/nsSigHandlers.cpp:187
(zen-alpha:174047): Gtk-WARNING **: 10:54:19.228: Theme parsing error: gtk.css:6616:68: Invalid name of pseudo-class
[Parent 174047, Main Thread] WARNING: Theme parsing error: gtk.css:6616:68: Invalid name of pseudo-class: 'glib warning', file /home/runner/work/desktop/desktop/engine/toolkit/xre/nsSigHandlers.cpp:187
(zen-alpha:174047): Gtk-WARNING **: 10:54:19.322: Theme parsing error: gtk.css:6616:68: Invalid name of pseudo-class
[Parent 174047, Main Thread] WARNING: Theme parsing error: gtk-dark.css:6616:68: Invalid name of pseudo-class: 'glib warning', file /home/runner/work/desktop/desktop/engine/toolkit/xre/nsSigHandlers.cpp:187
(zen-alpha:174047): Gtk-WARNING **: 10:54:19.365: Theme parsing error: gtk-dark.css:6616:68: Invalid name of pseudo-class


need some help making sense of this mess

---

