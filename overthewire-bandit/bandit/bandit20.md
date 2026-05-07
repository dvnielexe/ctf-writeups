# Level 20 → Level 21

## Objective
Use the provided setuid binary to connect to a local service and submit the current password.

## Key Concept
Processes can communicate over network ports using TCP connections.

## Commands Used

Start a listener on a chosen port:

```bash
nc -lvp 4444
```

Open another terminal session and run:

```bash
./suconnect 4444
```

## Explanation
The `suconnect` binary connects to a specified local port and waits for the current level password.

The process involved:
1. Starting a Netcat listener on a local port
2. Running the `suconnect` binary with that port number
3. Sending the current password through the Netcat listener

After verifying the password, the service returned the password for the next level.

## Why Two Terminals Were Needed
One terminal handled the listening service using Netcat, while the second terminal executed the `suconnect` binary.

This allowed both processes to communicate over the chosen port.

## What I Learned
- Netcat can act as both a client and a server
- Localhost services communicate through TCP ports
- Some challenges require multiple simultaneous processes
- Networking fundamentals are essential in cybersecurity