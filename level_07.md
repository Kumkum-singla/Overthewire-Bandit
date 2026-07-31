# Bandit Level 6 → Level 7

## Objective
Find a file on the server that satisfies all of the following conditions:
- Owned by user `bandit7`
- Owned by group `bandit6`
- Exactly 33 bytes in size

## Commands Used

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat <file_path>
```

## Command Breakdown

### `find`
Searches for files and directories.

### `/`
Starts searching from the root directory.

### `-user bandit7`
Matches files owned by the user `bandit7`.

### `-group bandit6`
Matches files belonging to the group `bandit6`.

### `-size 33c`
Matches files that are exactly 33 bytes in size (`c` stands for bytes).

### `2>/dev/null`
Redirects error messages (such as "Permission denied") to `/dev/null`, keeping the output clean.

## Skills Learned
- Searching the filesystem with `find`
- Filtering by file owner, group, and size
- Redirecting standard error using `2>/dev/null`
