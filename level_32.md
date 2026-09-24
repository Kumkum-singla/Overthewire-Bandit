## Level 31 → Level 32

### Objective

The task was to work with a Git repository and push a file containing the required text to the remote repository.

### Steps

Clone the repository:

```bash
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
cd repo
```

Check the repository:

```bash
ls -la
cat README.md
```

The README specified creating a file named `key.txt` containing:

```text
May I come in?
```

Create the file:

```bash
echo "May I come in?" > key.txt
```

Initially, `git add key.txt` did not work because `key.txt` was ignored by `.gitignore`.

Force-add the file:

```bash
git add -f key.txt
```

Configure the Git identity for this repository:

```bash
git config user.email "bandit31@localhost"
git config user.name "bandit31"
```

Commit the file:

```bash
git commit -m "Add key"
```

Push it:

```bash
git push
```

The remote repository validated the file and displayed the password for Level 32.

### Key concepts learned

- Git repositories
- `.gitignore`
- Force-adding ignored files with `git add -f`
- Git commits
- Git push
- Git identity configuration
- Reading remote Git server responses

---