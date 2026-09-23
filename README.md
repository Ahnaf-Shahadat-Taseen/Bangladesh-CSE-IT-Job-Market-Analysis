<div align="center">

# 🇧🇩 Bangladesh CSE / IT Job Market Analysis

### Interactive Power BI–style dashboard built on 337 live job postings from bdjobs.com


</div>

---

## 📖 Overview

This project answers a question every Computer Science & Engineering student in Bangladesh asks:

> **"What are companies actually hiring for right now, and what skills do I need?"**

Instead of guessing from anecdotes, this repo collects **real job postings** from Bangladesh's largest employment marketplace ([bdjobs.com](https://bdjobs.com)) and turns them into an **interactive, self-contained analytics dashboard** — no Power BI license, no Tableau, no server, no internet connection required.

Everything runs in a single HTML file you can double-click.

---

## 🚀 Live Demo

If you enable **GitHub Pages** on this repo (Settings → Pages → Branch: `main` → `/root`), the dashboard is instantly hosted at:

```
https://<your-username>.github.io/<repo-name>/cse_job_market_dashboard.html
```

Or just clone and open locally:

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
open cse_job_market_dashboard.html      # macOS
start cse_job_market_dashboard.html     # Windows
xdg-open cse_job_market_dashboard.html  # Linux
```

> 💡 **No build step. No `npm install`. No dependencies.** The dataset is embedded directly in the HTML file.

---

## 📊 Dashboard

A fully interactive business-intelligence report modelled on the Power BI look and feel.

### 🎛 Dropdown Slicers (7)

| Slicer | Description |
|---|---|
| **Role Category** | Software Engineer, Web Developer, Data/AI, Network, Cyber Security, QA, DevOps, IT Management, etc. |
| **Experience** | Entry (0–1 yr) · Junior (2–3) · Mid (4–5) · Senior (6–8) · Lead (8+) |
| **Location** | Dhaka, Chattogram, Gazipur, Sylhet, Anywhere in BD, and more |
| **Skill** | Python, JavaScript, SQL, Networking, ERP, Data Analysis, … |
| **Job Type** | Full-time · Contract · Internship · Part-time · Freelance |
| **Workplace** | Office · Home · Hybrid |
| **Month** | Jul 2026 · Aug 2026 · Sep 2026 |

Each slicer is a real checkbox dropdown with an **internal search box**, **Select all / Clear**, and a **live record count next to every item**. Slicers **cross-filter each other** — selecting `Role = Data / AI` instantly narrows the Skill and Location lists to only what's relevant, exactly like Power BI.

### 📈 KPI Cards (6)

| KPI | What it tells you |
|---|---|
| **Job Postings** | Postings in the current filter scope (+ % of total) |
| **Total Vacancies** | Open seats, plus average seats per posting |
| **Hiring Companies** | Unique employers, plus posts per employer |
| **Avg Salary (BDT)** | Mean disclosed monthly salary + how many posts disclosed it |
| **Fresher Friendly** | % of roles requiring ≤ 3 years of experience |
| **Dhaka Share** | % of postings concentrated in the capital |

All six recalculate instantly on every filter change.

### 📉 Visuals (7)

| Visual | Type | Interaction |
|---|---|---|
| Hiring Trend Over Time | Gradient area + line chart | Hover for weekly tooltips |
| Role Category Mix | Donut with center total | Click a slice or legend to filter |
| Top In-Demand Skills | Horizontal bar chart | Click a bar to filter by skill |
| Top Hiring Companies | Horizontal bar chart | Ranked by posting count |
| Jobs by Location | Horizontal bar chart | Click a bar to filter by district |
| Experience Level Demand | Clustered bar (postings vs vacancies) | Click a level to filter |
| **Role × Experience Matrix** | Heat map | Click a cell → applies **two filters at once** |
| Job Listings Detail | Sortable 10-column table | Click any header to sort · direct links to the live posting |

### ✨ Extra Features

- 🌓 **Light / Dark theme** toggle
- ↺ **Reset filters** button + removable filter chips
- ⭳ **Export data** — downloads only the currently filtered rows as CSV (UTF-8 BOM, Excel-safe)
- 📱 Responsive grid — reflows cleanly on laptop, tablet, and phone
- 🔒 **100% offline** — no CDN, no external fonts, no tracking, no API calls at runtime

---

## 📁 Dataset

### `bd_cse_job_market_last3months.csv`

**337 rows · 14 columns · UTF-8 with BOM** (opens cleanly in Excel)

| Column | Type | Description | Example |
|---|---|---|---|
| `position` | text | Official job title as published | `Software Engineer` |
| `skills` | text | Semicolon-separated skill list | `Python; MySQL; REST API` |
| `experience` | text | Experience requirement as stated by employer | `2 to 3 years` |
| `company_name` | text | Hiring organisation | `Betopia Group` |
| `job_locations` | text | Work location(s) | `Dhaka` |
| `education` | text | Required degree / academic background | `BSc in Computer Science & Engineering` |
| `job_type` | text | Employment nature | `FullTime` |
| `workplace` | text | Office / Home / Hybrid | `Office` |
| `vacancies` | integer | Number of open positions | `3` |
| `salary` | text | Salary range or `Negotiable` | `Tk. 40000 - 60000 (Monthly)` |
| `posted_date` | date | Publication date (`YYYY-MM-DD`) | `2026-09-23` |
| `deadline` | date | Application deadline (`YYYY-MM-DD`) | `2026-10-15` |
| `source` | text | Data origin | `bdjobs.com` |
| `job_url` | url | Direct link to the original posting | `https://bdjobs.com/h/details/1537213` |

