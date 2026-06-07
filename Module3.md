# Linux Commands Cheat Sheet

---

## Module 1 - Linux Core Concepts 1

### System Information

| Command | Description |
|---------|-------------|
| `uname` | Print system information |
| `uname -a` | Show all system information |
| `uname -r` | Show kernel version only |
| `dmesg` | Print kernel ring buffer (diagnostic messages) |
| `lsb_release -a` | Show OS version |
| `cat /etc/os-release` | Show OS details |

> 💡 dmesg = best tool for troubleshooting hardware issues
> 💡 Kernel version format → `6.8.0-101-generic`
> - `6` = Major version
> - `8` = Minor version
> - `0` = Patch version

---

### Block Devices

| Command | Description |
|---------|-------------|
| `lsblk` | List all block devices |
| `lsblk -d -o NAME,TYPE` | Show only disks, no partitions |
| `lsblk -d -o NAME,TYPE \| grep disk` | Filter only disk type devices |

| Device Type | Description |
|-------------|-------------|
| `disk` | Physical hard drive |
| `part` | Partition of a disk |
| `rom` | CD/DVD ROM |

> 💡 `-d` = hides partitions, shows only main disk
> 💡 `-o` = select specific columns to display

---

### File Types

| Command | Description |
|---------|-------------|
| `file <filename>` | Check actual type of any file |
| `file /root/firefox.deb` | Example - check .deb file |

| Extension | Type | Used In |
|-----------|------|---------|
| `.deb` | Debian binary package | Ubuntu, Debian |
| `.rpm` | RPM package | CentOS, RHEL, Fedora |
| `.tar.gz` | Compressed archive | Any distro |

> 💡 file command = tells actual file type regardless of extension

---

### Directory Operations

| Command | Description |
|---------|-------------|
| `mkdir directory_name` | Create single directory |
| `mkdir -p parent/{child1,child2}` | Create parent with 2 child dirs |
| `mkdir -p parent1/{child1,child2} parent2/{child1,child2}` | Create 2 parents each with 2 child dirs |
| `tree directory_name` | View directory structure |
| `ls` | List files in current directory |
| `ls -l` | List with details |
| `pwd` | Print current working directory |
| `cd directory_name` | Change directory |
| `cd ..` | Go back one directory |

> 💡 `-p` = creates nested directories in one shot, no error if already exists

---

### Move & Copy Operations

| Command | Description |
|---------|-------------|
| `mv source dest` | Move file or directory |
| `mv oldname newname` | Rename file or directory |
| `cp source dest` | Copy file |
| `cp -r source dest` | Copy entire directory |

> ⚠️ `mv` = cuts the source (original is gone)
> ⚠️ `cp` = copies the source (original stays)
> 💡 `mv` works same for both files and directories, no `-r` needed

---

### Delete Operations

| Command | Description |
|---------|-------------|
| `rm filename` | Delete a file |
| `rm -r directory_name` | Delete directory and its contents |
| `rm -rf directory_name` | Force delete, no confirmation |
| `rm -rf dir1 dir2` | Delete multiple directories at once |

| Flag | Meaning |
|------|---------|
| `-r` | Recursive (deletes everything inside) |
| `-f` | Force (no confirmation prompt) |

> ⚠️ `rm -rf` is irreversible — no recycle bin in Linux
> ⚠️ NEVER run `rm -rf /` — wipes entire system
> 💡 Always run `ls` first to confirm location before deleting

---