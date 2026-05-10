URL : [URL-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented)

For this lab, I try to intercept the request of accessing `Admin Panel` 
<img width="916" height="754" alt="Screenshot 2026-05-10 122057" src="https://github.com/user-attachments/assets/aa354ec6-045d-44af-9ded-f91662e992c1" />

Then I modify a request endpoint to `/` since it raises `Access Denied` error when I keep using `/admin` endpoint for the request. Furthremore, by appending the request with `X-Original-URL` header which redirects us to the endpoint that I want 
<img width="935" height="353" alt="Screenshot 2026-05-10 122659" src="https://github.com/user-attachments/assets/34f26135-0ce8-411a-968d-8fa42928b999" />

After that I have my access and privilege to admin control panel. Notice that in order to delete user `carlos`, I must add the whole request including paramter to `X-Original-URL` header
<img width="934" height="482" alt="Screenshot 2026-05-10 123433" src="https://github.com/user-attachments/assets/18a672f6-fad8-488c-b8f1-2be7660974fd" />

However, it raises an error that Missing parameter for username.
<img width="936" height="545" alt="Screenshot 2026-05-10 122948" src="https://github.com/user-attachments/assets/683afe33-76a1-4d90-a749-e2a1fe61b475" />

Now I realize that the parameter should be included after the HTTP request and the base privileged URL is only used in `X-Original-URL` header
<img width="938" height="547" alt="Screenshot 2026-05-10 123006" src="https://github.com/user-attachments/assets/8f8ffe7f-bad9-433b-9d1b-f50b24b3ab6b" />

Happy Hacking#!#!#!@
