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

---
