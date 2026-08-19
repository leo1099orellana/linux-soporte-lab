# ⭐ Troubleshooting Guide

Real errors that came up while working through this lab, and how I diagnosed and fixed each one. This is the part that reflects actual support work: **not memorizing commands, but knowing what a message means and what to check next.**

Each case follows the same pattern: **symptom → cause → how I diagnosed it → fix.**

---

### `Permission denied`

- **Symptom:** a command or file access is refused.
- **Cause:** either the action needs admin rights, or the file is owned by another user.
- **Diagnosed:** ran `ls -l` on the file to see its owner and permissions.
- **Fix:** used `sudo` for a system-level action, or corrected ownership with `sudo chown usuario archivo` / permissions with `chmod`.

---

### `command not found`

- **Symptom:** the shell doesn't recognize a command.
- **Cause:** usually a **typo**, or the package that provides it isn't installed, or (for your own script) you forgot the `./` in front.
- **Diagnosed:** re-read the command for typos; checked if the tool was installed with `which nombre` / `dpkg -l | grep nombre`.
- **Fix:** corrected the typo, installed the package with `sudo apt install`, or ran a local script as `./script.sh`.

---

### `No such file or directory`

- **Symptom:** the file "isn't there" even though you're sure it exists.
- **Cause:** almost always a **path problem** — you're not in the directory you think, or you mixed an absolute and a relative path.
- **Diagnosed:** ran `pwd` to confirm where I was, then `ls` to confirm the file's actual location.
- **Fix:** used the correct path (absolute `/full/path/file` works from anywhere), or `cd`'d into the right directory first.

---

### A wildcard matches nothing

- **Symptom:** `ls *.log` returns nothing or an error.
- **Cause:** there are no files of that type in the current directory.
- **Diagnosed:** ran `ls` alone to see what's actually there.
- **Fix:** moved to the right directory, or used the correct extension/pattern.

---

### `Could not get lock /var/lib/dpkg/lock` (apt is busy)

- **Symptom:** `apt install` fails saying it can't get a lock.
- **Cause:** another process (an automatic update, or an apt command still running) is using the package system.
- **Diagnosed:** checked for running apt/dpkg processes with `ps aux | grep -i apt`.
- **Fix:** waited for it to finish; only if truly stuck, investigated the held lock rather than force-deleting it.

---

### Disk full / system acting strange

- **Symptom:** things fail to write, the system feels broken, services won't start.
- **Cause:** the disk is at 100%.
- **Diagnosed:** `df -h` to confirm which filesystem is full.
- **Fix:** found what's eating space (old logs, temp files) and cleared it safely, e.g. old archives in `/var/log` after confirming they're not needed.

---

### A service won't start

- **Symptom:** an app or service is down.
- **Cause:** could be config, permissions, or a dependency — the log says which.
- **Diagnosed:** `systemctl status servicio` for the summary, then `journalctl -u servicio` or the service's log in `/var/log/` with `tail`/`grep` for the actual error.
- **Fix:** addressed whatever the log pointed to (fixed the config, corrected permissions, freed a port), then restarted the service.

---

> **The takeaway:** in support, the value isn't knowing every command by heart — it's reading the error, forming a hypothesis, and checking it methodically. That's what this guide documents.
