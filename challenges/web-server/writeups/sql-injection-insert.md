## Challenge name: SQL injection - Insert

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Insert](https://www.root-me.org/en/Challenges/Web-Server/SQL-injection-Insert)

**The registration form is vulnerable to SQL injection via the email field. Use stacked/multiple INSERT queries:**

```
value'), ('admin', 'pass', (SELECT flag FROM flag LIMIT 1))--
```

**This creates a new user with the flag as the username/password. Login with this new user to see the flag.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
