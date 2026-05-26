## Challenge name: SQL injection - Authentication GBK

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Authentication-GBK](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Authentication-GBK)

**The application uses `addslashes()` which escapes quotes by adding backslashes. However, with GBK character encoding, certain byte sequences can eat the backslash.**

**When `%81` is followed by `'` (which becomes `\'` after addslashes, i.e., `%5C%27`), the sequence `%81%5C` forms a valid GBK Chinese character, consuming the backslash and leaving the `'` unescaped.**

**Payload:**
```
login=admin%81'+or+1=1--+-&password=1
```

**This bypasses `addslashes()` and injects the SQL.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
