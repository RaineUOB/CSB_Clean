# Exercises sheet 4

## WEB Security

1. What is the impact of a successful SQL injection attack? Do you know any SQL injection examples?

2. What are the types of XSS attacks? Explain! What is the difference between them?

3. List three design goals for a firewall.

4. What are some weaknesses of a packet filtering firewall?

5. What is the difference between a packet filtering firewall and a stateful inspection firewall?

6. One approach to defeating the tiny fragment attack is to enforce a minimum length of the transport header that must be contained in the first fragment of an IP packet. If the first fragment is rejected, all subsequent fragments can be rejected. However, the nature of IP is such that fragments may arrive out of order. Thus, an intermediate fragment may pass through the filter before the initial fragment is rejected. How can this situation be handled?

7. A common management requirement is that “all external Web traffic must flow via the organization’s Web proxy.” However, that requirement is easier stated than implemented. Discuss the various problems and issues, possible solutions, and limitations with supporting this requirement. In particular consider issues such as identifying exactly what constitutes “Web traffic” and how it may be monitored, given the large range of ports and various protocols used by Web browsers and servers.

8. What are two common techniques used to protect a password file?

9. Why is it useful to have host-based firewalls?

10. What are three benefits that can be provided by an intrusion detection system?

11. What is the difference between statistical anomaly detection and rule-based intrusion detection?

12. What metrics are useful for profile-based intrusion detection?

13. An example of a host-based intrusion detection tool is the tripwire program (you can google it). This is a file integrity checking tool that scans files and directories on the system on a regular basis and notifies the administrator of any changes. It uses a protected database of cryptographic checksums for each file checked and compares this value with that recomputed on each file as it is scanned. It must be configured with a list of files and directories to check, and what changes, if any, are permissible to each. It can allow, for example, log files to have new entries appended, but not for existing entries to be changed. What are the advantages and disadvantages of using such a tool? Think! Consider the problem of determining which files should only change rarely, which files may change more often and how, and which change frequently and hence cannot be checked. Hence consider the amount of work in both the configuration of the program and on the system administrator monitoring the responses generated.



## Answers
- **ANS A.1:** A successful SQL injection attack can result in unauthorized access to sensitive data, such as passwords, credit card details, or personal user information. Many high-profile data breaches in recent years have been the result of SQL injection attacks, leading to reputational damage and regulatory fines. In some cases, an attacker can obtain a persistent backdoor into an organization's systems, leading to a long-term compromise that can go unnoticed for an extended period. There are a wide variety of SQL injection vulnerabilities, attacks, and techniques, which arise in different situations. Some common SQL injection examples include:
  - Retrieving hidden data, where you can modify a SQL query to return additional results.
  - Subverting application logic, where you can change a query to interfere with the application's logic.
  - UNION attacks, where you can retrieve data from different database tables.
  - Examining the database, where you can extract information about the version and structure of the database.
  - Blind SQL injection, where the results of a query you control are not returned in the application's responses.

- **ANS A.2:** There are three main types of XSS attacks. These are:
  - Reflected XSS, where the malicious script comes from the current HTTP request.
  - Stored XSS, where the malicious script comes from the website's database.
  - DOM-based XSS, where the vulnerability exists in client-side code rather than server-side code. 

- **ANS A.3:** Three design goals of a Firewall are: 
  - 1. All traffic from inside to outside, and vice versa, must pass through the firewall. This is achieved by physically blocking all access to the local network except via the firewall. Various configurations are possible, as explained later in this section.
  - 2. Only authorized traffic, as defined by the local security policy, will be allowed to pass. Various types of firewalls are used, which implement various types of security policies, as explained later in this section.
  - 3. The firewall itself is immune to penetration. This implies that use of a trusted system with a secure operating system.

- **ANS A.4:** Some weaknesses of packet filtering are: 
  - 1. Because packet filter firewalls do not examine upper-layer data, they cannot prevent attacks that employ application-specific vulnerabilities or functions. For example, a packet filter firewall cannot block specific application commands; if a packet filter firewall allows a given application, all functions available within that application will be permitted.
  - 2. Because of the limited information available to the firewall, the logging functionality present in packet filter firewalls is limited. Packet filter logs normally contain the same information used to make access control decisions (source address, destination address, and traffic type).
  - 3. Most packet filter firewalls do not support advanced user authentication schemes. Once again, this limitation is mostly due to the lack of upper-layer functionality by the firewall.
  - 4. They are generally vulnerable to attacks and exploits that take advantage of problems within the TCP/IP specification and protocol stack, such as network layer address spoofing. Many packet filter firewalls cannot detect a network packet in which the OSI Layer 3 addressing information has been altered. Spoofing attacks are generally employed by intruders to bypass the security controls implemented in a firewall platform.
  - 5. Finally, due to the small number of variables used in access control decisions, packet filter firewalls are susceptible to security breaches caused by improper configurations. In other words, it is easy to accidentally configure a packet filter firewall to allow traffic types, sources, and destinations that should be denied based on an organization's information security policy.

