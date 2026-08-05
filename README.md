Phishing Email Analysis



A practical SOC analyst training project focused on investigating a simulated

Microsoft 365 credential phishing email.



The project demonstrates the process of reviewing email headers, identifying

social engineering techniques, extracting indicators of compromise, assessing

risk, and recommending incident response actions.



Project objectives



\- Analyze a suspicious email

\- Review sender and destination domains

\- Interpret SPF, DKIM, and DMARC results

\- Extract indicators of compromise

\- Classify the phishing technique

\- Assess incident severity

\- Recommend containment and remediation actions

\- Map the activity to MITRE ATT\&CK



Investigation summary



The analyzed email impersonated Microsoft and claimed that the recipient's

Microsoft 365 account would be suspended within 24 hours.



The email directed the recipient to an external account-verification page.



Several indicators confirmed that the message was malicious:



\- the sender domain was not associated with Microsoft;

\- the embedded URL used a different domain;

\- SPF authentication failed;

\- no DKIM signature was present;

\- DMARC authentication failed;

\- the message used urgency and fear;

\- the email requested account verification through an external link.



Final classification



text

Classification: Credential phishing

Severity: High

Confidence: High

Target: Microsoft 365 credentials

