URL: [Basic SSRF against another back-end system](https://portswigger.net/web-security/learning-paths/ssrf-attacks/ssrf-attacks-common-ssrf-attacks/ssrf/lab-basic-ssrf-against-backend-system#)

<img width="1256" height="346" alt="Screenshot 2026-04-15 122900" src="https://github.com/user-attachments/assets/79886c7d-1472-4dfc-afc5-199709aec816" />

I do the same thing like the [previous lab](https://github.com/tkhnnh/WebSecurityAcademyDocs/blob/main/SSRF/Basic%20SSRF%20against%20the%20local%20server.md)

But the goal is to find the last octet of the targeted address first, to achive that I use Intruder function of burpsuite

<img width="1594" height="848" alt="Screenshot 2026-04-15 122845" src="https://github.com/user-attachments/assets/668d2118-27ee-4401-98ca-ca55cd8dc2dd" />
By setting up the payload, the list of numbers and here is the result

<img width="1402" height="150" alt="Screenshot 2026-04-15 123236" src="https://github.com/user-attachments/assets/c7abb714-7df4-4f4f-817b-25762d3ad3bc" />
the last octet is 116

Now I do the same thing as the last lab but rather than `localhost` I replace that with the targeted IP address `http://192.168.0.116:8080/admin/delete?username=carlos`

<img width="1255" height="292" alt="Screenshot 2026-04-15 123425" src="https://github.com/user-attachments/assets/ca2eec94-f183-4900-9a36-17ceafe1e5ac" />

happy hacking!@$!@$
