# 02 — Editing Config Files

> **Support context:** most fixes on a Linux server come down to editing a configuration file — a service that won't start, a wrong setting, a port to change. Doing this safely, over the terminal, is a core support skill.

## The golden rule: back up first

Before touching any config, make a copy. If the change breaks something, you restore it in one command.

```bash
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

If it goes wrong:

```bash
cp /etc/ssh/sshd_config.bak /etc/ssh/sshd_config
```

## nano — the quick editor

Simple and direct, no modes. Good for a fast edit.

| Key | Action |
|-----|--------|
| `Ctrl + O` | Save (write out) |
| `Enter` | Confirm the filename |
| `Ctrl + X` | Exit |
| `Ctrl + W` | Search inside the file |

```bash
sudo nano /etc/ssh/sshd_config
```

> `![Editing with nano](screenshots/02-nano.png)`

## vim — the one that's always there

More powerful, and **installed on every server** (nano sometimes isn't, on minimal installs). Worth knowing the basics so you're never stuck.

| Key | Action |
|-----|--------|
| `i` | Enter insert mode (start typing) |
| `Esc` | Leave insert mode |
| `:w` | Save |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit **without** saving (get out safely) |

## nano or vim? (interview answer)

> *"I use nano when it's available because it's simpler and faster for a quick config edit, but I can work in vim because it's the one that never fails — it's on every server, even minimal ones."*

That answer shows judgment, which is what they're actually asking about.

---

➡️ Next: [Packages & software](03-packages-and-software.md)
