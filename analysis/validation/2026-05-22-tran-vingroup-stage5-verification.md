# Stage 5 — Manual Ratio Verification Table

**File:** `analysis/validation/2026-05-22-tran-vingroup-stage5-verification.md`
**Author:** Tan Tran | **Date:** 2026-05-30
**Company:** Vingroup Joint Stock Company (VIC, HOSE) — FY2025
**LLM output compared:** `deliverables/2026-05-22-tran-vingroup-llm-raw.md`

---

| Ratio | Formula (named-range notation) | Manual value (show arithmetic) | LLM's value | Match? | One-line note |
|-------|-------------------------------|-------------------------------|-------------|--------|---------------|
| EVA | `currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)` | NOPAT = 11,064,814 + 0.80 × 29,159,736 = 34,392,603; startYear_cap = 132,730,912 + 153,834,481 = 286,565,393; EVA = 34,392,603 − (0.12 × 286,565,393) = **+4,756 VND millions** | +4,756 VND millions | ✓ | LLM used correct prior-year capital base; rounding (4,755.64 → 4,756) is acceptable |
| ROE (average equity) | `INC_net / AVERAGE(startYear_equity, currentYear_equity)` | avg_equity = (153,834,481 + 151,488,935) / 2 = 152,661,708; ROE = 11,064,814 / 152,661,708 = **7.25%** | 7.25% | ✓ | LLM correctly averaged both year-end equity figures — a common shortcut error would be to use end-of-period only |
| Times Interest Earned (TIE) | `INC_ebit / INC_interest_expense` | 3,628,893 / 29,159,736 = **0.124×** | 0.124× | ✓ | LLM correctly flagged sub-1× as critical; confirmed EBIT covers only 12.4% of interest expense |
| **Inventory Turnover** | `INC_cost_goods_sold / startYear_inventory` | 247,489,507 / 114,090,183 = **2.169×** | 2.169× | ⚠ **Interpretation divergence** | LLM value is arithmetically correct per spec (start-of-year inventory). However, standard finance textbooks use **average inventory**: (114,090,183 + 201,580,276) / 2 = 157,835,230 → Inventory Turnover = **1.568×** — a 38% lower result. Because inventory grew 77% YoY, using start-of-year inventory overstates turnover efficiency. The spec's named-range convention is internally consistent but produces a more favourable result than the average-inventory method. Final analysis should disclose this limitation. |
| Quick Ratio | `(BAL_cash_marketable_securities_curr + BAL_receivables_curr) / BAL_liabilities_current_curr` | (83,380,686 + 267,209,963) / 587,454,564 = 350,590,649 / 587,454,564 = **0.597×** | 0.597× | ✓ | LLM correctly used current-year receivables (267,209,963); using prior-year would have given 0.466× — a 22% understatement |
| ROE via Du Pont | `RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden` | 7.384 × 0.397 × 0.1036 × 0.322 = **9.77%**; direct ROE (start) = 11,064,814 / 153,834,481 = 7.19%; divergence = 2.57% | 9.77% | ✓ | LLM correctly disclosed the 2.57% time-mismatch divergence from direct ROE per V2 validation rule |

---

## Key Finding — Inventory Turnover Interpretation Divergence

The one substantive issue identified in this verification is **not** an arithmetic error by the LLM but a **methodological limitation inherited from the spec**.

The spec instructs: `INC_cost_goods_sold / startYear_inventory` — consistent with the model's named-range convention of using prior-year balances as denominators throughout (also used in Asset Turnover, ROA, ROC, ACP).

**The problem:** Vingroup's inventory grew **77% YoY** (from VND 114,090,183M to VND 201,580,276M), driven by VinFast vehicle stockpiling and Vinhomes land bank accumulation. Using only the opening balance as the denominator produces a turnover of 2.169× that reflects the smaller prior-year inventory base — overstating efficiency relative to the full-year inventory position.

| Method | Inventory Base | Turnover Result |
|--------|---------------|-----------------|
| Spec (start-of-year) | 114,090,183 | **2.169×** |
| Textbook (average) | 157,835,230 | **1.568×** |
| Difference | — | **0.601× (28% gap)** |

**Resolution for final analysis:** The Inventory Turnover of 2.169× should be reported alongside a disclosure that the average-inventory method yields 1.568×, and that the higher figure is partly an artefact of the model's start-of-year convention applied during a year of rapid inventory growth. This is a spec gap — the retrospective will flag it.
