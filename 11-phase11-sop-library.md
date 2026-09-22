# PHASE 11: SOP library

Each SOP follows **Trigger → Inputs → Procedure → Outputs → QA → Owner → Automation level**. Automation-level values match Section 7's five-level scale.

## SOP-01: SEO Client Onboarding

| Field | Detail |
|---|---|
| Trigger | Contract signed |
| Inputs | Client contact info, domain(s), access credentials |
| Procedure | Create client record → pre-call enrichment crawl and SERP snapshot → schedule and conduct discovery interview → populate client profile schema → viability check (Go/Go-with-conditions/Pause) → set measurement baseline → log initial hypotheses |
| Outputs | Client profile record, measurement plan, hypothesis register entries, access/risk log |
| QA | FCMO confirms schema completeness and viability decision before Stage 2 begins |
| Owner | FCMO |
| Automation level | AI-assisted (enrichment, schema-fill); Human decision required (viability) |

## SOP-02: SEO Discovery (Business & Market Intelligence)

| Field | Detail |
|---|---|
| Trigger | Onboarding "Go" decision |
| Inputs | CRM export, sales-call access, review sites, support tickets |
| Procedure | Offer inventory → buyer/influencer mapping → win/loss and lost-deal review → customer-language extraction and clustering → journey mapping → commercial-intent mapping → market maturity assessment |
| Outputs | Customer-language bank, journey map, commercial intent map, differentiation-and-proof register |
| QA | Every verbatim must cite a source; human curates final language bank |
| Owner | FCMO + Research Agent |
| Automation level | AI-assisted |

## SOP-03: Technical Audit

| Field | Detail |
|---|---|
| Trigger | Onboarding "Go," or scheduled monthly re-audit |
| Inputs | Domain, crawl access, GSC property access |
| Procedure | Full crawl → GSC indexing pull → CrUX/PSI pull → rendered-vs-raw diff → structured-data extraction → severity × certainty ÷ effort scoring |
| Outputs | Ranked issue register, developer tickets, monitoring configuration |
| QA | Sampled human review of top 20 issues; redirect/canonical changes double-checked against rendered HTML |
| Owner | Technical SEO Agent (detection); FCMO + dev team (remediation) |
| Automation level | Fully automated (detection); AI-assisted (prioritization); Human decision required (remediation design) |

## SOP-04: Keyword Research

| Field | Detail |
|---|---|
| Trigger | Onboarding, or monthly refresh |
| Inputs | Seeds, customer-language bank, GSC queries, competitor page titles |
| Procedure | Seed discovery → expansion (autocomplete, PAA, related searches) → normalization → intent classification with SERP evidence → clustering by SERP overlap → demand enrichment → opportunity scoring |
| Outputs | Scored, clustered keyword table with recommended actions |
| QA | Ambiguous intent forced to human review; top 50 clusters reviewed by FCMO |
| Owner | Keyword Intelligence Agent; FCMO approves |
| Automation level | Fully automated (expansion/clustering); AI-assisted (scoring); Human decision required (final prioritization) |

## SOP-05: Competitor Research

| Field | Detail |
|---|---|
| Trigger | Onboarding, or monthly refresh, or competitor-event trigger |
| Inputs | Business competitor list, SERP snapshots |
| Procedure | Identify three competitor sets (business/SERP/AI-answer) → crawl and classify content footprint → backlink/authority signal pull → SERP ownership analysis → gap synthesis |
| Outputs | Competitor evidence ledger (Competitor → Evidence → Gap → Opportunity → Action) |
| QA | Every row cites a dated snapshot; 10% human spot-check |
| Owner | Competitor Intelligence Agent |
| Automation level | Automated with QA |

## SOP-06: Content Gap Analysis

| Field | Detail |
|---|---|
| Trigger | Monthly, or after competitor/keyword refresh |
| Inputs | Content inventory, keyword clusters, competitor content footprint |
| Procedure | Run the Content Decision Engine (create/update/refresh/consolidate/prune) against current performance and coverage data |
| Outputs | Prioritized content action queue |
| QA | Guardrail: never auto-recommend pruning a URL with active backlinks or conversions without flagging for review |
| Owner | Content Opportunity Agent |
| Automation level | Automated with QA |

## SOP-07: Content Brief Creation

| Field | Detail |
|---|---|
| Trigger | Content Decision Engine flags "Create" or "Update," or FCMO requests |
| Inputs | Target cluster, SERP synthesis, customer-language bank, SME roster |
| Procedure | Identify information gap vs. top results → draft information-gain plan from client-owned material → assign SME → draft outline as questions → specify evidence and compliance requirements |
| Outputs | Complete brief per the Section 3.6 standard |
| QA | Information-gain plan cannot be empty; similarity check against top-ranking pages |
| Owner | Content Brief Agent; strategist/SME sign-off |
| Automation level | AI-assisted |

