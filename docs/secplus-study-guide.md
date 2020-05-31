---
id: study-guide
title: Study Guide
---

Follow the ComptTIA Objectives listed [here](https://gitlab.com/oscarneedscoffee/notes/-/blob/master/software/security/security-plus/udemy-course/CompTIA-Security-SY0-501.pdf)

## Braindump and Review.

Source material came from [Udemy](sec-plus-udemy.md), and Linux Academy's CompTIA Security+ Cert prep from Justin Mitchell.

- RSA is the de facto standard and key size is up to 2,048 bits
- DSA Digital Signing Algorithm developed in 1991 adopted by NIST as FIPS 186 in 1994 
- CIRT Cyber Incident Response Team
- MD5 is 128 bits, SHA-256 is 256 bits, [HMMAC](#hashing-algorithms)
- [Asymmetric algorithms](#asymmetric-algorithms): 
  - Diffie-Helman, 
  - RSA 2048 bits
  - DSA: Adopted by NIST for digital signature standard 
  - Elliptical Curve Cryptosystem
- [PKI](#pki)
- Know [RAID Levels](#raid)


<!-- ------------- Types of Attacks 1.2---------------------------->
## Types of Attacks

CompTIA Objects 1.2

### Malware

Malware is malicious software. Types are **polymorphic, virus, armored virus, worms, Trojans, and crypto-malware, keyloggers, adware, spyware, bots, RATs, logic bombs, backdoor**. Ransomware is crypto-malware but the threat actors want money in exchange for an encryption key

- RAT (Remote Access Trojan): toolkit to gain access to target
- Backdoor

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
  - Input validation mitigates attacks suck as: buffer overflows, XSS, CSRF/XSRF, and injection attacks
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
- **Verification** is ensuring what the code is supposed to do. Ensure system meets design requirements and meets needs of the customer.
- **Model verification**
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

### Agreement types

[17. Third Party Agreements](sec-plus-udemy.md#17-third-party-agreements)

- SLA
- BPA
- ISA

<!--         *** section 5.3 concepts: Quant & Qual ***  -->
### Assessments

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

### Hashing Algorithms

- hashing, message digest
- MD5 has 128 bit output, written by Ron Rivest
- SHA-0 and SHA-1 similar to MD5. MD5 and SHA-0 to 1 are deprecated. SHA-2 is composed of SHA-224, 256, 386, and 512. SHA-256 is the most common
- *HMMAC* (Hashed Message Authentication Code): designed to avoid hash collisions. It uses a shared secret key. It's hashed then password protected.

### Asymmetric Algorithms

1. Diffie-Hellman: The first public key-exchange. Users exchanged a secret key over insecure medium. Susceptible to *man-in-the-middle* attacks
2. RSA Made in 1977 by Rivest, Shamir, and Adelman. De facto standard. *key size up to 2048 bits*
3. Digital Signature Algorithm (DSA): for determining integrity, doesn't provide confidentiality. Developed in '91 and adopted by NIST as their Digital Signature Standare in FIPS 186 in 1994
4. Elliptical Curve Cryptosystem: more secure, uses finite real and rational numbers, very fast, requires smaller keys

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

More info in the [Udemy notes](sec-plus-udemy.md#29-pki)