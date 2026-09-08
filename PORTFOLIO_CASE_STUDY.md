# Portfolio Case Study: Vertical Spread Analyzer

*Copy-paste this into your portfolio website. Adapt styling to match your site.*

---

## 📊 Vertical Spread Analyzer

**Role:** Solo Developer (Vibe Coding + Client Collaboration)  
**Stack:** Vanilla JavaScript, SheetJS, Black-Scholes Mathematics, CSS Grid  
**Duration:** Multi-week iterative build (20+ client feedback cycles)  
**Live Demo:** [yourusername.github.io/vertical-spread-analyzer](https://yourusername.github.io/vertical-spread-analyzer)  
**Source:** [github.com/yourusername/vertical-spread-analyzer](https://github.com/yourusername/vertical-spread-analyzer)

---

### The Problem

Options traders analyzing vertical spreads face a critical workflow gap:

- **Professional platforms** (ThinkorSwim, Bloomberg) are expensive and locked behind brokerage accounts
- **Excel-based analysis** requires manual computation of Black-Scholes probabilities across hundreds of strike combinations
- **Existing web tools** lack the domain-specific features traders actually need: per-expiry targets, expected value ranking, and side-by-side comparison

A client — an active options trader — needed a tool that could ingest raw option chain data and deliver ranked, probability-adjusted spread recommendations without subscription fees or backend infrastructure.

---

### The Solution

A zero-backend, browser-based quantitative engine that:

1. **Ingests** raw option chain Excel files (auto-detecting headers, date serials, and column mappings)
2. **Computes** true risk-neutral probabilities using Black-Scholes with continuous dividend yield adjustment
3. **Generates** all valid vertical spread combinations and filters by liquidity, probability, and expected value
4. **Ranks** candidates by Return Multiple, EV, or EV/Month with per-expiry leaderboards
5. **Compares** selected trades side-by-side with one-click add/remove
6. **Exports** full results to CSV for further analysis

---

### The Iterative Development Process

This wasn't built in a single session. It evolved through **20+ cycles of real client feedback**:

| Iteration | Client Need | Solution Implemented |
|-----------|------------|-------------------|
| **1-3** | Basic spread analysis | Core Black-Scholes engine, call/put debit spread logic |
| **4-6** | True probability, not delta proxy | Full `Nd2` computation with `d₂ = [ln(S/K) + (r−q−½σ²)T] / (σ√T)` |
| **7-9** | Different targets per expiry | Per-Expiry Price Target mode with live implied-% calculation |
| **10-13** | Filter noisy data | Multi-select expiry dropdowns, column filters (set/range/text), structure search |
| **14-16** | Find best trades quickly | Top-N ranking panel per expiry with configurable sort metric |
| **17-19** | Compare candidates | Checkbox-driven comparison cards with full metric display |
| **20+** | Polish & transparency | Drag-drop upload, progress bars, tooltips, status logging, dark-mode UI |

---

### Technical Deep Dive

#### State Management Without Frameworks

The app handles complex reactive state entirely in vanilla JS:

- **Multi-select expiry filters** with select-all/clear and persistent selection across re-renders
- **Per-expiry price targets** — independent target price for each expiration date, stored in a keyed object
- **Column-level filters** — three filter types (set, range, text) with active indicator badges
- **Checkbox-selected comparison items** — persistent highlighting and side-panel rendering
- **Sortable results table** — multi-column sorting with ascending/descending toggle

All state lives in native `Set` and `Object` structures, with explicit re-render triggers.

#### Financial Engine

```javascript
// True Black-Scholes d2 with continuous dividend yield
const T = days / 365;
const r = 0.045;  // risk-free rate
const q = divYield;  // continuous dividend yield
const sigma = normalizeIV(iv);  // implied volatility

const d2 = (Math.log(S / K) + (r - q - 0.5 * sigma * sigma) * T) 
           / (sigma * Math.sqrt(T));

// Call debit spread: probability long strike finishes ITM
const nd2 = normalCDF(d2);

// Put debit spread: probability long strike finishes ITM  
const nd2_put = 1 - normalCDF(d2);
```

**Key design decisions:**
- Uses **continuous dividend yield** (`q`) for accurate probability on dividend-paying underlyings (SPY, QQQ, AAPL)
- Falls back to delta-approximated probability when IV data is missing
- Computes **payoff at target price** (not just max profit) for realistic return estimation
- Normalizes EV to 30-day periods for cross-expiry comparison

#### Boundary Strike Logic

A subtle but critical feature: the engine automatically finds the "boundary strike" per expiry:

- **Bull Call Spreads:** Ceiling strike = first strike ≥ target price. Short strike must be ≤ ceiling.
- **Bear Put Spreads:** Floor strike = last strike ≤ target price. Short strike must be ≥ floor.

This prevents recommending spreads where the short leg is unrealistically far from the target.

#### Performance

- Parses 5,000+ option legs client-side in <500ms
- Generates and filters all valid spread combinations in real-time
- Zero server calls, zero API keys, zero subscriptions
- Single HTML file — opens instantly in any browser

---

### Key Features

| Feature | What It Does | Why It Matters |
|--------|-------------|---------------|
| **Smart Excel Parsing** | Auto-detects headers, handles Excel date serials (1900/1904), skips malformed rows | Traders get data from brokers in inconsistent formats |
| **Dual Analysis Modes** | Annual % proration OR per-expiry custom price targets | Different strategies need different target frameworks |
| **Boundary Strike Logic** | Auto-finds ceiling (calls) / floor (puts) per expiry | Prevents impossible spread recommendations |
| **Top-N Ranking** | Configurable leaderboards per expiry (Return Multiple, EV, EV/Month) | Surfaces best opportunities without manual scanning |
| **Side-by-Side Compare** | Checkbox-driven comparison cards with full metrics | Enables rapid trade selection |
| **CSV Export** | Full computed metrics export | Integrates with external analysis workflows |

---

### Outcome

A production-ready trading analysis tool that demonstrates:

- **Domain expertise** in quantitative finance, derivative pricing, and options mechanics
- **Frontend engineering** at scale without framework dependencies
- **Iterative product development** — translating client feedback into working features
- **Rapid prototyping** via AI-assisted development workflows
- **End-to-end ownership** — from problem identification to deployment

---

### What I Learned

1. **Client-driven iteration beats upfront perfection.** The tool became significantly more useful when I stopped guessing features and started responding to actual trader workflows.

2. **Vanilla JS can handle surprising complexity.** Multi-dimensional filtering, reactive state, and financial computation — all without React, Vue, or a build step.

3. **Domain knowledge is the differentiator.** The code quality matters, but what makes this project stand out is the financial intuition encoded into every formula and edge case.

---

### Testimonial

> *"This replaced my Excel spreadsheet entirely. The per-expiry targets and Top-5 ranking save me 30 minutes every morning."*  
> — Client, Active Options Trader

---

*Built with iterative client feedback, vibe coding, and a lot of Black-Scholes.*
