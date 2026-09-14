Link: [Broken brute-force protection, IP block](https://portswigger.net/web-security/authentication/password-based/lab-broken-bruteforce-protection-ip-block)

So I tried to login with username `carlos` with multiple failed attempts and the site started blocking me. Even I change my IP address for the request it would not work, then I read this documenataion.

Reference:
[Flawed brute-force protection](https://portswigger.net/web-security/authentication/password-based)

"The counter for the number of failed attempts resets if the IP owner logs in successfully. This means an attacker would simply have to log in to their own account every few attempts to prevent this limit from ever being reached."

which means that in this lab I just need to append credential of `wiener:peter` before each pair of credentials in the wordlist to bypass the filter

I captured the Login request with `POST /Login` and move it to Intruder for brute-forcing task.
Then I created a small python script to print out the 100 times username lists and password candidate list  (ensure that username `wiener` and its password always go before `carlos` and `carlos`'s potential password)
```
print("This is the payload for 1st position: ")

for i in range(0,101):
	print("wiener")
	print("carlos")

print("This is the payload for 2nd position: ") 
with open("wordlist.txt", "r") as file:
	for line in file:
		print("peter")
		print(line.rstrip())
```

As I specified 2 positions because in the Intruder tab, I would set them in the according spot.
<img width="1477" height="704" alt="Screenshot 2026-09-14 at 3 26 15 pm" src="https://github.com/user-attachments/assets/ce14068a-8f35-46e6-9f95-b16f114c5893" />

By using the Pitchfork Attack mode could help me brute-force multiple payloads with multiple positions simultaneously. By Appending the credential of `wiener` before `carlos`, it helps me bypass the filter successfully and keeps reseting the counter of the blocking filter.

<img width="1476" height="812" alt="Screenshot 2026-09-14 at 3 26 32 pm" src="https://github.com/user-attachments/assets/22662b83-c067-4f33-8174-ab95e18f87d8" />

Happy hacking@$!@$#
