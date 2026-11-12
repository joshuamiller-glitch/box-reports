# DS3_SURVIVORS_J - JN05W2 (W-J; 2026-11-12T13:58:09Z; Shadow only, no PASS claims)

JN05W2 = live panel base (installed panel + P7 cut, NO JN04 layers, NO WA_C1) + F3 (WB_X_FR_F3 context cut) + E1 (WG_E1 governor) + C22 (S6 stack count and day P&L <= -2R) + BR3S (breadth_ext15 == 3 skip, P7) + FLAT45K (K7 flat -45). Hook order inner to outer: W-B context cut, W-X flat, W-S stack gate, W-C governor; BR3S through the entry-gate mixin. Reference LPB_BASE (exact, 43 months). JN05W2J = the same five on the JN04RM base (extra). Leave-one-out = one set per layer left out.

## Months done per set

| set | months DONE of 43 |
|--|--|
| JN05W2 | 10 |
| JN05W2_nF3 | 10 |
| JN05W2_nE1 | 9 |
| JN05W2_nC22 | 5 |
| JN05W2_nBR3S | 10 |
| JN05W2_nFLAT | 10 |
| JN05W2J | 9 |

## 1. Identity check (before anything)

JN05W2_ID (the same hook stack with every layer null) is identical trade by trade to LPB_EMPTY and to the stored LPB_BASE in 202610 (769 trades, net 12,236.22).

## 2. Trend-week clause (first): weekly P&L, L6M, vs LPB_BASE

(not built yet)

## 3. Windows (exact; each row vs LPB_BASE; mean columns all-weeks and carry-dropped; only windows with all months present are shown)

| cell | window | mean $/wk all-weeks | LPB_BASE all-weeks | d mean all-weeks | mean (carry week dropped) | mean_ref (carry dropped) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN05W2 | L1M | 606 | 341 | +266 | -7190 | -16180 | 36371 | 51253 | +29.0 | +8990 | n/a |  |
| JN05W2_nF3 | L1M | -1519 | 341 | -1859 | -7314 | -16180 | 42856 | 51253 | +16.4 | +8866 | n/a |  |
| JN05W2_nE1 | L1M | 3254 | 341 | +2913 | 12406 | 17539 | 24205 | 51253 | +52.8 | -5132 | n/a |  |
| JN05W2_nBR3S | L1M | 8071 | 341 | +7730 | 17123 | 17539 | 19086 | 51253 | +62.8 | -416 | n/a |  |
| JN05W2_nFLAT | L1M | 157 | 341 | -183 | -6990 | -16180 | 36147 | 51253 | +29.5 | +9190 | n/a |  |
| JN05W2J | L1M | 2631 | 341 | +2290 | 8186 | 17539 | 17862 | 51253 | +65.1 | -9352 | n/a |  |

## 4. Acceptance

| set | acceptance (W-C acceptance_p7) |
|--|--|

## 5. Behavioural scorecards (W-Q behavior_scorecard.py plain words)

## 6. Live weeks (11-02..05 and 11-06..11)

Exact engine, month 202611 (day files NQ_20261102..11 built by W-T; 11-12 stub not replayed). Reference LPB_BASE = the same engine with the live panel only. The JN04RM base is not replayed here (its inputs end 11-05). Label days; frozen live week A = 11-02..05, week B = 11-06..11 (11-09 label = Sunday-evening open).

| set | week A 11-02..05 net $ | week B 11-06..11 net $ | trades | by book (A+B) |
|--|--|--|--|--|
| LPB_BASE | (not finished) ||||
| JN05W2 | (not finished) ||||
| JN05W2_nF3 | (not finished) ||||
| JN05W2_nE1 | (not finished) ||||
| JN05W2_nC22 | (not finished) ||||
| JN05W2_nBR3S | (not finished) ||||
| JN05W2_nFLAT | (not finished) ||||

## 7. Worst 10 L6M P7 sessions, entry by entry

(not built yet)
