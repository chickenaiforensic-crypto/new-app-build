# BUILD ORDER — v1.25.0 → v1.26.0

**Clean Inputs · True Surface · Per-System Calls**

Issued: 2026-09-09 · **Re-cut 2026-09-09** after the Owner's per-system ruling ·
Canonical home: `/Users/thecreator/Projects/the_games/Bets/master_app/project_4/`

> **SUPERSEDES `BUILD_ORDER_2026-09-08_v1.26.0.md`, which is NOT authorised and must not be built.**
> This file replaces the earlier 2026-09-09 cut in place — one order, current content only. The
> earlier cut was sequenced around the Master Call; the Owner has since ruled that the Combiner is
> **not** the current focus. That reordering, plus a lookahead leak found while testing the new
> direction, changes what comes first. The 2026-09-08 order moves to `_quarantine-for-deletion/`
> on the Owner's clearance.

You are building against **one file**: `Dalxic Stats Engine v1.25.0.dc.html` (18,391,941 bytes).
Read this order top to bottom before touching it. The contract is `DALXIC_BUILD_CONSOLIDATED_v3.8.md`
(→ v3.9 at Stage 6). Where this order cites a `§`, that is the spec.

---

## 0 · OWNER RULINGS THAT SHAPE THIS ORDER

**R1 — the purpose (2026-09-09).** *"Our purpose is to let the UI read true to simple computation."*
Every figure and every sentence the surface prints is verifiably true, or it does not ship.
"Consistent" is not the bar.

**R2 — each system calls on its own (2026-09-09).** *"The master call is not being done now — we are
focusing on having each system call on its own. We will analyse backtest to auto-calibrate gaps and
call thresholds that will then be used as parameters for calls that produce the best accuracy
reflection."*

