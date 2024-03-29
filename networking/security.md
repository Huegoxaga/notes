# Cyber Security

- Cyber security is the approach and actions associated with security risk management processes followed by organizations and states to protect confidentiality, integrity and availability of data and assets used in cyber space. The concept includes guidelines, policies and collections of safeguards, technologies, tools and training to provide the best protection for the state of the cyber environment and its users - D.Schatz, R. Bashroush, & J. Wall (2017)
- The protection afforded to an automated information system in order to attain the applicable objectives of preserving the integrity, availability, and confidentiality of information system resources (includes hardware, software, firmware, information/data, and telecommunications). (NIST Computer Security Handbook)
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
      - Spear-Phishing refers to attacks that target to a smaller group of people
    - Following a phishing email will lead to a website made up to look exactly like the real thing
      - Sophisticated phishing websites will even have secure connections, however they cannot fake the website URL via phishing alone
    - Phishing emails can also include malicious attachments
      - End users must be trained to spot phishing emails and to not open any links or attachments from suspicious emails
  - Typo-squatting
    - Typo-squatting is when a malicious actor owns a domain name that is very similar to a legitimate website that is visited often. By creating a look-a-like web page, username and password credentials can easily be stolen. These web pages can also be used to try to download malware onto the visitor’s computer
    - This should be distinguished from cyber squatting or domain squatting, which is owning a desirable domain name and "sitting on it" until there is a motivated buyer
  - Brute-force and Dictionary Attacks
    - Brute-force attacks use a random approach, trying every combination of letters, numbers, and symbols until it is successful
    - A dictionary attack is a method of breaking into a password-protected computer or server by systematically entering every word in a dictionary as a password
    - If the hashed password on the host is found. A list of hash code can be generated base on the dictionary. Then the original password might be retrieved if a match if found
    - The best defense is to have a highly secure password. Encourage employees to use a "pass phrase" -- a complex enough series of words, numbers, and symbols will make the amount of time needed to crack the password so long that it is practically infeasible
  - Code Injection
    - Whereby the attacker takes advantage of a bug in software that allows them to input something that was not expected
    - For example, on a website that may be expecting you to type your first name to fill out a form, an attacker might type in some malicious code instead
    - If the software was not programmed to check the input for validity, it may end up executing the malicious code. This can be used by the attacker to destroy data or to gain further access
  - CSRF Attack
    - Also known as XSRF, "sea surf" session riding, cross-site reference forgery, and hostile linking
    - Attacker lures the user's to open a malicious website that sending malicious request with valid session data stored in browser's cookies
      - New random CSRF tokens can be generated by servers and send to the clients' browsers after each legit request, to prevent CSRF attack
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
  - The goal could be damaging the computer or its data, stealing data, opening a "backdoor" to gain more access, sending a political message, or even just to simply seeing how far the malware will spread
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
  - Bot - A bot is a piece of malicious software that gets orders from a master
    - Bots (also known as zombies) are Internet connected devices that have been hijacked by a malicious actor
    - Bots can be remotely controlled by the attacker
    - Groups of bots form botnets, all of which can be controlled from a centralized location
    - Botnets can be used for Distributed Denial of Service (DDoS) attacks, to send spam, or to spread more malware
  - Cryptojacking software - is when an attacker covertly uses the victim's device to mine cryptocurrency for the attacker
    - Seemingly legitimate programs can be running cryptomining software in the background, effectively making them malware
    - Cryptomining is another use of botnets, enabling the malicious actor to use all of the compromised computers to mine cryptocurrency
- A white hat hacker is an ethical computer hacker, or a computer security expert, who specializes in penetration testing and other testing methodologies that ensure the security of an organization's information systems
- Penetration test is an authorized simulated cyberattack on a computer system, performed to evaluate the security of the system
- A vulnerability assessment is a systematic review of security weaknesses in an information system by doing various scans
  - Vulnerability assessments and penetration tests are complementary, as both have desirable qualities the other lacks (scans are automated and relatively quick; pen tests are rigorous and provide more context)
- Zero-day vulnerabilities
  - This is term that describes any serious vulnerability that is known to no one except a hacker who has just discovered it
  - "Day one" is the day when the vendor of the software becomes aware of the vulnerability, for which they will then typically create a security patch
  - These vulnerabilities are often shared (or sold) between black hat hackers
  - If they are discovered by a white hat hacker, they may by reported directly to the software vendor (sometimes for a reward), or posted publicly to draw attention and incite improvements
