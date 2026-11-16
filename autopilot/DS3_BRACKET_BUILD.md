# DS3_BRACKET_BUILD - the five bracket cells on TL3_EV_JN05W2JL2 (deadline order 2026-11-16, P2 and P3)
**STATUS: A7|asia|40x40: L3M,L6M,HOLD,GAP; U7|asia|40x40: L3M,L6M,HOLD,GAP; K7|nyam|40x40: L3M,L6M,HOLD,GAP; K7|nyam|40x60: L3M,L6M; K7|london|40x60: L3M,L6M. Not a PASS claim. Dollars are BASE lots; x1.75 = live lots; $4.84 = FEES.md round-turn repriced (net - lots x 3.66).**

Reference: TL3_EV_JN05W2JL2 (final, 43 months). Cells: hook d10_hooks fix=[target, stop] on ONE book in ONE session, policy-line equivalent (`pol`): only the stop and target points change, lots x baseStop/newStop rounded half-up min 1 (the DS7.cs default lotmult), cut arms/trails/caps/day-lock R left at the engine values. Placebo (3 seeds) = the same target/stop applied to a pseudo-random subset of ALL signals (every book and session) with the same expected count as the cell's signals (share of all signals); matched random control (3 seeds) = the same bracket applied to a pseudo-random 50% of the cell's own book x session signals (same book x session x month mix, half the count, so read the control against about half of the real effect). Pass rule: DD not worse than the reference AND the real cell beats all six controls on both DD cut and mean delta, per window; W44-removed rows shown for windows that contain 2026-W44 (L3M, L6M). Windows: L3M 2026-08..10, L6M 2026-05..10, HOLD 2025-11..2026-04, GAP 2026-02-07..04-30, PRE 2024-10..2025-06, X' 2023-04..2024-01. Drawdown is the whole-stack max drawdown (daily cumulative) in the window.

