# DS3_L2_UF_ENTRY_C2 - L2-UNTIL-FOUND cycle 2, ENTRY: pre-signal book lean + ES book as a modifier of the split, and a walk-forward hazard add gate (agent UF-ENTRY, 2026-10-30)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C2_prereg.md sha256 e9363de254220c91d7d7e2f7268c9a583380d0d83f353159c80b7f313c89ba4c (DECISIONS.md, before any cell statistic); 424 cells (400 modifier + 24 hazard), spec sha256 884fc44d3a51d98fbf2296351a7a3958dc330f4b69f3cbc187dd6736b172d52c; PRE+X' selection out/uf/entry_c2/pre_sel.json (copy autopilot/UF_ENTRY_C2_PRESEL.json) sha256 55ff22d5e46b53d84a8d6e0c52560dc72fc7992017650d42fe0de9405e068cc7 logged before the one recent look. Masks as cycle 1 (2026 ~5 weeks: a sign only). dead_lookup: 0 EXACT/NEAR hits for the 424 specs; 40 cells whose rule is a signal-second NQ imb5 or ES imb5 skip/size (near L2EA ideas on the market-entry base) are scored but excluded from selection and the RC (384 count).
Units as cycle 1: Delta $/wk, exact lock engine ST HM WT KB SM PE at EQUAL RISK (EQR frame A, c* on WF = PRE u HOLD, last column), MDE80 in parentheses; N basis primary, L = LIVE-CAL (N + stop exits 2.45 pt), M beside; +pt/fill = extra cost per remainder lot-fill, charged to the cell AND to the base it is compared with. Two bases: S = the 70/30 split, C = the cycle-1 cost-robust mix (F .9 / dip 8 / no gate). Every cell is reported vs the split, vs its own base, and vs market.
Data note: the 1-s tables carry order add / cancel / refill aggregates per side and level bucket (the only MBO-derived information on disk; raw MBO is not on disk, so order lifetimes and queue position are NOT run). Hazard build diagnostic: the out-of-sample correlation of the hazard prediction with the add's realised pts was printed per refit quarter during the build (range -0.05..+0.07 including the recent quarters); it was not used to select anything.

