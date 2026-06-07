# Linux Commands Cheat Sheet

---

## Module 4 - Linux Basic Commands 2

### Create Files with Content

| Command | Description |
|---------|-------------|
| `touch file.txt` | Create empty file |
| `echo "text" > file.txt` | Create file with text |
| `echo "text" >> file.txt` | Append text to existing file |
| `cat > file.txt` | Create file, type multiple lines (Ctrl+D to save) |
| `vi file.txt` | Create and edit file in vi editor |

> 💡 `>` = overwrites ⚠️
> 💡 `>>` = appends safely ✅

---

### Tarball & Compression

| Command | Description |
|---------|-------------|
| `tar -czf file.tar.gz folder` | Create gzip compressed tarball |
| `tar -xzf file.tar.gz` | Extract tarball |
| `tar -xzf file.tar.gz -C /path/` | Extract to specific location |
| `tar -tf file.tar.gz` | View contents without extracting |
| `gunzip file.gz` | Extract gzip only (no tar) |
| `zcat file.gz` | Read gz file without extracting |

| Flag | Meaning |
|------|---------|
| `-c` | Create new tarball |
| `-x` | Extract tarball |
| `-z` | Compress/decompress using gzip |
| `-f` | Specify filename |
| `-C` | Destination folder |

> 💡 `.tar.gz` = bundled + compressed → use `tar -xzf`
> 💡 `.gz` only = only compressed → use `gunzip`
> 💡 TAR = packs, GZIP = squeezes. Together they make `.tar.gz`

---

### Find Files

| Command | Description |
|---------|-------------|
| `find /path -name "filename"` | Find file by name |
| `find /path -name "*.txt"` | Find all .txt files |
| `find /path -type f` | Find only files |
| `find /path -type d` | Find only directories |
| `find / -name "filename"` | Search entire system |

> 💡 `find` = searches filenames, not file contents
> 💡 Always specify directory like `/opt` instead of `/` to avoid slow search

---

### Search Inside Files (grep)

| Command | Description |
|---------|-------------|
| `grep "text" file.txt` | Search text in a file |
| `grep -r "text" /path` | Search recursively in directory |
| `grep -i "text" file.txt` | Case insensitive search |
| `grep -r "text" /path > output.txt` | Save results to file |

> 💡 `grep` = searches inside file contents
> 💡 `-i` = case insensitive (matches TEXT, text, Text)
> 💡 Key difference:
> - `find` = searches filenames
> - `grep` = searches inside file contents

---

### Redirect Operators

| Symbol | Meaning | Example |
|--------|---------|---------|
| `>` | Write to file (overwrites) | `echo "hi" > file.txt` |
| `>>` | Append to file | `echo "hi" >> file.txt` |
| `<` | Take input from file | `cat < file.txt` |
| `2>` | Redirect errors (STDERR) | `python3 script.py 2> error.txt` |
| `&>` | Redirect both output + errors | `script.py &> output.txt` |

| Stream | Number | Description |
|--------|--------|-------------|
| STDIN | 0 | Standard input |
| STDOUT | 1 | Normal output → `>` |
| STDERR | 2 | Error output → `2>` |

> 💡 `>` = redirects normal output
> 💡 `2>` = redirects error messages
> 💡 `&>` = redirects everything

---

### Read Compressed Files

| Command | Description |
|---------|-------------|
| `zcat file.gz` | Read gz file without extracting |
| `gunzip file.gz` | Extract gz file |
| `zcat file.gz > output` | Read gz and save to file |

> 💡 `zcat` = read gzip file directly without extracting it first

---