### `data.json`

The same 337 records **enriched for analytics**, used by the dashboard:

- `role` — postings auto-classified into **15 role categories** via title keyword rules
- `exp` — free-text experience normalised into **6 seniority buckets**
- `skills` — parsed into a clean **array** instead of a delimited string
- `salary` — numeric monthly BDT midpoint parsed from the salary text (`null` when negotiable)
- `loc` — location strings normalised (primary district extracted, trimmed)

### Coverage

| Dimension | Value |
|---|---|
| Collection date | 23 September 2026 |
| Posting window | 22 July 2026 → 23 September 2026 |
| Total postings | **337** |
| Unique companies | **264** |
| Total vacancies | **695** |
| Postings with explicit skills | **335 / 337 (99.4%)** |
| Postings with disclosed salary | **102 (30.3%)** |
| Source | bdjobs.com public job-search API |

---

## 💡 Key Insights

### 🔝 Most In-Demand Skills

| Rank | Skill | Postings |
|---|---|---|
| 1 | Software Development | 26 |
| 2 | JavaScript | 26 |
| 3 | LAN / WAN Networking | 22 |
| 4 | Troubleshooting | 22 |
| 5 | IT Support Service | 20 |
| 6 | Python | 19 |
| 7 | SEO / Digital Marketing | 19 |
| 8 | Data Analysis | 18 |
| 9 | MySQL | 18 |
| 10 | ERP Software | 17 |

> **Takeaway:** the BD market rewards **breadth over depth**. Pure coding roles compete with a very large volume of *IT support, networking and ERP* roles. A CSE graduate who pairs programming with networking or ERP fundamentals has a far wider funnel.

### 📊 Role Distribution

```
Other IT / General         ████████████████████  99
IT Management              ████████              42
IT Support / Admin         ██████                29
Network / Infrastructure   ██████                28
Software Engineer          ██████                28
Database / ERP             ████                  21
Web Developer              ████                  20
Data / AI                  ███                   17
Digital Marketing / SEO    ███                   14
UI/UX & Design             ██                    12
Mobile App Developer       ██                     8
QA / Testing               █                      6
Trainer / Academic         █                      5
DevOps / Cloud             █                      4
Cyber Security             █                      4
```

### 🎓 Experience Demand

| Level | Postings | Share |
|---|---|---|
| 2–3 yrs (Junior) | 113 | 33.5% |
| Not specified | 92 | 27.3% |
| 4–5 yrs (Mid) | 64 | 19.0% |
| 0–1 yrs (Entry) | 36 | 10.7% |
| 6–8 yrs (Senior) | 21 | 6.2% |
| 8+ yrs (Lead) | 11 | 3.3% |

> **Takeaway:** only **~11%** of postings are true entry-level, but **44%** are open to candidates with ≤ 3 years. The hardest jump in the Bangladeshi CSE career ladder is **0 → 2 years** — internships and personal projects matter enormously.

### 📍 Geographic Concentration

**Dhaka = 254 of 337 postings (75.4%)**, followed by Anywhere-in-BD (36), Chattogram (13), Gazipur (11), Narayanganj (4). The market is overwhelmingly capital-centric, and remote/"anywhere" roles are the second-largest category.

### 💰 Salary

Only **30%** of postings disclose a salary. Among those, the **average disclosed monthly salary is ≈ BDT 44,000**. The majority are listed as *Negotiable*, so treat this figure as indicative, not definitive.

### 🏢 Top Hiring Employers

Betopia Group (12) · PKSF (7) · BURO Bangladesh (6) · Bangladesh Labour Foundation (4) · BYSL Global Technology Group (4) · BRACNet Limited (4) · KSF Luxury Homes (3) · ZTE Corporation (3) · Excel Technologies (3)

> Notably, **NGOs and development agencies** (PKSF, BURO, BLF, Red Crescent) are significant IT employers in Bangladesh — a channel most CSE students overlook.

### 🧭 Underserved, High-Opportunity Niches

**Cyber Security (4)**, **DevOps / Cloud (4)**, and **QA / Testing (6)** have the *fewest* postings — but that also means the *least* competition. These are the fastest-growing global specialisations and remain thin in the local supply pool.

---

