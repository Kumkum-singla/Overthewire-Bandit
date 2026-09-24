## Level 32 → Level 33

### Objective

The level starts with the **Uppercase Shell**, which converts commands entered by the user to uppercase.

After logging in:

```bash
ssh bandit32@bandit.labs.overthewire.org -p 2220
```

The shell displayed:

```text
WELCOME TO THE UPPERCASE SHELL
```

### Understanding the problem

Normal commands such as:

```bash
ls
```

are converted to:

```text
LS
```

Since `LS` is not the normal lowercase `ls` command, it does not execute as expected.

### Escape the Uppercase Shell

Use:

```bash
$0
```

`$0` refers to the shell itself. Because the uppercase conversion does not change `$0`, it can be used to start a normal shell.

After getting the normal shell, verify the current user:

```bash
whoami
```

Then retrieve the password for the next level:

```bash
cat /etc/bandit_pass/bandit33
```

### Key concepts learned

- Shell behavior
- Environment variables
- `$0`
- Escaping a restricted/custom shell
- Linux command execution
- Password-file conventions in the Bandit environment

---