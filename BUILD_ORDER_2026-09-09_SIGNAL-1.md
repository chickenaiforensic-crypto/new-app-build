# BUILD ORDER — SIGNAL 1 · RATINGS H2H

**One signal. Correct match after match. Reflected truthfully on the surface.**

Issued: 2026-09-09 · Owner authorisation: `V1c proceed`, 2026-09-09
Engine: `Dalxic Stats Engine v1.26.0-wip.dc.html` · Contract: `DALXIC_BUILD_CONSOLIDATED_v3.8.md` §5 Signal 1 · §5 Signal 4 · §6 · §8.1 · §10

> **Scope.** Signal 1 (`rating:player:{id}[:{surface}]@{date}`) and nothing else. Signal 4 (Surface
> Factor) is in scope **only because it is the same node and the same function** with a qualifier.
> No other signal, no Combiner, no page beyond the Fact Checker's descent. When this order closes,
> **Ratings H2H is finished and there is no further work on it.**
>
> This order supersedes **V1c** in `BUILD_ORDER_2026-09-09_v1.26.0.md`, which is folded in whole
> (parts R5/R6 below). Everything else in that order stands untouched.

**Already landed and not repeated here:** V1b-2 — the Stage-4 divisor now counts as at the match's
own date (Owner ruling 2026-09-09). It does not feed Signal 1 (proven: 344 readings, zero moved) but
it is in the same file and must stay green.

---

## 0 · WHAT "100% CORRECT" MEANS FOR THIS SIGNAL

Four claims, each of which must be provable by a gate, not by inspection:

1. **The formula is the contract's formula.** `Rating = Σ own points (in window) ÷ Σ opp points (same matches)` — hand-derived, fixture-asserted.
2. **Every match is accounted for.** Considered, used, or excluded-by-name. Nothing silently dropped, inside a match or across the set.
3. **No configuration can change the number silently.** A bad window or a bad minimum refuses by name; it never widens the window or disables a gate.
4. **The surface reconstructs the number.** The operator can reach every row, see each row's own contribution, and watch the running total close exactly on the headline.

---

## 1 · THE CHAIN — everything Signal 1 touches

```
rating:player:{id}[:{surface}]@{date}
 └─ ratingOf(playerId, atDate, canon, cfg, dateIndex, surface)            engine 1331-1353
     ├─ priorMatchesOf(canon, playerId, atDate, inclusive = true)         engine 1294-1305
     ├─ surface filter          c.surface === surface  (strict equality)
     ├─ parseRatingsWindowOf(cfg.signalRatingsWindow, atDate)             engine 1318-1324
     └─ per row: ownOppPointsOf(row, playerId, cfg, dateIndex)            engine 1309-1314
                  └─ matchFlatScoreOf(row, cfg, dateIndex)                engine 1263-1290
                      ├─ parseRawScoreOf   §3 Stage 1
                      ├─ reduceSetOf       §3 Stage 2
                      └─ pointsForGamesOf + setFlatOf   §3 Stage 3
                      (Stage 4's divisor is NOT read by Signal 1 — it takes
                       winnerSum / loserSum, which are pre-divisor)
```

**Signal 1 depends on §3 Stages 1-3 and nothing else.** That boundary is why this order can close
one signal completely without waiting for the rest.

---

## 2 · DEFECT REGISTER — Signal 1, complete

Every entry measured on the live vault against `rating:player:jannik-sinner@2026-09-08`
(**value 1.6873 · own 712.9 · opp 422.5 · used 303**).

