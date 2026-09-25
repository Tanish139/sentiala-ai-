
# 🔎 What is Sentiala AI?

**Sentiala AI** is a modern **OSINT (Open-Source Intelligence) investigation platform** designed to help users discover, organize, analyze, correlate, visualize, and report information from publicly available sources.

Sentiala AI is more than a simple search tool. It provides an investigation workspace where information can be transformed from individual sources and evidence into structured, connected, and understandable intelligence.

## 🧠 How Sentiala AI Works

A typical investigation follows this workflow:

**Target → Discovery → Sources → Evidence → Correlation → Analysis → Visualization → Report**

Sentiala AI brings these stages together into one platform.

## 🔍 Core Capabilities

* 🔎 **Source Discovery** — Discover and organize relevant publicly available sources.
* 📚 **Evidence Management** — Collect and structure investigation evidence.
* 🔗 **Evidence Correlation** — Identify relationships between different findings.
* 🧠 **Intelligence Analysis** — Analyze collected information using structured analysis.
* 📊 **Scoring** — Prioritize investigative findings.
* 🌍 **Geolocation Analysis** — Display geographic information on an interactive map.
* 🕐 **Timeline Analysis** — Organize events and findings chronologically.
* 🕸️ **Network Visualization** — Visualize relationships between entities and findings.
* 📑 **Source Matrix** — Compare information across different sources.
* 🔬 **Deep Scan** — Perform deeper analysis across investigation data.
* 📡 **Live Intelligence Feed** — Display investigation information in an interactive feed.
* 📝 **Investigation Reports** — Generate structured investigation reports.
* 🖥️ **Interactive Dashboard** — Manage investigations from a centralized interface.

## 🕸️ Intelligence Visualization

Sentiala AI is designed to make complex investigations easier to understand visually.

Investigations can be explored using:

* 🌍 World Maps
* 🕸️ Network Graphs
* 🕐 Timelines
* 📊 Source Matrices
* 📋 Evidence Boards
* 📡 Live Feeds
* 📝 Investigation Reports

## ⚙️ Technology Stack

Sentiala AI is built using:

* Python
* FastAPI
* Uvicorn
* HTTPX
* Pytest
* HTML
* CSS
* JavaScript
* Interactive data visualization
* JSON-based geographic data
* SQLite for local development

The backend and frontend are separated into modular components to make the project easier to maintain and extend.

---

# 🚀 How to Install and Run Sentiala AI

Sentiala AI can be run locally on:

* 🪟 Windows
* 🐉 Kali Linux

Make sure **Git and Python 3** are installed before starting.

---

# 🪟 Windows Installation

## 1. Clone the repository

Open **PowerShell** or the VS Code terminal:

```powershell
git clone https://github.com/YOUR-USERNAME/sentiala-ai.git
cd sentiala-ai
```

Replace `YOUR-USERNAME` with your GitHub username.

## 2. Create a virtual environment

```powershell
python -m venv .venv
```

## 3. Activate the virtual environment

```powershell
.venv\Scripts\activate
```

You should see `(.venv)` at the beginning of your terminal.

## 4. Install dependencies

```powershell
python -m pip install -r requirements.txt
```

## 5. Create the environment file

```powershell
Copy-Item .env.example .env
```

If the project requires API keys or additional configuration, add them to `.env`.

**Never upload `.env` to GitHub.**

## 6. Run the tests

```powershell
python -m pytest -q
```

## 7. Start the backend

```powershell
python -m uvicorn backend.app.main:app --reload
```

The backend will normally run at:

```text
http://127.0.0.1:8000
```

Keep this terminal open.

## 8. Start the frontend

Open a **second PowerShell/VS Code terminal**.

Make sure you are inside the Sentiala AI project folder, then run:

```powershell
python -m http.server 5500 --directory frontend
```

Open your browser and visit:

```text
http://127.0.0.1:5500
```

Sentiala AI should now be running locally.

---

# 🐉 Kali Linux Installation

## 1. Install required packages

Open the Kali terminal:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv git unzip -y
```

## 2. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/sentiala-ai.git
cd sentiala-ai
```

