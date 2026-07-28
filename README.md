# Retirement Corpus Calculator — The Life Expense Pyramid
### One salary, split across life's claims, and the corpus that must fund life after work

**Model & concept:** Suresh Tumu · AMFI-certified · TechnoFunda community · Chennai
**Built in partnership with Claude (Anthropic) · July 2026**

A single, self-contained HTML file. No installation, no server, no data collection — every calculation runs in your own browser, and nothing you type ever leaves your device. Works on desktop and mobile, portrait or landscape, online or offline.

---

## 1. What it answers

Take one salary and divide it across life's real claims — income tax, living expenses, loans, insurance, children's goals, and retirement savings. Loans start, run their course, and close; the money they freed then flows into savings. What's left after everything is what builds your corpus, compounding until retirement. That corpus must then fund your lifestyle — plus the tax on its own income — for the rest of your life.

Two questions, answered live as you move any control:

1. **The Magic Number** — the corpus required at retirement so your lifestyle is funded exactly to the plan-until age, ending at zero.
2. **On Track or Gap** — whether your accumulation reaches it, shown as a % FUNDED verdict with the year the money would run dry if it falls short — and, beyond flat math, the **Monte Carlo survival rate** across 1,000 simulated market lives.

This is an educational what-if illustration, not investment advice. Consult a financial advisor for decisions.

## 2. Quick start

Open the file. The defaults describe someone starting at 25 on Rs 1,00,000/month: 6% compound inflation, 6% salary growth, 5% lifestyle growth, 10% accumulation return, retirement at 60 spending 100% of their final lifestyle to age 90, a conservative post-retirement mix (annuity 30% @6% locked, FD 50% @7%, equity 20% @10% with 3 years of cash cover), and Rs 5,00,000 already in hand. Loans open at a Rs 50L home, Rs 10L self-education, and a Rs 5L vehicle, with children's education (Rs 20L @45) and marriage (Rs 10L @52) funded as savings goals. This opens ON TRACK at ~124% funded.

Five things to try first:
- **Salary vs Lifestyle growth** — raise salary growth to 10% while lifestyle stays at 5% and watch the funded % climb. The gap between what you earn and what you spend is what builds wealth.
- **Income slider** Rs 1L to Rs 2L — watch income tax appear (0% at Rs 12L/year, then rising by slab) and the loan defaults rescale with your earning power.
- **Home loan** toward Rs 1 Cr — watch the debt meter go red, then hit "Auto-fit loans" to snap them to what the salary can service.
- **Starting age** 22 vs 30 — three years either side is a sea change.
- **Corpus buckets** — drag Equity up and FD absorbs the change; slide FD to 100% and watch the magic number climb and Monte Carlo survival fall.

## 3. The model, precisely

The engine runs in yearly steps. Living expenses are **percentages of income**; loans are **absolute rupees** the tool turns into EMIs; savings are simply whatever income is left after everything else.

**Income tax (new regime, computed live).** The Tax row is not editable — it applies the FY2026-27 New Regime slabs (nil up to Rs 4L, then 5/10/15/20/25/30% bands), a Rs 75,000 standard deduction, the Section 87A rebate (which makes taxable income up to Rs 12L tax-free), and 4% cess. At Rs 1L/month the tax is effectively zero; it rises by slab as income grows. Move the income slider and the tax recalculates.

**Loans in rupees, with an affordability engine.** Each loan (Home, Self-Education, Vehicle) is set in rupees, with its own interest rate and tenure, and defaults that scale with your income (roughly 50× monthly income for the home, 10× for education, 5× for the vehicle — sliders start at zero for anyone who has no such loan). The tool computes the EMI by amortization (compound / reducing-balance, the way banks actually do it) and expresses it as a share of that year's salary. It enforces a **tax-aware debt ceiling**: while your salary is Rs 2L/month or below (max 20% tax bracket), total concurrent EMIs may reach **40%** of salary — the tax you save funds the extra servicing; above Rs 2L/month (25%+ bracket) the ceiling tightens to **30%**.

**The assisted waterfall and Auto-fit.** If your loans breach the ceiling, the tool shows its work: it would stretch the home-loan tenure, stretch the vehicle loan, then delay the vehicle start, and if it still doesn't fit it names the binding loan and computes the eligible amounts. A one-click **Auto-fit** button scales every loan proportionally so the peak lands exactly at the ceiling — or you drag the sliders yourself. The home loan is a **step-up loan** — a lighter EMI while an education loan is still running, then it accelerates once that clears. Nothing is ever changed without your click.

