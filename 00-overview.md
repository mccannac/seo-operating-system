# SEO Operating System (SEO-OS)

*Exported from Claude Docs — September 22, 2026*

**A 2026 Fractional-CMO architecture, rebuilt from the UW–Madison Digital Marketing Bootcamp SEO curriculum (2021)**

*Prepared September 21, 2026. Scope of this document: Phase 1 (curriculum ingestion), Phase 2 (2021 → 2026 modernization layer), Phase 3 (FCMO operating model, including the agent layer). Source references like [S4] point to the Source Register at the end.*

---

## 0. Executive summary

**What the archive is.** Fifty files: 15 lecture decks, a syllabus, a study guide, a final-project worksheet, seven spreadsheets, and 24 images (a one-page audit checklist plus screenshots of worked examples). It is a solid *practitioner-level curriculum* (roughly "SEO fundamentals for a marketing generalist"). It is not an operating system: it teaches tasks, not a lifecycle. It has no business discovery, no prioritization model beyond a keyword sort, no governance, no experimentation, and nothing on AI search.

**What survives.** About a third of the curriculum is durable and should become system components almost unchanged: the crawl → index → rank mental model, search-intent thinking, duplicate/canonical handling, internal linking, the content-audit (red/yellow/green) method, the historical-optimization refresh workflow, the baseline → measure → compare → refine tracking cycle, and the three-horizon roadmap and modeled-investment slides from the example decks.

**What breaks.** Several things are wrong or dangerous if used as taught:

- **Prioritizing keywords by "lowest CPC" and "avoid low-volume topics"** (a paid-ads metric used as an SEO filter; the archive's own keyword sheet shows the tool suggesting real-estate and stock valuation terms for an instrument-appraisal practice).
- **`noindex` in robots.txt**, "sitemaps guarantee indexing", "crawlability is a ranking signal", "bounce rate / time on site / social signals are top ranking factors."
- **`.gov`/`.edu` comment-link hunting, forum and directory link dropping, and routine disavowing.**
- **Retired tools:** Structured Data Testing Tool, Mobile-Friendly Test, GA Universal Analytics screens, robots.txt tester, "Coverage" report.
- **FAQ/HowTo schema as a SERP lever** (FAQ rich results stopped appearing in Google Search on May 7, 2026 [S5]).

**What's missing entirely.** Business model and buyer research, entity/brand strategy, AI Overviews / AI Mode, LLM-assistant discovery and crawlers, AI-content policy, programmatic SEO, first-party data and privacy, attribution limits, JavaScript rendering, international SEO, migrations, log analysis, governance, and experimentation.

**The single most important 2026 finding for system design.** Google's own guidance (May 15, 2026) says AI Overviews and AI Mode are "rooted in our core Search ranking and quality systems" and that optimizing for generative AI search is, from Google's perspective, still SEO [S2][S3][S20]. Practitioners contest how far that framing holds outside Google (for example, [S19]), and independent studies show real click losses where AI answers appear [S10]. The system therefore treats **foundational SEO as the base layer and AI-search visibility as a measured, separate reporting layer**, not a separate discipline with its own magic tactics. Tactics Google explicitly says you can skip (llms.txt, "chunking," AI-specific rewrites, inauthentic mention-seeding) are demoted to **UNCERTAIN / low priority** rather than sold to clients as strategy.

**The design in one paragraph.** SEO-OS is a client-scoped **knowledge base ("Client Brain")** fed by APIs, read by narrowly-scoped **agents**, orchestrated by deterministic **workflows** (n8n), and governed by **human approval gates** proportional to risk. Every recommendation carries evidence, a confidence grade, an effort estimate, and an owner. Everything the client sees passes a human FCMO. Anything that can publish, email, redirect, block crawlers, or spend money never runs unattended.

### Ten design principles

1. **Business outcome first.** Traffic is a diagnostic; pipeline and revenue are outcomes.
2. **Evidence or it didn't happen.** Every claim in a deliverable links to a data pull, a SERP snapshot, or a primary source.
3. **Separate detection from judgment.** Machines detect; humans (or human+AI) interpret and decide.
4. **Score opportunities, don't sort by volume.** (Section 3.4.)
5. **First-party truth beats third-party estimates.** Search Console, GA4, CRM, sales calls, and logs outrank vendor "volume" and "authority" scores.
6. **Autonomy is earned per task, not granted per tool.** Four autonomy levels; irreversible actions never exceed level 2.
7. **Scraped content is untrusted input.** Agents must be robust to prompt injection from the web.
8. **Every agent has an evaluation set.** No agent goes live without a golden-case test.
9. **Learn on purpose.** Hypotheses are logged before execution and closed out after.
10. **Don't oversell the frontier.** AI-search tactics are labeled ESTABLISHED, EMERGING, or EXPERIMENTAL (Section 2.3).

### How status labels are used

| Label | Meaning |
|---|---|
| **CURRENT** | Still broadly applicable as taught |
| **MODERNIZED** | Fundamentally useful, but must be updated |
| **OUTDATED** | Should generally not be used as originally taught |
| **CONTEXTUAL** | Useful only in specific situations |
| **UNCERTAIN** | Needs further validation; do not present to clients as fact |

Confidence notes: where I relied on Google's own documentation I say so; where I relied on secondary reporting or vendor blogs I flag it, and where sources conflict I say so rather than pick a winner.

---