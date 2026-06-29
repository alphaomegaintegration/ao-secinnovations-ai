# SEC AI Proof-of-Value Program — AWS PAiTH

**Deploying trusted AI for the U.S. Securities and Exchange Commission on the Private AI Tech Hub (PAiTH).**

This repository contains the presentation and supporting materials for a set of mission-aligned
AI Proof-of-Value (POV) demos — for the Divisions of **Enforcement**, **Economic and Risk Analysis (DERA)**,
and **Examinations** — built with **Continuum Design**, deployed on **Amazon Bedrock** inside the secure
**AWS PAiTH** landing zone, and protected with **Zscaler** zero-trust access and **SPLX.ai** red-teaming.

> **Confidential.** Prepared by Alpha Omega for U.S. SEC review. Please limit distribution to intended recipients.

---

## 📺 How to review the presentation

There are three ways to view the deck — pick whichever is easiest.

### 1. Online (recommended) — GitHub Pages
The presentation is hosted live at:

**➡️ https://alphaomegaintegration.github.io/ao-secinnovations-ai/**

The landing page links straight to the interactive slides and the downloadable PDF. Nothing to install.

### 2. Interactive PDF
Open **[`SEC-PAiTH-POV-Presentation.pdf`](SEC-PAiTH-POV-Presentation.pdf)** in any PDF reader.
It is a 10-page, 16:9 interactive document with:

- a **bookmarks panel** for jumping to any section,
- a **clickable agenda** (each item links to its slide), and
- **live hyperlinks** to all referenced source repositories.

### 3. Interactive HTML slides (offline)
Download and open **[`SEC-PAiTH-POV-Presentation.html`](SEC-PAiTH-POV-Presentation.html)** in any modern
browser. It runs entirely offline (no server needed).

| Key | Action |
|-----|--------|
| `→` / `Space` | Next slide |
| `←` | Previous slide |
| `F` | Toggle fullscreen |
| Click dots (bottom) | Jump to a slide |

---

## 🗂️ Agenda

1. **PAiTH** — the secure, governed home for federal generative AI (foundation + architecture).
2. **Continuum Design** — Alpha Omega's AI modeling engine that turns ideas into working systems in hours.
3. **SEC "Fed Claw" Fraud Monitor** *(Enforcement)* — asset recovery before funds go dark.
4. **Agentic Examiner** *(EXAMS)* — automated pre-exam intelligence; **ready to demo live**.
5. **Zscaler + SPLX** — zero-trust access plus continuous AI red-teaming.
6. **XBRL Quality Guard** *(DERA)* — filing-data integrity, **proven in 2 weeks**.

A closing slide consolidates the measurable business value across all initiatives.

---

## 📦 Repository contents

