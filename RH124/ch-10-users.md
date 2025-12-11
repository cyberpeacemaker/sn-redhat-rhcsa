```shell
id, ps awwu, 
su -, sudo -i
useradd, usermod (-L, -s /sbin/nologin), groupadd, groupod, newgrp, 
chage(-d 0), passwd
```
- [super, system, regular], [primary, supplementary] group
- `/etc/passwd`, {name, placeholder, UID, GID, comment, home, shell}, [/bin/bash, /sbin/nologing]
- `/etc/group`, {name, placeholder, GID, list of user}
- `/etc/sudoers.d`, interactive login/non-login shell, #TODO: ENV
-  manage, restrict local user accounts
    1. run `useradd` 
    2. read `etc/login.defs`
    3. write `/etc/group`, `/etc/passwd`, `etc/shadow`
    4. create `/home/username`
    5. cope `etc/skel`
- `/etc/shadow`, {name, hash password, last changed, min, max, warn, inactive, expire, reserved}, {algo, (yes option), salt, hased}


---

Here's how to parse and interpret that information.

---


2. **/home/operator1/bin**

   These are user-specific directories belonging to **operator1**, meaning:

   * Commands installed for operator1 will be found before system-wide commands.
   * Even though the shell was invoked in `/home/student`, the environment most likely belongs to operator1 (e.g., via `su - operator1`).

3. **/home/student/.local/bin**

4. **/home/student/bin**

   These are user-specific directories for the **student** user.
   Their presence suggests:

   * The user `operator1` **may have inherited environment variables **from `student`, or vice-versa.
   * This prompt may be from `operator1` switching into the `student` directory, or `su` without a login shell.

5. **System-wide executable directories:**

   * `/usr/local/bin`
   * `/usr/bin`
   * `/usr/local/sbin`
   * `/usr/sbin`

   Standard executable search paths for system-wide commands.

---

## ✔️ What Does This Tell Us?

* The **search order** prioritizes user‐specific directories for `operator1`, then `student`, then the system directories.
* If a command exists in multiple locations, the earliest directory in `$PATH` “wins.”
* The prompt suggests the user is `operator1` but currently inside the directory `/home/student`.

---

## ✔️ Summary (Short Version)

You're looking at a `$PATH` variable showing the directories the shell will search for executables, in order. It includes personal `bin` directories for both `operator1` and `student`, followed by normal system paths such as `/usr/bin` and `/usr/sbin`.


---

## Exactly — that explains it perfectly. Let me break it down clearly.
#
---

# ✔️ What `sudo su` Does

When you run:

```bash
sudo su
```

* `sudo` runs a command (`su`) **as root**.
* `su` (without `-`) switches to the root user **but keeps the environment of the calling user**.
* So your **PATH gets merged**: it keeps some of your original environment **and** prepends standard system directories for root (`/sbin`, `/bin`, `/usr/sbin`, `/usr/bin`, `/usr/local/sbin`, `/usr/local/bin`).

---

# ✔️ Why the System Directories Appear

1. **Root’s PATH always includes system directories** like `/bin`, `/sbin`, `/usr/bin`, `/usr/sbin`.
2. Because you used `sudo su` (no `-` for a login shell):

   * You inherit **operator1’s PATH** at the front.
   * Root’s system directories are appended (or sometimes prepended depending on configuration).

So the PATH you saw:

```
/home/operator1/.local/bin
/home/operator1/bin
/sbin
/bin
/usr/sbin
/usr/bin
/usr/local/sbin
/usr/local/bin
```

…is **operator1’s personal directories first**, then the system directories that root expects.

---

# ✔️ Key Difference: `su -` vs `su`

| Command     | Environment loaded?                    | PATH Example                                                                     |
| ----------- | -------------------------------------- | -------------------------------------------------------------------------------- |
| `sudo su`   | Keeps caller’s env + system dirs       | operator1 bins + system dirs                                                     |
| `sudo su -` | Full root login shell, root’s env only | Only root’s PATH: `/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin` |

---

✅ **Bottom line:**

Yes, the system directories appear because `sudo su` switches to root **without a login shell**, so the shell merges your personal PATH with root/system defaults.

---

If you want, I can draw a **diagram of how PATH changes with `sudo su` vs `sudo su -`**, which makes it super clear. Do you want me to do that?

