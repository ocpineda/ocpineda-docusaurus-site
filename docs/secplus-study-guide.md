---
id: study-guide
title: Study Guide
---

## Risk Management

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


### [13. Quantitative Risk Calculations](sec-plus-udemy.md#13-quantitative-risk-calculations)

- Single Loss Expectancy = AV x EF
- Annualized Rate of Occurrence **(ARO)**
- Annualized Loss Expectancy = SLE x ARO

### [14. Business Impact Analysis](sec-plus-udemy.md#14-business-impact-analysis-bia)

- BIA is a subset of contingency planning. 
- What are the types of impact?
- Qualitative impact calculations:
  - MTBF, MTTF, MTTR
- Calculating downtime: RTO, RPO


### [17. Third Party Agreements](sec-plus-udemy.md#17-third-party-agreements)
- SLA
- BPA
- ISA
### Types of Data
- types of data are public, confidential, and private

## Braindump & stuff from other sites.

Everything below this may have come from sources other than Udemy which I currently don't have time to organize. 

Most stuff from Linux Academy's CompTIA Security+ Cert prep from Justin Mitchell.

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


## Staging environments and security implications
  
  - Sandboxing: isolating a system from other hardware, software or networks
  - 4 environments to know: dev, test, stage, prod

## Data security & privacy practices

### Types of data

- Public
- Proprietary information: includes trade secrets, unique to org's operations
- Confidential information: restrictive access. Usually requires a *Non-Disclosure Agreement* (NDA).

### Private information
- PHI Personal health information
- PII

### Data Roles
A **data owner** is accountable and usually a senior management. They own the data, but will appoint a **data steward** or **custodian**.  A **privacy officer** is responsible for the overall data for the ENTIRE organization.

### Data Retention

- Version control, recover from cyber attacks, legal/regulatory compliance
- Different data types may have different storage requirements
- Data destruction techniques

## Hashing Algorithms
- hashing, message digest
- MD5 has 128 bit output, written by Ron Rivest
- SHA-0 and SHA-1 similar to MD5. MD5 and SHA-0 to 1 are deprecated. SHA-2 is composed of SHA-224, 256, 386, and 512. SHA-256 is the most common
- *HMMAC* (Hashed Message Authentication Code): designed to avoid hash collisions. It uses a shared secret key. It's hashed then password protected.

## Asymmetric Algorithms
1. Diffie-Hellman: The first public key-exchange. Users exchanged a secret key over insecure medium. Susceptible to *man-in-the-middle* attacks
2. RSA Made in 1977 by Rivest, Shamir, and Adelman. De facto standard. *key size up to 2048 bits*
3. Digital Signature Algorithm (DSA): for determining integrity, doesn't provide confidentiality. Developed in '91 and adopted by NIST as their Digital Signature Standare in FIPS 186 in 1994
4. Elliptical Curve Cryptosystem: more secure, uses finite real and rational numbers, very fast, requires smaller keys

## PKI
- Public Key Infrastructure is a framework
- certs issued by a Cert Auth (CA)
- provides authentication with digital signatures
- confidentiality by encryptions
- non-repudiation: 
- Important to know how the keys work. 
  - **CONFIDENTIALITY** If Bob sends a message to Mary, he uses Mary's *public key* to encrypt.  Mary then uses her *private key* to decrypt. No one else can read the messaage 
  - **AUTHENTICATION & NON-REPUDIATION** Bob's private key is used to digitally sign the message.  Mary uses Bob's public key to verify the signature. If anyone else added to the message, it would change the signature.
  - You NEVER send your private key. So any test choices with sending private keys are wrong.


## Firewalls

Part of *CompTIA objectives 3.2* secure network architecture. Monitor network traffice, and decides to allow or block. Enforces rules to NAT, packet filtering, ACLs, stateful ACL, or application layer proxies.

### Firewall Techniques

>All firewalls should have **implicit deny**. Rules are read top-down, so implicit deny should be the last rule in the stack.

1. **NAT:** designed to resolve IPv4 shortages and works with IPv6. NAT provides a public IP, and firewalls can be configured to perform NAT
2. **Basic packet filtering**: Only uses packet headers to allow or block.
3. **Access Control Lists (ACLs)** Mostly used in file systems. Often an explicit deny, and read top-down
4. **Application based firewalls** : Allows deeper examination of packets rather than just source and destination addresses like network firewalls. ABFs are good for very sensitive data.  \*Note: ABFs are slower than network firewalls.  
5. **Stateful packet inspections:** Looks deep into state of packet, and can discern to allow or block

## Account Policy Enforcement

- Maps to Sec+ objective 4.4
- **Credential Management:** secure means to store passwords. 
- Microsoft uses **Group Policy Objects (GPOs)** by Microsoft. Local settings managed on enterprise like **password length and complexity requirements**.
- set expiration dates-- useful for employees who leave the company.
- **Account disablement**  This makes auditing easier than deleting an account.
- **Account lockout** best practice to lockout after several unsuccessful entries.
- **Account recovery** usually don't think about it until it's needed. An account recovery plan should be established to verify user and recover account.
- **Password history** don't want password reuse where users recycle passwords that may have been previously compromised. You don't want them to use the same passwords everywhere.