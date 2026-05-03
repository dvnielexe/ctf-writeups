# Level 9 → Level 10

## Objective
Find the password stored in `data.txt` among a few human-readable strings preceded by several `=` characters.

## Key Concept
The `strings` command extracts readable text from binary or non-human-readable files.

## Command Used

```bash
strings data.txt | grep "=="
```

## Explanation
- `strings data.txt` extracts readable strings from the file
- `grep "=="` filters lines containing multiple `=` characters

This narrowed the output down to a small number of possible matches, making the password easy to identify.

## What I Learned
- Some files contain a mix of binary and readable data
- `strings` is useful during file analysis and reverse engineering
- Combining commands improves efficiency during enumeration