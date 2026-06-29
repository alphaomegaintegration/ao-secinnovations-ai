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
Once Pages is enabled (see [Enabling GitHub Pages](#-enabling-github-pages-one-time-repo-admin) below), the
presentation is hosted at:

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
| `index.html` | GitHub Pages landing page (links to the deck + PDFs). |
| `SEC-PAiTH-POV-Presentation.html` | The interactive slide deck (HTML). |
| `SEC-PAiTH-POV-Presentation.pdf` | The interactive PDF version (bookmarks + links). |
| `AWS-PAiTH-Overview.pdf` | Supporting overview of the AWS PAiTH platform. |
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

## ⚙️ Enabling GitHub Pages (one-time, repo admin)

1. Push this repository to GitHub (`alphaomegaintegration/ao-secinnovations-ai`) — see below.
2. In the repo on GitHub, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Set **Branch** to `main` and **folder** to `/ (root)`, then click **Save**.
5. Wait ~1 minute, then refresh. The site goes live at:
   **https://alphaomegaintegration.github.io/ao-secinnovations-ai/**

To push for the first time:

```bash
git add .
git commit -m "Add SEC PAiTH POV presentation, PDF, and reviewer materials"
git push -u origin main
```

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
