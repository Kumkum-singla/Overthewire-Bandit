# Bandit Level 8 → Level 9

## Objective

The password for the next level is stored in the file `data.txt` and is the **only line that occurs exactly once**.

---

## Commands Used

```bash
sort data.txt | uniq -u
```

---

## Command Breakdown

### `sort`

Sorts all lines in the file alphabetically so that identical lines are placed next to each other.

### `uniq`

Processes adjacent duplicate lines.

### `-u`

Prints **only** the lines that appear exactly once.

---

## Why `sort` is Required

The `uniq` command only detects duplicate lines that are adjacent. If duplicate lines are scattered throughout the file, `uniq` alone cannot identify them correctly.



## Key Learning

- `sort` arranges lines alphabetically.
- `uniq` works only with adjacent duplicate lines.
- `uniq -u` displays lines that occur exactly once.
- Piping (`|`) sends the output of one command directly as input to another.

---

## Commands Learned

```bash
sort data.txt
sort -u data.txt
sort data.txt | uniq
sort data.txt | uniq -u
```

---

## Password

**Retrieved successfully and used to access the next level.**
