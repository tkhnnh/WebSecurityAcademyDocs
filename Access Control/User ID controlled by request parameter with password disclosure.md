URL : [User ID controlled by request parameter with password disclosure](https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure)

First, logged in as `wiener`, then from `wiener`  request modify the parameter value to `administrator` to observe any changes

<img width="938" height="477" alt="Screenshot 2026-05-10 160718" src="https://github.com/user-attachments/assets/758dcdb4-b6ba-4c34-90c8-d3a63ea6a114" />
<img width="934" height="484" alt="Screenshot 2026-05-10 160707" src="https://github.com/user-attachments/assets/fd6dcc24-c2b4-416f-84c1-2413e2e346ff" />

By changing the parameter value of `id` I can actually escalate my privilege to `administratror`. 
<img width="1409" height="665" alt="Screenshot 2026-05-10 160815" src="https://github.com/user-attachments/assets/9ea56921-8e18-4eae-b9ab-c3424860ce53" />

Next step is retrieving `administrator password. Just capture the `change password` request and I can view it in the payload
<img width="918" height="769" alt="Screenshot 2026-05-10 160951" src="https://github.com/user-attachments/assets/9b4a908d-eeb4-47d3-ba22-69e3db9f6d35" />

Now it's time to eliminate `carlos`

happy hacking!@#$@!$
