## Challenge name: Oh My Grub

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Oh-My-Grub](https://www.root-me.org/en/Challenges/Forensic/Oh-My-Grub)

**Your company lost access to an old server. Recover the files by bypassing the boot loader.**

### Step 1: Extract files

Extract the provided archive:

```bash
unzip file.zip
tar -xf file.tar
```

This gives a virtual disk image: `root-disk001.vmdk` and `root.ovf`.

### Step 2: Boot the VM

Boot the VMDK using QEMU:

```bash
qemu-system-x86_64 root-disk001.vmdk -m 1280
```

### Step 3: Edit GRUB boot parameters

When the GRUB boot menu appears, select the first option and press `e` to edit the boot parameters.

Find the line starting with `linux`. By default it ends with `ro quiet` (read-only root, boot messages hidden).

Replace it with:

```
rw init=/bin/bash
```

This mounts the root filesystem as read-write and starts a bash shell directly instead of the normal init process.

### Step 4: Get the flag

Press `F10` or `Ctrl+X` to boot with the modified parameters. You will get a root shell immediately.

List files and find the flag:

```bash
ls -la
cat flag.txt
```
