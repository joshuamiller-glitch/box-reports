# DS3 per-session brackets (D3BA, T-BRACKET section A addendum) - SCREEN (direct replay of 15 survivors pending) (2026-10-27 16:13Z)

**Verdict counts: {'SCREENED': 300}.** 300 cells (5 books x 3 sessions x 20), 15 preregs (sha256 in autopilot/DECISIONS.md, l2vast/ds3/prereg/BAS_<book>_<session>_prereg.md), ledger counted. Books: ST, HM (10-lot DS2 books), KB, SM, PE = PB3B_R5_P1 (10 fixed lots; its variable pullback-sized lots are not modelled); PB_ST10_SWZ_T3 has no trade list in the registry: not run. EM is not in this addendum.

**Basis.** Every cell was screened on the CALIBRATED-MAPPED basis: the exit-type execution correction is fitted on the stage-1 direct replay (year x target distance x stop distance); for cells with a 40-pt stop, whose distance lies outside the 60-90 pt fit range, the stop-exit execution credit is capped at 0 (conservative basis). Only the survivors (top screened cell per book x session = 15 cells) are repriced by DIRECT L2 replay (session-s trades of the swapped sequence, plus a replayed 60/60 base for method-matched pairing). Unreplayed cells are SCREENED, not PASS/CANDIDATE. Dollar locks stay at the fixed live values (10-lot R = $12,000); lots fixed at 10.

**Method.** The bracket is applied only to entries whose entry time falls in the session (ASIA 18:00-02:00, LONDON 02:00-09:30, NY 09:30-16:55 ET), other sessions keep 60/60; the sequence is regenerated with busy logic through the 1-s path; the paired delta is on identical entries of the session; weekly mean / SD / maxDD of the WHOLE book through the exact per-book lock engine; ATR cells: target = k x the IS (to 2024-01) median 30-min range of the session: ASIA 12.0, LONDON 21.25, NY 42.5 pt (targets rounded to 1 pt: ASIA 12/18/24, LONDON 21/32/42, NY 42/64/85), stop 60 (R<1 when the target is below 60).

**Direct-replay cost/ETA (asked by the lead).** Exit pricing needs a new pass per new (target, stop) bracket; the stage-1 event tables only cover (30,40,45) x (60,75) for ST/HM and (30,40) x 60 for KB/SM, and cannot be reused for other brackets because the replay prices OCO exits per fill. Cost 0.39 worker-hours per 1,000 priced trades: all 300 cells on all sessions would be about 235 worker-hours (about 65 h at 3.5 workers); the survivor-only pass (session trades only: 35k trades + 34k base trades) is about 27 worker-hours.

