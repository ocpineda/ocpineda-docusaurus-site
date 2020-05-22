---
id: udemy-comptia
title: CompTia Security + Exam
---

import useBaseUrl from '@docusaurus/useBaseUrl';

# CompTIA Security+ SY0-501 from Udemy

These are notes from Mike Meyer's [Udemy course](https://www.udemy.com/course/comptia-security-certification-sy0-501-the-total-course/)

## Risk Management

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

---

### 7. Security Controls

A mechanism to protect our IT infrastructue, or to remediate problems we have. What separates security engineer from IT is a security engineer understands, applies, and implements security controls.

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

---

### 12. Frameworks

A framework is a project idea and come from various sources:

- Regulartory
- Non-regulatory: ISACA IT infrastructure
- National Standards
- International Standards: ISO 2700
- Industry specific

NIST SP800-37: Risk Management Framework
<img src={useBaseUrl('img/NIST-SP800-37.png')} />  

Auth is an important process when defining


### 13. Quantitative Risk Calculations

Single Loss Expectancy  
`SLE = AV (Asset Value) x EF (Exposure Factor)`

ARO Annualized Rate of Occurrence: The number of times bad thing will occur  

ALE Annualized Loss Expectantcy:
`ALE = SELE x ARO`

Qualitative Risk Assessment: relies on descriptive elements  


#### Risk Response Techniques:

1. Mitigate
2. Transfer aka Risk Sharing. ex: buying insurance
3. Accept: This is not ignoring the risk. You implemented controls and risk remains
4. Avoid the risk. Again, you are not ignoring risk 