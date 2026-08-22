# Pattern Catalog: Signs of AI Writing

Source: Wikipedia's [WikiProject AI Cleanup](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing) essay (the primary, most-cited field guide of its kind, built from thousands of flagged AI-generated Wikipedia edits), cross-checked and extended with independent research: Wikipedia's own talk-page archives (where editors log patterns not yet folded into the main essay), and analysis from outlets covering the essay in depth (Beutler Ink, MakeUseOf, Forbes, FlowingData, Wikiwand, humanizeai.com, isitslop.io, and others), plus separate research into Persian-language LLM-writing tells.

Wikipedia's own essay stresses: **none of these signs individually prove AI authorship.** LLMs are trained on human writing and human writers share some of these habits; some signs (word-frequency spikes especially) are population-level statistical signals, not reliable per-document proof. Treat this catalog as a checklist for density and repetition, not a word blacklist.

---

## 1. Vocabulary & phrase tells (English)

LLM output leans on a recognizable, shifting set of "safe" words and inflating phrases. The exact word list has shifted release over release (Wikipedia's essay tracks this by era), so treat the *category* — not any single word — as the signal.

**Overused "AI vocabulary" words** (flag when several appear in one short piece, not on a single use):
delve, tapestry, intricate/intricacies, pivotal, underscore(s), boast(s)/boasting, bolstered, crucial, garner(ed), interplay, key (as filler adjective), landscape (figurative), meticulous/meticulously, testament, vibrant, valuable, enduring, foster(ing), align with, enhance, showcase/showcasing, highlight(ing), emphasiz(e/ing), robust, comprehensive, dive into, navigate (figurative), realm, journey (figurative, non-travel), unlock, unleash, game-changer, cutting-edge, seamless(ly), holistic, multifaceted, nuanced, myriad, plethora, ever-evolving, correlate/causal/empirical (Grok-specific overuse).

**Inflated significance / notability phrases** — the single most Wikipedia-flagged category. Text takes a routine fact and dresses it as historically or culturally important:
- "stands as a testament to..."
- "serves as a testament/reminder..."
- "plays a vital/significant/crucial/pivotal role..."
- "underscores/highlights its importance/significance..."
- "marks a pivotal moment / turning point / watershed moment..."
- "leaves a lasting/indelible mark/legacy..."
- "rich cultural heritage / rich tapestry..."
- "cementing/solidifying its place..."
- "setting the stage for..."
- "symbolizing its ongoing/enduring/lasting..."
- "contributing to the broader..."
- "evolving landscape / focal point / deeply rooted..."

*Fix*: state the fact plainly and let it carry its own weight. Cut the inflating clause entirely, or replace it with a concrete, specific consequence the text actually supports (not a new invented one).

**Boilerplate/formal-letter phrasing surfacing in non-letter content**: "I hope this message finds you well", "Thank you for your time and consideration", "I am willing to help in any way I can" — a dead giveaway when it appears in a blog post, article, or narrative rather than an actual letter/email.

**Leftover chatbot artifacts**: "Certainly! Here is...", "I hope this helps!", "Let me know if you have any questions!", "Sure, here's a breakdown..." — collaborative dialogue phrasing left in from the raw generation, never edited out.

## 1b. Vocabulary & phrase tells

Persian LLM output has its own recognizable tics, separate from the English word list above — don't rely on the English list for Persian text.

- Overused formal/inflating adjectives: (crucial), (innovative), (efficiency/productivity) dropped in generically, often disconnected from the actual subject.
- Needlessly bureaucratic/formal phrasing replacing a simple direct instruction — e.g. where a human would just write.
- generic, vague generalizing that never lands on a specific concrete detail; reads complete on the surface but says nothing precise about the actual subject.
- Mechanical/dry use of set phrases regardless of the emotional or contextual register of the passage.
- Missing colloquialisms, idioms, and proverbs that a Persian human writer would naturally reach for — their total absence across a long piece is itself a tell.
- Absence of real personal experience, concrete anecdote, or story-level specificity — content stays at the level of general claims.
- Repetition of the same word/phrase reworded several times across a passage without adding new information (semantic padding).
- Uniform sentence length/paragraph rhythm with no coordination between short and long sentences (see Section 4).

*Fix*: replace generic formal phrasing with direct, plain equivalents; insert or restore idiom/colloquial texture consistent with the piece's actual register; cut reworded restatements down to one instance.

## 2. Structural & rhetorical patterns (language-agnostic — check in any language)

**Negative parallelism / contrast-reframe**: "It's not X, it's Y." / "It's not just about X — it's about Y." The single most-cited structural tell. Legitimate when the contrast is real and earns its place; an AI tell when it manufactures a contrast nobody was making, purely for rhythm.

**Rule of three**: reflexive triplets — three adjectives, three examples, three clauses, three bullets — even when a third item is redundant or picked only for cadence ("scalable, efficient, and future-proof" where the third just restates the first two). Check: does the sentence lose anything if the third item is deleted? If not, the shape was doing the work, not the content.

**False ranges**: "ranging from X to Y", "from intimate gatherings to global movements", "from technical expertise to creative vision" — implies a real spectrum where there's just two loosely related things dressed up to sound comprehensive.

**Section summaries that restate**: "In summary...", "In conclusion...", "Overall...", "To sum up..." followed by a restatement of what was just said, adding zero new information — especially reflexive in short pieces that don't need a summary at all.

**Superficial analysis tacked onto facts** (a.k.a. "tailing clauses"): a factual sentence gets a present-participle clause bolted on that gestures at significance without explaining it — "...highlighting Pakistan's entry into the global community", "...further enhancing its significance as a dynamic hub", "...illustrating its lasting influence." Delete the clause, or replace with an actual explanation if the text supports one.

**Editorializing asides**: inserted opinions about importance rather than content — "it's important to note that...", "it's worth mentioning...", "no discussion would be complete without...", "needless to say...".

**Vague attribution**: "studies show", "experts say", "many believe", "it is widely regarded" with no named source. *Fix*: name the actual source if the author has one, rephrase as the author's own claim, or cut it — never invent a citation to fill the gap.

**Process narration**: the text describes the process that produced it instead of just stating the finding — "after reviewing the available sources...", "upon closer analysis...", "an examination of the article shows..." A subtler, less-common tell (from Wikipedia talk-page discussion, not yet in the main essay body) but a clear giveaway once you know it.

**Compulsive both-sides hedging**: text that raises a claim only to immediately undercut it with an equally generic counter-claim, producing false balance rather than an actual judgment — reads safe and says nothing.

**Actor-less/personification constructions**: the object of an action gets promoted to grammatical subject/"doer" without a real actor — "the policy has led to...", "the changes have resulted in..." at high density, where a human would more often name who did what.

**Staccato anaphora/asyndeton triplets** used as a reflexive closer: "No fluff. No filler. No noise." Occasionally a deliberate device; an AI tell when it's the default way every section wraps up.

**Overuse of long descriptive section/heading titles** that read like restated summaries rather than short labels (from Wikipedia talk-page discussion — a newer, less-documented pattern).

## 3. Formatting tells

Mostly relevant to web/article-style content; check for fiction/prose too but expect fewer hits there.

- **Em dash overuse**: more em dashes than the genre/author's baseline, especially unspaced or placed where a comma, colon, parenthesis, or (correctly used) hyphen would read more naturally. A rough working threshold: more than ~1 per 200 words in non-fiction prose is worth a look — but don't strip every single em dash on principle; sparing, well-placed use is completely normal human writing.
- **Missing en dashes**: hyphens substituted for en dashes in ranges/scores (1990-2000, 3-2) where an en dash (–) belongs.
- **Excessive bolding**: key terms bolded on nearly every line in a way that feels mechanical rather than editorial.
- **Bullet lists with bold lead-in + colon + restating sentence**: "**Scalability:** The system is designed to scale easily across use cases." — the bolded term just gets reworded in the sentence that follows, adding nothing. A strong tell when done consistently across a list.
- **Bullet/numbered lists used where flowing prose would read better** — especially in narrative or essay content, where a human writer would rarely chop reasoning into list form.
- **Title Case Applied To Every Heading**, inconsistently or mechanically.
- **Non-standard bullet markers**: bullet character (•), stray hyphen/en dash, hash (#), or emoji used as list markers, especially left over from a markdown-to-plaintext copy-paste.
- **Emoji used as decoration or bullet substitutes** at a density that doesn't match the rest of the author's voice.

## 4. Statistical/stylistic tells (rhythm and texture — read for feel, not by search)

- **Metronomic sentence rhythm / low "burstiness"**: most sentences land in a narrow length band; no genuine short-sharp sentence next to a longer, comma-laden one. Human prose naturally varies; flat, even rhythm across a full passage is a tell.
- **Paragraph-recipe uniformity**: every paragraph follows the same internal shape (claim → example → restatement), section after section.
- **Grammatically flawless throughout**: no fragments, no natural imperfections, every clause perfectly balanced — fine in isolation, a tell in density across a long piece with zero variation.
- **"Hollow polish"**: technically correct, smooth prose that says less on a second read than it appeared to on the first — mundane ideas dressed in confident, even language. Harder to fix mechanically; flag it for the author rather than trying to silently patch it, since fixing this requires actual added insight/specificity, not a pattern swap.

*Fix strategy for this whole section*: vary sentence length deliberately when rewriting; break at least one paragraph's recipe per few paragraphs; don't try to introduce fake typos or fragments purely to look human — vary structure and content specificity instead.

## 5. Sensitive-domain trigger list

Flag the piece for the Step 4 fact-check warning if it contains any of:
- Medical/health claims: symptoms, treatments, drug names, dosages, diagnoses, medical study results.
- Scientific/academic claims: research findings, statistics, historical dates/facts presented as settled, citations of studies or papers.
- Legal claims: statements about law, regulation, rights, or legal process presented as fact or advice.
- Financial claims: specific figures, investment claims, market/statistical projections.

This applies **regardless of how many or few vocabulary/structural AI-tells were actually found in that content** — the warning is about fact accuracy, which this skill does not and cannot verify, not about writing style.

## 6. What NOT to over-correct

- A single em dash, one triplet, one "delve" in a long piece is not a problem — don't hunt-and-destroy every literal instance of a listed word irrespective of context.
- A real, earned contrast statement is not negative parallelism just because it uses "not X, it's Y" phrasing — check whether the contrast is actually doing work.
- Fiction/creative writing legitimately uses rhetorical rhythm, repetition-for-effect, and stylized prose that would read as a tell in an encyclopedia article — weigh genre before flagging.
- Never invent specifics (names, numbers, sources, quotes) to fix a vague-attribution or hollow-polish flag. If the author's own text doesn't supply the specific, the honest fix is to soften the claim into their voice or cut it, not to fabricate.
