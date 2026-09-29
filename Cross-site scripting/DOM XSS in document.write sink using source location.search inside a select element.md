Link: [DOM XSS in document.write sink using source location.search inside a select element](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink-inside-select-element)
Difficulty: Practitioner


# Action 
From inspect page, I find this script
```

                                var stores = ["London","Paris","Milan"];
                                var store = (new URLSearchParams(window.location.search)).get('storeId');
                                document.write('<select name="storeId">');
                                if(store) {
                                    document.write('<option selected>'+store+'</option>');
                                }
                                for(var i=0;i<stores.length;i++) {
                                    if(stores[i] === store) {
                                        continue;
                                    }
                                    document.write('<option>'+stores[i]+'</option>');
                                }
                                document.write('</select>');

```
This shows me that there is another parameter beside `productId` which is `storeId`. 
<img width="1509" height="910" alt="Screenshot 2026-09-29 at 2 23 33 pm" src="https://github.com/user-attachments/assets/dd0362ea-a4f3-46d6-8e0f-f64114884e4b" />

The image above show that I can manipulate the `storeId` parameter to enter the payload
```
&storeId=2;<script>alert(1)</script>
```
The reason why I placed a semi colon there to force the result of the unit return first then execute the payload script that I insert in, since it will be innerHTML function updates in the HTML page 
<img width="1506" height="910" alt="Screenshot 2026-09-29 at 2 32 04 pm" src="https://github.com/user-attachments/assets/423fb5e4-fab7-4874-b56a-157920c7953c" />


Happy Hacking@!#!@!#
