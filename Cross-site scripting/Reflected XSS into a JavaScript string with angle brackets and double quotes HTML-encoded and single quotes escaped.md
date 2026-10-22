Link: [Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped]()
Difficulty: Practitioner

# Action 
Based on the lab description, I know that the angle brackets (`<` or `>`) and double quotes (`"`) will be converted into HTML -encoded token. Therefore, my only solution is to use the backslash (`\`) which could help me escape javascript string.
In code, `\` is usually used to escape special characters in a string, I will try to put a single `\` in the search box and see how the server handles the request
<img width="1920" height="994" alt="Screenshot_20261022_160937" src="https://github.com/user-attachments/assets/0b638077-1807-43c6-a4a6-69209620b75a" />

As the `\` is putting in the search box, the server returns a `\\` which tells  me that I could use this special character to craft my payload. Attempt to escape the `'` with this payload
```
\'
```
<img width="1920" height="994" alt="Screenshot_20261022_161116" src="https://github.com/user-attachments/assets/3c862d8a-d37e-4e50-b70a-1e15287cd94e" />

I can easily insert the single quote inside the target now. Here is the final payload
```
\';-alert()//
```

Happy Hacking
!@#!@#!
