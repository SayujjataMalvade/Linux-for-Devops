# AWK – Column-Based Text Processing Guide

`awk` is a powerful text-processing tool used primarily for **column-wise data manipulation**. It works well with structured text files such as logs, CSVs, or space-delimited files and is widely used in Linux/Unix shell scripting.

This document provides a professional, GitHub-ready reference for common `awk` use cases.

---

## Basic Syntax

```bash
awk 'pattern { action }' filename
```

* If no pattern is specified, the action is applied to **every line**.
* Fields (columns) are accessed using `$1`, `$2`, `$3`, etc.

---

## Print Specific Columns

### Print First Column

```bash
awk '{print $1}' demo.txt
```

* Prints the **first column** from each line of `demo.txt`.
* Default field separator is **whitespace**.

---

### Print Multiple Columns and Save to File

```bash
awk '{print $2, $9}' demo.txt > text.txt
```

* Extracts the **2nd and 9th columns**.
* Redirects output to `text.txt`.
* Original file remains unchanged.

---

## Change Field Separator

### Use Dot (`.`) as Field Separator

```bash
awk -F. '{print $2}' demo.txt
```

* `-F.` sets `.` as the field delimiter.
* Prints the column **after the dot**.

Example input:

```
user.name
```

Output:

```
name
```

---

## Perform Calculations on Columns

### Sum Values of a Column

```bash
awk '{sum += $6} END {print sum}' demo.sh
```

* Adds all values from the **6th column**.
* `END` block runs after the last line is processed.
* Useful for calculating totals (e.g., file sizes, salaries, usage stats).

---

## Common Use Cases

* Column-based data extraction
* Log file analysis
* Report generation
* Data transformation in shell scripts
* Aggregation (sum, average, count)

---

## Best Practices

* Always verify column positions before processing
* Combine `awk` with `grep`, `sed`, and pipes for powerful workflows
* Use meaningful variable names for readability




