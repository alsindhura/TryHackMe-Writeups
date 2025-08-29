Link: https://tryhackme.com/room/socfundamentals 

<img width="1201" height="1201" alt="image" src="https://github.com/user-attachments/assets/081004db-1d0c-4fad-b3fe-3843f4ed4393" />

Learn about the SOC team and their processes.

**Module 1: Introduction to SOC**

Technology has made our lives more efficient, but with this efficiency comes more responsibility. Modern-day fears have come a long way from the exploitation of physical assets. The critical data, called secrets, are no longer stored in physical files. Organizations carry tons of confidential data in their network and systems. Any unauthorized disruption, loss, or modification to this data may cause them a huge damage. Threat actors discover and exploit new vulnerabilities in these networks and systems daily, becoming a major concern in cyber security. Traditional security practices may not be enough to prevent many of these threats. Dedicating a whole team to managing your organization’s security is important.

A SOC (Security Operations Center) is a dedicated facility operated by a specialized security team. This team aims to continuously monitor an organization’s network and resources and identify suspicious activity to prevent damage. This team works 24 hours a day, seven days a week.

This room will delve into some key concepts of SOC, one of the most important fields in defensive security.

**Learning Objectives**

- Building a baseline for SOC (Security Operations Center)

- Detection and response in SOC

- The role of People, Processes, and Technology

- Practical exercise

**Answer the questions below**

1. _What does the term SOC stand for?_

Answer: `Security Operations Center`

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Purpose and Components**

The main focus of the SOC team is to keep Detection and Response intact. The SOC team has some resources available in the form of security solutions that help them achieve this. These solutions integrate the whole company’s network and all the systems to monitor them from one centralized location. Continuous monitoring is required to detect and respond to any security incident.

<img width="794" height="634" alt="image" src="https://github.com/user-attachments/assets/b866ee70-0d72-4502-b558-011c4f0a2e2b" />

**Detection**

- **_Detect vulnerabilities_**: A vulnerability is a weakness that an attacker can exploit to carry out things beyond their permission level. A vulnerability might be discovered in any device’s software (operating system and programs), such as a server or computer. For instance, the SOC might discover a set of MS Windows computers that must be patched against a specific published vulnerability. Strictly speaking, vulnerabilities are not necessarily the SOC’s responsibility; however, unfixed vulnerabilities affect the security level of the entire company.

- **_Detect unauthorized activity_**: Consider the case where an attacker discovered the username and password of one of the employees and used them to log in to the company system. It is crucial to detect this kind of unauthorized activity quickly before it causes any damage. Many clues, such as geographic location, can help us detect this.

- **_Detect policy violations_**: A security policy is a set of rules and procedures created to help protect a company against security threats and ensure compliance. What is considered a violation would vary from company to company; examples include downloading pirated media files and sending confidential company files insecurely.

- **_Detect intrusions_**: Intrusions refer to unauthorized access to systems and networks. One scenario would be an attacker successfully exploiting our web application. Another would be a user visiting a malicious site and getting their computer infected.

**Response**

Support with the incident response: Once an incident is detected, certain steps are taken to respond to it. This response includes minimizing its impact and performing the root cause analysis of the incident. The SOC team also helps the incident response team carry out these steps.

There are three pillars of a SOC. With all these pillars, a SOC team becomes mature and efficiently detects and responds to different incidents. These pillars are People, Process, and Technology.

<img width="825" height="801" alt="image" src="https://github.com/user-attachments/assets/5e907e74-f560-4e56-9dd6-90d50ccf735e" />

People, Process, and Technology coexist in a SOC environment. A team of professional individuals working on state-of-the-art security tools in the presence of proper processes is what makes a mature SOC environment.

In the upcoming tasks, we will discuss each of these pillars individually and examine how they are important parts of SOC.

**Answer the questions below**

1. _The SOC team discovers an unauthorized user is trying to log in to an account. Which capability of SOC is this?_

