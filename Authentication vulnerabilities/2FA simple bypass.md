URL : [2FA simple bypass](https://portswigger.net/web-security/authentication/multi-factor/lab-2fa-simple-bypass)

First I need to log in with `wiener:peter` 
<img width="1902" height="914" alt="Screenshot 2026-05-27 231621" src="https://github.com/user-attachments/assets/53637b67-438e-4eec-b771-f84b66f80367" />


<img width="1903" height="993" alt="Screenshot 2026-05-27 231641" src="https://github.com/user-attachments/assets/2e1735c8-3df2-4cce-a92b-806330cb3e47" />
-> notice the endpoint of the URL is `/my-account?id=wiener`

What if the software does not implement forcing to check whether users enter the 2FA code or not, which can lead user to bypass the 2FA by just abusing the URL
So after log ing as `carlos:montoya` -> User will be redirect to 2FA page, by modifying `login2` to `my-account?id=carlos` which helps me bypass this security mechanism

# Solution for  mitigation
Implementing like a path checking if users do not give right correct code for 2FA, keep them at that page or if they hit the limit returning them to the login page

Happy HAking!#!@#
