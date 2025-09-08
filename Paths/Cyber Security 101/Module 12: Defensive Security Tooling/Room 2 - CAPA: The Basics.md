Link : https://tryhackme.com/room/capabasics (Premium Room)

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/84d4b3f7-12ac-4cb5-94f9-edc835025fca" />

Learn to use CAPA to identify malicious capabilities.

**Module 1: Introduction**

One of the challenges when analyzing potentially malicious software is that we risk our machine or environment being compromised when we run it unless we have a sandbox or a completely isolated environment where we can test all we want. Generally speaking, there are two types of analysis: dynamic analysis and static analysis. This room will focus on conducting static analysis using a tool called CAPA.

<img width="739" height="600" alt="image" src="https://github.com/user-attachments/assets/773d31f4-201e-404a-8bb5-1149e8b52b83" />

CAPA (Common Analysis Platform for Artifacts) is a tool developed by the FireEye Mandiant team. It is designed to identify the capabilities present in executable files like Portable Executables (PE), ELF binaries, .NET modules, shellcode, and even sandbox reports. It does so by analyzing the file and applying a set of rules that describe common behaviours, allowing it to determine what the program is capable of doing, such as network communication, file manipulation, process injection, and many more.

The beauty of CAPA is that it encapsulates years of reverse engineering knowledge into an automated tool, making it accessible even to those who may not be experts in reverse engineering. This can be incredibly useful for analysts and security professionals, allowing them to quickly understand potentially malicious software's functionality without manually reverse engineering the code.

This tool is particularly useful in malware analysis and threat hunting, where understanding a binary's capabilities is crucial for incident response and defensive measures.


**Learning Objectives**

- Explore what CAPA is

- Learn how to use CAPA effectively

- Understand common fields and results rendered by using the tool

- Leverage the tool to Identify the program’s potential activity


**Room Prerequisites**

Familiarity with the MITRE ATT&ACK Framework is recommended but not mandatory before starting the course. You may check the room associated with it.

