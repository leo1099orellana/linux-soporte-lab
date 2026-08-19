# 05 — Logs & Health Checks

> **Support context:** when something fails, the log tells you *why*. Reading logs and doing quick health checks is how you turn "it's broken" into an actual diagnosis.

## Where logs live

Most system logs are under `/var/log/`:

```bash
ls /var/log/
```

Common ones: `syslog` (general), `auth.log` (logins / sudo), plus a file or folder per service.

## Reading logs

| Command | Use |
|---------|-----|
| `tail archivo.log` | Show the **last** lines — the most recent events are at the end |
| `tail -f archivo.log` | Follow the log **live** (great while reproducing a problem) |
| `head archivo.log` | Show the first lines |
| `less archivo.log` | Open a long log to scroll (`q` to quit, `/word` to search) |
| `grep error archivo.log` | Show only lines containing "error" |

**Why `tail` for errors:** logs append new entries at the bottom, so the newest error is at the end — `tail` gets you there instantly instead of scrolling the whole file.

```bash
# The classic support move: filter a big log for the problem
grep -i error /var/log/syslog | tail -20
```

> `![Reading a log with tail and grep](screenshots/05-logs.png)`

## Quick health checks

Before blaming the app, rule out the basics — disk, memory, is the service even running:

```bash
df -h            # disk space (a full disk breaks all kinds of things)
free -h          # memory usage
top              # live CPU / memory per process (q to quit)
ps aux | grep ssh    # is a specific process running?
systemctl status ssh # is a service running? why did it stop?
```

`df -h` is the first thing to check on a "everything is slow / nothing works" complaint — a disk at 100% is a surprisingly common cause.

---

➡️ Next: [Troubleshooting guide](troubleshooting.md)
