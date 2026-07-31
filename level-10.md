# Bandit Level 9 → Level 10

## Objective
Find the password hidden inside a binary file.

## Commands Used

file data.txt
strings data.txt
strings data.txt | grep "=="

## Explanation

- `file` identifies the file type.
- `strings` extracts readable text from a binary file.
- `grep` filters lines containing multiple `=` characters, where the password is hidden.

## New Commands Learned

### file
Determines the type of a file.

### strings
Extracts printable strings from binary files.

### grep
Searches text matching a specific pattern.

## Key Learning

Not every file is plain text. Binary files often contain hidden readable strings that can be extracted using `strings`.
