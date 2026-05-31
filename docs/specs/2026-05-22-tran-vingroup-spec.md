---
template: spec
purpose: "Technical specification for model-driven projects — defines scope, inputs, formulas, validation, and analysis requirements precisely enough that any competent executor (human or LLM) can produce correct output"
audience: student
fields_required: [title, author, date, version, company, scope, model_architecture, data_inputs, derived_inputs, formulas, validation, analysis_requirements, output_format, references]
naming_convention: "YYYY-MM-DD-{slug}.md"
courses: [BUS-629]
notes: "Authored for BUS-629 VEMBA Stage 4. v3 — named-range notation completed for all 25+ ratios across all six categories; validation rules expanded to cover all six categories per instructor feedback 2026-05-30. All figures in VND millions. Reporting standard: Vietnamese Accounting Standards (VAS). FY2025 current year, FY2024 prior year."
---

# Technical Specification: Vingroup Accounting & Performance Ratios Analysis

**Author:** Tan Tran
**Date:** 2026-05-22
**Version:** 3.0 (named-range notation completed; validation rules expanded)
**Company:** Vingroup Joint Stock Company (VIC, HOSE)

---

## 1. Scope & Objective

This specification defines the full ratio model and analysis for **Vingroup Joint Stock Company (ticker: VIC, listed on HOSE)** for fiscal year ending **31 December 2025** (FY2025), with prior-year comparatives from **FY2024**.

- **Reporting Standard:** Vietnamese Accounting Standards (VAS) — audited consolidated financials
- **Reporting Currency / Units:** Vietnamese Dong (VND), all figures in **VND millions** unless otherwise noted
- **Exchange Rate Reference:** 25,450 VND/USD as of 31 Dec 2025 (State Bank of Vietnam year-end rate)
- **Analytical Objective:** Compute all 25+ performance, profitability, efficiency, leverage, liquidity, and Du Pont ratios; interpret results against conglomerate-appropriate benchmarks; decompose ROE via Du Pont; and produce 3–5 actionable strategic recommendations
- **Intended Audience:** Graduate finance students and course instructor (BUS-629 VEMBA, Shidler College of Business, University of Hawaiʻi at Mānoa); assumes familiarity with corporate finance concepts but not with Vingroup specifically
- **Business Context:** Vingroup is a **diversified conglomerate** — not a pure-play real estate company. FY2025 revenue of VND 331.8 trillion reflects major contributions from VinFast (EV/auto), real estate, hospitality, and healthcare. Benchmarks must reflect this multi-segment structure.

---

## Part A — Model Specification

### 2. Model Architecture

The model is a multi-tab Excel workbook structured as follows:

| Tab | Contents | Role |
|-----|----------|------|
| **Cover** | Company metadata, color key, named-range convention guide | Reference only |
| **Balance Sheet** | FY2025 and FY2024 balance sheet line items | Data input (yellow cells) |
| **Income Statement** | FY2025 and FY2024 income statement items; % of sales columns auto-computed | Data input (yellow cells) |
| **Cash Flow Statement** | FY2025 and FY2024 operating, investing, financing cash flows | Data input (yellow cells) |
| **Ratios** | Four analyst assumptions (blue cells); all derived inputs and ratio outputs auto-compute from named ranges | Assumption input + output |
| **Notes** | Company metadata, data sources, AI usage declaration, self-check instructions | Documentation |

**Color coding convention:**

| Style | Meaning |
|-------|---------|
| Yellow background | DATA INPUTS — overwrite with company figures |
| Light-blue background + blue text | ASSUMPTIONS — analyst inputs (share price, shares, WACC, tax rate) |
| Green text | FORMULAS — cross-sheet references; do not overwrite |
| Gray background | RATIO OUTPUTS — computed values; do not overwrite |

**Data flow:** Balance Sheet / Income Statement / Cash Flow tabs → named ranges → Ratios tab derived inputs → Ratios tab output cells.

---

### 3. Data Inputs

All values below are sourced from the Stage 3 populated workbook. The executor does **not** look up, infer, or estimate any figure — every data point is stated explicitly here.

#### 3a. Balance Sheet Inputs (VND millions)

