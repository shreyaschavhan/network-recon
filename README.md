`My Notes on Network Recon`

## Network Recon Notes

```
Start date: 06 Sept 2023
```
Why to do network recon?

> - To gather information and access the current security posture of the organization.
> - Map the attack surface to focus our efforts on potential entry points and weaknesses,
increasing the efficiency of our attacks/security assessment.

---

- whois

> Why use whois?
> - Whois is a TCP service that aims to provide public information about a domain name.
> - We use this to find the information about the owner/registrar of the domain.

> - Command: 
```python
whois
```
> - Example:
```python
┌──(shreyas㉿kali)-[~]
└─$ whois google.com                                                                    
   Domain Name: GOOGLE.COM
   Registry Domain ID: 2138514_DOMAIN_COM-VRSN
   Registrar WHOIS Server: whois.markmonitor.com
   Registrar URL: http://www.markmonitor.com
   Updated Date: 2019-09-09T15:39:04Z
   Creation Date: 1997-09-15T04:00:00Z
   Registry Expiry Date: 2028-09-14T04:00:00Z
   Registrar: MarkMonitor Inc.
   Registrar IANA ID: 292
   Registrar Abuse Contact Email: abusecomplaints@markmonitor.com
   Registrar Abuse Contact Phone: +1.2086851750
   Domain Status: clientDeleteProhibited https://icann.org/epp#clientDeleteProhibited
   Domain Status: clientTransferProhibited https://icann.org/epp#clientTransferProhibited
   Domain Status: clientUpdateProhibited https://icann.org/epp#clientUpdateProhibited
   Domain Status: serverDeleteProhibited https://icann.org/epp#serverDeleteProhibited
   Domain Status: serverTransferProhibited https://icann.org/epp#serverTransferProhibited
   Domain Status: serverUpdateProhibited https://icann.org/epp#serverUpdateProhibited
   Name Server: NS1.GOOGLE.COM
   Name Server: NS2.GOOGLE.COM
   Name Server: NS3.GOOGLE.COM
   Name Server: NS4.GOOGLE.COM
   DNSSEC: unsigned
   URL of the ICANN Whois Inaccuracy Complaint Form: https://www.icann.org/wicf/
>>> Last update of whois database: 2023-09-06T02:49:00Z <<<

```

---

- ipconfig / ifconfig / ip
> Why do we use them?
> - They provide details about the network interfaces on the system, including IP addresses, subnet masks, default gateways, DNS servers, and more.
> - So, we usually use these commands to understand ip configurations of a system.
> - This can help us:
>    - Troubleshoot network connectivity issues.
>    - Configuring and managing network interfaces.
>    - And more.

> - Commands:
```python
Windows: ipconfig
Linux or Unix-systems: ifconfig / ip a
```

--- 

- ping
> Why do we use ping?
> - Ping is primarily used to test whether a device or host on a network is reachable or not.
> - It sends a series of ICMP (Internet Control Message Protocol) echo request packets to the target host, and if the host is online and operational, it should respond with ICMP echo reply packets.
> - Other uses:
>    -  Ping measures the time it takes for a packet to travel from the source device to the destination host and back. This is also known as Round Trip time (RTT).
>    -  Detect packet loss.
>    -  Detect network instability: Consistently high or erratic ping times may indicate network congestion or instability.
>    -  Ping can also be used to verify DNS resolution.

> - Commands:
```python
ping
```
> - Example:
```python
ping google.com

Pinging google.com [142.250.192.110] with 32 bytes of data:
Reply from 142.250.192.110: bytes=32 time=24ms TTL=118
Reply from 142.250.192.110: bytes=32 time=25ms TTL=118
Reply from 142.250.192.110: bytes=32 time=26ms TTL=118
Reply from 142.250.192.110: bytes=32 time=24ms TTL=118

Ping statistics for 142.250.192.110:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 24ms, Maximum = 26ms, Average = 24ms
```

---

- arp
> Why use arp?
> - ARP (Address resolution protocol) is responsible for mapping or resolving an IP address (layer 3) to a corresponding physical MAC (Media Access Control) address (layer 2) on a local network.
> - We use arp to:
>    - View the ARP cache. What's arp cache? ARP cache is a temporary table of IP addresses and their corresponding MAC address.
>    - Trouble-shoot problems with not responding devices if you suspect there's a MAC address conflict or ARP cache corruption.
>    - to discover the MAC address associated with the target device's IP address.
>    - MAC Address Spoofing Detection by comparing output of arp with already known valid MAC addresses.

> - Command
```
arp --help
```


---

- route
> Why use route?
> - We use it to view and manage the routing table on a computer or network device.

> - Command
```
route print
```

---

- traceroute / trace / tracert
> Why do we use traceroute / trace / tracert>
> - to trace the route that packets take from your computer to a destination host or IP address.
> - to identify and display the network path, including the intermediate routers or network devices (hops), that data packets traverse to reach the target destination.
> - It helps us:
>    - Understand the Network Topology.
>    - Identify Points of Failure i.e.  identify the specific router or hop where packet loss or latency occurs.
>    - Verify that our data is taking the intended routing path.
>    - etc

> - Commnads
```
Windows: tracert example.com
Linux/Unix: traceroute example.com
```
> - Example:
```python
$ tracert google.com

Tracing route to google.com [2404:6800:4009:832::200e]
over a maximum of 30 hops:

  1     2 ms     1 ms     1 ms  2401:4900:1c8e:3ca4:b6a7:c6ff:fe1f:bcf8
  2    21 ms    24 ms    37 ms  2401:4900:1c2c:8fff::1
  3    43 ms    24 ms    21 ms  2404:a800:2a00:101::14d
  4    28 ms    28 ms    44 ms  2404:a800::167
  5    26 ms    24 ms    25 ms  2001:4860:1:1::10e0
  6    30 ms    26 ms    28 ms  2404:6800:80b2::1
  7     *       24 ms     *     2001:4860:0:1::27e6
  8     *        *        *     Request timed out.
  9    28 ms    28 ms    26 ms  2001:4860:0:115d::1
 10    26 ms    24 ms    24 ms  2001:4860:0:1::5ecf
 11    28 ms    25 ms    29 ms  bom07s45-in-x0e.1e100.net [2404:6800:4009:832::200e]

Trace complete.
```

---

- nmap
> Why use nmap?
> - It's an open-source network scanning and reconnaissance tool.
> - We use it for various reasons:
>    - Network Discovery
>    - Port Scanning
>    - Operating System Fingerprinting
>    - Service Version Detection
>    - Vulnerability Assessment
>    - Firewall and Security Policy Auditing
>    - Network Mapping and Topology Analysis
>    - Scriptable Scans
>    - etc, etc.

> - Basic Command:
```
nmap
```
