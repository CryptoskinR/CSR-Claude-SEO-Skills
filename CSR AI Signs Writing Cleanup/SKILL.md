---
name: csr-ai-signs-writing-cleanup
description: >
  Detects and rewrites "AI writing tells" (patterns from Wikipedia's "Signs of AI writing"
  guide, plus extra vocabulary/structural/formatting tells from further research, including
  Persian-specific ones) in any text - articles, essays, stories, novels, scripts, marketing
  copy, academic drafts, any language, any length. Use whenever the user wants to "de-AI" a
  text, make it "sound less like ChatGPT", "humanize" it, remove robotic tone, or clean an
  AI-assisted draft before publishing - even without the word "AI", e.g. "make this sound more
  natural" or "fix the robotic tone". Always outputs: the cleaned text, a full itemized change
  report per pattern, and a numeric checkpoint tally per category. Adds a fact-check warning
  for academic/scientific/medical/legal/financial content. Skill instructions are in English;
  replies must be in the user's own language.
---

# AI Writing Signs Cleanup

A skill for finding and neutralizing "AI writing tells" — the surface-level and structural patterns that make text read as LLM-generated — in any text the user provides, while preserving their meaning, facts, and voice. Grounded in Wikipedia's WikiProject AI Cleanup essay ["Signs of AI writing"](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), extended with additional patterns from independent research (see `references/pattern-catalog.md`), including patterns specific to Persian-language text.

**Read `references/pattern-catalog.md` before doing any rewriting.** It contains the full, categorized list of tells, concrete before/after examples, thresholds for when a pattern is worth flagging, and fix strategies. This file only covers the workflow.

## Core principle

These are *signs*, not proof, and not a style ban. A single em dash, one triplet, one "delve" does not make text sound AI-written — density and repetition across a piece does. The goal is never to mechanically delete every instance of every listed word or structure (that produces flat, over-corrected prose that reads just as artificial in the other direction). The goal is to reduce the *statistical fingerprint* — the repetition, the uniformity, the reflexive hedging and inflation — while leaving deliberate, well-placed, sparing uses of the same devices alone, because human writers use them too.

Never fabricate facts, sources, statistics, quotes, or specifics to replace a vague AI-ism. If a vague claim ("studies show...") can't be grounded in something the author actually has, the fix is to soften it into the author's own voice or cut it — not to invent a citation.

Never change the actual claims, arguments, plot, or factual content of the piece. This is a style/pattern edit, not a rewrite of substance.

## Workflow

### 1. Intake

Get the text: pasted in the message, an uploaded file, or an artifact already in the conversation. If it's a file, read it directly (don't ask the user to re-paste it).

Identify, from the text and/or what the user says about it:
- **Language(s)** of the text. Structural/rhetorical patterns (Section 2–4 of the catalog) apply across languages. Vocabulary-word tells (Section 1 of the catalog) are mostly English-specific; for Persian text, use the Persian-specific tells in Section 1b of the catalog instead of/alongside the English list. For any other language, apply the structural/formatting/rhythm patterns, and use judgment on vocabulary — the same *kind* of tell (generic import words, inflated formal register, empty transitional phrases) exists in most languages even if the exact words differ.
- **Content type**: blog/article, fiction (short story, novel chapter, script), opinion/essay, marketing/product copy, academic/research writing, news, other. This affects which formatting patterns even apply — bullet-with-bold-lead-in and heading-per-section tells matter for articles, barely apply to prose fiction.
- **Sensitive domain check**: does the text make claims in medicine, health, academic/scientific research, law, or finance (statistics, study results, dosages, legal advice, financial figures, medical claims, historical/scientific facts presented as settled)? Flag this now — it changes the output (see Step 5).

### 2. Scan

Go through the text against every category in `references/pattern-catalog.md` and tag every instance found, categorized by pattern name. Keep a running tally per category as you go — this becomes the checkpoint at the end. Note both instances you will change and, briefly, any borderline case you deliberately left alone because it was sparing/deliberate/well-placed (don't over-report these, just keep the count honest).

For rhythm/uniformity-type patterns (metronomic sentence length, paragraph-recipe repetition, low burstiness) there's no regex to run by hand — read the piece for feel: do most sentences land in a narrow length band, does every paragraph do claim→example→restatement, does every section resolve the same way? Flag it as one instance of that category per section/passage where it's noticeably present, not per sentence.

### 3. Fix

For each flagged instance, apply the fix strategy from the catalog:
- **Delete outright** when the phrase adds zero content (empty transitions, restated summaries, leftover chatbot pleasantries, letter-boilerplate in non-letter content).
- **Rewrite/replace** with something concrete and specific to *this* piece's actual content when the pattern is inflating or generalizing something real (vocabulary tells, overemphasis-on-significance phrasing, false ranges, superficial tacked-on analysis). Pull the replacement from what the text itself already establishes — don't invent new facts.
- **Restructure** for rhythm/structural patterns: vary sentence length, break up a uniform paragraph recipe, turn a bullet-with-bold-restatement into a plain sentence, drop a triplet to two items (or expand to a real, non-interchangeable third), remove or attribute a vague claim.
- **Soften/attribute or cut** vague attributions ("studies show", "experts say") — either name what's actually known, rephrase as the author's own assessment, or remove the claim.

Preserve the author's actual voice and any place where a "tell" pattern is doing real work (a genuine, well-earned contrast; an em dash the author clearly reaches for elsewhere in ways that read as their own habit; a true, non-generic three-item list). Judgment over mechanical zeal.

### 4. Sensitive-domain warning

If Step 1 flagged medical, scientific/academic, legal, or financial content, add a clearly marked warning to the author in the final reply (in their language) — regardless of whether any AI-vocabulary pattern was found in that specific claim. The warning should tell them plainly to fact-check the specific facts, figures, study citations, dosages, legal statements, or financial numbers themselves before publishing, since this cleanup pass only addresses writing style/patterns and does not verify factual accuracy. Do not skip this even if the piece looks well-sourced — the point is the author verifies it, not that the tool judges it verified.

### 5. Output

Reply with, in this order, **written in the language the user is using/requested** (the skill instructions above are English; the output is not):

1. **The cleaned text.** For anything long-form (roughly >100 lines / a full article or story chapter), deliver it as a file/artifact per the normal file-creation rules, not dumped inline. For short passages, inline is fine.
2. **A full change report**, as a list, grouped by pattern category, each item briefly quoting or describing the original and what it became (or that it was removed) — e.g. "Negative parallelism — «...» → rewritten as «...»". Keep each line short; this is a scan list, not prose commentary.
3. **A checkpoint tally**, formatted as a flat list of counts, one line per pattern category that had at least one change, phrased in the same shape as: "Count of <pattern> changed: N". Include a final total line summing all categories. Only list categories with count ≥ 1 — don't pad the tally with zeroes.
4. **The sensitive-domain warning**, if triggered, as its own clearly separated final note.

Do not add unrelated commentary, don't re-explain the Wikipedia essay to the user, and don't lecture about AI writing in general — just do the work and hand back the four items above.
