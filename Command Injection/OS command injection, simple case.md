Link : [OS command injection, simple case](https://portswigger.net/web-security/os-command-injection/lab-simple)
Difficulty: $$\color{green}{Apprentice}$$

The goal is to trigger `whoami` command via a vulnerable check stock button in the site.

First, let's capture the request when triggering `stock`
<img width="1603" height="900" alt="Screenshot From 2026-09-16 00-09-02" src="https://github.com/user-attachments/assets/99192a91-ed19-4436-be62-0274022492d3" />

Then forward this request to `Repeater` tab, now I insert a command in between of two `&`
<img width="1603" height="900" alt="Screenshot From 2026-09-16 00-10-17" src="https://github.com/user-attachments/assets/4b5fb035-4b1e-4c61-a2b6-ddae07d9b7ca" />

Nothing happened, how about encoding the `&` to URL-encoding schema
<img width="1603" height="900" alt="Screenshot From 2026-09-16 00-11-40" src="https://github.com/user-attachments/assets/de0358d7-414f-4d55-8dce-e9625a59a535" />

It wotks, pieace of cake

Happy Hacking!@#$!@$
