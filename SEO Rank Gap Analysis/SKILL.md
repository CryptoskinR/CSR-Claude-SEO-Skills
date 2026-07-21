---
name: seo-rank-gap-analysis
description: "Diagnoses why a competitor's page outranks the user's own page for a specific target query/keyword — even when the competitor's page looks technically or content-wise weaker. Use this skill whenever the user provides two links (their own page and a competitor's page) that compete for the same topic/keyword and asks why the competitor ranks higher, or how to overtake the competitor — even if the words 'SEO' or 'ranking' are not used explicitly, e.g. 'why is this page beating us?', 'how do I outrank this site?', 'what did this competitor do better?'. Fully general-purpose: works for any industry, any site type (e-commerce, news, content, service, B2B), and any site/content language — always analyze and respond in the language the user is communicating in (or the language of the pages being compared), not any fixed language."
---

# Competitor Rank Gap Analysis

## Purpose

Take the user's own page + a competitor's page that compete for the same query → check technical, content, search-intent, E-E-A-T, and current algorithm-update factors together → produce a specific hypothesis for the rank gap plus prioritized, actionable fixes — not a generic recycled checklist.

This skill is for when the user has a *specific, named* competitor and wants to know why they're behind, not a general site-wide SEO audit without a comparison.

## Language handling

This skill itself is written in English, but it must work for a page or user in **any** language. Always:
- These instructions (SKILL.md) are in English purely so the skill itself is portable and maintainable — that has no bearing on the output language.
- **Always respond in the language the user is writing to you in for this conversation**, regardless of what language the two pages being compared are in, and regardless of this file's language. If the user writes in Persian, respond entirely in Persian (translate all labels, table headers, and section titles below, not just the prose). If they write in English, respond in English. The pages being analyzed may be in a third language entirely (e.g. a Persian-speaking user comparing two English-language pages) — that never changes the response language.
- Still note in the output if the two pages are in different languages from each other, since that itself can be a reason for divergent rankings (e.g. different regional SERPs, hreflang issues) — but this is a factual observation to make in the user's language, not a language switch.

## When NOT to use this

If the user gives only one link, with no specific competitor, and just wants that one page's SEO improved in isolation, this skill doesn't apply — it needs a relative comparison against a real competitor to be meaningful.

## Required inputs

These three are mandatory; if the user hasn't given them, ask before proceeding:

1. The user's own page URL
2. The competitor's page URL (the one that currently outranks them)
3. The target keyword/query this comparison is about — without this, search-intent and SERP analysis is meaningless

