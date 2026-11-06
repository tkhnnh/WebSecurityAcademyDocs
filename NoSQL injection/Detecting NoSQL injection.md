Link: [Detecting NoSQL injection](https://portswigger.net/web-security/nosql-injection/lab-nosql-injection-detection)
Difficulty: Apprentice 

# Definition
NoSQL databases store and retrieve data in a format other tahn traditional SQL relational tables. They are designed to handle large volumes of unstructured or semi-structured data.

How to spot the vulnerability?
There are two types of NoSQL vulnerability:
- NoSQL syntax injection
- NoSQL operator injection

For this lab, NoSQL syntax injection would be my choice.
# Action

How to detect syntax injection ? I will try to submit a fuzz string like these below
```
'"`{
;$Foo}
$Foo \xYZ
```

Then, determining which characters are processed, in this case, I choose `'` which results in syntax error 
<img width="1249" height="210" alt="Screenshot 2026-11-06 at 4 28 18 pm" src="https://github.com/user-attachments/assets/6b445f76-c6bb-4e6d-8e56-8eac64d3fa63" />

The reason is inputting `'` just adds one more `'` and breaks the statement, next, proceed to detect the conditional behaviour stage. By appending this payload at the end of the query
```
'||'1'=='1
```
The lab is solved. 
Happy Hacking!@$@$!@

