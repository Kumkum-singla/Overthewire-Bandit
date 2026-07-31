# Bandit Level 1 → Level 2

## Objective

Retrieve the password for Bandit Level 2 from the file named `-`.

## Command Used

```bash
cat ./-
```

## What I Learned

- Some filenames can start with `-`.
- Prefixing the filename with `./` tells the shell that it is a file in the current directory.
- `./` refers to the current working directory.

## Mistakes I Made

- I initially tried `cat -`, which did not work because `-` was interpreted as an option instead of a filename.
- I was confused about why `./` was required.
- I learned the difference between a command option and a filename.

## Key Takeaway

When a filename starts with `-`, use `./filename` (or another valid path) so Linux treats it as a filename instead of a command option.
