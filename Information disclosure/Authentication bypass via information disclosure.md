Link: [Authentication bypass via information disclosure]()
Difficulty: Apprentice

# Recon
The lab informs that there is a custom HTTP header to used, so I will try every header with the login request to see whether and I found that the TRACE method works

# TRACE 

The `TRACE` HTTP method performs a message loop-back test along the path to the target resource.

The final recipient of the request should reflect the message as received (excluding any field that may hold sensitive data) back to the client as the message body of a `200 OK` response. 

# Action
Attempting to access the admin page would result in `401 Unauthorized`
<img width="1534" height="717" alt="Screenshot_20261018_103828" src="https://github.com/user-attachments/assets/80da26fc-dbaa-4b25-8bb3-02fbed565bf5" />

Let's try the `TRACE` method
<img width="1535" height="494" alt="Screenshot_20261018_104004" src="https://github.com/user-attachments/assets/cfe083de-abf9-4529-870c-319082f503e6" />


Notice that there is a new header `X-Custom-IP-Authorization` which includes the IP of the sender, by modifying it to `localhost`  which route back the http traffic to local so Authorization would be passed easily.
<img width="1529" height="710" alt="Screenshot_20261018_104351" src="https://github.com/user-attachments/assets/85d6fb6c-7489-419d-a734-1f0c40129401" />

Now it's time to delete `carlos`
<img width="1537" height="715" alt="Screenshot_20261018_104431" src="https://github.com/user-attachments/assets/1a77fa3e-2de2-4f93-b557-12dd0ef58308" />


Happy Hacking!@#$!@$#@
