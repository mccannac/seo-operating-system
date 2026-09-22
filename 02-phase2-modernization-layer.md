# PHASE 2: The 2021 → 2026 modernization layer

**How to read this section.** The pattern is *what the coursework teaches → what remains valid → what has changed → what the system should do instead*. Where the coursework is internally inconsistent or factually wrong (not merely dated), I say so. † marks a change I know from background knowledge but did not re-verify in this session.

## 2.0 Timeline of changes that matter

| When | Change | Effect on this curriculum | Ref |
|---|---|---|---|
| Jun 2021 | Page experience / Core Web Vitals begin rolling into ranking | Course was written just as this landed; speed advice stayed generic | [S7] |
| Dec 2022† | E-A-T becomes **E-E-A-T** (Experience added) | Course teaches "EAT" | [S18] |
| Aug–Sep 2023 | FAQ rich results restricted; HowTo removed | Course teaches rich snippets as a lever | [S5] |
| Dec 2023 | **Mobile-Friendly Test, Mobile Usability report, and API retired**; Lighthouse is the pointer | Course audit relies on the Mobile-Friendly Test | [S6] |
| Mar 2024 | **INP replaces FID** as a Core Web Vital | Course predates INP | [S7] |
| Mar 2024 | Spam policy expansion (scaled content abuse, expired domain abuse, site reputation abuse) | Relevant to AI content and link practices | [S12] |
| Jul 2023–2024† | Universal Analytics sunset → GA4 | Every GA screen and metric in the course | — |
| Sep 2025 | `&num=100` stops working; rank-tracker cost/coverage changes; Search Console impressions and average position shift | Course teaches "look at the first and second SERPs" and rank tracking depth | [S11] |
| Sep 2025 | Latest Quality Rater Guidelines version (per secondary reporting) | E-E-A-T, AI content, YMYL scope | [S18] |
| Feb 2026 | **Bing Webmaster Tools "AI Performance"** public preview (Copilot/AI summary citations, grounding queries) | First first-party AI-citation data | [S8] |
| Mar 2026 | Spam update (Mar 24–25) then broad core update (Mar 27–Apr 8) | Scaled-content risk | [S12] |
| May 7, 2026 | **FAQ rich results stop appearing** in Google Search; report/testing support removed in stages | Course's structured-data value proposition | [S5] |
| May 13, 2026 | GA4 adds a native **AI Assistant** channel (coverage of platforms reported inconsistently) | Attribution of AI referrals | [S13] |
| **May 15, 2026** | Google publishes **"Optimizing your website for generative AI features on Google Search"** | Official position on GEO/AEO | [S2][S3] |
| **Jun 3, 2026** | Search Console **Generative AI performance reports** (impressions only; staged rollout) plus an opt-out control | First official Google AI-visibility data | [S4] |
| Jun & Aug 2026 | Additional spam updates (details unconfirmed by Google) | Volatility annotation | [S12] |

## 2.1 The modernization table

Columns: **Concept** | **Original approach (2021)** | **Status** | **Modern interpretation** | **Keep / Modify / Remove** | **Reason**

