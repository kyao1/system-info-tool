# ⚙️ System Information Tool

A command-line Python tool that collects detailed system information — OS, CPU, RAM, disk, and network — and saves a report to a `.txt` or `.json` file.

> **Project by Konan Achille Yao** | B.S. Computer Science @ IU Indianapolis (Luddy School)

🔴 **[Live Demo](https://kyao1.github.io/system-info-tool)** &nbsp;·&nbsp; 🐍 **Python 3.6+, no external libraries required for basic use**

---

## What It Does

IT support and sysadmin teams constantly need to inventory machines — this tool automates that. Run it on any computer and instantly get a full snapshot of the system, ready to save and share.

```
╔══════════════════════════════════════╗
║       SYSTEM INFORMATION REPORT      ║
║       by Konan Achille Yao            ║
╚══════════════════════════════════════╝
  Collected at: 2026-03-11 14:32:07

── OPERATING SYSTEM
────────────────────────────────────────
  System:                Windows
  OS Name:               DESKTOP-KY401
  Release:               11
  Architecture:          AMD64
  Processor:             Intel64 Family 6

── MEMORY (RAM)
────────────────────────────────────────
  Total RAM:             16.00 GB
  Available RAM:         9.43 GB
  Used RAM:              6.57 GB
  RAM Usage:             41.1%

── NETWORK
────────────────────────────────────────
  Hostname:              DESKTOP-KY401
  Local IP:              192.168.1.105
  Public IP:             98.xxx.xxx.xxx

  Save report to file? (txt / json / no): txt
  ✔ Report saved to: sysinfo_DESKTOP-KY401_20260311_143207.txt
```

---

## How to Run

**Basic (no installs needed):**
```bash
git clone https://github.com/kyao1/system-info-tool.git
cd system-info-tool
python3 system_info.py
```

**With full CPU & RAM details (recommended):**
```bash
pip install psutil
python3 system_info.py
```

---

## Features

| Feature | Details |
|---|---|
| OS Info | System, release, version, architecture |
| CPU Info | Core count, frequency, usage % (requires psutil) |
| RAM Info | Total, used, available, usage % (requires psutil) |
| Disk Info | All drives, mount points, free space (requires psutil) |
| Network Info | Hostname, local IP, public IP, MAC address |
| Save Report | Export to `.txt` or `.json` with timestamp + hostname |

---

## What I Learned

- Using Python's built-in `platform` and `socket` modules
- Optional dependency handling with `try/except ImportError`
- File I/O — writing structured `.txt` and `.json` reports
- Working with `psutil` for real hardware data
- How IT teams collect system inventory in real environments

---

## Skills Demonstrated

`Python` · `platform module` · `socket module` · `psutil` · `File I/O` · `JSON` · `IT Systems` · `Sysadmin concepts`

---

## Author

**Konan Achille Yao**
- LinkedIn: [linkedin.com/in/konanyao](https://linkedin.com/in/konanyao)
- CompTIA A+ certified | A.S. Cybersecurity & Information Assurance (GPA 3.9) | IU Indianapolis CS student
