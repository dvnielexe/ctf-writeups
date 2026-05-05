# Level 15 → Level 16

## Objective
Submit the current level password to port `30001` on `localhost` using SSL/TLS encryption.

## Key Concept
Some network services require encrypted communication instead of plain TCP connections.

## Command Used

```bash
openssl s_client -connect localhost:30001
```

After connecting, the current password was pasted into the session.

## Explanation
- `openssl s_client` creates a secure SSL/TLS connection
- `-connect localhost:30001` connects to the service running on port `30001`
- Unlike the previous level, `nc` alone would not work because the service expects encrypted communication

After sending the correct password, the server returned the password for the next level.

## What I Learned
- SSL/TLS encrypts network communication
- `openssl s_client` can interact with secure services
- Different services may require different connection methods