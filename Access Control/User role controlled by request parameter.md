URL: [User role controlled by request parameter](https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter)

For this lab, first, capture the login request with given credentials
<img width="940" height="213" alt="Screenshot 2026-05-08 001334" src="https://github.com/user-attachments/assets/34b9e14a-7df4-4fab-96e9-3ca6b362afc1" />

Therre is a field called `Admin` which is a boolean field allowing to give admin access for a specific request. Attempting capturing the `Home` request to observe whether are there any changes in control dashboard
<img width="1908" height="286" alt="Screenshot 2026-05-08 001529" src="https://github.com/user-attachments/assets/a0babe9e-e068-4884-922d-a6cc899ccca2" />

Then also with deleting `Carlos` request, it is compulsory to make `Admin` to true to give administrative privilege in order to execute the request
<img width="934" height="359" alt="Screenshot 2026-05-08 001711" src="https://github.com/user-attachments/assets/3de18dcf-0194-4a6a-b0f0-4b680c129584" />

Happy Hacking!#!@#!@#!
