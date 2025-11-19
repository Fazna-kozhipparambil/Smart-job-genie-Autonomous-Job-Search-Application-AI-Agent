# SmartJob Agent – Automated AI Job Search & Application System
<img width="1748" height="1240" alt="Card - Smartjob Genie (2)" src="https://github.com/user-attachments/assets/0dfcc62a-3009-426e-90a3-5ce575b44365" />

##  Overview

SmartJob Agent is a multi‑agent AI system built using **Google ADK (Agent Development Kit)** and deployed on **Vertex AI Agent Engine**. It automates the **entire job search workflow** — from understanding your resume to auto‑applying and tracking applications.

This project demonstrates advanced agentic AI concepts including:

* Multi‑agent orchestration
* Sequential & loop agents
* Tool‑enabled agents (web search, scraping, code execution)
* Context engineering
* State & memory management
* A2A (Agent‑to‑Agent) communication
* Deployment on Vertex AI Agent Engine

---

##  Features

### **1. User Profile Agent**

* Converts resume (PDF/text) → structured JSON profile.
* Extracts skills, experience, job roles, location preferences.
* Cleans and normalizes text.

### **2. Job Search Agent**

* Searches job portals using Google Search Tool.
* Scrapes job descriptions, requirements, salary, and job URLs.
* Filters by user preferences.

### **3. Job Ranking Agent**

* Uses Gemini reasoning to evaluate job–user fit.
* Scores jobs based on skills match, experience, JD requirements.
* Returns top‑ranked opportunities.

### **4. Resume + Cover Letter Generator Agent**

* Customizes bullet points using job‑specific keywords.
* Generates optimized cover letters with Gemini.
* Outputs PDF‑ready formatting.

### **5. Auto‑Apply Agent**

* Automatically fills forms.
* Uploads resume & cover letter.
* Uses long‑running operations for multi‑step forms.

### **6. Application Tracker Agent**

* Stores job history in memory.
* Tracks applied jobs and statuses.
* Avoids duplicates and manages follow‑ups.

---

##  Architecture Diagram

<img width="1300" height="455" alt="smart_job_genie_architecture" src="https://github.com/user-attachments/assets/ac76b585-cdec-4489-a92f-6bd67d83f35b" />


---

##  Tech Used

* **Google ADK** (Agent Development Kit)
* **Vertex AI Agent Engine** (deployment)
* **Gemini Pro 1.5** – reasoning, ranking, writing
* **Google Search Tool**
* **Python Tools** (for scraping + transformation)
* **InMemorySessionService** for session state
* **Memory Bank** for long‑term tracking
* **A2A Protocol** for agent‑to‑agent messaging

---

##  Project Structure

```
smartjob-agent/
│
├── agents/
│   ├── user_profile_agent.py
│   ├── job_search_agent.py
│   ├── job_ranking_agent.py
│   ├── resume_cover_agent.py
│   ├── auto_apply_agent.py
│   └── tracker_agent.py
│
├── deployment/
│   ├── main_agent.py
│   ├── vertex_config.yaml
│   └── start.py
│
├── docs/
│   └── architecture_diagram.png
│
└── README.md
```

---

##  Installation

```bash
git clone https://github.com/yourusername/smartjob-agent.git
cd smartjob-agent
pip install -r requirements.txt
```

---

## Deployment on Vertex AI Agent Engine

### **1. Enable APIs**

* Vertex AI
* IAM Service Account
* Cloud Run
* Cloud Build

### **2. Set environment variables**

```bash
export PROJECT_ID="your-gcp-project-id"
export LOCATION="us-central1"
```

### **3. Deploy main agent**

```bash
adk deploy \
  --project=$PROJECT_ID \
  --location=$LOCATION \
  --entry-file=deployment/main_agent.py \
  --service-account=agent-sa@$PROJECT_ID.iam.gserviceaccount.com \
  --name=smartjob-engine
```

### **4. Test your deployed agent**

```bash
adk sessions start --agent=smartjob-engine
```

---

##  Example Query

```
Find data analyst jobs in Texas. Customize my resume and apply automatically.
```

---

## Future Improvements

* Multi‑platform auto‑apply (LinkedIn, Indeed, ZipRecruiter)
* Interview preparation agent
* AI portfolio generator
* Salary prediction model

---

## License

MIT License

---

## Contributing

PRs are welcome! For major changes, please open an issue first.
