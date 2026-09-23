Link: [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)
Difficulty : Apprentice 

# Definition
Stored XSS, also known as Persistent XSS or Second-Order XSS, is another web application vulnerability that the request with malicious payload is being saved in the server and could be potentially triggered whenever the relevant aciton is made.

## Reference 
[HTML Javascript](https://www.w3schools.com/html/html_scripts.asp)

# Performing Stored XSS

The target will be these inputs option for the comment in a random post in the lab.
<img width="1499" height="832" alt="Screenshot 2026-09-23 at 11 40 20 pm" src="https://github.com/user-attachments/assets/479ba42d-3174-41e4-ad18-5784328607bd" />

Instead of normal string text, I will insert malicious HTML javascript payload to make a HTTP request send to the server, which means whoever click and view this post hypothetically will be triggered Stored XSS.
```
<script>alert(1)</script>
```
Directly into the comment box
<img width="1496" height="834" alt="Screenshot 2026-09-24 at 12 00 44 am" src="https://github.com/user-attachments/assets/884a55ae-854e-4212-813c-c4226539b5b4" />

<img width="1511" height="906" alt="Screenshot 2026-09-23 at 11 59 35 pm" src="https://github.com/user-attachments/assets/e66d2b4e-e3ec-48c9-973a-0d7900e8b246" />


Done Happy Hacking!@#!@3
