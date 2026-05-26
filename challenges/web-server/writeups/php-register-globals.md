## Challenge name: PHP - register globals

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/PHP-register-globals](https://www.root-me.org/en/Challenges/Web-Server/PHP-register-globals)

**The server has `register_globals` enabled, which allows injecting superglobal variables via URL parameters.**

**Inject `$_SESSION` directly:**
```
/index.php?_SESSION[logged]=1
```

**This sets the session variable `logged` to 1, bypassing authentication.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