- Attack Surfaces
  - Represents all the points of exposure of a system or application to attackers
  - Each of these points of potential attack are often referred to as attack vectors
  - They are categorized in these ways:
    - Network attack surface
      - the profile exposed to network-based attacks, including protocol vulnerabilities, denial-of-service, and link disruption attacks
    - Software attack surface
      - refers to code vulnerabilities affecting the OS, applications, and server software such as Apache or IIS
    - Human attack surface
      - often neglected by those more focused on technological measures applying to the above two categories often the greatest weakness of any organization, susceptible to social engineering, human error, fatigue, and insider threats
- Attack Trees
  - Helps to illustrate possible techniques to breach security and achieve a particular objective
  - Branching and hierarchical structure
  - Objective is the root node
  - Branches represent ways to achieve the objective
  - Leaves represent ways to initiate an attack
  - Non-leaf nodes are either AND or OR nodes
    - AND: all sub-goals must be achieved
    - OR: one or more sub-goals must be achieved
  - Cost, difficulty, and other attributes can be designated for branches to compare alternatives
- The CIA Triad - A model for information assurance (IA)
  - Confidentiality - The protection of confidential data from being inappropriately disclosed to an unauthorized party
  - Integrity - The assurance that information and programs are changed only in a specified and authorized manner
  - Availability - The assurance of the continued operation of systems and services to authorized users

## Stages of a Cyber Attack

### Reconnaissance

- There are two types of reconnaissance
  - Passive Reconnaissance - Refers to information gathering methods that are unlikely to alert the target
    - For example, if the target is a web server, a passive reconnaissance technique would be to simply connect to a website hosted by that web server as if you were using the website like anyone else
  - Active Reconnaissance - Refers to gathering of information by interacting with the target more directly. This type of recon is more likely to be discovered
    - Typically involves network scans, which may include pings, port scans, certain information gathering requests being sent to specific ports/services, and so on
- Types of Information Gained from Recon
  - Network Information – General information about the network as a whole, including, IP Addresses, Network Topology, Domain Names
  - Host Information – Information about individual devices on the network, including, Operating System and Patches, Open Ports and Running Services, Usernames and Group Names
  - Security Policy Information – Information about security software, physical security devices, and policies that are in place on the network and equipment, including, Firewalls and Intrusion Detection Systems, Password Policies
  - Human Information – Information pertaining to the people that use the network. Useful for social engineering attacks, including, Names and Roles, Email Addresses, Telephone Numbers, Social Information

### Analysis for Potential Vulnerabilities

- Vulnerability Analysis is about taking the information gained from recon and figuring out a way to utilize it towards exploitation
- The issues can be addressed by
  - a white hat consultant or taken advantage of by a black hat hacker
  - use premade tools that scan for and analyze well-known security issues that have not been addressed in the target network
  - perform related analysis and research into the vulnerabilities that are present

#### Common Vulnerabilities

- Missing Patches - Unpatched software is vulnerable to well-known, published exploits
- Use of Broken Algorithms
  - This ties in closely to the previous topic of outdated software
  - Algorithms used for encryption or hashing are inevitably rendered useless as computers advance far enough to be able to crack them within a reasonable amount of time
  - Some algorithms are retired early due to weaknesses found in their implementation
  - Vendors often provide patches in order to implement the latest and greatest algorithms – but those patches need to actually be applied and those algorithms need to be turned on
  - Because encryption is a computationally intensive task, it may not be possible for older hardware to run newer or stronger versions of algorithms
  - Running a mix of newer and older hardware and software might mean being forced to use the lowest common denominator when it comes to algorithms
  - List of Commonly Found Outdated Algorithms
    - Symmetric Encryption Algorithms
      - DES, 2DES, 3DES – these have been made obsolete by AES, although 3DES is still used.
      - RC4 – Security concerns. Made obsolete by AES.
      - Blowfish – Made obsolete by Twofish and then Threefish. Less commonly used than AES
    - Asymmetric Encryption Algorithms
      - When it comes to asymmetric algorithms, RSA and Diffie-Hellman were both first published in the late 70’s, but have been periodically improved upon over the years and can be made more and more secure by increasing the key strength used for the encryption process
    - Hashing Algorithms
      - SHA-1 – made obsolete by SHA-2 and SHA-3
      - MD5 (and its predecessors) – Broken. Use SHA-2 or SHA-3
    - Recommended Algorithms (2019)
      - Symmetric Encryption Algorithms
        - AES with 128-bit key strength (or 256 for especially secure systems)
      - Asymmetric Encryption Algorithms
        - RSA with 2048-bit key strength (or 4096 for especially secure systems)
        - Elliptic-Curve Diffie-Hellman with 256-bit key strength
      - Hashing Algorithms
        - SHA-256 (which is a version of SHA-2) or better
