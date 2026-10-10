Link: [Basic server-side template injection (code context)](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic-code-context)
Difficulty: Practitioner


# Recon
Based on the given information, I know that the template which target is currently using is `Tornado`  but I will have to double check later, first let find the vulnerable function. After I logged in with given credential.
The `/my-account` page provides me with `updating username and email functionalities, which then I find the `preferred name` updating function vulnerable to SSTI.

While intercepting with Burp HTTP traffic, I learn that when updating the preferred name, a POST request of `/my-account/change-blog-post-author-display` will be sent to server with 2 queries.

1. blog-post-author-display
2. csrf
   
# Action
Let's exploit the `blog-post-author-display` with SSTI, and the payload is constructed like this 
```
blog-post-author-display=user.first_name}}{{7*7
```
<img width="1540" height="752" alt="Screenshot_20261011_103333" src="https://github.com/user-attachments/assets/ec125b81-97bd-42fc-82e9-aeec2c3d1541" />

Now, to confirm whether any change is being made, make a comment for any post
<img width="676" height="377" alt="Screenshot_20261011_103441" src="https://github.com/user-attachments/assets/7ce8afb0-6b07-43fb-842a-d834219787eb" />

It actually append the multiplication of given equation to the name which assure me that the query is vulnerable to SSTI.
The payload to solve the lab, I will need to import a python library called `os` which includes `remove` function
```
blog-post-author-display=user.first_name}}{{__import(os).remove('/home/carlos/morale.txt')
```
SOLVED
Happy Hacking!@#!#!
