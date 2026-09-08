Link : [Username enumeration via response timing](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing)

# Overview 
Our goal is to find another pair of credential beside the given one `wiener:peter`

# Process
Let's intercept the login POST request to examine the mechanism of login services. I noticed that multiple failed attempts could lock me out for 30 mins. So I read the hint and found out this protection mechanism is based on IP.
Therefore, if I could manipulate the IP address in the request, technically, I could bypass it with bruteforce.

Here is the request in Intruder tab 
<img width="1600" height="900" alt="Screenshot From 2026-09-08 16-21-27" src="https://github.com/user-attachments/assets/7e763d7b-e8e9-4b34-b382-8713267a085a" />

### Explaination
I use Pitchfork Attack which allows me to perform brutefocing attack in each allocated payload placeholder parallelly. The first payload is set to numbers within `X-Forwarded-For` header is number  0-200. The second payload is the username with provided username list. However, after multiple times bruteforce and observe the results, I noticed the appearance pattern of `mysql` was more frequent than others, which I assumed that it was what I need to find.
<img width="1883" height="1020" alt="Screenshot From 2026-09-08 16-27-27" src="https://github.com/user-attachments/assets/dcfaa6d8-a00f-462c-a70d-90f1b546bb48" />

Then continue with the process, I did the same thing with finding password for user `mysql`
<img width="1600" height="900" alt="Screenshot From 2026-09-08 16-28-14" src="https://github.com/user-attachments/assets/1bc7b5ba-05d8-4a58-b7a0-c9873ac0d3c7" />

Here is the result, I just need to search for HTTP code 302 which means successful authentication

<img width="1883" height="1020" alt="Screenshot From 2026-09-08 15-57-03" src="https://github.com/user-attachments/assets/d3ed12d5-8290-4632-94be-b3131f9a12da" />

<img width="1920" height="962" alt="Screenshot From 2026-09-08 15-57-47" src="https://github.com/user-attachments/assets/94c00e60-8a9e-44b1-b4bf-36245f6a1620" />

Finished!!

Happy Hacking@!$@#!$
