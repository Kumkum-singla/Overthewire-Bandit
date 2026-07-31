# Bandit Level 5 → Level 6

## Objective

Find the file that meets all of the following conditions:

- Human-readable
- Exactly 1033 bytes in size
- Not executable

The file is located somewhere inside the `inhere` directory.

## Commands Used

```bash
cd inhere
```

```bash
find . -type f -size 1033c ! -executable
```

```bash
cat ./maybehere07/.file2
```


## Command Explanation

### `cd inhere`

Changes the current working directory to `inhere`.

### `find . -type f -size 1033c ! -executable`

Searches for a file that satisfies specific conditions.

- `find` → Searches for files and directories.
- `.` → Start searching from the current directory.
- `-type f` → Search only for regular files.
- `-size 1033c` → Match files that are exactly 1033 bytes (`c` = bytes).
- `! -executable` → Exclude executable files.

### `cat`

Displays the contents of the file in the terminal.

## Concepts Learned

- Recursive file searching using `find`
- Filtering by file type (`-type f`)
- Searching by exact file size (`-size`)
- Excluding files using the NOT operator (`!`)
- Reading file contents with `cat`

## Outcome

Successfully located the file matching all required conditions and retrieved the password for Bandit Level 6.