| Named Range | Description | FY2025 Value | FY2024 Value |
|-------------|-------------|-------------|-------------|
| `BAL_cash_marketable_securities_curr` | Cash and marketable securities | 83,380,686 | 51,301,250 |
| `BAL_receivables_curr` | Receivables (current year) — **used in Quick Ratio** | 267,209,963 | 190,046,565 |
| `BAL_receivables_prior` | Receivables (prior year) — used in turnover ratios | 190,046,565 | — |
| `BAL_inventories_curr` | Inventories (current year) | 201,580,276 | 114,090,183 |
| `BAL_inventories_prior` | Inventories (prior year) — used in turnover ratios | 114,090,183 | — |
| `BAL_other_current_assets_curr` | Other current assets | 106,601,539 | 41,041,913 |
| `BAL_assets_current_curr` | Total current assets | 658,772,464 | 396,479,911 |
| `BAL_ppe_gross_curr` | Property, plant & equipment (gross) | 298,694,616 | 258,629,492 |
| `BAL_accumulated_depreciation_curr` | Less accumulated depreciation | 103,300,472 | 75,686,159 |
| `BAL_ppe_net_curr` | Net tangible fixed assets | 195,394,144 | 182,943,333 |
| `BAL_intangibles_curr` | Intangible assets (incl. goodwill) | 3,955,994 | 4,517,414 |
| `BAL_other_assets_curr` | Other assets | 260,500,023 | 252,663,245 |
| `BAL_assets_total_curr` | **Total assets (current year)** | **1,118,622,625** | 836,603,903 |
| `BAL_assets_total_prior` | **Total assets (prior year)** | **836,603,903** | — |
| `BAL_debt_short_term_curr` | Debt due for repayment (short-term) | 114,000,484 | 95,189,145 |
| `BAL_accounts_payable_curr` | Accounts payable | 57,785,917 | 45,035,056 |
| `BAL_other_current_liabilities_curr` | Other current liabilities | 415,668,163 | 365,067,839 |
| `BAL_liabilities_current_curr` | **Total current liabilities** | **587,454,564** | 505,292,040 |
| `BAL_debt_long_term_curr` | Long-term debt (current year) | 224,500,548 | 132,730,912 |
| `BAL_debt_long_term_prior` | Long-term debt (prior year) | 132,730,912 | — |
| `BAL_other_long_term_liabilities_curr` | Other long-term liabilities | 155,178,578 | 44,746,470 |
| `BAL_liabilities_total_curr` | **Total liabilities** | **967,133,690** | 682,769,422 |
| `BAL_common_stock_curr` | Common stock and paid-in capital | 97,211,548 | 109,366,131 |
| `BAL_retained_earnings_curr` | Retained earnings | 54,277,387 | 44,468,350 |
| `BAL_equity_shareholders_curr` | **Total shareholders' equity (current year)** | **151,488,935** | 153,834,481 |
| `BAL_equity_shareholders_prior` | **Total shareholders' equity (prior year)** | **153,834,481** | — |

> **Note:** `BAL_common_stock_curr + BAL_retained_earnings_curr = 151,488,935` matches `BAL_equity_shareholders_curr` exactly — confirmed no minority interest gap in the VAS consolidated presentation.

#### 3b. Income Statement Inputs (VND millions, FY2025)

| Named Range | Description | FY2025 Value | FY2024 Value |
|-------------|-------------|-------------|-------------|
| `INC_sales` | Net sales | 331,837,561 | 189,068,040 |
| `INC_cost_goods_sold` | Cost of goods sold | 247,489,507 | 139,140,098 |
| `INC_sga` | Selling, general & administrative expenses | 49,053,914 | 33,202,226 |
| `INC_depreciation` | Depreciation | 31,665,247 | 22,627,124 |
| `INC_ebit` | Earnings before interest and taxes (EBIT) | 3,628,893 | (5,901,408) |
| `INC_other_income` | Other income | 51,968,218 | 45,620,158 |
| `INC_interest_expense` | Interest expense | 29,159,736 | 22,980,044 |
| `INC_taxable_income` | Taxable income | 26,437,375 | 16,738,706 |
| `INC_taxes` | Taxes | 15,372,561 | 11,462,648 |
| `INC_net` | **Net income** | **11,064,814** | 5,276,058 |
| `INC_dividends` | Dividends paid | — | 666,188 |
| `INC_retained` | Addition to retained earnings | 11,064,814 | 4,609,870 |

> **Critical flag — Other Income:** `INC_other_income` (VND 51,968,218M) is **14.3× larger than EBIT** (VND 3,628,893M). This means net income is entirely dependent on non-operating income. The Stage 5 analysis must assess whether this income is recurring. Without it, Vingroup would report a net loss.

#### 3c. Cash Flow Inputs (VND millions, FY2025)

