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

  # How PhishScan Works
Input: Accepts either an email file (e.g., .eml) or a direct URL.
- Extraction & Parsing: Pulls out key elements — headers, body, and attachments from emails; URL components from links.
- Analysis Modules: Runs each module (header checks, URL scans, content analysis, etc.) on the extracted data.
- API Integration: Connects to external threat intelligence services (such as VirusTotal and AbuseIPDB) to gather the latest threat information.
- Scoring Algorithm: Combines results from all modules using a weighted scoring system.
- Output: Produces a clear report summarizing individual checks, the overall score, and the final verdict.- **Input**: Accepts either an email file (e.g., .eml) or a direct URL.
- Extraction & Parsing: Pulls out key elements — headers, body, and attachments from emails; URL components from links.
- **Analysis Modules**: Runs each module (header checks, URL scans, content analysis, etc.) on the extracted data.
- API Integration: Connects to external threat intelligence services (such as VirusTotal and AbuseIPDB) to gather the latest threat information.
- Scoring Algorithm: Combines results from all modules using a weighted scoring system.
- Output: Produces a clear report summarizing individual checks, the overall score, and the final verdict.

# Setup Guide
1- Clone the Repository:

```bash
git clone https://github.com/ShabanMSoltan/PhishScan.git
cd PhishScan
```
2- Create and Activate a Virtual Environment (Recommended):

-Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```
-Windows:
```bash
python -m venv venv
venv\Scripts\activate
```
3- Install Dependencies: Make sure your repository includes a requirements.txt file. If it doesn’t, you can generate one after installing the packages manually during development.
```bash
# First time setup or if requirements.txt is missing
pip install requests beautifulsoup4 dnspython python-whois tabulate html5lib
pip freeze > requirements.txt # To generate the file for others

# If requirements.txt is already present
pip install -r requirements.txt
```

2ز
2ز


