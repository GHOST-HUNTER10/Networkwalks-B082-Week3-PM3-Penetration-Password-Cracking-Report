#  Penetration Testing Report: Password Cracking Assessment

## Week 3 — PM3 | John the Ripper & Networkwalks Tools

<p align="center">

**Password Security Assessment & Dictionary Attack Analysis**

</p>

---

##  PROJECT INFORMATION

| **Field**           | **Details**                                       |
| ------------------- | ------------------------------------------------- |
| **Project**         | Password Cracking with JTR and Networkwalks Tools |
| **Assessment Type** | Password Security / Penetration Testing Lab       |
| **Date**            | August 2026                                       |
| **Name**            | Kovilen Sookalingum                             |
| **Client**          | Networkwalks Academy                              |
| **Environment**     | Kali Linux / Web-Based Security Tools             |
| **Classification**  |  EDUCATIONAL — INTERNAL USE ONLY                |

---

## ⚠️ AUTHORIZATION & ETHICAL USE ⚠️

> **IMPORTANT — AUTHORIZED SECURITY TESTING ONLY**
>
> This repository documents an authorized cybersecurity training exercise conducted within a controlled educational environment.
>
> The techniques, commands, tools, and procedures documented in this repository must only be used against systems, files, accounts, and data for which explicit permission has been obtained.
>
> Unauthorized password cracking, credential testing, or access to protected information may violate applicable laws, regulations, and organizational policies.
>
> **Educational and research purposes only.**

---

#  EXECUTIVE SUMMARY

## Assessment Overview

This penetration testing laboratory assessed the security of password-protected PDF documents using **John the Ripper (JTR)** and **Networkwalks Password Cracker**.

The assessment focused on:

* Extracting password hashes from authorized PDF files
* Performing dictionary-based password attacks
* Evaluating password strength
* Comparing command-line and web-based password-testing tools
* Documenting security weaknesses
* Providing remediation recommendations

The assessment demonstrated that predictable passwords can significantly reduce the effectiveness of password-protected documents.

---

##  Key Findings

| **Finding ID** | **Description**                                            | **Severity** | **Status**  |
| -------------- | ---------------------------------------------------------- | ------------ | ----------- |
| **F-001**      | Weak password `password1` identified                       | 🔴 HIGH      | ✅ Confirmed |
| **F-002**      | Common phrase `good-luck` identified                       | 🔴 HIGH      | ✅ Confirmed |
| **F-003**      | Keyboard pattern `1qaz2wsx` identified                     | 🟡 MEDIUM    | ✅ Confirmed |
| **F-004**      | Password hash extraction demonstrated                      | 🔴 CRITICAL  | ✅ Confirmed |
| **F-005**      | JTR and Networkwalks successfully recovered weak passwords | 🔴 HIGH      | ✅ Confirmed |

---

##  Assessment Results

| **Metric**                 |              **Result** |
| -------------------------- | ----------------------: |
| **Documents Tested**       |                       4 |
| **Passwords Recovered**    |                     4/4 |
| **Recovery Rate**          |                **100%** |
| **Observed Recovery Time** | < 1 second per password |
| **Testing Tools**          |      JTR + Networkwalks |
| **Overall Risk**           |                 🔴 HIGH |

---

#  INTRODUCTION

##  Background

**John the Ripper (JTR)** is a command-line password-security auditing tool used by security professionals to evaluate password strength and identify weak credentials.

The assessment also used the **Networkwalks Password Cracker**, a web-based tool designed to demonstrate dictionary-based password recovery.

The purpose of this laboratory was to demonstrate how weak passwords can be recovered when an attacker obtains password-verification data from a protected document.

---

## Scope

### In-Scope Targets

The assessment covered four authorized password-protected PDF documents:

```text
My.pdf    ---TEST
lock1.pdf --- My Locked PDF1
pdf2.pdf  --- My Locked PDF2
PDF3.pdf  --- My Locked PDF3
```

### Tools Used

* John the Ripper 1.9.0-jumbo-1
* `pdf2john.pl`
* `pdf2john.py`
* `office2john.py`
* RockYou wordlist
* Networkwalks Password Cracker
* Kali Linux

### Assessment Techniques

* Hash extraction
* Hash-format validation
* Dictionary attacks
* Password-pattern analysis
* Rule-based password testing
* Password verification
* Security-impact assessment

---

## Objectives

The objectives of this assessment were:

