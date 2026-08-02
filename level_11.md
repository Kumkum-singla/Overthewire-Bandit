# Bandit Level 10 → Level 11

## Objective

Decode the Base64-encoded contents of `data.txt` to find the password.

## Commands Used

```bash
cat data.txt
base64 -d data.txt
```

## Explanation

- `cat` displays the contents of the file.
- `base64 -d` decodes Base64-encoded data back to its original form.

## New Command Learned

### base64

Encodes or decodes Base64 data.

#### Decode

```bash
base64 -d file
```

#### Encode

```bash
base64 file
```

## Key Learning

Base64 is an encoding method, not encryption. It converts binary data into text for safe storage and transmission and can be decoded without a secret key.