| # | Defect | Measured evidence | Law |
|---|---|---|---|
| **S1-1** | 263 of 303 source rows unreachable — hard `slice(0, 40)`, no page, no scroll, no search | the 40 visible rows sum to own **94.6** / opp **45.9** against a headline of 712.9 / 422.5 — **13% reconcilable** | §10 lineage |
| **S1-2** | 8 rows silently dropped — `if (!p.ok) continue;` | **311 considered, 303 used.** 6 walkovers + 2 retirements (`"5-0"`, `"4-1"`) named nowhere | B0.3 |
| **S1-3** | No per-row contribution — columns stop at `SCORE`, `RND` | the headline cannot be checked against any row | §10 lineage |
| **S1-4** | The descent flips perspective — rating says `own/opp`, `points:{id}` shows `winner/loser` | on a match Sinner lost, column 1 is his opponent; nothing says so | §10 lineage |
| **S1-5** | 8 used matches scored only **part** of their sets, unflagged | 8 sets dropped inside otherwise-scoring matches; the table cannot tell them from clean ones | B0.3 |
| **S1-6** | **A window typo silently reads as "All"** | `"6 months"` → **303 matches, 1.6873**. `"Months:6"` → **37 matches, 2.1333**. A **26% swing**, no warning. `parseRatingsWindowOf` returns `null` for anything unrecognised — the comment says so | B0.3 |
| **S1-7** | **A blank or non-numeric minMatches silently disables the gate** | `parseInt("")` → `NaN`; `used < NaN` is false. **285 of 830 players** resolve that should refuse at minMatches 5 | B0.3 |
| **S1-8** | The Surface card's node id puts the qualifier **after** the moment | built `rating:player:{id}@{date}:Clay` → **1.632 (baseline)** (value 1.6319). Correct `rating:player:{id}:Clay@{date}` → **1.561 (Clay)** | §6 grammar |
| **S1-9** | **The spec contradicts itself** — §5 Signal 4 line 251 gives the node as `…@{date}:{surface}`; §6 line 309 gives the grammar as `[:{qualifier}][@{moment}]` | this is the *cause* of S1-8: the card followed §5, the parser follows §6 | §0.4 — Owner |
| **S1-10** | **No fixture asserts a rating value** | 0 of 33 signal/score fixtures assert a number; all assert refusal or liveness | B0.10 |
| **S1-11** | `ownSum / oppSum` is unguarded | not reachable today — smallest `loserSum` across all scoreable matches is **0.1**, because a scored set always pays the loser ≥ 1 point — but the invariant is undocumented and ungated | B0.3 |

---

## 3 · PART R1 — NO CONFIGURATION CHANGES THE NUMBER SILENTLY

Closes **S1-6**, **S1-7**, **S1-11**.

**R1.1 · The window.** `parseRatingsWindowOf` currently returns `null` for anything it does not
recognise, and `null` means *no lower bound*. Split the two meanings:

```js
// §5 Signal 1 · the window is "All" or "Months:N". Anything else is a NAMED refusal, never a
// silent widening to All — a typo used to move this signal 26% with no warning (B0.3).
function parseRatingsWindowOf(text, atDate) {
  const s = String(text).trim();
  if (/^all$/i.test(s)) return { ok: true, floor: null };
  const mm = /^months:(\d+)$/i.exec(s);
  if (!mm) return { ok: false, refusal: "WINDOW_INVALID", given: s };
  const d = new Date(String(atDate) + "T00:00:00Z");
  d.setUTCMonth(d.getUTCMonth() - parseInt(mm[1], 10));
  return { ok: true, floor: d.toISOString().slice(0, 10) };
}
```
`ratingOf` returns the refusal. **`"All"` and `"Months:N"` behave exactly as today** — this only
removes the silent third path.

**R1.2 · The minimum.** In `ratingOf`, before the gate:
```js
if (!Number.isInteger(minMatches) || minMatches < 0)
  return { ok: false, refusal: "MIN_MATCHES_INVALID", given: String(minMatchesText) };
```
**Do not** substitute a default. A blank field is an operator error and says so.

**R1.3 · The divisor invariant.** Guard the ratio and document why it cannot fire:
```js
// A scored set always pays the loser at least 1 point (points_table floor), so oppSum > 0
// whenever used > 0. Guarded anyway: an unreachable branch that returns a named refusal is
// cheaper than a silent Infinity (B0.3). Smallest loserSum observed on the live vault: 0.1.
if (!(oppSum > 0)) return { ok: false, refusal: "NO_OPPONENT_POINTS", ownSum: round4(ownSum) };
```

**Ledger.** All three carry `detail` + `remedy` (§8.3). `SIGNAL_REMEDY` gains all three codes.

**Acceptance.** `"6 months"` → `WINDOW_INVALID` naming the string, **not** 303 matches.
Blank minimum → `MIN_MATCHES_INVALID`. `"All"` and `"Months:6"` return **1.6873 / 303** and
**2.1333 / 37**, unchanged.

---

## 4 · PART R2 — THE PRODUCER RETURNS ITS LINEAGE

Closes **S1-2**, **S1-3**, **S1-5**. **Additive: `value`, `ownSum`, `oppSum`, `matchesUsed` do not move.**

`ratingOf` records what it already decided instead of discarding it:

```js
for (const c of rows) {
  const p = ownOppPointsOf(c, playerId, cfg, dateIndex);
  if (!p.ok) { lineage.push({ rowIndex: c.rowIndex, used: false, refusal: p.refusal }); continue; }
  ownSum += p.own; oppSum += p.opp; used++; rowIdxs.push(c.rowIndex);
  lineage.push({ rowIndex: c.rowIndex, used: true, own: p.own, opp: p.opp,
    setsScored: p.setsUsed, setsHeld: p.setsHeld,          // S1-5 — partial scoring is visible
    runOwn: round4(ownSum), runOpp: round4(oppSum) });
}
return { ok: true, value: round4(ownSum / oppSum), matchesUsed: used,
  matchesConsidered: lineage.length, matchesExcluded: lineage.length - used,
  ownSum: round4(ownSum), oppSum: round4(oppSum), rowIdxs, lineage, shareA, negligible };
```

`ownOppPointsOf` passes `setsUsed` and `sets.length` through from `matchFlatScoreOf`. **The running
totals are produced here, in R2 COMPUTE — never on the surface (B0.13).**

**Acceptance.** For Sinner @2026-09-08: `matchesConsidered` **311**, `matchesUsed` **303**,
`matchesExcluded` **8**; the 8 carry `WALKOVER` ×6 and `UNPARSEABLE_SCORE` ×2; 8 used rows report
`setsScored < setsHeld`; the final `runOwn`/`runOpp` equal **712.9 / 422.5** exactly.

---

## 5 · PART R3 — THE NODE ID IS BUILT ONCE, CORRECTLY

Closes **S1-8**. Raises **S1-9** to the Owner.

```js
// R2. §6 grammar, one producer (B0.1): quantity:subject[:qualifier][@moment].
// The qualifier ALWAYS precedes the moment. Three shipped defects came from hand-built ids
// (v1.16.1 ratingOf, v1.21.1 blend:pair, and the Surface card).
function nodeIdOf(quantity, subject, qualifier, moment) {
  return quantity + ":" + subject + (qualifier ? ":" + qualifier : "") + (moment ? "@" + moment : "");
}
```
Every `rating:` id in R4 is built through it — the `nodeOf` map (engine **3897-3905**) included.

**Acceptance.** The Surface card's id `parseNode`s to `{ qualifier: "Clay", moment: "<date>" }` and
displays `1.561 (Clay) · 63% - 37%`, not `1.632 (baseline)` (value 1.6319). Grep R4: no `"rating:player:"` string
concatenation survives outside `nodeIdOf`. Live surface values, unchanged and now reachable:
**Hard 1.7318 (182)** · **Clay 1.6792 (79)** · **Grass 1.556 (42)** · **Carpet `NO_SURFACE_HISTORY`**.

---

## 6 · PART R4 — THE DESCENT KEEPS ITS PERSPECTIVE

Closes **S1-4**. `points:{id}` gains the reading player as a qualifier:

- `points:{id}:{playerId}` → columns labelled **`own` / `opp`** for that player.
- `points:{id}` unqualified → columns stay **`winner` / `loser`**, exactly as today.

Built through `nodeIdOf`, so the qualifier precedes the moment. The rating node's `FROM WHAT` rows
link to the **qualified** form, so a descent from a rating never changes whose numbers you are
reading.

**Acceptance.** From `rating:player:jannik-sinner@…`, descending into
`AUSTRA-ATP-2021-R128-008` shows set 1 as **`own 1.00 / opp 0.40`** (Sinner won that set 6-3),
where the unqualified node shows `0.40 / 1.00` winner-first. Both correct; neither ambiguous.

---

## 7 · PART R5 — THE UI REFLECTION

Closes **S1-1**, and renders R2's lineage. This is the Owner's *"clean UI reflection"*.

### 7.1 · Header
```
FROM WHAT          311 ROWS · 303 USED · 8 EXCLUDED
```
Replaces `sourceLabel`. **Delete `sourceTruncLabel` and its `sc-if` block entirely** (UI template
1380-1382) — there is no truncation left to warn about.

### 7.2 · Columns

Five added to the right of `RND`, inside an `overflow-x:auto` container so the **table** scrolls
left and right and the page never does:

| MATCH ID | DATE | WINNER | LOSER | SCORE | RND | **OWN** | **OPP** | **DIFF** | **RATIO** | **RUNNING (Newest → Oldest)** |
|---|---|---|---|---|---|---|---|---|---|---|
| MIAMI-…-F-001 | 2026-07-12 | Sinner | — | 6-7(7) 7-6(2) 6-3 6-4 | F | 3.7 | 2.5 | +1.2 | 1.480 | 1.480 |
| …-SF-001 | 2026-07-10 | Sinner | — | 6-4 6-4 6-4 | SF | 3.0 | 1.2 | +1.8 | 2.500 | 1.811 |
| …-QF-002 | 2026-07-07 | Sinner | — | 7-5 7-6 6-3 | QF | 3.0 | 1.5 | +1.5 | 2.000 | 1.865 |
| … | | | | | | | | | | |
| AUSTRA-…-R128-008 | 2021-02-08 | Shapovalov | Sinner | 3-6 6-3 6-2 4-6 6-4 | R128 | 3.0 | 3.8 | −0.8 | 0.789 | **1.687** |

