# Sentiala AI

Sentiala AI is an intelligent, modern OSINT (Open-Source Intelligence) investigation platform designed to help users discover, organize, analyze, correlate, and visualize publicly available information in a structured investigative workflow.

The platform combines automated intelligence analysis with evidence management, source discovery, correlation, scoring, geolocation, timelines, network visualization, and investigative reporting to provide a unified environment for exploring complex information.

Sentiala AI is built with a focus on clarity, speed, extensibility, and professional investigative workflows. Instead of presenting information as disconnected search results, the platform organizes discovered intelligence into relationships, evidence, sources, entities, timelines, geographic context, and analytical insights.

## Core Capabilities

* **OSINT Investigation Engine** — Coordinate investigative workflows and process collected intelligence.
* **Source Discovery** — Discover and organize relevant publicly available sources.
* **Evidence Management** — Collect, structure, validate, and analyze investigative evidence.
* **Evidence Correlation** — Identify relationships and connections between evidence and discovered information.
* **Intelligence Analysis** — Analyze investigation data and generate structured analytical results.
* **Scoring System** — Evaluate and prioritize investigative findings using structured scoring mechanisms.
* **Geolocation Analysis** — Provide geographic context for relevant investigative information.
* **Timeline Analysis** — Organize events and findings chronologically.
* **Network Visualization** — Visualize relationships between entities, sources, and findings.
* **Source Matrix** — Compare and organize information across multiple sources.
* **Deep Scan Workflows** — Support deeper investigative analysis across collected information.
* **Investigation Reports** — Generate structured reports from investigation data.
* **Interactive Dashboard** — Provide a centralized investigation workspace.
* **API Backend** — FastAPI-based backend designed for modularity and future integrations.
* **Automated Testing** — Test coverage for core backend functionality and investigative components.

---

# Technology Stack

Sentiala AI uses a modular architecture built around:

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
* SQLite for local development and investigation storage

---

# Project Architecture

The project separates the backend, frontend, OSINT processing, data models, visualization, reporting, and testing components.

### Backend

The backend contains:

* API routes
* Database configuration
* Investigation models
* Source models
* Investigation schemas
* OSINT discovery
* Evidence processing
* Correlation analysis
* Intelligence scoring
* Geolocation
* Investigation engine
* Reporting
* Validation utilities

### Frontend

The frontend provides dedicated components for:

* Investigation dashboard
* Target information
* Evidence board
* Live intelligence feed
* Network graph
* World map
* Timeline
* Source matrix
* Deep scan
* AI analysis panel
* Investigation reports

---

# How to Run Sentiala AI

Sentiala AI can be run locally on **Windows** or **Kali Linux**.

> **Recommended:** Python 3.12 or another Python version supported by the project's dependencies.

Before starting, make sure Git and Python are installed.

---

# 🪟 Running on Windows

## 1. Clone the repository

Open **PowerShell** or the VS Code terminal:

```powershell
git clone https://github.com/YOUR-USERNAME/sentiala-ai.git
cd sentiala-ai
```

Replace `YOUR-USERNAME` with your GitHub username.

---

## 2. Create a virtual environment

```powershell
python -m venv .venv
```

---

## 3. Activate the virtual environment

```powershell
.venv\Scripts\activate
```

After activation, your terminal should show something similar to:

```text
(.venv) PS C:\...\sentiala-ai>
```

---

## 4. Install dependencies

Use:

```powershell
python -m pip install -r requirements.txt
```

If `pip` is already working normally, the following also works:

```powershell
pip install -r requirements.txt
```

---

## 5. Configure environment variables

Copy the example environment file:

```powershell
Copy-Item .env.example .env
```

Open `.env` and configure any required settings or API keys.

**Never commit `.env` to GitHub.**

---

## 6. Run the backend

With the virtual environment activated:

```powershell
python -m uvicorn backend.app.main:app --reload
```

The backend will normally be available at:

```text
http://127.0.0.1:8000
```

Keep this terminal running.

---

## 7. Run the frontend

Open a **second VS Code terminal**.

Activate the environment if necessary:

```powershell
.venv\Scripts\activate
```

Then run:

```powershell
python -m http.server 5500 --directory frontend
```

The frontend will normally be available at:

```text
http://127.0.0.1:5500
```

