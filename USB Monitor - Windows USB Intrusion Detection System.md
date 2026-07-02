🔒 USB Monitor - Windows USB Intrusion Detection System

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [System Requirements](#system-requirements)
- [Installation](#installation)
- [Build Instructions](#build-instructions)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Logging](#logging)
- [Security Report](#security-report)
- [Future Improvements](#future-improvements)
- [Skills Demonstrated](#skills-demonstrated)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Author](#author)

## 📖 Overview

**USB Monitor** is a Windows-based USB Intrusion Detection System (IDS) developed in C++. It continuously monitors USB storage devices connected to a computer and automatically performs security actions whenever removable media is detected.

The application combines Windows Device Notifications with periodic drive polling to ensure reliable USB detection even if Windows notifications fail.

### 🎯 Purpose

This tool demonstrates:
- Endpoint security concepts
- USB monitoring techniques
- Digital forensics practices
- Automated incident response

> **⚠️ Educational Notice:** This project is intended for educational and research purposes only. Use in production environments requires additional security hardening and compliance review.

## 💻 System Requirements

### Hardware
- x86 or x64 architecture
- USB ports (for testing)

### Software
| Requirement | Minimum Version |
|-------------|-----------------|
| Windows OS | Windows 7 SP1 / Windows Server 2008 R2 |
| Visual Studio | 2019 or 2022 Community/Professional |
| Windows SDK | 10.0 or later |
| C++ Standard | C++11 or later |

### Permissions Required
- **Administrator privileges** - Required for:
  - Registering device notifications
  - Locking workstation
  - Accessing drive serial numbers
  - Writing to security logs

  ## 📥 Installation

### Option 1: Download Pre-built Binary
1. Download the latest release from the [Releases](https://github.com/yourusername/USB_Monitor/releases) page
2. Extract the ZIP file to your preferred location
3. Run `USB_Monitor.exe` as Administrator

### Option 2: Build from Source
1. Clone the repository:
   ```bash
   git clone https://github.com/davidwairimu-netsec/USB_Monitor.git
   cd USB_Monitor

Open the solution in Visual Studio:
USB_Monitor.sln

Build the solution (Ctrl+Shift+B)
Run as Administrator (Right-click → "Run as administrator")

## Step 6: Build Instructions

Detailed compilation guide:

```markdown
## 🔧 Build Instructions

### Using Visual Studio IDE

1. **Open the project**
   - Launch Visual Studio
   - File → Open → Project/Solution
   - Navigate to `USB_Monitor.sln`

2. **Select configuration**
   - Debug (for testing) or Release (for production)
   - x86 or x64 architecture

3. **Build**
   - Build → Build Solution (or Ctrl+Shift+B)

4. **Output location**

Debug: ./USB_Monitor/Debug/USB_Monitor.exe
Release: ./USB_Monitor/Release/USB_Monitor.exe

Required Libraries
All required libraries are included with Windows SDK:
windows.h - Windows API
winuser.h - Window management
setupapi.h - Device management
fileapi.h - File operations
shlwapi.h - Shell utilities

## Step 7: Usage

## 🚀 Usage

### Starting the Monitor

1. **Run as Administrator** (Required)

Right-click USB_Monitor.exe → Run as administrator

2. **Expected behavior:**
- A window will appear briefly then hide (system tray)
- Log file `usb_access_log.txt` is created
- Monitor starts watching for USB devices

3. **Testing the monitor:**
- Insert any USB storage device
- Observe the workstation locks automatically
- Check `usb_access_log.txt` for logged events

### Running in Background

The application runs as a hidden window. To stop it:
1. Open Task Manager (Ctrl+Shift+Esc)
2. Find `USB_Monitor.exe`
3. End the process

### Example Session
[2026-06-30 14:22:10] [ALERT] USB INSERTION DETECTED
[2026-06-30 14:22:11] [INFO] Drive: E:
[2026-06-30 14:22:11] [INFO] Label: KINGSTON_16GB
[2026-06-30 14:22:12] [INFO] Serial: 0A1B2C3D
[2026-06-30 14:22:12] [INFO] File System: FAT32
[2026-06-30 14:22:15] [ALERT] Workstation locked
[2026-06-30 14:22:30] [REMOVAL] USB Drive E: removed

Step 8: Configuration

## ⚙️ Configuration

### Current Settings (Hardcoded)

| Setting | Value | Description |
|---------|-------|-------------|
| Polling Interval | 2 seconds | Backup detection frequency |
| File Types Inspected | TXT, LOG, CSV, XML, JSON, CFG, INI | Scannable file extensions |
| Max Files Scanned | 3 | Per USB insertion |
| Snippet Size | 100 characters | Per file sample |
| Log Rotation | None | Appends to single file |

### Future Configuration Options

A `config.ini` file is planned for future releases:

```ini
[Settings]
PollingInterval = 2000
MaxFilesToScan = 5
SnippetSize = 200
LockWorkstation = true
LogToEventViewer = false
WhitelistEnabled = false
WhitelistFile = whitelist.txt

Note: Configuration via config file is not yet implemented. Settings are currently hardcoded in the source.


## Step 9: Troubleshooting

Add common issues and solutions:

```markdown
## 🔍 Troubleshooting

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Program doesn't start | Not running as Administrator | Right-click → Run as administrator |
| No USB detection | Missing device notifications | Reboot and try again |
| Can't lock workstation | Insufficient privileges | Run as Administrator |
| Log file not created | Write permission denied | Check folder permissions |
| USB not detected | Driver issues | Update USB drivers |

### Known Limitations

- ❌ Single-user only
- ❌ No whitelist support
- ❌ Limited file type scanning
- ❌ No network alerting
- ❌ No encryption for logs

### Debug Mode

To enable debug output, uncomment in `USB_Monitor.cpp`:

```cpp
// Uncomment for verbose logging
// #define DEBUG_MODE

Crash Handling
If the application crashes, check:

Windows Event Viewer → Windows Logs → Application

Look for errors with source "USB_Monitor"

Check if antivirus software is blocking the program

## Step 10: License

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Summary
- ✅ Commercial use allowed
- ✅ Modification allowed  
- ✅ Distribution allowed
- ✅ Private use allowed
- ❌ Liability limitation
- ❌ Warranty disclaimer

### Educational Use
This software is provided for **educational and research purposes only**. The author is not responsible for:
- Data loss or corruption
- System instability
- Security breaches
- Misuse of the software



## 👨‍💻 Author

**David K. Wairimu**
- 🔐 Cybersecurity | Digital Forensics | Network Security
- 💻 C++ Developer | Windows API Specialist

### Connect
- 📧 Email: [makincisco@gmail.com](makincisco@gmail.com)
- 🔗 LinkedIn: [linkedin.com/in/david-wairimu-54b739256](https://linkedin.com/in/david-wairimu-54b739256)
- 🐙 GitHub: [github.com/davidwairimu-netsec](https://github.com/davidwairimu-netsec)

## 🙏 Acknowledgments

- Windows SDK documentation
- Microsoft Device Notification API
- Open-source community
- Cybersecurity mentors and instructors

## 📚 References

- [Microsoft Win32 API Documentation](https://docs.microsoft.com/en-us/windows/win32/)
- [Windows Device Notifications](https://docs.microsoft.com/en-us/windows/win32/devio/registering-for-device-notifications)
- [USB Device Class Specifications](https://www.usb.org/document-library)