The Combiner (`blendOf`, the Master Call, M-Fit's blend-weight search) is **deferred**. The seven
systems each produce their own call, gated by a per-system gap that is fitted from a backtest.

**R3 — swap is presentational, and that is all (2026-09-09).** *"The swap is just there to flip
around and that is not home and away. Home and away will be made into its own signal for qualifiers
etc."*

`predReferenceOrder` takes **two arguments**. No `homeSide`, no hook, no plumbed placeholder — a
parameter that is always `null` is placeholder energy (B0.15). Home/away arrives later as **its own
signal with its own qualifier grammar**, exactly like Signal 4's `:{surface}`. It never becomes an
ordering override.

**R4 — no forced symmetry in the signals (2026-09-08, standing).** `oo2Of`, `oo3Of`,
`commonOpponentsOf`, `ratingOf`, `tpiOf`, `h2hOf` — **no formula is touched by this order.**

**R5 — leak fix (b), Owner-approved 2026-09-09.** The backtest excludes the match under test **by
row id**, not by shifting the moment back a day. A same-day earlier-round match is legitimately
prior and must keep counting.

**R6 — the drafter writes the spec section (2026-09-09).** The per-system call is not in the Build
Document. It is drafted here as **§5A** (Stage 5) for the Owner to accept before Stage 5 is built.

---

## 1 · THE SEQUENCE — six stages, 22 parts

Each part is independently verifiable and lands in order. Nothing outside these parts is authorised.
Ambiguity → **stop and ask** (§0.4).

| Stage | Why it is here | Parts |
|---|---|---|
| **0 · SIGNAL VERIFICATION** | Proves each signal computes the number the contract specifies. **Nothing today proves this** — 0 of 33 signal fixtures assert a value. | V1–V3 |
| **1 · CLEAN INPUTS** | Nothing calibrated on leaked data is worth anything. This is the foundation. | L1 · L2 |
| **2 · WRONG NUMBERS** | A figure that is wrong, or a value that is `NaN`, before any cosmetics. | W1 · W2 · W3 · W4 |
| **3 · FALSE STATEMENTS** | Sentences the surface prints that are not true. | F1–F8 |
| **4 · ORDER STABILITY** | Scoped to **OO2/OO3 only** — the two systems whose answer changes with typing order. Prerequisite for calibrating them. | O1 · O2 · O3 · O4 |
| **5 · PER-SYSTEM CALLS** | R2's actual ask. **Gated on the Owner accepting §5A.** | S1–S5 |
| **6 · CLOSE-OUT** | Spec v3.9, docs, vBump. | C1 · C2 · C3 |

**Deferred by R2, not cancelled:** the Master Call display-inversion, M-Fit's blend-weight search,
and the Combiner's order-dependence. Each returns with its own `proceed`.

### 1.1 · Fixture arithmetic

Base **78**. V3 `+9` (one per signal + the §3 pipeline), L1 `+1`, W2 `+1`, O4 `+1`,
S5 `+2` (one refusal, one control) → **92**.

> **92 fixtures — 65 proven-red · 9 arithmetic-proven · 3 OPEN-exemption (proven NOT to fire) · 15 control-clean · 0 open.**

**`arithmetic` is a fourth population and must not be folded into the other three.** A refusal fixture
proves a gate can go red; a control proves the gates stay silent; an exemption proves a check
correctly does not fire; an **arithmetic** fixture proves a signal returns the *right number*. Today
the build has none of the fourth kind.

The shipped line reads *"64 proven-red"*. **It was never right** — three of those 64 are §2.5.1
exemption fixtures that prove a check correctly does **not** fire. F1 corrects it to 61 in the
record before this order's additions take it to 65. **Correct it; never increment it.**

### 1.2 · What was pre-executed while drafting this order

Not proposals — these were implemented against the real engine and run on the live vault:

| Check | Result |
|---|---|
| Full suite after F1 + W1 + W2 + O1 + O4 | **80 fixtures — 63/63 proven-red · 3/3 exempt · 14/14 control · 0 open**, 12 scopes |
| Live vault under the same patches | 0 row refusals · 0 edition refusals · 14,795 rows · 201/201 editions · registry 830 — **unchanged** |
| O4 mutation test (stub `predReferenceOrder` to input order) | fixture goes **RED**, suite `open: 1` — the gate can fail |
| W2 typo weight | `refusal: "BLEND_WEIGHTS_INVALID", invalid: ["h2h"]` — no `NaN` reaches the surface |
| W1 corrected id | `rating:player:{id}:Clay@{date}` → `1.561 (Clay)`; the shipped id → `1.632 (baseline)` |
| O1 canonical node | identical `value`/`cls` from either typed order on **91/91** live pairs |
| **L1 leak, measured** | see §4 — H2H inflated **+26.0 pts**, Surface **+22.0 pts** |

Exact fixture JSON for L1, W2, O4 and S5 is given verbatim. Nothing here is "tune it until it passes".

### 1.3 · What this order CANNOT make true

**Yes:** after Stages 1–4, no figure on any of the seven pages is wrong, no sentence beside one is
false, and no system's inputs contain its own answer. After Stage 5 each system calls on its own,
with a gap fitted from clean data.

**No:** the Combiner's order-dependence remains (deferred by R2), and OO2/OO3 path selection is still
internally asymmetric — Stage 4 makes their reads **stable**, not **mirrored**. Removing that needs a
change to locked §5 internals and its own authorisation. Logged as §13.1 row 8, not hidden.

---

## 2 · ANCHORS — confirm every one by its quoted string

Engine script: file lines **461,929 – 466,243**. Line numbers below are **within the engine script**
(1 = `// DALXIC STATS ENGINE — one file.`).

| Region | Engine lines |
|---|---|
| R1 · CONFIG | 1 – 603 |
| R2 · COMPUTE | 604 – 2018 |
| R3 · LEDGER | 2019 – 2605 |
| R4 · SURFACE | 2606 – 4313 |

| What | Line | Quoted anchor |
|---|---|---|
| `priorMatchesOf` boundary | 1278 | `if (inclusive ? d > bound : d >= bound) continue;` |
| `opponentsOf` boundary | 1353 | `if (c.playerAId === playerId && String(c.date) <= bound)` |
| `pointsVsOpponentOf` boundary | 1366 | `if (!isVs \|\| String(c.date) > bound) continue;` |
| `hopRatioOf` boundary | 1448 | `for (const row of arr) if (String(row.date) <= bound) { c = row; break; }` |
| `ratingOf` negligible flag | 1328 | `const negligible = isSurface && Math.abs(shareA - 0.5) <= cfg.signalSurfaceNegligibleGap;` |
| `rowChecksOf` winner-domain push | 826 | `if (cfg.winnerDomain.indexOf(c.winner) < 0) out.MISSING_PLAYER.push(i);` |
| `blendOf` signature | 1558 | `function blendOf(pA, pB, atDate, surface, canon, cfg, liveCounts) {` |
| `blendOf` weight sum | 1590 | `for (const r of speaking) { wSum += r.weight; wrSum += r.weight * r.ratio; }` |
| `runFixturesOf` partition | 1998 | `const refusal = runs.filter(r => r.fx.code !== "CONTROL");` |
| `refusal:check` fixture label ×2 | 2550, 2561 | `"proven · step 3 green" : "not built"` |
| `mfitRatiosOf` | 2704 | `function mfitRatiosOf(pA, pB, atDate, surface, canon, cfg, liveCounts, pairIndex) {` |
| `runMFit` scope build | 3099 | `const ratios = mfitRatiosOf(c.playerAId, c.playerBId, c.date, c.surface,` |
| `commitRows` DECISION row | 3752 | `Object.assign({ label: "DECISION", value: cm.decision === "OVERWRITE"` |
| Prediction resolve | 3832 | `const rA = this.resolvePredTarget(st.predA, m, M.registry);` |
| Prediction refusal branch | 3840 | `if (rA.unresolved \|\| rB.unresolved) {` |
| `nodeOf` map | 3868 | `const nodeOf = {` |
| **`nodeOf.surface` — the W1 bug** | **3872** | `surface: "rating:player:" + rA.id + "@" + st.predDate + (st.predSurface` |
| `predRows` map | 3878 | `predRows = (node.rows \|\| []).map(r => {` |
| Gates fixture row verdict | 4052 | `verdict: r.fx.code === "CONTROL" ? (r.pass ? "PROVEN CLEAN"` |
| Gates FIXTURES tip | 4061 | `Four codes carry two fixtures, at row and at payload scope` |
| Gates SCOPES tip | 4070 | `and section 5 signals 1-4.` |
| Gates verdict banner | 4077 | `gateVerdict = F.open` |

---

## 3 · HOW TO RUN & VERIFY

### Browser
```
cd /Users/thecreator/Projects/the_games/Bets/master_app/project_4
python3 -m http.server 8899
# open  http://localhost:8899/Dalxic%20Stats%20Engine%20v1.26.0.dc.html   (after the rename)
```
Good state: header `v1.26.0`, `GREEN · 0 REFUSALS`, `ROWS 14,795`; all 7 pages render; boots with
DevTools → Network → Offline; zero external requests.

### Headless
Extract the engine script, keep R1–R3 (cut at `// ================= REGION 4 · SURFACE`), pull the
three payloads, drive `configOf` → `modelOf` → `carve` → `ingestOf` → checks → `buildLedger` →
`runFixturesOf`.

**Green baseline to hold:** `CONFIG_ABSENT none` · 14,795 canon rows · 0 row refusals · 0 edition
refusals · 201/201 editions · registry 830 · `DECLARATION_CONFLICT` 3 · **83 fixtures, 0 open** ·
GREEN true. Then `node --check` the **full** engine script (R4 included).

---

# STAGE 0 · SIGNAL VERIFICATION

> **Why this stage exists.** The Owner asked for confirmation that every signal is computed
> accurately, one after the other. **That confirmation cannot be given from the build as it stands**,
> for three evidenced reasons:
>
> 1. **No gate proves a signal's arithmetic.** All **33** signal- and score-scope fixtures assert
>    either *"it refused with code X"* or *"it did not refuse"*. **Zero assert a value.** Every
>    refusal path is proven; not one number is.
> 2. **The contract contradicts itself**, so "accurate" is undefined in places. §13.1 already logs
>    seven disagreements, two of them signal formulas (Signal 3, Signal 5). A partial reconciliation
>    of §5 while drafting this stage found **two more that are not logged** — see V1.
> 3. **The order's other stages do not close this.** Stages 1–6 make the surface truthful, the
>    measurement clean and the reads stable. None of them verifies a formula.
>
> **What the same partial pass did confirm** — and this is the good news: where the contract is
> unambiguous, the engine matches it. OO2's `(R1 × R2) ÷ R3`, OO3's `(R1 × R2) ÷ (R3 × R4)`,
> TPI's strict 7-match window and Signal 1's window ratio all reconcile **exactly** against §5.
> The hard arithmetic looks right. It is simply **unproven**, and "looks right" is not the bar.

## V1 — RECONCILE EACH SIGNAL AGAINST THE CONTRACT

One signal at a time, in this order: §3 pipeline → S1 rating → S2 tpi → S3 common → S4 surface →
S5 h2h → S6 oo2 → S7 oo3 → S8 fatigue. For each: read the §-text and the engine function side by
side and record **match** or **departure**. Do not change a formula (§0.4). Every departure becomes
a §13.1 row for the Owner.

**Already logged (§13.1):** #1 Signal 5 "1.0 = never-played" · #2 Signal 3 pooled-vs-median.

**Found while drafting this stage — NOT logged, and both need a §13.1 row:**

| New | This document says | The engine does | Consequence |
|---|---|---|---|
| **A** | **§5 Signal 4** (line 251) — ledger node `rating:player:{id}@{date}:{surface}` — qualifier **after** the moment | **§6** (line 309) — grammar `{quantity}:{subject}[:{qualifier}][@{moment}]` — qualifier **before** the moment. `parseNode` implements §6 | **This is the root cause of W1.** The PREDICTION card follows §5 Signal 4 literally; the parser follows §6. Neither was careless — the contract says both. §6 is the parseable one (a date cannot be a qualifier), so **W1's fix must also correct §5 Signal 4's node id** |
| **B** | **§5 Combiner** (line 302) — "cut-points (Clear, Plain, Tight) applied to the **Blended Ratio**" | Cut-points applied to `underdogShare = min(shareA, 1−shareA)` — a share, not a ratio | **§3 Stage 5** (line 202) says the cut-points map *"the loser's **share** of the match budget"*. §3 and the engine agree; §5's Combiner line is wrong. The cut-points are 0.40 / 0.25 / 0 — meaningless on an unbounded ratio |

**§13.1 says its list "is not asserted to be exhaustive." Two more in one partial pass is the
measure of how much of §5 has never been reconciled.** V1 completes the pass.

## V1b — THE FIRST TRACE, DONE. SIGNAL 1, ONE MATCH.

Owner instruction 2026-09-09: *"pull out the first match in the system and follow its computation."*
Subject: **`AUSTRA-ATP-2021-R128-008`**, 2021-02-08, Australian Open R128, Hard —
**Denis Shapovalov def Jannik Sinner `3-6 6-3 6-2 4-6 6-4`** (Sinner's first match in the vault).

**The arithmetic is correct.** Hand-derived from §3 and checked against the engine:

| set | token | hi-lo | reduced | Shapovalov games/pts/flat | Sinner games/pts/flat |
|---|---|---|---|---|---|
| 1 | 3-6 | 6-3 | 3-6 | 3 · 4 · 0.4 | 6 · 10 · 1.0 |
| 2 | 6-3 | 6-3 | 6-3 | 6 · 10 · 1.0 | 3 · 4 · 0.4 |
| 3 | 6-2 | 6-2 | 6-2 | 6 · 10 · 1.0 | 2 · 2 · 0.2 |
| 4 | 4-6 | 6-4 | 4-6 | 4 · 4 · 0.4 | 6 · 10 · 1.0 |
| 5 | 6-4 | 6-4 | 6-4 | 6 · 10 · 1.0 | 4 · 4 · 0.4 |
| | | | **TOTAL** | **3.8** | **3.0** |

Engine returns `winnerSum 3.8 · loserSum 3.0`. **Hand and engine agree exactly.** Set 1 — a set the
match winner *lost* — scores 4 : 10 the right way round, so the v1.12.1 fix holds on live data.
**Signal 1: own points 3.0 (Sinner) · opp points 3.8 (Shapovalov) · Rating 0.789.** The own/opp
numbers the Owner asked about are right.

**Three things around them are not. Two are new.**

### V1b-1 · The rating is built from the match it is being asked about *(this is L1, made concrete)*
`rating:player:jannik-sinner@2021-02-08` → `matches used: 1`, `FROM WHAT: row 3945`.
**Row 3945 is `AUSTRA-ATP-2021-R128-008` — the match itself.** Sinner's rating "as of" that day is
derived 100% from the match played that day. He lost it, so Signal 1 rates him 0.789 **because of
the result it is being asked to predict.**
→ **Widens L1.** L1 was scoped to the backtest harness. This trace shows the *Fact Checker* shows it
too, on any historical read. A live future fixture is unaffected (the match is not in the vault).
L1's acceptance must include a Fact Checker read, not only a backtest.

### V1b-2 · **LANDED 2026-09-09** — the Stage-4 divisor read the future, and it changed a displayed class
`flat:AUSTRA-ATP-2021-R128-008` shows `winner ÷ divisor 155 · loser ÷ divisor 311` — Shapovalov's and
Sinner's **whole-career** match counts, through the vault's last date of **2026-07-12**, applied to a
**2021-02-08** match. As at the match date both had played **1**.

| divisor basis | loser share | class |
|---|---|---|
| career totals (**shipped**) | 28.2% | **Plain** |
| totals as at the match date | 44.1% | **Tight** |
| no divisor | 44.1% | **Tight** |

**The class of a 2021 match is decided by matches played in 2022-2026, and silently changes every
time the vault grows.** §6 requires a strict temporal cutoff; **`flat:{id}` carries no `@moment` at
all**, so it cannot express one. The Owner ruling of 2026-09-07 set the divisor to "the player's
total matches played" but did not say *as at when* — so this is a **§13.1 row needing an Owner
ruling**, not a defect the developer may fix alone (§0.4).

> **OWNER RULING 2026-09-09 — option (a), counts as at the match date. Non-negotiable.**
> *"Using 2026 career totals to classify a 2021 match is a direct violation of §6 (Strict Temporal
> Cutoff) and Law B0.5. A match's classification must not change retroactively just because the
> player played more matches five years later."*
>
> **BUILT AND VERIFIED, 2026-09-09** — in `Dalxic Stats Engine v1.26.0-wip.dc.html`:
> - `liveMatchCountsOf` → **`matchDateIndexOf`** (per-player sorted match dates, built once per memo
>   epoch) + **`matchesPlayedAsOf`** (binary search, matches on or before the row's own date,
>   counting one played that same day). All 53 `liveCounts` references renamed `dateIndex` so the
>   name states what it carries.
> - `flat:{id}` inputs now read `÷ N matches played by {date}` and the basis line cites §6.
> - The score-scope fixture's stub counts became a real date index; **no assertion weakened**.
>
> | Check | Result |
> |---|---|
> | `AUSTRA-ATP-2021-R128-008` | divisors **155/311 → 1/1** · loser share **28.2% → 44.1%** · class **Plain → Tight** |
> | matches actually played by 2021-02-08 | Shapovalov 1 · Sinner 1 — the divisor now matches reality |
> | Live vault | 14,795 rows · 0 row refusals · 0 edition refusals · 201/201 editions · registry 830 — **unchanged** |
> | Fixtures | 78 total · 64/64 refusal-population · 14/14 control · **0 open** |
> | **Signal values** | **344 readings compared before/after — zero moved.** Every signal reads the *pre-divisor* sums, so Signals 1-7 are byte-identical, as required |
> | Scale of the leak | **3,654 of 14,624** scoreable matches re-classified (25%): Tight→Plain 1004 · Plain→Clear 800 · Plain→Tight 784 · Clear→Plain 546 · Tight→Clear 298 · Clear→Tight 222 |
> | File integrity | all three payloads byte-identical · engine round-trips exactly · `node --check` OK |

### V1b-3 · NEW — the descent flips perspective without saying so
The rating node says **own 3.0 · opp 3.8**. Descend to `points:AUSTRA-ATP-2021-R128-008` and set 1
reads **`3-6 · flat 0.40 / 1.00`** — column 1 is **Shapovalov**, the match *winner*. For a match
Sinner **won**, column 1 would be Sinner. **Nothing on the node says which column is "own".**
The §10 **lineage** gate — *"every figure traces to source rows via the FROM WHAT descent"* — fails
on the exact question asked: you can reach the row, but not see how it contributed to the figure you
started from.
→ **Fix:** `points:{id}` accepts the reading player as a qualifier — `points:{id}:{playerId}` — and
labels its columns `own` / `opp` for that player, falling back to `winner` / `loser` when no
qualifier is given. Built through `nodeIdOf` (W1), so the qualifier precedes the moment.

**This is the shape every V1 signal trace must take:** hand-derive, compare, then say what is wrong
*around* a correct number. Signal 1 is done. Eight to go.

## V1c — FROM WHAT MUST BE COMPLETE AND SELF-RECONCILING (Owner instruction, 2026-09-09)

Owner, on `rating:player:jannik-sinner@2026-09-08`: *"It hard fixes 40 OF 303 SHOWN — no way to see
the others… there's no left and right scroll that will further breakdown each score into points then
convert to ratings then the difference… so that right from there the system feeds off its accuracy."*

**Audit of that exact node.**

| Finding | Measured |
|---|---|
| **1 · 263 of 303 rows unreachable** | `source_rows_shown` = 40, applied as a hard `slice(0, 40)`. No page, no scroll, no search. The 40 visible rows sum to **own 94.6 / opp 45.9** against a headline of **712.9 / 422.5** — the operator can reconcile **13%** of the figure. The §10 **lineage** gate cannot be satisfied. |
| **2 · 8 rows silently dropped** | Sinner holds **311** rows at or before the moment. The signal used **303**. **8 are excluded and appear nowhere** — not listed, not counted, not named. `ratingOf` does `if (!p.ok) continue;`. |
| **3 · no per-row breakdown** | Columns stop at `SCORE` and `RND`. Nothing shows how a row contributed, so the headline cannot be checked by eye. (This is V1b-3, now the Owner's own finding.) |

**The 8 dropped rows, named for the first time:**
```
CINCIN-ATP-2024-R16-006  2024-08-16  "W/O"  WALKOVER            MADRID-ATP-2024-QF-004  2024-05-02  "W/O"  WALKOVER
INDIAN-ATP-2021-R32-013  2021-10-12  "W/O"  WALKOVER            MONTRE-ATP-2023-R16-008 2023-08-11  "W/O"  WALKOVER
INDIAN-ATP-2022-R16-006  2022-03-16  "W/O"  WALKOVER            PARISM-ATP-2023-R16-008 2023-11-02  "W/O"  WALKOVER
CINCIN-ATP-2025-F-001    2025-08-18  "5-0"  UNPARSEABLE_SCORE (retired)
MIAMI-ATP-2022-QF-001    2022-03-30  "4-1"  UNPARSEABLE_SCORE (retired)
```
Seven walkovers and two retirements written as part-sets. **B0.3 says every absence is a named
refusal carrying its reason.** The refusals exist inside the engine; the surface never shows them.

### V1c-1 · `ratingOf` returns its lineage (additive — no number moves)

`ratingOf` gains a `lineage` array alongside `rowIdxs`. **`value`, `ownSum`, `oppSum` and
`matchesUsed` are unchanged** — this records what the function already decided, it does not
re-decide it. The `continue` that drops an unscoreable match records it instead:
```js
for (const c of rows) {
  const p = ownOppPointsOf(c, playerId, cfg, liveCounts);
  if (!p.ok) { lineage.push({ rowIndex: c.rowIndex, used: false, refusal: p.refusal }); continue; }
  ownSum += p.own; oppSum += p.opp; used++; rowIdxs.push(c.rowIndex);
  lineage.push({ rowIndex: c.rowIndex, used: true, own: p.own, opp: p.opp,
    runOwn: round4(ownSum), runOpp: round4(oppSum) });
}
```
`considered = lineage.length` is also returned. **B0.13 — the running totals are produced here, in
R2, never on the surface.**

### V1c-2 · The ledger carries it

The `rating` branch returns `lineage` on the node and sets `sourceRows` to **every considered row**,
used or not. New inputs: `matches considered` (311) beside `matches used` (303) and
`excluded` (8). The `points:{id}` descent gains the reading player as a qualifier —
`points:{id}:{playerId}` — labelling its columns `own`/`opp` for that player and falling back to
`winner`/`loser` unqualified (V1b-3). Built through `nodeIdOf`, so the qualifier precedes the moment.

### V1c-3 · The columns the Owner asked for

`FROM WHAT` gains five columns to the right of `RND`, inside an `overflow-x:auto` container so the
table scrolls left and right without the page doing so:

| MATCH ID | DATE | WINNER | LOSER | SCORE | RND | **OWN** | **OPP** | **DIFF** | **RATIO** | **RUNNING** |
|---|---|---|---|---|---|---|---|---|---|---|
| …-2026-F-001 | 2026-07-12 | Sinner | — | 6-7(7) 7-6(2) 6-3 6-4 | F | 3.7 | 2.5 | +1.2 | 1.480 | 1.480 |
| …-2026-SF-001 | 2026-07-10 | Sinner | — | 6-4 6-4 6-4 | SF | 3.0 | 1.2 | +1.8 | 2.500 | 1.811 |
| …-2026-QF-002 | 2026-07-07 | Sinner | — | 7-5 7-6 6-3 | QF | 3.0 | 1.5 | +1.5 | 2.000 | 1.865 |
| … | | | | | | | | | | |
| AUSTRA-…-R128-008 | 2021-02-08 | Shapovalov | Sinner | 3-6 6-3 6-2 4-6 6-4 | R128 | 3.0 | 3.8 | −0.8 | 0.789 | **1.687** |

**The last row's RUNNING is the headline.** Verified end to end: running totals close at
**712.9 / 422.5** and **1.687**, identical to the node. **The figure becomes checkable by eye, which
is the whole point of the descent.**

> **OWNER RULING 2026-09-09 — RUNNING is locked to newest-first.** The table is fixed to
> newest → oldest and the column is labelled **`RUNNING (Newest → Oldest)`**. Option (b) —
> re-deriving the column per sort — is **rejected as over-engineering** and would put compute on the
> surface. **If the operator sorts by any other column, RUNNING hides itself or reads
> `N/A (sort changed)`. It must never present meaningless arithmetic silently.**

An excluded row renders in the refused treatment with its code in place of the numbers —
`W/O · WALKOVER · contributes nothing (B0.3)` — never blank, never zero, never omitted.

### V1c-4 · Every row reachable

`source_rows_shown` stops being a truncation and becomes a **page size**. Add PREV / NEXT, a
`page n of m` label, and a filter box matching id / player / round. The header reads
**`311 ROWS · 303 USED · 8 EXCLUDED`**, replacing `sourceLabel` and deleting `sourceTruncLabel` —
**there is no truncation left to warn about.** Running totals are computed over the whole lineage in
R2, so page 4 shows the same running figures it would show unpaged.

### V1c-5 · Anchors

| What | Where |
|---|---|
| `ratingOf` accumulation loop | engine 1316–1321 |
| ledger `rating` branch | engine 2269–2311 |
| `sourceRows` / `sourceLabel` / `sourceTruncLabel` | engine 4145–4152, 4299–4301 |
| FROM WHAT header | UI template 1354–1356 |
| column headers | UI template 1361–1367 |
| `sc-for list="{{ sourceRows }}"` grid (6 cols) | UI template 1369–1378 |
| `sourceTruncated` block — **delete** | UI template 1380–1382 |

### V1c-6 · Acceptance

- `rating:player:jannik-sinner@2026-09-08` header reads **311 ROWS · 303 USED · 8 EXCLUDED**.
- All 311 rows reachable by paging; the 8 excluded ones appear with `WALKOVER` / `UNPARSEABLE_SCORE`.
- The last row's `RUNNING` reads **1.687**; `runOwn`/`runOpp` close at **712.9 / 422.5** — asserted by
  a V3 arithmetic fixture, not by eye.
- `value`, `ownSum`, `oppSum`, `matchesUsed` **byte-identical to v1.25.0** on all 830 players —
  V1c is additive.
- The table scrolls horizontally inside its own container; the page never scrolls sideways.
- `points:{id}:jannik-sinner` labels its columns `own`/`opp`; unqualified still reads `winner`/`loser`.

**This is the pattern.** Signal 1 is the first to carry a complete, self-reconciling descent; V1's
remaining eight traces each end with the same treatment for their own node.

## V2 — HAND-COMPUTE A KNOWN ANSWER FOR EACH SIGNAL

For each signal, build a minimal canon and **derive the expected value by hand from the §-formula** —
on paper, from first principles. **Never by calling the function and recording what it returned**;
that proves only that the function is deterministic.

Worked example — Signal 1, from §5's `Rating = Σ own points ÷ Σ opp points`:
```
canon: p-x beats p-y 6-0 6-0 on 2025-01-01
§3:  6-0 is a legal final score, no reduction rule matches
     points_table: games 6 -> 10 points ; games 0 -> 1 point
     set_flatten_divisor 10  ->  winner flat 1.0 per set, loser flat 0.1 per set
     two sets   ->  winnerSum 2.0 · loserSum 0.2
§5:  Rating(p-x @2025-06-01) = 2.0 / 0.2 = 10.000     <- derived by hand
     Rating(p-y @2025-06-01) = 0.2 / 2.0 =  0.100     <- derived by hand
```
The fixture asserts `10.000` and `0.100`. If the points table, the flattener, the divisor or the
ratio direction ever moves, the fixture goes red and names which.

## V3 — NINE ARITHMETIC FIXTURES, ONE NEW SCOPE

New `arithmetic` scope in `runFixtureOf`. Nine fixtures — one per signal plus the §3 pipeline —
each carrying `expectValue` and a tolerance of `0.0001`:
```js
if (fx.scope === "arithmetic") {
  const rows = (fx.canon || []).map((r, i) => Object.assign({ rowIndex: i }, r));
  const res = ARITHMETIC_SUBJECT[fx.signal](fx, rows, cfg, liveMatchCountsOf(rows));
  const pass = res.ok && Math.abs(res.value - fx.expectValue) <= 0.0001;
  return { fired: pass ? [fx.code] : [], pass,
    detail: !res.ok ? "refused " + res.refusal
      : pass ? "value " + res.value + " matches the hand-computed " + fx.expectValue
      : "value " + res.value + " ≠ hand-computed " + fx.expectValue };
}
```
Gates KPI gains an **ARITHMETIC** tile reading `9/9`. **Do not fold it into PROVEN RED** — it proves
a different thing (F1's discipline).

**Acceptance for Stage 0.** Every signal reconciled and its verdict written down. Every departure a
§13.1 row. Nine arithmetic fixtures green. Mutation test: perturb one `points_table` entry → **at
least four** arithmetic fixtures go red (rating, tpi, common, h2h all descend through §3 scoring);
restore. Only then is *"each signal computes what the contract specifies"* a statement anyone can
make.

---

# STAGE 1 · CLEAN INPUTS

## 4 · L1 — A MATCH IS IN ITS OWN INPUTS

**This is the most serious defect in the build, and it lands exactly where R2 is heading.**

**Problem.** Every signal but TPI reads *"at or before the moment"* **inclusive**. A match dated `D`
is therefore part of its own inputs when read as of `D`:

| Function | Boundary | Same-day match |
|---|---|---|
| `priorMatchesOf(..., inclusive=true)` → `ratingOf`, surface | `d > bound` skipped | **included** |
| `opponentsOf` | `<= bound` | **included** |
| `pointsVsOpponentOf` → `commonOpponentsOf`, `h2hOf` | `> bound` skipped | **included** |
| `hopRatioOf` → `oo2Of`, `oo3Of` | `<= bound` | **included** |
| `priorMatchesOf(..., inclusive=false)` → `tpiOf` | `d >= bound` skipped | **excluded** — the only clean one |

**Diagnostic — 150 most recent vault matches, each signal computed twice**, once as shipped and once
with the moment moved back a day. This pair isolates the size of the leak; it is not the fix:

| System | as shipped | moment −1 day | inflated by |
|---|---|---|---|
| **h2h** | 87.8% (147 calls) | **61.8% (68 calls)** | **+26.0** |
| **surface** | 80.7% (150) | **58.7% (138)** | **+22.0** |
| rating | 75.3% (150) | 72.5% (149) | +2.9 |
| tpi · common · oo2 · oo3 | 64.8 · 71.0 · 64.6 · 61.9 | unchanged | 0.0 |

**The fix you are building is (b), not the day-shift.** Under fix (b) on 500 matches the leak-free
readings are `h2h` **65.2%** (155 speak) and `surface` **63.8%** (434 speak) — higher than the
day-shift figures because (b) correctly keeps a legitimately-prior same-day earlier round, which
(a) throws away. That difference is exactly why R5 chose (b).

H2H's coverage collapses **147 → 68**: for **79** matches the only meeting on or before that date
**was the match itself**. The system read "A beat B" and predicted A — a tautology scored as a
correct call. Surface behaves the same way because the surface-filtered history is thin.

Common/OO2/OO3 show a zero delta because they exclude the direct pair structurally
(`x !== pA && x !== pB`; `Y !== pB`) — the match under test can never enter them.

**Why the boundary itself is NOT the bug.** For a genuine future fixture the match is not in the
vault, so nothing leaks and *"at or before"* is right. The bug is that a **backtest** uses the
match's own date as the moment while the match sits in the canon.

**Required (R5 — fix (b)).**
1. **No signal function changes.** Signals are pure `(input, config) → output`; the harness passes a
   canon without the row under test:
   ```js
   // R2. Section 7.1 — a backtest never lets a match contribute to its own prediction.
   // Excluding by row id (not by date) keeps a legitimately-prior same-day earlier round counting.
   function canonWithoutRowOf(canon, rowIndex) {
     return canon.filter(c => c.rowIndex !== rowIndex);
   }
   ```
2. Every backtest read for a match goes through it. `commonOpponentsOf`, `oo2Of` and `oo3Of` may
   keep the full canon **only** with this comment, because it is provably identical:
   > `// Structurally excludes the direct pA-pB meeting, so the row under test cannot enter. Verified: zero accuracy delta across 150 matches.`
3. **Fixture (B0.10) — new `backtest` scope, one fixture.**
   ```json
   { "code": "BACKTEST_SELF_INCLUSION", "scope": "backtest",
     "player": "bt-a", "playerB": "bt-b", "asOf": "2025-04-01", "signal": "h2h",
     "canon": [
       { "date": "2025-04-01", "rawScore": "6-0 6-0", "playerAId": "bt-a", "playerBId": "bt-b", "winnerId": "bt-a", "loserId": "bt-b", "rowIndex": 0 }
     ],
     "note": "Section 7.1. The only meeting between bt-a and bt-b IS the match under test. Read at its own date the signal resolves and 'predicts' the known winner; with the row excluded it must refuse NO_DIRECT_HISTORY. Planted violation: self-inclusion." }
   ```
   Branch logic:
   ```js
   if (fx.scope === "backtest") {
     const all = (fx.canon || []).map((r, i) => Object.assign({ rowIndex: i }, r));
     const lc = liveMatchCountsOf(all);
     const leaked = h2hOf(fx.player, fx.playerB, fx.asOf, all, cfg, lc);
     const clean  = h2hOf(fx.player, fx.playerB, fx.asOf, canonWithoutRowOf(all, 0), cfg, lc);
     const pass = leaked.ok && !clean.ok && clean.refusal === "NO_DIRECT_HISTORY";
     return { fired: pass ? [fx.code] : [], pass,
       detail: !leaked.ok ? "the fixture vault does not exercise self-inclusion"
         : clean.ok ? "the row under test still reaches its own signal"
         : "self-inclusion resolves (" + leaked.value + "); excluded it refuses " + clean.refusal };
   }
   ```

**Acceptance.** Headless, on one scope, run each signal twice — as shipped, then through
`canonWithoutRowOf` — and confirm the **paired drop**: `h2h` and `surface` each fall by **20 points or
more**, `rating` by ~3, and `tpi` / `common` / `oo2` / `oo3` by 0.0. On a 500-match scope the
leak-free readings are `h2h` **65.2%** (155 speak) and `surface` **63.8%** (434 speak); `h2h`
coverage must fall sharply, because most of its shipped "calls" were the match reading itself.
Fixture proven red. Stub `canonWithoutRowOf` to the identity function → fixture goes red.

---

## 5 · L2 — M-FIT CARRIES THE SAME LEAK

**Problem.** `runMFit` (3099) calls `mfitRatiosOf(c.playerAId, c.playerBId, c.date, c.surface, eligible, …)`
— the match's own date against a canon containing it. Every accuracy number M-Fit has ever produced,
and any weight it proposed, was fitted on leaked data.

**Required.** Route `mfitRatiosOf`'s canon through `canonWithoutRowOf(eligible, c.rowIndex)`. Delete
the design note claiming `negligibleGap` fields "could not move accuracy" — that reasoning was
correct for the blend and is **wrong** the moment a gap gates a call (Stage 5).

**Do not otherwise touch M-Fit's blend-weight search** — deferred by R2. It stays, correct, unused.

**Acceptance.** A backtest of the same scope before and after returns a *lower* accuracy. Record both
numbers in the vBump note — the drop is the leak, and it is the point.

---

# STAGE 2 · WRONG NUMBERS & UNSAFE VALUES

## 6 · W1 — THE SURFACE CARD LINKS TO THE WRONG QUANTITY

**One line, and it prints a wrong number.** Line 3872 builds the Surface card's Fact Checker link with
the qualifier **after** the moment:
```
built    rating:player:jannik-sinner@2026-01-15:Clay
         -> qualifier NULL · moment "2026-01-15:Clay"   ->  1.632 (baseline)
correct  rating:player:jannik-sinner:Clay@2026-01-15
         -> qualifier Clay · moment 2026-01-15          ->  1.561 (Clay) · 61% - 39%
```
The card is headed **Clay**; OPEN SYSTEM shows the **Baseline**, stamped `(baseline)`. Third
occurrence of this bug class (v1.16.1 `ratingOf`, v1.21.1 `blend:pair`).

**Required.** Fix the line, then **kill the class**. One pure R2 producer, and every node id in R4
built through it — there are eight (`nodeOf` ×7 plus `doLogCall`):
```js
// R2. Section 6 grammar, one producer (B0.1): quantity:subject[:qualifier][@moment].
// The qualifier ALWAYS precedes the moment. Three shipped defects came from hand-built ids.
function nodeIdOf(quantity, subject, qualifier, moment) {
  return quantity + ":" + subject + (qualifier ? ":" + qualifier : "") + (moment ? "@" + moment : "");
}
```

**Acceptance.** The Surface card's id `parseNode`s to `{ qualifier: "<surface>", moment: "<date>" }`
and its node displays `(<surface>)`, not `(baseline)`. Grep R4 for `":player:"` / `":pair:"` string
concatenation → every hit is inside `nodeIdOf`.

---

## 7 · W2 — BLEND WEIGHTS PRODUCE `null (NaN)`

**Breaks B0.3 on the live path.** `blendOf` (1590) sums weights and divides with no validation:

| Input | Shipped result |
|---|---|
| any one BLEND weight typed as `one` | `ok: true`, `value: NaN`, `cls: null` |
| all seven weights `0` | `ok: true`, `value: NaN`, `cls: null`, 3 signals still "speaking" |

The badge renders **`null (NaN)`**. COCKPIT BLEND fields are free text, so one keystroke reaches it;
`MFIT_CANDIDATES` includes `0`, so APPLY can too.

*(Kept in this order despite R2's deferral: the Combiner still renders on PREDICTION today, and a
`NaN` on a live surface is not something to leave in place while the page exists.)*

**Required.**
1. In `blendOf`, before the division:
   ```js
   const bad = speaking.filter(r => !Number.isFinite(r.weight) || r.weight < 0);
   if (bad.length) return { ok: false, refusal: "BLEND_WEIGHTS_INVALID", rows, invalid: bad.map(r => r.key) };
   let wSum = 0, wrSum = 0;
   for (const r of speaking) { wSum += r.weight; wrSum += r.weight * r.ratio; }
   if (!(wSum > 0)) return { ok: false, refusal: "BLEND_WEIGHTS_INVALID", rows, invalid: ["all"] };
   ```
2. Ledger `blend` branch names it — `detail`: *"blend.weight.{names} is not a positive number, so the
   weighted mean has no divisor."* · `remedy`: *"Set at least one blend.weight.* to a positive number
   on COCKPIT → BLEND."*
3. `SIGNAL_REMEDY` gains the code (§8.3).
4. `applyMFitWeights` refuses a proposal summing to 0, and refuses one whose accuracy is below the
   live config without a second explicit click.
5. **Fixture — existing `signal` scope, no runner branch touched:**
   ```json
   { "code": "BLEND_WEIGHTS_INVALID", "scope": "signal", "signal": "blend",
     "player": "sig-h1", "playerB": "sig-h2", "asOf": "2025-06-01",
     "canon": [{ "date": "2025-01-01", "rawScore": "6-4 6-3", "playerAId": "sig-h1", "playerBId": "sig-h2", "winnerId": "sig-h1", "loserId": "sig-h2" }],
     "cfgPatch": { "blendWeightRatingText": "0", "blendWeightTpiText": "0", "blendWeightCommonText": "0",
       "blendWeightSurfaceText": "0", "blendWeightH2hText": "0", "blendWeightOo2Text": "0", "blendWeightOo3Text": "0" },
     "note": "Section 5 Combiner. Every blend weight is zero, so the weighted mean has no divisor. Refuses by name — never a NaN ratio and a null class on the Master Call badge (B0.3)." }
   ```

**This guard and this fixture were executed against the live vault while drafting: suite 79 fixtures
0 open, the fixture fired `BLEND_WEIGHTS_INVALID`, every existing fixture stayed green, a typo weight
returned `invalid: ["h2h"]`, and no runner branch was edited.** If your run differs, stop and ask.

---

## 8 · W3 — `MISSING_PLAYER` DOUBLE-COUNTS A ROW

A row that **both** misses a player **and** carries an out-of-domain winner is pushed twice
(lines 818 and 826). Probe → `MISSING_PLAYER = [0, 0]` for one row. The node is labelled
*"count(rows the check refused)"* and would report **2 for 1 row**; FROM WHAT lists it twice.
Dormant on the live vault (0 hits) — a latent lie, not a live one.

**Required.** Guard the second push so a row is recorded once. **Do not** change which rows the check
catches. **Acceptance.** One-row probe → length **1**; live still 0; existing fixture still red.

---

## 9 · W4 — `blendOf` CARRIES A DEAD PARAMETER

`blendOf(…, liveCounts)` declares `liveCounts` and **never references it** — it derives `eLive` from
the eligible slice internally. Every caller passes it, which reads as though those counts are used.

Add one comment recording the related fact found while auditing: **the Stage-4 divisor feeds nothing
any signal reads.** `ownOppPointsOf` and `hopRatioOf` both take `winnerSum`/`loserSum`, which are
*pre*-divisor. The divisor affects only the `flat:{id}` node's own display.

**Acceptance.** `node --check` clean; ≥10 pairs byte-identical before and after.

---

# STAGE 3 · FALSE STATEMENTS ON THE SURFACE

## 10 · F1 — EXEMPTION FIXTURES ARE NOT "PROVEN RED"

`OPEN_FINAL_EXEMPT`, `OPEN_SPINE_EXEMPT`, `OPEN_DECLARED_MISMATCH_EXEMPT` each render
**`fired = none`** beside **`verdict = PROVEN RED`**, and all three are folded into `PROVEN RED 64/64`
and the banner. Truth today: **61 proven-red, 3 exemption, 14 control.**

**Required.**
1. `runFixturesOf` partitions **three** ways — `control` (`code === "CONTROL"`), `exempt`
   (`fx.exempt === true`), `refusal` (the rest). `open` = the sum of all three shortfalls.
2. Row verdict (4052) gains `fx.exempt` → `"PROVEN EXEMPT"` / `"EXEMPTION FAILED"`.
3. New `EXEMPT` KPI reading `3/3`, tip: *"Section 2.5.1. These plant a violation on an OPEN edition
   and prove the check correctly does NOT fire. They are not proven-red."*
4. `PROVEN RED` tip drops *"Each planted its violation and the named refusal or flag fired"* as a
   claim over the whole population.
5. Banner: `GREEN · 65 PROVEN RED · 3 EXEMPT · 15 CLEAN`.

**Correct the record everywhere it is stated** — engine `steps[2].note`, Gates KPI + tips, spec
§8.2 #7 and §8.4, both cold-starts. **Correct 64 → 61, then land 65. Never increment 64.**

---

## 11 · F2 — GATES "FIXTURES" TIP IS WRONG

Line 4061 claims *"Four codes carry two fixtures, at row and at payload scope."* Measured: **seven**
codes carry more than one, three carry three, and three pairs are signal/signal:
```
UNKNOWN_ROUND -> edition, edition, payload      NO_PATH_FOUND            -> signal, signal
PLAYER_ID_UNRESOLVED -> row, row, payload       NULL_SCORE_IN_CHAIN      -> signal, signal
MISSING_SCORE -> row, payload                   INSUFFICIENT_SHARED_PATHS-> signal, signal
MISSING_DATE  -> row, payload
```
A **regression of a closed finding** — `AUDIT_2026-09-07` §4 item 3 corrected this sentence once
("three" → "four"). A hand-counted sentence drifts at every fixture.

**Required.** Derive it, never count it:
```js
function fixtureCodeSpreadOf(fixtures) {
  const byCode = new Map();
  for (const f of fixtures) {
    if (f.code === "CONTROL") continue;
    if (!byCode.has(f.code)) byCode.set(f.code, []);
    byCode.get(f.code).push(f.scope);
  }
  const multi = [...byCode.entries()].filter(([, s]) => s.length > 1)
    .map(([code, scopes]) => ({ code, count: scopes.length, scopes }));
  return { codes: byCode.size, multi };
}
```
**Acceptance.** Add a scratch fixture; the tip's numbers move with no string edited.

---

## 12 · F3 — GATES "SCOPES" TIP IS WRONG

Line 4070 ends *"…section 5 signals 1-4."* The `signal` scope holds **29** fixtures covering
Signals **1–8 and the Combiner**. Derive `sub` from `Object.keys(F.scopes)`; replace the trailing
clause with *"…section 3 score pipeline, section 5 signals 1-8 and the Combiner, section 7.1
backtest, and section 8.2 #5 prediction order."*

**Acceptance.** `SCOPES` value equals the count of names in its own sub-label; no unbuilt range named.

---

## 13 · F4 — `refusal:check` CLAIMS "PROVEN" WITHOUT READING THE PROOF

Lines 2550 / 2561 check only that a fixture **exists in the config array** — never that it passed.
A failing fixture still reads *"proven · step 3 green"*. Same class as `AUDIT_2026-09-07` §4 item 2,
closed at v1.11.0.

`buildLedger` cannot call `runFixturesOf` (the runner takes the ledger) — **do not create that cycle.**
State only what the ledger knows:
```js
value: m.fixtures.some(f => f.code === code)
  ? m.fixtures.filter(f => f.code === code).length + " registered · run on GATES"
  : "no fixture registered"
```
Tip gains: *"Registration is not proof. Open GATES to see whether the fixture went red."*
**Acceptance.** Grep `"proven · step 3 green"` → zero hits.

---

## 14 · F5 — COCKPIT COMPLETENESS TOOLTIP OVERCLAIMS

The header tooltip claims *"Every number, list, pattern, ladder and separator the compute layer reads
… is reachable here."* **Fourteen compute-read values are not on the surface at all:**
`payload_required_fields` · `payload_refusal_for` · `payload_optional_fields` ·
`duplicate_key_fields` · `payload_winner_values` · `row_keys` · `declaration_fields` ·
`declarations_marker` · `status_marker` · `rows_array_key` · `rows_count_key` ·
`sourcing_prompt_template` · `player_status_prompt_template` · plus the surface caps
`surface_domain` · `prediction_rows_shown` · `registry_suggest_cap`.

The comment at line 3801 also states `prediction_rows_shown` **is** a cockpit control. It is not.

**Required.** Add editable `cfgDefs` rows for the twelve already stored as plain strings/lists
(no plumbing needed). Add **read-only `DECLARED` rows** for the three objects — `row_keys`,
`declaration_fields`, `payload_refusal_for` — rendered as formatted JSON. **Do not** invent a JSON
edit path into `ingestOf` (B0.15); reachability is the claim, editability is not. Fix the 3801
comment. Add to the tooltip: *"Values stamped DECLARED are shown, not editable."*

**Acceptance.** A script listing every key `modelOf` reads vs every key `cfgDefs` renders returns an
empty difference but for metadata.

---

## 15 · F6 — SOURCING → COMMITTED RENDERS EIGHT BLANK PILLS

The template (UI line 531) renders each commit row's pill as `{{ c.state }}`; `commitRows` (3751)
builds `Object.assign({ label, value, tip }, pill(...))` and `pill()` returns only `{color, line, fill}`.
**`state` is never set** — after every commit, all eight rows show a coloured pill containing nothing.

**Required.** Give each row the `state` word its colour already implies, matching
`statusCommitRows`. Change no value and no colour. **Acceptance.** Stage 2 new + 1 refused, commit,
screenshot: every pill carries a word.

---

## 16 · F7 — TWO GAP PARAMETERS ARE DEAD CONFIG

`signal.oo2.negligibleGap` and `signal.oo3.negligibleGap` are declared in `CONFIG_TEXT`, typed in
`modelOf`, given COCKPIT controls with tooltips claiming they flag TIGHT — and **read by no compute
function**. Only `signalSurfaceNegligibleGap` is read (line 1328), and only for the surface rating.

Two of the three "gaps" R2 wants calibrated currently do nothing.

**Required.** Do **not** patch the tooltips. Stage 5 replaces all three with live
`signal.{x}.callGap` keys. Until Stage 5 is authorised, the two dead controls carry the stamp
`DECLARED · NOT READ` and the tip *"Declared but read by no compute function. Superseded by
signal.{x}.callGap at §5A — see Stage 5."* **A control that does nothing must say so (B0.6).**

**Acceptance.** No COCKPIT control claims an effect it does not have.

---

## 17 · F8 — OFF-VAULT NAME REFUSES BY NAME

`resolvePredTarget` (3031) computes `offVault` — and **nothing reads it**. "Nobody McGhost" →
`nobody-mcghost` gets a chip, builds a node, every signal refuses, and the operator sees a bare
`NO_CALL` as though the players were real and the data thin.

**Required.** Extend the existing refusal branch (3840) to also refuse on `rA.offVault || rB.offVault`,
reusing `PLAYER_ID_UNRESOLVED` (registered §12.4.4, already fixture-covered — **no new code, no
count change**). `detail`: *"{Player A|Player B}: “{typed}” is not a registered player."* ·
`remedy`: *"Pick a name from the list, or add a player_aliases entry on COCKPIT → PLAYER IDENTITY."*

**Acceptance.** `Nobody McGhost` vs `jannik-sinner` + date → the named refusal + remedy; no node
built; no `NO_CALL`. Grep: `offVault` is read.

---

# STAGE 4 · ORDER STABILITY — OO2 / OO3 ONLY

**Why this is still in the order after R2.** Measured `fwd × rev` (1.0000 = perfectly mirrored):

| System | median | worst |
|---|---|---|
| rating · tpi · h2h | 1.0000 | ≤ 1.0001 |
| common | 1.0000 | 1.0032 |
| **oo2** | **0.7999** | **0.0819** |
| **oo3** | 1.0194 | **34.7222** |

**OO2 and OO3 are the only two systems whose answer changes with typing order — and, on the 500-match
leak-free backtest, the only two that barely predict (57.9% and 51.6% at gap 0).** Those two facts are
almost certainly related: a value that moves with argument order is a value carrying noise.

You cannot fit a threshold to a system whose value depends on which name was typed first, and you
cannot fairly judge whether OO2/OO3 are worth keeping until their readings are stable. This stage is
therefore a **prerequisite for Stage 5 and for the OO3 decision in §23** — not Master-Call work.

## 18 · O1 — CANONICAL REFERENCE ORDER (two arguments)

```js
// Section 8.2 #5. OO2/OO3 fan out from pA's side, so a pair node is not order-invariant. The pair
// is ordered canonically before any pair node is built. Ascending id string: deterministic, no data
// lookup, no config, no clock (B0.5 / B0.12). Two arguments — home/away is a future SIGNAL with its
// own qualifier (Owner ruling 2026-09-09), never an ordering override.
function predReferenceOrder(idA, idB) {
  const lo = idA < idB ? idA : idB, hi = idA < idB ? idB : idA;
  return { pA: lo, pB: hi, inverted: lo !== idA };
}
function pairNodeIdOf(quantity, idA, idB, qualifier, moment) {
  const ord = predReferenceOrder(idA, idB);
  return { ord, id: nodeIdOf(quantity, "pair:" + ord.pA + ":" + ord.pB, qualifier, moment) };
}
```
Apply to the **`oo2` and `oo3` pair nodes** in `nodeOf`, and to `common` / `h2h` for consistency
(they are already symmetric, so nothing moves — verify that). Compute the order **once per render**
(B0.2). **No `homeSide`, no `predHomeSide` state, control, config key or template element.**

**Acceptance.** `pairNodeIdOf("oo2", a, b, …).id === pairNodeIdOf("oo2", b, a, …).id`; identical
node readings from either typed order on ≥10 real pairs. `common` / `h2h` values unchanged.

## 19 · O2 — DISPLAY FROM THE OPERATOR'S SIDE (exact inversion)

The canonical node is read **once**; the operator's A/B choice controls only which column is left.
When `ord.inverted`, on the OO2/OO3 cards: `pctA`↔`pctB`, `colorA`↔`colorB`, `weightA`↔`weightB`,
`barA` → `100 − barA`, `ratioTip` ratio → `round4(1 / ratio)`, `favoured` token `pA`↔`pB` — **the
favoured player is unchanged**. `nameA`/`nameB` are always the operator's sides. Fatigue is
per-player and is **never** inverted.

A sign-exact flip of an already-computed figure is not a computation (§8.1, B0.13) — **no `L.get`
re-issued.**

**Acceptance.** A pair entered both ways shows the same favoured player on the OO2/OO3 cards; only
columns and percentages swap. Screenshot both.

## 20 · O3 — SWAP NOTE

One muted line under the swap control (≤110 chars, ≤8-word runs — B0.13):

> *Order is presentational. Each system's call is the same either way.*

**Do not** write that a home side will make order directional — that is not the plan (R3).

## 21 · O4 — ORDER-STABILITY FIXTURE (not a tautology)

The superseded order asserted `clsOf(o1.pA, o1.pB) === clsOf(o2.pA, o2.pB)` — one function, identical
arguments. It cannot fail. Assert instead on the **favoured player**, and on the **surface's own
producer**:

```js
if (fx.scope === "predorder") {
  const rows = (fx.canon || []).map((r, i) => Object.assign({ rowIndex: i }, r));
  const pickOf = (pA, pB) => { const b = blendOf(pA, pB, fx.asOf, null, rows, cfg);
    return b.ok ? (b.value > 1 ? pA : b.value < 1 ? pB : "even") : "REFUSED:" + b.refusal; };
  const rawDiffers = pickOf(fx.player, fx.playerB) !== pickOf(fx.playerB, fx.player);
  const o1 = predReferenceOrder(fx.player, fx.playerB), o2 = predReferenceOrder(fx.playerB, fx.player);
  const orderStable = o1.pA === o2.pA && o1.pB === o2.pB;
  const idStable = pairNodeIdOf("oo2", fx.player, fx.playerB, null, fx.asOf).id
                === pairNodeIdOf("oo2", fx.playerB, fx.player, null, fx.asOf).id;
  const pass = rawDiffers && orderStable && idStable;
  return { fired: pass ? [fx.code] : [], pass,
    detail: !rawDiffers ? "the fixture vault does not exercise a pick disagreement"
      : !orderStable ? "predReferenceOrder is not order-insensitive"
      : !idStable ? "pairNodeIdOf does not yield one node id for both orders"
      : "raw order disagrees on the favoured player; the canonical node id is one value" };
}
```

`idStable` is load-bearing: because `pairNodeIdOf` is the **single producer** of a pair node id
(B0.1), a render block that bypasses canonical order must bypass it — and the DoD grep catches that.

**Fixture vault — given, and executed.** Only OO2/OO3 can produce a disagreement, so the canon needs
a 3-hop chain from each side, dates cascading **backward** along each chain (the v1.18.1 lesson):

```json
{ "code": "PREDICTION_ORDER_STABLE", "scope": "predorder",
  "player": "pred-a", "playerB": "pred-b", "asOf": "2025-06-01",
  "canon": [
    { "date": "2025-03-01", "rawScore": "6-0 6-0", "playerAId": "pred-a", "playerBId": "x1",     "winnerId": "pred-a", "loserId": "x1" },
    { "date": "2025-02-01", "rawScore": "6-0 6-0", "playerAId": "x1",     "playerBId": "y1",     "winnerId": "x1",     "loserId": "y1" },
    { "date": "2025-01-01", "rawScore": "6-0 6-0", "playerAId": "y1",     "playerBId": "pred-b", "winnerId": "y1",     "loserId": "pred-b" },
    { "date": "2025-03-05", "rawScore": "6-0 6-0", "playerAId": "pred-b", "playerBId": "x2",     "winnerId": "pred-b", "loserId": "x2" },
    { "date": "2025-02-05", "rawScore": "6-0 6-0", "playerAId": "x2",     "playerBId": "y2",     "winnerId": "x2",     "loserId": "y2" },
    { "date": "2025-01-05", "rawScore": "6-0 6-0", "playerAId": "y2",     "playerBId": "pred-a", "winnerId": "y2",     "loserId": "pred-a" },
    { "date": "2025-04-01", "rawScore": "6-0 6-0", "playerAId": "pred-a", "playerBId": "pred-b", "winnerId": "pred-a", "loserId": "pred-b" }
  ],
  "note": "Section 8.2 #5. Two mirror-image 3-hop chains plus one direct meeting — a vault that is symmetric by inspection. The raw entry orders nevertheless each favour whichever player was typed first (337.688 -> pred-a; 333.476 -> pred-b). predReferenceOrder makes the pair, and therefore the pair node id, one value." }
```

**Measured while drafting:** `blend(pred-a, pred-b) = 337.688` favours pred-a; `blend(pred-b, pred-a)
= 333.476` favours pred-b. Signals speaking: `rating`, `h2h`, `oo2`. **A vault symmetric to the eye
still backs whoever you type first.** Executed with F1 + W1 + W2 + O1: 80 fixtures, 0 open; stubbing
`predReferenceOrder` turned it RED. **Do not weaken an assertion to make a fixture pass.**

---

# STAGE 5 · PER-SYSTEM CALLS + GAP CALIBRATION

> **GATE: Stage 5 begins only when the Owner has accepted §5A (S1 below).** It is new behaviour, not
> a fix. Nothing in Stage 5 is built before that word.

## 22 · S1 — SPEC §5A, DRAFTED FOR THE OWNER (R6)

> ### §5A · Per-System Calls
>
> Each of the seven systems of §5 produces a **ratio** — `pA` relative to `pB`. A ratio is not a call.
> A system **calls** when its ratio is far enough from parity to be worth acting on; below that it
> stays silent and says so.
>
> **Share and gap.** `shareA = ratio ÷ (ratio + 1)`; `gap = |shareA − 0.5|`. A gap of `0` is a
> coin toss; `0.5` is total certainty.
>
> **The call.** For system `x` with configured `signal.x.callGap`:
> - the system's own §5 refusal (`NO_DIRECT_HISTORY`, `INSUFFICIENT_HISTORY`, …) stands first —
>   it cannot call on data it does not have;
> - if `gap < signal.x.callGap` the system refuses **`GAP_BELOW_THRESHOLD`**, carrying its gap and
>   its threshold, with the remedy *"Lower signal.x.callGap, or accept that this system has no call
>   on this fixture."* — a named refusal, never a defaulted call (B0.3);
> - otherwise the system calls the side its ratio favours, classified by **§3's existing
>   `call_cutpoints`** against `underdogShare = 0.5 − gap`. **One class taxonomy across the build —
>   Clear / Plain / Tight — never a second.**
>
> **Reference order.** `pA` is the numerator. `oo2` and `oo3` fan out from `pA`'s side and are not
> order-invariant, so §8.2 #5 orders the pair canonically before their nodes are built. Calls from
> the remaining five systems are order-invariant by construction.
>
> **Calibration (§7.1).** `signal.x.callGap` is **FITTED**, not ruled: it is fitted by backtest over
> the last `calibration_scope` matches, maximising the system's accuracy subject to at least
> `calibration_min_calls` calls. Three rules bind every backtest this build runs:
> 1. **A match never contributes to its own prediction** — the row under test is excluded from the
>    canon by row id (engine `v1.26.0`). Reading at the match's own date inflated H2H by 26.0 points
>    and Surface by 22.0 points on a 150-match sample.
> 2. **Orientation is balanced.** The store normalises `playerA` = winner on every row, so presenting
>    matches in store order makes the label constant and measures a position-biased system against
>    its own bias. Each match is presented in a randomised orientation, and the realised label
>    balance is reported with the result.
> 3. **Accuracy is never reported without its call count.** A gap that raises accuracy by silencing
>    the system is a worse parameter, not a better one.
>
> Proposals are applied only on an explicit operator click (B0.12).
>
> **Retired.** `signal.surface.negligibleGap`, `signal.oo2.negligibleGap` and
> `signal.oo3.negligibleGap` are replaced by `signal.x.callGap` for all seven systems. The latter two
> were declared and read by nothing.

**Nothing in §5A changes a §5 formula, a cut-point, a refusal name or a schema.** It adds one
derived quantity (`gap`), one refusal (`GAP_BELOW_THRESHOLD`) and one fitted parameter per system.

## 23 · S2 — ONE PRODUCER, SEVEN PARAMETERS

```js
// §5A. One producer for every system's call (B0.1). No literal (B0.12) — the gap and the
// cut-points both arrive as config. Reuses §3's class taxonomy; never defines a second.
function signalCallOf(ratio, callGap, cfg) {
  if (!Number.isFinite(ratio) || ratio <= 0) return { ok: false, refusal: "RATIO_INVALID" };
  const shareA = round4(ratio / (ratio + 1));
  const gap = round4(Math.abs(shareA - 0.5));
  if (gap < callGap) return { ok: false, refusal: "GAP_BELOW_THRESHOLD", gap, callGap, shareA };
  const underdogShare = round4(0.5 - gap);
  let cls = null;
  for (const cp of cfg.callCutpoints) if (underdogShare >= cp.min) { cls = cp.class; break; }
  return { ok: true, favoured: ratio > 1 ? "pA" : "pB", cls, gap, shareA, underdogShare };
}
```

**Config — seven new keys** (`CONFIG_TEXT` + `CONFIG_KEYS` + `configOf` + `modelOf` + a COCKPIT
control each, stamped `FITTED` once calibrated): `signal_rating_call_gap`, `signal_tpi_call_gap`,
`signal_common_call_gap`, `signal_surface_call_gap`, `signal_h2h_call_gap`, `signal_oo2_call_gap`,
`signal_oo3_call_gap`. Plus `calibration_scope` and `calibration_min_calls`.
**Retire** the three `negligibleGap` keys and their controls. `config_version` **24 → 25**.

**Shipping defaults — 500-match backtest, leak-free (fix b) and balanced-orientation**, minimum
**100 calls**. A starting point for the calibrator, not rulings:

| System | speaks | baseline (gap 0) | callGap | accuracy | calls | 95% CI | z |
|---|---|---|---|---|---|---|---|
| rating | 483/500 | 65.6% | **0.10** | 76.0% | 104 | 68–84% | 5.3 |
| tpi | 374/500 | 63.1% | **0.10** | 75.2% | 117 | 67–83% | 5.5 |
| surface | 434/500 | 63.8% | **0.10** | 75.0% | 124 | 67–83% | 5.6 |
| common | 422/500 | 62.8% | **0.15** | 71.4% | 147 | 64–79% | 5.2 |
| oo2 | 466/500 | 53.4% | **0.25** | 68.3% | 123 | 60–77% | 4.1 |
| h2h | 155/500 | 65.2% | **0.05** | 66.4% | 131 | 58–75% | 3.8 |
| oo3 | 480/500 | 54.8% | **0.20** | 59.1% | 232 | 53–65% | 2.8 |

`calibration_min_calls` ships at **100**. At a floor of 40 the table reports TPI at 92.5% on 40 calls
— a 95% CI running past 100%, which is an artefact of the small slice, not a finding. **Every one of
the seven systems is significantly better than chance once gated** (z 2.8 – 5.6). None should be
retired.

> **METHODOLOGY — two corrections made while producing this table. Both are now binding rules.**
>
> **1 · Self-inclusion (L1).** Reading a signal at the match's own date let the match into its own
> inputs. H2H read 87.8%; leak-free it reads 65.2%.
>
> **2 · Degenerate label.** The store normalises **`playerA` = winner on all 14,795 rows**. Presenting
> matches in store order makes the label constant, so "accuracy" only measures `P(ratio > 1)` — which
> silently scores a positionally-biased system against its own bias. Isolated by re-running with
> randomised orientation:
>
> | System | store order | balanced | shift |
> |---|---|---|---|
> | rating · tpi · surface · h2h | 65.6 · 63.1 · 63.8 · 65.2 | identical | **0.0** — position-blind |
> | common | 64.7% | 62.8% | −1.9 |
> | **oo2** | 57.9% | **53.4%** | **−4.5** — was flattered by its own bias |
> | **oo3** | 51.6% | **54.8%** | **+3.2** — was penalised by it |
>
> **This reversed a conclusion.** On store order OO3 looked like a coin flip (51.6%) and a candidate
> for retirement. Balanced, it reads 54.8% at baseline and **59.1% at gap 0.20 over 232 calls
> (z = 2.8)** — weak, but real. **OO3 is kept.** OO2 likewise: 53.4% baseline is not significant
> (z = 1.5), but **68.3% at gap 0.25 over 123 calls (z = 4.1)** is. Both are the weakest of the seven
> and both are gated hardest — that is the honest treatment, not retirement.

**Recommended addition to Stage 1 (drafter's recommendation, needs the Owner's word).** Both defects
above were **measurement** defects, not engine defects — the engine computed correctly and the
measurement lied. If a backtest is going to set live call parameters, the measurement path needs the
same gate discipline as the compute path: `canonWithoutRowOf` and a balanced-orientation harness as
named R2 producers, each with a fixture, rather than a script. L1's fixture covers self-inclusion;
a second fixture should cover orientation balance.

## 24 · S3 — THE CALL ON THE PREDICTION CARDS

Each per-system card gains its call: favoured player name, class badge (Clear / Plain / Tight), and
the gap. A system refusing `GAP_BELOW_THRESHOLD` renders in the existing refused treatment with its
gap, its threshold and the §8.3 remedy — **the same card shape as every other refusal**, no new
visual language. Every value is read off the system's own ledger node (§8.1). The Master Call badge
stays exactly as it is (deferred by R2).

## 25 · S4 — GAP CALIBRATION (COCKPIT → M-FIT)

A second section in the existing M-FIT tab — **not an eighth page** (B0.13). Same
Propose → Review → Apply discipline as the blend fit (B0.12): it runs the leak-free backtest over
`calibration_scope`, sweeps each system's gap independently, and shows **accuracy and coverage
together** per candidate. Nothing is applied without a click. Report per system: current gap,
proposed gap, accuracy at each, and call count at each. A proposal that raises accuracy while
dropping below `calibration_min_calls` is shown and **refused**, with its reason.

## 26 · S5 — FIXTURES (B0.10)

Two, both in the existing `signal` scope — **no new scope, no runner branch touched**:
- `GAP_BELOW_THRESHOLD` — a canon whose ratio sits inside the configured gap; the system must refuse
  by name and never fall through to a call.
- `CONTROL` — the same canon with a gap wide enough to call; the system must resolve to a class.

---

# STAGE 6 · CLOSE-OUT

## 27 · C1 — DOCUMENTS

**`DEVELOPER_COLDSTART.md` contradicts itself on its first page. Rewrite, current content only.**

| Says | Truth |
|---|---|
| §2.1 "the authorised work is BUILD_ORDER v1.25.0 (Parts A/B/C) only" | its own header says v1.26.0 |
| §1 "the full target architecture is **v3.7**" | v3.7 is a SUPERSEDED stub; the contract is v3.8 → v3.9 |
| §3 not-ready branch "has drifted (fixed in the current order, A4)" | fixed at v1.25.0 — verified, both branches expose exactly 257 keys |
| §6 "await the next `<S10 sub-pin> proceed`" | the next unit is this order |
| §7 "No shipping under the `v1.24.0` label" | should read v1.25.0 → v1.26.0 |

**Every line anchor in §3 is wrong. Replace with:**

| §3 table | Correct |
|---|---|
| runtime | **15 – 321** |
| `dx-rows` | **323 – 459,966** |
| `dx-declarations` | **459,967 – 460,174** |
| `dx-status` | **460,175 – 460,491** |
| `<x-dc>` UI template | **460,494 – 461,928** |
| engine script | **461,929 – 466,243** (**4,313** lines, not ~3,960) |
| R1 · R2 · R3 · R4 | **1–603 · 604–2018 · 2019–2605 · 2606–4313** |
| `renderVals()` · `memo()` · `notReadyVals()` | **3253 · 3126 · 3171** |

**`SUPERVISOR_COLDSTART.md`** — correct the fixture baseline to F1's split; correct ledger row 199,
which logs the Surface card as the same cosmetic as Rating/TPI (it is a malformed node id returning
the wrong quantity — W1); add the L1 leak as a finding.

**Quarantine.** `_quarantine-for-deletion/` holds the v1.24.0 engine and the full v3.7 text; add
`BUILD_ORDER_2026-09-08_v1.26.0.md`. **Ask the Owner to clear all three; do not delete without it.**

**Screenshots.** The two undated PNGs show a **superseded UI** (one shared search box; a Ratings card
with absolute values and a delta). Rename to `REFERENCE_2026-09-08_*.png` or move to `_reference/`.

## 28 · C2 — SPEC → v3.9

Copy `…v3.8.md` → `…v3.9.md`; edit **only** the successor; replace v3.8 with a `SUPERSEDED → v3.9`
stub; quarantine the full v3.8 text after the auditor clears. **Allowed edits, exactly these:**

1. **Header** — a `**v3.9:**` line recording: §5A per-system calls; §7.1 leak-free backtest; §8.2 #5
   canonical pair order for OO2/OO3; the corrected fixture split; §13.1 rows 8 and 9.
2. **New §5A** — verbatim from S1 above.
3. **§7.1** — append: *"A backtest never lets a match contribute to its own prediction: the row under
   test is excluded from the canon by row id (engine `v1.26.0`). Reading a signal at the match's own
   date inflated H2H by 26.0 points and Surface by 22.0 points on a 150-match sample."*
4. **§8.2 #5** — append: *"OO2 and OO3 fan out from `pA`'s side and are not order-invariant, so the
   two resolved ids are ordered canonically (ascending id string) before their pair nodes are built.
   The operator's A/B choice controls only which column renders where — the inverted side is the
   exact inverse of the canonical figure, never recomputed. The swap control is presentational.
   **Home and away is a future signal with its own qualifier, not an ordering override (Owner ruling
   2026-09-09).** A name resolving to no registered player refuses `PLAYER_ID_UNRESOLVED` with a
   remedy — never a silent `NO_CALL`."*
5. **§8.2 #7 and §8.4 — correct, do not increment:**
   > **83 fixtures — 65 proven-red · 3 OPEN-exemption (proven NOT to fire, §2.5.1) · 15 control-clean · 0 open (engine `v1.26.0`).**
   > Live scopes: `control · edition · row · ledger · payload · flag · identity · statuspayload · dedupe · score · signal · predorder · backtest`.
   >
   > *Correction of record: v3.7 and v3.8 stated "64 refusal proven-red". Three of those 64 are §2.5.1 OPEN-exemption fixtures, which prove a check correctly does **not** fire. The proven-red population at v1.25.0 was 61, not 64.*
6. **§13.1** — two rows:
   > | 8 | §5 — OO2/OO3 path selection and the Combiner's arithmetic mean | `blend(A,B)` and `blend(B,A)` disagree on the favoured player in ~12% of live pairs (11/91, top-14 players, 2025-06-01) and on the class in ~23%. OO2/OO3 fan out from pA's side (fwd × rev up to 34.7×); the weighted arithmetic mean of ratios is order-dependent by construction. Canonical pair order (§8.2 #5, v1.26.0) makes each pair node **one value per fixture**; it does not make the two orientations mirror internally. | **Not ruled.** Two candidate fixes, each its own authorisation: (a) symmetric OO2/OO3 paths — rank by each path's own latest match date, dedupe path sets; (b) a weighted **geometric** mean in the Combiner, which is exactly order-invariant. |
   > | 9 | §5 — "at or before the moment" | Correct for a live fixture (not yet in the vault) and wrong for a backtest (already in it). Fixed at the harness, not the boundary: §7.1 excludes the row under test by id (v1.26.0). Recorded because the §5 prose alone does not distinguish the two cases. | **Ruled** 2026-09-09 — fix (b), harness-side. No §5 boundary changed. |

**Not allowed.** Editing any existing formula, cut-point, refusal name, schema or foundation law.

## 29 · C3 — vBUMP & FILE

1. Everything green — live vault 0 refusals, **83** fixtures 0 open, all 7 pages, offline boot.
2. `CONFIG_TEXT`: `app_version` → `v1.26.0`; `config_version` **24 → 25** (S2 adds seven `callGap`
   keys plus two calibration keys and retires three); `vbump_log` entry recording, in order: the L1
   leak with its measured inflation and the before/after M-Fit accuracy; W1's third-occurrence node-id
   defect; W2's `NaN`; the 64 → 61 → 65 correction; the two dead gap keys; §5A; and the note that
   canonical-order pair node ids mean a Call Log entry written before v1.26.0 in the non-canonical
   order reads as not-logged. Refresh `steps[*].note` and `spec` / `spec_note` / `spec_state`.
3. Rename → `Dalxic Stats Engine v1.26.0.dc.html`. Mirrors byte-identical.
4. Update both cold-starts (C1).
5. **Stop.** The Combiner's return, the OO2/OO3 symmetric-path fix, a geometric-mean Combiner and the
   home/away signal each need their own Owner `proceed`.

---

## 30 · DEFINITION OF DONE

- [ ] `node --check` clean on the full engine script.
- [ ] Headless: 0 row refusals, 0 edition refusals, **83 fixtures 0 open**, GREEN true, registry 830.
- [ ] Browser: header `v1.26.0`, `GREEN · 0 REFUSALS`, all 7 pages, offline boot.
- [ ] **L1** paired run on one scope, as-shipped vs `canonWithoutRowOf`: `h2h` and `surface` each drop **≥20 points**, `rating` ~3, the other four 0.0; `h2h` coverage falls sharply. Fixture proven red; identity-stub turns it red.
- [ ] **L2** M-Fit accuracy before and after the fix both recorded in the vBump note.
- [ ] **W1** Surface card id `parseNode`s to `{qualifier, moment}` and displays `(<surface>)`. Grep: every pair/player id built by `nodeIdOf`.
- [ ] **W2** `x` in any blend weight → `BLEND_WEIGHTS_INVALID` + remedy, never `null (NaN)`. Fixture red.
- [ ] **W3** one-row probe → `MISSING_PLAYER` length 1; live still 0.
- [ ] **W4** `liveCounts` gone; ≥10 pairs byte-identical.
- [ ] **F1** no row shows `fired = none` beside `PROVEN RED`; banner `65 PROVEN RED · 3 EXEMPT · 15 CLEAN`; every stated count corrected, not incremented.
- [ ] **F2/F3** both tips derived — add a scratch fixture, numbers move, no string edited.
- [ ] **F4** grep `"proven · step 3 green"` → 0 hits.
- [ ] **F5** modelOf-reads vs cfgDefs-renders difference empty but for metadata.
- [ ] **F6** every commit pill carries a word. Screenshot.
- [ ] **F7** no COCKPIT control claims an effect it does not have.
- [ ] **F8** off-vault name → `PLAYER_ID_UNRESOLVED` + remedy; no node; no `NO_CALL`.
- [ ] **O1** `pairNodeIdOf` order-insensitive; ≥10 pairs identical either way; `common`/`h2h` unchanged. **Grep: no `predHomeSide`; `predReferenceOrder` takes exactly two parameters.**
- [ ] **O2** both orders → same favoured player on OO2/OO3 cards. Screenshot both. No `L.get` re-issued.
- [ ] **O3** note present, ≤110 chars, no home/away-as-ordering claim.
- [ ] **O4** fixture red when `predReferenceOrder` is stubbed to input order. Restored.
- [ ] **S1** Owner has accepted §5A **before** S2–S5 were started.
- [ ] **S2–S5** seven `callGap` keys live; three `negligibleGap` keys retired; `signalCallOf` is the only producer of a call; calibration reports accuracy **and** coverage; both fixtures red.
- [ ] Spec `v3.9` created, `v3.8` stubbed, the six allowed edits applied, **no existing formula / cut-point / refusal / schema touched** — diff and confirm.
- [ ] Both cold-starts current; file renamed; `vbump_log` added; `config_version` = 25.
- [ ] Three things you would improve listed; craft gaps fixed; re-rendered; re-checked (CLAUDE.md gate).

---

## 31 · HARD DON'TS

- **No calibrating on leaked data.** Stage 1 lands first. Any number produced before L1 is void.
- **No `homeSide` parameter, no home/away hook, no `predHomeSide` anything** (R3, B0.15).
- **No touching `ratingOf`, `tpiOf`, `commonOpponentsOf`, `h2hOf`, `oo2Of`, `oo3Of`, `fatigueOf` or
  `blendOf`'s formula** (R4). W2 adds a guard *before* a division; W4 removes a dead parameter.
- **No second class taxonomy.** §5A reuses `call_cutpoints`. Clear / Plain / Tight, once.
- **No incrementing "64".** It was never right. Correct it to 61 in the record, then land 65.
- **No hand-counted figure in a tip** (F2/F3).
- **No node id built by string concatenation outside `nodeIdOf` / `pairNodeIdOf`.** Three shipped
  defects came from hand-built ids.
- **No Stage 5 before the Owner accepts §5A.**
- **No accuracy figure reported without its call count.** A gap that lifts accuracy by silencing the
  system is a worse parameter, not a better one.
- **No computation on a surface.** O2's inversion is a sign-exact flip (§8.1, B0.13).
- **No weakening a fixture assertion to make it pass.** If a fixture vault will not exercise its
  violation, stop and ask.
- **No deleting from `_quarantine-for-deletion/` without the Owner's word.**
- **No shipping under `v1.25.0`.**
