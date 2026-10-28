# DS3 per-session brackets (D3BA, T-BRACKET section A addendum) - SCREEN + DIRECT SURVIVORS (2026-10-28 00:44Z)

**Verdict counts: {'SCREENED': 285, 'DEAD': 15}.** 300 cells (5 books x 3 sessions x 20), 15 preregs (sha256 in autopilot/DECISIONS.md, l2vast/ds3/prereg/BAS_<book>_<session>_prereg.md), ledger counted. Books: ST, HM (10-lot DS2 books), KB, SM, PE = PB3B_R5_P1 (10 fixed lots; its variable pullback-sized lots are not modelled); PB_ST10_SWZ_T3 has no trade list in the registry: not run. EM is not in this addendum.

**Basis.** Every cell was screened on the CALIBRATED-MAPPED basis: the exit-type execution correction is fitted on the stage-1 direct replay (year x target distance x stop distance); for cells with a 40-pt stop, whose distance lies outside the 60-90 pt fit range, the stop-exit execution credit is capped at 0 (conservative basis). Only the survivors (top screened cell per book x session = 15 cells) are repriced by DIRECT L2 replay (session-s trades of the swapped sequence, plus a replayed 60/60 base for method-matched pairing). Unreplayed cells are SCREENED, not PASS/CANDIDATE. Dollar locks stay at the fixed live values (10-lot R = $12,000); lots fixed at 10.

**Method.** The bracket is applied only to entries whose entry time falls in the session (ASIA 18:00-02:00, LONDON 02:00-09:30, NY 09:30-16:55 ET), other sessions keep 60/60; the sequence is regenerated with busy logic through the 1-s path; the paired delta is on identical entries of the session; weekly mean / SD / maxDD of the WHOLE book through the exact per-book lock engine; ATR cells: target = k x the IS (to 2024-01) median 30-min range of the session: ASIA 12.0, LONDON 21.25, NY 42.5 pt (targets rounded to 1 pt: ASIA 12/18/24, LONDON 21/32/42, NY 42/64/85), stop 60 (R<1 when the target is below 60).

**Direct-replay cost/ETA (asked by the lead).** Exit pricing needs a new pass per new (target, stop) bracket; the stage-1 event tables only cover (30,40,45) x (60,75) for ST/HM and (30,40) x 60 for KB/SM, and cannot be reused for other brackets because the replay prices OCO exits per fill. Cost 0.39 worker-hours per 1,000 priced trades: all 300 cells on all sessions would be about 235 worker-hours (about 65 h at 3.5 workers); the survivor-only pass (session trades only: 35k trades + 34k base trades) is about 27 worker-hours.

