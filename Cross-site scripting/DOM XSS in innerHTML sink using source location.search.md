Link: [DOM XSS in innerHTML sink using source location.search](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)
Difficulty: Apprentice 

# How it works
Let's have a look at the script:
```
                            function doSearchQuery(query) {
                                document.getElementById('searchMessage').innerHTML = query;
                            }
                            var query = (new URLSearchParams(window.location.search)).get('search');
                            if(query) {
                                doSearchQuery(query);
                            }

```

So the function will take the input source and parse it directly into the HTML page with `innerHTML` function which is very bad since attacker could abuse that to insert XSS payload
# Action
Let's test the search box.
<img width="1508" height="786" alt="Screenshot 2026-09-29 at 2 13 56 pm" src="https://github.com/user-attachments/assets/f709fe4a-98f4-4bef-ae35-818a748d74d9" />
I can easily notice that whatever I inputed will be place inside the `<span>` tag, and also cannot escape the input text, I already tested with `<script>` but it does not trigger. Then, this is the payload to exploit
```
<img src=x onerror=alert(1)>
```

it works perfectly. Happy Hacking@!@!#!..