- [MITRE ATT&CK](https://tryhackme.com/r/room/mitre)

**Virtual Machine**

Press the Start Machine button below.

We will use the tool inside the machine attached to this task. The machine will start in a split-screen view. If you opt to access the machine via Remote Desktop (RDP), you may also use the following credentials below.

- Username: `Administrator`

- Password: `letmein123!`

- IP Address 	MACHINE_IP

Note that inside this VM, we have installed CAPA so you can get a feel for running the tool and experiment further with the different command parameters. However, it takes a long time to finish using the attached VM. Hence, we have pre-processed the reports such as the following:

- cryptbot.txt

- cryptbot_vv.txt

- cryptbot_vv.json

And placed them under the directory C:\Users\Administrator\Desktop\capa. Almost all the files we will use in this room are in the said directory.


**Answer the questions below**

1. _I'm excited to learn more about CAPA!_

Answer: No answer needed

---

**Module 2: Tool Overview: How CAPA Works**

In this task, we will see how to use CAPA.  Running the tool is as easy as 1..2..3.  First, open a PowerShell, noting that it might take a while before the prompt appears. Next is to make sure that you are in the correct directory (C:\Users\Administrator\Desktop\capa); then you need to run capa or capa.exe, then point to the binary, and that’s it!

In this example, we will use cryptbot.bin; please note that the results of this file will be discussed throughout the succeeding task.

After running the command, wait for the result, which may take several minutes. We don't intend this to finish but rather to let you get a feel for running the tool, so we suggest that you continue the task while CAPA is running or stop the processing. There are alternative ways to proceed with the analysis of the results. See the command below.

```
PS C:\Users\Administrator\Desktop\capa> capa.exe .\cryptbot.bin
loading : 100%|████████████████████| 485/485 [00:00<00:00, 1108.84     rules/s]
/ analyzing program...
```

In addition to the -h command, which gives us more information about the parameters available with the tool, we will use two (2) most used parameters, which is the -v and -vv, which will give us a more detailed result. However, this will increase the processing time. We will have a discussion about the results of these options in the coming tasks.

| Option              | Description                          | Sample Syntax                          |
|---------------------|--------------------------------------|----------------------------------------|
| `-h` or `--help`    | Show this help message and exit.     | `capa -h`                              |
| `-v` or `--verbose` | Enable verbose result document.      | `capa.exe .\cryptbot.bin -v`           |
| `-vv` or `--vverbose` | Enable a very verbose result document. | `capa.exe .\cryptbot.bin -vv`         |

This should be the output of the command. *Please take note that results may vary. If you ran CAPA on some files, it might or might not give the same information as below.

```
PS C:\Users\Administrator\Desktop\capa> capa .\cryptbot.bin
┌─────────────┬────────────────────────────────────────────────────────────────────────────────────┐
│ md5         │ 3b9d26d2e7433749f2c32edb13a2b0a2                                                   │
│ sha1        │ 969437df8f4ad08542ce8fc9831fc49a7765b7c5                                           │
│ sha256      │ ae7bc6b6f6ecb206a7b957e4bb86e0d11845c5b2d9f7a00a482bef63b567ce4c                   │
│ analysis    │ static                                                                             │
│ os          │ windows                                                                            │
│ format      │ pe                                                                                 │
│ arch        │ i386                                                                               │
│ path        │ /home/strategos/Room-CAPA/cryptbot.bin                                             │
└─────────────┴────────────────────────────────────────────────────────────────────────────────────┘
┌──────────────────────┬───────────────────────────────────────────────────────────────────────────┐
│ ATT&CK Tactic        │ ATT&CK Technique                                                          │
├──────────────────────┼───────────────────────────────────────────────────────────────────────────┤
│ DEFENSE EVASION      │ Obfuscated Files or Information [T1027]                                   │
│                      │ Obfuscated Files or Information::Indicator Removal from Tools [T1027.005] │
│                      │ Virtualization/Sandbox Evasion::System Checks [T1497.001]                 │
│ DISCOVERY            │ File and Directory Discovery [T1083]                                      │
│ EXECUTION            │ Command and Scripting Interpreter::PowerShell [T1059.001]                 │
│                      │ Shared Modules [T1129]                                                    │
│ IMPACT               │ Resource Hijacking [T1496]                                                │
│ PERSISTENCE          │ Scheduled Task/Job::At [T1053.002]                                        │
│                      │ Scheduled Task/Job::Scheduled Task [T1053.005]                            │
└──────────────────────┴───────────────────────────────────────────────────────────────────────────┘
┌─────────────────────────────┬────────────────────────────────────────────────────────────────────┐
│ MAEC Category               │ MAEC Value                                                         │
├─────────────────────────────┼────────────────────────────────────────────────────────────────────┤
│ malware-category            │ launcher                                                           │
└─────────────────────────────┴────────────────────────────────────────────────────────────────────┘
┌──────────────────────────┬──────────────────────────────────────────────────────────────────────────┐
│ MBC Objective            │ MBC Behavior                                                             │
├──────────────────────────┼──────────────────────────────────────────────────────────────────────────┤
│ ANTI-BEHAVIORAL ANALYSIS │ Virtual Machine Detection [B0009]                                        │
│ ANTI-STATIC ANALYSIS     │ Executable Code Obfuscation::Argument Obfuscation [B0032.020]            │
│                          │ Executable Code Obfuscation::Stack Strings [B0032.017]                   │
│ COMMUNICATION            │ HTTP Communication [C0002]                                               │
│                          │ HTTP Communication::Read Header [C0002.014]                              │
│ DATA                     │ Check String [C0019]                                                     │
│                          │ Encode Data::Base64 [C0026.001]                                          │
│                          │ Encode Data::XOR [C0026.002]                                             │
│ DEFENSE EVASION          │ Obfuscated Files or Information::Encoding-Standard Algorithm [E1027.m02] │
│ DISCOVERY                │ File and Directory Discovery [E1083]                                     │
│ EXECUTION                │ Command and Scripting Interpreter [E1059]                                │
│ FILE SYSTEM              │ Create Directory [C0046]                                                 │
│                          │ Delete File [C0047]                                                      │
│                          │ Read File [C0051]                                                        │
│                          │ Writes File [C0052]                                                      │
│ MEMORY                   │ Allocate Memory [C0007]                                                  │
│ PROCESS                  │ Create Process [C0017]                                                   │
└──────────────────────────┴──────────────────────────────────────────────────────────────────────────┘
┌──────────────────────────────────────────────────────┬──────────────────────────────────────────────┐
│ Capability                                           │ Namespace                                    │
├──────────────────────────────────────────────────────┼──────────────────────────────────────────────┤
│ reference anti-VM strings                            │ anti-analysis/anti-vm/vm-detection           │
│ reference anti-VM strings targeting VMWare           │ anti-analysis/anti-vm/vm-detection           │
│ reference anti-VM strings targeting VirtualBox       │ anti-analysis/anti-vm/vm-detection           │
│ contain obfuscated stackstrings (2 matches)          │ anti-analysis/obfuscation/string/stackstring │
│ reference HTTP User-Agent string                     │ communication/http                           │
│ check HTTP status code                               │ communication/http/client                    │
│ reference Base64 string                              │ data-manipulation/encoding/base64            │
│ encode data using XOR                                │ data-manipulation/encoding/xor               │
│ contain a thread local storage (.tls) section        │ executable/pe/section/tls                    │
│ get common file path                                 │ host-interaction/file-system                 │
│ create directory                                     │ host-interaction/file-system/create          │
│ delete file                                          │ host-interaction/file-system/delete          │
│ read file on Windows (4 matches)                     │ host-interaction/file-system/read            │
│ write file on Windows (5 matches)                    │ host-interaction/file-system/write           │
│ get thread local storage value                       │ host-interaction/process                     │
│ create process on Windows                            │ host-interaction/process/create              │
│ allocate or change RWX memory                        │ host-interaction/process/inject              │
│ reference cryptocurrency strings                     │ impact/cryptocurrency                        │
│ link function at runtime on Windows (5 matches)      │ linking/runtime-linking                      │
│ parse PE header (4 matches)                          │ load-code/pe                                 │
│ resolve function by parsing PE exports (186 matches) │ load-code/pe                                 │
│ run PowerShell expression                            │ load-code/powershell/                        │
│ schedule task via at                                 │ persistence/scheduled-tasks                  │
│ schedule task via schtasks                           │ persistence/scheduled-tasks                  │
└──────────────────────────────────────────────────────┴──────────────────────────────────────────────┘
```

Since we know that the processing time takes several minutes, we have pre-processed this to a file named cryptbot.txt located in C:\Users\Administrator\Desktop\capa.  At the same time, this has been attached to this task; just click the button  from the upper right side of this task. Open another PowerShell terminal and use the command Get-Content cryptbot.txt

`PS C:\Users\Administrator\Desktop\capa> Get-Content .\cryptbot.txt`

Loading the content to PowerShell will give the same output from the terminal above.

 So, that's it! We are done!

 But wait, what are those results? How can we interpret this?

 **Answer the questions below**

 1. _What command-line option would you use if you need to check what other parameters you can use with the tool? Use the shortest format._

Answer: `-h`

2. _What command-line options are used to find detailed information on the malware's capabilities? Use the shortest format._

Answer: `-v`

3. _What command-line options do you use to find very verbose information about the malware's capabilities? Use the shortest format._

Answer: `-vv`

4. _What PowerShell command will you use to read the content of a file?_

Answer: `Get-Content`

---

**Module 3: Dissecting CAPA Results Part 1: General Information, MITRE and MAEC**

As mentioned in the previous task, the results of running CAPA against cryptbot.bin  will be discussed in the succeeding task. As such, we will dissect the results per block and topic.

The first block contains basic information about the file. This includes the following:

- The cryptographic algorithms, such as the md5, and sha1/256.

- The analysis field tells us how CAPA performed its analysis on the file.

- The os field reveals the operating system (OS) context for which the identified capabilities apply.

- The arch field allows us to determine whether we are dealing with a binary related to x86 architecture.

- The path where the analyzed file was located.

```
┌─────────────┬────────────────────────────────────────────────────────────────────────────────────┐
│ md5         │ 3b9d26d2e7433749f2c32edb13a2b0a2                                                   │
│ sha1        │ 969437df8f4ad08542ce8fc9831fc49a7765b7c5                                           │
│ sha256      │ ae7bc6b6f6ecb206a7b957e4bb86e0d11845c5b2d9f7a00a482bef63b567ce4c                   │
│ analysis    │ static                                                                             │
│ os          │ windows                                                                            │
│ format      │ pe                                                                                 │
│ arch        │ i386                                                                               │
│ path        │ /home/strategos/Room-CAPA/cryptbot.bin                                             │
└─────────────┴────────────────────────────────────────────────────────────────────────────────────┘
```

**MITRE ATT&CK**

The MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) framework is a comprehensive global knowledge repository that meticulously documents the tactics and techniques employed by threat actors at every stage of a cyber-attack. It functions as a strategic playbook, providing detailed insights into attackers' methods, from gaining initial access to maintaining a presence, escalating privileges, evading defenses, moving laterally within a network, and much more.

 CAPA uses this format for the output. Note that some results may or may not contain the Technique and Sub-technique Identifier. 


 ```
┌──────────────────────┬───────────────────────────────────────────────────────────────────────────┐
│ ATT&CK Tactic        │ ATT&CK Technique                                                          │
├──────────────────────┼───────────────────────────────────────────────────────────────────────────┤
│ DEFENSE EVASION      │ Obfuscated Files or Information [T1027]                                   │
│                      │ Obfuscated Files or Information::Indicator Removal from Tools [T1027.005] │
│                      │ Virtualization/Sandbox Evasion::System Checks [T1497.001]                 │
│ DISCOVERY            │ File and Directory Discovery [T1083]                                      │
│ EXECUTION            │ Command and Scripting Interpreter::PowerShell [T1059.001]                 │
│                      │ Shared Modules [T1129]                                                    │
│ IMPACT               │ Resource Hijacking [T1496]                                                │
│ PERSISTENCE          │ Scheduled Task/Job::At [T1053.002]                                        │
│                      │ Scheduled Task/Job::Scheduled Task [T1053.005]                            │
└──────────────────────┴───────────────────────────────────────────────────────────────────────────┘
```

 In CAPA's final output, they referenced the MITRE Framework. This helps analysts or defenders map the file's behaviour to the adversary's playbook, which can help narrow down the scope of the investigation during an incident. To dig deeper into this topic, you might want to check out our room for [MITRE ATT&CK Framework](https://tryhackme.com/r/room/mitre).

 **MAEC**
 
