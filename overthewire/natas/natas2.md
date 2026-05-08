
---

## Level 2 — `level2.md`

```md
# Natas Level 2

## Goal
Find the password for the next level.

## Login
- Username: `natas2`
- Password: `TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI`

## Challenge
The webpage appears mostly empty except for a simple message.

## Solution
Inspecting the page source revealed the following image reference:

```html
<img src="files/pixel.png">
```

The files/ directory looks interesting, so it is accessed directly in the browser

Inside the directory was a file names `users.txt`
The password for the next level is stored in there 