Optional inputs (use them if the user already has and provides them; otherwise explicitly ask for them in the output section, since you can't fetch these yourself):

- Screaming Frog output for both pages
- PageSpeed Insight / Core Web Vitals output (lab data, and field data if available) for both pages
- Search Console CTR and position data for the user's own page, for this exact query
- Backlink data (Ahrefs/Semrush/Moz or similar) for both pages — the specific page, not the whole domain

---

## Step 1 — Direct technical/content comparison (via web_fetch)

Fetch both pages with `web_fetch` and extract the following into a side-by-side comparison table:

- Title and meta description — length and match with the target keyword
- Heading structure (H1–H3) and whether the target keyword appears in the H1
- Estimated main-content word count
- Publish/last-updated date (if shown on the page)
- Presence or absence of a named author with a credible bio
- Presence of Schema/Structured Data (search the source for `application/ld+json`; identify the type: Article, Product, FAQ, HowTo, Review, etc.)
- Number of relevant internal links on the page
- Number of images and quality of alt text
- Correctness of canonical tag and meta robots

Note: this is a static-HTML analysis, not a full JavaScript render. If the site is heavily JS-rendered, tell the user explicitly that some client-rendered content may not be visible in this check.

---

## Step 2 — Search intent analysis on the current SERP

Use `web_search` for the target keyword and, without directly quoting search results (per copyright rules), extract:

- The dominant content type among the top results (comprehensive guide, listicle, product page, comparison, video)
- Which special SERP features are active (Featured Snippet, People Also Ask, AI Overview, Video Pack, Local Pack)
- Whether the user's page or the competitor's page matches this dominant pattern more closely

This step is often the most important clue: a page that looks "more complete" or "more technical" frequently underperforms simply because its format doesn't match what Google wants to show for that specific query.

---

## Step 3 — E-E-A-T and real-experience signals

Compare qualitatively (not just a checklist):

- Which page shows evidence of first-hand experience (original photos/media, details that only come from actually using the product/service, proprietary data)
- Which page has clearer, more verifiable sourcing
- Which page is more current relative to recent developments in the topic

---

## Step 4 — Factors you cannot measure directly

Tell the user explicitly that you need these and have no direct tool for them, unless they supply the data:

- Backlink profile of **the specific page** (not the whole domain) on both sides — number of referring domains and their topical relevance, not just a third-party DA/DR score (that score is an estimate, not a direct Google signal)
- Domain/page age — checkable via the Wayback Machine
- The user's own page's real CTR for this query, from Search Console
- Field-data Core Web Vitals (CrUX), not just PageSpeed Insight lab data

---

## Step 5 — Current algorithm-update factors — always include these

Based on major 2026 Google core updates (especially the March 2026 update):

- **Independent per-page evaluation**: overall domain authority no longer automatically "rescues" a weak page — each page is evaluated relatively independently now. So if the competitor's domain is simply better known but this specific page looks weak, that alone isn't a sufficient explanation — dig deeper.
- **Relative/comparative ranking**: Google ranks pages against competing pages for the same query, not in a vacuum. A lower rank doesn't necessarily mean the user's page is "bad" — often it just means the competitor currently offers something this specific page doesn't yet.
- **Site-wide Core Web Vitals aggregation**: if a significant share of the user's site has poor CWV (the LCP threshold has tightened to roughly 2 seconds), even a well-optimized individual page can be dragged down by the site's overall average. Ask the user to check CWV on a sample of other pages on their site too, not just this one.
- **Keyword cannibalization**: check whether the user has several pages on their own site targeting nearly the same topic/query, which may be competing with each other internally and diluting ranking power.
- **AI Overview / AI Mode citation**: with `web_search`, check whether the competitor is being cited in Google's AI-generated summary answers for this query — this is a newer credibility signal and tends to align with the same E-E-A-T signals that drive organic ranking.

---

## Step 6 — Estimate an implicit rank position for each page

Always give a concrete, numbered rank estimate for both pages for the target query — not just a qualitative "the competitor is stronger" verdict. Base it on everything gathered in Steps 1–5: relative domain strength, page-level technical/content quality, publish timing relative to when the story/topic broke (critical for news/trending queries — a multi-day lag behind the first outlets to cover a breaking topic is often a bigger factor than on-page quality), sourcing/E-E-A-T gaps, and SERP intent match.

- Give an estimated rank range for each page (e.g. "positions 1–5" / "position ~20+"), not a single false-precise number.
- Always state the reasoning behind each estimate explicitly — which specific factors from Steps 1–5 drove the estimate up or down.
- Always caveat clearly that this is an inferred estimate, not a measured ranking — you have no rank-tracking tool. The only way to confirm it is the user's own Search Console position data or a rank tracker.
- If you could not fetch one of the two pages directly (robots-blocked, etc.), say so again here and note that the estimate for that side leans more heavily on domain-level and timing signals than on-page evidence — don't present it with false confidence.

---

## Step 7 — Final output

Give the output in chat (not a separate file, unless the user explicitly asks for one), in the user's own language, structured like this:

```
🔎 Comparison: [user's page] vs [competitor's page] for query "[target query]"

📋 Technical/content comparison
| Factor | Your page | Competitor's page |
|---|---|---|
| ... | ... | ... |

🎯 Search intent match
[Explain what format the current SERP is favoring, and which page matches it better]

⭐ E-E-A-T and real-experience signals
[Qualitative comparison]

📍 Estimated rank position (inferred, not measured)
- Your page: ~[range] — because [specific reasons]
- Competitor's page: ~[range] — because [specific reasons]
[Caveat that this is an estimate based on available signals, not real rank-tracking data; confirm with Search Console/rank tracker]

🚧 Data needed for a fuller analysis
[Specific list: page-level backlinks, domain age, real CTR, field-data CWV, etc.]

🧩 Main hypothesis for the rank gap
[Specific and reasoned, not generic]

✅ Recommended actions (prioritized)
1. [Quick win]
2. [Medium-term action]
3. [Structural/long-term action]
```

If multiple queries or competitors are being checked at once, give separate output per case, then call out any shared pattern across them at the end (e.g. the same weak factor recurring everywhere) — that indicates a systemic site issue rather than a single-page problem.

---

## Notes

- Never draw a firm conclusion based solely on a third-party DA/DR score — these are estimates, not a direct Google ranking signal.
- If a page can't be fetched with `web_fetch` (blocked, network error), tell the user and ask them to paste the HTML or a screenshot directly; in that case Step 1 will be more limited.
- This skill complements deeper content editing/scoring tools — it doesn't replace them. Its focus is "why are we behind this specific competitor," not rewriting an article end to end.
