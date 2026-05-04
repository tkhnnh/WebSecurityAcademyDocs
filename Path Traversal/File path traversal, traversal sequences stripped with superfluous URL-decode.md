URL : [File path traversal, traversal sequences stripped with superfluous URL-decode](https://portswigger.net/web-security/file-path-traversal/lab-superfluous-url-decode)

In this problem, I still try and exploit the filename parameter by intercepting a request containing that parameter

<img width="1254" height="234" alt="Screenshot 2026-05-04 221015" src="https://github.com/user-attachments/assets/e8460356-78a2-48be-81ea-5def742d729e" />

Attempting inject payload with URL-encoding schema for `../` -> `%2e%2e%2f`
<img width="1256" height="552" alt="Screenshot 2026-05-04 220919" src="https://github.com/user-attachments/assets/94e8810f-2cc0-4188-a245-6894afd072a3" />
<img width="1260" height="555" alt="Screenshot 2026-05-04 220909" src="https://github.com/user-attachments/assets/1c3922c4-67f5-4604-bd68-7392c24acf3d" />

But they didnt work out, however , I tried with another one which is nested URL-decoding `%` is `%25` and `.` is `%2e` and `/` is `%2f`
<img width="1257" height="559" alt="Screenshot 2026-05-04 220859" src="https://github.com/user-attachments/assets/504a3287-0216-4985-bb05-e9b13720c310" />

Happy Hacking!@#$!@#