1. Extract password hashes from authorized PDF files.
2. Test password strength using dictionary attacks.
3. Recover weak passwords where possible.
4. JTR with Networkwalks tools.
5. Document security findings.
6. Evaluate potential impact.
7. Provide remediation recommendations.

---

# METHODOLOGY

## Attack Framework

```text
┌─────────────────────────────────────────────────────────────┐
│                 PHASE 1: RECONNAISSANCE                     │
│                                                             │
│  • Identify authorized PDF files                            │
│  • Verify Kali Linux environment                            │
│  • Verify John the Ripper installation                      │
│  • Locate hash-extraction utilities                        │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                 PHASE 2: HASH EXTRACTION                    │
│                                                             │
│  • Extract PDF password hashes                              │
│  • Validate extracted hash format                          │
│  • Save hashes for authorized testing                      │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                 PHASE 3: PASSWORD TESTING                   │
│                                                             │
│  • Dictionary attacks                                      │
│  • RockYou wordlist                                        │
│  • Password-pattern analysis                               │
│  • Compare JTR and Networkwalks results                    │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                 PHASE 4: VERIFICATION                       │
│                                                             │
│  • Verify recovered passwords                              │
│  • Document results                                        │
│  • Capture screenshots                                     │
│  • Assess security impact                                  │
└─────────────────────────────────────────────────────────────┘
```

---

# ENVIRONMENT & TOOL CONFIGURATION

## John the Ripper

The JTR installation was verified before beginning the assessment.

```bash
john --version
```

Example environment:

```text
John the Ripper 1.9.0-jumbo-1
```

Supported PDF formats were also checked:

```bash
john --list=formats | grep PDF
```

---

## Wordlist

The RockYou wordlist was used for dictionary-based testing:

```text
/usr/share/wordlists/rockyou.txt
```

The wordlist contains commonly used passwords and is frequently used in controlled password-security assessments.

---

## Networkwalks Tools

