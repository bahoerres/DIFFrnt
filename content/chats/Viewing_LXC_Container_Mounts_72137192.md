---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Viewing LXC Container Mounts

Created: 2024-07-03 19:06:52 UTC
Updated: 2024-07-03 19:09:18 UTC
UUID: 72137192-1451-47b4-bba9-595d5103873b
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Assistant** - 2024-07-03 19:06:58 UTC

 To see a clean output of mounts in an LXC (Linux Container), you can use the `lxc-info` command with the `-c lxc.mount.entry` option. Here's the command:

```
lxc-info -n <container_name> -c lxc.mount.entry
```

Replace `<container_name>` with the name of your specific container.

If you want to see all mounts, including those not explicitly defined in the container configuration, you can use the `lxc-attach` command to run `mount` inside the container:

```
lxc-attach -n <container_name> -- mount
```

This will show you all active mounts within the container.

Would you like me to explain these commands further or provide any additional information about LXC mounts?

---

**Human** - 2024-07-03 19:06:58 UTC

is there a command to see a clean output of mounts on my lxc?

---

**Human** - 2024-07-03 19:07:18 UTC

well, from the console of the container..

---

**Assistant** - 2024-07-03 19:07:18 UTC

 Ah, I see. If you're already inside the container's console, you don't need to use LXC-specific commands. You can use standard Linux commands to view the mounts. Here are a couple of options:

1. Using the `mount` command:
   ```
   mount
   ```
   This will show all mounted filesystems.

2. For a cleaner, more readable output, you can use:
   ```
   mount | column -t
   ```
   This pipes the output through `column` to align the columns neatly.

3. If you want to see only the mount points and the filesystems, you can use:
   ```
   df -h
   ```
   This shows mounted filesystems with human-readable sizes.

4. For a more detailed view that includes mount options, you can check the `/proc/mounts` file:
   ```
   cat /proc/mounts
   ```

5. If you want to filter for specific types of mounts, you can use `grep`. For example, to see only the bind mounts:
   ```
   mount | grep '\btype\b.*\bbind\b'
   ```

Would you like me to explain any of these commands further?

---

**Human** - 2024-07-03 19:09:18 UTC

now to troubleshoot a "device is busy"

---

**Assistant** - 2024-07-03 19:09:18 UTC

 Certainly. When you encounter a "device is busy" error while trying to unmount a filesystem, it usually means that some process is still using the mounted filesystem. Here are some steps to troubleshoot this issue:

1. First, identify which mount point is causing the issue. Let's say it's `/mnt/example`.

2. Use the `lsof` command to list open files on the mount point:
   ```
   lsof /mnt/example
   ```
   This will show processes that are using files or have their working directory on the mount.

3. If `lsof` isn't available, you can use `fuser`:
   ```
   fuser -m /mnt/example
   ```
   This shows processes using the mount point.

4. To see if any shell is using the directory as its current working directory:
   ```
   lsof | grep cwd | grep /mnt/example
   ```

5. If you identify the processes, you can try to stop them or change their working directory.

6. For stubborn mounts, you can try the lazy unmount option:
   ```
   umount -l /mnt/example
   ```
   This detaches the filesystem immediately, cleaning up references when it's no longer busy.

7. In extreme cases, you might need to use the force option (be cautious with this):
   ```
   umount -f /mnt/example
   ```

8. If it's a network filesystem (NFS), check if the server is responsive:
   ```
   showmount -e <server_ip>
   ```

9. Check `dmesg` or system logs for any related errors:
   ```
   dmesg | tail
   ```

Would you like me to elaborate on any of these steps or provide more information on a specific aspect of troubleshooting "device is busy" errors?

---

