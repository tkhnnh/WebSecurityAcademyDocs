Link: [DOM XSS in jQuery selector sink using a hashchange event](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-selector-hash-change-event)
Difficulty: Apprentice

# hashevent
Usually, it will be represent as `#` symbol, which handle single-page application transition.

# Action
The goal is to trigger `print()` function from the client web browser, luckily, that function can be triggered via `onerror()` handler. First, I need to build my exploit server with `iframe` tag. Here is the payload
In the body:
```
<iframe src="https://0a9400c104ca2cc080280309002400ba.web-security-academy.net/#" onload=" this.src+='<img onerror=print()'"><iframe>
```

## Payload explanation
The src method is appended with `#` which could trigger the jquery hashevent. So after loading the first src, it will continue with the onload method which load the tag img which trigger the print() function.
Then just sent it to the victim

Happy Hacking@#!@#!@
