# Windows Registry Hives – DFIR Cheat Sheet

## System Registry Hives

Location:

C:\Windows\System32\Config\

|   Hive   |            Description                 |
|----------|-------------                           |
| SAM      | Local user accounts                    |
| SECURITY | Security policies                      |
| SOFTWARE | Installed software and configuration   |
| SYSTEM   | System configuration and services      |
| DEFAULT  | Default user profile settings          |

---

## User Registry Hives

### NTUSER.DAT

Location:

C:\Users\<username>\NTUSER.DAT

Contains the following artifacts:

---

### User Configuration

Registry Path:

HKCU\Software\Microsoft\Windows\CurrentVersion

Examples:

HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer  
HKCU\Software\Microsoft\Windows\CurrentVersion\Run  
HKCU\Software\Microsoft\Windows\CurrentVersion\Policies  

---

### Recent Files

Registry Path:

HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs

Contains:

- Recently opened files
- File extensions
- MRU (Most Recently Used) order

---

### Explorer Activity

Registry Paths:

HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\RunMRU  
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths  
HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist

Artifacts:

- Commands executed from Run dialog
- Paths typed in Explorer
- Programs executed through Explorer

---

### Shellbags

Registry Paths:

HKCU\Software\Microsoft\Windows\Shell\BagMRU  
HKCU\Software\Microsoft\Windows\Shell\Bags  

(Also sometimes)

HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\BagMRU  
HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\Shell\Bags  

Contains:

- Folder navigation history
- Folder view preferences
- Evidence of directory browsing

---

### User-Specific Registry Keys

Examples:

HKCU\Control Panel  
HKCU\Environment  
HKCU\Network  
HKCU\Printers  

Contains:

- User environment variables
- Network mappings
- Printer configuration
- User desktop settings


---

### USRCLASS.DAT

Location:

C:\Users\<username>\AppData\Local\Microsoft\Windows\UsrClass.dat

Contains:

- Shellbags
- Explorer activity
- File associations
- COM object registrations

---

## Registry Hive Log Files

Location:

C:\Windows\System32\Config\

Files:

- *.LOG
- *.LOG1
- *.LOG2

Example:

SYSTEM.LOG1  
SYSTEM.LOG2

These contain **transaction logs used to recover registry changes**.

---

## Quick Reference

| Hive | Path |
|-----|------|
| SYSTEM | C:\Windows\System32\Config\SYSTEM |
| SOFTWARE | C:\Windows\System32\Config\SOFTWARE |
| SAM | C:\Windows\System32\Config\SAM |
| SECURITY | C:\Windows\System32\Config\SECURITY |
| DEFAULT | C:\Windows\System32\Config\DEFAULT |
| NTUSER | C:\Users\<user>\NTUSER.DAT |
| USRCLASS | C:\Users\<user>\AppData\Local\Microsoft\Windows\UsrClass.dat |

---

## DFIR Notes

Most DFIR investigations focus on these hives:

- NTUSER.DAT
- UsrClass.dat
- SYSTEM
- SOFTWARE

These contain the majority of **user activity artifacts** used during forensic analysis.
