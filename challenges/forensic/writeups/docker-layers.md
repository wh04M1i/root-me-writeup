## Challenge name: Docker Layers

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Docker-layers](https://www.root-me.org/en/Challenges/Forensic/Docker-layers)

**We were provided a `.tar` file containing a Docker image. The goal is to recover the encrypted flag and find the password used.**

### Step 1: Analyze the Docker history

Using `container-diff` to analyze the Docker image layers:

```
container-diff analyze -t history ch29.tar
```

The history reveals:
```dockerfile
/bin/sh -c #(nop) ADD file:d2abf27fe2e8b0b5f4da68c018560c73e11c53098329246e3e6fe176698ef941 in /
/bin/sh -c #(nop)  CMD ["bash"]
/bin/sh -c apt update -y
/bin/sh -c apt install -y curl openssl
/bin/sh -c #(nop) COPY file:2ca89eb39686ffcc3d2d87bbc9293559252cff471f80c2ed5d024b214f9a6fa3 in /
/bin/sh -c echo -n $(curl -s https://pastebin.com/raw/P9Nkw866) | openssl enc -aes-256-cbc -iter 10 -pass pass:$(cat /pass.txt) -out flag.enc
/bin/sh -c rm /pass.txt
```

The flag was fetched from pastebin, encrypted with AES-256-CBC using a password from `/pass.txt`, and then `/pass.txt` was deleted.

### Step 2: Extract the layers

Untar the file and explore the layers:

```
tar -xf ch29.tar
```

Extract all `.tar` layer files recursively. After extracting all layers, find `flag.enc` and `pass.txt`:

```
cat pass.txt
d4428185a6202a1c5806d7cf4a0bb738a05c03573316fe18ba4eb5a21a1bc8ea
```

### Step 3: Decrypt the flag

Use `openssl` to decrypt `flag.enc` with the recovered password:

```
openssl enc -aes-256-cbc -iter 10 -d -in flag.enc -out flag.txt
cat flag.txt
```

The flag is revealed after decryption.
