---
name: csr-news-article-writer
description: >-
  Generates a publish-ready news article from either a link/links to a specific news story, or just a topic with no link. Use this whenever the user wants a news article, blog news post, or press-style write-up produced from a source link or a bare topic — even if they don't say "news article" explicitly, e.g. "write something about this announcement", "turn this link into a post", "write an article about [event/topic]". Niche-agnostic — works for tech, business, sports, entertainment, science, or any other beat. Applies SEO and editorial-quality rules (sourcing discipline, AI-pattern removal, structure) while writing, not as a separate edit pass.
---

# News Article Writer

## Purpose

Take one of two inputs:
- (a) one or more links to a specific news story, or
- (b) just a topic/event, with no link

...and produce a complete, publish-ready news article, in a reporting-analysis tone with disciplined sourcing, plus a short editorial report (sources used, a quality score, and any unverified claims).

This skill is deliberately generic: it makes no assumptions about niche, industry, site, brand, or CMS. Anything specific to a particular publication (house style, category taxonomy, internal linking rules, a preferred phrase list) belongs in that site's own reference material, not in this skill.

## Output language

Write the final article in the same language the user is using to talk to you in this conversation — **not** necessarily the language of the source links. If the user explicitly asks for a different output language (e.g. "write this in English" while chatting in French), use that language instead. When in doubt, default to the conversation's language.

---

## Step 1 — Research

### Case A: link(s) given
`web_fetch` each link. From each, extract:
- The core facts and claims
- The name of the original/primary source outlet and the date
- Direct quotes, with the speaker's name and title
- Precise numbers and statistics
- Proper nouns (people, organizations, products) with correct spelling

If the story is fast-moving or details may have changed since the linked page was published, run a follow-up `web_search` to check for anything more recent.

### Case B: topic only, no link
- Use `web_search` to find credible sources. Prefer established, subject-matter outlets over unverified aggregators or forums — what counts as "established" depends on the beat (a trade publication for tech, a wire service or major outlet for general news, a recognized specialist site for a hobby/niche topic).
- Fetch and cross-check at least 2–4 sources before writing.
- **If credible sources conflict, or a claim comes from only one unconfirmed source:**
  - Still write the article, but with an appropriately cautious tone (e.g. "sources describe," "according to leaked/unofficial reports," rather than stating it as settled fact).
  - Flag each unverified claim with `[UNVERIFIED]`.
  - In the final report (Step 6), count these and, if you know of a plausible source that could confirm or deny the claim but haven't fetched it, name it as a suggestion — without deciding on your own to chase it down or to withhold the article.

## Step 2 — Identify the story's shape

Most news pieces fall into one of a few recognizable shapes. Identifying the shape up front determines the article's structure and how it should end:

