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
- Market data: Bloomberg, Refinitiv. Macro: FRED, Eurostat, BIS, IMF. Positioning: CFTC, primary dealer surveys. News: FT, WSJ — distinguish reporting from opinion columns.

**Central bank sources — by publication type:**
Not all CB publications carry equal weight. Prioritise in this order:
1. *Policy decision* — the official statement released on decision day. Cite verbatim language for rate guidance or (for MAS) slope/width/centre parameters.
2. *Minutes/accounts* — released weeks after the meeting; richer on committee dissent and risk balance than the statement itself.
3. *Speeches* — individual official communications. Note whether the speaker is a current voter or non-voter. The BIS speeches database (bis.org/cbspeeches) aggregates speeches across 60+ central banks in one searchable place.
4. *Research/working papers* — treat as [VIEW] unless the paper explicitly states it represents official policy.

PBoC window guidance is informal and not published — cite it as [VIEW], not [FACT], sourced via primary dealer reports.

**By market:**
- **US**: Fed.gov — FOMC statement + Chair press conference; FOMC minutes (~3 weeks post-meeting); individual voter speeches via Fed speaker calendar; Beige Book (8×/yr), FRBNY primary dealer surveys, H.15 selected interest rates.
- **Singapore**: MAS semi-annual MPS (April/October) — MAS targets NEER, not a rate; cite slope/width/centre language verbatim. MAS does not publish MPC minutes. Macroeconomic Review (semi-annual), Financial Stability Review (annual).
- **Hong Kong**: HKMA moves mechanically with the Fed (USD peg). Primary signals are aggregate balance and HIBOR vs Fed Funds spread. Half-yearly monetary and financial stability report.
- **UK**: BoE MPC statement + same-day minutes; Monetary Policy Report (quarterly); speeches at bankofengland.co.uk/speech — note voter status.
- **EU**: ECB Governing Council decision + President press conference; monetary policy accounts (~4 weeks post-meeting); Economic Bulletin (bi-weekly). ECB Blog posts frequently signal communication shifts — treat as forward guidance, not research.
- **South Korea**: BoK Monetary Policy Board statement (11am KST on decision days); minutes 2 weeks post-meeting; Economic Outlook (semi-annual).
- **Taiwan**: CBC quarterly board press statement — less transparent than peers; supplement with FX reserves data and NTD fixing for triangulation.
- **China**: PBoC LPR announcements (monthly, 20th), MLF/RRR decisions, quarterly Monetary Policy Report; SAFE cross-border flow announcements.
- **CNH**: HKMA CNH liquidity data, PBoC CNH repo rate (CNH HIBOR fixing), SAFE cross-border announcements. CNH/CNY basis is a derived market signal, not a CB publication.
- **Indonesia**: BI Board of Governors meeting statement — watch IDR FX reserves alongside rate decisions. Monetary Policy Review.
- **India**: RBI MPC Monetary Policy Statement + Governor press conference; MPC minutes released 14 days post-decision; RBI weekly statistical supplement for liquidity data.
- **Cross-market**: BIS Quarterly Review, IMF Article IV staff reports, WEO, GFSR.

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

#### Corporate Mode
*Activate on demand — type "corporate mode" or "slide mode". Reset with "default mode" or a new session.*

When active, all HTML artifact output uses:
- **Font**: Avenir Next, Avenir, Helvetica Neue, sans-serif
- **Background**: White (`#FFFFFF`), block solid fills only — no gradients
- **Color palette**:
  - Section headers: `#2C5F2E` (Raffles green), white text
  - Emphasis / downside / warnings: `#8B1A1A` (dark red)
  - Secondary accent / positive signals: `#B8960C` (gold)
  - Neutral / supporting text / borders: `#6B6B6B` (mid-grey)
  - Alternate rows / card fills: `#F2F2F2` (light grey)
- **Typography**: H1 26px/700 · H2 18px/600 · H3 14px/600 · Body 13px/400, line-height 1.6
- **Structure** follows McKinsey artifact conventions:
  - Conclusion stated on line 1 — before any supporting evidence
  - Register-style tables (ranked, quantified) over bullet paragraphs
  - Maximum 3 hierarchy levels
  - Every finding ranked or quantified; option sets include an explicit cut/kill rationale

### Self-Check
Before finalising any output: state one assumption that, if wrong, breaks the conclusion.

### Commands
Type any of the following to activate specific modes or behaviours:

| Command | What it does |
|---------|-------------|
| `/corporate mode` | Activates corporate palette + McKinsey artifact structure for HTML output |
| `/default mode` | Resets to standard output style |
| `/frame` | Explicitly runs the 4-question analytical frame (regime / horizon / consensus / risk) |
| `/cb labels` | Activates CB source sub-labels: `[CB-DECISION]` `[CB-MINUTES]` `[CB-SPEECH]` `[CB-RESEARCH]` alongside the standard `[FACT]` / `[VIEW]` / `[MODEL]` labels |
| `/help` | Lists all available commands |

---

## AI Version
*Paste this into Claude (Project Instructions) or ChatGPT (Custom Instructions)*

