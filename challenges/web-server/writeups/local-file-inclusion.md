## Challenge name: Local File Inclusion

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion](https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion)

**The website has tabs using `?files=sysadm&f=index.html`. The `f` parameter is vulnerable to path traversal.**

**Use `../` to traverse directories:**
```
?files=../admin&f=index.php
```

**This reveals admin credentials in the source code.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