## SOP-08: Internal Linking Review

| Field | Detail |
|---|---|
| Trigger | Monthly, or after new content publishes |
| Inputs | Crawl graph, content embeddings, priority clusters |
| Procedure | Detect orphans and hub gaps → suggest source→target links with anchor and placement → cap suggestions per review batch |
| Outputs | Link suggestion list with expected benefit |
| QA | Check target indexability; cap links per page; anchor-variety rule |
| Owner | Internal Linking Agent; editor approves |
| Automation level | AI-assisted |

## SOP-09: Local SEO Review

| Field | Detail |
|---|---|
| Trigger | Monthly, for any client with a physical/service-area presence |
| Inputs | GBP data, review feeds, local rank grid, citation audit |
| Procedure | Compare category/services/review velocity/completeness against competitors → flag inconsistencies and suspensions → draft profile-change recommendations |
| Outputs | Local diagnostics, recommended changes, review-request plan |
| QA | Policy checklist against GBP guidelines before any recommendation is surfaced |
| Owner | Local SEO Agent; FCMO approves any profile change |
| Automation level | Automated with QA (monitoring); Human-only (any live edit) |

## SOP-10: Structured Data Implementation

| Field | Detail |
|---|---|
| Trigger | New page type launched, or audit flags missing/invalid/deprecated schema |
| Inputs | Page HTML, entity records |
| Procedure | Select eligible schema type → generate JSON-LD → verify parity with visible content → flag deprecated types (e.g., FAQ) |
| Outputs | Validated JSON-LD draft with rollout notes |
| QA | Automated parity test; validator pass; sampled human review; post-deploy GSC monitoring |
| Owner | Structured Data Agent; dev team deploys |
| Automation level | AI-assisted (generation); Human decision required (deployment) |

## SOP-11: Link Opportunity Sourcing

| Field | Detail |
|---|---|
| Trigger | Monthly |
| Inputs | Competitor backlink data, brand-mention monitoring, broken-link scans |
| Procedure | Identify unlinked mentions, competitor-linked-not-us pages, broken-link replacement opportunities, and expert-commentary requests |
| Outputs | Prioritized outreach opportunity list |
| QA | No fabricated data; every opportunity cites its source |
| Owner | Research/Competitor agents (sourcing); FCMO/relationship owner (all outreach) |
| Automation level | AI-assisted (sourcing); Human-only (all outreach) |

## SOP-12: Monthly SEO Analysis

| Field | Detail |
|---|---|
| Trigger | Monthly cadence |
| Inputs | Full month of warehouse data, hypothesis register |
| Procedure | Compile KPI tree → decompose anomalies → test open hypotheses → draft findings |
| Outputs | Monthly analysis draft (feeds Strategic report, SOP-13) |
| QA | Data-quality checks precede any causal claim |
| Owner | Analytics Agent |
| Automation level | Automated with QA |

## SOP-13: Executive Reporting

| Field | Detail |
|---|---|
| Trigger | Monthly analysis complete |
| Inputs | KPI tree, hypothesis results, risk register |
| Procedure | Draft strategic report and executive one-pager → FCMO reviews and personally edits → deliver |
| Outputs | Strategic report, executive one-pager |
| QA | "Bad news must appear" rule; every number reconciles to the warehouse |
| Owner | Reporting Agent + Executive Summary Agent draft; FCMO approves |
| Automation level | AI-assisted (drafting); Human decision required (final content) |

## SOP-14: SEO QA (deliverable review)

| Field | Detail |
|---|---|
| Trigger | Any client-facing deliverable drafted (audit, brief, report, content) |
| Inputs | Draft deliverable, evidence ledger |
| Procedure | Verify claims against evidence → check numbers against source tables → check for AI-content policy violations → flag missing conversion paths, disclosures, or compliance gaps |
| Outputs | Pass/fail with annotated defects |
| QA | Seeded-error test sets run weekly to measure the QA agent's own recall |
| Owner | SEO QA Agent; human reviewer has final say |
| Automation level | Automated with QA |

## SOP-15: AI-Agent QA (system health)

| Field | Detail |
|---|---|
| Trigger | Quarterly, or after any prompt/model change |
| Inputs | Golden test cases, evaluation set, recent agent outputs |
| Procedure | Re-run each agent's golden set → compare outputs to expected results → check score-drift logs → review sampled human-override rate per agent |
| Outputs | Agent scorecard (accuracy, edit rate, defects escaping to clients) |
| QA | No prompt or model change ships without passing the regression suite |
| Owner | FCMO / technical lead |
| Automation level | Automated with QA |
