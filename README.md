# Retirement Corpus Calculator — The Life Expense Pyramid
### One salary, split across life's claims, and the corpus that must fund life after work

**Model & concept:** Suresh Tumu · AMFI-certified · TechnoFunda community · Chennai
**Built in partnership with Claude (Anthropic) · July 2026**

A single, self-contained HTML file. No installation, no server, no data collection — every calculation runs in your own browser, and nothing you type ever leaves your device. Works on desktop and mobile, online or offline.

---

## 1. What it answers

Take one salary and divide it across life's real claims — income tax, living expenses, loans, insurance, children's goals, and retirement savings. Loans start, run their course, and close; the freed EMIs then pour into equity. Savings compound until retirement into a corpus; that corpus must then fund every inflated expense for the rest of life.

Two questions, answered live as you move any control:

1. **The Magic Number** — the corpus required at retirement so expenses are funded exactly to the plan-until age, ending at zero.
2. **On Track or Gap** — whether your accumulation reaches it, shown as a % FUNDED verdict with the year the money would run dry if it falls short — and, beyond flat math, the **Monte Carlo survival rate** across 1,000 simulated market lives.

This is an educational what-if illustration, not investment advice. Consult a financial advisor for decisions.

## 2. Quick start

Open the file. The defaults describe someone starting at 25 on Rs 1,00,000/month: 7% compound inflation, 6% salary growth, 10% accumulation return, retirement at 60 with 96% of last-drawn lifestyle to age 90, a conservative post-retirement mix (annuity 30% @6.5%, FD 50% @7%, equity 20% @10% with 3 years of cash cover), and Rs 5,00,000 already in hand. Loans open at a Rs 50L home, Rs 10L self-education, and a Rs 5L vehicle, with children's education (Rs 20L @45) and marriage (Rs 10L @52) funded as savings goals. This opens ON TRACK at ~124% funded.

Five things to try first:
- **Income slider** Rs 1L to Rs 2L — watch income tax appear (0% at Rs 12L/year, then rising by slab) and the debt ceiling stay generous.
- **Home loan** toward Rs 1 Cr — watch the debt meter go red and the assisted story name the binding loan.
- **Starting age** 22 vs 30 — three years either side is a sea change.
- **Cash cover** 0 to 7 years — safety has a price: more years parked in FD raises the magic number.
- **Corpus buckets** — slide FD to 100% (no annuity, no equity) and watch the magic number climb and Monte Carlo survival fall.

## 3. The model, precisely

The engine runs in yearly steps. Living expenses and savings are **percentages of income**; loans are **absolute rupees** the tool turns into EMIs.

**Income tax (new regime, computed live).** The Tax row is not editable — it applies the FY2026-27 New Regime slabs (nil up to Rs 4L, then 5/10/15/20/25/30% bands), a Rs 75,000 standard deduction, the Section 87A rebate (which makes taxable income up to Rs 12L tax-free), and 4% cess. At Rs 1L/month the tax is effectively zero; it rises by slab as income grows. Move the income slider and the tax recalculates.

**Loans in rupees, with an affordability engine.** Each loan (Home, Self-Education, Vehicle) is set in rupees, with its own interest rate and tenure. The tool computes the EMI by amortization and expresses it as a share of that year's salary (a step-up view — the EMI rises with your salary). The single rule it enforces is a **tax-aware debt ceiling**: while your salary is Rs 2L/month or below (max 20% tax bracket), total concurrent EMIs may reach **40%** of salary — the tax you save funds the extra servicing; above Rs 2L/month (25%+ bracket) the ceiling tightens to **30%**. The ceiling is checked year by year against your grown salary.

**The assisted waterfall.** If your loans breach the ceiling, the tool doesn't just fail — it shows its work: it stretches the home-loan tenure (up to 30 years, closing by 60), then stretches the vehicle loan, then delays the vehicle start, and if it still doesn't fit, it names the binding loan so you know exactly what to trim. The home loan is a **step-up loan** — it pays a lighter EMI while an education loan is still running, then accelerates once that clears.

**Freed EMIs become equity.** When a loan closes, its freed EMI doesn't vanish — 70% flows into equity/MF accumulation (the growth phase of your career), 30% lifts your lifestyle (a bigger phone, a TV, upgrades). This is why the savings rate ramps from ~15% early to ~39% in the final working years, and why most of the corpus is built late.

**Children as goals, not loans.** Education and marriage have deadlines you know decades ahead. Funded as savings goals from the start, Rs 20L at 45 costs about 1.3% of income a month, and Rs 10L at 52 about 0.6% — a fraction of what borrowing late would cost.

**Allocation is yours to decide.** A banner shows how much of your income is committed (living + EMIs + savings) and how much is unassigned. The tool deliberately does **not** auto-balance — it nudges you to place the free cash yourself: raise savings, lift lifestyle, or afford a bigger loan. Nothing is decided until you place it.

**Post-retirement buckets.** At retirement the corpus deploys into three buckets: **Annuity** (locked for life, pays income, passes to nominee), **FD/Liquid**, and **Equity/MF**. Each retirement year is funded from FD, which is topped back up to a **cash-cover** level (default 3 years) by selling equity — so ready cash is always on hand while the rest keeps compounding. The Magic Number is found by search: the smallest corpus that survives to the plan-until age under this policy.

**Monte Carlo.** 1,000 simulated lives per recalculation (seeded, reproducible), swinging accumulation and equity-bucket returns by the volatility sigma each year while FD and annuity stay fixed. Flat returns overstate safety — a plan that looks well-funded on averages can be a coin-flip in real markets.

## 4. Honest limits

Yearly steps; contributions at year-end, lumpsums at year-start; ages are integers. EMIs are modeled as a level share of the start-year salary (a simplification of true step-up schedules). Insurance premiums (health, term) are held flat during working years. The debt ceiling and tax calculation reflect FY2026-27 rules and simplify some real-world details (no HRA, 80C legacy, or surcharge above Rs 50L income). Monte Carlo randomizes market returns only, with independent yearly draws — real markets have fat tails and momentum this doesn't capture. Nothing here is a return guarantee.

## 5. Visitor stats

A GoatCounter snippet sits just before the closing body tag. It counts page views only — it never sees the numbers users type — and can email a periodic report.

---
*Version: July 2026 (v2 affordability engine) — rupee loans, live income-tax calculation, tax-aware debt ceiling, step-up home loan, freed-EMI-to-equity transition, children as savings goals, allocation nudge, annuity/FD/equity buckets with cash cover, income streams, share links, Monte Carlo, PDF report, feedback form.*
