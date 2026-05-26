## Challenge name: Logs analysis - web attack

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Logs-analysis-web-attack](https://www.root-me.org/en/Challenges/Forensic/Logs-analysis-web-attack)

**Extract a password from web server logs using a blind SQL injection timing attack analysis.**

### Step 1: Analyze the log file

The web server log contains SQL injection attempts. The `order` parameter contains base64-encoded values, and there are URL-encoded parameters.

Decode the URL-encoded values and the base64 `order` parameter to reveal the SQL queries:

```sql
ORDER BY ASC
CASE WHEN 1 THEN TRUE
ASCII()
CHAR()
BIN()
SUBSTRING(string, start, length)
CONCAT(exp1, exp2, exp3)
FIELD(value, val1, val2, val3)
```

### Step 2: Understand the attack pattern

The query interpretation:
1. From the `members` table, extract the leftmost character of the password for the account with `id = 1`
2. Convert the value: char → int → binary
3. Extract the leftmost 2 bits
4. If the value is `00`, respond immediately; otherwise sleep (2, 4, or 6 seconds)

### Step 3: Extract the flag from timing differences

The response times in the log correspond to each bit of the password. By analyzing the timing differences:

- 0 seconds → bits `00`
- 2 seconds → bits `01`
- 4 seconds → bits `10`
- 6 seconds → bits `11`

Write a Python script to parse the log timestamps and reconstruct the password:

```python
f = open("log.txt", "r")
sec = []

for line in f:
    sec.append(int(line.split(" ")[3].split(":")[-1]))
f.close()

secStr = ""
for i in range(len(sec) - 1):
    secRst = sec[i+1] - sec[i]
    if secRst < 0:
        secRst += 60
    if i % 4 == 0:
        secStr += "\n"
    secStr += str(secRst)

# Convert timing to binary: 0→00, 2→01, 4→10, 6→11
# Then convert binary to ASCII
```

Run the script to reconstruct the flag from the timing-based side-channel attack.
