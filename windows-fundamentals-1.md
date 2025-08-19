# (File System & Permissions)

## 📂 File Systems in Windows

- **NTFS (New Technology File System)** → used in modern Windows versions.
- **Older File Systems**:
    - **FAT16/FAT32 (File Allocation Table)** → still used in USBs, SD cards.
    - **HPFS (High Performance File System)** → older, not common now.
- **NTFS Advantages**:
    - Journaling → can auto-repair files after crashes.
    - Supports files **> 4GB**.
    - File/Folder Permissions.
    - File/Folder Compression.
    - Encryption via **EFS (Encrypting File System)**.

---

## 🔑 NTFS Permissions

- Permissions can be applied to files and folders.
- **Types of Permissions**:
    - Full Control
    - Modify
    - Read & Execute
    - List Folder Contents
    - Read
    - Write
- **How to View Permissions**:
    1. Right-click file/folder → Properties.
    2. Go to **Security** tab.
    3. Select user/group → view assigned permissions.
- **Special Permissions** → more granular controls (refer to Microsoft docs).

---

## 📑 Alternate Data Streams (ADS)

- **What it is**: Hidden data streams in NTFS files.
- Every file has a main data stream (`$DATA`), but can contain additional hidden streams.
- **Uses**:
    - Legitimate: Windows writes ADS info when files are downloaded (e.g., marking Internet origin).
    - Malicious: Malware can hide code/data inside ADS.
- **Viewing ADS**:
    - Windows Explorer doesn’t show ADS.
    - Can use **PowerShell** or third-party tools to view.

---

## 🛡️ Security Takeaways

- **NTFS** gives Windows strong security features missing in older file systems.
- **Permissions** control who can read/write/modify files.
- **ADS** can be used both for security markers (legit use) and hiding malicious payloads.
- Security analysts should always check for **hidden ADS data** when investigating files.

---

# (Windows Folder & System32)

## 🖥️ Windows Folder (`C:\Windows`)

- Traditionally contains the **Windows operating system files**.
- **Location flexibility**:
    - Doesn’t have to be on `C:` drive.
    - Can reside in a different folder or drive.
- **System Environment Variable**: `%windir%` points to the Windows folder.

### 🔹 What are Environment Variables?

- Store information about the **OS environment**.
- Examples:
    - OS path
    - Number of processors
    - Location of temporary folders

---

## 📂 Key Subfolder: System32

- **Holds critical OS files** required for Windows to function.
- **Caution**:
    - Deleting or modifying files/folders here can **break the OS**.
- Common contents:
    - System libraries (`.dll`)
    - Executable system tools (`.exe`)
    - Drivers and configuration files

---

## 🛡️ Security & Admin Takeaways

- System32 is a **high-value target** for malware.
- Always **backup or use caution** when interacting with critical OS folders.
- Understanding Windows folder structure helps in:
    - Incident response
    - Malware analysis
    - System administration

---

## 👥 User Accounts

- There are two main types of accounts in Windows:
    - **Standard User**: can only change their own files/folders. Cannot install programs or mess with system settings.
    - **Administrator**: has full control — can add/delete users, change settings, install programs, basically do whatever they want.
    - Example: In universities, students are usually standard users — they can’t open certain settings or even turn off the computer in some cases. Admins can monitor and control what standard users do.
- **How to see other users**:
    - Search for “other users” in Windows.
    - Or run `lusrmgr.msc` in the Run command. This will show all users and groups and a brief idea of what they can do.
- **Things every user has in common**:
    - Desktop
    - Downloads
    - Music
    - Documents
    - Pictures
- Running `lusrmgr.msc` is a good way to quickly see all users and their groups, which helps you understand what permissions each user has.

---

## 🎛️ User Control

- As we discussed before, admins control what local users can do.
- This is called **User Access Control (UAC)**.
- **What it does:**
    - Prevents standard users from making changes that could affect the system.
    - Prompts for admin approval whenever a program tries to change system settings or install software.
- **Example:**
    - If a standard user tries to install a new program, Windows will ask for an admin password or confirmation.
    - This helps protect the computer from accidental changes or malware.

---

## 🖥️ Control Panel & Task Manager

- **Task Manager**:
    - View running processes, CPU/RAM usage, start-up apps.
    - Security relevance: spot suspicious processes or high resource usage.
- **Control Panel**:
    - Access system settings, programs, user accounts, network settings.
    - Security relevance: configure Windows Firewall, User Accounts, updates.
