# 🧠 Memory Management in Linux

## Checking RAM Usage

### free -m
Displays memory usage in megabytes.

```bash
free -m
```

### Shows:
- Total RAM
- Used memory
- Available memory
- Swap usage

---

## Swap Memory

Swap is disk space used as **extended memory** when physical RAM is exhausted.

### Key Points:
- Acts as an extension of RAM
- Created from disk or cloud volumes (EBS)
- Slower than RAM
- Prevents system crashes during high memory usage

---

## Why Swap Is Needed
When RAM usage reaches 100%, Linux moves inactive memory pages to swap to maintain system stability.

---

## Check Swap Usage

```bash
swapon --show
```

```bash
free -m
```
