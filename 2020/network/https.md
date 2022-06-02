---
layout: default
title: HTTPS
parent: 2020
nav_order: 12
---

# HTTPS
{: .no_toc }
Presented on 23th May 2020 by [Taeim](https://github.com/kwontaeim)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


##  What is HTTP?

- `HTTP` stands for Hypertext Transfer Protocol, and it is a protocol – or a prescribed order and syntax for presenting information – used for transferring data over a network. Most information that is sent over the Internet, including website content and API calls, uses the HTTP protocol. There are two main kinds of HTTP messages: requests and responses.

##  HTTP vs. HTTPS: What are the differences?

![image](https://user-images.githubusercontent.com/21251967/171753549-32ea94c6-f729-4170-946e-bacd3e98a831.png)

- `HTTPS` is HTTP with encryption. The only difference between the two protocols is that `HTTPS` uses TLS (SSL) to encrypt normal HTTP requests and responses.
- As a result, HTTPS is far more secure than HTTP. A website that uses HTTP has http:// in its URL, while a website that uses HTTPS has https://.

## HTTPS and SSL

- HTTPS consists of communication over Hypertext Transfer Protocol (HTTP) within a connection encrypted by Transport Layer Security, or its predecessor, Secure Sockets Layer.

## SSL and TLS

- `SSL` stands for Secure Sockets Layer, and it refers to a protocol for encrypting and securing communications that take place on the Internet. Although SSL was replaced by an updated protocol called `TLS` (Transport Layer Security) some time ago, "SSL" is still a commonly used term for this technology.
- The main use case for SSL/TLS is securing communications between a client and a server, but it can also secure email, VoIP, and other communications over unsecured networks.

## What is an SSL certificate?

![image](https://user-images.githubusercontent.com/21251967/171753563-59b4cdae-f7ec-4024-b950-9cacd3017116.png)

- For an SSL certificate to be valid, domains need to obtain it from `a certificate authority (CA)`. A CA is an outside organization, a trusted third party, that generates and gives out SSL certificates. The CA will also digitally sign the certificate with their own private key, allowing client devices to verify it. Most, but not all, CAs will charge a fee for issuing an SSL certificate.
- Once the certificate is issued, it needs to be installed and activated on the website's origin server. Web hosting services can usually handle this for website operators. Once it's activated on the origin server, the website will be able to load over HTTPS and all traffic to and from the website will be encrypted and secure.

## Why should websites use HTTPS(SSL)?

1. An SSL certificate encrypts sensitive data
2. SSL ensures the information goes where it is intended
3. SSL guards against scams
4. An SSL certificate promotes customer confidence and trust
5. An SSL certificate improves SEO

## Behind the Scenes of SSL Cryptography
Asymmetric and symmetric keys work together to create an SSL-encrypted connection.

<img width="450" alt="image" src="https://user-images.githubusercontent.com/21251967/171753603-479faa72-1ba3-445d-b719-53aa9afa6dc2.png">

- Symmetric encryption (or pre-shared key encryption) uses a single key to both encrypt and decrypt data. Both the sender and the receiver need the same key to communicate.

<img width="450" alt="image" src="https://user-images.githubusercontent.com/21251967/171753631-b4ded365-9200-4735-b5ad-88b9f3068643.png">

- Asymmetric encryption (or public-key cryptography) uses a separate key for encryption and decryption. Anyone can use the encryption key (public key) to encrypt a message. However, decryption keys (private keys) are secret. This way only the intended receiver can decrypt the message. The most common asymmetric encryption algorithm is RSA.

<img width="317" alt="image" src="https://user-images.githubusercontent.com/21251967/171753663-5283c1ac-f163-4a9b-b3b3-a7998bc9f3b4.png">

1. Server sends a copy of its asymmetric public key.
2. Browser creates a symmetric session key and encrypts it with the server's asymmetric public key. Then sends it to the server.
3. Server decrypts the encrypted session key using its asymmetric private key to get the symmetric session key.
4. Server and Browser now encrypt and decrypt all transmitted data with the symmetric session key. This allows for a secure channel because only the browser and the server know the symmetric session key, and the session key is only used for that session.

## What is a handshake?

- TLS handshakes are a series of datagrams, or messages, exchanged by a client and a server. A TLS handshake involves multiple steps, as the client and server exchange the information necessary for completing the handshake and making further conversation possible.
- The exact steps within a TLS handshake will vary depending upon the kind of key exchange algorithm used and the cipher suites supported by both sides. The RSA key exchange algorithm is used most often.


![image](https://user-images.githubusercontent.com/21251967/171753685-d082fd00-75f4-4c91-8b2d-56a36ccb40ed.png)

1. The 'client hello' message: The client initiates the handshake by sending a "hello" message to the server. The message will include which TLS version the client supports, the cipher suites supported, and a string of random bytes known as the "client random."
2. The 'server hello' message: In reply to the client hello message, the server sends a message containing the server's SSL certificate, the server's chosen cipher suite, and the "server random," another random string of bytes that's generated by the server.
3. Authentication: The client verifies the server's SSL certificate with the certificate authority that issued it. This confirms that the server is who it says it is, and that the client is interacting with the actual owner of the domain.
4. The premaster secret: The client sends one more random string of bytes, the "premaster secret." The premaster secret is encrypted with the public key and can only be decrypted with the private key by the server. (The client gets the public key from the server's SSL certificate.)
5. Private key used: The server decrypts the premaster secret.
6. Session keys created: Both client and server generate session keys from the client random, the server random, and the premaster secret. They should arrive at the same results.
7. Client is ready: The client sends a "finished" message that is encrypted with a session key.
8. Server is ready: The server sends a "finished" message encrypted with a session key.
9. Secure symmetric encryption achieved: The handshake is completed, and communication continues using the session keys.

## How does HTTPS works?

![image](https://user-images.githubusercontent.com/21251967/171754045-293444db-9785-4ea8-b035-33171d7c4997.png)

![image](https://user-images.githubusercontent.com/21251967/171754052-8c7216ad-9ef2-4527-9c1b-bc8bde6013be.png)

Prerequisites
- You need to trust that public key cryptography & signature works:
  - Any message encrypted with Bob’s public key can only be decrypted with Bob’s private key.
  - Anyone with access to Alice’s public key can verify that a message (signature) could only have been created by someone with access to Alice’s private key.




