# Linux User Management & Access Revocation Guide

This document explains Linux user account fields, important user-management commands, password aging, and **best practices to immediately revoke access when an employee leaves an organization**. It is written from a **DevOps / System Administrator** perspective.

---

## 1. Understanding `/etc/passwd` Entry

Example:
```
sam:x:1001:1002::/home/sam:/bin/sh
```

Field-by-field explanation:

| Field | Description |
|------|------------|
| `sam` | Username |
| `x` | Encrypted password stored in `/etc/shadow` |
| `1001` | UID (User ID) |
| `1002` | GID (Primary Group ID) |
| `` | Comment / GECOS field (Full name / nickname) |
| `/home/sam` | Home directory |
| `/bin/sh` | Login shell assigned to user |

---

## 2. `/etc/shadow` File

Command:
```
cat /etc/shadow
```

Purpose:
- Stores **encrypted passwords**
- Maintains **password aging policies**

To view password details for a specific user:
```
sudo grep sayujjata /etc/shadow
```

---

## 3. Password Aging & Expiry (`chage`)

Command:
```
chage -l username
```

Sample output:
```
Last password change            : Nov 21, 2025
Password expires                : never
Password inactive               : never
Account expires                 : never
Minimum days between change     : 0
Maximum days between change     : 99999
Warning days before expiry      : 7
```

Check account expiration:
```
sudo chage -E username
```

---

## 4. User & Group Identification

```
id username
```

---

## 5. User Management Commands

### Change Username
```
sudo usermod -l oldname newname
```

### Change Shell
```
sudo usermod -s /sbin/nologin username
```

---

## 6. Locking & Unlocking Users

### Lock
```
sudo usermod -L username
sudo passwd -l username
```

### Unlock
```
sudo usermod -U username
sudo passwd -u username
```

---

## 7. Employee Exit – Immediate Access Revocation (SOP)

### 1. Lock User
```
sudo usermod -L username
```

### 2. Expire Account
```
sudo chage -E 0 username
```

### 3. Disable Shell
```
sudo usermod -s /sbin/nologin username
```

### 4. Kill Sessions
```
who
pkill -u username
```

### 5. Backup Home
```
sudo tar -czf /backup/username_home_$(date +%F).tar.gz /home/username
```

### 6. Remove SSH Keys
```
rm -f /home/username/.ssh/authorized_keys
```

### 7. Remove Sudo Access
```
sudo deluser username sudo
sudo visudo
```

### 8. Disable Cron Jobs
```
sudo crontab -u username -l
sudo crontab -u username -r
```

### 9. Rotate Credentials
- App passwords
- DB credentials
- API tokens
- Cloud IAM keys

---

## 8. Documentation Checklist

✔ Ticket ID  
✔ Date & Time  
✔ Commands Used  
✔ Approval Reference  

---

## 9. Delete User (After Approval Only)

```
sudo userdel -r username
```

---

## 10. Summary

| Action | Command |
|------|--------|
| Lock | usermod -L |
| Disable | nologin / chage -E 0 |
| Delete | userdel -r |

### Best Practice
```
Lock → Backup → Audit → Delete
```
