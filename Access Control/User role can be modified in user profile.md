URL : [User role can be modified in user profile](https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile)

Again, First, I need to login with the given account. Since I couldn't find any parameter or endpoint that contains `roleid`. Then inserting this parameter into the payload of the request came up to my mind
<img width="938" height="543" alt="Screenshot 2026-05-08 010653" src="https://github.com/user-attachments/assets/2b10f1a3-cffb-46e5-aeb7-0c20c000611b" />

Then my profile dashboard now have new section `Admin control panel`
<img width="1756" height="638" alt="Screenshot 2026-05-08 010945" src="https://github.com/user-attachments/assets/a67afd56-4aae-4be9-8c6d-12182f50265f" />

Explaination:
So inside the request of changing email, I inserted an extra endpoint called `roleid` equals to 2 which set the role of my user to administrative level

Happy Hacking!@#!@#!#!
