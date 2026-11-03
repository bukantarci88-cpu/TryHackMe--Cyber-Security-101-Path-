# SEC 12.4. FlareVM

#### **FlareVM**

#### **Task 1 - Introduction**

**FlareVM**, or "**Forensics, Logic Analysis, and Reverse Engineering**," stands out as a comprehensive and carefully curated collection of specialized tools uniquely designed to meet the specific needs of reverse engineers, malware analysts, incident responders, forensic investigators, and penetration testers.  

#### **Task 2 - Arsenal of Tools**

**Reverse Engineering & Debugging :** Reverse engineering is like solving a puzzle backward: you take a finished product apart to understand how it works. Debugging is identifying errors, understanding why they happen, and correcting the code to prevent them.

- **Ghidra** - NSA-developed open-source reverse engineering suite.
- **x64dbg** - Open-source debugger for binaries in x64 and x32 formats.
- **OllyDbg** - Debugger for reverse engineering at the assembly level.
- **Radare2** - A sophisticated open-source platform for reverse engineering.
- **Binary Ninja** - A tool for disassembling and decompiling binaries.
- **PEiD** - Packer, cryptor, and compiler detection tool.

**Disassemblers & Decompilers:** Disassemblers and Decompilers are crucial tools in malware analysis. They help analysts understand malicious software’s behaviour, logic, and control flow by breaking it into a more understandable format. The tools mentioned below are commonly used in this category.

- **CFF Explorer** - A PE editor designed to analyze and edit Portable Executable (PE) files.
- **Hopper Disassembler** - A Debugger, disassembler, and decompiler.
- **RetDec** - Open-source decompiler for machine code.

**Static & Dynamic Analysis:** Static and dynamic analysis are two crucial methods in cyber security for examining malware. Static analysis involves inspecting the code without executing it, while dynamic analysis involves observing its behaviour as it runs. The tools mentioned below are commonly used in this category.

- **Process Hacker** - Sophisticated memory editor and process watcher.
- **PEview** - A portable executable (PE) file viewer for analysis.
- **Dependency Walker** - A tool for displaying an executable’s DLL dependencies.
- **DIE (Detect It Easy)** - A packer, compiler, and cryptor detection tool.

**Forensics & Incident Response:** Digital Forensics involves the collection, analysis, and preservation of digital evidence from various sources like computers, networks, and storage devices. At the same time, Incident Response focuses on the detection, containment, eradication, and recovery from cyberattacks. The tools mentioned below are commonly used in this category.

- **Volatility** - RAM dump analysis framework for memory forensics.
- **Rekall** - Framework for memory forensics in incident response.
- **FTK Imager** - Disc image acquisition and analysis tools for forensic use.

**Network Analysis:** Network Analysis includes different methods and techniques for studying and analysing networks to uncover patterns, optimize performance, and understand the underlying structure and behaviour of the network.

- **Wireshark** - Network protocol analyzer for traffic recording and examination.
- **Nmap** - A vulnerability detection and network mapping tool.
- **Netcat** - Read and write data across network connections with this helpful tool.

**File Analysis:** File Analysis is a technique used to examine files for potential security threats and ensure proper file permissions.

- **FileInsight** - A program for looking through and editing binary files.
- **Hex Fiend** - Hex editor that is light and quick.
- **HxD** - Binary file viewing and editing with a hex editor.

**Scripting & Automation:** Scripting and Automation involve using scripts such as PowerShell and Python to automate repetitive tasks and processes, making them more efficient and less prone to human error.

- **Python** - Mainly automation-focused on Python modules and tools.
- **PowerShell Empire** - Framework for PowerShell post-exploitation.

**Sysinternals Suite:** The Sysinternals Suite is a collection of advanced system utilities designed to help IT professionals and developers manage, troubleshoot, and diagnose Windows systems.

- **Autoruns** - Shows what executables are configured to run during system boot-up.
- **Process Explorer** - Provides information about running processes.
- **Process Monitor** -Monitors and logs real-time process/thread activity.

