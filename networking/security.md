# Cyber Security

- Cyber security is the approach and actions associated with security risk management processes followed by organizations and states to protect confidentiality, integrity and availability of data and assets used in cyber space. The concept includes guidelines, policies and collections of safeguards, technologies, tools and training to provide the best protection for the state of the cyber environment and its users - D.Schatz, R. Bashroush, & J. Wall (2017)
- Cyber Security is aim to protect confidentiality, integrity, and availability of data.
  - A model of three equal parts, all of which must be balanced while creating the policies and procedures that guide the organization’s cyber security plan
- Confidentiality - Confidentiality means ensuring that only the right people can access your data. Factors of confidentiality includes:
  - Data encryption is the "scrambling" of data in an effort to ensure that only the people with the means to decrypt it have the ability to read it.
    - The Enigma machines were a tool designed to encrypt and decrypt messages mechanically
  - Authentication is testing a user in an effort to ensure that they are who they say they are. A username and password pair are an example of authentication factors
  - Authorization is about making sure that users have access only to the data and privileges that they need - nothing more and nothing less
- Integrity - It means ensuring that your data remains consistent
  - Bad actors could modify data while it is "in transit" on the network or while the data is "at rest" on a server's hard drive
  - Data can also be unintentionally modified by user error, hardware or software issues, or even natural events
  - Data integrity can be ensured by techniques such as creating a checksum of the data as well as keeping backups
- Availability - It means ensuring that your data is always accessible for those who need it
  - This could be ensuring that internal resources such as databases are always accessible for employees or ensuring that externalresources such as a corporate websites are always accessible for customers or the general public
  - Bad actors could attempt to attack publicly accessible resources so that customers can’t reach them, creating a potential loss of business
  - Resources can also go down on their own due to hardware failure or software crashes. Backups and redundancy are used to combat this
- Actors
  - Hackers (External Threats)
    - Black Hats – Hack for profit. Self-employed or work in a cyber crime organization.
    - White Hats – Use hacking skills for legal and ethical purposes, often hired by organizations to perform security testing on their systems
    - Hobbyists – Hack for fun and to see what they can accomplish
    - State Sponsored Hackers – Increasingly common, they attempt to steal other governments' secrets, undermine regimes, and even attack private companies for their state’s financial or political gain
    - Hacktivists – Those who hack for social or political reasons
    - Vulnerability Broker – Expert hackers who live in a grey area attempting to find "zero-day" exploits that no one else knows about. They can then sell the knowledge they gain to other hackers or they can alert the target organization to the vulnerabilities in the hopes of claiming bounties.
    - Script Kiddies – Those without much knowledge but that are still a threat due to premade hacking tools
  - Employees (Internal Threats)
    - Disgruntled Employees
    - Untrained Employees
  - Victims (Targets)
    - Executives and Management - The number one target due to their level of access. Management at all levels have a responsibility to learn how to avoid common attacks.
    - Untrained Employees - Employees not given the training they need in order to avoid common attacks.
    - Customers - Customer data such as credit card or personal information can be stolen from the organization’s systems. Customers can be the victim of fake corporate emails being sent to them
- Security threat in general is caused by a combanation of malicious intent and negligence/accidents
- Internal Threat Sources
  - Around 2-out-of-3 cyber attacks come from the inside
  - Internal threats are also much harder to detect
  - They include:
    - Phishing / Malicious Emails
    - Accessing corporate systems from unknown/compromised devices
    - Excessive access privileges on corporate systems
    - Social Engineering (refers to low-tech methods)
