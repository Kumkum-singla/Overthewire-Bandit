# Bandit Level 26 → Level 27

## Objective

Use the SUID program `bandit27-do` to execute a command as `bandit27` and retrieve the password for Level 27.

## Step 1 — List the files

After logging in as `bandit26`:

```bash
ls -la
```

Look for:

```text
bandit27-do
```

## Step 2 — Check permissions

```bash
ls -l bandit27-do
```

The program has SUID permissions, allowing it to execute commands with `bandit27` privileges.

## Step 3 — Test it

```bash
./bandit27-do id
```

The output should show that the command is running as `bandit27`.

## Step 4 — Get the password

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

The output is the password for `bandit27`.

## Commands Used

```bash
ls -la
ls -l bandit27-do
./bandit27-do id
./bandit27-do cat /etc/bandit_pass/bandit27
```
