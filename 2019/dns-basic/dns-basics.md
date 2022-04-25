---
layout: default
title: DNS Basics
parent: 2019
nav_order: 3
---

# DNS Basics
{: .no_toc }
Presented on 13th July 2019 by [Taeim](https://github.com/kwontaeim)

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


##  The Internet, what is it..?

- The Internet is a network of networks that interconnects devices to exchange information.
- In order to `talk` to each other, all of these devices must have a unique numerical address called an Internet Protocol address or IP Address. An example of an IP address is 94.127.53.132
- When you visit a website from your browser, you are requesting the website from your device’s IP address to the web server’s IP address.
- However, you don’t type in the ip address of the web server, rather the domain name of for example www.google.com
- In so doing, you have queried the DNS.

So what is this DNS?

##  What is the Domain Name System (DNS)?

- The Domain Name System or DNS overcomes this problem of remembering IP addresses by mapping domain names to IP addresses.
- While this sounds like a phone book, it is not a centralised database.
- The DNS is a distributed database across a hierarchy of networks of servers and provide ways for devices and software (like browsers and email) to query the DNS to get an IP address.
- Domain names must be unique.
- Domain names are used for naming websites and email addresses.

Let’s look at a typical domain name.
### www.example.com
- `com` is the First Level Domain or Top Level Domain (TLD)
- `example` is the Second Level Domain
- `www` is the Third Level Domain
- Each Top Level Domain (TLD) is managed by a specific organization called a Registry Operator under contract with ICANN.
- Top Level Domains (TLDs) are divided into two types􏰀
  ○ the generic Top Level Domains (gTLDs) (e.g .com and .org)
  ○ the country code Top Level Domains (ccTLDs) (e.g .uk for United Kingdom and .us for the United States).
- The second level domain is the part that you register which is used to provide online systems such as websites and emails.
- Domains are sold by a large number of registrars and resellers who do so under contract with registrars.

##  Structure of the Domain Name System

-  The DNS processes domain names following their hierarchical structure. A domain name is composed of different parts separated by “dots” and each part represents a hierarchy in the domain name structure and this hierarchy descent from the right to the left part of the domain name.
-  At the highest level of the domain name system is the Root zone. This root zone is managed by Internet Corporation for Assigned Names and Numbers (ICANN) through the PTI (Public Technical Identifiers) which began performing the IANA functions on behalf of ICANN in October 2016. This root zone is maintained by VeriSign through its contract with ICANN and ICANN created a subcontract with PTI to work with VeriSign. PTI has a reporting responsibility to the Customer Standing Committee which provides the oversight for the IANA functions.

##  How does the Domain Name System work?

What happens when I type `www.example.com` in my browser?
-  You type `www.example.com` into your browser’s address bar.
-  The DNS server queries the “root servers” for the information. N.B. The root zone only knows information about the zones they are responsible for which is the Top Level Domains (TLDs). There are 13 root servers which have copies distributed around the world.
-  The root server will refer the DNS server to the `.com` TLD nameservers . The TLD Name servers knows information of all second level domains under their zone.
-  The Top Level Domain Name servers will refer us to the DNS servers responsible for `example.com`
-  The DNS servers authoritative for example.com will give us the IP address for www.example.com” and the web resource is displayed.
-  Every time a DNS query is made, the root servers are the first servers to be contacted. However, there is no need to contact the root servers every time a query is made since results can be obtained from the DNS cache which stores information for recent previous queries. If the DNS server do not find the results in the cached copies it asks a series of servers through a process called recursion until it reaches the authoritative name servers for that domain.

##  Who makes this DNS System work?

### The role of ICANN
- To ensure the continued interoperability of the Internet’s unique identifier systems, ICANN performs a number of functions.
- Management of the Internet’s unique identifiers.
- Coordination of policies determined by the five RIRs for allocating and assigning sets of unique numerical identifiers needed to make the IP system work consistently around the world.
- Managing (through PTI) the distribution and allocation of IP address “blocks” to the RIRs.
 Therefore, ICANN oversees the assignment of both IP addresses and domain names.

### ICANN is guided by the following principles
- To preserve the operational stability and security of the Internet, particularly the domain name system.
- To promote competition and choice for registrants, especially in the generic top-level domain arena􏰀
- To achieve broad representation of global Internet communities􏰀
- And, to develop policy appropriate to its mission through bottom up, consensus-based processes.
### ICANN’s mandate is to act in the public interest on issues regarding the management of the DNS system.


### The ICANN Community

### ICANN is made up of different communities , representing different interests on the Internet and all contribute to any final decisions that ICANN makes.

### There are three “supporting organisations” that represent
- The organisations that deal with IP addresses
- The organisations that deal with domain names
- The managers of country code top-level domains

### Then there are four “advisory committees” that provide ICANN with advice and recommendations. These represent􏰁
- Governments and international treaty organisations
- Root server operators
- Those concerned with the Internet’s security
- The “at large” community, representing the interests of Internet users.

### Who does the work at ICANN?
- For ICANN to carry out its work of managing and coordinating the Internet’s domain name system and its unique identifiers, there are volunteers who work tirelessly to make sure the DNS system runs smoothly. ICANN as an organisation is responsible for the coordination and supporting the volunteers in their work.