---
id: cissp-study-guide
title: CISSP course from Linux Academy
---

## About

CISSP course from Linux Academy. The instructor is Ermin Kreponic.

## Stuff I do not know

## Security Governance

### CIA triad

- **Confidentiality**: secrecy, ensures only people who have access have it.
  - Confidentiality controls are:
    - encryption
    - access control
    - steganography
  - Causes of unintentional data disclosures
    - human error
    - oversight
    - ineptitude.
  - Violation of confidentiality attacks
    - capturing network traffic
    - stealing password files
    - *social engineering* this is the one corporations are most susceptible to
    - port scanning
    - shoulder surfing
    - eavesdropping
    - sniffing
    - escalation of privileges.
  - Countermeasures to ensure confidentiality
    - Encryption
    - Network traffic padding
    - Rigorous access control
    - strict authentication process
    - Data classification
    - Personnel training
  - Confidentiality also entails:
    - **Sensitivity**: The importance of data. What's the potential for harm?
    - **Discretion**: preventing or minimizing the harm of disclosure of information
    - **Criticality**: Describe how important the information is.
    - **Concealment**: Hiding information
    - **Secrecy**: describes the prevention of information
    - **Privacy**: Keeping PII confidential especially if the disclosure could harm.
    - **Seclusion**: Don't store information where it can be reached easy. Store info in an out-of-way location
    - **Isolate**: keep the data separated from each other.
- **Integrity**: ensures the data is not altered. This is why we use hashing.
  - Involves preventing intentional unauthorized modification of any kind.
  - Setting up access controls and logging to track who is attempting to access data
  - Ensures data is:
    - Unaltered
    - Preserved
    - Correct
  - Integrity violation attacks
    - Malware
    - Reverse shells or backdoors
    - vulnerable code
    - human error
  - Countermeasure to integrity attacks
    - IDS
    - hash sum checks
    - mandatory security awareness training.