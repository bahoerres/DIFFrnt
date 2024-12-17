---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Changing Symlink to Different Home Directory

Created: 2024-08-11 21:45:44 UTC
Updated: 2024-08-11 22:08:01 UTC
UUID: 3984d689-e69c-44a2-a80a-f04b82ae4968
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-08-11 21:45:55 UTC

rwxrwxrwx 1 blake blake  37 Aug 11 15:55 config -> /home/nick/.cache/wal/colors-swaylock

how do i change the symlink here to /home/blake?

---

**Assistant** - 2024-08-11 21:45:55 UTC

 To change the symlink to point to `/home/blake` instead of `/home/nick`, you can use the `ln` command with the `-sf` options. Here's how you can do it:

1. First, remove the existing symlink:
   ```
   rm config
   ```

2. Then create a new symlink pointing to the desired location:
   ```
   ln -sf /home/blake/.cache/wal/colors-swaylock config
   ```

The `-s` option creates a symbolic link, and the `-f` option forces the creation of the link, overwriting the destination if it already exists.

After running these commands, the symlink should now point to `/home/blake/.cache/wal/colors-swaylock`.

You can verify the change by running `ls -l` again. The output should look similar to:

```
rwxrwxrwx 1 blake blake  37 Aug 11 [current_time] config -> /home/blake/.cache/wal/colors-swaylock
```

Make sure you have the necessary permissions to modify the symlink and that the target file exists in the new location.

Would you like me to explain any part of this process in more detail?

---

**Human** - 2024-08-11 22:08:01 UTC

this is part of the theme i'm setting up.. can you give me a hand translating this? haha 

Symlink the updates.timer and updates.service files from waybar/modules/updates/ into ~/.config/systemd/user

---

**Assistant** - 2024-08-11 22:08:01 UTC

 Certainly! I'd be happy to help you translate that instruction into the actual commands you need to run. Let's break it down step by step:

1. First, we need to create the target directory if it doesn't already exist:

```bash
mkdir -p ~/.config/systemd/user
```

2. Now, we'll create the symlinks. We'll assume that the source files are in a directory called `waybar/modules/updates/` in your current working directory. If they're somewhere else, you'll need to adjust the paths accordingly.

```bash
ln -sf $(pwd)/waybar/modules/updates/updates.timer ~/.config/systemd/user/updates.timer
ln -sf $(pwd)/waybar/modules/updates/updates.service ~/.config/systemd/user/updates.service
```

Here's what these commands do:

- `ln -sf`: This creates a symbolic link (`-s`) and forces it to overwrite any existing file (`-f`).
- `$(pwd)`: This expands to your current working directory.
- The rest of the path (`waybar/modules/updates/updates.timer`) is the relative path to the source file.
- `~/.config/systemd/user/updates.timer` is the destination path for the symlink.

After running these commands, you should have two new symlinks in your `~/.config/systemd/user/` directory, pointing to the `updates.timer` and `updates.service` files in your waybar modules directory.

You can verify that the symlinks were created correctly by running:

```bash
ls -l ~/.config/systemd/user/updates.*
```

This should show you the two symlinks and where they point to.

Is there anything else about this process you'd like me to explain or help with?

---

