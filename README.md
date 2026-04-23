# Centralized AI-Based Threat Intelligence Dashboard

Centralized AI-Based Threat Intelligence Dashboard is a FastAPI-based cybersecurity project that collects, analyzes, stores, and visualizes Indicators of Compromise (IOCs) such as domains, IP addresses, URLs, and hashes. The system simulates a mini SOC / SIEM-style platform with a modern dashboard, alerts, threat feed ingestion, incident drilldown, and auto-generated threat reports.

## Project Overview

The goal of this project is to build a centralized threat intelligence platform for final year engineering evaluation. Instead of only storing IOC records in a table, the system performs automated IOC classification, risk scoring, dashboard analytics, alert prioritization, and report generation from one shared threat dataset.

## Main Features

- Login page for platform access
- Add IOC module for manual threat entry
- Automatic IOC type detection
- AI-style threat scoring and confidence generation
- Risk classification as `LOW`, `MEDIUM`, and `HIGH`
- Threat feed simulation with manual and bulk auto-feed insertion
- SOC-style dashboard with charts and KPI cards
- Search and filter support by IOC, type, risk, and status
- Alerts page for high-risk threats
- Threat detail page with investigation view
- Reports page with threat-family summaries
- Status tracking as `Open`, `Investigating`, and `Closed`

## Supported IOC Types

- Domain
- IP Address
- URL
- File Hash

## Tech Stack

- Backend: FastAPI
- Language: Python
- Database: SQLite
- Templates: Jinja2
- Frontend: HTML, CSS, JavaScript
- Charts: Chart.js
- Server: Uvicorn

## Project Structure

```text
centralized-ai-threat-intelligence/
├── backend/
│   ├── api/
│   │   └── health.py
│   ├── services/
│   │   ├── analysis.py
│   │   └── repository.py
│   ├── static/
│   │   ├── css/
│   │   │   └── styles.css
│   │   └── js/
│   │       └── dashboard.js
│   ├── templates/
│   │   ├── base.html
│   │   ├── login.html
│   │   ├── dashboard.html
│   │   ├── add_ioc.html
│   │   ├── feed.html
│   │   ├── alerts.html
│   │   ├── reports.html
│   │   └── threat_detail.html
│   ├── main.py
│   └── project.db
├── docs/
├── screenshots/
├── requirements.txt
└── README.md
```

## How the System Works

1. The user logs into the platform.
2. The user adds an IOC manually or through the threat feed module.
3. The backend detects the IOC type.
4. The analysis engine assigns:
   - threat family
   - confidence
   - score
   - risk level
5. The record is stored in the SQLite database.
6. The dashboard reads the stored data and generates:
   - summary cards
   - analytics charts
   - filtered threat tables
7. High-risk threats appear in the Alerts module.
8. Detailed threat investigation is available through the threat detail page.
9. Threat-family summaries are generated in the Reports module.

## Core Modules

### 1. Dashboard

The dashboard is the main operations board of the project. It shows:

- KPI summary cards
- Top threat types
- Risk distribution
- Source distribution
- Threat trend
- Status overview
- Tactics coverage
- Active vulnerabilities
- Latest reports
- Threat search and triage table

### 2. Add IOC

This module allows users to enter suspicious indicators manually. Each IOC is analyzed and stored with:

- IOC value
- IOC type
- threat category
- confidence
- score
- risk
- status
- source

### 3. Threat Feed

This module simulates cyber threat intelligence ingestion.

It supports:

- manual feed entry
- automatic feed generation

The purpose is to show how incoming threat data affects the dashboard and reports.

### 4. Alerts

The alerts module displays high-risk threats and allows:

- filtering by status
- high-risk review
- updating case status

### 5. Threat Detail

Each stored threat can be opened in a dedicated detail page. It includes:

- threat profile
- risk score
- telemetry
- investigation summary
- recommended actions
- related threats

### 6. Reports

The reports module automatically creates grouped summaries for threat families such as:

- Malware
- Phishing
- Botnet
- Ransomware

It also includes a `New Additions` section so newly inserted IOCs are reflected automatically.

## Backend Logic

### IOC Analysis Engine

The IOC analysis logic is implemented in `backend/services/analysis.py`.

It performs:

- IOC type detection
- threat family mapping
- deterministic score generation
- confidence calculation
- risk classification

### Repository Layer

The database and analytics logic is implemented in `backend/services/repository.py`.

It handles:

- database initialization
- schema creation
- record normalization
- data insertion
- filtering
- analytics generation
- report generation
- threat detail retrieval

## Database

The project uses a SQLite database with a main table named `threats`.

Important fields include:

- `id`
- `ioc`
- `type`
- `threat`
- `confidence`
- `score`
- `status`
- `source`
- `created_at`
- `updated_at`

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/your-repo/centralized-ai-threat-intelligence.git
cd centralized-ai-threat-intelligence
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

### 3. Activate the environment

Windows:

```bash
venv\Scripts\activate
```

macOS / Linux:

```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Run the server

```bash
uvicorn backend.main:app --reload
```

### 6. Open the application

```text
http://127.0.0.1:8000
```

Demo login:

- Username: `admin`
- Password: `admin123`

## Requirements

The project uses the following main Python packages:

- `fastapi`
- `uvicorn[standard]`
- `jinja2`
- `python-multipart`

## API / Utility Route

The project also includes a health check route:

- `GET /api/health`

## Future Improvements

- Real-world threat intelligence API integration
- VirusTotal / AbuseIPDB / MISP support
- PostgreSQL migration
- WebSocket-based real-time updates
- PDF report export
- Advanced machine learning scoring
- Analyst notes and collaboration features
- Role-based authentication

## Author

**Rishika H.J**  
B.Tech CSE (Cybersecurity)

## Project Status

- Backend completed
- Modular frontend completed
- Dashboard analytics completed
- Alerts and reports completed
- Threat feed simulation completed
- Threat detail drilldown completed