| **Tool**                      | **Purpose**                       |
| ----------------------------- | --------------------------------- |
| Networkwalks Hash Calculator  | PDF hash extraction               |
| Networkwalks Password Cracker | Dictionary-based password testing |
| Networkwalks Academy Portal (https://Networkwalks.com) | Educational resources             |

---

# FINDINGS & EVIDENCE

# 🔴 F-001 — Weak Password `password1`

**Severity:** HIGH
**Status:** ✅ Confirmed

## Description

The password:

```text
password1
```

was successfully recovered from an authorized test document.

The password consists of a common dictionary word combined with a simple numerical suffix, making it highly predictable.

---

## Evidence

Hash extraction:

```bash
perl /usr/share/john/pdf2john.pl My.pdf > hash_pdf.txt
```

Dictionary testing:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash_pdf.txt
```

The password was successfully recovered during the authorized laboratory exercise.

---

## Impact

Potential impact of using passwords of this type includes:

* Unauthorized document access
* Exposure of confidential information
* Increased risk of password reuse
* Low resistance to dictionary attacks

---

## Recommendation

Immediately replace weak passwords with strong, unique passphrases.

Recommended characteristics:

* 12+ characters
* Multiple character types
* No common dictionary words
* No predictable patterns
* No personal information
* No password reuse

---

# 🔴 F-002 — Common Phrase `good-luck`

**Severity:** HIGH
**Status:** ✅ Confirmed

## Description

The authorized document `lock1.pdf` was protected using the phrase:

```text
good-luck
```

Although longer than a single short word, the phrase is predictable and may appear in common password dictionaries.

---

## Evidence

Hash extraction was performed using the available JTR extraction utility.

The recovered password was:

```text
good-luck
```

---

## Impact

Potential risks include:

* Dictionary-based recovery
* Predictable password guessing
* Social-engineering-assisted guessing
* Password reuse exposure

---

## Recommendation

Use long, unique, randomly generated passwords or passphrases rather than common expressions.

---

# 🟡 F-003 — Keyboard Pattern `1qaz2wsx`

**Severity:** MEDIUM
**Status:** ✅ Confirmed

## Description

The authorized document `PDF3.pdf` used:

```text
1qaz2wsx
```

This is a recognizable keyboard pattern and is therefore predictable.

---

## Impact

Keyboard-pattern passwords can be included in password dictionaries and specialized pattern-based password lists.

Potential risks include:

* Predictable password structure
* Fast dictionary recovery
* User habit exploitation
* Increased password-guessing success

---

## Recommendation

Organizations should prevent the use of:

* Keyboard sequences
* Sequential numbers
* Repeated characters
* Common password patterns

---

# 🔴 F-004 — Password Hash Extraction

**Severity:** CRITICAL
**Status:** ✅ Confirmed

## Description

The assessment demonstrated that password-protected PDF files can contain password-verification information that can be extracted into a format suitable for offline password testing.

Example:

```bash
perl /usr/share/john/pdf2john.pl My.pdf > hash.txt
```

The resulting data can then be supplied to an authorized password-testing process.

---

## Security Impact

Potential consequences include:

* Offline password testing
* Reduced detection opportunities
* Faster password evaluation
* Increased risk when weak passwords are used

---

## Recommendation

Organizations should:

* Use strong passwords
* Use modern document encryption
* Apply additional access controls
* Protect sensitive documents using appropriate information-protection solutions
* Restrict access to protected files
* Monitor access to sensitive information

---

# 🔴 F-005 — Tool Comparison

**Severity:** HIGH
**Status:** ✅ Confirmed

The assessment compared two password-testing approaches:

* John the Ripper
* Networkwalks Password Cracker

| **Feature**          | **John the Ripper** | **Networkwalks** |
| -------------------- | ------------------- | ---------------- |
| Installation         | Required            | None             |
| Interface            | CLI                 | Web              |
| Learning Curve       | Medium/High         | Low              |
| Speed                | Fast                | Moderate         |
| Control              | High                | Limited          |
| Wordlist Flexibility | High                | Moderate         |
| Automation           | High                | Limited          |
| Platform             | Linux               | Browser          |
| Visual Feedback      | Limited             | Excellent        |

---

# PASSWORD SECURITY ANALYSIS

## Weak Password Examples

The assessment demonstrated the risks associated with passwords such as:

```text
password1
good-luck
1qaz2wsx
12345678
qwerty
```

These examples demonstrate several common password weaknesses:

* Dictionary words
* Common phrases
* Keyboard patterns
* Sequential numbers
* Predictable structures

---

## Strong Password Characteristics

A strong password should:

```text
✓ Be long
✓ Be unique
✓ Avoid dictionary words
✓ Avoid keyboard patterns
✓ Avoid personal information
✓ Avoid password reuse
✓ Resist common password dictionaries
```

For real systems, randomly generated passwords stored in a reputable password manager are preferred.

---

# RISK ASSESSMENT

| **Finding**               | **Severity** | **Likelihood** | **Potential Impact** |
| ------------------------- | ------------ | -------------- | -------------------- |
| Weak dictionary passwords | 🔴 HIGH      | High           | High                 |
| Common phrases            | 🔴 HIGH      | High           | High                 |
| Keyboard patterns         | 🟡 MEDIUM    | High           | Medium               |
| Hash extraction           | 🔴 CRITICAL  | Medium/High    | High                 |
| Weak-password wordlists   | 🔴 HIGH      | High           | High                 |

## Overall Risk

# 🔴 HIGH

The overall assessment risk is classified as **HIGH** because all four authorized test documents were successfully evaluated and passwords were recovered.

---

# RECOMMENDATIONS

## Immediate Actions

| **Priority** | **Recommendation**                       | **Timeline** |
| ------------ | ---------------------------------------- | ------------ |
| 🔴 HIGH      | Replace weak passwords                   | Immediate    |
| 🔴 HIGH      | Audit password-protected documents       | 48 hours     |
| 🔴 HIGH      | Implement strong password requirements   | 24 hours     |
| 🔴 HIGH      | Block commonly compromised passwords     | Immediate    |
| 🟠 MEDIUM    | Security-awareness training              | 1 week       |
| 🟠 MEDIUM    | Review document-encryption configuration | 1 week       |

---

## Password Policy

Recommended controls:

```text
Minimum Length:          12+ characters
Common Passwords:        Block
Dictionary Words:        Block
Keyboard Patterns:       Block
Personal Information:    Block
Password Reuse:          Block
Known Breached Passwords: Block
MFA:                     Enable where available
Password Manager:        Recommended
```

---

## Additional Security Controls

Organizations should consider:

### Authentication

* Multi-factor authentication
* Password managers
* Strong password policies
* Compromised-password screening

### Monitoring

* Authentication logging
* Failed-login monitoring
* Security-event alerting
* Periodic access reviews

### Document Security

* Strong encryption
* Restricted permissions
* Secure document sharing
* Access logging
* Data classification
* Least-privilege access

---

# LAB EVIDENCE & SCREENSHOTS


## Phase 1 — Environment & Tool Setup

| **Screenshot** | **Description**                                |
| -------------- | ---------------------------------------------- |
| <img src="EVIDENCE/W3-PM3/p1.jpeg" alt="Evidence p1" width="450"/>
     | Kali Linux virtual-machine environment         |
| `p2(1).jpeg`   | John the Ripper installation/help verification |

---

## Phase 2 — Hash Extraction

| **Screenshot** | **Description**                      |
| -------------- | ------------------------------------ |
| `p3(1).jpeg`   | PDF hash extraction using `pdf2john` |
| `p4.jpeg`      | Extracted `$pdf$` hash               |
| `L1(1).jpeg`   | Locating PDF extraction utilities    |
| `L2(1).jpeg`   | Troubleshooting extraction           |
| `L3(1).jpeg`   | `office2john.py` extraction          |
| `L11.jpeg`     | Verification of extraction utility   |
| `L22.jpeg`     | Extracted `pdf2.pdf` hash            |
| `L34.jpeg`     | `PDF3.pdf` hash extraction           |

---

## Phase 3 — Password Testing

| **Screenshot** | **Description**                       |
| -------------- | ------------------------------------- |
| `p5(1).jpeg`   | JTR dictionary-testing session        |
| `p7.jpeg`      | Networkwalks Password Cracker         |
| `L33(1).jpeg`  | Networkwalks password-recovery result |
| `L33.jpeg`     | PDF3 password-recovery result         |

---

## Phase 4 — Verification

| **Screenshot** | **Description**                   |
| -------------- | --------------------------------- |
| `p6(1).jpeg`   | Flag/result verification          |
| `L4(2).jpeg`   | Second verification result        |
| `L44(1).jpeg`  | Third verification result         |
| `L31(1).jpeg`  | Final verification                |
| `L32.jpeg`     | Alternate final-result screenshot |

---


# TOOL USAGE GUIDE

## Verify JTR

```bash
john --version
```

## List Supported Formats

```bash
john --list=formats
```

## Extract PDF Hash

```bash
perl /usr/share/john/pdf2john.pl document.pdf > hash.txt
```

## Extract Using Python Utility

```bash
python3 /usr/share/john/pdf2john.py document.pdf > hash.txt
```

## Dictionary Testing

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

## Display Results

```bash
john --show hash.txt
```

> **All commands above are intended only for authorized laboratory files and security assessments.**

---

# LESSONS LEARNED

The assessment demonstrated several important cybersecurity principles:

1. Weak passwords can undermine otherwise protected documents.
2. Common dictionary passwords provide limited security.
3. Keyboard patterns are predictable.
4. Password hashes may be suitable for offline testing when obtained by an attacker.
5. Strong encryption should be combined with strong authentication practices.
6. Password policies should prevent common and compromised passwords.
7. Security assessments can identify weaknesses before they are exploited.

---

# CONCLUSION

The Week 3 password-security assessment successfully demonstrated the risks associated with weak and predictable passwords.

A total of **four authorized PDF documents** were tested, with passwords successfully recovered from **4/4 documents** in the laboratory environment.

The results demonstrate that password-protected documents should not rely on:

* Common dictionary words
* Short phrases
* Keyboard patterns
* Reused passwords
* Predictable numerical combinations

The most important remediation is to implement strong, unique passwords and additional security controls such as multi-factor authentication, secure document access controls, and compromised-password screening.

---

# GLOSSARY

| **Term**              | **Definition**                                                                       |
| --------------------- | ------------------------------------------------------------------------------------ |
| **Hash**              | A cryptographic representation used for verification or password-processing purposes |
| **Dictionary Attack** | Password testing using a list of likely passwords                                    |
| **Wordlist**          | A file containing potential password candidates                                      |
| **Salt**              | Random data incorporated into password-processing mechanisms                         |
| **Password Cracking** | Attempting to recover a password from password-verification data                     |
| **Brute Force**       | Testing possible character combinations systematically                               |
| **Rule-Based Attack** | Applying transformations to wordlist entries                                         |
| **JTR**               | John the Ripper, a password-security auditing tool                                   |
| **MFA**               | Multi-Factor Authentication                                                          |

---

---

#  CLASSIFICATION

**Document Classification:**  EDUCATIONAL — INTERNAL USE ONLY

**Distribution:** Authorized personnel only

---

<p align="center">

###  END OF REPORT

**Cybersecurity Training & Authorized Security Assessment**

</p>
