# 📊 Vertical Spread Analyzer

> **Client-driven, iteratively refined** — A browser-based quantitative options engine built through 20+ iterations of real trader feedback.  
> Parses raw option chains, computes true Black-Scholes probabilities, and ranks vertical spreads by expected value. Zero backend. Zero subscriptions.

[![Live Demo](https://img.shields.io/badge/🚀%20Live%20Demo-GitHub%20Pages-0ea5e9?style=flat-square)](https://yourusername.github.io/vertical-spread-analyzer/)
[![Built With](https://img.shields.io/badge/Built%20With-Vibe%20Coding-10b981?style=flat-square)](https://github.com/topics/vibe-coding)
[![Domain](https://img.shields.io/badge/Domain-Quant%20Finance-f59e0b?style=flat-square)]()
[![Stack](https://img.shields.io/badge/Stack-Vanilla%20JS%20%7C%20XLSX%20%7C%20Black--Scholes-6366f1?style=flat-square)]()
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)]()

---

## 🎯 What It Does

Upload an Excel option chain → get ranked vertical spread recommendations in seconds.

| Feature | Detail |
|--------|--------|
| **📁 Smart Parsing** | Auto-detects Excel date serials, headers, and column mappings |
| **🧮 True Black-Scholes** | Computes `Nd2` with dividend yield adjustment: `d₂ = [ln(S/K) + (r−q−½σ²)T] / (σ√T)` |
| **🎯 Dual Target Modes** | Annual % proration **OR** per-expiry custom price targets |
| **🔍 Intelligent Filtering** | Multi-select expiry dropdowns, column filters, structure search |
| **🏆 Top-N Ranking** | Per-expiry leaderboards by Return Multiple, EV, or EV/Month |
| **⚖️ Side-by-Side Compare** | Checkbox-driven comparison cards for trade selection |
| **📤 CSV Export** | Full results export for further analysis |

---

## 🧠 The Development Story

### From Client Pain Point to Polished Tool

This project was born from a real trader's workflow problem and evolved through **20+ iterative cycles** of feedback and refinement:

**Phase 1 — Core Engine**
- Built the initial Black-Scholes probability calculator and spread payoff engine
- Client needed true `Nd2` (not delta approximation) with dividend yield support

**Phase 2 — Analysis Modes**
- Added "Annual Target %" mode for directional views
- Client requested **Per-Expiry Price Targets** — different price levels for each expiration
- Implemented live implied-% calculation as targets are typed

**Phase 3 — Filtering & Discovery**
- Multi-select expiry dropdown with select-all/clear
- Column-level filters (set, range, text) with active indicators
- Structure/strike search bar for rapid lookup

**Phase 4 — Ranking & Comparison**
- Top-N summary panel per expiry (client: "show me the best 5 per month")
- Side-by-side comparison cards with one-click add/remove

**Phase 5 — Polish**
- Drag-and-drop file upload with progress bar
- Dark-mode trading terminal aesthetic
- Comprehensive tooltips explaining every metric
- Detailed status logging for transparency

**The result:** A fully functional quant tool that runs entirely in the browser, processes thousands of option legs client-side, and delivers institutional-grade spread analysis — shaped by real user needs at every step.

---

## 🛠️ Technical Highlights

### Architecture
```
Single HTML file
├── SheetJS (XLSX parsing)
├── Vanilla JS state machine
├── Custom normalCDF approximation
├── Multi-select dropdown engine
├── Column filter system (set/range/text)
└── Responsive CSS grid + sticky table headers
```

### Key Algorithms
- **Nd2 Computation:** Risk-neutral probability with continuous dividend yield adjustment
- **Payoff Engine:** Target-price payoff calculation for partial ITM scenarios
- **EV Normalization:** `(MaxReturn/MaxLoss) × Nd2` scaled to 30-day periods
- **Boundary Strike Logic:** Automatic ceiling/floor strike selection per expiry based on target price

### Edge Cases Handled
- Excel date serial conversion (1900/1904 epoch)
- Missing IV fallback to delta-approximated probability
- Debit spread validation (filters out negative-cost structures)
- Empty/malformed row skipping with detailed logging

---

## 🚀 Quick Start

### Option A: Open Locally
1. Download `index.html`
2. Open in any modern browser — no server required
3. Upload your option chain Excel (see [sample data](sample-data/))
4. Set Market View and click **Run Analysis**

### Option B: Use Sample Data
We include a [sample QQQ option chain](sample-data/sample-option-chain.csv) so you can try the tool immediately without sourcing your own data.

### Option C: Deploy Your Own Fork
This repo is configured for **GitHub Pages** auto-deployment. Push to `main` and your live demo updates instantly. See [deployment guide](#deployment).

---

## 📁 Project Structure

```
vertical-spread-analyzer/
├── index.html                  # The full application (self-contained)
├── README.md                   # This file
├── LICENSE                     # MIT License
├── sample-data/
│   └── sample-option-chain.csv # Try-it-now sample data
├── .github/
│   └── workflows/
│       └── pages.yml           # GitHub Pages auto-deploy
└── assets/                     # Screenshots & demo media
```

---

## 📸 Screenshots

*(Add your screenshots to the `assets/` folder and update these links)*

| Upload & Market View | Results Table | Top-N Ranking | Comparison Panel |
|:---:|:---:|:---:|:---:|
| ![Upload](assets/screenshot-upload.png) | ![Results](assets/screenshot-results.png) | ![TopN](assets/screenshot-topn.png) | ![Compare](assets/screenshot-compare.png) |

---

## 🏷️ Tags

`#vibe-coding` `#quantitative-finance` `#options-trading` `#black-scholes` `#vanilla-javascript` `#client-side-analysis` `#fintech` `#portfolio-project` `#iterative-development`

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

*Built with iterative client feedback, vibe coding, and a lot of Black-Scholes.*
