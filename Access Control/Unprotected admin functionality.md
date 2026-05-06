URL : [Unprotected admin functionality](https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality)

try to access hidden endpoint like  `robots.txt` to find out which endpoints are disallow from accessing
<img width="1674" height="174" alt="Screenshot 2026-05-07 013008" src="https://github.com/user-attachments/assets/bb82491d-a71f-48b2-a308-f91f2ab945cb" />

`/administrator-panel` endpoint is hidden
<img width="1919" height="431" alt="Screenshot 2026-05-07 013258" src="https://github.com/user-attachments/assets/a582989b-51a9-42ec-8219-237f1da82d0e" />

Then by accessing that endpoint help me perform administrative functions
Happy Hacking#!@#!@#!#

# Further Information
The reason why is there a `robots.txt` file is because that file tells the crawling bot which parts of the website they can access and which cannot
