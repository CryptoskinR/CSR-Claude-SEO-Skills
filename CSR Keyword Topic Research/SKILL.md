---
name: csr-keyword-topic-research
description: "Given a URL (a homepage, an articles/blog listing page, or any specific page the user points to), research and recommend a target keyword plus a timely, expandable topic angle for a new piece of content. Use this skill whenever the user asks for keyword research, "what should I write about", topic ideas, content ideas tied to a site, or SEO keyword suggestions — even if they only paste a link and say something like "find me something good to write about" or "کیورد ریسرچ کن". Fully general-purpose: works for any site, niche, industry, or language — do not assume a specific site, topic, or language. Combines evergreen keyword research (intent, volume/competition signals, SERP fit) with same-day trending-angle research (news, trends, events) so the output keyword is both search-worthy and freshly relevant on the day the skill runs."
---

# Keyword + Topic Research

## What this skill produces

Given one URL, this skill outputs:
1. A short list (2–3) of candidate target keywords, each with reasoning
2. One recommended keyword (the pick), with a topic/angle to write about *today* that expands it
3. Claude's own suggestions or caveats for improving the pick further

This is a conversational deliverable (reply in chat), not a file — unless the user asks for a file.

## Ground rules

- **No fabricated numbers.** Never invent search volume, keyword difficulty scores, or CPC numbers. Real numbers only come from a connected keyword-data tool (see Step 2a). Without one, use `web_search` to build *directional* signals instead (see Step 3) and say so plainly in the output — e.g. "appears to be a lower-competition, steady-interest term" rather than "1,200 searches/month, KD 18".
- **Always disclose what you could and couldn't do.** If any step had to fall back to an estimate instead of real data because a relevant tool wasn't connected, say so explicitly in the final output (see Step 6) — don't silently present an estimate as if it were verified data.
- **Match the site's language and tone**, detected from the fetched page — never default to English or assume Persian. If the page is in Persian, respond in Persian; if English, respond in English; etc.
- **Stay general.** Nothing in this skill should assume a specific niche, industry, or site. The steps below apply the same way to a fragrance blog, a B2B SaaS site, a recipe site, or a news outlet.
- **Today's date matters.** Step 5 (trending angle) is time-sensitive by design — always search freshly, never reuse a trending angle from earlier in the conversation or from training knowledge.

## Step 0 — Get the input

Ask for a URL if the user hasn't given one (homepage, an articles/blog listing page, or any specific page). One link is enough to start. If the user gives multiple links or a whole site's worth of context, that's fine too — just make sure you have at least one concrete URL before proceeding.

## Step 1 — Understand the source page

`web_fetch` the URL. From it, extract:

- **Niche/domain**: what is this site actually about, at a specific level (not just "gaming" but "PC/console game reviews and guides", not just "fragrance" but "niche/designer fragrance reviews for a Persian-speaking audience")
- **Audience & tone**: who reads this, how formal/casual is the writing, what depth level (beginner vs. expert)
- **Language**: the language to use for the final output
- **Content type/format patterns**: if this is a listing/archive page, skim titles of recent articles — this tells you both the site's usual content shape (reviews? guides? news? listicles?) and what's *already been covered*, which you'll need in Step 6 to avoid recommending a duplicate topic
- **Monetization/goal signals** if visible (ads, affiliate links, products, newsletter signup) — useful context for whether informational or commercial-intent keywords fit better

If the page fails to fetch (blocked, error), tell the user and ask them to paste the page content or try a different link instead of guessing at the niche.

## Step 2 — Generate seed keywords

Based on Step 1, brainstorm a first batch of candidate seed keywords/topics that fit the site's niche and audience. Then expand each seed using `web_search`:

- Search the seed term itself and note autocomplete-style related phrasing that shows up in the results
- Search variants like `"[seed] چیست"` / `"what is [seed]"`, `"[seed] vs"`, `"best [seed]"` — whatever phrasing fits the niche and language — to surface People-Also-Ask-style question variants
- Look at what related searches or "people also search for" content appears in the result set

Build a working list of 8–15 candidate keyword phrases before narrowing down.

## Step 2a — Check for a real keyword-data tool before estimating

Before falling back to search-based estimation, check whether a real keyword-data source is available:

- If a keyword-research tool (e.g. Semrush, Ahrefs, or similar) is already connected and usable, use it now on the candidate list from Step 2 to pull real search volume, keyword difficulty, and trend data. This replaces the directional estimation in Step 3 with actual numbers — use the real data instead of guessing.
- If nothing is connected yet, call `search_mcp_registry` with keywords like `["SEO", "keyword research", "search volume"]`. If it returns relevant connectors, call `suggest_connectors` and let the user pick — don't just silently proceed. If the user picks one, use it for this and future steps in the same run. If the user declines or nothing relevant is found, continue with the estimation approach in Step 3, but remember this gap for Step 6.
- Don't block the whole research on getting a connector set up. If the user doesn't want to connect anything right now, proceed with the `web_search`-based estimation so they still get a usable answer today — just be upfront about it in the final output.