## 🔧 How It Was Built

### Pipeline

```
┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐   ┌──────────────────┐
│  1. COLLECT      │──▶│  2. FILTER       │──▶│  3. ENRICH       │──▶│  4. VISUALISE    │
│  bdjobs public   │   │  CSE/IT relevance│   │  role, seniority │   │  single-file     │
│  job-search API  │   │  + 3-month window│   │  skills, salary  │   │  HTML dashboard  │
│  3,114 raw posts │   │  → 337 postings  │   │  → data.json     │   │  SVG + vanilla JS│
└──────────────────┘   └──────────────────┘   └──────────────────┘   └──────────────────┘
```

**1 · Collection.** The bdjobs front-end is an Angular SPA, so the HTML contains no job data. Inspecting the compiled bundle revealed the public search endpoint `api.bdjobs.com/Jobs/api/JobSearch/GetJobSearch`. Paginating the IT/Telecom category plus **24 CSE-related keyword queries** (`software engineer`, `machine learning`, `devops`, `cyber security`, …) yielded **3,114 raw postings**.

**2 · Filtering.** Deduplicated by job ID, restricted to the 3-month window, and kept only postings that are in the IT category *or* have a CSE/IT-relevant title **and** a computing degree requirement → **337 postings**.

**3 · Enrichment.** Each posting's detail record was fetched for the employer-declared skill list. Where absent, skills were extracted from the job description against a **100-term technology dictionary**. Titles were classified into 15 role categories by regex; experience text was normalised into 6 seniority buckets; salary strings were parsed to numeric BDT.

**4 · Visualisation.** All charts are **hand-written SVG** with vanilla JavaScript — no Chart.js, no D3, no React. This keeps the dashboard a single portable file that works offline forever and will never break from a CDN going down.

### Tech Stack

`Python` · `requests` · `pandas` · `BeautifulSoup` · `HTML5` · `CSS3 Grid` · `Vanilla JavaScript (ES6)` · `Inline SVG`

---

## 📂 Repository Structure

```
.
├── cse_job_market_dashboard.html    # ⭐ Main deliverable — open this in any browser
├── index.html                       # Copy of the dashboard for GitHub Pages hosting
├── bd_cse_job_market_last3months.csv# Clean tabular dataset (337 × 14)
├── data.json                        # Enriched analytics-ready records
├── analysis_summary.md              # Plain-text statistical summary
└── README.md                        # You are here
```

---

## 🎯 Who Is This For?

- **CSE / IT students** planning which stack to learn before graduation
- **Job seekers** benchmarking salary expectations and experience requirements
- **Career counsellors & universities** aligning curriculum with market demand
- **Recruiters & HR analysts** studying the competitive hiring landscape
- **Data analysts** looking for a compact, real-world BI portfolio project

---

## ⚠️ Limitations & Honest Caveats

- **Single source.** Data comes only from bdjobs.com. Many startups and international companies hire through LinkedIn, Facebook groups, or private referrals and are therefore not represented.
- **Snapshot, not a census.** Captures postings visible on 23 Sep 2026; expired listings older than the platform's retention are missing, which is why July is sparsely populated.
- **Posting ≠ hire.** A job advertisement does not guarantee an actual hire, and one posting may fill multiple or zero seats.
- **Salary bias.** Only 30% disclose pay, and those that do skew toward NGO and fixed-grade roles, so the average is not representative of the private tech sector.
- **Rule-based classification.** Role categories and skill extraction use keyword rules, not machine learning — expect a small margin of misclassification, particularly in the "Other IT" bucket.

---

## 🔄 Reproducing / Updating the Data

The dashboard reads `data.json`, which is embedded at build time. To refresh with newer postings:

1. Re-run the collection against the bdjobs search endpoint for your desired window.
2. Regenerate `bd_cse_job_market_last3months.csv` and `data.json` with the same schema.
3. Replace the `const DATA = [...]` array inside `cse_job_market_dashboard.html` with the new JSON.

No other change is needed — every visual, KPI and slicer is derived dynamically from that array.

---

## 🤝 Contributing

Contributions are welcome. Good first issues:

- Add additional sources (LinkedIn, Skill.jobs, Shomvob) for broader coverage
- Improve the role classifier (ML-based instead of regex)
- Add a salary-distribution box plot and a skill co-occurrence network
- Build a scheduled GitHub Action to refresh the dataset monthly

Open an issue to discuss, then submit a pull request.

---

## 📄 License

Released under the **MIT License** — free to use, modify and distribute with attribution.

**Data attribution:** job posting information is publicly available on [bdjobs.com](https://bdjobs.com) and remains the property of the respective employers. This dataset was compiled strictly for **educational and research purposes**. Please respect bdjobs.com's terms of service and do not use this data for commercial redistribution or unsolicited outreach.

---

<div align="center">

**⭐ If this helped you plan your CSE career, consider starring the repo.**

*Built with real data, not assumptions.*

</div>
