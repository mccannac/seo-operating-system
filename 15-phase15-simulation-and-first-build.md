# PHASE 15: Simulated client run

## The fictional client

**Meridian Advisory Group** — a $10M/year regional wealth-management and financial-advisory firm headquartered in one metro market, currently serving clients primarily in that home market, planning to expand its advisory practice into three new metropolitan markets over the next 18 months. Fee-based model, high LTV (~$8,500/year per client household), long sales cycle (4–7 months from first contact to signed engagement), heavily relationship- and trust-driven, YMYL-adjacent (financial advice) which raises the compliance bar throughout.

## Stage-by-stage information flow

### Intake

**In:** Signed engagement; domain; CMS (WordPress); no existing GSC/GA4 access set up; three target expansion metros named by the CEO; compliance team contact identified as a required reviewer for any published claim.

**System does:** Pre-call crawl finds a thin, brochure-style site with no blog, no location pages, and a GBP listing only for the home market. Brand SERP snapshot shows the firm ranks for its own name but nothing else. Structuring Agent drafts the client profile from the discovery interview transcript, flagging `ymyl_flag: true` and populating `markets: [{home_metro, priority: current}, {metro_2, priority: planned_q3}, {metro_3, priority: planned_q4}, {metro_4, priority: planned_q2_next_year}]`.

**Human checkpoint:** FCMO confirms viability — **Go with conditions**: compliance review required on all published content; no expansion-market content until the firm has at least a licensed presence or clear service-area legitimacy in that state (a real regulatory constraint for financial advisors, not a generic caution).

### Audit

**In:** Full crawl of ~40 pages; CrUX shows mobile LCP failing on the homepage; no schema present; robots.txt blocks nothing unusual; sitemap is stale (references pages removed 2 years ago).

**System does:** Technical Agent produces a ranked issue register: stale sitemap (high certainty, low effort), missing Organization/FinancialService schema (medium certainty, low effort), mobile LCP failure on a hero video background (high certainty, medium effort — needs dev).

**Human checkpoint:** Sampled review confirms priorities; dev ticket created for the LCP fix (Human decision required on remediation design, per Section 7).

### Search & Keyword Intelligence

**In:** Seeds from client offers (retirement planning, estate planning, tax-efficient investing) plus the three expansion metros.

**System does:** Expansion produces clusters like "fee-only financial advisor [metro_2]" and "retirement planning [home_metro]." The **geographic-fit gate (Section 6.3)** automatically excludes all metro_2/metro_3/metro_4 clusters from scoring except a small "brand-awareness" set the FCMO explicitly re-admits, because the firm has no licensed presence there yet — this is the gate working as designed, not a limitation. Home-market clusters score normally; "retirement planning [home_metro]" scores high (BV=5, WIN=3, DCF=high) because the firm has 15 years of real client outcomes to draw on (GAIN=5).

**Human checkpoint:** FCMO reviews the top 50, explicitly overrides the gate for a small set of brand-building, non-locational content ("how fee-only advisors are compensated," an evergreen educational piece with no location claim) to start earning topical relevance ahead of the physical expansion.

### Competitive Intelligence

**In:** Three business competitors named by the CEO; SERP competitors discovered independently include two national robo-advisor brands that rank on "retirement planning" nationally but aren't true business competitors for a high-touch regional practice.

**System does:** Competitor Intelligence Agent classifies the national robo-advisors as SERP competitors only, not business competitors, and flags that Meridian's real differentiation (in-person relationship model) is not competing on the same axis as the SERP suggests — a nuance a keyword-volume-only approach would miss entirely.

**Human checkpoint:** FCMO confirms this reading and decides not to chase the robo-advisor-dominated head terms, redirecting effort to consultative, locally-flavored content instead.

### Opportunity Scoring & Prioritization

**Out:** A ranked backlog where the top 10 items are entirely home-market and brand-building content plus the technical fixes — **zero expansion-market content**, correctly, because the geographic gate and the compliance flag both suppress it until Stage 1 expansion (a state registration, a local office) actually happens.

### Strategy & Roadmap

**Out:** A 90-day roadmap: technical fixes (weeks 1–3), four home-market content pieces built on real advisor case studies with compliance review (weeks 2–10), schema implementation (week 4), and a **standing hypothesis**: "When Meridian receives state registration in metro_2 (expected Q3), re-run keyword scoring with that market's geographic gate lifted, and have three location-specific content pieces ready to publish within 2 weeks of registration" — the system is explicitly primed for the expansion event rather than guessing at its timing.

