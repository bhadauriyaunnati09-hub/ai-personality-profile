# Day 16 – Build Your First Stock Research Skill

## 🎯 Challenge: AcademyBind 60-Day AI Challenge

**Day:** 16
**Topic:** Claude Custom Skills — Stock Fundamental Research
**Difficulty:** Intermediate
**Time Taken:** ~45 minutes

---

## 📌 What I Built

A reusable **Claude Custom Skill** named `stock-fundamental-research` that performs deep fundamental analysis of Indian and global listed stocks.

Instead of typing the same long prompt every time, I created a persistent skill that can be invoked instantly for any stock — TCS, Infosys, Reliance, HDFC Bank, Tata Motors, and more.

---

## 🛠️ Skill Details

| Field | Value |
|-------|-------|
| **Skill Name** | `stock-fundamental-research` |
| **Category** | Finance / Research |
| **Platform** | Claude.ai Custom Skills |
| **Effort Level** | Low / Medium |

### Description
> Analyze Indian and global listed companies using fundamentals, financial statements, business quality, competitive advantages, valuation, risks, and growth prospects. Generate evidence-based research reports and investor-friendly summaries. Never provide direct buy, sell, or hold recommendations.

---

## ⚙️ How the Skill Works

The skill supports **5 analysis modes**:

| Mode | When to Use |
|------|-------------|
| **Quick Take** | Single stock, brief overview (default) |
| **Deep Dive** | Full detailed analysis with HTML output |
| **Compare** | Two stocks side-by-side |
| **Pros & Cons** | Strengths and risks breakdown |
| **Portfolio Fit** | How a stock fits your existing holdings |

---

## 📊 Research Checklist Covered

The skill automatically analyzes:

- ✅ CMP, Market Cap, Face Value, 52W High/Low
- ✅ P/E, P/B, EV/EBITDA vs sector and 5Y average
- ✅ Revenue, Profit, EPS CAGR (3Y/5Y)
- ✅ EBITDA Margin & Net Profit Margin (5Y trend)
- ✅ Free Cash Flow (3–5Y)
- ✅ D/E Ratio, Interest Coverage, Current Ratio
- ✅ ROE & ROCE (current, 3Y avg, 5Y avg)
- ✅ Dividend history & payout
- ✅ Promoter holding trend & pledging (>10% flagged 🚩)
- ✅ FII/DII trends (8 quarters)
- ✅ Moat, pricing power, competitive advantages
- ✅ Management quality & governance
- ✅ Sector tailwinds/headwinds
- ✅ Latest earnings commentary & top news
- ✅ Peer comparison (3 closest peers)
- ✅ Price Chart

---

## 🔴 Mandatory Rules Built Into the Skill

1. Use **live data first** — Screener → Tickertape → Moneycontrol → NSE/BSE
2. **Never fabricate data** — flags unavailable data with 🚩
3. **Cite source** beside every key figure
4. **No buy/sell/hold calls** or target prices — ever
5. No predictions; only historical trend discussion
6. Plain English with jargon explained on first use

---

## 🧪 Test Run — Stocks Analyzed

Tested the skill on the following stocks to verify output quality:

- **TCS** (Tata Consultancy Services) — Quick Take
- **Infosys vs TCS** — Compare Mode

### Sample Output Sections
- Valuation verdict (Cheap / Fair / Expensive)
- Financial health interpretation (D/E, Interest Coverage, Current Ratio)
- Growth classification (Accelerating / Steady / Slowing / Declining)
- Fundamental Quality rating (Strong / Moderate / Weak)

---

## 💡 Key Learnings

1. **Claude Custom Skills are reusable workflows** — write the prompt once, use it forever without copy-pasting.

2. **Structured output modes** (Quick Take vs Deep Dive) make the same skill useful for both beginners and advanced users.

3. **Mandatory rules inside the skill** prevent hallucination and ensure responsible AI use — especially critical in finance.

4. **Source hierarchy** in the prompt ensures Claude always tries to fetch live data before falling back to cached knowledge.

5. **Effort level matters** — setting it to Low/Medium before running financial research avoids hitting usage limits on a single long response.

---

## 📁 Files in This Folder

```
Day16/
├── day16.md          ← This documentation file
└── screenshots/      ← Screenshots of the skill and generated reports
```

---

## 🔗 Resources Used

- [Claude Custom Skills Documentation](https://claude.ai)
- [Screener.in](https://screener.in) — Financial data source
- [Tickertape](https://tickertape.in) — Stock analysis platform
- [NSE India](https://nseindia.com) — Exchange data

---

## ⚠️ Disclaimer

*This skill is built for educational purposes only. It does not provide investment advice and does not make buy, sell, or hold recommendations. All figures must be independently verified. The final decision is always the user's.*

---

## 🏷️ Tags

`#AcademyBind` `#60DayAIChallenge` `#Day16` `#ClaudeAI` `#CustomSkills` `#StockResearch` `#FinanceAI` `#FundamentalAnalysis` `#Python` `#AI` `#MachineLearning`

---

*Completed as part of the AcademyBind 60-Day AI Challenge*
*Day 16 of 60 ✅*
