---
id: study-guide
title: Study Guide
---

## Objectives

Follow the CompTIA Objectives listed [here](https://gitlab.com/oscarneedscoffee/notes/-/blob/master/software/security/security-plus/udemy-course/CompTIA-Security-SY0-501.pdf)

|    **Domain**                             | **% of Examination**  |
|-------------------------------------------|-----------------------|
|  1.0 Threats, Attacks and Vulnerabilities | 21%                   |
|  2.0 Technologies and Tools               | 22%                   |
|  3.0 Architecture and Design              | 15%                   |
|  4.0 Identity and Access Management       | 16%                   |
|  5.0 Risk Management                      | 14%                   |
|  6.0 Cryptography and PKI                 | 12%                   |

## TODO

- [ ] Update Cryptography section

## Braindump and Review

Source material came from [Udemy](sec-plus-udemy.md), and Linux Academy's CompTIA Security+ Cert prep from Justin Mitchell.

>Stuff in this "Braindump and Review" section has not been organized into sections. Skip this section if you want. It's just a scratch.

- RSA is the de facto standard and key size is up to 2,048 bits
- DSA Digital Signing Algorithm developed in 1991 adopted by NIST as FIPS 186 in 1994 
- CIRT Cyber Incident Response Team
- MD5 is 128 bits, SHA-256 is 256 bits, [HMAC](#hashing-algorithms)
- [Asymmetric algorithms](#asymmetric-algorithms): 
  - Diffie-Helman, 
  - RSA 2048 bits
  - DSA: Adopted by NIST for digital signature standard 
  - Elliptical Curve Cryptosystem
- [SMTP is port 25, Telnet 23, IMAP 143, and POP is 110](#protocols)
- Pentesting know the [different types](#penetration-testing)
- [PKI](#pki)
- [RAID Levels](#raid)
- LDAP uses port 636
- Password Authentication Protocol PAP authenticates over plain text
- Simple Network Management Protocol (SNMP) is a standard for managing devices on IP based networks
- [Fire exitinguishers](#fire-extinguishers) classes
- Key escrow is when keys are held and in certain circumstances and authorized third party gets access to those keys.
- A P7B certificate is good for transferring certs and cert chains but not the private key.
- Know differences between active scanning and passive scanning.
- Active tools
- [XSS and XSRF](#appplication-attacks)

- 3.1 Frameworks, Best Practices and secure config guides
  - frameworks are blueprints to define structural architecture
  - reference architectures takes frameworks further
  - Types are: regulatory, non-reg, national, international, industry specific
  - **Secure Configuration Guides** are guides to tell you how to configure specific systems
    - guides can come from vendor, government or **Center for Internet Security (CIS)**
  - **Defense in Depth** uses **vendor diversity**, **control diversity** (with admin controls , technical controls), and **User training**

- 3.7 Cloud Concepts
  - Cloud Models SaaS is software available in cloud. ex. Office 365. software on demand
    - PaaS: Multiple software to provide a service. DB, OS provided by provider
    - IaaS: offers bare metal. Provider only provides servers, customer does the rest
  - Cloud Systems:
    - Private cloud: pricey, customer gets to define security, processing and data
    - Public cloud: anyone can access environment, customer data is still segregated
    - Community Cloud: orgs with common interests will share an environment
    - Hybrid Cloud: Any mix of the above
  - SaaS: outsourcing security. A vendor that does this is a **managed security service provider (MSSP)**
  - **Cloud access security broker (CASB)**: acts as enforcement between provider and customers.

- 3.8 resiliency & automation. **Conntinuous Monitoring**, automate configuration validation
  - templates for automation and create a **master image** 
  - snapshots, revert to known state, "rollback to a known configuration" is MS language to revert to known state
  - Live boot media: external device with boot
  - **Elasticity** is ability to scale up and down quickly
  - **Scalability** only lets you scale out (more nodes) or up (stronger hardware)
  
<!-- ------------- Threats, Attacks, Vulnerabilities 1.0 ---------------------------->
## Threats, Attacks, Vulnerabilities

CompTIA Objectives section 1.0

### Malware

CompTIA Objectives Section 1.2  

Malware is malicious software. Types are **polymorphic, virus, armored virus, worms, Trojans, and crypto-malware, keyloggers, adware, spyware, bots, RATs, logic bombs, backdoor**. Ransomware is crypto-malware but the threat actors want money in exchange for an encryption key

- **RAT** (Remote Access Trojan): toolkit to gain access to target
- Backdoor

<!--           ** Types of attacks 1.2 **               -->
### Appplication Attacks 

- **DoS, DDoS**: cut off access. In DoS, the attacker is attacking a known vulnerability. DDoS attacks use multiple attack systems with a zombie network made up of compromised systems 
- **Man-in-the-Middle:** Injected between two hosts. Hard to detect because both systems receive expected replies.
-**Buffer overflow:** most common attack, data is too much for buffer. Attacker exploits improper input validations
- **Injections**: un-validated input allows privilege escalation
- **Cross Site Scripting (XSS)**: similar to injection, but part of web process
  - Non-persistent XSS:  executes once
  - Persistent XSS: attacks web server or backend, and used to scrape data.
  - Dom-based XSS attack: Attack never touches the backend and is on the client side
  - XSS is used for: authentication theft from web app, session hijacking, deploying hostile content, changing user settings, impersonating a user
- **Cross Site Request Forgery (XSRF)**: authorized mechanism for unauthorized use. It exploits truse in a previously authenticated request

Attacks use:

1. **Privilege escalation:** The first step in an attack is to get root
2. **Amplification**: Like DDoS. Hard to defend against because traffic comes from a legitimate source
3. **DNS Poisoning**: Like ARP poisoning. Attacker makes unauthorized incorrect mods to DNS table of host
4. **Domain Hijacking**: Changing the domain registration, spreads false domain via DNS. Redirect Domain name to attacker's site.
5. **Man-in-the-Browser**: Like MitM, MitB installed on target, and waits for a trigger, and makes modifications to the web traffic.
6. **Zero Day**: takes advantage of a vulnerability the vendor doesn't know about
7. **Replay attack**: captures some traffic, and replays it later to bypass authentication. They capture and reuse certs and tokens.
8. **Pass the hash**: When an attacker captures a password hash and tries to reuse it to authenticate.

#### Hijacking Attacks

- **Clickjacking**: attacker uses invisible overlay in UI.
- **Session hijacking**: Gets control of an already authenticated session.
- **Typosquatting** and **URL Hijacking**: typo squatting uses a similar URL if you make a typo for a site.

#### Other Attacks

- **Driver Manipulation**: since drivers are less secure than OS, they're vulnerable
- **Shimming**: puts code between driver and OS
- **Refactoring**
- **Spoofing**: traffic looks like it's coming from somewhere else
  - *MAC spoofing*
  - *IP spoofing*
- **Smurf Attack**: spoofs a packet to all systems and forges from address so the target gets all the echo replies causing a DoS to the

<!--           ** Pen testing 1.4 **               -->
### Penetration Testing

Section 1.4

- White Box testing is done by someone who knows the system
- Grey Box is fro someone who has some knowledge
- Black Box is done by an outside with no previous knowledge of the system

<!--           ** Vulnerability Scanning 1.5 **               -->
### Vulnerability Scanning

Objectives section 1.5  

Vulnerability Scanning is the process of examining system for security holes **before** an attacker finds them.

- different from *pen testing* since you perform your own scans instead of an outside agency
- You only find out the vulnerabilities exists, whereas **Pen testing** tests the entire security posture

#### Uses of V scanning

- ID lack of controls
- ID common misconfigurations

#### Methods of V scanning

- **Intrusive tests** makes modifications and may break the system
- **Non-intrusive** does not modify, but does not go as deep. Same concept as active and passive testing
- **Non-credentialed scans** are from the outside the system and quick. This does not give you as much information as a **Credentialed Scan**. A credentialed scan takes much longer and uses up a system's processing power.

#### V scan results

- **Plan of action**: what measures are taken when results are found. How do we shore up and put controls in place.
- **False positive**: incorrectly reported as a vulnerability
- **False negative**: should have been ID'ed as vulnerability

<!-- ---------- Technology and tools 2.0--------------- -->
## Tools and Tech

CompTIA Objectives 2.0 Technology and Tools

### Protocols

- SMTP is port 25
- Telnet port 23
- IMAP 143
- POP 110
- DNS port 53
- HTTP 80
- TFTP 69
- SNMP 161/162
  
<!-- ---------- Architecture 3.0 --------------- -->
## Architecture Concepts

CompTIA objectives 3.0

### Firewalls

Part of *CompTIA objectives 3.2 secure network architecture*. Monitor network traffice, and decides to allow or block. Enforces rules to NAT, packet filtering, ACLs, stateful ACL, or application layer proxies.

#### Firewall Techniques

>All firewalls should have **implicit deny**. Rules are read top-down, so implicit deny should be the last rule in the stack.

1. **NAT:** designed to resolve IPv4 shortages and works with IPv6. NAT provides a public IP, and firewalls can be configured to perform NAT
2. **Basic packet filtering**: Only uses packet headers to allow or block.
3. **Access Control Lists (ACLs)** Mostly used in file systems. Often an explicit deny, and read top-down
4. **Application based firewalls** : Allows deeper examination of packets rather than just source and destination addresses like network firewalls. ABFs are good for very sensitive data.  \*Note: ABFs are slower than network firewalls.  
5. **Stateful packet inspections:** Looks deep into state of packet, and can discern to allow or block

### Secure Staging
  
Staging environments and security implications CompTIA Objectives 3.4  

- Sandboxing: isolating a system from other hardware, software or networks
- 4 environments to know: dev, test, stage, prod
  - test vs. stage: 
  - test should be as close to prod as possible. Here we can ensure app is bug free prior to prod
  - stage is optional. Allows for deployment to prod in a controlled manner.

### RAID

CompTIA Objective section 4.8 RAID 

- RAID 0 Striping. Good for high speed, not fault tolerant
- RAID 1 Mirroring. Storage is halved
- RAID 5 striping & parity. Striped across, and one block for parity. One drive can fail, and data won't be lost.
- RAID 6 striping with double parity. Two drives can fail.

<!--         ** Secure Coding and Deployments Objective 3.6**        -->
### Secure Coding

CompTIA section 3.6
Below are common best practices for secure coding

- *OWASP Top 10*, and *MITRE 25* list are two of the most common lists of software vulnerabilites
- Errors should be captured in a log file with an ACL of who can access the log files. Don't echo to user
- **Input validation** should prevent actor from changing input before it's sent to backend.
  - Input validation mitigates attacks suck as: buffer overflows, [XSS, CSRF/XSRF, and injection attacks](#appplication-attacks)
- **Normalization** checks and corrects inputs. ex. phone number in the proper format.
- Databases are susceptible to attack
- Use stored procedures to prevent SQL injection attacks
- **Code signing** provides a method to ensure software integrity
  - Code is evidence of code's source
  - Code signing uses **PKI**. The key should be issued by a CA
  - Programs should use proven crypto libraries. **Don't roll your own**
- Obfuscation in development and testing environments ensure data elements were incidentally exposed to an external factor.
  - Obfuscating code is rarely recommended.
- Code reuse can fail on multiple systems
- Dead code: output no longer used.

> Because we can't guarantee security of the client, all sensitive operations should b e performed on the server side.

Systems can be allowed input validations from client and server, but don't trust the client.

- **Memory Management**: Errors in memory management like buffer overflows need to be managed
- **Data Exposure**: refers to the loss of control over data from a system. *Data at rest, data in transit, and data in use* must be accounted for.

### Code Quality and Testing

- **Code Analysis** processes to inspect code for weaknesses and vulnerabilities.  
  - Static analysis examines the code without execution
  - Dynamic analysis tests the code while its in operation. Feed test inputs and measures against expected
    - *Fuzzing* is a form of dynamic in which a brute force test method is used to detect input validation issues or vulnerabilities.
- Stress Testing aka performance testing is used to determine bottlenects or variables.
  - **load testing** is testing to ensure the system works under normal conditions
  - **Stress testing** takes load testing even more.
- **Model Verification** is ensuring what the code is supposed to do. Ensure system meets design requirements and meets needs of the customer.
- Version control
  - Change management allows us to maintain lists of what issues arise, issues fixed and how changes are being implemented. Can determine if everything was tested, failures, and how to roll back.

<!--         ** Virtualization Concepts 3.7**        -->
### Virtualization

Virtualization Section 3.7

- Virtualization allows a computer to have more than one OS
- A **Hypervisor** separates an OS and applications from underlying hardware. A hypervisor allocates resources to VMs

#### Hypervisor types

1. Type 1: Baremetal run directly on hardware
2. Type 2: run on top of the OS. More popular in early days of virtualization

#### Containers/ Application Cells

- **Application Cells** aka **containers** offer the same functionality as VM
- Rather than running mulitple independent OSes, containers run portions of an OS separate from the kernel
- running portions of OS allows it to allocate resources to specific containers, and each contains a separate portion of the application
- Less overhead since containers don't need to share resources with other applications compared to VMs.

#### VM Sprawl

VM Sprawl is when there are too VMs and they can't be managed.

- VM Sprawl happens when we don't have appropriate policies in place.
- There's a natural tendency not to disrupt production environments
- Easy to lose track of VMs in a large environment
- Having the proper policies will help prevent it

#### VM Escape

- VM escape is when an attack can leave the VM and hit the host OS.
- Most VMs come with built-in escape protection
- The same intrusion detection you use on regular systems should be used on VMs

<!--         ** Physical Controls 3.9**        -->
### Physcial Security Controls

Objectives section 3.9

#### Fire Extinguishers

- Class A: ordinary combustibles like wood, cloth, paper, rubber, plastics
- Class B: flammable liquids
- Class C: electrical
- Class D: combustible metals
- Class K: cooking oils \*mnemonic 'K' is for kitchen

<!-- --------- Identity & Access Managment 4.0 --------------->
## Identity & Access Managment

CompTIA Objective 4.0

### Account Policy Enforcement

- Maps to Sec+ objective 4.4
- **Credential Management:** secure means to store passwords. 
- Microsoft uses **Group Policy Objects (GPOs)** by Microsoft. Local settings managed on enterprise like **password length and complexity requirements**.
- set expiration dates-- useful for employees who leave the company.
- **Account disablement**  This makes auditing easier than deleting an account.
- **Account lockout** best practice to lockout after several unsuccessful entries.
- **Account recovery** usually don't think about it until it's needed. An account recovery plan should be established to verify user and recover account.
- **Password history** don't want password reuse where users recycle passwords that may have been previously compromised. You don't want them to use the same passwords everywhere.

<!-- ------- 5.0 Risk Management ------------------------ -->
## Risk Management

CompTIA objectives 5.0 

- What is CIA?
- Who are the threat actors?
- What are the attributes of threat actors?
- [Define Risk](sec-plus-udemy.md#4-what-is-risk). Look at terms like
  - Assets
  - Vulnerabilities
  - Threats
  - Likelihoods
  - Impact
- What is a [security control](sec-plus-udemy.md#7-security-controls)?
  - [Types of security controls](sec-plus-udemy.md#types-of-security-controls)
  - [Security controls functions](sec-plus-udemy.md#security-controls-functions)

### Business Impact Analysis

 [14. Business Impact Analysis](sec-plus-udemy.md#14-business-impact-analysis-bia)

- BIA is a subset of contingency planning. 
- What are the types of impact?

<!--         *** section 5.2 Agreement Types ***  -->
### Agreement Types

Objectives section 5.2 

[17. Third Party Agreements](sec-plus-udemy.md#17-third-party-agreements)

- **SLA**: If either party is providing service, this breaks down minimum terms of service like uptime, response time, etc..
- **BPA**: should outline roles/responsibilities of partners. 
- **ISA (Interconnection Security Agreement)**: Usually by feds when systems from different entities must connect. This is a technical agreement

#### MOU and MOA

**Memorandum of Understanding** is not a legal document. Broadly describes undestandings, goals and plans.

**Memorandum of Agreement** is a specific document with understandings, goals, plans. **This is a legally binding** contract that both parties must sign.

<!-- *** section 5.3 concepts: Quant & Qual ***  -->
### Assessments

<!--         *** section 5.3 concepts: Quant & Qual ***  -->
#### Quantitative assessements

[13. Quantitative Risk Calculations](sec-plus-udemy.md#13-quantitative-risk-calculations)

- Single Loss Expectancy = AV x EF
- Annualized Rate of Occurrence **(ARO)**
- Annualized Loss Expectancy = SLE x ARO

#### Qualitative assessments 

CompTIA objectives 5.2 BIA concepts include qualitative and quantative

- Qualitative impact calculations:
  - MTBF, MTTF, MTTR
- Calculating downtime: RTO, RPO

<!--          *** Incident Response 5.4 ***           -->
### Incident Response

Objective 5.4 **Incident Response (IR)** is the organized approach to addressing and managing the aftermath of a security breach or cyber attack.

- A plan beforehand is vital.

#### IR Roles

1. Incident Response Team: A specialized group during particular incidents
2. Security Management: Leads the IRT, and provides corporate support for the team
3. Compliance officers: have detailed knowledge of compliance rules.
4. Technical staff: help determine details of cyber incidents.
5. **CIRT**: A predefined group of SME (Subject Matter Experts) you can pull in during incident response procedures.

During an incident is not the time to test and discover what to do. IR needs exercises. One common exercise is a **table top exercise**.

#### Steps of IR

1. Prep
2. ID
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned

<!--      *** Disaster Recovery 5.6 ***    -->
### Disaster Recovery

Objectives section 5.6

#### Recovery Sites

- A **hot site** has everything including data to get back up and running
- **Warm sites** have equipment, but not up to date data and may need other configurations
- **Cold sites** are the cheapest options and is basically just office space.

#### Backups

A **full backup** is everything. A **Snapshot** is a backup of a VM and usually not on different media. An **incremental backup** is from when data has changed from ANY type of backup.  A **differential backup** backs up data starting from the last full backup.

<!--      *** Data security and privacy practices 5.8 ***    -->
### Data security & privacy practices

CompTIA Objective 5.8

#### Types of data

- types of data are public, confidential, and private
- Public
- Proprietary information: includes trade secrets, unique to org's operations
- Confidential information: restrictive access. Usually requires a *Non-Disclosure Agreement* (NDA).

#### Private information

- PHI Personal health information
- PII

#### Data Roles

A **data owner** is accountable and usually a senior management. They own the data, but will appoint a **data steward** or **custodian**.  A **privacy officer** is responsible for the overall data for the ENTIRE organization.

#### Data Retention

- Version control, recover from cyber attacks, legal/regulatory compliance
- Different data types may have different storage requirements
- Data destruction techniques

<!-- ----------------- Cyrpto 6.---------------------------------->
## Cryptography

###  TODO (Organize this section)

- Pinning prevents MitM from forging certs assoc. public key with server
- RC4 is a stream cipher by Rivest
- WPA uses RC4 ciphers and TKIP encryption (temporal key integrity protocol)
- DSA developed by NIST for signatures
- Certs: EV will not cover unknown subdomains, Wildcard will cover
- **stream ciphers** encrypt bit by bit, have low error propagation because of that. It has low diffusion meaning it's ciphertext to plaintext differences are low.
- CBC Cipher Block Chaining XORs 64-bit block chains
- **Stapling** reduces costs to CAs by appending a time-stamped response to every SSL check.
- Cryptography is a **PAIN** privacy, authentication, integrity, non-repudiation
- confusion vs. diffusion, substitution and permutation
- counter mode (CTR) - adds counter to cipher

### Hashing Algorithms

- hashing, message digest
- MD5 has 128 bit output, written by Ron Rivest
- SHA is Secure Hashing Algorithms
- **SHA-0 **and SHA-1 similar to MD5. MD5 and SHA-0 to 1 are deprecated. SHA-2 is composed of SHA-224, 256, 386, and 512. **SHA-256** is the most common
- **HMAC** (Hashed Message Authentication Code): designed to avoid hash collisions. It uses a shared secret key. It's hashed then password protected.

### Symmetric

- DES: 64 bits, but 8 bits are for parity so resulting is 56 bits
- 3DES: DES deprecated in 1998 so 3DES was the stopgap.
  - DES EEE2 two keys, encryption happens 3 times
  - DES EDE2 two keys encrypt, decrypt, encrypt
  - DES EEE3 three
- AES (advanced encryption standard) NIST decided in 2002 by NIST
- RC4 by Rivest. Fast cipher used by WEP. 40 bits in length but paired with 24 bit IV to create a 64 bit WEP

- CTR adds counter
- ECB easy to break
- GCM Galois with counter
- CBC Cipher Block Chain  64 bit, slightly error rate

### Asymmetric Algorithms

1. **Diffie-Hellman**: The first public key-exchange. Users exchanged a secret key over insecure medium. Susceptible to *man-in-the-middle* attacks
2. **RSA** Made in 1977 by Rivest, Shamir, and Adelman. De facto standard. *key size up to 2048 bits*
3. **(DSA)** Digital Signature Algorithm:  for determining integrity, doesn't provide confidentiality. Developed in '91 and adopted by NIST as their Digital Signature Standare in FIPS 186 in 1994
4. **(ECC) Elliptical Curve Cryptosystem**: more secure, uses finite real and rational numbers, very fast, requires smaller keys

### Wireless Cryptography

- WEP uses RC4 for authent and encryption 40 bits in standard, 128 bit for commercial IV (initialization vector). Got breached in 2009 for TJ Maxx, credit cards
- WPA successor to WEP. Also based on RC4, uses TKIP 
  - 256 bit keys
  - per packet key mixing
  - 48 bit IV size
  - backwards compatible
- WPA 2. replaces TKIP with AES Counter, and CBC and CCMP
  - pre-auth means easier roaming
  - only auth network users
- EAP: 
  - EAP-FAST addressed issues in LEAP
  - EAP-TLS is EAP over a tunnel. Security over authentication process
  - PEAP by Cisco, MS, and RSA. Offers encrypted TLS.
- IEEE 802.1X. Devices are
  - 1. supplicant
  - 2. Switch
  - 3. auth server (RADIUIS, TACACS, etc...)

### PKI

- Public Key Infrastructure is a framework
- certs issued by a Cert Auth (CA)
- provides authentication with digital signatures
- confidentiality by encryptions
- non-repudiation:
- Important to know how the keys work. 
  - **CONFIDENTIALITY** If Bob sends a message to Mary, he uses Mary's *public key* to encrypt.  Mary then uses her *private key* to decrypt. No one else can read the messaage 
  - **AUTHENTICATION & NON-REPUDIATION** Bob's private key is used to digitally sign the message.  Mary uses Bob's public key to verify the signature. If anyone else added to the message, it would change the signature.
  - You NEVER send your private key. So any test choices with sending private keys are wrong.
- OCSP (online cert status protocol): status of your cert

#### PKI certificate types

1. Root Cert: Most important
2. User cert: digital ID for the user. "something you have"
3. Web Server SSL Cert 
   1. Domain Validation (DV): CA verifies applicant is validated
   2. Extended (EV): additional, must be legal entity
4. Subject Alternative Name (SAN) Cert: allows multiple domain names
5. Wildcard certs: In case you need more subdomains in the future.
6. Internal Certs:
   1. Self-signed certs: no need to pay a CA because you trust. Put a cert on all your machines

- Cert File Types
  - DER: common with Java platforms
  - PEM Privacy Enhanced Mail: most common, ASCII files
  - PFX: Binary format This is the Windows format of PKCS 12
  - CER: Windows cert type. Only has public key. If you need transfer, use PFX type
  - P7B: only has cert and chain cert, not private key


More info in the [Udemy notes](sec-plus-udemy.md#29-pki)