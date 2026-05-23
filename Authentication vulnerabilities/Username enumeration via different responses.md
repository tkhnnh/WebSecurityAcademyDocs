<img width="1477" height="839" alt="Screenshot 2026-05-23 210906" src="https://github.com/user-attachments/assets/a4de04e8-162b-4408-a03b-d78c6f96fe69" />URL : [Username enumeration via different responses](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses)

For this lab, I focus mostly my attention on the authentication page, which is the login form. The task is to get into the service with given username list and also password list, therefore, the best option is to use brute-forcing method.

First, I enter random username and password to view the error
<img width="1915" height="765" alt="Screenshot 2026-05-23 202801" src="https://github.com/user-attachments/assets/0d9848d4-6768-4c47-9eca-757bd481f258" />

The error tells us that the username must be invalid. So I capture the POST login request and use Intruder to brute-force and find the valid username
<img width="1595" height="883" alt="Screenshot 2026-05-23 210942" src="https://github.com/user-attachments/assets/faf2cc07-42d4-4ba2-8f43-513f4410fa53" />

By checking the length of the response, I can filter out the username that I want
<img width="1477" height="839" alt="Screenshot 2026-05-23 210906" src="https://github.com/user-attachments/assets/79442f9a-54f1-47ea-8e7a-fdf8e58ac628" />


Doing the same thing with password
<img width="1596" height="886" alt="Screenshot 2026-05-23 211054" src="https://github.com/user-attachments/assets/ce1075d7-612c-4fe2-92ab-c005b12ce92b" />

Also filter out the length of the response 
<img width="1478" height="837" alt="Screenshot 2026-05-23 211444" src="https://github.com/user-attachments/assets/6ea8ab0d-623b-4a91-930d-05dce293d602" />

Then, finally using the Repeater to confirm the found credentials `apache:nicole`
<img width="1596" height="881" alt="Screenshot 2026-05-23 211527" src="https://github.com/user-attachments/assets/fc32378f-c222-4249-87ae-5493b498ced9" />


Happy Hacking@#!@#!
