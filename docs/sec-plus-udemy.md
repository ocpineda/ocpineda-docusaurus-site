---
id: udemy-comptia
title: Udemy Notes
---

import useBaseUrl from '@docusaurus/useBaseUrl';

CompTIA Security+ SY0-501 lecture notes from Udemy

These are notes from Mike Meyer's [Udemy course](https://www.udemy.com/course/comptia-security-certification-sy0-501-the-total-course/)

## TODO

- [ ] Review examples in BIA example "Identify Resource Requirements" in Myers' CompTIA cert book
- [ ] Review PKI
- [ ] Check out wrong answers in Linux Academy

## Resources

- Source for original [MD notes](https://gitlab.com/oscarneedscoffee/notes/-/tree/master/software/security)
- [Study guide](secplus-study-guide.md)
- [CompTIA Sec+ Objectives](https://gitlab.com/oscarneedscoffee/notes/-/blob/master/software/security/security-plus/udemy-course/CompTIA-Security-SY0-501.pdf)


## Section 1: Risk Management

### 1. INTRODUCTION 

Curriculum [here](udemy-course/CompTIA-Security-SY0-501.pdf)

### 2. CIA

Confidentiality, Integrity, and Availability.   
- Is your info private?
- Can I trust this info? 
- Can I get my info when I need it?

These form the CIA triad. Meyers feels CIA isn't enough. He also addes *auditing & accountability* and *non-repudiation*

<img src={useBaseUrl('img/cia.jpg')} width="300px" />  

Accounting & auditing helps you keep track of issues. Non-repudiation ensures the receiver cannot deny receiving the message.

### 3. THREAT ACTORS

Threat actors have attributes such as
- internal or external threats
- Level of sophistication
- Intent or motivation
- Use of open source intelligence [(OSINT)](../sec-definitions.md#open-source-intelligence)

The types of threat actors are:
1. Script kiddies
2. Hacktavists
3. Organized crime-- money motivated
4. Nation states.  
5. Insiders.  

**Nation states** are the biggest threat because of greater resources. This TA goes for [*Advanced Persistent Threats (APT)*](../sec-definitions.md#advanced-persistent-threat). **Insiders** are not only employees, but can be vendors, cleaning staff, contractors, etc... This is anyone who has access to your resources in any way.

### 4. WHAT IS RISK?

Risk is _potential for harm_. To understand risk, you need some key terms. 
- **Assets** are the parts that you are worried about. They can be people, doors, paperwork, doors, or even intangibles such as reputation.
- **Vulnerabilities** are weaknesses to your assets that may cause harm
- **Threats** are the negative events that exploit a vulnerability
- **Likelihood** is the level of certainty that something bad will happen
- **Impact** is the actual harm when threats and vulnerabilities are exploited.

A threat is enacted by a *threat agent*. This is usually a person, but can be an entity such as a hurricane, virus, act of God, etc...  The __impact__ of a risk can be evaluated quantitatively or qualitatively. Impact is usually considered on an annual bases e.g. _"How many times a year will my network fail"_.  

Risk is often considered by this formula:  
`threats --> vulnerabilities = risk`  
If you don't have threats and vulnerabilities, you have no risk. [NIST](../sec-definitions.md#nist) has a list of threats in their publication [SP 800-30](https://csrc.nist.gov/publications/detail/sp/800-30/rev-1/final)


### 5. Managing Risk

Check out the [Common Vulnerabilities and Exposures database](https://cve.mitre.org)

### 7. Using Guides for Risk Assessment

- benchmark 


---

### 7. Security Controls

A mechanism to protect our IT infrastructue, or to remediate problems we have. What separates security engineer from IT is a security engineer understands, applies, and implements security controls.

Security controls don’t say how to perform the steps needed to mitigate a threat, only that they must be performed

There are thousands of controls you have to implement. You do it with a RMF (Risk Management Framework).

#### Types of Security Controls

1. Administrative
2. Technical
3. Pysical

#### Security Controls Functions

- Deterrent
- Preventive
- Detective
- Corrective
- Compensating: Alternative or temporary fix when we can't do what we want.

*For the exam, be comfortable applying type and function of a control*

### Best practice

A standard is a ruleset voluntarily adopted by an industry to provide more uniform products and services

A **security policy** is a document that organizations generate to declare what actions and attitudes they will take for certain critical aspects of their infrastructure. 

- Acceptable use

enterprise information security architecture (EISA)
- The EISA analyzes security systems in place. 
- It encompasses industry-standard frameworks, such as the NIST RMF discussed previously. 
- The EISA accounts for regulatory and non-regulatory influences—laws and standard operating procedures—and how compliance manifests. That includes national and international laws and practices.

Activity Phase Controls
The phases are before, during, and after an attack. 

Deterrent controls
> You need to know five phase control types for both essential skills and the CompTIA Security+ exam: deterrent, preventative, detective, corrective, and compensating

Defective applied during an attack. IDS is an example. 

Corrective is applied after an attack. 

Compensating You use compensating controls to keep going until a better control is available or possible

#### Standards
A standard is a ruleset voluntarily adopted by an industry to provide more uniform products and services  

PCI-DSS

---


### 12. Frameworks

A framework is a description of a complex process, concentrating on major steps and the flows between the stops. In security, the framework used is a *risk management framework (RMF)*  NIST is a popular RMF

A framework is a project idea and come from various sources:

- Regulatory
- Non-regulatory: ISACA IT infrastructure
- National Standards
- International Standards: ISO 2700
- Industry specific

NIST SP800-37: Risk Management Framework
<img src={useBaseUrl('img/NIST-SP800-37.png')} />  


#### Laws

- HIPAA *Health Insurance Portability and Accountability Act* privacy and security for medical information. Who has access to records, and how to store it.
- SOX Sarbanes-Oxley of 2002. Requires businesses to retain records for specific time periods.


---

### 13. Quantitative Risk Calculations

Single Loss Expectancy  
`SLE = AV (Asset Value) x EF (Exposure Factor)`

ARO Annualized Rate of Occurrence: The number of times bad thing will occur  

ALE Annualized Loss Expectantcy:
`ALE = SLE x ARO`

Qualitative Risk Assessment: relies on descriptive elements  

#### Risk Response Techniques:

1. Mitigate
2. Transfer aka Risk Sharing. ex: buying insurance
3. Accept: This is not ignoring the risk. You implemented controls and risk remains
4. Avoid the risk. Again, you are not ignoring risk 

### 14. Business Impact Analysis (BIA)

> A business impact analysis is designed to mitigate the effects of an incident, not to prevent an incident.

#### NIST SP 800-34 Revision 1 *"Contingency Planning Guide for Federal Information Systems"*

1. Determine mission/business processes and recovery criticality.
2. Identify resource requirements.
3. Identify recovery priorities for system resources.

BIA is a subset of *contingency planning (CP)*

#### Types of Impact

- Financial
- Reputation
- Property
- Safety/life
- privacy
  - privacy threshold assessment (PTA)
  - privacy impact assessment (PIA)

#### Calculating Impact

The Sec+ exam only touches on qualitative measurements.  MTBF, MTTF, and MTTR.

1. MTBF Mean Time between Failures: usually for hardware. This means device will be repaired, not replaced.
2. MTTF Mean Time to Failure: The length of time a device is expected to last in operation. Device will be replaced
3. MTTR Mean Time to Recovery: The amount of time for hardware to recover from failure.

#### Calculating Downtime

1. RTO *Recovery Time Objective*: The max time a resource may remain unavailable before an unacceptable impact on other resources.
2. RPO *Recovery Point Objective*: The amount of time that will pass between an incident and recovery from backup. ex: if you backed up yesterday, the RPO is 24 hours

### 15. Organizing Data

in Myers book see *MODULE 1-6: DATA SECURITY AND PRIVACY POLICIES*

Types of Data:  

- Public 
- Confidential: Limited to authorized viewing as agreed by parties involved
- Private: 





### 17. Third Party Agreements

- SLA: Legal document to specify what a third party will guarantee to the organization
- BPA: When two businesses get together
- ISA: Interconnection Security Agreement. Not a legal document, but technical. Usually used in telecom and between government agencies.
- MOA (Memorandum of Agreement): Legal document with terms and details of agreement





## Section 2: Cryptography

[See study guide](secplus-study-guide.md#cryptography)
- Module 6 in CompTIA objectives

### 29. PKI

[More in study guide](secplus-study-guide.md#pki)

- PKI uses symmetric and asymmetric algorithms, and hashing.
- Symmetric algorithms are fast, but don't scale well. Asymmetric isn't fast, and doesn't encrypt large amounts of data as well.
- Asymmetric systems use private and public key pairs. You don't send your private key.


To exchange messages between two parties, each party must have each other's public keys.

<img src={useBaseUrl('img/asymm-keys.jpg')} />  

