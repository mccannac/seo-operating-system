# PHASE 1: Ingest and understand the curriculum

## 1.1 What is actually in the archive

| Group | Files | What I found | Reliability for extraction |
|---|---|---|---|
| **Lecture decks** | 15 PDFs (Lessons 1, 3–16) | 24–59 slides each, but only ~2.5–5K characters of text per deck: heavily image-based (stock photos, UI screenshots of Keyword Planner, Moz, Google Analytics *Universal* UI, GMB setup, Markup Helper). Each deck carries an identical 4-slide "course path" preamble. | Text layers extracted for all 15; I visually reviewed the Intro and Measurement decks. Tool-demo slides in other decks show UIs that no longer exist. |
| **Study guide** | 1 PDF, 46 pp. | The densest source: ~19 modules summarized in outline form (its text repeats once in the file). Contains the technical claims I audit in Phase 2. | Full text read. |
| **Syllabus** | 1 PDF | Course map, learning objectives, activities, required reading (Papagiannis, *Effective SEO and Content Marketing*, Wiley 2020, **not in the archive**). | Full text read. |
| **Final project form** | 2 PDFs (byte-identical) | The capstone template: keyword discovery → SERP evaluation → on-page/technical/backlink scoring (1–5) → 3–5 target keywords → 3 pages with title/meta/H1/alt. | Full text read. |
| **HubSpot Historical Optimization Workbook** | 2 XLSX (byte-identical; one has a mangled filename) | Two-tab refresh tracker: blog master list by page views; "posts to optimize" with target topics, snippet status, before/after 4-week page views, % change, status, notes. | Read. |
| **Manual SEO Audit Questions** | 1 XLSX | 14-item manual audit (domain check → heading tags) with tool per item, applied to two window-and-door sites. | Read. |
| **Keyword Stats export** | 1 XLSX, ~1,000 rows | Google Keyword Planner export (Apr 2020–Mar 2021) for a learner project on violin appraisal/lutherie topics. Monthly-search columns are empty (account without ad spend → volume buckets only). | Read (structure + sample). |
| **Untitled spreadsheets** | 3 XLSX | (a) keyword shortlist with volume bucket and competition; (b) manual-audit comparison of two window/door sites vs. a contractor site, with heading extracts; (c) GA exercise template (Sept 2020 vs Aug 2020 on-page metrics). | Read. |
| **Images** | 24 (1 checklist + 23 screenshots) | Audit checklist; 2×2 keyword difficulty/volume matrix; YMYL breakout prompt; content-type matrix for agencies; final-project rubric; **example client SEO decks** (competitor bubble chart, modeled search investment, three "Horizon" roadmap, KPI dashboards, GA benchmark vs industry, funnel analyses); a completed learner final project (cocktail blog). | Viewed all 24. |

**Gaps in the archive itself:** no deck for Lesson 2 (Search Engines in Depth; covered only in the study guide), Lesson 17 (SEO Audits II), or Lessons 18–19 (final project presentations). The screenshots include real third-party client metrics (a financial-services firm, an engineering firm, a clinical-trial finder). I treated them as *patterns to learn from* and will not carry any of that data into the system.

**Licensing note.** The decks are marked © 1996–2021 HackerU Ltd. This document paraphrases concepts and re-expresses them as system components; it does not reproduce slide text. Confirm licensing before redistributing any original material to clients.

## 1.2 Knowledge model: SEO domains and how well the curriculum covers them

Coverage rating: **Strong** (taught with method), **Moderate** (taught as concepts, thin on method), **Thin** (mentioned), **Absent**.

