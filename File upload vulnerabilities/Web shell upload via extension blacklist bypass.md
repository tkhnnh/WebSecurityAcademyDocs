Link: [Web shell upload via extension blacklist bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-extension-blacklist-bypass)
Difficulty: Practitioner

# Action 
<img width="1537" height="719" alt="Screenshot_20261102_131302" src="https://github.com/user-attachments/assets/0397d04e-2ce9-4a21-989e-0e3a22960042" />
When I upload the payload with `php` extension, the server reject it because it is in the blacklist. Therefore, by manipulating `.htaccess` file, I could upload the payload with other extension but can make it executable as well.

## What is `.htaccess` ? 
It is a directory-level configuration file used by the Apache HTTP Server.
It allows web developers and administrators to alter the server's behaviour for a specific directory and all its subdirectories without needing to edit the global server configuration files.

 Then, by adding this line 
 ```
 AddType application/x-httpd-php .cheers
```

Now, I can upload the payload with the extension `.cheers` and it will execute the php payload
<img width="1537" height="719" alt="Screenshot_20261102_132553" src="https://github.com/user-attachments/assets/ecf35c7a-ebcd-4c14-b887-461b2f496f24" />


Happy Hacking@#$@#$@
