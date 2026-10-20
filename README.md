# WebSecurityAcademyDocs

> My hands-on learning journey through [PortSwigger's Web Security Academy](https://portswigger.net/web-security) — documenting every lab I complete in my own words.

I use this repo to prove skills by doing: for each vulnerability class I work through PortSwigger's labs and write up how I identified the issue, exploited it in a controlled environment, and how it's defended against. Everything here is for **educational and defensive purposes**, using PortSwigger's intentionally vulnerable practice labs in authorized settings.

---

## Browse by topic

Click any topic to see my write-ups.

| Topic | Notes |
|---|---|
| 🔌 [API testing](API%20testing) | Server-side parameter pollution and REST API abuse |
| 🔑 [Access Control](Access%20Control) | Broken access control, referer-based checks |
| 🪪 [Authentication vulnerabilities](Authentication%20vulnerabilities) | Login flaws, password-reset logic |
| 💻 [Command Injection](Command%20Injection) | OS command injection, blind & output redirection |
| 🧬 [Cross-site scripting](Cross-site%20scripting) | Reflected, stored & DOM-based XSS |
| 📂 [Information disclosure](Information%20disclosure) | Leaked data, version-control history exposure |
| 🗂️ [Path Traversal](Path%20Traversal) | File path traversal attacks |
| 💉 [SQL injection](SQL%20injection) | Classic & blind SQL injection |
| 🌐 [SSRF](SSRF) | Server-side request forgery, blind/OOB detection |
| 📝 [Server-side template injection](Server-side%20template%20injection) | SSTI across template engines (e.g. FreeMarker) |
| 🧊 [Web cache deception](Web%20cache%20deception) | Cache-based information exposure |

---

## What each write-up covers

Every lab note follows the same structure so it's easy to scan:

- **What it is** — the vulnerability class in plain language
- **Approach** — how I identified and reasoned about the issue
- **Walkthrough** — the steps I took to solve the lab
- **Defenses** — how it's prevented or mitigated
- **Takeaways** — what I learned

## About me

I'm building practical web application security skills through consistent, hands-on practice. This repo is an ongoing record of that work and grows as I cover more of the Academy.

- 🎯 Practising with [Burp Suite](https://portswigger.net/burp) and the [Web Security Academy](https://portswigger.net/web-security)
- 📈 Working through topics methodically, from access control to template injection

## Disclaimer

All content is based on PortSwigger's free, intentionally vulnerable labs and is intended for learning only. Never apply these techniques against systems you do not own or have explicit written permission to test.
