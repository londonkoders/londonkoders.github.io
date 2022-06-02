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

- `HTTPS` is HTTP with encryption. The only difference between the two protocols is that `HTTPS` uses TLS (SSL) to encrypt normal HTTP requests and responses.
- As a result, HTTPS is far more secure than HTTP. A website that uses HTTP has http:// in its URL, while a website that uses HTTPS has https://.

## HTTPS and SSL

- HTTPS consists of communication over Hypertext Transfer Protocol (HTTP) within a connection encrypted by Transport Layer Security, or its predecessor, Secure Sockets Layer.

## SSL and TLS

- `SSL` stands for Secure Sockets Layer, and it refers to a protocol for encrypting and securing communications that take place on the Internet. Although SSL was replaced by an updated protocol called `TLS` (Transport Layer Security) some time ago, "SSL" is still a commonly used term for this technology.
- The main use case for SSL/TLS is securing communications between a client and a server, but it can also secure email, VoIP, and other communications over unsecured networks.

## What is an SSL certificate?
- For an SSL certificate to be valid, domains need to obtain it from `a certificate authority (CA)`. A CA is an outside organization, a trusted third party, that generates and gives out SSL certificates. The CA will also digitally sign the certificate with their own private key, allowing client devices to verify it. Most, but not all, CAs will charge a fee for issuing an SSL certificate.
- Once the certificate is issued, it needs to be installed and activated on the website's origin server. Web hosting services can usually handle this for website operators. Once it's activated on the origin server, the website will be able to load over HTTPS and all traffic to and from the website will be encrypted and secure.

## Why should websites use HTTPS(SSL)?

1. An SSL certificate encrypts sensitive data
2. SSL ensures the information goes where it is intended
3. SSL guards against scams
4. An SSL certificate promotes customer confidence and trust
5. An SSL certificate improves SEO

## Behind the Scenes of SSL Cryptography
- Asymmetric and symmetric keys work together to create an SSL-encrypted connection.
  - Symmetric encryption (or pre-shared key encryption) uses a single key to both encrypt and decrypt data. Both the sender and the receiver need the same key to communicate.
- Asymmetric encryption (or public-key cryptography) uses a separate key for encryption and decryption. Anyone can use the encryption key (public key) to encrypt a message. However, decryption keys (private keys) are secret. This way only the intended receiver can decrypt the message. The most common asymmetric encryption algorithm is RSA.

1. Server sends a copy of its asymmetric public key.
2. Browser creates a symmetric session key and encrypts it with the server's asymmetric public key. Then sends it to the server.
3. Server decrypts the encrypted session key using its asymmetric private key to get the symmetric session key.
4. Server and Browser now encrypt and decrypt all transmitted data with the symmetric session key. This allows for a secure channel because only the browser and the server know the symmetric session key, and the session key is only used for that session.

## What is a handshake?



