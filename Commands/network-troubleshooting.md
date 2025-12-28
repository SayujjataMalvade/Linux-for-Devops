# 🌐 Network & Port Troubleshooting

## Checking Open Ports and Services

### netstat -tulnp
Displays active TCP/UDP ports and associated services.

```bash
netstat -tulnp
```

### Used To:
- Identify services listening on ports
- Verify which ports are in use
- Check application exposure

---

## Connectivity Testing

### ping
Checks network connectivity.

```bash
ping <hostname_or_ip>
```

### Used To:
- Verify reachability
- Check packet loss
- Measure network latency

---

## Port Reachability Testing

### telnet
Checks whether a specific port is reachable on a remote server.

```bash
telnet <ip_address> <port>
```

### Example:
```bash
telnet 10.0.0.5 22
```

Used to verify if SSH or application ports are open.