## Window L3M

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | maxDD -32772 (ref -22565; -45.2%), worst wk -13709 (ref -13430), d net -2417/wk (live x1.75 -4230; $4.84 -2433), stops 13.70 (10.27) | maxDD -32772 (ref -22508; -45.6%), worst wk -13709 (ref -13430), d net -2868/wk (live x1.75 -5020; $4.84 -2880), stops 12.55 (9.43) | FAILS (DD vs ref -45.2%; beats all 6 controls on DD and mean: no) |
| U7|asia|40x40 | maxDD -19400 (ref -22565; +14.0%), worst wk -6939 (ref -13430), d net +1716/wk (live x1.75 +3004; $4.84 +1682), stops 9.89 (10.27) | maxDD -19400 (ref -22508; +13.8%), worst wk -5235 (ref -13430), d net +1400/wk (live x1.75 +2450; $4.84 +1367), stops 9.05 (9.43) | FAILS (DD vs ref +14.0%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x40 | maxDD -23765 (ref -22565; -5.3%), worst wk -14595 (ref -13430), d net +1524/wk (live x1.75 +2667; $4.84 +1498), stops 13.39 (10.27) | maxDD -22691 (ref -22508; -0.8%), worst wk -14595 (ref -13430), d net +1615/wk (live x1.75 +2826; $4.84 +1589), stops 12.55 (9.43) | FAILS (DD vs ref -5.3%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x60 | maxDD -23765 (ref -22565; -5.3%), worst wk -13831 (ref -13430), d net +1118/wk (live x1.75 +1957; $4.84 +1110), stops 10.27 (10.27) | maxDD -22110 (ref -22508; +1.8%), worst wk -13831 (ref -13430), d net +1209/wk (live x1.75 +2117; $4.84 +1201), stops 9.43 (9.43) | FAILS (DD vs ref -5.3%; beats all 6 controls on DD and mean: no) |
| K7|london|40x60 | maxDD -21970 (ref -22565; +2.6%), worst wk -14936 (ref -13430), d net -1390/wk (live x1.75 -2432; $4.84 -1405), stops 10.04 (10.27) | maxDD -21970 (ref -22508; +2.4%), worst wk -14936 (ref -13430), d net -1799/wk (live x1.75 -3148; $4.84 -1813), stops 9.21 (9.43) | FAILS (DD vs ref +2.6%; beats all 6 controls on DD and mean: no) |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | +7.3% / +2616 | -9.0% / +527 | +0.8% / +955 | -5.1% / -1927 | -10.5% / -1626 | -24.3% / -1235 |
| U7|asia|40x40 | -2.9% / +1327 | -8.1% / +1767 | -3.3% / +1221 | -6.3% / +288 | +11.3% / +457 | +0.2% / +1910 |
| K7|nyam|40x40 | -26.2% / +1620 | -9.0% / -1392 | -3.9% / +341 | -2.3% / +1202 | -5.3% / +1189 | -1.8% / +566 |
| K7|nyam|40x60 | -6.4% / +1802 | -1.5% / -1565 | +0.8% / +98 | -1.8% / +848 | -5.3% / +921 | -1.8% / +525 |
| K7|london|40x60 | -8.7% / +1875 | -0.5% / -1443 | -7.6% / +364 | +0.2% / -87 | +4.5% / +62 | +9.4% / +524 |

## Window L6M

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | maxDD -32772 (ref -22565; -45.2%), worst wk -13709 (ref -13430), d net -1060/wk (live x1.75 -1855; $4.84 -1078), stops 14.57 (10.88) | maxDD -32772 (ref -22508; -45.6%), worst wk -13709 (ref -13430), d net -1286/wk (live x1.75 -2250; $4.84 -1301), stops 14.00 (10.46) | FAILS (DD vs ref -45.2%; beats all 6 controls on DD and mean: no) |
| U7|asia|40x40 | maxDD -19715 (ref -22565; +12.6%), worst wk -10253 (ref -13430), d net +1151/wk (live x1.75 +2014; $4.84 +1116), stops 11.07 (10.88) | maxDD -19715 (ref -22508; +12.4%), worst wk -10253 (ref -13430), d net +993/wk (live x1.75 +1737; $4.84 +959), stops 10.65 (10.46) | FAILS (DD vs ref +12.6%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x40 | maxDD -23765 (ref -22565; -5.3%), worst wk -14595 (ref -13430), d net +489/wk (live x1.75 +856; $4.84 +466), stops 14.04 (10.88) | maxDD -22691 (ref -22508; -0.8%), worst wk -14595 (ref -13430), d net +535/wk (live x1.75 +936; $4.84 +512), stops 13.62 (10.46) | FAILS (DD vs ref -5.3%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x60 | maxDD -23765 (ref -22565; -5.3%), worst wk -13831 (ref -13430), d net +377/wk (live x1.75 +659; $4.84 +371), stops 10.88 (10.88) | maxDD -22110 (ref -22508; +1.8%), worst wk -13831 (ref -13430), d net +422/wk (live x1.75 +739; $4.84 +417), stops 10.46 (10.46) | FAILS (DD vs ref -5.3%; beats all 6 controls on DD and mean: no) |
| K7|london|40x60 | maxDD -21970 (ref -22565; +2.6%), worst wk -14936 (ref -13430), d net -1410/wk (live x1.75 -2468; $4.84 -1421), stops 10.65 (10.88) | maxDD -21970 (ref -22508; +2.4%), worst wk -14936 (ref -13430), d net -1615/wk (live x1.75 -2826; $4.84 -1625), stops 10.23 (10.46) | FAILS (DD vs ref +2.6%; beats all 6 controls on DD and mean: no) |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | +3.6% / +894 | -9.0% / +1256 | +0.8% / -33 | -5.1% / -1520 | -10.5% / -1113 | -24.3% / -429 |
| U7|asia|40x40 | -2.9% / +928 | -8.1% / +1656 | -3.3% / +656 | -6.3% / -280 | -1.2% / -506 | +0.2% / +1221 |
| K7|nyam|40x40 | -26.2% / +235 | -9.0% / +1006 | -3.9% / -220 | -2.3% / +542 | -5.3% / +298 | -1.8% / +110 |
| K7|nyam|40x60 | -6.4% / +284 | -1.5% / -419 | +0.8% / -559 | -1.8% / +419 | -5.3% / +230 | -1.8% / +270 |
| K7|london|40x60 | -8.7% / +935 | -0.5% / +76 | -7.6% / -632 | +0.2% / -465 | +4.5% / -197 | +7.6% / -24 |

## Window HOLD

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | maxDD -72222 (ref -74402; +2.9%), worst wk -28915 (ref -31211), d net -1305/wk (live x1.75 -2284; $4.84 -1304), stops 12.14 (10.17) | n/a | FAILS (DD vs ref +2.9%; beats all 6 controls on DD and mean: no) |
| U7|asia|40x40 | maxDD -67152 (ref -74402; +9.7%), worst wk -33286 (ref -31211), d net +1155/wk (live x1.75 +2022; $4.84 +1124), stops 10.21 (10.17) | n/a | FAILS (DD vs ref +9.7%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x40 | maxDD -84992 (ref -74402; -14.2%), worst wk -35148 (ref -31211), d net -431/wk (live x1.75 -754; $4.84 -460), stops 14.50 (10.17) | n/a | FAILS (DD vs ref -14.2%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x60 | not finished | n/a | not finished |
| K7|london|40x60 | maxDD -76096 (ref -74402; -2.3%), worst wk -30842 (ref -31211), d net -194/wk (live x1.75 -339; $4.84 -201), stops 10.25 (10.17) | n/a | not finished (controls pending); real DD -2.3%, d mean -194 |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | +2.0% / -717 | -7.8% / +1528 | -9.6% / -83 | +6.1% / -420 | +1.3% / -1246 | +2.6% / +322 |
| U7|asia|40x40 | -2.0% / -707 | -10.3% / +117 | -8.0% / -683 | +14.9% / +1262 | +9.9% / +691 | -3.1% / -686 |
| K7|nyam|40x40 | -6.5% / -638 | -14.4% / +1195 | -17.3% / -458 | -3.1% / +61 | -7.3% / -267 | -7.8% / -315 |
| K7|nyam|40x60 | n/f | n/f | n/f | n/f | -0.6% / -31 | +3.0% / -553 |
| K7|london|40x60 | +0.4% / -37 | -12.6% / +1690 | n/f | +1.9% / +64 | n/f | n/f |

## Window GAP

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | maxDD -65204 (ref -54615; -19.4%), worst wk -28915 (ref -30852), d net -1311/wk (live x1.75 -2294; $4.84 -1297), stops 13.16 (10.29) | n/a | FAILS (DD vs ref -19.4%; beats all 6 controls on DD and mean: no) |
| U7|asia|40x40 | maxDD -65476 (ref -54615; -19.9%), worst wk -23888 (ref -30852), d net -903/wk (live x1.75 -1580; $4.84 -941), stops 10.54 (10.29) | n/a | FAILS (DD vs ref -19.9%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x40 | maxDD -52584 (ref -54615; +3.7%), worst wk -30605 (ref -30852), d net -1367/wk (live x1.75 -2393; $4.84 -1387), stops 13.83 (10.29) | n/a | FAILS (DD vs ref +3.7%; beats all 6 controls on DD and mean: no) |
| K7|nyam|40x60 | not finished | n/a | not finished |
| K7|london|40x60 | maxDD -52542 (ref -54615; +3.8%), worst wk -27650 (ref -30852), d net +983/wk (live x1.75 +1721; $4.84 +976), stops 10.29 (10.29) | n/a | not finished (controls pending); real DD +3.8%, d mean +983 |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | -23.3% / -1048 | -6.3% / +3239 | -31.8% / +13 | +8.1% / +1447 | -14.7% / -1502 | +15.9% / +1548 |
| U7|asia|40x40 | -21.0% / -1391 | +5.8% / +946 | -20.7% / -700 | -6.2% / -624 | -20.9% / -2034 | +0.9% / -791 |
| K7|nyam|40x40 | -21.1% / -1290 | +0.2% / +2857 | -21.0% / +362 | +1.1% / -98 | +0.1% / -349 | +0.0% / -517 |
| K7|nyam|40x60 | n/f | n/f | n/f | n/f | +2.3% / -213 | -1.6% / -853 |
| K7|london|40x60 | -10.7% / -609 | +9.1% / +3926 | n/f | +1.5% / +351 | n/f | n/f |

## Window PRE

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | not finished | n/a | not finished |
| U7|asia|40x40 | maxDD -80137 (ref -70931; -13.0%), worst wk -29106 (ref -28958), d net -158/wk (live x1.75 -277; $4.84 -183), stops 9.23 (9.03) | n/a | not finished (controls pending); real DD -13.0%, d mean -158 |
| K7|nyam|40x40 | not finished | n/a | not finished |
| K7|nyam|40x60 | maxDD -70642 (ref -70931; +0.4%), worst wk -27717 (ref -28958), d net -103/wk (live x1.75 -181; $4.84 -109), stops 9.05 (9.03) | n/a | not finished (controls pending); real DD +0.4%, d mean -103 |
| K7|london|40x60 | not finished | n/a | not finished |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| U7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|london|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window X'

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | not finished | n/a | not finished |
| U7|asia|40x40 | not finished | n/a | not finished |
| K7|nyam|40x40 | not finished | n/a | not finished |
| K7|nyam|40x60 | not finished | n/a | not finished |
| K7|london|40x60 | not finished | n/a | not finished |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| U7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|london|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |

## P3: the exact policy lines, session names, override or stack
Source: the live DS7.cs (~/DS7.cs, ApplyPolicyBracket, line 2733) and THP policy format (autopilot/THP_POLICY_bracket_section.txt). Read directly, not inferred.

**Exact policy lines** (format `bracket <D6 tag> <session> stop=<pts> target=<pts>`; session names are the engine SessionNames lower-cased: asia, london, pre, nyam, nypm, close, as in the live log line `P7 POLICY BRACKET: stop 60.0 target 58.0 lots 12 (rule [bracket P7 * target=58])`):
1. `bracket A7 asia stop=40 target=40`
2. `bracket U7 asia stop=40 target=40`
3. `bracket K7 nyam stop=40 target=40`
4. `bracket K7 nyam stop=40 target=60`
5. `bracket K7 london stop=40 target=60`
(the engine applied these through the hook `fix=[target, stop]` with `pol=1`; in the engine the K7 and the others have an own bracket 60/60 (target ~58-60 after fills); the cells change only the named book in only the named session.)

**Override or stack.** ApplyPolicyBracket loops the bracket rules in FILE ORDER and applies the FIRST rule whose book (`*` or the tag), regime/session (`*`, day regime, session name or entry context fresh|rechase) and conditions match, then `break`s. So rules never stack. A session line overrides a wildcard line such as `bracket K7 * target=59` only if it appears BEFORE it in the file; if it appears after, the wildcard matches first and the session line is never reached. The five lines must therefore be placed above any `bracket K7 *` / `bracket <tag> *` line for the same book. Note also the wildcard line in the file today sets only target (stop stays at the book value), a session line sets both.

**Lots.** Unless `lotmult=` is given, lots are multiplied by baseStop/newStop and rounded half-up (min 1): a 40-point stop on a 60-point book gives x1.5 lots ($-risk parity), as in the cells (policy-equivalent version: lots x 60/stop). The target line only (`target=` without `stop=`) leaves stop and lots unchanged.

**Cuts, trails, caps.** The cells leave every other layer exactly as the JL2 engine has them: the TH-L2 loss cut, state cut, context cut and flat cut arms (30-point panel arm and the policy `pct` lines, where `pct` is relative to the trade stop distance in the live file), tight trails, day caps, give-back lock and week floor (lock R stays at the session-table value, not the new stop), P7 cap, the stack cap, and the JL2 layers (wb_hooks panel with ctxcut and p7_daycap 42000/8400, ec_hooks K7 flat cut 45, scr_hooks conjunction gate, c_gov skip rule, ev_panel ATR skip for P7, S1B-COMB base with the JN05W2J works config, atr input jnr_atr_ev3). Caveat to state plainly: in the live DS7 the loss-side `pct` arm and `TradeStopPts`-based levels move with the policy stop (pct = unrealised / stop distance), while the sim's state-cut arm is a fixed 30-point value; the cells do not rescale it, so a 40-point stop meets the same 30-point arm. This is the engine behaviour and is not changed by the hook.

