# Bandit Level 18 → Level 19

## Goal

Log in as bandit18 and find the password for bandit19.

## Problem

When logging in normally:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220
```

the password is accepted, but the connection immediately closes with:

```text
Enjoy your stay.
Connection to bandit.labs.overthewire.org closed.
```

This happens because the `.bashrc` file for bandit18 is configured to close the connection.

## Step 1: Run a command directly through SSH

Instead of starting an interactive shell, run a command during the SSH connection:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
```

Enter the bandit18 password.

The `ls` command is executed before the connection closes.

## Step 2: Find the password

The command output reveals a file containing the password for bandit19.

Read the file using:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat <filename>
```

Replace `<filename>` with the file shown by `ls`.

The output is the password for bandit19.

## What I Learned

- SSH can execute a command directly without opening an interactive shell.
- A user's shell configuration can affect an SSH session.
- `ssh user@host command` runs the specified command remotely.
- `cat` can be used to display the contents of a file.
