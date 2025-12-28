# 🧪 Real-World Linux Troubleshooting Scenarios

---

## Scenario 1: Server Is Slow or Unresponsive

### Commands
```bash
top
free -m
```

### Diagnosis
- High CPU usage → Check top processes
- Low available memory → Swap usage increasing

### Action
- Restart or optimize heavy processes
- Increase RAM or swap if required

---

## Scenario 2: Application Not Accessible

### Commands
```bash
netstat -tulnp
ping <server-ip>
telnet <server-ip> <port>
```

### Diagnosis
- Port not listening → Application is down
- Port listening but unreachable → Firewall or Security Group issue

---

## Scenario 3: Memory Exhaustion Issue

### Commands
```bash
free -m
swapon --show
```

### Diagnosis
- RAM fully utilized
- Swap heavily used

### Action
- Add swap space
- Optimize memory-intensive services

---

## Scenario 4: SSH Not Working

### Commands
```bash
telnet <server-ip> 22
netstat -tulnp | grep 22
```

### Diagnosis
- SSH service stopped
- Port 22 blocked by firewall

---

## Scenario 5: Identify Server OS in Cloud

### Command
```bash
hostnamectl
```

### Use Case
- Confirm AMI OS
- Verify kernel compatibility for deployments
