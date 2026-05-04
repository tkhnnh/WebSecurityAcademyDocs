URL : [File path traversal, validation of file extension with null byte bypass](https://portswigger.net/web-security/file-path-traversal/lab-validate-file-extension-null-byte-bypass)

As usual, still capturing the request containing `filename`
<img width="1261" height="232" alt="Screenshot 2026-05-04 224358" src="https://github.com/user-attachments/assets/0090bb67-de51-416b-9de1-489ec8de8fbb" />

Then perform path traversal attack, however, it does not work 
<img width="1261" height="254" alt="Screenshot 2026-05-04 225323" src="https://github.com/user-attachments/assets/685f7355-d30c-4935-aa84-ea620bef316a" />

Maybe, I need to specify a specific file extension which is `%00`
<img width="1257" height="555" alt="Screenshot 2026-05-04 225533" src="https://github.com/user-attachments/assets/1bd132b0-aff0-432e-91a4-6c032ac1da12" />

happy Hacking!@#!@#
