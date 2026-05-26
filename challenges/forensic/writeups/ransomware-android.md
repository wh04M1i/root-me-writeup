## Challenge name: Ransomware Android

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Ransomware-Android](https://www.root-me.org/en/Challenges/Forensic/Ransomware-Android)

**Recover encrypted files from an Android tablet compromised by ransomware.**

### Step 1: Static analysis with jadx

Decompile the provided APK (`org.simplelocker-1.apk`) using `jadx`:

```
jadx org.simplelocker-1.apk
```

From `AndroidManifest.xml`, the app has:
- Automatic startup on boot
- Access to external storage
- Background service execution

The entry point is `org.simplelocker.Main`, which starts `MainService`.

### Step 2: Analyze the encryption classes

In `FilesEncryptor.java`, encrypted files are saved with a `.enc` extension.

In `AesCrypt.java`, the constructor derives the encryption key by hashing a hardcoded password with SHA-256:

```java
public static final String CIPHER_PASSWORD = "mcsTnTld1dDn";
```

The encryption uses AES in CBC mode with a static IV (16 zero bytes) and PKCS7 padding.

### Step 3: Write a decryption script

```python
from Crypto.Cipher import AES
from Crypto.Hash import SHA256

password = b"mcsTnTld1dDn"
key = SHA256.new(password).digest()
iv = b"\x00" * 16

cipher = AES.new(key, AES.MODE_CBC, iv)

with open("confidentiel.jpg.enc", "rb") as f:
    encrypted = f.read()

decrypted = cipher.decrypt(encrypted)

with open("confidentiel.jpg", "wb") as f:
    f.write(decrypted)
```

### Step 4: Verify and get the flag

Run the script and verify the output:

```
file confidentiel.jpg
```

Open the recovered JPEG image to reveal the flag.
