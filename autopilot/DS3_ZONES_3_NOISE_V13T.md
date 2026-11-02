# DS3_ZONES_3_NOISE_V13T - phase-averaged noise band on V13T_LIVE (PARTIAL)

Shadow only. No PASS claims. Z3 (T-ZONES-3 s3). Cap 2026-10-31.

Base: V13T_LIVE = V13Z with lines empty, lock none (per-book locks only), lockfix legs, xcost 0.80, stopcost 2.45, tshort 0. Shipped layer = 8-line set (HALF at D20 on 7 non-OTE lines, OTE-62 B73 D30).
Status: PARTIAL. 3 shards still running (about 45 of 100 draws complete for all 11 phases; flip2 n=46, flip5 n=45). Final numbers will be appended as a new file when the run completes (no overwrite).

## Method
- Perturbation: random flip of p% (2% or 5%) of live rows to half lots (information-free). Each draw is run as a real engine composite at 9 week-key shifts (-4..+4 of the lock/week-floor reset) at xcost 0.80, paired with the base at the same phase; cut = (maxDD_base - maxDD_flip)/maxDD_base.
- Band = 95th percentile of |cut|. "single" = phase 0 only; "PA9" = mean of the 9 shifts per draw; "PA11" = also averages the cost phases (xcost 0.58 and 1.02 at shift 0).
- Rule for a lead to count: PA cut > band in L6M AND (PRE or X'), same sign (plus no-harm, volume-matched placebo, equal-risk, carrying-episode drop).

## Band (95th pct of |maxDD cut|, fraction of base maxDD)
| flip | window | n | single (phase 0) | PA9 (headline) | PA11 |
|---|---|---|---|---|---|
| 2% | L3M | 46 | 0.080 | 0.194 | 0.165 |
| 2% | L6M | 46 | 0.174 | 0.179 | 0.174 |
| 2% | HOLD | 46 | 0.159 | 0.168 | 0.158 |
| 2% | MID | 46 | 0.182 | 0.192 | 0.175 |
| 2% | PRE | 46 | 0.062 | 0.079 | 0.068 |
| 2% | X' | 46 | 0.187 | 0.135 | 0.118 |
| 5% | L3M | 45 | 0.193 | 0.162 | 0.162 |
| 5% | L6M | 45 | 0.335 | 0.257 | 0.271 |
| 5% | HOLD | 45 | 0.261 | 0.202 | 0.215 |
| 5% | MID | 45 | 0.544 | 0.315 | 0.312 |
| 5% | PRE | 45 | 0.089 | 0.100 | 0.098 |
| 5% | X' | 45 | 0.317 | 0.191 | 0.181 |

Headline use: PA9 column. Phase-averaging shrinks the band for 5% flips (MID 0.54 -> 0.32, X' 0.32 -> 0.19, L6M 0.34 -> 0.26) but not for 2% flips in L6M/HOLD/MID (about 0.17-0.19 either way): that noise is draw-specific (which rows get halved), not lock-phase.

## Base (shipped layer, no flips) maxDD by phase, $k
| window | mean over 9 shifts | SD over shifts | xcost 0.58 | xcost 1.02 |
|---|---|---|---|---|
| L6M | 172 | 14 | 134 | 166 |
| PRE | 168 | 6 | 164 | 169 |
| X' | 89 | 5 | 90 | 95 |

The base itself moves about +-8% across week shifts in L6M, so any single-path L6M cut below about 0.17-0.26 is within noise.

## Caveats
- Partial: n about 45 per cell; the 95th percentile at n=45 is a rough estimate (about 2 draws above it). Treat as +-0.03.
- xcost 0.58/1.02 are one shift (0) only.
- Source: out/zones3/s3_v13tl/phase_tl_noise_{0,1,2}.pkl, table at out/zones3/s3_v13tl/tl_band.csv, code l2vast/ds3/code/zones3_s3/tl_band.py.
