# Bandit Level 17 → Level 18

## Goal

Find the password for bandit18 by comparing two files: `passwords.old` and `passwords.new`.

## Step 1: List the files

```bash
ls
```

The files were:

```text
passwords.new
passwords.old
```

## Step 2: Compare the files

```bash
diff passwords.old passwords.new
```

`diff` compares two files and shows the differences between them.

The line beginning with `>` is the line from `passwords.new`.

The new password shown in that line is the password for bandit18.

## Step 3: Log in as bandit18

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

Enter the password found using `diff`.

## What I Learned

- `ls` is used to list files.
- `diff` is used to compare two files.
- The `>` symbol in the diff output indicates a line from the second file.
