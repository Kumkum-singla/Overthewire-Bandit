# Bandit Level 28 → 29

## Goal

The password for the next level is stored in a Git repository. The current `README.md` contains a redacted version of the password.

## Step 1: Create a temporary working directory

The Bandit home directory was not writable, so I used `/tmp` on my Kali machine.

```bash
cd /tmp
mkdir bandit28
cd bandit28
```

## Step 2: Clone the Git repository

From my Kali machine:

```bash
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
```

When prompted about the SSH host key, I entered:

```text
yes
```

Then I entered the Bandit 28 password.

## Step 3: Enter the repository

```bash
cd repo
```

Check the files:

```bash
ls -la
```

The repository contains:

```text
.git
README.md
```

## Step 4: Check the Git history

```bash
git log --oneline
```

The Git history showed that the README had been modified in previous commits.

## Step 5: View the previous version

The current README had the password redacted, so I checked the previous commit:

```bash
git show HEAD~1
```

The previous version of `README.md` contained the actual password for Bandit 29.

## Commands Used

```bash
cd /tmp
mkdir bandit28
cd bandit28
git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
cd repo
ls -la
git log --oneline
git show HEAD~1
```

## What I Learned

Git keeps the history of changes made to files. Even if sensitive information is removed from the latest version of a file, it may still exist in an earlier commit.

**Key concept:** Git history can reveal previously committed information.
