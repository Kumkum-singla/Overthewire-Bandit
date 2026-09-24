# Bandit Level 29 → Level 30

## Goal

Find the password for `bandit30`.

## Step 1: Create a temporary working directory

I solved this level from my own Kali machine, so the Git repository was cloned from the local Kali terminal.

```bash
mktemp -d
```

Example:

```text
/tmp/tmp.qT9hkNHQlP
```

Then:

```bash
cd /tmp/tmp.qT9hkNHQlP
```

## Step 2: Clone the repository

Run this from the **Kali machine**, not from inside the `bandit29@bandit` SSH session:

```bash
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
```

Enter the `bandit29` password when prompted.

> If you try to clone using `localhost:2220` while logged into the Bandit server, the server blocks the connection because localhost SSH connections are not allowed.

## Step 3: Enter the repository

```bash
cd repo
```

Check the files:

```bash
ls -la
```

Read the README:

```bash
cat README.md
```

The password is not in the current branch.

## Step 4: Check the branches

```bash
git branch -a
```

This shows the branches available in the repository.

The important branch is:

```text
remotes/origin/dev
```

## Step 5: Switch to the dev branch

```bash
git checkout dev
```

Then check the README again:

```bash
cat README.md
```

The password for `bandit30` can be found in the `dev` branch.

## Step 6: Log in to Bandit 30

After obtaining the password:

```bash
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

Enter the password found in the repository.

## Commands Used

```bash
mktemp -d
cd /tmp/<your-directory>
git clone ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
cd repo
ls -la
cat README.md
git branch -a
git checkout dev
cat README.md
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

## What I Learned

- Git repositories can contain multiple branches.
- The required information may not be present in the current branch.
- `git branch -a` can be used to view local and remote branches.
- `git checkout dev` switches to the `dev` branch.
- When working with the OverTheWire Git repositories, cloning from my own Kali machine avoids the server's localhost SSH restriction.
