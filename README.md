
# 🐧 Red Hat Enterprise Linux (RHEL) on WSL2 – Complete Installation Guide

This README explains step-by-step how to install Red Hat Enterprise Linux (RHEL) on Windows Subsystem for Linux 2 (WSL2) in Windows 11.

---

## ✅ Requirements

- Windows 10/11
- Virtualization enabled in BIOS (check via Task Manager → Performance → CPU → Virtualization)
- PowerShell (Run as Administrator)
- RHEL `.tar.gz` WSL image file from Red Hat or download it from repo
- Optional: VMware Workstation 17.5+ for dual virtualization support

---
## 🧰 How to Install WSL

Open PowerShell as Administrator and run:

```
wsl --install
```

This will automatically install WSL and the default Linux distro (usually Ubuntu). You can ignore or remove Ubuntu later if you're only using RHEL.

---

If you got this error
```
Error code: Wsl/InstallDistro/Service/RegisterDistro/CreateVm/HCS/HCS_E_SERVICE_NOT_AVAILABLE
```
then Open PowerShell as Administrator and run:

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:HypervisorPlatform /all /norestart
```

➡️ Then restart your computer.

---

## 📥 Step 2: Download RHEL WSL Image OR Download from repo

1. Create a free Red Hat account at: https://developers.redhat.com/
2. Visit: https://developers.redhat.com/products/rhel/download
3. Download the WSL image (e.g., `rhel-10.0-x86_64-wsl2.tar.gz`) OR Download from repo rhel-10.0-x86_64-wsl2.tar.gz
4. Open cmd type: mkdir "%USERPROFILE%\Documents\ISO"
5. Save it here: `C:\Users\<YourUsername>\Documents\ISO\rhel-10.0-x86_64-wsl2.tar.gz` 
                              


## 📁 Step 3: Create Target Install Folder

Run in PowerShell:

```
mkdir C:\WSL\RHEL10
```

---

## 🚀 Step 4: Import RHEL into WSL

Run in PowerShell (Admin):

```
wsl --import RHEL10 C:\WSL\RHEL10 "C:\Users\<YourUsername>\Documents\ISO\rhel-10.0-x86_64-wsl2.tar.gz" --version 2
```

This installs RHEL with WSL2 backend.

---

## 💻 Step 5: Start and Use RHEL

```
wsl -d RHEL10
```

Set RHEL as default:

```
wsl --set-default RHEL10
```

---

## 🔐 Step 6: First Time Setup

Inside the RHEL WSL terminal:

```
passwd                             # Set root password
subscription-manager register      # Optional Red Hat registration
dnf update -y                      # Update system packages
```

---

## 📂 Step 7: Access Files

- Access Windows from Linux: `/mnt/c/`
- Access Linux from Windows: `\\wsl$\RHEL10\`

---

## 📎 Common WSL Commands

```
wsl --list --verbose            # View all installed distros
wsl --set-version RHEL10 2      # Ensure WSL2 is used
wsl --unregister RHEL10         # Delete this distro
wsl --shutdown                  # Shutdown all WSL instances
```

---

## ⚠️ Notes

- Do NOT disable `VirtualMachinePlatform` or `Microsoft-Windows-Subsystem-Linux` features if using WSL2.
- VMware Workstation 17.5+ supports Hyper-V and works fine with WSL2.
- GitHub file upload limit is 100 MB. Use Google Drive/OneDrive/Dropbox to share `.tar.gz` images.

---

## 🔗 Useful Links

- [Red Hat Developer Portal](https://developers.redhat.com/)
- [Download RHEL](https://developers.redhat.com/products/rhel/download)
- [WSL Official Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
