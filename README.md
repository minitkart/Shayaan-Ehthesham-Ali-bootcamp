# Enterprise SIEM Lab: Deployed a Wazuh SIEM Cluster to Aggregate Logs and Create Custom Alert Dashboards

## Project Description
This project demonstrates the complete deployment of an enterprise-grade **Wazuh SIEM cluster** to centralize telemetry aggregation across distributed enterprise endpoints and create custom real-time SOC alert dashboards. Orchestrated via containerized microservices (Wazuh Manager, Wazuh Indexer, and Wazuh Dashboard), the cluster ingests security telemetry from Linux servers and Windows domain controllers, applies custom XML detection rules mapped to the **MITRE ATT&CK Framework**, and exposes security events through custom visualization dashboards and an automated REST API analysis pipeline.

---

## Deliverables & Repository Structure
```text
├── YourName_ProjectName.ipynb       # Main Jupyter Notebook containing deployment configs, API ingestion, and dashboard metrics
├── requirements.txt                 # Python dependencies required for execution
├── README.md                        # Architecture overview, setup steps, and dataset reference
├── YourName_ProjectReport.docx      # Comprehensive capstone project documentation report
├── docker-compose.yml               # Wazuh SIEM cluster container orchestration manifest
├── local_rules.xml                  # Custom Wazuh XML threat detection rules
├── wazuh_aggregated_alerts.json     # Aggregated cluster security alerts dataset
└── wazuh_custom_dashboard.png       # Rendered custom SOC alert dashboard visualization
```

---

## Dataset Reference
* **Dataset Name:** Wazuh SIEM Aggregated Security Alerts Telemetry (`wazuh_aggregated_alerts.json`)
* **Source & Reference:** Exported cluster alerts generated during simulated attack scenarios (SSH brute force, FIM tampering, and privilege escalation), structured according to the official [Wazuh Alert Format Specification](https://documentation.wazuh.com/current/user-manual/reference/ossec-conf/alerts.html) and [Elastic Security Analytics Datasets](https://github.com/elastic/examples/tree/master/Machine%20Learning/Security%20Analytics%20Recipes).

---

## Technologies Used
* **SIEM Platform:** Wazuh Server / Manager 4.8.0, Wazuh Indexer (OpenSearch), Wazuh Dashboard
* **Containerization:** Docker, Docker Compose
* **Programming & Automation:** Python 3.10+, Jupyter Notebook
* **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Requests, Tabulate
* **Framework Alignment:** MITRE ATT&CK Matrix for Enterprise (Tactics: Initial Access, Credential Access, Privilege Escalation, Defense Evasion)

---

## Setup & Execution Instructions

### 1. Prerequisites
- Python 3.10 or higher
- Docker & Docker Compose (for live cluster hosting)
- 4–8 GB RAM allocated to Docker

### 2. Install Python Dependencies
```bash
pip install -r requirements.txt
```

### 3. Deploy Wazuh Cluster (Optional Live Lab)
To start the multi-container Wazuh SIEM cluster locally:
```bash
docker compose -f docker-compose.yml up -d
```
Access the Wazuh Dashboard at `https://localhost:443` (Default credentials: `admin` / `SecretPassword!`).

### 4. Run the SIEM Analytics Pipeline
Launch Jupyter Notebook to load the aggregated cluster dataset, evaluate custom detection rules, and generate the custom SOC alert dashboards:
```bash
jupyter notebook YourName_ProjectName.ipynb
```
Select **Kernel -> Restart and Run All** to generate `wazuh_custom_dashboard.png` and export `wazuh_soc_incident_triage.csv`.