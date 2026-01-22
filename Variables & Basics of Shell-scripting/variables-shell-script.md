# Linux Environment Variables & Shell Scripting – Practical Guide

This document provides a clean, professional overview of **environment variables**, **shell scripting basics**, **archiving logs**, and **positional parameters**. It is designed for Linux learners, DevOps beginners, and GitHub documentation.

---

## Environment Variables

Environment variables are used to store system-wide or user-specific values that can be accessed by applications and shell scripts.

### Types of Environment Variables

1. **Temporary Variables**

   * Available only for the current shell session
   * Lost after logout or terminal close

2. **Permanent Variables**

   * Persist across reboots and sessions
   * Stored in configuration files

---

### Ways to Store Environment Variables Permanently

| File              | Scope        | Description                               |
| ----------------- | ------------ | ----------------------------------------- |
| `/etc/profile`    | All users    | Loads variables for all users system-wide |
| `~/.bashrc`       | Current user | Executed for every interactive shell      |
| `~/.bash_profile` | Current user | Executed during login shells              |

> **Best Practice:**
>
> * Use `/etc/profile` for global variables
> * Use `~/.bashrc` or `~/.bash_profile` for user-specific variables

---

## Shell Scripting Basics

A **shell script** is a file containing a series of Linux commands executed sequentially.

### Running a Shell Script

```bash
./script_name.sh
```

or

```bash
bash script_name.sh
```

---

### Shebang Line

Every shell script should start with a **shebang line**:

```bash
#!/bin/bash
```

* Informs the system which shell interpreter to use
* Multiple shells exist (`bash`, `sh`, `zsh`), so defining one is a best practice

---

## Archiving and Compressing Logs

Archived logs are commonly used for **backup and storage management**.

---

### ZIP Utility

```bash
zip text.zip file1 file2
```

* Creates a ZIP archive

```bash
zip -r archive.zip directory/
```

* Recursively archives directories

---

### GZIP Utility

```bash
gzip filename
```

* Compresses (encrypts) a file

```bash
gunzip filename.gz
```

* Decompresses (decrypts) a file

---

### TAR Utility (Archiving Multiple Files and Directories)

#### Create Archive

```bash
tar -cvf file-name.tar file1 file2 directory/
```

* `c` → create
* `v` → verbose
* `f` → file name

#### Extract Archive

```bash
tar -xvf file-name.tar
```

* `x` → extract

---

## Positional Parameters in Shell Script

Positional parameters are used to access arguments passed to a shell script.

| Parameter | Description                          |
| --------- | ------------------------------------ |
| `$0`      | Name of the shell script             |
| `$#`      | Total number of arguments            |
| `$@`      | All arguments passed                 |
| `$?`      | Exit status of last executed command |

> Exit status `0` indicates success, non-zero indicates failure.

---

## Taking User Input in Shell Script

```bash
read variable_name
```

Example:

```bash
echo "Enter your name:"
read name
echo "Hello, $name"
```

---

## Summary

* Environment variables can be temporary or permanent
* Shell scripts automate Linux tasks
* Archiving tools (`zip`, `gzip`, `tar`) help manage backups
* Positional parameters enable dynamic script execution
