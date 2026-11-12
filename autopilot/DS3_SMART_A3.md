# DS3_SMART_A3 — T-SMART item A3: structure stops with equal-$ lots (W-SM3)

Generated 2026-11-12 19:38Z UTC. Exact engine, one set per job (TP engine), base JN05W2 = live panel + F3 + E1 + C22 + BR3S + FLAT45K (JN05W2J = same on JN04RM). Shadow only, no PASS claim.

**CAVEAT (every table):** the engine state cut fires in the engine but did NOT fire live on 2026-11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). Rows marked **S0 = state cut OFF = the live-realistic case** are read first and compared with SMA3_REF_S0 (JN05W2 with every state cut switched off, K7 flat45 kept); **S1** rows keep the state cut and compare with JN05W2.

Hook th_smart/sm_hooks.py (copy of W-X ec_hooks, features fr1/fr3/fr5/fr15 = confirmed 2-2 fractal pivot of the 1/3/5/15-min bars, so = session open, sx = running session extreme, kc = Keltner mid EMA20 of 5-min closes, st = Supertrend, vwap = session VWAP): structure stop at the level - buf, exit filled 1.4 pt adverse (live native central; WORKED stop = market exit at the decision second, the native 60 and 80 catastrophe stops stay as backstops), lots x 60/se (se = distance to the stop clamped 25..60 pts, so up to x2.4) applied after the live sizers, then the day caps and locks apply to those lots. Prereg autopilot/SMART_A3_PREREG.md. Name SMA3_<feat><buf>_<books>_<S0|S1>[J].

Dead-cell lookup (loss|struct_stop_eq|<book>|<feat>, 32 specs): 0 hits; first-order evidence from W-X fo_a.parquet (LPB): only U7 kc buf2 (+17.7% L6M cut, +$717/wk) and K7 vwap buf6 (+9.4%, +$919) were positive; P7 / H7 / M7 / A7 structure stops were null or negative.

## 0. Trend-week clause first, then L6M / HOLD (a window appears only when all its months are present)

| set | months | reference | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | HOLD cut % | HOLD d mean/wk | PRE cut % | X' cut % | GAP cut % | WF cut / beat |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SMA3_FR154_K_S1 | 2 | JN05W2 | (running) ||||||||||
| SMA3_FR156_K_S0 | 2 | SMA3_REF_S0 | (running) ||||||||||
| SMA3_KC2_U_S0 | 3 | SMA3_REF_S0 | (running) ||||||||||
| SMA3_KC2_U_S1 | 1 | JN05W2 | (running) ||||||||||
| SMA3_KC4_U_S0 | 1 | SMA3_REF_S0 | (running) ||||||||||
| SMA3_KU_S0 | 2 | SMA3_REF_S0 | (running) ||||||||||
| SMA3_REF_S0 | 1 |  | (reference) ||||||||||

cut % = stack maxDD vs the reference (positive = shallower); d mean = all-weeks mean difference ($/wk, carry week kept); WF = bi-weekly re-pick walk-forward (only with all 43 months).

## 1. Per book, L6M (cell vs its reference): trades, mean lots, d net $/wk, full stops per wk, EarlyCut (structure-stop) exits per wk, StateCut exits per wk

## 2. acceptance_p7 (L6M only, fail on > 2 of 20) for complete L6M cells with L6M cut >= 5%


## 3. Transfer to the user lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75)

The structure-stop lots rule is a ratio (60/se, se 25..60), so the equal-$ risk property is lot-independent; at the user lots the rounding matters less (cell lots K7/M7/A7 are 1-3, so x2.4 rounds up to 2-7) and every day cap / lock scales x1.75 with the lots, so the cap-binding days move with it. R is the book stop x $20 x lots (60 pt x $20 = $1,200 per lot). These pages are at the cell lots; a user-lots rerun is queued only for cells that survive (stage 2).
