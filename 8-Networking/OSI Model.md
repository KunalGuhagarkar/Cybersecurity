# OSI Model

Resource: https://aws.amazon.com/what-is/osi-model/

## What is OSI Model?

The Open Systems Interconnection (OSI) model is a conceptual framework that divides network communications functions into seven layers. Sending data over a network is complex because various hardware and software technologies must work cohesively across geographical and political boundaries. The OSI data model provides a universal language for computer networking, so diverse technologies can communicate using standard protocols or rules of communication. Every technology in a specific layer must provide certain capabilities and perform specific functions to be useful in networking. Technologies in the higher layers benefit from abstraction as they can use lower-level technologies without having to worry about underlying implementation details.

## Why is OSI Model Important?

The layers of the Open Systems Interconnection (OSI) model encapsulate every type of network communication across both software and hardware components. The model was designed to allow two standalone systems to communicate via standardised interfaces or protocols based on the current layer of operation.

#### Benefits of OSI Model

1. Shared Understanding of complex systems

    Engineers can use the OSI model to organize and model complex networked system architectures. They can separate the operating layer of each system component according to its main functionality. The ability to decompose a system into smaller, manageable parts via abstraction makes it easier for people to conceptualize it as a whole.

2. Faster Research and Developement

    With the OSI reference model, engineers can understand their work better. They know which technological layer (or layers) they’re developing for when they create new, networked systems that need to communicate with each other. Engineers can develop networked systems and take advantage of a series of repeatable processes and protocols. 

3. Flexible standardization

    The OSI model does not specify the protocols to use between levels, but rather the tasks that protocols perform. It standardizes network communication development so people can rapidly understand, build, and decompose highly complex systems—all  without prior knowledge of the system. It also abstracts details, so engineers don’t require the understanding of every aspect of the model. In modern applications, the lower levels of networking and protocols are abstracted away to simplify system design and development. The following image shows how the OSI model is used in modern application development.

![OSI Model Image](../assets/osi.png)

## Seven Layers of OSI Model

1. Physical Layer

    The physical layer refers to the physical communication medium and the technologies to transmit data across that medium. At its core, data communication is the transfer of digital and electronic signals through various physical channels like fiber-optic cables, copper cabling, and air. The physical layer includes standards for technologies and metrics closely related with the channels, such as Bluetooth, NFC, and data transmission speeds.

2. Data Link Layer

    The data link layer refers to the technologies used to connect two machines across a network where the physical layer already exists. It manages data frames, which are digital signals encapsulated into data packets. Flow control and error control of data are often key focuses of the data link layer. Ethernet is an example of a standard at this level. The data link layer is often split into two sub-layers: the Media Access Control (MAC) layer and Logical Link Control (LLC) layer. 

3. Network Layer

    The network layer is concerned with concepts such as routing, forwarding, and addressing across a dispersed network or multiple connected networks of nodes or machines. The network layer may also manage flow control. Across the internet, the Internet Protocol v4 (IPv4) and IPv6 are used as the main network layer protocols.

4. Transport layer

    The primary focus of the transport layer is to ensure that data packets arrive in the right order, without losses or errors, or can be seamlessly recovered if required. Flow control, along with error control, is often a focus at the transport layer. At this layer, commonly used protocols include the Transmission Control Protocol (TCP), a near-lossless connection-based protocol, and the User Datagram Protocol (UDP), a lossy connectionless protocol. TCP is commonly used where all data must be intact (e.g. file share), whereas UDP is used when retaining all packets is less critical (e.g. video streaming).

5. Session layer

    The session layer is responsible for network coordination between two separate applications in a session. A session manages the beginning and ending of a one-to-one application connection and synchronization conflicts. Network File System (NFS) and Server Message Block (SMB) are commonly used protocols at the session layer.

6. Presentation layer

    The presentation layer is primarily concerned with the syntax of the data itself for applications to send and consume. For example, Hypertext Markup Language (HTML), JavaScipt Object Notation (JSON), and Comma Separated Values (CSV) are all modeling languages to describe the structure of data at the presentation layer. 

7. Application layer

    The application layer is concerned with the specific type of application itself and its standardized communication methods. For example, browsers can communicate using HyperText Transfer Protocol Secure (HTTPS), and HTTP and email clients can communicate using POP3 (Post Office Protocol version 3) and SMTP (Simple Mail Transfer Protocol).

Not all systems that use the OSI model implement every layer.

