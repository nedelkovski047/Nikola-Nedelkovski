# Nikola Nedelkovski

**Data engineer / analyst** · Business Information Systems graduate · North Macedonia

I build data systems that turn messy, unstructured sources into reliable, structured data. At **Pova**, a construction procurement platform, I spent about a year on data architecture: schema design, SKU consistency, a Snowflake migration, and Python/SQL validation.

## Technical skills

| Area | Tools |
|---|---|
| Languages | Python, SQL, JavaScript |
| Databases | PostgreSQL, Snowflake, MongoDB, SQLite |
| Analytics / BI | Power BI, SQL window functions |
| Backend | FastAPI, Pydantic, SQLAlchemy (async), Node.js |
| Data collection | aiohttp, BeautifulSoup, Playwright, pypdf |
| LLM integration | Gemini API (structured extraction) |
| Machine learning | Logistic Regression, Random Forest, XGBoost, SMOTE |
| Deployment | Docker, Render, Git / GitHub |

## Featured project

### [LRCR: Local Regulatory Change Radar](https://github.com/Nikola-Nedelkovski/lrcr)

An asynchronous Python backend that monitors official public-sector publications, identifies regulatory changes, and checks whether the documents they reference are publicly available. When a document can't be found online, it drafts a Freedom of Information request for human review.

**How it works**
1. **Extraction.** A PDF is parsed and an LLM converts it into a validated, structured schema (Pydantic) of regulatory changes and the documents they reference.
2. **Verification.** Async scrapers (aiohttp, BeautifulSoup, Playwright) search the relevant institutions' websites for each referenced document.
3. **Drafting.** If the document isn't found, a formal request is generated and queued.
4. **Human review.** A person approves or rejects each draft in a protected web interface. Only approval triggers an e-mail.

**Engineering decisions**
- **Human-in-the-loop by design.** LLM output can be wrong, so the system can produce a draft but never an unreviewed e-mail.
- **Concurrency-safe.** Database constraints guarantee one request per document, and a conditional update ensures a request can't be sent twice.
- **Resilient collection.** Retries with exponential backoff, file-type verification, and a distinction between "not found" and "could not check".
- **Secured.** Authentication on every route, CSRF protection, a strict Content-Security-Policy, and escaping of all LLM and scraper output.
- **Deployable.** Dockerised, PostgreSQL in production and SQLite locally, scheduled polling with APScheduler.

**Stack:** Python · FastAPI · Pydantic · SQLAlchemy · PostgreSQL · aiohttp · Playwright · Gemini API · Docker · Render

## Contact

[GitHub](https://github.com/Nikola-Nedelkovski) · [LinkedIn](https://www.linkedin.com/in/YOUR-LINKEDIN) · your.email@example.com
