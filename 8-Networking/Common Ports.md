# Common Network Ports

**Source:** [14 common network ports you should know](https://opensource.com/article/18/10/common-network-ports) by Kedar Vijay Kulkarni, Opensource.com (Oct 4, 2018). Licensed [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

**YouTube:** [Common Network Ports - CompTIA A+ 220-1101 - 2.1](https://www.youtube.com/watch?v=dh8h-4u7Wak)

---

## What is a port?

- Physical ports on a computer let it communicate with peripheral devices such as a keyboard and mouse, and connect to internet devices via Ethernet cables.
- In computer networking, ports serve a similar purpose: a port is a **communication endpoint** when one computer connects to another.
- Different services on the same computer can also expose ports and communicate with one another through them.
- If a software application or service needs to communicate with others, it exposes a port.
- Ports are identified by positive 16-bit unsigned integers, from **0 to 65535**. Other services use the port number to communicate with the service or app.

## Port ranges

Port numbers are divided into three ranges:

- **Well-known ports** (also called *system ports*): 0 through 1023
- **Registered ports**
- **Dynamic or private ports**

The Internet Assigned Numbers Authority (IANA) has assigned port numbers to commonly used services like SSH, FTP, HTTP, and HTTPS.

## Example: SSH uses port 22

```bash
ssh username@example.com -v
```

`-v` stands for verbose, and the output includes a line like:

```text
debug1: Connecting to example.com [<IP Addr>] port 22
```

SSH connects using port 22 by default. Use the `-p` option to specify another port number.

## Common ports

| Port Number | Usage |
|-------------|-------|
| 20 | File Transfer Protocol (FTP) Data Transfer |
| 21 | File Transfer Protocol (FTP) Command Control |
| 22 | Secure Shell (SSH) |
| 23 | Telnet: remote login service, unencrypted text messages |
| 25 | Simple Mail Transfer Protocol (SMTP) E-mail Routing |
| 53 | Domain Name System (DNS) service |
| 80 | Hypertext Transfer Protocol (HTTP) used in World Wide Web |
| 110 | Post Office Protocol (POP3) used by e-mail clients to retrieve e-mail from a server |
| 119 | Network News Transfer Protocol (NNTP) |
| 123 | Network Time Protocol (NTP) |
| 143 | Internet Message Access Protocol (IMAP) Management of Digital Mail |
| 161 | Simple Network Management Protocol (SNMP) |
| 194 | Internet Relay Chat (IRC) |
| 443 | HTTP Secure (HTTPS): HTTP over TLS/SSL |

## Most frequently encountered

The author most commonly comes across ports **80, 443, 20, 21, 22, 23, 25, and 53**. Knowing these ports can help you work more efficiently.