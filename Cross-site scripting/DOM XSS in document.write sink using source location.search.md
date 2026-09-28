Link: [DOM XSS in document.write sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)
Difficulty: Apprentice 

# Definition
DOM-based XSS vulnerabilities arises when Javascript take input from attacker controllable source and passes it to a sink that supports dynamic code execution such as `eval()` or `innerHTML`
Especially it won't work when testing for DOM with Page Source since it does not make any change to the HTML it self.
DOM (Document Object Model) is what a browser builds with javascript which can also be manipulated with the same language.

## Reference
[What is the difference between HTML and DOM?](https://medium.com/@leetcore/what-is-the-difference-between-html-and-dom-c704ed3d1305)
[What is DOM-based cross-site scripting?](https://portswigger.net/web-security/cross-site-scripting/dom-based)

# Action
First, based on given information from the lab description, I find that the search engine is currently using a javascript function called `document.write` and parse the query, which is the source input directly into the function without sanitising. That is my attack point, by manipulating the input of the search box, I could trigger DOM-based XSS, first, I need to inpsect the page to confirm whether the site actually uses the function `document.write`
<img width="1501" height="824" alt="Screenshot 2026-09-28 at 10 28 10 am" src="https://github.com/user-attachments/assets/837eb946-9766-4685-9c12-b4fd8e62a08b" />

Well, the good thing is that it does use the function, next how can I trigger XSS ? Simply enough, look at how the query is being passed into the function, I come up with the way to escape the input. By adding like this:
```
'">);
```
To escape the `document.write` function then coming next is my XSS payload, which turns out to be like this
```
'">);<script>alert(document.domain)</script>
```
<img width="1500" height="909" alt="Screenshot 2026-09-28 at 10 31 06 am" src="https://github.com/user-attachments/assets/510f69a9-d184-4609-b1cb-342aefa26b4b" />
And that triggers the vulnerability.

Happy Hacking!@#$@!#$
