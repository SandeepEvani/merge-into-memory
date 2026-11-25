## What is the Internet?

The Internet is the inter-network communication, which is how different networks discover and communicate with each other.
The collation of different networks together forms the internet.

To understand what precisely is a network and how exactly the communication across the networks happen, we'll have to deep dive into the semantics.

## IP and DNS

IP address is the address that is allocated to a machine that's connected to the internet(LAN/WAN)

DNS -- Domain Name Service, is an alias for IP address.

The IP is of two versions :: IPv4 and IPv6.

IPv4 notation :: 255.255.255.255
It's again divided into two, the subnet mask (network ID) and Host ID.

## Bandwidth and Latency

- Bandwidth is how much data can be pushed per second 
- Latency is how fast the data can be pushed from source to destination.

## DNS

DNS is a Domain Name System, converts IPs into names which can be accessed across the internet.

DNS is a huge and distributed Database, which has the mappings with the name and the IP address.

DNS resolver is the software running either in the router or with the Internet provider which is responsible to resolve the DNS to an IP.

A DNS Zone is a part of the DNS Database.

Zone file contains the DNS records which in turn contains the name of a particular DNS and an Associated value to it (Mostly an IP).

Nameserver is where all the zone files are hosted

