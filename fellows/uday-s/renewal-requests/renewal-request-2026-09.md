# Fellowship Renewal Request — Uday Sonawane

**Project:** Mycroft market-sentiment pipeline + Humanitarians AI video series
**Group:** Mycroft
**Current agreement:** 21 August 2026 → 30 September 2026
**Requested renewal:** 1 October 2026 → 31 December 2026
**Reporting period:** 21 August → 18 September 2026 (4 weeks, 85 hours)

### Where the evidence is

- **Finished videos** are in Google Drive, linked per week below.
- **GitHub folders** hold each video's source — script, scene code, fact-check and sources — **not the video files**, which the repository excludes by policy.
- **Pipeline code** is in `nikbearbrown/mycroft`, linked per pull request.

---

## Summary

The Mycroft market-sentiment pipeline described six processing steps in its recipe, but none of them had been written. All eleven scripts belonging to that recipe were copies of the same empty 74-line template — including the ones meant to fetch data, which made no network calls at all.

Over these four weeks I wrote all six steps. Each was submitted as a pull request and all four have been merged into `nikbearbrown/mycroft`.

**My contribution:** I am the sole author of the four pipeline pull requests and of all eight videos — script, scene code, fact-check and render for each.

To show the steps actually work rather than merely run, I also built a test set of 18 deliberately broken records. Each defect is assigned in advance to the step that is supposed to catch it, so the result is a number rather than an opinion: all 18 are caught, at the exact locations expected.

Alongside the engineering I produced eight videos, about 26 minutes in total. Four document the pipeline work itself; four explain AI and STEM topics. All are merged into `nikbearbrown/humanitarians-youtube`.

**Hours: 85 across four weeks — 22, 23, 20, 20. Every week at or above 20, each with a dated frictional log and a merged pull request.**

---

## 1. The pipeline — six steps, all merged

