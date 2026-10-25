# Windows CMD Commands Cheat Sheet

A practical collection of **Windows Command Prompt (CMD) commands** for file and folder management, process and service management, networking, system information, disk management, user accounts, and troubleshooting.

> **Note:** Some commands require Administrator privileges. Run commands carefully, especially those that delete files, manage disks, or modify user accounts.

## Table of Contents

1. [File and Folder Management](#1-file-and-folder-management)
2. [Process and Service Management](#2-process-and-service-management)
3. [Network and Firewall Commands](#3-network-and-firewall-commands)
4. [Hardware and System Information](#4-hardware-and-system-information)
5. [Disk and Volume Management](#5-disk-and-volume-management)
6. [Windows Tools and User Accounts](#6-windows-tools-and-user-accounts)
7. [User Account Management](#7-user-account-management)
8. [Useful CMD Utilities](#8-useful-cmd-utilities)
9. [Safety Notes](#9-safety-notes)

---

## 1. File and Folder Management

These commands help create, copy, move, rename, list, and delete files and folders.

| Command          | Purpose                         | Example                      |
| ---------------- | ------------------------------- | ---------------------------- |
| `dir`            | List files and folders          | `dir`                        |
| `md` / `mkdir`   | Create a directory              | `mkdir MyFolder`             |
| `cd`             | Change directory                | `cd MyFolder`                |
| `cd ..`          | Go to the parent directory      | `cd ..`                      |
| `copy`           | Copy a file                     | `copy file.txt backup.txt`   |
| `xcopy`          | Copy files and directories      | `xcopy *.txt "C:\Backup\"`   |
| `move`           | Move files or folders           | `move file.txt "C:\Backup\"` |
| `ren` / `rename` | Rename a file                   | `ren old.txt new.txt`        |
| `del` / `erase`  | Delete files                    | `del file.txt`               |
| `rmdir` / `rd`   | Remove a directory              | `rmdir EmptyFolder`          |
| `type`           | Display a text file             | `type notes.txt`             |
| `echo`           | Display text or write to a file | `echo Hello > notes.txt`     |
| `tree`           | Display a directory structure   | `tree /F`                    |
| `cls`            | Clear the screen                | `cls`                        |

### Examples

**Create a folder**

```cmd
mkdir pawankumarpatel
```

**Copy all text files into a folder**

```cmd
xcopy *.txt "pawankumarpatel\"
```

**Move a file into a folder**

```cmd
move file.txt "pawankumarpatel\"
```

**Move all text files into a folder**

```cmd
move *.txt "pawankumarpatel\"
```

**Rename a file**

```cmd
ren filepk.txt pkfight.txt
```

**Delete a specific file**

```cmd
del file1.txt
```

**Delete multiple specified files**

```cmd
del file1.txt file2.txt file3.txt
```

**Delete all text files in the current directory**

```cmd
del *.txt
```

**Delete files matching a pattern**

```cmd
del *file1*
```

**Remove an empty directory**

```cmd
rmdir pawankumarpatel
```

**Remove a directory and its contents**

```cmd
rmdir /S pawankumarpatel
```

> **Warning:** `del` and `rmdir /S` can permanently delete files. Check the target directory before executing them.

### CMD vs. Linux Commands

| Task                       | Windows CMD           | Linux                |
| -------------------------- | --------------------- | -------------------- |
| List files                 | `dir`                 | `ls`                 |
| Create folder              | `mkdir folder`        | `mkdir folder`       |
| Copy file                  | `copy a.txt b.txt`    | `cp a.txt b.txt`     |
| Move file                  | `move a.txt folder\`  | `mv a.txt folder/`   |
| Rename file                | `ren old.txt new.txt` | `mv old.txt new.txt` |
| Delete file                | `del a.txt`           | `rm a.txt`           |
| Delete folder and contents | `rmdir /S /Q folder`  | `rm -r folder`       |
| Clear terminal             | `cls`                 | `clear`              |
| Display file contents      | `type file.txt`       | `cat file.txt`       |

**Important:** `rm`, `rm -f`, and `cp` are not standard Windows CMD commands. They are available in shells such as Linux, macOS, Git Bash, and PowerShell in different forms.

---

## 2. Process and Service Management

Use these commands to inspect running processes, terminate tasks, and manage Windows services.

| Command                                   | Purpose                        |
| ----------------------------------------- | ------------------------------ |
| `tasklist`                                | Display running processes      |
| `tasklist /FI "IMAGENAME eq notepad.exe"` | Find a specific process        |
| `taskkill /PID 1234`                      | Terminate a process by PID     |
| `taskkill /PID 1234 /F`                   | Forcefully terminate a process |
| `taskkill /IM notepad.exe`                | Terminate a process by name    |
| `taskkill /IM notepad.exe /F`             | Forcefully terminate Notepad   |
| `sc query`                                | List or query services         |
| `net start`                               | Display running services       |
| `net start "ServiceName"`                 | Start a service                |
| `net stop "ServiceName"`                  | Stop a service                 |
| `driverquery`                             | List installed drivers         |

### Examples

**View running processes**

```cmd
tasklist
```

**Find Notepad**

```cmd
tasklist /FI "IMAGENAME eq notepad.exe"
```

**Terminate a process using its PID**

```cmd
taskkill /PID 1234 /F
```

Replace `1234` with the actual process ID.

**Display running services**

```cmd
net start
```

**Start or stop a service**

```cmd
net start "Spooler"
net stop "Spooler"
```

Run these service commands in an elevated CMD window if required. Stopping critical services may affect Windows functionality.

**List installed drivers**

```cmd
driverquery
```

---

## 3. Network and Firewall Commands

These commands help inspect network configuration and manage Windows Firewall.

| Command                                       | Purpose                                 |
| --------------------------------------------- | --------------------------------------- |
| `ipconfig`                                    | Show IP configuration                   |
| `ipconfig /all`                               | Show detailed network information       |
| `ipconfig /flushdns`                          | Clear the DNS resolver cache            |
| `ping google.com`                             | Test network connectivity               |
| `tracert google.com`                          | Trace the network route                 |
| `netstat -ano`                                | Display connections and listening ports |
| `arp -a`                                      | Display the ARP cache                   |
| `getmac`                                      | Display network adapter MAC addresses   |
| `netsh advfirewall show allprofiles`          | Show firewall profile status            |
| `netsh advfirewall set allprofiles state on`  | Enable all firewall profiles            |
| `netsh advfirewall set allprofiles state off` | Disable all firewall profiles           |

### Examples

**Display detailed IP information**

```cmd
ipconfig /all
```

**Check connectivity**

```cmd
ping google.com
```

**Display active connections and PIDs**

```cmd
netstat -ano
```

**Enable Windows Firewall**

```cmd
netsh advfirewall set allprofiles state on
```

**Open Network Connections**

```cmd
ncpa.cpl
```

Shortcut: press `Win + R`, enter `ncpa.cpl`, and press Enter.

> Keep Windows Firewall enabled. Disabling it reduces protection against unwanted network connections.

---

## 4. Hardware and System Information

Use these commands to inspect your Windows installation, BIOS information, processor, memory, and hardware.

| Command                                       | Purpose                                                                |
| --------------------------------------------- | ---------------------------------------------------------------------- |
| `systeminfo`                                  | Display detailed system information                                    |
| `winver`                                      | Show Windows version                                                   |
| `hostname`                                    | Display the computer name                                              |
| `whoami`                                      | Display the current user                                               |
| `wmic cpu`                                    | Query CPU information on supported systems                             |
| `wmic bios get serialnumber`                  | Retrieve BIOS serial number, if available                              |
| `wmic computersystem get totalphysicalmemory` | Query installed physical memory in bytes                               |
| `wmic nic get macaddress`                     | Query network adapter MAC addresses                                    |
| `wmic partition get name,size,type`           | Query partition information                                            |
| `wmic process list brief`                     | List process information                                               |
| `wmic product get name,version`               | Query product information for supported Windows Installer applications |

### Examples

**Display Windows version**

```cmd
winver
```

**Display system details**

```cmd
systeminfo
```

**Display computer name**

```cmd
hostname
```

**Display current user**

```cmd
whoami
```

**Query CPU information**

```cmd
wmic cpu get name
```

**Query BIOS serial number**

```cmd
wmic bios get serialnumber
```

**Query physical memory**

```cmd
wmic computersystem get totalphysicalmemory
```

**Query network adapter MAC addresses**

```cmd
wmic nic get macaddress
```

### Important: WMIC Availability

`wmic.exe` is deprecated and may not be installed or enabled on newer Windows versions. If a WMIC command fails, use PowerShell alternatives.

wmic cpu

wmic bios get serialnumber

wmic bios get serialnumer

wmic computersystem get total physicalmemory

wmic nic get macaddress

wmic partition get name,size,type

For example, open PowerShell and run:

```powershell
Get-CimInstance Win32_Processor | Select-Object Name
Get-CimInstance Win32_BIOS | Select-Object SerialNumber
Get-CimInstance Win32_ComputerSystem | Select-Object TotalPhysicalMemory
Get-CimInstance Win32_NetworkAdapterConfiguration |
    Where-Object { $_.MACAddress } |
    Select-Object Description, MACAddress
Get-CimInstance Win32_Process | Select-Object Name, ProcessId
```

**Note:** `wmic product get name,version` can be slow and may trigger Windows Installer consistency checks. Prefer other inventory methods when possible.

---

## 5. Disk and Volume Management

These commands help inspect drives, check file systems, and work with DiskPart.

| Command           | Purpose                                  |
| ----------------- | ---------------------------------------- |
| `vol C:`          | Display a volume label and serial number |
| `chkdsk C:`       | Check a file system                      |
| `chkdsk C: /scan` | Scan an NTFS volume online               |
| `diskpart`        | Open the DiskPart utility                |
| `list disk`       | List physical disks inside DiskPart      |
| `list volume`     | List volumes inside DiskPart             |
| `list partition`  | List partitions of the selected disk     |
| `select disk 0`   | Select Disk 0                            |
| `detail disk`     | Display details of the selected disk     |
| `exit`            | Exit DiskPart                            |

### Examples

**Display volume information**

```cmd
vol C:
vol D:
```

**Check the C drive**

```cmd
chkdsk C:
```

**Perform an online NTFS scan**

```cmd
chkdsk C: /scan
```

### DiskPart Workflow

Open CMD as Administrator.

```cmd
diskpart
list disk
select disk 0
detail disk
list partition
list volume
exit
```

This sequence is for inspection only; it does not delete or format partitions.

> **Critical safety warning:** Never run `clean`, `format`, `delete partition`, or similar destructive DiskPart commands unless you have verified the correct disk and backed up important data. Selecting the wrong disk can cause data loss.

---

## 6. Windows Tools and User Accounts

These commands open useful Windows administration tools.

| Command        | Purpose                                      |
| -------------- | -------------------------------------------- |
| `regedit`      | Open Registry Editor                         |
| `lusrmgr.msc`  | Open Local Users and Groups, where supported |
| `ncpa.cpl`     | Open Network Connections                     |
| `services.msc` | Open Services management                     |
| `devmgmt.msc`  | Open Device Manager                          |
| `eventvwr.msc` | Open Event Viewer                            |
| `taskmgr`      | Open Task Manager                            |
| `perfmon`      | Open Performance Monitor                     |
| `resmon`       | Open Resource Monitor                        |
| `msinfo32`     | Open System Information                      |
| `cleanmgr`     | Open Disk Cleanup, where available           |
| `control`      | Open Control Panel                           |
| `appwiz.cpl`   | Open Programs and Features                   |
| `sysdm.cpl`    | Open System Properties                       |

**Example: Open Event Viewer**

```cmd
eventvwr.msc
```

**Example: Open Device Manager**

```cmd
devmgmt.msc
```

**Example: Open Services**

```cmd
services.msc
```

**Example: Open Registry Editor**

```cmd
regedit
```

Registry Editor can change important Windows settings. Export a registry key before modifying it, and do not delete unfamiliar entries.

---

## 7. User Account Management

Use `net user` to view and manage local Windows accounts.

| Command                              | Purpose                                    |
| ------------------------------------ | ------------------------------------------ |
| `net user`                           | List local user accounts                   |
| `net user username`                  | Display information about an account       |
| `net user username *`                | Set or change a password interactively     |
| `net user username /add`             | Create a local user                        |
| `net user username /delete`          | Delete a local user                        |
| `net user administrator /active:yes` | Enable the built-in Administrator account  |
| `net user administrator /active:no`  | Disable the built-in Administrator account |

### Examples

**List local user accounts**

```cmd
net user
```

**Display account information**

```cmd
net user username
```

**Create a local user**

```cmd
net user testuser * /add
```

Enter the password when prompted. This avoids placing the password directly in the command.

**Change a user's password**

```cmd
net user testuser *
```

**Delete a user**

```cmd
net user testuser /delete
```

**Enable the built-in Administrator account**

```cmd
net user administrator /active:yes
```

**Disable the built-in Administrator account**

```cmd
net user administrator /active:no
```

These account-management commands may require Administrator privileges. Enabling the built-in Administrator account increases risk if it is left enabled unnecessarily.

---

## 8. Useful CMD Utilities

| Command               | Purpose                                       |
| --------------------- | --------------------------------------------- |
| `help`                | Display available CMD commands                |
| `command /?`          | Show help for a particular command            |
| `doskey /history`     | Display the current session's command history |
| `date /t`             | Display the current date                      |
| `time /t`             | Display the current time                      |
| `echo %USERNAME%`     | Display the current username                  |
| `echo %COMPUTERNAME%` | Display the computer name                     |
| `where python`        | Locate an executable on the PATH              |
| `where git`           | Locate Git on the PATH                        |
| `set`                 | Display environment variables                 |
| `path`                | Display the executable search path            |
| `shutdown /?`         | Display shutdown command help                 |

### Examples

**Display command help**

```cmd
ipconfig /?
```

**Display the current username**

```cmd
echo %USERNAME%
```

**Find the Python executable**

```cmd
where python
```

**View command history**

```cmd
doskey /history
```

**Display the current date and time**

```cmd
date /t
time /t
```

---

## 9. Safety Notes

- Open CMD as Administrator only when elevated permissions are necessary.
- Back up important data before performing disk operations.
- Review file paths and wildcard patterns before deleting files.
- Avoid disabling Windows Firewall during normal use.
- Do not share BIOS serial numbers, MAC addresses, passwords, or other sensitive system information publicly.
- Prefer interactive password prompts over passwords written directly in commands.
- Use PowerShell alternatives when WMIC is unavailable.
- Practice administrative commands in a test environment before using them on important systems.

## Learning Goals

This cheat sheet is useful for practicing:

- Windows system administration
- File and directory operations
- Process and service management
- Network troubleshooting
- Hardware and operating system inspection
- Disk and partition inspection
- Local account administration
- Basic IT support and cybersecurity labs

**Disclaimer:** This repository is intended for educational purposes and authorized system administration. Always understand a command's effects before running it.

---

**Contributions:** Suggestions and corrections are welcome. You can improve this reference by adding more Windows CMD examples, troubleshooting workflows, and PowerShell equivalents.