Answer: `Detection`

2. _What are the three pillars of a SOC?_

Answer: `People, Process, Technology`

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: People**

Regardless of the evolution of automating the majority of security tasks, the People in a SOC will always be important. A security solution can generate numerous red flags in a SOC environment, which can cause huge noise.

Imagine you are part of a fire brigade team and have centralized software where all the city’s fire alarms are integrated. Suppose you get many fire notifications at once, all for different places. When you get into those locations, your team finds out most of those were only triggered by excessive smoke from cooking. Eventually, all the efforts will be a waste of time and resources.

In a SOC, with security solutions in place without human intervention, you'll end up focusing on more irrelevant issues. There are always the People who help the security solution to identify truly harmful activities and enable a prompt response.

The People are known as the SOC team. This team has the following roles and responsibilities.

<img width="1140" height="572" alt="image" src="https://github.com/user-attachments/assets/81f4cd89-4ddd-4edb-8e37-3293b1b07871" />


- **_SOC Analyst (Level 1)_**: Anything detected by the security solution would pass through these analysts first. These are the first responders to any detection. SOC Level 1 Analysts perform basic alert triage to determine if a specific detection is harmful. They also report these detections through proper channels.

- **_SOC Analyst (Level 2)_**: While Level 1 does the first-level analysis, some detections may require deeper investigation. Level 2 Analysts help them dive deeper into the investigations and correlate the data from multiple data sources to perform a proper analysis.

- **_SOC Analyst (Level 3)_**: Level 3 Analysts are experienced professionals who proactively look for any threat indicators and support in the incident response activities. The critical severity detection reported by Level 1 and Level 2 Analysts are often security incidents that need detailed responses, including containment, eradication, and recovery. This is where Level 3 analysts’ experience comes in handy.

- **_Security Engineer_**: All analysts work on security solutions. These solutions need deployment and configuration. Security Engineers deploy and configure these security solutions to ensure their smooth operation.

- **_Detection Engineer_**: Security rules are the logic built behind security solutions to detect harmful activities. Level 2 and 3 Analysts often create these rules, while the SOC team can sometimes also utilize the detection engineer role independently for this responsibility.

- **_SOC Manager_**: The SOC Manager manages the processes the SOC team follows and provides support. The SOC Manager also remains in contact with the organization’s CISO (Chief Information Security Officer) to provide him with updates on the SOC team’s current security posture and efforts.

Note: The roles in the SOC team can increase or decrease depending on the size and criticality of the organizations.

**Answer the questions below**

1. _Alert triage and reporting is the responsibility of?_

Answer: `SOC Analyst (Level 1)`

2. _Which role in the SOC team allows you to work dedicatedly on establishing rules for alerting security solutions?_

Answer: `Detection Engineer`

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Process**

We discussed the roles and responsibilities of different individuals working in the SOC team. Each role has its own Processes, just as we saw the role of Level 1 SOC Analysts as the first responders to carry out alert triage and determine if it is harmful. Let’s discuss some important processes involved in a SOC.

**Alert Triage**

The alert triage is the basis of the SOC team. The first response to any alert is to perform the triage. The triage is focused on analyzing the specific alert. This determines the severity of the alert and helps us prioritize it. The alert triage is all about answering the 5 Ws. What are these 5 Ws?

<img width="740" height="627" alt="image" src="https://github.com/user-attachments/assets/e502f533-73b8-42e1-9f19-b5d87eb0c80d" />

Following are some questions that need to be answered during the triage of an alert. 

**Alert**: Malware detected on Host: GEORGE PC


| **5 Ws**  | **Answers** |
|----------|-------------|
| **What?** | A malicious file was detected on one of the hosts inside the organization’s network. |
| **When?** | The file was detected at 13:20 on June 5, 2024. |
| **Where?** | The file was detected in the directory of the host: "GEORGE PC". |
| **Who?** | The file was detected for the user George. |
| **Why?** | After the investigation, it was found that the file was downloaded from a pirated software-selling website. The investigation with the user revealed that they downloaded the file as they wanted to use a software for free. |

