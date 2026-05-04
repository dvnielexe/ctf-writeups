# Level 14 → Level 15

## Objective
Submit the current level password to a service listening on port `30000`.

## Key Concept
Network services can listen on specific TCP ports for incoming connections.

## Command Used

```bash
nc localhost 30000
```

After connecting, the current password was pasted into the session.

## Explanation
- `nc` (Netcat) is a networking utility used to communicate with TCP/UDP services
- `localhost` refers to the current machine
- `30000` is the target port number

Once connected, submitting the correct password returned the password for the next level.

## What I Learned
- Services communicate through ports
- Netcat is useful for interacting with network services
- Basic networking knowledge is important in cybersecurity