# Level 11 → Level 12

## Objective
Decode the contents of `data.txt`, which were encoded using ROT13.

## Key Concept
ROT13 is a substitution cipher that rotates alphabetic characters by 13 positions.

## Command Used

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

## Explanation
- `cat data.txt` displays the contents of the file
- `tr` translates characters from one set into another
- `'A-Za-z'` represents all uppercase and lowercase letters
- `'N-ZA-Mn-za-m'` shifts each letter by 13 places

This decodes the ROT13-encoded text and reveals the password.

## What I Learned
- ROT13 is a basic encoding technique
- `tr` is useful for character substitution
- Simple encodings appear often in cybersecurity challenges