# Level 4 → Level 5

## Objective
Locate the only human-readable file inside a directory containing multiple files.

## Key Concept
The `file` command identifies file types and formats.

## Command Used

```bash
file ./-file07
```

## Explanation
The `file` command checks the contents of a file and identifies its type.

The correct file returned:

```text
ASCII text
```

indicating it was human-readable.

## What I Learned
- The `file` command is useful for reconnaissance and enumeration
- Not all files contain readable text
- ASCII text files can usually be viewed directly with `cat`