### A. Search fundamentals and strategy

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Definition of SEO | Format content and tech to raise visibility in results, improving traffic quantity and quality | **MODERNIZED** | Earn visibility and conversions across classic results, SERP features, maps, video, and AI answer surfaces; judge by business outcomes | Modify | "Results" now include AI Overviews/AI Mode and assistant citations [S1][S2] |
| Search-engine landscape | Google/Bing/Yahoo with market-share stats (92.4 / 2.6 / 1.8%) | **OUTDATED** | Multi-surface: Google (Search, AI Overviews, AI Mode, Discover, Maps, YouTube), Bing/Copilot, ChatGPT search, Perplexity, others. Use *the client's own* analytics for channel mix | Modify | Static share stats age quickly; surface diversity matters more |
| Search intent | Learn / Find / Buy | **MODERNIZED** | Keep the principle; classify as informational, navigational, commercial-investigation, transactional, local, plus multi-step/comparison tasks. Validate intent from **SERP composition**, not a label | Keep + expand | Google describes AI Mode as suited to complex, multi-part questions and uses "query fan-out" into sub-queries [S1] |
| SERP types | Knowledge graph, product, local, video, image, ads, news, snippets | **MODERNIZED** | Add AI Overviews, AI Mode, People Also Ask, discussion/forum modules, shopping and local packs. Record which modules appear per query cluster | Modify | Module mix changes click potential; it feeds the opportunity model |
| E-A-T | "Component of Google's algorithm" scored per site; checklist of certifications, bios, SSL | **MODERNIZED** | **E-E-A-T is a quality framework from rater guidelines, not a ranking factor or score.** Experience was added; Trust is the anchor. Evidence lives at page, author, and brand level | Modify | Treat as an *evidence-building checklist* (real authors, first-hand material, transparent sourcing), not a "score" [S18] |
| "Top ranking factors" list | Page speed, bounce rate, time on site, CTR, social signals, backlinks | **OUTDATED** (as a factor list) / **CONTEXTUAL** (as diagnostics) | Do not optimize GA bounce rate or time-on-site *as if* they were ranking inputs. Google's ranking systems and possible use of click data are not publicly specified. Use engagement metrics to diagnose UX and conversion | Remove as "factors"; keep as diagnostics | Presenting unverified factors as fact erodes client trust; treat click-behavior effects as **UNCERTAIN** |
| "Crawlability is a ranking signal" | Crawlable = ranks better | **OUTDATED** | Crawlability and indexability are **eligibility prerequisites**; without them nothing ranks. They are not ranking boosts | Modify | Google says pages must be indexed and snippet-eligible to be supporting links in AI features [S2] |
| Topical authority / content themes / silos | Content silos, deep architecture "increases authority" | **UNCERTAIN** | Cluster content around topics because it helps users, internal linking, and coverage. Google has not confirmed a "topical authority score" | Modify | Useful planning heuristic, not a guaranteed lever |

