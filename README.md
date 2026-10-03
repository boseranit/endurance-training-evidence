# Endurance Training Evidence

**Research-to-practice reference, with a cycling focus.** Browse the platform at <https://boseranit.github.io/endurance-training-evidence/>.

Start at [docs/index.md](docs/index.md) to look up a question or training topic, then follow its graded conclusions to the supporting research. This file is the repository entry and the local publishing notes, not an evidence source. The text documents under `docs/` are authoritative; `site/` is a generated rendering and must not be edited or committed.

## Reading the site

Use the question and decision indexes, topic navigation, [key conclusions](docs/evidence/claims.md), [supporting sources](docs/evidence/bibliography.md) and full-text search to pin down what the research says. Each conclusion has a stable ID, evidence grade, source links and an owning topic page. New papers can change a conclusion through the [documented update workflow](docs/research-methods.md#updating-after-a-new-paper); publication does not silently refresh the evidence.

This is a targeted, critically appraised investigation for a trained amateur with about 7–12 training hours per week, not an exhaustive systematic review and not a plan for someone training about 30 hours. Evidence was checked on 2026-10-02. That date is a search and access date, not a guarantee that every relevant publication was found. Sources were read as full text, abstract, or metadata, and each record states which. No transcript was supplied, so starting-claim paper matches are not confirmed attributions. Example weeks are coaching applications of the maintained conclusions, not proven optima and not individualized medical advice. Iron supplementation, unexplained persistent fatigue, RED-S concerns, and heat exposure need the safeguards in the relevant chapters. Do not self-prescribe iron, deliberate dehydration, or heat stress from a performance claim.

`initial_prompt.md` is local working material, not part of the public reference.

## Local preview

Use Python 3.10 or newer. These commands are the same on Windows, macOS, and Linux. Activate a virtual environment first if you use one; `.venv/` is ignored, and another location is fine.

```bash
python -m pip install -r requirements.txt
python -m mkdocs serve
python -m mkdocs build --strict
```

`serve` follows `site_url`, so the preview is <http://127.0.0.1:8000/endurance-training-evidence/>. `build --strict` fails on missing internal links or anchors.

## Publication

A push to `main` builds the site and deploys it to GitHub Pages. A pull request runs the same strict build and does not deploy. A manual run deploys only when it is from `main`. The workflow uses Python 3.12 and runs `pip install -r requirements.txt`, then `mkdocs build --strict`.
