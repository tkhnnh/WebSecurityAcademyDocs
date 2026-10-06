Link: [Stored XSS into anchor href attribute with double quotes HTML-encoded](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded)
Difficulty: Apprentice

# Analysis
The site has comment section which allows user to convey the feeling about a post, for each input section, only `Website` section directly enmbed the input into the href url
```
<p>
                        <img src="/resources/images/avatarDefault.svg" class="avatar">                            <a id="author" href="http://google.com">test</a> | 06 October 2026
                        </p>
                        <p>hello</p>
                        <p></p>
```
# Action
To trigger XSS on this target, all I need to do is inserting my payload into `Website` section
```
javascript:alert(window.origin)
```

`javascript:` is a pseudo-protocol used in browser address bars or HTML links

Happy Hacking!@#!@#!