### B. Keyword and intent research

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Keyword Planner as the primary source | Volume/CPC/competition from Google Ads tool | **MODERNIZED** | Keyword Planner is one input. Without ad spend it returns volume *buckets* (visible in the archive's own export). Blend with **Search Console queries**, SERP-derived expansions, sales/support language, and third-party estimates | Modify | First-party data beats estimates |
| Select keywords by **lowest average CPC** | "Identify the terms with the lowest average CPC" | **OUTDATED / harmful** | CPC is an auction price for paid ads. Higher CPC often signals *commercial value*. Use CPC only as a commercial-intent proxy | **Remove** | Optimizes for the wrong thing |
| **Avoid content on low-volume topics** | Volume as gatekeeper | **OUTDATED** | Low-volume, high-intent queries often convert best; AI-search fan-out queries have no reliable volume; emerging topics show zero | **Remove** | Replace with the opportunity model (Section 3.4) |
| Short-tail vs long-tail by word count | ≤2 words vs ≥3 | **MODERNIZED** | Tail = specificity and intent, not length. Conversational, multi-clause queries are growing | Modify | Word count is a poor proxy |
| Prefix + keyword + suffix mixing | Manual combinatorics | **MODERNIZED** | Keep as a seed technique; supplement with LLM-assisted expansion and SERP mining (PAA, autocomplete, related searches, GSC) and **cluster by SERP overlap** | Modify | Scales better and stays grounded in what Google actually returns |
| 2×2 difficulty × volume → page tier | High-authority pages for hard terms, blog for easy terms | **CURRENT** (idea) | Keep the principle. Replace vendor "difficulty" with **SERP-based winnability** (who ranks, page types, freshness, authority gap) | Keep + modify | Vendor difficulty scores are proprietary and inconsistent |
| Keyword density / frequency | "Keyword use and frequency matter" | **OUTDATED** | No target density. Aim for semantic coverage and clarity; keyword stuffing is a spam-policy violation | Remove | [S12] |
| Keyword cannibalization | Multiple pages for the same query = self-competition | **CURRENT** | Reframe as **intent overlap**: multiple URLs serving the same intent. Detect via GSC query-page pairs; not always harmful; consolidate with evidence | Keep + modify | Avoid needless merges |
| Buying-stage tagging | Tag key phrases by stage | **CURRENT** | Keep; connect stage to conversion path and CRM stage | Keep | Bridges SEO to revenue |

### C. On-page and content

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Title tag length/rules | 65–70 chars; include keyword; avoid stop words, all caps | **MODERNIZED** | Google truncates by pixel width and frequently rewrites title links. Write clear, unique, descriptive titles; drop "avoid stop words"; test CTR in GSC | Modify | Titles are a relevance and click asset, not a keyword container |
| Meta description | Include keywords + CTA | **MODERNIZED** | Not a ranking factor; Google often generates its own snippet. Still worth writing for click-through on important pages | Modify | Low leverage per page |
| **Meta keywords** (logged in content audit) | Log meta keywords in audit | **OUTDATED** | Ignored by Google; remove from audit templates† | Remove | Wasted effort |
| H1 rules | "H1 is a major ranking factor; exactly one per page" | **MODERNIZED** | Headings help users, accessibility, and machine parsing. Multiple H1s are not a problem in themselves†. Audit *clarity and hierarchy*, not counts | Modify | The course's own sample site (3 H1s) was judged "alright" |
| Alt text | Describe images; use keywords | **CURRENT** | Describe the image for accessibility; no stuffing. Original, quality images matter for visual search and AI surfaces [S2] | Keep | — |
| Duplicate content and canonicals | Use `rel=canonical` | **CURRENT** | Canonical is a *hint*. Handle parameters, faceted navigation, syndication, and JS-rendered canonicals. Check the rendered HTML | Keep + modify | — |
| Internal linking and anchors | Manual linking | **CURRENT** | Still among the highest-ROI on-page levers. Automate opportunity discovery (semantic similarity, orphan detection, link-depth) with human approval | Keep + automate | — |
| Site architecture | Flat vs deep; silos increase authority | **CONTEXTUAL** | Logical hierarchy and short click paths matter. The course contradicts itself: it recommends fewer clicks from home *and* claims deep architecture raises authority | Modify | Prefer "important pages ≤3 clicks; topical grouping; no orphans" |
| XML sitemap | "Guarantees Google sees all pages" | **MODERNIZED** | A discovery **hint**, not a guarantee. Keep only canonical, indexable URLs. Add IndexNow for Bing/others† | Modify | — |
| Accessibility | "Search engines take accessibility into account for ranking" | **UNCERTAIN** (ranking) / **CURRENT** (value) | Do it for users and legal risk; semantic HTML also aids parsing. Don't promise ranking gains | Keep, reframe | — |
| Content strategy 5 steps | Goals → audience → type → channels → distribute | **CURRENT** | Keep skeleton; add **differentiation test** ("what can only we say?") and conversion pathing | Keep + extend | Google calls "non-commodity" content the key AI-visibility lever [S2] |
| Personas | HubSpot "Make My Persona" | **MODERNIZED** | Build from evidence: CRM, sales calls, support tickets, reviews, GSC queries | Modify | Invented personas hide real language |
| **AI-generated content** | *(not covered)* | **NEW** | Google's stance: quality and usefulness matter, not production method; **scaled low-value content is spam** (scaled content abuse). Use AI to assist expert-led work, never to mass-produce pages | Add policy | 2026 spam/core updates reinforced scaled-content enforcement [S12] |
| Programmatic SEO | *(not covered)* | **CONTEXTUAL** | Legitimate when each page carries unique data or utility (directories, comparison tools). High risk when templated filler | Add gated method | Needs information-gain test and sampled QA |
| Content velocity | *(implied "publish consistently")* | **OUTDATED** | Cadence is a project-management convenience, not a ranking lever. Deceptive date bumps are risky (secondary reports) | Modify | — |
| Content audit (R/Y/G) | GA + GSC + code log → red/yellow/green | **CURRENT** | **Best method in the archive.** Rebuild on GSC API + GA4 + backlinks + conversions; output keep/update/consolidate/prune/redirect | Keep + modernize | — |
| Historical optimization | Refresh top decayed posts; compare 4-week windows | **CURRENT** | Automate decay detection; extend comparison windows and control for seasonality and update volatility | Keep + modernize | — |

### D. Technical SEO

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Robots.txt | "Instructs bots how to index"; `noindex` "located in robots.txt" | **OUTDATED / incorrect** | robots.txt controls **crawling**, not indexing. `noindex` belongs in a meta robots tag or `X-Robots-Tag` (Google dropped robots.txt noindex in 2019†). Blocking a URL in robots.txt can prevent Google from seeing a `noindex` | Correct | Course error |
| robots.txt for AI crawlers | *(not covered)* | **NEW** | Vendors run **separate** bots for training, search indexing, and user fetch. Blocking one does not block the others. OpenAI: blocking `OAI-SearchBot` removes a site from ChatGPT search answers; `GPTBot` (training) is independent | Add | [S9] |
| HTTPS/SSL | Encrypt; HTTP vs HTTPS | **CURRENT** | Baseline hygiene | Keep | — |
| Site speed | Server, images, plugins, PHP 7.2, 64-bit OS | **MODERNIZED** | Measure **Core Web Vitals in field data** (LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1 at the 75th percentile). PHP 7.2 is long end-of-life†. Ranking weight is modest relative to relevance; UX and conversion are the stronger justification | Modify | INP replaced FID (Mar 2024) [S7] |
| 404 pages | "Bad for SEO" | **MODERNIZED** | 404s are normal. Fix when internal links point to them, when URLs with backlinks/traffic vanished, or when soft 404s appear | Modify | Avoid false-alarm audits |
| 301 vs 302 | Permanent vs temporary; `.htaccess` snippets | **CURRENT** (concept) / **CONTEXTUAL** (snippets) | Use permanent redirects for moves; implement at the CDN/edge/framework layer as needed. Apache snippets apply only to Apache | Keep concept | — |
| Mobile-friendliness | Mobile-Friendly Test | **OUTDATED (tool)** | Tool retired Dec 2023; use Lighthouse and real-device checks; mobile-first indexing is the default | Replace tool | [S6] |
| Preferred domain | www vs non-www | **CURRENT** | Consolidate with 301 and canonical | Keep | — |
| GSC sections | Performance, URL Inspection, **Coverage**, Sitemap, **Mobile Usability**, **Sitelinks Search Box** | **OUTDATED** | Coverage → **Page indexing** report†; Mobile Usability retired [S6]; sitelinks search box discontinued†; **new: Generative AI performance reports** [S4] | Replace | UI changes; API and bulk export are the automation path |
| JavaScript rendering | *(not covered)* | **NEW** | Compare raw vs rendered HTML; ensure critical content, links, canonicals, and structured data are present after rendering | Add | Frequent hidden cause of index gaps |
| International / hreflang | *(not covered)* | **NEW / CONTEXTUAL** | Only when relevant | Add | — |

### E. Structured data

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Tools | Google Structured Data Markup Helper; **Structured Data Testing Tool** | **OUTDATED** | Use **Rich Results Test** (for Google features) and the **Schema Markup Validator** (general schema.org)† | Replace | Testing Tool was already retired around the course's writing† |
| JSON-LD | Recommended | **CURRENT** | Still the preferred format | Keep | — |
| Rich snippets as a lever | Structured data "allows rich snippets" | **MODERNIZED** | Rich results for many types remain (Product, Article, Event, Recipe, Review snippets, Video, etc.). **FAQ rich results are gone** (May 7, 2026); HowTo removed in 2023; several niche types deprecated in Jan 2026 (secondary). Markup may remain, causes no harm, and won't produce visible FAQ results | Modify | [S5] |
| Structured data for AI search | *(not covered)* | **UNCERTAIN** | Google says structured data is **not required** for generative AI features and no special AI markup exists [S2]. Keep schema for eligible rich results, entity clarity, and data quality, with markup **matching visible content** | Keep for classic reasons | Don't sell schema as an "AI hack" |

### F. Local SEO

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Google My Business | Claim, NAP, photos, replies | **MODERNIZED** | Now **Google Business Profile (GBP)**†. Google's stated pillars: relevance, distance, prominence. Expert survey (Whitespark, n=47) ranks primary category and proximity highest; reviews rising; citations declining in weight | Modify | Weights are expert opinion, not Google data (**UNCERTAIN** as numbers) [S14] |
| Citation building | List on Yellowpages, Citysearch, Merchant Circle… | **MODERNIZED** | NAP consistency remains **hygiene** (data aggregators + top industry/local directories). Stop volume-based directory submission | Modify | Several listed directories are obsolete |
| Review signals | Get reviews on many sites | **CURRENT** | Google reviews (volume, recency, rating, text, responses) matter most for GBP; solicit ethically; never gate or buy | Keep + tighten | Policy risk |
| Behavioral signals | CTR, click-to-call, check-ins | **UNCERTAIN** | Directionally plausible; unproven causal weight. Optimize the profile for user action, not the "signal" | Reframe | — |
| Voice / "near me" | Q&A format, NAP, schema for voice | **MODERNIZED** | Keep accurate business data and concise answers. Assistant landscape changed (Cortana discontinued†); treat "voice" as conversational search | Modify | — |

### G. Off-page and links

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Links as top-3 factor; "best off-page tactic" | Link building as core | **MODERNIZED** | Links remain a meaningful signal, but *earned* editorial links from digital PR, original research, partnerships, and genuine relationships are the ethical path | Modify | Spam updates target manipulative links [S12] |
| Link value factors (relevance, anchor, freshness, decay, diversity…) | Triage dimensions | **CURRENT** | Keep as **triage dimensions**, not a formula | Keep | — |
| Vendor authority metrics (DA/DR/Authority Score) | Used as KPIs; referring IPs/subnets, citation flow | **CONTEXTUAL** | Third-party proxies, not Google metrics. Use for relative comparison and prospecting; do not present as "authority" outcomes | Modify | Prevents vanity KPI |
| `.gov` / `.edu` **comment** links; forum/Reddit link dropping; directory submission | "Search for .edu/.gov sites with comments crawlers can follow" | **OUTDATED / high risk** | Comment and forum link placement is spam behavior. Google does not treat TLDs as inherently valuable† | **Remove** | Reputational and spam risk |
| Guest blogging | Do's and don'ts | **CONTEXTUAL** | Only for genuine audience exposure in relevant publications; qualify links when appropriate; never mass or paid | Restrict | Link-scheme risk |
| Paid links | "Google looks down on" | **CURRENT** | Correct. Use `rel="sponsored"`/`ugc`/`nofollow` where applicable | Keep | — |
| Nofollow | Prevents sharing value | **OUTDATED** | Nofollow is a hint†; sculpting via nofollow is not a strategy | Modify | — |
| Disavow | Monitor backlinks and disavow "negative links" | **CONTEXTUAL** | Use only for a **manual action** or for links you or a vendor created. Google says most sites don't need it; its systems ignore most spam | Restrict | [S15] |
| Unlinked brand mentions | Ask for a link | **CURRENT** | Ethical, high-yield; keep human-sent | Keep | — |
| Broken-link building | Replace dead links with your content | **CURRENT** | Keep only when your content is genuinely equivalent or better | Keep | — |
| Social signals | "Amplify ranking factors" | **UNCERTAIN** | Treat social/video/forums as **distribution and discovery channels**, not ranking levers | Reframe | — |
| Brand mentions and AI answers | *(brand mentions taught as SEO)* | **UNCERTAIN** | Real brand presence and reputation help users and may correlate with AI citations; **seeking inauthentic mentions is spam and Google says it won't help** [S2] | Ethical only | — |

### H. Measurement, analytics, and reporting

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Analytics platform | Universal Analytics screens | **OUTDATED** | GA4 (events, engagement rate, key events, BigQuery export). Build reports on Search Console + GA4 + CRM | Replace | — |
| KPI set | Pageviews, bounce, time on site, pages/visit, scroll depth | **MODERNIZED** | Three tiers: outcome (revenue, pipeline, qualified leads), leading (visibility, qualified sessions), diagnostic (engagement, CWV). Don't lead with diagnostics | Modify | — |
| Baseline → compare cycle | 8-step tracking loop | **CURRENT** | Add algorithm-update annotations, seasonality, and (where feasible) holdout comparisons | Keep + strengthen | — |
| Rank tracking | "Keyword ranking increase" as KPI | **MODERNIZED** | Track rank for a **priority set** (top ~20 depth is reliable); `&num=100` removal made deep tracking costlier and shifted GSC impressions/position [S11] | Modify | Google has not formally explained the change |
| Attribution | Not covered | **NEW** | SEO is assisted-conversion heavy. Use blended attribution: GA4 key events + CRM opportunity source + hidden form fields; state uncertainty | Add | — |
| Privacy / first-party data | Not covered | **NEW** | Consent-mode gaps mean under-counting; integrate CRM; minimize personal data sent to LLMs | Add | — |
| Zero-click | Not covered | **NEW** | Report *visibility* (impressions, cited presence) alongside clicks; segment by intent; see Section 2.3 | Add | [S10] |
| Tool list | Ubersuggest, MozBar, WooRank, Website Grader | **CONTEXTUAL** | Generic "grader" scores are shallow; do not base audits on them. Prefer crawler + GSC + CrUX + logs | Replace | — |
| Audit format | 14-item manual audit + automated grader | **MODERNIZED** | Keep the structure; automate detection; add severity and impact/effort scoring | Modify | — |

### I. Emerging search (2021 view → 2026 view)

| Concept | Original approach | Status | Modern interpretation | Action | Reason |
|---|---|---|---|---|---|
| Voice search | Alexa/Google/Siri/Cortana; Q&A format | **MODERNIZED** | Fold into conversational-query coverage; low standalone priority | Demote | — |
| Visual search | Alt text, image sitemap, quality images | **MODERNIZED** | High-quality original images and video are explicitly recommended for generative AI surfaces [S2]; alt text and clean image delivery remain | Modify | — |
| Video | YouTube SEO, transcripts, video sitemap, schema | **CURRENT** | Video is a first-class result and citation type; keep and extend | Keep | — |
| AI Overviews / AI Mode | *(absent)* | **NEW / ESTABLISHED (as features)** | Present in Google Search; use query fan-out; links to supporting pages; controlled by standard eligibility (indexed, snippet-eligible) | Add | [S1][S2] |
| LLM-assistant discovery | *(absent)* | **EMERGING** | ChatGPT search, Copilot, Perplexity and others retrieve web content via their own crawlers/indexes. Allow the search crawlers you want, and measure | Add (measured) | [S8][S9] |
| llms.txt, chunking, AI-only rewrites | *(absent)* | **UNCERTAIN** | Google says not needed. Some third-party claims of effects on other assistants lack strong evidence. Zero-cost items (llms.txt) may be done last; never sold as strategy | Deprioritize | [S2] |
| Entity understanding | Knowledge graph on SERP (taught as a SERP type) | **MODERNIZED** | Consistent organization/person/product identity across site, GBP, schema, profiles, and reputable third-party sources | Add | Foundation for brand and author trust |

## 2.2 What the coursework got wrong (not just old)

These should be *corrected explicitly* if any of the original material is reused with clients.

1. **`noindex` in robots.txt** and robots.txt "instructs bots how to index."
2. **"Sitemap guarantees that Google sees all pages."**
3. **"Crawlability is a ranking signal."**
4. **Lowest CPC as a keyword-selection criterion.**
5. **Meta keywords logged as an audit item.**
6. **Nofollow "prevents Google from sharing the value of your links."**
7. **Deep architecture "increases authority"** while also advising fewer clicks from the home page.
8. **Disavowing as routine backlink hygiene.**
9. **`.gov`/`.edu` comment links.**
10. **"Google uses accessibility for ranking."** (unsupported as stated)

## 2.3 Evidence ladder for AI-search claims

The brief asked me not to exaggerate emerging AI-search concepts. This is the ladder the system uses to label every AI-related tactic before it reaches a client.

| Tier | Definition | Items | System behavior |
|---|---|---|---|
| **ESTABLISHED** | Backed by Google/Bing/OpenAI documentation or unambiguous behavior | Content must be indexed and snippet-eligible to be linked in AI features; AI Overviews/AI Mode use query fan-out; AI features rooted in core ranking/quality systems; separate AI crawlers with separate robots.txt tokens; Search Console and Bing now report AI-surface visibility (with limits) | Build into audits and reports |
| **EMERGING** | Real signal, thin or contested evidence | AI-referral traffic is small but tends to convert well (vendor/analyst data, varies); brand/entity presence correlating with citations; conversational-query coverage; multimodal (image/video) inclusion | Monitor; run small experiments; label uncertainty |
| **EXPERIMENTAL** | Vendor-promoted, no strong independent support | llms.txt / markdown mirrors; content "chunking"; prompt-mimicking Q&A rewrites; "share of model" scores from sampled prompts; AI-visibility scores as KPIs | Do not sell as strategy; allow only low-cost tests with a pre-registered success metric |
| **RISKY** | Can violate spam policies | Inauthentic mention-seeding; mass AI-generated pages; scaled programmatic pages without unique value | Prohibit |

### What the data says about zero-click and AI answers (and its limits)

- **Pew (US panel, 2025):** users clicked a traditional result on 8% of visits with an AI summary vs. 15% without; about 1% clicked a source link inside the summary [S10].
- **Ahrefs (Dec 2025):** position-one CTR was reduced by about 58% when an AI Overview appeared [S10].
- **Later data shows partial stabilization** in one tracker (organic CTR on AI-Overview queries rising from 1.3% to 2.4% between Dec 2025 and Feb 2026, still below queries without an overview) [S10]. Studies use different definitions and samples, so **do not average them**.
- **Impact varies sharply by intent:** informational queries are hit hardest; branded and transactional queries far less. So the opportunity model includes a **click-realism** term (Section 3.4).

## 2.4 Validation flags: what I could not settle

- **Search Console AI reports:** announced Jun 3, 2026 with a staged rollout and impressions-only data (no clicks) [S4]. **Confirm access per property before promising it in a client scope.**
- **GA4 AI Assistant channel:** secondary sources disagree on which platforms it covers (ChatGPT/Gemini/Claude vs. a list including Copilot, Grok, Deepseek) and on Perplexity [S13]. **Verify in each property.** Sessions without referrers still land in Direct.
- **Local ranking weights:** percentages in circulation come from an expert opinion survey and are re-quoted inconsistently; I use ranks, not percentages.
- **Spam/core update targets:** Google rarely specifies; several "what it targeted" claims are third-party inference [S12]. The system annotates dates and avoids causal claims.
- **Some sources are vendor or agency blogs.** I prefer Google, Bing, and OpenAI documentation and flagged where I couldn't fetch the primary page (e.g., web.dev thresholds).
- **Whether GEO tactics help outside Google:** weak or mixed evidence; the industry debate is live [S19][S20].
