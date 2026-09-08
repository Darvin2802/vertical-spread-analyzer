# 🚀 GitHub Upload & Deployment Guide

## Step 1: Prepare Your Files

You should have the following files ready:

```
vertical-spread-analyzer/
├── index.html              ← Your main app (rename from 17_with_per_expiry_mode.html)
├── README.md               ← The README we created
├── LICENSE                 ← MIT License
├── .gitignore              ← Git ignore rules
├── sample-data/
│   └── sample-option-chain.csv
└── .github/
    └── workflows/
        └── pages.yml       ← Auto-deploy to GitHub Pages
```

> **Important:** Rename your HTML file from `17_with_per_expiry_mode.html` to `index.html`. GitHub Pages serves `index.html` as the homepage.

---

## Step 2: Create a New GitHub Repository

### Option A: Using GitHub Website (Easiest)

1. Go to [github.com/new](https://github.com/new)
2. **Repository name:** `vertical-spread-analyzer`
3. **Description:** `Browser-based quantitative options engine — parses Excel chains, computes Black-Scholes probabilities, ranks vertical spreads by expected value`
4. **Visibility:** `Public` ✅ (for portfolio exposure)
5. **Initialize with:** ❌ Uncheck "Add a README" (we have our own)
6. **Add .gitignore:** ❌ Uncheck (we have our own)
7. **Choose a license:** ❌ Uncheck (we have our own)
8. Click **Create repository**

---

## Step 3: Upload Your Files

### Option A: Drag & Drop (Fastest for first upload)

1. On your new empty repo page, click **"uploading an existing file"**
2. Drag ALL your files into the browser window:
   - `index.html`
   - `README.md`
   - `LICENSE`
   - `.gitignore`
   - The entire `sample-data/` folder
   - The entire `.github/workflows/` folder
3. At the bottom, write commit message: `Initial commit: Vertical Spread Analyzer`
4. Click **Commit changes**

### Option B: Command Line (Recommended for updates)

```bash
# 1. Open terminal in your project folder
cd /path/to/vertical-spread-analyzer

# 2. Initialize git
git init

# 3. Add all files
git add .

# 4. Commit
git commit -m "Initial commit: Vertical Spread Analyzer"

# 5. Add remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/vertical-spread-analyzer.git

# 6. Push to main branch
git branch -M main
git push -u origin main
```

---

## Step 4: Enable GitHub Pages

This gives you a **live demo URL** that recruiters can click instantly.

1. Go to your repo on GitHub
2. Click **Settings** tab (top right)
3. In the left sidebar, click **Pages**
4. Under **Build and deployment** → **Source**, select **GitHub Actions**
5. That's it! The workflow file (`.github/workflows/pages.yml`) handles the rest

### Verify Deployment:

1. Go to **Actions** tab in your repo
2. You should see a workflow run starting
3. Wait for the green checkmark ✅ (takes ~1-2 minutes)
4. Your live URL will be: `https://YOUR_USERNAME.github.io/vertical-spread-analyzer/`
5. Add this URL to your README (replace `yourusername` in the badge link)

---

## Step 5: Add Screenshots (Critical for Portfolio Impact)

Recruiters judge repos in 5 seconds. Screenshots are everything.

1. **Take 4 screenshots** of your app in action:
   - Upload / Market View panel
   - Results table with filters active
   - Top-N ranking panel
   - Side-by-side comparison cards

2. Save them as:
   - `assets/screenshot-upload.png`
   - `assets/screenshot-results.png`
   - `assets/screenshot-topn.png`
   - `assets/screenshot-compare.png`

3. Upload them to the `assets/` folder in your repo

4. The README already has placeholder links — they will auto-display once you upload

### Pro Tip: Record a 15-sec GIF
Use [ScreenToGif](https://www.screentogif.com/) or [LICEcap](https://www.cockos.com/licecap/) to record yourself uploading the sample data and running analysis. Add it right below the badges in README.

---

## Step 6: Update README with Your Info

Before sharing, update these placeholders in `README.md`:

| Placeholder | What to Replace With |
|-------------|---------------------|
| `yourusername` | Your actual GitHub username (in the Live Demo badge URL) |
| `[Your Name]` | Your name (in LICENSE file) |
| Screenshot paths | Your actual uploaded screenshots |

---

## Step 7: Add Topics/Tags to Your Repo

On your GitHub repo main page, click the **⚙️ gear icon** next to "About" and add these topics:

```
vibe-coding, quantitative-finance, options-trading, black-scholes, vanilla-javascript, 
client-side-analysis, fintech, portfolio-project, excel-parser, trading-tools
```

This makes your repo discoverable when recruiters search GitHub for these keywords.

---

## Step 8: Pin This Repo on Your Profile

1. Go to your **GitHub Profile** page
2. Click **"Customize your pins"**
3. Select **vertical-spread-analyzer**
4. Click **Save pins**

Now this project appears at the top of your profile — the first thing anyone sees.

---

## Step 9: Update Your GitHub Profile README

If you don't have a profile README, create one:

1. Create a new repo named **exactly** `YOUR_USERNAME` (e.g., `johndoe`)
2. Make it public
3. Add a `README.md`

Add this section about the project:

```markdown
## 🚀 Featured Project

### [📊 Vertical Spread Analyzer](https://github.com/YOUR_USERNAME/vertical-spread-analyzer)
A client-side quantitative options engine built through iterative client feedback. 
Parses Excel option chains, computes true Black-Scholes probabilities with dividend 
adjustment, and ranks vertical spreads by expected value — zero backend required.

**Tech:** Vanilla JS | SheetJS | Black-Scholes | CSS Grid  
**Highlights:** Dual analysis modes, per-expiry targets, Top-N ranking, side-by-side comparison

[🌐 Live Demo](https://YOUR_USERNAME.github.io/vertical-spread-analyzer/) | 
[📁 Source](https://github.com/YOUR_USERNAME/vertical-spread-analyzer)
```

---

## ✅ Final Checklist

Before you share this with recruiters, verify:

- [ ] Repo is **Public**
- [ ] `index.html` is at root level
- [ ] README has your correct username in links
- [ ] GitHub Pages is enabled and showing green ✅ in Actions
- [ ] Live demo URL works: `https://YOUR_USERNAME.github.io/vertical-spread-analyzer/`
- [ ] Screenshots are uploaded to `assets/`
- [ ] Topics/tags are added
- [ ] Repo is pinned on your profile
- [ ] Profile README mentions this project
- [ ] Sample data is included so anyone can try it

---

## 🎯 Next Steps After GitHub

### Add to Your Portfolio Website
Create a dedicated case study page. See the `portfolio-case-study.md` template we provided earlier.

### Share on LinkedIn
Post with the "iterative client-driven development" angle. Include the live demo link and a screenshot.

### Add to Resume
**Bullet point suggestion:**
> Built a client-side quantitative options analysis engine (Vanilla JS, Black-Scholes) that parses Excel option chains and ranks vertical spreads by expected value. Iteratively refined through 20+ client feedback cycles. Deployed via GitHub Pages with zero backend infrastructure.

---

*Questions? Open an issue on this repo or reach out directly.*
