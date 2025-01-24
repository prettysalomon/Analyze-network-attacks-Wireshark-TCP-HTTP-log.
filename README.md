
<h1>Analyze Network Attacks using Wireshark TCP/HTTP log!</h1>

<h2>Scenario</h2>

You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like. 

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor. 

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

 


<h2>Project Description</h2>

The travel agency's web server, which is crucial for employees to access and recommend vacation packages to customers, experienced a severe disruption due to an apparent cyberattack. An automated alert from the monitoring system indicated unusual activity, and further investigation using a packet sniffer revealed an overwhelming number of TCP SYN requests originating from an unfamiliar IP address. This traffic volume caused the server to become unresponsive, resulting in connection timeout errors for users attempting to access the company's website.


This project aims to analyze the attack, identify its impact on business operations, and implement long-term security measures to prevent similar incidents in the future. The next steps involve discussing more robust countermeasures such as enabling SYN cookies, rate limiting, intrusion detection/prevention systems (IDS/IPS), and traffic filtering solutions. The goal is to enhance the server's resilience against DoS attacks while ensuring continued availability and reliability of the company's online services.

<h2>Access Supporting material</h2>

-[Wireshark TCP/HTTP log](https://docs.google.com/spreadsheets/d/1enpRzrIao3J2Lp2tOI0hmu1Cu7D7CjLGhFAiTiR9J64/edit?gid=218501934#gid=218501934)

-[The Attack](https://docs.google.com/document/d/12prjbAFWB_PD-AqGnHOpWySOeJLnwEYKAVFk2S76OWM/edit?usp=sharing)



<h2>Analysis of the data</h2>

One potential explanation for the website’s connection timeout error message is a DoS attack. The logs show that the web server stops responding after it is overloaded with high volume of incoming TCP SYN packet requests.These requests consume system resources as the server attempts to allocate memory and maintain half-open connections, leading to service degradation and an inability to respond to legitimate users. This event could be a type of DoS attack called 'SYN flooding'.


<h2>How the attack is causing the website malfunction</h2>

When the website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. The handshake consists of three steps:
1. A SYN packet is sent from the source to the destination, requesting to connect.
2. The destination replies to the source with a SYN-ACK packet to accept the connection request. The destination will reserve resources for the source to connect.
3. A final ACK packet is sent from the source to the destination acknowledging the permission to connect.

In the case of a SYN flood attack, a malicious actor will send a large number of SYN packets all at once, which overwhelms the server’s available resources to reserve for the connection. When this happens, there are no server resources left for legitimate TCP connection requests.

The logs indicate that the web server has become overwhelmed and is unable to process the visitors’ SYN requests. The server is unable to open a new connection to new visitors who receive a connection timeout message.

<h2>Solutions to implement</h2>

To address the issue, the following actions should be taken:

-Restart the affected web server to clear the connection backlog.

-Implement SYN cookies to manage and filter incomplete connections more effectively.

-Deploy an Intrusion Prevention System (IPS) to detect and block similar attack patterns.

-Consider using a Web Application Firewall (WAF) or DDoS protection services from a cloud provider to handle volumetric attacks.

