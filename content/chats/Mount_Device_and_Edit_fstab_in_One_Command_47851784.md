---
created: 2024-12-08T11:55
updated: 2024-12-12T09:04
---
# Mount Device and Edit fstab in One Command

Created: 2024-07-03 20:14:52 UTC
Updated: 2024-07-03 20:43:59 UTC
UUID: 47851784-0011-41ef-b786-1790ab22cbe1
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-07-03 20:14:58 UTC

can i mount a device and write it to fstab with a single command?

---

**Assistant** - 2024-07-03 20:14:58 UTC

 Yes, you can mount a device and add it to the fstab file with a single command, but it requires combining multiple operations. Here's an example of how you could do this:

```bash
sudo mount /dev/sdb1 /mnt/mydrive && echo "/dev/sdb1 /mnt/mydrive ext4 defaults 0 2" | sudo tee -a /etc/fstab
```

This command does the following:

1. Mounts the device `/dev/sdb1` to `/mnt/mydrive`
2. If the mount is successful, it appends an entry for this mount to the `/etc/fstab` file

Please note:

- Replace `/dev/sdb1` with your actual device path
- Replace `/mnt/mydrive` with your desired mount point
- Replace `ext4` with the appropriate filesystem type
- Adjust the mount options, dump, and pass values as needed

Be cautious when modifying fstab, as incorrect entries can cause boot issues. It's always a good idea to backup your fstab file before making changes.

Would you like me to explain any part of this command in more detail?

---

**Human** - 2024-07-03 20:16:56 UTC

lets try for an nfs share at 192.168.0.25 with share /mnt/purgatory/Media and local mountpoint of /Media

---

**Assistant** - 2024-07-03 20:16:56 UTC

 Certainly. Here's a command to mount an NFS share and add it to fstab in one go:

```bash
sudo mount -t nfs 192.168.0.25:/mnt/purgatory/Media /Media && echo "192.168.0.25:/mnt/purgatory/Media /Media nfs defaults 0 0" | sudo tee -a /etc/fstab
```

This command does the following:

1. Mounts the NFS share from 192.168.0.25:/mnt/purgatory/Media to the local directory /Media
2. If the mount is successful, it adds an entry for this mount to the /etc/fstab file

A few things to note:

- Ensure the local mount point (/Media) exists before running the command
- The NFS server (192.168.0.25) must be accessible and the share (/mnt/purgatory/Media) must be exported
- You may need to adjust the mount options based on your specific requirements

Would you like me to break down any part of this command or explain the fstab entry in more detail?

---

**Human** - 2024-07-03 20:19:58 UTC

now, i've used mkdir -p /Media/downloads/complete

how can i chown blake:blake and chmod 775 that full tree with one line?

---

**Assistant** - 2024-07-03 20:19:58 UTC

 To change the ownership to blake:blake and set permissions to 775 for the entire directory tree under /Media/downloads/complete, you can use the following command:

```bash
sudo chown -R blake:blake /Media/downloads/complete && sudo chmod -R 775 /Media/downloads/complete
```

This command does two things:

1. `sudo chown -R blake:blake /Media/downloads/complete`: Changes the owner and group of all files and directories under /Media/downloads/complete to blake:blake recursively.

2. `sudo chmod -R 775 /Media/downloads/complete`: Changes the permissions of all files and directories under /Media/downloads/complete to 775 recursively.

The `-R` flag in both commands ensures that the changes are applied recursively to all subdirectories and files.

Note that you'll need sudo privileges to run this command if you're not already the owner of the directory.

Would you like me to explain the permissions (775) in more detail?

---

**Assistant** - 2024-07-03 20:20:30 UTC

 Ah, I see. That's a common mistake. The difference between `-r` and `-R` is important:

1. `-r` (lowercase) is often used for "reverse" or other specific options in some commands.
2. `-R` (uppercase) is typically used for "recursive" operations in many Unix/Linux commands.

For `chown` and `chmod`, the recursive flag is indeed `-R` (uppercase). Using `-r` (lowercase) would typically result in an error or unexpected behavior.

It's a good habit to check the man pages (`man chown` or `man chmod`) or use the `--help` option (`chown --help` or `chmod --help`) when you're unsure about command options. These resources can quickly clarify such details.

Thanks for sharing your experience - it's a helpful reminder that case sensitivity in command options can be crucial in Linux/Unix environments.

---

**Human** - 2024-07-03 20:20:30 UTC

ok.. i guess i could have read the help.. i was trying -r and getting a not found error

---

**Assistant** - 2024-07-03 20:23:22 UTC

 Yes, that's correct. Now that you've mounted the NFS share on your Proxmox host, you can use it as a storage location for your virtual machines or containers. Here's how you can typically add it in Proxmox:

1. In the Proxmox web interface, go to Datacenter -> Storage.

2. Click on "Add" and choose "Directory" as the storage type.

3. Fill in the details:
   - ID: Give it a unique name (e.g., "NFS_Media")
   - Directory: Use the mount point you created (/Media)
   - Content: Select what you want to store here (ISO images, backups, disk images, etc.)

4. Click "Add" to create the new storage.

After adding this, you'll be able to use this storage location when creating new VMs or containers, storing backups, uploading ISO images, etc.

Remember that the performance of your VMs or containers using this storage will depend on your network speed and the performance of the NFS server.

Would you like more details on any specific use case for this new storage in Proxmox?

---

**Human** - 2024-07-03 20:23:22 UTC

ok. so now that mount i just added to my proxmox host.. from here i can add a mount point as a drive essentially, right?

---

**Human** - 2024-07-03 20:43:59 UTC

how can i pass that mount to a container on the proxmox host?

---

**Assistant** - 2024-07-03 20:43:59 UTC

 To pass the NFS mount to a container on your Proxmox host, you can use the "bind mount" feature. Here's how to do it:

1. From the Proxmox web interface, select the container you want to add the mount to.

2. Go to the "Resources" tab of the container.

3. Click on "Add" and choose "Mount Point".

4. Fill in the details:
   - MP: The path inside the container where you want the mount to appear (e.g., /mnt/media)
   - Path: The path on the host where the NFS share is mounted (/Media)
   - Type: Choose "Bind mount"

5. You can also set options like "Read-only" if needed.

6. Click "Add" to create the mount point.

Alternatively, you can do this via the command line on the Proxmox host:

```bash
pct set <container_id> -mp0 /Media,mp=/mnt/media
```

Replace <container_id> with your actual container ID, and adjust the paths as needed.

After adding the mount point, you'll need to restart the container for the changes to take effect.

Remember that the container will now have access to this NFS share, so consider any security implications this might have.

Would you like me to explain any part of this process in more detail?

---

