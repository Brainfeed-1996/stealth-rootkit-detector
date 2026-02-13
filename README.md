# Stealth Rootkit Detector

Advanced Linux Kernel Module (LKM) for identifying malicious hooks in the system call table.

## Features

- **Kernel Memory Forensics**: Detect syscall table modifications
- **Integrity Checking**: Verify syscall addresses against kernel text segment
- **Hook Detection**: Identify common rootkit techniques
- **Logging**: Kernel log output via dmesg

## Architecture

```
stealth-rootkit-detector/
├── detector.c       # Kernel module implementation
├── Makefile         # Build configuration
├── src/             # Additional source files
├── README.md        # This file
└── .github/
    └── workflows/
        └── ci.yml   # CI/CD pipeline
```

## Usage

### Build

```bash
make
```

### Load Module

```bash
sudo insmod detector.ko
```

### Check Results

```bash
dmesg | tail
```

### Unload

```bash
sudo rmmod detector
```

## Detection Method

The detector performs memory forensics by:
1. Locating the `sys_call_table` via kallsyms
2. Checking each syscall address against kernel text segment boundaries
3. Flagging addresses outside `_text` and `_etext` as potential hooks

## Requirements

- Linux kernel headers
- GCC with kernel module support
- sudo/root for loading modules

## Disclaimer

**Educational Use Only**: This tool is for security learning and authorized testing only.

## License

MIT
