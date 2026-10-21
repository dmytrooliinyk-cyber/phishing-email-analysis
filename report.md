# Phishing Email Investigation Report

## Executive Summary

A simulated suspicious email impersonating the Microsoft Security Team was analyzed as part of a SOC investigation exercise.

The message claimed that the recipient's Microsoft 365 account would be suspended within 24 hours unless identity verification was completed through an external link.

Review of the message body, sender information, authentication results, and embedded URL identified multiple indicators consistent with credential phishing.

## Final Verdict

Classification: Credential Phishing

Severity: High

Confidence: High

Target: Microsoft 365 credentials

## Evidence Reviewed

The investigation used the following repository artifacts:

- `email_body.txt`
- `email_headers.txt`
- `iocs.txt`
- `analyst_notes.md`

No external or live malicious infrastructure was required for the analysis.

## Email Details

Sender:

Microsoft Security Team <security-alert@microsoft-support-example.com>

Recipient:

employee@example.com

Subject:

URGENT: Your Microsoft 365 account will be suspended

Embedded URL:

https://microsoft-account-verification.example.com/login

## Header Analysis

The supplied headers contain the following authentication results:

| Control | Result |
| --- | --- |
| SPF | Fail |
| DKIM | None |
| DMARC | Fail |

Additional header information:

- Source IP: `192.0.2.45`
- Sending host: `mail.microsoft-support-example.com`
- Mailer: `PHP/8.2`

The sender domain does not match an official Microsoft domain.

The authentication failures are considered supporting evidence alongside the suspicious sender identity, URL, and message content.

## Sender Analysis

The message presents itself as an official Microsoft security notification.

However, the sender uses:

`microsoft-support-example.com`

rather than an official Microsoft domain.

This mismatch is a strong indicator that the displayed identity should not be trusted.

## URL Analysis

The message attempts to redirect the recipient to:

`https://microsoft-account-verification.example.com/login`

The domain is separate from the sender domain and is not an official Microsoft domain.

The wording of the URL attempts to appear related to Microsoft account verification.

Within the context of the supplied evidence, the link is considered suspicious and consistent with a credential-phishing workflow.

## Social Engineering Analysis

The email uses several techniques intended to pressure the recipient into acting quickly.

### Urgency

The recipient is told that verification must occur within 24 hours.

### Fear

The message threatens account suspension and loss of access to Microsoft 365 services.

### Authority Impersonation

The sender claims to represent Microsoft's security department.

### Generic Greeting

The message begins with:

`Dear User`

rather than identifying the recipient.

### Account Verification Request

The recipient is instructed to verify their identity through an external link.

Together, these techniques are consistent with a phishing attempt designed to reduce scrutiny and encourage immediate action.

## Indicators of Compromise

| Type | Indicator |
| --- | --- |
| Sender email | `security-alert@microsoft-support-example.com` |
| Sender domain | `microsoft-support-example.com` |
| Sending host | `mail.microsoft-support-example.com` |
| Source IP | `192.0.2.45` |
| URL | `hxxps://microsoft-account-verification[.]example[.]com/login` |
| URL domain | `microsoft-account-verification.example.com` |
| Subject | `URGENT: Your Microsoft 365 account will be suspended` |
| Message-ID | `20260805091358.12345@microsoft-support-example.com` |
| SPF | Fail |
| DKIM | None |
| DMARC | Fail |

## Suspected Objective

The likely objective is theft of Microsoft 365 credentials.

The email attempts to convince the recipient to open an external account-verification page while presenting the request as an urgent Microsoft security action.

The supplied evidence does not show whether a recipient actually entered credentials.

## Potential Impact

If credentials were submitted to a malicious page, potential consequences could include:

- Microsoft 365 account takeover;
- unauthorized mailbox access;
- access to cloud-stored organizational data;
- use of the compromised account for additional phishing;
- unauthorized access to resources available to the affected account.

These are potential consequences rather than confirmed outcomes in this simulated case.

## MITRE ATT&CK Mapping

The observed delivery method is consistent with:

- T1566.002 — Phishing: Spearphishing Link

This mapping describes the observed phishing delivery technique only.

The evidence in this repository does not establish later-stage attacker activity.

## Recommended Containment

For an equivalent real-world incident:

1. block confirmed malicious sender addresses and domains where appropriate;
2. block the phishing URL through available security controls;
3. identify other recipients of the same or similar message;
4. remove matching phishing emails from affected mailboxes;
5. warn users who received or interacted with the message.

## Recommended Investigation

Analysts should determine:

- whether any user opened the URL;
- whether credentials were submitted;
- whether unusual Microsoft 365 sign-ins followed the email;
- whether mailbox rules were created or modified;
- whether additional phishing messages were sent from affected accounts;
- whether other organizational resources were accessed.

## Recommended Remediation

If credential compromise is suspected or confirmed:

1. reset the affected password;
2. revoke active sessions where appropriate;
3. review authentication activity;
4. review mailbox configuration and forwarding rules;
5. verify multi-factor authentication configuration;
6. review access to connected organizational resources;
7. continue monitoring the affected account.

## Evidence Preservation

For a real investigation, preserve:

- the original email;
- full email headers;
- mailbox metadata;
- relevant authentication logs;
- URL and domain indicators;
- analyst notes;
- investigation timeline;
- containment and remediation actions.

## Conclusion

The supplied evidence is consistent with a Microsoft 365 credential-phishing email.

The combination of sender-domain mismatch, external account-verification link, failed SPF and DMARC checks, absent DKIM signature, urgent language, authority impersonation, and credential-verification request supports a High-confidence Credential Phishing classification.

This repository represents a simulated training investigation and does not contain evidence of a real compromised account.
