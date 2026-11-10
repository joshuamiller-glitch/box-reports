# DS3_REDO_R2b_STACKCUT - StackCut variants, exact engine (ROLLFIX1), 2026-11-10 08:17Z

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. EXACT engine rows (patched ROLLFIX1 S1b engine), reference = patched S1-COMB. STANDING RULE: StackCut stays ON; OFF is a reference row only. Rule 2/2a labels use sz_core.prior_info; the bi-weekly walk-forward cannot be computed because the variants were run only on the L6M and PRE months (WF label suffix UNKNOWN-WF, 15% allowance).**

Live rule (replica sim.stack_on_stop): when a book is STOPPED and its entry session is Asia, every other open position on the same side is cut by 50% (rounded up; one lot = exit all) with exit name StackCut. Variants run: pct 25/75/100, sessions all / Asia+London, trigger = second same-side stop within 30 min / either side / other same-side open lots >= 4.

Identity test (live spec through the new hook vs the patched S1-COMB lists): L6M: 6 of 6 months identical to the patched S1-COMB; PRE: 17 of 17 months identical to the patched S1-COMB.

## Exact rows vs live (maxDD cut; d mean $/wk; (b) equal-mean cut; worst-20 cut; StackCut exits)

| set | variant | L6M maxDD / cut / d mean / (b) / w20 cut / n StackCut | PRE maxDD / cut / d mean / (b) / w20 cut / n StackCut | label |
|--|--|--|--|--|
| CDE_SC_LIVE | live: 50%, Asia-only, first stop, same side | 79907 / +0.0 / +0 / +0.0 / +0.0 / 67 | 140288 / +0.0 / +0 / +0.0 / +0.0 / 141 | LIVE setting |
| CDE_SC_OFF | OFF (reference row only) | 83537 / -4.5 / -4174 / -22.1 / +9.9 / 0 | 138499 / +1.3 / +192 / +2.6 / -3.9 / 0 | reference row only (standing rule: layer stays ON) |
| CDE_SC_P25 | pct 25, Asia-only | 81588 / -2.1 / -235 / -2.9 / +2.0 / 65 | 141031 / -0.5 / +151 / +0.6 / -1.0 / 137 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) |
| CDE_SC_P75 | pct 75, Asia-only | 82817 / -3.6 / -383 / -5.0 / +1.3 / 123 | 138295 / +1.4 / -200 / -0.0 / +1.7 / 223 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) |
| CDE_SC_P100 | pct 100, Asia-only | 85764 / -7.3 / -7619 / -45.4 / +4.4 / 179 | 138354 / +1.4 / +117 / +2.2 / +0.9 / 329 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) |
| CDE_SC_ALL | 50%, ALL sessions | 90449 / -13.2 / -86 / -13.5 / +5.3 / 151 | 136290 / +2.8 / -1309 / -7.5 / -1.1 / 371 | recent: no / RECENT-ONLY-UNKNOWN-WF (allow 15%, PRE deeper -3%) |
| CDE_SC_AL | 50%, Asia+London | 89829 / -12.4 / -350 / -13.8 / +7.8 / 122 | 136385 / +2.8 / -836 / -3.6 / -0.8 / 247 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -3%) |
| CDE_SC_SECOND | 50%, Asia, only on the 2nd same-side stop within 30 min | 83404 / -4.4 / -4816 / -25.1 / +7.6 / 11 | 142229 / -1.4 / +195 / +0.0 / -3.3 / 26 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) |
| CDE_SC_ANYSIDE | 50%, Asia, cut other books on either side | 76439 / +4.3 / +1055 / +7.7 / -8.3 / 152 | 139276 / +0.7 / +284 / +2.7 / -11.0 / 449 | RECENT-OK / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) |
| CDE_SC_LOTS4 | 50%, Asia, only if other same-side open lots >= 4 | 80100 / -0.2 / -1073 / -4.1 / +2.7 / 28 | 139810 / +0.3 / -151 / -0.8 / -1.1 / 67 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -0%) |

## Counterfactual: what the StackCut exits would have done held to their bracket (never-cut universe path, no later state cut)

| window | StackCut exits | matched to universe | actual net P&L of those trades | same trades held to bracket (no state cut) | cut minus hold | by entry session (n / cut minus hold) |
|--|--|--|--|--|--|--|
| L6M | 67 | 60 | -56380 | -49970 | -592 | 0 58 / -719; 1 2 / +127 |
| PRE | 141 | 133 | -143243 | -131966 | -3857 | 0 111 / +1795; 1 18 / -4209; 3 4 / -1442 |
| X' | 111 | 109 | -125369 | -130364 | +7267 | 0 88 / +7129; 1 20 / -20; 3 1 / +159 |
| HOLD | 137 | 127 | -125073 | -134641 | +17685 | 0 120 / +17446; 1 6 / +597; 3 1 / -358 |
| ALL | 436 | 412 | -438915 | -438804 | +21618 | 0 360 / +28835; 1 46 / -5575; 3 6 / -1642 |

Reading: the -$439k is the P&L of the trades that ended by StackCut (they were losers: the other leg of a stopped book on the same side); the same trades held to their bracket would have made about the same (-$439k), so the cut itself is worth about +$21.6k over 43 months, all of it in Asia (+$28.8k) and slightly negative in London (-$5.6k) and NY-AM (-$1.6k): the rule is not the source of the loss, it avoided a small part of it; the loss is the stop of the first book.
