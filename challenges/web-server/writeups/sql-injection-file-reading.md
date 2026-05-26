## Challenge name: SQL injection - File reading

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-File-reading](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-File-reading)

**Determine 4 columns via `ORDER BY`. Find the `member` table with columns: `member_id`, `member_login`, `member_password`, `member_email`.**

**Extract all data:**
```
1 UNION SELECT 1, member_login, member_password, member_email FROM member--
```

**The password may be encoded (e.g., SHA1 hash XOR'd with its own base64). Reverse the encoding to get the plaintext password.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
