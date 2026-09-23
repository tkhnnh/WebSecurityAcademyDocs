Link : [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)
Difficulty : Apprentice

# Definition
Reflected XSS  is a web application vulnerability where a malicious payload got injected directly to via the HTTP request and immediately response back.

# How to trigger Reflected XSS in this room
## Reference 
[HTML JavaScript](https://www.w3schools.com/html/html_scripts.asp)


With the above resource, I will use HTML Javascript to execute XSS in this lab with the payload
```
<script>alert(1)</script>
```

Since the site does not sanitize the input which means when I insert the payload via HTTP request the server will interpret the payload as part of the HTML page and execute it.
<img width="1497" height="742" alt="Screenshot 2026-09-23 at 11 31 43 pm" src="https://github.com/user-attachments/assets/b43e3f7b-b532-42f1-b0f4-7f84cf60107d" />

Then I will see the result, which tells me that I successfully execute Reflected XSS in this lab
<img width="1490" height="907" alt="Screenshot 2026-09-23 at 11 33 09 pm" src="https://github.com/user-attachments/assets/2157df95-b1ef-4448-b0bd-76d37838ec97" />

Happy Hacking!@#!
