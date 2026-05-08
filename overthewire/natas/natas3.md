# Natas Level 3

## Goal
Find the password for the next level.

## Login
- Username: `natas3`
- Password: `3gqisS4Dx2uzy0RQh3bPtlzhMHxQXv9y`

## Challenge
The webpage only displays the message:

```text
There is nothing on this page
```

## Solution
Inspecting the page source revealed a small hint suggesting that even Google would not find the hidden content this time.

That pointed toward checking the `robots.txt` file, which websites use to tell search engine crawlers which paths should not be indexed

Navigating to:

http://natas3.natas.labs.overthewire.org/robots.txt

revealed a hidden directory:

/s3cr3t/

Opening the directory showed a file named:

users.txt

Accessing:

http://natas3.natas.labs.overthewire.org/s3cr3t/users.txt

revealed the password for the next level.