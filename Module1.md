# Linux Commands Cheat Sheet

---

## Module 1 - Linux Core Concepts 1

### System Information

| Command | Description |
|---------|-------------|
| `uname` | Print system information |
| `uname -a` | Show all system information |
| `dmesg` | Print kernel ring buffer (diagnostic messages) |

> 💡 dmesg = best tool for troubleshooting hardware issues

---

### Block Devices

| Command | Description |
|---------|-------------|
| `lsblk` | List all block devices |
| `lsblk -d -o NAME,TYPE` | Show only disks, no partitions |
| `lsblk -d -o NAME,TYPE \| grep disk` | Filter only disk type devices |

> 💡 -d = hides partitions | -o = select specific columns

---