Malware Attribute Enumeration and Characterization is a specialized language designed to encode and communicate complex details concerning malware. It contains an extensive range of attributes, including behaviours, artefacts, and interconnections among various instances of malware. This language functions as a standardized system for tracking and analyzing the complicated complexities of malware.

```
┌─────────────────────────────┬────────────────────────────────────────────────────────────────────┐
│ MAEC Category               │ MAEC Value                                                         │
├─────────────────────────────┼────────────────────────────────────────────────────────────────────┤
│ malware-category            │ launcher                                                           │
└─────────────────────────────┴────────────────────────────────────────────────────────────────────┘
```

Let’s check the table below to see the most commonly used MAEC values by CAPA: Downloader and Launcher.

| MAEC Value | Description                                                                                     |
|------------|-------------------------------------------------------------------------------------------------|
| Launcher   | Exhibits behaviours that trigger specific actions similar to malware behaviour.                |
| Downloader | Exhibits behaviours wherein it downloads and executes other files, usually seen on more complex malware. |

When CAPA tags a file with a “launcher” MAEC value, it indicates that the file demonstrates behaviour similar to but not limited to:

- Dropping additional payloads

- Activating persistence mechanisms

- Connecting to command-and-control (C2) servers

- Executing specific functions

This is interesting! Some of these behaviours are also present in the Malware Behavior Catalogue (MBC)  and Capability block, which we will discuss in the next task!


Additionally, when CAPA tags a file with a “Downloader” MAEC value, it indicates that the file demonstrates behaviour similar but not limited to:

- Fetching additional payloads or resources from the internet

- pulling in updates

- executing secondary stages

- retrieving configuration files

**Answer the questions below**

1. _What is the sha256 of cryptbot.bin?_

Answer: `ae7bc6b6f6ecb206a7b957e4bb86e0d11845c5b2d9f7a00a482bef63b567ce4c`

2. _What is the Technique Identifier of Obfuscated Files or Information?_

Answer: `T1027`

3. _What is the Sub-Technique Identifier of Obfuscated Files or Information::Indicator Removal from Tools?_

Answer: `T1027.005`

4. _When CAPA tags a file with this MAEC value, it indicates that it demonstrates behaviour similar to, but not limited to, Activating persistence mechanisms?_

Answer: `launcher`

5. _When CAPA tags a file with this MAEC value, it indicates that the file demonstrates behaviour similar to, but not limited to, Fetching additional payloads or resources from the internet?_

Answer: `Downloader`

---

**Module 4: Dissecting CAPA Results Part 2: Malware Behavior Catalogue**

