# One Retry, Never a Chain — Script

**Title:** One Retry, Never a Chain
**Slug:** hai-mycroft-retry (suggested)
**Sprint:** Mycroft Sprint 4 — Handle Failures
**Channel:** claude-hai · **Persona:** Simba · **Register:** Pragmatist · **Voice:** Kokoro `af_bella`
**Format:** ai-explainer, single 16:9 cut (matches the Sprint 3 router video's format; a 9:16 Shorts derivative can follow the same THE SHORTS LAW treatment if a full build is wanted later)



Pattern column is a suggestion, matching this series' established shapes. Unlike the last two builds in this series, this script needs **no new components** — every beat fits a shape already built and QC'd on `hai-mycroft-gateway`, `how-kv-cache-works`, `hai-mycroft-router`, or `hai-paged-attention`: `FactStack` (×2), `RouterFlow` (×1), `TestSuiteProof` (×1), `DataTable` (×2), `FindingPair` (×3), plus the four house components. GATE L can be a formality on this one if a full build is requested — the fit is already clear at the script stage.

## Beats

### B00 · INTRO — cold open
**Pattern:** `ClaudeComposerAsk` (reuse) · **Motion:** type-on

> Hi, I am Simba, and this one's the fourth Mycroft sprint — the one where the router finally gets to retry. One retry, ever, on the tier above — and the real question I built this sprint to answer: can a wrong answer in the right shape still slip through, with nothing catching it and no retry helping?

**On screen:** ask types in (condensed version of the question above); output lines land answered:
- "one retry, ever — on the escalation tier, never a chain"
- "24 fixtures, every deliberate trap: 0% failure"

### B01 · SUMMARY — BLUF
**Pattern:** `ClaudeStatement` (reuse) · **Motion:** fade

> The rule: retry happens exactly once, on the escalation tier, triggered by a free check failing. There's no retry loop in the code — so a chain of retries isn't just discouraged, it's structurally impossible.

**On screen — kicker:** THE RULE · **sparkLine:** "No loop exists, so a chain isn't a rule to remember — it's a shape the code can't take."

### B02 · STRUCTURE — validators.py
**Pattern:** `FactStack` (reuse) · **Motion:** illustrate

> validators dot py holds five checks, one per task type: the answer is an allowed label, the JSON has its required keys, a contradiction verdict actually quotes the input, a summary's numbers all appear in the input, and a RAG answer cites a passage. Two more checks run on everything, no matter the task: the answer isn't empty, and it isn't cut off.

**On screen — kicker:** VALIDATORS.PY — ONE CHECK PER TASK TYPE · **facts:**
- sentiment/topic answer is an allowed label
- structured extraction JSON has its required keys
- a contradiction verdict actually quotes the input
- a summary's numbers all appear in the input
- a RAG answer cites a passage

**closingLine:** Plus two universal checks on everything: not empty, not cut off.

### B03 · STRUCTURE — gateway.py + the adapter changes
**Pattern:** `RouterFlow` (reuse) · **Motion:** illustrate

> gateway dot py is the whole path: route to a tier, call the model, run the check, and if it fails, retry exactly once — on the tier above. That's the entire retry logic. No loop exists to walk back down or try a third time. And the adapters changed too: every failure now reports whether retrying could actually help. A bad API key, an unknown model, or a request that's simply too large are terminal — the gateway never retries those, because no retry fixes them.

**On screen:**
- **kicker:** THE GATEWAY — ROUTE, CALL, CHECK, RETRY ONCE
- **steps:** "request routed to its tier" → "model called" → "free check runs on the answer" → "check fails → retry once, tier above"
- **refuseNote:** bad key / unknown model / too large → terminal, never retried
- **omittedNote:** no second retry — the loop doesn't exist, so a chain can't happen
- **sparkLine:** One retry is a shape the code can take. A third attempt isn't a shape it has.

### B04 · WHAT WAS BUILT — tests and the bench run
**Pattern:** `TestSuiteProof` (reuse) · **Motion:** stagger

> bench slash run dot py runs every frozen fixture through the whole path and grades each answer against your key, writing both a log and a results file. Tests went from ninety-six to a hundred forty-six over the sprint.

**On screen — stats:** "96 → 146 tests" · **rules (numbered):**
1. validators.py — one free check per task type, plus two universal ones
2. prompts.py — one prompt per task type, each asking for exactly what its check will accept
3. bench/run.py — every frozen fixture, graded against your key, logged

**capstone:** First full graded run across all 24 fixtures — not a sample.

### B05 · RESULTS — the final sweep
**Pattern:** `DataTable` (reuse) · **Motion:** illustrate

> Final sweep, twenty-four fixtures: twenty-four requests became twenty-six attempts. Escalation happened on eight percent — two fixtures. Failure: zero percent. Total cost: zero point zero zero two five zero dollars, about a hundredth of a cent per request. Latency: three ninety-three milliseconds at the median, seven thirty-four at the ninety-fifth percentile. Of the twenty-four, sixteen were graded — fourteen correct.

**On screen — title:** THE FINAL SWEEP, 24 FIXTURES · rows: requests/attempts 24 → 26 · escalation 8% (2 fixtures) · failure 0% · cost $0.00250 total (~$0.0001/request) · latency p50 393ms / p95 734ms · **footnote:** 16 of 24 graded, 14 correct

### B06 · FINDINGS — the headline, and what the two flags actually were
**Pattern:** `FindingPair` (reuse) · **Motion:** illustrate

> This sprint was built around one worry: a model returning a wrong answer in the right shape, where no free check catches it and no retry helps. Across twenty-four fixtures, including every deliberate trap — that happened zero times. The two flagged fixtures turned out to be your answer key, not the model: sent dash oh-oh-one and sent dash oh-oh-four are keyed negative, both models answered positive, and the models are right. The cheap twenty-b model even got sent dash oh-oh-four correct — the exact headline where the negative words belong to a rival company, the same trap that once reached a finished brief.

**On screen:**
- **kicker:** THE WORRY THIS SPRINT WAS BUILT TO TEST
- Finding 1 — "THE FAILURE THAT DIDN'T HAPPEN" / "A wrong answer in the right shape, uncaught and unhelped by retry — across 24 fixtures, including every deliberate trap." / stat: **0%**
- Finding 2 — "THE TWO FLAGS WERE THE ANSWER KEY" / "sent-001 and sent-004 are keyed negative; both models answered positive — correctly. The cheap model caught the rival-company trap." / stat: **2 of 2**

### B07 · PROBLEMS — the quote check, and the model that vanished
**Pattern:** `FindingPair` (reuse) · **Motion:** illustrate

> Two things broke early. My quote check was too strict — all three first-sweep escalations were false alarms, because the models quoted both conflicting statements joined together, a reasonable answer the check rejected for wanting one contiguous span. Fixing the prompt dropped escalation from eleven percent to eight. And the strong tier's model just disappeared: qwen slash qwen3 point 6 dash 27b started returning 404 a week after working fine — Groq's own deprecation page still recommends it. Replaced with qwen3 point 8 dash 27b.

**On screen:**
- **kicker:** PROBLEMS HIT AND FIXED, PART ONE
- Finding 1 — "QUOTE CHECK TOO STRICT" / "All three first-sweep escalations were false alarms — models quoted both statements joined together; the check wanted one contiguous span. Escalation dropped 11% → 8%." / stat: **FIXED**
- Finding 2 — "THE STRONG TIER'S MODEL VANISHED" / "qwen/qwen3.6-27b started 404ing a week in — Groq's deprecation page still recommends it. Replaced with qwen3.8-27b." / stat: **FIXED**

### B08 · PROBLEMS — the token budget, and the double-counted log
**Pattern:** `FindingPair` (reuse) · **Motion:** illustrate

> The replacement model was then refused on every call — its 1,024-token budget exceeded the account's cap of 1,000 output tokens per minute. Lowered to 896, and it worked. And the summary itself was wrong once: a smoke run and the full sweep shared one dated log file, double-counting three requests — twenty-seven instead of twenty-four. Log files are now stamped to the second. One more thing broke on purpose: a test that hardcoded 1,024 broke the moment the budget changed — correctly.

**On screen:**
- **kicker:** PROBLEMS HIT AND FIXED, PART TWO
- Finding 1 — "TOKEN BUDGET EXCEEDED THE RATE CAP" / "The replacement model was refused on every call: 1,024 tokens exceeded the account's 1,000-output-tokens-per-minute cap. Lowered to 896." / stat: **FIXED**
- Finding 2 — "ONE LOG FILE, TWO RUNS" / "A smoke run and the full sweep shared one dated log file, double-counting 3 requests — 27 instead of 24. Log files now stamp to the second." / stat: **FIXED**
- **sparkLine:** A test that hardcoded 1024 broke when the budget changed — correctly.

### B09 · FINDINGS — escalation's real price
**Pattern:** `DataTable` (reuse) · **Motion:** illustrate

> Two numbers are worth keeping. First: escalated requests cost three point two times a normal one — zero point zero zero zero two eight two dollars against zero point zero zero zero zero eight eight. Two of twenty-four requests took twenty-three percent of the spend. Retrying is cheap in absolute terms and expensive in relative terms — which is exactly why the trigger has to be right.

**On screen — title:** ESCALATION'S REAL PRICE · rows: normal request $0.000088 · escalated request $0.000282 (3.2×) · **footnote:** 2 of 24 requests = 23% of total spend · **sparkLine:** Cheap in absolute terms, expensive in relative terms — which is why the trigger has to be right.

### B10 · FINDINGS — the cost ladder isn't monotonic
**Pattern:** `FactStack` (reuse) · **Motion:** illustrate

> Second: the cost ladder isn't monotonic. On the gate prompt, the strong tier cost twenty percent less than the cheap tier — despite a thirteen-times higher sticker price on output. Cheap spent seventy-seven tokens thinking; strong answered in two. The crossover sits around five output tokens, so on real work, strong is far more expensive. What it proves is narrower, and still useful: sticker ratio and real ratio can point in opposite directions.

**On screen — kicker:** THE COST LADDER ISN'T MONOTONIC · **facts:**
- on the gate prompt, the strong tier cost 20% less than the cheap tier
- despite a 13× higher sticker price on its output tokens
- cheap spent 77 tokens thinking; strong answered in 2

**closingLine:** Sticker ratio and real ratio can point in opposite directions — the crossover sits around five output tokens.

### B11 · SUMMARY — verdict
**Pattern:** `ClaudeVerdictArtifact` (reuse) · **Motion:** stagger

> So: one retry, on the tier above, and no loop for it to become a chain. Zero failures across twenty-four fixtures, including every deliberate trap — the two flags this sprint found were a wrong answer key, not a wrong model. And two numbers worth carrying forward: an escalation costs three times a normal request, and the sticker price doesn't predict the real one. Both the retry trigger and the tier choice need real numbers, not list prices.

**Artifact lines:**
- Delivered: one retry, structurally impossible to chain — five per-type validators, rewritten adapters, and a graded bench run for every fixture.
- Proven: 0% failure across 24 fixtures, including every deliberate trap — retry escalated on only 8%, and both flags were the answer key, not the model.
- Worth watching: escalation costs 3.2× a normal request, and sticker price doesn't predict real cost — the retry trigger and the tier choice both need real numbers.

### B12 · NEXT STEPS — handoff
**Pattern:** `ClaudeComposerAsk` (reuse) · **Motion:** type-on

> Your turn. If you're pricing tiers by sticker rate alone — have you actually checked where your own cost ladder crosses over? It might not be where the price list says.

### B13 · OUTRO
**Pattern:** `ClaudeTitleOutro` (reuse) · **Motion:** fade

> One retry, never a chain. Simba, for Humanitarians AI.

**On screen:** title restate, terracotta period, handle, subline "one retry · zero failures · Mycroft."

---

## Sources
The Mycroft Sprint 4 report ("Handle Failures") as pasted directly into this session — board goal, `validators.py`/`prompts.py`/`gateway.py`/`bench/run.py`/adapter changes, the 96→146 test count, the 24-fixture final sweep (24/26 requests, 8% escalation, 0% failure, $0.00250 total cost, p50 393ms / p95 734ms latency, 16/24 graded with 14 correct), the sent-001/sent-004 answer-key correction, the five problems hit and fixed (quote-check strictness, the vanished qwen3.6-27b model, the 1,000-tokens-per-minute rate cap, the double-counted log file, the hardcoded-1024 test), and the two cost findings (3.2× escalation premium, the non-monotonic gate-prompt cost ladder). Every figure in this script is drawn from that report; nothing was estimated or invented.