- Weak Passwords
  - Multi-factor authentication can be used to enhance authentication challenges on systems. Categories of multi-factor authentication mechanisms
    - Something you know (like a username and password)
    - Something you have (like a bank card or key fob)
    - Something you are (fingerprint, etc.)
- Lax Physical Security
  - In the end, having physical access to a computer or device is the simplest way to be able to exploit it
  - Simply being able to momentarily plug in a USB drive into the computer of a distracted person can lead to a completely compromised system
  - Physical security should mean physical access barriers, like locked network cabinets, locked doors, disabled Ethernet ports that aren’t in use, and so forth
- Weak Wireless Access Point Security
  - It doesn’t help that, as previously mentioned, wireless encryption standards are notoriously weak
  - Some hackers do what is called "wardriving", which is driving around in a car with a laptop or smartphone running software that searches for open or easily crackable wireless networks
  - You should never consider your traffic over wireless networks (unless otherwise encrypted by TLS, a VPN, etc.) to be secure, especially public Wi-Fi networks
- Unmanaged Mobile Devices
  - Most organizations today either provide employees with mobile devices or have "Bring Your Own Device" (BYOD) policies whereby company resources can be accessed via personal mobile devices
  - Mobile devices (especially personal ones) represent a weak point in security, since they are difficult to manage from an IT perspective and because they usually connect to the network wirelessly
  - Mobile devices can be lost or stolen and should be configured so that the IT department has the ability to wipe them remotely
  - Organizations can use Mobile Device Management (MDM) software to mitigate some of the risk
- Excessive Levels of Access
  - Users should only have the access they need, nothing more and nothing less. When privileges are no longer required, they should be removed
  - Excessive privileges increase the potential for attacks from internal threats as well as accounts compromised by external threats
  - A common issue is "privilege creep", where over time users are slowly allowed more and more access on the network and its systems beyond what they currently need to do their job. This is especially common in employees who change roles in the organization
- Unchecked User Input
  - SQL code injection
- Software Misconfigurations
  - Often, end users or IT staff will configure software in such a way that it is more convenient for them to use rather than configuring it in such a way that it is secure IT staff may also misconfigure software by accident or due to lack of knowledge
  - Common misconfigurations often lead to common exploits

### Exploitation

- Exploitation is the actual attack on the system that the attacker is trying to compromise, taking place after the recon and analysis steps
- An exploit is a piece of software, a chunk of data, or a sequence of commands that takes advantage of a bug or vulnerability to cause unintended or unanticipated behavior to occur on computer software, hardware, or something electronic

### Completing the Objective

- Gaining further access
- Could include obtaining, modifying, or causing damage to target

### Making an Escape

- Exfiltration of data
- Covering your tracks

## Related Tools

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

### Metasploit

- The most used software for discovering and launching exploits is Metasploit, which is an all-in-one penetration testing framework
- Metaploit contains hundreds of checks and tests to see whether an exploit on a certain system is possible, making it very useful in the analysis step of a cyber attack
- Try the `search check:yes` command in Metasploit to see a complete list of tests
  - Note that some tests have risks -- many may be caught by intrusion detection software
- Searches can be done for tests and exploits for specific operating systems or software that you find on the target network
- Searches can also be done for particular classes of exploits

#### Modules

- A module is a piece of software that the Metasploit Framework uses to perform a task, such as scanning or exploiting a target
- Different types of modules can be used together to perform an attack
- Metasploit includes thousands of modules
- Types of modules
  - Exploit modules
    - The main action of the attack
    - Ex. Taking advantage of unpatched software on the target machine, causing a buffer overflow
  - Payload modules
    - After the target is exploited, what do we want to do or send to the target machine?
    - Ex. Send a file to start a reverse shell, files to stage the next part of the attack, etc.)
    - a reverse shell is a common payload type that will allow the attacker to use the command-line interface of a remote machine, giving them the ability to execute any commands on it that they wish
    - It is called a reverse shell because, via the exploit, you are actually causing the victim to open the remote shell connection to you
  - Auxiliary modules
    - Includes scanners, sniffers, etc.
  - Encoders
    - Used to scramble the code used in the other modules so that they will be less likely to be detected by anti-virus software

