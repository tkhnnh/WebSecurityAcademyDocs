Link: [Reflected XSS into a JavaScript string with angle brackets HTML encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-string-angle-brackets-html-encoded)
Difficulty: Apprentice

# Action 
Let's inspect how my input will be handled in the server

```
<script>
                        var searchTerms = 'abc';
                        document.write('<img src="/resources/images/tracker.gif?searchTerms='+encodeURIComponent(searchTerms)+'">');
                    </script>
```
Simply, the input on search box will be assigned to a variable called `searchTerms` which then is used within the  `document.write` function. Therefore, I need to using backslash to escape the string.
First, I need to close the single quote by adding `'` to my input and inspect the result.
Nothing changed, now it's time for escaping string character the verdict backslash but which one is preferred one backslash or two? 

In JavaScript, the backslash (\) serves primarily as an escape character that modifies the meaning of the following character.  In string literals, it is used to include special characters (like newlines \n or tabs \t) or to escape delimiters (like \" or \'). To include a literal backslash in a string, you must escape it by using two backslashes (\\).
Then in this case, I will use two and 
<img width="1154" height="396" alt="Screenshot 2026-10-09 at 11 30 38 pm" src="https://github.com/user-attachments/assets/ba53f924-2aca-40e3-bb93-89c2cbed166d" />
It works, now appending with `-alert(1)//` the frontslash is to comment out the rest of the javascript function which is abundant.
<img width="1160" height="648" alt="Screenshot 2026-10-09 at 11 33 31 pm" src="https://github.com/user-attachments/assets/a04a0148-d36f-45b7-a1a9-8667587a5dbb" />

Happy Hacking!#!@#!
