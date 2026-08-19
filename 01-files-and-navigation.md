# 01 — Files & Navigation

> **Support context:** the first thing you do on any server is find your way around — where am I, what's here, where are the files a user or a service needs. Then you manage those files: copy, move, back up, package them to send.

## Navigating

| Command | What it does |
|---------|--------------|
| `pwd` | Print the current directory (where am I) |
| `ls` | List files |
| `ls -l` | Long format: permissions, owner, size, date |
| `ls -lh` | Same, with human-readable sizes (KB/MB) |
| `ls -a` | Include hidden files (those starting with `.`) |
| `cd /ruta` | Change directory (absolute path) |
| `cd ..` | Go up one level |
| `cd` | Go back to your home directory |

**Absolute vs relative path:** an absolute path starts from root (`/etc/ssh/`) and works from anywhere. A relative path (`ssh/`) is read from where you currently are. Mixing these up is one of the most common "file not found" causes — see [troubleshooting](troubleshooting.md).

> `![ls -l output](screenshots/01-ls.png)`

## Managing files and folders

| Command | What it does |
|---------|--------------|
| `mkdir carpeta` | Create a folder |
| `touch archivo.txt` | Create an empty file |
| `cp origen destino` | Copy |
| `cp -r carpeta destino` | Copy a folder and its contents |
| `mv origen destino` | Move **or** rename |
| `rm archivo` | Delete a file |
| `rm -r carpeta` | Delete a folder and everything in it |

> ⚠️ **Careful with `rm -r`** — there's no recycle bin on the command line. Always run `pwd` / `ls` first to confirm you're deleting what you think you are.

## Wildcards

Wildcards let you act on many files at once:

| Wildcard | Matches |
|----------|---------|
| `*` | Any number of characters — `rm *.log` deletes every `.log` file |
| `?` | Exactly one character — `ls foto?.jpg` matches `foto1.jpg`, `foto2.jpg` |
| `[ ]` | One character from a set — `ls foto[12].jpg` |
| `{ }` | A list — `touch archivo{1,2,3}.txt` creates three files |

> `![Wildcards in action](screenshots/01-wildcards.png)`

## Packaging files to send (tar / gzip)

A real support task: **collect a service's logs and send them to a vendor or a teammate.** You bundle them into one compressed file.

```bash
# Create a compressed archive of a folder
tar -czvf logs.tar.gz /var/log/miapp/

# Extract it somewhere
tar -xzvf logs.tar.gz
```

Flags: **c**reate, **x**tract, **z** = gzip compression, **v**erbose (show progress), **f** = filename.

---

➡️ Next: [Editing config files](02-editing-configs.md)
