# Windows_User_Simulator

**Program Design Purpose**: We want to create a distributed and no-centralized single/multiple users’ activities emulator system to simulate and monitor a mid size cluster of users’ normal network traffic actions and the local activities events. The system can be applied to support below scenario : 

- Auto repeat/replay specified numbers of users (blue team) activities (benign-traffic) or or attack-action (red team) in cyber exercise event.
- Generate required network traffic flow with different network protocols for network security research project. 
- Be used to build the repeatable users’ test environment for AI/ML trained model’s testing and verification.
- Provide library API for customer to build customized complex “Human type” action. 

[TOC]

------

### Introduction

The Cluster Users Emulator is a multiple users’ action emulation system running in a network/compute cluster system which can satisfy the customers’ requirement about:

- Network-traffic / node activities / group-users interactive action generation. 

- Robotic process / tasks automation. 

- System tasks’ process monitoring and control.

  

#### System structure 

The user Emulator system can be deployed on single compute node, real network system, VMs based SDN (software defined network). The product contents three parts, the “User actions repository”, the “User action emulator/scheduler” and the “scheduler monitor hub”. (The 3 parts relationship is shown in the below system deployment structure diagram)

![](doc/img/RM_diagram_system.png)

- **User Actions Repository** : Provide the library APIs repository to simulate simple user’s normal activities/events under hardware, network, OS and App level. (Such as starting the online meeting, send/receive email, upload/download files, edit MS-Office doc, On/Off Windows FW, watch online/offline video…)
- **User Action Emulator**: A RPA type scheduler to invoke the lib from action repository to build more complex “Human type” activities and run the tasks based on the users’ timeline playbook configuration.
- **Scheduler Monitor Hub**: A no-centralized monitor website host which provides plug and play tasks state view function for the customer to monitor and control all/parts of their schedulers in a computers/servers cluster. 

The modules relationship diagram is shown below: 

![](doc/img/RM_diagram_module.png)

`Version: 0.1`



------

### System Design

We want to create an intelligent "actor” program which can simulate a normal MS-Windows user’s daily action ( different kinds of network access, system level operation and different app level operation) to generate user’s regular or random event based on the customer’s requirement. So, it can:

- Be used to repeat/replay specified large numbers of users (blue team) activities in cyber exercise event.
- Generate required network traffic flow for network security research project. 
- Be used as repeatable user’s test environment for AI/ML trained module’s verification.

##### System Work Flow Diagram

The system will work under the below work diagram 

![](doc/img/RM_Diagram_workflow.png)



#### User Actions Repository

User Actions Repository is library APIs repository to simulate simple user’s normal activities/events under hardware, network, OS and App level. (Such as starting the online meeting, send/receive email, upload/download files, edit MS-Office doc, On/Off Windows FW, watch online/offline video…)

Currently we provide 5 main repositories with 18 kinds of basic user action functions and 28 kinds of pre-built complex user’s actors components. The 5 main feature repositories covers: 

- Network traffic action generators. 
- Application operation action generators. 
- User’s human activities action generators.
- System control action generators.
- Other action generators.

The Introduction link of User Action Repository [click [here](ReadMe_User_Actions_Repository.md) ] 



#### **User Action Emulator**

User Actor Emulator is a RPA type scheduler to invoke the lib from action repository to build more complex “Human type” activities and run the tasks based on the users’ timeline playbook configuration.





------











##### Actors Module: 

Actor module are the basic components to simulate one kind of normal user's  action such as file editing, surf the internet, access multi-media  and so on. 



Network traffic action generator

| Actor module name | function provided        | traffic/protocol type                                        |
| ----------------- | ------------------------ | ------------------------------------------------------------ |
| pingActor         | ping                     | Internet Control Message Protocol (ICMP)                     |
| webActor          | http(s)                  | Fetch a website, send http(s) request.                       |
| webDownloader     | http(s)                  | Download website components: https web cert, css, html, js, images, downloadable link. |
|                   | Page screen shot         | whole webpage to image.                                      |
| transferActor     | ftp(s)                   | Upload and download a file                                   |
|                   | sftp                     | Transfer files via sftp                                      |
|                   | nfs/smb                  | Copy a file or directory to or from a nfs or smb share.      |
| sshConnector      | ssh/scp                  | ssh connection or scp file transfer                          |
| sshForwarder      | ssh                      | forward port thought open port.                              |
| udpCom            | udp                      | Any kinds of UDP message communication or file transfer.     |
| tcpCom            | tcp                      | Any kinds of TCP message communication or file transfer.     |
| emailActor        | SMTP/IMAP4,POP,IMAP_SSL  | Email receive and send (Gmail, Hotmail, Mailu)               |
| camEchoClient     | RTSP                     | Real-Time Streaming(IP camera)                               |
|                   | HLS                      | HTTP Live Streaming such as video web site.                  |
| pcapReplayActor   | replaying packet in pcap | parsing pcap file and send the packet to the specific destination. |
| telnetActor       | telnet                   | remote login/Open a telnet connection and issue commands     |



System App Action genreator

| Actor module name | function provided                                          |      |
| ----------------- | ---------------------------------------------------------- | ---- |
| zoomActor         | Join zoom meeting                                          |      |
| musicActor        | Search audio files and play one by one                     |      |
| videoActor        | Search video/picture files and play one by one             |      |
| msFileActor(Word) | Create/edit MS-word(*.docx) file                           |      |
| msFileActor(PPT)  | Create/edit MS-powerpoint(*.pptx) file                     |      |
| msTeamsActor      | Join teams meeting, send a message.                        |      |
| fileActor         | file search, copy, move, delete, execute, rename, compress |      |
| pdfReader         | Check pdf file and parse the info.                         |      |
|                   |                                                            |      |



