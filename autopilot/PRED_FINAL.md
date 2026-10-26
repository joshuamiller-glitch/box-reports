# PRED_FINAL (PRED-COORD, 2026-10-24 19:17Z)

**Verdict: NOT FOUND.** No cell reaches the conditional + strata-matched holdout AUC bar (0.68 pooled / 0.66 Asia, h<=+30) on the unlocked label; no cell has more than 2 of 5 economic conditions in cell + neighbours.

## Vetted lead: I5-rocket (block I), Asia +15, UNLOCKED conditional label (FOUND-protocol vetting by predI)

- Holdout (2025-07+) conditional AUC 0.609 [0.550, 0.669]; strata-matched 0.599 [0.535, 0.656]; WF 0.585 [0.542, 0.628]; WF-PRE 0.558. +30: 0.597.
- By year: 2024 0.500 (chance), 2025 0.626, 2026 0.611; 56% of the excess sits in the 12 holdout months. Pooled (all sessions) same features: 0.548.
- CPCV (conditional): rf 0.582 (|WF-CPCV| 0.003). Permutation rank 1.00 (null mean 0.499, sd 0.022). Noise-in-top-20 share 0.24 (FOUND needs 0): FAILS. Brier skill WF +0.007, holdout +0.036 (weak).
- Economic grid (hard/soft/flatten, theta .3-.8, h 10/15/20/30, locks ON): best pass_count 2 of 5; 0 cells with five in cell or in two neighbours.
- Replication: new ROCKET kernels + model seed + shifted folds: Asia h15 0.592 [0.530,0.654] (strata 0.584); reverse-time (2023-04..2024-01, never scored, n=190): 0.556 [0.481,0.624], fails predI pre-set rule.
- Best-of-many: 864 pooled/Asia h<=30 candidate cells in block I round 10. Within-cell placebo (20 seeds, permuted within session-type x entry-count strata, same pipeline incl. per-seed re-selection): holdout mean 0.508 sd 0.032 max 0.571; WF mean 0.526 sd 0.022 max 0.559; 0 of 20 reach 0.609 (3.2 sd above placebo mean) - covers the h15/Asia selection only, not the 864-cell best-of pick. predI files: l2vast/pred/I/out/vet_v1..v6, rows/I_round11.json.
- Short of the bar by ~0.05 AUC (plain), ~0.06 (strata-matched); noise condition and economic conditions fail. NOT FOUND.

## Unlocked leaderboard top 10 (conditional holdout AUC, FOUND-eligible cells: pooled/Asia, h<=+30; locked-label reference column)

| # | family | h | session | unlocked cond HOLD AUC [CI] | strata-matched | unlocked WF | locked reference (cond HOLD) | status |
|---|---|---|---|---|---|---|---|---|
| 1 | I5-rocket | +15 | ASIA | 0.609 [0.55,0.67] | 0.599 | 0.585 | - | vetted lead: NOT FOUND (see above) |
| 2 | R7-pool-share | +10 | ASIA | 0.602 [-,-] | 0.601 | 0.570 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 3 | R7-pool-first | +30 | ASIA | 0.600 [-,-] | 0.597 | 0.561 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 4 | I5-rocket | +30 | ASIA | 0.597 [0.54,0.65] | 0.594 | 0.578 | - | vetted lead: NOT FOUND (see above) |
| 5 | G2 | +15 | ASIA | 0.591 [0.53,0.65] | 0.585 | 0.563 | 0.555 | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 6 | F9-13 | +20 | ASIA | 0.588 [0.53,0.65] | 0.589 | 0.556 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 7 | R7-pool-share | +20 | ASIA | 0.588 [-,-] | 0.588 | 0.586 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 8 | K9-S_I5 | +30 | ASIA | 0.586 [0.52,0.65] | 0.587 | 0.573 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 9 | I5 | +30 | ASIA | 0.586 [0.52,0.65] | 0.587 | 0.573 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |
| 10 | R7-pool-rate | +20 | ASIA | 0.586 [-,-] | 0.579 | 0.567 | - | short of bar by >=0.06; not vetted (same Asia-WF-PRE-weak pattern) |

Unlocked baseline R0u-FR-B (FAILPRED stack trained conditionally), Asia +15 holdout: 0.470 [0.41,0.53]. Pooled +15: 0.453. All are at or below chance.

## Noise ceiling (X1 placebo control X31, labels permuted within session-type x entry-count strata, 96 pooled/Asia cells)

Conditional holdout AUC mean 0.509, sd 0.025, max 0.561; WF-PRE max 0.583 over 288 cells. Conditional AUCs of 0.55-0.58 are within ~2 sd of selection noise.

## Trials and holdout looks (hand-off to STRUCT48 lead)

- Corrected trial count (DSR starting point): **27744** (file l2vast/pred/ledger/trials_corrected.json; convention in SCHEMA.md s.12). Declared (incl. generative-search evaluations, append-only ledger l2vast/pred/ledger/trials.jsonl): 11072541.
- Holdout looks logged: 105 (l2vast/pred/ledger/holdout_looks.jsonl). The holdout (2025-07+) has been read repeatedly across ~80 rounds; any structural-rule FOUND must use a fresh prereg and, where possible, the never-scored 2023-04..2024-01 span.

## Not re-scored on the unlocked label (0 stores)
none

## Files
autopilot/PRED_LEADERBOARD.md (side-by-side locked vs unlocked), l2vast/pred/SCHEMA.md, l2vast/pred/labels_unlocked/, l2vast/pred/rows/*.json, l2vast/pred/prereg/
