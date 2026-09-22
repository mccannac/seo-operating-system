# PART 4: Recommended build sequence

| Phase | Weeks | Build | Exit criterion |
|---|---|---|---|
| **1. Foundation** | 1–3 | Client Brain schema; connectors (Search Console, GA4, Bing Webmaster); annotation calendar; weekly digest (A0) | Digest runs for two pilot clients without manual data work |
| **2. Diagnostics** | 4–7 | Audit check library and Technical Agent; regression monitors; CWV pipeline | Issue register beats a manual audit on recall in a blind test |
| **3. Intelligence** | 8–11 | Keyword pipeline and opportunity model; SERP Agent; Competitor ledger | FCMO rates top-50 clusters ≥80% actionable |
| **4. Content system** | 12–15 | Decision engine; brief agent with gates; internal-linking agent | Briefs pass information-gain review; zero fabricated claims in a 30-item audit |
| **5. Authority and local** | 16–19 | Opportunity radar, mention detection, GBP monitor (read-only) | All outreach remains human-sent |
| **6. Executive layer and hardening** | 20–24 | Reporting and Executive Summary agents; QA agent; evaluation suite; AI Visibility Monitor | Agent scorecard in place; incident drill passed |

**Suggested next deliverables** (each is a natural Phase 4 step): (1) the client-intake questionnaire and Client Brain schema in full; (2) n8n workflow specifications for the first four automations (GSC ingest, weekly digest, technical regression monitor, keyword refresh); (3) system prompts, output schemas, and golden test cases for each agent; (4) the KPI dashboard spec and the executive-report template.

---

# Appendix A: Source register

*Primary sources are marked **(P)**; everything else is secondary reporting or commentary and should be verified against the primary page before being quoted to a client.*

