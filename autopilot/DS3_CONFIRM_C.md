# DS3_CONFIRM_C - DR5m_pb1_rm0.5 X60_75 (direct L2 basis) as a stack add under a hard total-contract cap (D3CFC, 2026-10-28)
Research only; CPU-only; nothing live. Prereg `l2vast/ds3/prereg/D3CFC_prereg.md` sha256 1c1f27d21266d561284acbbaafad0d872819c84192dfcfbc1a1a2e3d2647454d (18 cells = 2 stacks x 3 caps x 3 windows; F = 18; ledger +18 to 68,221), logged before any capped P&L was computed. PRE-only text `DS3_CONFIRM_C_PREHOLD.md` (sha256 33899822...2c28); ONE holdout look + second-holdout (X) look logged (tracks D3CFC_CAPS, D3CFC_CAPS_SPAN2). UNTOUCHED never read. Code `l2vast/ds3/code/cfc/`, outputs `l2vast/ds3/out/cfc/` (caps_pre.json, caps_final.json, events_caps.parquet, diag_cut_trades.txt).

## Setup (what exactly was run)
- Trade list: D3O1 direct basis, 429 trades 2023-02..2026-10-09, DR5m_pb1_rm0.5 X60_75, 10 lots, od_asm.py logic (stop exits XJ touch-join, targets as limit fills = optimistic upper bound). Uncapped reproduces D3O1 exactly: WF +5,742, WFPRE +6,980, HOLD +4,293, X +2,441 $/wk.
- Live stack = o2_conc.py timeline (the 57-lot-peak engine): ST10+HM10+WT7, KB/SM/PB at 10 lots x frozen monthly weights (stack A, gross peak 48.7), entries 09:00-09:59 blocked, post-lock exits. Stack B (reading of "current lots"): same rows, all weights 1 = KB10/SM10/PB10 as in the W44 live files (gross peak 57). Both are scored because "current lots" is ambiguous; A is what the 57-lot peak was computed on.
- Cap rule: hard cap on TOTAL gross open contracts. Per DR5m trade allowed = clip(floor(cap - peak live gross over [entry, exit]), 0, 10) whole contracts (0 = not taken). The reduced trade re-runs through the exact lock engine (o2_eng.run_ext, spec stk) at those lots (locks key on realised dollars, so this is not P&L x fraction).
- Windows: WF 2024-02..2026-10-16 (142 wk), HOLD 2025-07+ (68 wk), X 2023-04..2024-01 (44 wk).

