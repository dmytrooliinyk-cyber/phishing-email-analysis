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

```text
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
