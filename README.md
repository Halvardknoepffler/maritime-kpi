Interactive KPI Dashboard — Vulnerabilities &amp; Strengths of the French Maritime Supply Chain | KEDGE P42
# MaritimeKPI Dashboard

**Vulnerabilities & Strengths of the French Maritime Supply Chain**  
KEDGE Business School — MSc Global Supply Chain — Promotion P42 — 2025

> An interactive KPI dashboard measuring port capacity utilization, chokepoint dependency, and supply chain resilience across the Energy and Agri-Food sectors. Built for public port authorities, policymakers, and maritime companies.

---

## Team

| Name | Role |
|------|------|
| Arabi Zhour | Project lead — Vulnerabilities & Literature Review |
| Yu Bingqin | Energy sector |
| Elayen Chaimae | Agri-Food sector |
| Bacha Wissam | KPIs & Methodology |
| Knoepffler Halvard | Strengths & Dashboard |

**Tutors:** Nadine Kafa (KPIs / SCM) · Pierre Cariou (Maritime SC)

---

## Live Site

```
https://halvardknoepffler.github.io/maritime-kpi
```

---

## Tech Stack

| Element | Details |
|---------|---------|
| Language | HTML5 / CSS3 / Vanilla JavaScript |
| Charts | Chart.js 4.4.0 (loaded via CDN — no install needed) |
| Fonts | Google Fonts — Playfair Display + Outfit |
| Framework | None — single file, no build step |
| Hosting | GitHub Pages |
| Data | Static — hardcoded from official sources |

---

## File Architecture

Everything lives in a **single file: `index.html`**.

```
index.html
│
├── <head>         Google Fonts + Chart.js CDN links
├── <style>        All CSS — CSS variables, layout, components
├── <body>
│   ├── <nav>      Fixed top navigation bar
│   ├── <aside>    Left sidebar with KPI links
│   └── <main>
│       ├── #sec-home        Overview — hero, risk score, stats, timeline
│       ├── #sec-capacity    Capacity Utilization KPI (core KPI)
│       ├── #sec-trade       Throughput Growth, EU Market Share, HHI
│       ├── #sec-choke       Chokepoint Dependency, Port Dependency
│       ├── #sec-whatif      Interactive What-If scenarios
│       ├── #sec-bench       International Benchmarking
│       ├── #sec-sources     Data Sources & Methodology
│       ├── #sec-recos       Recommendations
│       └── #sec-glossary    KPI Glossary
└── <script>       All JavaScript — navigation, chart init, slider logic
```

**How sections work:** Each section is `display:none` by default. The `goTo(page)` function shows the target section and hides all others. Charts are initialized lazily (only when the section is first visited) to improve load speed.

---

## Design System

| Variable | Value | Usage |
|----------|-------|-------|
| `--navy` | `#0e2340` | Nav, headers, primary dark |
| `--gold` | `#b8914a` | Accent, active states, hero highlights |
| `--bg` | `#f7f6f2` | Page background (warm off-white) |
| `--surface` | `#ffffff` | Cards, sidebar |
| `--red` | `#8b1a2a` | High risk indicators |
| `--amber` | `#c08000` | Sensitive zone indicators |
| `--green` | `#1e6b43` | Comfortable zone indicators |
| `--font-d` | Playfair Display | All titles and KPI values |
| `--font-b` | Outfit | Body text, labels, buttons |

**Aesthetic direction:** Scandinavian minimal — light background, generous whitespace, serif display font, no emojis, muted gold accent.

---

## Data Sources

| Source | URL | KPIs Used |
|--------|-----|-----------|
| SDES — Statinfo Ports Maritimes | statistiques.developpement-durable.gouv.fr | Capacity Utilization, Port Dependency, Throughput Growth |
| Eurostat — Maritime Transport | ec.europa.eu/eurostat | EU Market Share, Geo. Diversification |
| UN Comtrade Plus | comtradeplus.un.org | Chokepoint CDR, Trade Overview, Benchmarking |
| CRE — Régulation Énergie | cre.fr | LNG Terminal Capacity, ATTM7 decisions |
| UNCTAD — LSCI | unctadstat.unctad.org | Port Connectivity Score |
| Academic Literature | — | Vulnerability framework, What-If basis |

### Key academic references
- Jiang et al. (2023) — chokepoint vulnerability
- Bedoya-Maya et al. (2025) — Suez rerouting impact (AIS data)
- Verschuur, Lumma & Hall (2025) — climate & security shocks
- Oral & Paker (2023) — maritime cybersecurity
- Wendler-Bosco & Nicholson (2020) — port disruptions & delay rate
- Merk et al. (2011) — Seine axis benchmarking
- Ang, C. (2021) — maritime chokepoint mapping

---

## KPIs — Formulas & 2024 Values

### Capacity Utilization Ratio (Core KPI)
```
CUR = Throughput_2024 / Max(Throughput_2000–2024)
```
**Methodology:** Since official design capacity is unavailable, we use the maximum historical throughput as a proxy (MAT/HEAT framework).

