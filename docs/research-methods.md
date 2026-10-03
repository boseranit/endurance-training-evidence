# Research and maintenance method

This is a living, question-led evidence platform, not a completed systematic review. Start at the [front page](index.md); use the [glossary](CONTEXT.md) before comparing apparently similar training labels.

## Reference root and derived copies

`docs/` is the authoritative reference root. Topic pages, conclusion records, source records, and paths in this reference, including `topics/`, `evidence/references.json`, and `topic_file` values, are relative to `docs/`, not to the repository root. Citation aliases and claim IDs are unchanged by that layout. The front page is `index.md`.

Answers and new-paper updates are maintained through the stable conclusions, their source records, and the owning topic pages. Route a question to an existing conclusion and topic page; do not open a parallel document for a question that page already owns. Revise that conclusion, its sources and the topic page together, using [the update workflow](#updating-after-a-new-paper).

The repository-root `README.md` is the GitHub project entry and local publishing instructions. It is not an evidence source. A generated `site/` directory, when present, is a derived rendering of this reference; do not edit it or treat it as a second source. `initial_prompt.md` remains at the repository root and is not part of the published reference.

## Scope and provenance

- Target decision: improve VO₂max, sustainable cycling power, general fitness, and event-relevant performance within approximately 7–12 available training hours per week.
- Prefer trained amateur cyclists. Elite cyclists, other endurance sports, recreationally active people, and untrained participants must be identified rather than pooled implicitly.
- Initial evidence check: **2026-10-02**. This is a search/access date, not a guarantee that every relevant publication has been found.
- The starting material is the repository-root file `initial_prompt.md`, which is not part of this reference. It describes claims from a transcript but does not contain the transcript itself. Papers can be matched to those descriptors; exact quotation, speaker intent, and attribution remain unverified. Published topic scope points question ownership at the [question map](index.md#question-map). Do not send readers to `initial_prompt.md` to learn which topic owns a question.
- Initial discovery uses targeted searches, review reference lists, and original-source retrieval. The search register records the queries and access routes actually used. There is no preregistered exhaustive search, independent duplicate extraction, or PRISMA flow; do not describe this as a systematic review.
- General web search initially failed and was restored during the investigation; the research agents were notified and used it for further discovery and update searches. PubMed search presented an access challenge. Europe PMC records and accessible journal/full-text sources provide direct verification; search-generated summaries are discovery aids, not extraction evidence. Each source records its actual access level.

## Authority and document roles

1. **The eight evidence chapters (`topics/`) are the maintained authority for empirical conclusions.** Each important conclusion has a stable claim ID, an evidence grade, population limits, direct references, and uncertainty.
2. **The source register (`evidence/references.json`) is the bibliographic and extraction record.** Its source IDs connect claims to retrieved original records, designs, populations, outcomes, and limitations.
3. **The claim register (`evidence/claims.md`) routes questions to conclusions.** It is an index, not a second independent evidence judgment.
4. **The bibliography (`evidence/bibliography.md`) exposes the source register in readable form.** Its annotations must stay consistent with the extraction record.
5. **The [model topic](topics/training-model.md) integrates mechanisms and priorities; the [program-design topic](topics/program-design.md) owns practical application.** Example schedules are coaching implementations of supported principles, not experimentally validated packages or proof of an optimum. [Starting-claim appraisals](evidence/starting-claims.md) and [research gaps](evidence/research-gaps.md) are linked appendices, not additional independent judgments.
6. **The glossary (`CONTEXT.md`) owns terminology.** Resolve definitions there before silently changing the meaning of a term in a topic brief.

When documents conflict, inspect the underlying studies and update the owning topic page's conclusion first. A newer timestamp alone does not make a statement correct. Reconcile the conclusion register, bibliography, model/program applications and front page in the same update. This reference keeps one live version of each topic page rather than maintaining competing copies.

## Evidence hierarchy and extraction

Prefer, in order: systematic reviews/meta-analyses; randomized or controlled interventions; trained-athlete longitudinal studies; consensus/position stands; high-quality observational work; carefully labeled physiological reasoning and expert commentary. Review quality and population relevance can override this rough ordering: a heterogeneous meta-analysis does not automatically outweigh a directly relevant, well-controlled trial.

For every source used for an important conclusion, record:

- Stable source ID; authors, publication year, title, DOI/PMID when available, and a direct source link.
- Actual retrieval URL(s), access level (**full-text**, **abstract**, or **metadata**), and checked date.
- Design; sample size/sex/training history and baseline fitness when available; intervention duration; comparator and outcome.
- Absolute or relative change and effect size/uncertainty where verified. Within-group improvement is not a between-group advantage. No statistical significance does not prove equivalence.
- Whether the result is acute, longitudinal, observational, mechanistic, or consensus guidance.
- Major limitations, adverse effects/recovery costs, conflicting findings, and relevance to the target cyclist.

If a detail is absent from the retrieved source, say “not available in the retrieved abstract/record,” not an invented estimate. Metadata-only access verifies bibliographic identity, not a study's results. Acute signaling, lactate, heart rate, or time above 90% VO₂max cannot on their own establish superior chronic adaptation.

## Qualitative conclusion grades

| Label | Meaning in this platform |
|---|---|
| **Strong evidence** | Consistent, reasonably robust evidence for the specific claim; directness and population limits still apply. |
| **Moderate evidence** | Credible support, but limited trials, precision, population transfer, comparator control, or conflicting findings constrain confidence. |
| **Plausible but uncertain** | Mechanism, acute response, or limited observational/intervention evidence suggests a benefit without establishing the practical claim. |
| **Mostly coaching practice** | A useful implementation choice with little direct comparative evidence for the exact dose, timing, or optimum. |

Do not grade “cycling,” “Zone 2,” or “nutrition” globally. Grade the actual proposition: carbohydrate supports long-session performance may be well supported while 120 g/hour is optimal for every ride is not. These labels are a transparent editorial shorthand, not a formal clinical GRADE assessment.

## Updating after a new paper

1. **Route the question.** Identify the topic, existing claim IDs, and source IDs before starting a new document. Extend an existing topic unless the subject is genuinely distinct.
2. **Retrieve and verify.** Find the original paper; check publication status, corrections/retractions, DOI identity, access level, and publication date. Add explicit recent-date and relevant-population searches, not only author-name searches.
3. **Extract before deciding.** Enter the design, participants, intervention, outcomes, magnitude, uncertainty, and limitations in the source register. Track online-first versus issue year consistently; explain a discrepancy rather than guessing.
4. **Compare like with like.** Check trained status, baseline fitness, sex, comparator, total dose, diet, test method, and acute versus longitudinal endpoint. Ask whether a new result genuinely contradicts an existing claim or asks a different question.
5. **Revise the existing conclusion.** Keep its ID when the question is unchanged. State what changed, supporting and conflicting sources, and whether the grade or practical implication changes. Retain disagreements explicitly; do not overwrite them with an average claim unsupported by any study.
6. **Propagate the decision.** Update claim routing, bibliography, affected model/program topic pages, and relevant schedule assumptions together. An exact recipe remains coaching practice unless evidence directly tests that recipe.
7. **Record the update.** Add a concise [changelog](CHANGELOG.md) entry with date, affected claim IDs, new sources, changed decision, and remaining uncertainty. A topic page's evidence-check date changes only after a meaningful recheck.
8. **Check navigation and arithmetic.** Follow links from index → claim → source; verify local targets/anchors, source IDs, date/DOI consistency, and any affected weekly totals or interval-work calculations.

## Answering a future question

A useful answer contains: **decision → evidence grade → linked claim → original studies and relevant population → uncertainty → practical consequence**. Quote the maintained conclusion, not an uncited recollection of a topic overview. For a question outside the current evidence, state the gap, search it, then update the relevant topic page.

For example, “Are 30/15s better than 4-minute intervals?” requires separating acute time near VO₂max, chronic VO₂max change, test-specific performance, and which long-interval protocol served as comparator. “Can I ride harder on easy days?” requires checking LT1/VT1, weekly dose, hard-session quality, fueling, and the lack of a universal FTP percentage.

## Safety and personalization boundaries

These documents are educational programming guidance, not diagnosis or individualized medical care. Persistent unexplained fatigue, dizziness, heat illness symptoms, recurrent illness/injury, disordered eating concerns, menstrual disturbance, or suspected iron deficiency warrant qualified assessment. Do not self-prescribe iron, deliberate dehydration, or heat stress based on a performance claim. Example weeks assume an already-trained, healthy cyclist tolerating similar volume; they are not instructions to jump from inactivity to the listed workload.
