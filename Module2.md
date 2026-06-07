# Linux Commands Cheat Sheet

---

## Module 2 - Linux Core Concepts 2

### Init Process

| Command | Description |
|---------|-------------|
| `ls -l /sbin/init` | Check which init process is used |
| `ps -p 1` | Verify PID 1 (always the init process) |

> 💡 Init process = first process that starts on boot, always gets PID 1
> 💡 Modern Linux systems use **systemd** as init process

---

### systemd Targets

| Command | Description |
|---------|-------------|
| `systemctl get-default` | Show current default target |
| `systemctl set-default multi-user.target` | Set default to CLI mode (on next reboot) |
| `systemctl set-default graphical.target` | Set default to GUI mode (on next reboot) |
| `systemctl isolate multi-user.target` | Switch to CLI mode immediately |
| `systemctl isolate graphical.target` | Switch to GUI mode immediately |

> 💡 set-default = changes on next reboot
> 💡 isolate = changes immediately

| Old Runlevel | systemd Target | Description |
|-------------|----------------|-------------|
| 1 | `rescue.target` | Single user, troubleshooting |
| 3 | `multi-user.target` | CLI only, no GUI (servers/VMs) |
| 5 | `graphical.target` | GUI mode (desktop) |

---

### systemctl - Service Management

| Command | Description |
|---------|-------------|
| `systemctl start <service>` | Start a service |
| `systemctl stop <service>` | Stop a service |
| `systemctl restart <service>` | Restart a service |
| `systemctl status <service>` | Check service status |
| `systemctl enable <service>` | Auto start on boot |
| `systemctl disable <service>` | Don't start on boot |
| `systemctl list-units` | List all running units |

> 💡 systemctl = remote control for all services on Linux

---

### File Type

| Command | Description |
|---------|-------------|
| `file <filename>` | Check actual type of any file |
| `file /root/firefox.deb` | Example - check .deb file type |

| Extension | Type | Used In |
|-----------|------|---------|
| `.deb` | Debian binary package | Ubuntu, Debian |
| `.rpm` | RPM package | CentOS, RHEL, Fedora |
| `.tar.gz` | Compressed archive | Any distro |

> 💡 file command = tells actual file type regardless of extension

---

### Hardware Info

| Command | Description |
|---------|-------------|
| `lspci` | List all PCI devices |
| `lspci \| grep -i ethernet` | Find ethernet controller and vendor |
| `lspci \| grep -i vga` | Find graphics card |
| `lspci \| grep -i audio` | Find audio device |

> 💡 -i in grep = case insensitive search
> 💡 lspci = best command to identify hardware vendors

---