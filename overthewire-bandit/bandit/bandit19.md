# Level 19 → Level 20

## Objective
Use the setuid binary in the home directory to retrieve the password for the next level.

## Key Concept
A setuid binary runs with the permissions of the file owner instead of the current user.

## Commands Used

List files in the directory:

```bash
ls -l
```

Run the binary without arguments:

```bash
./bandit20-do
```

Use the binary to read the password file:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

## Explanation
The home directory contained a binary named `bandit20-do`.

Running it without arguments displayed usage instructions showing that it could execute commands as another user.

The file had the setuid permission bit enabled, meaning commands executed through it would run with the privileges of `bandit20`.

Using the binary with `cat` allowed access to the protected password file.

## What I Learned
- Setuid binaries can temporarily elevate privileges
- File permissions are an important Linux security concept
- Executables should always be inspected before use
- Privilege escalation concepts are common in cybersecurity