# Grep Command – File Analysis in Linux

`grep` is a powerful Linux command used to **search and analyze text inside files**. It is commonly used by **DevOps engineers and system administrators** for log analysis, debugging shell scripts, and troubleshooting production issues.

---

## What is Grep?
- Searches for a **specific word or pattern** inside files
- Supports case-insensitive search, line numbers, exclusions, and counting
- Widely used for **log analysis** and **script debugging**

---

## Basic Syntax

```
grep [options] pattern filename
```

Example:
```
grep error demo.sh
```

---

## Common Grep Operations

### Case-Insensitive Search
```
grep -i error demo.sh
```
- Ignores case sensitivity

---

### Count Lines Containing a Word
```
grep -ic error demo.sh
```
Shows how many lines contain `error`.

---

### Exclude Matching Lines
```
grep -v error demo.sh
```
Shows lines that do NOT contain `error`.

---

### Count Lines That Do NOT Contain a Word
```
grep -cv error demo.sh
```

---

### Case-Insensitive Exclusion Count
```
grep -icv error demo.sh
```

---

### Show Line Numbers with Matches
```
grep -in error demo.sh
```

---

## DevOps Use-Cases
- Log analysis
- Script debugging
- Production issue investigation

---

## Summary

| Option | Purpose |
|------|--------|
| -i | Ignore case |
| -c | Count lines |
| -v | Exclude matches |
| -n | Show line numbers |


