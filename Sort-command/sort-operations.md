# Linux `sort` Command – Data Sorting

The `sort` command in Linux is used to **sort lines of text files**. It is widely used by **Linux administrators and DevOps engineers** for organizing data, logs, and command output.

---

## What is the `sort` Command?
- Sorts file content line by line
- Default sorting is **alphabetical (lexicographical)**
- Can sort numbers, reverse order, and more

---

## Basic Syntax

```
sort filename
```

Example:
```
sort demo.sh
```

This sorts data in **alphabetical order (A–Z, 0–9)**.

---

## Common Sort Operations

### 1. Numeric Sort

```
sort -n filename
```

- `-n` → Sorts numerically instead of alphabetically

Example:
```
10
2
30
```
Without `-n` → `10 2 30`  
With `-n` → `2 10 30`

---

### 2. Reverse Sort

```
sort -r filename
```

- `-r` → Sorts in **reverse order**

Example:
```
Z → A
9 → 0
```

---

### 3. Numeric + Reverse Sort

```
sort -nr filename
```

Sorts numbers from **highest to lowest**.

---

## DevOps Use-Cases

- Sort log files
- Organize user lists
- Analyze numerical data
- Use with pipes

Example:
```
df -h | sort -h
```

---

## Summary Table

| Option | Description |
|------|------------|
| `sort` | Alphabetical sort |
| `-n` | Numeric sort |
| `-r` | Reverse sort |
| `-nr` | Numeric reverse sort |


