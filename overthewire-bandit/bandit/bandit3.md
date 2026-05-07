# Level 3 → Level 4

## Objective
Find and read a hidden file in the directory.

## Key Concept
Files beginning with `.` are hidden by default in Linux.

## Commands Used

```bash
ls -a
```

```bash
cat ./...Hiding-From-You
```

## Explanation
`ls -a` lists all files, including hidden ones.

After identifying the hidden file, `cat` was used with a relative path to display its contents.

## What I Learned
- Hidden files are common in Linux systems
- `ls -a` is useful for file enumeration
- Relative paths help access files safely