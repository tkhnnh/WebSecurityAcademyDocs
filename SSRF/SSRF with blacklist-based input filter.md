URL: [SSRF with blacklist-based input filter](https://portswigger.net/web-security/learning-paths/ssrf-attacks/ssrf-attacks-circumventing-defenses/ssrf/lab-ssrf-with-blacklist-filter#)


The goal is to replace localhost with alternatives since it has been filtered by blacklist 
<img width="1254" height="372" alt="Screenshot 2026-04-16 174830" src="https://github.com/user-attachments/assets/6e0a02a7-ec91-4d12-89f9-7c75b2de6029" />

SO I tried with `127.1` but it still blocks
Afterward, I learn about doubling URL encoding, so the symbol `%` in URL encoding is `%25` and a is `%61` so if I replace a with `%2561` which means that the server will resolve `%25` to `%`
then continueing on resolving `%61` to `a`
<img width="1257" height="623" alt="Screenshot 2026-04-16 175659" src="https://github.com/user-attachments/assets/9c308801-aad8-4f14-821f-5294d59098bb" />

It works perfectly. Now let's solve it
<img width="1251" height="374" alt="Screenshot 2026-04-16 214212" src="https://github.com/user-attachments/assets/a39c4ca2-19ce-4b8b-9531-a0a35ed9d936" />

Happy Hacking!#!@#!
