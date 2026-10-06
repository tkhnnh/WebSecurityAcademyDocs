Link: [Reflected XSS into attribute with angle brackets HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-attribute-angle-brackets-html-encoded)
Difficulty: Apprentice

# Action 
The search box has been sanitized properly with  angle brackets which means whenever I input `<>` turns out to be `&lt;&gt;` in the Page Source. So the mechanism would take the input into the `value` section inside the `<input>` tag
<img width="878" height="282" alt="Screenshot_20261006_232037" src="https://github.com/user-attachments/assets/c110209b-55c1-436a-9019-d2db86f26963" />

So payload would be to comment out the `value` with `"`, implementing with `onmouseover`
```
"onmouseover"=alert(1)
```

<input type=text placeholder='Search the blog...' name=search value=""onmouseover="alert(1)">

Happy Hacking!@#!$!  
