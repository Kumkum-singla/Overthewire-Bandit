# Bandit Level 30 → Level 31

## Objective

Find the password for Bandit Level 31 in the Git repository.

## Commands

```bash
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
```

Enter the Bandit 30 password when asked.

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

Check the Git tags:

```bash
git tag
```

The tag is:

```text
secret
```

Show the contents of the tag:

```bash
git show secret
```

This reveals the password for Level 31.

## Login to Level 31

```bash
ssh bandit31@bandit.labs.overthewire.org -p 2220
```

Enter the password obtained from:

```bash
git show secret
```

## Important Note

Do not use:

```bash
git show tag
```

unless there is actually a tag named `tag`.

Use:

```bash
git tag
```

to see the available tag names, then:

```bash
git show <tag-name>
```

For this level:

```bash
git show secret
```

## What I Learned

- Git repositories can contain tags.
- `git tag` lists available tags.
- `git show <tag-name>` displays the object referenced by a tag.
