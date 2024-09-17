## Internal Network Penetration Testing ##

<h2> Table of Contents </h2>

* [Internal Network Penetration Testing Introduction](#introduction)
* [Scope](#scope)
* [Host Discovery](#host-discovery)
* [Service Discovery And Port Scanning](#service-discovery-and-port-scanning)
* [Vulnerability Scanning](#vulnerability-scanning)
* [Web-Based Attack Surfaces](#web-based-attack-surfaces)
* [Generating Payloads](generating-payloads)

## Introduction  
Internal penetration testing is an essential practice for identifying and mitigating risks within an organization's network. By simulating an insider threat, organizations can better understand their vulnerabilities and strengthen their security posture against potential attacks. Regular testing not only helps to comply with regulations but also fosters a culture of security awareness among employees.


## Scope  
The scope of engagement comprises of an internal network `10.10.10.0/24` and a domain name: [Virtual InfoSec Africa](https://virtualinfosecafrica.com)

## Host Discovery  
Host discovery is a network scanning technique used to identify active devices (hosts) on a network. It helps network administrators understand which devices are connected, their IP addresses, and their operational status. Host discovery can be crucial for network management, security assessments, and troubleshooting.  
Methods for Host Discovery:  
* Using the ping tool  
The ping command is used to send packets to a destination address; if packets is returned, the network is confirmed online.


* Using the Nmap tool  
Host discovery using the nmap tool;

1. We can have a list of all the addresses in the above Scope

2. We can find out the hosts online in this network by passing to the nmap, the list of the addresses file
filter the results using the grep command, cut using the awk command and then saving it in another file. [Hosts online scan]
![host_up](images/host_up.png)

* Using the Aiodnsbrute tool  
The aiodnsbrute tool is used to brute force a domain name and force out its ip address.Demonstration using the domain provided in the [Scope](#scope)  
1. Install aiodnsbrute using the command "pip3 install aiodnsbrute"  
2. Find a list of wordlists of common subdomains  
3. Run aiodnsbrute  
[aiodnsbruteforcing] 


## Service Discovery And Port Scanning  
In an internal network, services on devices connected to this network can be differenciated from each other due to their assigned port numbers.  
We scan ports to find out the services they are running.  


2. Separate the output of the results into their respective protocols  


3. For each protocol text file created, insert into it, its ip address it runs on using the vim command  

<br>
<h2> VULNERABILITY SCANNING </h2> <br>

| SERVICE VERSIONS | VULNERABILITIES: EXPLOITDB | VULNERABILITIES: MITRE CVE|
|--------------------------------------------|----------------------------|---------------------------|
| http apache httpd 2.4.49                   | ------------ |(https://www.cve.org/CVERecord?id=CVE-2021-42013).    It was found that the fix for CVE-2021-41773 in Apache HTTP Server 2.4.50 was insufficient. An attacker could use a path traversal attack to map URLs to files outside the directories configured by Alias-like directives.
| ssl/http apache httpd 2.4.49               | ------------ |(https://www.cve.org/CVERecord?id=CVE-2021-34798).  Malformed requests may cause the server to dereference a NULL pointer. This issue affects Apache HTTP Server 2.4.48 and earlier.
| mysql MySQL 5.6.49                         | ------------ |(https://www.cve.org/CVERecord?id=CVE-2020-14867)   Difficult to exploit vulnerability allows high privileged attacker with network access via multiple protocols to compromise MySQL Server. Successful attacks of this vulnerability can result in unauthorized ability to cause a hang or frequently repeatable crash (complete DOS) of MySQL Server.
| vnc RealVNC 5.3.2                          | ------------ |(https://www.cve.org/CVERecord?id=CVE-2022-41975) . RealVNC VNC Server before 6.11.0 and VNC Viewer before 6.22.826 on Windows allow local privilege escalation via MSI installer Repair mode.
| rdp Microsoft Terminal Services            | ------------ |(https://www.cve.org/CVERecord?id=CVE-2014-0296).  The Remote Desktop Protocol (RDP) implementation in Microsoft Windows 7 SP1, Windows 8, Windows 8.1, and Windows Server 2012 Gold and R2 does not properly encrypt sessions, which makes it easier for man-in-the-middle attackers to obtain sensitive information by sniffing the network or modify session content by sending crafted RDP packets, aka "RDP MAC Vulnerability."
| smtp Exim smtpd 4.92                       | ------------ |(https://www.cve.org/CVERecord?id=CVE-2023-51766).  Exim before 4.97.1 allows SMTP smuggling in certain PIPELINING/CHUNKING configurations. Remote attackers can use a published exploitation technique to inject e-mail messages with a spoofed MAIL FROM address, allowing bypass of an SPF protection mechanism. This occurs because Exim supports <LF>.<CR><LF> but some other popular e-mail servers do not.
| telnet BSD telnetd                         | https://www.exploit-db.com/exploits/21018  https://www.exploit-db.com/exploits/19520  https://www.exploit-db.com/exploits/409                     |(https://www.cve.org/CVERecord?id=CVE-2011-4862).  Buffer overflow in libtelnet/encrypt.c in telnetd in FreeBSD 7.3 through 9.0, MIT Kerberos Version 5 Applications (aka krb5-appl) 1.0.2 and earlier, Heimdal 1.5.1 and earlier, GNU inetutils, and possibly other products allows remote attackers to execute arbitrary code via a long encryption key, as exploited in the wild in December 2011.
| netbios-ssn Samba 3.6.25                   | ------------ |(https://www.cve.org/CVERecord?id=CVE-2015-0240).  The Netlogon server implementation in smbd in Samba 3.5.x and 3.6.x before 3.6.25, 4.0.x before 4.0.25, 4.1.x before 4.1.17, and 4.2.x before 4.2.0rc5 performs a free operation on an uninitialized stack pointer, which allows remote attackers to execute arbitrary code via crafted Netlogon packets that use the ServerPasswordSet RPC API, as demonstrated by packets reaching the _netr_ServerPasswordSet function in rpc_server/netlogon/srv_netlog_nt.c.
| microsoft-ds Windows 7 - Samba file sharing| ------------ |(https://www.cve.org/CVERecord?id=CVE-2007-2407).  The Samba server on Apple Mac OS X 10.3.9 and 10.4.10, when Windows file sharing is enabled, does not enforce disk quotas after dropping privileges, which allows remote authenticated users to use disk space in excess of quota.
| mysql MySQL 5.5.62                         | ------------ |------------------| 
| vnc UltraVNC 1.2.1.7                       | ------------ |(https://www.cve.org/CVERecord?id=CVE-2019-8280)  UltraVNC revision 1203 has out-of-bounds access vulnerability in VNC client inside RAW decoder, which can potentially result code execution. This attack appear to be exploitable via network connectivity. This vulnerability has been fixed in revision 1204.
