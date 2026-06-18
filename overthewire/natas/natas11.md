# OverTheWire Natas Level 11 → 12

## Level Goal

Find the password for Natas Level 12.

## Challenge Overview

The application allows users to change the page background color.

A hint on the page states:

```text
Cookies are protected with XOR encryption
```

The source code is available and reveals how the cookie is generated and processed.

## Source Code Analysis

The application stores user settings in a cookie named:

```text
data
```

The cookie is created using:

```php
setcookie("data", base64_encode(xor_encrypt(json_encode($d))));
```

When a request is received, the cookie is processed as follows:

```php
json_decode(
    xor_encrypt(
        base64_decode($_COOKIE["data"])
    ),
    true
);
```

The application expects data similar to:

```json
{
  "showpassword":"no",
  "bgcolor":"#ffffff"
}
```

The password is displayed only when:

```php
showpassword = "yes"
```

is present in the decoded data. :contentReference[oaicite:4]{index=4}

## Understanding the Vulnerability

The cookie uses XOR encryption with a repeating key.

XOR has an important property:

```text
Plaintext XOR Key = Ciphertext

Ciphertext XOR Plaintext = Key
```

Because we already know the plaintext structure of the default cookie, we can recover the encryption key by XORing the known plaintext against the decoded cookie value. :contentReference[oaicite:5]{index=5}

## Recovering the Key

1. Obtain the value of the `data` cookie.
2. URL decode it.
3. Base64 decode it.
4. XOR the result with the known plaintext JSON.

Example logic:

```php
$key = $ciphertext ^ $known_plaintext;
```

This reveals the repeating XOR key used by the application. :contentReference[oaicite:6]{index=6}

## Crafting a New Cookie

Create a new JSON object:

```json
{
  "showpassword":"yes",
  "bgcolor":"#ffffff"
}
```

Encrypt it using the recovered XOR key and Base64 encode the result.

Pseudo-process:

```text
JSON Encode
    ↓
XOR Encrypt
    ↓
Base64 Encode
    ↓
Replace Cookie
```

## Exploitation

Replace the existing `data` cookie with the newly generated value.

Refresh the page.

The application decrypts the cookie, sees:

```json
{
  "showpassword":"yes"
}
```

and reveals the password for the next level. :contentReference[oaicite:7]{index=7}

## Vulnerability

This level demonstrates:

- Weak custom cryptography
- Client-side trust issues
- Cookie tampering
- XOR key recovery using known plaintext

## Why It Works

The application assumes that encrypted data is trustworthy.

However, because the plaintext format is predictable and XOR is reversible, an attacker can recover the key and generate arbitrary valid cookies. :contentReference[oaicite:8]{index=8}

## Key Takeaway

Encryption alone does not guarantee integrity.

Sensitive authorization decisions should never rely solely on client-controlled data, even when that data is encrypted.