| Domain | Curriculum coverage | Where it lives | Key gap for an FCMO system |
|---|---|---|---|
| Strategy / roadmapping | Moderate | Syllabus; Horizon Review + Modeled Investment images | No prioritization method, no tie to revenue model or resourcing |
| Business discovery | **Absent** | Final project asks "what topics do you want to be known for" | No intake, revenue model, sales cycle, constraints |
| Audience research | Thin | Persona exercise (HubSpot Make My Persona); review-mining tip | No first-party research (sales calls, CRM, support) |
| Search intent | Moderate | Lesson 1 (learn/find/buy); Lesson 4 buying stages | Only three intents; no SERP-based intent validation |
| Keyword research | Strong (method) / weak (judgment) | Lessons 3–4, Keyword Planner; 2×2 matrix | CPC-based selection; volume-only; no clustering or SERP realism |
| Competitive intelligence | Moderate | Lesson 14; final-project scoring tables; content matrix | Competitors = "first two SERPs" only; subjective 1–5 scores |
| Technical SEO | Moderate | Lesson 8; checklist | Several wrong claims; no JS rendering, logs, migrations, international |
| Information architecture | Thin | Lesson 6 (silos, flat vs deep) | Internally inconsistent guidance |
| On-page SEO | Strong (mechanics) | Lessons 5–6 | Over-weights tags and keyword frequency |
| Content strategy | Moderate | Lesson 12; content-audit method | Strong audit method; weak on differentiation and information gain |
| Content production | Thin | Lesson 12 | No brief standard, QA, or AI policy |
| Internal linking | Moderate | Lesson 6 | Manual only |
| Structured data | Moderate | Lesson 10 | Retired tools; rich-result landscape changed |
| Local SEO | Moderate | Lesson 11 | Directory list obsolete; GMB naming; factor weights outdated |
| Off-page / link building | Moderate | Lessons 7, 9 | Includes spam-risk tactics |
| Digital PR | Thin | "Earned links," traditional media | No PR method |
| Measurement | Moderate | Lesson 15; tracking cycle; GA exercise | UA-based; vanity KPIs; no attribution thinking |
| Reporting | Thin | Example client decks | Useful *patterns*, no cadence or exec standard |
| Auditing | Strong (structure) | Lesson 16; manual audit; checklist | Manual, tool-shallow, unprioritized |
| Emerging search | Moderate (2021) | Lesson 13: voice, visual, video | Voice framing obsolete; no AI search at all |
| AI / search visibility | **Absent** | n/a | Entire domain missing |
| **Added:** Content refresh / historical optimization | Strong | HubSpot workbook | Best asset in the archive |
| **Added:** SEO forecasting / business case | Thin | "Modeled Search Investment" image | Excellent seed; needs method |
| **Added:** Accessibility | Thin | Lesson 12 | Claims ranking impact (UNCERTAIN) |
| **Added:** Governance, risk, compliance | **Absent** | n/a | Needed for AI agents and outreach |
| **Added:** Experimentation / learning loop | Thin | Tracking cycle | Needs hypothesis registry and closeouts |

## 1.3 Frameworks extracted

| # | Framework (as taught) | Source | Type | Verdict → reuse |
|---|---|---|---|---|
| F1 | **Crawl → index → rank; on-page / off-page / technical** trichotomy | Lessons 1–2 | Mental model | Keep as the base taxonomy; add "content/entity" and "SERP/AI surface" layers |
| F2 | **Basic audit checklist** (on-page 7 items, off-page 6, technical 7) | Checklist image, Lesson 16 | Checklist | Convert to automated check library (Section 3.3) |
| F3 | **14-item manual audit** (domain check, SERP appearance, speed, mobile, security, URL, structure, UX, social, content quality, headings) | Manual audit XLSX | Audit questions | Convert to hybrid audit; 8 of 14 are automatable |
| F4 | **Keyword difficulty × volume 2×2** mapping keyword sets to page tiers (L1 home / L2 category / L3+ blog) | Matrix image | Decision matrix | **Keep the idea** (match difficulty to page authority); replace vendor difficulty with SERP-based winnability |
| F5 | **Keyword list method:** seed → prefix/main/suffix → tool → export → sort by impressions, CPC | Lessons 3–4 | Process | Keep seed→expand→classify; **remove CPC-lowest filter**; replace sorting with opportunity score |
| F6 | **Buying-stage tagging** of key phrases | Lesson 4 activity | Classification | Keep; expand to intent taxonomy (Section 3.4) |
| F7 | **On-page element scoring 1–5** (title, meta, H1, alt; URL, speed, mobile; DA, links, anchors) | Final project | Scorecard | Keep as a *diagnostic rubric* for SERP-competitor teardown; add evidence column and remove subjective-only scoring |
| F8 | **Content audit red/yellow/green** using GA (pageviews, entrances, bounce, exit) + GSC (clicks, impressions, CTR, position) + code logging (title, meta, H1–H6) | Lesson 12 | Method | **Highest-value framework in the archive.** Modernize into keep/update/consolidate/prune/redirect decision engine |
| F9 | **Historical optimization workbook** (rank posts by views → pick decayed posts → update → compare 4-week before/after) | HubSpot XLSX | Template | Automate decay detection; add seasonality control |
| F10 | **Content strategy 5 steps** (goals, audience, content type, channels, distribute) + persona builder | Lesson 12 | Process | Keep skeleton; personas from real data |
| F11 | **Content-type matrix** (which formats competitors use: blogs, webinars, podcasts, guides, case studies…) | Matrix image | Competitive artifact | Reuse for content-footprint analysis |
| F12 | **Competitive research quad:** keyword, content, backlink, site-structure analysis (+ SWOT hint) | Lesson 14 | Method | Extend to business competitors vs SERP competitors vs AI-answer competitors |
| F13 | **Tracking cycle (8 steps):** strategy → discuss → baseline → execute → collect → compare → refine → report | Lesson 15 | Loop | **Keep as the measurement spine**; add controls, annotations |
| F14 | **KPI set:** organic sessions, keyword rank, leads/conversions, bounce, pages/session, avg duration; Authority Score/DA as KPI in examples | Lesson 15; KPI dashboard images | KPIs | Re-tier: outcome, leading, diagnostic (Section 3.9) |
| F15 | **Example client-deck patterns:** topline metrics vs benchmark; traffic-source table; landing-page bounce analysis; funnel step drop-off; competitor bubble chart (avg position vs keyword count); **modeled search investment** (30/50/75% improvement scenarios → visits → leads → conversions); **three horizons** (fixes → content roll-ups → platform/CMS) | Screenshots | Reporting/strategy templates | Adopt as executive-report modules (Sections 3.9, 3.1) |
| F16 | **Final-project rubric** (keyword research 30, competitor 25, content/site structure 20, on-page 20, instructions 5) | Rubric image | Assessment | Repurpose as **QA rubric for an onboarding audit deliverable** |
| F17 | **YMYL breakout** (pick YMYL site; check E-A-T signals; Moz DA) | Breakout image | Exercise | Keep YMYL risk-tiering; drop DA reliance |
| F18 | **Link value factors** (relevance, anchor, freshness, decay, diversity, footer/sidebar, spam) and **backlink analysis views** (top pages, top linking sites, top anchors) | Lessons 7, 9 | Analysis | Keep as triage dimensions; treat vendor metrics as proxies |
| F19 | **Local signals list** (proximity, GMB associations, links, citation consistency, DA, on-page keywords, anchors, CTR/click-to-call, social) | Lesson 11 | Checklist | Modernize with GBP-first structure (Section 2.1) |