## Survivors (top screened cell per book x session)
| cell | n sess. trades | required win | observed win (gap CI) | avg win / loss | paired pts/trade WF [CI] | MDE | PRE | HOLD | SPAN2 | 2x | whole-book WF d mean $/wk [CI] | d SD | d maxDD | neighbours | placebo rank raw/recentred | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ST_ASIA_t90_s40 | 2171 | 0.316 | 0.341 (+0.026) | 84.6 / -39.2 | +1.00 [-1.29, +3.15] | 3.32 | -0.80 | +2.27 | +3.25 | +0.35 | -5,612 [-13,478, +2,174] | -1,845 | +26,066 | disagree | 0.05/0.85 | DEAD |
| ST_LONDON_k2 | 2634 | 0.593 | 0.594 (+0.001) | 39.8 / -57.8 | +0.06 [-1.33, +1.49] | 2.04 | -0.04 | +0.14 | +0.05 | -0.00 | -3,052 [-6,371, +257] | -4,830 | +48,673 | disagree | 0.70/0.65 | DEAD |
| ST_NY_t40_s75 | 4167 | 0.658 | 0.648 (-0.010) | 37.1 / -63.0 | +0.17 [-1.08, +1.33] | 1.83 | -0.06 | +0.36 | +2.49 | -0.57 | -1,278 [-4,719, +2,199] | -3,306 | +20,134 | agree | 0.95/0.65 | DEAD |
| HM_ASIA_t75_s60 | 1710 | 0.448 | 0.475 (+0.027) | 71.9 / -57.8 | +0.74 [-0.87, +2.10] | 2.15 | +0.85 | +0.65 | -1.07 | +0.94 | -2,623 [-7,978, +2,472] | -3,033 | +62,613 | disagree | 0.60/0.80 | DEAD |
| HM_LONDON_k1 | 2538 | 0.750 | 0.738 (-0.012) | 19.7 / -54.0 | -0.47 [-2.94, +1.90] | 3.51 | -0.55 | -0.41 | -0.42 | -1.04 | -4,177 [-9,616, +906] | -3,769 | +226,312 | disagree | 0.65/0.45 | DEAD |
| HM_NY_t60_s75 | 2567 | 0.560 | 0.559 (-0.001) | 53.3 / -64.1 | +0.86 [-0.26, +1.97] | 1.63 | +2.09 | -0.19 | +0.92 | +1.16 | +1,428 [-1,507, +4,388] | +1,933 | +29,245 | disagree | 1.00/0.85 | DEAD |
| KB_ASIA_t60_s75 | 2080 | 0.566 | 0.579 (+0.013) | 57.0 / -71.9 | +0.63 [-0.83, +2.05] | 2.03 | +2.27 | -0.52 | +3.18 | -0.22 | -1,331 [-7,490, +5,396] | +230 | +140,965 | disagree | 1.00/0.90 | DEAD |
| KB_LONDON_t30_s75 | 2786 | 0.722 | 0.709 (-0.013) | 28.4 / -69.8 | -0.29 [-2.45, +1.90] | 3.16 | +0.25 | -0.67 | -1.30 | -0.62 | -2,742 [-9,445, +3,484] | -3,877 | +101,483 | disagree | 0.80/0.40 | DEAD |
| KB_NY_t75_s40 | 4481 | 0.356 | 0.364 (+0.008) | 65.8 / -37.5 | +0.65 [-0.64, +1.86] | 1.84 | -0.47 | +1.54 | +0.28 | -0.25 | -4,337 [-9,141, +1,202] | -3,605 | -22,100 | disagree | 0.50/0.80 | DEAD |
| SM_ASIA_t40_s60 | 720 | 0.608 | 0.647 (+0.039) | 37.7 / -57.4 | -0.13 [-2.83, +2.82] | 4.11 | -1.20 | +0.68 | -2.03 | -0.50 | -215 [-3,115, +2,878] | -1,342 | -11,177 | disagree | 0.65/0.55 | DEAD |
| SM_LONDON_t60_s75 | 816 | 0.564 | 0.567 (+0.004) | 57.0 / -70.9 | +0.50 [-1.61, +2.65] | 3.00 | +0.82 | +0.19 | -0.57 | -0.34 | -321 [-3,107, +2,276] | +2,959 | +35,304 | disagree | 0.85/0.65 | DEAD |
| SM_NY_t60_s40 | 847 | 0.414 | 0.443 (+0.029) | 51.9 / -37.0 | +0.30 [-1.89, +2.37] | 3.07 | +0.07 | +0.57 | +0.51 | -0.40 | -146 [-1,805, +1,620] | +236 | -4,560 | agree | 0.40/0.60 | DEAD |
| PE_ASIA_t60_s75 | 1934 | 0.560 | 0.577 (+0.017) | 57.7 / -71.7 | -0.49 [-1.72, +0.86] | 1.84 | -1.07 | -0.10 | +0.60 | -0.48 | -1,822 [-7,587, +4,241] | -1,570 | -7,341 | agree | 0.55/0.25 | DEAD |
| PE_LONDON_t75_s60 | 1879 | 0.446 | 0.457 (+0.011) | 72.1 / -57.8 | +0.36 [-1.11, +1.68] | 1.94 | +1.47 | -0.44 | -1.21 | +0.42 | +2,229 [-1,251, +5,817] | +577 | -41,025 | agree | 0.40/0.85 | DEAD |
| PE_NY_k1 | 3929 | 0.594 | 0.580 (-0.014) | 38.4 / -53.9 | -0.41 [-1.27, +0.51] | 1.28 | +0.07 | -0.83 | -0.44 | -0.54 | -889 [-3,758, +1,992] | -2,056 | -67,235 | disagree | 0.55/0.20 | DEAD |

## 3-session bracket table per book (base 60/60 everywhere unless a cell is a PASS/CANDIDATE)
- **ST**: no PASS or CANDIDATE: ASIA 60/60, LONDON 60/60, NY 60/60 (all sessions keep the base bracket).
- **HM**: no PASS or CANDIDATE: ASIA 60/60, LONDON 60/60, NY 60/60 (all sessions keep the base bracket).
- **KB**: no PASS or CANDIDATE: ASIA 60/60, LONDON 60/60, NY 60/60 (all sessions keep the base bracket).
- **SM**: no PASS or CANDIDATE: ASIA 60/60, LONDON 60/60, NY 60/60 (all sessions keep the base bracket).
- **PE**: no PASS or CANDIDATE: ASIA 60/60, LONDON 60/60, NY 60/60 (all sessions keep the base bracket).

## All 300 cells (screen basis unless stage = direct)
Full table with required vs observed win rate, paired deltas, whole-book weekly stats: l2vast/ds3/out/ba/sess_screen.csv (screen) and rows/DS3_TBRACKET_SESSION.json (all cells, `stage` field).

Top 8 screened paired effects (MDE next to each): KB_ASIA_t60_s75 +1.38 [-0.16, +2.82] MDE 2.06; SM_LONDON_t60_s75 +1.24 [-1.00, +3.51] MDE 3.22; ST_NY_t40_s75 +0.99 [-0.36, +2.27] MDE 1.95; KB_ASIA_t90_s75 +0.79 [-2.25, +3.89] MDE 4.39; SM_LONDON_t40_s75 +0.75 [-2.33, +3.65] MDE 4.16; SM_LONDON_t30_s75 +0.72 [-2.68, +4.12] MDE 4.75; ST_NY_t30_s75 +0.70 [-0.82, +2.09] MDE 2.14; ST_NY_t40_s60 +0.63 [-0.45, +1.71] MDE 1.53

Cells with a screened paired CI above 0: 0 of 300; with positive WF, PRE, HOLD and SPAN2 effects: 8 (selection among 20 cells per session; a best-of-20 positive is expected under the null).

Nearest scored cells: D3BA stage 1 (all-session grid), STRUCT48 T1.4, FAILPRED STEP2 C1/C2, D3NT (fixed target 55/57 comparison; targets 40/45/60 overlap conceptually). No gate softened; MDE (2-5 pt/trade at session size) exceeds every screened effect, so a null here means "could not have seen less than the MDE".
