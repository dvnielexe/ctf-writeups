# Natas Level 4 Writeup

## Goal
Access the next level by bypassing the referrer check.

## Analysis

Visiting the challenge page displays a message indicating that access is only granted if the request comes from a specific URL.

This suggests the application validates the `Referer` HTTP header before revealing the password.

## Exploitation

Intercept the request or send a custom request with the required `Referer` header.

Example:

```bash
curl -H "Referer: http://natas5.natas.labs.overthewire.org/" \
-u natas4:<current_password> \
http://natas4.natas.labs.overthewire.org/
```

The server accepts the request because the supplied `Referer` matches the expected value.

## Result

The page reveals the password for the next level.

## Lessons Learned

- HTTP headers should never be trusted for authentication.
- Users can freely modify headers such as `Referer`.
- Access controls must be enforced server-side using proper authentication mechanisms.