- **OWN / OPP** — this row's contribution, from the reading player's side.
- **DIFF** — `own − opp`.
- **RATIO** — `own ÷ opp` for that row alone.
- **RUNNING** — `runOwn ÷ runOpp` from the top of the list to that row. **The last row is the
  headline.** Verified: closes on **712.9 / 422.5** and **1.687**.

> **OWNER RULING 2026-09-09 — RUNNING is locked to newest-first.** The table is fixed newest →
> oldest and the column is labelled **`RUNNING (Newest → Oldest)`**. Re-deriving per sort is
> rejected — over-engineering, and compute on the surface. **On any other sort the column hides
> itself or reads `N/A (sort changed)`. It never presents meaningless arithmetic silently.**

### 7.3 · Excluded and partial rows
- **Excluded** row: refused treatment, code in place of the numbers —
  `W/O · WALKOVER · contributes nothing (B0.3)`. Never blank, never zero, never omitted.
- **Partial** row (`setsScored < setsHeld`): amber marker `3 of 5 sets scored`, with the per-set
  detail one click away at `points:{id}:{playerId}`.

### 7.4 · Every row reachable
`source_rows_shown` stops being a truncation and becomes a **page size**: PREV / NEXT, a
`page n of m` label, and a filter matching id / opponent / round. Running totals come from R2 over
the whole lineage, so **page 4 shows the same running figures it would show unpaged**.

### 7.5 · Anchors

| What | Where |
|---|---|
| `ratingOf` accumulation loop | engine **1339-1343** |
| ledger `rating` branch | engine **2298-2340** |
| `srcCap` slice / `sourceRows` | engine **4174-4182** |
| `sourceLabel` / `sourceTruncated` / `sourceTruncLabel` | engine **4328-4330** (and the not-ready mirror at **3276**) |
| FROM WHAT header | UI template 1354-1356 |
| column headers | UI template 1361-1367 |
| `sc-for list="{{ sourceRows }}"` grid (6 cols) | UI template 1369-1378 |
| `sourceTruncated` block — **delete** | UI template 1380-1382 |

---

## 8 · PART R6 — THE GATES (B0.10)

Closes **S1-10**. Base **78** → **83**.

**Refusal fixtures (existing `signal` scope, no runner branch touched) — +2:**

| Code | Plants |
|---|---|
| `WINDOW_INVALID` | `cfgPatch: { signalRatingsWindow: "6 months" }` — must refuse, **not** silently read All |
| `MIN_MATCHES_INVALID` | `cfgPatch: { signalRatingsMinMatchesText: "" }` — must refuse, **not** silently pass |

**Arithmetic fixtures — new `arithmetic` scope, +3.** Each asserts a **hand-derived** value to
`0.0001`. **Never record what the function returned.**

*Worked derivation, `RATING_ARITHMETIC` — from §5 Signal 1 and §3, on paper:*
```
canon: p-x beats p-y 6-0 6-0 on 2025-01-01
§3 Stage 2: 6-0 is a legal final score; no reduction rule matches
§3 Stage 3: points_table 6 games -> 10 pts ; 0 games -> 1 pt ; divisor 10
            per set: winner flat 1.0 · loser flat 0.1 ; two sets -> 2.0 and 0.2
§5 Signal 1: Rating(p-x @2025-06-01) = 2.0 / 0.2 = 10.0000
             Rating(p-y @2025-06-01) = 0.2 / 2.0 =  0.1000
```
*(This derivation was checked against the engine while drafting: it returns 10 and 0.1.)*

| Code | Asserts |
|---|---|
| `RATING_ARITHMETIC` | the two values above, both sides |
| `RATING_SURFACE_ARITHMETIC` | the same canon marked `surface: "Clay"` — the **qualified** node returns the Clay value and an unqualified read returns the baseline; proves R3's grammar end to end |
| `RATING_LINEAGE_COMPLETE` | on a canon holding one scoreable match and one walkover: `matchesConsidered === 2`, `matchesUsed === 1`, `matchesExcluded === 1`, the excluded row carries `WALKOVER`, and the final `runOwn`/`runOpp` equal `ownSum`/`oppSum` |

