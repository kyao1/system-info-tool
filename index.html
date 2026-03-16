"""
system_info.py
--------------
A command-line tool that collects and displays detailed system information
including OS, CPU, RAM, disk, and network details — then saves a report to a file.

Useful for IT inventory, troubleshooting, and sysadmin tasks.

Author : Konan Achille Yao
GitHub : github.com/kyao1
"""

import platform
import socket
import os
import datetime
import json


# ── Collectors ────────────────────────────────────────────────────────────────

def get_os_info() -> dict:
    """Collect operating system details."""
    return {
        "System":       platform.system(),
        "OS Name":      platform.node(),
        "Release":      platform.release(),
        "Version":      platform.version(),
        "Architecture": platform.machine(),
        "Processor":    platform.processor() or "N/A",
    }


def get_cpu_info() -> dict:
    """Collect CPU details."""
    info = {
        "Physical Cores": "N/A",
        "Total Cores":    "N/A",
        "Max Frequency":  "N/A",
        "Current Freq":   "N/A",
        "CPU Usage":      "N/A",
    }

    try:
        import psutil
        freq = psutil.cpu_freq()
        info["Physical Cores"] = str(psutil.cpu_count(logical=False))
        info["Total Cores"]    = str(psutil.cpu_count(logical=True))
        info["Max Frequency"]  = f"{freq.max:.2f} MHz" if freq else "N/A"
        info["Current Freq"]   = f"{freq.current:.2f} MHz" if freq else "N/A"
        info["CPU Usage"]      = f"{psutil.cpu_percent(interval=1)}%"
    except ImportError:
        info["Note"] = "Install psutil for detailed CPU info: pip install psutil"

    return info


def get_ram_info() -> dict:
    """Collect RAM/memory details."""
    info = {
        "Total RAM":     "N/A",
        "Available RAM": "N/A",
        "Used RAM":      "N/A",
        "RAM Usage":     "N/A",
    }

    try:
        import psutil
        vm = psutil.virtual_memory()
        info["Total RAM"]     = f"{vm.total / (1024**3):.2f} GB"
        info["Available RAM"] = f"{vm.available / (1024**3):.2f} GB"
        info["Used RAM"]      = f"{vm.used / (1024**3):.2f} GB"
        info["RAM Usage"]     = f"{vm.percent}%"
    except ImportError:
        info["Note"] = "Install psutil for RAM info: pip install psutil"

    return info


def get_disk_info() -> dict:
    """Collect disk usage details."""
    info = {}

    try:
        import psutil
        partitions = psutil.disk_partitions()
        for i, p in enumerate(partitions):
            try:
                usage = psutil.disk_usage(p.mountpoint)
                info[f"Drive {p.device}"] = {
                    "Mount":      p.mountpoint,
                    "File System": p.fstype,
                    "Total":      f"{usage.total / (1024**3):.2f} GB",
                    "Used":       f"{usage.used / (1024**3):.2f} GB",
                    "Free":       f"{usage.free / (1024**3):.2f} GB",
                    "Usage":      f"{usage.percent}%",
                }
            except PermissionError:
                info[f"Drive {p.device}"] = "Permission denied"
    except ImportError:
        info["Note"] = "Install psutil for disk info: pip install psutil"

    return info


def get_network_info() -> dict:
    """Collect network/IP details."""
    info = {
        "Hostname":    "N/A",
        "Local IP":    "N/A",
        "Public IP":   "N/A (no internet connection)",
        "MAC Address": "N/A",
    }

    try:
        info["Hostname"] = socket.gethostname()
        info["Local IP"] = socket.gethostbyname(socket.gethostname())
    except Exception:
        pass

    try:
        import psutil
        for name, addrs in psutil.net_if_addrs().items():
            for addr in addrs:
                if addr.family == psutil.AF_LINK if hasattr(psutil, 'AF_LINK') else 17:
                    info["MAC Address"] = addr.address
                    break
    except Exception:
        pass

    # Try to get public IP
    try:
        import urllib.request
        public_ip = urllib.request.urlopen("https://api.ipify.org", timeout=3).read().decode()
        info["Public IP"] = public_ip
    except Exception:
        pass

    return info


