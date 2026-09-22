## 3.5 Stage 5: Competitive intelligence

**Principle:** a client has *three* competitor sets, and they are rarely the same companies.

| Competitor set | Definition | How found |
|---|---|---|
| **Business competitors** | Who buyers actually compare you with | Sales input, review sites, intake |
| **SERP competitors** | Domains and pages that occupy the results for your target clusters (often publishers, marketplaces, forums) | SERP snapshots across clusters; frequency of appearance |
| **AI-answer competitors** | Sources cited when AI features answer your target questions | Manual/sampled prompt checks; Bing AI Performance and Search Console AI reports for your *own* side [S4][S8] |

*(The course's "look at the first and second SERPs" method survives, but deep-SERP sampling is now costlier and less reliable after `&num=100` stopped working [S11]. Cap depth at roughly the top 20.)*

### Analysis dimensions

| Dimension | Evidence collected | Method |
|---|---|---|
| Organic visibility | Ranking keyword counts, estimated traffic, share of cluster visibility | Vendor API (directional) |
| Content footprint | Page inventory by type (guide, comparison, case study, tool, video) | Crawl + LLM classification; the course's content-type matrix (F11) |
| Topic coverage | Which clusters they cover, depth, and freshness | Embedding clustering of their pages |
| Search-intent coverage | Intent mix vs. ours | Intent classifier |
| Authority signals | Referring domains (relevant ones), notable editorial links, link velocity | Backlink APIs; treat vendor scores as proxies |
| Technical strengths | CWV field data, rendering, structured data, architecture | Crawler; CrUX |
| SERP ownership | Which modules they win (snippets, video, PAA, local pack, AI citations) | SERP snapshots |
| Local visibility | Map-pack presence, GBP completeness, review count/recency | SERP + GBP analysis |
| Brand / entity signals | Brand search demand trend, panels, third-party coverage, author entities | SERP + news monitoring |
| AI-search visibility (where measurable) | Citation frequency in sampled AI answers; treat as **directional** | Manual/sampled checks; document prompt set and date |

### Standard output row

| Competitor | Evidence | Gap | Opportunity | Recommended action |
|---|---|---|---|---|
| *(illustrative)* Competitor B | Ranks top 3 for 14 terms in the "insurance appraisal" cluster with a 2,000-word guide and 6 case-study pages (crawl + SERP snapshot dated 2026-09-14) | Client has one thin service page and no proof content | Winnable cluster where client holds real credentials | Create pillar guide + 3 anonymized case studies from client's own work; link from service page; pitch a broker association for a data-backed feature. Hypothesis: +20% qualified clicks in 120 days |

**QA rules:** every row must cite a dated snapshot or export; no row without an owner and a hypothesis; competitor claims about *traffic* are labeled estimates.

---

## 3.6 Stage 6: Content strategy

**Goal:** convert intelligence into a prioritized editorial and optimization program that is *differentiated, evidence-based, and tied to conversion*, and that avoids generic AI-generated "SEO content." Google's own guidance frames "non-commodity" content (unique insight beyond common knowledge) as the most consequential factor for visibility in its AI features [S2].

### Content decision engine (per URL and per cluster)

| Trigger (from GSC/GA4/crawl/CRM) | Decision | Action |
|---|---|---|
| Business-relevant intent, **no page** | **Create** | Brief → SME → production |
| Impressions high, CTR low or position 4–20 | **Update (optimize)** | Retitle, tighten intent match, add missing sections, internal links |
| Traffic/rank **decayed** vs. trailing baseline (seasonality-adjusted) | **Refresh** | Update facts, examples, evidence; keep URL |
| Multiple URLs serving one intent, splitting impressions | **Consolidate** | Merge into strongest URL; 301 the rest; preserve backlinks |
| No traffic, no links, no business value, no unique content | **Prune** | 404/410, or redirect to the closest relevant page |
| Performing and converting | **Protect and extend** | Add internal links, supporting content, conversion path tests |
| Weak on E-E-A-T evidence (YMYL) | **Upgrade evidence** | Expert reviewer, citations, author bio, update process |

*This is the course's red/yellow/green content audit (F8) and historical optimization workbook (F9), rebuilt as an automated queue with human approval.*

### Content brief standard

A brief is not a keyword list. Required sections:

1. **Target cluster, intent, and page type**
2. **Business goal and conversion path** (next step for the reader; CRM event)
3. **Audience and funnel stage** (from the customer-language bank)
4. **SERP synthesis:** what ranks now, what format, what's missing
5. **Information-gain plan:** the specific first-hand experience, data, expert perspective, or original visual this page will contain that the top results do not
6. **Named author and SME** with credentials and what they'll contribute
7. **Evidence requirements:** sources to cite, data to gather, claims that need proof
8. **Outline as questions to answer**, not as headings to stuff
9. **Internal links** (in and out), anchor guidance
10. **Media plan:** original photos/video/diagrams; alt text guidance
11. **Entity and schema notes** (only where it matches visible content)
12. **Compliance and YMYL notes**
13. **QA checklist and measurement:** metric, baseline, review date

### AI usage policy for content

| Category | Rule | Examples |
|---|---|---|
| **Allowed** | AI assists research and editing; humans own claims | Research synthesis, outline options, SERP summaries, transcript-to-draft from *SME interviews* with human edit, metadata drafts, translation with review, link suggestions |
| **Restricted** | Requires SME-sourced input, named editor, and evidence check | Drafting body copy; YMYL topics (also require qualified expert review) |
| **Prohibited** | Never | Mass page generation without unique value; fabricated quotes, stats, reviews, credentials, or "first-hand" experience; auto-publishing; AI-authored outreach at scale |

Google's position is that production method is not the issue; scaled low-value content is [S12]. The March 2026 core update coverage reinforces that AI-assisted content is not penalized by default, but scaled, unedited, low-information content is.

### Quality gates before publish

- **Information-gain test:** would a reader learn something they can't get from the top five results? If not, don't publish.
- **Intent match** to the SERP evidence.
- **Cannibalization check** against existing URLs.
- **Fact and claim check** against the evidence ledger; every statistic sourced.
- **E-E-A-T evidence check:** author identity, credentials, first-hand material, sources.
- **Similarity/plagiarism check.**
- **Accessibility and rendering check.**
- **Conversion path present.**

### Programmatic content (if the client's model supports it)

Permitted only when each page carries unique, verifiable data or utility. Require: a template quality spec, a per-page uniqueness metric, staged rollout (10–50 pages), indexing and engagement review before scaling, and a kill switch. Otherwise treat as scaled content abuse risk [S12].

---

## 3.7 Stage 7: Authority and off-page strategy

**Principle:** authority is *earned reputation*, and the system's job is to find real opportunities and prepare humans, not to manufacture signals.

### What can be systematized

| Function | Automation role | Human role |
|---|---|---|
| **Link-worthy asset discovery** | Analyze which content types earn links in the niche; propose asset ideas | Choose and produce assets with real data or expertise |
| **Digital PR opportunity radar** | Monitor news, expert-request platforms, and topical trends; alert on fits | Decide what to say; pitch; build relationships |
| **Industry publications and partners** | Compile lists by relevance and audience | Judge fit; relationship outreach |
| **Citations** | Audit NAP/aggregator consistency; flag mismatches | Fix and verify listings |
| **Unlinked mentions** | Detect brand mentions without links | Human-sent, personalized request |
| **Competitor backlink opportunities** | Find pages linking to several competitors but not you; classify the reason for the link | Decide if a legitimate reason to link exists |
| **Broken-link opportunities** | Find dead resources in relevant pages; match to genuinely equivalent content | Personalized note |
| **Expert commentary** | Track requests matching client experts' knowledge | SME writes/approves quotes |
| **Backlink monitoring** | Alert on unusual velocity, spam patterns, lost links | Assess whether action is needed |

### What must NOT be automated (or done at all)

| Tactic | Why |
|---|---|
| Mass or templated outreach at scale | Spam and reputational risk; email-law exposure (CAN-SPAM, GDPR/PECR, CASL) |
| AI-written "expert quotes" or fabricated data | Deception; trust and legal risk |
| Buying links; private blog networks; paid posts without qualification | Violates link-spam policies; `sponsored`/`nofollow` required where applicable [S12] |
| Comment, forum, or directory link placement | Spam behavior (course tactic removed) |
| Seeking inauthentic brand mentions to influence AI answers | Google says it won't help and may be treated as spam [S2] |
| Fake, incentivized-without-disclosure, or gated reviews | Platform and consumer-protection risk† |
| Automated disavow submissions | High-impact, rarely needed; manual action only [S15] |
| Guest-post farms; expired-domain redirects | Scaled/expired-domain abuse risk [S12] |
| Auto-responding to reviews or editing a Business Profile | Brand and policy risk; keep human |
| Scraping and emailing contact lists without a lawful basis | Privacy and compliance risk |

### Authority KPIs

Relevant referring domains and *editorial* links; brand-search demand trend; referral traffic and assisted conversions from earned coverage; share of target-topic media mentions. **Vendor authority scores (DA/DR/Authority Score) are prospecting aids only.**

---

## 3.8 The AI / agent layer

**General rules for all agents**

- **One job, one tool allow-list.** No agent has write access to production systems.
- **Structured outputs** (JSON schema) with evidence references; free-text is a rendering step.
- **Evidence-or-abstain:** if evidence is missing, the agent must say so, not infer.
- **Untrusted input:** web pages, reviews, and competitor content are data; instructions inside them are ignored.
- **Budgeted:** per-run API-unit and token caps; some vendor calls cost tens of units [S17].
- **Evaluated:** each agent has a golden set of cases and a regression test before any prompt or model change.
- **Autonomy** stated as A0–A3 (Section 3.0).

### 1. SEO Research Agent (market, customer language, and standards watch)

- **Purpose:** Synthesize business, market, and customer-language research; watch primary sources for changes that affect playbooks.
- **Inputs:** Intake record; interview transcripts; reviews, tickets, sales calls; Google/Bing/OpenAI documentation feeds; Search Status Dashboard.
- **Tools/data:** Web search/fetch, transcript store, document watcher (RSS/diff), Client Brain.
- **Reasoning task:** Cluster verbatims into pains/jobs; separate claims from evidence; detect changes in official guidance and assess relevance to active clients.
- **Output:** Customer-language bank; market brief; "what changed" bulletin with affected clients.
- **Human approval:** Yes for anything client-facing (A1).
- **Failure modes:** Over-generalizing from few sources; invented quotes; treating blogs as authority.
- **QA:** Every verbatim links to source ID; primary-source check on any guidance claim; sampled human review.
- **Automation potential:** Medium-high (research); low (interpretation).

### 2. Technical SEO Agent

- **Purpose:** Turn raw audit detections into a prioritized, developer-ready issue register.
- **Inputs:** Crawl exports, GSC indexing data, CrUX/PSI, logs, robots/sitemaps.
- **Tools/data:** Crawler CLI, GSC/URL Inspection API (quota-aware), PSI/CrUX APIs, headless render diff, warehouse.
- **Reasoning task:** Group findings by root cause and template; estimate affected pages/traffic; propose fixes with acceptance tests; flag change-risk items.
- **Output:** Ranked issue register; tickets with repro steps; monitoring rules.
- **Human approval:** Yes for prioritization and any ticket to dev (A1→A2 for ticket creation).
- **Failure modes:** False positives on intentional exclusions; recommending risky changes (canonical/redirect) without context; ignoring JS rendering.
- **QA:** Detection unit tests on known-issue sites; require URL evidence; second-check redirects/canonicals against rendered HTML.
- **Automation potential:** High for detection; medium for triage; low for remediation design.

### 3. Keyword Intelligence Agent

- **Purpose:** Build and refresh the keyword-cluster universe and score opportunities.
- **Inputs:** Seeds, GSC queries, customer-language bank, vendor exports, SERP data.
- **Tools/data:** Keyword/SERP APIs, embeddings, warehouse, opportunity-model scorer.
- **Reasoning task:** Expand, classify intent with SERP evidence, resolve ambiguous head terms, cluster, and assign dimension scores with rationale.
- **Output:** Cluster table with intent, entities, scores, recommended action, and evidence.
- **Human approval:** Yes for the top-50 and any strategic cluster (A1).
- **Failure modes:** Trusting vendor volume; mis-clustering; intent errors (for example "appraisal"); hallucinated volumes.
- **QA:** Numeric fields only from API; 10% human sample; consistency test on repeated runs; ambiguity flags forced.
- **Automation potential:** High for expansion/clustering; medium for scoring; human for value judgments (BV, GAIN).

### 4. Competitor Intelligence Agent

- **Purpose:** Maintain the competitor evidence ledger across three competitor sets.
- **Inputs:** Competitor domains, SERP snapshots, crawls, backlink data, review data.
- **Tools/data:** Crawl/scrape (respecting robots and terms), backlink API, SERP API, LLM classifier.
- **Reasoning task:** Classify their content footprint; detect gaps; explain *why* a competitor ranks using evidence, not speculation.
- **Output:** Competitor → Evidence → Gap → Opportunity → Action rows (Section 3.5).
- **Human approval:** Yes (A1).
- **Failure modes:** Over-attributing rank to one factor; stale data; presenting estimates as facts; prompt injection from scraped pages.
- **QA:** Snapshot date on every row; estimate labels; injection-resistant pipeline; spot checks.
- **Automation potential:** Medium-high.

### 5. Content Opportunity Agent

- **Purpose:** Run the content decision engine (create/update/refresh/consolidate/prune).
- **Inputs:** Content inventory, GSC/GA4 performance, backlink/link data, opportunity scores, conversions.
- **Tools/data:** Warehouse queries, decay detector, similarity search, cannibalization detector.
- **Reasoning task:** Apply decision rules; propose consolidation pairs; estimate impact; flag risk (URLs with links or conversions).
- **Output:** Prioritized action queue with rationale, expected impact, and rollback notes.
- **Human approval:** Yes, especially prune/consolidate (A1).
- **Failure modes:** Recommending prunes that discard backlinks/assisted conversions; seasonality misread; merging pages with distinct intent.
- **QA:** Guardrail rules (never prune with links/conversions without review); backtests on past changes.
- **Automation potential:** High (detection); medium (decision).

### 6. Content Brief Agent

- **Purpose:** Produce briefs that enforce information gain and evidence requirements.
- **Inputs:** Target cluster, SERP synthesis, customer-language bank, SME roster, client proof assets.
- **Tools/data:** SERP fetch, Client Brain, brief template.
- **Reasoning task:** Identify what top results lack; propose an information-gain plan from *client-owned* material; draft outline as questions.
- **Output:** Completed brief (Section 3.6 standard).
- **Human approval:** Yes; strategist and SME sign-off (A1).
- **Failure modes:** Generic briefs cloned from top results; proposing "expertise" the client doesn't have; fabricated proof.
- **QA:** "Information-gain plan" cannot be empty; every proof item must map to a client asset; similarity check against top results.
- **Automation potential:** Medium-high.

### 7. Internal Linking Agent

- **Purpose:** Find and rank internal-link opportunities and structural problems.
- **Inputs:** Crawl graph, content embeddings, conversion pages, priority clusters.
- **Tools/data:** Crawler, embeddings/vector search, CMS (read).
- **Reasoning task:** Suggest source→target links with anchor and placement; detect orphans, hub gaps, and cannibalizing anchors.
- **Output:** Link suggestion list with context sentence and expected benefit.
- **Human approval:** Yes; editor approves; optional A2 to create CMS draft edits.
- **Failure modes:** Irrelevant/over-optimized anchors; link overload; linking to noindex/redirected pages.
- **QA:** Check target status/indexability; cap links per page; anchor variety rules.
- **Automation potential:** High for suggestions; A2 for drafts.

### 8. SERP Analysis Agent

- **Purpose:** Describe what the SERP rewards for a cluster: modules, page types, freshness, and AI-surface presence.
- **Inputs:** SERP snapshots (location/device specified), top URLs, module presence.
- **Tools/data:** SERP API; page fetch; LLM classifier.
- **Reasoning task:** Infer dominant intent and format; identify feature ownership; estimate click yield; note AI Overview presence.
- **Output:** SERP brief per cluster; click-realism input (CLK) for the model.
- **Human approval:** Sample (A1).
- **Failure modes:** Personalization/location variance treated as universal; sampling once; volatility during updates.
- **QA:** Snapshot metadata (date/location/device); repeat sampling on priority clusters; update-calendar flags.
- **Automation potential:** High.

### 9. Local SEO Agent

- **Purpose:** Monitor and diagnose local visibility (GBP, reviews, pack rankings, citations).
- **Inputs:** GBP data (read), review feeds, local rank grids, citation audit, competitor GBPs.
- **Tools/data:** GBP API/export, local rank tracker, SERP API.
- **Reasoning task:** Compare categories, services, review velocity, and completeness against competitors; spot suspensions and inconsistencies.
- **Output:** Local diagnostics; recommended profile changes; review-request plan; anomaly alerts.
- **Human approval:** Required for **any** profile edit or review response. Agent never edits GBP (A0–A1 only).
- **Failure modes:** Recommending category or name changes that risk suspension; treating survey weights as facts; spammy location pages.
- **QA:** Policy checklist against Google's GBP guidelines; human verification.
- **Automation potential:** Medium (monitoring high, action low).

### 10. Structured Data Agent

- **Purpose:** Generate and validate schema that matches visible content.
- **Inputs:** Page HTML, entity records, feed data.
- **Tools/data:** Schema.org vocabulary, validators (Rich Results Test manual, Schema Markup Validator), Search Console reports.
- **Reasoning task:** Choose eligible types; produce JSON-LD; check parity with visible content; flag deprecated types (for example FAQ) [S5].
- **Output:** JSON-LD drafts with validation results and rollout notes.
- **Human approval:** Yes; deployment is a ticket (A1→A2 draft).
- **Failure modes:** Marking up content not on the page; stale prices/availability; over-markup with no benefit.
- **QA:** Automated parity test; validator pass; sampled human review; post-deploy GSC monitoring.
- **Automation potential:** High for generation; medium for governance.

### 11. SEO QA Agent

- **Purpose:** Gatekeeper for deliverables: catches errors, unsupported claims, and policy violations before human review.
- **Inputs:** Draft deliverables (audits, briefs, reports, content), evidence ledger.
- **Tools/data:** Rule engine, similarity checks, link/URL checkers, claim-to-source matcher.
- **Reasoning task:** Verify claims have evidence; check numbers against source tables; detect AI-content policy violations; check brand voice and formatting.
- **Output:** Pass/fail with annotated defects.
- **Human approval:** Human reviewer sees QA report; QA cannot approve alone.
- **Failure modes:** False confidence; misses subtle factual errors; over-blocking.
- **QA:** Seeded-error test sets (planted defects) run weekly; track recall/precision.
- **Automation potential:** Medium-high.

### 12. Analytics Agent

- **Purpose:** Monitor performance, detect anomalies, and explain movement.
- **Inputs:** GSC, GA4, CRM outcomes, rank data, update calendar, release log.
- **Tools/data:** Warehouse, seasonal decomposition/anomaly detection, annotation store.
- **Reasoning task:** Decompose changes (page group, query class, device, brand vs. non-brand, intent); test against known events (updates, releases, tracking changes); propose hypotheses.
- **Output:** Anomaly alerts with likely causes, confidence, and next checks; weekly diagnostics.
- **Human approval:** Alerts auto (A3); interpretation reviewed before client communication.
- **Failure modes:** Correlation-as-cause; ignoring tracking breakage or consent effects; misreading `&num=100`-type data shifts [S11].
- **QA:** Data-quality checks first (tags, sampling, consent); backtests on known incidents.
- **Automation potential:** High for detection; medium for explanation.

### 13. Reporting Agent

- **Purpose:** Assemble recurring reports from governed data and templates.
- **Inputs:** Approved KPI tree, warehouse, annotations, hypothesis register.
- **Tools/data:** BI tool/API, report templates.
- **Reasoning task:** Populate modules; write plain-language commentary bounded by data; highlight deltas versus baseline/plan.
- **Output:** Weekly ops digest; monthly report draft.
- **Human approval:** Yes for monthly/quarterly (A1); weekly internal digests may run A3.
- **Failure modes:** Confident narrative over noisy data; metric drift; omitting bad news.
- **QA:** Numbers pulled programmatically, never typed by the model; reconcile to source dashboards; "bad news must appear" rule.
- **Automation potential:** High.

### 14. Executive Summary Agent

- **Purpose:** Convert the report into a one-page decision document for executives.
- **Inputs:** Approved monthly report, scenario model, risk register.
- **Tools/data:** Client Brain, report outputs.
- **Reasoning task:** Lead with business outcome and confidence; separate what we know from what we believe; state decisions requested.
- **Output:** One-page summary: outcome, drivers, risks, next 30/60/90 decisions.
- **Human approval:** FCMO must edit and approve (A1).
- **Failure modes:** Overstating attribution; hiding uncertainty; jargon.
- **QA:** Claims tagged with confidence; checklist for "decisions requested"; tone review.
- **Automation potential:** Medium (drafting), low (judgment).

### 15. AI Visibility Monitor (measurement-only; EMERGING)

- **Purpose:** Track first-party AI-surface data and sampled AI answers, without overclaiming.
- **Inputs:** Search Console generative AI reports (where available), Bing AI Performance, GA4 AI referrals, log data for AI crawlers, a fixed prompt set.
- **Tools/data:** GSC/Bing exports, GA4, logs, sampled prompt runs.
- **Reasoning task:** Trend citations/impressions by page and topic; flag drops; compare with classic organic; document sampling method.
- **Output:** AI visibility panel with clear labels: **first-party**, **sampled**, **estimated**.
- **Human approval:** Sample review; A0/A1 only.
- **Failure modes:** Non-deterministic prompt results treated as rankings; conflating impressions with clicks; partial platform coverage [S4][S8][S13].
- **QA:** Fixed prompt panel; repeated runs; report ranges; never a headline KPI.
- **Automation potential:** Medium.

### Agent run schedule

| Cadence | Agents | Output |
|---|---|---|
| Onboarding (weeks 1–4) | Research, Technical, Keyword, Competitor, SERP, Content Opportunity | Onboarding Audit Pack and 90-day roadmap |
| Daily/continuous | Analytics (alerts), Technical (regression monitors) | Alerts |
| Weekly | Analytics, Reporting, AI Visibility Monitor, Local | Ops digest |
| Monthly | Keyword refresh, Content Opportunity, Competitor, Reporting, Executive Summary | Monthly report and exec page |
| Per initiative | Brief, Internal Linking, Structured Data, QA | Briefs, links, schema, QA reports |
| Quarterly | Research (standards review), all agents' eval reruns | Playbook update; agent scorecard |

---

## 3.9 Measurement, reporting, and learning

### KPI tree

| Tier | Metrics | Use |
|---|---|---|
| **Outcome** | Revenue and pipeline from organic; qualified leads; cost/lead vs. other channels; payback | Executive headline (with confidence) |
| **Leading** | Non-brand clicks and impressions by intent; share of target-cluster visibility; local pack visibility; qualified organic sessions; assisted conversions; AI-surface impressions/citations (labeled) | Programme steering |
| **Diagnostic** | Index coverage, CWV, crawl errors, CTR by page group, engagement rate, referral quality | Root-cause analysis |

**Attribution stance:** SEO is under-credited by last-click. Use GA4 key events, CRM opportunity source fields, and hidden form fields; state uncertainty; report ranges. Consent gaps and referrer-less AI sessions mean under-counting [S13].

### Cadence

| Cadence | Audience | Content |
|---|---|---|
| Weekly (internal) | FCMO + team | Anomalies, tickets, experiments in flight |
| Monthly | Client marketing lead | KPI tree, what moved and why, next actions |
| Quarterly | Executives | Strategy review, scenario model vs. actual, resource decisions |

### Anomaly rules (Analytics Agent)

- Non-brand clicks or impressions deviate beyond seasonal expectation by page group (not just sitewide).
- Index coverage change > threshold; new `noindex`, robots.txt or sitemap diff.
- CWV regression at the 75th percentile on any key template.
- Brand SERP change; GBP suspension or rating drop.
- Sudden ranking volatility coinciding with a logged Google update: **annotate, do not diagnose** until the rollout completes [S12].
- Tracking failure (tag drops, conversion spikes/drops without traffic change).
- Data-source change (for example, definition or coverage changes in vendor tools) [S11].

### Executive report structure (one page + appendix)

1. **Headline outcome** vs. plan (with confidence grade)
2. **What changed and why** (evidence; update annotations)
3. **What's working / what isn't** (bad news is mandatory)
4. **Risks and dependencies** (dev capacity, approvals, algorithm volatility)
5. **Decisions requested** (30/60/90-day)
6. **Scenario tracker** (the "Modeled Search Investment" pattern from the archive: conservative / expected / stretch, with assumptions)
7. **Appendix:** KPI tables, experiment log, technical status

### Learning loop

| Element | Description |
|---|---|
| **Hypothesis register** | ID, statement, metric, baseline, expected effect, start/end dates, owner, result, decision |
| **Experiment discipline** | Pre-register success metric; avoid overlapping tests on the same page group; use before/after with seasonality control or holdouts where feasible |
| **Post-mortems** | Every closed hypothesis writes a lesson into the Client Brain and the shared playbook |
| **Agent evaluation** | Golden sets and seeded-error tests; monthly scorecard: accuracy, edit rate, time saved, defects escaping to clients |
| **Prompt/model change control** | Versioned prompts; regression before rollout; rollback plan |
| **Playbook review** | Quarterly: re-validate against primary sources (Google/Bing documentation, update history); retire practices that no longer hold |

---

## 3.10 Governance, risk, and compliance

| Risk | Control |
|---|---|
| **Prompt injection from scraped/competitor/review content** | Treat web text as data; separate "instructions" from "content" in prompts; no tool calls triggered by fetched content; allow-listed tools; output schema validation; log tool calls |
| **Client data leakage** | Per-client tenants; least-privilege credentials; data minimization (no personal data in prompts); vendor DPAs; retention limits |
| **Hallucinated facts and metrics** | Numbers only from APIs; evidence ledger; QA agent; human review |
| **Spam-policy exposure** | AI-content policy; scaled/programmatic gating; link-scheme prohibitions (Section 3.7) [S12] |
| **Irreversible actions** | Autonomy ceiling A2; named approvers; staging first; rollback plans |
| **Cost overrun** | Per-run and per-client budgets; caching; agent cost estimates before paid calls [S17] |
| **Platform and data volatility** | Source-change monitoring (Search Console, Bing, GA4, SERP vendors); annotate data breaks; retire brittle dependencies |
| **Transparency with clients** | Disclose AI-assisted workflows and human-review commitments in the engagement; never present sampled/estimated data as first-party |
| **Regulatory/YMYL** | Expert review, claim substantiation, industry rules (health, finance, legal) |

---