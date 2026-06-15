Excellent — here is a full, **cohesive mastery roadmap + portfolio** designed precisely for:

- backend Python
    
- API integrations
    
- data modeling
    
- selective scraping as backup
    
- ETL (light, maintainable)
    
- SQL
    
- dashboards _only as consumer, not main job_
    

This is **not DevOps-heavy**, no Swift, no frontend burden.  
Just core backend + data integration engineering.

---

# 🎯 90-Day Full Curriculum

_(lean, deep, employable — not scatter)_

### **Phase 1: Core Backend & APIs (Weeks 1–4)**

**Goal:** Build APIs, consume APIs, handle auth, pagination & rate limits.

#### Skills

- Python requests
    
- FastAPI fundamentals
    
- Async calls vs sync
    
- OAuth2 / JWT
    
- Pagination handling
    
- Retry strategies / 429 / exponential backoff
    
- JSON → dict → pydantic models
    

#### Outcome

- call any major platform API
    
- build your own clean REST layer
    

#### Deliverables

- Build a FastAPI endpoint that:
    
    - Calls a public API (e.g. Mercado Livre products)
        
    - Normalizes result
        
    - Stores in PostgreSQL
        
    - Exposes clean `/products`
        

---

### **Phase 2: SQL & Data Architecture (Weeks 5–8)**

**Goal:** Stop thinking core = scraping.  
Real value = **normalization, modeling, schema consistency.**

#### Skills

- PostgreSQL deeply
    
- indexing, query plans (EXPLAIN)
    
- star schema vs snowflake
    
- normalization 1NF → BCNF
    
- Slowly Changing Dimensions (SCD2)
    
- OLTP vs OLAP design
    

#### Tools

- PostgreSQL
    
- dbdiagram.io (ERDs)
    
- dbt (optional, later)
    

#### Deliverables

- Model **dim_product, dim_seller, fact_sales**
    
- Create index strategy document
    
- Build queries:
    
    - “top selling SKU per region”
        
    - “price drift over time”
        
    - “duplicate merchant detection”
        

---

### **Phase 3: ETL & Data Pipelines (Weeks 9–10)**

**Goal:** ingest → clean → validate → store → expose via API.

#### Skills

- Batch ingestion
    
- cleaning & dedupe
    
- foreign key enforcement
    
- incremental loads (“only pull new”)
    
- dead-letter handling (failed records)
    

#### Tools

- Python + pandas/Polars
    
- SQLAlchemy (ORM basics)
    
- schedule / cron
    

#### Deliverables

- ETL script fetches new marketplace data daily
    
- Detects price deltas & stock changes
    
- Logs failures to a dead-letter table
    

---

### **Phase 4: Selective Scraping (Weeks 11–12)**

**Goal:** Scrape _only what APIs don’t provide_.

#### Skills

- legal & ethical scraping
    
- anti-bot respect (timings, headless, caching)
    
- merging scraped + API fields
    
- schema stability when upstream changes
    

#### Tools

- Playwright
    
- static HTML scrape → API augment
    

#### Deliverables

- scraper module fills missing attributes
    
- reports differences cleanly into PostgreSQL
    

---

## 🧠 Resulting Competency

You’re not "just backend" or "just scraping."

You become:  
**Backend Data Integration Engineer**  
who:

- consumes APIs
    
- models reliable warehouse data
    
- exposes an API others consume
    

No frontend.  
No mobile.  
No devops.

---

# 📁 Portfolio (3 Project Suite)

## **Project 1: Marketplace Data Sync & API**

**Core Hire Magnet**

**Data Sources**

- Mercado Livre official API
    

**Includes**

- OAuth token refresh
    
- paginated fetch
    
- normalize categories, sellers, SKUs
    
- PostgreSQL warehouse
    
- **your API**: `/products`, `/sellers`, `/price-history`
    

**Screenshot needed**

- ER diagram
    
- price drift table
    

---

## **Project 2: Brazil Business Registry Normalization (CNPJ Intelligence Lite)**

_(You mentioned interest earlier)_  
Public, messy datasets → one clean unified DB.

**Input**

- Dados públicos do CNPJ
    
- Simples Nacional table
    
- CNAE metadata
    

**Output API**

- `/company/{cnpj}`
    
- `/search?cnae=…&city=…`
    
- `/risk-score`
    

**Value**

- dedupe
    
- address normalization
    
- merged branches
    
- historical status transitions
    

---

## **Project 3: Price Monitoring + API + Telegram Alerts**

**Why it works**:

- uses API first
    
- scrapes only if missing fields
    
- daily ETL
    
- sends delta messages to Telegram bot
    

**Deliverables**

- alerts: price up/down > X%
    
- delta table to PostgreSQL
    
- dashboard optional (Metabase)
    

---

# 🌎 You Now Have a Hireable Portfolio Without Frontend

|Skill|Demonstrated In Projects|
|---|---|
|API auth + pagination|Marketplace Sync|
|SQL + modeling|CNPJ Intelligence|
|ETL + validation|Price Monitor|
|selective scraping|Price Monitor|
|productized API backend|all 3|

This is a **real portfolio** recruiters understand instantly.

---

# 🚀 Bonus: Positioning Statement (CV/LinkedIn)

> **Python Backend & Data Integration Engineer**  
> Specializing in:

- REST API integration
    
- data normalization & warehousing
    
- ETL pipelines
    
- enrichment via selective scraping
    

Focus:

- marketplace analytics
    
- business registry intelligence
    
- automated ingestion, delta alerts & exposure via FastAPI
    

---

# 🎯 After 90 Days, Your Optional Add-ons (only if wanted)

- basic S3 storage
    
- async job queue (Celery / RQ)
    
- dbt transformations
    
- Metabase dashboards
    

Not mandatory.  
Only when portfolio is done and job-ready.