## 1.4 Reusable artifacts → system components

The point is not to file these away but to *convert* them. Each row shows the modern component, who owns each step, and the target format.

| Source artifact | Modern system component | Human / LLM / API / Automation | Format |
|---|---|---|---|
| Final project form | **Onboarding Audit Pack** (research + strategy + first-90-day plan), scored by the F16 rubric | FCMO approves; agents draft; APIs supply data | Report template + JSON schema |
| *(none in archive)* → new | **Client Intake Form + Client Brain schema** (Section 3.1) | Human interview + LLM structuring | Form → structured record (Postgres/Notion) |
| Manual audit questions XLSX | **Audit Check Library** (each row = check ID, detector, severity model, remediation, owner) | API/crawler detect; LLM triage; human interpret | Database table + n8n workflow |
| SEO checklist image | **Quick-Scan Health Score** (run in first 48 hours) | Automation | Scored report |
| Keyword Planner sheet | **Keyword Intelligence Workbook**: seed → expansion → intent → cluster → opportunity score | API + LLM; human validates top 50 | Sheet/DB with versioned runs |
| Prefix–main–suffix method | **Query Expansion prompt + SERP-mined expansion** (PAA, autocomplete, GSC queries, sales-call phrases) | LLM + API | Prompt template |
| 2×2 difficulty/volume matrix | **Page-tier assignment rule** inside the opportunity model | Automation | Rule + visual |
| Competitor tables (1–5 scoring) | **Competitor Evidence Ledger** (competitor → evidence → gap → opportunity → action) | API collect; LLM synthesize; human approve | Table |
| Content audit R/Y/G | **Content Decision Engine** (keep / update / consolidate / prune / redirect) | Automation scores; human decides | Dashboard + queue |
| HubSpot historical workbook | **Refresh Queue** with decay alerts and before/after tracking | Automation + human | Table + n8n |
| Persona builder | **Persona-from-evidence record** (sources cited) | Human + LLM | Structured doc |
| Tracking cycle | **Hypothesis Register + Measurement Plan** | Human authors; automation monitors | Register |
| KPI images | **Three-tier KPI tree** and **Executive Report** modules | Automation compiles; human narrates | Dashboard + PDF/HTML |
| Modeled Search Investment slide | **Scenario Model** (conservative / expected / stretch with stated assumptions) | Human + spreadsheet | Model |
| Horizon Reviews | **Roadmap template** (Fix now / Build next / Scale later) | Human | Roadmap |
| Content-type matrix | **Content Footprint Map** for competitor gap analysis | LLM + human | Matrix |
| Rubric | **Deliverable QA checklist** | Human reviewer + QA agent | Checklist |

## 1.5 What the curriculum never asked, and an FCMO must

These become new system modules in Phase 3: business model and unit economics; sales cycle and lead quality; brand positioning and differentiation; entity/brand signals; SERP-feature and AI-surface analysis; JS rendering and log-file analysis; migrations; international/hreflang; programmatic content; AI-content and data-privacy policy; experimentation; stakeholder communication; and resourcing/constraint planning.