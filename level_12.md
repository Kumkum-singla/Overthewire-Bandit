# Bandit Level 11 → Level 12

## Objective

Decode the ROT13-encoded contents of `data.txt` to find the password.

## Commands Used

```bash
cat data.txt
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## Explanation

- `cat` displays the contents of the file.
- `|` (pipe) passes the output of one command as the input to another.
- `tr` translates characters from one set with the corresponding characters in another set.
- `A-Z` represents all uppercase letters.
- `a-z` represents all lowercase letters.
- `N-ZA-M` is the uppercase alphabet rotated by 13 positions.
- `n-za-m` is the lowercase alphabet rotated by 13 positions.

## New Command Learned

### tr

Translates or replaces characters from one set with corresponding characters from another.

#### Syntax

```bash
tr 'SET1' 'SET2'
```

#### Decode ROT13

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

#### Example

```bash
echo "hello" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Output

```text
uryyb
```

## Key Learning

ROT13 (Rotate by 13) is a simple substitution cipher that shifts every alphabet letter by 13 positions. Since the English alphabet has 26 letters, applying ROT13 twice restores the original text. The `tr` command performs this translation by replacing each character in the first set with its corresponding character in the second set.
````

