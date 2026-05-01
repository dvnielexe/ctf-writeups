# Level 1 → Level 2

## Objective
Read the file named `-` in the home directory.

## Key Concept
Filenames beginning with special characters can confuse shell commands.

## Command Used

```bash
cat ./-
```

## Explanation
Using `./` specifies the current directory and prevents `cat`
from interpreting `-` as an option.

## What I Learned
- Special filenames require careful handling
- Relative paths can avoid command parsing issues