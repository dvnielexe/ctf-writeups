# Level 16 → Level 17

## Objective
Find the correct SSL-enabled service between ports `31000` and `32000` and retrieve the credentials for the next level.

## Key Concept
Port scanning helps identify open services and determine which ports are running specific protocols.

## Commands Used

Scan ports:

```bash
nmap localhost -p 31000-32000
```

Connect to the SSL-enabled port:

```bash
openssl s_client -connect localhost:31790
```

## Explanation
- `nmap` scans the specified range of ports on localhost
- The scan revealed which ports were open
- One of the open ports supported SSL/TLS communication
- `openssl s_client` was then used to connect securely to that port

After sending the current password, the service returned a private SSH key for the next level.

The SSH key was saved locally and used to authenticate as `bandit17`.

## Additional Commands

Set secure permissions for the SSH key:

```bash
chmod 600 bandit17.key
```

Login using the key:

```bash
ssh -i bandit17.key bandit17@bandit.labs.overthewire.org -p 2220
```

## What I Learned
- `nmap` is useful for service discovery
- Open ports may run different protocols
- SSH keys can be used instead of passwords
- File permissions matter when handling private keys