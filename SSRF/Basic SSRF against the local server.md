URL : [Basic SSRF against the local server](https://portswigger.net/web-security/learning-paths/ssrf-attacks/ssrf-attacks-common-ssrf-attacks/ssrf/lab-basic-ssrf-against-localhost#)

First capture the request of `Check stock`
<img width="1913" height="725" alt="Screenshot 2026-04-15 120414" src="https://github.com/user-attachments/assets/d668bfb2-17d4-4f4a-a0ef-5424dd84118b" />
<img width="992" height="233" alt="Screenshot 2026-04-15 120357" src="https://github.com/user-attachments/assets/37e9549c-2b0a-4fdd-9d44-579e51879dd3" />

`stockApi` is my target to perform SSRF by changing the URL to `http://localhost/admin`
<img width="1256" height="551" alt="Screenshot 2026-04-15 120341" src="https://github.com/user-attachments/assets/b4ae3740-9510-4c65-bc6a-68b81010a30b" />

And I got a valid 200 HTTP code, dig deeper to find available function to perform the deletion of user `carlos` I ended up with this
<img width="602" height="548" alt="Screenshot 2026-04-15 120752" src="https://github.com/user-attachments/assets/70efb0fb-bb3c-4232-9daa-a15d7b3a55e8" />

Here is the result
<img width="1247" height="547" alt="Screenshot 2026-04-15 120925" src="https://github.com/user-attachments/assets/16a1df9a-3b64-4ad1-9d88-ad1ba2dd08a9" />
The code 302 HTTP status tells me that the resource has been moved temporarily  to a differnt location

Happy Hacking!@#!@#!