| File / folder | Description |
|---------------|-------------|
| `index.html` | GitHub Pages landing page (links to the deck + PDF). |
| `SEC-PAiTH-POV-Presentation.html` | The interactive slide deck (HTML). |
| `SEC-PAiTH-POV-Presentation.pdf` | The interactive PDF version (bookmarks + links). |
| `POV-REPOS.md` | Index of each POV, its SEC division, ROI, and source repositories. |
| `agentic-exam-assistant/` | Live demo source — *its own repository* (see [Live demo](#-live-demo-agentic-examiner)). Not tracked here. |

---

## 🛡️ Platform & security summary

- **Deployment:** AWS PAiTH — Amazon Bedrock, EKS, Cognito, CloudWatch, DynamoDB, S3, and MemoryDB inside a
  secure VPC landing zone, with **Bedrock Guardrails** (denied topics, PII redaction, content filters).
- **Zero-trust access:** **Zscaler** — zero-trust network access, full SSL inspection, cloud firewall, and
  inline DLP on all traffic.
- **AI assurance:** **SPLX.ai** — automated, continuous red-teaming (prompt-injection, jailbreak, and
  data-exfiltration testing) with audit-ready findings mapped to federal AI risk frameworks.
- **Defense in depth:** Zscaler zero-trust → Cognito auth → Bedrock Guardrails → SPLX.ai red-team → audit archive.

---

## ▶️ Live demo: Agentic Examiner

The Agentic Examiner is maintained as its **own repository** (it carries its own history and local secrets,
so it is intentionally **not** committed here):

**https://github.com/alphaomegaintegration/agentic-exam-assistant**

To run it locally:

```bash
git clone https://github.com/alphaomegaintegration/agentic-exam-assistant.git
cd agentic-exam-assistant
cp .env.example .env        # then add your own API key(s)
pip install -r requirements.txt
./run.sh                    # opens the Streamlit app at http://localhost:8501
```

It is a Streamlit web app that pulls a firm's ADV filings, prior exam deficiencies, and news sentiment to
build an explainable "Risk Briefing Book." It uses live SEC EDGAR data with an offline fallback.

> ⚠️ **Never commit API keys.** The demo's `.env` is git-ignored. Use `.env.example` as the template and keep
> real keys local. This static review repository (and GitHub Pages) serves only the slides and PDFs — no secrets.

---

## ▶️ Live demo: Fed Claw Fraud Monitor

The "Fed Claw" Fraud Monitor *(Division of Enforcement)* is maintained as its **own repository**:

**https://github.com/alphaomegaintegration/secfedclaw-watch-v2**

A connection-aware securities-surveillance prototype that fuses social, market, and official
(SEC/FINRA/Nasdaq) signals into non-accusatory **review-priority packages** for authorized human review —
the interactive **dashboard is the product surface**. It runs **fully offline in replay mode with zero
credentials**, so it demos anywhere; add a `.env` later to go live.

Run the offline replay demo (no API keys needed):

```bash
git clone https://github.com/alphaomegaintegration/secfedclaw-watch-v2.git
cd secfedclaw-watch-v2
python3 -m venv .venv && . .venv/bin/activate     # Windows: .venv\Scripts\activate
pip install -r requirements-dev.txt               # numpy; the scan/scoring core is stdlib-only

python3 scan.py --no-live --tickers AAPL TSLA AMC GME   # score a universe from cached artifacts
python3 dashboard_v2.py                                 # build out/dashboard_v2.html
python3 serve.py                                        # prints a tokenized 127.0.0.1:8787 URL — open it
```

To go **live** on real market/social data, add credentials and run preflight first:

```bash
cp .env.example .env     # POLYGON_API_KEY, SEC_USER_AGENT, GEMINI_API_KEY, …
python3 preflight.py                     # per-source readiness: GO / DEGRADED / REPLAY
python3 scan.py --live --discover 25     # scan defaults + the top-25 live movers
```

> 💡 **Demo tip:** the default mega-cap universe correctly scores **LOW** — use `--discover` to pull the
> thin/micro-cap movers that actually surface coordination flags. (A Docker path also exists:
> `docker compose up -d dashboard`, then read the access token from `docker compose logs dashboard`.)
> **WATCH-only** — review-priority signals for human analysts, never trading actions or accusations;
> `serve.py` binds to `127.0.0.1` and is token-gated, so don't expose it publicly.

---

## ▶️ Live demo: XBRL Quality Guard

The XBRL Quality Guard *(DERA)* is an agentic-AI auditor for SEC XBRL filings that uses Claude on Amazon
Bedrock as a **reasoner over deterministic XBRL tooling** (Arelle + the live US-GAAP taxonomy) to flag
likely tagging errors before they reach DERA's economic models. It is maintained in its **own repositories**:

**https://github.com/alphaomegaintegration/continuum-xbrl-quality-guard** (core)
**https://github.com/alphaomegaintegration/CD-sec-demo** (Databricks pipeline)

Unlike the other two, this demo is **AWS-backed** (Bedrock, Aurora/Postgres, S3, OpenSearch) — not a
zero-credential local run. Prerequisites: Python 3.11+, Node 20+, Docker 24+, an SEC `User-Agent` email, and
an AWS account with Bedrock model access (Claude Sonnet 4.5, Haiku 4.5, Titan Embeddings v2).

Stand it up:

```bash
git clone https://github.com/alphaomegaintegration/continuum-xbrl-quality-guard.git
cd continuum-xbrl-quality-guard
make bootstrap          # create .venv, install deps, validate AWS creds
cp .env.example .env    # configure AWS, Postgres, EDGAR, and Bedrock settings
bash infra/bootstrap.sh # provision S3 buckets, RDS cluster, ECR repos

docker compose up --build               # start the MCP servers (edgar / arelle / taxonomy)
make ingest                             # pull ~1,000 smaller-reporting-company filings to S3
make scan                               # orchestrator audits every filing
streamlit run src/reviewer_ui/app.py    # open the DERA reviewer queue (human-in-the-loop)
```

> 🔒 **Access & secrets:** these repositories are **private** — request access if your clone is denied.
> AWS/Bedrock credentials resolve from the standard AWS chain; never commit keys (`.env` is git-ignored).
> The repo's `XBRL_Quality_Guard_Technical_Execution_Plan.md` is the full engineering runbook.

---

## 📚 Referenced source repositories

| POV | Division | Repository |
|-----|----------|------------|
| Fed Claw Fraud Monitor | Enforcement | `alphaomegaintegration/secfedclaw-watch-v2` |
| XBRL Quality Guard | DERA | `alphaomegaintegration/continuum-xbrl-quality-guard` · `CD-sec-demo` |
| Agentic Examiner | EXAMS | `alphaomegaintegration/agentic-exam-assistant` |

See [`POV-REPOS.md`](POV-REPOS.md) for full details on each POV, including problem statements, quick-win
prototypes, and projected ROI.

---

*Prepared by Alpha Omega · Creating New Possibilities · for U.S. SEC review. Confidential.*