- Attack Types
  - Distributed Denial of Service (DDoS) Attacks
    - A common "low-tech" attack that is hard to defend against
    - The attacker uses a swarm of computers under their control (referred to as a botnet) to flood the target with network traffic
    - The goal is to overwhelm the target so that it cannot respond to legitimate requests
    - Advanced firewalls can detect what is and isn’t legitimate traffic, but they can become overwhelmed too
    - If a business falls victim to repeated DDoS attacks, they can hire a specialized mitigation service which has the infrastructure required to fend off these attacks
    - A [map](http://www.digitalattackmap.com/) of daily DDoS attacks around the world
  - Port Scans
    - Ports that are left open can have anyone make a connection into them
    - If the software listening on that port has a vulnerability, it is possible for the attacker to send unexpected, malicious payloads into that port in order to exploit the vulnerability
    - From there, the hacker may be able to execute their own code on the victim’s computer, opening the floodgates to many other avenues of attack
    - Attackers do reconnaissance on which ports are open by using port scanning software to send packets to every port. They then see what responses (if any) they receive back
    - They can target all of the ports of a single computer, or scan all of the ports of all computers on a network – they just need to find one ”in“
    - The responses they receive back can be a telltale sign about what type of software is listening on a given port as well as the operating system running on the computer. From there, they can research possible vulnerabilities and exploits they can use to gain access
    - Example [Port Scanner](https://www.whatismyip.com/port-scanner/) Tool
  - Access Attacks
    - Certain versions of software will have "well-known" exploits and potentially even premade hacking tools to take advantage of them.
    - Software vendors will typically patch these issues. This is the importance of updating software. On the other hand, brand new updates will sometimes bring with them brand new problems to be exploited
    - Another necessary step is "reducing the attack surface" of the computer, which means uninstalling or turning off unused software or services (especially on servers). This reduces the number of avenues of attack
  - Packet Sniffing
    - A packet is a unit of data sent across a computer network. “Inside” the packet is the data that a computer is trying to send to another
    - A packet could contain part of an email, a webpage, or anything else accessed via the computer network
    - "Sniffing" packets means to have a computer on the network which is listening in and recording packets that are not being sent or addressed to them -- in other words, the packet sniffer is eavesdropping on the conversations of other computers
    - This means that if the data inside the packet is not encrypted, it can be read by anyone that is recording the packets on the network
    - Legitimate websites that require you to log in should always have secure connections(HTTPS) available
  - Phishing
    - The practice of sending emails purporting to be from reputable companies in order to induce individuals to reveal personal info
    - Following a phishing email will lead to a website made up to look exactly like the real thing
    - Sophisticated phishing websites will even have secure connections, however they cannot fake the website URL via phishing alone
    - End users must be trained to spot phishing emails and to not open any links or attachments from suspicious emails
  - Brute-force and Dictionary Attacks
    - Brute-force attacks use a random approach, trying every combination of letters, numbers, and symbols until it is successful
    - A dictionary attack is a method of breaking into a password-protected computer or server by systematically entering every word in a dictionary as a password
    - If the hashed password on the host is found. A list of hash code can be generated base on the dictionary. Then the original password might be retrieved if a match if found
    - The best defense is to have a highly secure password. Encourage employees to use a "pass phrase" -- a complex enough series of words, numbers, and symbols will make the amount of time needed to crack the password so long that it is practically infeasible
  - Code Injection
    - Whereby the attacker takes advantage of a bug in software that allows them to input something that was not expected
    - For example, on a website that may be expecting you to type your first name to fill out a form, an attacker might type in some malicious code instead
    - If the software was not programmed to check the input for validity, it may end up executing the malicious code. This can be used by the attacker to destroy data or to gain further access
  - Drive-by Attacks
    - Hackers look for websites that have vulnerabilities and take advantage of them in order to insert their own code
    - The modified website may not look any different than usual. Once the hacker has placed the code on the website, anyone who visits the website might run the code. The code could install malware onto the computer or redirect the web browser to a different malicious website set up by the hacker
    - Keeping web browsers and anti-virus software up-to-date and minimizing the number of plugins on your web browser is the best defense
  - Information Queries
    - Not exactly an attack, but is often a precursor
    - A large amount of information can typically be found online about websites and businesses, usually part of registration processes
    - Further information can be found via social media (of the organization, or of employees)
    - This information can be used towards further social engineering attacks
- Malware can be referred to as any unwanted or undesirable program that infects computers in order to achieve some sort of malicious goal
  - The goal could be damaging the computer or its data, stealing data, opening a “backdoor” to gain more access, sending a political message, or even just to simply seeing how far the malware will spread
  - Malware comes in a variety of types, including viruses, adware, spyware, ransomware, and more
- Malware Types
  - Viruses - Computer viruses are a type of malware that attach themselves to other, legitimate programs. That program is then said to be “infected”, and when it is executed it will also run the malicious code of the virus, often in order for the virus to spread or cause further damage
  - Worms - they are totally self-contained programs that replicate across networks on their own, often at an exponential rate. Once a system is infected, the worm will attempt to spread via such means as emailing itself to all of the victim’s email contacts
    - They are named after tapeworms, which consist of a head attached to a long train of reproductive segments, each of which can produce more worms when detached. This is a reference to the self-replicating nature of computer worms
  - Trojan Horses - Malicious programs that trick us into willingly running it in on our computers by appearing to be something that we want. Often, Trojans will establish a "backdoor" that hackers can use to much more easily access the system
  - Ransomware - A computer infected with ransomware will have part or all of its data encrypted, rendering the data inaccessible. A message will then be displayed, asking the user to pay a certain amount of money in order for the data to be decrypted
    - The name is derived from the malware holding the data for ransom. Unfortunately for many of those who pay, the data will often not be decrypted after all
  - Spyware - It is a general term for any malware that has the intention to gather information such as personal data or passwords and send it back to a centralized server
    - Spyware can keep track of every keystroke on a computer (this type is more specifically referred to as a keylogger)
    - Its purposes can very, including use in identity theft, selling of data to advertisers, or even for spying on someone the bad actor knows
  - Adware - It displays unwanted advertisements, generating income for the creator of the adware
    - Adware will often change your web browser’s home page to something that includes ads, and will periodically redirect the web page you are on to more ads
    - Adware may also display ads in the toolbar of the operating systems, or will open its own windows separate from that of your web browser
- A white hat hacker is an ethical computer hacker, or a computer security expert, who specializes in penetration testing and other testing methodologies that ensure the security of an organization's information systems
- Penetration test is an authorized simulated cyberattack on a computer system, performed to evaluate the security of the system
- A vulnerability assessment is a systematic review of security weaknesses in an information system by doing various scans
  - Vulnerability assessments and penetration tests are complementary, as both have desirable qualities the other lacks (scans are automated and relatively quick; pen tests are rigorous and provide more context)
- Zero-day vulnerabilities
  - This is term that describes any serious vulnerability that is known to no one except a hacker who has just discovered it
  - "Day one" is the day when the vendor of the software becomes aware of the vulnerability, for which they will then typically create a security patch
  - These vulnerabilities are often shared (or sold) between black hat hackers
  - If they are discovered by a white hat hacker, they may by reported directly to the software vendor (sometimes for a reward), or posted publicly to draw attention and incite improvements

## Related Tools

### Penetration Testing Tools

- Vulnerability Scanners
  - A more advanced version of the port scanners
  - Not only can they scan the network for open ports, but they can also scan for virtual machines, mobile devices, databases, etc
  - They analyze any responses they receive in order to tell you as much as possible about the target, allowing you to research potential vulnerabilities for that type of system
  - They are `nmap` (most widely used), `Nessus` (popular, not free), `Nipper`, `Core Impact`, `SAINT`
- Password Crackers
  - Password crackers are automated tools that attempt to guess a user’s password
  - They can use a totally random approach (brute-force attack) or one that references a list or table of likely possibilities (dictionary attack)
  - Password cracking tools have legitimate uses in the event that a password is lost and cannot be reset
  - They are `John the Ripper` (the most popular), `Ophcrack`, `Medusa`
- Packet Sniffers
  - Used to capture and analyze packets on a computer network. Many can be used on both wired and wireless (Wi-Fi, Bluetooth, etc.) connections
  - Anything sent unencrypted on a network can be assumed to be compromised
    - encrypting enhance security and sacrifice speed
  - They are `Wireshark` (most popular), `Fiddler`, `Tcpdump`
- Vulnerability Exploitation Tools
  - These tools provide information about security vulnerability and have the capability to assist in the development of exploit code against a remote target machine
  - They are `Metasploit` (most popular), `Core Impact`, `Sqlmap`, `Netsparker`, `W3af`
- Wireless Hacking Tools
  - Wireless networks (such as Wi-Fi networks) are very convenient, but that convenience comes at a cost, they are far more susceptible to network security threats than wired networks
  - Wireless networks are more vulnerable due to the simple fact that they require much less physical access
  - Outdated wireless security standards are very easy to crack
  - Popular tools include `nSSIDer`, `Aircrack-ng`, `Cain & Able`
- Forensic Tools
  - Digital forensics is the practice of obtaining and protecting evidence on computers and storage media
  - The ability to audit and understand IT incidents is useful in any organization
  - Forensic Tools can do one particular task or can be an all-in-one package that can perform a variety of functions. These tools can protect evidence from modification, recover deleted files, gather and summarize logs from the computer, and so forth
  - Digital forensics is an entire discipline of its own
  - Available tools are `The Sleuth Kit` (most popular), `Autopsy` (graphical environment for The Sleuth Kit), `Helix`, `Encase`

## Authorization Protocols

- Each of the following protocal can be used to authenticate a user from an identity provider
- Each protocols supports various types of authorization flows
  - A flow consists of a serial of steps involved for a user to be authenticated
  - Different flows can be adapoted for different use case
- Single-Sign On (SSO) happens when one login can access multiple different app, regradless which authorization method is implemented
  - Similarly, there is a Single Logout (SLO) feature

### SAML

- SAML stands for `Security Assertion Markup Language`
- The active version if `SAML 2.0`
- It is an XML-based markup language
- It is used to exchange authentication and authorization identities between security domains
  - It allows members of the organization to sign into web apps or any other service providers (SPs) with the credentials from an existing identity provider (IDP) used by the organization
  - SPs can connect to one or more IDPs through SAML
- SAML login is a type of organization-specific logins (enterprise logins)
- It enables SSO by using one or more SPs sharing one IDP or a fedration of IDPs
- Compare to OAuth, SAML is more user based

### OAuth

- The `Open Authorization` (OAuth) authorization framework is a protocol that allows a user to grant a third-party web site or application access to the user's protected resources, without necessarily revealing their long-term credentials or even their identity
- It works with OpenID Connect (OIDC) - an identity layer built on top of the OAuth 2.0 framework that verifies the identity of the end-user and to obtain basic user profile information in JWT token
- `OAuth 2.0` is the active version
- Auth0 generates access tokens for API authorization scenarios, in JSON web token (JWT) format
- It enables Single-Sign On (SSO)
- Compare to SAML, OAuth is more application based
- OAuth has the following flows
  - Authorization Code Flow
  - Implicit Flow

### LDAP

- LDAP (Lightweight Directory Access Protocol) is an open and cross platform protocol used for directory services authentication
  - It manages the access of on-premise devices
- It is an internet protocol in the application layer
