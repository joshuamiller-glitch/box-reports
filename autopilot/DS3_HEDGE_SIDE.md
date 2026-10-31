# DS3_HEDGE_SIDE - the hedge side, part 1: sleeves and the chop-day book (C1, 2026-11-01 overnight). POST-HOC pricing of pre-stated cells, nothing here is a PASS, nothing goes live

Prereg `l2vast/ds3/prereg/HEDGE_SIDE_prereg.md` sha256 `e25e64c5d52a786fd88c2fb4f6ec3485780eca819f876c5fb007dfc1cfd91bc3` (in DECISIONS.md before scoring; dead_lookup NOT FOUND x6 before scoring; the 40 cells appended to DEAD_CELLS after, program HEDGE1). Code `l2vast/ds3/code/hedge/`, results `l2vast/ds3/out/hedge/`. Capped 20260206, UNTOUCHED never read. Stack = the Sunday composite on the one-convention engine at live lots (DD-1 COMP|off: maxDD ALL 241k = the single PRE episode, worst-20 -1,098k, weekly SD 50k); the as-is stack and the composite with the 12R week lock are the two other stacks in section 4. Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149; PX = PRE+X' (selection). Units $k unless stated. "Hedge value" = change in the STACK's maxDD (weekly cumulative), worst-20 (sum of the 20 worst weeks; shown only for PRE, X', ALL because L3M/L6M/HOLD have fewer than 20 losing weeks), SD and Calmar when a sleeve of 1/2/3/5 NQ lots is added; the sleeve's own mean is a column, not the headline.

## Plain sentence

**No sleeve in the VWAP-reversion family or its cousins is a demonstrated hedge for the Sunday composite.** Added at 1-5 NQ lots (T-CLOSE could fill 10-20 lots at 15:30) the market-fill VWAP-reversion sleeves move the stack's PRE/X' maxDD by 3% or less and the weekly SD by about 0.5% or less, because 3 lots of an NQ sleeve are a weekly SD of 3-8k against the stack's 50k and the stack's 241k PRE drawdown is one episode. The worst-20 gain of the two positive-mean sleeves (RVW1 F30: +28k at 3 lots on 1,098k, M fills; +14k LIVE-CAL) is mostly the sleeve's own mean: the part above what a constant weekly P&L would give is +18k with a 95% interval of -7k to +44k; its P&L in the stack's 20 worst weeks (465 per lot-week) vs the other weeks (164) differs by +301 with CI -111 to +729 over 14 independent episodes; the weekly correlation to the stack is -0.00 (PX +0.08); and it does not beat the random-timing / random-sign placebos on ALL maxDD (67-74%). Across all 40 cells the largest "better in the stack's worst-20 weeks" t is 1.93 and none exceeds 2 (chance gives about one); the purged 5-fold CV picks E in 3 of 5 folds and has a positive held-out score in 3 of 5 (E's folds +0.05 / -0.08 / +0.01). The one negatively correlated sleeve, the 10:30-14:30 VWAP-band fade (B z>=2.0: corr -0.25 ALL, -0.27 PX, -0.33 inside the worst-20 weeks), has a negative mean and does not cut maxDD (L6M +5%, L3M +12% worse). Two LEADS, Shadow only: (i) the prior-value-area 80% rule (E): positive mean in all five windows (L6M +0.30k per lot-week, MDE 1.19k), cuts the stack maxDD in BOTH PRE (-6.2% at 3 lots, -9.5% at 5) and X' (-11.3%, -18.8%), same sign under LIVE-CAL, no change in L6M, placebo rank 81-95% (below the 95% bar), and at 20 lots it blows up (L6M maxDD 23k to 90k); (ii) the CHOP-DAY tag: on the 52 pre-registered tag days (7% of days) the stack lost 9.4k per tag day on the 8 tag days that fall in its 20 worst weeks (7 distinct weeks) and a 3-lot VWAP-band fade earned +14.3k on exactly those 8 days (8 of 8 winners) while losing 8.2k on the other 44 tag days (20 of 44 winners): a day-level hedge pattern with an effective N of 7 episodes, selected in-sample on PX. As a regime-switched stack (halve the trend books after 10:30 on tag days + that fade at 3 lots) the ALL maxDD goes 241.2k to 231.6k and the worst-20 -1,098k to -1,086k with L6M unchanged, and it beats the shuffled-tag and random-tag placebos at only 82-84% on both (bar 95%); a post-hoc looser tag (23% of days) cuts ALL maxDD 8.5% and L6M 10% and also stays under the bar on the ALL gates (74-87%). Verdict: hedge value at 1-5 lots is too small to separate from the stack's own noise, and scaling it up does not help (RVW1's worst-20 gain peaks near 10 lots and falls back at 20, E's does not); the road is Shadow forward logging of E, the chop-day tag and the B fade on tag days, with the ASSEMBLY section (C2, link at the end) deciding whether any of it sits beside the assembly portfolio.

## Page 1 - the table (3 lots, recent windows first; M = measured fills, LC = LIVE-CAL fills incl. the passive-fill haircut; tail windows only for worst-20)

| sleeve (3 lots; fills M \| LIVE-CAL) | own mean $k/wk (MDE) at 3 lots | corr to stack (ALL / PX; inside worst-20 wk) | stack worst-20 $k before→after (PRE · X' · ALL) | stack maxDD $k before→after (L6M · PRE · X' · ALL) | D7 spec |
|---|---|---|---|---|---|
| A* RVW1 F30 limit-at-touch (15:30, z>=1.0, 30/30) [pre-named] | L6M +0.33 (1.21) · PRE +0.78 (1.00) · X' +0.38 (1.15) · ALL +0.61 (0.66) | -0.00 / +0.08; in worst-20 -0.18 | M -875→-855 · -420→-425 · -1098→-1070<br>LC -875→-867 · -420→-421 · -1098→-1084 | M 23→21 · 241→239 · 121→120 · 241→239<br>LC 23→22 · 241→240 · 121→120 · 241→240 | NQ 1-min chart, OnBarClose, ET, RTH only (skip half days). Series from 09:30 bars: tp=(H+L+C)/3, VWAP=cum(tp*vol)/cum(vol), dev=Close-VWAP, sigma=expa… (full spec section 6) |
| A  RVW1 F30 market (15:30, z>=1.0, 30/30) | L6M +0.64 (1.36) · PRE +1.18 (1.06) · X' +0.45 (1.23) · ALL +0.89 (0.70) | +0.03 / +0.08; in worst-20 -0.14 | M -875→-848 · -420→-424 · -1098→-1071<br>LC -875→-855 · -420→-427 · -1098→-1076 | M 23→21 · 241→239 · 121→117 · 241→239<br>LC 23→22 · 241→240 · 121→118 · 241→240 | As RVW1 F30 but MARKET order at the 15:30:00 bar open (needs a fill at the open; a 1-s delay turns the T-CLOSE HOLD edge negative), OCO +30/-30 from f… (full spec section 6) |
| B  VWAP-band fade (z>=2.0, limit, T20/S30, 10:30-14:30) | L6M -0.24 (1.56) · PRE -0.45 (1.04) · X' +0.12 (1.34) · ALL -0.25 (0.73) | -0.25 / -0.27; in worst-20 -0.33 | M -875→-876 · -420→-396 · -1098→-1086<br>LC -875→-875 · -420→-409 · -1098→-1093 | M 23→24 · 241→239 · 121→118 · 241→239<br>LC 23→24 · 241→239 · 121→119 · 241→239 | NQ 1-min, OnBarClose, ET. VWAP/dev/sigma as RVW1. From the 10:30 bar close to the 14:29 bar close, the FIRST bar with |z|>=2.0 triggers (one trade/day… (full spec section 6) |
| C  IB-edge fade (limit at edge, S25, target IB mid) | L6M -0.90 (2.49) · PRE -0.56 (1.67) · X' -0.43 (1.76) · ALL -0.56 (1.10) | -0.01 / +0.02; in worst-20 -0.14 | M -875→-906 · -420→-435 · -1098→-1114<br>LC -875→-896 · -420→-432 · -1098→-1114 | M 23→26 · 241→239 · 121→130 · 241→239<br>LC 23→25 · 241→243 · 121→128 · 241→243 | NQ 1-min, ET. IB = high/low of the 09:30-10:29 bars. At 10:30 place an OCO pair: SELL LIMIT at IB high, BUY LIMIT at IB low (cancel the other on fill;… (full spec section 6) |
| D  failed-breakout fade (IB, B3, target IB mid) | L6M -1.43 (2.22) · PRE -0.00 (1.34) · X' -1.15 (1.24) · ALL -0.62 (0.90) | +0.03 / +0.08; in worst-20 -0.09 | M -875→-880 · -420→-434 · -1098→-1110<br>LC -875→-884 · -420→-439 · -1098→-1114 | M 23→28 · 241→231 · 121→131 · 241→231<br>LC 23→29 · 241→232 · 121→133 · 241→232 | NQ 1-min, OnBarClose, ET. IB as above. From 10:30 to 14:30: a bar whose extreme is >= IB edge +3 pts, followed within 5 bars by a CLOSE back inside th… (full spec section 6) |
| E  prior-VA 80% rule (X40, target opposite edge) | L6M +0.91 (3.57) · PRE +1.08 (3.28) · X' +0.28 (1.66) · ALL +0.90 (1.85) | -0.06 / -0.09; in worst-20 -0.04 | M -875→-869 · -420→-415 · -1098→-1089<br>LC -875→-870 · -420→-416 · -1098→-1091 | M 23→23 · 241→226 · 121→107 · 241→226<br>LC 23→23 · 241→227 · 121→107 · 241→227 | NQ 1-min, ET. Prior RTH day (09:30-15:59) 70% value area: 1-pt bins of typical price weighted by volume, expanded from the POC by the larger neighbour… (full spec section 6) |
| F  close-fade standalone (fade stack signals 14:40-15:00, flat 16:00) | L6M +0.17 (1.53) · PRE +0.16 (0.81) · X' +0.00 (1.12) · ALL +0.14 (0.60) | +0.05 / -0.00; in worst-20 +0.11 | M -875→-873 · -420→-428 · -1098→-1089<br>LC -875→-874 · -420→-428 · -1098→-1089 | M 23→23 · 241→241 · 121→120 · 241→241<br>LC 23→23 · 241→241 · 121→120 · 241→241 | Needs the D6 signal log: at 15:00:00 ET sum side*lots over the stack's trades ENTERED 14:40-15:00 ET (all books; the composite's taken signals); if no… (full spec section 6) |
| CHOP-DAY book (tag at 10:30; trend books x0.5 after 10:30 on tag days + 3-lot B z1.5 market fade on tag days) | fade sleeve on 52 tag days: L6M -0.28 (0.74) · PRE +0.13 (0.36) · X' +0.06 (0.47) · ALL +0.04 (0.27) | regime delta vs stack -0.13; inside worst-20 +0.08 | M -875→-870 · -420→-415 · -1098→-1086 (LIVE-CAL identical to 0.1k) | M 23→23 · 241→232 · 121→123 · 241→232 | tag + fade spec section 6 |

Own mean is the sleeve's weekly P&L at 3 lots, MDE = 2.8 x SE of the weekly series. "corr to stack" = weekly correlation (ALL, PX) and inside the stack's 20 worst weeks. The stack columns are before→after adding 3 lots. Every row is "no hedge established" on the gates of section 2; E and the chop-day book are the only LEADS. The full D7 spec is section 6.

## 1. Stack-level hedge value by lots (M and LIVE-CAL, all windows)

| sleeve | basis | lots | ΔmaxDD L6M | ΔmaxDD PRE | ΔmaxDD X' | ΔmaxDD ALL | Δworst-20 PRE | Δworst-20 X' | Δworst-20 ALL | ΔSD ALL | ΔCalmar ALL | Δmean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RVW1_F30_LMT | M | 1 | -1.4 | -0.6 | -0.2 | -0.6 | +7.6 | -0.8 | +9.3 | +0.01 | +0.001 | +0.20 |
| RVW1_F30_LMT | M | 2 | -1.5 | -1.3 | -0.4 | -1.3 | +14.1 | -2.2 | +18.6 | +0.03 | +0.002 | +0.41 |
| RVW1_F30_LMT | M | 3 | -1.4 | -1.9 | -0.6 | -1.9 | +20.6 | -5.5 | +27.8 | +0.08 | +0.003 | +0.61 |
| RVW1_F30_LMT | M | 5 | -1.4 | -2.7 | -1.0 | -2.7 | +27.2 | -11.9 | +44.4 | +0.22 | +0.005 | +1.02 |
| RVW1_F30_LMT | M | 10 | -1.2 | +2.2 | -2.0 | +2.2 | +35.2 | -28.0 | +63.8 | +0.88 | +0.008 | +2.04 |
| RVW1_F30_LMT | M | 20 | -0.8 | +12.1 | -4.0 | +12.1 | +21.8 | -61.3 | +46.2 | +3.45 | +0.012 | +4.08 |
| RVW1_F30_LMT | LC | 1 | -0.6 | -0.5 | -0.1 | -0.5 | +3.8 | -0.2 | +4.9 | +0.00 | +0.001 | +0.11 |
| RVW1_F30_LMT | LC | 2 | -0.8 | -1.0 | -0.1 | -1.0 | +6.3 | -0.6 | +9.7 | +0.01 | +0.001 | +0.22 |
| RVW1_F30_LMT | LC | 3 | -0.6 | -1.4 | -0.2 | -1.4 | +8.7 | -1.8 | +14.3 | +0.04 | +0.002 | +0.33 |
| RVW1_F30_LMT | LC | 5 | -0.3 | -1.5 | -0.3 | -1.5 | +11.5 | -4.9 | +22.2 | +0.12 | +0.003 | +0.55 |
| RVW1_F30_LMT | LC | 10 | +0.8 | +0.7 | -0.5 | +0.7 | +10.7 | -13.9 | +31.1 | +0.52 | +0.005 | +1.10 |
| RVW1_F30_LMT | LC | 20 | +3.2 | +8.6 | +1.1 | +8.6 | -12.0 | -36.2 | +9.0 | +2.14 | +0.007 | +2.20 |
| A | M | 1 | -1.5 | -0.6 | -1.2 | -0.6 | +10.1 | -0.5 | +9.8 | +0.04 | +0.001 | +0.30 |
| A | M | 2 | -1.5 | -1.2 | -2.5 | -1.2 | +19.1 | -1.6 | +18.2 | +0.09 | +0.003 | +0.59 |
| A | M | 3 | -1.4 | -1.9 | -3.7 | -1.9 | +27.7 | -4.5 | +26.6 | +0.17 | +0.004 | +0.89 |
| A | M | 5 | -1.4 | -2.3 | -6.1 | -2.3 | +39.2 | -10.3 | +43.4 | +0.39 | +0.007 | +1.48 |
| A | M | 10 | -1.2 | +3.0 | -12.3 | +3.0 | +58.9 | -24.8 | +63.0 | +1.27 | +0.011 | +2.96 |
| A | M | 20 | -0.8 | +13.6 | -23.0 | +13.6 | +63.8 | -68.5 | +44.6 | +4.43 | +0.018 | +5.92 |
| A | LC | 1 | -1.5 | -0.4 | -1.0 | -0.4 | +7.5 | -1.4 | +7.3 | +0.04 | +0.001 | +0.23 |
| A | LC | 2 | -1.4 | -0.9 | -1.9 | -0.9 | +14.0 | -3.7 | +14.7 | +0.10 | +0.002 | +0.46 |
| A | LC | 3 | -1.4 | -1.3 | -2.9 | -1.3 | +19.9 | -7.6 | +21.9 | +0.18 | +0.003 | +0.69 |
| A | LC | 5 | -1.2 | -0.6 | -4.8 | -0.6 | +26.0 | -15.5 | +34.2 | +0.40 | +0.005 | +1.14 |
| A | LC | 10 | -0.9 | +6.5 | -9.6 | +6.5 | +32.3 | -35.1 | +40.1 | +1.31 | +0.007 | +2.29 |
| A | LC | 20 | -0.4 | +20.6 | -19.2 | +20.6 | +8.9 | -90.0 | -2.0 | +4.56 | +0.010 | +4.57 |
| B | M | 1 | +0.1 | -0.7 | -0.7 | -0.7 | +0.7 | +8.5 | +4.3 | -0.26 | -0.000 | -0.08 |
| B | M | 2 | +0.2 | -1.5 | -1.5 | -1.5 | -0.1 | +16.1 | +8.1 | -0.49 | -0.000 | -0.17 |
| B | M | 3 | +1.1 | -2.2 | -2.2 | -2.2 | -0.9 | +23.2 | +11.6 | -0.70 | -0.000 | -0.25 |
| B | M | 5 | +2.8 | -3.7 | -3.7 | -3.7 | -5.1 | +36.1 | +17.2 | -1.06 | -0.000 | -0.41 |
| B | M | 10 | +7.1 | -7.3 | -7.0 | -7.3 | -27.4 | +61.2 | +10.5 | -1.58 | -0.001 | -0.83 |
| B | M | 20 | +25.9 | -12.1 | +10.0 | -12.1 | -101.6 | +68.1 | -54.1 | -0.90 | -0.002 | -1.66 |
| B | LC | 1 | -0.0 | -0.7 | -0.4 | -0.7 | +1.0 | +4.0 | +2.2 | -0.15 | -0.000 | -0.07 |
| B | LC | 2 | +0.4 | -1.3 | -0.9 | -1.3 | +0.8 | +7.5 | +3.8 | -0.28 | -0.000 | -0.14 |
| B | LC | 3 | +1.0 | -2.0 | -1.3 | -2.0 | +0.4 | +10.6 | +5.3 | -0.40 | -0.000 | -0.21 |
| B | LC | 5 | +2.2 | -3.0 | -2.2 | -3.0 | -0.9 | +16.0 | +7.6 | -0.59 | -0.000 | -0.36 |
| B | LC | 10 | +5.3 | -4.9 | -2.6 | -4.9 | -13.0 | +26.1 | +3.8 | -0.85 | -0.001 | -0.71 |
| B | LC | 20 | +15.4 | -6.0 | +5.1 | -6.0 | -61.3 | +22.1 | -41.7 | -0.30 | -0.003 | -1.42 |
| C | M | 1 | +0.5 | -0.6 | +3.3 | -0.6 | -10.2 | -4.0 | -4.2 | +0.01 | -0.001 | -0.19 |
| C | M | 2 | +1.7 | -1.2 | +6.5 | -1.2 | -20.5 | -9.8 | -9.9 | +0.07 | -0.001 | -0.37 |
| C | M | 3 | +3.2 | -1.8 | +9.8 | -1.8 | -30.7 | -15.7 | -16.0 | +0.18 | -0.002 | -0.56 |
| C | M | 5 | +6.4 | -3.0 | +20.4 | -3.0 | -58.6 | -27.4 | -36.5 | +0.55 | -0.003 | -0.93 |
| C | M | 10 | +14.4 | +0.4 | +47.4 | +0.4 | -138.5 | -68.2 | -101.3 | +2.31 | -0.008 | -1.86 |
| C | M | 20 | +44.8 | +29.7 | +101.8 | +29.7 | -376.6 | -194.2 | -375.1 | +8.97 | -0.024 | -3.73 |
| C | LC | 1 | +0.5 | +0.6 | +2.1 | +0.6 | -6.8 | -3.5 | -4.0 | +0.01 | -0.001 | -0.18 |
| C | LC | 2 | +1.4 | +1.1 | +4.4 | +1.1 | -13.7 | -7.7 | -9.4 | +0.05 | -0.002 | -0.36 |
| C | LC | 3 | +2.4 | +1.9 | +7.1 | +1.9 | -21.2 | -12.2 | -15.5 | +0.12 | -0.003 | -0.54 |
| C | LC | 5 | +4.6 | +3.9 | +13.4 | +3.9 | -41.3 | -22.1 | -30.6 | +0.37 | -0.005 | -0.89 |
| C | LC | 10 | +10.1 | +12.0 | +30.4 | +12.0 | -100.4 | -55.0 | -81.7 | +1.57 | -0.011 | -1.79 |
| C | LC | 20 | +25.1 | +40.9 | +67.1 | +44.5 | -265.8 | -161.0 | -257.8 | +6.16 | -0.025 | -3.58 |
| D | M | 1 | +1.8 | -3.5 | +3.4 | -3.5 | -1.7 | -4.9 | -2.0 | +0.06 | +0.000 | -0.21 |
| D | M | 2 | +3.5 | -7.0 | +6.7 | -7.0 | -3.3 | -9.8 | -6.9 | +0.14 | +0.001 | -0.41 |
| D | M | 3 | +5.3 | -10.5 | +10.1 | -10.5 | -5.0 | -14.7 | -11.8 | +0.27 | +0.002 | -0.62 |
| D | M | 5 | +8.8 | -17.6 | +16.8 | -17.6 | -16.5 | -25.0 | -29.7 | +0.61 | +0.003 | -1.03 |
| D | M | 10 | +17.6 | -33.8 | +38.1 | -33.8 | -64.1 | -64.6 | -82.6 | +2.03 | +0.005 | -2.06 |
| D | M | 20 | +35.2 | -24.3 | +82.7 | -24.3 | -221.2 | -182.0 | -252.9 | +7.02 | -0.009 | -4.12 |
| D | LC | 1 | +1.9 | -3.1 | +4.0 | -3.1 | -3.1 | -6.5 | -3.5 | +0.05 | -0.000 | -0.31 |
| D | LC | 2 | +3.8 | -6.2 | +8.0 | -6.2 | -6.1 | -12.9 | -10.0 | +0.13 | -0.000 | -0.61 |
| D | LC | 3 | +5.6 | -9.3 | +12.0 | -9.3 | -9.3 | -19.4 | -16.4 | +0.25 | -0.000 | -0.92 |
| D | LC | 5 | +9.4 | -15.5 | +20.6 | -15.5 | -24.1 | -32.9 | -38.1 | +0.60 | -0.000 | -1.53 |
| D | LC | 10 | +18.8 | -28.3 | +47.7 | -28.3 | -79.6 | -88.7 | -100.1 | +2.04 | -0.002 | -3.06 |
| D | LC | 20 | +37.5 | -15.8 | +102.1 | +27.3 | -254.9 | -245.5 | -290.6 | +7.18 | -0.032 | -6.11 |
| E | M | 1 | +0.0 | -5.0 | -4.5 | -5.0 | +3.2 | +3.5 | +5.0 | -0.10 | +0.003 | +0.30 |
| E | M | 2 | +0.0 | -9.9 | -9.1 | -9.9 | +5.3 | +5.1 | +8.2 | -0.06 | +0.007 | +0.60 |
| E | M | 3 | +0.0 | -14.9 | -13.6 | -14.9 | +6.4 | +4.8 | +8.8 | +0.12 | +0.010 | +0.90 |
| E | M | 5 | +0.0 | -23.0 | -22.7 | -23.0 | +6.7 | -0.4 | -0.5 | +0.91 | +0.017 | +1.50 |
| E | M | 10 | +0.0 | -36.3 | -45.3 | -36.3 | -6.4 | -20.4 | -40.1 | +5.16 | +0.031 | +3.01 |
| E | M | 20 | +66.8 | -47.4 | -2.3 | -47.4 | -123.3 | -110.8 | -149.5 | +20.83 | +0.054 | +6.02 |
| E | LC | 1 | +0.0 | -4.8 | -4.4 | -4.8 | +2.7 | +3.1 | +4.5 | -0.10 | +0.003 | +0.28 |
| E | LC | 2 | +0.0 | -9.6 | -8.8 | -9.6 | +4.2 | +4.3 | +7.1 | -0.06 | +0.006 | +0.55 |
| E | LC | 3 | +0.0 | -14.4 | -13.3 | -14.4 | +4.8 | +3.5 | +7.2 | +0.12 | +0.009 | +0.83 |
| E | LC | 5 | +0.0 | -22.1 | -22.1 | -22.1 | +4.0 | -2.5 | -3.5 | +0.92 | +0.016 | +1.38 |
| E | LC | 10 | +0.0 | -34.5 | -44.2 | -34.5 | -12.6 | -25.0 | -46.9 | +5.19 | +0.029 | +2.75 |
| E | LC | 20 | +71.9 | -44.0 | +2.5 | -44.0 | -137.5 | -122.0 | -165.2 | +20.97 | +0.048 | +5.50 |
| F | M | 1 | +0.0 | +0.0 | -0.2 | +0.0 | +0.6 | -2.7 | +3.3 | +0.05 | +0.000 | +0.05 |
| F | M | 2 | +0.0 | +0.0 | -0.5 | +0.0 | +1.2 | -5.3 | +6.6 | +0.11 | +0.000 | +0.09 |
| F | M | 3 | +0.0 | +0.0 | -0.7 | +0.0 | +1.8 | -8.0 | +9.1 | +0.19 | +0.001 | +0.14 |
| F | M | 5 | +0.0 | +0.0 | -1.2 | +0.0 | +3.1 | -13.3 | +8.9 | +0.39 | +0.001 | +0.23 |
| F | M | 10 | +18.7 | +0.0 | +0.5 | +0.0 | +6.1 | -40.2 | -7.1 | +1.16 | +0.002 | +0.47 |
| F | M | 20 | +56.2 | +0.0 | +7.6 | +0.0 | +10.4 | -94.8 | -91.9 | +3.70 | +0.004 | +0.94 |
| F | LC | 1 | +0.0 | +0.0 | -0.2 | +0.0 | +0.6 | -2.8 | +3.2 | +0.05 | +0.000 | +0.04 |
| F | LC | 2 | +0.0 | +0.0 | -0.5 | +0.0 | +1.1 | -5.5 | +6.4 | +0.11 | +0.000 | +0.09 |
| F | LC | 3 | +0.0 | +0.0 | -0.7 | +0.0 | +1.7 | -8.3 | +8.9 | +0.19 | +0.001 | +0.13 |
| F | LC | 5 | +0.1 | +0.0 | -1.1 | +0.0 | +2.8 | -13.9 | +8.5 | +0.39 | +0.001 | +0.21 |
| F | LC | 10 | +18.8 | +0.0 | +1.1 | +0.0 | +5.5 | -41.2 | -8.0 | +1.15 | +0.002 | +0.43 |
| F | LC | 20 | +56.4 | +0.0 | +8.8 | +0.0 | +9.0 | -96.8 | -93.9 | +3.69 | +0.004 | +0.86 |

ΔmaxDD: negative = maxDD cut (good) in this table (after minus before); Δworst-20: positive = tail improved (less negative). Calmar = mean/maxDD within the window.

(Full window table with SD and Calmar by window is out/hedge/window_tables.csv; at 3 lots ΔSD ALL is at most +0.25k and ΔCalmar ALL at most +0.005 for any sleeve.)

## 2. Does the sleeve beat what randomness gives?

**2a. Risk labels (DRAWDOWN-FIRST convention).** RISK-KEEP = L6M maxDD cut >= 20% AND the sleeve's L6M mean not beyond its MDE on the downside AND beats the placebos; "volume effect" if only the first two hold.

| sleeve | maxDD cut at 3 / 5 lots (M): L6M · PRE · X' | same under LIVE-CAL | own mean L6M inside MDE | beats BOTH placebos (>=95%, ALL maxDD and ALL worst-20; M and LC) | RISK-KEEP label | label |
|---|---|---|---|---|---|---|
| RVW1_F30_LMT | +6% / +6% · +0.8% / +1.1% · +0.5% / +0.8% | +3% / +1% · +0.6% / +0.6% · +0.2% / +0.3% | yes (+0.33k vs MDE 1.21k at 3 lots) | no | no | no hedge established: L6M maxDD cut 6%, PRE/X' under 1%, placebo rank 67-74% on ALL maxDD |
| A | +6% / +6% · +0.8% / +1.0% · +3.1% / +5.1% | +6% / +5% · +0.6% / +0.2% · +2.4% / +4.0% | yes (+0.64k vs MDE 1.36k at 3 lots) | no | no | no hedge established: same as RVW1 (market fill) |
| B | -5% / -12% · +0.9% / +1.5% · +1.8% / +3.0% | -4% / -9% · +0.8% / +1.2% · +1.1% / +1.8% | yes (-0.24k vs MDE 1.56k at 3 lots) | no | no | no: the one negative correlation (-0.25) but negative mean, L6M maxDD worse 5% and L3M 12% |
| C | -14% / -28% · +0.8% / +1.3% · -8.1% / -16.9% | -11% / -20% · -0.8% / -1.6% · -5.9% / -11.1% | yes (-0.90k vs MDE 2.49k at 3 lots) | no | no | no: worsens L6M maxDD 14%, X' 8%, and the ALL worst-20 by 16k |
| D | -23% / -38% · +4.4% / +7.3% · -8.4% / -13.9% | -25% / -41% · +3.9% / +6.4% · -10.0% / -17.1% | yes (-1.43k vs MDE 2.22k at 3 lots) | no | no | no: worsens L6M maxDD 23% and X' 8% (PRE cut 4%), worst-20 -12k |
| E | -0% / -0% · +6.2% / +9.5% · +11.3% / +18.8% | -0% / -0% · +6.0% / +9.2% · +11.0% / +18.3% | yes (+0.91k vs MDE 3.57k at 3 lots) | no | no | LEAD, shadow only: PRE and X' maxDD both cut, L6M unchanged, placebo rank 81-95% (below the 95% bar) |
| F | -0% / -0% · -0.0% / -0.0% · +0.6% / +1.0% | -0% / -0% · -0.0% / -0.0% · +0.6% / +0.9% | yes (+0.17k vs MDE 1.53k at 3 lots) | no | no | no: 60 trades in 3 years, 80% of the 20-week P&L is one week |

**2b. The placebos (200 draws each; random-timing = same trade count, hold, direction mix, bracket distances, random day and entry bar; random-sign = same trades, sign flipped with p 0.5; for LC both carry the same 60% passive-fill retention).** "Real beats %" = share of the 200 draws whose hedge change is worse than the real one. Placebo sleeves are unprofitable after costs, which is why the worst-20 column of a positive-mean sleeve reads 95-100% (that is the mean, see 2c) while the maxDD column does not.

| sleeve | basis | placebo | real beats % of 200 draws: ΔmaxDD ALL | Δworst-20 ALL | ΔmaxDD L6M | ΔmaxDD PX | Δworst-20 PX | placebo mean ΔmaxDD-cut ALL / Δworst-20 ALL ($k) | hedge claim (>=95% on ALL maxDD and ALL worst-20 vs BOTH) |
|---|---|---|---|---|---|---|---|---|---|
| RVW1_F30_LMT | M | random-timing | 74% | 99% | 84% | 74% | 98% | -3.0 / -10.6 | no |
| RVW1_F30_LMT | M | random-sign | 68% | 100% | 70% | 68% | 95% | -1.5 / -4.1 | no |
| RVW1_F30_LMT | LC | random-timing | 68% | 98% | 79% | 68% | 90% | -2.1 / -7.7 | no |
| RVW1_F30_LMT | LC | random-sign | 67% | 98% | 80% | 67% | 85% | -0.9 / -3.4 | no |
| A | M | random-timing | 65% | 100% | 79% | 65% | 98% | -2.4 / -11.0 | no |
| A | M | random-sign | 68% | 100% | 78% | 68% | 100% | -1.5 / -6.5 | no |
| A | LC | random-timing | 72% | 100% | 80% | 72% | 99% | -4.7 / -16.6 | no |
| A | LC | random-sign | 72% | 100% | 74% | 72% | 96% | -2.4 / -10.3 | no |
| B | M | random-timing | 76% | 96% | 52% | 76% | 92% | -5.3 / -15.0 | no |
| B | M | random-sign | 48% | 88% | 38% | 48% | 82% | +2.6 / -1.7 | no |
| B | LC | random-timing | 76% | 92% | 72% | 76% | 88% | -4.3 / -11.8 | no |
| B | LC | random-sign | 58% | 82% | 61% | 58% | 75% | +0.7 / -2.9 | no |
| C | M | random-timing | 70% | 77% | 44% | 70% | 60% | -7.0 / -34.3 | no |
| C | M | random-sign | 40% | 48% | 44% | 40% | 34% | +5.8 / -14.3 | no |
| C | LC | random-timing | 68% | 85% | 64% | 68% | 76% | -9.8 / -41.4 | no |
| C | LC | random-sign | 40% | 62% | 100% | 40% | 59% | +2.1 / -18.6 | no |
| D | M | random-timing | 91% | 70% | 22% | 91% | 56% | -4.9 / -20.5 | no |
| D | M | random-sign | 74% | 70% | 0% | 74% | 60% | +2.9 / -19.4 | no |
| D | LC | random-timing | 89% | 72% | 26% | 89% | 61% | -5.9 / -29.0 | no |
| D | LC | random-sign | 76% | 74% | 0% | 76% | 65% | +1.7 / -25.4 | no |
| E | M | random-timing | 90% | 86% | 71% | 90% | 86% | -4.5 / -19.6 | no |
| E | M | random-sign | 84% | 94% | 51% | 84% | 94% | +1.9 / -15.7 | no |
| E | LC | random-timing | 90% | 90% | 68% | 90% | 88% | -5.5 / -21.5 | no |
| E | LC | random-sign | 81% | 95% | 56% | 81% | 92% | +2.3 / -22.0 | no |
| F | M | random-timing | 52% | 90% | 25% | 52% | 88% | -0.7 / -3.0 | no |
| F | M | random-sign | 0% | 90% | 0% | 0% | 81% | +0.0 / -1.4 | no |
| F | LC | random-timing | 52% | 92% | 24% | 52% | 90% | -0.3 / -3.2 | no |
| F | LC | random-sign | 0% | 91% | 0% | 0% | 80% | +0.0 / -1.5 | no |

**2c. Conditional correlation: is the sleeve better exactly when the stack is worst? (ALL, the stack's 20 worst weeks vs the other 129; 14 independent episodes among the 20; CI by resampling weeks)**

| sleeve | own P&L per lot in the stack's 20 worst weeks ($/wk) | in the other 129 weeks | difference [95% CI, resample] | t (Welch) | corr inside worst-20 / outside | independent episodes among the 20 | excess Δworst-20 at 3 lots vs mean-only [CI] | largest single week share of the 20-week sleeve P&L | Δ with 2026-01-19 week removed (L6M maxDD, ALL w20) |
|---|---|---|---|---|---|---|---|---|---|
| RVW1_F30_LMT | +465 | +164 | +301 [-111, +729] | +1.31 | -0.18 / +0.10 | 14 | +18.1k [-6.7k, +43.8k] | 26% | -4.1 , +27.8 |
| A | +497 | +265 | +232 [-173, +635] | +1.06 | -0.14 / +0.11 | 14 | +13.9k [-10.4k, +38.1k] | 24% | -5.8 , +26.6 |
| B | +216 | -129 | +346 [-168, +846] | +1.31 | -0.33 / -0.23 | 14 | +20.7k [-10.1k, +50.7k] | 46% | +0.2 , +11.6 |
| C | -171 | -189 | +17 [-708, +821] | +0.04 | -0.14 / +0.00 | 14 | +1.0k [-42.5k, +49.3k] | n/a | +1.6 , -16.0 |
| D | -93 | -223 | +130 [-434, +703] | +0.45 | -0.09 / +0.08 | 14 | +7.8k [-26.0k, +42.2k] | n/a | +5.3 , -11.8 |
| E | +343 | +294 | +49 [-692, +747] | +0.13 | -0.04 / -0.08 | 14 | +2.9k [-41.5k, +44.8k] | 44% | +0.0 , +8.8 |
| F | +165 | +28 | +137 [-129, +481] | +0.85 | +0.11 / +0.10 | 14 | +8.2k [-7.8k, +28.8k] | 80% | +0.0 , +9.1 |

Effective N: the 20 worst weeks of the composite form 14 episodes (weeks within 2 of each other counted once), so a CI on a mean over them rests on about 14 draws, and the stack's 241k maxDD is ONE episode. "Excess" = the Δworst-20 above what the sleeve's all-weeks mean would give by itself (3 x 20 x difference). No sleeve's excess has a CI above zero. Last column: the same 3-lot add with the 2026-01-19 week (the as-is stack's L6M maxDD week) zeroed in both stack and sleeve; the ALL worst-20 column does not move, and the L6M maxDD change of RVW1 / A flips from a 1.4k cut to a 4-6k increase when that week is removed, i.e. their small L6M cut rests on that one week.

**2d. 40-cell family (selection score on PX, 3 lots, min of M and LC; weekly correlation; Welch t of "better in the worst-20 weeks").** The best-of-40 t is 1.93; 0 cells exceed 2.

| rank | cell | n events | own PX mean $/wk/lot M (MDE) \| LC | selection score (PX, 3 lots, min of M/LC) | weekly corr ALL | cond t |
|---|---|---|---|---|---|---|
| 1 | E|va80|X40|tgedge | 344 | +263 (723) \| +238 | +0.0319 | -0.06 | +0.13 |
| 2 | E|va80|X25|tgedge | 344 | +5 (348) \| -24 | +0.0254 | -0.08 | +0.74 |
| 3 | E|va80|X40|tg30 | 344 | +114 (224) \| +74 | +0.0117 | -0.17 | +1.93 |
| 4 | E|va80|X25|tg30 | 344 | +61 (192) \| +28 | +0.0112 | -0.05 | +1.31 |
| 5 | A|rvw|t1530|z1.0|mkt | 726 | +306 (269) \| +244 | +0.0080 | +0.03 | +1.06 |
| 6 | D|failbo_ib|B3|tgmid | 774 | -143 (328) \| -239 | +0.0070 | +0.03 | +0.45 |
| 7 | A|rvw|t1530|z1.0|lmt | 726 | +213 (254) \| +113 | +0.0064 | -0.00 | +1.31 |
| 8 | A|rvw|t1530|z1.5|mkt | 557 | +271 (220) \| +224 | +0.0064 | +0.06 | +0.95 |
| 9 | A|rvw|t1530|z1.5|lmt | 557 | +194 (204) \| +109 | +0.0055 | +0.04 | +1.29 |
| 10 | B|vband|z2.0|lmt|T20 | 1016 | -80 (276) \| -75 | +0.0055 | -0.25 | +1.31 |
| 11 | D|failbo_ib|B3|tg30 | 774 | -100 (241) \| -169 | +0.0041 | -0.03 | +1.32 |
| 12 | F|stackfade|x1600|stopNone | 60 | +35 (220) \| +31 | +0.0038 | +0.05 | +0.85 |
| 13 | F|stackfade|x1550|stop40 | 60 | +1 (149) \| -5 | +0.0030 | -0.00 | +1.21 |
| 14 | F|stackfade|x1550|stopNone | 60 | +72 (161) \| +68 | +0.0024 | +0.02 | +0.80 |
| 15 | F|stackfade|x1600|stop40 | 60 | -23 (162) \| -29 | +0.0017 | +0.01 | +0.78 |
| 16 | D|failbo_ib|B10|tgmid | 649 | -162 (336) \| -235 | +0.0010 | +0.04 | +0.21 |
| 17 | B|vband|z2.0|mkt|T20 | 1016 | -64 (274) \| -152 | -0.0004 | -0.20 | +1.17 |
| 18 | D|failbo_ib|B10|tg30 | 649 | -81 (228) \| -152 | -0.0024 | -0.01 | +1.08 |
| 19 | A|rvw|t1515|z1.0|lmt | 711 | +190 (227) \| +88 | -0.0061 | -0.00 | +0.06 |
| 20 | E|va_edge|X20|tg25 | 336 | -32 (161) \| -31 | -0.0064 | -0.01 | +0.60 |
| 21 | B|vband|z1.5|mkt|T20 | 1040 | -121 (277) \| -193 | -0.0068 | -0.06 | +0.46 |
| 22 | B|vband|z1.5|lmt|T20 | 1040 | -140 (282) \| -119 | -0.0085 | -0.10 | +0.51 |
| 23 | A|rvw|t1515|z1.0|mkt | 711 | +177 (229) \| +81 | -0.0088 | -0.01 | +0.20 |
| 24 | E|va_edge|X20|tgpoc | 336 | -22 (250) \| -31 | -0.0097 | -0.01 | -0.16 |
| 25 | A|rvw|t1515|z1.5|lmt | 543 | +174 (196) \| +95 | -0.0109 | +0.08 | -0.54 |
| 26 | E|va_edge|X30|tg25 | 336 | -28 (196) \| -29 | -0.0134 | -0.06 | +0.32 |
| 27 | A|rvw|t1515|z1.5|mkt | 543 | +153 (199) \| +76 | -0.0144 | +0.07 | -0.50 |
| 28 | C|ibedge|X25|tgmid | 982 | -172 (413) \| -164 | -0.0160 | -0.01 | +0.04 |
| 29 | C|ibedge|X25|tg20 | 982 | -127 (233) \| -116 | -0.0171 | +0.05 | +0.39 |
| 30 | B|vband|z2.0|lmt|T30 | 1016 | -123 (322) \| -106 | -0.0184 | -0.14 | +0.56 |
| 31 | D|failbo_pd|B3|tg30 | 393 | -87 (188) \| -138 | -0.0188 | -0.03 | +1.93 |
| 32 | B|vband|z1.5|lmt|T30 | 1040 | -207 (329) \| -153 | -0.0216 | -0.06 | +1.75 |
| 33 | E|va_edge|X30|tgpoc | 336 | -86 (291) \| -68 | -0.0225 | -0.00 | +0.14 |
| 34 | C|ibedge|X15|tg20 | 982 | -190 (193) \| -162 | -0.0233 | +0.12 | -0.72 |
| 35 | D|failbo_pd|B10|tg30 | 324 | -62 (184) \| -87 | -0.0240 | +0.11 | -0.31 |
| 36 | B|vband|z2.0|mkt|T30 | 1016 | -135 (319) \| -218 | -0.0284 | -0.12 | +0.55 |
| 37 | B|vband|z1.5|mkt|T30 | 1040 | -203 (331) \| -292 | -0.0292 | -0.05 | +1.72 |
| 38 | C|ibedge|X15|tgmid | 982 | -289 (338) \| -237 | -0.0304 | +0.05 | -0.38 |
| 39 | F|uncond|x1600 | 1037 | -11 (812) \| -58 | -0.0555 | +0.20 | +0.53 |
| 40 | F|uncond|x1550 | 1037 | +103 (548) \| +56 | -0.0601 | +0.28 | -1.19 |

**2e. Purged 5-fold CV over the 119 PX weeks (2-week embargo; the cell is re-picked on the other four folds with the PX rule)**

| fold | test weeks | cell picked on the other folds (2-wk embargo) | held-out score | held-out maxDD cut $k | held-out worst-5 gain $k | pre-named RVW1-LMT held-out score | maxDD cut | worst-5 gain |
|---|---|---|---|---|---|---|---|---|
| 0 | 24 | E|va80|X40|tgedge | +0.051 | +13.6 | -1.9 | +0.008 | +0.6 | +1.9 |
| 1 | 24 | E|va80|X40|tgedge | -0.084 | -8.5 | -12.2 | +0.006 | -0.3 | +3.1 |
| 2 | 24 | A|rvw|t1530|z1.5|mkt | -0.001 | +2.1 | -3.7 | +0.009 | +3.2 | -0.6 |
| 3 | 23 | B|vband|z2.0|mkt|T20 | +0.008 | +3.4 | +0.8 | +0.013 | +1.9 | +6.0 |
| 4 | 23 | E|va80|X40|tgedge | +0.014 | +5.8 | -6.5 | +0.094 | +9.8 | +17.0 |

Folds with a positive held-out score for the CV-picked cell: 3 of 5; for RVW1-LMT: 5 of 5.

## 3. The CHOP-DAY book (regime-switched stack)

Tag at 10:30 ET (prereg): first-hour range (09:30-10:29) < 0.6 x the median of the previous 20 days AND 5-min ER of 09:30-10:30 < 0.3: 70 tag days in the bar history, **52 in the engine window = 7.0% of days** (the sizing question in the order assumes more). On tag days: every trend-book row entering at or after 10:30 ET gets the ER multiplier x0.5 through the engine's mer_fn route (integer lots half-up, min 1, so a 1-lot book cannot halve), and the PX-selected fade sleeve (of the 18 B/C/D cells, ranked on tag days in PX: **B VWAP-band fade z>=1.5, market, target 30 / stop 30, flat 15:50**) runs at 3 lots. Placebos: shuffled tag (tags permuted within calendar month) and random tag of the same share, 200 draws each, the halving re-run through the engine every draw (200 / 200 draws), the fade masked by the placebo tag.

| variant (3-lot fade sleeve B z1.5 market T30 on tag days; halve = engine mer x0.5 at/after 10:30 on tag days) | ΔmaxDD cut ALL $k | Δworst-20 ALL $k | ΔmaxDD cut L6M $k | ΔSD ALL $k | beats % shuffled-tag (n) ΔmaxDD ALL / Δw20 ALL | beats % random-tag (n) ΔmaxDD ALL / Δw20 ALL |
|---|---|---|---|---|---|---|
| halve only | +7.9 | -2.0 | +0.0 | +0.16 | 80% / 32% (200) | 80% / 38% (200) |
| fade only | +1.7 | +14.3 | +0.0 | +0.05 | 74% / 100% (200) | 82% / 100% (200) |
| halve + fade (M) | +9.6 | +12.3 | +0.0 | +0.21 | 82% / 82% (200) | 84% / 84% (200) |
| halve + fade (LIVE-CAL) | +9.6 | +12.3 | +0.0 | +0.21 | 82% / 82% (200) | 84% / 84% (200) |

| variant | window | maxDD $k | worst-20 $k | SD $k | mean $k/wk | Calmar |
|---|---|---|---|---|---|---|
| halve + fade (M) | L3M | 21.4 | n/a | 44.3 | 34.0 | +1.591 |
| halve + fade (M) | L6M | 22.9 | n/a | 42.2 | 40.4 | +1.764 |
| halve + fade (M) | HOLD | 97.0 | n/a | 51.5 | 38.0 | +0.392 |
| halve + fade (M) | PRE | 231.6 | -870.0 | 55.6 | 23.3 | +0.101 |
| halve + fade (M) | X' | 123.0 | -414.9 | 32.3 | 8.0 | +0.065 |
| halve + fade (M) | ALL | 231.6 | -1085.8 | 50.1 | 22.2 | +0.096 |
| halve + fade (LIVE-CAL) | L3M | 21.4 | n/a | 44.3 | 34.0 | +1.590 |
| halve + fade (LIVE-CAL) | L6M | 22.9 | n/a | 42.2 | 40.4 | +1.764 |
| halve + fade (LIVE-CAL) | HOLD | 97.0 | n/a | 51.5 | 38.0 | +0.391 |
| halve + fade (LIVE-CAL) | PRE | 231.6 | -870.2 | 55.6 | 23.3 | +0.100 |
| halve + fade (LIVE-CAL) | X' | 123.1 | -415.1 | 32.3 | 8.0 | +0.065 |
| halve + fade (LIVE-CAL) | ALL | 231.6 | -1085.8 | 50.1 | 22.2 | +0.096 |
| halve only | L3M | 21.4 | n/a | 44.7 | 34.4 | +1.610 |
| halve only | L6M | 22.9 | n/a | 42.2 | 40.7 | +1.777 |
| halve only | HOLD | 97.0 | n/a | 51.4 | 38.2 | +0.394 |
| halve only | PRE | 233.3 | -876.4 | 55.6 | 23.1 | +0.099 |
| halve only | X' | 124.2 | -421.4 | 32.6 | 7.9 | +0.064 |
| halve only | ALL | 233.3 | -1100.1 | 50.2 | 22.2 | +0.095 |
| composite | L3M | 21.4 | n/a | 44.7 | 34.4 | +1.611 |
| composite | L6M | 22.9 | n/a | 42.7 | 41.1 | +1.797 |
| composite | HOLD | 97.0 | n/a | 51.8 | 38.6 | +0.398 |
| composite | PRE | 241.2 | -875.2 | 55.7 | 23.1 | +0.096 |
| composite | X' | 120.5 | -419.6 | 32.6 | 8.0 | +0.066 |
| composite | ALL | 241.2 | -1098.1 | 50.3 | 22.3 | +0.092 |
| asis | L3M | 88.0 | n/a | 45.5 | 12.2 | +0.138 |
| asis | L6M | 88.0 | n/a | 43.9 | 21.7 | +0.247 |
| asis | HOLD | 144.2 | n/a | 53.8 | 21.9 | +0.152 |
| asis | PRE | 162.0 | -810.6 | 50.4 | 18.6 | +0.115 |
| asis | X' | 316.5 | -572.1 | 29.0 | -3.4 | -0.011 |
| asis | ALL | 316.5 | -1161.1 | 47.2 | 13.1 | +0.041 |

Columns of the first table: ΔmaxDD cut and Δworst-20 are positive = better. The tag is ex ante (10:30), rows before 10:30 are untouched, and nothing is read after the cap. **Halving alone** cuts ALL maxDD 7.9k (3%) at -0.1k/wk of mean but leaves the worst-20 unchanged (-2.0k) and L6M untouched (0.0); it beats the shuffled/random tags at 80% on maxDD and 32-38% on worst-20. **The fade alone** earns +6.1k in total over 52 tag days (3 lots): the whole of its Δworst-20 (+14.3k, 100% of placebos) comes from 8 tag days inside 7 of the stack's 20 worst weeks (stack -9.4k per such tag day vs +0.9k on the other 44), where the fade won 8 of 8; on the other 44 tag days it lost 8.2k (20 of 44 winners). 23 of 26 B/C/D/E cells are also positive on those 8 days (VWAP-band cells 8/8 or 7/8), so it is the state, not the cell: the stack loses on chop days and a fade wins there. That is the mechanism the order asked for, and its evidence is 8 days. Lots (halving on):

| lots of the chop fade (halving always on) | ΔmaxDD cut L6M · PRE · X' · ALL ($k) | Δworst-20 PRE · X' · ALL ($k) | ΔSD ALL ($k) | Δmean ALL ($k/wk) |
|---|---|---|---|---|
| 1 | -0.0 · +8.5 · -3.3 · +8.5 | +1.1 · +0.4 · +2.8 | -0.18 | -0.05 |
| 2 | -0.0 · +9.1 · -2.9 · +9.1 | +3.4 · +2.6 · +7.5 | -0.20 | -0.04 |
| 3 | -0.0 · +9.6 · -2.5 · +9.6 | +5.2 · +4.7 · +12.3 | -0.21 | -0.02 |
| 5 | -0.0 · +10.7 · -1.6 · +10.7 | +8.6 · +9.1 · +21.5 | -0.23 | +0.00 |
| 10 | -0.0 · +13.5 · -1.1 · +13.5 | +14.3 · +19.9 · +31.1 | -0.21 | +0.07 |
| 20 | -0.0 · +19.1 · -3.3 · +19.1 | +15.1 · +36.6 · +28.3 | +0.04 | +0.21 |

| post-hoc LOOSE tag (fh < 0.8 x median, ER < 0.4; 175 tag days = 23% of days; ONE extra look, not in the prereg) | ΔmaxDD cut ALL $k | Δworst-20 ALL $k | ΔmaxDD cut L6M $k | beats % shuffled-tag (200): maxDD ALL / w20 ALL / maxDD L6M | beats % random-tag (200) |
|---|---|---|---|---|---|
| halve only | +24.6 | +11.7 | +0.5 | 92% / 48% / 85% | 88% / 58% / 88% |
| halve + fade (M) | +20.4 | +23.4 | +2.3 | 87% / 74% / 94% | 84% / 80% / 98% |

Reading: the pre-registered tag is too thin to move the stack (ALL maxDD cut 4%, worst-20 gain 1%); the looser tag is stronger (ALL maxDD cut 8.5%, L6M cut 10%) but is a second look, its L6M cut beats 94.5% / 98.5% of shuffled / random tags while its ALL gates are 74-87%, so neither passes the 95% bar on both. Treat the tag as a Shadow regime flag to log, not as a rule.

## 4. The other two stacks (3 lots) and equal-risk

Equal-risk = (stack + 3 lots) x c with c set so the ALL worst-20 equals the stack's (linear daily scaling, not an engine re-run), and the change in mean; the right-hand columns are the same add on the as-is stack (ALL maxDD 316k: the sleeves move it by -9.6k to +49.6k, C and D worsen it) and on the composite with the 12R week lock. Sign here: Δ = after - before for maxDD (negative = cut).

| sleeve | basis | equal-risk scale c (stack+3 lots, ALL worst-20 = stack's) | Δmean at c: L3M · L6M · HOLD · PRE · X' · ALL ($k/wk) | stack = as-is: ΔmaxDD ALL / Δworst-20 ALL (3 lots) | stack = composite+12R lock: ΔmaxDD ALL / Δworst-20 ALL |
|---|---|---|---|---|---|
| RVW1_F30_LMT | M | 1.026 | +1.11 · +1.41 · +1.51 · +1.40 · +0.60 · +1.21 | -4.9 / +25.0 | +1.3 / -3.8 |
| RVW1_F30_LMT | LC | 1.014 | +0.56 · +0.72 · +0.81 · +0.72 · +0.33 · +0.64 | -4.3 / +14.4 | +1.5 / -6.0 |
| A | M | 1.025 | +1.27 · +1.67 · +1.73 · +1.78 · +0.66 · +1.46 | -7.6 / +29.9 | +1.5 / -2.0 |
| A | LC | 1.020 | +0.75 · +1.21 · +1.29 · +1.44 · +0.51 · +1.15 | -5.4 / +27.2 | +4.5 / -9.4 |
| B | M | 1.011 | +0.45 · +0.20 · +0.14 · -0.21 · +0.21 · -0.01 | -9.6 / +9.6 | +3.8 / +3.0 |
| B | LC | 1.006 | +0.32 · +0.12 · +0.07 · -0.19 · +0.00 · -0.08 | -2.9 / +3.4 | +1.3 / +2.6 |
| C | M | 0.986 | +0.07 · -1.48 · -1.25 · -0.88 · -0.53 · -0.87 | +23.8 / -7.9 | +10.4 / -27.6 |
| C | LC | 0.988 | -0.63 · -1.33 · -1.15 · -0.79 · -0.53 · -0.80 | +20.9 / -9.4 | +10.0 / -19.2 |
| D | M | 0.989 | -0.60 · -1.85 · -1.69 · -0.25 · -1.22 · -0.85 | +40.3 / -7.7 | -5.0 / -25.7 |
| D | LC | 0.985 | -0.90 · -2.35 · -2.17 · -0.58 · -1.60 · -1.23 | +49.6 / -12.5 | -3.2 / -30.9 |
| E | M | 1.008 | +3.23 · +1.25 · +1.62 · +1.27 · +0.34 · +1.09 | -7.3 / +18.3 | -16.0 / -23.4 |
| E | LC | 1.007 | +3.12 · +1.11 · +1.48 · +1.16 · +0.26 · +0.98 | -4.6 / +16.7 | -15.2 / -25.2 |
| F | M | 1.008 | +0.95 · +0.52 · +0.60 · +0.36 · +0.07 · +0.33 | +8.2 / +8.4 | -2.0 / -13.6 |
| F | LC | 1.008 | +0.93 · +0.50 · +0.58 · +0.34 · +0.05 · +0.31 | +8.8 / +8.2 | -1.9 / -13.8 |

## 5. Fills, haircut, replication, caveats

- **Simulator.** NQ 1-min OHLC bars, ET, RTH only, 1,041 complete days (half days skipped), signals at a bar close and orders from the next bar, a same-bar stop/target tie is a stop, no target in the fill bar of a limit entry, $4.84 RT per contract, $20/point. M = market +0.25, target on touch, stop cost 1.28 pts, time exit slip 0.25. LIVE-CAL = market +0.50, target needs one tick through, stop cost 2.45 (the engine's join-stop figure), exit slip 0.50, and for limit-at-touch entries the **passive-fill haircut**: the fill needs a strict one-tick trade-through (the T-CLOSE harness rule), then only 60% of fills are kept (= live stop-join fill 8/17 = 0.47 over the replay's 0.78, T4.2_Y4 note, 0.60 rounded), NEUTRAL = random 60% averaged over 20 draws, ADVERSE = drop the best 40% of fills by P&L (RVW1 F30 limit ALL worst-20 gain at 3 lots: ADVERSE -25.5k vs +14.3k neutral and +27.8k at M). The limit price is the signal-bar close -/+ 0.125 (half a tick, the proxy for the bid/ask: no quote tape was used for these cells; the T-CLOSE harness used the real 1-s bid/ask for RVW1).
- **Replication.** RVW1 F30 (15:30, z>=1.0, 30/30, 1 lot) on this simulator earns 296/wk market and 204/wk limit (ALL); the T-CLOSE harness reported 214/wk and 133/wk per lot (M basis, WF 142 weeks) and a 577/621 limit fill rate (mine 681/726): the same trade count (~65% of days) but my means are 1.4-1.5x higher, so every own-mean here is the optimistic side and no conclusion depends on it. The disclosed pre-prereg sanity replication was this check.
- **Scale.** The sleeves are 3-8k of weekly SD against the stack's 50k; the lots table shows the worst-20 gain peaking near 10 lots for RVW1 (+64k M, +31k LC) and falling back at 20 lots (+46k M, +9k LC) as the sleeve's own tail takes over; E at 20 lots takes the L6M maxDD from 23k to 90k; capacity is 10 lots on the quote-based T edge and ~20 on the M edge at 15:30.
- **One episode.** The stack's ALL maxDD is the single PRE drawdown and L6M's is one week cluster; maxDD claims have an effective N of 1-2 episodes. The 2026-01-19 week check is in 2c.
- **Selection and multiplicity.** 40 sleeve cells + 18 chop-fade cells ranked once on PX; the per-family picks and the pre-named RVW1 F30 limit were looked at once across the windows; best-of-40 conditional t = 1.93. Romano-Wolf not run. The 8-day pattern in section 3 and the loose tag are post-hoc looks beside the prereg.
- **Close-fade (family F).** The standalone book that fades the stack's own 14:40-15:00 signals (the INST-B finding: those signals are followed by -13 to -24 pts sided into 15:50/16:00, 3-5 SE) trades only 60 days in 3 years; per lot it earned +165 a week in the stack's 20 worst weeks vs +28 elsewhere (difference +137, CI -129 to +481) and 80% of that 20-week P&L is one week. The unconditional close-fade (fade the 14:40-15:00 move, 1,037 trades) worsens the stack tail (selection score -0.05 / -0.06, the last two of 40 on PX).

## 6. D7 / D6 specs (Shadow only; NT8 1-minute NQ bars, OnBarClose, ET; nothing is live)

- **A* RVW1 F30 limit-at-touch (15:30, z>=1.0, 30/30) [pre-named]**: NQ 1-min chart, OnBarClose, ET, RTH only (skip half days). Series from 09:30 bars: tp=(H+L+C)/3, VWAP=cum(tp*vol)/cum(vol), dev=Close-VWAP, sigma=expanding population std of dev. At the CLOSE of the 15:29 bar (15:30:00) z=dev/sigma; if |z|>=1.0 place a LIMIT at the best bid (long, z<=-1) / best ask (short, z>=+1), 1 lot (shadow), live 300 s, cancel 15:35:00 if unfilled. On fill: OCO target +30 / stop -30 pts from the fill; else MARKET flat 16:00:00 (submit at the 15:59 bar close). Exact spec = DS3_SPEC_RVW1_F30.md v2.
- **A  RVW1 F30 market (15:30, z>=1.0, 30/30)**: As RVW1 F30 but MARKET order at the 15:30:00 bar open (needs a fill at the open; a 1-s delay turns the T-CLOSE HOLD edge negative), OCO +30/-30 from fill, flat 16:00:00.
- **B  VWAP-band fade (z>=2.0, limit, T20/S30, 10:30-14:30)**: NQ 1-min, OnBarClose, ET. VWAP/dev/sigma as RVW1. From the 10:30 bar close to the 14:29 bar close, the FIRST bar with |z|>=2.0 triggers (one trade/day): LIMIT at best bid/ask toward VWAP (long if z<=-2), live 300 s; OCO target +20 / stop -30 from fill; MARKET flat 15:50:00. Session 10:30-15:50 ET.
- **C  IB-edge fade (limit at edge, S25, target IB mid)**: NQ 1-min, ET. IB = high/low of the 09:30-10:29 bars. At 10:30 place an OCO pair: SELL LIMIT at IB high, BUY LIMIT at IB low (cancel the other on fill; cancel both 14:30). On fill: stop 25 pts beyond the IB edge (initial risk 25), target = IB midpoint (minimum 8 pts from the fill), MARKET flat 15:50:00. Fill rule used in research: strict 1-tick trade-through.
- **D  failed-breakout fade (IB, B3, target IB mid)**: NQ 1-min, OnBarClose, ET. IB as above. From 10:30 to 14:30: a bar whose extreme is >= IB edge +3 pts, followed within 5 bars by a CLOSE back inside the IB, fires the FADE at the next bar open (market, toward the inside); stop = excursion extreme +-2 pts (skip if > 40 pts away), target = IB midpoint (min 8 pts), flat 15:50:00. One trade/day (first).
- **E  prior-VA 80% rule (X40, target opposite edge)**: NQ 1-min, ET. Prior RTH day (09:30-15:59) 70% value area: 1-pt bins of typical price weighted by volume, expanded from the POC by the larger neighbour; VAH=top of upper bin, VAL=bottom of lower bin. If the 09:30 open is above VAH (below VAL), the FIRST 1-min close back inside the VA from 09:35 to 13:00 fires a market order toward the opposite edge at the next bar open; stop 40 pts beyond the re-entry edge, target = opposite edge (min 8 pts away), flat 15:50:00.
- **F  close-fade standalone (fade stack signals 14:40-15:00, flat 16:00)**: Needs the D6 signal log: at 15:00:00 ET sum side*lots over the stack's trades ENTERED 14:40-15:00 ET (all books; the composite's taken signals); if nonzero place a MARKET order for the OPPOSITE side (shadow 1 lot) at the 15:00 bar open, no stop, MARKET flat 16:00:00. Only ~60 days in 3 years trigger.
- **CHOP-DAY tag (D6 policy line, shadow log only)**: at 10:30:00 ET log tag = (09:30-10:29 high-low) < 0.6 x median of the previous 20 days' same range AND ER(5-min closes 09:30..10:30; |net|/sum|step|, 12 steps) < 0.3; log the stack's rows entering after 10:30 with the flag so the x0.5 ER multiplier can be priced forward; and the fade sleeve "B z1.5 market" (VWAP-band fade, first bar 10:30-14:30 with |z|>=1.5 toward VWAP, target 30 / stop 30, flat 15:50) at 1 lot on tag days only.

## 7. Assembly (C2 appends here; do not overwrite)

C2 writes `autopilot/DS3_HEDGE_ASSEMBLY.md` (S8 RTY, B1 BTC, Q1CCO NQ, GC sleeve audit and the stack's worst-20 with it added). The section below is C2's.

