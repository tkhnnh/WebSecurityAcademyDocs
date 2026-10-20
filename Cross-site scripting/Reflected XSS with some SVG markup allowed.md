Link: [Reflected XSS with some SVG markup allowed](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-some-svg-markup-allowed)
Difficulty: Practitioner

# Recon
Based on the lab description, I know that the tag `<svg>` is not included in the blocklist, confirm it works with the search box. Now, what is svg?

SVG stands for Scalable Vector Graphics, is used to define vector-based graphics for the Web (defines graphic in XML format). Therefore, it acts like a container which requires other tags within for the markup (<rect/>,<polygon/>,etc.)
 Let's bruteforce the see what tags are allowed inside the `<svg>` container. By using Intruder in Burpsuite,

 <img width="1025" height="556" alt="Screenshot 2026-10-21 at 10 35 59 am" src="https://github.com/user-attachments/assets/c9870eda-b7c2-485c-9cc5-afa86e0da70c" />
I placed the parameter inside the `<svg>` tag and also use tags from the [cheatshet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) for the payload.

Then in the dialog I find, `<animatetransform>` tag appears with 200 HTTP code which is successful.

Peforming the same thing for finding the right events
```
/?search=<svg><animatetransform $$=1></svg>
```
And for the payloads for the event, I just use them from the cheatsheet as well.
# Action
Time to craft the payload
```
<svg><animatetransform onbegin=alert(1)></svg>
```
Happy Hacking!@#$@!
