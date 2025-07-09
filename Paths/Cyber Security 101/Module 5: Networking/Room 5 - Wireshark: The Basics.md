Link: https://tryhackme.com/room/wiresharkthebasics

![image](https://github.com/user-attachments/assets/5b30fc29-47c1-4b95-acac-fedc132d5d3e)

Learn the basics of Wireshark and how to analyse protocols and PCAPs.

**Module 1: Introduction**

Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools. In this room, we will look at the basics of Wireshark and use it to perform fundamental packet analysis.

There are two capture files given in the VM. You can use the “http1.pcapng” file to simulate the actions shown in the screenshots. Please note that you need to use the “Exercise.pcapng” file to answer the questions.

**Answer the questions below**

_Which file is used to simulate the screenshots?_

Answer: `http1.pcapng`

_Which file is used to answer the questions?_

Answer: `Exercise.pcapng`

--------------------------------------------------------------------------------------------------------------------------------------------------

**Module 2: Tool Overview**

﻿**Use Cases**

Wireshark is one of the most potent traffic analyser tools available in the wild. There are multiple purposes for its use:

- Detecting and troubleshooting network problems, such as network load failure points and congestion.

- Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.

- Investigating and learning protocol details, such as response codes and payload data.

Note: Wireshark is not an Intrusion Detection System (IDS). It only allows analysts to discover and investigate the packets in depth. It also doesn't modify packets; it reads them. Hence, detecting any anomaly or network problem highly relies on the analyst's knowledge and investigation skills.

**GUI and Data**

Wireshark GUI opens with a single all-in-one page, which helps users investigate the traffic in multiple ways. At first glance, five sections stand out.

| Component                   | Description                                                                                                                                         |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toolbar**                | The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting, and merging. |
| **Display Filter Bar**     | The main query and filtering section.                                                                                                               |
| **Recent Files**           | List of the recently investigated files. You can recall listed files with a double-click.                                                           |
| **Capture Filter and Interfaces** | Capture filters and available sniffing points (network interfaces). The network interface is the connection point between a computer and a network. The software connection (e.g., `lo`, `eth0`, `ens33`) enables networking hardware. |
| **Status Bar**             | Tool status, profile, and numeric packet information.                                                                                               |

Extra infomation:

```
A network interface is a point of connection between a computer and a network. It can be either hardware or software, and it allows your device to send and receive data over a network.
Types of Network Interfaces

- Physical (Hardware) Interfaces:

    - Ethernet (eth0, eth1, etc.): Wired network connections.

    - Wi-Fi (wlan0, etc.): Wireless network connections.

    - Fiber, Bluetooth, or USB adapters.

- Virtual (Software) Interfaces:

    - Loopback (lo): Used for internal communication within the same machine (e.g., 127.0.0.1).

    - VPN interfaces: Used by virtual private networks.

    - Bridge interfaces: Used in virtualization or advanced networking setups.

```

The below picture shows Wireshark's main window. The sections explained in the table are highlighted. Now open the Wireshark and go through the walkthrough.

 ![image](https://github.com/user-attachments/assets/165fe6a2-3844-461b-8cf1-2925ec3c8c6c)

 
**Loading PCAP Files**

Extra info: 

`PCAP files are packet capture files that store network traffic data. They are used to record and analyze packets transmitted over a network.`

The above picture shows Wireshark's empty interface. The only available information is the recently processed  "http1.cap" file. Let's load that file and see Wireshark's detailed packet presentation. Note that you can also use the "File" menu, dragging and dropping the file, or double-clicking on the file to load a pcap.

![image](https://github.com/user-attachments/assets/02186ad9-ad07-40da-88e1-49a19132728a)

Now, we can see the processed filename, detailed number of packets and packet details. Packet details are shown in three different panes, which allow us to discover them in different formats. 

| Pane                 | Description                                                                                                                                               |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Packet List Pane**  | Summary of each packet (source and destination addresses, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels. |
| **Packet Details Pane** | Detailed protocol breakdown of the selected packet.                                                                                                      |
| **Packet Bytes Pane** | Hex and decoded ASCII representation of the selected packet. It highlights the packet field depending on the clicked section in the details pane.          |


**Colouring Packets**

Along with quick packet information, Wireshark also colour packets in order of different conditions and the protocol to spot anomalies and protocols in captures quickly (this explains why almost everything is green in the given screenshots). This glance at packet information can help track down exactly what you're looking for during analysis. You can create custom colour rules to spot events of interest by using display filters, and we will cover them in the next room. Now let's focus on the defaults and understand how to view and use the represented data details.


Wireshark has two types of packet colouring methods: temporary rules that are only available during a program session and permanent rules that are saved under the preference file (profile) and available for the next program session. You can use the "right-click menu" or "View --> Coloring Rules" menu to create permanent colouring rules. The "Colourise Packet List" menu activates/deactivates the colouring rules. Temporary packet colouring is done with the "right-click menu" or "View --> Conversation Filter" menu, which is covered in TASK-5.

The default permanent colouring is shown below.

![image](https://github.com/user-attachments/assets/6e433280-dcab-4a9c-b1a0-e4e456b949a9)

**Traffic Sniffing**

You can use the blue "shark button" to start network sniffing (capturing traffic), the red button will stop the sniffing, and the green button will restart the sniffing process. The status bar will also provide the used sniffing interface and the number of collected packets.

![image](https://github.com/user-attachments/assets/19abd437-a8d0-40ea-b197-32259ec28aa7)

**Merge PCAP Files**

Wireshark can combine two pcap files into one single file. You can use the "File --> Merge" menu path to merge a pcap with the processed one. When you choose the second file, Wireshark will show the total number of packets in the selected file. Once you click "open", it will merge the existing pcap file with the chosen one and create a new pcap file. Note that you need to save the "merged" pcap file before working on it.

![image](https://github.com/user-attachments/assets/aecd47ac-431a-45e0-94b0-e39ccbdde581)


**View File Details**

Knowing the file details is helpful. Especially when working with multiple pcap files, sometimes you will need to know and recall the file details (File hash, capture time, capture file comments, interface and statistics) to identify the file, classify and prioritise it. You can view the details by following "**Statistics --> Capture File Properties**" or by clicking the "**pcap icon located on the left bottom**" of the window.

![image](https://github.com/user-attachments/assets/9fd5a5fa-82db-45a2-a032-5065225cf779)

**Answer the questions below**

**Use the "Exercise.pcapng" file to answer the questions.**

1. _Read the "capture file comments". What is the flag?_

Answer: `TryHackMe_Wireshark_Demo`

**_Explanation:_**

After opening Wireshark we see the file `Exercise.pcapng` under Open section and click on it

![image](https://github.com/user-attachments/assets/a857c15c-5a99-4eb0-b8bc-5c0d6d4c34ef)

Now under "Statistics" we select `capture file properties`, a pop-up window opens up

![image](https://github.com/user-attachments/assets/d275f063-e153-4561-b335-f82e266d62ac)

Now we scroll down in the pop-up window and we can see our flag

![image](https://github.com/user-attachments/assets/abb65315-cefc-48db-bdc7-505df254290c)

2. _What is the total number of packets?_

Answer: `58620`

**_Explanation:_**

Same steps as above till pop-up window appears

And we see something called `Packets` under Statistics and that is our answer to the second question

![image](https://github.com/user-attachments/assets/9e00a698-1440-461e-9753-0347b5174e7e)

3. _What is the SHA256 hash value of the capture file?_

Answer: `f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb`

**_Explanation:_**

Same steps as above till pop-up window appears

Under File section we find an entry called `Hash (SHA256)` and it's value is our answer

![image](https://github.com/user-attachments/assets/df8d21ce-8ba1-4be0-b8d5-5ceb787810ee)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Module 3: Packet Dissection**

**Packet Dissection**

Packet dissection is also known as protocol dissection, which investigates packet details by decoding available protocols and fields. Wireshark supports a long list of protocols for dissection, and you can also write your dissection scripts. You can find more details on dissection [here](https://github.com/boundary/wireshark/blob/master/doc/README.dissector).

Note: This section covers how Wireshark uses OSI layers to break down packets and how to use these layers for analysis. It is expected that you already have background knowledge of the OSI model and how it works. 

**Packet Details**

You can click on a packet in the packet list pane to open its details (double-click will open details in a new window). Packets consist of 5 to 7 layers based on the OSI model. We will go over all of them in an HTTP packet from a sample capture. The picture below shows viewing packet number 27.

![image](https://github.com/user-attachments/assets/0548a395-cb89-4b08-a5c6-081535f94c04)

Each time you click a detail, it will highlight the corresponding part in the packet bytes pane.

![image](https://github.com/user-attachments/assets/dd74f171-c10c-46ed-bf21-77bab070f077)

Let's have a closer view of the details pane.

![image](https://github.com/user-attachments/assets/717c3ac0-6a5e-46a9-84da-a6290acd97de)

We can see seven distinct layers to the packet: frame/packet, source [MAC], source [IP], protocol, protocol errors, application protocol, and application data. Below we will go over the layers in more detail.

**_The Frame (Layer 1)_**: This will show you what frame/packet you are looking at and details specific to the Physical layer of the OSI model.

![image](https://github.com/user-attachments/assets/996dc779-9ef5-4205-843a-ed41677628b1)

**_Source [MAC] (Layer 2)_**: This will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.

![image](https://github.com/user-attachments/assets/6a31a285-2270-44be-bdc0-e218188eb2a7)

**_Source [IP] (Layer 3)_**: This will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.

![image](https://github.com/user-attachments/assets/e1407517-9219-433e-b74e-3562236c83e9)

**_Protocol (Layer 4)_**: This will show you details of the protocol used (UDP/TCP) and source and destination ports; from the Transport layer of the OSI model.

![image](https://github.com/user-attachments/assets/2322771f-c2e0-484a-9bb9-0b675dc9bdab)

**_Protocol Errors_**: This continuation of the 4th layer shows specific segments from TCP that needed to be reassembled.

![image](https://github.com/user-attachments/assets/fe8ed99d-b46d-49dc-9fd7-98e3e20e7edf)

**_Application Protocol (Layer 5)_**: This will show details specific to the protocol used, such as HTTP, FTP,  and SMB. From the Application layer of the OSI model.

![image](https://github.com/user-attachments/assets/365d83c0-cc13-4dbc-ab9e-0d74d2d8ba81)

**_Application Data_**: This extension of the 5th layer can show the application-specific data.

![image](https://github.com/user-attachments/assets/eae97790-e435-49d3-a7c2-10602a46c3fb)

Now that we understand what a general packet is composed of, let's look at various application protocols and their specific details.

**Answer the questions below**

**Use the "Exercise.pcapng" file to answer the questions.**

1. _View packet number 38. Which markup language is used under the HTTP protocol?_

Answer: `eXtensible Markup Language`

**_Explanation:_**

We click on packet 38 once and then on the Packet details pane we see something called `eXtensible Markup Language` and that is our answer

![image](https://github.com/user-attachments/assets/5fcc16df-6793-4d9f-a601-f5493205e53f)

2. _What is the arrival date of the packet? (Answer format: Month/Day/Year)_

Answer: `05/13/2004`

**_Explanation_**

Same steps as above until we see `Arrival Time` under "Frame"

![image](https://github.com/user-attachments/assets/6fadb8ad-3321-4cb6-9f92-52fa277edfe4)

3. _What is the TTL value?_

Answer: `47`

**_Explanation:_**

Same steps as above until we see `Time to Live` under "Internet Protocol Version"

![image](https://github.com/user-attachments/assets/4e44da94-9b9e-42b0-8fb1-f09a3833c4f3)

4. _What is the TCP payload size?_

Answer: `424`

**_Explanation_**

We can find `TCP Payload` under `Transmission Control Protocol`

![image](https://github.com/user-attachments/assets/e499ff92-6e29-40ed-87d7-aa9e7b0052d3)

5. _What is the e-tag value?_

_(For example: 82ecb-6321-9e904585)_

Answer: `9a01a-4696-7e354b00`

**_Explanation:_**

Under "Hyper Text Transfer Protocol" we can see `E-Tag`

![image](https://github.com/user-attachments/assets/2a515134-31c6-48d2-9503-e097a80be862)
