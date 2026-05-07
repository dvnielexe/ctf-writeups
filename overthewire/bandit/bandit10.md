# Level 10 → Level 11

## Objective
Decode the base64-encoded contents of `data.txt`.

## Key Concept
Base64 is an encoding format commonly used to represent binary data as readable text.

## Command Used

```bash
base64 -d data.txt
```

## Explanation
- `base64` is a Linux utility for encoding and decoding base64 data
- `-d` tells the command to decode the contents

The decoded output revealed the password for the next level.

## What I Learned
- Encoded data is not the same as encrypted data
- Base64 is commonly encountered in cybersecurity and web technologies
- Linux provides built-in tools for handling encoded content