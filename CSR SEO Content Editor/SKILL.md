---
name: csr-seo-content-editor
description: Edits and optimizes articles for SEO and Google ranking performance. Use whenever the user provides an article for review, editing, SEO improvement, content-quality checking, or article analysis — even if the words "SEO" or "skill" aren't mentioned. Works across any content niche or domain (gaming, fragrance, finance, health, travel, tech, food, legal, etc.) by automatically detecting the domain from the text and applying the appropriate evaluation criteria — no fixed domain list required. Includes a check for uniform sentence/paragraph rhythm (a subtle AI-writing tell) and fixes it with targeted variance edits.
---

# SEO Content Editor

## Purpose
Take an article → produce three integrated outputs:
1. Analytical report
2. Change log
3. Revised article

---

## Step 1 — Detect Domain & Intent

Before anything else, determine directly from the article's own content:

- **Domain/niche**: infer it from the text itself — do not rely on a preset list (gaming, fragrance, finance, health, travel, tech, food, legal, real estate, education, etc. are all in scope). If the article spans more than one domain, name the primary one.
- **Content type**: news / guide / analysis / comparison / tutorial / listicle / reference
- **Search intent**: informational / navigational / commercial / transactional

These determine the tone and evaluation criteria for everything below, including which domain-specific rigor checks apply in Section E.

---

## Step 2 — Analyze With Checklist

