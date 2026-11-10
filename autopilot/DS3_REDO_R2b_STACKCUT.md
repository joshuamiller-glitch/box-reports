# DS3_REDO_R2b_STACKCUT - StackCut variants, exact engine (ROLLFIX1), 2026-11-10 04:50Z

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. EXACT engine rows (patched ROLLFIX1 S1b engine), reference = patched S1-COMB. STANDING RULE: StackCut stays ON; OFF is a reference row only. Rule 2/2a labels use sz_core.prior_info; the bi-weekly walk-forward cannot be computed because the variants were run only on the L6M and PRE months (WF label suffix UNKNOWN-WF, 15% allowance).**

Live rule (replica sim.stack_on_stop): when a book is STOPPED and its entry session is Asia, every other open position on the same side is cut by 50% (rounded up; one lot = exit all) with exit name StackCut. Variants run: pct 25/75/100, sessions all / Asia+London, trigger = second same-side stop within 30 min / either side / other same-side open lots >= 4.

Identity test (live spec through the new hook vs the patched S1-COMB lists): L6M: 6 of 6 months identical to the patched S1-COMB; PRE: 0 of 0 months identical to the patched S1-COMB.

## Exact rows vs live (maxDD cut; d mean $/wk; (b) equal-mean cut; worst-20 cut; StackCut exits)

| set | variant | L6M maxDD / cut / d mean / (b) / w20 cut / n StackCut | PRE maxDD / cut / d mean / (b) / w20 cut / n StackCut | label |
|--|--|--|--|--|
| CDE_SC_LIVE | live: 50%, Asia-only, first stop, same side | 79907 / +0.0 / +0 / +0.0 / +0.0 / 67 | not run yet | LIVE setting |
| CDE_SC_OFF | OFF (reference row only) | not run yet | not run yet | reference row only (standing rule: layer stays ON) |
| CDE_SC_P25 | pct 25, Asia-only | not run yet | not run yet | incomplete |
| CDE_SC_P75 | pct 75, Asia-only | not run yet | not run yet | incomplete |
| CDE_SC_P100 | pct 100, Asia-only | not run yet | not run yet | incomplete |
| CDE_SC_ALL | 50%, ALL sessions | not run yet | not run yet | incomplete |
| CDE_SC_AL | 50%, Asia+London | not run yet | not run yet | incomplete |
| CDE_SC_SECOND | 50%, Asia, only on the 2nd same-side stop within 30 min | not run yet | not run yet | incomplete |
| CDE_SC_ANYSIDE | 50%, Asia, cut other books on either side | not run yet | not run yet | incomplete |
| CDE_SC_LOTS4 | 50%, Asia, only if other same-side open lots >= 4 | not run yet | not run yet | incomplete |

## Counterfactual: what the StackCut exits would have done held to their bracket (never-cut universe path, no later state cut)

| window | StackCut exits | matched to universe | actual net P&L of those trades | same trades held to bracket (no state cut) | cut minus hold | by entry session (n / cut minus hold) |
|--|--|--|--|--|--|--|
| L6M | 67 | 60 | -56380 | -49970 | -592 | 0 58 / -719; 1 2 / +127 |
| PRE | 141 | 133 | -143243 | -131966 | -3857 | 0 111 / +1795; 1 18 / -4209; 3 4 / -1442 |
| X' | 111 | 109 | -125369 | -130364 | +7267 | 0 88 / +7129; 1 20 / -20; 3 1 / +159 |
| HOLD | 137 | 127 | -125073 | -134641 | +17685 | 0 120 / +17446; 1 6 / +597; 3 1 / -358 |
| ALL | 436 | 412 | -438915 | -438804 | +21618 | 0 360 / +28835; 1 46 / -5575; 3 6 / -1642 |

Reading: the -$439k is the P&L of the trades that ended by StackCut (they were losers: the other leg of a stopped book on the same side); the same trades held to their bracket would have made about the same (-$439k), so the cut itself is worth about +$21.6k over 43 months, all of it in Asia (+$28.8k) and slightly negative in London (-$5.6k) and NY-AM (-$1.6k): the rule is not the source of the loss, it avoided a small part of it; the loss is the stop of the first book.
