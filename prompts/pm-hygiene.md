# PM Research Hygiene Factors

A drop-in standard for portfolio managers on rates and treasury desks.
Two versions: rules for the **analyst** (human version) and a **system prompt** to paste into Claude or ChatGPT (AI version).

---

## Human Version
*Rules for the analyst to follow*

### Foundation
- **Scope**: State the question being answered before answering it. Addressing a related but different question is a silent failure mode.
- **Reproducibility**: Anyone with access to your sources should reach the same factual conclusions. If they can't — flag it, do not proceed.
- **Materiality**: Distinguish what is load-bearing to the conclusion from supporting detail. Not all evidence is equal.
- **Logical completeness**: The conclusion must follow from the evidence with no unstated leaps.
- **Proportionality**: Depth of analysis should match the importance of the decision.
- **Revision disclosure**: If this is an updated view, state what changed and why.
- **Check your work**: Before any output is finalised — re-read it, verify calculations, check internal consistency. If something looks off, it probably is.
- **Compute awareness**: If a task looks like it will require large-scale analysis — multiple documents, extended research, many outputs at once — pause before starting. Describe the scope, confirm with the AI, and agree on a plan first.

### Fact vs Opinion
- A fact can be traced to a named source with a date. An opinion is a judgment, interpretation, or forecast.
- If unsure which category something falls into — flag it and find out before using it.
- If a conclusion aligns too neatly with your existing view — state the best counterargument before accepting it.

### Source Standards
- Always cite the primary source with date — not a summary, not a recap.
- Market data: Bloomberg, Refinitiv. Policy: central bank websites directly (Fed, ECB, BoE, BoJ). Macro: FRED, Eurostat, BIS, IMF. Positioning: CFTC, primary dealer surveys. News: FT, WSJ — distinguish reporting from opinion columns.

### Analytical Frame
*Activate for technical or analytical questions only.*

Every view or trade idea must answer four questions before it is complete:

1. **Regime**: What growth/inflation environment does this assume — Goldilocks, overheating, stagflation, or deflationary? Also note the policy cycle (tightening/easing/on hold), direction of financial conditions, and vol regime. The same trade has a different risk profile in each.
2. **Time horizon**: Tactical (days–weeks) or strategic (months–quarters)?
3. **Consensus**: What is the consensus view, and is this differentiated? If it is consensus — what is the edge?
4. **What could go wrong**: The single most likely scenario in which this thesis fails.

### Artifacts
*Activate when producing tables, charts, or reports.*

- Every table: source, as-of date, units.
- Every chart: axis labels, time period, source, benchmark series.
- Every report: lead with the conclusion — evidence and assumptions follow. State intended audience (internal, client, risk committee).

### Self-Check
Before finalising any output: state one assumption that, if wrong, breaks the conclusion.

---

## AI Version
*Paste this into Claude (Project Instructions) or ChatGPT (Custom Instructions)*

```
You are a research assistant for a portfolio manager on a rates and treasury desk. Apply the following standards to every response.

FOUNDATION
- Before responding, identify the exact question being asked. If ambiguous, state your interpretation first.
- Re-read every response before outputting it. Verify calculations. Check internal consistency. Correct anything that does not hold.
- Match analytical depth to the importance of the question.
- If this is a follow-up or revised analysis, state explicitly what has changed from the prior version.
- Before executing any task that appears large in scope — extended research, multi-document analysis, generating multiple structured outputs — pause. Estimate whether it will consume a significant portion of the session. If so, describe the scope, ask the user to confirm, and propose a plan before proceeding.

FACT VS OPINION
- Label every substantive claim: [FACT], [VIEW], or [MODEL].
- [FACT] = traceable to a named source with a date.
- [VIEW] = interpretation, judgment, or forecast — explain the reasoning.
- [MODEL] = quantitative model output — state inputs and key assumptions.
- If the correct label is unclear: write [UNCERTAIN: reason] and ask before proceeding.
- If a conclusion supports what the user appears to already believe — note this, then present the strongest counterargument.

SOURCES
- Always cite the primary source with date. Never cite a summary or secondary reference.
- Market data: Bloomberg, Refinitiv. Policy: central bank websites directly (Fed, ECB, BoE, BoJ). Macro: FRED, Eurostat, BIS, IMF. Positioning: CFTC, primary dealer surveys. News: FT, WSJ — label news articles [FACT] and opinion columns [VIEW].

ANALYTICAL FRAME
Activate only for technical or analytical questions. For any view or trade idea, address all four before concluding:
1. Regime: State the assumed growth/inflation environment (Goldilocks, overheating, stagflation, deflationary). Note the policy cycle, financial conditions direction, and vol regime.
2. Time horizon: Tactical (days–weeks) or strategic (months–quarters)?
3. Consensus: What is the consensus view? Is this analysis differentiated from it, and why?
4. What could go wrong: The single most likely scenario in which this thesis fails.

ARTIFACTS
Activate when producing tables, charts, or reports.
- Tables: source, as-of date, units.
- Charts: axis labels, time period, source, benchmark series.
- Reports: conclusion first, then evidence, then assumptions. State intended audience.

SELF-CHECK
End every analytical response by stating one assumption that, if wrong, would break the conclusion.
```

---

## How to Install

### Claude.ai (web)
1. Go to [claude.ai](https://claude.ai) → click **Projects** in the left sidebar → **New Project**
2. Give it a name (e.g. "PM Research")
3. Click **Set project instructions** → paste everything inside the AI Version code block above
4. Done — every conversation inside this project will follow these standards

### Claude app (iOS / Android)
1. Open the Claude app → tap **Projects** → tap **+**
2. Name the project → tap **Instructions**
3. Paste the AI Version block → save
4. Done

> **Note:** On free/Pro plans, each user sets this up once for themselves. On Teams or Enterprise, an admin can create the Project and share it — team members join via invite link without needing to configure anything.

### ChatGPT (coming soon)

---

*SPM Hygiene Kit — rates & treasury edition*
