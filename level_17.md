# Bandit Level 16 → Level 17

## Goal

Find the port between 31000 and 32000 that provides the next level's SSH private key through an SSL/TLS connection.

## Step 1: Scan the ports

```bash
nmap -sV -p 31000-32000 localhost
```

The scan showed:

```text
31046/tcp  open  echo
31518/tcp  open  ssl/echo
31691/tcp  open  echo
31790/tcp  open  ssl/unknown
31960/tcp  open  echo
```

The correct port was `31790` because it was an SSL/TLS service and was not an echo service.

## Step 2: Connect to the SSL service

```bash
openssl s_client -connect localhost:31790
```

After the SSL connection was established, I entered the Level 16 password.

The server returned an SSH private key.

## Step 3: Save the private key

```bash
nano /tmp/bandit17.key
```

I pasted the private key into the file and saved it.

## Step 4: Set permissions

```bash
chmod 600 /tmp/bandit17.key
```

`600` gives the owner read and write permissions while giving no permissions to the group or other users.

## Step 5: Exit bandit16

```bash
exit
```

I had to exit bandit16 because OverTheWire blocks SSH connections to the server when they originate from localhost.

## Step 6: Connect directly from Kali

```bash
ssh -i /tmp/bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
```

`-i` specifies the SSH private key used for authentication.

`-p 2220` specifies the SSH port used by the Bandit server.


## What I Learned

- Port scanning with Nmap.
- Service detection with `-sV`.
- SSL/TLS connections using OpenSSL.
- SSH private-key authentication.
- Linux file permissions using `chmod`.
- Why SSH connections should be made directly from the client machine.
