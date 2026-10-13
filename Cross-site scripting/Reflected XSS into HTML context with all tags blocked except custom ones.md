Link: [Reflected XSS into HTML context with all tags blocked except custom ones](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-all-standard-tags-blocked)
Difficulty: Practitioner

# Recon
Performing a brute-force attack to find out what kind of custom tags are allow in this target 
<img width="1343" height="331" alt="Screenshot_20261014_103940" src="https://github.com/user-attachments/assets/8ccf16d1-0b62-4528-a0db-8df51b7a88fb" />

And filter out tags with 200 http code, among the found tags, I choose `xss`, let find the event of this tag
<img width="1343" height="303" alt="Screenshot_20261014_104127" src="https://github.com/user-attachments/assets/b1dedc31-e30e-4182-8cf4-082f136c2d90" />

And with same methodology, I choose `onfocus`. It's time to craft the payload
# Action
I could not use the tag `iframe` for this lab due to all the tags being blocked, therefore, I could not modify the size to use `resize` flag. Instead, I will use `script` tag which execute javascript code by using browser to render
```
<script> 
location='https://0a3600ff046d818082085330008600d0.web-security-academy.net/?search=%3Cxss+id%3Dx+onfocus%3Dalert%28document.cookie%29+tabindex%3D1%3E#x';
</script>
```

## Explaining how the payload works
By utilizing what have been found earlier, tag and event, I also add a small attribute `id` which assigns a name for this tag and I could call it with its name.

`tabindex` attribute controls whether an HTML element can receive keyboard focus and how it fits into the page's tab navigation sequence. By setting it to 1, forces an element into a custom priority tab order.

Finally, I use `#` to execute the payload.


Happy Hacking!@#!@#!$!
