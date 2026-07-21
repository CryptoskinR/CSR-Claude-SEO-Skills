---
name: csr-seo-indexing-diagnosis
description: Diagnoses why WordPress (or any CMS) pages show as "Crawled" in Google Search Console but are not being indexed (Crawled – currently not indexed). Use this whenever the user shares one or more page links or page source and says the page is live, has been crawled, but isn't showing up in Google or isn't indexed — even if they don't say "SEO" or "indexing" explicitly, e.g. "why isn't this page showing up?". Domain-agnostic: works for any site or content niche, not just a specific industry.
---

# Indexing Diagnosis (Crawled – Currently Not Indexed)

## Purpose
Receive one or more page links (or page source/HTML if a link can't be fetched) → run a two-layer check (technical + content quality) → deliver a specific diagnosis with a concrete action, not a generic checklist.

This skill is for the specific case where the user has already confirmed the page:
- is live and accessible
- has been crawled by Google (per Google Search Console)
- but is not indexed / not appearing in search results

If the user isn't sure of the exact status, first ask them to check Google Search Console → Page Indexing → click into the page to confirm the precise label ("Crawled – currently not indexed" vs. "Discovered – currently not indexed" vs. "Excluded by noindex tag" etc.), since the diagnosis and fix differ by status. This skill targets the first case specifically.

---

## Step 1 — Technical Check (rule out simple causes first)

For each link, fetch the page (or ask the user for the page source/`<head>` if fetching isn't possible) and check:

- [ ] **meta robots** — must include `index`, must NOT include `noindex`
- [ ] **canonical tag** — must point to the page's own URL; if it points elsewhere, that *is* the problem (Google is being told to index a different URL instead)
- [ ] **title and meta description** — must exist and be unique, not duplicated from another page on the same site
- [ ] If the site uses an SEO plugin (Yoast, RankMath, All in One SEO, etc.), consider an accidentally-toggled "No Index" setting on that specific post — this is visible directly in the fetched `meta-robots` value

If any of these is broken, stop here and tell the user the problem is technical and specific (e.g., wrong canonical target) — no need to proceed to content-quality analysis.

If everything technical checks out clean (which is the common case for genuine "Crawled – currently not indexed"), proceed to Step 2.

---

## Step 2 — Content Quality Analysis

When Google crawls a page but deliberately doesn't index it, its quality systems have judged the page doesn't clear the value bar. Check these three angles for each page:

### A) Topic saturation / redundancy (the most common cause)
- Is this exact topic already covered, at the same moment, by dozens or hundreds of other sources (official announcements, pricing, release dates, breaking news)?
- Does the content add its own analysis/angle/first-hand experience, or is it essentially a rewrite of an official source or other outlets' reporting?
- For reference/glossary/general-guide pages: is the information so generic and widely documented (e.g. definitions of common terminology already explained identically across dozens of existing pages) that another near-identical copy adds nothing? This type of content needs either a much narrower/more specialized scope, or a genuinely distinctive angle (first-hand examples, localized context, media/audio, a niche the existing coverage doesn't serve).

### B) Sourcing and verifiability (E-E-A-T)
- Find quotes attributed to people or outlets without a link — check whether that named source is actually identifiable and credible, or reads like a fabricated/generic name
- Vague phrases like "rumors suggest," "analysts say" with no specific name are a weak trust signal
- If there's genuine first-person experience in the text (not just a general claim), note it as a strength

### C) Repetition / scale pattern (Scaled Content Abuse)
- Within the page itself: are sections or entries repeated verbatim or near-verbatim (e.g. the same term/fact appearing under two different categories with nearly identical wording)?
- At the site level: is this page one of many with an identical structure/template where only the subject changes?
- Per Google's official Scaled Content Abuse policy, the issue is volume without added value — not whether AI was used to produce it. So the analysis should focus on whether *this specific page* offers enough value to a reader on its own, not on how it was produced.

---

## Step 3 — Output

For each link, give exactly this format (in the conversation, not as a separate deliverable file — this is a diagnostic answer, not a document):

```
[Page name/URL]

✅ Technical: [Clean / Specific issue — name it precisely]

📊 Likely reason(s) it isn't indexed:
1. [Primary reason, with a concrete example from the actual text]
2. [Secondary reason, if applicable]

💡 Suggested action: [Specific and actionable, not generic]
```

After analyzing each page individually, if more than one page was reviewed and they share a common pattern (e.g. both compete with widely-duplicated coverage), call that out separately at the end — it signals a systemic issue with the type of content being produced, not a one-off page problem.

Never suggest "Request Indexing" in Search Console before the user has actually made a substantive content change — remind them that requesting reindexing without a real content change is usually ineffective.

---

## Notes

- If a URL can't be fetched (blocked, network error, paywalled), tell the user and ask them to paste the raw HTML/page source directly. In that case, Step 1 (technical check via `<head>`) can't be completed, and you should say explicitly that only the content-quality analysis is possible.
- This skill pairs with `seo-content-editor` but serves a different purpose: `seo-content-editor` does a full rewrite/scoring pass on a single article (three-part output: report + change log + revised article). This skill diagnoses *why an already-published page isn't indexed* — its output is shorter and focused purely on root-cause diagnosis, not a full rewrite.
