# Level 13 → Level 14

## Objective
Use the provided SSH private key to log into the next level.

## Key Concept
SSH key authentication allows secure login without using passwords.

## Commands Used

Display the private key:

```bash
cat sshkey.private
```

Login using the SSH key:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

Read the password for the next level:

```bash
cat /etc/bandit_pass/bandit14
```

## Explanation
- `-i sshkey.private` tells SSH which private key to use
- `localhost` refers to the current machine
- After authenticating as `bandit14`, the password could be read from `/etc/bandit_pass/bandit14`

## What I Learned
- SSH supports key-based authentication
- Private keys must be protected carefully
- `localhost` refers to the machine currently being used
- Linux systems store sensitive data with permission restrictions