**Reporting**

The detected harmful alerts need to be escalated to higher-level analysts for a timely response and resolution. These alerts are escalated as tickets and assigned to the relevant people. The report should discuss all the 5 Ws along with a thorough analysis, and screenshots should be used as evidence of the activity.

**Incident Response and Forensics**

Sometimes, the reported detections point to highly malicious activities that are critical. In these scenarios, high-level teams initiate an incident response. The incident response process is discussed in detail in the [Incident Response](https://tryhackme.com/r/room/incidentresponsefundamentals) room. A few times, a detailed forensics activity also needs to be performed. This forensic activity aims to determine the incident’s root cause by analyzing the artifacts from a system or network.

**Answer the questions below**

1. _At the end of the investigation, the SOC team found that John had attempted to steal the system's data. Which 'W' from the 5 Ws does this answer?_

Answer: `Who`

2. _The SOC team detected a large amount of data exfiltration. Which 'W' from the 5 Ws does this answer?_

Answer: `What`

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: Technology**

Having the right People and Processes in place would never be enough without security solutions for detection and response. The Technology portion in the SOC pillars refers to the security solutions. These security solutions efficiently minimize the SOC team's manual effort to detect and respond to threats.

An organization’s network consists of many devices and applications. As a security team, individually detecting and responding to threats in each device or application would require significant effort and resources. Security solutions centralize all the information of the devices or applications present in the network and automate the detection and response capabilities.

Let's get a brief understanding of some of these security solutions:

- **_SIEM_**: Security Information and Event Management (SIEM) is a popular tool used in almost every SOC environment. This tool collects logs from various network devices, referred to as log sources. Detection rules are configured in the SIEM solution, which contains logic to identify suspicious activity. The SIEM solution provides us with the detections after correlating them with multiple log sources and alerts us in case of a match with any of the rules. Modern SIEM solutions surpass this rule based detection analysis, providing us with user behavior analytics and threat intelligence capability. Machine learning algorithms support this to enhance the detection capabilities.

Note: The SIEM solution only provides the Detection capabilities in a SOC environment.

- **_EDR_**: Endpoint Detection and Response (EDR) provides the SOC team with detailed real-time and historical visibility of the devices’ activities. It operates on the endpoint level and can carry out automated responses. EDR has extensive detection capabilities for endpoints, allowing you to investigate them in detail and respond with a few clicks.

- **_Firewall_**: A firewall functions purely for network security and acts as a barrier between your internal and external networks (such as the Internet). It monitors incoming and outgoing network traffic and filters any unauthorized traffic. The firewall also has some detection rules deployed, which help us identify and block suspicious traffic before it reaches the internal network.

Several other security solutions play unique roles in a SOC environment, such as Antivirus, EPP, IDS/IPS, XDR, SOAR, and more. The decision on what Technology to deploy in the SOC comes after careful consideration of the threat surface and the available resources in the organization.

**Answer the questions below**

1. _Which security solution monitors the incoming and outgoing traffic of the network?_

Answer: `Firewall`

2. _Do SIEM solutions primarily focus on detecting and alerting about security incidents? (yea/nay)_

Answer: `yea`

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Practical Exercise of SOC**

This practical exercise uses People, Processes, and Technology and gives you a practical walkthrough of the role of a Level 1 Analyst in the SOC team.

Click on the View Site button below to display the lab on the right side of the screen.

Scenario

You are the Level 1 Analyst of your organization’s SOC team. You receive an alert that a port scanning activity has been observed on one of the hosts in the network. You have access to the SIEM solution, where you can see all the associated logs for this alert. You are tasked to view the logs individually and answer the question to the 5 Ws given below.

Note: The vulnerability assessment team notified the SOC team that they were running a port scan activity inside the network from the host: `10.0.0.8`

**Answer the questions below**

1. _What: Activity that triggered the alert?_

Answer: `Port Scan`

**_Explanation:_**

We click on "View Site" and we can see an issue called "Port Scanning" open

<img width="1020" height="890" alt="image" src="https://github.com/user-attachments/assets/63fd6617-4e0a-4b74-8435-da6104fc37a8" />

2. _When: Time of the activity?_

Answer: `June 12, 2024 17:24`

**_Explanation:_**

We can see the time 

<img width="1023" height="883" alt="image" src="https://github.com/user-attachments/assets/86e6dc02-40b2-40a5-9c63-f7e8b679158f" />

3. _Where: Destination host IP?_

Answer: `10.0.0.3`

**_Explanation:_**

We can see a button called "Acknowledge" and clicking on that shows another button called "Investigate in SIEM" 

<img width="1020" height="885" alt="image" src="https://github.com/user-attachments/assets/2c161143-b2a0-4b71-89a7-fbc57ac1b935" />
<img width="1023" height="892" alt="image" src="https://github.com/user-attachments/assets/3a8882b2-0e79-4d82-aef0-f1a7129055fc" />

We click on "Investigate in SIEM" and scrolling down we can see the Destination IP address

<img width="1019" height="879" alt="image" src="https://github.com/user-attachments/assets/0baba386-0872-47bb-88bc-e88b34314514" />

4. _Who: Source host name?_

Answer: `NESSUS`

**_Explanation:_**

We scroll right and we can see the source host name

<img width="1020" height="880" alt="image" src="https://github.com/user-attachments/assets/cbea37d1-a48e-4f07-9c5a-cb656d24ec5f" />

5. _Why: Reason for the activity? Intended/Malicious_

Answer: `Intended`

**_Why_**

Because the source range is "Private" and a tool called "Nessus" is used within private network

6. _Additional Investigation Notes: Has any response been sent back to the port scanner IP? (yea/nay)_

Answer: `yea`

**_Explanation:_**

We can see the source IP as `10.0.0.3` and destination IP as `10.0.0.8`

<img width="1027" height="856" alt="image" src="https://github.com/user-attachments/assets/25360f62-69da-4721-9b04-4f224bf68cde" />


7. _What is the flag found after closing the alert?_

Answer: `THM{000_INTRO_TO_SOC}`

**_Explanation:_**

We click on the button "Complete Investigation"

<img width="1020" height="878" alt="image" src="https://github.com/user-attachments/assets/fd84161f-613f-417c-b1c3-63e1bcae73ad" />

We will see a dialog box with the options 

<img width="684" height="315" alt="image" src="https://github.com/user-attachments/assets/0d379d6d-a348-4bc3-a0e4-176e767bfdb6" />

Since this is intended and not a malicious one we select the option B

<img width="491" height="451" alt="image" src="https://github.com/user-attachments/assets/629e6b69-a513-48b7-87b6-fda9093652cb" />

Now we click on "Go To Alerts Dashboard"

<img width="1012" height="884" alt="image" src="https://github.com/user-attachments/assets/8dc7058e-7124-439e-8264-f7599f3b57f1" />

And click on Close Alert and we can see the flag

<img width="425" height="185" alt="image" src="https://github.com/user-attachments/assets/d6d63c10-a18e-405e-a126-c8295bee9b39" />

------------------------------------------------------------------------------------------------------------------------------------------------

**Module 7: Conclusion**

This room helped us learn some exciting facts about the SOC team. We saw its responsibilities and the pillars, People, Process, and Technology, that mature any SOC environment. This room focused on understanding how People, Processes, and Technology play their roles in the day-to-day SOC use cases. Lastly, we got our hands on a practice lab and solved a real-world SOC alert as a level 1 Analyst.

**Answer the questions below**

1. _I understand the fundamentals of a SOC._

Answer: No answer needed

------------------------------------------------------------------------------------------------------------------------------------------------
