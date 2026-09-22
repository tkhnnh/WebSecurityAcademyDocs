Link: [Blind OS command injection with time delays](https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays)
Difficulty: Practitioner

How each command is being executed in a linux command line:
```
ls || grep ...
```
with these two command either one of them fails, the other is still being executed no matter what. `||` is the `or` operator. Essentially, the solution is pretty simple to bypass the filter
Thinking about the request will be sent to server using command line, for example, it would assumably execute the command line too called `email` to send the email.
```
email=x || ping -c 10 127.0.0.1
```
if I can insert the `||` into the payload to trigger the `ping` command meaning that I successfully perform Blind OS command injection
<img width="1164" height="734" alt="Screenshot 2026-09-22 at 11 34 43 pm" src="https://github.com/user-attachments/assets/e173f576-950f-4cf1-a025-d3cb581d79b9" />
I did it succesfully.

Happy Hacking@!#!#
