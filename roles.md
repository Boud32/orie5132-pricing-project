# Project Roles — Choice Modeling, Assortment Optimization and Pricing
**ORIE 5132 | Due: Monday April 27th, 11:59pm ET**

---

## James — Problems 1, 2, 3

**Core MNL: Estimation, Assortment Optimization, Pricing**

### Problem 1: MNL Model
- Implement MLE to estimate the MNL model on `data.csv` (153k rows)
- Features: star rating, review score, hotel brand, location score, accessibility score, historical price, displayed price, promotion flag
- Report and interpret coefficients β₀...β₈
- **This output unblocks Fran and Akhil — share results early**

### Problem 2: Assortment Optimization under MNL
- Using P1's estimated model, find the optimal subset of hotels to display for each of `data1.csv`, `data2.csv`, `data3.csv`, `data4.csv`
- Report expected revenue under each optimal assortment

### Problem 3: Pricing under MNL
- Using P1's model, find optimal prices for all hotels in each of `data1–4.csv`
- Maximize expected revenue assuming all hotels are displayed

**Note:** Build P1 as a reusable function (returns fitted model/coefficients) — Akhil needs to re-run it on a different dataset for P7.

---

## Fran — Problems 4, 5

**Mixture MNL: Segmentation, Estimation, Integer Programming**

### Problem 4: Mixture of MNL
- Segment `data.csv` into early customers (booking window ≥ 7 days) and late customers (booking window < 7 days)
- Estimate θ₁ and θ₂ (proportion of each type) from data
- Fit separate MNL models for each customer type using MLE
- Compare and comment on the sensitivity parameters across the two types

### Problem 5: Early vs. Late Reservations
- Using P4's mixture model, solve for each of `data1–4.csv`:
  - **S**: optimal assortment when customer type is unknown (integer program)
  - **S₁**: optimal assortment for a known type-1 (early) customer
  - **S₂**: optimal assortment for a known type-2 (late) customer
  - Compare expected revenue of S vs. S₁ under type-1 MNL
  - Compare expected revenue of S vs. S₂ under type-2 MNL

**Depends on:** James's P1 results (β estimates for baseline comparison)

---

## Akhil — Problems 6, 7

**Extended Models: Custom Segmentation + AI Agents**

### Problem 6: Mixture of MNL with Other Ways of Defining Customer Types
- Propose a different way to segment customers (e.g., Saturday vs. weekday bookings, solo vs. family travel, etc.) — justify your choice
- Estimate the new mixture MNL model on `data.csv`
- Repeat the full Problem 5 analysis (S, S₁, S₂, revenue comparisons) for `data1–4.csv` under this new model

### Problem 7: AI Agents as Customers
- Take `data.csv`, remove the booking column, and prompt an AI agent (state which one and version) to make booking decisions for each search query — include the no-purchase option
- Use AI-generated choices as the new booking column
- Re-estimate the MNL model from P1 on this AI dataset; compare parameters to James's human-data results
- Use the AI agent as a predictive model: give it a subset of real data as context, ask it to predict held-out bookings; compare out-of-sample accuracy to James's MNL
- Discuss what this reveals about AI agents' ability to simulate human choice behavior

**Depends on:** James's P1 code (re-run on AI-generated data)

**Prompting tips from James:**
- Use a consistent prompt structure for every query — same format, same attribute ordering
- Include all hotel attributes + full customer context in each prompt
- Always include the no-purchase option explicitly
- Hold out test queries before prompting so the AI never sees them

---

## Coordination Notes

| Dependency | Action |
|---|---|
| Fran and Akhil need P1 β estimates | James shares results as soon as P1 is done |
| Akhil needs P1 code to be reusable | James exposes a function that accepts a booking column as input |
| Akhil can reference Fran's P5 for P6 structure | Fran shares P5 writeup/code when ready |