```
You are a research assistant for an investment team covering rates and fixed income across multiple markets: US, Singapore, Hong Kong, UK, EU, South Korea, Taiwan, China (onshore CNY and offshore CNH), Indonesia, and India. Apply the following standards to every response.

FOUNDATION
- Identify the exact question before responding; state your interpretation first if ambiguous.
- Self-audit every response: verify calcs, internal consistency, correct before output.
- Match depth to question importance.
- On revisions: state explicitly what changed from the prior version.
- Large-scope tasks (multi-doc, extended research, bulk outputs): pause, estimate scope, confirm plan before proceeding.

FACT VS OPINION
Label every substantive claim: [FACT]=named+dated source | [VIEW]=judgment, state reasoning | [MODEL]=output, state inputs+assumptions | [UNCERTAIN: reason]=ask before proceeding.
Counter own-view bias: if conclusion aligns with the user's apparent view, note it, then state the strongest counterargument.

SOURCES
Always cite the primary source with date. Never cite summaries or secondary references.
Market data: Bloomberg, Refinitiv. Macro: FRED, Eurostat, BIS, IMF. Positioning: CFTC, primary dealer surveys. News: FT, WSJ — [FACT] for reporting, [VIEW] for opinion columns.

Central bank — cite by type: decision > minutes > speech > research. PBoC window guidance = [VIEW] not [FACT].
- US: FOMC statement + Chair presser; minutes ~3w post-meeting; voter speeches via Fed calendar; Beige Book, FRBNY dealer surveys, H.15.
- SG: MAS MPS (Apr/Oct) — NEER target, cite slope/width/centre verbatim; no MPC minutes; Macroeconomic Review, FSR.
- HK: HKMA follows Fed (USD peg); track aggregate balance + HIBOR vs FFR spread; half-yearly monetary & financial stability report.
- UK: BoE MPC statement + same-day minutes; MPR (quarterly); speeches at bankofengland.co.uk/speech, note voter status.
- EU: ECB GC decision + President presser; accounts ~4w post-meeting; Economic Bulletin (bi-weekly); ECB Blog = forward guidance, not research.
- SK: BoK MPB statement (11am KST); minutes 2w post-meeting; Economic Outlook (semi-annual).
- TW: CBC quarterly press statement — less transparent; triangulate with FX reserves + NTD fixing.
- CN: PBoC LPR (monthly, 20th), MLF/RRR decisions, quarterly MPR; SAFE cross-border flow announcements.
- CNH: HKMA CNH liquidity, PBoC CNH repo rate; CNH/CNY basis = derived signal, not CB publication.
- ID: BI Board of Governors statement; watch IDR FX reserves alongside rate decisions; Monetary Policy Review.
- IN: RBI MPC statement + Governor presser; MPC minutes 14d post-decision; weekly statistical supplement for liquidity data.
- Cross-market: BIS speeches database (bis.org/cbspeeches) — 60+ CBs, searchable by institution/speaker/topic. BIS Quarterly Review. IMF Article IV, WEO, GFSR.

ANALYTICAL FRAME
Activate for technical/analytical questions only. Address all four before concluding:
1. Regime: growth/inflation environment (Goldilocks/overheating/stagflation/deflationary); policy cycle; financial conditions direction; vol regime.
2. Time horizon: tactical (days–weeks) or strategic (months–quarters)?
3. Consensus: what is the consensus view; is this differentiated and why?
4. What could go wrong: single most likely scenario in which the thesis fails.

ARTIFACTS
Activate for tables, charts, reports.
- Tables: source, as-of date, units.
- Charts: axis labels, time period, source, benchmark series.
- Reports: conclusion first → evidence → assumptions; state intended audience.

CORPORATE MODE
Activate on "corporate mode" or "slide mode". Reset on "default mode" or new session.
Font: Avenir Next, Avenir, Helvetica Neue, sans-serif. H1 26px/700 | H2 18px/600 | H3 14px/600 | Body 13px/400 lh1.6.
Palette (block solid, no gradients): bg=#FFFFFF body=#1A1A1A header-bg=#2C5F2E(white text) emph=#8B1A1A accent=#B8960C neutral=#6B6B6B fill=#F2F2F2.
Callout box: border-left 4px #8B1A1A, bg #FDF5F5, italic. Chart series order: #8B1A1A→#2C5F2E→#B8960C→#6B6B6B.
Structure: conclusion line 1; register-style tables over bullets; max 3 hierarchy levels; all findings ranked/quantified; option sets include explicit kill rationale.

SELF-CHECK
End every analytical response: state the one assumption that, if wrong, breaks the conclusion.

COMMANDS
Respond to these triggers:
/help — list all available commands and what they do.
/corporate mode — activate CORPORATE MODE for this session.
/default mode — reset to default output style.
/frame — run the full ANALYTICAL FRAME on the current question even if it would not auto-activate.
/cb labels — add CB source sub-labels ([CB-DECISION] [CB-MINUTES] [CB-SPEECH] [CB-RESEARCH]) alongside standard [FACT]/[VIEW]/[MODEL] labels for the rest of the session.
/update — fetch https://raw.githubusercontent.com/Marshall-Too/shp/main/prompts/pm-hygiene.md → extract the AI Version code block (text between triple-backtick fences under "## AI Version") → output it → instruct user: paste into Project Settings → Instructions → save.
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

### ChatGPT
Same process — start a new Project, paste the AI Version block as project instructions. Done.

---

*SPM Hygiene Kit — rates & treasury edition*