| Named Range | Description | FY2025 Value |
|-------------|-------------|-------------|
| `CASH_operating` | Cash provided by operations | 68,854,782 |
| `CASH_capex` | Capital expenditures | (76,157,072) |
| `CASH_investing` | Cash provided by (used for) investments | (139,928,403) |
| `CASH_financing` | Cash provided by (used for) financing | 102,009,230 |
| `CASH_net_change` | Net increase in cash | 30,935,609 |

#### 3d. Analyst Assumptions

| Named Range | Description | Value |
|-------------|-------------|-------|
| `share_price` | Share price (VND/share) — HOSE closing 31 Dec 2025 | 169,600 |
| `shares_outstanding` | Shares outstanding (millions) | 7,706 |
| `cost_capital` | Cost of capital / WACC | 0.12 (12.0%) |
| `tax_rate` | Corporate tax rate | 0.20 (20.0%) |
| `yearCurrent` | Current fiscal year | 2025 |
| `yearStart` | Prior fiscal year | 2024 |

> **WACC derivation:** Risk-free rate 9.5% (10-yr Vietnam Government Bond yield) + equity risk premium 5.5% × beta 1.56 (Yahoo Finance 5Y monthly), with 67% debt weight and cost of debt 9–10% (Vingroup coupon rates). Tax rate 20% is Vietnam statutory rate; effective rate may vary by subsidiary.

---

### 4. Derived Inputs

All intermediate computed values used in ratio formulas. Formulas stated in named-range notation. All values verified numerically.

| Named Range | Description | Formula | Computed Value (VND millions) |
|-------------|-------------|---------|-------------------------------|
| `market_capitalization` | Market cap | `share_price × shares_outstanding` | 1,306,937,600 |
| `startYear_equity` | Equity at start of year | `BAL_equity_shareholders_prior` | 153,834,481 |
| `startYear_inventory` | Inventory at start of year | `BAL_inventories_prior` | 114,090,183 |
| `startYear_receivables` | Receivables at start of year | `BAL_receivables_prior` | 190,046,565 |
| `startYear_total_assets` | Total assets at start of year | `BAL_assets_total_prior` | 836,603,903 |
| `startYear_total_capitalization` | Total cap at start of year | `BAL_debt_long_term_prior + BAL_equity_shareholders_prior` | 286,565,393 |
| `currentYear_after_tax_operating_income` | After-tax operating income (NOPAT) | `INC_net + (1 − tax_rate) × INC_interest_expense` | **34,392,603** |
| `currentYear_daily_sales_average` | Average daily sales | `INC_sales / 365` | 909,144 |
| `currentYear_equity` | Book value of equity | `BAL_equity_shareholders_curr` | 151,488,935 |
| `currentYear_cash_marketable_securities` | Cash + marketable securities | `BAL_cash_marketable_securities_curr` | 83,380,686 |
| `currentYear_assets_current` | Current assets | `BAL_assets_current_curr` | 658,772,464 |
| `currentYear_liabilities_current` | Current liabilities | `BAL_liabilities_current_curr` | 587,454,564 |
| `currentYear_cost_goods_sold_daily` | Daily COGS | `INC_cost_goods_sold / 365` | 678,053 |
| `currentYear_debt_long_term` | Long-term debt | `BAL_debt_long_term_curr` | 224,500,548 |
| `currentYear_working_capital_net` | Net working capital | `BAL_assets_current_curr − BAL_liabilities_current_curr` | 71,317,900 |
| `currentYear_assets_total` | Total assets | `BAL_assets_total_curr` | 1,118,622,625 |
| `currentYear_total_capitalization` | Total capitalization | `currentYear_debt_long_term + currentYear_equity` | 375,989,483 |
| `currentYear_liabilities_total` | Total liabilities | `BAL_liabilities_total_curr` | 967,133,690 |
| `avg_equity` | Average equity | `AVERAGE(startYear_equity, currentYear_equity)` | 152,661,708 |
| `avg_total_assets` | Average total assets | `AVERAGE(startYear_total_assets, currentYear_assets_total)` | 977,613,264 |
| `avg_total_capitalization` | Average total cap | `AVERAGE(startYear_total_capitalization, currentYear_total_capitalization)` | 331,277,438 |

> **NOPAT verification:** 11,064,814 + (0.80 × 29,159,736) = 11,064,814 + 23,327,789 = **34,392,603** VND millions. *(v1 had a typo of 34,392,803 — corrected in v2.)*