### Execution

**Out:** Content briefs generated for the four home-market pieces, each requiring named-advisor SME input and **compliance sign-off** before publication (Section 7: legal/compliance-sensitive content is Human-only). Internal Linking Agent proposes links from the new content to existing service pages. Structured Data Agent drafts FinancialService and Person (advisor) schema — the QA Agent explicitly checks these against the archive's own Phase 2 finding that FAQ schema no longer produces visible results, so no FAQ markup is proposed for a "rank boost."

### Monitoring

**Out:** Baseline established at Stage 1 measurement plan; monthly cadence begins. Three months in, the Analytics Agent flags a genuine anomaly: a sharp drop in home-market brand impressions. Root-cause candidates: (1) a Google core update (dates checked against the update calendar — none logged that week), (2) a tracking break (tags_firing confirmed healthy), (3) a GBP suspension (confirmed: the listing was flagged for a name mismatch after a rebrand). **The system correctly avoids blaming "Google" and surfaces the actual, boring, fixable cause.**

### Reporting

**Out:** The operational digest shows the GBP issue and its fix status to the practitioner team weekly. The strategic report to Meridian's internal marketing coordinator explains the GBP incident and its resolution. The executive one-pager to the CEO states, in plain language: "A listing data mismatch temporarily reduced our visibility in [home_metro]; it's now corrected, and we expect recovery within 2–4 weeks based on typical GBP re-indexing timelines" — six questions answered, no jargon, one page.

## Where the system succeeds

- The geographic-fit gate prevents wasted effort on markets the firm can't legally or practically serve yet — precisely the kind of business-context judgment a volume-only keyword tool would miss.
- The three-competitor-set model (Section 3.5) correctly separates true business competitors from SERP-only competitors, avoiding a strategy built around the wrong rivals.
- The anomaly diagnosis correctly resists the reflexive "algorithm update" explanation and finds the real, mundane cause.
- The compliance gate (YMYL flag) correctly routes every piece of content through a human/expert review path with no automated bypass.

## Where human intervention is necessary (and the system does not pretend otherwise)

- **The Go/Go-with-conditions decision at intake** required the FCMO's judgment about a real regulatory constraint (state licensing) that no data pull could have surfaced — this had to come from the discovery interview.
- **The override of the geographic gate** for brand-building content was a genuine strategic call, not a scoring outcome — the model presented the option; a human made the trade-off.
- **Every piece of content required named-advisor SME input and compliance sign-off** — the system accelerated research and drafting, but the actual claims about financial outcomes came from licensed humans, as they must.
- **The GBP incident resolution** (correcting the listing, communicating with Google, if needed) was executed by a human; the system's contribution was fast, correct detection, not the fix itself.
- **The decision to re-engage the expansion-market keyword clusters** on the Q3 registration event is logged as a standing hypothesis precisely because it depends on a real-world regulatory milestone the system cannot itself trigger or verify — a human confirms registration is complete before the gate lifts.

---

# Recommended first build

**Build Stage 1 (Minimum Viable SEO OS) for exactly one real client, using no code beyond a single simple n8n workflow, before writing a single line of the agent layer.**

Concretely, in order:

1. **Set up the client-intake schema in Airtable** (Section 3.1's minimum schema, Section 8.2's Client entity) — this alone forces the disciplined thinking the rest of the system depends on, and costs a day.
2. **Connect GSC and GA4 to Google Sheets** via n8n's scheduled HTTP/API nodes — one simple workflow, no database yet.
3. **Build the opportunity-scoring formula (Section 6.2) as a literal spreadsheet**, scored manually by a human for the first cycle, so the FCMO internalizes what "good" evidence for BV/GAIN/STRAT looks like before any agent is asked to approximate that judgment.
4. **Run one full onboarding cycle by hand-in-the-loop with the workflow's help**, not the agent's — this produces the first golden test cases (Section 15/3.9) that Stage 3's agents will later be evaluated against, which is the single most important artifact for making the eventual agent layer trustworthy rather than merely plausible.

**Why this and not something more ambitious:** the constrained-scoring protocol, the QA agent, and the entire human-in-the-loop model all depend on having a real, human-produced standard of "correct" to check AI output against. Building the agent layer before that standard exists (skipping to Stage 3) is the single most common way these systems fail — they end up automating a process nobody has actually validated yet. The n8n workflows, the database schema, and the agent prompts in this document are all ready to build on top of that foundation the moment it exists.
