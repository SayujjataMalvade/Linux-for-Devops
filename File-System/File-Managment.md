# Linux File System, Storage & File Management Notes

This document contains **Linux fundamentals** related to memory types, file systems, permissions, links, storage, and important directories. It is suitable for **DevOps engineers, Linux admins, and interview preparation**.

---

## 1. Configuration Files: Volatile vs Non-Volatile Memory

### Volatile Memory
- **RAM**
- Data is lost when the system is rebooted or powered off

### Non-Volatile Memory
- **ROM / Disk (HDD, SSD, NVMe)**
- Configuration files are stored on disk
- Examples:
  - `/etc`
  - `/var`
  - `/home`

✅ **Linux configuration files are stored in non-volatile memory (disk)**.

---

## 2. Storage & File Management

### File Permissions

- `chmod` → Change file permissions  
- `chown` → Change file owner  
- `chgrp` → Change group ownership  

### Permission Values

| Permission | Value |
|----------|-------|
| Read (r) | 4 |
| Write (w) | 2 |
| Execute (x) | 1 |

Permissions are represented as **4 2 1**.

Example:
```
drwxr-x---
```
- Owner (root): `rwx`
- Group: `r-x`
- Others: `---`

Use:
```
ls -la
```

---

## 3. File Operations

### Copy & Move
```
cp source destination
mv oldname newname
```

### File Type
```
file filename
```

### File Metadata
```
stat filename
```
Shows:
- Access time
- Modified time
- Change time
- UID / GID
- File size

---

## 4. Linux File System & Inodes

- Linux stores files in a **systematic structure**
- Each file is assigned an **inode number**
- Inode contains metadata (not filename)
- Inodes are **limited**

Check inode number:
```
ls -i
```

---

## 5. Directory Commands

```
mkdir   # create directory
rmdir   # remove empty directory
cd      # change directory
pwd     # present working directory
rm -rf  # force remove files/directories
```

---

## 6. Soft Link vs Hard Link

### Hard Link
- Shares the **same inode number**
- Cannot be created for directories
- Exists even if original file is deleted

Create hard link:
```
ln /path/to/file hardlink_name
```

### Soft Link (Symbolic Link)
- Has a **different inode**
- Can be created for directories
- Breaks if original file is deleted

Create soft link:
```
ln -s /path/to/file softlink_name
```

---

## 7. Disk & Storage Commands

### Disk Usage
```
df -h    # disk usage
df -i    # inode usage
du -sh * # directory-wise usage
```

### Block Devices
```
lsblk
```

---

## 8. LVM (Logical Volume Manager)

- Used for managing physical and logical storage
- Allows **online disk expansion**
- Can attach storage **without stopping services** (web server, DB)

---

## 9. File System Table

```
cat /etc/fstab
```
- Defines file systems
- Mount points
- Persistent mounts after reboot

---

## 10. Important Linux Directories

| Directory | Purpose |
|--------|--------|
| `/etc` | Configuration files |
| `/home` | User home directories |
| `/bin` | User binary commands |
| `/sbin` | System binaries |
| `/boot` | Boot loader & kernel files |
| `/tmp` | Temporary files |
| `/dev` | Device files |
| `/proc` | Virtual process files |
| `/var` | Logs & variable data (**important for DevOps**) |
| `/usr` | User applications & libraries |
| `/mnt` | Temporary mount points |

---

## 11. `ls -la` vs `ls -lrt`

- `ls -la` → List all files including hidden with permissions
- `ls -lrt` → List files sorted by **time**, oldest first

---

## 12. Find Command (Housekeeping)

Used to clean old files and keep OS healthy.

### Find file by name
```
find /var -name "*lastlog*"
```

### Delete logs older than 7 days
```
find /var -name "*_log*" -mtime +7 -delete
```

⚠️ Use `-delete` carefully in production.

---

---

📘 *Perfect for Linux fundamentals, DevOps interviews, and GitHub documentation.*
