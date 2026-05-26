## Challenge name: Capture This

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Capture-this](https://www.root-me.org/en/Challenges/Forensic/Capture-this)

**An employee lost his Keepass password. A cropped screenshot is the only clue.**

### Step 1: Extract and examine files

The challenge provides a `.zip` file containing:
- A PNG image (screenshot of passwords)
- A `.kdbx` file (KeePass database)

The `.kdbx` file is encrypted and requires a master password.

### Step 2: Analyze the image

The screenshot shows a list of passwords, but none of them work for the KeePass database. Upon close inspection, the letter `k` is peeking from the right edge — the image was cropped.

### Step 3: Exploit aCropalypse vulnerability

The image was cropped using a tool vulnerable to **aCropalypse (CVE-2023-28303)**. This vulnerability occurs when screenshot/cropping tools fail to truncate the original image data after cropping — the cropped file retains the original pixel data beyond the new IEND marker.

Use a Python script to restore the original image by recovering the leftover pixel data:

```python
#!/usr/bin/env python3
import struct
import sys
import zlib
import os

def restore_png(input_file):
    with open(input_file, 'rb') as f:
        data = f.read()
    
    # Find IEND
    iend_idx = data.find(b'IEND')
    if iend_idx == -1:
        print("No IEND found")
        return
    
    # Everything after the first IEND chunk might be leftover original data
    restored_data = data[:iend_idx + 12]  # Keep up to IEND
    
    # But we need to also scan for additional IDAT chunks after IEND
    # The actual leftover data is after the new IEND
    leftover = data[iend_idx + 12:]
    
    # Find IHDR in the leftover to reconstruct
    ihdr_idx = leftover.find(b'IHDR')
    if ihdr_idx == -1:
        print("No hidden IHDR found")
        return
    
    # Extract the original full image from the leftover data
    original_data = leftover[ihdr_idx - 4:]  # Include chunk length
    with open('/tmp/restored.png', 'wb') as f:
        f.write(b'\x89PNG\r\n\x1a\n' + original_data)
    print("Restored image saved to /tmp/restored.png")

if __name__ == '__main__':
    restore_png(sys.argv[1])
```

### Step 4: Find the master password

The restored image reveals the full uncropped screenshot showing the KeePass master password: `-=b9w9h^+j%\x-rMPUqv9Vv`@X%*=a`

### Step 5: Open the KeePass database

Use the recovered password to unlock the `.kdbx` file and retrieve the flag.

**Flag:** `@cropalypse_vuln_is_impressive`
