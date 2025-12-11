```shell
mandb, updatedb
man, apropos, whatis
man [-K, -k, -I, --wildcard, --regex]
less [/string, n, -I]
apropos -a, -r, -w
```

- manual secion [1, 5, 8]
- `/etc/mam_db.conf`, `/usr/share/man`

---

# Find the command
ChatGPT said:Ah — you’re asking “How would I discover that getfacl exists in the first place?”
In other words: If you only know you want to look up permissions, how would you find the right command?

# Apropos

apropos permission
apropos acl
apropos access

✅ 5. Search the filesystem for likely binaries

ls /usr/bin | grep acl
ls /bin | grep facl

---

Ah — you’re asking **“How would I *discover* that `getfacl` exists in the first place?”**
In other words: *If you only know you want to look up permissions, how would you find the right command?*

Great question. Here are reliable ways to find the right Linux tool *even if you don’t know its name yet.*


For example:

```
getfacl (1)      - get file access control lists
setfacl (1)      - set file access control lists
chmod (1)        - change file modes or Access Control Lists
```

This is **exactly how you would discover `getfacl`** if you only knew “ACL” or “permissions.”

---

# ✅ 2. Use `man -k` (same as apropos)

```bash
man -k permission
man -k acl
```

Equivalent to `apropos`, but good to remember.

---

# ✅ 3. Search package contents (Debian/Ubuntu)

If you think “there must be a command, but I don’t know which package it’s in,” try:

```bash
apt search acl
```

or:

```bash
apt search permission
```

This would show:

```
acl - Access Control List utilities
```

The package `acl` contains `getfacl` and `setfacl`.

---

# ✅ 4. Use `whatis` if you suspect a name

If you guess something, try:

```bash
whatis getfacl
whatis setfacl
```

---

# ✅ 5. Search the filesystem for likely binaries

If you know the command might exist but not the exact name:

```bash
ls /usr/bin | grep acl
```

or:

```bash
ls /bin | grep facl
```

This often reveals:

```
getfacl
setfacl
```

---

# ✅ 6. Search the internet with the task in plain language

If you simply search:

> “Linux view ACL of file”
> “Linux show effective permissions”
> “Linux recursive permissions viewer”

You will get results explaining `getfacl`.
(Online search is often how sysadmins discover new tools.)

---

# 🔍 Summary: Best discovery flow

If I were trying to find a command to inspect detailed permissions *without knowing `getfacl`*, I would do:

### **Step 1 — Ask system for help**

```bash
apropos permission
```

### **Step 2 — See `getfacl` and `setfacl` appear**

### **Step 3 — Read man page**

```bash
man getfacl
```

…and now you know exactly what to use.

---

# ⭐ Bonus: Find all commands related to files

If you want to explore broadly:

```bash
apropos file
apropos directory
apropos access
```

Or even:

```bash
man 1 intro
```

which lists categories of commands.

---

If you want, I can show you:

* how to read the output of `getfacl`
* how to inspect effective permissions (owner + group + ACL)
* how to find commands for other categories (network, processes, hardware, etc.)

Just tell me what you’re exploring!