#### Metasploit Commands

- `service postgresql start`, Using this command in the Terminal will start the database service that Metasploit uses. This is recommended as it will make Metasploit run faster
- `msfconsole`, Using this command in the Terminal will start the main interactive command-line tool for Metasploit
- `load msgrpc`, Starting Metasploit RPC server
- `help`, Typing the help in the Metasploit console will show you all of the different Metasploit commands as well as descriptions of them. It is a good place to start
- `search`, Type `search <data>` to search the Metasploit database for any modules that have the something in its name. (Ex. search windows)
  - Note: you may want to go to View > Zoom Out so that the text is not wrapping around
- `use`, Type `use <module>` to select a module to use. You must identify the module by its full name, which you would have obtained using the search command (or from reading it online)
- `show info`, Once you have selected a module, use show info to display available targets, basic options, a description, and references of the module
- `show targets`, Once you have selected a module, use show targets to view the different target types for the module. For example, you may find that the module can change targets between Windows and Linux, and you may want to select a specific target type depending on the system you want to attack.
  - Note: Targets are selected using the set command. Ex. set TARGET Windows Server 2003 SP2
- `show payloads`, Once you have selected a target for the module, use show payloads to view the different actions that the module can take after the exploitation has been completed. For example, the module may be able to open a reverse shell if the exploit is successful
  - Note: Payloads are selected using the set command. Ex. set PAYLOADS generic/shell_bind_tcp
- `show options`, Once you have selected a module, a target type, and a payload, use show options to view the different settings you can configure, some of which are mandatory before the module can be executed.
  - Note: Options are configured using the set command. Ex. set LHOST 192.168.10.42
- `Common Options`
  - LHOST – The local IP address to listen on. Use ifconfig to view the IP address of the virtual machine, which is what you want to set LHOST to.
  - LPORT – The local port number to listen on. The number chosen does not matter too much, unless the number is already being used by another service. For that reason, it is best to choose a number >1024 or to use the default if it is already set.
  - `RHOST` – The IP address of the target.
  - `RPORT` – The port number that you are attempting to send traffic to on the target.
- `set`
  - As previously mentioned, this command is used to set the values for the options, targets, and payloads of a module.
    - Ex. set TARGET Windows Server 2003 SP2
    - Ex. set PAYLOADS generic/shell_bind_tcp
    - Ex. set LHOST 192.168.10.42
  - You can use the show command and use an ID number to set a target or payload from the list rather than using a long target/payload name.
  - Example: set payload generic/shell_reverse_tcp OR set target 3
  - Use the show command after any set commands to verify the changes.
  - `run` or `exploit` Once all of your modules have been selected and all of the mandatory options have been configured, you are ready to go.
  - You can type either of the above commands to execute your attack
  - it doesn't make a different which of the two you choose
    - Note: run is faster to type, but entering exploit just seems cooler

#### Armitage

- Armitage is a graphical environment for Metasploit – as we know, graphical interfaces can make software easier to use
- It is still important to be able to use Metasploit itself, as it provides more control and you may not always be using it on a system that has a desktop
- Before using Armitage, you must start Metasploit and run its RPC (remote procedure call) server so that Metasploit will accept commands from Armitage (instructions on next slide)
- Once the Metasploit RPC server is running, open Armitage, enter the relevant information, and click Connect

### Recon

- Zenmap (Nmap)
  - Zenmap is a graphical interface for the network scanner Nmap
  - Nmap means "network mapper". It functions as a way for you to gain an understanding of the network’s topology, helping you to identify any potential weak points for exploitation
  - Nmap is considered an active recon tool
  - Nmap can gather Network Information and Host Information
- recon-ng
  - recon-ng is an all-in-one tool for web and social media reconnaissance, specialized in gathering Human Information
  - It can be used to find out public information about an organization that is on the web, such as domain name registries, host names, and contact info
  - recon-ng can also search and interact with popular social media websites like Twitter and LinkedIn
    - like running a query to find all people on LinkedIn who list a certain organization as an employer, including past employees, then find any listed phone numbers for those people
  - recon-ng can act as a useful tool for the first steps towards a social engineering attack
