URL : [Multi-step process with no access control on one step](https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step)

For this lab, I have to login as  `administrator` to understand of upgrading privilege for a user. It comprises of two steps:

1. Requesting leveraging privilege for a specific user
<img width="1625" height="532" alt="Screenshot 2026-05-12 232237" src="https://github.com/user-attachments/assets/360b8fda-5050-420a-91f0-ab515c9e75ca" />
<img width="936" height="447" alt="Screenshot 2026-05-12 232058" src="https://github.com/user-attachments/assets/918f9618-65e6-4df7-958f-8cd2bdd1872e" />

2. Confirming
<img width="935" height="444" alt="Screenshot 2026-05-12 232013" src="https://github.com/user-attachments/assets/6c78cf3c-c055-4182-a93d-7eecadb73560" />
<img width="1542" height="686" alt="Screenshot 2026-05-12 232028" src="https://github.com/user-attachments/assets/9c193e0a-af79-4eaa-b7fb-426fac6c8fc6" />

With that, now, I can log in as `wiener` and try to perform the second request to confirm my request  of leveraging my account's privilege
How? Simply, just make a POST request of changing email
<img width="1533" height="538" alt="Screenshot 2026-05-12 234408" src="https://github.com/user-attachments/assets/1bcb7969-5432-4b71-af60-8f42ad3c09c2" />

Adding required `action` ,`username`, and `confirmed` to perform the second request
<img width="936" height="589" alt="Screenshot 2026-05-12 234359" src="https://github.com/user-attachments/assets/1b36b71d-dfa9-40cc-bc3a-54ddbb42b848" />

Happy Hacking!@#$!@#$
