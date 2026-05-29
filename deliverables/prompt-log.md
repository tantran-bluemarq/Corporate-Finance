# Prompt Log

## Stage 2 — Company Selection Memo

**Date:** 2025-05-21
**Tool:** Claude (claude.ai)

**Prompt used:**

I'm drafting a Stage 2 company selection memo for my finance course. The memo template is at:
https://raw.githubusercontent.com/adamwstauffer/shidler/main/docs/templates/memo-template.md

Please read the template, then draft a memo for the company Vingroup (VIC, HOSE) that fills in every section. Use the YAML frontmatter exactly as shown. Length: 400–600 words. Audience: a managing director — concise, evidence-tight.

Before you draft, ask me three to five clarifying questions about the company.

**Context provided to AI:**
- Company: Vingroup JSC (VIC, HOSE)
- Analytical focus: profitability, debt structure, revenue growth, financial risk
- Hypotheses: high D/E ratio due to VinFast expansion; potential domino effect if VinFast fails
- Data sources: HOSE filings, Vingroup IR, Vietstock, Bloomberg, annual reports
- Time period: 2024–2025
- Also uploaded: Vingroup Annual Report 2025 (PDF)

**AI output:** Draft memo saved at docs/decisions/2026-05-21-Tran-Vingroup-selection.md

## Stage 3 – Model Population & Validation

**Date:** 2026-05-23
**Tool:** Claude (claude.ai)

**Prompt used:**

I'm populating the Stage 3 financial model for my finance course. The Stage 3 requirements are at:
https://raw.githubusercontent.com/adamwstauffer/shidler/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage3-model-population-validation.md

Please read the requirements, then help me populate and validate the Excel ratios template (from Stage 1) for Vingroup (VIC, HOSE) across all three financial statements.

The file to populate is: models/builds/YYYY-MM-DD-tran-vingroup-financials.xlsx

Before you begin, ask me any clarifying questions about the data I've already entered or sourced.

**Context provided to AI:**
- Company: Vingroup JSC (VIC, HOSE)
- Template: Stage 1 performance-ratios-template.xlsx (tabs: Balance Sheet, Income Statement, Cash Flow, Ratios, Notes)
- Data sources: Vingroup Annual Report 2025 (audited), HOSE filings, Vietstock, Bloomberg
- Reporting standard: VAS, unit = VND billions (tỷ đồng)
- Time period: FY2024 (prior) and FY2025 (current)
- Ratios tab assumptions: share price, shares outstanding, WACC (~12%), tax rate (20%)
- Also uploaded: completed Excel file for validation

**AI output:** Validated Excel model saved at models/builds/2026-05-22-tran-vingroup-financials.xlsx

## Stage 4 — Technical Specification (Round 1 Draft)

**Date:** 2026-05-22
**Tool:** Claude (claude.ai)

**Prompt used:**
I'm drafting a Stage 4 technical specification for my finance course.
The Stage 4 requirements are at:
https://raw.githubusercontent.com/adamwstauffer/shidler/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage4-technical-specification.md

The spec template is at:
https://raw.githubusercontent.com/adamwstauffer/shidler/main/docs/templates/spec-template.md

Please read both URLs, then using the spec template structure, draft
a full technical specification for Vingroup Joint Stock Company (VIC,
HOSE) FY2025 ratio analysis. Populate every section (Part A items
1–7, Part B items 8–11), use named-range notation throughout, and
include real numbers from my uploaded Stage 3 workbook.

**Context provided to AI:**
- Company: Vingroup JSC (VIC, HOSE)
- Reporting standard: Vietnamese Accounting Standards (VAS)
- Fiscal year: FY2025 (current) / FY2024 (prior)
- Currency: VND millions
- Uploaded: 2026-05-22-tran-vingroup-financials.xlsx (Stage 3 workbook)

**AI output:** Draft spec saved at
`docs/specs/2026-05-22-tran-vingroup-spec.md` (v1.0)

---

## Stage 4 — HIL Review Note (Round 1 → Round 2)

**Date:** 2026-05-22

**Gap 1 — NOPAT typo in §4 Derived Inputs:**
After reviewing v1, I verified the NOPAT formula manually:
`INC_net + (1 − tax_rate) × INC_interest_expense
= 11,064,814 + 0.80 × 29,159,736 = 34,392,603`.
The spec stated 34,392,803 — a 200-unit typo. Because NOPAT is the
anchor value for ROA, ROC, EVA, Operating Profit Margin, and Du Pont
ROA, any error here propagates to every downstream ratio. I corrected
the value in v2 and added step-by-step verification arithmetic as a
footnote in §4.