## 0. Plain verdict
* **Nothing in the family beats either base.** Of 384 scored cells, share >= 0 vs the split at +0 pt on N: base S cells L6M 23%, HOLD 22%, PRE 24%; base C cells 43% / 15% / 45%. Vs the cell's own base: S 23/22/24%, C 30/24/31%. The average modifier LOSES: vs own base L6M skip -8.0k (S -7.9k), half -3.2k, up-when-with -6.2k..-7.5k, F-0.2 +0.3k..+1.0k, F+0.2 -0.4k..-1.7k, hazard gate -13k..-17k (all four thresholds, all three feature sets, both bases). White RC over the 384 cells (centred weekly deltas, 2000 draws): vs split N L6M max t 3.16, p 0.798, cum-adj p 1.000 (best UF2|S|agree_nqnow_esdlt30|q0.1|Fp); HOLD max t 2.53, p 0.891, cum-adj p 1.000 (best UF2|S|agree_nqnow_esdlt30|q0.1|Fp); PRE max t 3.26, p 0.580, cum-adj p 1.000 (best UF2|S|nq_can_own_now|q0.1|Fp); vs own base N L6M max t 3.16, p 0.920, cum-adj p 1.000 (best UF2|S|agree_nqnow_esdlt30|q0.1|Fp). N_cum = 146,028 = 145,644 stored (UF_TRIALS, incl. cycle-1 entry/loss) + 384: cumulative-adjusted p = 1.0 everywhere vs a base.
* **PRE-selected cell `UF2|C|esnq_div|q0.2|Fp`**: on the cost-robust base C, when the ES-minus-NQ imbalance divergence at the signal is in the worst 20% (ES book leans against the trade relative to NQ; q20 from SEL only, fires on ~18% of trades) buy 100% at market, no dip add (F .9 -> 1.0). Positive in all five windows vs its own base on N at all three cost levels, but small and inside MDE: vs C (N, +0 pt) 2026 +0.5k, L6M +2.7k (4.8k), HOLD +1.7k, PRE +2.2k, X' +2.2k; vs the split (N): 2026 +11.4k, L6M +4.4k (14.7k), HOLD +0.9k, PRE +3.5k, X' +9.2k (most of it is the base C itself); vs market (N): L6M +27.3k (16.0k), HOLD +23.5k, PRE +11.5k, X' +13.1k; at +2 pt vs market +22.8k / +19.4k / +6.7k / +9.5k. LIVE-CAL and M in section 1.
* Tier: **BEST-AVAILABLE-NEGATIVE** as an improvement over the split / over C (CI(PRE) vs own [-0.8k, +5.0k], CI(HOLD) [-1.7k, +5.2k] include 0; placebo ranks vs the split P1 0.90/0.80/0.95/0.90 and P2 1.00/0.90/0.80/1.00 (L6M/HOLD/PRE/X') - HOLD < 0.95; RC p 0.9; cumulative-adjusted 1.0; one rule among 384 with t_own L6M 1.6); **CANDIDATE-RECENT** vs market entry only because C is. Not PASS. The positive sign vs its own base in all windows at 5k MDE is not evidence: 30 of the 384 cells are >= 0 vs their own base in L6M, HOLD, PRE and X' together.
* **Pre-signal lean is not information about the signal's quality.** NQ imbalance/delta/OFI 10-60 s before the signal, cancel-to-add ratio and refill failures at my best, own-depth change, ES imbalance/delta and ES-NQ divergence, thin book: applied as skip, half size, 1.5x when with, or F-shift, none lifts the split or C on average and the PRE-negative/recent-positive pattern of cycle 1 repeats in the individual best cells (looked-data table below). Skipping removes winners (the signal edge is at the market price, skipping 10-20% of signals costs ~8k at equal risk).
* **Hazard add gate: dead.** Walk-forward LightGBM (100 trees, depth 3, quarterly refit, trailing 12 m of closed events) gates the add on predicted marginal pts: every one of 24 cells is -9k..-20k vs its base in L6M/HOLD/PRE (random gate at the same add rate is as good or better: P1 rank 0.10/0.10/0.90 for S NQES th 1.0, 0.15/0.10/0.15 for C NQES th 0). The add's profit is in the tail of deep dips that look unattractive ex ante; the ex-ante book does not rank them.
* Cost-robust base C unchanged as the cycle-1 finding: C vs split N +0 pt: L6M +1.6k HOLD -0.8k PRE +1.2k X' +6.9k; at +1 pt +11.3k/+7.9k/+6.9k/+10.4k; at +2 pt +17.8k/+14.0k/+12.2k/+13.5k.

## 1. SETTINGS TABLE (recent windows first)
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 0 | vs split | +11.4k (29.5k) | +4.4k (14.7k) | +0.9k (13.8k) | +3.5k (10.2k) | +9.2k (10.2k) | 1.048 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 0 | vs own base | +0.5k (3.1k) | +2.7k (4.8k) | +1.7k (4.9k) | +2.2k (4.2k) | +2.2k (4.0k) | 1.020 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 0 | vs market | +32.6k (41.6k) | +27.3k (16.0k) | +23.5k (17.2k) | +11.5k (11.0k) | +13.1k (10.5k) | 1.114 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 1 | vs split | +12.6k (29.1k) | +14.3k (13.9k) | +9.8k (14.0k) | +10.3k (11.3k) | +12.9k (10.2k) | 1.075 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 1 | vs own base | +0.9k (4.8k) | +2.9k (5.2k) | +1.8k (5.2k) | +3.2k (4.5k) | +2.4k (4.0k) | 1.025 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 1 | vs market | +31.2k (39.6k) | +24.8k (16.0k) | +21.2k (16.9k) | +9.8k (10.9k) | +11.0k (9.9k) | 1.106 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 2 | vs split | +18.9k (35.2k) | +21.2k (15.4k) | +16.4k (15.3k) | +15.4k (11.2k) | +16.3k (10.7k) | 1.103 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 2 | vs own base | +2.0k (2.1k) | +3.2k (5.1k) | +2.2k (5.1k) | +3.0k (4.1k) | +2.6k (4.0k) | 1.023 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | N | 2 | vs market | +29.1k (36.8k) | +22.8k (15.3k) | +19.4k (16.1k) | +6.7k (10.4k) | +9.5k (9.8k) | 1.093 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 0 | vs split | +4.2k (46.5k) | +3.2k (13.5k) | +0.2k (12.5k) | +0.7k (9.5k) | +5.8k (8.7k) | 1.011 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 0 | vs own base | -0.5k (7.1k) | +0.1k (5.9k) | -0.8k (6.0k) | +0.6k (4.0k) | +0.5k (2.9k) | 0.994 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 0 | vs market | +20.5k (36.6k) | +22.1k (15.6k) | +19.1k (15.3k) | +7.3k (10.0k) | +9.1k (9.0k) | 1.066 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 1 | vs split | +1.5k (43.8k) | +9.8k (14.3k) | +6.2k (13.6k) | +6.3k (9.9k) | +8.8k (8.8k) | 1.044 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 1 | vs own base | -0.3k (5.3k) | +0.8k (6.0k) | -0.2k (5.9k) | +2.6k (4.0k) | +0.8k (2.8k) | 1.003 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 1 | vs market | +14.5k (31.6k) | +19.4k (15.0k) | +16.6k (14.6k) | +5.4k (9.9k) | +7.2k (8.9k) | 1.058 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 2 | vs split | -2.6k (36.5k) | +14.1k (15.1k) | +10.5k (14.2k) | +11.5k (10.1k) | +12.3k (9.2k) | 1.075 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 2 | vs own base | +2.2k (2.1k) | +3.1k (7.8k) | +1.8k (7.4k) | +2.8k (3.5k) | +1.1k (2.8k) | 1.007 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | L | 2 | vs market | +7.8k (32.7k) | +16.5k (15.1k) | +14.0k (14.5k) | +3.0k (9.9k) | +6.1k (8.9k) | 1.051 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 0 | vs split | -13.4k (28.5k) | +1.9k (13.9k) | +0.3k (14.4k) | +3.3k (9.1k) | +8.0k (9.3k) | 1.064 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 0 | vs own base | +1.7k (4.0k) | +0.4k (4.7k) | +0.9k (4.7k) | +2.2k (3.7k) | +2.2k (4.5k) | 1.019 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 0 | vs market | +6.1k (35.8k) | +15.3k (15.7k) | +12.0k (15.8k) | +11.1k (11.1k) | +10.9k (9.1k) | 1.068 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 1 | vs split | -11.8k (36.0k) | +6.7k (15.4k) | +4.8k (16.6k) | +11.1k (10.1k) | +10.7k (9.5k) | 1.099 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 1 | vs own base | +4.3k (7.1k) | +1.4k (4.9k) | +1.7k (4.9k) | +2.8k (3.7k) | +2.4k (4.5k) | 1.022 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 1 | vs market | +7.1k (34.8k) | +13.8k (15.2k) | +10.5k (15.4k) | +9.6k (10.6k) | +9.6k (9.1k) | 1.064 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 2 | vs split | -7.2k (37.2k) | +11.2k (16.1k) | +8.6k (17.9k) | +19.1k (11.1k) | +14.7k (10.2k) | 1.134 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 2 | vs own base | +2.3k (4.7k) | +2.6k (5.5k) | +2.9k (5.3k) | +2.8k (3.5k) | +2.6k (4.5k) | 1.020 |
| C + F=1.0 when ES-NQ divergence in worst 20% (PRE-selected) | M | 2 | vs market | +5.9k (34.0k) | +12.8k (14.6k) | +9.3k (14.7k) | +8.3k (10.6k) | +8.3k (9.1k) | 1.056 |

### References (same engine; cycle-1 numbers reproduced)
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| split vs market | N | 0 | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | 1.064 |
| C (F.9 X8) vs market | N | 0 | +32.1k (41.5k) | +24.4k (15.1k) | +21.7k (17.0k) | +9.0k (10.6k) | +10.7k (9.5k) | 1.093 |
| C vs split | N | 0 | +10.9k (29.9k) | +1.6k (14.4k) | -0.8k (13.5k) | +1.2k (9.1k) | +6.9k (8.8k) | 1.027 |
| split vs market | N | 1 | +18.2k (39.5k) | +10.1k (15.5k) | +11.1k (14.8k) | -0.8k (11.4k) | -2.2k (8.7k) | 1.029 |
| C (F.9 X8) vs market | N | 1 | +30.2k (39.4k) | +21.7k (14.5k) | +19.2k (16.1k) | +6.4k (10.3k) | +8.5k (9.3k) | 1.079 |
| C vs split | N | 1 | +11.7k (26.2k) | +11.3k (12.0k) | +7.9k (12.5k) | +6.9k (9.7k) | +10.4k (9.3k) | 1.049 |
| split vs market | N | 2 | +10.4k (39.1k) | +1.8k (16.1k) | +3.1k (14.8k) | -8.6k (11.9k) | -6.7k (8.6k) | 0.991 |
| C (F.9 X8) vs market | N | 2 | +27.0k (37.4k) | +19.4k (14.2k) | +17.1k (15.5k) | +3.5k (10.2k) | +6.7k (9.3k) | 1.068 |
| C vs split | N | 2 | +16.7k (35.4k) | +17.8k (14.5k) | +14.0k (14.5k) | +12.2k (10.0k) | +13.5k (9.7k) | 1.078 |
| split vs market | L | 0 | +16.0k (44.4k) | +18.7k (15.9k) | +18.9k (15.5k) | +6.5k (11.9k) | +3.0k (8.8k) | 1.054 |
| C (F.9 X8) vs market | L | 0 | +21.0k (40.8k) | +22.0k (15.2k) | +20.0k (15.8k) | +6.7k (10.5k) | +8.5k (9.3k) | 1.072 |
| C vs split | L | 0 | +4.7k (47.6k) | +3.1k (13.1k) | +1.1k (12.1k) | +0.2k (8.8k) | +5.3k (8.6k) | 1.017 |
| split vs market | L | 1 | +13.0k (39.9k) | +9.4k (15.5k) | +10.4k (14.6k) | -1.0k (11.4k) | -1.7k (8.6k) | 1.014 |
| C (F.9 X8) vs market | L | 1 | +14.8k (31.7k) | +18.5k (14.1k) | +16.8k (14.4k) | +2.7k (10.3k) | +6.4k (9.1k) | 1.055 |
| C vs split | L | 1 | +1.8k (42.2k) | +8.9k (13.3k) | +6.4k (12.8k) | +3.6k (9.4k) | +7.9k (8.8k) | 1.041 |
| split vs market | L | 2 | +10.3k (36.4k) | +2.7k (16.1k) | +3.7k (14.6k) | -8.3k (11.2k) | -5.9k (8.7k) | 0.978 |
| C (F.9 X8) vs market | L | 2 | +5.6k (32.0k) | +13.2k (14.6k) | +12.1k (14.5k) | +0.1k (10.2k) | +4.9k (9.1k) | 1.044 |
| C vs split | L | 2 | -4.9k (34.8k) | +10.8k (13.0k) | +8.6k (12.3k) | +8.5k (9.8k) | +11.0k (9.2k) | 1.068 |
| split vs market | M | 0 | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | 1.003 |
| C (F.9 X8) vs market | M | 0 | +4.3k (35.4k) | +14.9k (17.0k) | +11.1k (16.4k) | +8.8k (11.6k) | +8.5k (9.4k) | 1.048 |
| C vs split | M | 0 | -15.2k (25.7k) | +1.5k (15.2k) | -0.6k (14.6k) | +1.0k (9.6k) | +5.7k (8.8k) | 1.045 |
| split vs market | M | 1 | +18.5k (44.1k) | +7.3k (14.5k) | +5.9k (14.2k) | -1.2k (11.5k) | -0.7k (8.5k) | 0.968 |
| C (F.9 X8) vs market | M | 1 | +2.7k (34.7k) | +12.4k (16.6k) | +8.7k (16.0k) | +6.7k (11.1k) | +7.1k (9.4k) | 1.042 |
| C vs split | M | 1 | -16.4k (34.0k) | +5.3k (17.1k) | +2.9k (16.8k) | +8.1k (10.1k) | +8.1k (8.9k) | 1.076 |
| split vs market | M | 2 | +12.6k (42.7k) | +2.4k (13.7k) | +1.3k (14.1k) | -9.5k (11.7k) | -5.5k (9.2k) | 0.931 |
| C (F.9 X8) vs market | M | 2 | +3.6k (34.6k) | +10.1k (16.4k) | +6.3k (15.7k) | +5.3k (10.9k) | +5.6k (9.4k) | 1.035 |
| C vs split | M | 2 | -9.7k (32.2k) | +8.3k (17.5k) | +5.4k (17.7k) | +15.9k (11.1k) | +11.9k (9.9k) | 1.112 |

### Best S-based cell by SEL t (PRE-selected on base S) `UF2|S|nq_canratio_own_pre|q0.1|half` and the best hazard cells
| row | basis | +pt/fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 0 | vs split | -0.5k (12.7k) | -0.8k (5.5k) | -1.3k (5.5k) | +2.6k (6.5k) | +2.9k (7.0k) | 1.042 |
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 0 | vs market | +20.0k (49.0k) | +21.7k (18.2k) | +21.2k (18.8k) | +10.5k (13.4k) | +6.4k (11.7k) | 1.109 |
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 1 | vs split | -2.8k (9.5k) | -1.7k (5.2k) | -2.1k (5.3k) | +2.4k (6.5k) | +2.5k (6.9k) | 1.043 |
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 1 | vs market | +15.3k (44.0k) | +8.3k (16.5k) | +9.0k (16.7k) | +1.6k (13.3k) | +0.4k (11.3k) | 1.073 |
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 2 | vs split | -3.0k (10.4k) | -1.8k (5.5k) | -2.2k (5.6k) | +1.8k (6.7k) | +2.3k (6.8k) | 1.047 |
| S best (half size when own-side cancel/add ratio in worst 10%) | N | 2 | vs market | +7.3k (43.3k) | +0.1k (16.5k) | +1.0k (16.0k) | -6.8k (13.8k) | -4.4k (11.0k) | 1.037 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 0 | vs split | -3.3k (9.6k) | -2.1k (5.3k) | -2.4k (5.3k) | +2.0k (6.7k) | +2.4k (6.9k) | 1.042 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 0 | vs market | +12.5k (49.9k) | +16.5k (17.5k) | +16.3k (18.1k) | +8.6k (14.0k) | +5.5k (11.9k) | 1.099 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 1 | vs split | -3.4k (9.9k) | -2.1k (5.1k) | -2.5k (5.1k) | +1.0k (6.7k) | +2.1k (6.9k) | 1.043 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 1 | vs market | +9.5k (44.5k) | +7.3k (16.6k) | +7.8k (16.5k) | -0.0k (13.6k) | +0.5k (11.4k) | 1.057 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 2 | vs split | -4.5k (10.4k) | -2.4k (5.3k) | -2.8k (5.4k) | +0.9k (6.7k) | +1.7k (7.1k) | 1.046 |
| S best (half size when own-side cancel/add ratio in worst 10%) | L | 2 | vs market | +5.9k (38.7k) | +0.3k (16.4k) | +1.0k (15.7k) | -7.4k (12.9k) | -4.2k (11.2k) | 1.023 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 0 | vs split | -4.8k (9.8k) | -2.8k (5.5k) | -3.2k (5.4k) | +1.8k (6.8k) | +1.4k (7.2k) | 1.046 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 0 | vs market | +14.8k (42.1k) | +10.6k (16.9k) | +8.4k (16.2k) | +9.6k (12.6k) | +4.3k (11.1k) | 1.050 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 1 | vs split | -7.7k (12.1k) | -3.6k (5.8k) | -4.0k (5.7k) | +2.0k (7.0k) | +1.4k (7.1k) | 1.047 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 1 | vs market | +11.1k (39.2k) | +3.8k (15.5k) | +2.0k (15.0k) | +0.8k (12.8k) | +0.6k (10.7k) | 1.014 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 2 | vs split | -5.6k (10.1k) | -3.3k (5.6k) | -3.7k (5.6k) | +2.6k (7.2k) | +1.4k (6.9k) | 1.049 |
| S best (half size when own-side cancel/add ratio in worst 10%) | M | 2 | vs market | +7.3k (39.0k) | -0.7k (14.2k) | -2.2k (14.2k) | -7.1k (12.6k) | -4.1k (11.1k) | 0.977 |

### L6M-ranked best cells vs the split, N, +0 pt (SELECTED ON LOOKED DATA)
| cid | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 110 | UF2|S|es_imb_pre|q0.2|skip | +37.3k (90.6k) | +33.9k (47.7k) | +26.8k (42.8k) | -0.2k (24.9k) | +6.5k (22.3k) |
| 310 | UF2|C|es_imb_pre|q0.2|skip | +50.4k (93.5k) | +33.3k (47.5k) | +25.7k (42.5k) | +0.8k (26.9k) | +13.3k (25.2k) |
| 115 | UF2|S|es_imb_pre|q0.1|skip | +28.4k (54.7k) | +22.9k (36.6k) | +18.4k (32.7k) | +7.2k (17.5k) | +3.8k (19.4k) |
| 311 | UF2|C|es_imb_pre|q0.2|half | +27.8k (94.9k) | +22.6k (33.8k) | +15.6k (30.9k) | +2.8k (18.2k) | +11.5k (16.3k) |
| 315 | UF2|C|es_imb_pre|q0.1|skip | +33.4k (64.9k) | +22.5k (39.9k) | +15.7k (35.9k) | +7.9k (21.1k) | +9.8k (22.9k) |
| 60 | UF2|S|nq_canratio_own_pre|q0.2|skip | +2.2k (28.0k) | +19.6k (17.7k) | +17.5k (20.0k) | +2.2k (19.0k) | -1.1k (16.6k) |
| 260 | UF2|C|nq_canratio_own_pre|q0.2|skip | +10.2k (58.7k) | +15.9k (25.4k) | +12.2k (26.4k) | +2.0k (20.7k) | +2.9k (19.5k) |
| 111 | UF2|S|es_imb_pre|q0.2|half | +22.0k (79.4k) | +15.8k (32.3k) | +12.3k (28.8k) | -2.4k (15.2k) | +2.7k (13.6k) |

### Top 10 by SEL t (PRE-only ranking) vs the split, N, +0 pt
| cid | cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 354 | UF2|C|esnq_div|q0.2|Fp | +11.4k (29.5k) | +4.4k (14.7k) | +0.9k (13.8k) | +3.5k (10.2k) | +9.2k (10.2k) |
| 372 | UF2|C|agree_nqnow_esdlt30|q0.2|up | +15.9k (40.9k) | +2.4k (14.7k) | -0.8k (14.9k) | +2.4k (10.2k) | +8.9k (10.4k) |
| 299 | UF2|C|nq_own_chg|q0.1|Fp | +10.9k (31.5k) | +0.8k (15.3k) | -2.0k (14.0k) | +1.8k (9.3k) | +9.3k (8.7k) |
| 298 | UF2|C|nq_own_chg|q0.1|Fm | +12.3k (37.7k) | +4.0k (14.3k) | -0.3k (13.7k) | +2.7k (8.9k) | +7.7k (9.1k) |
| 246 | UF2|C|nq_dlt_pre|q0.1|half | +11.6k (45.9k) | +3.8k (16.3k) | -0.1k (16.3k) | +6.3k (12.7k) | +7.3k (12.6k) |
| 367 | UF2|C|agree_nqpre_esnow|q0.1|up | +4.5k (32.2k) | +2.0k (13.7k) | -0.0k (13.6k) | +2.4k (10.5k) | +10.3k (9.0k) |
| 259 | UF2|C|nq_ofi30|q0.1|Fp | +11.4k (29.5k) | +1.8k (14.4k) | -1.2k (13.5k) | +2.4k (9.1k) | +7.4k (8.6k) |
| 224 | UF2|C|nq_imb_chg|q0.2|Fp | -0.4k (52.0k) | +1.8k (17.8k) | -2.3k (16.7k) | +2.0k (9.5k) | +7.7k (8.1k) |
| 377 | UF2|C|agree_nqnow_esdlt30|q0.1|up | +10.7k (30.3k) | -0.1k (14.0k) | -2.6k (13.3k) | +2.0k (9.1k) | +7.8k (8.9k) |
| 359 | UF2|C|esnq_div|q0.1|Fp | +12.6k (34.3k) | +4.9k (15.2k) | +1.0k (14.3k) | +3.3k (10.1k) | +7.2k (8.9k) |


## 2. Family map (means over the family's cells, N, equal risk)
vs the split, base S cells:
| family | n | 2026 | L6M | HOLD | PRE | X' | share>=0 L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|
| H_haz | 12 | +7.2k | -14.0k | -13.8k | -13.5k | -6.0k | 0.00/0.00/0.00 |
| M_agree | 30 | -1.6k | -3.2k | -3.4k | -1.2k | +0.0k | 0.20/0.20/0.23 |
| M_es | 40 | +1.3k | -2.6k | -2.8k | -3.9k | -1.1k | 0.28/0.28/0.23 |
| M_esnq | 10 | +9.7k | -7.0k | -7.2k | +0.7k | -3.2k | 0.20/0.10/0.40 |
| M_nq | 100 | +2.6k | -4.5k | -4.3k | -2.7k | +0.5k | 0.26/0.24/0.26 |

vs the split, base C cells:
| family | n | 2026 | L6M | HOLD | PRE | X' | share>=0 L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|
| H_haz | 12 | +19.0k | -14.0k | -17.3k | -16.0k | +1.2k | 0.00/0.00/0.00 |
| M_agree | 30 | +8.5k | -0.9k | -3.7k | +0.2k | +7.1k | 0.50/0.10/0.70 |
| M_es | 40 | +9.9k | -0.1k | -2.7k | -2.6k | +6.0k | 0.45/0.20/0.38 |
| M_esnq | 10 | +17.4k | -1.5k | -4.2k | +2.4k | +4.4k | 0.60/0.40/0.80 |
| M_nq | 100 | +10.3k | -2.8k | -5.1k | -1.9k | +7.1k | 0.44/0.14/0.43 |

vs the split at +1 pt per remainder fill, base C cells:
| family | n | 2026 | L6M | HOLD | PRE | X' | share>=0 L6M/HOLD/PRE |
|--|--|--|--|--|--|--|--|
| H_haz | 12 | +21.5k | -2.8k | -7.2k | -8.5k | +5.7k | 0.17/0.00/0.00 |
| M_agree | 30 | +8.9k | +8.6k | +4.8k | +6.0k | +10.5k | 0.97/0.83/1.00 |
| M_es | 40 | +10.3k | +9.3k | +5.8k | +3.0k | +9.5k | 0.90/0.75/0.75 |
| M_esnq | 10 | +18.1k | +8.2k | +4.5k | +8.2k | +7.7k | 0.80/0.70/1.00 |
| M_nq | 100 | +10.5k | +6.5k | +3.4k | +3.9k | +10.6k | 0.80/0.74/0.81 |

vs own base, action means, base S:
| action / hazard th | n | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| Fm | 36 | +2.1k | +0.3k | +0.1k | -0.6k | -0.2k |
| Fp | 36 | +0.4k | -1.7k | -1.7k | -0.2k | -0.1k |
| half | 36 | +4.6k | -3.2k | -3.5k | -2.9k | -0.3k |
| skip | 36 | +6.2k | -7.9k | -7.6k | -5.6k | -0.4k |
| th=0.0 | 3 | -2.1k | -15.4k | -13.6k | -12.5k | -5.7k |
| th=0.5 | 3 | +3.1k | -13.6k | -13.3k | -11.4k | -6.4k |
| th=1.0 | 3 | +15.7k | -11.2k | -12.3k | -10.3k | -5.6k |
| th=2.0 | 3 | +11.9k | -15.6k | -15.9k | -19.8k | -6.3k |
| up | 36 | -3.5k | -7.5k | -7.2k | -3.3k | +0.4k |

vs own base, action means, base C:
| action / hazard th | n | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| Fm | 36 | +4.3k | +1.0k | +0.7k | -1.0k | -0.1k |
| Fp | 36 | -1.3k | -0.4k | -0.9k | +0.3k | +0.4k |
| half | 36 | -0.6k | -3.2k | -3.4k | -3.1k | -1.0k |
| skip | 36 | -1.2k | -8.0k | -7.3k | -6.4k | -1.7k |
| th=0.0 | 3 | +10.6k | -14.1k | -16.1k | -14.6k | -5.1k |
| th=0.5 | 3 | +1.5k | -17.3k | -18.1k | -16.8k | -5.6k |
| th=1.0 | 3 | +4.9k | -16.4k | -17.0k | -18.0k | -5.9k |
| th=2.0 | 3 | +14.6k | -13.0k | -12.7k | -17.4k | -5.6k |
| up | 36 | -4.0k | -6.2k | -5.7k | -2.8k | +1.5k |


## 3. Gates, placebo, RC, tails for the selected cell
* Placebo vs the split base (delta vs the real split at equal risk; rank = share of draws the real cell beats):
| cell | placebo (20 draws) | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|
| UF2|S|nq_canratio_own_pre|q0.1|half | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.50 | 0.45 | 0.90 | 0.85 | 0.40 |
| UF2|S|nq_canratio_own_pre|q0.1|half | P2 lean features shuffled between trades of the same day: rank | 0.15 | 0.15 | 0.85 | 0.85 | 0.55 |
| UF2|C|nq_own_chg|q0.1|Fp | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.25 | 0.20 | 0.80 | 1.00 | 0.60 |
| UF2|C|nq_own_chg|q0.1|Fp | P2 lean features shuffled between trades of the same day: rank | 0.30 | 0.30 | 0.75 | 0.95 | 0.45 |
| UF2|C|esnq_div|q0.2|Fp | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.90 | 0.80 | 0.95 | 0.90 | 0.65 |
| UF2|C|esnq_div|q0.2|Fp | P2 lean features shuffled between trades of the same day: rank | 1.00 | 0.90 | 0.80 | 1.00 | 0.70 |
| UF2|C|agree_nqnow_esdlt30|q0.2|up | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.90 | 0.80 | 0.75 | 0.90 | 0.80 |
| UF2|C|agree_nqnow_esdlt30|q0.2|up | P2 lean features shuffled between trades of the same day: rank | 0.60 | 0.60 | 0.85 | 0.70 | 0.80 |
| UF2|S|HAZ|NQES|th=1.0 | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.10 | 0.10 | 0.90 | 0.00 | 0.30 |
| UF2|C|HAZ|NQES|th=0.0 | P1 same action on a random subset at the same rate (hazard: random gate at the same add rate): rank | 0.15 | 0.10 | 0.15 | 0.75 | 0.00 |

* V2 gates vs the split / vs own base: mean_up (PRE>0) yes/yes; holdout_sign (HOLD>0) yes (+0.9k)/yes (+1.7k); SPAN2 yes/yes; placebo>=0.95: HOLD fails (0.80/0.90); CI(PRE lo>0) vs split [-3.5k, +10.8k] NO, vs own NO, vs market [+3.8k, +18.9k] yes; cost (+1, +2 pt): positive vs own base and vs market; year_share vs split 0.44, vs own 0.43; maxDD(engine HOLD) 702k vs split 625k (fail), vs own base 684k vs 685k (pass); RC fail.
* Neighbours (same base and rule, other tail/action):
  - UF2|C|esnq_div|q0.2|skip: vs split L6M/HOLD/PRE/X' -13.5/-13.1/-2.1/-5.8k; vs own -14.8/-11.9/-3.2/-12.4k
  - UF2|C|esnq_div|q0.2|half: vs split L6M/HOLD/PRE/X' -6.2/-9.5/+1.6/+1.5k; vs own -7.6/-8.4/+0.4/-5.3k
  - UF2|C|esnq_div|q0.2|up: vs split L6M/HOLD/PRE/X' -12.2/-14.3/+8.8/+3.8k; vs own -13.4/-13.1/+7.5/-3.0k
  - UF2|C|esnq_div|q0.2|Fm: vs split L6M/HOLD/PRE/X' +2.4/-0.9/+0.3/+5.5k; vs own +0.8/-0.0/-0.9/-1.4k
  - UF2|C|esnq_div|q0.1|skip: vs split L6M/HOLD/PRE/X' +4.7/+1.8/+6.3/+4.2k; vs own +3.0/+2.5/+4.9/-2.7k
  - UF2|C|esnq_div|q0.1|half: vs split L6M/HOLD/PRE/X' +1.7/-0.5/-3.1/+5.1k; vs own +0.1/+0.4/-4.2/-1.7k
  - UF2|C|esnq_div|q0.1|up: vs split L6M/HOLD/PRE/X' -4.9/-7.6/+4.0/+5.7k; vs own -6.4/-6.5/+2.8/-1.1k
  - UF2|C|esnq_div|q0.1|Fm: vs split L6M/HOLD/PRE/X' +3.3/+0.6/+1.6/+7.3k; vs own +1.7/+1.4/+0.4/+0.4k
  - UF2|C|esnq_div|q0.1|Fp: vs split L6M/HOLD/PRE/X' +4.9/+1.0/+3.3/+7.2k; vs own +3.2/+1.8/+2.0/+0.3k
* RC detail: vs split N: L6M max t 3.16, p 0.798, cum-adj p 1.000 (best UF2|S|agree_nqnow_esdlt30|q0.1|Fp); HOLD max t 2.53, p 0.891, cum-adj p 1.000 (best UF2|S|agree_nqnow_esdlt30|q0.1|Fp); PRE max t 3.26, p 0.580, cum-adj p 1.000 (best UF2|S|nq_can_own_now|q0.1|Fp); X' max t 3.48, p 0.619, cum-adj p 1.000 (best UF2|C|nq_own_chg|q0.2|Fp). M basis vs split L6M max t 2.35, p 0.917, cum-adj p 1.000 (best UF2|S|es_dlt30|q0.2|Fm). LIVE-CAL vs split L6M max t 2.51, p 0.904, cum-adj p 1.000 (best UF2|S|nq_canratio_own_pre|q0.2|skip). Vs market (the base's claim): N L6M max t 5.37, p 0.004, cum-adj p 0.782 (best UF2|S|nq_canratio_own_pre|q0.2|skip); N HOLD max t 4.32, p 0.032, cum-adj p 1.000 (best UF2|C|es_imb_pre|q0.1|Fm). Single test of the selected cell vs its own base N L6M: t 1.59, HOLD t 0.95; vs split L6M t 0.84.
* Tail HOLD (sd / worst-20 sum at c*): selected 183k / -0.78M vs split 169k / -0.63M.
* D6 session cells, row attribution (N, c=1, $k/wk; no per-cell MDE, all inside the stack MDE), selected cell vs its base C:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | +0.1k | +0.1k | +0.0k | +0.2k | -0.0k |
| PE london | +0.1k | +0.0k | +0.0k | +0.0k | -0.1k |
| HM asia | +0.6k | +0.5k | +0.4k | +0.4k | -0.2k |
| HM nyam | -0.0k | +0.1k | +0.4k | +0.2k | +1.5k |
| SM asia | -0.0k | +0.1k | +0.1k | +0.1k | +0.1k |
| SM london | +0.0k | -0.6k | -0.5k | +0.0k | +0.0k |
| ST asia | +0.7k | +0.6k | +0.6k | -0.1k | +0.2k |
| WT london | -0.0k | -0.2k | -0.1k | +0.3k | -0.1k |

  and vs the split:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | +1.6k | +0.5k | +0.5k | +0.2k | -0.1k |
| PE london | +1.6k | +0.8k | +0.8k | -0.0k | +0.2k |
| HM asia | +3.3k | +1.8k | +1.5k | +0.8k | -1.5k |
| HM nyam | -0.5k | +0.4k | +0.8k | -1.0k | +1.5k |
| SM asia | -0.2k | -0.2k | -0.8k | +0.4k | +0.5k |
| SM london | +0.1k | -0.6k | -0.4k | -0.4k | +0.1k |
| ST asia | +1.6k | +1.2k | +0.2k | +1.5k | +0.8k |
| WT london | -1.1k | -1.5k | -1.2k | -0.2k | +0.7k |


## 3b. Look-ahead audit (coordinator warning on day-level features, vol_tag_entry_day)
Cycle-2 cells use ONLY features computed from the NQ/ES 1-s tables over windows ending at the signal second T0 (or at the first dip second for the hazard model), the thin/thick rel_tot8 at the entry sample, and SEL-window quantiles as thresholds. No day-level feature (vol_tag, day range, first-hour, overnight range, gap) is used: no cycle-2 cell is void. Hazard refits use only events closed before each refit date. Cycle 1 (DS3_L2_UF_ENTRY_C1.md) used EINT1 feature columns (sig_st1_age, htf_vwap_atr, htf_gap_eth, sig_hma_sp) in the G11 regime-sizer cells only; availability of htf_vwap_atr / htf_gap_eth at the signal second (as-of the last closed bar vs same-day information) was NOT re-verified here. G11 cells were ~0 and none was the selected cell, so no cycle-1 verdict depends on them; treat G11 as unverified.
## 4. What was learned
1. The book before the signal does not rank signals. Every NQ / ES / cancel-refill lean variable, in every action, is at best a coin flip around its base; skip and size changes cost 3-8k at equal risk because they discard signal edge faster than they remove losers. This is consistent with L2EA (signal-second book skips at market entry) and EINT1.
2. The MBO-derived columns on disk (add/cancel size at my best, refill failures) carry no usable lean: cancel-to-add ratio at the extreme tail (q10) halves L6M/HOLD slightly negative vs the split (-0.8k/-1.3k) and positive in PRE/X' (+2.6k/+2.9k): a PRE-recent sign flip, the cycle-1 pattern again.
3. ES-NQ divergence as a veto of the dip add (go all market) is the only cell with the same sign in every window vs its base (+0.5 to +2.7k, MDE 5k), which is what a rule with a real but small effect or 1 of 384 chance cells would look like; the neighbour (q10) is +3.1k/+1.8k/+2.0k/+0.3k vs C. Worth a forward look, not a rule.
4. Hazard / learned add gate: dead again (L2SE F7, ADDUW gates, now this): the dip add is a convex payoff that should be taken unconditionally.
5. Floor unchanged: the 70/30 split (and its cost-robust C form) remains the ENTRY best; nothing in two cycles improves it beyond MDE.
## 5. Caveats
2026 is ~5 weeks. c* is calibrated on WF (EQR standard), SEL-only for selection. Skip and size modifiers hold lock R at nominal lots (size multiplier scales P&L), as EINT1 did; equal-risk scaling then re-levers the stack. The F-shift cells re-run the kernel with a per-trade F. The hazard gate decides once at the first dip second. Placebo draws 20. The 40 near-L2EA cells and the 11 cycle-1 repeats are controls.
## 6. Files
code l2vast/ds3/code/uf/ufe2_feat.py (stores/features), ufe2_sig.py, ufe2_cells.py, ufe2_haz.py (hazard), ufe2_run.py (stage 0), ufe2_stageA.py, ufe2_stageB.py, ufe2_plac.py, ufe2_gates.py (RC, gates, sessions), ufe2_report.py; outputs l2vast/ds3/out/uf/entry_c2/ ; cells l2vast/ds3/prereg/UF_ENTRY_C2_cells.csv.
