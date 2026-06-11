# Natas Level 5 Writeup

## Goal
Gain access by bypassing a client-side restriction.

## Analysis

The page states that you are not logged in.

Inspecting the browser cookies reveals a cookie named:

```text
loggedin=0
```

This suggests authentication status is being determined entirely from a client-controlled cookie.

## Exploitation

Modify the cookie value:

```text
loggedin=1
```

This can be done using:

- Browser Developer Tools
- Cookie Editor extensions
- Intercepting proxies such as Burp Suite

Refresh the page after changing the cookie.

## Result

The application treats the user as authenticated and displays the password for the next level.

## Lessons Learned

- Client-side cookies should not be trusted for authorization decisions.
- Authentication state must be validated on the server.
- Sensitive access checks should never depend solely on user-controlled data.