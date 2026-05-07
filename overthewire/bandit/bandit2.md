# Level 2 → Level 3

## Objective
Read a file with spaces in its filename.

## Key Concept
Spaces in filenames are interpreted as separators by the shell unless escaped properly.

## Command Used

```bash
cat ./spaces\ in\ this\ filename
```

## Explanation
The backslash `\` escapes each space character so the shell treats the filename as a single argument.

Another valid approach would be:

```bash
cat "./spaces in this filename"
```

## What I Learned
- Spaces in filenames must be escaped or quoted
- Linux shells split commands based on spaces
- Quotation marks can simplify handling complex filenames