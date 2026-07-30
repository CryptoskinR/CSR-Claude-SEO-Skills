---
name: csr-analysis-review-writer
description: Writes a complete analysis/review-style article on any topic and in any language, given just a topic and a category from the user (no link or source required up front). Fully general-purpose and domain-agnostic — works for games, tech, finance, consumer products, or anything else. Use this skill whenever the user gives a topic and asks for an "analysis," "review," "deep dive," or an article in an analytical style (as opposed to a plain news writeup) — even if the words "analysis" or "skill" are never said, e.g. "write me an article about X, category: review." Always respond to the user and write the article in the same language the user made the request in, using prose and conventions that read naturally to a native speaker of that language — never a literal, translated-sounding style.
---

# Analysis / Review Article Writer (general-purpose, domain-agnostic)

## Purpose

Take two things from the user:
- (a) a **topic** (the product, event, or subject to write about)
- (b) a **category** (e.g. "analysis and review," "deep dive," or whatever label the user gives it)

Then, without needing a pre-supplied link, research the topic yourself and produce a complete analysis-style article using the tone and structure defined below — plus 4 suggested image placements, a closing section titled exactly "Conclusion" (translated into the response language, see Step 0), and a meta description/snippet of at most 130 characters.

This skill carries no domain assumptions (gaming/tech/finance/anything) — infer the domain from whatever topic the user gives you and research accordingly.

---

## Step 0 — Language

Write your entire response — including the article itself, all section titles, and the final report — in the same language the user used to make the request. Do not default to English if the user asked in another language.

