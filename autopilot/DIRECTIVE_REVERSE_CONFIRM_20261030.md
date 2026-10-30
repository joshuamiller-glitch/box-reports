# T-SIGNAL-DECAY ADDENDUM — REVERSE CONFIRMATION — user directive pasted 2026-10-30 (verbatim)

T-SIGNAL-DECAY ADDENDUM — REVERSE CONFIRMATION: every entry confirmation, mirrored, as the exit (user, 2026-10-30)

Applies to T-SIGNAL-DECAY and uses the full T-CONFIRM-LAYER catalogue (v2 + COMBOS + BARS + SUB-MINUTE). Same scoring: per contract first, measured fills (market exit at the path +1 tick; live-cal basis beside), recent-first, placebos (random exits at the same rate and time-since-entry; the mirrored confirmation on a shuffled day), lock-engine stack line, session as a column.

The idea
Whatever confirms the entry, its opposite is evidence the trade is wrong. If a 15-s Heikin-Ashi flip in favour is the entry confirmation, a 15-s HA flip against is the exit trigger; a bullish FVG forming at the pullback got you long, a bearish FVG forming against you gets you out; EMA-8/21 cross up in, cross down out; CCI back above −100 in, CCI back below +100 (or below −100) out; absorption on the bid in, absorption on the ask out; price reclaiming VWAP in, losing VWAP out. The exit is the entry rule read backwards.

A. Every catalogue item mirrored (all timeframes 1 s .. weekly where defined; every bar type)
ICT/SMC (opposing FVG / iFVG / OB / breaker formed or touched against; liquidity taken against; BOS / CHoCH against; SMT against; premium/discount flipped), price structure (opposing swing / level broken; opposing candle pattern), profile/VWAP (VWAP / band / POC / VAH-VAL lost against), MA / trend events (cross, reclaim, slope, ribbon, distance — all against), every oscillator's trigger against, bar-type events against (HA flip, renko reversal brick, range-bar close, footprint delta / stacked imbalance / unfinished auction against), book / tape events against, time (killzone ends). Each as: EXIT at market when it prints / EXIT at the bar close / TIGHTEN the stop to the event's level / EXIT HALF; × ONLY UNDER WATER (the user's case: the trade is going against) / ONLY IN PROFIT / ALWAYS; × a minimum age (0 / 1 / 2 / 5 min); vs hold-to-bracket on identical entries, lot-matched.

B. PAIRED cells (entry confirmation X -> exit on mirror(X))
For every entry-confirmation cell that is ≥ 0 or CANDIDATE-RECENT in the confirm-layer stages (and for the market and 70/30 bases with no entry confirmation, using the top-50 singles as exit triggers), the paired cell: enter on X, exit on mirror(X), with the same timeframe / bar type / parameters; and the asymmetric pairs (enter on X, exit on mirror(Y)) for the top-20 X × top-20 Y. The COMBOS version: an AND-set entry mirrored as an OR-set exit (any member reversing) and as an AND-set exit (all members reversing), and k-of-n.

C. Interaction with the live rules
Each mirrored exit scored alone, beside the live path TH rules, beside the L2 health rules the user runs, and inside the T-SIGNAL-DECAY combinations; the saved-loss / forfeited-win split; P(target | mirror fired but held) so the user sees what the reversed signal is actually worth; time from the mirror event to the eventual bracket exit.

D. Report
DS3_REVERSE_CONFIRM.md: per item × timeframe × action × state (under water / in profit / always), per contract first, fire rate, saved vs forfeited, the paired table (X in / mirror(X) out) per book; the plain sentences "exiting a losing KB when the 15-s HA flips against saves X pts per contract on Y% of trades in the last 6 months (MDE Z); of the trades it exits, W% would have reached the target"; "the best in/out pair is …". Anything ≥ 0 per contract L6M and HOLD, placebo-beaten: profit / loss rules in THP_POLICY.txt in D6's vocabulary (feature = the mirrored event, named in DS3_THL2_NEEDS.md with its exact definition).
