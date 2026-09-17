# Bandit Level 21 → Level 22

## Goal

Find the password for `bandit22`.

## Steps

First, check the cron job:

```bash
cat /etc/cron.d/cronjob_bandit22
```

The cron job runs:

```bash
/usr/bin/cronjob_bandit22.sh
```

Read the script:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

The script contains:

```bash
#!/bin/bash
chmod 644 /tmp/t706ldsS90RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t706ldsS90RqQh9aMcz6ShpAoZKF7fgv
```

The script copies the `bandit22` password into a temporary file in `/tmp`.

Read the file:

```bash
cat /tmp/t706ldsS90RqQh9aMcz6ShpAoZKF7fgv
```

This gives the password for `bandit22`.

## Key Concept

Cron jobs can automatically execute commands at scheduled intervals. Here, the cron job runs a script as `bandit22`, which copies the password into a file that we can read.
