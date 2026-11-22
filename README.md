# Know Your Leader — Maharashtra Assembly Transparency Portal

> *"Before you press the button, know who you're voting for."*

**Submitted Module:** Aatish Das — User Interface (HTML / Jinja2 Templates)  
**Institution:** MIT World Peace University (MIT WPU) — B.Tech CSE Core (Div 6, Batch 2)  
**Alignment:** UN SDG 16 (Peace, Justice & Strong Institutions) · Digital India

---

## Project Overview

**Know Your Leader** is a transparency web portal built using **Python (Flask)**, **HTML/Jinja2**, and **CSS** that presents verified public records for all **288 sitting MLAs** and **4,144 candidates** across the Maharashtra Legislative Assembly (2024 General Election and 2026 bye-elections).

The portal brings together:
- **Sworn Form 26 Affidavits (ADR / MyNeta):** Movable and immovable assets, liabilities, 5-year ITR income trails, education, age, and case-by-case pending criminal cases or convictions.
- **Election Mandates (ECI):** Votes polled, vote share percentages, victory margins, and runner-up comparisons.
- **Accountability Tracking:** MLA Local Area Development (LAD) fund allocations vs. verified spending, constituency development works, and party manifesto pledge tracking.

---

## My(Aatsih Das) Contribution — User Interface (`templates/`)

This repository contains the complete **User Interface layer (9 HTML/Jinja2 templates · 519 lines)** rendered server-side by the Flask backend:

| Template File | Lines | Page / Component Description |
| :--- | :---: | :--- |
| `templates/base.html` | 29 | Master layout template featuring the sticky navigation bar (`MLAs`, `How we work`, `Compare`), CSS/favicon links, Jinja2 `{% block content %}` slot, and footer attribution. |
| `templates/cover.html` | 21 | Full-screen election landing screen (*Opening D* design) with animated ballot-stamp graphic and portal entry call-to-action. |
| `templates/home.html` | 70 | Main dashboard displaying 6 live house-statistic cards, party seat-share horizontal bar chart, search/party/district/sort filter bar, and the 288-MLA card grid. |
| `templates/mla.html` | 155 | Detailed MLA profile template rendering mandate vote bars, case-by-case criminal record tables, ITR income bar charts, asset/liability breakdowns, LAD fund tables, and party manifesto pledge statuses. |
| `templates/patil.html` | 113 | Flagship fully-researched profile template for **Chandrakant Patil (Kothrud)**, including 2019–2024 asset growth comparisons, watch-list flags, development works, and an SVG donut chart for manifesto delivery. |
| `templates/ac.html` | 47 | Constituency view (`/ac/<acno>`) displaying SC/ST/General reservation status, 2024 result summary, and reusable Jinja2 macros (`cand_table`) for general and bye-election candidate rosters. |
| `templates/compare.html` | 34 | Side-by-side comparison page (`/compare`) allowing users to select any two sitting MLAs and compare party, assets, liabilities, criminal cases, education, and election margins. |
| `templates/how.html` | 44 | Methodology and transparency rules page (*"No source, no number"*, *"Declared ≠ convicted"*) along with the dataset coverage summary table. |
| `templates/404.html` | 6 | Custom error page extending `base.html` for invalid MLA or constituency routes. |

### Key UI & Jinja2 Features Implemented
- **Template Inheritance & Macros:** Shared navigation and footer structure via `{% extends "base.html" %}` and reusable candidate roster tables via `{% macro cand_table %}` in `ac.html`.
- **Dynamic Data Rendering:** Server-side Jinja2 loops, conditional badges (`Crorepati`, `Deep Profile`, `Woman MLA`, `bye 2026`), and custom Python formatting helpers (`inr()`, `cr()`, `initials()`, `p_color()`).
- **Data Visualisations:** Pure HTML/CSS horizontal vote-share bars, vertical ITR income bars, and dynamic SVG `<circle>` dash-array segments for the manifesto promise donut chart.

---

## How to Run (Full Application Integration)

When combined with the backend (`app.py`), stylesheet (`static/css/`), and dataset (`data/portal_data.json`):

```bash
# 1. Install Flask
pip install flask

# 2. Start the local server
python app.py

# 3. Open in your browser
[http://127.0.0.1:5000](http://127.0.0.1:5000)


Team Credits (MIT WPU — B.Tech CSE)

Chirag Jadhav — Member 1: Research & Data Filling (data_pipeline/ · Python)

Aatish Das— Member 2: User Interface (templates/ · HTML / Jinja2)

Mughdha kirve 3 — Member 3: Images, Colour Palette & Styling (static/ · CSS / SVG)

Gaurav singh 4 — Member 4: Application Logic & Automated Browser Testing (app.py, test_flask.py · Python)

(Team roster: Chirag Jadhav · Mugdha Kirve · Aatish Das · Gaurav Singh)

Disclaimer
All candidate figures are sourced from self-sworn Form 26 affidavits (ADR / MyNeta) and Election Commission of India (ECI) records. Declared criminal cases are pending cases as filed and do not imply conviction. This portal presents verified public facts without ranking or political endorsement
