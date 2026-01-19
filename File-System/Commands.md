# Linux Process Management, Cron, Logs & Package Management

This document covers **process management**, **cron jobs**, **log management**, and **package management** for Linux systems. Useful for **DevOps engineers and interview preparation**.

---

## 1. Process Management

### Kill Process
Used to terminate a process forcefully.

kill -9 <PID>

Example:
kill -9 1234

- `-9` sends SIGKILL (immediate termination)

---

## 2. Process Priority

### nice
Used when starting a process to define its priority.

nice -n 5 command

- Lower value → Higher priority  
- Higher value → Lower priority

### renice
Used to change priority of a running process.

renice -n 5 -p <PID>

---

## 3. Zombie Process

### What is a Zombie Process?
- Parent process terminated
- Child process still exists
- State shown as `Z`

### Kill Zombie Process
kill -9 <PID>

Note: Correct fix is restarting the parent process.

---

## 4. Cron Job (Task Scheduling)

Cron is used to schedule automated tasks.

Open crontab:
crontab -e

### Cron Fields
minute (0–59)  
hour (0–23)  
day of month (1–31)  
month (1–12)  
day of week (0–6)

Example:
*/5 * * * * ping -c 1 google.com

---

## 5. Enable Service at Boot

systemctl enable service-name

Example:
systemctl enable nginx

---

## 6. Log Management

Logs are stored in:
cd /var/log

View logs:
tail logfile
head logfile

Custom lines:
tail -n 50 logfile
head -n 20 logfile

Read logs:
less logfile   (press q to exit)
more logfile

---

## 7. Package Management

Install packages:
yum install package-name
apt-get install package-name

Remove packages:
apt-get remove package-name


- /var/log → System logs
- yum / apt → Package management
