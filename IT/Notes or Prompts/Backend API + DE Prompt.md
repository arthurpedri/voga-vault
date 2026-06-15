Absolutely — here are curated, **non-random**, high-signal resources mapped directly to your 90-day backend + API + data integration curriculum.

No cloud, no frontend overload, no 20-hour courses that waste your time.

---

# 📌 Phase 1: Backend & APIs (Weeks 1–4)

### 🧠 Core Concept: API consumption + exposure (FastAPI)

#### 📚 Learn FastAPI

- **FastAPI Official Tutorial** (best, concise)  
    [https://fastapi.tiangolo.com/tutorial/](https://fastapi.tiangolo.com/tutorial/)
    
- **FastAPI by Example** (pragmatic, auth + DB)  
    https://fastapi.tiangolo.com/advanced/tutorial/
    

#### 🐍 Python API Consumption

- **Real Python — Working with APIs in Python**  
    [https://realpython.com/python-requests/](https://realpython.com/python-requests/)
    

#### 📚 HTTP, Pagination & Auth

- **MDN – HTTP Fundamentals**  
    [https://developer.mozilla.org/en-US/docs/Web/HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
    
- **OAuth 2 Simplified**  
    [https://oauth.net/2/](https://oauth.net/2/)
    

#### 🎯 Short, targeted topics

- **Retries & Backoff**  
    [https://pypi.org/project/backoff/](https://pypi.org/project/backoff/)
    
- **Async I/O in Python**  
    [https://realpython.com/async-io-python/](https://realpython.com/async-io-python/)
    

---

# 📌 Phase 2: SQL Deep Dive & Modeling (Weeks 5–8)

### 🧠 Core Concept: schema mastery, warehousing logic

#### 🏛 SQL Mastery

- **SQLBolt (best beginner → intermediate)**  
    [https://sqlbolt.com/](https://sqlbolt.com/)
    
- **Mode Analytics SQL School**  
    [https://mode.com/sql-tutorial/](https://mode.com/sql-tutorial/)
    
- **Use The Index, Luke! (indexing, query planning)**  
    [https://use-the-index-luke.com/](https://use-the-index-luke.com/)
    

#### 🏗 Data Modeling (critical)

- **Dimensional Modeling (Kimball Group)**  
    [https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/)
    
- **Star vs Snowflake Visual Guide**  
    https://vertabelo.com/blog/star-vs-snowflake-schema/
    

#### 🛠 Query Optimization

- **PostgreSQL EXPLAIN Visualizer (pev2)**  
    [https://explain.dalibo.com/](https://explain.dalibo.com/)
    

---

# 📌 Phase 3: Light ETL & Data Cleaning (Weeks 9–10)

### 🧠 Core Concept: ingestion → cleaning → normalization

#### 🧹 Dataframe Processing

- **Polars Book (free + modern)**  
    https://pola.rs/book/
    
- **Pandas 20-minute Official Tour**  
    [https://pandas.pydata.org/docs/getting_started/intro_tutorials/](https://pandas.pydata.org/docs/getting_started/intro_tutorials/)
    

#### 🧰 ETL Principles

- **Data Pipelines with Python**  
    https://realpython.com/python-data-pipelines/
    
- **Mage.ai Intro (lightweight ETL tool)**  
    https://docs.mage.ai/getting-started/overview
    

---

# 📌 Phase 4: Selective Scraping (Weeks 11–12)

### 🧠 Core Concept: scrape only missing API fields

#### 🕸 Browser Automation

- **Playwright Python Intro**  
    [https://playwright.dev/python/docs/intro](https://playwright.dev/python/docs/intro)
    

#### 📚 Responsible Scraping

- **Scraping Guide by Dataquest (legality, etiquette)**  
    https://www.dataquest.io/blog/web-scraping-python/
    

#### 🛑 Avoiding Anti-Bot Damage

- **Headers, Throttling & Rotations Basics**  
    [https://scrapeops.io/web-scraping-playbook/](https://scrapeops.io/web-scraping-playbook/)
    

---

# 🧱 Database Tools for Schema & ERD

|Tool|Purpose|
|---|---|
|dbdiagram.io|clean ERD visuals|
|DBeaver|DB GUI, introspection|
|pgAdmin|Postgres management|
|PEV2|Visual EXPLAIN planner|

---

# 🧠 Very Specific Reading List (High Value Only)

|Topic|Resource|
|---|---|
|Data Integrity|“What Every Data Scientist Needs to Know About SQL” (Mode Analytics)|
|Normalization|Stanford DB Notes (short, gold standard)|
|OLTP vs OLAP|Snowflake docs section (clear diagrams)|
|REST Design|Microsoft REST API Guidelines (surprisingly excellent)|

---

# 🎯 Practice Projects (exact skill correlation)

|Project|Skill Reinforcement|
|---|---|
|Mercado Livre API Sync|auth, pagination, ETL|
|CNPJ Normalize DB|dedupe, schema design|
|Price Drift Monitor|delta detection, alerts|
|Telegram ETL Alerts|backend without UI|
|Mini ETL Failure Log|retry, dead-letter table|

---

# 🛠 Dev Environment Setup (minimal but complete)

- Python 3.11
    
- Poetry OR pipenv (optional)
    
- Postgres (local)
    
- DBeaver
    
- FastAPI + uvicorn
    
- Polars
    
- requests (core HTTP client)
    

---

# 🤓 Study Tips (This is where most fail)

1. **Don’t learn frameworks, learn patterns**  
    e.g. OAuth token refresh, pagination strategy
    
2. **Model before coding**  
    ERD first → API second → ETL third
    
3. **APIs over scraping**  
    scraping is fallback, not architecture
    
4. **Repetition > novelty**  
    build 2–3 integrations, not 20 half-built ones
    

---

# 📌 Optional but Strong After Curriculum

_(NOT needed now)_

If one day you want:

- dbt (analytics layer)
    
- S3 (simple storage)
    
- Redshift/BigQuery (warehouse)
    

That’s layer **after** this foundation — not first job skill, not required for backend integrator role.