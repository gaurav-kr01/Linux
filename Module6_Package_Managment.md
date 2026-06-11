# Linux Package Management

---

## What is Package Management?

Package management is basically installing, updating and removing software on Linux — just like App Store on iPhone or Play Store on Android. Instead of downloading and installing software manually, a package manager does everything for you in one command.

Without package manager:
```bash
# You find software online
# Download manually
# Install manually
# Handle all dependencies yourself 😤
```

With package manager:
```bash
# One command does everything ✅
sudo apt install firefox
```

---

## How it Works — 3 Main Parts

**1. Package (`.deb` / `.rpm`)**
A compressed file containing the software, its settings and instructions on how to install it.

**2. Repository (Repo)**
A remote server maintained by Linux — think of it like an App Store server where all software is stored safely.

**3. Package Manager (`APT` / `DNF`)**
The tool that connects to the repo, downloads the software and installs it cleanly.

---

## Different Distros, Different Package Managers

| Distro | Package Manager | Command |
|--------|----------------|---------|
| Ubuntu/Debian | APT | `apt install` |
| CentOS/RHEL | YUM/DNF | `yum install` |
| Any Linux | RPM/DPKG | `rpm` / `dpkg` |

> 💡 Since your system is Ubuntu — you will mostly use `APT`

---

## APT vs DPKG — What is the Difference?

| Tool | Type | Can Download? | Handles Dependencies? |
|------|------|--------------|----------------------|
| `dpkg` | Low level | ❌ No | ❌ No |
| `apt` | High level | ✅ Yes | ✅ Yes |

> 💡 `dpkg` = works only with local files on disk, can't download anything
> 💡 `apt` = connects to internet, downloads software and handles everything automatically
> 💡 Think of `apt` as the smart layer on top of `dpkg`

---

## What are Dependencies?

When you install software, it often needs other software to run — these are called dependencies.

For example:
```
Firefox needs:
├── libasound2
├── libcairo2
└── libgtk3
```

> 💡 `apt` handles all dependencies automatically — you don't have to worry about them
> 💡 `dpkg` does NOT handle dependencies — if something is missing it just fails ❌

---

## APT Commands

### Update & Upgrade
```bash
# Update local package list (always run this first)
sudo apt update

# Upgrade all installed packages to latest version
sudo apt upgrade
```

> 💡 `apt update` = updates the list of available software (doesn't install anything)
> 💡 `apt upgrade` = actually installs the newer versions

---

### Install Software
```bash
# Install from internet (most common way)
sudo apt install firefox

# Install from local .deb file (using apt)
sudo apt install /root/firefox.deb

# Install from local .deb file (using dpkg)
sudo dpkg -i /root/firefox.deb
```

> 💡 Always use `apt install` for local .deb files too — it handles dependencies
> 💡 Use `dpkg -i` only when you have no internet and all dependencies are already installed

---

### Remove Software
```bash
# Remove software (keeps settings)
sudo apt remove firefox

# Remove software + delete all settings
sudo apt purge firefox

# Remove unused dependencies (cleanup)
sudo apt autoremove

# Remove software + its unused dependencies together
sudo apt autoremove --purge firefox
```

> 💡 `remove` = uninstalls but keeps your config files (useful if you want to reinstall later)
> 💡 `purge` = removes everything including config files (clean wipe)
> 💡 `autoremove` = cleans up leftover dependencies that are no longer needed

---

### Search & Inspect
```bash
# Search for software
apt search firefox

# List all installed packages
dpkg -l

# Check if specific package is installed
dpkg -l | grep firefox
```

---

## Common Errors & Fixes

### Error 1 — Unmet Dependencies
```
Error: package has unmet dependencies, but it is not installable
```
**Fix:**
```bash
# Step 1 - update package list first
sudo apt update

# Step 2 - try installing again
sudo apt install firefox
```
> 💡 This happens because your local package list is outdated — `apt update` fixes it

---

### Error 2 — Unsupported File
```
E: Unsupported file /root/firefox given on commandline
```
**Fix:**
```bash
# Wrong ❌
sudo apt install /root/firefox

# Correct ✅ (need .deb extension)
sudo apt install /root/firefox.deb
```
> 💡 Always include the `.deb` extension in the file path

---

### Error 3 — Wrong Command for Remove
```bash
# Wrong ❌ (file path only used for install)
sudo apt purge /root/firefox.deb

# Correct ✅ (use package name for remove)
sudo apt purge firefox
```
> 💡 For installing → use file path `/root/firefox.deb`
> 💡 For removing → use package name `firefox`

---

### Error 4 — Broken DPKG Installation
```
dpkg was interrupted, you must manually run to correct the problem
```
**Fix:**
```bash
# Force APT to fix broken installation
sudo apt install -f
```
> 💡 `-f` = fix broken — scans the system and completes any interrupted installations

---

## Quick Reference

| Command | Description |
|---------|-------------|
| `sudo apt update` | Update package list |
| `sudo apt upgrade` | Upgrade all packages |
| `sudo apt install <pkg>` | Install software |
| `sudo apt remove <pkg>` | Remove software (keep settings) |
| `sudo apt purge <pkg>` | Remove software + settings |
| `sudo apt autoremove` | Clean unused dependencies |
| `sudo apt install -f` | Fix broken installation |
| `apt search <pkg>` | Search for software |
| `dpkg -l` | List all installed packages |
| `sudo dpkg -i <file.deb>` | Install local .deb file |

---