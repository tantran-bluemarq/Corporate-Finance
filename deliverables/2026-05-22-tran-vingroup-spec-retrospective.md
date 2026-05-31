---
template: spec-retrospective
date: 2026-05-30
author: Tan Tran
company: Vingroup Joint Stock Company (VIC, HOSE)
spec_file: docs/specs/2026-05-22-tran-vingroup-spec.md
stage5_output: deliverables/2026-05-22-tran-vingroup-llm-raw.md
---

# Stage 4 Spec: Retrospective

**Author:** Tan Tran | **Date:** 2026-05-30
**Company:** Vingroup Joint Stock Company (VIC, HOSE)
**Spec:** `docs/specs/2026-05-22-tran-vingroup-spec.md`
**LLM output:** `deliverables/2026-05-22-tran-vingroup-llm-raw.md`

---

## 1. Section-by-Section Verdict

| Spec section | Verdict | Symptom in Stage 5 output |
|-------------|---------|--------------------------|
| A.1 Scope and Objective | Clear | Company context, VAS note, audience all reproduced correctly |
| A.2 Model Architecture | Clear | Tab layout and color coding referenced correctly |
| A.3 Data Inputs | Clear | All 30+ named ranges reproduced without error |
| A.4 Named Range Conventions | Clear | BAL, INC, CASH, RATIO prefixes used consistently |
| A.5 Derived Inputs | Clear | NOPAT, averages, daily rates all correct |
| A.6 Ratio Definitions | Vague | EBIT margin (1.09%) absent from raw output; spec defined Profit Margin as INC_net/INC_sales only, no INC_ebit/INC_sales row |
| A.6 Inventory Turnover convention | Vague | LLM reported 2.169x per spec; average method gives 1.568x (38% lower); spec gave no warning about 77% inventory growth making start-of-year misleading |
| A.7 Validation Rules | Clear | All six checks passed; V2 time-mismatch and V6 TIE flag disclosed correctly |
| B.8 Analysis Requirements | Vague | Spec listed benchmark peers but no specific peer values; LLM cited directional ranges only |
| B.9 Du Pont Decomposition | Clear | Four-factor decomposition, step-by-step multiplication, and time-mismatch all correct |
| B.10 Strategic Recommendations | Clear | Five recommendations, each citing a specific ratio with an actionable step |
| B.11 Output Format | Clear | All seven sections present, length and tone on target |

---

## 2. Top Three Gaps with Evidence

### Gap 1: EBIT margin missing from section 5

**Where it surfaced:** LLM reported Profit Margin (3.33%) and NOPAT margin (10.36%) but never EBIT margin. Manual calc: 3,628,893 / 331,837,561 = 1.09% — the key number for H3 — absent from the entire raw output.

**Spec cause:** Section 5 had no ratio row using INC_ebit as a margin numerator. The LLM followed the spec and did not add an unspecified ratio.

**Fix:** Add to Profitability table in section 5:
> EBIT Margin | `INC_ebit / INC_sales` | % | 1.09% | Core operating profit before non-operating items; required because Other Income (VND 51,968M) is 14.3x EBIT

---

### Gap 2: Inventory Turnover convention not flagged for rapid growth

**Where it surfaced:** LLM stated 2.169x per spec formula. Verification table found average method yields 1.568x (38% lower). Inventory grew 77% YoY so the start-of-year figure materially overstates efficiency. LLM did not flag this because the spec did not mention it.

**Spec cause:** Section 5 defined the formula without any note about when large YoY changes make it misleading.

**Fix:** Add below Inventory Turnover in section 5:
> Note: If inventory grew more than 20% YoY, also compute average-inventory result and present both. FY2025: 247,489,507 / 157,835,230 = 1.568x vs. spec value 2.169x.

---

### Gap 3: Cash flow ratios not required for H3

**Where it surfaced:** LLM discussed capex but never computed FCF (= -7,302,290 VND millions) or CFO/Net Income (6.22x), both essential for testing H3. Both had to be added manually in the final analysis.

**Spec cause:** Section 8 covered six ratio categories but no cash flow section. The Stage 2 hypotheses were not referenced in the spec so the LLM had no instruction to test H3 with cash flow data.

**Fix:** Add to section 8:
> Cash Flow Analysis: Compute (a) FCF = CASH_operating + CASH_capex = -7,302,290; (b) CFO/Net Income = 6.22x; (c) CFF as share of FCF shortfall. Assess whether negative FCF is structural or temporary.

---

## Three Revisions

1. Add EBIT Margin row to section 5 Profitability with a note distinguishing it from NOPAT Margin. Addresses Gap 1.
2. Add an averaging warning to Inventory Turnover in section 5 requiring both results when YoY growth exceeds 20%. Addresses Gap 2.
3. Add Cash Flow Analysis to section 8 requiring FCF, CFO/NI, and CFF coverage tied to the three Stage 2 hypotheses. Addresses Gap 3.

---

## 3. Effectiveness Rating

**My rating: 4**

The spec did its core job well: all 25+ ratios were correct, Du Pont was exact, recommendations cited specific values, no hallucinations. It falls short of 5 for two concrete reasons: EBIT margin (1.09%) was missing entirely from the raw output because section 5 did not define it, and FCF was never computed because section 8 did not require cash flow analysis. Both required material additions in the final analysis. A rating of 5 means trusting the output without re-checking; these two omissions prevented that.

---

## 4. Forward Link

Next time I write a spec, I will map each section to at least one hypothesis before writing any ratio definitions, so that every hypothesis has a corresponding named-range formula and every formula has a clear analytical purpose.

---

## 5. Retrospective Process Feedback

The section-by-section verdict table was the most useful part. It forced a specific symptom for each verdict, which prevented vague self-assessment. Without it I would have rated the spec a 4 and not identified the EBIT margin gap specifically.

One structural change: add a column to the section 1 table labelled "Hypothesis tested." If a section maps to no hypothesis, that flags either redundancy or an untested hypothesis. In my case, section 5 had no mapping to H3 (cash flow), which is exactly why Gap 3 reached Stage 5 without being caught. Surfacing that at spec-writing time would have saved the manual correction later.
