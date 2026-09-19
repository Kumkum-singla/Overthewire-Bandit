# Bandit Level 25 → Level 26

## Objective

Use the SSH private key `bandit26.sshkey` to log in as `bandit26` and retrieve the password for Level 26.

## Step 1 — Copy the SSH key

From your Kali/client machine:

```bash
scp -P 2220 bandit25@bandit.labs.overthewire.org:~/bandit26.sshkey /tmp/bandit26.key
```

Set permissions:

```bash
chmod 600 /tmp/bandit26.key
```

> Run these commands from your own Kali machine, not from inside the Bandit server.

## Step 2 — Shorten the terminal

Before connecting, run:

```bash
stty rows 5 cols 80
```

This makes the terminal only 5 rows high, so the restricted `more` program opens Vim instead of immediately exiting.

## Step 3 — Log in

```bash
ssh -i /tmp/bandit26.key bandit26@bandit.labs.overthewire.org -p 2220
```

When the `more` screen appears, press:

```text
v
```

This opens Vim.

## Step 4 — Read the password

If Vim shows Visual mode, press:

```text
Esc
```

Then type:

```vim
:e /etc/bandit_pass/bandit26
```

Press Enter.

The displayed password is the password for `bandit26`.

## Troubleshooting

### `error in libcrypto`

Copy the key again:

```bash
scp -P 2220 bandit25@bandit.labs.overthewire.org:~/bandit26.sshkey /tmp/bandit26.key
```

Then:

```bash
chmod 600 /tmp/bandit26.key
```

### Localhost warning

Do not SSH from inside the Bandit server. Exit to your Kali terminal and run:

```bash
stty rows 5 cols 80
ssh -i /tmp/bandit26.key bandit26@bandit.labs.overthewire.org -p 2220
```