---

### 5. Ratio Definitions & Formulas

All 25+ ratios organized by category. Named-range formulas stated precisely. **Computed values included** so the Stage 5 executor can verify their model matches before proceeding to analysis.

#### Performance Ratios

| Ratio | Named Range | Formula | Unit | Computed Value | Interpretation Guide |
|-------|------------|---------|------|----------------|----------------------|
| Market Value Added (MVA) | `RATIO_mva` | `market_capitalization − currentYear_equity` | VND millions | 1,155,448,665 | Positive = market values firm above book |
| Market-to-Book Ratio | `RATIO_market_to_book` | `market_capitalization / currentYear_equity` | × | 8.63× | >1 = market premium to book |
| Economic Value Added (EVA) | `RATIO_eva` | `currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)` | VND millions | +4,756 | Barely positive — value marginally created above 12% hurdle rate |

#### Profitability Ratios

| Ratio | Named Range | Formula | Unit | Computed Value | Interpretation Guide |
|-------|------------|---------|------|----------------|----------------------|
| ROA (start) | `RATIO_roa_start` | `currentYear_after_tax_operating_income / startYear_total_assets` | % | 4.11% | Prior-year asset base efficiency |
| ROC (start) | `RATIO_roc_start` | `currentYear_after_tax_operating_income / startYear_total_capitalization` | % | 12.00% | Return on long-term capital |
| ROE (start) | `RATIO_roe_start` | `INC_net / startYear_equity` | % | 7.19% | Net return to equity holders |
| ROA (avg) | `RATIO_roa_avg` | `currentYear_after_tax_operating_income / avg_total_assets` | % | 3.52% | Smoothed |
| ROC (avg) | `RATIO_roc_avg` | `currentYear_after_tax_operating_income / avg_total_capitalization` | % | 10.38% | Smoothed |
| ROE (avg) | `RATIO_roe_avg` | `INC_net / avg_equity` | % | 7.25% | Smoothed |

#### Efficiency Ratios

| Ratio | Named Range | Formula | Unit | Computed Value | Interpretation Guide |
|-------|------------|---------|------|----------------|----------------------|
| Asset Turnover | `RATIO_asset_turnover` | `INC_sales / startYear_total_assets` | × | 0.397× | Revenue per VND prior-year assets |
| Receivables Turnover | `RATIO_receivables_turnover` | `INC_sales / startYear_receivables` | × | 1.746× | Times receivables collected annually |
| Avg Collection Period | `RATIO_avg_collection_period` | `startYear_receivables / currentYear_daily_sales_average` | Days | 209 days | **Very long** — flag for analysis |
| Inventory Turnover | `RATIO_inventory_turnover` | `INC_cost_goods_sold / startYear_inventory` | × | 2.169× | Times inventory sold annually |
| Days in Inventory | `RATIO_days_in_inventory` | `startYear_inventory / currentYear_cost_goods_sold_daily` | Days | 168 days | Long cycle — real estate normal |
| Profit Margin | `RATIO_profit_margin` | `INC_net / INC_sales` | % | 3.33% | Net profit per VND revenue |
| Operating Profit Margin | `RATIO_operating_profit_margin` | `currentYear_after_tax_operating_income / INC_sales` | % | 10.36% | After-tax operating efficiency |

#### Leverage Ratios

| Ratio | Named Range | Formula | Unit | Computed Value | Interpretation Guide |
|-------|------------|---------|------|----------------|----------------------|
| LT Debt Ratio | `RATIO_lt_debt_ratio` | `currentYear_debt_long_term / (currentYear_debt_long_term + currentYear_equity)` | % | 59.71% | LT debt share of long-term capital |
| LT Debt-Equity Ratio | `RATIO_lt_debt_equity` | `currentYear_debt_long_term / currentYear_equity` | × | 1.482× | LT debt per VND equity |
| Total Debt Ratio | `RATIO_total_debt_ratio` | `currentYear_liabilities_total / currentYear_assets_total` | % | 86.46% | Share of assets financed by liabilities |
| **Times Interest Earned (TIE)** | `RATIO_tie` | `INC_ebit / INC_interest_expense` | × | **0.124×** | **⚠ CRITICAL: EBIT covers only 12.4% of interest expense. Sub-1× means operating profit alone cannot service debt. Vingroup survives due to INC_other_income (VND 51,968,218M). Stage 5 must explain this explicitly.** |
| Cash Coverage | `RATIO_cash_coverage` | `(INC_ebit + INC_depreciation) / INC_interest_expense` | × | 1.210× | Adds back depreciation — marginally above 1× |
| Debt Burden | `RATIO_debt_burden` | `INC_net / currentYear_after_tax_operating_income` | × | 0.322× | 32.2% of operating profit reaches equity holders |
| Leverage Ratio | `RATIO_leverage` | `currentYear_assets_total / currentYear_equity` | × | 7.384× | Equity multiplier; primary ROE driver |