**Savings = whatever's left, so borrowing has an honest cost.** Each year, savings is simply income minus tax, living expenses, actual EMIs, and goal contributions; 30% of the leftover lifts lifestyle and 70% is invested. Because EMIs genuinely compete with savings, a bigger loan means less saved during those years — so a bigger loan correctly produces a *smaller* corpus, not a larger one. The savings rate rises naturally as loans close: modest in the peak-debt years, climbing past a third of income in the final stretch.

**Salary growth vs lifestyle growth — the discipline gap.** Two separate levers. Salary growth drives how fast you earn and save; **lifestyle growth** (usually slower) drives how fast your spending rises. The gap between them is what builds wealth — a raise you don't fully spend becomes retirement savings. Crucially, your retirement need is anchored to your slower-growing *lifestyle*, not your full last-drawn salary, because a disciplined earner never consumed all of it. This is why earning more genuinely helps here: raise salary growth while lifestyle holds, and the magic number stays put while the corpus grows.

**Retirement need = your lifestyle, not your salary.** The target is the lifestyle you actually live on, carried forward at the lifestyle-growth rate — set as a percentage (default 100%) of that final lifestyle. Near retirement a salary splits into tax, savings and actual spending; in retirement the tax on salary and the savings both stop, so what the corpus must replace is the lifestyle portion, plus the tax on the corpus's own income.

**Children as goals, not loans.** Education and marriage have deadlines you know decades ahead. Funded as savings goals from the start, Rs 20L at 45 costs about 1.3% of income a month and Rs 10L at 52 about 0.6% — a fraction of what borrowing late would cost.

**Allocation is yours to decide.** A banner shows how much of your income is committed (living + EMIs + savings) and how much is unassigned. The tool deliberately does **not** auto-balance — it nudges you to place the free cash yourself. Nothing is decided until you place it.

**Post-retirement buckets and tax.** At retirement the corpus deploys into three buckets whose shares always total 100%: **Annuity** (a return-of-corpus policy — principal locked, pays income for life at a fixed 6%, full principal returned to your nominee on death), **FD/Liquid**, and **Equity/MF**. Drag any of the three and FD/Liquid absorbs the change; annuity stays put. Each retirement year is funded from FD, which is topped back up to a **cash-cover** level (default 3 years) by selling equity — so ready cash is always on hand while the rest keeps compounding. **Tax in retirement is charged only on income** — annuity payout and FD interest at the new-regime slabs, and realised equity gains at 12.5% LTCG above the Rs 1.25L annual exemption — **never on the principal you draw back**. Under the new regime senior citizens are taxed on the same slabs as everyone else. The Magic Number is found by search: the smallest corpus that survives to the plan-until age under this policy.

**Monte Carlo.** 1,000 simulated lives per recalculation (seeded, reproducible), swinging accumulation and equity-bucket returns by the volatility sigma each year while FD and annuity stay fixed. Flat returns overstate safety — a plan that looks well-funded on averages can be a coin-flip in real markets.

## 4. Honest limits

Yearly steps; contributions at year-end, lumpsums at year-start; ages are integers. Insurance premiums (health, term) are held flat during working years. The tax calculation reflects FY2026-27 new-regime rules and simplifies some real-world details (no HRA, 80C legacy, surcharge above Rs 50L income, or old-regime senior-citizen deductions such as 80TTB). The end-of-plan leftover is shown both as a nominal figure and discounted to retirement-day money, so the inflation illusion on a large nominal number is visible. Monte Carlo randomizes market returns only, with independent yearly draws — real markets have fat tails and momentum this doesn't capture. Nothing here is a return guarantee.

## 5. Visitor stats

A GoatCounter snippet sits just before the closing body tag. It counts page views only — it never sees the numbers users type — and can email a periodic report.

---
*Version: July 2026 — rupee loans with a tax-aware debt ceiling and Auto-fit, live income-tax calculation, step-up home loan, honest "savings = what's left" accumulation, separate salary-growth and lifestyle-growth levers, retirement need anchored to lifestyle, income-only post-retirement tax, children as savings goals, allocation nudge, three-way annuity/FD/equity buckets with cash cover, today's-money framing, income streams, share links, Monte Carlo, PDF report, feedback form.*
