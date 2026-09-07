Link : [Username enumeration via response timing](https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-response-timing)

# Overview 
Our goal is to find another pair of credential beside the given one `wiener:peter`

# Process
Let's intercept the login POST request to examine the mechanism of login services. I noticed that multiple failed attempts could lock me out for 30 mins. So I read the hint and found out this protection mechanism is based on IP.
Therefore, if I could manipulate the IP address in the request, technically, I could bypass it with bruteforce.
