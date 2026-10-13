Link: [Reflected XSS into HTML context with most tags and attributes blocked](https://portswigger.net/web-security/cross-site-scripting/contexts/lab-html-context-with-most-tags-and-attributes-blocked)
Difficulty: Practitioner

# Recon
If a malicious input containing forbidden tags were to be inserted on the search box, an error with http code 400 would appear with a message tag not allowed

Let's enumerate which tags are allowed in this WAF by using `Intruder`
