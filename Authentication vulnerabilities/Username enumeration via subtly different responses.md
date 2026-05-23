URL: [Username enumeration via subtly different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses)

Keep focusing on the login page, but this time, the resonse is too generic
<img width="1918" height="767" alt="Screenshot 2026-05-23 214040" src="https://github.com/user-attachments/assets/7ad6b685-b18d-4d8b-b2cf-1fe9ec469e52" />

However, as the title hinted, there must be a slightly different discrepancy between responses. So, forwarding the request to Intruder, also, adding a small extraction filter for the response `Grep - Extract`
<img width="1594" height="885" alt="Screenshot 2026-05-23 220149" src="https://github.com/user-attachments/assets/d938ea4d-3b86-442d-93c3-65d4f2046a40" />

Configuring the Extraction
<img width="672" height="615" alt="Screenshot 2026-05-23 220343" src="https://github.com/user-attachments/assets/86c8fafe-0d2d-4145-8d1f-fab5d12e1060" />

Analyze the discrepancy in these responses, I can tell that one response does not have the `.` which is crazily small difference
<img width="1478" height="838" alt="Screenshot 2026-05-23 215859" src="https://github.com/user-attachments/assets/e955bd4d-d682-4552-97c3-7e1961049dd9" />
<img width="1476" height="839" alt="Screenshot 2026-05-23 215845" src="https://github.com/user-attachments/assets/3b96d746-b3d8-4ee6-a417-e6b38f21a6c4" />

Therefore, I got the username which is `antivirus`. Now do the same thing to find the password, however, for password I think we only need to filter out the Status code only
<img width="1474" height="833" alt="Screenshot 2026-05-23 221031" src="https://github.com/user-attachments/assets/d2ec232f-27ab-4c5c-9a51-be8d0d310c40" />
<img width="1595" height="884" alt="Screenshot 2026-05-23 221018" src="https://github.com/user-attachments/assets/fab8ab43-655b-4b55-9d41-4c9d783ce74b" />

Happy Hacking!@#!#!