| Delivered | Pull request | Merged |
|---|---|---|
| Test fixtures + step 1, verify provenance | [mycroft #23](https://github.com/nikbearbrown/mycroft/pull/23) | 2026-08-27 |
| Steps 2–3, ingest and shape validation | [mycroft #37](https://github.com/nikbearbrown/mycroft/pull/37) | 2026-09-04 |
| Steps 4–5, quality check and scoring | [mycroft #40](https://github.com/nikbearbrown/mycroft/pull/40) | 2026-09-11 |
| Step 6, the human-readable report | [mycroft #48](https://github.com/nikbearbrown/mycroft/pull/48) | 2026-09-18 |

Together: 4 commits, 53 files, roughly 8,900 new lines.

### How the steps are designed

Each step is deliberately limited, so that evidence of a problem survives long enough for the step responsible for catching it to do so.

- **Ingest moves data; it does not fix it.** If it quietly corrected the wrong record count or skipped the unreadable file, step 3 would have nothing left to find.
- **The quality check marks bad rows; it does not delete or convert them.** Stale and wrong-typed rows stay in the data, flagged.
- **The scoring step reproduces the original arithmetic exactly**, but raises a named flag every time that original quietly substitutes a value — for example treating `"N/A"` as zero, or falling back to a score of 50 that looks like a neutral reading when it actually means "no data".
- **The final report separates what was measured from what was inferred**, and links each figure back to the hash of the file it came from.

Each step was also tested for what it must *not* catch, so responsibilities do not overlap: step 3 leaves all ten of step 4's defects alone.

### Why this matters

Running the clean test set and the deliberately corrupted one produces the **same headline score — 64, "slightly bullish"** — even though four rows beneath one of them are contaminated. The number alone cannot tell the two apart. The flags can, which is why the steps raise them.

## 2. Eight videos (about 26 minutes)

**Mycroft engineering series** — four episodes covering the pipeline work above. Each is tied to a specific commit and picks up where the previous episode's open list of unfinished items left off. The series ends with all six steps written.

| Ep | Date | Title | Video | Source |
|---|---|---|---|---|
| 1 | 2026-08-27 | Build the Defects First | [Week 1 Drive](https://drive.google.com/drive/folders/1oZmi0MADsrm9v3m93hRnzJXY3TUuZNWb) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-08-27-weekly-fixtures-before-validators) |
| 2 | 2026-09-03 | Transport, Do Not Repair | [Week 2 Drive](https://drive.google.com/drive/folders/1AL97V0-u9K991N0CO1Jgo7BVe-Qs6KgT) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-03-mycroft-weekly-transport-do-not-repair) |
| 3 | 2026-09-10 | Both Sets Scored 64 | [Week 3 Drive](https://drive.google.com/drive/folders/1U8GSp28cr9roLlnD4PnEkTW84G2S0ohl) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-10-mycroft-weekly-both-sets-scored-64) |
| 4 | 2026-09-17 | It Never Says Pass | [Week 4 Drive](https://drive.google.com/drive/folders/1s3_KJqqub5sMbM4s3QZsYnOvMbdYBt5E) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-17-mycroft-weekly-it-never-says-pass) |

**Four AI and STEM explainers.**

| Date | Title | Topic | Video | Source |
|---|---|---|---|---|
| 2026-08-27 | State Space Models and Mamba | How SSMs, S4 and Mamba work, and where they break down | [Week 1 Drive](https://drive.google.com/drive/folders/1oZmi0MADsrm9v3m93hRnzJXY3TUuZNWb) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-08-27-state-space-models-and-mamba) |
| 2026-09-03 | The Brand That Didn't Exist | Generative Engine Optimization | [Week 2 Drive](https://drive.google.com/drive/folders/1AL97V0-u9K991N0CO1Jgo7BVe-Qs6KgT) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-03-generative-engine-optimization) |
| 2026-09-10 | The Gap You Can Actually Close | Zero-day vulnerabilities, from a defensive angle | [Week 3 Drive](https://drive.google.com/drive/folders/1U8GSp28cr9roLlnD4PnEkTW84G2S0ohl) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-10-zero-day-vulnerability) |
| 2026-09-18 | The Constraint Isn't Speed | 6G and what it means for IoT| [Week 4 Drive](https://drive.google.com/drive/folders/1s3_KJqqub5sMbM4s3QZsYnOvMbdYBt5E) | [source](https://github.com/nikbearbrown/humanitarians-youtube/tree/main/fellows/uday-s/2026-09-18-6g-and-iot) |

Every folder contains a `FACTCHECK.md`, `SOURCES.md` and `BUILD-LOG.md` showing where each figure on screen came from and how it was checked.

---

## Weekly evidence

85 hours across four weeks, every week at or above 20. Hours are self-reported; each week's dated frictional log records what was worked on, and the pull request and commit show what was delivered.

| Week | Hours | Delivered | Videos | Frictional log | Work evidence |
|---|---|---|---|---|---|
| 1 · 08-21 → 08-27 | 22 | Test fixtures + step 1; 2 videos | [Week 1](https://drive.google.com/drive/folders/1oZmi0MADsrm9v3m93hRnzJXY3TUuZNWb) | [step 1](../frictional-logs/2026-08-27-step-1-verify-provenance.md) | [mycroft #23](https://github.com/nikbearbrown/mycroft/pull/23) · [`c9d83d46`](https://github.com/nikbearbrown/humanitarians-youtube/commit/c9d83d46) |
| 2 · 08-28 → 09-03 | 23 | Steps 2–3; 2 videos | [Week 2](https://drive.google.com/drive/folders/1AL97V0-u9K991N0CO1Jgo7BVe-Qs6KgT) | [step 2](../frictional-logs/2026-09-03-step-2-ingest-declared-inputs.md) · [step 3](../frictional-logs/2026-09-03-step-3-validate-data-shape.md) | [mycroft #37](https://github.com/nikbearbrown/mycroft/pull/37) · [`ec1ea417`](https://github.com/nikbearbrown/humanitarians-youtube/commit/ec1ea417) |
| 3 · 09-04 → 09-10 | 20 | Steps 4–5; 2 videos | [Week 3](https://drive.google.com/drive/folders/1U8GSp28cr9roLlnD4PnEkTW84G2S0ohl) | [step 4](../frictional-logs/2026-09-10-step-4-transform-and-quality-check.md) · [step 5](../frictional-logs/2026-09-10-step-5-run-approved-tools.md) | [mycroft #40](https://github.com/nikbearbrown/mycroft/pull/40) · [`0188c63d`](https://github.com/nikbearbrown/humanitarians-youtube/commit/0188c63d) |
| 4 · 09-11 → 09-18 | 20 | Step 6; 2 videos | [Week 4](https://drive.google.com/drive/folders/1s3_KJqqub5sMbM4s3QZsYnOvMbdYBt5E) | [step 6](../frictional-logs/2026-09-17-step-6-produce-human-report.md) | [mycroft #48](https://github.com/nikbearbrown/mycroft/pull/48) · [`3f727cf3`](https://github.com/nikbearbrown/humanitarians-youtube/commit/3f727cf3) |

Each video folder also records the exact time its video was compiled, in `BUILD-LOG.md` and in the `build.at` field of `beat_sheet.json`:

| Compiled | Video |
|---|---|
| 2026-08-27 21:41 | Build the Defects First |
| 2026-08-27 23:09 | State Space Models and Mamba |
| 2026-09-03 19:40 | Transport, Do Not Repair |
| 2026-09-03 22:19 | The Brand That Didn't Exist |
| 2026-09-10 17:06 | Both Sets Scored 64 |
| 2026-09-10 18:00 | The Gap You Can Actually Close |
| 2026-09-17 23:19 | It Never Says Pass |
| 2026-09-18 00:33 | The Constraint Isn't Speed |

**Supervision:** Shradha Katte. Review evidence is the merged pull requests above — four in `nikbearbrown/mycroft`, three in `nikbearbrown/humanitarians-youtube`.

---

## Gaps and limits of this evidence

Stated plainly so they are not discovered later:

- **The frictional logs here are copies.** The working originals stay private in the `mycroft` repository; these are the same records, published so they can be opened as evidence.
- **The GitHub folders do not contain the videos.** They hold each video's script, scene code, fact-check and source list. The finished videos are only in the Drive folders linked above.
- **Weekly hours are self-reported.** The frictional logs are dated per step and record what was worked on, and the pull requests and build timestamps show dated output, but none of these is a timesheet: they evidence *work done*, not hours counted.
- **Two claims in this report are evidenced in the `mycroft` repository rather than here** — the 18-defect corpus result and the counts of untested files and undocumented commands. They are visible in the merged pull requests linked above.

## Next period — October 2026

Each phase is ordered so it unblocks the one after it.

### Week 1 — finish the one recipe that is complete

Six working scripts now exist, but the recipe they belong to still says they do not. The aim is to get this recipe honestly promoted to `RUNNABLE-SAMPLE`.

- **By 2 Oct** — write the `RUN_LOG.md` entry covering steps 1–6. At the moment the reports refer to scripts that no logged run produced, which breaks the chain from report back to source.
- **By 5 Oct** — close the 13 `[TODO: DEV]` markers still in the recipe and add its lifecycle details. The evidence needed for that promotion already exists — sample runs, audits, conformance output — it simply has not been claimed.
- **By 6 Oct** — create `logs/gate-decisions/` and record decisions for gates 1 to 4. That folder does not exist yet, so no gate has ever been formally cleared.
- **By 7 Oct** — fix three known contract problems: a missing `type_errors` field in step 3, a mismatch in the reader, and a conflict over log paths in the template.

### Week 2 — make the automated checks actually check

- **By 9 Oct** — add a pytest job to CI. At present CI runs none of the 72 Python test files that already exist in the repository.
- **By 12 Oct** — fix the skip list in `conformance.mjs`. It currently excludes `data`, `ingest`, `gigo` and `tools`, which means the verification command never looks at a recipe's step scripts.
- **By 13 Oct** — clear the manifest drift — six generated files are out of sync, which is why the verification command does not report clean.
- **By 14 Oct** — apply the `.gitattributes` line-ending rules across the whole repository, not just the two folders currently covered. Otherwise file hashes differ between Windows and Linux, which matters anywhere a hash is used as proof.

### Weeks 3–4 — build the `snickerdoodle` command-line tool

97 of the 99 recipes describe a command-line tool that has never been built. Each recipe tells the reader to run commands like `snickerdoodle run <recipe> --step <name>` and `snickerdoodle gate <recipe> --gate N --decision approve`. In practice the six steps are run by calling the Python scripts directly.

- **By 22 Oct** — build `run` first. The six steps already share one interface — the same input, output and dry-run options, results printed as JSON, and a non-zero exit when the run should stop — so there is a working pattern to follow.
- **By 28 Oct** — build `gate`, which produces the same gate-decision records that Week 1 creates by hand.

### Ongoing — reuse the test-fixture approach

The approach behind the 18-defect corpus is not specific to this recipe: a frozen set of test data, a manifest saying which step must catch which defect, and a checker that confirms it did. Turning that into a shared format would let other recipes be graded on what they catch, rather than only on whether they run.
