# Bandit Level 14 → Level 15

## Objective

Use the password from Level 14 to connect to the service on `localhost` port `30000` and obtain the password for Level 15.

## Commands Used

```bash
nc localhost 30000
```

Paste the Level 14 password when prompted and press **Enter**.

## Explanation

- Connected to the service running on `localhost` at port `30000` using `nc`.
- Entered the current level's password.
- The service verified the password and returned the password for **Bandit Level 15**.

## Command Explained

### `nc`

**Purpose:** Netcat is a networking utility used to connect to TCP/UDP services, send data, and test network connections.

**Syntax**

```bash
nc <host> <port>
```

**Example**

```bash
nc localhost 30000
```

Connects to the service running on port `30000` of the local machine.

## Key Learning Points

- `localhost` refers to the local machine (`127.0.0.1`).
- Services communicate over specific network ports.
- `nc` is a simple tool for interacting with network services.
