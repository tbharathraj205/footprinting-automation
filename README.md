# 🕵️‍♂️ Footprinting Automation

**Footprinting Automation** is a cybersecurity reconnaissance (recon) tool that automates the process of information gathering (footprinting) using **n8n** and **OpenAI GPT**.  
It combines the power of command-line tools like **Nmap**, **Nslookup**, **Dig**, and **Traceroute**, and automatically formats the output into a **dark-themed HTML dashboard** showing open ports, DNS data, traceroute results, vulnerabilities, and a risk score — all explained in *simple layman’s terms*.

---
## 📁 Project Structure
```
footprinting-automation/
├── webpage/
│ ├── index.html # Frontend web interface (Matrix background + input form)
│ └── footprint-automation.json # n8n workflow file (backend automation)
└── README.md # Documentation (this file)

```

---

## ⚙️ How It Works

### 🔹 Step 1 – User Interaction
The **index.html** page is the user interface where you enter a domain name (like `example.com`).  
When you hit **Submit**, it sends a POST request to your **n8n webhook URL**.

---

### 🔹 Step 2 – n8n Workflow
The file `footprint-automation.json` contains an n8n automation that runs several security tools:

| Node | Function |
|------|-----------|
| 🧩 **Webhook** | Receives the domain name (`myText`) from the web page |
| ⚙️ **nmap** | Scans open ports and running services |
| 🌐 **nslookup** | Gets DNS and IP mapping details |
| 📡 **dig** | Retrieves A, NS, MX, and TXT records |
| 🚦 **traceroute** | Maps the network route from source to target |
| 🔗 **Merge** | Combines all scan results into a single data stream |
| 💬 **OpenAI GPT (AI Agent)** | Converts raw output into a dark-themed HTML report |
| 🧠 **Respond to Webhook** | Sends back the generated HTML dashboard to the web page |

---

### 🔹 Step 3 – AI-Generated Dashboard
Once the workflow completes:
- All raw command outputs are merged
- GPT-4.1-nano processes the data and generates a **self-contained HTML dashboard**
- The dashboard includes:
  - Open ports and services (in table form)
  - DNS records (A, NS, MX, TXT)
  - Traceroute summary (with a layman explanation)
  - Possible vulnerabilities and their risks
  - Security score (0–100) with progress bar
  - Recommended next steps to secure the system

---

## 🧠 AI Agent Logic (Simplified)
The AI agent converts raw scan data into a report that:
- Keeps **all factual data** (no guessing)
- Uses **inline CSS only** (dark, modern theme)
- Adds **human-readable explanations**
- Assigns a **security score** and **risk label** (Good / Low / Moderate / High)
- Suggests **actionable improvements**

---

## 💻 Setup Guide

### 1️⃣ Prerequisites
- [n8n](https://n8n.io) installed (local or cloud)
- [OpenAI API key](https://platform.openai.com/)
- Basic command-line tools available: `nmap`, `nslookup`, `dig`, `traceroute`
- A modern browser for the frontend

---

### 2️⃣ Import the Workflow

1. Open **n8n**  
2. Click **Import Workflow**  
3. Upload the file:  
webpage/footprint-automation.json

4. Set your **Webhook URL** (copy it from the “Webhook” node in n8n)  
5. Replace the placeholder in `index.html`:


const N8N_WEBHOOK = "https://your-n8n-domain/webhook/sample";

### 3️⃣ Run Locally

1. Open the file:

    webpage/index.html


2. Enter a domain like example.com

3. Click Submit

4. Wait for the scan to finish — your report will appear below the form.

### 4️⃣ Deploy Online (Optional)


📊 Example Output (Dashboard Includes)

1. Domain and IP details

2. Open ports with explanations

3. DNS records (A, NS, MX, TXT)

4. Traceroute path + plain-language summary

5. Possible vulnerabilities per service

6. Security score with progress bar

7. Risk category (Good, Low, Moderate, High)

8. Actionable security recommendations

## 🧩 File Details
File	Description
index.html	User interface with Matrix animation background. Sends user input (domain) to n8n. Displays HTML report response.
footprint-automation.json	n8n workflow with full automation logic for scanning, merging results, and using GPT to generate dashboard output.

## 🔐 Security & Ethics

This project is for educational and ethical hacking purposes only.

Do not use this tool on domains or systems you don’t own or have permission to test.

The author (Bharath Raj) is not responsible for misuse or illegal activities.

## 🧑‍💻 Author

Bharath Raj
(Cybersecurity & AI Enthusiast)

GitHub: @tbharathraj205


## 🌟 Show Your Support

If you like this project:

⭐ Star the repo

🐛 Report issues

💡 Suggest improvements

Footprinting Automation made simple — Automated, Intelligent, and Ethical 🔍