Gates KPI gains an **ARITHMETIC** tile. **It is a fourth population — never folded into PROVEN RED**,
which proves a gate can go red, not that a number is right.

> **83 fixtures — 63 proven-red · 3 arithmetic-proven · 3 OPEN-exemption · 14 control-clean · 0 open.**

**Mutation test.** Perturb one `points_table` entry → `RATING_ARITHMETIC` and
`RATING_SURFACE_ARITHMETIC` must both go red. Restore.

---

## 9 · OPEN RULINGS — needed before this order can close

**Ruling A · What does `@{date}` mean for this node?**
`rating:player:{id}@2021-02-08` includes matches played **on** 2021-02-08. §5 Signal 4 says
*"≤ target date"*, so the node is **spec-correct** as *"end of day D"*. It only misleads when used to
predict a match on day D — Sinner's rating that day came 100% from the match he lost that day.

- **(a)** *(recommended)* Keep the node as-is — it is the contract — and **state it on the node**:
  `as of : 2021-02-08 (inclusive — matches played that day are counted)`. The backtest already
  excludes the row under test by id (ruled 2026-09-09). Add one guard: if the two players already
  have a match on the entered date, PREDICTION warns that the fixture is in the vault.
- **(b)** Change the node to strictly-prior. **This changes a §5 formula** and needs its own pin.

**Ruling B · §5 Signal 4's node id contradicts §6 (S1-9).**
Line 251 says `rating:player:{id}@{date}:{surface}`; line 309 says `[:{qualifier}][@{moment}]`.
§6 is the parseable one — a date cannot be a qualifier. **Authorise correcting line 251 to
`rating:player:{id}:{surface}@{date}`** as a §13.1-logged spec correction, or rule the other way.
R3 cannot close honestly while the contract says both.

---

## 10 · DEFINITION OF DONE

- [ ] `node --check` clean on the full engine script.
- [ ] Live vault: 14,795 rows · 0 row refusals · 0 edition refusals · 201/201 editions · registry 830.
- [ ] **83 fixtures, 0 open** — 63 proven-red · 3 arithmetic · 3 exemption · 14 control.
- [ ] **R1** `"6 months"` → `WINDOW_INVALID`; blank minimum → `MIN_MATCHES_INVALID`; `"All"` → **1.6873/303**; `"Months:6"` → **2.1333/37**.
- [ ] **R2** Sinner @2026-09-08: considered **311**, used **303**, excluded **8**; `runOwn`/`runOpp` close on **712.9 / 422.5**; `value` **1.6873 unchanged**.
- [ ] **R2 regression** `value` / `ownSum` / `oppSum` / `matchesUsed` byte-identical on **all 830 players** — R2 is additive.
- [ ] **R3** Surface card id parses `{qualifier, moment}` and reads `(Clay)`; Hard **1.7318**/182, Clay **1.6792**/79, Grass **1.556**/42, Carpet `NO_SURFACE_HISTORY`. No hand-built `rating:` id in R4.
- [ ] **R4** `points:{id}:jannik-sinner` labels `own`/`opp`; unqualified still `winner`/`loser`.
- [ ] **R5** header reads `311 ROWS · 303 USED · 8 EXCLUDED`; all 311 reachable by paging; the 8 excluded named; the 8 partial marked; last row's RUNNING reads **1.687**; table scrolls horizontally, page does not; RUNNING hides or reads `N/A` on any other sort.
- [ ] **R6** mutation test red on both arithmetic fixtures, then restored.
- [ ] Rulings **A** and **B** answered and applied.
- [ ] Three things you would improve listed; craft gaps fixed; re-rendered; re-checked (CLAUDE.md gate).

---

## 11 · HARD DON'TS

- **No formula change.** `Rating = Σ own ÷ Σ opp` is the contract. R1 adds refusals, R2 adds a
  record, R3-R5 fix ids and rendering. **The number does not move except where a defect was moving it.**
- **No default substituted for a bad config value.** A typo refuses by name (B0.3).
- **No silent exclusion.** Every considered row is used or named.
- **No arithmetic fixture whose expected value was read off the function.** Hand-derive or it proves nothing.
- **No hand-built node id.** Everything through `nodeIdOf`.
- **No compute on the surface.** Running totals come from R2 (B0.13, §8.1).
- **No RUNNING column under a sort it was not defined for.**
- **No folding `arithmetic` into PROVEN RED.**
- **No touching any other signal, the Combiner, or M-Fit.**
- **Nothing ships under `v1.25.0`**, and nothing calls itself `v1.26.0` until the wider order closes.
