# Level 18 → Level 19

## Objective
Retrieve the contents of the `readme` file even though `.bashrc` immediately logs the user out after login.

## Key Concept
SSH can execute commands directly without starting a full interactive shell session.

## Command Used

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

## Explanation
- The normal login process triggered `.bashrc`, which immediately logged the user out
- By passing a command directly to SSH, the command executed before the logout behavior could interfere
- `cat readme` displayed the password for the next level

## What I Learned
- SSH can execute remote commands directly
- Shell startup files like `.bashrc` affect login behavior
- There are multiple ways to interact with remote Linux systems