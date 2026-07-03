# Phishing Analysis

**Platform:** TryHackMe  
**Room:** The Greenholt Phish  
**Category:** Phishing Analysis  
**Difficulty:** Beginner

---

## Objective

Analyze and investigate a suspicious email to identify and extract key artifacts, determine its origin and authenticity, and assess the potential maliciousness of the email.

---

## Skills Demonstrated

- Email Header Analysis
- Phishing Investigation
- Attachment Analysis
- Threat Intelligence

---

## Tools Used

- VirusTotal
- `sha256sum`
- WHOIS
- Message Header Analyzer
- SPF Surveyor
- DMARC Inspector

---

## Methodology

My methodology in this lab was to apply the concepts I learned about phishing email analysis.

I started by analyzing the email headers, both manually and using **Message Header Analyzer**, paying particular attention to the **Return-Path**, which appeared suspicious, and to the failed **SPF** validation.

After analyzing the headers and obtaining information about the source IP address using **WHOIS** (which identified the owner as HostPapa), I proceeded with the attachment analysis.

I saved the attachment without opening it, generated its **SHA256** hash using the `sha256sum` command, and submitted it to **VirusTotal**. The analysis confirmed that the attachment was a known Trojan and revealed that its actual file type was a **RAR archive**.

---

## Evidence

### Email Header Analysis

![Email Header](images/email-header.png)

*Description of the evidence.*

---

### Attachment Analysis

![VirusTotal Analysis](images/attachment-analysis.png)

*Description of the evidence.*

---

## Key Takeaways

- Learned how to identify phishing indicators within email headers.
- Understood the importance of verifying suspicious attachments before interacting with them.
- Improved my ability to recognize sender spoofing techniques.

---

## Real-World Relevance

Phishing remains one of the most common initial access techniques used by threat actors.

The ability to analyze suspicious emails, validate email authentication mechanisms, inspect attachments, and identify indicators of compromise (IOCs) is an essential skill for SOC analysts and incident responders.