Open that address in your browser.

---

## 8. Run the tests

Before using or modifying the project, you can verify the installation with:

```powershell
python -m pytest -q
```

A successful test run should report that all available tests pass.

---

# 🐉 Running on Kali Linux

## 1. Clone the repository

Open a terminal:

```bash
git clone https://github.com/YOUR-USERNAME/sentiala-ai.git
cd sentiala-ai
```

---

## 2. Make sure Python and Git are installed

```bash
python3 --version
git --version
```

If Python, pip, or the virtual-environment package is missing:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv git -y
```

---

## 3. Create a virtual environment

```bash
python3 -m venv .venv
```

---

## 4. Activate the virtual environment

```bash
source .venv/bin/activate
```

Your terminal should then show something similar to:

```text
(.venv) user@kali:~/sentiala-ai$
```

---

## 5. Install dependencies

```bash
python -m pip install -r requirements.txt
```

If pip needs to be upgraded:

```bash
python -m pip install --upgrade pip
```

Then install the requirements again:

```bash
python -m pip install -r requirements.txt
```

---

## 6. Configure environment variables

Create your local environment file:

```bash
cp .env.example .env
```

Edit it:

```bash
nano .env
```

Add any required configuration or API keys, then save the file.

**Do not upload `.env` to GitHub.**

---

## 7. Run the backend

```bash
python -m uvicorn backend.app.main:app --reload
```

The backend will normally be available at:

```text
http://127.0.0.1:8000
```

Keep this terminal running.

---

## 8. Run the frontend

Open another terminal and navigate to the project:

```bash
cd sentiala-ai
```

Activate the environment:

```bash
source .venv/bin/activate
```

Then run:

```bash
python -m http.server 5500 --directory frontend
```

Open:

```text
http://127.0.0.1:5500
```

in your browser.

---

## 9. Run the tests

```bash
python -m pytest -q
```

This verifies that the main project components are functioning correctly.

---

# ⚡ Quick Start

If the environment has already been configured, Windows users can start the backend with:

```powershell
.venv\Scripts\activate
python -m uvicorn backend.app.main:app --reload
```

Then in another terminal:

```powershell
python -m http.server 5500 --directory frontend
```

Kali Linux:

```bash
source .venv/bin/activate
python -m uvicorn backend.app.main:app --reload
```

Second terminal:

```bash
source .venv/bin/activate
python -m http.server 5500 --directory frontend
```

---

# 🧪 Testing

Run the complete test suite with:

### Windows

```powershell
python -m pytest -q
```

### Kali Linux

```bash
python -m pytest -q
```

The project includes tests for:

* API functionality
* Analysis
* Correlation
* Discovery
* Deep scanning
* Investigation engine
* Evidence
* Registry
* Scoring
* Validation

---

# 🔐 Security & Responsible Use

Sentiala AI is intended for **lawful and ethical use of publicly available information**.

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

Only investigate information that you are legally permitted to access and process.

---

# 📁 Important Files

```text
sentiala-ai/
│
├── backend/
│   └── app/
│       ├── api/
│       ├── models/
│       ├── osint/
│       ├── schemas/
│       ├── services/
│       └── utils/
│
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── services/
│   │   ├── animations/
│   │   ├── assets/
│   │   ├── styles/
│   │   └── visualizations/
│   └── index.html
│
├── tests/
├── .env.example
├── .gitignore
├── requirements.txt
├── start.bat
├── start.sh
├── README.md
└── LICENSE
```

---

# 🚀 Project Goals

The long-term goal of Sentiala AI is to evolve into a powerful intelligence-analysis environment that brings together:

**Discovery + Evidence + Correlation + Analysis + Visualization + Reporting**

within a single modern platform.

The project is designed to remain modular so that additional intelligence providers, analytical modules, visualization systems, APIs, authentication, collaboration features, and reporting capabilities can be integrated over time.

---

# 📌 Project Status

Sentiala AI is an actively developed project.

The current version provides a functional foundation for OSINT investigations, evidence management, analysis, correlation, visualization, and reporting.

Future releases may expand the platform with additional data sources, intelligence capabilities, automation, integrations, and collaboration features.

---

# 📄 License

See the `LICENSE` file included in this repository for licensing information.
