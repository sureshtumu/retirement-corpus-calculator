# Retirement Corpus Calculator — The Life Expense Pyramid
### One salary, twenty lots of ₹5, and the corpus that must fund life after work

**Model & concept:** Suresh Tumu · AMFI-certified · TechnoFunda community · Chennai
**Built in partnership with Claude (Anthropic) · July 2026**

A single, self-contained HTML file. No installation, no server, no data collection — every calculation runs in your own browser, and nothing you type ever leaves your device. Works on desktop and mobile, online or offline.

---

## 1. What it answers

Take one salary and split it into life's buckets — tax, house, loans, insurance, travel, savings. Loans end over time and their freed EMIs flow into savings. Savings compound until retirement into a corpus; that corpus must then fund every inflated expense for the rest of life.

Two questions, answered live as you move any control:

1. **The Magic Number** — the corpus required at retirement so expenses are funded exactly to the plan-until age, ending at zero.
2. **On Track or Gap** — whether your accumulation (plus what you already hold) reaches it, shown as a % FUNDED verdict with the year the money would run dry if it falls short — and, beyond flat math, the **Monte Carlo survival rate** across 1,000 simulated market lives.

This is an educational what-if illustration, not investment advice. Consult a financial advisor for decisions.

## 2. Quick start

Open the file. The defaults describe someone starting at 25 on ₹1,00,000/month: 7% compound inflation, 6% salary growth, 10% accumulation return, retirement at 60 with 75% of final-salary lifestyle to age 90, the corpus split across annuity 30% @6.5%, FD/liquid 35% @7% and equity 35% @12% with 3 years of expenses kept as cash cover, and ₹5,00,000 already in hand. This opens ON TRACK at ~140% funded, with ~68% of simulated lives surviving in the Monte Carlo panel.

Five things to try first:
- **Starting age** 22 vs 30 — three years either side is a sea change (142% vs 85% funded; the late starter runs dry at 84).
- **House Loan EMI year-slider** 30 → 20 — the freed EMI auto-invests and the corpus jumps by over a crore, live.
- **Corpus buckets** — slide FD to 100% (no annuity, no equity) and watch the magic number climb from ₹9.0 Cr to ₹12.0 Cr, and Monte Carlo survival fall from 68% to 46%.
- **Cash cover** 0 → 7 years — safety has a price: more years parked in FD raises the magic number from ₹8.4 Cr to ₹10.1 Cr.
- **Healthcare inflation** at 12% — the India-specific warning, quantified.
- **Salary growth** at 10% — earning more doesn't save a plan whose lifestyle rides the salary.

## 3. The model, precisely

All category amounts are **percentages of income** (the "20 lots of ₹5 on ₹100" idea); rupee equivalents show in each row's grey line. The engine runs in yearly steps.

**Two indexes.** Salary grows at its own rate — contributions ride on it. Retirement lifestyle is anchored to the **last-drawn salary**, then inflates at price inflation, with **healthcare on its own (usually higher) rate**.

**Allocation & normalization.** At the starting age, active expense rows plus monthly savings should total 100% of income. Above 100%, every row is proportionately scaled by `100/total` in all calculations, with a red note stating the factor. Below 100%, the shortfall is simply unallocated.

**Accumulation.** Yearly: `corpus = (corpus + lumpsums landing this year) × (1 + return) + monthly savings × 12 × salary-index × normalization`. The lumpsum ("Already Accumulated Corpus") is absolute rupees — it neither scales with income nor inflates, and compounds from the year it lands, even if that is the retirement year itself (a 55- or 60-year-old starter is fully supported).

**Auto-linked freed money.** Each year-slider category (Education Loan, Child Education & Marriage, House EMI, Vehicle) owns a "Freed when … ends" savings tranche: its start age always equals the loan's end, its % mirrors the loan's. Shorten the loan and the corpus responds instantly. Edit the tranche's % to redirect less than 100%; Remove it to spend the freed money; Restore re-links.

**Post-retirement buckets (the Indian reality).** At retirement the corpus deploys into three buckets: **Annuity** (share 0–60%, rate 5.5–9%) whose principal is *locked for life* — it pays a level income and passes to the nominee, shown separately in the verdict; **FD/Liquid** (rate 5.5–12%); and **Equity/MF** (the remainder, rate 6–25%). Each retirement year is funded from the FD/liquid bucket, which is then topped back up to the **cash cover** level (0–7 years of expenses, default 3) by selling equity — so ready cash is always on hand while the rest keeps compounding. Surplus income parks back into FD. **The Magic Number is found by search**: the smallest corpus that survives to the plan-until age under this same policy, after pension/rent income.

