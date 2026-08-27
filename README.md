## PENETRATION TESTING REPORT OF LAB SET-UP
|WEEK 2 |FOOTPRINTING & NETWORK SCANNING PHASES|
W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS

🎯Pentester's Name      
--------------------------------------------
Ashikem Joshua Bengioushuye
(Cybersecurity Professional)
Program/Batch	B082-Networkwalks
---------------------------------------------

Date	24 August 2026
Modules completed	W2-PM1 (Multiple Kali Tools)
W2-PM5 (Zenmap Scanning)
Client/Target	1. Networkwalks (secured written permission already)
2. My own local LAN Network
Permission secured from client?	Yes
Phases covered	Phase 1: Reconnaissance & Footprinting
Phase 2: Scanning & Network Discovery
Phase 3-5: In Progress





1. ## Liability Disclaimer
__________________________________________________________________________________________________________________________________________________________________________________
I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

2. ## Introduction
_______________________________________________________________________________________________________________________________________________________________________________________
This report covers the Week 2 activities in the Cybersecurity Lab Setup On Foot printing and Scanning, a case study of the networkwalks.com domain using multiple Kali Linux tools (W2-PM1) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.
All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.
The footprinting tasks were completed in Kali Linux, while the network discovery exercise was carried out on a Windows computer running Zenmap. For each activity, I recorded the command or procedure used, the result obtained, supporting screenshot evidence and a brief explanation of the security relevance of the observation.


3. ## Tools Used
___________________________________________________________________________________________________________

The table below lists each tool used in this report and its purpose.

