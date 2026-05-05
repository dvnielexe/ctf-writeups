# Level 17 → Level 18

## Objective
Find the only changed line between `passwords.old` and `passwords.new`.

## Key Concept
The `diff` command compares files line by line and highlights differences.

## Command Used

```bash
diff passwords.old passwords.new
```

## Explanation
- `diff` compares both files and displays lines that differ
- The changed line in `passwords.new` contained the password for the next level

The output showed:
- A line removed from the old file
- A line added to the new file

The added line was the correct password.

## What I Learned
- `diff` is useful for identifying changes between files
- File comparison is important in system administration and cybersecurity
- Small changes in files can contain sensitive information