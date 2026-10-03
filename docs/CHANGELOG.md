# Evidence and reference change history

## 2026-10-03 — Reference root in `docs/`; platform rename and refocus

- Moved the maintained reference into `docs/`, now the authoritative reference root. The front page is `index.md` (formerly root `README.md`). Backlinks that meant contents still target `index.md`. Current display labels say reference contents; destinations are unchanged.
- Refocused the platform as **Endurance Training Evidence**, a living research-to-practice reference rather than a read-in-order book. The front page leads with questions, decisions, graded conclusions and sources. Part I–III remains an optional conceptual reading route. This is a naming and navigation refocus, not a new evidence review. The evidence-check date remains **2026-10-02**.
- Topic-scope lines now point question ownership at the question map (`index.md#question-map`) instead of the unpublished prompt. Search provenance and historical notes that still name that file were left in place.
- Source and conclusion anchors, citation aliases, claim IDs, scientific claims, uncertainty, and search-query provenance are unchanged. Source-register topic paths stay reference-root-relative (`topics/...`).
- Repository-root `README.md` is the project entry only. `initial_prompt.md` stays at the repository root and is not part of the reference. Generated `site/` is a derived rendering, not a second source.
- Added pinned MkDocs/Material dependencies, explicit topic/conclusion/source navigation, full-text search, source-view links and a GitHub Actions artifact-deployment workflow. Main-branch updates deploy; pull requests only build. The public repository and Actions-based Pages destination are named `endurance-training-evidence`.
- Verification: strict MkDocs build passed. Browser checks covered the question-first desktop entry, all 21 question rows, durability search and topic navigation, a 40/20 conclusion/source-register lookup with the matching DOI and recorded access level, and 390-pixel mobile navigation without page-width overflow.
- A rendered-page crawl checked 19 pages and 2,398 internal links/anchors with no failures; the structured source register returned HTTP 200. External paper URLs were not bulk availability-tested.
- Enabled native rendering of the four existing Mermaid diagrams and visually checked the conceptual model. Optional numbered reading lists retain their intended starting numbers. Markdown remains authoritative; generated HTML is not committed.

## 2026-10-02 — Initial living-book edition

- Organized the folder as a linked book: conceptual model, eight maintained evidence chapters, program design, and reference appendices. `README.md` is the contents and question-routing page. The ten-section report publication requirement was withdrawn; the assembled synthesis was migrated into chapters rather than retained as a competing report.
- Covered all 21 questions in `initial_prompt.md`. Published 76 stable conclusions and 452 deduplicated source records from 513 chapter extractions, retaining original citation aliases, access levels and extraction provenance. Recorded 143 discovery/search entries. These are not 452 independent trials or an exhaustive systematic review.
- Preserved the 7-, 9- and 12-hour example weeks and twelve-week progression. Weekly availability includes strength: 390+30, 480+60 and 660+60 minutes. Exact recipes, placement and routine deload dates are explicitly coaching applications, not proven optima.
- Restored general web-search access during the investigation; used original abstracts, full texts and metadata records with their respective limits. No transcript was supplied: starting-claim paper matches remain unconfirmed attributions.
- **PHY-C05 / TID-C02 / DUR-C02:** qualified Cove 2025's interval-length-based “polarized” classification, sex-specific study-mean inclusion, 2023 search cutoff, low certainty, limited volume regression and internal count/CI discrepancies. It is not a measured 80/20 or direct polarized-versus-pyramidal result and does not establish a causal volume optimum.
- **PHY-C05:** integrated the six-week 2026 randomized HIIT-with/without-four-extra-hours trial in 19 moderately trained cyclists/triathletes. No detected group advantage is not equivalence, a general hour-dose curve or proof that additional volume is useless.
- **INT-C01–C03 / INT-C06–C08:** preserved Odden's association versus causality and adjusted-model interpretation; separated acute oxygen uptake from adaptation; added Hanstock 2020's randomized 40/20-versus-4×8 comparison (illness-primary, not a performance ranking) and the directly retrieved acute Rønnestad–Hansen 2016 mechanism paper. Corrected interval-sequence labels and session-count arithmetic in the distribution chapter.
- **DUR-C09 / FUEL-C01–C03 / FUEL-C06–C07:** distinguished severe next-day carbohydrate restriction after depletion from skipping breakfast; included measured Norte gastrointestinal outcomes and its 95%-of-first-GET preload; restricted sucrose oxidation equivalence to the glucose+sucrose mixture tested; downgraded the imprecise train-low null; kept ~1.2 g/kg/hour early recovery conditional on rapid restoration. Main 2026's correction replaces a duplicated schematic figure, not a stated wattage revision.
- **REC-C07 / REC-C10:** removed ferritin-only treatment rules. Post-heat haemoglobin dilution and deficiency can coexist; assessment considers multiple markers, inflammation, symptoms and context. No indiscriminate iron supplementation.
- **STR-C02:** flagged the strength review's positive efficiency estimate/negative interval versus negative Figure 3 as a source-reporting inconsistency. Beneficial magnitude and low certainty are retained without inventing a corrected signed estimate. Online-2025 versus issue-2026 dates are recorded.
- **MON-C07:** separated three-minute WEP-versus-modelled-W′ agreement error from within-protocol W′ repeatability; removed a purported 2 kJ decision threshold.

Future entries should state the affected claim IDs, added or corrected sources, changed decision, remaining uncertainty and affected chapters. Follow [the update workflow](research-methods.md#updating-after-a-new-paper).

### Verification of the initial edition

- Parsed 19 Markdown documents and rendered the contents page and program-design chapter with MarkdownIt. This was a parser/navigation smoke, not a browser visual audit.
- Checked 1,440 local links and their targets/anchors; corrected four VO₂-chapter contents links to the existing stable conclusion anchors. No local-link failures remained.
- Checked all 76 conclusion anchors/grades, 513 source aliases and canonical-source mappings, and coverage of the 21-question index.
- Exercised six question → chapter → conclusion → original-source lookup routes: added volume, 30/15 adaptation, 40/20 evidence, sugar formulation, heavy strength and CP/W′ validity.
- Verified 420/540/720-minute total-time weeks, including strength and all hard-session warm-up/recovery/finish components, plus interval-work arithmetic across all 12 progression rows.
- External paper access remains at the levels recorded per source; this verification was not a bulk live-URL availability test. The obsolete report file and its empty directory were removed.
