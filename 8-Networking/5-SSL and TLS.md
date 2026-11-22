# SSL and TLS Basics

Secure Sockets Layer (SSL) and Transport Layer Security (TLS) are cryptographic protocols that provide secure communication over a network. They work by encrypting data exchanged between a client and a server, ensuring confidentiality and integrity. SSL was the predecessor to TLS, and while SSL is now considered outdated and insecure, the term "SSL" is often still used interchangeably with "TLS." The protocols establish a secure connection using digital certificates for authentication and encryption algorithms for data protection.

**Resource:** [What's the Difference Between SSL and TLS?](https://aws.amazon.com/compare/the-difference-between-ssl-and-tls/)

**YouTube:** [TLS vs SSL - What's the Difference?](https://youtu.be/J7fI_jH7L84?si=uFvhZGX4JfcUUAEm)

---

## What's the difference between SSL and TLS?

Secure Sockets Layer (SSL) is a communication protocol, or set of rules, that creates a secure connection between two devices or applications on a network. SSL is technology your applications or browsers may have used to create a secure, encrypted communication channel over any network.

However, SSL is an older technology that contains some security flaws.

Transport Layer Security (TLS) is the upgraded version of SSL that fixes existing SSL vulnerabilities. TLS authenticates more efficiently and continues to support encrypted communication channels.

---

## What are the similarities between SSL and TLS?

### Terminology

TLS is the direct successor to SSL, and all versions of SSL are now deprecated. However, it's common to find the term SSL describing a TLS connection. In most cases, the terms SSL and SSL/TLS both refer to the TLS protocol and TLS certificates.

### Purpose

TLS is a secure communication protocol that enables encryption and authentication, and this was true for SSL before it was deprecated. TLS and SSL both use digital certificates that facilitate the handshake process and establish encrypted communications between a browser and a web server.

### Usage in HTTPS

HTTP is a protocol or set of communication rules for client-server communication over any network. HTTPS is the practice of establishing a secure SSL/TLS protocol on an insecure HTTP connection.

Before it connects with a website, your browser uses TLS to check the website's TLS or SSL certificate. TLS and SSL certificates show that a server adheres to the current security standards. You can find evidence about the certificate within the browser address bar. An authentic and encrypted connection displays https:// instead of http://. The additional s stands for secure.

---

## Key differences: SSL vs. TLS

### SSL/TLS Handshakes

A handshake is a process in which a browser authenticates a server's SSL or TLS certificate. This process authenticates both parties, then exchanges cryptographic keys.

An SSL handshake was an explicit connection, while a TLS handshake is an implicit one. The SSL handshake process had more steps than the TLS process. By removing additional steps and reducing the total number of cipher suites, TLS has sped up the process.

### Alert Messages

Alert messages are how SSL and TLS protocols communicate errors and warnings. In SSL, there are only two alert message types: warning and fatal. A warning alert indicates that an error has occurred, but the connection can continue. A fatal alert indicates that the connection must be terminated immediately. Additionally, SSL alert messages are unencrypted.

TLS has an additional alert message type called close notify. The close notify alert signals the end of the session. TLS alerts are also encrypted for additional security.

### Message Authentication

Both SSL and TLS use message authentication codes (MACs), a cryptographic technique for verifying the authenticity and integrity of messages. By using a secret key, the record protocol generates the MAC as a fixed-length code and attaches it to the original message.

The SSL protocol uses the MD5 algorithm—which is now outdated—for MAC generation. TLS uses Hash-Based Message Authentication Code (HMAC) for more complex cryptography and security.

### Cipher Suites

A cipher suite is a collection of algorithms that create keys to encrypt information between a browser and a server. Typically, a cipher suite includes a key exchange algorithm, a validation algorithm, a bulk encryption algorithm, and a MAC algorithm. Several algorithms in TLS were upgraded from SSL due to security concerns.

---

## Summary of differences: SSL vs. TLS

| | SSL | TLS |
|---|---|---|
| **Stands For** | SSL means Secure Sockets Layer. | TLS means Transport Layer Security. |
| **Version History** | SSL is now replaced with TLS. SSL moved through versions 1.0, 2.0, and 3.0. | TLS is the upgraded version of SSL. TLS has moved through versions 1.0, 1.1, 1.2, and 1.3. |
| **Activity** | Every SSL version is now deprecated. | TLS versions 1.2 and 1.3 are actively used. |
| **Alert Messages** | SSL has only two types of alert messages. Alert messages are unencrypted. | TLS alert messages are encrypted and more diverse. |
| **Message Authentication** | SSL uses MACs. | TLS uses HMACs. |
| **Cipher Suites** | SSL supports older algorithms with known security vulnerabilities. | TLS uses advanced encryption algorithms. |
| **Handshake** | An SSL handshake is complex and slow. | A TLS handshake has fewer steps and a faster connection. |