| Port | Sector | 2024 | Max Historical | CUR |
|------|--------|------|----------------|-----|
| Dunkerque | Gas (Import) | 8.39 Mt | 9.76 Mt | **85.9% — High Risk** |
| Marseille | Gas (Import) | 7.89 Mt | 10.11 Mt | **78.0% — Sensitive** |
| Nantes Saint-Nazaire | Gas (Import) | 4.73 Mt | 8.77 Mt | **53.9% — Comfortable** |
| HAROPA | Gas (Import) | 0.75 Mt | 1.39 Mt | **54.3% — Comfortable** |
| HAROPA | Cereals (Export) | 7.04 Mt | 8.94 Mt | **78.8% — Sensitive** |
| La Rochelle | Cereals (Export) | 3.0 Mt | 4.41 Mt | **68.2% — Comfortable** |
| Dunkerque | Cereals (Export) | 1.28 Mt | 3.07 Mt | **41.8% — Comfortable** |
| Nantes Saint-Nazaire | Cereals (Export) | 0.54 Mt | 1.89 Mt | **28.8% — Comfortable** |

**Thresholds:** Below 70% = Comfortable · 70–85% = Sensitive · Above 85% = High Risk

### Port Dependency Ratio
```
PDR = Volume_port / Total_national_flows
```

**Energy imports 2024 (Source: SDES):**
- Marseille: 34.4% · HAROPA: 27.5% · Dunkerque: 13.2% · Nantes: 12.2%

**Cereal exports 2024 (Source: SDES):**
- HAROPA: 52.2% · La Rochelle: 22.3% · Dunkerque: 9.5% · Nantes: 4.0%

### Other KPIs
```
Throughput Growth  = (T_t − T_{t-1}) / T_{t-1}
EU Market Share    = Throughput_France / Throughput_EU
HHI (Geo. Div.)   = Σ(Share_basin)²
CDR (Chokepoint)  = Chokepoint_flows / Total_flows
LSCI (Connectivity) = UNCTAD index (~260 in 2024, down from ~290 in 2017)
MTDR (Delay Rate)  = Disruption_days / Total_days
```

---

## Real Throughput Data (SDES — Energy Imports, all French ports)

| Year | Total (Mt) | YoY Growth |
|------|------------|------------|
| 2020 | 99.7 | −16.2% |
| 2021 | 99.6 | −0.1% |
| 2022 | 116.7 | +17.2% |
| 2023 | 111.5 | −4.5% |
| 2024 | 107.3 | −3.7% |

---

## How to Deploy on GitHub Pages

1. Go to [github.com/new](https://github.com/new)
2. Create a public repository named `maritime-kpi`
3. Upload `index.html` (rename from `maritime-dashboard-v3.html`)
4. Go to **Settings → Pages → Branch: main → / (root) → Save**
5. Wait 2–3 minutes → live at `https://YOUR_USERNAME.github.io/maritime-kpi`

---

## How to Update the Data

All data is hardcoded in the `<script>` section at the bottom of `index.html`.

| What to update | Where in the code |
|----------------|-------------------|
| Hero ship image | CSS `.hero-bg` → `background:` URL |
| Capacity bar values | HTML — `style="width:XX%"` on `.cap-f` elements + `.cap-p` text |
| Port dependency charts | JS `initPD()` function — `data:[]` arrays |
| Throughput growth chart | JS `TOT[]` and `GRW[]` arrays near top of script |
| EU Market Share chart | JS `initEU()` function — dataset `data:[]` arrays |
| Risk score | HTML — `.rb-rn` (number) and `.rb-rt` (label) |
| Stat cards | HTML — `.sc-v` values in `#sec-home` |
| Timeline events | HTML — `.tl-i` blocks in `#sec-home` |
| What-if scenarios | HTML — `.sp` panels + JS `upH()` function for Hormuz slider |
| Benchmark table | HTML — `.bt tbody` rows |
| Recommendations | HTML — `.rc` items in `#sec-recos` |

---

## Planned Updates (V4)

- [ ] Replace hero image with real cargo ship at sea (URL ready)
- [ ] Integrate Bingqin's exact Energy throughput growth values + EU market share
- [ ] Integrate Chaimae's exact Agrifood throughput growth + port dependency values
- [ ] Integrate Wissam's final KPI formulas + delay rate values
- [ ] Add Zhour's exact Chokepoint Dependency Ratio values per chokepoint
- [ ] Add new What-If scenario: Oil price shock / Iran crisis impact
- [ ] Add current geopolitical event to timeline (Iran/OPEC oil crisis 2025)
- [ ] Update all chart data with final validated numbers from the group

---

## How to Recreate from Scratch

If you want to rebuild the site from zero while keeping the same design:

1. Start with the CSS variables block — these define the entire color system
2. Build the nav + sidebar structure first (they are fixed/sticky)
3. Build each section as a hidden `<div class="sec">` block
4. Add Chart.js from CDN — no other dependencies needed
5. The `goTo()` function handles all navigation
6. Charts are initialized inside `initCharts(page)` — called lazily per section
7. All styling uses utility-style class names defined in the `<style>` block

**The entire site is self-contained — one file, no build tools, no npm, no server.**

---

*Last updated: April 2026 — V3 — KEDGE P42*