## Step 3 — Classify intent and estimate competition (directional, not exact)

For each candidate, classify search intent: informational, commercial-investigation, transactional, or navigational. Drop anything navigational (branded searches for someone else's product/site aren't useful content targets here) unless the user's goal is explicitly comparison content.

If Step 2a found a connected keyword-data tool, use its numbers here instead of estimating — skip straight to intent classification plus the real volume/difficulty/trend data it returned. The rest of this step is the fallback for when no such tool is available: for a directional competition read, search each remaining candidate and note:
- Are the top results dominated by large, high-authority sites, or is there a mix including smaller/independent sites? (More of the latter = more realistic to compete.)
- Are the top results well-written and specific and comprehensive, or are they thin/outdated/generic? (Thin or dated top results = opportunity.)
- What content format wins (listicle, guide, review, news piece, product page)? This tells you what format to write if you target this keyword — matching the dominant format matters more than keyword density.

Narrow the list to 4–6 promising candidates.

## Step 4 — Cross-check against what the site already covers

Compare the shortlist against the article titles/topics you saw in Step 1 (if the URL was a listing page) or against what you can find by searching `site:<domain>` for the candidate topic. Drop or reshape any candidate that would duplicate/cannibalize an existing page, unless the intent is explicitly to update/refresh that older piece — flag that distinction if it comes up.

## Step 5 — Find today's trending angle

This is what turns a good evergreen keyword into a piece worth publishing *today* specifically. For the 2–3 strongest remaining keyword candidates:

- `web_search` for current news, launches, events, or discussions in that specific sub-topic (not just the general niche) — using the actual current date, not a remembered one
- Check whether anything genuinely newsworthy or freshly relevant intersects with the keyword: a release, an update, a debate, a seasonal moment, an anniversary, a data point just published, etc.
- Apply a real-connection filter: if tying the keyword to today's trend feels forced, don't force it — a keyword with no natural news hook can still be recommended as a solid evergreen piece, just say so explicitly instead of manufacturing a fake news angle.
- If a genuine hook exists, note the specific angle it enables (a clear explainer, a comparison, a data-backed take, an opinion/analysis extension) — not just "write about X because it's trending," but *what new value the site's content would add* beyond repeating the news itself.

## Step 6 — Pick and package the output

Present:

1. **The shortlist** (2–3 keywords) — one line each: the keyword, its intent, and why it made the cut
2. **The recommendation** — the single best pick, with:
   - The keyword/target phrase
   - Search intent
   - Why it fits this specific site/audience (tie back to Step 1)
   - The competitive read from Step 3 (directional, no fake numbers)
   - Today's angle from Step 5 — what specifically to write about right now, and why that timing matters (or, if there's no trending hook, say it's a strong evergreen pick instead and explain why now is still fine)
   - Recommended content format (matches what's winning in the SERP from Step 3)
3. **Claude's own suggestions/caveats** — anything Claude would flag: a risk (topic might date quickly), a stronger long-tail variant worth considering instead, or a related keyword worth targeting in a follow-up piece.
4. **Data-gap disclosure (only if Step 2a didn't find a connected tool)** — state plainly which step ran on estimates instead of real data (e.g. "search volume and difficulty are directional estimates from search results, not verified numbers"), and name the specific tool that would close the gap (e.g. "connecting Semrush or Ahrefs would let me pull real volume/difficulty/trend data instead of estimating it"). Don't bury this in a footnote — it belongs in the main answer since it affects how much weight the user should put on the recommendation.

Keep the whole output conversational and scannable — headers/bullets are fine, but this is a chat answer, not a formatted report artifact, unless the user asks to save it as a file.

## Notes

- If the user gives feedback pushing back on the pick (e.g. "we already tried that angle" or "audience won't care about that"), don't just re-search blindly — treat that as a new constraint and re-run Steps 3–6 with it factored in.
- If the site is multi-topic (e.g. covers more than one niche or vertical, as in the case that motivated this skill), ask which vertical the user wants this round of research for if it's not obvious from the URL, rather than mixing signals from both.
- This skill is deliberately generic — do not hardcode niche-specific tool names, competitor names, or language assumptions into it when reusing or extending it for a specific site. Site-specific knowledge belongs in that site's own project/reference files, not in this skill.
