# PhishScan
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/b53901b6-f8d6-4b2a-82f0-02e0ab14516a" />

PhishScan is a Python-based tool designed to examine emails and URLs for potential phishing threats. It evaluates key elements such as sender reputation, message content, and attachments, while leveraging multiple threat intelligence services to deliver a comprehensive phishing risk assessment.

# Features
Email Header Analysis
- Validates SPF, DKIM, and DMARC authentication results.
- Checks header alignment to identify potential spoofing attempts.
  
Sender Reputation
- Performs WHOIS lookups to gather domain registration details.
- Integrates with VirusTotal and AbuseIPDB to assess domain and IP reputation.

URL Scanning & Analysis
- Scans embedded URLs using VirusTotal, Google Safe Browsing, and IPQualityScore (IPQS).
- Conducts lexical analysis to flag suspicious patterns (e.g., unusual length, special characters, phishing-related keywords, typosquatting).

Content Inspection
- Analyzes both text and HTML email bodies for common phishing keywords and phrases.
- Detects suspicious HTML forms and obfuscation techniques (e.g., hidden elements, JavaScript-based tricks).

Attachment Checking
- Reviews email attachments for high-risk file types and malicious extensions.

Scoring 
- Generates an overall phishing probability score.
- Provides a clear verdict (e.g., Safe, Suspicious, or Phishing).

  