User action generator

| Actor module name      | function provided                                         |      |
| ---------------------- | --------------------------------------------------------- | ---- |
| mouse_keyboard Actor   | Replay recorded user mouse + keyboard action              |      |
|                        | Simulate user's mouse+keyboard action based on pre-config |      |
| TelegramActor          | Send message to phone by telegram                         |      |
| gameActor(dino/sudoku) | Play google dino game. play sudoku game.                  |      |
|                        |                                                           |      |



Other action generator

| Actor module name | function provided                                            |      |
| ----------------- | ------------------------------------------------------------ | ---- |
| SerialConnector   | Send and read message to/from COM port.                      |      |
| camEchoServer     | Computer built in camera/usb camera video read record. Start a HLS server. |      |
| ScreanRecorder    | snapshot the screen under frequency.                         |      |
| DBHandler         | DataBase (SQLite3, influxDB, arangodb) access action simulator. |      |
|                   |                                                              |      |



System control action generator 

| Actor module name | function provided                                            |      |
| ----------------- | ------------------------------------------------------------ | ---- |
| CmdActor          | Run window commend under cmd or powershell.                  |      |
| SettingActor      | Change some OS setting (on/off firewall, change display bg, sort desktop, reboot) |      |
|                   |                                                              |      |





Example Timeline: 

Bob is a system technical support officer. He login his Windows server at 8:50 am

| Time  | Action                                                       | action time (testCase setting) | current progress                |
| ----- | ------------------------------------------------------------ | ------------------------------ | ------------------------------- |
| 9:01  | Ping a servers list to check the server's connection. (open console ping the dest one by one, sequential ) | 10 min                         | done                            |
| 9:10  | Bob runs the ping client program ping 100 servers need to check and record down the result.(run pingClient.py, multi-thread parallel ping) | 10 min                         | done                            |
| 9:13  | During watching the ping result refresh, bob run server network checking cmd in terminal one by one (ipconfig, Tracert www.google.com.sg , Pathping www.google.com.sg, Getmac, Nslookup www.google.com.sg) | 5 min                          | done                            |
| 9:20  | Bob ssh to 12 Ubuntu servers and run some cmd  record done the result.(run sshConnector.py do server one by one sequential) | 12min                          | done                            |
| 9:32  | Bob use "Tree" cmd to search some files.                     | 2 min                          | done                            |
| 9:35  | Bob start a zoom meeting with his colleague to discuss for half hour | 30 min                         | done                            |
| 10:05 | Write down and draw some diagram based on the meeting.       | 8 min                          | X: need the screen to be 1080P  |
| 10:15 | Bob search some question in google.(run WebScreenShoter.py do web access and random link click action one by one sequential) | 15 min                         | Done                            |
| 10:30 | Bob find what he want, and download the related web's cert, image, js, css,  file.(run WebDownloader.py do the download) | 5 min                          | Done                            |
| 10:35 | Bob send this friend some message and image(video) by telegram .(run telegramClient.py do the message sending) | 5 min                          | x : use YC's telegram password, |
| 10:40 | Bob watch YouTube video for 30 min                           | 30min                          | Done                            |
| 10:48 | Bob read checked the email for 2 min                         | 2min                           | x : use YC's telegram password, |
| 10:50 | Bob Open a word document and write a report.                 | 25 min                         | Done                            |
| 11:25 | Bob made one presentation slides.                            | 13 min                         | Done                            |
| 11:35 | Bob feel tired and play the google dino game for a short while. | 10 min                         | Done                            |
| 12:00 | Bob went for lunch                                           | 60min                          |                                 |
| 13:10 | Bob ping 100 random address  in the subnet 192.168.56.0/24 to check the connection. | 30 min                         | Done                            |
| 13:45 | Bob ssh to 10 random host to run the cmd in the subnet 192.168.57.0/24 | 20 min                         | Done                            |
| 14:10 | Bob turn off his private firewall for 30min                  | 1min                           | Done                            |
| 14:30 | Bob turn search the web and download pic, js, cert file      | 20min                          | Done                            |
| 14:50 | Bob send 2000+ UDP message to 100 different ip 192.168.57.0/24 each IP send 20 UPD message. | 20 min                         | Done                            |
| 15:15 | Bob edit the ppt and pause the test result in.               | 3 min                          | Done                            |
| 15:20 | Bob play game for 10 min                                     | 10 min                         | Done                            |
| 15:40 | Bob run server network checking cmd in terminal one by one (ipconfig, Tracert www.google.com.sg , Pathping www.google.com.sg, Getmac, Nslookup www.google.com.sg) | 5 min                          | Done                            |
| 15:55 | Bob start to pause more result he collected just now in this report | 2 min                          | Done                            |
| 16:00 | Bob watch local video and listen the music for 30 min        | 30 min                         | Done                            |
| 16:35 | Bob check and open all pictures in the picture window        | 15min                          | Done                            |
| 17:00 | Bob send 2000+ UDP message to 100 different ip 192.168.58.0/24 each IP send 20 UPD message. | 20 min                         | Done                            |
| 17:25 | Bob edit the ppt and pause the test result in.               | 5min                           | Done                            |
| 17:35 | Bob edit his daily work report word file                     | 10 min                         | Done                            |
| 17:50 | Bob logout his account.                                      |                                |                                 |



remove access the windows vm:

```
ssh -L 127.0.0.1:3389:192.168.57.10:3389 -p 6022 -J rp_fyp_ctf@gateway.ncl.sg ls23@172.18.178.10
```

