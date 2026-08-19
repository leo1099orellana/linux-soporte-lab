# 04 — Permissions

> **Support context:** "I can't open / edit / run this file" is one of the most common tickets on Linux. Almost always it's a permissions or ownership problem. Knowing how to read and fix permissions solves it fast.

## Reading permissions

`ls -l` shows the permissions on the left:

```
-rwxr-xr--  1 leonel  soporte  2048 Aug 19 16:00 script.sh
```

Reading `-rwxr-xr--`:

| Block | Who | Meaning |
|-------|-----|---------|
| `rwx` | **owner** (leonel) | read, write, execute |
| `r-x` | **group** (soporte) | read, execute |
| `r--` | **others** | read only |

- **r** = read, **w** = write, **x** = execute
- First character: `-` file, `d` directory

## Changing permissions — `chmod`

**Symbolic** (easy to read):

```bash
chmod +x script.sh        # make it executable
chmod u+w archivo.txt     # give the owner write
chmod o-r archivo.txt     # remove read from others
```

**Numeric** (each digit = owner / group / others, r=4 w=2 x=1):

```bash
chmod 755 script.sh       # rwx r-x r-x  (common for scripts)
chmod 644 archivo.txt     # rw- r-- r--  (common for regular files)
```

## Changing ownership — `chown`

```bash
sudo chown leonel archivo.txt          # change owner
sudo chown leonel:soporte archivo.txt  # change owner and group
```

> `![Permissions before and after](screenshots/04-permissions.png)`

## sudo — running as administrator

`sudo` runs a single command with admin rights. You need it to touch system files, install software, or manage other users' files. If a command returns **"Permission denied"**, the fix is usually either `sudo` or correcting ownership with `chown` — see [troubleshooting](troubleshooting.md).

---

➡️ Next: [Logs & health checks](05-logs-and-monitoring.md)
