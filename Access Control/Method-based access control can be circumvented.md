URL: [Method-based access control can be circumvented](https://portswigger.net/web-security/access-control/lab-method-based-access-control-can-be-circumvented)

For this lab, first , I need to understand what are inside `Admin panel` with given credentials. Turn out, it is a control dashboard to leverage or downgrade the privilege of users existing on the system.

<img width="938" height="351" alt="Screenshot 2026-05-10 125628" src="https://github.com/user-attachments/assets/157e8631-404b-45f2-97b2-a59a9c67d662" />

What if during `wiener` session, a request like above is made to leverage his own privilege
<img width="933" height="486" alt="Screenshot 2026-05-10 145706" src="https://github.com/user-attachments/assets/f26507d1-9915-4967-86d8-c971f4d01e66" />

I successfully leverage `wiener` to administrator privilege
Happy Hacking!@$@$!@#
