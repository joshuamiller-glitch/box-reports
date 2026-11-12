# DS3_GAPS_G3 — PRESS THE TREND DAY (GAPS item G3) — W-G3

Generated 2026-11-12 19:46Z. Shadow only, no PASS claim. Prereg autopilot/GAPS_G3_PREREG.md (sha line in DECISIONS.md). Hook code/th_g3/g3_hooks.py (outermost layer; rules in the prereg). Exact engine, one set per job, TP engine, tag GAPS. Each cell = base + ONE press rule, reference = its own base on the same months. Bases: **L = JN05W2** (43/43 months), **N = JN05W2_NOCUT** (6/43), J = JN05W2J (43/43), NJ = JN05W2J_NOCUT (5/43). Months done per G3 set: 20 sets, 18 month-runs.

**Caveat on every row:** the engine state cut fires in the engine but did NOT fire live on 11-11 (autopilot/DS3_P7_CUT_FIDELITY.md); the N / NJ rows (state cut off) are the live-realistic world. Cells judged first on the trend-week clause (best 5 AND best 20 weeks) and drawdown.

## Identity gate

G3_ID99_L (press trigger never true) on 202610 must equal JN05W2 (598 trades, net 25,943.82): DONE - see check below

Result: 598 trades net 25943.82 vs JN05W2 598 trades net 25943.82 -> **IDENTICAL**

## 0. Trend-week clause

No exact cell has a complete window yet (a window is scored when all its months exist for the cell AND its base).


## 3. acceptance_p7 and behavioural scorecard (cells with >= 6 months; partial sets count only covered sessions)


## 4. Descriptive first-order screen on JN05W2's own L6M trades (history UNMODIFIED; 4,169 trades, 26 weeks; only a prior, exact is the verdict)

For each trigger: entries taken while the press is on, same-side as the press vs counter-trend, their net P&L (JN05W2 as run), and the rough change a rule would make (x1.5 size on same-side = +0.5 x same-side net; skip counter-trend = - counter-trend net).

| trig   |   n_all |   n_same |   n_ct |   same_net |   same_mean |   same_win |   ct_net |   ct_mean |   ct_win |   est_x15 |   est_skipct |   n_weeks |
|:-------|--------:|---------:|-------:|-----------:|------------:|-----------:|---------:|----------:|---------:|----------:|-------------:|----------:|
| S2     |    4169 |     1403 |    687 |   38494.3  |       27.44 |       0.4  | 35755.6  |     52.05 |     0.42 |  19247.1  |    -35755.6  |        26 |
| S3     |    4169 |     1315 |    625 |   45548.9  |       34.64 |       0.4  | 38353.9  |     61.37 |     0.42 |  22774.4  |    -38353.9  |        26 |
| S5     |    4169 |     1125 |    535 |   21786.3  |       19.37 |       0.4  | 46072.8  |     86.12 |     0.43 |  10893.2  |    -46072.8  |        26 |
| R2     |    4169 |      951 |    100 |    4820.08 |        5.07 |       0.41 |  4591.78 |     45.92 |     0.47 |   2410.04 |     -4591.78 |        26 |
| R3     |    4169 |      609 |     64 |   20247.9  |       33.25 |       0.42 |  4675.28 |     73.05 |     0.44 |  10124    |     -4675.28 |        26 |

Reading: counter-trend entries during the press are net winners (mean $45-86 vs same-side $5-35), so "skip counter-trend" is negative on its face; sizing same-side entries is the only positive prior and is modest (about +$0.4-0.9k/wk at x1.5 over 26 weeks).

## 5. R at the cell's lots vs fixed dollars (transfer to the user's lots)

Triggers use R fixed = $1,200 (60 pts x $20 x 1 lot). At the user's lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75) the same 2R/3R/5R lines correspond to 1.75x the dollars if R is lot-scaled; the run triggers (R2/R3: 2 or 3 consecutive same-side Target winners), the 90/75/120-point targets, the give-back keep fractions and the size multiples transfer unchanged. The +5R day-profit cap and the 2R give-back arm are per book in R of that book's base lots, so they scale with lots automatically.

## 6. Live weeks replay

Frozen week (11-02..05) and 11-09..11: the 202611 month (hist day files, state arrays, TP cache) was built by W-T at 13:52Z; the survivors replay uses sets named FW_*. G3 replay of the frozen week for promoted cells is queued behind the L6M/HOLD rows (not run yet). 11-12 raw data exists only to ~08:00Z (Databento licence lag).

## 7. v1.9-style spec

Written only for cells that survive (none yet).
