> **FIRST-ORDER SCREEN ONLY: every number on this page that is not in the "Exact-engine status" table is a first-order screen (pnl per planned lot x new lots, realized-only state); it is NOT a verdict (Addendum 1). Exact-engine rows: six finalists, L6M then PRE, X', HOLD.**

> **TESTING DEFECT FOUND AND FIXED (Addendum 1 c).** The identical-to-the-dollar test between bases flagged 4 cells (D consec_loss, stack level, f=0, k=2..5): maxDD 0 on every base. Cause: my rule's loss counter reset only after a win, so a book or stack that was skipped could never trade or win again (permanent lock-out, all P&L 0 from the first trigger on). It was a rule-semantics bug, not a cached trade list: base lists differ (see base-change proof below). Fix (DECISIONS.md line at 16:2xZ): consecutive-loss and consecutive-win counters reset at the label-day roll. All three bases and this page were re-scored after the fix; the re-run check result is the first line of the base-comparison section.

> **ROLL-EXCL (lead 17:35Z): every first-order and exact number on this page excludes the 31 base trades (of the 33 listed in roll_bracket_trades.csv; 2 listed rows are not in the COMB list) alive across a contract roll (key book + entry second +-2 s); their P&L is zeroed before state and scoring. Engine-internal state of the exact runs (lock/cooldown/equity states) still saw those artifact P&L jumps; the 14 roll days are checked in the lock/cooldown exact runs on the R1 page.**

# SZ-CDE - families C (parity), D (equity-curve/state/locks), E (exposure), K slice (P7)  - 2026-11-09 17:37Z

**Label: first-order on base S1b-COMB (live D7 v1.5 with the seven state-cut lines), 21135 trades 2023-04..2026-10 (last label day 20261030; the 2026-11-01..05 live weeks are not in the list, so L1M/L2M/L3M windows end 2026-10-30); entries not live-matched; in-sample; PRE-PROOF; post-hoc; Shadow only; no PASS claims.** Reference = Q1-A (the base lots). 3274 cells (C 140, D 1980, E 1110, K 44). Prereg: autopilot/SZ_CDE_PREREG.md (sha in DECISIONS.md).