#### Liquidity Ratios

| Ratio | Named Range | Formula | Unit | Computed Value | Interpretation Guide |
|-------|------------|---------|------|----------------|----------------------|
| NWC to Assets | `RATIO_nwc_to_assets` | `currentYear_working_capital_net / currentYear_assets_total` | % | 6.38% | Thin positive buffer |
| Current Ratio | `RATIO_current_ratio` | `currentYear_assets_current / currentYear_liabilities_current` | × | 1.121× | Near minimum acceptable level |
| Quick Ratio | `RATIO_quick_ratio` | `(currentYear_cash_marketable_securities + BAL_receivables_curr) / currentYear_liabilities_current` | × | 0.597× | **Below 1× — liquid assets cannot cover current liabilities** |
| Cash Ratio | `RATIO_cash_ratio` | `currentYear_cash_marketable_securities / currentYear_liabilities_current` | × | 0.142× | Cash covers only 14.2% of current liabilities |

> **Quick Ratio note:** Formula uses `BAL_receivables_curr = 267,209,963` (FY2025 current-year figure) explicitly — not the prior-year alias `startYear_receivables`.

#### Du Pont System

| Ratio | Named Range | Formula | Unit | Computed Value | Note |
|-------|------------|---------|------|----------------|------|
| ROA (Du Pont) | `RATIO_roa_dupont` | `RATIO_asset_turnover × RATIO_operating_profit_margin` | % | 4.11% | ✓ Must match ROA (start) exactly |
| ROE (Du Pont) | `RATIO_roe_dupont` | `RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden` | % | 9.77% | Will **not** match ROE (start) = 7.19% — see V2 |

---

### 6. Validation Rules

The executor must verify all checks below before proceeding to analysis. Checks are organized by the same six categories as §5 to ensure complete coverage.

---

**PERFORMANCE CHECKS**

**VP1 — EVA sign consistency:**
`RATIO_eva = currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)`
= 34,392,603 − (0.12 × 286,565,393) = 34,392,603 − 34,387,847 = **+4,756** VND millions.
Must be positive (barely). If negative, check NOPAT formula or WACC input.

**VP2 — Market-to-Book sanity:**
`RATIO_market_to_book = market_capitalization / currentYear_equity`
= 1,306,937,600 / 151,488,935 = **8.63×**.
Must be >1 (Vingroup trades at a premium to book). If <1, recheck `share_price` or `shares_outstanding`.

---

**PROFITABILITY CHECKS**

**VPR1 — ROA (start) cross-check:**
`RATIO_roa_start = currentYear_after_tax_operating_income / startYear_total_assets`
= 34,392,603 / 836,603,903 = **4.11%**.
Must match Du Pont ROA exactly (see V1 below). Any discrepancy = formula error; stop and investigate.

**VPR2 — ROC vs. WACC:**
`RATIO_roc_start = 12.00%` must equal `cost_capital = 12.0%` within ±0.05%. This confirms near-zero EVA (+4,756) is arithmetically consistent with ROC barely clearing WACC. If ROC deviates materially, check `startYear_total_capitalization` derivation.

---

**EFFICIENCY CHECKS**

**VE1 — ACP × daily sales = prior receivables:**
`RATIO_avg_collection_period × currentYear_daily_sales_average`
= 209 × 909,144 = **190,011,096 ≈ startYear_receivables (190,046,565)**. ✓ Minor rounding acceptable (within 0.02%).

**VE2 — Days in Inventory × daily COGS = prior inventory:**
`RATIO_days_in_inventory × currentYear_cost_goods_sold_daily`
= 168 × 678,053 = **113,912,904 ≈ startYear_inventory (114,090,183)**. ✓ Minor rounding acceptable (within 0.16%).

---

**LEVERAGE CHECKS**

**V1 (formerly VL1) — Du Pont ROA (must match exactly):**
`RATIO_asset_turnover × RATIO_operating_profit_margin = 0.3966 × 0.1036 = 4.11%`
Must equal `RATIO_roa_start = 34,392,603 / 836,603,903 = 4.11%`. ✓ Confirmed. Any discrepancy = formula error; stop and investigate.

**VL2 — TIE critical flag (sub-1× expected — must be flagged, not corrected):**
`RATIO_tie = INC_ebit / INC_interest_expense = 3,628,893 / 29,159,736 = 0.124×`.
This is below 1.0×. The spec requires Stage 5 to identify `INC_other_income` (51,968,218) as the bridging item enabling net profitability despite sub-1× TIE, and to assess whether this other income is recurring.

**VL3 — Total Debt Ratio complement:**
`RATIO_total_debt_ratio + (currentYear_equity / currentYear_assets_total)`
= 86.46% + (151,488,935 / 1,118,622,625) = 86.46% + 13.54% = **100.00%**. ✓ Must sum to 100%.

---

**LIQUIDITY CHECKS**

**VLQ1 — NWC consistency:**
`currentYear_working_capital_net = currentYear_assets_current − currentYear_liabilities_current`
= 658,772,464 − 587,454,564 = **71,317,900**.
`RATIO_nwc_to_assets = 71,317,900 / 1,118,622,625 = 6.38%`. ✓ Confirmed.

**VLQ2 — Quick Ratio uses current-year receivables (not prior-year alias):**
`RATIO_quick_ratio` numerator = `currentYear_cash_marketable_securities + BAL_receivables_curr`
= 83,380,686 + 267,209,963 = **350,590,649**.
`RATIO_quick_ratio = 350,590,649 / 587,454,564 = 0.597×`. ✓ Confirmed.
**Do NOT substitute `startYear_receivables` (190,046,565) here** — that would give 0.466×, which is incorrect.

---

**DU PONT CHECKS**

**V2 (formerly VDP1) — Du Pont ROE time-mismatch (expected divergence — explain, do not fix):**
`RATIO_roe_dupont = RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden`
= 7.384 × 0.397 × 0.1036 × 0.322 = **9.77%** vs. `RATIO_roe_start = 7.19%`.
Divergence of 2.57% is expected and arises because `RATIO_leverage` uses current-year assets (1,118,622,625) while `RATIO_asset_turnover` uses prior-year assets (836,603,903). This is a known model design feature. Stage 5 must acknowledge and explain this explicitly.

**VDP2 — Balance Sheet balance (prerequisite for all ratios):**
`BAL_assets_total_curr` (1,118,622,625) = `BAL_liabilities_total_curr + BAL_equity_shareholders_curr`
(967,133,690 + 151,488,935 = 1,118,622,625). ✓ Confirmed.

**VDP3 — Net Income reconciliation (prerequisite for all profitability ratios):**
`INC_taxable_income − INC_taxes = 26,437,375 − 15,372,561 = 11,064,814 = INC_net`. ✓ Confirmed.

**VDP4 — NOPAT formula:**
`currentYear_after_tax_operating_income = INC_net + (1 − tax_rate) × INC_interest_expense`
= 11,064,814 + 0.80 × 29,159,736 = **34,392,603**. ✓ Confirmed.
*(v1 had a typo of 34,392,803 — corrected in v2.)*

---

## Part B — Analysis Specification

### 7. Analysis Requirements

For each category: (a) state computed values, (b) compare to benchmarks below, (c) interpret in Vingroup's specific conglomerate context, (d) flag cross-category connections.

**Benchmark peers (conglomerate-appropriate):**

| Peer | Type | Market |
|------|------|--------|
| Masan Group (MSN, HOSE) | Vietnam diversified conglomerate | Vietnam |
| CapitaLand Group | Real estate + diversified conglomerate | Singapore |
| SM Group | Diversified conglomerate | Philippines |
| Vietnam large-cap average | VN-Index top 20 | Vietnam |

**Performance (MVA = 1,155,448,665; Market-to-Book = 8.63×; EVA = +4,756)**
- EVA is barely positive (+4,756 VND millions on a capital base of 286,565,393). This means Vingroup is creating value above its 12% hurdle rate, but only marginally. Interpret: Is 8.63× market-to-book justified by this thin EVA?
- Cross-category: EVA must be read alongside ROC (12.00%) — ROC barely clears the 12% WACC hurdle, explaining the near-zero EVA.

