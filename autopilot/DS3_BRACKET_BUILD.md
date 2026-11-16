# DS3_BRACKET_BUILD - the five bracket cells on TL3_EV_JN05W2JL2 (deadline order 2026-11-16, P2 and P3)
**STATUS: A7|asia|40x40: no window complete; U7|asia|40x40: no window complete; K7|nyam|40x40: no window complete; K7|nyam|40x60: no window complete; K7|london|40x60: no window complete. Not a PASS claim. Dollars are BASE lots; x1.75 = live lots; $4.84 = FEES.md round-turn repriced (net - lots x 3.66).**

Reference: TL3_EV_JN05W2JL2 (final, 43 months). Cells: hook d10_hooks fix=[target, stop] on ONE book in ONE session, policy-line equivalent (`pol`): only the stop and target points change, lots x baseStop/newStop rounded half-up min 1 (the DS7.cs default lotmult), cut arms/trails/caps/day-lock R left at the engine values. Placebo (3 seeds) = the same target/stop applied to a pseudo-random subset of ALL signals (every book and session) with the same expected count as the cell's signals (share of all signals); matched random control (3 seeds) = the same bracket applied to a pseudo-random 50% of the cell's own book x session signals (same book x session x month mix, half the count, so read the control against about half of the real effect). Pass rule: DD not worse than the reference AND the real cell beats all six controls on both DD cut and mean delta, per window; W44-removed rows shown for windows that contain 2026-W44 (L3M, L6M). Windows: L3M 2026-08..10, L6M 2026-05..10, HOLD 2025-11..2026-04, GAP 2026-02-07..04-30, PRE 2024-10..2025-06, X' 2023-04..2024-01. Drawdown is the whole-stack max drawdown (daily cumulative) in the window.

## Window L3M

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | not finished | not finished | not finished |
| U7|asia|40x40 | maxDD -19400 (ref -22565; +14.0%), worst wk -6939 (ref -13430), d net +1716/wk (live x1.75 +3004; $4.84 +1682), stops 9.89 (10.27) | maxDD -19400 (ref -22508; +13.8%), worst wk -5235 (ref -13430), d net +1400/wk (live x1.75 +2450; $4.84 +1367), stops 9.05 (9.43) | not finished (controls pending); real DD +14.0%, d mean +1716 |
| K7|nyam|40x40 | not finished | not finished | not finished |
| K7|nyam|40x60 | not finished | not finished | not finished |
| K7|london|40x60 | not finished | not finished | not finished |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | +7.3% / +2616 | n/f | +0.8% / +955 | n/f | -10.5% / -1626 | n/f |
| U7|asia|40x40 | n/f | -8.1% / +1767 | n/f | -6.3% / +288 | n/f | +0.2% / +1910 |
| K7|nyam|40x40 | -26.2% / +1620 | n/f | -3.9% / +341 | n/f | n/f | n/f |
| K7|nyam|40x60 | n/f | -1.5% / -1565 | n/f | n/f | n/f | n/f |
| K7|london|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window L6M

| cell | real (drawdown first) | W44 removed | verdict |
|---|---|---|---|
| A7|asia|40x40 | not finished | not finished | not finished |
| U7|asia|40x40 | not finished | not finished | not finished |
| K7|nyam|40x40 | not finished | not finished | not finished |
| K7|nyam|40x60 | not finished | not finished | not finished |
| K7|london|40x60 | not finished | not finished | not finished |

Controls (drawdown cut % vs reference, d mean $/wk):
| cell | placebo 1 | placebo 2 | placebo 3 | matched 1 | matched 2 | matched 3 |
|---|---|---|---|---|---|---|
| A7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| U7|asia|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x40 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|nyam|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |
| K7|london|40x60 | n/f | n/f | n/f | n/f | n/f | n/f |

## Window HOLD

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

## Window GAP

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

## Window PRE

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

