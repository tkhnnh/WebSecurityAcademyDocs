Link : [Blind SQL injection with conditional responses](https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses)
Difficulty: Practitioner

# Existing info
```
- The application uses a tracking cookie for analytics, and performs a SQL query containing the value of the submitted cookie.
- The results of the SQL query are not returned, and no error messages are displayed. But the application includes a Welcome back message in the page if the query returns any rows.
- The database contains a different table called users, with columns called username and password. You need to exploit the blind SQL injection vulnerability to find out the password of the administrator
```

# Action
The tracking cookie now is the target since it performs a SQL query containing the value of the submitted cookie stemming from the description.
This is the value of the cookie
```
Cookie: TrackingId=hqwBSm59E90D20g7; session=6brBUIOD2aFFXnBKL9eh9O3upAiUapOS
```

Intercept any request containing this `TrackingId` is my target so far. The question is how to perform Blind SQL, reference `results of the SQL query are not returned, and no error messages are displayed. But the application includes a Welcome back message in the page if the query returns any rows.`
Note that if the query of the cookie value is true which means the message `Welcome back!` displayed.
<img width="1542" height="793" alt="Screenshot_20260924_183010" src="https://github.com/user-attachments/assets/1de9b920-811e-4a41-a456-f4aad2f82f64" />

And with the false condition
<img width="1535" height="796" alt="Screenshot_20260924_183054" src="https://github.com/user-attachments/assets/5af50a23-b21b-4d4d-af16-6082172b895e" />

Next, I will check whether the information given by the lab is true by checking the table `users` exists or not
<img width="1534" height="789" alt="Screenshot_20260924_183206" src="https://github.com/user-attachments/assets/87d89631-7629-418e-985f-5db367160303" />

Fortunately, it is real information, hence, it's time to search for the password. First of all, let's confirm the length of the password.
<img width="1535" height="786" alt="Screenshot_20260924_183353" src="https://github.com/user-attachments/assets/04ce9c12-3059-44df-b560-389c8e9fac36" />

With this formula, I finally find the length of the password
<img width="1540" height="832" alt="Screenshot_20260924_183444" src="https://github.com/user-attachments/assets/0cea0368-d995-45ce-8e65-86ea3d63c489" />

Well, in order to recover the whole password with 20 characters, I need to bruteforce each character 1 by 1 with Intruder. Also, since I assume that the password only contains lowercase, alphanumeric characters, which results in 34 characters.
I will use the function called SUBSTRING(string,start, length) to guess each character of the password and a small script to generate the payload
```
import string

lowercase_str = string.ascii_lowercase
for char in lowercase_str:
    print(char)

for num in range(0,10):
    print(num)
```

Or the payload is here
```
a
b
c
d
e
f
g
h
i
j
k
l
m
n
o
p
q
r
s
t
u
v
w
x
y
z
0
1
2
3
4
5
6
7
8
9
```



Here is the first character `o`. 
<img width="1798" height="934" alt="Screenshot_20260924_185230" src="https://github.com/user-attachments/assets/12717b6f-abc0-4bee-ae60-d2113f774988" />
=> The password is
```
o45hio8rb7yrm04f9mpa
```

Confirming the password
<img width="1535" height="829" alt="Screenshot_20260924_190125" src="https://github.com/user-attachments/assets/0c1626e4-0fbe-4009-9634-a8262962c9c6" />

Now, it's time to login as `administrator` and wrap up the lab.

Happy Hacking@#!#!@

## Reference 
[SUBSTRING](https://www.w3schools.com/sql/func_sqlserver_substring.asp)
