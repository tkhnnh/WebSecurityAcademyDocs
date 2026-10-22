Link : [Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-onclick-event-angle-brackets-double-quotes-html-encoded-single-quotes-backslash-escaped)
Difficulty: Practitioner


# Action 

First, I find the tag which includes the `onclick` event which is the url input field.
Let's try to escape the single quote character with backslash and I notice that single quote cannot be escaped
<img width="745" height="276" alt="Screenshot 2026-10-23 at 10 12 17 am" src="https://github.com/user-attachments/assets/47f260aa-886a-494f-af85-2768d997c4ce" />

The site filters out my backslash.
Therefore, I try to use the script from the academy
```
http://google.com\&apos;-alert(document.domain)-&apos;
```
So what does this payload actually do? The `&apos;` sequence is an HTML entity representing an apostrophe or single quote. Because the browser HTML-decodes the value of the `onclick` attribute before the Javascript is interpreted, the entities are decoded as quotes, which become string delimiters, and so the attack succeds
<img width="632" height="156" alt="Screenshot 2026-10-23 at 10 11 19 am" src="https://github.com/user-attachments/assets/0eb3637a-04ec-4964-a718-1e1bb4b6a9c8" />

Happy Hacking!@#$!@$