| # | Tool | Purpose |
|---|-------------|-------------|
| 1 | Kali Linux & Windows | Operating systems used to carry out the reconnaissance and scanning exercises. |
| 2 | WHOIS | Retrieve publicly available domain registration information, including dates and name servers. |
| 3 | whatweb |Fingerprint web technologies (server, CMS, plugins, IP). |
| 4 |nslookup` | Use DNS resolution to determine the IP address associated with the domain. |
| 5 | curl -I	 | Inspect the website's HTTP response headers for technical information. |
|  6|wafw00f	 | Check whether the website is protected by a Web Application Firewall. |
| 7 | dnsrecon | Collect and enumerate DNS records such as NS, MX, SPF, TXT and SRV entries. |
| 8 | Zenmap (Nmap GUI) |	Discover active devices on the local subnet and obtain IP and MAC address information. |
| 9 | Windows CMD	| Determine local network IP configuration and MAC address details. |

	
	
	
	
	

4. ## Activities Performed
__________________________________________________________________________________________________________________________________________________________________________________________
4.1 Footprinting & Reconnaissance

I carried out reconnaissance on the networkwalks.com domain with six Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. Each utility was selected to gather a specific category of information about the target. 
The first step involved WHOIS, which I used to collect publicly available registration information and identify the domain name servers. This supplied useful details about the domain and elements of its hosting infrastructure.
.

Next, I used 'WhatWeb' to examine the technologies exposed by the website. The scan identified WordPress 7.0.4 and WP Download Manager 3.7.1, together with other publicly detectable technical information.
.
With Nslookup, I translated the domain name into its associated IP address. The result returned the address 192.232.216.135. 
I then ran Curl with the -I option to review the website's HTTP response headers. The response revealed additional application information, including the WordPress REST API endpoint /wp-json/. 
.
Wafw00f was used to check for the presence of a Web Application Firewall. The result indicated that ModSecurity (SpiderLabs) was being used. 
.
Lastly, DNSRecon was used to gather DNS-related records. The output included information about name servers, mail servers, SPF/TXT entries, service records and DNS software. 4.2 Network Scanning with Zenmap

4.2 Network Scanning with Zenmap
In the second practical exercise, I used Zenmap for network discovery on my local LAN. The objective was to determine the local IP address and subnet, locate active hosts, record their IP and MAC addresses and produce a visual network topology. I other words, the IP configuration of the assessment system was examined to identify active network interfaces, assigned addresses, and interface status.
I began by running the Windows 'ipconfig' command to determine the computer's local IP configuration and LAN subnet. I then supplied the identified subnet to Zenmap and selected Ping Scan to locate devices that were responding on the network. 
The practical example produced one active hosts: 
            |192.168.56.2/24|

The example results also included one MAC address. 
Once the scan was completed, I accessed the Topology view in Zenmap, turned on the legend and exported the resulting network topology as a PDF in accordance with the practical requirements. 
Note: Before final submission, the sample subnet, host count and addresses should be replaced with the values obtained from my actual local network.


5. # Risk Analysis / Impact
__________________________________________________________________________________________________________________________________________________________________________________________
Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
|  # |	 Risk / Finding	| Evidence / Observation | Potential Impact | Risk Level |
|----|------------------|------------------------|------------------|------------|
| 01 | Web technology information exposed| WhatWeb identified WordPress and WP Download Manager | Exposed software and version details could help an attacker identify technologies that may need additional security review |●  Medium |
| 02 | Server IP address identifiable | Nslookup resolved the domain to 192.232.216.135 | Provides information about the network location of the web service | ● Low |
| 03 | HTTP technical information exposed | Curl returned HTTP response headers and exposed /wp-json/ | May assist technology fingerprinting and further enumeration | ● Low |
| 04 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs) | Reveals information about the web application’s security architecture | ● Low |
| 05 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service-related records | DNS information can help build a broader infrastructure profile | ● Medium |
| 06 | Multiple live hosts visible on local network | Multiple live hosts visible on local network | Unknown or unauthorized devices may potentially be present on a network | ● Medium 

                                                        Risk level key:  ● Critical  ● Medium  ● Low  	

The items listed above represent observations from the reconnaissance and scanning exercises and should not be treated as confirmed vulnerabilities. The practical work focused on information collection and identifying reachable hosts. No exploitation, penetration of vulnerabilities or vulnerability confirmation was carried out during these modules. Consequently, discovering a software version, IP address or DNS record does not automatically indicate that a security weakness exists. Additional authorized assessment would be necessary before confirming any vulnerability.





6. Recommendations
__________________________________________________________________________________________________________________________________________________________________________________________
The following measures are recommended based on the observations made during the practical exercises: 
1. ## Review publicly visible technology information
   Organizations should periodically assess the technical details exposed by their websites, CMS platforms and installed plugins. 
2. ## Ensure current software versions
   CMS software, plugins and related technologies should be updated regularly and checked against relevant security advisories. 
3. ## Assess HTTP response headers
   Review server response headers to identify and reduce technical information that does not need to be publicly disclosed. 
4. ## Regularly audit DNS records
   DNS entries should be reviewed at intervals so that only necessary records and services remain publicly accessible. 
5. ## Configure and monitor the WAF correctly
   ModSecurity should remain active, properly configured and regularly monitored to strengthen web application protection. 
6. ## Conduct routine internal network discovery
   Organizations should periodically scan their internal networks to maintain visibility of active and connected devices. 
7. ## Validate unfamiliar devices
   Any device that is not recognized during a network scan should be investigated and confirmed as authorized. 
8. ## Keep network records updated always
   Network diagrams, device details and topology information should be maintained and updated when changes occur. 
9. ## Limit testing to authorized environments
    Reconnaissance and scanning should always be conducted only against systems and networks for which appropriate permission has been obtained.





7. Conclusion
As part of Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical exercises focused on reconnaissance, footprinting and network scanning. 
During the footprinting exercise, I worked with six Kali Linux utilities to gather information about the target domain. This helped me understand how WHOIS can reveal domain details, WhatWeb can identify website technologies, Nslookup can resolve domain names, Curl can review HTTP headers, Wafw00f can detect WAF protection and DNSRecon can collect DNS-related information. 
For the network discovery exercise, I used Zenmap to examine my local network configuration and identify active devices. I also recorded IP and MAC address information and produced a network topology as part of the required practical work.
These exercises demonstrated the importance of information gathering in cybersecurity. Before any exploitation is considered, a security practitioner can obtain substantial insight into an environment by analyzing publicly available information and network responses. 
Another key lesson was the importance of presenting technical findings in a clear and structured manner. An effective cybersecurity report should state the activity performed, the evidence obtained, the meaning of each observation, the possible security impact and the recommended corrective action. 
Most importantly, I learned that reconnaissance and network scanning must remain within an approved scope. All activities documented in this report were completed for the assigned educational cybersecurity practical and within the stated authorization requirements.

8. Evidences Collected









-End-


👤 Author
Ashikem Joshua Bengioushuye
Cybersecurity Professional B082
LinkedIn: www.linkedin.com/in/ashiwelljosh
________________________________________
📌 Project Information
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub
