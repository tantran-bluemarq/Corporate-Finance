# Vingroup Joint Stock Company: Ratio Analysis, FY2025

**Author:** Tan Tran | **Date:** 2026-05-30 | **Standard:** VAS | **Currency:** VND millions
**Raw output:** `deliverables/2026-05-22-tran-vingroup-llm-raw.md`
**Verification:** `analysis/validation/2026-05-22-tran-vingroup-stage5-verification.md`
**Spec retrospective:** `deliverables/2026-05-22-tran-vingroup-spec-retrospective.md`

---

## 1. Company & Data Summary

Vingroup (VIC, HOSE) is Vietnam's largest conglomerate: real estate (Vinhomes), EVs (VinFast/Nasdaq), hospitality (Vinpearl), healthcare (Vinmec). FY2025 financials are VAS audited, consolidated, year end 31 Dec 2025. All figures VND millions.

| Assumption | Value | Source |
|-----------|-------|--------|
| Share price | VND 169,600 | HOSE, 31 Dec 2025 |
| Shares outstanding | 7,706M | Vingroup FY2025 AR |
| WACC | 12.0% | Rf 9.5%, ERP 5.5%, beta 1.56 |
| Tax rate | 20.0% | Vietnam statutory CIT |

**Limitation:** VAS provides no segment breakdown. VinFast, Vinhomes, and Vinpearl cannot be isolated from the consolidated statements.

---

## 2. Ratio Results by Hypothesis

### H1: Leverage has risen sharply, pressuring liquidity ✅ CONFIRMED

> *Expected: VinFast build-out financed by external debt → D/E surge, declining current ratio and TIE.*

| Ratio | Formula | FY2025 | FY2024 | Change |
|-------|---------|--------|--------|--------|
| D/E (total debt / equity) | `(BAL_debt_long_term_curr + BAL_debt_short_term_curr) / BAL_equity_shareholders_curr` | **2.234×** | ~0.87× | ⬆ Sharp rise |
| LT Debt growth | FY2024 → FY2025 | 224,501 | 132,731 | **+69% YoY** |
| Total Debt Ratio | `BAL_liabilities_total_curr / BAL_assets_total_curr` | **86.46%** | 81.6% | ⬆ Rising |
| Leverage Ratio | `BAL_assets_total_curr / BAL_equity_shareholders_curr` | **7.384×** | N/A | High |
| TIE | `INC_ebit / INC_interest_expense` | **0.124×** | Negative | ⚠ Sub-1× |
| Cash Coverage | `(INC_ebit + INC_depreciation) / INC_interest_expense` | **1.210×** | N/A | Barely above 1× |
| Current Ratio | `BAL_assets_current_curr / BAL_liabilities_current_curr` | **1.121×** | N/A | Below comfort |
| Quick Ratio | `(BAL_cash + BAL_receivables_curr) / BAL_liabilities_current_curr` | **0.597×** | N/A | ⚠ Below 1× |

**Verdict:** Confirmed. Long-term debt grew 69% YoY (VND 132.7T → 224.5T) as VinFast drew capital for factory expansion. Total debt now funds 86.46% of all assets. TIE of 0.124× is the critical signal: EBIT covers only 12.4% of annual interest expense, with the gap bridged by VND 52T of Other Income. If that income shrinks, Vingroup cannot service debt from operations alone. Current ratio 1.121× and quick ratio 0.597× confirm liquidity has deteriorated exactly as hypothesised.

---

### H2: Real estate pre-sales used as internal funding ⚠ PARTIALLY SUPPORTED

> *Expected: Vinhomes pushed pre-sales aggressively → sharp rise in unearned revenue (customer deposits), widening gap between cash collected and revenue recognised.*

| Ratio / Item | Formula | FY2025 | FY2024 | Signal |
|-------------|---------|--------|--------|--------|
| Other Current Liabilities (deposit proxy) | Balance Sheet | **415,668,163** | 365,067,839 | +13.9% YoY |
| Revenue growth | FY2024 → FY2025 | 331,838 | 189,068 | +75.5% |
| Receivables growth | FY2024 → FY2025 | 267,210 | 190,047 | +40.6% |
| Avg Collection Period | `startYear_receivables / (INC_sales / 365)` | **209 days** | N/A | Very long |
| CFO / Net Income | `CASH_operating / INC_net` | **6.22×** | N/A | CFO far exceeds net income |

**Verdict:** Partially confirmed. The deposit proxy (Other Current Liabilities) grew 13.9% — meaningful in absolute terms (VND +50.6T) but slower than revenue growth of 75.5%, suggesting pre-sales acceleration was real but not the dominant driver. The stronger signal is CFO of VND 68.9T vs. Net Income of VND 11.1T (6.22×): cash collected significantly exceeds reported earnings, consistent with deposits received before revenue is recognised. ACP of 209 days confirms a large wedge between cash collection and revenue recognition across the business.

---

### H3: VinFast capex outpaced CFO, funded by CFF ✅ CONFIRMED

> *Expected: Capex surged with factory expansion → FCF deeply negative → gap funded by large CFF inflows.*

| Item | Formula | FY2025 Value |
|------|---------|-------------|
| Cash from Operations (CFO) | `CASH_operating` | **+68,854,782** |
| Capital Expenditures (Capex) | `CASH_capex` | **(76,157,072)** |
| **Free Cash Flow (FCF = CFO + Capex)** | N/A | **(7,302,290) ← NEGATIVE** |
| Capex as % of CFO | `abs(CASH_capex) / CASH_operating` | **110.6%** |
| Cash from Financing (CFF) | `CASH_financing` | **+102,009,230** |
| CFF covers FCF shortfall? | N/A | Yes: CFF is 14× the FCF gap |
| Net cash change | N/A | +30,935,609 |

**Verdict:** Confirmed. Capex of VND 76.2T exceeded CFO of VND 68.9T by 10.6%, producing **negative FCF of VND -7.3T**. The entire gap — and more — was funded by CFF of VND +102T from new debt and equity raises. Vingroup is in a phase where operations cannot self-fund growth and the company depends on continued capital market access. If credit markets tighten, this funding model breaks.

---

## 3. Full Ratio Summary Table

### Performance

| Ratio | Value | Unit | vs. Benchmark |
|-------|-------|------|---------------|
| MVA | 1,155,448,665 | VND millions | Large positive |
| Market-to-Book | 8.63 | × | High vs. conglomerate avg 2 to 4x |
| EVA | +4,756 | VND millions | Near-zero on VND 286T capital base |

### Profitability

| Ratio | Value | Unit | Note |
|-------|-------|------|------|
| ROA (start) | 4.11% | % | In range |
| ROC (start) | 12.00% | % | Exactly at WACC, no surplus |
| ROE (start) | 7.19% | % | Below VN benchmark 8 to 15% |
| ROA (avg) | 3.52% | % | N/A |
| ROC (avg) | 10.38% | % | Below WACC |
| ROE (avg) | 7.25% | % | N/A |
| EBIT Margin (added, missing from LLM) | **1.09%** | % | ⚠ True core operating signal |
| Net Profit Margin | 3.33% | % | Inflated by Other Income |
| NOPAT Margin | 10.36% | % | Interest add-back inflates |

### Efficiency

| Ratio | Value | Unit | Note |
|-------|-------|------|------|
| Asset Turnover | 0.397 | × | Within range |
| Receivables Turnover | 1.746 | × | Slow |
| Avg Collection Period | 209 | days | Very long, 7 months |
| Inventory Turnover (spec) | 2.169 | × | ⚠ Overstated, see below |
| **Inventory Turnover (corrected)** | **1.568** | × | Average method; inventory grew 77% YoY |
| Days in Inventory | 168 | days | Long cycle |

**Inventory Turnover correction:** LLM used start-of-year inventory (2.169×). Inventory grew 77% YoY (114,090 → 201,580), so average method is more accurate:
`247,489,507 / ((114,090,183 + 201,580,276) / 2) = 1.568×`: 38% lower than LLM stated.

### Leverage

| Ratio | Value | Unit | Note |
|-------|-------|------|------|
| LT Debt Ratio | 59.71% | % | High |
| LT Debt-Equity | 1.482 | × | Debt-heavy |
| Total Debt Ratio | 86.46% | % | Above benchmark |
| **TIE** | **0.124** | × | ⚠ CRITICAL |
| Cash Coverage | 1.210 | × | Barely above 1× |
| Debt Burden | 0.322 | × | 32% of NOPAT reaches equity |
| Leverage Ratio | 7.384 | × | Primary ROE driver |

### Liquidity

| Ratio | Value | Unit | Note |
|-------|-------|------|------|
| NWC to Assets | 6.38% | % | Thin |
| Current Ratio | 1.121 | × | Below 1.2× comfort |
| Quick Ratio | 0.597 | × | ⚠ Below 1× |
| Cash Ratio | 0.142 | × | Very low |

### Du Pont

| Component | Value |
|-----------|-------|
| Leverage | 7.384× |
| Asset Turnover | 0.397× |
| Operating Profit Margin | 10.36% |
| Debt Burden | 0.322× |
| **ROE (Du Pont)** | **9.77%** |
| ROE (direct) | 7.19% |
| Divergence | +2.57% (expected per V2 time-mismatch) |

---

## 4. Du Pont Analysis

```
ROE = 7.384 × 0.397 × 0.1036 × 0.322 = 9.77%
```

Leverage (7.384×) is doing almost all the work. At conservative leverage of 3×, ROE drops to 3.97%: below Vietnam's risk-free rate of 9.5%. Without leverage, the business earns approximately 1.32% ROE.

**Time-mismatch (V2):** Du Pont ROE (9.77%) differs from direct ROE (7.19%) by 2.57% because RATIO_leverage uses current-year assets while RATIO_asset_turnover uses prior-year assets. Assets grew 34% in FY2025: so the divergence is expected, not an error.

**ROA check (V1):** 0.397 × 0.1036 = 4.11% = direct ROA. ✓

---

## Strategic Recommendations

### R1: Refinance short-term debt before it matures (H1: TIE = 0.124×)
VND 114T short-term debt is due soon. EBIT covers only 12.4% of interest. **Action:** Refinance at least VND 57T into 3–5 year bonds matched to Vinhomes handover cash flows.

### R2: Grow EBIT to reduce Other Income dependency (H1/H3: EBIT margin = 1.09%)
Net income disappears without VND 52T Other Income. FCF is already negative. **Action:** Set a public EBIT target of VND 20T within 3 years. Disclose Other Income components quarterly so investors can assess what is recurring.

### R3: Accelerate receivables collection (H2: ACP = 209 days)
VND 267T in receivables is growing faster than revenue. Cash/NI ratio of 6.22× shows deposits are being collected, but the ACP gap is widening. **Action:** Cap VinFast dealer credit at 90 days via bank floor-plan facility. Securitise Vinhomes instalment receivables to accelerate cash conversion.

### R4: Add segment EVA hurdles before approving capex (H3: FCF = -VND 7.3T)
Capex of VND 76.2T exceeded CFO by 10.6%: producing negative FCF funded entirely by new debt. Near-zero consolidated EVA (+4,756M) suggests capital is barely earning its cost. **Action:** Require segment-level EVA approval for any capex above VND 5T. VinFast's segment WACC is likely above the 12% consolidated rate.

### R5: Build a liquidity buffer (H1: Quick Ratio = 0.597×)
Liquid assets cover only 60% of current liabilities. With negative FCF and sub-1× TIE, there is no margin for error. **Action:** Target VND 50T minimum liquidity reserve (cash + committed undrawn facilities) through non-core asset sales of VND 20–30T.

---

## 6. LLM Evaluation

### What the LLM got right
- All 25+ ratio values match spec exactly (verified in table)
- Du Pont step-by-step correct; time-mismatch disclosed; ROA check passed
- TIE = 0.124× correctly flagged as top risk
- Quick Ratio used current-year receivables: HIL fix worked
- R1–R5 each cite specific ratio values

### Where the LLM was wrong or incomplete

| Issue | Type | Fix applied |
|-------|------|-------------|
| EBIT margin (1.09%) not reported | Spec gap | Added to §3 and H3 |
| Inventory Turnover = 2.169× overstated | Spec gap (start-of-year during 77% growth) | Corrected to 1.568× in §3 |
| FCF not calculated | LLM omission | Computed and added in H3 |
| Other Income not linked to VinFast domino mechanism | LLM omission | Connected in H2 |
| ROC = 12.00% stated as exact: EVA not contextualised as near-zero | Minor | Clarified in H1/§3 |

**No hallucinations.** All errors trace to spec gaps or hypothesis framing not in the spec: not fabrication.

---

## 7. Executive Justification

Vingroup's FY2025 numbers confirm all three hypotheses: and together they paint a coherent picture of a conglomerate running a high-risk funding model.

VinFast needed capital it could not generate internally. Vingroup raised it through debt (+69% LT debt YoY) and through Vinhomes pre-sales (Other Current Liabilities +VND 50T, CFO 6× net income). Capex still exceeded CFO by 10%, so CFF of VND 102T: new bonds and equity: filled the gap. The result: 86% debt-to-assets, TIE of 0.124×, quick ratio of 0.597×.

This is not a company in crisis. It is a company that has deliberately leveraged itself to fund a generational bet on Vietnam's EV market. The market agrees with the bet: 8.63× book says so. The ratios say the bet has almost no margin for error.

My call: **Hold with downside watch.** The upside: VinFast reaches break-even, Vinhomes delivers its pipeline, EBIT margin reaches 5%+: is real but already priced in at 8.63× book. The downside: Other Income shrinks, credit markets tighten, FCF stays negative: is a solvency scenario. The refinancing of VND 114T short-term debt and the growth of EBIT from 1.09% to something sustainable are not optional improvements. They are what keeps the funding model from unravelling.

---

## 8. Data Sources & Limitations

- Vingroup Annual Report 2025 (VAS, audited): https://vingroup.net/en/investor-relations
- HOSE: https://www.hsx.vn | VinFast 20-F: https://investors.vinfastauto.com
- SBV rate: 25,450 VND/USD, 31 Dec 2025 | Beta: 1.56 (Yahoo Finance, 5Y monthly)
- Stage 3 workbook: `models/builds/2026-05-22-tran-vingroup-financials.xlsx`

**Limitations:** (1) No VAS segment disclosure: all ratios consolidated; (2) Other Income not disaggregated: VinFast link is inferential; (3) Other Current Liabilities used as deposit proxy: VAS does not separate unearned revenue explicitly; (4) Inventory Turnover corrected from spec value (2.169× → 1.568×); (5) Benchmark figures are directional estimates only.
