## Challenge name: PHP - Filters

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/PHP-Filters](https://www.root-me.org/en/Challenges/Web-Server/PHP-Filters)

**Direct path to `/etc/passwd` is blocked. Use `php://filter` wrapper to read source code:**
```
?page=php://filter/convert.base64-encode/resource=index.php
```

**Decode the base64 output to find the source. It reveals a `config.php` file. Read it with the same technique to get credentials.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
