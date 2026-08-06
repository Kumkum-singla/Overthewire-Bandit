# Bandit Level 13 → Level 14

## Objective

Use the SSH private key provided in Level 13 to authenticate as `bandit14` and retrieve the password for the next level.

## Steps Performed

1. Connected to `bandit13` using the password obtained from the previous level.
2. Listed the files in the home directory:
   ```bash
   ls
   ```
3. Found the file:
   ```text
   sshkey.private
   ```
4. Displayed the contents of the private key:
   ```bash
   cat sshkey.private
   ```
5. Copied the key using **Ctrl + Shift + C**.
6. Exited the Bandit server.
7. Created a new file on the local machine, pasted the copied key into it, and saved it with the `.key` extension (for example, `private.key`).
8. Changed the file permissions so that only the owner could access the key:
   ```bash
   chmod 700 private.key
   ```
9. Connected to `bandit14` using the private key:
   ```bash
   ssh bandit14@bandit.labs.overthewire.org -p 2220 -i private.key
   ```
10. After successfully logging in, displayed the password stored in the file specified by the level instructions:
    ```bash
    cat /etc/bandit_pass/bandit14
    ```
11. Copied the displayed password to use for the next level.

## Commands Used

```bash
ls
cat sshkey.private
chmod 700 private.key
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i private.key
cat /etc/bandit_pass/bandit14
```

## Command Explanation

### `chmod 700 private.key`

The `chmod` command is used to change the permissions of a file or directory.

- `7` (Owner) = **Read (4) + Write (2) + Execute (1)** = **7**
- `0` (Group) = **No permissions**
- `0` (Others) = **No permissions**

This means only the file's owner can read, modify, or execute the file, while everyone else has no access.

SSH requires private key files to have restrictive permissions because allowing other users to read the key would compromise its security. If the permissions are too open, SSH refuses to use the key and displays a **"Permissions are too open"** or **"Permission denied"** error.

## Key Learnings

- SSH can authenticate users using a private key instead of a password.
- Private keys must have restrictive permissions before SSH will accept them.
- The `chmod 700` command ensures that only the owner can access the private key.
- The `-i` option specifies which identity (private key) SSH should use for authentication.
- The `cat` command can be used to view the contents of a file, including the password file for the next Bandit level.