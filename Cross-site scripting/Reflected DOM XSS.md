Link: [Reflected DOM XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-dom-xss-reflected)
Difficulty: Practitioner

# Action
First, input some strings to the search engine and notice that the query `search-result` is being called with JSON data format returned
Check `searchResults.js`, the `eval()` function was being used with parameter from `searchResultobj` which is untrusted source.
<img width="644" height="130" alt="Screenshot_20261002_213839" src="https://github.com/user-attachments/assets/96c3f058-74fe-457f-aa2c-3552ab0e66b5" />

Here is the intercepted request
<img width="1539" height="797" alt="Screenshot_20261002_214227" src="https://github.com/user-attachments/assets/973c088c-6377-40e0-9bde-3d4c9611bc9c" />

In the Response section, the format of returned JSON data is 
```
{"results":[],"searchTerm":""}
```

Here is the payload
```
\"-alert(1)}//
```
## Explanation
In order to execute the alert function, I need to escape the quotation mark from the `searchTerm` which is why there is `\"` and an arithmetic operator (in this case the subtraction operator) is then used to separate the expressions before the `alert()` function is called
Finally, `//` to comment out the abundant closing double quote marks and the racket.

happy Hakicng!@#!@#
