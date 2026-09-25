# Beat Sheet — Prefill vs. Decode (Shorts)

**Channel:** claude-hai · **Persona:** Simba · **Voice:** Kokoro `af_bella`
**Format:** ai-explainer, condensed · **Aspect:** 9:16 (2160×3840) · **Total runtime:** 0:39 (39.17s, Kokoro ground truth)

THE SHORTS LAW derivative of `hai-prefill-decode`: single cycle, no revision, condensed subset of the long cut's beats (hook, both diagrams, verdict, outro), reusing `ParallelPass`/`AutoregressiveLoop` via their new `916` portrait compositions, pointing back to the long cut.

| Beat | Act | Timestamp | Duration | Pattern | Note |
|---|---|---|---|---|---|
| B00 | INTRO | 0:00 | 8.57s | `ClaudeComposerAsk916` | Condensed hook question |
| B01 | STRUCTURE | 0:09 | 7.01s | `ParallelPass916` | Prefill diagram, portrait |
| B02 | STRUCTURE | 0:16 | 9.34s | `AutoregressiveLoop916` | Decode diagram, portrait |
| B03 | SUMMARY | 0:25 | 9.70s | `ClaudeVerdictArtifact916` | Two-bottleneck verdict |
| B04 | OUTRO | 0:35 | 4.56s | `ClaudeTitleOutro916` | Points back to the long cut |

## Build note
`ParallelPass916` and `AutoregressiveLoop916` composition IDs were added to `Root.tsx` this build — both diagram components were already responsive to portrait (built with `useVideoConfig` + `portrait = height > width`, matching this reel's existing house-component convention), so no new component code was needed, only the portrait `<Composition>` registration. `tsc --noEmit` clean.

Compile emitted two informational SKIN LINT notices (COLD OPEN LAW / OUTRO LAW expecting the base `ClaudeComposerAsk`/`ClaudeTitleOutro` ids) — expected false positives, since `...916` ids point at the same components under their portrait registration; not a defect.