Reading guide: (a) = cell vs Q1-A at equal lots (maxDD cut % = positive is shallower; d mean $/wk L6M). (b) = every cell scaled by one global factor so its L6M mean equals Q1-A (0 $/wk), then maxDD / worst-20 / Ulcer cut vs Q1-A; size-down-everything scores 0 by construction. Class A = lots-only static (first-order valid); B = skips/state (ranking valid, mean not, exact re-run needed for re-entries); C = lock/give-back/week-floor (engine marks open P&L and flattens: first-order is a skip-only proxy ON TOP of the base that already holds the live locks; loosened values and StackCutPct x sessions are exact-driver only). State for D/E = realized P&L of cell-sized trades with exit < signal second (open P&L not in any state). Placebo = donor multipliers reassigned to random trades in the same book x session (100 draws; stat = min of (b) cut over L6M, PRE, X'). Family p = max over the whole CDE set (3274 cells) per draw. WF = monthly 2024-01..2026-10, 26 trailing weeks, 7-day embargo, picks the best trailing equal-mean maxDD cell, OOS maxDD cut at equal mean shown per family.

## Headline

- Cells on the bar (CANDIDATE-DD, first-order, all still need the EXACT engine): 0; LEADs (equal-mean maxDD lower on L6M, PRE and X' with placebo p<=.10 but another gate fails): 269. Cells that dominate Q1-A on BOTH mean and maxDD (L6M, HOLD, PRE; down-only): 289.

- WF of the picking procedure (OOS 2024-01..2026-10, 148 weeks): ALL_CDEK: OOS maxDD cut +16% raw / -35% at equal mean (d mean -6331 $/wk); C: OOS maxDD cut +32% raw / +0% at equal mean (d mean -5217 $/wk); D: OOS maxDD cut +36% raw / +16% at equal mean (d mean -4086 $/wk); E: OOS maxDD cut +31% raw / -1% at equal mean (d mean -5231 $/wk); K: OOS maxDD cut +27% raw / +15% at equal mean (d mean -2306 $/wk); D_state_only: OOS maxDD cut +36% raw / +16% at equal mean (d mean -3996 $/wk); E_ALL_scope: OOS maxDD cut +14% raw / -32% at equal mean (d mean -5771 $/wk); D_ALL_scope: OOS maxDD cut +20% raw / -14% at equal mean (d mean -4941 $/wk).

- Live week (frozen file, 180 DS7-book trades): Q1-A total +104810, trade-level maxDD $14,490; the week has no stack losing day, so it cannot separate cells; columns show d total and d trade-level dd vs Q1-A.

- Family C best (down-only, ranked by the joint equal-mean cut): riskcap_per_trade R$3600 on scope P7 cuts L6M maxDD 37% at equal lots (d mean -7611 $/wk) and 15% / 17% / 20% at equal mean on L6M / PRE / X'; placebo p 0.01, family p 1.00; family WF OOS equal-mean cut +0%; LEAD (w20 fails).
- Family D best (down-only, ranked by the joint equal-mean cut): eqdd_stack_20d Y10000_f0.50_sticky on scope ALL cuts L6M maxDD 44% at equal lots (d mean -7414 $/wk) and 25% / 24% / 30% at equal mean on L6M / PRE / X'; placebo p 0.01, family p 0.53; family WF OOS equal-mean cut +16%; LEAD (w20 fails).
- Family E best (down-only, ranked by the joint equal-mean cut): max_books_on n1_f0.5 on scope sess_london cuts L6M maxDD 27% at equal lots (d mean +145 $/wk) and 28% / 26% / 17% at equal mean on L6M / PRE / X'; placebo p 0.09, family p 0.98; family WF OOS equal-mean cut -1%; LEAD (w20 fails WF-family fails).
- Family K best (down-only, ranked by the joint equal-mean cut): P7_lots_by_session L4_nyam on scope P7 cuts L6M maxDD 7% at equal lots (d mean +1860 $/wk) and 12% / 13% / 18% at equal mean on L6M / PRE / X'; placebo p 0.04, family p 1.00; family WF OOS equal-mean cut +15%; LEAD (w20 fails).


## C. Equal-risk / parity

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 128 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+32.1/+39.0/+40.5 | -19.0/-31.9 | +19.0 | -7611 | +15.4 | +15.4/+17.5/+19.5 | 22.45 | 0.19 | 0.01 | 1.00 | +0.3 | -40358 / -3076.2 | A | LEAD (w20 fails) |
| riskcap_per_trade | R$2400 | P7 | +44.2/+45.3/+48.3/+56.9 | -0.6/-42.3 | +14.0 | -10997 | +10.4 | +10.4/+17.1/+30.8 | 21.20 | 0.21 | 0.02 | 1.00 | +0.3 | -54807 / -1390.8 | A | LEAD (w20 fails) |
| volparity_down | win120_refmin | M7 | +2.0/+3.4/+3.6/+1.9 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+2.9 | 19.59 | 0.03 | 0.02 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| riskcap_per_trade | R$3600 | ALL | +31.0/+34.2/+42.1/+49.8 | -7.9/-32.9 | +11.6 | -8566 | +2.3 | +2.3/+18.0/+29.0 | 19.44 | 0.22 | 0.01 | 1.00 | +0.3 | -38377 / -5021.2 | A | LEAD (w20 fails) |
| esparity_down | last100tr_refmin | M7 | +2.0/+3.4/+3.6/+0.6 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.59 | 0.03 | 0.02 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| esparity_down | last200tr_refmin | M7 | +2.0/+3.4/+3.6/+0.6 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.59 | 0.03 | 0.07 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| esparity_down | last50tr_refmin | M7 | +2.0/+3.4/+3.6/+0.6 | -6.0/-3.4 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.59 | 0.03 | 0.07 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| volparity_down | win60_refmin | M7 | +2.0/+3.4/+3.6/+0.3 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.3 | 19.59 | 0.03 | 0.05 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| volparity_down | win20_refmin | M7 | +2.0/+3.4/+3.6/-0.4 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+0.6 | 19.59 | 0.03 | 0.19 | 1.00 | +0.3 | na / na | A | dd-only (placebo p 0.19) |
| esparity_down | last50tr_refmed | K7 | +0.1/+0.0/+0.0/+0.0 | -1.1/+0.0 | +1.0 | +105 | +0.5 | +0.5/+0.4/+0.4 | 19.09 | 0.00 | 0.01 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| riskcap_per_trade | R$3600 | M7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +0.3 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | O7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +0.3 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | A7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +0.3 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | K7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +0.3 | +0 / +0.0 | A | no |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+32.1/+39.0/+40.5 | -19.0/-31.9 | +19.0 | -7611 | +15.4 | +15.4/+17.5/+19.5 | 22.45 | 0.19 | 0.01 | 1.00 | +0.3 | -40358 / -3076.2 | A | LEAD (w20 fails) |
| volparity_down | win120_refmin | M7 | +2.0/+3.4/+3.6/+1.9 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+2.9 | 19.59 | 0.03 | 0.02 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |
| esparity_down | last100tr_refmin | M7 | +2.0/+3.4/+3.6/+0.6 | -6.0/-3.5 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.59 | 0.03 | 0.02 | 1.00 | +0.3 | na / na | A | LEAD (w20 fails) |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| volparity_up | win60_refmed_clip.5-1.5 | ALL | +35.0/+28.9/+45.3/+21.0 | -1.7/-36.6 | +27.0 | -6463 | +16.5 | +16.5/+29.7/-1.5 | 22.76 | 0.39 | 0.30 | 1.00 | +0.3 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$2400(up-allowed) | ALL | +14.6/+15.0/+39.1/+58.6 | -8.4/-28.6 | +8.4 | -5172 | -3.8 | -3.8/+26.0/+49.7 | 18.30 | 0.85 | 0.03 | 1.00 | +0.3 | -31394 / -4663.6 | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$3600(up-allowed) | ALL | -26.5/-29.0/+8.5/+41.3 | -64.5/+6.4 | +4.4 | +5143 | -7.6 | -7.6/+22.2/+50.1 | 17.66 | 0.98 | 0.01 | 1.00 | +0.3 | +5643 / +597.1 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmed_clip.5-1.5 | ALL | +33.9/+33.5/+48.7/+39.9 | +11.4/-36.4 | -9.1 | -11625 | -9.9 | -9.9/+14.7/+0.2 | 17.29 | 0.39 | 0.43 | 1.00 | +0.3 | na / na | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmin_clip.5-1.5 | ALL | +47.5/+43.9/+43.3/+52.7 | +26.1/-42.1 | +1.2 | -14157 | -1.9 | -1.9/-10.0/+8.2 | 18.63 | 0.39 | 0.29 | 1.00 | +0.3 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$1200(up-allowed) | ALL | +58.9/+56.0/+69.3/+80.2 | +44.2/-64.9 | -2.8 | -18661 | -13.9 | -13.9/+15.0/+45.0 | 16.67 | 0.42 | 0.06 | 1.00 | +0.3 | -67772 / -9229.3 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win120_refmed_clip.5-1.5 | ALL | +35.5/+32.1/+36.7/+25.1 | +2.5/-33.9 | +3.9 | -10863 | -2.7 | -2.7/-0.8/-19.2 | 18.50 | 0.39 | 0.50 | 1.00 | +0.3 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$6000(up-allowed) | ALL | -111.9/-114.0/-52.4/-0.1 | -172.9/+77.8 | -8.7 | +21242 | -22.7 | -22.7/+11.8/+42.1 | 15.49 | 0.99 | 0.01 | 1.00 | +0.3 | +79059 / +10423.6 | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$8400(up-allowed) | ALL | -197.4/-199.0/-113.2/-41.5 | -281.4/+149.2 | -8.9 | +41335 | -23.1 | -23.1/+11.7/+41.4 | 15.43 | 0.93 | 0.04 | 1.00 | +0.3 | +152474 / +20250.0 | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$4800(up-allowed) | ALL | -70.8/-70.0/-21.7/+17.2 | -116.9/+42.7 | -9.5 | +10995 | -24.1 | -24.1/+11.6/+39.8 | 15.31 | 0.86 | 0.02 | 1.00 | +0.3 | +42021 / +5162.9 | A | UP-ALLOWED report row (never promoted) |


## D. Equity-curve / state / locks (down-only ranked; up-allowed and anti-martingale in the report rows below)

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1966 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_20d | Y10000_f0.50_sticky | ALL | +44.3/+43.9/+43.3/+48.1 | +24.7/-38.2 | +25.0 | -7414 | +25.3 | +25.3/+24.0/+30.5 | 25.43 | 0.30 | 0.01 | 0.53 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | ALL | +46.6/+40.8/+44.6/+47.4 | +24.8/-40.5 | +26.1 | -8363 | +25.1 | +25.1/+22.3/+26.3 | 25.37 | 0.33 | 0.01 | 0.70 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y4R_f0.25_sticky | P7 | +30.3/+41.6/+44.9/+53.2 | +16.9/-40.0 | +28.4 | -4029 | +19.1 | +19.1/+36.1/+45.8 | 23.48 | 0.17 | 0.01 | 0.92 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y4R_f0.25_sticky | ALL | +44.3/+40.7/+51.1/+39.4 | +38.8/-50.1 | +34.1 | -7804 | +24.0 | +24.0/+33.3/+17.3 | 24.98 | 0.29 | 0.01 | 0.97 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y2R_f0.25_sticky | P7 | +38.3/+41.6/+44.9/+58.7 | +29.6/-43.7 | +24.7 | -7597 | +16.6 | +16.6/+25.5/+44.1 | 22.77 | 0.20 | 0.01 | 0.99 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | P7 | +32.7/+35.7/+30.2/+41.6 | +13.8/-30.1 | +19.7 | -5171 | +18.2 | +18.2/+15.2/+29.0 | 23.22 | 0.19 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y30000_f0.50_sticky | ALL | +32.1/+43.9/+43.3/+40.1 | +24.7/-32.8 | +11.1 | -5954 | +14.8 | +14.8/+28.8/+24.7 | 22.29 | 0.26 | 0.07 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| week_loss_book_R | X2R_f0.00 | P7_sess_london | +10.1/+15.9/+27.9/+11.8 | -16.1/-15.2 | +18.5 | +1072 | +13.3 | +13.3/+30.4/+14.9 | 21.92 | 0.01 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y30000_f0.25_sticky | sess_nyam | +7.9/+16.4/+11.3/+21.9 | -17.6/-5.8 | +18.1 | +1638 | +12.8 | +12.8/+16.0/+26.1 | 21.79 | 0.03 | 0.04 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_london | +29.8/-25.1/+43.4/+12.8 | -16.3/-23.4 | +27.2 | -47 | +29.6 | +29.6/+43.3/+12.7 | 27.00 | 0.10 | 0.04 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | P7_sess_nyam | +9.9/+16.4/+11.3/+23.5 | -7.6/-7.7 | +15.7 | +694 | +12.0 | +12.0/+13.4/+25.3 | 21.59 | 0.03 | 0.06 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/+14.7/+7.4/+10.8 | -22.3/-5.3 | +20.9 | +1478 | +17.3 | +17.3/+11.9/+15.1 | 22.98 | 0.03 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.50_sticky | sess_london | +22.3/-3.3/+38.8/+10.7 | -14.1/-19.5 | +23.0 | +267 | +23.0 | +23.0/+39.3/+11.6 | 24.68 | 0.10 | 0.05 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | P7_sess_london | +11.1/+7.9/+24.5/+8.7 | -17.2/-14.9 | +18.9 | +922 | +13.9 | +13.9/+26.9/+11.5 | 22.05 | 0.06 | 0.04 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_20d | Y10000_f0.50_sticky | ALL | +44.3/+43.9/+43.3/+48.1 | +24.7/-38.2 | +25.0 | -7414 | +25.3 | +25.3/+24.0/+30.5 | 25.43 | 0.30 | 0.01 | 0.53 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | ALL | +46.6/+40.8/+44.6/+47.4 | +24.8/-40.5 | +26.1 | -8363 | +25.1 | +25.1/+22.3/+26.3 | 25.37 | 0.33 | 0.01 | 0.70 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| week_loss_book_R | X2R_f0.00 | P7_sess_london | +10.1/+15.9/+27.9/+11.8 | -16.1/-15.2 | +18.5 | +1072 | +13.3 | +13.3/+30.4/+14.9 | 21.92 | 0.01 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/+14.7/+7.4/+10.8 | -22.3/-5.3 | +20.9 | +1478 | +17.3 | +17.3/+11.9/+15.1 | 22.98 | 0.03 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| lock_giveback | arm1.5R_keep0.7(live2/.5) | ALL | +5.4/+0.5/+31.2/-0.0 | -16.3/-14.3 | +14.9 | +2242 | +12.1 | +12.1/+36.1/+7.1 | 21.61 | 0.02 | 0.04 | 1.00 | +15.7 | -16500 / -1800.0 | C | LEAD (w20 fails) |
| lock_daycap_loss | loss1R(live2) | P7 | +25.7/+8.2/+17.0/+6.1 | -22.5/-9.8 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.3 | 25.61 | 0.04 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | C | LEAD (w20 fails) |
| dayloss_book_R | X1.0R_f0.00 | P7 | +25.7/+8.2/+17.0/+6.1 | -22.5/-9.8 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.3 | 25.61 | 0.04 | 0.06 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| consec_loss | book_k4_f0.00 | P7 | +8.9/+13.0/+30.9/+0.0 | -23.6/-7.7 | +23.3 | +1680 | +13.9 | +13.9/+34.7/+5.4 | 22.05 | 0.01 | 0.04 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| week_loss_stack | X30000_f0.00 | sess_london | +9.4/-9.8/+34.8/+0.9 | -19.3/-16.2 | +23.3 | +1293 | +13.2 | +13.2/+37.5/+5.1 | 21.89 | 0.03 | 0.05 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| lock_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | +0.0/+0.0/+0.0/+0.0 | -4.7/-0.4 | +6.5 | +1107 | +3.7 | +3.7/+3.7/+3.7 | 19.72 | 0.00 | 0.02 | 1.00 | +15.7 | -43695 / -3560.0 | C | LEAD (w20 fails) |
| week_profit_protect_stack | X60000_f0.50 | P7 | +0.0/+0.0/+0.0/+0.0 | -9.8/+0.0 | +2.9 | +869 | +2.9 | +2.9/+2.9/+2.9 | 19.56 | 0.01 | 0.04 | 1.00 | +15.7 | -9235 / +0.0 | B | LEAD (w20 fails) |
| lock_daycap_win | win4R(live5) | A7 | +0.0/+0.0/+0.0/+0.0 | -0.3/+0.0 | +0.1 | +29 | +0.1 | +0.1/+0.1/+0.1 | 19.02 | 0.00 | 0.19 | 1.00 | +15.7 | +0 / +0.0 | C | dd-only (placebo p 0.19) |
| lock_weekfloor | floor16R(live12) | M7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | C | no |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| antimartingale_UP | book_n4_x1.25 | ALL | +0.0/-0.8/-0.6/-0.9 | -1.7/+0.1 | -1.6 | -54 | -0.2 | -0.2/-0.7/-1.1 | 18.96 | 0.01 | 0.09 | 1.00 | +15.7 | +0 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n4_x1.50 | ALL | +4.0/-0.8/-0.3/-1.9 | +1.1/-0.2 | -0.4 | -300 | +3.0 | +3.0/-1.4/-2.9 | 19.58 | 0.02 | 0.09 | 1.00 | +15.7 | -655 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| eqdd_stack_UP_at_high | Y20000_f0.50_up1.25 | ALL | +35.8/+38.8/+40.5/-2.9 | +32.1/-27.8 | +12.5 | -4856 | +22.9 | +22.9/+28.6/-23.5 | 24.65 | 0.29 | 0.46 | 1.00 | +15.7 | +25118 / +5079.1 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.50 | ALL | +4.7/-2.3/-5.5/-5.4 | -8.4/+2.6 | -16.3 | -5268 | -16.3 | -16.3/-28.8/-28.6 | 16.33 | 0.04 | 0.42 | 1.00 | +15.7 | -3448 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.25 | ALL | -3.3/-0.8/-2.4/-1.4 | -1.5/+1.2 | -31.3 | -6208 | -31.3 | -31.3/-30.1/-28.9 | 14.47 | 0.02 | 0.63 | 1.00 | +15.7 | -2651 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.25 | ALL | -12.8/+0.9/-9.7/-6.0 | +2.3/+4.9 | -41.8 | -6002 | -42.0 | -42.0/-38.1/-33.5 | 13.38 | 0.06 | 0.76 | 1.00 | +15.7 | -1210 / +1860.0 | B | UP-ALLOWED report row (never promoted) |
| eqdd_stack_UP_at_high | Y45000_f0.50_up1.25 | ALL | -13.1/+9.2/+34.9/-24.2 | +33.8/-14.7 | -43.4 | -4080 | -31.5 | -31.5/+24.3/-44.3 | 14.45 | 0.19 | 0.81 | 1.00 | +15.7 | +25118 / +5079.1 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n4_x1.25 | ALL | -13.0/-3.6/-6.4/-19.9 | +6.6/+2.9 | -44.7 | -6487 | -45.3 | -45.3/-36.9/-54.2 | 13.08 | 0.05 | 0.99 | 1.00 | +15.7 | -1085 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.50 | ALL | -31.7/-5.7/-20.8/-11.8 | +0.2/+9.8 | -55.2 | -5150 | -59.9 | -59.9/-46.6/-35.7 | 11.88 | 0.12 | 0.69 | 1.00 | +15.7 | -5591 / +3720.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n3_x1.25 | ALL | -24.4/-0.4/-5.1/-20.8 | +19.9/+6.0 | -69.9 | -7184 | -65.0 | -65.0/-39.4/-60.2 | 11.52 | 0.08 | 0.97 | 1.00 | +15.7 | +707 / +0.0 | B | UP-ALLOWED report row (never promoted) |


## E. Exposure / concentration

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1110 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| max_books_on | n1_f0.5 | sess_london | +27.5/-18.2/+25.6/+16.9 | -11.7/-18.9 | +27.6 | +145 | +27.8 | +27.8/+26.0/+17.3 | 26.32 | 0.13 | 0.09 | 0.98 | -1.1 | +7051 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+37.1 | -27.3/-3.5 | +26.2 | +2318 | +19.3 | +19.3/+12.6/+41.8 | 23.54 | 0.03 | 0.01 | 1.00 | -1.1 | +715 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+42.8 | -26.1/-5.2 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+47.0 | 23.53 | 0.02 | 0.01 | 1.00 | -1.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+41.4 | -26.1/-4.6 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+45.7 | 23.53 | 0.02 | 0.02 | 1.00 | -1.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+39.3 | -26.5/-4.6 | +25.7 | +2240 | +19.1 | +19.1/+12.4/+43.6 | 23.49 | 0.02 | 0.02 | 1.00 | -1.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | ALL | +41.1/+49.0/+44.8/+59.1 | -1.1/-41.5 | +43.6 | -9667 | +11.9 | +11.9/+17.5/+38.8 | 21.57 | 0.15 | 0.01 | 1.00 | -1.1 | -53550 / -4440.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_trunc | sess_london | +19.8/+15.6/+26.7/+10.6 | -12.4/-16.2 | +22.3 | +431 | +21.0 | +21.0/+27.7/+11.9 | 24.04 | 0.10 | 0.04 | 1.00 | -1.1 | +10545 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| max_books_on | n1_f0.5 | P7_sess_london | +11.1/+1.1/+10.6/+10.7 | -10.5/-12.5 | +17.9 | +102 | +11.4 | +11.4/+10.9/+11.1 | 21.44 | 0.06 | 0.05 | 1.00 | -1.1 | +4500 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap8_skip | sess_london | +10.2/+18.4/+8.4/+8.5 | -9.7/-11.7 | +16.9 | +804 | +12.6 | +12.6/+10.8/+11.0 | 21.73 | 0.05 | 0.02 | 1.00 | -1.1 | +7590 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_trunc | P7_sess_london | +10.9/+10.2/+15.5/+10.7 | -4.3/-9.3 | +13.8 | -38 | +10.8 | +10.8/+15.4/+10.6 | 21.30 | 0.04 | 0.03 | 1.00 | -1.1 | +1921 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7 | +34.2/+42.0/+47.2/+48.3 | -9.7/-38.1 | +42.4 | -8070 | +9.1 | +9.1/+27.0/+28.6 | 20.90 | 0.10 | 0.01 | 1.00 | -1.1 | -57130 / -3830.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap4_trunc | sess_london | +33.7/-4.3/+46.5/+10.8 | -6.0/-29.1 | +32.2 | -729 | +32.0 | +32.0/+45.1/+8.5 | 27.95 | 0.16 | 0.12 | 1.00 | -1.1 | +12842 / +0.0 | B | dd-only (placebo p 0.12) |
| corr_same_side | N60min_f0.5_ge1_others | P7_sess_london | +14.9/+7.1/+15.9/+15.5 | +8.5/-13.6 | +7.8 | -2075 | +8.4 | +8.4/+9.5/+9.0 | 20.73 | 0.05 | 0.11 | 1.00 | -1.1 | +1193 / +0.0 | B | dd-only (placebo p 0.11) |
| total_lots_cap | cap6_skip | ALL | +41.1/+52.4/+45.1/+45.7 | +7.1/-39.5 | +39.9 | -10461 | +8.2 | +8.2/+14.4/+15.4 | 20.69 | 0.18 | 0.02 | 1.00 | -1.1 | -52835 / -4440.0 | B | LEAD (w20 fails WF-family fails) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| max_books_on | n1_f0.5 | sess_london | +27.5/-18.2/+25.6/+16.9 | -11.7/-18.9 | +27.6 | +145 | +27.8 | +27.8/+26.0/+17.3 | 26.32 | 0.13 | 0.09 | 0.98 | -1.1 | +7051 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+37.1 | -27.3/-3.5 | +26.2 | +2318 | +19.3 | +19.3/+12.6/+41.8 | 23.54 | 0.03 | 0.01 | 1.00 | -1.1 | +715 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+41.4 | -26.1/-4.6 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+45.7 | 23.53 | 0.02 | 0.02 | 1.00 | -1.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| corr_same_side | N60min_f0.5_ge1_others | P7_sess_london | +14.9/+7.1/+15.9/+15.5 | +8.5/-13.6 | +7.8 | -2075 | +8.4 | +8.4/+9.5/+9.0 | 20.73 | 0.05 | 0.11 | 1.00 | -1.1 | +1193 / +0.0 | B | dd-only (placebo p 0.11) |
| newentry_haircut_day_dd | Y3000_f0.0 | K7 | +12.9/-1.2/+9.3/+8.4 | +6.9/-5.9 | +3.8 | -1367 | +8.6 | +8.6/+4.8/+3.9 | 20.78 | 0.19 | 0.02 | 1.00 | -1.1 | -15095 / -1220.0 | B | LEAD (w20 fails WF-family fails) |


## K. P7 specific

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 44 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lots_by_session | L4_nyam | P7 | +6.7/+13.1/+7.5/+12.5 | -23.5/-3.4 | +17.1 | +1860 | +12.3 | +12.3/+13.1/+17.7 | 21.65 | 0.04 | 0.04 | 1.00 | +15.0 | -6197 / +0.0 | A | LEAD (w20 fails) |
| P7_lots_by_session | L3_nyam | P7 | +6.9/+12.7/+7.5/+11.1 | -20.4/-3.9 | +15.3 | +1060 | +10.2 | +10.2/+10.7/+14.2 | 21.15 | 0.05 | 0.16 | 1.00 | +15.0 | -9798 / +48.3 | A | dd-only (placebo p 0.16) |
| P7_lots_by_session | L4_london | P7 | +16.5/+5.5/+26.1/+10.2 | -4.7/-15.8 | +16.4 | -360 | +15.4 | +15.4/+25.1/+9.1 | 22.46 | 0.06 | 0.08 | 1.00 | +15.0 | +1193 / +0.0 | A | LEAD (w20 fails) |
| P7_lots_by_session | L6_all | P7 | +12.7/+19.3/+14.8/+20.2 | -4.4/-12.7 | +13.6 | -1536 | +7.9 | +7.9/+10.1/+15.8 | 20.63 | 0.18 | 0.01 | 1.00 | +15.0 | -12046 / -1882.7 | A | LEAD (w20 fails) |
| P7_lots_by_session | L5_london | P7 | +9.3/+3.1/+15.6/+8.5 | -1.1/-9.6 | +8.3 | -297 | +8.4 | +8.4/+14.7/+7.6 | 20.73 | 0.06 | 0.06 | 1.00 | +15.0 | -225 / +0.0 | A | LEAD (w20 fails) |
| P7_lots_by_session | L6_nyam | P7 | +4.6/+6.1/+3.8/+7.1 | -12.9/-1.9 | +9.1 | +1126 | +8.2 | +8.2/+7.4/+10.6 | 20.69 | 0.03 | 0.01 | 1.00 | +15.0 | -1898 / +0.0 | A | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N30min_f0.0 | P7 | +2.7/+6.5/+4.4/+8.9 | -7.0/-3.9 | +9.3 | +843 | +5.4 | +5.4/+7.1/+11.4 | 20.09 | 0.01 | 0.01 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_lots_by_session | L5_nyam | P7 | +2.1/+6.9/+3.7/+7.3 | -11.4/-1.6 | +8.7 | +734 | +4.5 | +4.5/+6.1/+9.6 | 19.88 | 0.04 | 0.17 | 1.00 | +15.0 | -4299 / +0.0 | A | dd-only (placebo p 0.17) |
| P7_lots_by_session | L6_london | P7 | +6.0/+3.0/+10.5/+3.6 | -5.0/-6.8 | +8.0 | -4 | +6.0 | +6.0/+10.5/+3.6 | 20.21 | 0.06 | 0.22 | 1.00 | +15.0 | +1418 / +0.0 | A | dd-only (placebo p 0.22) |
| P7_after_P7_stop | same_session_N60min_f0.5 | P7 | +1.3/+1.6/+10.5/+2.2 | -3.7/-3.9 | +6.0 | +467 | +2.9 | +2.9/+11.9/+3.8 | 19.56 | 0.01 | 0.03 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N60min_f0.0 | P7 | +6.6/+2.9/+28.7/-0.0 | -8.3/-9.2 | +11.7 | +866 | +9.3 | +9.3/+30.8/+2.9 | 20.94 | 0.01 | 0.04 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N120min_f0.5 | P7 | +1.2/+1.1/+13.5/+1.0 | -3.2/-4.5 | +5.5 | +332 | +2.3 | +2.3/+14.5/+2.1 | 19.45 | 0.01 | 0.02 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N30min_f0.5 | P7 | +0.1/+2.8/+0.2/+5.5 | -3.7/-1.6 | +4.9 | +444 | +1.6 | +1.6/+1.7/+7.0 | 19.31 | 0.01 | 0.03 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N90min_f0.5 | P7 | -1.7/+3.5/+8.8/-0.5 | -3.4/-3.3 | +5.1 | +427 | -0.2 | -0.2/+10.1/+0.9 | 18.96 | 0.01 | 0.09 | 1.00 | +15.0 | +0 / +0.0 | B | no |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lots_by_session | L4_nyam | P7 | +6.7/+13.1/+7.5/+12.5 | -23.5/-3.4 | +17.1 | +1860 | +12.3 | +12.3/+13.1/+17.7 | 21.65 | 0.04 | 0.04 | 1.00 | +15.0 | -6197 / +0.0 | A | LEAD (w20 fails) |
| P7_after_P7_stop | same_session_N30min_f0.0 | P7 | +2.7/+6.5/+4.4/+8.9 | -7.0/-3.9 | +9.3 | +843 | +5.4 | +5.4/+7.1/+11.4 | 20.09 | 0.01 | 0.01 | 1.00 | +15.0 | +0 / +0.0 | B | LEAD (w20 fails) |
| P7_first_in_session | first_f0.5 | P7 | -1.7/+18.3/+1.1/+35.4 | +2.3/-10.8 | +4.7 | -1889 | -8.7 | -8.7/-5.7/+31.0 | 17.47 | 0.10 | 0.46 | 1.00 | +15.0 | +55 / +0.0 | B | no |
| P7_when_others_on | U7_sameside_f0.5 | P7 | +14.7/+17.1/+8.8/-9.4 | -2.3/-6.0 | +15.9 | -371 | +13.6 | +13.6/+7.6/-10.8 | 21.99 | 0.03 | 0.38 | 1.00 | +15.0 | +0 / +0.0 | B | no |
| P7_later_in_session | later_f0.5 | P7 | +13.7/+11.1/+29.1/+6.0 | +11.0/-19.6 | +8.8 | -5213 | -5.0 | -5.0/+13.7/-14.4 | 18.09 | 0.13 | 0.41 | 1.00 | +15.0 | -36947 / -1335.8 | B | no |


## Cells that dominate Q1-A on both mean and maxDD (down-only; L6M, HOLD and PRE; (a) at equal lots)

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| consec_loss | stack_k5_f0.00 | ALL | +33.6/+33.4/+46.8/-42.6 | -46.1/-16.3 | +37.8 | +413 | +34.5 | +34.5/+47.5/-40.6 | 29.00 | 0.22 | 0.63 | 1.00 | +15.7 | -5710 / +0.0 | B | no |
| lock_daycap_loss | loss1R(live2) | P7 | +25.7/+8.2/+17.0/+6.1 | -22.5/-9.8 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.3 | 25.61 | 0.04 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | C | LEAD (w20 fails) |
| dayloss_book_R | X1.0R_f0.00 | P7 | +25.7/+8.2/+17.0/+6.1 | -22.5/-9.8 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.3 | 25.61 | 0.04 | 0.06 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |
| total_lots_cap | cap6_trunc | sess_london | +25.2/+12.4/+24.1/+3.5 | -18.1/-14.0 | +29.0 | +1094 | +27.9 | +27.9/+26.8/+7.0 | 26.35 | 0.14 | 0.12 | 1.00 | -1.1 | +11305 / +0.0 | B | dd-only (placebo p 0.12) |
| newentry_haircut_day_dd | Y6000_f0.0 | P7_sess_nyam | +23.8/+22.1/+15.7/-12.2 | -21.7/-6.7 | +22.1 | +835 | +25.9 | +25.9/+18.0/-9.1 | 25.65 | 0.03 | 0.62 | 1.00 | -1.1 | -9135 / +0.0 | B | no |
| total_lots_cap | cap4_skip | sess_nyam | +21.2/+15.9/+4.0/+30.6 | -37.7/-4.9 | +26.1 | +356 | +22.2 | +22.2/+5.1/+31.4 | 24.41 | 0.06 | 0.16 | 1.00 | -1.1 | -11810 / +0.0 | B | dd-only (placebo p 0.16) |
| week_loss_stack | X10000_f0.50 | sess_london | +21.2/+9.7/+26.0/-17.9 | -17.5/-11.9 | +27.7 | +1338 | +24.6 | +24.6/+29.2/-12.7 | 25.20 | 0.03 | 0.71 | 1.00 | +15.7 | +0 / +0.0 | B | no |
| same_side_lots_cap | cap6_trunc | sess_london | +19.8/+15.6/+26.7/+10.6 | -12.4/-16.2 | +22.3 | +431 | +21.0 | +21.0/+27.7/+11.9 | 24.04 | 0.10 | 0.04 | 1.00 | -1.1 | +10545 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap4_skip | P7_sess_nyam | +18.8/+16.4/+5.7/+39.4 | -34.5/-5.1 | +24.1 | +200 | +19.3 | +19.3/+6.3/+39.8 | 23.54 | 0.03 | 0.12 | 1.00 | -1.1 | -12000 / +0.0 | B | dd-only (placebo p 0.12) |
| dayloss_stack$ | X3000_f0.00 | P7_sess_nyam | +16.5/+12.8/+7.9/-37.8 | -14.7/-6.2 | +18.0 | +348 | +17.5 | +17.5/+9.0/-36.2 | 23.02 | 0.02 | 0.97 | 1.00 | +15.7 | +0 / +0.0 | B | no |
| dayloss_stack$ | X3000_f0.00 | sess_nyam | +16.0/+11.1/+7.2/-39.1 | -17.7/-3.7 | +18.1 | +221 | +16.7 | +16.7/+7.9/-38.0 | 22.79 | 0.10 | 0.92 | 1.00 | +15.7 | +0 / +0.0 | B | no |
| consec_loss | book_k4_f0.00 | ALL | +15.6/+15.7/+33.5/+1.1 | -23.3/-11.3 | +26.2 | +183 | +16.1 | +16.1/+33.9/+1.7 | 22.64 | 0.06 | 0.07 | 1.00 | +15.7 | -9430 / -1800.0 | B | LEAD (w20 fails) |
| total_lots_cap | cap4_trunc | sess_nyam | +14.0/+8.8/+2.2/+22.0 | -22.3/-2.7 | +21.1 | +1577 | +18.4 | +18.4/+7.2/+26.0 | 23.28 | 0.08 | 0.03 | 1.00 | -1.1 | -2210 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| eqdd_stack_20d | Y10000_f0.50_sticky | P7_sess_london | +13.7/+7.9/+24.5/-1.0 | -12.1/-15.5 | +18.2 | +471 | +15.0 | +15.0/+25.7/+0.6 | 22.36 | 0.05 | 0.46 | 1.00 | +15.7 | +0 / +0.0 | B | dd-only (placebo p 0.46) |
| eqdd_stack_20d | Y10000_f0.50_live | P7_sess_london | +13.7/+7.5/+24.5/-6.0 | -12.1/-14.2 | +17.1 | +388 | +14.8 | +14.8/+25.5/-4.6 | 22.30 | 0.05 | 0.55 | 1.00 | +15.7 | +0 / +0.0 | B | dd-only (placebo p 0.55) |
| newentry_haircut_day_dd | Y6000_f0.5 | sess_nyam | +13.5/+10.6/+7.5/-5.5 | -15.5/-4.2 | +15.4 | +1081 | +16.6 | +16.6/+10.8/-1.8 | 22.78 | 0.02 | 0.78 | 1.00 | -1.1 | -4568 / +0.0 | B | dd-only (placebo p 0.78) |
| newentry_haircut_day_dd | Y3000_f0.5 | sess_nyam | +13.5/+10.6/+7.5/-4.1 | -18.4/-4.9 | +15.8 | +1153 | +16.8 | +16.8/+11.1/-0.2 | 22.83 | 0.03 | 0.73 | 1.00 | -1.1 | -6368 / +0.0 | B | dd-only (placebo p 0.73) |
| newentry_haircut_day_dd | Y6000_f0.5 | P7_sess_nyam | +13.5/+10.6/+7.5/-5.5 | -15.5/-4.2 | +15.4 | +1081 | +16.6 | +16.6/+10.8/-1.8 | 22.78 | 0.02 | 0.75 | 1.00 | -1.1 | -4568 / +0.0 | B | dd-only (placebo p 0.75) |
| newentry_haircut_day_dd | Y3000_f0.5 | P7_sess_nyam | +13.5/+10.6/+7.5/-4.1 | -18.4/-4.9 | +15.8 | +1153 | +16.8 | +16.8/+11.1/-0.2 | 22.83 | 0.03 | 0.61 | 1.00 | -1.1 | -6368 / +0.0 | B | dd-only (placebo p 0.61) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/+14.7/+7.4/+10.8 | -22.3/-5.3 | +20.9 | +1478 | +17.3 | +17.3/+11.9/+15.1 | 22.98 | 0.03 | 0.01 | 1.00 | +15.7 | +0 / +0.0 | B | LEAD (w20 fails) |


## Calmar frontier (rate: d mean $/wk per $1k of maxDD cut, L6M; best 15 cuts with a positive cut at the lowest mean sacrifice)

| technique | params | scope | L6M maxDD cut | d mean L6M | $/wk per $1k maxDD cut | (b) cut L6M |
|--|--|--|--|--|--|--|
| lock_giveback | arm1.5R_keep0.7(live2/.5) | ALL | +5.4 | +2242 | +524 | +12.1 |
| P7_lots_by_session | L4_nyam | P7 | +6.7 | +1860 | +348 | +12.3 |
| consec_loss | stack_k5_f0.00 | sess_nyam | +6.0 | +1570 | +327 | +10.8 |
| eqdd_stack_20d | Y30000_f0.25_sticky | sess_nyam | +7.9 | +1638 | +259 | +12.8 |
| week_loss_stack | X20000_f0.00 | P7_sess_london | +6.5 | +1287 | +248 | +10.5 |
| eqdd_book_20d_R | Y2R_f0.25_live | P7_sess_nyam | +6.8 | +1327 | +243 | +10.9 |
| eqdd_book_20d_R | Y2R_f0.25_live | sess_nyam | +6.8 | +1327 | +243 | +10.9 |
| same_side_lots_cap | cap4_trunc | P7_sess_nyam | +6.7 | +1267 | +237 | +10.6 |
| consec_loss | book_k4_f0.00 | P7 | +8.9 | +1680 | +236 | +13.9 |
| week_loss_stack | X20000_f0.00 | P7_sess_nyam | +10.9 | +2007 | +231 | +16.6 |
| total_lots_cap | cap4_trunc | P7_sess_nyam | +7.9 | +1434 | +228 | +12.2 |
| total_lots_cap | cap6_skip | sess_nyam | +12.9 | +2318 | +225 | +19.3 |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9 | +2299 | +223 | +19.3 |
| total_lots_cap | cap6_skip | P7_sess_nyam | +12.9 | +2299 | +223 | +19.3 |
| same_side_lots_cap | cap10_skip | sess_london | +8.0 | +1416 | +222 | +12.2 |


## P7 section (K slice, P7 maxDD $0 L6M in the stack list; P7-alone equal-mean frontier = P7-only series scaled to Q1-A P7 L6M mean)

| family | technique | params | scope | P7-alone (a) maxDD cut L6M | P7-alone (b) cut L6M/PRE/X' | P7 d mean L6M | stack (b) cut L6M/PRE/X' | placebo p | label |
|--|--|--|--|--|--|--|--|--|--|
| C | esparity_down | last50tr_refmin | P7 | +89.2 | +70.3/+16.6/+25.1 | +5075 | -14.5/+6.5/+27.7 | 0.14 | no |
| C | volparity_down | win120_refmin | P7 | +89.2 | +70.3/+16.6/-36.3 | +5075 | -14.5/+6.5/-15.2 | 0.18 | no |
| C | volparity_down | win120_refmed | P7 | +89.2 | +70.3/+1.3/-36.3 | +5075 | -14.5/-11.1/-15.2 | 0.13 | no |
| C | volparity_down | win60_refmin | P7 | +89.2 | +70.3/+16.6/-54.1 | +5075 | -14.5/+6.5/-29.1 | 0.38 | no |
| C | volparity_down | win20_refmin | P7 | +89.2 | +70.3/+16.6/+12.7 | +5075 | -14.5/+6.5/+23.6 | 0.12 | no |
| C | esparity_down | last200tr_refmin | P7 | +89.2 | +70.3/+16.6/+18.1 | +5075 | -14.5/+6.5/+22.1 | 0.19 | no |
| C | esparity_down | last100tr_refmin | P7 | +89.2 | +70.3/+16.6/+18.1 | +5075 | -14.5/+6.5/+22.1 | 0.13 | no |
| C | riskcap_per_trade | R$2400 | P7 | +80.3 | +68.6/+37.0/+51.5 | +8790 | +10.4/+17.1/+30.8 | 0.02 | LEAD (w20 fails) |
| C | riskcap_per_trade | R$3600 | P7 | +72.5 | +68.4/+36.0/+41.9 | +12176 | +15.4/+17.5/+19.5 | 0.01 | LEAD (w20 fails) |
| C | volparity_down | win20_refmed | P7 | +88.3 | +67.6/+0.7/-16.2 | +5045 | -21.7/-11.3/+5.6 | 0.16 | no |
| E | same_side_lots_cap | cap6_skip | P7 | +69.4 | +63.4/-14.1/+45.9 | +11716 | +9.1/+27.0/+28.6 | 0.01 | LEAD (w20 fails WF-family fails) |
| D | eqdd_book_20d_R | Y2R_f0.25_sticky | P7 | +74.4 | +62.4/+33.1/+47.7 | +9522 | +16.6/+25.5/+44.1 | 0.01 | LEAD (w20 fails) |
| D | eqdd_book_20d_R | Y4R_f0.25_sticky | P7 | +63.2 | +62.1/+35.6/+55.0 | +13585 | +19.1/+36.1/+45.8 | 0.01 | LEAD (w20 fails) |
| C | volparity_down | win60_refmed | P7 | +85.6 | +59.3/-0.8/-69.2 | +4967 | -15.4/-11.9/-34.7 | 0.42 | no |
| C | riskcap_per_trade | R$4800 | P7 | +60.7 | +58.0/+9.4/+16.9 | +13076 | -3.9/-2.3/-4.4 | 0.19 | no |
| E | total_lots_cap | cap6_skip | P7 | +69.4 | +57.2/-18.2/+41.8 | +10000 | +1.1/+20.5/+23.6 | 0.06 | LEAD (w20 fails WF-family fails) |
| D | week_loss_stack | X20000_f0.00 | P7_sess_nyam | +38.3 | +55.2/+41.8/+8.1 | +19294 | +16.6/+24.3/-18.8 | 0.83 | no |
| E | same_side_lots_cap | cap4_skip | P7 | +79.3 | +55.0/-147.7/+25.0 | +6443 | +3.0/-49.8/+7.8 | 0.37 | no |
| D | eqdd_book_20d_R | Y1R_f0.25_live | P7 | +68.2 | +52.3/-9.5/+17.3 | +9313 | +10.2/+24.6/+9.5 | 0.01 | LEAD (w20 fails) |
| D | week_loss_stack | X10000_f0.00 | P7_sess_nyam | +33.0 | +51.5/+35.0/-1.4 | +19331 | +16.2/+20.7/-33.0 | 0.94 | no |


## Exact-driver finalists (<=12, down-only, by 18:00Z): autopilot/SZ_CDE_FINALISTS.csv (12 rows).


| id | label |
|--|--|
| D ; eqdd_stack_20d ; Y10000_f0.50_sticky ; ALL | LEAD (w20 fails) |
| D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | LEAD (w20 fails) |
| D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | LEAD (w20 fails) |
| E ; max_books_on ; n1_f0.5 ; sess_london | LEAD (w20 fails WF-family fails) |
| C ; riskcap_per_trade ; R$3600 ; P7 | LEAD (w20 fails) |
| D ; eqdd_stack_20d ; Y30000_f0.50_sticky ; ALL | LEAD (w20 fails) |
| D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | LEAD (w20 fails) |
| E ; total_lots_cap ; cap6_skip ; sess_nyam | LEAD (w20 fails WF-family fails) |
| E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | LEAD (w20 fails WF-family fails) |
| E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | LEAD (w20 fails WF-family fails) |
| E ; same_side_lots_cap ; cap6_skip ; sess_nyam | LEAD (w20 fails WF-family fails) |
| K ; P7_lots_by_session ; L4_nyam ; P7 | LEAD (w20 fails) |


NOT first-order scorable (exact driver only): StackCutPct 0-100 x sessions and StackAsiaOnly variants; lock/give-back values looser than live (win cap 6-8R, give-back arm 3R/keep .3, floor 14-16R); every re-entry-dependent cell needs state_sizer_b-style engine support (the current exact driver patches only the ER lots step: rules D/E need a new engine hook = v1.6-style code, flagged to lead).


M_CDE.npz row alignment spot-check (M x base P&L in C.prepare(C.load_trades) order, maxDD re-derived on L6M/PRE/X' must equal the ledger): C|riskcap_per_trade|R$2400|P7 L6M maxDD 44621 vs ledger 44621 OK; D|week_loss_book_R|X2R_f0.00|P7_sess_london L6M maxDD 71799 vs ledger 71799 OK; K|P7_after_P7_stop|same_session_N120min_f0.5|P7 L6M maxDD 78932 vs ledger 78932 OK. Windows: the COMB list ends with label day 20261030 (2026-10-31 is a Saturday, base_b has no later trade), so L1M-L3M end there and the live weeks 11-01..05 are only in the held-out live-week columns.


## Exact-engine status of the finalists (hook code/th_sz_cde/cde_exact.py; regression month 202304 with a never-firing rule == S1-COMB; 2 workers; order: six best (F00 F01 F03 F11 F02 F04) on L6M, PRE, X', then the other six, HOLD last). EXACT-CONFIRMED = exact maxDD cut > 0 on every window that is complete; a window shown as na is not run yet; every other cell in this page is FIRST-ORDER ONLY.

| set | cell | L6M exact cut / first-order cut | PRE exact / FO | X' exact / FO | L6M d mean exact / FO | HOLD exact / FO | status |
|--|--|--|--|--|--|--|--|
| CDE_F00 | D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | +24.0 / +46.6 | na / na | na / na | -8998.6 / -8362.9 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F01 | E ; max_books_on ; n1_f0.5 ; sess_london | +25.8 / +27.5 | na / na | na / na | +800.3 / +145.4 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F02 | D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | +10.7 / +30.3 | na / na | na / na | -9190.4 / -4029.3 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F03 | C ; riskcap_per_trade ; R$3600 ; P7 | +18.9 / +37.4 | na / na | na / na | -12148.6 / -7610.8 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F04 | D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | +30.2 / +29.8 | na / na | na / na | -1576.1 / -46.8 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F05 | D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F06 | E ; same_side_lots_cap ; cap6_trunc ; sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F07 | D ; eqdd_stack_20d ; Y30000_f0.25_sticky ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F08 | E ; total_lots_cap ; cap6_skip ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F09 | E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F10 | E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F11 | K ; P7_lots_by_session ; L4_nyam ; P7 | +12.6 / +6.7 | na / na | na / na | +2788.0 / +1860.2 | na / na | EXACT-CONFIRMED on L6M (partial) |


## Family L (SZ-L cooldowns / chop pauses) top-5 EXACT vs first-order (hook codes 20 chop pause, 21 session-loss in cde_exact.py; windows as on this page, ref = S1-COMB trades; first-order from SZ-L raw_L.parquet whose windows run to 11-05)

| set | cell | technique / params | window | exact maxDD cut | first-order cut | exact d mean | FO d mean | exact equal-mean cut | removed trades n / P&L (winners / losers) | first-after-removed n / P&L | exact total vs ref total |
|--|--|--|--|--|--|--|--|--|--|--|--|

Cross-check vs sz_core (Z.score on the 12 finalists + top 20, M_CDE arrays): maxDD L6M and PRE identical (max abs diff 0 $). Means and equal-mean cuts differ by ~4k $/wk and a few points because this page ends the windows at label day 2026-10-30 (last day of the COMB trade list; 10-31 is a Saturday) while sz_core runs its calendar to 2026-11-05 and counts the empty weeks (zero P&L) in L1M-L6M means. Exact-run cut numbers use this page's windows.


## Old base vs new base (Addendum 1 a, b)

**Testing-defect check vs S1-COMB: 0 of 3274 cells have identical maxDD on L6M, PRE and X' (base-dependence is visible in every changed cell).  Testing-defect check vs OLD-BASE: 0 of 3274 cells have identical maxDD on L6M, PRE and X' (base-dependence is visible in every changed cell).  **

### (b) Base-change proof (zero-rule row = Q1-A base lots, same code on each base list)

| base | trades | StateCut | StackCut | BookLock | Stop* | Target | other | mean net/trade | total net | maxDD L6M / PRE / X' (Q1-A row) | L6M mean $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|
| S1B-COMB (new, tick) | 21135 | 6709 | 435 | 207 | 3853 | 9565 | 366 | 117 | 2466756 | see Q1-A row below | |
| S1-COMB (timer) | 21067 | 6694 | 435 | 213 | 3834 | 9527 | 364 | 119 | 2515766 | see Q1-A row below | |
| OLD-BASE (per-print cut) | 23776 | 0 | 127 | 157 | 614 | 9149 | 13729 | 76 | 1805146 | see Q1-A row below | |

Q1-A reference rows (maxDD $ / mean $/wk, carrying week dropped) from the three runs: S1b L6M 79907 / 29139, PRE 140288 / 14005, X' 116941 / 2931; S1 timer L6M 77094 / 26533, PRE 146318 / 13022, X' 113108 / 234; OLD-BASE L6M 141835 / 17518, PRE 165018 / 6470, X' 76171 / 3358. The three trade lists, exit mixes and drawdowns differ, so the base did change.

### (a) Cell results on the OLD bases next to the new base (FIRST-ORDER SCREEN ONLY; equal-mean cut L6M = objective (b))

- C family C: Spearman rank correlation of the cells (S1b vs S1-COMB, by min(L6M,PRE) equal-mean cut) = 0.39
- D family D: Spearman rank correlation of the cells (S1b vs S1-COMB, by min(L6M,PRE) equal-mean cut) = 0.46
- E family E: Spearman rank correlation of the cells (S1b vs S1-COMB, by min(L6M,PRE) equal-mean cut) = 0.42
- K family K: Spearman rank correlation of the cells (S1b vs S1-COMB, by min(L6M,PRE) equal-mean cut) = 0.77
- C family C: Spearman rank correlation of the cells (S1b vs OLD-BASE, by min(L6M,PRE) equal-mean cut) = 0.06
- D family D: Spearman rank correlation of the cells (S1b vs OLD-BASE, by min(L6M,PRE) equal-mean cut) = 0.38
- E family E: Spearman rank correlation of the cells (S1b vs OLD-BASE, by min(L6M,PRE) equal-mean cut) = 0.46
- K family K: Spearman rank correlation of the cells (S1b vs OLD-BASE, by min(L6M,PRE) equal-mean cut) = 0.72

| old base | fam | top-5 cell on S1b | L6M eq cut S1b | L6M eq cut old | PRE eq cut S1b | PRE eq cut old | rank S1b | rank old |
|--|--|--|--|--|--|--|--|--|
| S1-COMB | C | C ; riskcap_per_trade ; R$3600 ; P7 | +15.5 | +26.2 | +17.6 | +33.6 | 1 | 1 |
| S1-COMB | C | C ; riskcap_per_trade ; R$2400 ; P7 | +10.6 | +25.3 | +17.2 | +34.8 | 2 | 2 |
| S1-COMB | C | C ; volparity_down ; win120_refmin ; M7 | +3.0 | +11.0 | +4.6 | +5.2 | 3 | 12 |
| S1-COMB | C | C ; riskcap_per_trade ; R$3600 ; ALL | +2.5 | +15.2 | +18.2 | +33.5 | 4 | 3 |
| S1-COMB | C | C ; esparity_down ; last100tr_refmin ; M7 | +3.0 | +11.0 | +4.6 | +5.2 | 6 | 12 |
| S1-COMB | D | D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | +24.4 | +19.6 | +21.6 | +19.8 | 1 | 38 |
| S1-COMB | D | D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | +18.6 | +18.6 | +35.7 | +33.5 | 2 | 49 |
| S1-COMB | D | D ; eqdd_book_20d_R ; Y2R_f0.25_sticky ; P7 | +16.3 | -6.7 | +25.3 | +12.9 | 3 | 1666 |
| S1-COMB | D | D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | +29.8 | +31.2 | +43.4 | +44.6 | 4 | 10 |
| S1-COMB | D | D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | +13.3 | +15.5 | +30.4 | +32.0 | 5 | 67 |
| S1-COMB | E | E ; max_books_on ; n1_f0.5 ; sess_london | +27.8 | +27.1 | +26.0 | +21.9 | 1 | 19 |
| S1-COMB | E | E ; same_side_lots_cap ; cap6_trunc ; sess_london | +21.0 | +32.2 | +27.7 | +26.8 | 2 | 10 |
| S1-COMB | E | E ; total_lots_cap ; cap6_skip ; sess_nyam | +19.3 | +18.9 | +12.7 | +11.5 | 3 | 63 |
| S1-COMB | E | E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | +19.3 | +19.5 | +12.6 | +12.1 | 4 | 57 |
| S1-COMB | E | E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | +19.3 | +19.5 | +12.6 | +12.1 | 4 | 57 |
| S1-COMB | K | K ; P7_lots_by_session ; L4_nyam ; P7 | +12.3 | +16.5 | +13.1 | +12.0 | 1 | 3 |
| S1-COMB | K | K ; P7_lots_by_session ; L3_nyam ; P7 | +10.2 | +14.1 | +10.7 | +9.2 | 2 | 7 |
| S1-COMB | K | K ; P7_lots_by_session ; L4_london ; P7 | +15.4 | +13.9 | +25.1 | +24.1 | 3 | 1 |
| S1-COMB | K | K ; P7_lots_by_session ; L5_london ; P7 | +8.4 | +5.0 | +14.7 | +13.9 | 4 | 18 |
| S1-COMB | K | K ; P7_lots_by_session ; L6_all ; P7 | +7.7 | +12.9 | +9.9 | +11.0 | 5 | 4 |
| OLD-BASE | C | C ; riskcap_per_trade ; R$3600 ; P7 | +15.5 | +39.5 | +17.6 | +32.0 | 1 | 1 |
| OLD-BASE | C | C ; riskcap_per_trade ; R$2400 ; P7 | +10.6 | +31.4 | +17.2 | +38.1 | 2 | 2 |
| OLD-BASE | C | C ; volparity_down ; win120_refmin ; M7 | +3.0 | +15.0 | +4.6 | +13.7 | 3 | 28 |
| OLD-BASE | C | C ; riskcap_per_trade ; R$3600 ; ALL | +2.5 | +33.7 | +18.2 | +27.2 | 4 | 9 |
| OLD-BASE | C | C ; esparity_down ; last100tr_refmin ; M7 | +3.0 | +15.0 | +4.6 | +13.7 | 6 | 28 |
| OLD-BASE | D | D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | +24.4 | +45.1 | +21.6 | +25.7 | 1 | 42 |
| OLD-BASE | D | D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | +18.6 | +37.5 | +35.7 | +48.3 | 2 | 13 |
| OLD-BASE | D | D ; eqdd_book_20d_R ; Y2R_f0.25_sticky ; P7 | +16.3 | -1.3 | +25.3 | +15.6 | 3 | 1300 |
| OLD-BASE | D | D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | +29.8 | +28.4 | +43.4 | +33.2 | 4 | 34 |
| OLD-BASE | D | D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | +13.3 | +17.5 | +30.4 | +34.1 | 5 | 81 |
| OLD-BASE | E | E ; max_books_on ; n1_f0.5 ; sess_london | +27.8 | +30.8 | +26.0 | +19.2 | 1 | 30 |
| OLD-BASE | E | E ; same_side_lots_cap ; cap6_trunc ; sess_london | +21.0 | +45.3 | +27.7 | +20.9 | 2 | 29 |
| OLD-BASE | E | E ; total_lots_cap ; cap6_skip ; sess_nyam | +19.3 | +4.4 | +12.7 | +10.9 | 3 | 123 |
| OLD-BASE | E | E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | +19.3 | +8.6 | +12.6 | +12.5 | 4 | 79 |
| OLD-BASE | E | E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | +19.3 | +8.6 | +12.6 | +12.5 | 4 | 79 |
| OLD-BASE | K | K ; P7_lots_by_session ; L4_nyam ; P7 | +12.3 | +8.9 | +13.1 | +12.9 | 1 | 6 |
| OLD-BASE | K | K ; P7_lots_by_session ; L3_nyam ; P7 | +10.2 | -0.6 | +10.7 | +7.7 | 2 | 18 |
| OLD-BASE | K | K ; P7_lots_by_session ; L4_london ; P7 | +15.4 | +10.4 | +25.1 | +16.5 | 3 | 5 |
| OLD-BASE | K | K ; P7_lots_by_session ; L5_london ; P7 | +8.4 | +5.8 | +14.7 | +10.7 | 4 | 8 |
| OLD-BASE | K | K ; P7_lots_by_session ; L6_all ; P7 | +7.7 | +15.9 | +9.9 | +13.6 | 5 | 4 |

## Exact vs first-order, L6M (first exact result, 2026-11-09 15:35Z; six priority finalists, L6M months 2026-05..10 complete; PRE and X' running)
Survive in the engine (exact L6M maxDD cut about the first-order cut, equal-mean cut positive): E max_books_on n1 f0.5 on the London session (exact +25.8% vs FO +27.5%, d mean +800 $/wk, equal-mean +27.8%); D eqdd_stack_20d Y20000 f0.25 sticky on London (exact +30.2% vs FO +29.8%, d mean -1.6k, equal-mean +26.2%); K P7 lots cap 4 in NYAM (exact +12.6% vs FO +6.7%, d mean +2.8k, equal-mean +20.2%).
Deflate and fail at equal mean: D eqdd_book_20d_R Y1R f0.50 sticky ALL (FO +46.6% -> exact +24.0%; d mean -9.0k; equal-mean -9.9%: the first-order cut was mostly size-down); D eqdd_book_20d_R Y4R f0.25 P7 (FO +30.3% -> +10.7%, equal-mean -30.1%); C riskcap R$3600 on P7 (FO +37.4% -> +18.9%, equal-mean -38.7%).
So the broad/book-level state and risk-cap cells lose half or more of the first-order cut in the engine and do not beat size-down at equal mean; the session-scoped London/NYAM cells survive on L6M only. PRE and X' not yet exact; no cell is a candidate on L6M alone.

Keying check (lead, 17:00Z): cde_exact.py uses NO multiplier table keyed on a time or row. Every D/E/K rule and the L cooldown rules (codes 20, 21) compute the multiplier directly from the engine's own state at the decision call inside ntz_check (realized P&L, open lots, equity history, loss counts keyed by trade sig_ns session instance, chop flags looked up by searchsorted on the decision second); the decision second is the engine's arm time of the signal, which is the signal second (l2arm is called at the signal). The first-order path (cde_kernel.py) is sequential on sig_ts and M_CDE.npz rows were verified to the dollar against the ledger. Firing is visible in the exact output (CDE_L2 202605: 603 trades vs 672 in S1-COMB). No void needed.
