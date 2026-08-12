# Bandit Level 15 → Level 16

## Objective

Submit the current level password to the SSL/TLS service running on port `30001` to retrieve the password for the next level.

## Commands Used

```bash
openssl s_client -connect localhost:30001
```

After the secure connection is established, paste the current level password and press **Enter**.

## Explanation

- Connected to the SSL/TLS service running on `localhost` at port `30001` using `openssl s_client`.
- After the SSL handshake completed, entered the current Bandit 15 password.
- The server verified the password and returned the password for Bandit Level 16.

## Command Breakdown

### `openssl`

A command-line toolkit used for working with cryptography, SSL/TLS certificates, encryption, and secure network connections.

### `s_client`

Starts an SSL/TLS client and establishes a secure connection to a remote service. It is commonly used to test SSL/TLS-enabled servers and communicate with secure services from the terminal.

### `-connect`

Specifies the destination host and port in the format:

```text
hostname:port
```

In this level:

```text
localhost:30001
```

- `localhost` refers to the current machine.
- `30001` is the port where the SSL/TLS service is listening.

## Key Learning

- Some network services require SSL/TLS instead of a normal TCP connection.
- `openssl s_client` can be used to securely communicate with SSL/TLS-enabled services.
- After a secure connection is established, data can be sent and received just like a normal terminal session.
