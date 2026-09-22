Link : [ Blind OS command injection with output redirection](https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection)
Difficulty: Practitioner

The goal is to write the output of the command line `whoami` to a file within this folder `/var/www/images/`. I can achive this with output redirection `>`
Applying the same concept from [Blind OS Command injection with time delays](https://github.com/tkhnnh/WebSecurityAcademyDocs/blob/main/Command%20Injection/Blind%20OS%20command%20injection%20with%20time%20delays.md)
Here is the payload
<img width="1168" height="645" alt="Screenshot 2026-09-22 at 11 51 00 pm" src="https://github.com/user-attachments/assets/17775ad5-6abe-41f6-950c-54a26a8b76f2" />

URL-decoding:
- `%7C` = `|`
- `%3E` = `>`
- `%2F` = `/`

Try to access the image folder with that file name 
<img width="1195" height="865" alt="Screenshot 2026-09-22 at 11 49 23 pm" src="https://github.com/user-attachments/assets/82c79244-da9d-4d0e-b8e4-8927fbe09b50" />

Happy HAcking@#@!#!@#
