## Challenge name: Local File Inclusion - Wrappers

``` Challenge Link:``` [https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion-Wrappers](https://www.root-me.org/en/Challenges/Web-Server/Local-File-Inclusion-Wrappers)

**Upload only allows JPG files. `php://filter` is blocked and `data://` is detected as attack.**

**Use the `zip://` wrapper: Create a PHP file, zip it, rename the zip to `.jpg`, upload it, then access via:**
```
?page=zip://tmp/upload/your-file.jpg%23shell
```

**Where `shell` is the name of the PHP file inside the zip archive. Commands like `shell_exec()`, `system()`, `exec()` may be blocked, but you can use `scandir()` to list files and `show_source()` to read files.**

**Use the captured flag/password to validate the challenge.**

**Thankyou.**
