Link: [Basic server-side template injection](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-basic)
Difficulty: Practitioner

# Definition
Server-side template injection is an attack which attacker takes advantage of the template syntax to inject malicious payload and execute it on the server-side.

Template engines are designed to generate web pages by combining fixed templates with volatile data. Server-side template injection attacks can occur when user input is concatenated directly into a template, rather than passed as data. This allow attackers to inject arbitrary template directives in order to manipulate the  template engine, often enabling them to take complete control of the server.

# Action
In this lab, since I already know that the template which the target is currently using is `ERB`. But still, I tested it with my payload to confirm that information
<img width="1537" height="680" alt="Screenshot_20261010_234525" src="https://github.com/user-attachments/assets/5daed558-1f3e-4422-82b0-c91aaed65d4a" />

Notice the multiplication of 7 and 7 is 49, then I want to read the `/etc/passwd`
<img width="1537" height="680" alt="Screenshot_20261010_234624" src="https://github.com/user-attachments/assets/858a15e8-9c7e-4c28-9a10-3bc70fbe6e93" />

So it works, it's time to delete the required file.
<img width="1535" height="680" alt="Screenshot_20261010_234707" src="https://github.com/user-attachments/assets/4991df7a-51b5-4c1b-abf4-9ad5160db681" />


Done Happy Hacking!@#$!@$
