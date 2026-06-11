# Natas Level 7 Writeup

## Goal
Retrieve the password for the next level.

## Analysis

The application loads pages using a URL parameter:

```text
index.php?page=home
```

and

```text
index.php?page=about
```

This behavior suggests a Local File Inclusion (LFI) vulnerability.

Inspecting the source code reveals a hint pointing to the location of the password file.

## Exploitation

Use directory traversal to include the target file.

Example:

```text
http://natas7.natas.labs.overthewire.org/index.php?page=../../../../etc/natas_webpass/natas8
```

The traversal escapes the intended directory and loads the password file.

## Result

The contents of the password file are displayed, revealing the credentials for the next level.

## Lessons Learned

- Unsanitized file inclusion parameters can lead to Local File Inclusion (LFI).
- Directory traversal allows attackers to access unintended files.
- User input should be strictly validated before being used in file operations.