**Answer the questions below**

> Which tool is an Open-source debugger for binaries in x64 and x32 formats? x64dbg
> 

> What tool is designed to analyze and edit Portable Executable (PE) files? CFF Explorer
> 

> Which tool is considered a sophisticated memory editor and process watcher? Process Hacker
> 

> Which tool is used for Disc image acquisition and analysis for forensic use? FTK Imager
> 

> What tool can be used to view and edit a binary file? HxD
> 

#### **Task 3 - Commonly Used Tools for Investigation: Overview**

These tools are the basic ones used for initial investigations. 

| **Tool** | **Investigative Value** |
| --- | --- |
| Procmon | A helpful tool for tracking system activity, especially regarding malware research, troubleshooting, and forensic investigations. |
| Process Explorer | Allows you to see the Process of the Parent-child relationship, DLLs loaded, and its path. |
| HxD | Malicious files can be examined or altered via hex editing. |
| Wireshark | Observing and investigating network traffic to look for unusual activity. |
| CFF Explorer | Can generate file hashes for integrity verification, authenticate the source of system files, and validate their validity. |
| PEStudio | Static analysis or studying executable file properties without running the files. |
| FLOSS | Extracts and de-obfuscates all strings from malware programs using advanced static analysis techniques. |

**Process Monitor (Procmon): Process Monitor (Procmon)** is a Windows Sysinternals tool that captures **real-time file, registry, process, and thread activity**. It is commonly used for **malware analysis, troubleshooting, and digital forensics**. Security analysts use Procmon to investigate processes like **lsass.exe**, a legitimate Windows authentication process that is often targeted by attackers for **credential dumping** using tools like Mimikatz. Procmon provides visibility into system behavior and helps detect suspicious process activity

![the image shows how to leverage the tool. Here, we filtered for the process lsass.exe to see information about it.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727302306550.png)

**Process Explorer (Procexp):  Process Explorer (Procexp)** is a Windows Sysinternals tool that provides detailed information about **running processes, parent-child relationships, and user accounts**. It helps analysts identify **which processes are accessing files or folders** and investigate suspicious activity. In malware analysis, Process Explorer is useful for tracking **process creation chains**, such as programs launched from **Word documents, LNK files, or ISO files**, which are commonly abused by attackers. Process Explorer helps security analysts understand process behavior and detect suspicious execution paths. 

