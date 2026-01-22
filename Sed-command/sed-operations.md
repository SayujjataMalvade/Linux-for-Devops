# Sed (Stream Editor) – Quick Guide

`sed` is a **stream editor** used to perform basic text transformations on an input stream (a file or input from a pipeline). It allows you to edit files **without opening them in an interactive editor** like `vi` or `nano`.

This guide provides commonly used `sed` commands with clear explanations and examples, suitable for reference in a GitHub repository.

---

## Basic Syntax

```bash
sed 'command' filename
```

> By default, `sed` **does not modify the original file**. It only prints the result to standard output.

---

## Replace Text in a File

### Replace First Occurrence (Preview Only)

```bash
sed 's/error/test/' demo.txt
```

* Replaces the **first occurrence** of the word `error` with `test` on each line.
* Changes are shown on the terminal only.
* The original file remains unchanged.

---

### Replace and Save Changes to File

```bash
sed -i 's/error/test/' demo.txt
```

* The `-i` option edits the file **in place**.
* The original file is permanently modified.

---

### Replace All Occurrences (Global)

```bash
sed -i 's/error/test/g' demo.txt
```

* The `g` flag ensures **all occurrences** of `error` are replaced with `test` on every line.

---

## Print Specific Lines

### Print Lines 2 to 5

```bash
sed -n '2,5p' demo.txt
```

* `-n` suppresses automatic printing.
* `2,5p` prints only lines **2 through 5**.

---

## Delete Lines

### Delete Line Number 3 (Preview)

```bash
sed '3d' demo.txt
```

* Deletes line 3 from the output.
* The original file remains unchanged.

### Delete Line Number 3 and Save

```bash
sed -i '3d' demo.txt
```

* Permanently deletes line 3 from the file.

---

## Copy Data from One File to Another

```bash
sed 's/error/test/g' source.txt > destination.txt
```

* Applies the transformation on `source.txt`.
* Writes the modified output to `destination.txt`.
* The source file remains unchanged.

---

## Common Use Cases

* Search and replace text in large files
* Edit configuration files programmatically
* Extract specific lines or ranges
* Delete unwanted lines
* Transform file content during shell scripting

---

## Notes

* Always test commands **without `-i`** before applying permanent changes.
* Some systems (like macOS) require a backup extension:

```bash
sed -i.bak 's/error/test/g' demo.txt
```


