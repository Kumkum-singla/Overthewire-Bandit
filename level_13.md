````markdown
# Bandit Level 12 → Level 13

## Objective

The password for the next level is stored in `data.txt`, which is a hexdump of a file that has been repeatedly compressed using different formats.

## Commands Used

```bash
tempdir=$(mktemp -d)
cd "$tempdir"
cp ~/data.txt .
xxd -r data.txt > data
file data
mv data data.gz
gzip -d data.gz
file data
mv data data.bz2
bzip2 -d data.bz2
file data
tar -xf data
file data5.bin
tar -xf data5.bin
file data6.bin
mv data6.bin data6.bz2
bzip2 -d data6.bz2
# Continue checking the file type with `file`
# and extract/decompress accordingly until
# the final file is plain text.
cat data8
```

## Explanation

### `mktemp -d`

Creates a unique temporary directory. This provides a safe workspace to extract files without modifying the original `data.txt`.

```bash
tempdir=$(mktemp -d)
```

### `cd`

Changes the current working directory to the temporary directory.

```bash
cd "$tempdir"
```

### `cp`

Copies the original `data.txt` from the home directory into the temporary directory.

```bash
cp ~/data.txt .
```

- `~` represents the current user's home directory.
- `.` represents the current directory.

### `xxd -r`

Reverses the hexadecimal dump back into its original binary format.

```bash
xxd -r data.txt > data
```

- `-r` means reverse the hexdump.
- `>` redirects the reconstructed binary into a new file named `data`.

### `file`

Identifies the actual type of a file instead of relying on its filename or extension.

```bash
file data
```

The output determines which command should be used next.

Examples:

- `gzip compressed data`
- `bzip2 compressed data`
- `POSIX tar archive`
- `ASCII text`

### `mv`

Some decompression tools expect files to have the correct extension. Rename the file before extracting.

```bash
mv data data.gz
mv data data.bz2
```

### `gzip -d`

Decompresses a gzip-compressed file.

```bash
gzip -d data.gz
```

The `-d` option stands for **decompress**.

### `bzip2 -d`

Decompresses a bzip2-compressed file.

```bash
bzip2 -d data.bz2
```

### `tar -xf`

Extracts the contents of a tar archive.

```bash
tar -xf data
```

Options:

- `-x` → Extract files
- `-f` → Use the specified archive file

After extraction, a new file (for example, `data5.bin`) is created. Run `file` on the newly extracted file and continue the process.

### `cat`

Displays the contents of the final ASCII text file.

```bash
cat data8
```

This reveals the password for Bandit Level 13.

## Key Learning

This level demonstrates how to work with multiple file formats by repeatedly identifying a file's type and using the appropriate extraction or decompression tool.

The general workflow is:

1. Convert the hexdump back into a binary file using `xxd -r`.
2. Identify the file type with `file`.
3. Extract or decompress it using the correct command.
4. Repeat until the file becomes plain ASCII text.
5. Display the password using `cat`.

## Commands Learned

- `mktemp -d`
- `cp`
- `xxd -r`
- `file`
- `mv`
- `gzip -d`
- `bzip2 -d`
- `tar -xf`
- `cat`
````
