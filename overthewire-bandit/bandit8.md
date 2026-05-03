# Level 8 → Level 9

## Objective
Find the only line in `data.txt` that appears exactly once.

## Key Concept
The `uniq` command identifies duplicate or unique lines, but works best on sorted input.

## Command Used

```bash
sort data.txt | uniq -u
```

## Explanation
- `sort data.txt` arranges identical lines together
- `uniq -u` displays only lines that occur once

Without sorting, `uniq` may not detect duplicates correctly because matching lines could be separated.

## What I Learned
- Commands can be chained together using pipes (`|`)
- `sort` and `uniq` are commonly paired
- Text processing is a core Linux and cybersecurity skill