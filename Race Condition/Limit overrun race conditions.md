Link: [Limit overrun race conditions](https://portswigger.net/web-security/race-conditions/lab-race-conditions-limit-overrun)
Difficulty: Apprentice

# Definition
What is a race condition attack?

It occurs when websites process requests concurrently without adequate safeguards. The result of this implication is leading to multiple distinct threads interacting with the same data at the same time, resulting in a "collision" that causes unintended behaviour in the application

# Recon
I notice that the site gives me 20%  promotion code, so my goal is to apply that code to the item `Lightweight L33t Leather Jacket` until I can get that item for free which are 5 requests concurrently.
First, the item need to be in the cart, then, head to the checkout section. Then turning on the intercept requests on, to capture the request for performing an attack.

<img width="1919" height="842" alt="Screenshot_20261030_173027" src="https://github.com/user-attachments/assets/0a4ff85e-bab9-45b6-9465-f52ef7124934" />

I got the request in the Burp Repeater already, now let's create a group and send them all at one.
<img width="766" height="680" alt="Screenshot_20261030_173401" src="https://github.com/user-attachments/assets/ddb1606d-8c99-42b7-8c0d-361a599a6889" />

Then choose `send group in parallel` to execute the attack.
NOTE: Create as many requests as possible because some of the requests will be cancelled out due to the race (for me, 200 more requests)

<img width="1878" height="936" alt="Screenshot_20261030_220301" src="https://github.com/user-attachments/assets/e3382dd1-ca40-4939-96b3-286051deb31c" />

Happy Hacking@!$!@#4

