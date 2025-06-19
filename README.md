# Red Hat WSL Installation Guide

This guide explains how to install Red Hat Enterprise Linux (RHEL) on WSL2 in Windows 11.

---

## 🛠 Requirements
- Windows 10/11 with WSL2 enabled
- VMware Workstation 17.5+ (optional)
- Virtualization enabled in BIOS
- RHEL `.tar.gz` image from Red Hat Developer portal or download from this repo

---

## 📦 Step 1: Enable Required Features (PowerShell as Admin)

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:HypervisorPlatform /all /norestart
