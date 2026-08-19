# 03 — Packages & Software

> **Support context:** installing a tool a user or a service needs, and keeping the system patched, is bread-and-butter support work on Linux.

## Keeping the system updated

```bash
sudo apt update        # refresh the list of available packages
sudo apt upgrade       # install available updates
```

`apt update` doesn't install anything — it just refreshes the catalog. `apt upgrade` is what actually updates. Running `update` before installing anything is a good habit (avoids "package not found" on a stale catalog).

## Installing and removing software (apt)

```bash
sudo apt install htop      # install a package
sudo apt remove htop       # remove it (keeps config files)
sudo apt purge htop        # remove it AND its config files
apt search monitor         # search for a package by keyword
```

> `![apt install](screenshots/03-apt-install.png)`

## The three ways to install software

1. **From the repositories with `apt`** — the normal, preferred way. Handles dependencies automatically.
2. **From a `.deb` file with `dpkg`** — when a vendor gives you a downloaded package (e.g. an agent, a driver):
   ```bash
   sudo dpkg -i paquete.deb
   sudo apt -f install        # fixes missing dependencies if dpkg complains
   ```
3. **From source / a script** — least common in support; you compile or run an install script provided by the software.

## Checking what's installed

```bash
dpkg -l | grep htop        # is this package installed?
which htop                 # where is the binary?
```

---

➡️ Next: [Permissions](04-permissions.md)