**Gap 2 — TIE = 0.124× not stated in §5 Leverage table:**
The v1 spec described TIE generically as "EBIT coverage of interest;
<1.5× is distress zone" but never stated the actual computed value.
Calculating it — `INC_ebit / INC_interest_expense = 3,628,893 /
29,159,736 = 0.124×` — revealed this is the most critical ratio in
the model: EBIT covers only 12.4% of interest expense. A Stage 5 LLM
reading v1 would see a generic benchmark with no signal that Vingroup
is already deep inside distress territory. I revised §5 to state
TIE = 0.124× explicitly with a critical warning, added validation
rule V6 requiring Stage 5 to explain how `INC_other_income`
(VND 51,968,218M) bridges the gap, and made debt servicing the first
mandatory recommendation in §9.

**Gap 3 — `BAL_receivables_curr` missing as named range in §3:**
The Quick Ratio formula in §5 references `BAL_receivables_curr`
directly, but v1's §3 Data Inputs table only listed
`BAL_receivables_prior` with an explicit named range. The current-year
value (267,209,963) had no standalone named-range row. A Stage 5 LLM
scanning §3 would not find `BAL_receivables_curr` and could fail to
resolve the Quick Ratio formula. I added a dedicated row in §3 with a
note flagging its direct use in the Quick Ratio.

**Gap 4 — Benchmarks used single-sector real estate for a
diversified conglomerate:**
The v1 spec applied "Vietnam real estate developer" benchmarks to
Vingroup (asset turnover 0.15–0.25×, collection period 60–120 days).
Vingroup's FY2025 revenue reflects major contributions from VinFast
(EV/auto), real estate, hospitality, and healthcare. Single-sector
benchmarks would misrepresent Vingroup's efficiency ratios. I replaced
§7 benchmarks with conglomerate-appropriate peers: Masan Group
(Vietnam), CapitaLand (Singapore), and SM Group (Philippines).

**Changes made in v2:**
- §4: NOPAT corrected 34,392,803 → 34,392,603; arithmetic footnote added
- §5: Added "Computed Value" column to all 25+ ratio rows; TIE
  expanded with 0.124× value and critical flag
- §3: Added `BAL_receivables_curr = 267,209,963` as standalone row
- §6: Added V6 validation rule for TIE
- §7: Benchmarks replaced with conglomerate peers
- §9: Five mandatory recommendations (R1–R5) each cite a specific
  ratio value, replacing generic framing in v1

**AI output:** Revised spec saved at
`docs/specs/2026-05-22-tran-vingroup-spec.md` (v2.0)

## Stage 5 — LLM Analysis Execution & Evaluation

**Date:** 2026-05-30
**Tool:** Claude (claude.ai)

**Prompt used:**
I am executing Stage 5 of my BUS-629 project. The Stage 5
requirements are at:
https://github.com/adamwstauffer/shidler/blob/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage5-llm-analysis-evaluation.md

Please read my Stage 4 spec at docs/specs/2026-05-22-tran-vingroup-spec.md
and execute it as the sole input to produce the full ratio analysis
for Vingroup FY2025. No additional context beyond the spec.

**Context provided to AI:**
- Spec v2.0: docs/specs/2026-05-22-tran-vingroup-spec.md (sole input)
- Stage 3 workbook: models/builds/2026-05-22-tran-vingroup-financials.xlsx
  (used for manual verification only, not fed to LLM)

**AI output:** Raw analysis saved at
`deliverables/2026-05-22-tran-vingroup-llm-raw.md`

---

## Stage 5 — Manual Verification & Final Analysis

**Date:** 2026-05-30
**Tool:** Claude (claude.ai) + manual arithmetic

**Work done:**
1. Verified 6 ratios by hand from Stage 3 financials vs. LLM output.
   Found one interpretation divergence: Inventory Turnover 2.169x
   (spec, start-of-year) vs. 1.568x (corrected, average method)
   because inventory grew 77% YoY. All other values matched.
2. Identified two LLM omissions: EBIT margin (1.09%) not reported;
   Free Cash Flow (-7,302,290 VND millions) not computed.
3. Added H1/H2/H3 hypothesis framing, FCF calculation, and EBIT
   margin to final analysis. Corrected Inventory Turnover in ratio
   table.

**Outputs:**
- `analysis/validation/2026-05-22-tran-vingroup-stage5-verification.md`
- `deliverables/2026-05-22-tran-vingroup-final-analysis.md`
- `deliverables/2026-05-22-tran-vingroup-spec-retrospective.md`
