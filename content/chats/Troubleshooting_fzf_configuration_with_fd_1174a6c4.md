---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Troubleshooting fzf configuration with fd

Created: 2024-11-08 23:13:45 UTC
Updated: 2024-11-08 23:42:36 UTC
UUID: 1174a6c4-e12a-4bec-bad8-4863e5ddc07a
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-08 23:13:51 UTC

my fzf config contains this line : 

set -gx FZF_DEFAULT_COMMAND 'fd --type f --hidden --follow'

but when i call just fzf i get my normal display/popup but it says that command failed. 

let's fix it. what is that trying to do in the first place? and we can go from there.

---

**Assistant** - 2024-11-08 23:13:51 UTC

 Let me help you understand and fix this configuration.

That line is trying to set up a default command for fzf (fuzzy finder) to use when searching for files. Let's break down what it's trying to do:

1. `set -gx FZF_DEFAULT_COMMAND` - This sets a global environment variable that fzf uses
2. `fd --type f --hidden --follow` - This is using the `fd` command (a modern alternative to `find`) with options:
   - `--type f`: Only show files (not directories)
   - `--hidden`: Include hidden files
   - `--follow`: Follow symbolic links

The error you're getting likely means either:
1. `fd` is not installed on your system, or
2. It's installed under a different name (some systems call it `fdfind`)

Let's verify first - can you try running `which fd` or `fd --version` in your terminal and let me know what you get?

---

**Human** - 2024-11-08 23:14:34 UTC

so i could likely just install fd (i would image paru -S fd  ?) and it should work just fine?

---

**Assistant** - 2024-11-08 23:14:34 UTC

 Yes, exactly! Since you're on Arch Linux (given the `paru` reference), you can install `fd` with:

```bash
paru -S fd
```

or if you prefer using pacman directly:

```bash
sudo pacman -S fd
```

After installing fd, your existing fzf configuration should work as intended. The command will then:
1. Find files recursively from your current directory
2. Include hidden files (like .config files)
3. Follow symbolic links
4. Pass all these results to fzf for fuzzy finding

Give it a try after installing fd and let me know if you run into any other issues!

---

**Human** - 2024-11-08 23:20:19 UTC

how do i elevate but remain in the user's environment in order to run neovim with my user's configs, but privileges to write in /etc/

---

**Assistant** - 2024-11-08 23:20:19 UTC

 To run neovim with your user's configs but with root privileges, you should use `sudo -E` where the `-E` flag preserves the environment variables. However, to specifically maintain your neovim config, the best command would be:

```bash
sudoedit file_in_etc
```

OR if you really need to use nvim specifically:

```bash
sudo -E nvim file_in_etc
```

The reason `sudoedit` is generally preferred is that it's specifically designed for this use case and is more secure - it creates a temporary copy of the file, lets you edit it with your normal user's editor configuration, then copies it back with proper permissions when you save and quit.

If you want to make `sudoedit` always use neovim, you can set the EDITOR environment variable:
```bash
export EDITOR=nvim
```

You can put this in your .bashrc or .zshrc to make it permanent.

---

**Human** - 2024-11-08 23:25:30 UTC

and now, refresh my memory on scp

can i copy back to my host from inside the ssh session? or should i exit and use scp from my host (the recipient) device?

---

**Assistant** - 2024-11-08 23:25:30 UTC

 You can do it either way! Here's both approaches:

From inside the SSH session (pushing to your local machine):
```bash
scp file_to_send user@local_ip:/path/to/destination
```

From your local machine (pulling from remote):
```bash
scp user@remote_ip:/path/to/source/file /local/destination
```

Key points to remember about scp:
- Basic syntax is: `scp source destination`
- For remote locations, use: `user@hostname:/path`
- Use `-r` flag for directories
- Port can be specified with `-P port_number` if not using default 22

Most people find it clearer to exit and pull from their local machine, as you:
1. Have better tab completion for your local paths
2. Don't have to remember your local machine's IP
3. Don't have to worry about firewalls blocking incoming connections

If you share what you're trying to copy I can give you the exact command to use!

---

**Human** - 2024-11-08 23:28:03 UTC

and if it's a folder? so ~/Documents/chat-vault blake@192.168.20.13 if i'm in a ssh session on blake@192.168.0.63 ? (i'm using the 20.13 laptop to retreive a file from the 0.63 desktop)

---

**Assistant** - 2024-11-08 23:28:03 UTC

 Since you're copying a folder, you'll need the `-r` flag (recursive). From your SSH session on the 0.63 desktop, you'd use:

```bash
scp -r ~/Documents/chat-vault blake@192.168.20.13:~/
```

This will copy the entire chat-vault folder to your home directory on the 20.13 laptop.

OR, if you prefer (and probably easier), exit the SSH session and from your 20.13 laptop run:

```bash
scp -r blake@192.168.0.63:~/Documents/chat-vault ~/
```

The second approach is usually cleaner since you're pulling from your receiving machine. The destination path (`~/`) can be changed to wherever you want the folder to land on your laptop.

If you want to preserve timestamps and permissions, you can add the `-p` flag:
```bash
scp -rp blake@192.168.0.63:~/Documents/chat-vault ~/
```

---

**Assistant** - 2024-11-08 23:42:36 UTC

 Obsidian itself doesn't have a CLI - it's primarily an Electron app without command line capabilities. However, what you're trying to do can be approached in a few ways:

1. If you're using Obsidian Sync (the paid service):
   - Unfortunately there's no CLI way to force a sync - it needs the GUI app

2. If you're using a git-based sync solution:
   - You could trigger a git push from the command line
   - This assumes you've set up your vault with git sync

3. If you're using any folder sync solution (like Syncthing):
   - The sync should happen automatically when files change
   - Some sync solutions have CLI commands to force sync

4. If you're using iCloud/Dropbox/etc:
   - These typically don't have reliable CLI force-sync options

Without knowing your sync setup, I can't give you the exact solution, but if you let me know how you normally sync your vault, I can provide more specific guidance!

---

**Human** - 2024-11-08 23:42:36 UTC

oh, now let's get weird, huh.. does obsidian have cli? i just copied some items into my obsidian vault on  my desktop (remote) and while i don't have remote desktop capabilites set up, id like to be able to try and force sync i suppose, "from that device"

---

