URL: [Referer-based access control](https://portswigger.net/web-security/access-control/lab-referer-based-access-control)

For this lab, I need to view the request of upgrading users' privilege under admninistrator's perspective
<img width="940" height="589" alt="Screenshot 2026-05-13 012514" src="https://github.com/user-attachments/assets/fe32a91c-9f56-4a4d-b34e-8d393ec49f8e" />

So I need a `Referer` header point to the trusted source which ending with endpoint called `admin` and all the required parameters like `username` and `action` which are needed to perform an attack

Now, under `wiener` account, try to get a GET request then modify the request with required parameters and also the `Referer` header must match with the one from the administrator 
<img width="940" height="591" alt="Screenshot 2026-05-13 012800" src="https://github.com/user-attachments/assets/1331297d-9458-4d87-a991-a65f19867d74" />

Happy hacking1!$!@#$!@#
