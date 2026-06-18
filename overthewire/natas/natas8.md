# OverTheWire Natas Level 8 → 9

## Level Goal

Find the password for Natas Level 9.

## Challenge Overview

The page presents a form asking for a secret value. Submitting random input returns:

```text
Wrong secret
```

A link labeled **View Sourcecode** reveals the server-side PHP code. The application stores an encoded secret and compares it against user input after applying an encoding function. :contentReference[oaicite:0]{index=0}

## Source Code Analysis

```php
$encodedSecret = "3d3d516343746d4d6d6c315669563362";

function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}
```

The secret is encoded in three steps:

1. Base64 encode
2. Reverse the resulting string
3. Convert to hexadecimal

To recover the original secret, we simply reverse the process. :contentReference[oaicite:1]{index=1}

## Decoding the Secret

PHP:

```php
<?php
echo base64_decode(
    strrev(
        hex2bin("3d3d516343746d4d6d6c315669563362")
    )
);
?>
```

Or using Python:

```python
import base64

encoded = "3d3d516343746d4d6d6c315669563362"

decoded = base64.b64decode(
    bytes.fromhex(encoded)[::-1]
)

print(decoded.decode())
```

Output:

```text
oubWYf2kBq
```

## Exploitation

Enter the decoded secret into the form and submit it.

The application validates the value and reveals the password for the next level. :contentReference[oaicite:2]{index=2}

## Vulnerability

This level demonstrates:

- Reversible encoding is not encryption.
- Secrets embedded in source code can often be recovered.
- Security through obscurity is ineffective.

## Key Takeaway

Whenever an application reveals both the encoded value and the encoding algorithm, an attacker can often reverse the process and recover the original secret.