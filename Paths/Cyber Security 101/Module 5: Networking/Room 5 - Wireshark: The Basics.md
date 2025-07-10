Link: https://tryhackme.com/room/wiresharkthebasics (Premium Room)

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

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 4: Packet Navigation**

**Packet Numbers**

Wireshark calculates the number of investigated packets and assigns a unique number for each packet. This helps the analysis process for big captures and makes it easy to go back to a specific point of an event. 

![image](https://github.com/user-attachments/assets/a1babddd-4289-4fc3-8520-e146811d3441)

**Go to Packet**

Packet numbers do not only help to count the total number of packets or make it easier to find/investigate specific packets. This feature not only navigates between packets up and down; it also provides in-frame packet tracking and finds the next packet in the particular part of the conversation. You can use the "Go" menu and toolbar to view specific packets.

![image](https://github.com/user-attachments/assets/6a8c0c90-fa85-4b3c-9b80-c491f114ff11)

**Find Packets**

Apart from packet number, Wireshark can find packets by packet content. You can use the "Edit --> Find Packet" menu to make a search inside the packets for a particular event of interest. This helps analysts and administrators to find specific intrusion patterns or failure traces.

There are two crucial points in finding packets. The first is knowing the input type. This functionality accepts four types of inputs (Display filter, Hex, String and Regex). String and regex searches are the most commonly used search types. Searches are case insensitive, but you can set the case sensitivity in your search by clicking the radio button.

The second point is choosing the search field. You can conduct searches in the three panes (packet list, packet details, and packet bytes), and it is important to know the available information in each pane to find the event of interest. For example, if you try to find the information available in the packet details pane and conduct the search in the packet list pane, Wireshark won't find it even if it exists.

![image](https://github.com/user-attachments/assets/cef359bb-03a0-48c3-9ede-8321d34be697)

**Mark Packets**

Marking packets is another helpful functionality for analysts. You can find/point to a specific packet for further investigation by marking it. It helps analysts point to an event of interest or export particular packets from the capture. You can use the "Edit" or the "right-click" menu to mark/unmark packets.

Marked packets will be shown in black regardless of the original colour representing the connection type. Note that marked packet information is renewed every file session, so marked packets will be lost after closing the capture file. 

![image](https://github.com/user-attachments/assets/bfaa7242-f412-4680-989b-10b461795585)

**Packet Comments**

Similar to packet marking, commenting is another helpful feature for analysts. You can add comments for particular packets that will help the further investigation or remind and point out important/suspicious points for other layer analysts. Unlike packet marking, the comments can stay within the capture file until the operator removes them.

![image](https://github.com/user-attachments/assets/c0edb86e-80c0-4d68-9b7c-988c78369a73)

**Export Packets**

Capture files can contain thousands of packets in a single file. As mentioned earlier, Wireshark is not an IDS, so sometimes, it is necessary to separate specific packages from the file and dig deeper to resolve an incident. This functionality helps analysts share the only suspicious packages (decided scope). Thus redundant information is not included in the analysis process. You can use the "File" menu to export packets.

![image](https://github.com/user-attachments/assets/9eebac1f-5e77-4339-a86f-e3ee6f7eeae0)

**Export Objects (Files)**

Wireshark can extract files transferred through the wire. For a security analyst, it is vital to discover shared files and save them for further investigation. Exporting objects are available only for selected protocol's streams (DICOM, HTTP, IMF, SMB and TFTP).

![image](https://github.com/user-attachments/assets/a0f85507-4a5b-4eae-8396-c11c659ed004)

**Time Display Format**

Wireshark lists the packets as they are captured, so investigating the default flow is not always the best option. By default, Wireshark shows the time in "Seconds Since Beginning of Capture", the common usage is using the UTC Time Display Format for a better view. You can use the "View --> Time Display Format" menu to change the time display format.

![image](https://github.com/user-attachments/assets/950412c6-7682-402f-bc3b-2e7713adee57)

![image](https://github.com/user-attachments/assets/85bd9d9c-e392-45ff-943c-3109e559a2de)

**Expert Info**

Wireshark also detects specific states of protocols to help analysts easily spot possible anomalies and problems. Note that these are only suggestions, and there is always a chance of having false positives/negatives. Expert info can provide a group of categories in three different severities. Details are shown in the table below.

| Severity | Colour | Info                                                        |
|----------|--------|-------------------------------------------------------------|
| Chat     | 🟦 Blue   | Information on usual workflow.                             |
| Note     | 🟦 Cyan   | Notable events like application error codes.               |
| Warn     | 🟨 Yellow | Warnings like unusual error codes or problem statements.    |
| Error    | 🟥 Red    | Problems like malformed packets.                           |


Frequently encountered information groups are listed in the table below. You can refer to Wireshark's official documentation for more information on the expert information entries.

| Group      | Info                          | Group      | Info                             |
|------------|-------------------------------|------------|----------------------------------|
| Checksum   | Checksum errors.              | Deprecated | Deprecated protocol usage.       |
| Comment    | Packet comment detection.     | Malformed  | Malformed packet detection.      |

You can use the "lower left bottom section" in the status bar or "Analyse --> Expert Information" menu to view all available information entries via a dialogue box. It will show the packet number, summary, group protocol and total occurrence.

![image](https://github.com/user-attachments/assets/af4fb27f-dd17-4f2a-8baa-7729edbee5d9)

**Answer the questions below**

**Use the "Exercise.pcapng" file to answer the questions.**

1. _Search the "r4w" string in packet details. What is the name of artist 1?_

Answer:`r4w8173`

**_Explanation:_**

Click on View Site button and we can open the `Exercise.pcapng` file on Wireshark

And after opening the file click on `Edit -> Find Packet`

![image](https://github.com/user-attachments/assets/ea21e48e-26ee-4b99-b407-abbdecd743bf)

A space box opens with options on its left side

![image](https://github.com/user-attachments/assets/cb6e24cf-3030-44cb-9f80-6d3e647d6ea1)

Type `r4w` and ensure the option is selected as `String` and click on "Find" button

![image](https://github.com/user-attachments/assets/cfa6d69b-5299-4487-8f40-d47eb34b1511)

We see something like this and there inside h3 tag we can see `r4w8173` after artist 1 and that is our answer

![image](https://github.com/user-attachments/assets/44a03ef9-2528-481b-a0c2-72e80766eae6)


2. _Go to packet 12 and read the packet comments. What is the answer?
Note: use md5sum <filename> terminal command to get MD5 hash_

Answer: `911cd574a42865a956ccde2d04495ebf`

**_Exaplanation:_**

We go to the packet 12 and click on "Edit-> Packet Comment" and a pop up window appears and now we scroll down and find that we need to refer to a packet with the number `39765` and then we need to follow the instructions 

![image](https://github.com/user-attachments/assets/b57e8e26-05f3-4875-93db-5e293e27cc62)

![image](https://github.com/user-attachments/assets/ab7efe9b-b309-4698-b47c-5d7f577c26d3)

First we go to the packet 39765 and we find JPEG 

![image](https://github.com/user-attachments/assets/294ac96b-f52f-4880-86fa-878013d129e1)

Now we right click on that and select `Export Packet Bytes`

![image](https://github.com/user-attachments/assets/ba912c76-373d-45c6-995d-a1840dc2c9bf)

And now we save it to our local

![image](https://github.com/user-attachments/assets/0535e111-ee4d-48c5-8b85-a85849cee602)

And we use `md5sum filename` to get our flag

![image](https://github.com/user-attachments/assets/dafaa1b5-cea0-4677-bffb-3060edd91835)

2. _There is a ".txt" file inside the capture file. Find the file and read it; what is the alien's name?_

Answer: `PACKETMASTER`

**_Explanation:_**

We go to the `File -> Export Objects` and select `HTTP`

![image](https://github.com/user-attachments/assets/0dafcd1a-8b14-4ed8-a453-b35e4dd3eb0e)

A diglog box opens and we scroll down to see a file named `note.txt` and we save this file to our local

![image](https://github.com/user-attachments/assets/30b53e18-6059-445d-b63b-4f85a2cffe8a)

Now we open the file to find the name of the alien

![image](https://github.com/user-attachments/assets/59ccc125-a01f-4678-a86a-2db392140bf9)

3. _Look at the expert info section. What is the number of warnings?_

Answer: `1636`

**_Explanation:_**

We click on `Analyze -> Export Information`

![image](https://github.com/user-attachments/assets/7779eeb6-023d-472e-951b-5a706d81397b)

Export Information dialog box opens and we see Warnings count is 1636

![image](https://github.com/user-attachments/assets/a87dfa49-a609-48da-8ce8-1f87e744f9e2)

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 5: Packet Filtering**

**Packet Filtering**

Wireshark has a powerful filter engine that helps analysts to narrow down the traffic and focus on the event of interest. Wireshark has two types of filtering approaches: capture and display filters. Capture filters are used for "capturing" only the packets valid for the used filter. Display filters are used for "viewing" the packets valid for the used filter. We will discuss these filters' differences and advanced usage in the next room. Now let's focus on basic usage of the display filters, which will help analysts in the first place.

Filters are specific queries designed for protocols available in Wireshark's official protocol reference. While the filters are only the option to investigate the event of interest, there are two different ways to filter traffic and remove the noise from the capture file. The first one uses queries, and the second uses the right-click menu. Wireshark provides a powerful GUI, and there is a golden rule for analysts who don't want to write queries for basic tasks: "If you can click on it, you can filter and copy it".

**Apply as Filter**

This is the most basic way of filtering traffic. While investigating a capture file, you can click on the field you want to filter and use the "right-click menu" or "Analyse --> Apply as Filter" menu to filter the specific value. Once you apply the filter, Wireshark will generate the required filter query, apply it, show the packets according to your choice, and hide the unselected packets from the packet list pane. Note that the number of total and displayed packets are always shown on the status bar.

![image](https://github.com/user-attachments/assets/d32c34c1-60ec-4088-9b87-e40c0c6da12f)

**Conversation Filter**

When you use the "Apply as a Filter" option, you will filter only a single entity of the packet. This option is a good way of investigating a particular value in packets. However, suppose you want to investigate a specific packet number and all linked packets by focusing on IP addresses and port numbers. In that case, the "Conversation Filter" option helps you view only the related packets and hide the rest of the packets easily. You can use the"right-click menu" or "Analyse --> Conversation Filter" menu to filter conversations.


![image](https://github.com/user-attachments/assets/b2943ce4-6c9e-447c-9d23-0d70a8aa5a74)

**Colourise Conversation**

This option is similar to the "Conversation Filter" with one difference. It highlights the linked packets without applying a display filter and decreasing the number of viewed packets. This option works with the "Colouring Rules" option ad changes the packet colours without considering the previously applied colour rule. You can use the "right-click menu" or "View --> Colourise Conversation" menu to colourise a linked packet in a single click. Note that you can use the "View --> Colourise Conversation --> Reset Colourisation" menu to undo this operation.

![image](https://github.com/user-attachments/assets/ebe3a40e-787b-4bf3-ad21-41a686496264)

**Prepare as Filter**

Similar to "Apply as Filter", this option helps analysts create display filters using the "right-click" menu. However, unlike the previous one, this model doesn't apply the filters after the choice. It adds the required query to the pane and waits for the execution command (enter) or another chosen filtering option by using the ".. and/or.." from the "right-click menu".

![image](https://github.com/user-attachments/assets/2b96f91a-612c-40e7-8f9b-5273ac3d4dda)

**Apply as Column**

By default, the packet list pane provides basic information about each packet. You can use the "right-click menu" or "Analyse --> Apply as Column" menu to add columns to the packet list pane. Once you click on a value and apply it as a column, it will be visible on the packet list pane. This function helps analysts examine the appearance of a specific value/field across the available packets in the capture file. You can enable/disable the columns shown in the packet list pane by clicking on the top of the packet list pane.

![image](https://github.com/user-attachments/assets/e5615df6-00b4-4b8a-bf52-074a2c8c010a)

**Follow Stream**

Wireshark displays everything in packet portion size. However, it is possible to reconstruct the streams and view the raw traffic as it is presented at the application level. Following the protocol, streams help analysts recreate the application-level data and understand the event of interest. It is also possible to view the unencrypted protocol data like usernames, passwords and other transferred data.

You can use the"right-click menu" or  "Analyse --> Follow TCP/UDP/HTTP Stream" menu to follow traffic streams. Streams are shown in a separate dialogue box; packets originating from the server are highlighted with blue, and those originating from the client are highlighted with red.

![image](https://github.com/user-attachments/assets/cd512ee9-a04c-4d31-8b13-b90971f2f206)

Once you follow a stream, Wireshark automatically creates and applies the required filter to view the specific stream. Remember, once a filter is applied, the number of the viewed packets will change. You will need to use the "X button" located on the right upper side of the display filter bar to remove the display filter and view all available packets in the capture file. 

**Answer the questions below**

**Use the "Exercise.pcapng" file to answer the questions.**

1. _Go to packet number 4. Right-click on the "Hypertext Transfer Protocol" and apply it as a filter.
Now, look at the filter pane. What is the filter query?_

Answer: `http`

**_Explanation:_**

We go to the packet 4 and right click on `Hyper Text Transfer Protocol` and select 'Apply as filter-> Selected'

![image](https://github.com/user-attachments/assets/34d308c0-967b-4c6c-97df-9bb758ee6b9b)

And we can see a bar on the top with the text `http` and that is our answer

![image](https://github.com/user-attachments/assets/f5993f92-6b9e-4832-93ee-61144c097703)


2. _What is the number of displayed packets?_

Answer: `1089`

**_Explanation_**

We can find at the answer at the status bar 

![image](https://github.com/user-attachments/assets/67c00555-f219-4f25-82ad-5417bd60b8c0)

3. _Go to packet number 33790, follow the HTTP stream, and look carefully at the responses.
Looking at the web server's response, what is the total number of artists?_

Answer: `3`

**_Explanation:_**

We go to the packet 33790 and click on `Analyze -> Follow -> HTTP Stream`

![image](https://github.com/user-attachments/assets/822a9429-7b47-4278-8383-63a679248953)

And a dialog box opens, and we find there are 3 artists totally

![image](https://github.com/user-attachments/assets/c4b72ab2-1ceb-45b3-9d91-7836bd1777f8)


4. _What is the name of the second artist?_

Answer: `Blad3`

**_Explanation:_**

We see a h3 tag with the name of the 2nd artist

![image](https://github.com/user-attachments/assets/eb50829e-3053-4eed-ad50-2abc42c8e758)

--------------------------------------------------------------------------------------------------------------------------------------------

**Module 6: Conclusion**

Congratulations! You just finished the "Wireshark: The Basics" room. In this room, we covered Wireshark, what it is, how it operates, and how to use it to investigate traffic captures. 

Want to learn more? We invite you to complete the [Wireshark: Packet Operations](https://tryhackme.com/jr/wiresharkpacketoperations) room to improve your Wireshark skills by investigating packets in-depth. 

**Answer the questions below**

_Proceed to the next room and keep learning!_

Answer: No answer needed

--------------------------------------------------------------------------------------------------------------------------------------------