### Section A — AI Patterns (must be removed or rewritten)
Flag every instance of:
- [ ] Generic opening line: "The world of X has always been full of Y"
- [ ] "Final Thoughts" used as the closing section heading
- [ ] "The short answer is..." or "The answer is a definitive yes/no"
- [ ] "In this in-depth analysis", "As we've explored throughout this article"
- [ ] The same idea repeated with different phrasing across 3+ paragraphs
- [ ] Unnecessary/forced metaphors ("the game world is a metaphor for a shell")
- [ ] A final paragraph that just re-summarizes the whole article
- [ ] **Uniform sentence-length rhythm** (see "Sentence & Paragraph Rhythm Variance" below — check this explicitly, it's easy to miss on a normal read-through)

### Section A-1 — Sentence & Paragraph Rhythm Variance (a subtle but strong AI tell)

Even when every sentence is factually correct and well-written, LLM-generated prose tends to produce sentences — and paragraphs — that cluster tightly around a similar length (word/character count). Most sentences in a paragraph land in a narrow band (e.g. 15–25 words), with few or no very short (4–8 word) punchy sentences and few or no longer, more complex compound sentences. The same flattening often shows up one level up: paragraphs that are all roughly the same length, in the same 3–5 sentence shape, one after another. Human writers naturally vary this rhythm — a short declarative sentence for emphasis, then a longer one that unpacks it; a two-sentence paragraph right after a dense one — and that variance itself is part of what reads as "written by a person."

**How to detect it (Step 2):**
- For each paragraph, roughly estimate words per sentence — exact counting isn't necessary, a quick eyeball pass is enough.
- Flag any paragraph where every sentence clusters in a narrow band (e.g. all between 15–25 words, none under 10 or over 35) — the flat rhythm itself is the signal, not any single sentence's length.
- Zoom out one level: flag stretches of the article where consecutive paragraphs are all a similar length and sentence count, with no short (1–2 sentence) or long (6+ sentence) paragraph breaking the pattern.
- This is a distinct check from "sentences over 40 words" (Section D) — a paragraph can pass that rule and still fail this one if every sentence is a suspiciously similar medium length.

**How to fix it (Step 3):**
- Do NOT rewrite every sentence — that defeats "minimum change, maximum impact." In each flagged paragraph, make 1–2 targeted rhythm changes: split one longer sentence into a short punchy one plus a follow-up, or merge two adjacent short sentences into one longer one with a semicolon or conjunction — whichever restores contrast with the paragraph's neighbors.
- At the paragraph level, vary opening-sentence length across consecutive paragraphs, and where the article allows it, let at least one paragraph run short (1–2 sentences) for emphasis rather than defaulting to a uniform 3–5 sentence block throughout.
- Prefer concentrating changes where the flattening is worst rather than spreading small tweaks evenly across the whole article.
- Log each rhythm change in the change log under its own line item, same as any other edit, with Reason: "sentence/paragraph rhythm uniformity."
- Add a tally line to the Summary of Changes: `Sentences/paragraphs rebalanced for rhythm: [count]`.

### Section B — E-E-A-T
- [ ] Is the author identified?
- [ ] Is there genuine first-person experience? ("we tested this", "in our experience")
- [ ] Are sources named specifically (without necessarily linking — but name + date)?
- [ ] Are numeric/statistical claims accurate and internally consistent (no arithmetic errors)?

**No-link sourcing format** (use when the platform/publication doesn't want outbound links):
- "According to [named source]'s report, [month/year]"
- "Based on data from [named company/publication] covering [event/period]"
- "Based on [named credible study or journal in the field]"

⚠️ Never cite a source generically ("according to reputable outlets," "analysts say") — it must be a specific, ideally independently verifiable name. An unverifiable or unfamiliar named source is a trust *risk*, not a trust signal — flag it rather than treating the citation as automatically credible.

### Section C — SEO Structure
- [ ] H1: a single title containing the primary keyword
- [ ] H2s: logical, covering the main subtopics
- [ ] First paragraph: answers the core question directly (helps with AI Overviews / featured snippets)
- [ ] Paragraph length: max ~150 words
- [ ] No idea stated more than once

### Section D — Content Quality
- [ ] Is the information accurate and verifiable?
- [ ] Does the article add anything genuinely new relative to other coverage of the same topic, or is it a rehash of an official announcement / other outlets' reporting?
- [ ] Are there overly long sentences (40+ words) that should be split?
- [ ] Are AI-clichéd intensifiers overused ("crucial", "breathtaking", "ruthless", "game-changing", etc.)?

### Section E — Domain-Specific Rigor (auto-adapted, no fixed list)
Once the domain is identified in Step 1, reason about what a knowledgeable reader in *that* field would actually check, rather than applying a generic pass. Examples of the kind of rigor to apply once the domain is known:
- **Proper nouns** (products, studios, brands, people, institutions, place names) — verify accuracy and consistent spelling
- **Numeric claims** (prices, sales figures, statistics, dates, measurements) — check internal consistency and flag likely calculation errors
- **Domain jargon** — don't localize/translate specialized terms that are standard as-is in that field (e.g. game/console terminology, chemical/perfumery compound names, financial instrument names, medical terminology)
- **Sourcing convention appropriate to the domain** — e.g. weekly sales-chart citations for gaming, named journal/compound citations for science or fragrance, regulator/filing citations for finance, clinical-guideline citations for health, statute/case citations for legal
- **Regulatory caution** — for health, legal, or financial claims, flag anything requiring professional review instead of confidently rewriting it as fact

---

## Step 3 — Produce Integrated Output

Output in exactly this structure:

```
═══════════════════════════════════════
PART 1: ANALYTICAL REPORT
═══════════════════════════════════════

📋 Article Profile
- Domain: [auto-detected]
- Type: [news/guide/analysis/comparison/tutorial/...]
- Search Intent: [informational/navigational/commercial/transactional]
- Word count: [approx.]

📊 Overall Score: [X/100]

Scored across 4 criteria (25 points each):
- AI Patterns: [X/25] — [brief note; flag here if sentence/paragraph rhythm was uniform]
- E-E-A-T: [X/25] — [brief note]
- SEO Structure: [X/25] — [brief note]
- Content Quality: [X/25] — [brief note]

⚠️ Critical Issues (must fix):
1. [issue] ← [brief explanation]
2. ...

💡 Suggested Improvements:
1. [note]
2. ...

✅ Strengths:
1. [strength]
2. ...

═══════════════════════════════════════
PART 2: CHANGE LOG
═══════════════════════════════════════

[#]. [Type of change]
📍 Location: [section heading or start of sentence]
❌ Before: "[original text]"
✅ After: "[revised text]"
🔍 Reason: [one-line explanation]

[List changes in order, start to end of the article]

Summary of Changes:
- AI patterns removed: [count]
- Sources added/clarified: [count]
- Paragraphs merged/removed: [count]
- Sentences rewritten: [count]
- Sentences/paragraphs rebalanced for rhythm: [count]

═══════════════════════════════════════
PART 3: REVISED ARTICLE
═══════════════════════════════════════

[Full revised article — no additional commentary]
```

---

## Editing Rules

### What to change:
1. Generic closing heading ("Final Thoughts") → a specific summary heading, or remove it
2. Clichéd opening sentence → direct entry into the topic, or a direct answer to the core question
3. Vague/generic sourcing → named sourcing (with or without links, per the platform's policy)
4. Repetitive paragraphs → merge or cut
5. Sentences over ~40 words → split into two
6. Overused AI-style intensifiers → replace with something more specific/concrete
7. Arithmetic/factual inconsistencies → correct and log the change
8. Uniform sentence- or paragraph-length rhythm → apply 1–2 targeted split/merge changes per flagged spot to restore natural variance (see Section A-1) — don't rewrite the whole paragraph for this alone

### What NOT to change:
1. Correct, accurate technical/specialized information
2. Overall structure and section order (unless there's a clear SEO reason to change it)
3. The author's tone and voice
4. Domain-specific jargon and proper nouns
5. Never add external links unless the user's platform explicitly wants them

### Editing constraints:
- Aim for minimum change with maximum impact
- If a sentence isn't broken, leave it alone
- You cannot fabricate first-person experience that isn't in the source — note in the report that the author should consider adding it, rather than inventing it

---

## Warnings

⚠️ If you find a factual claim you're not confident about, flag it in the analytical report and mark it **[needs verification]** in the revised article — don't silently "correct" it.

⚠️ If the article references dates or events beyond your reliable knowledge cutoff, leave them unchanged and note in the analytical report that they need the author's verification.
