# Nikola Nedelkovski

Business Information Systems graduate · Python backend and data engineering · Bitola, North Macedonia

I build data projects in Python and SQL. I like turning messy, unstructured sources into reliable, structured data.

Currently looking for backend, data engineering and data analyst roles.

## Technical skills

| Area | Tools |
|---|---|
| Languages | Python, SQL |
| Backend | FastAPI, Pydantic, SQLAlchemy (async), REST/OpenAPI, APScheduler |
| Databases | PostgreSQL, SQLite |
| Data collection | aiohttp, BeautifulSoup, Playwright, pypdf |
| LLM integration | Gemini API (structured extraction) |
| Analytics / BI | Power BI |
| Tools | Docker, Git/GitHub, pytest, Render |

## Featured project

### [LRCR](https://github.com/nedelkovski047/lrcr)

An asynchronous Python backend that monitors official public-sector publications, finds regulatory changes, and checks whether the documents they reference are publicly available. When a document can't be found online, it drafts a Freedom of Information request for a person to review.

**How it works**
1. **Extraction.** A PDF is parsed and the Gemini API turns it into structured data (regulatory changes and the documents they reference), validated with Pydantic.
2. **Verification.** Async scrapers (aiohttp, BeautifulSoup, Playwright) search the relevant institutions' websites for each referenced document.
3. **Drafting.** If the document isn't found, a formal request is generated and queued.
4. **Human review.** A person approves or rejects each draft on a protected web page. Only approval sends the email.

**Engineering decisions**
- **Human review by design.** LLM output can be wrong, so the system can produce a draft but never an unreviewed email.
- **One request per document.** Enforced by database constraints.
- **Careful scraping.** Retries with exponential backoff, and "not found" is recorded separately from "could not check".
- **Security.** Authentication on every route, blocking of cross-site requests, a strict Content-Security-Policy, and HTML-escaping of all LLM and scraped text.
- **Tested and containerised.** 41 pytest tests, Docker image, scheduled polling with APScheduler.

**Stack:** Python · FastAPI · Pydantic · SQLAlchemy · PostgreSQL · aiohttp · Playwright · Gemini API · Docker

## Other work

- **Procurement data project (short-term):** helped a construction procurement platform move procurement data into Snowflake, and built a Python/SQL pipeline to clean, validate and load it.

## Contact

[LinkedIn](https://www.linkedin.com/in/nikola-nedelkovski047/) · nedelkovski08@gmail.com