Replace `YOUR-USERNAME` with your GitHub username.

## 3. Create a virtual environment

```bash
python3 -m venv .venv
```

## 4. Activate the virtual environment

```bash
source .venv/bin/activate
```

You should see `(.venv)` at the beginning of your terminal.

## 5. Install dependencies

```bash
python -m pip install -r requirements.txt
```

## 6. Create the environment file

```bash
cp .env.example .env
```

Edit the file if configuration or API keys are required:

```bash
nano .env
```

Save the file after making your changes.

**Never upload `.env` to GitHub.**

## 7. Run the tests

```bash
python -m pytest -q
```

## 8. Start the backend

```bash
python -m uvicorn backend.app.main:app --reload
```

The backend will normally run at:

```text
http://127.0.0.1:8000
```

Keep this terminal open.

## 9. Start the frontend

Open a **second Kali terminal**.

Navigate to the project:

```bash
cd sentiala-ai
```

Activate the environment:

```bash
source .venv/bin/activate
```

Start the frontend:

```bash
python -m http.server 5500 --directory frontend
```

Open your browser:

```text
http://127.0.0.1:5500
```

Sentiala AI should now be running locally.

---

# ⚡ Quick Start

If you have already installed and configured everything:

### Windows

**Terminal 1 — Backend**

```powershell
.venv\Scripts\activate
python -m uvicorn backend.app.main:app --reload
```

**Terminal 2 — Frontend**

```powershell
python -m http.server 5500 --directory frontend
```

Open:

```text
http://127.0.0.1:5500
```

### Kali Linux

**Terminal 1 — Backend**

```bash
source .venv/bin/activate
python -m uvicorn backend.app.main:app --reload
```

**Terminal 2 — Frontend**

```bash
source .venv/bin/activate
python -m http.server 5500 --directory frontend
```

Open:

```text
http://127.0.0.1:5500
```

---

# 🧪 Testing

Run the complete automated test suite from the project root:

```bash
python -m pytest -q
```

The test suite covers important components including:

* API functionality
* Analysis
* Correlation
* Discovery
* Deep scanning
* Investigation engine
* Evidence processing
* Registry
* Scoring
* Validation

---

# 🏗️ Project Architecture

```text
sentiala-ai/
│
├── backend/
│   ├── app/
│   │   ├── api/
│   │   ├── models/
│   │   ├── osint/
│   │   ├── schemas/
│   │   ├── services/
│   │   └── utils/
│   │
│   └── tests/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   ├── animations/
│   │   ├── assets/
│   │   ├── styles/
│   │   └── visualizations/
│   │
│   └── index.html
│
├── .github/
├── .vscode/
├── .env.example
├── .gitignore
├── requirements.txt
├── start.bat
├── start.sh
├── README.md
└── LICENSE
```

---

# 🎯 Project Vision

The vision behind Sentiala AI is to bring the major stages of an OSINT investigation into one unified platform:

**Discovery + Evidence + Correlation + Analysis + Visualization + Reporting**

The project is designed to provide a centralized environment for managing investigations while keeping the architecture modular and extensible.

Future development can expand the platform with additional data sources, analytical modules, integrations, automation, visualization capabilities, collaboration features, and reporting functionality.

---

# 🔐 Responsible Use

Sentiala AI is intended for **lawful and ethical OSINT investigations** using publicly available information that users are authorized to access.

Users are responsible for complying with applicable laws, regulations, privacy requirements, website terms of service, and organizational policies.

Do not use Sentiala AI for:

* Unauthorized access
* Credential theft
* Harassment
* Stalking
* Privacy violations
* Unauthorized surveillance
* Account compromise
* Other unlawful activities

Use the platform responsibly and only investigate information you are legally permitted to access and process.

---

# 📌 Project Status

Sentiala AI is an actively developed project with a functional foundation for:

* OSINT investigation
* Evidence management
* Source discovery
* Analysis
* Correlation
* Geolocation
* Visualization
* Timeline analysis
* Network analysis
* Investigation reporting

The project is designed to evolve through future releases and additional capabilities.

---

# 📄 License

See the `LICENSE` file included in this repository for licensing information.
