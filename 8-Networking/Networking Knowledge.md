# Networking Knowledge

## 1. What are Network Protocols

Resource: https://www.solarwinds.com/resources/it-glossary/network-protocols

### What are Network Protocols?

Network protocols are a set of rules outlining how connected devices communicate across a network to exchange information easily and safely.


### Types of Network Protocols

#### 1. Network Communication Protocols:

These Protocols determine the rules and formats to transfer data across networks.

Communication protocols govern various aspects of analog and digital communication, such as:

- Syntax
- Authentication
- Semantics
- Error Detection

##### Key Protocols include:

- Hyper-Text Transfer Protocol (HTTP): Protocol which allows communication between a server and browser.

    ![HTTP-Diagram](image.png)

- Transmission Control Protocol (TCP): Connection Oriented Protocol that helps in sequential transmission of data packets to ensure data reaches the destination on time and without duplication.

- Internet Protocol (IP): Facilitates routing the data packets across networks. IP contains addressing and control information to deliver packets across a network. It works along with TCP. While it ensures delivering the packets to the right address, TCP aligns them in the right order.

- User Datagram Protocol (UDP): UDP is a connectionless protocol that doesn't ensure a connection between the application and server before transmitting a message. Usecases: Broadcasts and multicast connections.

- File Transfer Protocol (FTP): Allows file sharing between servers by establishing two TCP connections, one for data transfer and the other for control. The data transfer connection transfers the files while the control connection transfers control information such as passwords to ensure data retrieval in case of data loss.

#### 2. Network Security Protocols:

These protocols ensure safe data transmission over the network connections. These define the procedures to secure data from any unauthorised access. These protocols leverage encryption and cryptography to safeguard.

##### Most widely used network security protocols:

- Secure File Transfer Protocol (SFTP): Secure File transfer across a network by using public-key encryption and authenticating the client and server.

- Hyper-Text Transfer Protocol Secure (HTTPS): Ensures the security of data transmitted between the browser and server through data encryption.

- Secure Socket Layer (SSL): Secures internet connections and safeguard sensitive data using encryption. SSL protocol enables both server-client communication and server-server communication.

#### 3. Network Management Protocols:

Network managers require standard policies and procedures to manage and monitor the network for maintaining smooth communication. Network management protocols ensure quick troubleshooting and optimal performance across the network.

##### Essential Network Protocols Management:

- Simple Network Management Protocol (SNMP): Helps administrators manage network devices by monitoring endpoint information to proactively track network performance and pinpoint network glitches for quick troubleshooting.

- Internet Control Message Protocol (ICMP): Helps diagnose network connectivity issues. Network devices employ ICMP for sending error messages, highlighting congestion and timeouts, and transmitting other operational information to assist in network troubleshooting.

