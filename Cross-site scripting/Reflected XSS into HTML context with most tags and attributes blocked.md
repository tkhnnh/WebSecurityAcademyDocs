Link: [Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)
Difficulty: Practitioner

# Recon
If a malicious input containing forbidden tags were to be inserted on the search box, an error with http code 400 would appear with a message tag not allowed

Let's enumerate which tags are allowed in this WAF by using `Intruder`
<img width="1473" height="552" alt="Screenshot 2026-10-13 at 4 57 16 pm" src="https://github.com/user-attachments/assets/38d98812-3066-427c-a242-4a7bba07a526" />


The Request of searching would look like this, for the payload, I will count on the [cheatsheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) that portswigger has already. Also, if a successful search is being completed, the result will contain Status code 200 (filter only 200 in the result to lock on the right payload)

<img width="1444" height="153" alt="Screenshot 2026-10-13 at 5 00 12 pm" src="https://github.com/user-attachments/assets/1969b70e-5ae7-4f12-9f01-13fabda987f0" />

Next, find the allowed event,
<img width="1480" height="545" alt="Screenshot 2026-10-13 at 5 00 57 pm" src="https://github.com/user-attachments/assets/6fffbe50-6c19-4efe-aa96-ba34026e1ac2" />

With the same method to filter out the result, I choose `onresize` because the specs say that no user interaction involved.

# Action
Let's go to the exploit server and craft out payload, in the body it will look like this:
```
<iframe src="https://0a3800560302bd0f80a46cfb0014006c.web-security-academy.net/?search=%3Cbody+onresize%3Dprint%28%29%3E%3C%2Fbody%3E" onload=this.style.width="100px"></iframe>
```

So I use the `iframe` tag which allow me to create a small frame in the whole body of the exploit page.`onload` event directly modifies the value of `width` in the target page so the `onresize` could be trigger without any user interaction.

Happy Hacking!@#!#!
