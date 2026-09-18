# Chaitanya Malepati

Humanitarians AI fellow. Weekly research-log teardowns of the **Medhavi** hub
(`medhavi-hub`) — subsystem audits documented as they happen, in the Brutalist
format. Video projects live in one dated lowercase-kebab folder per episode,
`YYYY-MM-DD-slug/`, with a `beat_sheet.json` and a README.

## Voice choice

**Series voice:** Bella (`af_bella`) — the `hai` persona.
**Register:** Pragmatist — method, when to use it, when not to.

Recorded as `metadata.voice_kokoro` in every beat sheet. Kept across the series
unless another explicit, documented re-voice decision is made.

### Re-voice decision — 2026-09-17

The series opened on Onyx (`am_onyx`). It is now **Bella (`af_bella`)**, decided
deliberately and recorded here, which is what `fellows/README.md` requires of a
voice change.

| | |
|---|---|
| **Was** | Onyx (`am_onyx`), locked at the first reel (2026-08-28, Concept Map) |
| **Now** | Bella (`af_bella`), from the second reel (2026-09-13, Memory API) onward |
| **Reason** | Bella is the voice the repo documents as the `hai` persona, and it is one of only two Kokoro voices the installed toolkit ships. Settled at episode two rather than left to accumulate |

**Consequence:** [What Is a Concept Map](2026-08-28-what-is-a-concept-map/) is
now the outlier — it is `am_onyx` and stays that way on disk. Re-voicing it is
optional and cheap in effort but not free: audio is the clock, so new narration
changes every beat duration and forces a re-cut of both masters. Worth doing if
the series is ever published as a set; not worth blocking on otherwise.

## House style

These reels are **Brutalist, not Claude-branded `ai-explainer`s**. Hard cuts,
no music bed, two type families, and no Claude framing: no `ClaudeComposerAsk`
cold open, no verdict page, no HANDOFF beat, no channel logo bug. Departures
from `ai-explainer` frame law are enumerated per-episode in that episode's
`BUILD-LOG.md`.

Beyond that, each reel takes its visual identity from the artifact it is about,
so the palette is per-episode rather than series-wide:

| Reel | Brand | Palette | Type |
|---|---|---|---|
| Concept Map | `brutalist-script` | `#0A0A0A` / `#F2F0EB` / `#E8452C` / `#6B6B6B` | Helvetica Neue Bold + Menlo |
| Memory API | `brutalist-deck` | `#000` / `#fff` / `#FFE500` / `#FF3B00` | Archivo Black + IBM Plex Mono |

Two episodes, two identities. Defensible per-reel — the Memory API deck is a
real artifact that came with its own design, and rendering it as-is beats
re-skinning it — but worth settling as a deliberate policy rather than letting
it accumulate.

Visuals are always produced **out-of-tree** and dropped into per-beat `media/`
slots, so the brutalist toolkit stays **read-only** and is used only for Kokoro
narration, conform/mux, and the 9:16 derivation. The renderer differs per reel:
a deterministic Pillow script for Concept Map, headless Chrome capturing the
real deck for Memory API.

## Reports

| Date | Title | Subject | Runtime | Status |
|---|---|---|---|---|
| 2026-09-13 | [Memory API](2026-09-13-memory-api/) | Cross-book learner memory — two tables, the `memory_subject` convention, and the fact that no textbook calls it yet | 2:51 | Built · fact-checked · GATE P signed · not published |
| 2026-08-28 | [What Is a Concept Map](2026-08-28-what-is-a-concept-map/) | Concept Map subsystem audit — schema, S3 layer, review gate, and the verified output's zero consumers | 3:49 | Built · QC'd · fact-checked · GATE P signed · not published |

GATE P is signed on both reels (2026-09-17). That signature covers the
**narration** — it is not a QC sign-off and not a fact-check sign-off; each
reel's README lists what remains open.

Both reels land on the same finding from opposite ends of the hub: the
machinery is built and correct, and nothing downstream consumes it. Worth
naming as a pattern if a third one does it too.

## Media policy

Rebuild with the free local toolkit
([brutalist.art](https://github.com/nikbearbrown/brutalist.art)). MP4, MP3,
per-beat renders, `pantry/` overrides and `_qc/` frames are never committed —
they stay local and gitignored. What lands here is the text package: beat
sheets, scripts, shot list, fact check, sources, pedagogy sign-off, build log,
the renderer, and — where the visuals come from one — the source deck.

Measured `mp3/timings.json` **is** committed despite the media rule. It is text,
it is the clock each reel was cut to, and the visuals cannot be re-conformed
without it.