| Shape | Example | Trait | Typical ending |
|---|---|---|---|
| Crisis / unconfirmed allegation | Leadership scandal, unconfirmed shutdown, internal turmoil | Story is developing, claims are unverified | An open, forward-looking closing section — no forced neat wrap-up |
| Data / analysis | Sales figures, performance stats, a market report | Verified, specific numbers | A forward-looking section (doesn't need a literal "Conclusion" header) |
| Explainer / practical guide | Pricing details, release logistics, how-to-prepare pieces | Fact-dense, actionable for the reader | A closing section that pulls the key facts together |
| Ongoing project / development update | A product roadmap update, a long-running initiative with periodic news | No confirmed end-state yet, prior coverage exists | A status-and-outlook close, explicit about what's still unknown (e.g. no confirmed date) |

If a story doesn't cleanly fit one row, blend approaches using judgment — this table is a guide, not a rigid template.

## Step 3 — Design the article's skeleton

Before drafting in full:

- **H1**: include the primary keyword/subject. **Maximum 66 characters including spaces.** Count it before finalizing; shorten if it runs long.
- **Opening paragraph**: no throat-clearing or generic scene-setting. Lead directly with the core fact plus the named primary source. This paragraph should, on its own, answer "what happened?" (useful for search snippets and AI answer boxes).
- **3–5 H2 sections**, each a distinct sub-topic (not just a timeline split). Common angles: background/why it happened, technical or financial detail, reactions from key people, points of dispute or tension, implications/outlook.
- **Closing section**: shaped by the story type identified in Step 2.

## Step 4 — Draft (apply editorial rules while writing, not after)

Apply these rules live, as you write — don't plan to "clean it up" in a later pass:

**Sourcing (no external links in body text):**
- "According to [outlet name], [month/year]"
- "According to [outlet name], reported by [journalist], [date]"
- "As claimed by [platform/individual name]"
- Never use a vague source ("sources say," "experts note," "reports suggest") — always name the specific outlet, platform, or person.

**Proper nouns:** on first mention, give the full/correct form. If translating or transliterating for a different-language output, give the original form in parentheses on first mention.

**Quotes:** always introduce with the speaker's full name and role/title, never left unattributed.

**Numbers:** precise, internally consistent (a common failure mode is a total that doesn't match the components listed elsewhere in the piece) — double-check arithmetic.

**Paragraph and sentence length:** max ~150 words per paragraph; break up sentences over ~40 words.

**Stylistic bans (universal AI-writing tells to avoid):**
- No generic scene-setting opener ("In today's fast-paced world of X…", "The world of X is constantly evolving…")
- No "In conclusion" or "Final thoughts" as a closing header — use a specific, content-matched header, or none
- No filler transition padding ("It is important to note that…", "It's worth mentioning that…", "Let's dive into…", "delve into")
- No manufactured rhetorical questions used as section transitions ("But what does this mean for the future?") unless the section genuinely poses an open question the story leaves unanswered
- No restating the same point across multiple paragraphs in different words
- No closing paragraph that's just a compressed re-summary of everything already said
- Avoid overused intensifiers ("groundbreaking," "game-changing," "unprecedented," "staggering") unless the fact actually earns the word — prefer a concrete detail instead

**Tone:** reporting-plus-light-analysis. A brief first-person or editorial aside (one or two sentences, not more) is fine where it naturally fits — e.g. a short comparison or a reaction to a striking number — but the piece should not read as an opinion column.

**Target length:** roughly 600–1,100 words, scaled to how much substance the story actually has — don't pad a thin story to hit a word count.

**Images:** mark suggested image placement with a short inline comment (e.g. `<!-- suggested image: description -->`) between sections; this skill does not generate or place actual images.

## Step 5 — Self-check before delivering

Before finalizing, check the draft against Step 4's rules: Are AI-writing tells removed? Is every claim attributed to a named source? Does the H1/H2 structure make sense? Does the opening paragraph directly answer the core question? Are any overlong sentences/paragraphs broken up? Is the H1 within 66 characters?

## Step 6 — Final output

Deliver in exactly this order:

```
═══════════════════════════════════════
ARTICLE
═══════════════════════════════════════

[Full article — H1 + body + closing section]

═══════════════════════════════════════
SUGGESTED METADATA
═══════════════════════════════════════

Meta Title: [max 66 characters including spaces, includes the primary keyword]
Meta Description: [max 130 characters, a genuine one-line summary, not clickbait — count characters before finalizing]

═══════════════════════════════════════
EDITORIAL REPORT
═══════════════════════════════════════

📚 Sources used:
- [source name] — [date] — [role: primary/corroborating/additional angle]
- ...

📊 Quality score: [X/100], scored against Step 4's rules
(AI-writing patterns removed: X/25 — Sourcing/attribution: X/25 — Structure: X/25 — Content quality: X/25)

⚠️ Unverified claims: [count]
1. [claim] ← [why it's unverified] ← [a plausible source to check next, if you know of one]
2. ...
(If none: "No unverified claims in this article.")
```

---

## Warnings

⚠️ If the story or any detail may postdate your reliable knowledge, verify current status with `web_search` rather than assuming older information still holds.

⚠️ Never invent a fact that wasn't in a source, even to fill out a thin section. If there isn't enough material, write a shorter section — or drop it — rather than guessing.

⚠️ This skill produces a draft article and its metadata. It does not know a specific publication's house style, category taxonomy, or internal linking conventions — if the user has those, ask for them or apply whatever they've already told you in this conversation.
