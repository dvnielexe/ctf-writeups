# Level 5 → Level 6

## Objective
Find a file with specific properties:
- Human-readable
- 1033 bytes in size
- Non-executable

## Key Concept
The `find` command can search for files using multiple conditions.

## Commands Used

Find files that are exactly 1033 bytes:

```bash
find . -size 1033c
```

Find non-executable files:

```bash
find . -type f ! -executable
```

## Explanation
- `find .` starts searching from the current directory
- `-size 1033c` searches for files that are exactly 1033 bytes
- `-type f` limits results to files only
- `! -executable` excludes executable files

Combining these filters makes it easier to identify the correct file.

## What I Learned
- `find` is one of the most powerful Linux enumeration tools
- Multiple filters can narrow search results efficiently
- File permissions are important during system analysis