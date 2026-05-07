# Level 6 → Level 7

## Objective
Find a file on the server with the following properties:
- Owned by user `bandit7`
- Owned by group `bandit6`
- Exactly 33 bytes in size

## Key Concept
The `find` command can search the entire filesystem using ownership and size filters.

## Command Used

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

## Explanation
- `find /` starts searching from the root directory
- `-user bandit7` filters files owned by the user `bandit7`
- `-group bandit6` filters files belonging to the group `bandit6`
- `-size 33c` searches for files that are exactly 33 bytes
- `2>/dev/null` suppresses permission denied errors

After locating the correct file, `cat` was used to display its contents.

## What I Learned
- `find` supports advanced filtering for enumeration
- Linux files have ownership and group permissions
- Redirecting errors helps clean terminal output