# Bandit Level 4 → Level 5

## Objective

Find the only **human-readable** file inside the `inhere` directory.

---

## Commands Used

```bash
cd inhere
```

```bash
file ./*
```

```bash
cat ./-fileXX
```

> Replace `-fileXX` with the file that is identified as human-readable.

---

## What I Learned

### `file` Command

The `file` command identifies the type of a file by examining its contents rather than its filename or extension.

**Syntax**

```bash
file <filename>
```

**Examples**

```bash
file notes.txt
```

```bash
file ./*
```

---

## Why `./*` Instead of `*`

Some filenames begin with a hyphen (`-`).

Using:

```bash
file ./*
```

ensures the shell treats them as file paths instead of command options.

- `.` = current directory
- `/` = path separator
- `*` = all files in the current directory

---

## Common `file` Outputs

| Output | Meaning | Human Readable |
|---------|---------|----------------|
| ASCII text | Plain text | ✅ Yes |
| UTF-8 Unicode text | Unicode text encoded in UTF-8 | ✅ Yes |
| Unicode text | Unicode text | ✅ Yes |
| empty | Empty file | ⚠️ Yes (contains nothing) |
| data | Unknown binary data | ❌ No |
| ELF 64-bit executable | Linux executable program | ❌ No |
| JPEG image data | Image file | ❌ No |
| PNG image data | PNG image | ❌ No |
| gzip compressed data | Compressed archive | ❌ No |
| bzip2 compressed data | Compressed archive | ❌ No |
| POSIX tar archive | Archive containing multiple files | ❌ No |
| symbolic link | Shortcut pointing to another file | Depends on target |

---

## Useful `file` Options

| Command | Description |
|---------|-------------|
| `file filename` | Identify a single file |
| `file ./*` | Identify every file in the current directory |
| `file -i filename` | Display MIME type and character encoding |
| `file -b filename` | Display only the file type (without filename) |
| `file -z filename` | Examine compressed files when supported |

---

## Key Takeaways

- `file` identifies file types by inspecting file contents.
- Human-readable files are usually reported as **ASCII text**, **UTF-8 Unicode text**, or **Unicode text**.
- Use `./` when filenames begin with `-` to prevent them from being interpreted as command-line options.
- `cat` displays the contents of a text file.

---

## Commands to Remember

```bash
cd inhere
```

```bash
file ./*
```

```bash
cat ./-fileXX
```