**Profitability (ROA start = 4.11%; ROC start = 12.00%; ROE start = 7.19%)**
- Benchmark: Vietnam large-cap conglomerate ROE typically 8–15%; ROA 3–6%.
- Key question: ROC of 12.00% exactly meets WACC — any cost increase or revenue miss pushes EVA negative. Has the 75% revenue growth (VND 189B → VND 332B) produced proportional profitability? Note EBIT grew from negative (FY2024: -5,901,408) to positive (FY2025: +3,628,893) — an improvement, but still thin.
- Cross-category: Profitability feeds Du Pont decomposition directly.

**Efficiency (Asset Turnover = 0.397×; ACP = 209 days; Days in Inventory = 168 days)**
- Benchmark: Diversified conglomerates with significant real estate and auto typically show asset turnover 0.25–0.50×. Vingroup at 0.397× is within range.
- Key question: Average collection period of 209 days is exceptionally long. For a conglomerate with real estate pre-sales and auto receivables, some lag is expected, but 209 days warrants explanation. Is this driven by VinFast dealer receivables or real estate installment collections?
- Cross-category: Asset turnover is a direct Du Pont input (`RATIO_asset_turnover`).

**Leverage (Total Debt Ratio = 86.46%; TIE = 0.124×; Cash Coverage = 1.210×; Debt Burden = 0.322×)**
- Benchmark: Vietnam property developers typically 75–85% total debt ratio; conglomerates with capital-intensive subsidiaries (like VinFast) may be higher.
- **TIE = 0.124× is the most critical finding in this model.** EBIT covers only 12.4% of interest expense. The executor must explain: (1) why Vingroup is not in default (answer: INC_other_income of VND 51,968,218M bridges the gap); (2) whether that other income is sustainable; (3) what happens to solvency if other income normalises.
- Cash Coverage = 1.210× — adding back depreciation (VND 31,665,247M) brings coverage just above 1×, but still thin.
- Long-term debt grew 69% YoY (132,731 → 224,501). Cross-category: High leverage drives RATIO_leverage = 7.384× which is the dominant Du Pont ROE multiplier.

**Liquidity (Current Ratio = 1.121×; Quick Ratio = 0.597×; Cash Ratio = 0.142×)**
- Benchmark: Current ratio >1.2 generally comfortable; quick ratio >0.8 preferred.
- Vingroup's quick ratio of 0.597× means liquid assets (cash + receivables) cover only 59.7% of current liabilities. Combined with TIE = 0.124×, this creates compounded short-term risk.
- Cross-category: Low liquidity + high leverage + sub-1× TIE = three concurrent stress signals. Stage 5 must assess whether these are structurally linked to the VinFast investment cycle or represent a genuine liquidity concern.

**Du Pont**
- Full decomposition: ROE = RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden
- = 7.384 × 0.397 × 0.1036 × 0.322 = **9.77%** (Du Pont) vs. 7.19% (direct — time-mismatch per V2)
- Primary driver is clearly RATIO_leverage (7.384×). Without this leverage, ROE would be approximately 1.32% (= 0.397 × 0.1036 × 0.322). Stage 5 must assess sustainability.

---

### 8. Du Pont Decomposition

```
ROE (Du Pont) = RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden
```

**Required steps:**

1. State each component with its formula and computed value:
   - `RATIO_leverage` = `currentYear_assets_total / currentYear_equity` = 1,118,622,625 / 151,488,935 = **7.384×**
   - `RATIO_asset_turnover` = `INC_sales / startYear_total_assets` = 331,837,561 / 836,603,903 = **0.397×**
   - `RATIO_operating_profit_margin` = `currentYear_after_tax_operating_income / INC_sales` = 34,392,603 / 331,837,561 = **10.36%**
   - `RATIO_debt_burden` = `INC_net / currentYear_after_tax_operating_income` = 11,064,814 / 34,392,603 = **0.322×**

2. Multiply through step-by-step and show intermediate products.

3. Compare Du Pont ROE (9.77%) to direct ROE (7.19%) and explain the 2.57% divergence using the time-mismatch rationale from V2.

4. Identify leverage (7.384×) as the dominant driver. Show what ROE would be at leverage = 3× (a more conservative level): estimated ROE ≈ 3 × 0.397 × 0.1036 × 0.322 ≈ **3.97%** — substantially lower.

5. Assess sustainability: leverage-driven ROE is fragile when TIE = 0.124×. Any rise in interest rates or decline in other income could create a solvency event.

6. Connect to §9: the Du Pont analysis motivates at least two recommendations — operating margin improvement and debt restructuring.

---

### 9. Strategic Recommendations