## Survivors (top screened cell per book x session)
| cell | n sess. trades | required win | observed win (gap CI) | avg win / loss | paired pts/trade WF [CI] | MDE | PRE | HOLD | SPAN2 | 2x | whole-book WF d mean $/wk [CI] | d SD | d maxDD | neighbours | placebo rank raw/recentred | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ST_ASIA_t90_s40 | 2171 | 0.325 | 0.341 (+0.016) | 83.7 / -40.6 | +0.40 [-1.96, +2.55] | 3.34 | -1.96 | +2.06 | +1.42 | -0.85 | -4,533 [-12,469, +3,321] | -7,320 | -16,084 | disagree | nan/nan | SCREENED |
| ST_LONDON_k2 | 2634 | 0.594 | 0.594 (+0.000) | 38.4 / -55.9 | +0.36 [-1.07, +1.83] | 2.05 | +0.24 | +0.45 | -0.38 | +0.59 | +1,186 [-2,563, +4,993] | -1,910 | -35,387 | disagree | nan/nan | SCREENED |
| ST_NY_t40_s75 | 4167 | 0.659 | 0.661 (+0.002) | 36.2 / -65.2 | +0.99 [-0.36, +2.27] | 1.95 | +0.55 | +1.34 | +2.89 | +1.06 | +3,027 [-587, +6,702] | -3,147 | -38,413 | agree | nan/nan | SCREENED |
| HM_ASIA_t75_s60 | 1710 | 0.456 | 0.476 (+0.020) | 69.8 / -58.1 | +0.14 [-1.48, +1.59] | 2.20 | +0.19 | +0.10 | -1.95 | -0.26 | -2,490 [-7,781, +2,462] | -2,880 | -33,252 | disagree | nan/nan | SCREENED |
| HM_LONDON_k1 | 2538 | 0.751 | 0.754 (+0.003) | 18.1 / -54.5 | -0.02 [-2.40, +2.29] | 3.35 | -0.46 | +0.30 | -0.01 | -0.15 | -4,144 [-9,490, +1,128] | -1,528 | +103,981 | disagree | nan/nan | SCREENED |
| HM_NY_t60_s75 | 2567 | 0.563 | 0.558 (-0.005) | 52.6 / -64.1 | +0.50 [-0.67, +1.65] | 1.68 | +2.49 | -1.21 | +1.45 | +0.44 | +2,636 [-295, +5,608] | +1,707 | +5,185 | disagree | nan/nan | SCREENED |
| KB_ASIA_t60_s75 | 2080 | 0.563 | 0.586 (+0.023) | 55.7 / -71.3 | +1.38 [-0.16, +2.82] | 2.06 | +2.97 | +0.28 | +3.08 | +1.28 | +1,578 [-4,701, +7,898] | +1,397 | +9,244 | disagree | nan/nan | SCREENED |
| KB_LONDON_t30_s75 | 2786 | 0.721 | 0.719 (-0.002) | 26.9 / -69.4 | +0.12 [-1.94, +2.39] | 3.22 | +0.31 | -0.02 | -0.56 | +0.19 | -2,194 [-8,169, +4,234] | -1,042 | +179,323 | disagree | nan/nan | SCREENED |
| KB_NY_t75_s40 | 4481 | 0.365 | 0.367 (+0.002) | 65.8 / -39.5 | +0.38 [-0.99, +1.69] | 1.90 | -1.45 | +1.83 | -0.39 | -0.79 | -4,787 [-9,059, -370] | -2,961 | -27,106 | disagree | nan/nan | SCREENED |
| SM_ASIA_t40_s60 | 720 | 0.609 | 0.650 (+0.041) | 36.4 / -55.9 | +0.38 [-2.24, +3.36] | 4.06 | -1.34 | +1.67 | -1.36 | +0.51 | +423 [-2,313, +3,406] | -1,788 | +312 | disagree | nan/nan | SCREENED |
| SM_LONDON_t60_s75 | 816 | 0.563 | 0.574 (+0.011) | 55.6 / -70.5 | +1.24 [-1.00, +3.51] | 3.22 | +1.56 | +0.93 | -0.15 | +1.14 | +574 [-2,208, +3,180] | +1,450 | -7,456 | disagree | nan/nan | SCREENED |
| SM_NY_t60_s40 | 847 | 0.419 | 0.445 (+0.026) | 53.2 / -39.4 | -0.05 [-2.35, +2.03] | 3.15 | -0.20 | +0.13 | +0.69 | -1.10 | -329 [-2,012, +1,285] | -148 | -4,620 | agree | nan/nan | SCREENED |
| PE_ASIA_t60_s75 | 1934 | 0.563 | 0.580 (+0.017) | 55.7 / -71.0 | -0.49 [-1.70, +0.83] | 1.82 | -0.99 | -0.15 | -0.33 | -0.48 | +1,486 [-3,851, +7,533] | -4,003 | +2,994 | agree | nan/nan | SCREENED |
| PE_LONDON_t75_s60 | 1879 | 0.454 | 0.458 (+0.003) | 70.0 / -58.2 | -0.11 [-1.54, +1.18] | 1.96 | +0.72 | -0.71 | -2.66 | -0.52 | +977 [-2,453, +4,250] | -361 | -40,911 | agree | nan/nan | SCREENED |
| PE_NY_k1 | 3929 | 0.593 | 0.585 (-0.008) | 37.7 / -53.9 | +0.04 [-0.87, +1.04] | 1.36 | +0.61 | -0.45 | +0.79 | +0.35 | -48 [-3,094, +3,177] | -55 | -27,420 | disagree | nan/nan | SCREENED |

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