| ID | Source | URL | Used for |
|---|---|---|---|
| S1 | **(P)** Google Search Central: *AI features and your website* | https://developers.google.com/search/docs/appearance/ai-features | How AI Overviews/AI Mode work; query fan-out |
| S2 | **(P)** Google Search Central: *Optimizing your website for generative AI features on Google Search* (May 15, 2026) | https://developers.google.com/search/docs/fundamentals/ai-optimization-guide | SEO relevance to AI features; non-commodity content; myths |
| S3 | **(P)** Google Search Central Blog (May 15, 2026) | https://developers.google.com/search/blog/2026/05/a-new-resource-for-optimizing | Announcement of S2 |
| S4 | **(P)** Google Search Central Blog: *Introducing Search Generative AI performance reports in Search Console* (Jun 3, 2026) | https://developers.google.com/search/blog/2026/06/gen-ai-performance-reports | AI-surface impressions reporting; staged rollout details via secondary coverage (impressions only, opt-out control) |
| S5 | Search Engine Journal / Search Engine Land on FAQ rich results retirement (May 7, 2026); Google documentation notice | https://www.searchenginejournal.com/google-drops-faq-rich-results-from-search/574429/ ; https://searchengineland.com/google-to-no-longer-support-faq-rich-results-476957 | FAQ rich result retirement and tooling timeline |
| S6 | **(P)** Google Search Central Blog: *The role of page experience in creating helpful content* (Apr 2023); Search Engine Land confirmation (Dec 2023) | https://developers.google.com/search/blog/2023/04/page-experience-in-search ; https://searchengineland.com/google-officially-drops-mobile-usability-report-mobile-friendly-test-tool-and-mobile-friendly-test-api-435377 | Retirement of Mobile-Friendly Test / Mobile Usability report |
| S7 | Core Web Vitals overview and thresholds (secondary; confirm on web.dev) | https://ppc.land/core-web-vitals/ | INP replaced FID (Mar 12, 2024); LCP/INP/CLS thresholds at p75 |
| S8 | **(P)** Bing Webmaster Blog: *Introducing AI Performance in Bing Webmaster Tools Public Preview* (Feb 2026); Bing help page | https://blogs.bing.com/webmaster/February-2026/Introducing-AI-Performance-in-Bing-Webmaster-Tools-Public-Preview ; https://www.bing.com/webmasters/help/ai-performance-9f8e7d6c | Copilot/AI-summary citation reporting |
| S9 | **(P)** OpenAI: *Overview of OpenAI Crawlers* | https://developers.openai.com/docs/gptbot | Separate bots for search vs. training; opt-out effects |
| S10 | Click-impact studies: Pew Research (via SerpApi summary); Ahrefs (Dec 2025); trend summary | https://serpapi.com/blog/the-state-of-the-serp-in-the-age-of-ai/ ; https://ahrefs.com/blog/ai-overviews-reduce-clicks-update ; https://www.seosummer.com/ai-overviews-organic-traffic/ | Zero-click and AI-answer click impact; methodological caveats |
| S11 | Coverage of the `&num=100` change (Google had not formally confirmed the cause) | https://www.jumpfly.com/blog/organic-search-impressions-fell-off-a-cliff-why-and-now-what/ | Rank-tracking/Search Console data shifts |
| S12 | Search Engine Journal on the March 2026 spam update; industry coverage of March core update and later spam updates. **Check the Google Search Status Dashboard for authoritative dates.** | https://www.searchenginejournal.com/google-begins-rolling-out-the-march-2026-spam-update/570428/ | Update timeline; spam-policy context |
| S13 | Coverage of GA4's AI Assistant channel (sources disagree on platform coverage) | https://www.madx.digital/learn/ga4-launches-ai-assistant-channel ; https://nogood.io/blog/how-to-track-ai-traffic/ | AI referral attribution limits |
| S14 | Whitespark Local Search Ranking Factors (expert survey) | https://whitespark.ca/local-search-ranking-factors/ | Local factor ranks (not Google data) |
| S15 | Search Engine Journal coverage of Google's disavow stance | https://www.searchenginejournal.com/google-disavow-tool/289871/ | Disavow only for manual actions/own schemes |
| S16 | n8n MCP overview (secondary) | https://uibakery.io/blog/n8n-mcp-guide | n8n MCP client/server and orchestration capabilities; verify in n8n docs |
| S17 | Comparison of SEO MCP servers/APIs (secondary) | https://mcpplaygroundonline.com/blog/seo-mcp-servers ; https://mcp.directory/blog/best-seo-mcp-servers-2026 | API-unit costs; vendor MCP availability |
| S18 | Quality Rater Guidelines explainers (secondary; official guidelines are published by Google) | https://theguidex.com/insights/google-quality-rater-guidelines | E-E-A-T framing; Sept 2025 version |
| S19 | iPullRank critique of Google's AI-search guidance | https://ipullrank.com/google-ai-search-guidance | Counter-view on "GEO is just SEO" |
| S20 | Search Engine Journal on Google's guide ("AEO and GEO still SEO") | https://www.searchenginejournal.com/googles-new-ai-search-guide-calls-aeo-and-geo-still-seo/575026/ | Independent summary of S2 |

# Appendix B: Curriculum traceability

| Course lesson | Primary system home |
|---|---|
| 1 Intro to SEO | 2.1-A; intent taxonomy (3.4) |
| 2 Search engines in depth | Technical audit (3.3); measurement setup (3.1) |
| 3–4 Keyword research | Keyword pipeline and opportunity model (3.4) |
| 5–6 On-page | Content decision engine (3.6); internal-linking agent; audit library |
| 7, 9 Off-page and link building | Authority system (3.7) |
| 8 Technical | Audit library (3.3); Technical Agent |
| 10 Structured data | Structured Data Agent; audit library |
| 11 Local | Local SEO Agent; local queries (3.4) |
| 12 Content marketing | Content strategy (3.6); brief standard; personas → customer-language bank (3.2) |
| 13 Emerging tech | 2.1-I; AI Visibility Monitor |
| 14 Competitive research | Competitive intelligence (3.5) |
| 15 Tracking | Measurement, reporting, and learning (3.9) |
| 16–17 Audits | Audit library; onboarding audit pack; final-project rubric as QA |