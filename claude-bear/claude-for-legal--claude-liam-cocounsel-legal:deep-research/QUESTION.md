# QUESTION.md

**Question:** Claude picked up cocounsel-legal's "deep-research" skill — did
it go off and research the law using its own legal judgment, or is that not
what's going on?

**Who asked / where:** Redo-mode reel. Source question carried over from the
locked source script (`claude-liam-cocounsel-legal:deep-research`, a
Teardown skill-explainer under `anthropics/claude-for-legal/`). Not a live
viewer submission.

**Name usable:** N/A (no submitter).

**Source-fidelity note:** the source's beat_sheet.json never received its
skill-specific "Claude's job: ___" fill — the literal placeholder `>` is
still present in four places (B00, B03, BVDT, BHTF), the identical bug
already documented on the `claude-for-legal--claude-liam-case-brief` and
`claude-for-legal--claude-liam-build-guide` sibling redos. The SKILL.md it
was meant to describe
(`/Users/bear/Documents/CoWork/bear-textbooks/books/anthropics/claude-for-legal/external_plugins/cocounsel-legal/skills/deep-research/SKILL.md`)
does not exist on this machine — confirmed by direct `ls` and by `find`
across the whole local `anthropics/claude-for-legal/` tree (only `youtube/`
exists locally; no `external_plugins/` directory). See BUILD-LOG.md for how
this redo handled the gap: the source DOES establish real, generic, true
facts about how a Claude skill works (a folder Claude reads before it acts,
one file — SKILL.md — read top to bottom and executed step by step, and the
specification semantics: repeatable results in exchange for a hard limit at
the file's edge), plus one literal preserved fact from the source's own
narration — "Legal research and synthesis via Westlaw Deep Research." What
did NOT carry over, because it was never actually present in the source: any
specific claim about what cocounsel-legal's deep-research procedure actually
searches, weighs, or writes. This redo treats "deep-research" literally and
generically — the named example of a skill-shaped folder, using only the
well-known, generic shape of a legal research answer (sources found, an
answer synthesized, citations attached) as anchor flavor — and never asserts
an invented procedure from the unread SKILL.md.