def get_python_info() -> dict:
    """Collect Python runtime info."""
    return {
        "Python Version": platform.python_version(),
        "Python Build":   " ".join(platform.python_build()),
        "Compiler":       platform.python_compiler(),
    }


# ── Report builder ────────────────────────────────────────────────────────────

def collect_all() -> dict:
    """Run all collectors and return full report."""
    return {
        "timestamp":  datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
        "os":         get_os_info(),
        "cpu":        get_cpu_info(),
        "ram":        get_ram_info(),
        "disk":       get_disk_info(),
        "network":    get_network_info(),
        "python":     get_python_info(),
    }


# ── Display ───────────────────────────────────────────────────────────────────

def color(text, code):
    return f"\033[{code}m{text}\033[0m"

SECTION_COLOR = "96"   # cyan
KEY_COLOR     = "97"   # white
VAL_COLOR     = "93"   # yellow

def print_section(title: str, data: dict, indent: int = 0) -> None:
    pad = "  " * indent
    print(f"\n{pad}{color(f'── {title} ', SECTION_COLOR)}")
    print(f"{pad}{'─' * (40 - indent * 2)}")
    for key, val in data.items():
        if isinstance(val, dict):
            print_section(key, val, indent + 1)
        else:
            print(f"{pad}  {color(key + ':', KEY_COLOR):<28} {color(str(val), VAL_COLOR)}")


def print_report(report: dict) -> None:
    print()
    print(color("╔══════════════════════════════════════╗", "96"))
    print(color("║       SYSTEM INFORMATION REPORT      ║", "96"))
    print(color("║       by Konan Achille Yao            ║", "96"))
    print(color("╚══════════════════════════════════════╝", "96"))
    print(f"  {color('Collected at:', '90')} {report['timestamp']}")

    sections = [
        ("OPERATING SYSTEM", report["os"]),
        ("CPU",              report["cpu"]),
        ("MEMORY (RAM)",     report["ram"]),
        ("DISK",             report["disk"]),
        ("NETWORK",          report["network"]),
        ("PYTHON RUNTIME",   report["python"]),
    ]

    for title, data in sections:
        print_section(title, data)

    print()
    print(color("═" * 42, "90"))
    print()


# ── Save to file ──────────────────────────────────────────────────────────────

def save_report(report: dict, fmt: str = "txt") -> str:
    """Save report to a .txt or .json file. Returns the filename."""
    ts       = datetime.datetime.now().strftime("%Y%m%d_%H%M%S")
    hostname = report["network"].get("Hostname", "unknown")
    filename = f"sysinfo_{hostname}_{ts}.{fmt}"

    if fmt == "json":
        with open(filename, "w") as f:
            json.dump(report, f, indent=2)
    else:
        with open(filename, "w") as f:
            f.write(f"SYSTEM INFORMATION REPORT\n")
            f.write(f"Generated: {report['timestamp']}\n")
            f.write(f"By: Konan Achille Yao\n")
            f.write("=" * 50 + "\n\n")

            def write_section(title, data, indent=0):
                pad = "  " * indent
                f.write(f"{pad}{title}\n")
                f.write(f"{pad}{'-' * 30}\n")
                for key, val in data.items():
                    if isinstance(val, dict):
                        write_section(key, val, indent + 1)
                    else:
                        f.write(f"{pad}  {key:<25} {val}\n")
                f.write("\n")

            sections = [
                ("OPERATING SYSTEM", report["os"]),
                ("CPU",              report["cpu"]),
                ("MEMORY (RAM)",     report["ram"]),
                ("DISK",             report["disk"]),
                ("NETWORK",          report["network"]),
                ("PYTHON RUNTIME",   report["python"]),
            ]
            for title, data in sections:
                write_section(title, data)

    return filename


# ── Entry point ───────────────────────────────────────────────────────────────

def main():
    print(color("\n  Collecting system information...", "90"))
    report = collect_all()
    print_report(report)

    # Ask to save
    try:
        choice = input("  Save report to file? (txt / json / no): ").strip().lower()
    except (KeyboardInterrupt, EOFError):
        choice = "no"

    if choice in ("txt", "json"):
        filename = save_report(report, fmt=choice)
        print(color(f"\n  ✔ Report saved to: {filename}\n", "92"))
    else:
        print(color("\n  Report not saved. Exiting.\n", "90"))


if __name__ == "__main__":
    main()
