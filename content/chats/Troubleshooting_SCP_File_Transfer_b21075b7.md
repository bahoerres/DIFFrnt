---
created: 2024-12-08T11:55
updated: 2024-12-08T11:55
---
# Troubleshooting SCP File Transfer

Created: 2024-11-30 00:35:46 UTC
Updated: 2024-11-30 00:37:59 UTC
UUID: b21075b7-42b4-4eb5-92f0-6bfd8fff06db
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-30 00:35:52 UTC

i'm confused.. 

 ~  scp blake@192.168.20.13:~/.tmux.conf ~/
scp: open local "/home/blake/.tmux.conf": No such file or directory

---

**Assistant** - 2024-11-30 00:35:52 UTC

 Let me help explain what's happening with your SCP command. The error occurs because you're trying to copy a .tmux.conf file from the remote server to your local machine, but there's no existing .tmux.conf file in your local home directory to write to.

However, this isn't actually a problem - SCP will create the file for you. The error message is a bit misleading. You can safely ignore it and proceed with the command. The file will be copied successfully from the remote server to your local machine.

If you want to verify the file was copied correctly, you can check your local home directory after running the command:

```bash
ls -la ~/.tmux.conf
```

Would you like to verify if the file transfer worked, or do you need help troubleshooting further?

---

**Human** - 2024-11-30 00:37:59 UTC

different issue on that one. bad symlink.

---

**Assistant** - 2024-11-30 00:37:59 UTC

 Ah, I see - a bad symlink would indeed cause that issue. If the .tmux.conf on the remote system is a broken symbolic link, that would explain the copy failure. You might want to check where that symlink is pointing on the remote system with:

```bash
ls -la ~/.tmux.conf
```

on the remote machine to see what's going on with the symlink target.

---

