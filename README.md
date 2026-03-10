# FUTURE_CS_02---Phishing-Email-Detection-Awareness-System
This repository contains a phishing email detection and awareness report created as part of the Cyber Security Task 2 (2026) program. The project analyzes public phishing email samples to identify attack indicators, classify risk levels, and produce actionable guidance for organizations.

## Objectives

- Analyze phishing email samples using passive header inspection techniques
- Identify technical and behavioral indicators of phishing attempts
- Classify email risk using a business-friendly framework (Safe / Suspicious / Phishing)
- Explain attack mechanics in plain language for non-technical stakeholders
- Provide clear prevention guidelines for end users and IT teams

## Scope

### In Scope

- Passive email header analysis (RFC 5322 parsing)
- Authentication validation (SPF, DKIM, DMARC status)
- Domain and IP reputation checks via WHOIS and DNS queries
- Safe URL extraction without clicking or execution
- Risk classification with documented scoring methodology

### Out of Scope

- Active exploitation or system access
- Attachment execution or macro analysis
- Clicking links or browsing to suspicious URLs
- Brute-force, DoS, or any disruptive testing
- Uploading raw samples containing sensitive data to public tools

## Analyzed Samples

| Sample ID | Description | Risk Level |
|-----------|-------------|------------|
| sample-1001.eml | Microsoft account spoof with Russian login alert | **High** |
| sample-1002.eml | Identical template, different Return-Path domain | **High** |
| sample-1005.eml | Portuguese legal notice spoof with partial authentication | **Medium** |


## Tools Used

- **Email Header Analysis:** Manual parsing, Google Message Header Tool, MXToolbox
- **Reputation Checks:** WHOIS, dig, nslookup, VirusTotal (passive)
- **URL Extraction:** grep, awk (read-only, no execution)
- **Documentation:** LaTeX for report generation, GitHub for version control

## Methodology Summary

1. Acquire samples from public, legitimate sources
2. Extract and parse email headers using CLI tools
3. Validate SPF, DKIM, and DMARC authentication results
4. Compare From, Return-Path, and Reply-To addresses for mismatches
5. Review Microsoft anti-spam flags (SCL, BCL, AuthAs)
6. Extract URLs safely and check domain reputation via passive APIs
7. Apply weighted scoring model to classify risk
8. Document findings in a client-ready report with remediation steps

## Key Findings

- All high-risk samples failed SPF and DKIM authentication
- Sender domains spoofed legitimate brands (e.g., access-accsecurity.com mimicking Microsoft)
- Reply-To addresses redirected to attacker-controlled Gmail accounts
- Microsoft Exchange Online Protection flagged samples with SCL >= 5
- Social engineering tactics (urgency, fear) used to prompt impulsive action
