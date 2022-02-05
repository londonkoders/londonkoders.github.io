---
layout: default
title: OSI 7
parent: 2020
nav_order: 10
---

## Section 1 Application Layer Protocols
## Topic 1.1:  Application, Presentation, and Session

### Application Layer
![image](https://user-images.githubusercontent.com/21251967/152638314-9c4f25ad-7bed-46be-8570-b1ae37d398d3.png)
- The application layer is closest to the end user.
- Network applications enable users to send and receive data with ease.
- The application layer acts as interface between the applications and the underlying network.
- Application layer protocols help exchange data between programs running on the source and destination hosts.
- The TCP/IP application layer performs the functions of the upper three layers of the OSI model.
- Common application layer protocols include: HTTP, FTP, TFTP, DNS.

### Presentation and Session Layer
- The presentation layer has three primary functions:
  - Format data
  - Compress data
  - Encrypt data
- Common standards for video include QuickTime and Motion Picture Experts Group (MPEG).
- Common graphic image formats are:
  - Graphics Interchange Format (GIF)
  - Joint Photographic Experts Group (JPEG)
  - Portable Network Graphics (PNG) format
- The session layer creates and maintains dialogs between source and destination applications.
- The session layer handles the exchange of information to initiate dialogs, keep them active, and to restart sessions that are disrupted or idle for a long period of time.

### TCP/IP Application Layer Protocols
![image](https://user-images.githubusercontent.com/21251967/152638874-7def2383-4309-4ae0-8a40-2aef20b72026.png)
- TCP/IP application protocols specify the format and control information necessary for common Internet functions.
- Application layer protocols must be implemented in both the source and destination devices.
- Application layer protocols implemented on the source and destination host must be compatible to allow communication.

## Topic 1.2: How Application Protocols Interact with End-User Applications

### Client-Server Model
![image](https://user-images.githubusercontent.com/21251967/152638950-744bbf86-e411-4bf3-857b-ca449eeacb53.png)
- The device requesting the information is called a client.
- The device responding to the request is called a server.
- Client and server processes are considered to be in the application layer.
- The client initiates the exchange by requesting data from the server.
- The server responds by sending one or more streams of data to the client.
- Application layer protocols describe the format of the requests and responses between clients and servers.
- The contents of the data exchange will depend of the application in use.
- Email is an example of a  Client-Server interaction.

### Peer-to-Peer Networks
![image](https://user-images.githubusercontent.com/21251967/152639340-43e14a9c-de2b-48af-9230-2ea93f0f0b38.png)
- In the peer-to-peer (P2P) networking model, the data is accessed without the use of a dedicated server.
- Two or more computers can be connected to a P2P network to share resources.
- Every connected end device (a peer) can function as both a server and a client.
- The roles of client and server are set on a per request basis.

### Peer-to-Peer Applications
![image](https://user-images.githubusercontent.com/21251967/152639366-f679a549-d3d2-42f5-bfdb-48774654bdac.png)
- Some P2P applications use a hybrid system.
- In hybrid P2P, resource sharing is decentralized.
- Indexes that point to resource locations are stored in a centralized directory.
- In a hybrid system, each peer accesses an index server to get the location of a resource stored on another peer.

### Common P2P Applications
![image](https://user-images.githubusercontent.com/21251967/152639410-3a4072dc-4361-4fec-b8a2-657e67d082e9.png)
- Common P2P networks include: eDonkey, G2, BitTorrent, Bitcoin.
- Many P2P applications allow users to share pieces of many files with each other at the same time.
- A small torrent file contains information about the location of other users and tracker computers.
- Trackers are computers keeping track of the files hosted by users.
- This technology is called BitTorrent.
- There are many BitTorrent clients, including  BitTorrent, uTorrent, Frostwire, and qBittorrent.

## Section 2 Well-Known Application Layer Protocols and Services
## Topic 2.1: Web and Email Protocols

### Hypertext Transfer Protocol and Hypertext Markup Language
![image](https://user-images.githubusercontent.com/21251967/152639592-b6a52301-b392-4a86-b91c-8f87c55dead5.png)
- A URL allows a web browser to establish a connection to that web server.
- URLs and Uniform Resource Identifier (URIs) are the names most people associate with web addresses.
- The URL http://cisco.com/index.html has three basic parts:
  - http (the protocol or scheme)
  - www.google.com (the server name)
  - index.html (the specific filename requested)
- Using DNS, the server name portion of the URL is then translated to the associated IP address before the server can be contacted.
![image](https://user-images.githubusercontent.com/21251967/152639633-eb99fd72-3b25-4a77-b215-65f9f7f590a8.png)
- The browser sends a GET request to the server’s IP address and asks for the index.html file.
- The server sends the requested file to the client.
- The index.html was specified in the URL and contains the HTML code for this web page.
- The browser processes the HTML code and formats the page for the browser window based on the code in the file.
![image](https://user-images.githubusercontent.com/21251967/152639642-40a9dc03-954f-4b9a-9226-fb092a79e96c.png)

### HTTP and HTTPS
![image](https://user-images.githubusercontent.com/21251967/152639654-42ae914f-3e53-483f-9b72-749da35089b5.png)

- HTTP 
  - Is a request/response protocol.
  - Has three common message types: GET, POST, PUT.
  - Is not secure. Messages can be intercepted.
- HTTPS uses authentication and encryption to secure data.

### Email Protocols
![image](https://user-images.githubusercontent.com/21251967/152639712-c3f7f4cb-8c62-4626-a460-0afe70f0f456.png)
- Email is a store-and-forward method of sending, storing, and retrieving electronic messages.
- Email messages are stored in databases on mail servers.
- Email clients communicate with mail servers to send and receive email.
- Mail servers communicate with other mail servers to transport messages from one domain to another.
- Email clients do not communicate directly when sending email.
- Email relies on three separate protocols for operation: SMTP (sending),POP (retrieving), IMAP (retrieving).

## Topic 2.2: IP Addressing
### Domain Name Service
![image](https://user-images.githubusercontent.com/21251967/152639757-d2995b45-50f1-47d7-9381-1f909016ab4f.png)
![image](https://user-images.githubusercontent.com/21251967/152639762-f3455aaa-8e19-4bc2-9455-714c72ee4150.png)

- While IP addresses are crucial for network communication, they are not easy to memorize.
- Domain names are created to make server addresses more user-friendly.
- The DNS protocol allows for the dynamic translation of a domain name into the correct IP address.
- The DNS protocol communications using a single format called a message.
- Domain names such as http://www.google.com are user-friendly addresses associated with the IP address of a specific server.
- However, computers still need the actual numeric address before they can communicate.
