# Sec 5.2. Wireshark The Basics

### Task 1 - Introduction

Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools.  

**Answer the questions below**

> Which file is used to simulate the screenshots? http1.pcapng
> 

> Which file is used to answer the questions? Exercise.pcapng
> 

### Task 2 - Tool Overview

**Use Cases:** Wireshark is one of the most potent traffic analyser tools available in the wild. There are multiple purposes for its use:

- Detecting and troubleshooting network problems, such as network load failure points and congestion.
- Detecting security anomalies, such as rogue hosts, abnormal port usage, and suspicious traffic.
- Investigating and learning protocol details, such as response codes and payload data.

Note: Wireshark is not an Intrusion Detection System (IDS). It only allows analysts to discover and investigate the packets in depth. It also doesn't modify packets; it reads them. Hence, detecting any anomaly or network problem highly relies on the analyst's knowledge and investigation skills.

**GUI and Data**  

| **Toolbar** | The main toolbar contains multiple menus and shortcuts for packet sniffing and processing, including filtering, sorting, summarising, exporting and merging. |
| --- | --- |
| **Display Filter Bar** | The main query and filtering section. |
| **Recent Files** | List of the recently investigated files. You can recall listed files with a double-click. |
| **Capture Filter and Interfaces** | Capture filters and available sniffing points (network interfaces).  The network interface is the connection point between a computer and a network. The software connection (e.g., lo, eth0 and ens33) enables networking hardware. |
| **Status Bar** | Tool status, profile and numeric packet information. |

![Wireshark - GUI](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761929821594.svg)

**Loading PCAP Files: D**ragging and dropping the file, or double-clicking on the file to load a pcap.

