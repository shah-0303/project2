# 📧 Smart Email Automation & Triage Assistant

An intelligent Natural Language Processing (NLP) and Large Language Model (LLM) orchestration pipeline designed for real-time inbound email ingestion, categorization, urgency scoring, metadata extraction, and human-in-the-loop auto-response dispatch.

---

## 🚀 Key Features

* **Intent Classification:** Automatically routes incoming emails into categories (`SUPPORT`, `BILLING`, `SALES`, `INQUIRY`, `FEEDBACK`, `SPAM`).
* **Dynamic Prioritization Engine:** Calculates real-time urgency metrics (`LOW`, `MEDIUM`, `HIGH`, `CRITICAL`) using weighted keyword heuristics and sentiment analysis.
* **Hybrid Processing Pipeline:** Seamlessly uses Google Gemini API (`gemini-2.5-flash`) for adaptive zero-shot triage, with an automatic fallback to local regex/NLP heuristics when offline.
* **Entity Extraction:** Detects and parses tracking IDs, invoice references (`INV-`, `REF-`, `TICKET-`), phone numbers, and currency values.
* **Interactive Control Center:** Streamlit-powered dashboard to monitor inbound volume, edit AI-generated draft replies, and dispatch responses.
* **Direct SMTP Dispatcher:** Sends real-world email replies directly to customer inboxes via standard TLS/SMTP authentication.
* **Persistence & Audit Trail:** Relational logging using SQLite and SQLAlchemy ORM.

---

## 🛠️ Tech Stack

* **Backend Framework:** FastAPI, Uvicorn, Pydantic V2
* **Database & ORM:** SQLite, SQLAlchemy
* **Frontend UI:** Streamlit
* **AI & NLP:** Google GenAI SDK (`gemini-2.5-flash`), Regular Expressions (RegEx)
* **Testing:** Pytest, HTTPX, FastAPI TestClient
* **Mailing:** Python `smtplib`, MIME multipart

---

## 📂 Project Structure

```text
smart-email-assistant/
│
├── app/
│   ├── __init__.py
│   ├── config.py         # App settings & environment variable loaders
│   ├── database.py       # SQLAlchemy engine & session factory
│   ├── engine.py         # Hybrid Gemini LLM + Rule-based NLP triage logic
│   ├── mailer.py         # Real-world SMTP email dispatch handler
│   ├── models.py         # Database schema definitions
│   ├── schemas.py        # Pydantic validation & response models
│   └── main.py           # FastAPI REST application & routing
│
├── tests/
│   ├── test_api.py       # Integration tests for FastAPI endpoints
│   └── test_engine.py    # Unit tests for classification & extraction logic
│
├── dashboard.py          # Interactive Streamlit operations dashboard
├── pytest.ini            # Pytest configuration
├── requirements.txt      # Project dependencies
├── Dockerfile            # Container build recipe
├── docker-compose.yml    # Multi-service container orchestrator
└── README.md             # Project documentation
