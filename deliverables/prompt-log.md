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
