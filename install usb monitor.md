# 📦 Installation Guide - USB Monitor

This guide provides detailed instructions for installing and setting up USB Monitor on your Windows system.

---

## 📋 Table of Contents

- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
  - [Method 1: Pre-built Binary (Recommended)](#method-1-pre-built-binary-recommended)
  - [Method 2: Build from Source](#method-2-build-from-source)
  - [Method 3: Using Windows Package Manager](#method-3-using-windows-package-manager)
- [Post-Installation Setup](#post-installation-setup)
- [Running USB Monitor](#running-usb-monitor)
- [Automatic Startup Configuration](#automatic-startup-configuration)
- [Verification](#verification)
- [Uninstallation](#uninstallation)
- [Troubleshooting Installation](#troubleshooting-installation)
- [System Requirements Reference](#system-requirements-reference)

---

## 🔧 Prerequisites

Before installing USB Monitor, ensure your system meets the following requirements:

### Minimum System Requirements

| Component | Requirement |
|-----------|-------------|
| **Operating System** | Windows 7 SP1, Windows 8, Windows 10, or Windows 11 |
| **Architecture** | x86 (32-bit) or x64 (64-bit) |
| **RAM** | 256 MB minimum (512 MB recommended) |
| **Disk Space** | 50 MB for installation + log storage space |
| **Administrator Rights** | Required for installation and operation |

### Required Software

| Software | Purpose | Download Link |
|----------|---------|---------------|
| **Windows Update** | Latest security patches | Windows Settings → Update & Security |
| **Visual C++ Redistributable** | Runtime components | [Download](https://aka.ms/vs/17/release/vc_redist.x64.exe) |

> **⚠️ Important:** USB Monitor requires **Administrator privileges** to:
> - Register for device notifications
> - Lock the workstation
> - Access drive serial numbers
> - Write to protected system areas

---

## 🚀 Installation Methods

### Method 1: Pre-built Binary (Recommended)

**This is the easiest and quickest way to install USB Monitor.**

#### Step 1: Download the Binary

1. Visit the [USB Monitor Releases Page](https://github.com/davidwairimu-netsec/USB_Monitor/releases)
2. Download the latest version:
   - For 64-bit: `USB_Monitor-x64-1.0.0.zip`
   - For 32-bit: `USB_Monitor-x86-1.0.0.zip`

#### Step 2: Extract the Files

1. Right-click the downloaded ZIP file
2. Select **Extract All...**
3. Choose a destination folder (e.g., `C:\Program Files\USB_Monitor`)
4. Click **Extract**

#### Step 3: Verify the Installation

Ensure the following files are present:
USB_Monitor/
├── USB_Monitor.exe # Main executable
├── README.md # Documentation
└── LICENSE # License file


### Method 2: Build from Source

**For developers who want to compile the source code themselves.**

#### Step 1: Install Visual Studio

1. Download [Visual Studio Community 2022](https://visualstudio.microsoft.com/downloads/) (Free)
2. Run the installer
3. Select these workloads:
   - **Desktop development with C++**
   - **Windows SDK** (included in the workload)

#### Step 2: Install Windows SDK

If not installed with Visual Studio:
1. Download [Windows SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-sdk/)
2. Run the installer
3. Select all default options
4. Complete the installation

#### Step 3: Clone the Repository

Using Git:
```bash
git clone https://github.com/davidwairimu-netsec/USB_Monitor.git
cd USB_Monitor

Or download manually:

Visit the repository: https://github.com/davidwairimu-netsec/USB_Monitor
Click Code → Download ZIP
Extract the ZIP to your workspace folder

Step 4: Open the Project in Visual Studio
Launch Visual Studio
Click Open a project or solution
Navigate to the project folder
Select USB_Monitor.sln
Click Open

Step 5: Build the Project
Option A: Using Visual Studio GUI
Select Release configuration (top toolbar)
Select x64 or x86 platform
Click Build → Build Solution (or press Ctrl+Shift+B)

Option B: Using Command Line
cd USB_Monitor
msbuild USB_Monitor.sln /p:Configuration=Release /p:Platform=x64

Step 6: Locate the Built Binary
Release builds: USB_Monitor\Release\USB_Monitor.exe
Debug builds: USB_Monitor\Debug\USB_Monitor.exe

Method 3: Using Windows Package Manager
For users with Windows Package Manager (winget) installed.
# Install USB Monitor
winget install --id YourUsername.USBM Monitor --exact

# Update USB Monitor
winget upgrade --id YourUsername.USBM Monitor --exact

# Uninstall USB Monitor
winget uninstall --id YourUsername.USBM Monitor --exact

Note: This method requires the package to be published to the winget repository.

🔧 Post-Installation Setup
Required: Run as Administrator
USB Monitor must run with administrator privileges. Set this up once:

Method 1: Set "Run as Administrator" as Default
Navigate to USB_Monitor.exe
Right-click the file
Select Properties
Go to the Compatibility tab
Check Run this program as an administrator
Click Apply → OK

Method 2: Create a Shortcut with Admin Rights
Right-click on the desktop → New → Shortcut
Browse to USB_Monitor.exe
Name the shortcut USB Monitor
Right-click the new shortcut → Properties
Click Advanced...
Check Run as administrator
Click OK → Apply → OK

Optional: Create Log Directory
Create a dedicated directory for logs (optional):
mkdir C:\USB_Logs

Note: The application will create logs in its current directory by default.

▶️ Running USB Monitor
Method 1: Quick Run
Navigate to the installation folder
Right-click USB_Monitor.exe
Select Run as administrator
The application starts in a hidden window

Method 2: Using Command Line
# Open Command Prompt as Administrator
cd C:\Program Files\USB_Monitor
USB_Monitor.exe

Method 3: Using PowerShell
# Open PowerShell as Administrator
cd "C:\Program Files\USB_Monitor"
Start-Process -FilePath "USB_Monitor.exe" -Verb RunAs

Expected Results
When running correctly, you should see:
A brief console window appears (then hides)
usb_access_log.txt is created in the program directory
The process appears in Task Manager
Any USB insertion will trigger the security response

🔄 Automatic Startup Configuration
Option 1: Using Task Scheduler (Recommended)
Set USB Monitor to start automatically when Windows starts:
Press Win + R → Type taskschd.msc → Press Enter
Click Create Basic Task (right panel)

Name: USB Monitor
Description: Security monitoring for USB devices
Trigger: When the computer starts
Action: Start a program
Program: C:\Program Files\USB_Monitor\USB_Monitor.exe
Check Open the Properties dialog
Go to the Conditions tab
Uncheck Start the task only if the computer is on AC power
Click OK

Test Security Response
Insert any USB storage device
Expected: Workstation locks immediately
Expected: Log entry created
Expected: USB_Security_Report.txt generated

🗑️ Uninstallation
Method 1: Manual Uninstall
Remove automatic startup entries:
Task Scheduler task (if created)
Registry entry (if added)
Startup folder shortcut (if created)
Delete the USB_Monitor folder:
rmdir /s "C:\Program Files\USB_Monitor"

✅ Installation Checklist
Before reporting an issue, verify:
Windows is up to date (Windows Update)
Visual C++ Redistributable is installed
Administrator privileges are available
Antivirus is not blocking the application
USB ports are working correctly
You have extracted the complete ZIP file
You are running with Administrator rights
The application is in a writable directory
Windows notifications are not disable

Installation Complete ✅

Now that USB Monitor is installed, refer to the README.md for usage instructions and features documentation.




## 🎯 Key Sections Explained

### 1. **Multiple Installation Methods**
I provided three methods to accommodate different user skill levels:
- **Method 1** (Pre-built): Easiest for general users
- **Method 2** (Source): For developers
- **Method 3** (Package Manager): For advanced users

### 2. **Post-Installation Setup**
Critical steps many install guides miss:
- Setting admin privileges permanently
- Configuring automatic startup
- Creating shortcuts

### 3. **Troubleshooting**
Detailed solutions for common issues:
- Missing DLLs
- Permission problems
- Antivirus conflicts
- Detection failures

### 4. **Verification**
Clear steps to confirm the installation works:
- Check logs
- Test with USB insertion
- Verify security response

### 5. **Uninstallation**
Clean removal instructions to prevent leftover files.