![Wireshark details](https://cdn-images.tryhackme.com/user-uploads/678ecc92c80aa206339f0f23/room-content/678ecc92c80aa206339f0f23-1767892422149.svg)

| Packet List Pane | Summary of each packet (source and destination addresses, protocol, and packet info). You can click on the list to choose a packet for further investigation. Once you select a packet, the details will appear in the other panels. |
| --- | --- |
| Packet Details Panel | Detailed protocol breakdown of the selected packet. |
| Packet Bytes Pane | Hex and decoded ASCII representation of the selected packet. It highlights the packet field depending on the clicked section in the details pane. |

**Colouring Packets: "View --> Coloring Rules"** menu to create permanent colouring rules.  

![Wireshark - packet colours](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1760957486290.svg)

**Traffic Sniffing:** The blue **"shark button"** to start network sniffing (capturing traffic), the red button will stop the sniffing, and the green button will restart the sniffing process.  

![Wireshark - traffic sniffing](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1760967343208.png)

**Merge PCAP Files:**  You can use the **"File --> Merge"** menu path to merge a pcap with the processed one.   

**View File Details:** You can view the details by following "**Statistics --> Capture File Properties"** or by clicking the **"pcap icon located on the left bottom"**. 

> Use the "Exercise.pcapng" file to answer the questions. Read the "capture file comments". What is the flag?
> 

TryHackMe_Wireshark_Demo

<img width="788" height="482" alt="image" src="https://github.com/user-attachments/assets/88e9bbb8-5f42-48c3-8018-c1e57d6729b7" />


> What is the total number of packets? 58620
> 

<img width="861" height="41" alt="image 1" src="https://github.com/user-attachments/assets/9440b548-e0d7-4db4-99b4-181f3c3a12dc" />

> What is the SHA256 hash value of the capture file?
> 

f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb

<img width="782" height="363" alt="image 2" src="https://github.com/user-attachments/assets/0ef7075c-84ed-4ca3-a19d-b2b0cc2d674b" />


### Task 3 - Packet Dissection

Wireshark supports a long list of protocols for dissection, and you can also write your dissection scripts.  

**Packet Details:** You can click on a packet in the packet list pane to open its details (double-click will open details in a new window). Packets consist of 5 to 7 layers based on the OSI model. 

![Wireshark - packet details](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761041216054.svg)

Each time you click a detail, it will highlight the corresponding part in the packet bytes pane. 

![Wireshark - packet bytes](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761041609772.svg)

![Wireshark - packet details](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761041779487.png)

We can see seven distinct layers to the packet: `frame/packet`,`source [MAC]`,`source [IP]`,`protocol`,`protocol errors`, `application protocol`, and `application data`. Below we will go over the layers in more detail.

**The Frame (Layer 1):**This will show you what frame/packet you are looking at and details specific to the Physical layer of the OSI model.

![Wireshark - layer 1](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761041779538.png)

**Source [MAC] (Layer 2):**This will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.

![Wireshark - layer 2](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761042014059.png)

**Source [IP] (Layer 3):**This will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.

![Wireshark - layer 3](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761042013990.png)

**Protocol (Layer 4):**This will show you details of the protocol used (UDP/TCP) and source and destination ports; from the Transport layer of the OSI model.

![Wireshark - layer 4](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761042014024.png)

**Protocol Errors:** This continuation of the 4th layer shows specific segments from TCP that needed to be reassembled.

![Wireshark - protocol error](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761042204301.png)

**Application Protocol (Layer 5):**This will show details specific to the protocol used, such as HTTP, FTP,  and SMB. From the Application layer of the OSI model.

![Wireshark - layer 5](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761042014014.png)

**Application Data:** This extension of the 5th layer can show the application-specific data.


**Answer the questions below**

> Use the "Exercise.pcapng" file to answer the questions. View packet number 38. Which markup language is used under the HTTP protocol?
> 

eXtensible Markup Language

<img width="468" height="272" alt="image 3" src="https://github.com/user-attachments/assets/8e7158fb-9203-4a27-98e9-1b5f890ccbc7" />


> What is the arrival date of the packet? 05/13/2004
> 

<img width="468" height="143" alt="image 4" src="https://github.com/user-attachments/assets/333cb6da-f98d-4314-b941-86e3f8e77184" />


> What is the TTL value? 47
> 

<img width="467" height="276" alt="image 5" src="https://github.com/user-attachments/assets/e0d0e346-4b75-4457-b1c7-3a01ea1c6469" />


What is the TCP payload size? 424

<img width="482" height="177" alt="image 6" src="https://github.com/user-attachments/assets/0e971a06-01bf-4d4b-be58-6572dc8a3b60" />


> What is the e-tag value?
> 

9a01a-4696-7e354b00 (An ETag (entity tag) is an HTTP response header used to uniquely identify a specific version of a resource. )

<img width="472" height="281" alt="image 7" src="https://github.com/user-attachments/assets/857d0e0c-67f5-4a2a-8d1e-529caac1fe54" />


### Task 4 - Packet Navigation

**Packet Numbers:** Assign unique IDs to packets

![Wireshark - packet numbers](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116217726.svg)

**Go to Packet:** Navigate directly to specific packets

![Wireshark - go to packet](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433008.gif)

**Find Packets:** Locate packets using search criteria. **Edit --> Find Packet**

![Wireshark - find packets](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433011.gif)

**Mark Packets:** Flag packets for further analysis. **"Edit"** or the **"right-click"** menu to mark

![Wireshark - mark packets](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433047.gif)

**Packet Comments:** Annotate packets with investigation notes

![Wireshark - packet comments](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1763530577252.gif)

**Export Packets:** Export selected packets for analysis

![Wireshark - export packets](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433024.gif)

**Export Objects (Files):** Extract transferred files from network traffic

![Wireshark - export objects](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433258.gif)

**Time Display Format:** Display timestamps in different formats. **View --> Time Display Format**

![Wireshark - Edit Time Display Format](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1761116433016.gif)


**Expert Info:** Identify protocol errors and anomalies

| **Severity** | **Colour** | **Info** |
| --- | --- | --- |
| **Chat** | **Blue** | Information on usual workflow. |
| **Note** | **Cyan** | Notable events like application error codes. |
| **Warn** | **Yellow** | Warnings like unusual error codes or problem statements. |
| **Error** | **Red** | Problems like malformed packets |

| **Group** | **Info** | **Group** | **Info** |
| --- | --- | --- | --- |
| **Checksum** | Checksum errors | **Deprecated** | Deprecated protocol usage |
| **Comment** | Packet comment detection | **Malformed** | Malformed packet detection |

You can use the **"lower left bottom section"** in the status bar or **"Analyse --> Expert Information"** menu to view all available information entries via a dialogue box. It will show the packet number, summary, group protocol and total occurrence.


**Answer the questions below**

> Use the "Exercise.pcapng" file to answer the questions. Search the "r4w" string in packet details. What is the name of artist 1?
> 

r4w8173

<img width="828" height="488" alt="image 8" src="https://github.com/user-attachments/assets/8f1dc18c-32a8-4e3c-8669-0168770ad072" />


> Go to packet 12 and read the packet comments. What is the answer?
> 

911cd574a42865a956ccde2d04495ebf

<img width="647" height="167" alt="image 9" src="https://github.com/user-attachments/assets/38dbf5b3-5e55-4df6-883e-9e5781bf61d5" />


Go to packet 39765, right-click it, select *Export Packet Bytes*, and save the file in JPEG Interchange Format (JFIF). 

> There is a ".txt" file inside the capture file. Find the file and read it; what is the alien's name?
> 

PACKETMASTER (Go to the *File* menu, select *Export Objects*, choose *TXT*, and save the file to the Desktop.)

> Look at the expert info section. What is the number of warnings? 1636
> 

<img width="732" height="831" alt="image 10" src="https://github.com/user-attachments/assets/2c79e213-d2e6-4d9d-9253-6c8c3d5412ff" />


### Task 5 - Packet Filtering

**Packet Filtering:** Filter traffic to reduce noise

**Apply as Filter:** Use queries or right-click filters. **Analyse --> Apply as Filter**

![Wireshark - apply as filter](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124912.gif)

**Conversation Filter:** Show related conversation packets. **Analyse --> Conversation Filter**

![Wireshark - conversation filter](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124660.gif)

**Colourise Conversation:** Highlight conversation without filtering. **View --> Colourise Conversation --> Reset Colourisation**

![Wireshark - colourise conversation](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124692.gif)

**Prepare as Filter:** Build filters before applying

![Wireshark - prepare as filter](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124871.gif)

**Apply as Column:** Display selected fields as columns. **Analyse --> Apply as Column**

![Wireshark - apply as column](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124914.gif)

**Follow Stream:** Reconstruct application-layer communication. **Analyse --> Follow TCP/UDP/HTTP Stream** 

![Wireshark - follow stream](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124617.gif)

**Simple Display Filter Queries:** Quickly filter packet captures. 

![Display Filter](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124666.png)

**Filter By Protocol Name or Port:** Filter traffic by protocol or port. There are two basic ways to filter based on a specific protocol: by protocol name and by protocol port number.

To filter by **protocol name**, simply type in the protocol name and hit enter or click on the arrow button at the right hand side of the display filter bar. The GIF below shows an example of how to filter for http traffic. You can similarly filter for other protocols using keywords like `arp`, `dhcp`, `ftp`, `smtp`, `pop`, `imap`, and more.

![Display Filter: Protocol Name](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404126755.gif)

To filter by **protocol port number**, you can use the structure "tcp.port == <port number>" or "udp.port == <port number>". For example, if you want to see only http packets, you would use the filter "tcp.port == 80" and then hit enter. 

![Display Filter: Port Number](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404126766.gif)

**Filter By IP:** Filter traffic by IP address. 

![Display Filter: IP](https://cdn-images.tryhackme.com/user-uploads/66c44fd9733427ea1181ad58/room-content/66c44fd9733427ea1181ad58-1768404124724.gif)

**Answer the questions below**

> Use the "Exercise.pcapng" file to answer the questions. Go to packet number 4. Right-click on the "Hypertext Transfer Protocol" and apply it as a filter. Now, look at the filter pane. What is the filter query? http
> 

<img width="727" height="490" alt="image 11" src="https://github.com/user-attachments/assets/e7fcaa58-2b69-49c2-b019-69b3837be603" />


> What is the number of displayed packets? 1089
> 

<img width="640" height="721" alt="image 12" src="https://github.com/user-attachments/assets/40c00689-ec55-4b53-96d3-0f8375bada98" />




> Go to packet number 33790, follow the HTTP stream, and look carefully at the responses.
Looking at the web server's response, what is the total number of artists? 3
> 

<img width="861" height="712" alt="image 13" src="https://github.com/user-attachments/assets/2b0d92f6-3192-4d32-869a-dd0886e51d39" />


> What is the name of the second artist? Blad3
> 

<img width="922" height="278" alt="image 14" src="https://github.com/user-attachments/assets/830140ba-088e-4822-88c9-e8d5392a78f7" />
