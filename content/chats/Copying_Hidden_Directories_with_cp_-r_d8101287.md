---
created: 2024-12-08T11:55
updated: 2024-12-08T11:55
---
# Copying Hidden Directories with cp -r

Created: 2024-11-01 21:35:52 UTC
Updated: 2024-11-01 21:36:40 UTC
UUID: d8101287-46c1-40dd-b40b-096cf6307e31
Account: 912bd4f0-edc2-4966-a180-6d01c38e12d1

---

**Human** - 2024-11-01 21:35:56 UTC

does cp -r not move .folders?

---

**Assistant** - 2024-11-01 21:35:56 UTC

 Let me clarify how `cp -r` works with hidden directories (folders starting with a dot):

`cp -r` does copy hidden folders and their contents, but you need to make sure they're included in your source path. Here are the key points:

```bash
# This WILL copy .hidden_folder:
cp -r /path/to/.hidden_folder /destination/

# This WILL NOT copy hidden folders:
cp -r /source/* /destination/

# This WILL copy everything including hidden folders:
cp -r /source/. /destination/
```

The key difference is that using `*` in the path doesn't include hidden files/folders by default, while explicitly specifying the hidden folder or using `.` will include them.

Would you like me to explain more about how shell globbing patterns work with hidden files?

---

**Assistant** - 2024-11-01 21:36:40 UTC

 Yes! It's one of those shell subtleties that's super useful to know! The `.` refers to the current directory and includes ALL files (including hidden ones), while `*` follows the Unix convention of not matching files that start with a dot by default.

If you ever specifically want to match just hidden files with a glob pattern, you can also use `.*`, but be careful - that will also match `.` and `..` (the current and parent directory references), which you usually don't want to copy!

---

**Human** - 2024-11-01 21:36:40 UTC

ahhh. the */. is interesting! today i learned!

---