**Retirement income streams.** Pension, rent, royalties: ₹/month at retirement, from/till ages, and an "inflates?" flag (rent yes, fixed annuity/pension no). These reduce the magic number directly; if income fully covers expenses, the verdict says so.

**Monte Carlo.** 1,000 simulated lives per recalculation (seeded — reproducible), swinging accumulation and equity-bucket returns by the volatility σ each year while FD and annuity stay fixed. The panel shows the 10th–90th percentile wealth band, the median path, failing lives in red, and a survival chip (green ≥ 80%). Flat returns overstate safety — the median simulated path grows slower than the average return (volatility drag), which is why an 118%-funded plan can be a coin-flip in real markets.

## 4. Control reference

**Levers:** monthly income at start · starting age 18–60 · inflation % + simple/compound · salary growth % · healthcare inflation % · accumulation return % · volatility σ · corpus buckets (annuity share+rate, FD share+rate, equity rate) · retirement expense ratio % · retirement age (auto-clamps ≥ start) · plan-until age.

**Expense rows:** % of income, from/till ages *or* a year-slider (capped at retirement − start; stored years survive slider round-trips), "in retirement till" age (0 = stops). Rows marked "at start" follow the starting-age slider; typing a from-age makes a row absolute.

**Accumulation rows:** the lumpsum (absolute ₹, editable landing age — also models future windfalls), base savings %, auto-linked freed tranches.

**Income rows:** all user-added, fully deletable.

**Buttons:** predefined rows have **Remove** (grey to zero, values preserved) and **Restore** (defaults, re-linked); user-added rows also have **Delete** (permanent).

**Sharing & output:** the **🔗 Copy share link** button encodes the entire scenario — plus your optional name and email — into a URL; opening it restores everything and shows "Scenario shared by …" so the recipient knows who's asking and where to reply. **⬇ Download PDF report** prints a dated, assumption-stamped report (choose "Save as PDF"). The **feedback form** opens your email app pre-addressed with subject "Retirement Corpus App — {your words}", optionally attaching your scenario summary — only if you tick the box.

## 5. For contributors — where things live

One HTML file, three zones. **CSS** at top: the palette is six variables in `:root`; `.mini`/`.rmini`, `.spanline`, print styles. **State**: `expenses[]`, `savings[]`, `incomes[]`, and `P` (all levers). Row flags: `atStart`, `slider`+`years`, `kind:"lump"`, `auto`+`link`, `med`, `custom`, `active`, `overridden`, `def` (Restore snapshot). **Engine**: `mult` (salary index), `infGrow`, `retExpense`, `walkBuckets`, `requiredCorpus` (binary search), `runMonteCarlo` (mulberry32-seeded), `simulate`, `syncAutoTranches`, `norm`. **Rendering**: `renderTables`, `renderVerdict`, `renderChart1/2/3`, with `recalc()` as the single heartbeat. Share links live in `shareState`/`copyShareLink`/`loadFromHash`.

Common enhancements: change defaults (edit row arrays *and* matching HTML `value=` attributes); add a category (append a row object — `slider:true, years:N` auto-creates its freed tranche); add a lever (copy a `.lever` block, add its id to the bind list); new ideas welcome via the feedback form. The engine is DOM-light by design — it can be smoke-tested in Node by stubbing `document` and calling `simulate()` directly; keep new logic in engine functions, not render strings.

**Visitor stats:** a GoatCounter snippet sits just before `</body>`. It counts page views only — it never sees the numbers users type — and can email a periodic report.

## 6. Honest limits

Yearly steps; contributions at year-end, lumpsums at year-start; ages are integers. Working-year expense spans affect the corpus only through their freed tranches — by design, matching the original Excel. The expense ratio applies uniformly to continuing categories. Monte Carlo randomizes market returns only (salary and inflation stay deterministic), with independent yearly draws — real markets have fat tails and momentum this doesn't capture. No tax modeling, deliberately. Nothing here is a return guarantee.

---
*Version: July 2026 — percentage ledger · duration sliders · auto-linked freed EMIs · lumpsum & late-starter support · salary step-up · healthcare inflation · annuity/FD/equity buckets · income streams · share links · Monte Carlo · PDF report · feedback form.*
