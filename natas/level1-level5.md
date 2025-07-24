## Level 1,2
### Solution
View the page source, and you’ll find the password hidden in an HTML comment or element.

## Level 3
### Solution

- Open the page source and look for image or file paths. You’ll see something like:
> files/pixel.png

Try navigating to the `/files/` directory manually in the URL. There, you may find another file like `users.txt` containing the password.


## Level 4
### Solution
The page and its source reveal nothing, so try looking for hidden paths.
- Access `robots.txt` (e.g., `http://natas4.natas.labs.overthewire.org/robots.txt`)

- It may contain entries like:
>Disallow: /s3cr3t/

Visit that folder (`/s3cr3t/`) and look for files such as `users.txt`. The password is likely inside.

## Level 5
### Solution
When you refresh the page, you see a message like:
<pre> Access disallowed. You are visiting from "http://natas4.natas.labs.overthewire.org/" while authorized users should come only from "http://natas5.natas.labs.overthewire.org/"</pre>

This means the server checks the *Referer* header.

Use a tool like **Burp Suite** or your browser’s developer tools to intercept the request and modify the *Referer* header to:
> Referer: http://natas5.natas.labs.overthewire.org/

Resend the request. The response will say:
<pre> Access granted. The password for natas5 is [password] </pre>

