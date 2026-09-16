# Level 20 → 21

## Goal

Use the `suconnect` setuid binary to connect to a localhost port.

It checks whether the received password matches the Bandit 20 password.
If it matches, the password for Bandit 21 is sent back.

## Steps

### Terminal 1

Start a listener with `nc`:

``` bash
nc -l 1234
```
Any unused port can be used here , i chose 1234

### Terminal 2

Run `suconnect` using the same port:

``` bash
./suconnect 1234
```

### Send the Bandit 20 password

Stop the previous listener if necessary with `Ctrl+C`.

In Terminal 1, send the Bandit 20 password through `nc`:

``` bash
echo "YOUR_BANDIT20_PASSWORD" | nc -l 1234
```

Then, in Terminal 2:

``` bash
./suconnect 1234
```

If the password is correct, `suconnect` sends the Bandit 21 password
back.

## Concepts Learned

-   `nc` (Netcat)
-   TCP listening
-   Localhost communication
-   Client/server communication
-   `|` (pipe)
-   `echo`
-   Setuid binaries
