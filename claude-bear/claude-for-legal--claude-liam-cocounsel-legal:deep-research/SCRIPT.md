# SCRIPT.md — Claude, Cocounsel Legal: Deep Research. (hai-simple redo)

Register: Plain. Persona: Liam, in for Bear. Voice: Kokoro `am_onyx`.
Redo of `claude-liam-cocounsel-legal:deep-research` (Teardown, skill-teardown
format) — question and true generic facts carried over; narration
re-registered to Plain (explain, then stop); cold open replaced with the
BrutalistHesitantWriter; close carries the Humanitarians AI skin.

**Source-fidelity note:** the source never filled in deep-research's specific
"Claude's job: ___" line (literal `>` placeholder survives in four spots),
and its SKILL.md is not reachable from this machine (see QUESTION.md /
BUILD-LOG.md). This script keeps every fact the source DOES establish — a
skill is a folder Claude reads before it acts; it executes the file's steps
in order; it is a specification with a payoff and a limit; "legal research
and synthesis via Westlaw Deep Research" is the one literal preserved
description — and uses "deep-research" only as the named anchor example (a
skill-shaped folder aimed at producing a synthesized, cited research
answer), never asserting invented detail about the actual legal-research
procedure inside its unread SKILL.md.

## B00 — cold open (BrutalistHesitantWriter)
You'd guess Claude used its own legal judgment to dig up this research. It
didn't — it followed written instructions. Deep-research just names one
such file. Let's see what's actually inside it.

## Act I — the wrong guess

**B01 — Sounds like legal judgment**
Hear "cocounsel-legal has a deep-research skill" and it sounds like Claude
went and did open-ended legal research on its own — like it weighed the
cases itself and decided what mattered.

**B02 — Broken, with a case** (pays off B00)
But nothing about Claude's judgment changes. Delete the skill's folder and
Claude loses no legal reasoning — there was nothing added. It just stops
following that one procedure.

## Act II — the mechanism

**B03 — One file** (ANCHOR PLANTED)
Here's what a skill actually is: one file. Cocounsel-legal deep-research,
for instance, is a folder holding a single SKILL.md — instructions for
turning a research question into a synthesized, cited answer, using Westlaw
Deep Research, written in plain language Claude reads before it starts.

**B04 — Read it, then follow it in order**
Claude reads that file top to bottom and works through it step by step, in
the order it's written — no branching, unless the file itself says branch.

**B05 — Spec, not judgment**
That makes a skill a specification, not a new judgment. The payoff: the
same search-and-cite process, every question. The limit: anything outside
those written steps, and Claude is off the map.

**B06 — The anchor returns** (ANCHOR PAYOFF)
So deep-research never taught Claude legal judgment. It just guarantees
that every time the skill runs, Claude reads that same file and produces
the same searched-and-cited structure — that's the whole trick.

## Act III — both directions

**B07 — Neither one is proof**
Watching Claude produce a well-cited memo doesn't prove it exercised legal
judgment — a file can be followed to the letter on a question it never
really weighed. And watching it miss a case doesn't prove the skill is
broken — it may just be a source the file's steps don't reach.

## Close

**BCRY — carry-out**
A skill doesn't hand Claude legal judgment — it's a file of steps that
turns a research question into the same searched-and-cited answer, the
same way, every time.

**BHTF — your turn**
Your turn. Paste this into Claude: pick one research question I ask over
and over. Write me a SKILL.md for it — plain language, ordered steps — then
read it back to me and walk me through exactly what you'll do, before you
do it.

**BOUT — outro**
Claude, Cocounsel Legal: Deep Research. Liam, in for Bear.

## Six-move audit

| Move | Beat | Note |
|---|---|---|
| Stakes first | B00–B01 | "a deep-research skill" sounds like Claude exercising its own legal judgment |
| Wrong guess | B00 → B02 | "judgment" corrected to "instructions"; broken with the delete-the-folder case |
| Mechanism | B03–B05 | one file, read top to bottom, spec not judgment |
| Anchor | B03 → B06 | cocounsel-legal:deep-research's single SKILL.md, planted then returned to |
| Both directions | B07 | a well-cited memo proves nothing about judgment; a missed case proves nothing about breakage |
| Carry-out | BCRY | one sentence, survives repetition |

## Beat-count note (redo)

Source is 7 beats (B00, B01 anatomy, B02 pipeline, B03 design tell, BVDT
verdict, BHTF your-turn, BOUT outro) — a compact skill-teardown format with
no explicit wrong-guess, anchor, or both-directions beat. hai-simple's spine
requires all three as their own beats (WRONG-GUESS LAW / ANCHOR LAW /
BOTH-DIRECTIONS LAW), so this redo expands modestly: B01 (stakes) and B02
(wrong guess, broken) are new; B03/B04/B05 carry the source's anatomy/
pipeline/design-tell facts across to the anchor; B06 is a new anchor-payoff
beat restating the design tell against the named anchor; B07 (both
directions) is new. Result: B00 + 7 body beats + BCRY/BHTF/BOUT = 11 beats —
a small, proportionate expansion of a 7-beat source, not a scale mismatch
(matches the identical-shape expansion on the `claude-for-legal--claude-
liam-case-brief` and `claude-for-legal--claude-liam-build-guide` sibling
redos, which hit the same source-fidelity gap). No new legal-specific fact
was invented anywhere in this expansion beyond the one literal preserved
description ("legal research and synthesis via Westlaw Deep Research") and
the well-known generic shape of a research answer (sources found, synthesis,
citations).

## One-flag audit

No inference-flag beat: every claim here is about the generic, verifiable
mechanism of a Claude skill (folder + SKILL.md, read-then-execute,
specification semantics) plus the one literal preserved source description —
not an inference about an unread source. Nothing in this script asserts what
deep-research's specific legal-research procedure actually does.
