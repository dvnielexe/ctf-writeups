# Level 12 → Level 13

## Objective
Extract the password from a hexdump file that has been compressed multiple times.

## Key Concept
File analysis and recursive decompression are important Linux and cybersecurity skills.

## Commands Used

Create a temporary working directory:

```bash
mkdir /tmp/bandit12
```

Copy the file into the directory:

```bash
cp data.txt /tmp/bandit12
```

Move into the directory:

```bash
cd /tmp/bandit12
```

Reverse the hexdump:

```bash
xxd -r data.txt data.bin
```

Identify file types during extraction:

```bash
file data.bin
```

Extract compressed files using the appropriate tools:

```bash
gzip -d
```

```bash
bzip2 -d
```

```bash
tar -xf
```

## Explanation
The challenge involved repeatedly identifying and extracting compressed files.

The process followed this cycle:
1. Identify the file type using `file`
2. Use the correct extraction tool
3. Repeat until the final readable file appeared

`xxd -r` converted the hexdump back into its original binary format before extraction began.

## What I Learned
- Hexdumps can be reversed into binary files
- `file` is extremely useful during analysis
- Compression formats include gzip, bzip2, and tar archives
- Working in `/tmp` is useful for temporary files