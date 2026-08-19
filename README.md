# Linux Support Lab

Hands-on Linux practice framed as **everyday IT-support tasks** on a Debian/Ubuntu server, worked entirely from the terminal (as you would over SSH on a real box).

The goal of this lab isn't to be a full Linux course — it's to show that I can **operate a Linux server, resolve common problems, and document the fix clearly**, which is what a support technician does day to day.

## 🧪 Environment

- **Host:** VirtualBox VM
- **OS:** Debian / Ubuntu (Linux)
- **Access:** terminal / command line (same workflow as SSH to a remote server)

> ℹ️ *(Add a screenshot of your VM / terminal here.)*
> `![Lab environment](screenshots/00-environment.png)`

## 🎯 What this lab shows

- Navigating and managing files on a Linux server
- Editing configuration files safely
- Installing and updating software (apt / dpkg)
- Reading and fixing file permissions
- Reading logs and doing basic health checks
- **Diagnosing and resolving real errors** (see the troubleshooting guide)

## 📖 Contents

| # | Topic | Support angle |
|---|-------|----------------|
| 01 | [Files & navigation](01-files-and-navigation.md) | Moving around a server, managing files, packaging logs to send |
| 02 | [Editing config files](02-editing-configs.md) | Changing service configs over the terminal, safely |
| 03 | [Packages & software](03-packages-and-software.md) | Installing tools users need, keeping the system updated |
| 04 | [Permissions](04-permissions.md) | Fixing "permission denied" and access problems |
| 05 | [Logs & health checks](05-logs-and-monitoring.md) | Finding out *why* something failed |
| ⭐ | [Troubleshooting](troubleshooting.md) | Real errors I hit and how I solved them |

> The **[troubleshooting guide](troubleshooting.md)** is the most useful part — it documents the actual problems that came up and how I diagnosed and fixed each one.

---

*Built by [Leonel Orellana](https://github.com/leo1099orellana) as part of my transition into IT support / infrastructure.*
