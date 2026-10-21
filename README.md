# Phishing Email Analysis

A practical SOC analyst investigation of a simulated Microsoft 365 credential-phishing email.

The project demonstrates a basic phishing triage workflow: reviewing the message and headers, identifying authentication failures and social-engineering indicators, extracting indicators of compromise, assessing risk, and documenting recommended response actions.

> All indicators and identities used in this repository are fictional and intended for training purposes.

## Investigation Scenario

A user received an email claiming to come from the Microsoft Security Team.

The message warned that the user's Microsoft 365 account would be suspended within 24 hours unless the recipient verified their identity through an external link.

The investigation focused on determining whether the message was legitimate and documenting the evidence supporting the final verdict.

## Evidence Reviewed

The repository contains:

- `email_body.txt` — simulated suspicious email
- `email_headers.txt` — simulated email headers
- `iocs.txt` — extracted indicators
- `analyst_notes.md` — investigation notes
- `report.md` — final SOC investigation report

## Investigation Workflow

Suspicious Email
↓
Message Review
↓
Header Analysis
↓
Sender / Domain Review
↓
SPF / DKIM / DMARC Review
↓
URL and IOC Extraction
↓
Social Engineering Analysis
↓
Risk Assessment
↓
Final Verdict
↓
Containment / Remediation Recommendations

## Key Findings

The investigation identified several suspicious indicators:

- the sender used `microsoft-support-example.com` rather than an official Microsoft domain;
- the embedded verification link used a separate external domain;
- SPF authentication failed;
- no DKIM signature was present;
- DMARC authentication failed;
- the message used urgency and fear by threatening account suspension;
- the recipient was addressed generically as `Dear User`;
- the message attempted to direct the recipient to an external account-verification page.

## Authentication Results

| Control | Result |
| --- | --- |
| SPF | Fail |
| DKIM | None |
| DMARC | Fail |

Authentication failures alone do not prove that an email is malicious, but in this case they support the broader set of suspicious indicators.

## Extracted Indicators

The investigation identified:

- sender email address;
- sender domain;
- sending hostname;
- source IP address;
- embedded URL;
- URL domain;
- message subject;
- Message-ID;
- email authentication results.

See `iocs.txt` for the extracted values.

## Social Engineering Indicators

The message uses several common phishing techniques:

- urgency;
- fear of account suspension;
- impersonation of a trusted organization;
- generic greeting;
- request for account verification;
- redirection to an external link.

## Final Assessment

Classification: Credential Phishing

Severity: High

Confidence: High

Target: Microsoft 365 credentials

The evidence is consistent with an attempt to direct the recipient to a fake account-verification page and obtain Microsoft 365 credentials.

## Recommended Response

For a real incident, an analyst should consider:

1. isolating or blocking the malicious sender and domains;
2. blocking the identified URL where appropriate;
3. searching mailboxes for similar messages;
4. removing matching phishing messages from affected inboxes;
5. confirming whether any recipient opened the link;
6. determining whether credentials were submitted;
7. resetting affected credentials if compromise is suspected;
8. reviewing sign-in activity for affected accounts;
9. preserving the original message and headers as evidence;
10. documenting the incident and final disposition.

## MITRE ATT&CK Context

The delivery method is consistent with:

- **T1566.002 — Phishing: Spearphishing Link**

The mapping is included as investigation context rather than proof that additional attacker activity occurred.

## Skills Demonstrated

- phishing email triage
- email-header analysis
- SPF, DKIM, and DMARC interpretation
- IOC extraction
- domain and URL analysis
- social-engineering analysis
- incident severity assessment
- security reporting
- containment and remediation planning
- MITRE ATT&CK mapping

## Scope and Limitations

This repository contains a simulated training case rather than a real production incident.

No live malicious infrastructure was contacted, and the project does not demonstrate malware execution, credential collection, or exploitation.

The final verdict is based only on the evidence included in this repository.

## Final Report

See `report.md` for the complete investigation report.
