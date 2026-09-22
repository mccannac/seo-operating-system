# PHASE 6–7: Prioritization engine and human-in-the-loop design

## 6.1 Why volume/difficulty/rank alone fail

A score built only from search volume, keyword difficulty, and current rank optimizes for **traffic acquisition**, not business outcome. It cannot distinguish a high-volume, unwinnable, wrong-intent term (the archive's own "appraisal" at 500K searches/month) from a low-volume term that converts at ten times the rate. **RECOMMENDATION:** score business value, winnability, and go-to-market readiness as separate, explicit dimensions, and multiply rather than average them where a zero in one dimension should zero out the whole opportunity (a page the client legally cannot claim, for instance).

## 6.2 The V2 opportunity-scoring formula

This extends the seven-dimension model in Section 3.4 with the additional variables requested (revenue potential, existing authority, probability of success, competitive intensity, time to impact, customer importance, conversion potential, geographic relevance, content readiness, technical dependency, data confidence). Several of the newly-requested variables are absorbed into the existing dimensions rather than duplicated — the mapping is shown explicitly so the model stays implementable in one spreadsheet tab rather than sprawling into an unmanageable score count.

| Requested variable | Where it lives in V2 | Why merged here |
|---|---|---|
| Business value, Revenue potential, Customer importance, Conversion potential | **BV** (Business Value) | All four describe "how close to money," rated together from CRM/margin/funnel data |
| Search intent | Gating step (Section 6.3), not a score | Wrong intent should exclude a cluster, not merely lower its score |
| Strategic relevance | **STRAT** | Unchanged from Section 3.4 |
| Existing authority, Competitive intensity | **WIN** (Winnability) | Both describe "can we realistically win," from the same competitive evidence |
| Probability of success | **WIN** × **DCF** (Data Confidence Factor, new — see below) | Split so a confident "we can win" is not the same as an uncertain guess |
| Effort, Technical dependency, Content readiness | **EASE** | All describe implementation cost/friction |
| Time to impact | **TTI** (new modifier, below) | Kept separate because a great opportunity that takes 18 months competes with the business's actual planning horizon |
| Geographic relevance | Client-specific gate, not a universal score | Only meaningful for multi-location or expansion clients (see the simulated run in the final tab) |
| Data confidence | **DCF** (new modifier, below) | Prevents the model from treating a thin-data guess as equal to a well-evidenced score |

### The formula

```
RawScore = 20 × [ (0.30 × BV) + (0.20 × WIN) + (0.15 × DEM) + (0.10 × CLK)
                 + (0.10 × GAIN) + (0.10 × STRAT) + (0.05 × EASE) ]

TimeAdjustedScore = RawScore × TTI_multiplier

OpportunityScore = TimeAdjustedScore × DCF_multiplier
```

Where:

- **BV, WIN, DEM, CLK, GAIN, STRAT, EASE** are 1–5 human- or evidence-scored dimensions as defined in Section 3.4 (BV now folds in revenue potential, customer importance, and conversion potential; WIN folds in existing authority and competitive intensity; EASE folds in technical dependency and content readiness).
- **TTI_multiplier** (Time to Impact) reflects that a client planning quarterly cannot weight an 18-month payoff the same as a 60-day one:

| Estimated time to measurable impact | TTI_multiplier |
|---|---|
| 0–90 days | 1.00 |
| 91–180 days | 0.90 |
| 181–365 days | 0.75 |
| 365+ days | 0.60 |

- **DCF_multiplier** (Data Confidence Factor) penalizes scores built on thin or estimated data, so the ranked list doesn't quietly launder a guess into a "77":

| Data confidence | Basis | DCF_multiplier |
|---|---|---|
| High | First-party data (GSC, CRM, sales) for ≥3 of the 7 dimensions | 1.00 |
| Medium | First-party data for 1–2 dimensions; rest from vendor estimates | 0.85 |
| Low | All dimensions from vendor estimates or LLM inference with no first-party check | 0.65 |

**Spreadsheet implementation** (one row per keyword cluster or opportunity):

```
=20*((0.30*BV)+(0.20*WIN)+(0.15*DEM)+(0.10*CLK)+(0.10*GAIN)+(0.10*STRAT)+(0.05*EASE))*TTI_MULT*DCF_MULT
```

Every input cell (`BV`, `WIN`, `DEM`, `CLK`, `GAIN`, `STRAT`, `EASE`, `TTI_MULT`, `DCF_MULT`) is a plain number column; the formula column is the only computed cell. This is deliberately implementable in Google Sheets or Airtable with no scripting — a database implementation (Postgres) simply stores the same nine inputs and computes the same expression in a view.

## 6.3 Gating rules (applied before scoring, not after)

A cluster is **excluded from scoring entirely** (not merely scored low) if any of the following hold:

1. **Wrong or unresolved intent** — SERP evidence contradicts the assumed intent (the "appraisal" case) and has not been disambiguated into a sub-cluster.
2. **Compliance red flag** — the claim required is one the client cannot substantiate, or the topic requires regulatory review not yet available.
3. **No geographic fit** — for location-bound clients, the query targets a market the client does not (yet) serve; re-admit it manually when Stage 1 expansion plans activate it (see the simulated run).
4. **Zero business relevance** (BV = 1 and no strategic override) — the topic has no plausible path to revenue or brand relevance.

Hard **must-win overrides** bypass the score entirely and are always top-of-queue: branded terms, Google Business Profile / local-pack presence for any client with a physical or service-area presence, and core transactional pages already earning revenue.

## 6.4 How an LLM assists without inventing scores

**RECOMMENDATION — the constrained-scoring protocol.** An LLM must never emit a final numeric score from a prompt like "rate this opportunity 1–5." That produces plausible-looking numbers with no accountable basis and no way to catch drift. Instead:

1. **The LLM extracts evidence, not scores.** For each dimension, the agent's job is to retrieve or compute the *inputs* a human would use to score it — e.g., for `WIN`, it reports "3 of the top 5 ranking pages are from domains with no evident topical authority in this niche; 2 of 5 pages are 5+ years old and thin," not "WIN = 4."
2. **Deterministic code computes the sub-score from a rubric, where possible.** Anything that can be derived from data (DEM from GSC/vendor volume, TTI from a lookup table, DCF from which fields are first-party) is computed by code, not asked of the LLM at all.
3. **The LLM proposes a score only for genuinely qualitative dimensions (BV, GAIN, STRAT), and must show its work.** The output is structured JSON with a `score`, a `rationale` citing the specific evidence used, and a `confidence`. No rationale, no score accepted by the pipeline.
4. **Every LLM-proposed score is sampled for human review** (Section 3.4: FCMO reviews the top 50; QA Agent spot-checks a random 10% of the rest for rationale quality).
5. **Score drift is monitored.** If the same cluster is re-scored on a later run and the LLM-proposed dimension moves by more than 1 point with no new evidence, the pipeline flags it rather than silently overwriting the prior value.
6. **The LLM never sets DCF or TTI.** Those are computed entirely from data provenance (are the values first-party or vendor-estimated?) and a lookup table, precisely because those two modifiers exist to guard against unaccountable confidence.

```json
{
  "cluster_id": "violin-appraisal-insurance",
  "dimension": "GAIN",
  "score": 5,
  "rationale": "Client is a certified USPAP appraiser with 12 years of case files; no competing page in the top 10 cites a certified appraiser or shows real case examples.",
  "evidence_refs": ["client_intake.credentials", "serp_snapshot_2026-09-14.top10"],
  "confidence": "high"
}
```

Rows with `confidence: "low"` or missing `evidence_refs` are rejected by the pipeline and routed to a human for manual scoring.

---

## 7. Human-in-the-loop model

**Operating principle.** The objective is not maximum automation; it is maximum useful leverage without sacrificing quality, judgment, trust, or client outcomes. The classification below is exhaustive across the system's components, using five levels: **Fully automated**, **Automated with QA**, **AI-assisted**, **Human decision required**, **Human-only**.

| Component | Classification | Rationale |
|---|---|---|
| Data pulls (GSC, GA4, CrUX, crawl, backlinks) | **Fully automated** | Deterministic retrieval; no judgment involved |
| Anomaly detection (statistical threshold breach) | **Fully automated** (detection) | Flagging a deviation is deterministic; explaining it is not (see below) |
| Anomaly *diagnosis* (likely cause) | **Automated with QA** | AI proposes causes; a human confirms before any client-facing statement |
| Technical issue detection (crawl-based) | **Fully automated** | Rule-based detectors (broken links, missing tags, etc.) |
| Technical issue *prioritization and remediation design* | **AI-assisted** | Severity scoring is automatable; sequencing against a client's actual dev capacity needs a human |
| Keyword expansion and clustering | **Fully automated** | Mechanical transformation of seed terms into clusters |
| Keyword *intent classification* | **Automated with QA** | AI classifies from SERP evidence; ambiguous cases and the top 50 clusters get human review |
| Opportunity scoring (deterministic dimensions: DEM, TTI, DCF) | **Fully automated** | Pure computation from data |
| Opportunity scoring (qualitative dimensions: BV, GAIN, STRAT) | **AI-assisted** | LLM proposes with evidence; human samples and can override |
| Final prioritization / roadmap sequencing | **Human decision required** | Business judgment about resourcing, client relationship, and risk appetite that no model has access to |
| **Strategic recommendations** | **Human decision required** | Always FCMO-owned; agents draft, never decide |
| Competitor content-footprint classification | **Automated with QA** | Mechanical categorization with sampled accuracy checks |
| Content brief drafting | **AI-assisted** | Structure and SERP synthesis automatable; the information-gain plan and SME assignment need a human |
| **Content publication** | **Human-only** (or A2 draft, human publishes) | Even for low-risk content, the publish action itself is never autonomous |
| Internal-link suggestion | **AI-assisted** | Suggestion is automatable; a human approves before any CMS change |
| Schema/structured-data generation | **AI-assisted** | Draft generation automatable; a human verifies parity with visible content before deployment |
| **Link outreach (pitching, guest posts, unlinked-mention requests)** | **Human-only** | Personalization and relationship risk make this unsuitable for automation at any stage beyond opportunity-finding |
| Backlink monitoring (detecting new/lost links, spam patterns) | **Fully automated** | Detection is mechanical |
| Disavow file preparation/submission | **Human decision required**, submission **Human-only** | Rare, high-impact, and Google explicitly says most sites don't need it [S15] |
| **Client communications** (reports, calls, emails to the client) | **Human-only** for delivery; **AI-assisted** for drafting | The FCMO must always be the voice the client hears from, even when a draft is machine-assisted |
| Report data compilation | **Fully automated** | Numbers pulled programmatically from the warehouse |
| Report narrative drafting | **AI-assisted** | Bounded by the actual numbers; never invents interpretation the human hasn't reviewed |
| Executive summary | **Human decision required** for final content | FCMO must edit and personally stand behind every claim before it reaches a CEO-level reader |
| **Technical changes to a live site** (redirects, canonicals, robots.txt, schema deployment) | **Human decision required**, execution **Human-only** or dev-team-executed | Irreversible-risk actions never exceed A2 (draft) autonomy |
| **Brand-sensitive claims** (differentiation, "best," comparative claims) | **Human-only** | Legal and reputational exposure; no AI sign-off substitutes for human accountability |
| **Legal/compliance-sensitive content** (YMYL, regulated claims) | **Human-only**, with qualified expert review | Beyond FCMO review — requires subject-matter/legal sign-off per Section 3.10 |
| **Reputation-sensitive actions** (review responses, Business Profile edits, crisis communications) | **Human-only** | No autonomy level permits these; agents may draft, but a human sends |
| Local citation / NAP consistency auditing | **Fully automated** | Mechanical comparison against aggregator data |
| Local citation *correction submission* | **AI-assisted** draft, **Human decision required** to submit | Directory submissions can affect a live public listing |
| Hypothesis register maintenance | **Automated with QA** | Automation logs and tracks; a human writes the actual hypothesis and closes it out |
| Playbook/QA rubric updates | **Human decision required** | Changing what "good" means for the system is a governance act |

**RECOMMENDATION.** Notice the pattern: almost nothing in this system is "Fully automated" once it touches judgment, relationships, or anything irreversible — and that is the intended shape, not an accident of caution. The leverage comes from collapsing the *research and drafting* burden, not from removing the human from decisions that carry business or reputational weight.