- Google Search Operators - advanced google search
  - exact match search in double qoutes
  - `OR` search - `epsi OR Coke`
  - `-` exclude search - `Happy -birthday`
  - use `()` to group terms
  - file type search - `"Corporate Directory" filetype:pdf`
  - search within a specific site - `site:`
  - search related to a given domain - `related:`
- Maltego
  - Maltego is a data visualizer for finding relationships between pieces of information found on the Internet
  - It performs data mining from open sources on the web
  - It then displays the information in a graph, showing the links between people, organizations, email addresses, network devices, and much more
  - Maltego is extensible – there are add-ons for searching more kinds of information, and from different sources
    - Try out the "Have I been Pwned?" add-on, which checks an email address against various databases that contain passwords and other information from data breaches over the years

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
  - For IDP supports OIDC, `https:/<IDP_Domain>/.well-known/openid-configuration` returns all related info for config
- `OAuth 2.0` is the active version
- Auth0 generates access tokens for API authorization scenarios, in JSON web token (JWT) format
- It enables Single-Sign On (SSO)
- Compare to SAML, OAuth is more application based
- OAuth has the following flows
  - Authorization Code Flow - Client sends login credentials directly to identity provider with client id and scope, the IDP returns a code ID, which can be further used to get access and refresh token from the IDP
    - The code only valid temporarily
    - An optional `state` parameter is a random string that the client can use, to comfirm the flow happens between the same parties, to prevent CSFR attacks
    - Proof Key for Code Exchange (PKCE) can be used in this flow. The app will generate and store a random string, it sends the hashed string in code ID request, and send the raw string during access token request. IDP server valid the raw string before returning the access token. This prevents authorization code interception attacks
    - A server side auth code flow will request the server to send code ID along with client secret for access token and refresh token
  - Implicit Flow - Client sends login credentials directly to identity provider with client id and scope, the IDP returns an access token directly
    - Refresh token is not returned
    - Less secure than auth code flow since info in the access token will be exposed
  - Client Credentials Flow - Apps request token directly from IDP using client id and client secret

### LDAP

- LDAP (Lightweight Directory Access Protocol) is an open and cross platform protocol used for directory services authentication
  - It manages the access of on-premise devices
- It is an internet protocol in the application layer

## Disaster Recovery

- Disaster recovery is the process of regaining access to the data, software, and hardware needed to resume the operations of an organization after a disaster, whether natural or induced
- Disaster Recovery Plan - Procedures to minimize losses caused by disasters (power failure, fire, flood, etc.
- Recovery Point Objective (RPO) - Defines the point in time to which data must be restored to be acceptable to the owner or user of the data
- Recovery Time Objective (RTO) - Defines the maximum duration of downtime that is acceptable before the Recovery Point Objective is achieved and business resumes

### Backup Strategies

- Methods to protect data
  - Performing backups regularly
  - Remote backups, using cloud storage and/or moving media off-site
  - Storing media in vaults/safes that are fire- and flood-rated
  - Storage Area Networks (SANs) with mirroring and replication
  - Surge protectors, uninterruptible power supplies (UPSs), and emergency generators
  - Fire prevention and suppression
  - Anti-malware and other security measures
- 3-2-1 Backup Rule
  - Keep at least three independent copies of your data
  - Use at least two different types of media
  - Store at least one copy off-site
  - There are variations of this, including 3-1-2, 3-2-2, 3-2-3, etc.
- Full Backup
  - Backs up all files
  - Generally should be performed at least once per week
- Incremental Backup
  - Backs up only files that have been changed or added since the last backup was performed
  - Restoring from an incremental backup requires the most recent full backup, and all subsequent incremental backups
- Differential Backup
  - Backs up files that have been changed or added since the last full backup was performed
  - Restoring from a differential backup requires the most recent full backup and only the most recent differential backup
- Continuous Data Protection (CDP)
  - CDP systems save a copy of every change made to the data, permitting a restore to any point in time
  - Differs from RAID, replication, or mirroring which only protect the current state of the data
- GFS Rotation
  - Grandfather/father/son cycles for daily/weekly/monthly backups
  - Can add other intervals such as quarterly, annually, etc. and remove certain sets from rotation
