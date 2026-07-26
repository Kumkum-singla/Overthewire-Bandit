# Bandit Level 7 → Level 8

## Objective
Find the password stored in `data.txt` next to the word `millionth`.

## Command Used

```bash
grep "millionth" data.txt
```

## Command Breakdown

- `grep` → Searches for matching text in a file.
- `"millionth"` → The search pattern.
- `data.txt` → The file being searched.

## Output

```text
millionth <password>
```

The string after `millionth` is the password for Bandit Level 8.

## What I Learned

- Used `grep` to search for specific text within a file.
- `grep` is much faster than reading a large file manually.
- Quotation marks are optional for a single word without spaces.