Writing in another language is not translation. Research and write directly in that language, with sentence rhythm, idiom, and structure that a native speaker of that language would consider natural for an analytical/review article in their own media landscape — not a version that reads like it was translated from English. Concretely:
- Don't mirror English sentence architecture (heavy nested clauses, "According to X, Y said Z" news-lede patterns) word for word. Rebuild the sentence the way a native writer of the target language would naturally construct it.
- Use whatever native-language conventions exist for connecting related clauses (in some languages that's a semicolon-like construction, in others a different connective) instead of chopping everything into short, choppy, telegraphic sentences that feel machine-translated.
- Keep proper nouns, brand names, and technical terms that are commonly left untranslated in that language's media (check convention per language/domain) — don't force-translate terms that native writers of that language would leave in their original form.
- On first mention of a proper noun (company, product, person), give the native-script form plus the original-language form in parentheses if that is standard practice in the target language's media; on later mentions use whichever form is customary.

---

## Step 1 — Research

- Use web search to find credible, recognized sources in the topic's own domain — not just whatever ranks first.
- Fetch at least 4–7 sources to build a full picture: background, technical/business details, reactions, and comparison to competitors or similar precedents.
- Extract key facts, numbers, dates, and proper names (with correct original-language spelling) from each source.

### ⚠️ Verify source credibility — before citing, not after

Not every source that shows up in search results is credible. Before citing any source in the article:
- If a source's name is unfamiliar or you're not sure what kind of site it is, run a separate search for "what is [domain]" or "[domain] about" to check.
- Never cite gambling/betting sites, unattributed aggregators with no named author, affiliate/lead-generation sites built purely to drive traffic, or SEO-farm "wiki" sites with no real editorial team — even if their content looks accurate on the surface.
- Prioritize recognized specialist outlets in the topic's own domain (established trade press, major outlets covering that industry) over generic content-mill sites.
- If you realize after drafting that a source you used wasn't credible, remove or replace that claim immediately — don't wait for the user to catch it.

---

## Step 2 — Tone and writing style (the most important part of this skill)

This is what separates the output from a generic, translated-sounding, AI-pattern article. Always follow these rules:

### Natural, idiomatic prose — never translation-shaped
- Write sentences the way a native speaker would naturally explain the topic to someone, not as if an English news-style sentence (attribution + formal quote) was mechanically carried over into the target language.
- Open up long, clause-stacked sentences and rebuild them in the order that reads naturally in the target language, rather than following the source language's structure token-for-token.

### Opening paragraph
- Start dense and direct with the key facts: what the topic is, when/where it's relevant, and the important numbers or prices.
- If timing matters (e.g. a launch date or event), include the reader's likely local-time equivalent in parentheses when relevant.
- No generic scene-setting openers ("The world of X has always been full of Y") — go straight to substance.

### Transparency about the limits of the analysis (when relevant)
If the article covers something that just happened (e.g. the first hours of a product launch) and long-term hands-on experience isn't possible yet, say so honestly early in the piece — that the analysis is based on official information and early reactions, not extended firsthand use. Only include this disclosure when it's actually true, not as a boilerplate line in every article.

### Section headings (H2)
- Short, noun-phrase headings (e.g. "The extraction loop — where the pressure comes from," "Launch timing and where it sits in the market"), not full sentences and not questions unless a question genuinely fits.
- Each heading should cover one distinct angle, not just a time-based split or a restatement of the previous section in different words.

### Sourcing (no external links)
- Format: "According to [source name]'s report from [date]" or as a trailing parenthetical: "(per [source name])."
- Vary where the attribution sits in the sentence — sometimes at the start, sometimes mid-sentence, sometimes as a trailing parenthetical. Repeating one fixed pattern ("According to X, Y" in every paragraph) is itself a tell of AI-generated writing.
- Never cite a vague, unnamed source ("according to reports," "experts say," "sources indicate") — always name the specific outlet.
- Each source gets at most one direct quotation (kept under 15 words); prefer paraphrasing everything and only quote directly when the exact wording genuinely matters.

### Balance and analytical honesty
- An analysis/review article must honestly cover both strengths and weaknesses/risks/open questions. Don't write one-sided praise or one-sided criticism.
- If early reactions (users, critics) are mixed, reflect both sides proportionally to their actual weight — don't cherry-pick one side.
- For claims that are unverified or come from a single source/user discussion, phrase them with honest vagueness ("some early feedback has been mixed") rather than attributing them to a specific group (e.g. "users in [country]") without a real source for that attribution.

### Technical terms
- Don't force-translate domain terms that are commonly used in their original form in that language's media for this domain (e.g. genre jargon, product/brand names).
- On first mention of a proper noun, follow whatever convention is standard in that language's media (see Step 0); afterward use whichever form is more natural in context.

### Never write
- A closing section literally titled anything other than the target-language equivalent of "Conclusion" (see Step 3, item 5)
- A generic, sweeping opening line or a forced metaphor
- Overused AI-writing filler words in the target language (equivalents of "crucial," "breathtaking," "ruthless," "game-changing") — use something more specific and concrete instead
- A closing paragraph that's just a repetitive summary of the rest of the article
- The same idea restated in different words across multiple paragraphs
- Invented facts to pad out a thin section — if the available information is limited, keep that section short or cut it rather than filling the gap with a guess

### Length
- Scale to how much substance the topic actually has — typically around 800–1,400 words (analysis pieces usually run longer than plain news because they cover multiple angles). Don't pad a thin topic to hit a word count.
- Max ~150 words per paragraph; break up sentences longer than roughly 40 words.
- Use the number format standard in the target language (e.g. localized digits/numeral conventions where that's the norm).

---

## Step 3 — Fixed article framework

Every article must include:

1. **Title (H1)**: short and direct, often structured as "[Topic] — [short analytical descriptor]" (e.g. "Product X — Strengths and Weaknesses One Day After Launch").
   - **Maximum 60 characters including spaces** — count it before finalizing; shorten if it runs over.
   - **Must have a hook**: purely descriptive/neutral is not enough. Build in something that creates genuine curiosity — tension, an implicit question, a surprising number, or a clear promise of angle (strengths vs. weaknesses, a comparison, a risk). A flat, purely reportorial title ("X — Analysis and Review") has no hook and needs to be sharpened.
2. **Opening paragraph**: key facts, per the rules above.
3. **(Optional) transparency paragraph**: per the rules above, only if genuinely warranted.
4. **3–6 H2 sections**: each a distinct angle (background/core idea, technical or operational details, reactions and feedback, market position/comparison to competitors, risks or open questions).
5. **Closing section titled the target-language equivalent of "Conclusion"**: this heading must always be exactly that word/phrase in the response language — not a "final thoughts" flourish or a generic wrap-up label. Its content must not be a repetitive summary; it must look forward — open questions still unresolved, things worth watching in the coming days/weeks, or the conditions the topic's success or failure actually depends on.
6. **4 image suggestions**: placed throughout the article at natural transition points between sections (not all bunched together), using the format `<!-- Suggested image: short description -->` between paragraphs/sections. You don't generate or place the image itself — just mark the right spot and describe its content. Put these 4 suggestions where an image would genuinely help comprehension (a concrete scene, an interface, a product shot), not mechanically every few paragraphs.
7. **Snippet (meta description)**: at most 130 characters, an engaging summary without clickbait, containing the core topic. Count the characters before finalizing.

---

## Step 4 — Final self-review

Before delivering, run this checklist against the final text:
- Does every sentence read naturally, or does it still feel translated? (Read it back mentally: would a native speaker actually phrase it this way?)
- Is every citation to a source you've actually verified as credible?
- Are both strengths and weaknesses/risks represented?
- Is the closing heading exactly the target-language equivalent of "Conclusion," and is its content forward-looking rather than a repeat of the article?
- Are there exactly 4 image suggestions placed at sensible points?
- Is the snippet under 130 characters? (Count it, don't estimate.)
- Is the H1 title under 60 characters (count it, don't estimate) and does it genuinely have a hook, not just a neutral label?
- Have all the "never write" patterns (generic conclusion label, forced metaphor, AI-filler words, vague sourcing) been removed?

---

## Step 5 — Final output

Structure the response like this (translate the section labels below into the response language; this is a layout, not literal text to output in English):

```
═══════════════════════════════════════
Article
═══════════════════════════════════════

[H1 title]

[full article body with H2 sections, inline image suggestions, and the closing "Conclusion" section]

═══════════════════════════════════════
Snippet
═══════════════════════════════════════

[max 130 characters — note the character count next to it]

═══════════════════════════════════════
Short analysis report
═══════════════════════════════════════

📚 Sources used:
- [source name] — [date] — [type: background/technical/reactions/…]
- ...

⚠️ Claims needing further verification: [count]
1. [claim] ← [why it's uncertain] ← [suggested next step, if any]
(If none: "No unverified claims remain in the article.")
```

---

## Warnings

⚠️ Never invent a fact that wasn't in a source, even to fill out a thin section or to make the article look more balanced.

⚠️ Check the credibility of any unfamiliar source before citing it — this is the single most important lesson this skill is built on. A gambling site was once mistakenly cited as an analytical gaming source, and if the mistake hadn't been caught, it would have stayed in the article.

⚠️ If some part of the article (an award claim, a statistic, a specific claim) can't be confirmed with a credible source, cut it entirely; don't write it and add "but this isn't important" — staying silent about an uncertain fact is always safer than explaining it incorrectly or half-correctly.

⚠️ If the user drafts a rewritten sentence and asks "did I get this right?", carefully compare the meaning against the original source's actual point — a rewrite can read smoothly while accidentally reversing the original meaning. Flag this directly and explicitly if it happens; don't let it slide.