- **ANS A.5:** A traditional packet filter makes filtering decisions on an individual packet basis and does not take into consideration any higher layer context. A stateful inspection packet filter tightens up the rules for TCP traffic by creating a directory of outbound TCP connections. There is an entry for each currently established connection. The packet filter will allow incoming traffic to high- numbered ports only for those packets that fit the profile of one of the entries in this directory

- **ANS A.6:** It will be impossible for the destination host to complete reassembly of the packet if the first fragment is missing, and therefore the entire packet will be discarded by the destination after a time-out.

- **ANS A.7:** A requirement like "all external Web traffic must flow via the organization's Web proxy." is easier stated than implemented. This is because identifying what actually constitutes “web traffic” is highly problematical. Although the standard port for HTTP web servers is port 80, servers are found on a large number of other ports (including servers belonging to large, well-known and widely used organizations). This means it is very difficult to block direct access to all possible web servers just using port filters. Whilst it is easy enough to configure web browser programs to always use a proxy, this will not stop direct access by other programs. It also means that the proxy server must have access to a very large number of external ports, since otherwise access to some servers would be limited. As well as HTTP access, other protocols are used on the web. All of these should also be directed via the proxy in order to implement the desired policy. But this may impact the operation of other programs using these protocols. In particular, the HTTPS protocol is used for secure web access that encrypts all traffic flowing between the client and the server. Since the traffic is encrypted, it means the proxy cannot inspect its contents in order to apply malware, SPAM or other desired filtering. Whilst there are some mechanisms for terminating the encrypted connections at the proxy, they have limitations and require the use of suitable browsers and proxy servers.

- **ANS A.8:**
  - One-way encryption: The system stores only an encrypted form of the user's password. When the user presents a password, the system encrypts that password and compares it with the stored value. In practice, the system usually performs a one-way transformation (not reversible) in which the password is used to generate a key for the encryption function and in which a fixed-length output is produced.
  - Access control: Access to the password file is limited to one or a very few accounts.

- **ANS A.9:** Host based firewalls are useful because: 
  - Filtering rules can be tailored to the host environment. Specific corporate security policies for servers can be implemented, with different filters for servers used for different application.
  - Protection is provided independent of topology. Thus both internal and external attacks must pass through the firewall.
  - Used in conjunction with stand-alone firewalls, the host-based firewall provides an additional layer of protection. A new type of server can be added to the network, with its own firewall, without the necessity of altering the network firewall configuration. 

- **ANS A.10:** Three benefits of an Intrusion detection system are: 
  - 1. If an intrusion is detected quickly enough, the intruder can be identified and ejected from the system before any damage is done or any data are compromised. Even if the detection is not sufficiently timely to preempt the intruder, the sooner that the intrusion is detected, the less the amount of damage and the more quickly that recovery can be achieved.
  - 2. An effective intrusion detection system can serve as a deterrent, so acting to prevent intrusions.
  - 3. Intrusion detection enables the collection of information about intrusion techniques that can be used to strengthen the intrusion prevention facility.

- **ANS A.11:** 
  - Statistical anomaly detection involves the collection of data relating to the behavior of legitimate users over a period of time. Then statistical tests are applied to observed behavior to determine with a high level of confidence whether that behavior is not legitimate user behavior.
  - Rule-Based Detection involves an attempt to define a set of rules that can be used to decide that a given behavior is that of an intruder.

- **ANS A.12:** Some useful metrics for Profile based intrusion detection: 
  - Counter: A nonnegative integer that may be incremented but not decremented until it is reset by management action. Typically, a count of certain event types is kept over a particular period of time.
  - Gauge: A nonnegative integer that may be incremented or decremented. Typically, a gauge is used to measure the current value of some entity.
  - Interval timer: The length of time between two related events.
  - Resource utilization: Quantity of resources consumed during a specified period.

- **ANS A.13:** A file integrity checking tool such as tripwire can be very useful in identifying changed files or directories on a system, particularly when those change should not have occurred. However most computer systems are not static, and significant numbers of files do change constantly. Hence it is necessary to configure tripwire with a list of files and directories to monitor, since otherwise reports to the administrator would be filled with lists of files that are changing as a matter of normal operation of the system. It is not too difficult to monitor a small list of critical system programs, daemons and configuration files. Doing this means attempts to alter these files will likely be detected. However the large areas of the system not being monitored means an attacker changing or adding files in these areas will not be detected. The more of the system that is to be monitored, the more care is needed to identify only files not expected to change. Even then, it is likely that user’s home areas, and other shared document areas, cannot be monitored, since they are likely to be creating and changing files in there regularly. As well, there needs to be a process to manage the update of monitored files (as a result of installing patches, upgrades, new services, configuration changes etc). This process has to verify that the changed files are correct, and then update the cryptographic checksums of these files. Lastly the database of cryptographic checksums must be protected from any attempt by an attacker to corrupt it, ideally by locating on read-only media (except when controlled updates are occurring).