![The image shows the process and it's parent. We can validate the process ID and other information of the process here](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727171765939.png)

**HxD: HxD** is a hex editor used for **forensic analysis, debugging, data recovery, and examining binary files**. It allows analysts to view and edit **raw hexadecimal data**, search byte patterns, and compare file contents. In malware analysis, HxD helps identify file types and hidden data. For example, the **4D 5A (MZ) header** indicates a Windows executable file. HxD provides visibility into a file’s raw bytes, helping analysts detect file structures, corruption, and suspicious content.

![The image shows the hex value of a file](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727170785692.png)

**CFF Explorer:**  CFF Explorer helps analyze **Portable Executable (PE) files** by displaying file details, hashes, headers, and metadata. It is useful for **verifying file integrity, detecting modifications, and investigating suspicious executables**. Examines Portable Executable (PE) files to view metadata, hashes, headers, and file structure for malware investigation and integrity checking.

![the image shows the information of the file when opened using the CFF explorer tool.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727170785706.png)

 **Wireshark:** Wireshark is a network analysis tool used to capture and inspect **network traffic, protocols, IP addresses, ports, and connections**. It helps analysts detect suspicious communication, malware activity, and possible data exfiltration. Analyzes network traffic to detect suspicious connections, protocols, and potential malicious communication.

![the image shows the capabilities of wireshark such as capturing the network traffic. We can see here the source and destination IP and also the port and protocol used.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727170785704.png)

**PEStudio:** PEStudio performs **static malware analysis** by examining executable files without running them. It provides information such as **entropy, imports, hashes, and file properties** to identify potentially malicious behavior. Performs static analysis of executables to identify suspicious characteristics such as entropy, imports, and indicators of malware without running the file.

![this image shows information about the certain file that you wish to examine.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727170785666.png)

**FLOSS:** LOSS (FireEye Labs Obfuscated String Solver) is a static analysis tool that extracts and de-obfuscates **hidden strings** from malware binaries. It can reveal useful indicators such as **URLs, IP addresses, file paths, API calls, registry keys, and configuration data**. These tools help security analysts investigate malware by analyzing **file structure, network behavior, executable properties, and hidden indicators** without executing malicious files.

**Answer the questions below**

> Which tool was formerly known as FireEye Labs Obfuscated String Solver? FLOSS
> 

> Which tool offers in-depth insights into the active processes running on your computer? Process Explorer
> 

> By using the Process Explorer (procexp) tool, under what process can we find smss.exe? System
> 

> Which powerful Windows tool is designed to help you record issues with your system's apps? Procmon
> 

> Which tool can be used for Static analysis or studying executable file properties without running the files? PEStudio
> 

> Using the tool PEStudio to open the file cryptominer.bin in the Desktop\Sample folder, what is the sha256 value of the file?  E9627EBAAC562067759681DCEBA8DDE8D83B1D813AF8181948C549E342F67C0E
> 

> Using the tool PEStudio to open the file cryptominer.bin in the Desktop\Sample folder, how many functions does it have? 102
> 

> What tool can generate file hashes for integrity verification, authenticate the source of system files, and validate their validity? CFF Explorer
> 

> Using the tool CFF Explorer to open the file possible_medusa.txt in the Desktop\Sample folder, what is the MD5 of the file? 646698572AFBBF24F50EC5681FEB2DB7
> 

> Use the CFF Explorer tool to open the file possible_medusa.txt in the Desktop\Sample folder. Then, go to the DOS Header Section. What is the e_magic value of the file? 5A4D
> 

#### **Task 4 - Analyzing Malicious Files!**

A suspicious **windows.exe** file was downloaded by a user on 09/24/2024 at 3:43 AM. This download was flagged as a potential threat. The monitoring team has sent you an email requesting to perform an analysis of it. They have sent you the file, which is now in  the **C:\Users\Administrator\Desktop\Sample** folder. 

![this image shows the files that we are going to use in this task](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727170544603.png)

**Analysis using PEStudio**

![this image shows static information about the windows.exe file when opened using PEStudio.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727174706257.png)

**Suspicious windows.exe Analysis:** A suspicious **windows.exe** file was downloaded and analyzed using **PEStudio**. The file showed several indicators of potentially malicious behavior.

- **Hashes (MD5/SHA-1)** were generated and should be checked against threat intelligence platforms like VirusTotal.
- The file pretended to be **Windows Registry Editor (REGEDIT)**, but its location outside **C:\Windows\System32** suggests possible impersonation.
- **Russian language metadata** in the version information was suspicious and may indicate a foreign malware sample or fake system tool.
- The missing **Rich Header** suggests the file may be **packed or obfuscated** to evade detection.
- Imported APIs revealed suspicious capabilities:
    - **set_UseShellExecute** → can launch additional processes.
    - **CryptoStream / RijndaelManaged / CreateDecryptor** → indicates encryption capabilities, potentially used for malicious communication or ransomware behavior.

PEStudio analysis revealed that **windows.exe shows multiple malware indicators**, including impersonation, possible obfuscation, process execution, and encryption functionality, requiring further investigation.

![this image shows more result when the file windows.exe was opened using PEStudio.></p>

<p>If you look at the <b>version field</b>, it can be said that the presence of Russian text (](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727175229441.png)

![this image shows the API calls that windows.exe uses](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727178234246.png)

**Analysis using FLOSS:** Open PowerShell and go to the directory where our file is, which is **C:\Users\Administrator\Desktop\Sample**. Note that it might take a while before the PowerShell prompt appears. Run the command `FLOSS.exe .\windows.exe > windows.txt`. This will run the tool **floss.exe** and output it to a file named windows.txt in the same directory.

```powershell
PS C:\Users\Administrator\Desktop\Sample > FLOSS.exe .\windows.exe > windows.txt
WARNING: floss: .NET language-specific string extraction is not supported yet
WARNING: floss: FLOSS does NOT attempt to deobfuscate any strings from .NET binaries
INFO: floss: disabled string deobfuscation
INFO: floss: extracting static strings
INFO: floss: finished execution after 0.34 seconds
INFO: floss: rendering results
```

![this image shows  the result when you run the tool floss.exe and output it on a file.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727179931028.png)

**Analyze with Process Explorer and Process Monitor:**  **Process Explorer** and **Process Monitor (Procmon)** are used to investigate the behavior of **cobaltstrike.exe**, focusing on process relationships and network activity.

🔍 **Process Explorer findings:**

- Identified the **parent-child process relationship**:
    - `explorer.exe` → parent process
    - `cobaltstrike.exe` → child process
- The **Process ID (PID)** was used to inspect network connections.
- The **TCP/IP tab** showed whether the process was communicating with external destinations, helping identify possible **C2 (Command and Control) connections**.

🛠️ **Process Monitor findings:**

- Used as a second verification tool to confirm activity.
- Filters were applied to focus only on **cobaltstrike.exe** because Procmon captures activity from all running processes.

Using **Process Explorer and Procmon together** provides deeper visibility into malware behavior, including **process execution, parent-child relationships, and suspicious network communications**.

![this image shows the processes related to cobaltstrike.exe](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727191613610.png)

![This image actually has a lot of information about the cobaltstrike.exe. We can see the properties of the file here. We focused on the TCP/IP tab as this contains information about network connectivity.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727191613592.png)

![this image shows how to use the filter for process monitor tool](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727192184037.png)

- Now, using this filter involves several steps. This includes:
    1. Select the **Process Name**
    2. Select **contains**
    3. type any value containing any word related to the process. In this case, **cobalt**
    4. Click **include**
    5. And then **Add** and Click on Apply
    6. You should be able to see the conditions added.

![This image shows the steps you will use to filter the results of process monitor tool.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727193011175.png)

This should give us a more detailed result.

![this image shows a filtered result concerning the cobaltstrike.exe binary.](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e6bbe59a46ee9407fd65bbe/room-content/5e6bbe59a46ee9407fd65bbe-1727193407393.png)

This confirms that the binary was indeed making a connection to an unknown IP address which is 47.120.46.210.

**Answer the questions below**

> Using PEStudio, open the file windows.exe. What is the entropy value of the file windows.exe? 7.999
> 

> Using PEStudio, open the file windows.exe, then go to manifest (administrator section). What is the value under requestedExecutionLevel? requireAdministrator
> 

> Which function allows the process to use the operating system's shell to execute other processes? set_UseShellExecute
> 

> Which API starts with R and indicates that the executable uses cryptographic functions? RijndaelManaged
> 

> What is the Imphash of cobaltstrike.exe? 92EEF189FB188C541CBD83AC8BA4ACF5
> 

> What is the defanged IP address to which the process cobaltstrike.exe is connecting? 47[.]120[.]46[.]210
> 

> What is the destination port number used by cobaltstrike.exe when connecting to its C2 IP Address? 81
> 

> During our analysis, we found a process called cobaltstrike.exe. What is the parent process of cobaltstrike.exe? explorer.exe
> 

#### **Task 5 - Conclusion**

**FlareVM (Forensics, Logic Analysis, and Reverse Engineering)** is a customized environment designed for **incident response, malware analysis, reverse engineering, and digital forensics**. The room introduced key malware analysis tools, including:

- **PEStudio** → Static analysis of executable files
- **CFF Explorer** → PE file structure and metadata analysis
- **Process Monitor** → Real-time monitoring of file, registry, and process activity
- **Process Explorer** → Process investigation and parent-child relationship analysis

FlareVM provides security analysts with a complete toolkit to investigate malware, analyze suspicious files, and perform effective digital forensics.
