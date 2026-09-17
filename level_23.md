# Bandit Level 22 → Level 23

## Objective

Find the password for the next level by examining the script
`/usr/bin/cronjob_bandit22.sh`.

## Commands Used

``` bash
cat /usr/bin/cronjob_bandit22.sh
```

The script contains:

``` bash
#!/bin/bash
chmod 644 /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
cat /etc/bandit_pass/bandit22 > /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

The important part is:

``` bash
cat /etc/bandit_pass/bandit22 > /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

This means the Bandit 22 password is copied into a file in `/tmp`.

Read the file:

``` bash
cat /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

The output is the password for Bandit Level 22.

## Explanation

The cron job runs the script automatically as the `bandit22` user.

The script:

1.  Reads the password from:

``` text
/etc/bandit_pass/bandit22
```

2.  Redirects the password into a temporary file:

``` text
/tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

3.  Changes the file permissions to:

``` bash
chmod 644
```

This makes the file readable by other users.

Therefore, we can simply read the temporary file using:

``` bash
cat /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

## Command Breakdown

### `cat`

Displays the contents of a file.

``` bash
cat /usr/bin/cronjob_bandit22.sh
```

Displays the cron job script.

``` bash
cat /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

Displays the password stored in the temporary file.

### `>`

Redirects command output into a file.

``` bash
cat /etc/bandit_pass/bandit22 > /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

This takes the password from `/etc/bandit_pass/bandit22` and writes it
into the temporary file.

### `chmod 644`

Changes the permissions of the file.

``` bash
chmod 644 /tmp/t7M5XXXXXXXXXXXXXXXXXXXX
```

`644` means:

``` text
Owner  → read + write
Group  → read
Others → read
```

Therefore, other users can read the file.

## Key Learning

-   Cron jobs can automatically execute scripts.
-   Always inspect cron job scripts to understand what they do.
-   Output redirection using `>` can write command output to a file.
-   File permissions determine who can read or modify a file.
-   A world-readable temporary file can expose sensitive information.
