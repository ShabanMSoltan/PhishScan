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
🔑 **API Key Configuration (Important)**

This tool relies on external security services that require valid API keys.  
**Do NOT hard-code API keys inside the script.**  
All keys must be added as **environment variables**, and the script will automatically load them using:

```python
os.environ.get("API_KEY_NAME")
```

**Required Environment Variables:**

- `VIRUSTOTAL_API_KEY` — API key for VirusTotal  
- `ABUSEIPDB_API_KEY` — API key for AbuseIPDB  
- `GOOGLE_SAFE_BROWSE_API_KEY` — API key for Google Safe Browsing (ensure you're using the correct API, e.g., Web Risk API)  
- `IPQS_API_KEY` — API key for IPQualityScore
### 🔧 Setting Environment Variables

#### **Linux / macOS (bash/zsh)**  
To configure your API keys on Linux or macOS, open your shell configuration file (such as `~/.bashrc` or `~/.zshrc`) and add the following lines:

```bash
export VIRUSTOTAL_API_KEY="your_actual_virustotal_key"
export ABUSEIPDB_API_KEY="your_actual_abuseipdb_key"
export GOOGLE_SAFE_BROWSE_API_KEY="your_actual_google_key"
export IPQS_API_KEY="your_actual_ipqs_key"
```

After saving the file, reload your shell:

```bash
source ~/.bashrc
```

(or simply open a new terminal session)



#### **Windows (Command Prompt — Temporary)**  
You can set environment variables temporarily in Command Prompt using:

```cmd
set VIRUSTOTAL_API_KEY="your_actual_virustotal_key"
set ABUSEIPDB_API_KEY="your_actual_abuseipdb_key"
set GOOGLE_SAFE_BROWSE_API_KEY="your_actual_google_key"
set IPQS_API_KEY="your_actual_ipqs_key"
```

*These values remain active only for the current session.*


#### **Windows (PowerShell — Temporary)**  
Alternatively, you can set them temporarily in PowerShell:

```powershell
$Env:VIRUSTOTAL_API_KEY="your_actual_virustotal_key"
$Env:ABUSEIPDB_API_KEY="your_actual_abuseipdb_key"
$Env:GOOGLE_SAFE_BROWSE_API_KEY="your_actual_google_key"
$Env:IPQS_API_KEY="your_actual_ipqs_key"
```

*These variables also last only for the current session.*


#### **Windows (Persistent — Recommended)**  
For permanent configuration:

1. Search for **“Environment Variables”** in the Start Menu  
2. Open **“Edit the system environment variables”**  
3. Click **“Environment Variables…”**  
4. Add new **User Variables** for each API key and assign the appropriate values  

This ensures the keys are always available across all sessions.



If any required API keys are missing, certain checks may be skipped or the tool may operate with limited functionality.  
The script should ideally handle missing keys gracefully by displaying a clear warning.



