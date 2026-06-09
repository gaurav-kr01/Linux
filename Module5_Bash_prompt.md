# Linux Bash Prompt

---

## Shell

Shell is basically a translator between you and Linux. When you type a command, the shell understands it and tells Linux what to do. There are different types of shells like bash, zsh, fish — but bash is the most popular and default on Ubuntu.

```bash
# Check your current shell
echo $SHELL

# Change your default shell
chsh -s /bin/bash
```

> 💡 Change only applies after logout and login again

---

## Environment Variables

Think of environment variables like settings on your phone — brightness, language, ringtone. Linux has similar settings stored as variables. For example, HOME stores your home directory, USER stores your username.

```bash
# Check a variable
echo $PROJECT

# Set a variable (temporary - lost after logout)
export PROJECT=MERCURY

# Set a variable (permanent - stays after logout)
echo 'export PROJECT=MERCURY' >> ~/.profile
source ~/.profile

# List all environment variables
env
```

Common environment variables:

| Variable | What it stores |
|----------|---------------|
| `HOME` | Your home directory |
| `USER` | Your username |
| `SHELL` | Your current shell |
| `PATH` | Where Linux looks for programs |
| `TERM` | Your terminal type |

> 💡 Always use `$` before variable name to get its value
> 💡 `export` is used to store a value in a variable

---

## Aliases

Aliases are shortcuts for commands. Instead of typing a long command every time, you create a short name for it.

```bash
# Create an alias (temporary)
alias up="uptime"

# Create an alias (permanent)
echo 'alias up="uptime"' >> ~/.profile
source ~/.profile

# Remove an alias
unalias up
```

Some useful aliases to have:

| Alias | Actual Command | What it does |
|-------|---------------|--------------|
| `ll` | `ls -l` | Detailed file list |
| `cls` | `clear` | Clear screen |
| `gs` | `git status` | Check git status |
| `up` | `uptime` | Check system uptime |

> 💡 `alias` is used for shortcuts, `export` is used for variables

---

## Profile Files

Profile files are like a startup checklist. Every time you login, Linux reads these files and sets everything up automatically — your variables, aliases, preferences — so you don't have to do it manually every time.

| File | When it runs |
|------|-------------|
| `~/.profile` | Every time you login |
| `~/.bashrc` | Every time you open a terminal |
| `~/.bash_profile` | Bash login shell only |

```bash
# Open and edit profile file
nano ~/.profile

# Apply changes without logout
source ~/.profile

# View profile file
cat ~/.profile
```

> 💡 Files starting with `.` are hidden files in Linux
> 💡 Use `ls -a` to see hidden files
> 💡 These files are called dotfiles in the DevOps world

---

## Custom Prompt (PS1)

PS1 controls how your terminal prompt looks. You can customize it to show date, username, hostname, current directory — whatever you want.

```bash
# Set custom prompt
export PS1="[\d]gaurav@Gaurav:\w$ "

# Make it permanent
echo 'export PS1="[\d]gaurav@Gaurav:\w$ "' >> ~/.profile
source ~/.profile
```

PS1 special characters:

| Character | What it shows | Example |
|-----------|--------------|---------|
| `\d` | Date | `Wed Apr 22` |
| `\t` | Time | `10:30:00` |
| `\u` | Username | `gaurav` |
| `\h` | Hostname | `Gaurav` |
| `\w` | Current directory | `~/documents` |
| `\$` | $ for user, # for root | `$` |

> 💡 PS1 = Prompt String 1

---

## PATH Variable

PATH is a list of folders where Linux looks for programs. When you type `python3`, Linux searches through all PATH folders to find it. Without PATH you would have to type the full path every time like `/usr/bin/python3`.

```bash
# Check your PATH
echo $PATH

# Add a new folder to PATH (permanent)
echo 'export PATH=$PATH:/new/folder' >> ~/.profile
source ~/.profile
```

Common folders in PATH:

| Folder | What it contains |
|--------|-----------------|
| `/bin` | Basic commands like ls, cat, cp |
| `/sbin` | System commands like reboot, fdisk |
| `/usr/bin` | User programs like python, git |
| `/usr/local/bin` | Manually installed programs |

---

## Quote Types

This is very important when working with profile files and variables.

| Quote | Usage | Example |
|-------|-------|---------|
| Single `'` | Plain text, no variable expansion | `echo 'hello $USER'` prints `hello $USER` |
| Double `"` | Allows variable expansion | `echo "hello $USER"` prints `hello gaurav` |
| Backtick `` ` `` | Runs a command inside | `` echo `date` `` prints current date |

> ⚠️ Always use single quotes `'` when adding to `~/.profile`
> ⚠️ Never use backticks when adding to profile files

---

## Your Own Startup Script

You can create your own script that loads automatically on every login — keeping all your variables and aliases in one clean place.

```bash
# Step 1 - create your script
nano ~/.my_variables.sh

# Step 2 - add everything inside
export PROJECT=MERCURY
export MY_NAME=Gaurav
alias ll="ls -l"
alias cls="clear"
alias gs="git status"

# Step 3 - link it to .profile
echo 'source ~/.my_variables.sh' >> ~/.profile

# Step 4 - apply
source ~/.profile
```
