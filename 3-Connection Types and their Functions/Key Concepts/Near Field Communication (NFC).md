
**Near Field Communication (NFC)** is a short-range wireless technology that allows devices to communicate and exchange data over very short distances, typically up to 4 inches (10 cm). NFC is commonly used for applications such as contactless payments, electronic ticketing, and data transfer between devices. It operates at a frequency of 13.56 MHz and supports various modes, including peer-to-peer communication, card emulation, and reader/writer modes. NFC enables quick and secure interactions with minimal setup, making it convenient for mobile payments, access control, and sharing information.


Resource: https://www.spiceworks.com/networking/what-is-near-field-communication/

YouTube: https://youtu.be/eWPtt2hLnJk?si=hjC8vv-q1NYtI5wO

![[Pasted image 20261021103702.png]]

**_Near Field Communication is a wireless personal area network (PAN) technology that connects two compatible devices in very close proximity of each other, in order to enable slow but reliable data transfer. This article explains how NFC works, with examples._**

## What is NFC (Near Field Communication)?
**Near Field Communication, commonly abbreviated as NFC, is defined as a wireless personal area network (PAN) technology that connects two compatible devices in very close proximity to each other, in order to enable slow but reliable data transfer.**

![[Pasted image 20261021103835.png]]

The NFC standard enables mobile devices such as smartphones to share data with one another in a brisk and painless manner with just a single tap. In order for the technology to function, there must be two devices that are compatible with it — i.e., both a target device and an initiator device.

Additional application software is required for NFC-enabled devices, such as smartphones, in order for such devices to function as their manufacturers intended them to. Without this application software, smartphones cannot make payments or read smart NFC posters. NFC technology is used to facilitate contactless payments in Apple Pay and Samsung Pay for smartphone users, to wirelessly charge wearable fitness devices, and to provide key card access to offices and schools.

- **Active communication mode**: In this mode, both the target and initiator devices are active devices. That is, both of them have a power source, and they can alternately generate a field through which they can communicate. An active device deactivates its radio frequency (RF) field while waiting to receive data.
  
- **Passive communication mode**: The initiator device supplies a carrier field while the target device is responsible for modulating the field that is already present in this mode. The passive device lacks power and has to draw its power from the electromagnetic field of the initiator device.

### Advantages
Using NFC offers several key advantages. It is inexpensive, and its benefits outweigh the costs. It allows for faster and more automatic communication between devices. It is backward compatible with other RFID devices. Using NFC does not require expertise. Users with decent technological know-how can use it.

### Challenges
However, NFC also has a few constraints. It only operates within a very short range and is prone to security vulnerabilities such as eavesdropping, which may lead to the loss of information. NFC has a very low rate of transferring data, making it unsuitable and slow for transferring large files between peers.


## Modes of Operation
The communication method in each mode of operation of NFC is different. These differences affect the field of operation and how it is used. 

- **Peer-to-peer mode**: This mode is compliant with ISO/IEC 18092 standards. It supports communication and the transfer of information between two NFC-compatible devices. At any point, any device can act as the initiator or a target.
- **Reader/writer mode**: This mode is compatible with the standards established by ISO/IEC 14443 and FeliCa. It allows devices to read NFC tags, such as those that are integrated into smart posters.
- **Card emulation mode:** In this mode, data stored on cards such as smart cards are read by an NFC reader. In this mode, a device that is capable of NFC communication connects with an NFC reader in the same way as a smart card can. Users utilize smartphones to gain access to information, such as ticketing information.


## Understanding NFC tags
In order for near-field communication (NFC) to function properly, tags are necessary. This is especially true in the context of [Internet of Things (IoT)Opens a new window](https://spiceworks.com/tech/iot/articles/what-is-iot-device-management/ "Opens a new window") device use cases. These tags are passive devices that allow for communication with active devices. They are categorized based on their formats and capacity. The ISO 14443 Types A and B as well as the Sony FeliCa standard serve as the foundation for the NFC tag type formats. These formats are similar but differ in the way they communicate.

- **Type 1:** The standards of the ISO/IEC 14443A standard were used as the basis for this tag. It is a simple and cost-effective tag that is ideal for use in several NFC applications. This tag is read and read/write capable. It has no data collision protection and has a memory of 96 bytes that can be expanded to 2K bytes. It has a communication speed of 106 kbit/s. Examples of common applications of this tag are in mobile payments and connecting Bluetooth devices.
- **Type 2**: This tag is similar to the type 1 tag, albeit it is faster. It adheres to the standards outlined in the ISO/IEC 14443A document. This tag is read and read/write capable. It has anti-collision support and a memory of 96 bytes that can be extended to 2K bytes. It also has a communication speed of 106 kbit/s. Examples of common applications of this tag are in the processing of event and transit tickets.
- **Type 3:** Based on the JIS X 6319-4 standard, this tag is more prevalent in Japan.This tag is read and read/write capable. It is more expensive per tag and has a memory capacity of up to 1 M byte. It has anti-collision support and a communication speed of 212 kbit/s. Examples of common applications of this tag are in health care devices and membership cards.
- **Type 4**: This tag is also similar to the type 1 tag.It is based on the standard specifications ISO/IEC 14443A and ISO/IEC 14443B.This tag is read and read/write capable. It has anti-collision support and a maximum memory capacity size of 32k bytes. It also has a communication speed of 106 kbit/s.

