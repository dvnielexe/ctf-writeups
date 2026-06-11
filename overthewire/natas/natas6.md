# Natas Level 6 Writeup

## Goal
Find the secret value required to retrieve the next password.

## Analysis

The page contains a form requesting a secret.

Viewing the source code reveals an included file:

```php
include "includes/secret.inc";
```

Since the file path is exposed, it may be possible to access it directly.

## Exploitation

Navigate to:

```text
http://natas6.natas.labs.overthewire.org/includes/secret.inc
```

The file contains a variable holding the secret value.

Example structure:

```php
$secret = "some_secret_value";
```

Submit the discovered value through the form.

## Result

The application validates the secret and displays the password for the next level.

## Lessons Learned

- Sensitive files should not be accessible from the web root.
- Source code disclosure often leads to credential exposure.
- Never store secrets in publicly accessible locations.