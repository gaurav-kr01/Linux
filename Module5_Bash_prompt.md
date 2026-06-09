# Linux Commands Cheat Sheet

---

## Module - Linux Bash Prompt

### What is Shell?

> 💡 Shell = translator between YOU and Linux
> 💡 bash, zsh, fish are just different types of shells

| Shell | Location | Description |
|-------|----------|-------------|
| `bash` | `/bin/bash` | Most popular, default on Ubuntu |
| `sh` | `/bin/sh` | Original shell, simpler |
| `zsh` | `/bin/zsh` | Modern, used on Mac |
| `fish` | `/bin/fish` | Beginner friendly |

```bash
# Check current shell
echo $SHELL

# Change default shell
chsh -s /bin/bash
```

> ⚠️ Shell change only applies after logout and login again

---

### Environment Variables

> 💡 Environment Variables = settings that Linux uses to configure itself
> 💡 `export` = stores a VALUE
> 💡 `$` before variable name = get its value

| Command | Description |
|---------|-------------|
| `echo $VARIABLE` | Check a variable value |
| `export VAR="value"` | Set variable (temporary) |
| `echo 'export VAR="value"' >> ~/.profile` | Set variable (persistent) |
| `source ~/.profile` | Apply changes immediately |
| `env` | List ALL environment variables |

**Common environment variables:**

| Variable | Description | Example |
|----------|-------------|---------|
| `HOME` | Home directory | `/home/gaurav` |
| `USER` | Current username | `gaurav` |
| `SHELL` | Current shell | `/bin/bash` |
| `PATH` | Program locations | `/usr/bin:/bin` |
| `TERM` | Terminal type | `xterm-256color` |

---

### Aliases

> 💡 `alias` = shortcut for a command
> 💡 Avoid using existing command names for aliases

```bash
# Create alias (temporary)
alias up="uptime"

# Create alias (persistent)
echo 'alias up="uptime"' >> ~/.profile

# Remove alias
unalias up
```

**Useful aliases:**

| Alias | Command | Description |
|-------|---------|-------------|
| `ll` | `ls -l` | Detailed file list |
| `cls` | `clear` | Clear screen |
| `gs` | `git status` | Git status |
| `ga` | `git add .` | Git add all |
| `up` | `uptime` | System uptime |

---

### Profile Files (Startup Scripts)

> 💡 Profile files = startup settings that run automatically every login
> 💡 Files starting with `.` are hidden files → use `ls -a` to see them
> 💡 These are called dotfiles in DevOps world

| File | When it runs |
|------|-------------|
| `~/.profile` | Every login |
| `~/.bash_profile` | Bash login shell |
| `~/.bashrc` | Every time terminal opens |

```bash
# Open profile file
nano ~/.profile

# Apply changes immediately (without logout)
source ~/.profile

# Check profile file
cat ~/.profile
```

**What you can store in profile files:**

```bash
# Variables
export PROJECT=MERCURY
export MY_NAME=Gaurav

# Aliases
alias ll="ls -l"
alias cls="clear"

# Custom prompt
export PS1="[\d]gaurav@Gaurav:\w$ "
```

---

### Custom Prompt (PS1)

> 💡 PS1 = Prompt String 1 = controls how terminal prompt looks

```bash
# Set custom prompt
export PS1="[\d]gaurav@Gaurav:\w$ "

# Make it persistent
echo 'export PS1="[\d]gaurav@Gaurav:\w$ "' >> ~/.profile
source ~/.profile
```

**PS1 special characters:**

| Character | Meaning | Example |
|-----------|---------|---------|
| `\d` | Date | `Wed Apr 22` |
| `\t` | Time | `10:30:00` |
| `\u` | Username | `gaurav` |
| `\h` | Hostname | `Gaurav` |
| `\w` | Current directory | `~/documents` |
| `\$` | $ for user, # for root | `$` |

---

### PATH Variable

> 💡 PATH = list of folders where Linux looks for programs
> 💡 Without PATH you'd have to type full path every time

```bash
# Check PATH
echo $PATH

# Add folder to PATH (persistent)
echo 'export PATH=$PATH:/new/folder' >> ~/.profile
source ~/.profile
```

**Common PATH folders:**

| Folder | Contains |
|--------|----------|
| `/bin` | Basic commands (ls, cat, cp) |
| `/sbin` | System commands (reboot, fdisk) |
| `/usr/bin` | User programs (python, git) |
| `/usr/local/bin` | Manually installed programs |

---

### Quote Types

> ⚠️ Always use single quotes `'` when adding to profile files

| Quote | Usage | Example |
|-------|-------|---------|
| Single `'` | Plain text, no variable expansion | `echo 'hello $USER'` |
| Double `"` | Allows variable expansion | `echo "hello $USER"` |
| Backtick `` ` `` | Runs a command | `` echo `date` `` |

---

### Create Your Own Startup Script

```bash
# Step 1 - create script
nano ~/.my_variables.sh

# Step 2 - add your variables and aliases inside
export PROJECT=MERCURY
export MY_NAME=Gaurav
alias ll="ls -l"
alias cls="clear"

# Step 3 - add to .profile
echo 'source ~/.my_variables.sh' >> ~/.profile

# Step 4 - apply
source ~/.profile
```

> 💡 Push to GitHub as backup
> 💡 Copy to any new server instantly — all settings ready!


---