## Table 1 - the add under each cap (stack A = the 57-lot-peak engine; d = stack-add vs the live stack; CI = paired bootstrap, 1000 draws)
| cap | window | trades | cut to 0 | partial | add mean/wk | add maxDD | add Sharpe | stack d_mean [95% CI] | d_Sharpe | d_maxDD | uncapped d_mean [CI] | uncapped d_Sharpe | uncapped d_maxDD | capped - uncapped d_mean [CI] | mean retained |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 40 | WF | 327 | 13 (4.0%) | 12 (3.7%) | 4,799 | 118,910 | 1.86 | +4,799 [1,863, 7,798] | +0.208 | -70,172 | +5,742 [2,561, 8,990] | +0.257 | -80,638 | -943 [-1,696, -265] | 84% |
| 40 | HOLD | 157 | 1 (0.6%) | 1 (0.6%) | 3,919 | 118,910 | 1.50 | +3,919 [-601, 8,372] | +0.169 | -70,172 | +4,293 [-262, 8,697] | +0.188 | -80,638 | -374 [-969, 0] | 91% |
| 40 | X | 91 | 22 (24.2%) | 9 (9.9%) | -1,254 | 72,654 | -0.61 | -1,254 [-5,508, 3,042] | -0.079 | +33,527 | +2,441 [-3,061, 8,111] | +0.210 | +146 | -3,695 [-6,706, -747] | -51% |
| 50 | WF | 327 | 0 (0.0%) | 9 (2.8%) | 5,448 | 118,910 | 1.99 | +5,448 [2,332, 8,576] | +0.243 | -80,638 | +5,742 [2,561, 8,990] | +0.257 | -80,638 | -294 [-567, -105] | 95% |
| 50 | HOLD | 157 | 0 | 1 (0.6%) | 4,205 | 118,910 | 1.58 | +4,205 [-329, 8,632] | +0.185 | -80,638 | +4,293 [-262, 8,697] | +0.188 | -80,638 | -88 [-264, 0] | 98% |
| 50 | X | 91 | 0 | 13 (14.3%) | 299 | 90,271 | 0.12 | +299 [-4,842, 5,491] | +0.049 | +19,583 | +2,441 [-3,061, 8,111] | +0.210 | +146 | -2,141 [-3,617, -762] | 12% |
| 60 | WF | 327 | 0 | 0 | 5,742 | 118,910 | 2.06 | = uncapped | +0.257 | -80,638 | +5,742 [2,561, 8,990] | +0.257 | -80,638 | 0 | 100% |
| 60 | HOLD | 157 | 0 | 0 | 4,293 | 118,910 | 1.61 | = uncapped | +0.188 | -80,638 | | | | 0 | 100% |
| 60 | X | 91 | 0 | 0 | 2,441 | 81,496 | 0.90 | = uncapped | +0.210 | +146 | | | | 0 | 100% |
(Stack A, cap 60: the weighted live stack peaks at 48.7 + 10 = 58.7 < 60, so a cap of 60 never binds. The d_maxDD column is the change in the STACK's maxDD from adding the book; negative = better.)

## Table 2 - stack B (all live books at the 10-lot W44 live lots; stack-only gross peak 57)
| cap | window | trades | cut to 0 | partial | add mean/wk | stack d_mean [95% CI] | d_Sharpe | d_maxDD | uncapped d_Sharpe | capped - uncapped d_mean [CI] | retained |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 40 | WF | 327 | 31 (9.5%) | 8 (2.4%) | 4,179 | +4,179 [1,367, 6,952] | +0.135 | -52,663 | +0.200 | -1,563 [-2,793, -366] | 73% |
| 40 | HOLD | 157 | 5 (3.2%) | 3 (1.9%) | 3,706 | +3,706 [-600, 8,101] | +0.101 | -52,663 | +0.139 | -586 [-1,617, 360] | 86% |
| 40 | X | 91 | 30 (33.0%) | 4 (4.4%) | -1,626 | -1,626 [-5,649, 2,673] | -0.089 | +28,449 | +0.185 | -4,067 [-7,755, -542] | -67% |
| 50 | WF | 327 | 13 (4.0%) | 2 (0.6%) | 4,871 | +4,871 [1,936, 7,886] | +0.163 | -65,686 | +0.200 | -871 [-1,593, -224] | 85% |
| 50 | HOLD | 157 | 2 (1.3%) | 0 | 3,853 | +3,853 [-633, 8,367] | +0.119 | -65,686 | +0.139 | -440 [-1,099, 0] | 90% |
| 50 | X | 91 | 14 (15.4%) | 11 (12.1%) | -892 | -892 [-5,423, 3,550] | -0.032 | +19,478 | +0.185 | -3,332 [-5,886, -663] | -37% |
| 60 | WF | 327 | 0 | 7 (2.1%) | 5,346 | +5,346 [2,249, 8,490] | +0.185 | -80,638 | +0.200 | -396 [-793, -129] | 93% |
| 60 | HOLD | 157 | 0 | 1 (0.6%) | 4,139 | +4,139 [-511, 8,632] | +0.135 | -80,638 | +0.139 | -154 [-462, 0] | 96% |
| 60 | X | 91 | 0 | 10 (11.0%) | 648 | +648 [-4,600, 5,923] | +0.073 | +6,809 | +0.185 | -1,792 [-3,044, -604] | 27% |
All-trade cut fractions (429 trades, 2023-02..2026-10-09; stack A / stack B): cap 40 cut to 0 8.9% / 14.9%, partial 4.9% / 2.8%; cap 50 0.0% / 6.5%, partial 5.8% / 3.5%; cap 60 0% / 0%, partial 0% / 4.0%. At-entry-only rule (no look at the stack's later entries): cut-to-0 5.4% / 14.9% (cap 40), 0% / 6.5% (cap 50).

## Margin (no margin schedule exists on disk)
FEES.md, INSTRUMENT_INVENTORY.md and INSTRUMENT_COSTS.md contain NO margin numbers (INSTRUMENT_COSTS: "no margin schedule on disk"). Assumption (as every earlier file): 5% of notional, NQ 21,000 x $20 = $21,000 per contract. This is an exchange-overnight-style proxy; the broker's INTRADAY NQ margin is firm-specific, normally far lower, and is NOT known here: the user must confirm it.
| arm | peak total gross lots (all windows) | 5%-proxy margin | account-break-even margin per contract ($700k / peak) |
|---|---|---|---|
| stack A alone | 48.7 | $1.02M | $14.4k |
| A + DR5m uncapped | 58.7 | $1.23M | $11.9k |
| A + DR5m, cap 50 | 50.0 | $1.05M | $14.0k |
| A + DR5m, cap 40 | 48.7 (stack alone already above 40; DR5m is cut, the cap itself is breached by the live books) | $1.02M | $14.4k |
| stack B alone | 57.0 | $1.20M | $12.3k |
| B + DR5m uncapped | 67.0 | $1.41M | $10.4k |
| B + DR5m, cap 60 | 60.0 | $1.26M | $11.7k |
| B + DR5m, cap 50 | 57.0 (stack alone above 50) | $1.20M | $12.3k |
Reading: capping DR5m at 50 lowers the proxy peak from $1.23M to $1.05M (A) but the live books alone are at $1.02M-$1.20M on this proxy. The cap only protects the account if the broker's real per-contract intraday margin is the binding number; at 5% the account is over-margined with or without DR5m, so the cap does not solve the margin question, the stack does. Per-contract grid: peak lots x margin per contract (e.g. at $1,000/contract the 58.7-lot peak needs $59k; at $5,000 $294k; at $10,000 $587k; at $11.9k it equals the $700k account).

## Verdict (prereg definition: WF AND HOLD d_mean > 0, d_Sharpe > 0, X d_mean >= 0, >= 75% of uncapped WF d_mean retained)
- Stack A: cap 60 = uncapped (never binds). Cap 50: WF/HOLD survive (95% / 98% of the mean kept, d_Sharpe +0.243 / +0.185 vs +0.257 / +0.188; d_maxDD unchanged -80.6k) but X d_mean falls from +2,441 to +299 (12% kept): FAILS the X criterion. Cap 40: WF 84%, HOLD 91% kept, X turns negative (-1,254): FAILS. So no capped arm passes the X condition at cap 40 or 50; WF/HOLD alone say cap 50 is nearly free (-294/wk [-567,-105] WF).
- Stack B (live books at 10 lots each): cap 60 survives WF/HOLD (93% / 96%) and X is +648 (27%); cap 50: WF 85%, HOLD 90%, X negative; cap 40: WF 73%, X negative.
- WHY X breaks (post-hoc, descriptive, from the same look; `diag_cut_trades.txt`): the trades the cap cuts are not random: in X the 13 partially-cut trades (cap 50, A) are 92% winners (mean +$12.1k vs -$0.6k for uncut), WF 9 cut trades 89% winners (+$11.6k vs +$2.2k). DR5m wins when the market trends and that is when the other books are loaded in the same direction, and a winning (target-hit) trade also stays open longer, so the peak-over-hold rule overlaps more stack entries (a duration/look-ahead bias that penalises DR5m; the at-entry-only cut fractions are lower, 5.4% vs 8.9% at cap 40 on A, but at-entry P&L was NOT scored: it would re-read the windows). The X result rests on 13-31 trades and a window where uncapped X is itself not significant (CI [-3,061, 8,111]); treat as a warning, not proof.
- Bottom line: a hard cap at 50-60 costs only 0-15% of the mean in WF/HOLD and leaves the maxDD benefit intact, but it cuts DR5m exactly on its best (trend) days, wipes the 2023-span result at 40-50, and does not make the 5%-proxy margin fit a $700k account. Cap-survivable: at 60 yes (stack A unaffected; stack B -7%/-4%), at 50 only on WF/HOLD, at 40 no.

## Power / multiplicity
MDE (paired, WF 142 wk) about 4-5k $/wk, HOLD 6-7k, X 7-8k: every capped-minus-uncapped difference is far below MDE in HOLD and X, so these are point estimates; the WF paired CI of capped-minus-uncapped excludes 0 (it is a deterministic subset of the same trades, so the paired CI is tight and is mostly the lost P&L). F = 18, all reported, no selection; the uncapped parent already fails the program-level best-of-N (forward-register only). The cap changes nothing about that.

## Deviations / disclosures
1. Per-event cut fractions (not P&L) were printed before the prereg text (cfc_prep.py, outcome-free). 2. Stack B (nominal lots) and the integer-floor rule are D3CFC's reading of "current lots" and "takes only what the cap allows"; o2_conc.py used fractional lots and stack A only (cap-50 cost there 4.7% on the nominal basis vs 5% of mean here). 3. Peak-over-hold is look-ahead on the stack's later entries (DR5m treated as junior), conservative for DR5m; in live the cap would instead block the stack's later entries. 4. Stack A weights before 2023-04 are garbage in the source (25,000x) and were overwritten with the first valid vector (outside all scored windows; trades before 2023-04 are not in any window). 5. The stack timeline contains only ST/HM/WT/KB/SM/PB (as o2_conc.py), not DS4 MV, DN or DS5 books: the true live total may be higher. 6. Direct basis = optimistic upper bound (XJ stop-join credit, target limit fills assumed). 7. Post-hoc descriptive cut-trade character table re-uses the already-looked windows' uncapped trade nets (no new scoring). 8. The 18 cells are 2 stacks x 3 caps x 3 windows; margin proxy is an assumption, not a fact.
