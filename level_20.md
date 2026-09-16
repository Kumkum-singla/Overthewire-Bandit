# Bandit Level 19 → 20

## Goal

The password for the next level can be obtained by using a setuid binary called `bandit20-do`.

## Steps

First, list the files in the home directory:

```bash
ls -la
```

We can see a file named `bandit20-do`.

Next, check what type of file it is:

```bash
file bandit20-do
```

The output shows that it is a setuid executable.

Now run the binary:

```bash
./bandit20-do
```

It shows that the binary can be used to execute a command as `bandit20`.

The password for `bandit20` is stored in `/etc/bandit_pass/bandit20`.

We can use `cat` through the setuid binary to read the password:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

The command displays the password for `bandit20`.

Finally, use that password to log in to the next level:

```bash
ssh bandit20@bandit.labs.overthewire.org -p 2220
```

## Explanation

The important concept in this level is **SUID (Set User ID)**.

A SUID executable runs with the permissions of its owner instead of the permissions of the user who executes it.

The `bandit20-do` binary is owned by `bandit20`. Therefore, when we use it to execute a command, that command runs with `bandit20`'s permissions.

Normally, `bandit19` would not be able to read the `bandit20` password file. However, `bandit20-do` allows us to execute `cat` with `bandit20`'s permissions:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

This allows us to obtain the password for the next level.

## Key Learning

- `ls -la` → Lists files along with their permissions.
- `file` → Identifies the type of a file.
- `./` → Executes a file from the current directory.
- `cat` → Displays the contents of a file.
- **SUID** → Allows an executable to run with the permissions of its owner.
- SUID binaries can sometimes allow users to perform actions they normally would not have permission to perform.