**Requirements:** 3 to 5 recommendations. Each must:
- Cite at least one specific ratio value computed in this model (not generic)
- Identify the specific risk or opportunity revealed
- State a concrete, actionable step with reference to Vingroup's business segments
- Acknowledge VAS reporting context and Vietnam market conditions where relevant

**Required framing — the following five areas must be addressed:**

**R1 — Debt servicing risk (evidence: TIE = 0.124×)**
TIE of 0.124× means EBIT covers only 12.4% of VND 29.2 trillion in annual interest expense. The recommendation must propose a specific action: e.g., refinancing short-term debt (VND 114,000,484M due) into longer-term instruments to reduce near-term cash flow pressure, or identifying which segments generate sufficient operating cash to ring-fence debt service.

**R2 — Other Income dependency (evidence: INC_other_income = VND 51,968,218M vs. INC_ebit = VND 3,628,893M)**
Other income is 14.3× larger than EBIT. The recommendation must identify what this income likely represents (asset disposals, investment gains, government support) and propose either: (a) a plan to grow core EBIT to reduce dependency, or (b) a disclosure enhancement so investors can assess recurrence.

**R3 — Receivables management (evidence: Average Collection Period = 209 days)**
ACP of 209 days is exceptionally long. The recommendation must connect this to a specific Vingroup business context (VinFast dealer financing? real estate installment structures?) and propose a concrete policy: e.g., tightening VinFast dealer credit terms from X days to Y days, or securitising real estate receivables to accelerate cash conversion.

**R4 — Capital allocation discipline (evidence: EVA = +4,756 VND millions; ROC = 12.00% exactly at WACC)**
ROC barely clears the 12% WACC hurdle, generating near-zero EVA despite VND 76,157,072M in capex during FY2025. The recommendation must address how Vingroup should prioritise future capex — which segment (VinFast EV, real estate, hospitality) generates returns above WACC — and propose a segment-level EVA hurdle rate framework.

**R5 — Liquidity buffer (evidence: Quick Ratio = 0.597×; Cash Ratio = 0.142×)**
Liquid assets cover only 59.7% of current liabilities. Combined with TIE = 0.124× and total debt ratio of 86.46%, the recommendation must propose a minimum cash buffer target and identify how Vingroup can achieve it (asset monetisation, committed credit facilities, working capital optimisation).

---

### 10. Output Format

**Document title:** Vingroup Joint Stock Company — Accounting & Performance Ratios Analysis, FY2025

**Sections (in this order):**

1. **Executive Summary** (150–200 words) — top 3 findings; overall financial health rating; one headline recommendation
2. **Company Overview** (100 words) — Vingroup conglomerate description, VIC/HOSE, VAS reporting, FY2025 context
3. **Ratio Summary Table** — all 25+ ratios: Ratio | Formula (named-range) | Value | Unit | vs. Benchmark
4. **Ratio Analysis by Category** — six categories (Performance, Profitability, Efficiency, Leverage, Liquidity, Du Pont): computed values → benchmark → Vingroup interpretation → cross-category connections. ~150–200 words each.
5. **Du Pont Decomposition** — four-factor breakdown per §8; step-by-step; time-mismatch explanation; leverage sustainability scenario.
6. **Strategic Recommendations** — R1–R5 per §9 format. Each: title → ratio evidence → risk/opportunity → actionable step.
7. **Data Sources & Limitations** — sources listed; VAS vs. IFRS note; flag that `INC_other_income` (VND 51,968,218M) requires disaggregation not available in consolidated VAS statements.

**Tone:** Professional, graduate-level finance. Define terms on first use. Write for a reader who knows finance but not Vingroup.

**Length:** 2,500–3,500 words (excluding ratio tables).

**Ratio table format:** Markdown tables with columns: Ratio | Formula (named-range) | Value | Unit | vs. Benchmark.

---

## References

- Vingroup Annual Report 2025 (audited consolidated financials, VAS): https://vingroup.net/en/investor-relations
- HOSE disclosure portal: https://www.hsx.vn
- VinFast Nasdaq disclosures: https://investors.vinfastauto.com
- State Bank of Vietnam year-end exchange rate (25,450 VND/USD, 31 Dec 2025)
- Yahoo Finance: VIC beta 1.56 (5-year monthly, retrieved for WACC estimation)
- BUS-629 Stage 1 ratios template: `models/templates/performance-ratios-template.xlsx`
- BUS-629 Stage 3 populated workbook: `models/builds/2026-05-22-tran-vingroup-financials.xlsx`
