# 💰 LIC vs Bank FD vs Mutual Fund — Premium Timing Calculator

> **Free, open-source financial calculator for Indian investors.**  
> Compare LIC insurance premiums against Bank FD/RD and Mutual Fund SIP with true time-weighted IRR, post-tax returns, and liquidity analysis.

🔗 **Live Demo:** [nagarajbhat.github.io/investment-calculator](https://nagarajbhat.github.io/investment-calculator/)

---

## 🤔 Why This Tool Exists

Standard LIC return calculators have a fundamental flaw: they treat all premiums as if they earn interest for the **full term**. But a premium paid in **Month 6** only earns interest for the **remaining** time — not from Day 1.

This calculator solves that by doing **chronological cash flow mapping** — every installment is tracked from its exact payment date to maturity, compounded independently.

---

## ✨ Features

### 📊 3-Way Comparison
| Track | What it calculates |
|---|---|
| 🏦 **Bank FD/RD** | Time-weighted compound interest per installment |
| 🛡️ **LIC Insurance** | True IRR using Newton-Raphson + Bisection solver |
| 📈 **Mutual Fund SIP** | Expected CAGR with LTCG/STCG tax treatment |

### 🏷️ Tax-Adjusted Returns (Indian Tax Rules)
- **Bank FD** — Interest taxed at your income slab rate (0–30%)
- **LIC** — Tax-free under **Sec 10(10D)** if premium ≤ 10% of sum assured & ≤ ₹5L/yr
- **Equity MF** — **LTCG 12.5%** on gains above ₹1.25L (Budget 2024)
- **Debt MF** — Taxed at slab rate (post April 2023 rules)
- **FD TDS clarification** — ₹50,000/yr threshold (< 60 yrs) · ₹1,00,000/yr (senior citizens) · Budget 2025

### 📐 Advanced Financial Math
- **IRR Solver**: Newton-Raphson with bisection fallback for net-loss scenarios
- **Cooling / Paid-Up Period**: Separate "Premium Payment Period" vs "Policy Maturity Period"
- **Time-Weighting**: Every installment compounded from its exact deposit date

### 🔒 Liquidity & Lock-in Analysis
- LIC: Fully locked · surrender = 30–50% loss
- FD: Break after 1 year with ~0.5–1% penalty
- MF: Redeem any business day · no lock-in (except ELSS 3 yrs)

### 💡 Smart Insights
- 3-way post-tax verdict with winner declaration
- Life cover / sum assured comparison (vs free debit card cover)
- IRR vs inflation vs FD rate warnings
- Real-world emergency scenario explanation

---

## 🛠️ Tech Stack

- **Pure HTML5 + Vanilla JavaScript** — zero dependencies, zero build step
- **Tailwind CSS CDN** — styling
- **Google Fonts (Inter)** — typography
- Single `index.html` file — works offline

---

## 🚀 Usage

### Run Locally
Just open the file in any browser:
```bash
open index.html
```
No server, no npm install, no build needed.

### Deploy to GitHub Pages
1. Fork this repo
2. Go to **Settings → Pages**
3. Set Source: `main` branch, `/ (root)` folder
4. Your URL: `https://YOUR_USERNAME.github.io/investment-calculator/`

---

## 🧮 How the Math Works

### Bank FD Track
Each installment `P` paid at time `t` is treated as an independent FD:
```
FV = P × (1 + r/n)^(n × (T_maturity - t))
```
Where `r` = annual rate, `n` = compounding frequency, `T_maturity` = full maturity year.

### Insurance IRR
Solved iteratively — finds the rate `r` such that:
```
NPV = Σ [ -premium_k / (1+r)^t_k ] + maturity / (1+r)^T = 0
```
Uses Newton-Raphson (fast) → falls back to bisection (stable for net-loss scenarios).

### Mutual Fund SIP
Each SIP instalment grows at expected CAGR:
```
FV = P × (1 + mfRate)^(T_maturity - t)
```
Tax applied on redemption: LTCG 12.5% (equity, gains > ₹1.25L) or slab rate (debt).

---

## 📋 Input Parameters

| Input | Description |
|---|---|
| Premium Frequency | Quarterly / Half-Yearly / Annually |
| Installment Amount | Per-installment premium (₹) |
| Premium Payment Period | Years you pay premiums |
| Policy Maturity Period | When policy actually matures (cooling period = difference) |
| Bank FD Rate | Annual FD/RD interest rate |
| Compounding | Monthly / Quarterly / Yearly |
| LIC Maturity Lump Sum | Expected maturity amount |
| Life Cover / Sum Assured | Death benefit amount |
| MF Expected Return | Annual CAGR expectation |
| MF Fund Type | Equity/Hybrid (LTCG) or Debt/Liquid (slab) |
| Income Tax Slab | Your applicable tax rate (0–30%) |

---

## ⚠️ Disclaimer

This tool is for **educational and comparison purposes only**. It is not financial advice. Actual returns depend on market conditions, policy terms, and individual tax situations. Consult a SEBI-registered financial advisor before making investment decisions.

---

## 📄 License

MIT License — free to use, modify, and distribute.

---

*Built with ❤️ by [Hegma Tech](https://github.com/nagarajbhat)*
