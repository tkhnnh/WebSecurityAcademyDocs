Link: [DOM XSS in jQuery anchor href attribute sink using location.search source](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink)
Difficulty: Apprentice 

# Goal
Change the URL of `back` button to trigger `document.cookie` alert

# Action
The site exposes the query which changing the page based on the `back` button.
```

                            $(function() {
                                $('#backLink').attr("href", (new URLSearchParams(window.location.search)).get('returnPath'));
                            });

```
So the default is `\` which redirect back to the mainpage, by manipulating it to 
```
javascript:alert(document.cookie)
```
By inserting the payload to `returnPath`, the URL href will be changed.
The payload triggers javascript alert to display the cookie of the page with the exposed query by clicking on the `back` button since the URL of its has been changed.

Happy Hacking!!@#
