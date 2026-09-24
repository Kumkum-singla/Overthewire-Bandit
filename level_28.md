# Bandit Level 27 → Level 28

## Objective

Clone the Git repository for `bandit27-git` and find the password for `bandit28`.

## Step 1 — Log in to Bandit 27

```bash
ssh bandit27@bandit.labs.overthewire.org -p 2220
```

Enter the `bandit27` password.

## Step 2 — Exit the Bandit server

The Git repository must be cloned from the client machine, not from `localhost` inside the Bandit server.

```bash
exit
```

## Step 3 — Create a directory on the client machine

```bash
mkdir bandit27
cd bandit27
```

## Step 4 — Clone the repository

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

When prompted, enter the `bandit27` password.

## Step 5 — Enter the repository

```bash
cd repo
```

## Step 6 — List the files

```bash
ls -la
```

## Step 7 — Read the README

```bash
cat README
```

The README contains the password for `bandit28`.

## Important Note

Do not use:

```bash
git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
```

or:

```bash
ssh -p 2220 bandit27-git@localhost
```

The Bandit server blocks connections to/from `localhost`.

Use the external hostname and port `2220`:

```bash
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
```

## Useful Linux Command

To remove the practice directory and its contents:

```bash
rm -r bandit27
```

`rmdir` only removes empty directories, while `rm -r` can remove a directory and its contents.
