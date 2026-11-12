# DS3_SURVIVORS_J - JN05W2 (W-J; 2026-11-12T13:27:47Z; Shadow only, no PASS claims)

JN05W2 = live panel base (installed panel + P7 cut, NO JN04 layers, NO WA_C1) + F3 (WB_X_FR_F3 context cut) + E1 (WG_E1 governor) + C22 (S6 stack count and day P&L <= -2R) + BR3S (breadth_ext15 == 3 skip, P7) + FLAT45K (K7 flat -45). Hook order inner to outer: W-B context cut, W-X flat, W-S stack gate, W-C governor; BR3S through the entry-gate mixin. Reference LPB_BASE (exact, 43 months). JN05W2J = the same five on the JN04RM base (extra). Leave-one-out = one set per layer left out.

## Months done per set

| set | months DONE of 43 |
|--|--|
| JN05W2 | 5 |
| JN05W2_nF3 | 4 |
| JN05W2_nE1 | 2 |
| JN05W2_nC22 | 0 |
| JN05W2_nBR3S | 0 |
| JN05W2_nFLAT | 0 |
| JN05W2J | 0 |

## 1. Identity check (before anything)

JN05W2_ID (the same hook stack with every layer null) is identical trade by trade to LPB_EMPTY and to the stored LPB_BASE in 202610 (769 trades, net 12,236.22).

## 2. Trend-week clause (first): weekly P&L, L6M, vs LPB_BASE

(not built yet)

## 3. Windows (exact; each row vs LPB_BASE; mean columns all-weeks and carry-dropped; only windows with all months present are shown)

(none scored yet)

## 4. Acceptance

| set | acceptance (W-C acceptance_p7) |
|--|--|

## 5. Behavioural scorecards (W-Q behavior_scorecard.py plain words)

## 6. Live weeks (11-02..05 and 11-06..11)

Needs the new NQ mbp-10 (batch GLBX-20261112-3MWRETB8E3 into /mnt/l2/l2vast/raw/NQ/ext/) and the hist day-file build; raw NQ mbp-10 for 2026-11-02..11 had not landed at 2026-11-12T13:12:52Z (newest dir GLBX-20261031; batch GLBX-20261112-3MWRETB8E3 submitted, log /mnt/l2/l2vast/buy_nq_l2.log). Live-week replay of JN05W2 and the five leave-one-out sets (FW-style sets, jnr_cfg_nov) runs after W-T builds the hist day files.


## 7. Worst 10 L6M P7 sessions, entry by entry

(not built yet)
