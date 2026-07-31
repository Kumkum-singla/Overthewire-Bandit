# Bandit Level 2 → Level 3

## Objective

Retrieve the password for Bandit Level 3 from the file named `--spaces in this filename--`.

## Command Used

```bash
cat "./--spaces in this filename--"
```

## What I Learned

- Filenames can contain spaces.
- Quotation marks preserve spaces in filenames.
- Another method is to escape each space using `\`.

## Mistakes I Made

- I repeatedly typed the filename incorrectly.
- I forgot to enclose the filename in quotes.
- I learned that the shell treats spaces as separators unless they are quoted or escaped.

## Key Takeaway

When a filename contains spaces, enclose it in quotes or escape every space with `\`.
