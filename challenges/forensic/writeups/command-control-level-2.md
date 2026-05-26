## Challenge name: Command & Control - level 2

```Challenge Link:``` [https://www.root-me.org/en/Challenges/Forensic/Command-Control-level-2](https://www.root-me.org/en/Challenges/Forensic/Command-Control-level-2)

**Recover the workstation hostname from a memory dump using Volatility.**

### Step 1: Extract and identify the image

Download and extract the memory dump:

```bash
tar -xvf ch2.tbz2
```

Identify the OS profile using Volatility:

```bash
volatility -f ch2.dmp imageinfo
```

The suggested profile is `Win7SP1x86_23418` (Windows 7 SP1 32-bit).

### Step 2: List registry hives

```bash
volatility -f ch2.dmp --profile=Win7SP1x86_23418 hivelist
```

Look for the SYSTEM registry hive. In this case:
- `0x8b21c008` → `\REGISTRY\MACHINE\SYSTEM`

### Step 3: Extract the computer name

The computer name is stored in the registry at `ControlSet001\Control\ComputerName\ComputerName`:

```bash
volatility -f ch2.dmp --profile=Win7SP1x86_23418 printkey -o 0x8b21c008 -K 'ControlSet001\Control\ComputerName\ComputerName'
```

Output:
```
REG_SZ ComputerName : (S) WIN-ETSA91RKCFP
```

### Step 4: Flag

The workstation hostname is the flag.

**Flag:** `WIN-ETSA91RKCFP`
