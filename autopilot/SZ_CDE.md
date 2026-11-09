# SZ-CDE - families C (parity), D (equity-curve/state/locks), E (exposure), K slice (P7)  - 2026-11-09 15:34Z

**Label: first-order on base S1b-COMB (live D7 v1.5 with the seven state-cut lines), 21135 trades 2023-04..2026-10 (last label day 20261030; the 2026-11-01..05 live weeks are not in the list, so L1M/L2M/L3M windows end 2026-10-30); entries not live-matched; in-sample; PRE-PROOF; post-hoc; Shadow only; no PASS claims.** Reference = Q1-A (the base lots). 3274 cells (C 140, D 1980, E 1110, K 44). Prereg: autopilot/SZ_CDE_PREREG.md (sha in DECISIONS.md).

Reading guide: (a) = cell vs Q1-A at equal lots (maxDD cut % = positive is shallower; d mean $/wk L6M). (b) = every cell scaled by one global factor so its L6M mean equals Q1-A (0 $/wk), then maxDD / worst-20 / Ulcer cut vs Q1-A; size-down-everything scores 0 by construction. Class A = lots-only static (first-order valid); B = skips/state (ranking valid, mean not, exact re-run needed for re-entries); C = lock/give-back/week-floor (engine marks open P&L and flattens: first-order is a skip-only proxy ON TOP of the base that already holds the live locks; loosened values and StackCutPct x sessions are exact-driver only). State for D/E = realized P&L of cell-sized trades with exit < signal second (open P&L not in any state). Placebo = donor multipliers reassigned to random trades in the same book x session (100 draws; stat = min of (b) cut over L6M, PRE, X'). Family p = max over the whole CDE set (3274 cells) per draw. WF = monthly 2024-01..2026-10, 26 trailing weeks, 7-day embargo, picks the best trailing equal-mean maxDD cell, OOS maxDD cut at equal mean shown per family.

## Headline

- Cells on the bar (CANDIDATE-DD, first-order, all still need the EXACT engine): 0; LEADs (equal-mean maxDD lower on L6M, PRE and X' with placebo p<=.10 but another gate fails): 269. Cells that dominate Q1-A on BOTH mean and maxDD (L6M, HOLD, PRE; down-only): 244.

- WF of the picking procedure (OOS 2024-01..2026-10, 148 weeks): ALL_CDEK: OOS maxDD cut +11% raw / -34% at equal mean (d mean -5600 $/wk); C: OOS maxDD cut +32% raw / -9% at equal mean (d mean -6152 $/wk); D: OOS maxDD cut +46% raw / +37% at equal mean (d mean -2249 $/wk); E: OOS maxDD cut +11% raw / -24% at equal mean (d mean -4750 $/wk); K: OOS maxDD cut +12% raw / -3% at equal mean (d mean -2386 $/wk); D_state_only: OOS maxDD cut +46% raw / +35% at equal mean (d mean -2805 $/wk); E_ALL_scope: OOS maxDD cut +17% raw / -29% at equal mean (d mean -5907 $/wk); D_ALL_scope: OOS maxDD cut +48% raw / +30% at equal mean (d mean -4154 $/wk).

- Live week (frozen file, 180 DS7-book trades): Q1-A total +104810, trade-level maxDD $14,490; the week has no stack losing day, so it cannot separate cells; columns show d total and d trade-level dd vs Q1-A.

- Family C best (down-only, ranked by the joint equal-mean cut): riskcap_per_trade R$3600 on scope P7 cuts L6M maxDD 37% at equal lots (d mean -7558 $/wk) and 16% / 18% / 20% at equal mean on L6M / PRE / X'; placebo p 0.01, family p 1.00; family WF OOS equal-mean cut -9%; LEAD (w20 fails WF-family fails).
- Family D best (down-only, ranked by the joint equal-mean cut): eqdd_book_20d_R Y1R_f0.50_sticky on scope ALL cuts L6M maxDD 47% at equal lots (d mean -8535 $/wk) and 24% / 22% / 27% at equal mean on L6M / PRE / X'; placebo p 0.01, family p 0.76; family WF OOS equal-mean cut +37%; LEAD (w20 fails).
- Family E best (down-only, ranked by the joint equal-mean cut): max_books_on n1_f0.5 on scope sess_london cuts L6M maxDD 27% at equal lots (d mean +145 $/wk) and 28% / 26% / 19% at equal mean on L6M / PRE / X'; placebo p 0.07, family p 0.89; family WF OOS equal-mean cut -24%; LEAD (w20 fails WF-family fails).
- Family K best (down-only, ranked by the joint equal-mean cut): P7_lots_by_session L4_nyam on scope P7 cuts L6M maxDD 7% at equal lots (d mean +1860 $/wk) and 12% / 13% / 19% at equal mean on L6M / PRE / X'; placebo p 0.04, family p 1.00; family WF OOS equal-mean cut -3%; LEAD (w20 fails WF-family fails).


## C. Equal-risk / parity

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 128 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+32.1/+39.0/+40.6 | -19.0/-31.9 | +19.1 | -7558 | +15.5 | +15.5/+17.6/+19.7 | 22.45 | 0.19 | 0.01 | 1.00 | -8.7 | -40358 / -3076.2 | A | LEAD (w20 fails WF-family fails) |
| riskcap_per_trade | R$2400 | P7 | +44.2/+36.0/+48.3/+57.6 | -0.6/-42.3 | +14.1 | -10944 | +10.6 | +10.6/+17.2/+32.0 | 21.20 | 0.21 | 0.01 | 1.00 | -8.7 | -54807 / -1390.8 | A | LEAD (w20 fails WF-family fails) |
| volparity_down | win120_refmin | M7 | +2.0/+3.4/+3.6/+2.1 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+3.1 | 19.55 | 0.03 | 0.01 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| riskcap_per_trade | R$3600 | ALL | +31.0/+34.2/+42.1/+50.9 | -7.9/-33.0 | +11.7 | -8513 | +2.5 | +2.5/+18.2/+30.6 | 19.44 | 0.22 | 0.01 | 1.00 | -8.7 | -38377 / -5021.2 | A | LEAD (w20 fails WF-family fails) |
| esparity_down | last100tr_refmin | M7 | +2.0/+3.4/+3.6/+0.7 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.55 | 0.03 | 0.02 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| esparity_down | last200tr_refmin | M7 | +2.0/+3.4/+3.6/+0.7 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.55 | 0.03 | 0.07 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| esparity_down | last50tr_refmin | M7 | +2.0/+3.4/+3.6/+0.7 | -6.0/-3.0 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.55 | 0.03 | 0.07 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| volparity_down | win60_refmin | M7 | +2.0/+3.4/+3.6/+0.3 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.4 | 19.55 | 0.03 | 0.05 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| volparity_down | win20_refmin | M7 | +2.0/+3.4/+3.6/-0.5 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+0.6 | 19.55 | 0.03 | 0.19 | 1.00 | -8.7 | na / na | A | dd-only (placebo p 0.19) |
| riskcap_per_trade | R$3600 | O7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | -8.7 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | M7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | -8.7 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$4800 | H7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | -8.7 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | A7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | -8.7 | +0 / +0.0 | A | no |
| riskcap_per_trade | R$3600 | K7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | -8.7 | +0 / +0.0 | A | no |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+32.1/+39.0/+40.6 | -19.0/-31.9 | +19.1 | -7558 | +15.5 | +15.5/+17.6/+19.7 | 22.45 | 0.19 | 0.01 | 1.00 | -8.7 | -40358 / -3076.2 | A | LEAD (w20 fails WF-family fails) |
| volparity_down | win120_refmin | M7 | +2.0/+3.4/+3.6/+2.1 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+3.1 | 19.55 | 0.03 | 0.01 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |
| esparity_down | last100tr_refmin | M7 | +2.0/+3.4/+3.6/+0.7 | -6.0/-3.1 | +7.7 | +305 | +3.0 | +3.0/+4.6/+1.7 | 19.55 | 0.03 | 0.02 | 1.00 | -8.7 | na / na | A | LEAD (w20 fails WF-family fails) |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| equal_risk_all_books | R$3600(up-allowed) | ALL | -26.5/-55.0/+8.5/+35.3 | -64.5/+5.5 | +2.9 | +4588 | -9.3 | -9.3/+20.9/+44.1 | 17.35 | 0.98 | 0.01 | 1.00 | -8.7 | +5643 / +597.1 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmed_clip.5-1.5 | ALL | +33.9/+20.6/+48.7/+37.8 | +11.4/-36.8 | -8.9 | -11572 | -9.7 | -9.7/+14.9/-3.2 | 17.29 | 0.39 | 0.22 | 1.00 | -8.7 | na / na | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmin_clip.5-1.5 | ALL | +47.5/+39.3/+43.3/+54.0 | +26.1/-42.3 | +1.4 | -14104 | -1.8 | -1.8/-9.8/+10.9 | 18.63 | 0.39 | 0.18 | 1.00 | -8.7 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$1200(up-allowed) | ALL | +58.9/+47.4/+69.3/+78.1 | +44.2/-65.3 | -2.6 | -18609 | -13.7 | -13.7/+15.1/+39.5 | 16.67 | 0.42 | 0.05 | 1.00 | -8.7 | -67772 / -9229.3 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win120_refmed_clip.5-1.5 | ALL | +35.5/+19.3/+36.7/+27.7 | +2.5/-33.9 | +4.1 | -10811 | -2.5 | -2.5/-0.7/-14.9 | 18.50 | 0.39 | 0.38 | 1.00 | -8.7 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$2400(up-allowed) | ALL | +14.6/-2.3/+39.1/+54.3 | -8.4/-29.3 | -6.1 | -8446 | -20.3 | -20.3/+14.3/+35.7 | 15.76 | 0.85 | 0.08 | 1.00 | -8.7 | -31394 / -4663.6 | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$6000(up-allowed) | ALL | -111.9/-157.3/-52.4/-10.3 | -172.9/+76.2 | -10.7 | +20282 | -25.0 | -25.0/+10.2/+34.9 | 15.17 | 0.99 | 0.01 | 1.00 | -8.7 | +79059 / +10423.6 | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$8400(up-allowed) | ALL | -197.4/-259.6/-113.2/-56.0 | -281.4/+146.9 | -11.0 | +39970 | -25.4 | -25.4/+10.1/+34.2 | 15.12 | 0.93 | 0.02 | 1.00 | -8.7 | +152474 / +20250.0 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win60_refmed_clip.5-1.5 | ALL | +35.0/+16.0/+45.3/+19.5 | -1.7/-36.7 | +11.2 | -10504 | -1.6 | -1.6/+14.4/-25.8 | 18.66 | 0.39 | 0.79 | 1.00 | -8.7 | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$4800(up-allowed) | ALL | -70.8/-104.6/-21.7/+8.7 | -116.9/+41.4 | -11.5 | +10237 | -26.4 | -26.4/+9.9/+32.4 | 15.00 | 0.86 | 0.02 | 1.00 | -8.7 | +42021 / +5162.9 | A | UP-ALLOWED report row (never promoted) |


## D. Equity-curve / state / locks (down-only ranked; up-allowed and anti-martingale in the report rows below)

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1966 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_book_20d_R | Y1R_f0.50_sticky | ALL | +46.6/+40.8/+44.6/+48.2 | +25.6/-40.8 | +25.4 | -8535 | +24.4 | +24.4/+21.6/+26.7 | 25.10 | 0.33 | 0.01 | 0.76 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y4R_f0.25_sticky | P7 | +30.3/+28.7/+44.9/+53.6 | +18.5/-41.6 | +28.0 | -4179 | +18.6 | +18.6/+35.7/+45.8 | 23.29 | 0.17 | 0.01 | 0.92 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y2R_f0.25_sticky | P7 | +38.3/+33.0/+44.9/+59.5 | +25.6/-42.2 | +15.9 | -7653 | +16.3 | +16.3/+25.3/+45.1 | 22.65 | 0.21 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_london | +29.8/-46.4/+43.4/+14.2 | -17.0/-23.1 | +27.3 | +16 | +29.8 | +29.8/+43.4/+14.2 | 27.01 | 0.10 | 0.07 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| week_loss_book_R | X2R_f0.00 | P7_sess_london | +10.1/-5.8/+27.9/+13.0 | -16.1/-14.5 | +18.5 | +1072 | +13.3 | +13.3/+30.4/+16.1 | 21.88 | 0.01 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y30000_f0.25_sticky | sess_nyam | +7.9/+16.4/+11.3/+24.2 | -17.6/-6.0 | +18.1 | +1638 | +12.8 | +12.8/+16.0/+28.2 | 21.75 | 0.03 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.50_sticky | sess_london | +22.3/-24.5/+38.8/+11.8 | -14.1/-19.2 | +23.0 | +267 | +23.0 | +23.0/+39.3/+12.6 | 24.64 | 0.10 | 0.06 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | P7_sess_london | +11.1/-11.8/+24.5/+9.6 | -17.2/-15.0 | +18.9 | +922 | +13.9 | +13.9/+26.9/+12.4 | 22.01 | 0.06 | 0.03 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_book_20d_R | Y4R_f0.25_sticky | ALL | +44.3/+25.1/+51.1/+36.3 | +40.4/-51.6 | +33.4 | -8025 | +23.1 | +23.1/+32.5/+12.0 | 24.66 | 0.29 | 0.04 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | P7_sess_nyam | +9.9/+16.4/+11.3/+25.9 | -7.6/-7.9 | +15.7 | +694 | +12.0 | +12.0/+13.4/+27.7 | 21.55 | 0.03 | 0.06 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y10000_f0.25_sticky | sess_london | +29.8/-41.1/+47.8/+13.0 | -27.0/-25.7 | +33.6 | -351 | +28.9 | +28.9/+47.1/+12.0 | 26.67 | 0.11 | 0.10 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/-6.6/+7.4/+11.9 | -22.3/-5.1 | +20.9 | +1478 | +17.3 | +17.3/+11.9/+16.2 | 22.94 | 0.03 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| dayloss_stack$ | X8000_f0.00 | P7_sess_london | +24.1/-30.0/+10.8/+10.1 | -8.6/-7.2 | +21.2 | +421 | +25.2 | +25.2/+12.1/+11.4 | 25.35 | 0.02 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_nyam | +9.9/+16.4/+11.3/+32.1 | -6.6/-6.6 | +15.8 | +406 | +11.1 | +11.1/+12.5/+33.0 | 21.34 | 0.03 | 0.08 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_book_20d_R | Y1R_f0.50_sticky | ALL | +46.6/+40.8/+44.6/+48.2 | +25.6/-40.8 | +25.4 | -8535 | +24.4 | +24.4/+21.6/+26.7 | 25.10 | 0.33 | 0.01 | 0.76 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_london | +29.8/-46.4/+43.4/+14.2 | -17.0/-23.1 | +27.3 | +16 | +29.8 | +29.8/+43.4/+14.2 | 27.01 | 0.10 | 0.07 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| week_loss_book_R | X2R_f0.00 | P7_sess_london | +10.1/-5.8/+27.9/+13.0 | -16.1/-14.5 | +18.5 | +1072 | +13.3 | +13.3/+30.4/+16.1 | 21.88 | 0.01 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/-6.6/+7.4/+11.9 | -22.3/-5.1 | +20.9 | +1478 | +17.3 | +17.3/+11.9/+16.2 | 22.94 | 0.03 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| consec_loss | book_k4_f0.00 | sess_london | +6.8/+8.5/+14.5/+5.2 | -30.7/-4.5 | +26.7 | +1277 | +10.7 | +10.7/+18.1/+9.2 | 21.23 | 0.05 | 0.04 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| lock_giveback | arm1.5R_keep0.7(live2/.5) | ALL | +5.4/+0.5/+31.2/-0.0 | -16.3/-14.4 | +15.0 | +2242 | +12.1 | +12.1/+36.1/+7.1 | 21.58 | 0.02 | 0.01 | 1.00 | +37.2 | -16500 / -1800.0 | C | LEAD (w20 fails) |
| dayloss_book_R | X1.0R_f0.00 | P7 | +25.7/-22.4/+17.0/+6.7 | -22.5/-10.2 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.9 | 25.57 | 0.04 | 0.09 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| lock_daycap_loss | loss1R(live2) | P7 | +25.7/-22.4/+17.0/+6.7 | -22.5/-10.2 | +38.5 | +47 | +25.8 | +25.8/+17.1/+6.9 | 25.57 | 0.04 | 0.07 | 1.00 | +37.2 | +0 / +0.0 | C | LEAD (w20 fails) |
| week_loss_stack | X30000_f0.00 | sess_london | +9.4/-32.3/+34.8/+1.2 | -19.3/-14.6 | +23.3 | +1293 | +13.2 | +13.2/+37.5/+5.4 | 21.85 | 0.03 | 0.05 | 1.00 | +37.2 | +0 / +0.0 | B | LEAD (w20 fails) |
| lock_combo | win5_loss2_arm2_keep0.7_floor12 | P7 | +0.0/+0.0/+0.0/+0.0 | -4.7/-0.4 | +6.5 | +1107 | +3.7 | +3.7/+3.7/+3.7 | 19.68 | 0.00 | 0.02 | 1.00 | +37.2 | -43695 / -3560.0 | C | LEAD (w20 fails) |
| week_profit_protect_stack | X60000_f0.50 | sess_london | +0.0/+0.0/+0.0/+0.0 | -3.7/+0.0 | +1.6 | +478 | +1.6 | +1.6/+1.6/+1.6 | 19.27 | 0.01 | 0.06 | 1.00 | +37.2 | +2299 / +0.0 | B | LEAD (w20 fails) |
| lock_daycap_win | win4R(live5) | A7 | +0.0/+0.0/+0.0/+0.0 | -0.3/+0.0 | +0.1 | +29 | +0.1 | +0.1/+0.1/+0.1 | 18.98 | 0.00 | 0.19 | 1.00 | +37.2 | +0 / +0.0 | C | dd-only (placebo p 0.19) |
| lock_weekfloor | floor16R(live12) | U7 | +0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0 | +0.0/+0.0/+0.0 | 18.96 | 0.00 | 0.01 | 1.00 | +37.2 | +0 / +0.0 | C | no |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| antimartingale_UP | book_n4_x1.25 | ALL | -1.4/-0.8/+1.0/-7.4 | +1.1/+0.8 | -3.2 | -186 | -2.1 | -2.1/+0.4/-8.1 | 18.58 | 0.02 | 0.20 | 1.00 | +37.2 | +0 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n4_x1.50 | ALL | -0.6/-0.8/+2.0/-9.0 | +9.5/+1.9 | -5.1 | -739 | -3.3 | -3.3/-0.5/-11.8 | 18.36 | 0.05 | 0.06 | 1.00 | +37.2 | -655 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| eqdd_stack_UP_at_high | Y20000_f0.50_up1.25 | ALL | +35.8/+28.3/+40.5/-13.9 | +32.1/-25.6 | +12.6 | -4836 | +23.0 | +23.0/+28.7/-36.6 | 24.62 | 0.29 | 0.59 | 1.00 | +37.2 | +25118 / +5079.1 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.50 | ALL | -6.2/-3.0/+0.0/-25.7 | +6.5/+5.8 | -12.8 | -2783 | -17.4 | -17.4/-10.6/-39.0 | 16.15 | 0.10 | 0.50 | 1.00 | +37.2 | -3448 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.25 | ALL | -12.9/-2.1/-10.3/-9.8 | -0.5/+7.7 | -38.1 | -5502 | -39.2 | -39.2/-36.0/-35.4 | 13.62 | 0.10 | 0.71 | 1.00 | +37.2 | -1210 / +1860.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.25 | ALL | -7.5/-0.8/-0.7/-17.3 | +1.2/+3.1 | -33.9 | -6220 | -36.7 | -36.7/-28.1/-49.2 | 13.87 | 0.05 | 0.92 | 1.00 | +37.2 | -2651 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.50 | ALL | -17.0/-13.0/-14.0/-31.8 | -4.3/+17.2 | -39.1 | -3861 | -34.9 | -34.9/-31.4/-51.9 | 14.06 | 0.22 | 0.54 | 1.00 | +37.2 | -5591 / +3720.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n4_x1.25 | ALL | -9.9/-7.5/-6.4/-22.1 | +5.0/+5.6 | -38.0 | -6078 | -38.8 | -38.8/-34.5/-54.3 | 13.66 | 0.07 | 0.95 | 1.00 | +37.2 | -1085 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n3_x1.25 | ALL | -28.1/-20.6/-5.0/-22.5 | +20.3/+8.2 | -70.8 | -7233 | -70.4 | -70.4/-39.6/-62.9 | 11.13 | 0.10 | 0.98 | 1.00 | +37.2 | +707 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n2_x1.25 | ALL | -33.5/-7.2/-11.3/-25.2 | +20.0/+7.8 | -68.2 | -6536 | -72.1 | -72.1/-43.4/-61.4 | 11.02 | 0.14 | 0.98 | 1.00 | +37.2 | -938 / +0.0 | B | UP-ALLOWED report row (never promoted) |


## E. Exposure / concentration

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1110 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| max_books_on | n1_f0.5 | sess_london | +27.5/-39.5/+25.6/+18.6 | -11.7/-18.6 | +27.6 | +145 | +27.8 | +27.8/+26.0/+19.0 | 26.28 | 0.13 | 0.07 | 0.89 | -24.2 | +7051 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_trunc | sess_london | +19.8/-2.9/+26.7/+11.7 | -12.4/-16.2 | +22.3 | +431 | +21.0 | +21.0/+27.7/+13.0 | 23.99 | 0.10 | 0.03 | 1.00 | -24.2 | +10545 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+30.7 | -27.3/-3.4 | +26.3 | +2318 | +19.3 | +19.3/+12.7/+35.8 | 23.51 | 0.03 | 0.01 | 1.00 | -24.2 | +715 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+35.4 | -26.1/-4.7 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+40.2 | 23.49 | 0.02 | 0.02 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+37.0 | -26.1/-5.3 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+41.6 | 23.49 | 0.02 | 0.01 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+33.0 | -26.5/-4.7 | +25.7 | +2240 | +19.1 | +19.1/+12.4/+37.8 | 23.45 | 0.02 | 0.02 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | ALL | +41.1/+39.7/+44.8/+54.9 | -0.5/-41.8 | +43.7 | -9614 | +12.1 | +12.1/+17.6/+32.7 | 21.57 | 0.15 | 0.01 | 1.00 | -24.2 | -53550 / -4440.0 | B | LEAD (w20 fails WF-family fails) |
| max_books_on | n1_f0.5 | P7_sess_london | +11.1/-20.2/+10.6/+11.8 | -10.5/-12.5 | +17.9 | +102 | +11.4 | +11.4/+10.9/+12.2 | 21.40 | 0.06 | 0.06 | 1.00 | -24.2 | +4500 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_trunc | P7_sess_london | +10.9/-4.6/+15.5/+11.8 | -4.3/-9.2 | +13.8 | -38 | +10.8 | +10.8/+15.4/+11.7 | 21.27 | 0.04 | 0.03 | 1.00 | -24.2 | +1921 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap8_skip | sess_london | +10.2/+11.2/+8.4/+9.4 | -9.7/-11.7 | +16.9 | +804 | +12.6 | +12.6/+10.8/+11.8 | 21.69 | 0.05 | 0.02 | 1.00 | -24.2 | +7590 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| corr_same_side | N30min_f0.0_ge1_others | sess_london | +31.6/-27.9/+38.0/+22.9 | +22.2/-24.7 | +9.1 | -4241 | +20.0 | +20.0/+27.5/+9.8 | 23.70 | 0.12 | 0.07 | 1.00 | -24.2 | -2230 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap4_trunc | sess_london | +33.7/-25.6/+46.5/+11.9 | -6.0/-29.2 | +32.2 | -729 | +32.0 | +32.0/+45.1/+9.6 | 27.90 | 0.16 | 0.09 | 1.00 | -24.2 | +12842 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7 | +34.2/+42.0/+47.2/+43.0 | -9.1/-38.3 | +42.5 | -8018 | +9.3 | +9.3/+27.1/+21.4 | 20.90 | 0.10 | 0.01 | 1.00 | -24.2 | -57130 / -3830.0 | B | LEAD (w20 fails WF-family fails) |
| corr_same_side | N30min_f0.5_ge1_others | sess_london | +20.6/-6.7/+20.0/+13.7 | +11.4/-13.1 | +11.8 | -1589 | +16.0 | +16.0/+15.4/+8.7 | 22.58 | 0.08 | 0.07 | 1.00 | -24.2 | +1341 / +0.0 | B | LEAD (w20 fails WF-family fails) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| max_books_on | n1_f0.5 | sess_london | +27.5/-39.5/+25.6/+18.6 | -11.7/-18.6 | +27.6 | +145 | +27.8 | +27.8/+26.0/+19.0 | 26.28 | 0.13 | 0.07 | 0.89 | -24.2 | +7051 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_trunc | sess_london | +19.8/-2.9/+26.7/+11.7 | -12.4/-16.2 | +22.3 | +431 | +21.0 | +21.0/+27.7/+13.0 | 23.99 | 0.10 | 0.03 | 1.00 | -24.2 | +10545 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+30.7 | -27.3/-3.4 | +26.3 | +2318 | +19.3 | +19.3/+12.7/+35.8 | 23.51 | 0.03 | 0.01 | 1.00 | -24.2 | +715 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| corr_same_side | N30min_f0.0_ge1_others | sess_london | +31.6/-27.9/+38.0/+22.9 | +22.2/-24.7 | +9.1 | -4241 | +20.0 | +20.0/+27.5/+9.8 | 23.70 | 0.12 | 0.07 | 1.00 | -24.2 | -2230 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| newentry_haircut_day_dd | Y3000_f0.0 | K7 | +12.9/-1.2/+9.3/+9.3 | +6.9/-6.1 | +3.8 | -1367 | +8.6 | +8.6/+4.8/+4.8 | 20.75 | 0.19 | 0.01 | 1.00 | -24.2 | -15095 / -1220.0 | B | LEAD (w20 fails WF-family fails) |


## K. P7 specific

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 44 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lots_by_session | L4_nyam | P7 | +6.7/+13.1/+7.5/+13.8 | -23.5/-3.4 | +17.1 | +1860 | +12.3 | +12.3/+13.1/+18.9 | 21.62 | 0.04 | 0.04 | 1.00 | -3.1 | -6197 / +0.0 | A | LEAD (w20 fails WF-family fails) |
| P7_lots_by_session | L3_nyam | P7 | +6.9/+12.7/+7.5/+12.3 | -20.4/-4.2 | +15.4 | +1060 | +10.2 | +10.2/+10.7/+15.3 | 21.12 | 0.05 | 0.16 | 1.00 | -3.1 | -9798 / +48.3 | A | dd-only (placebo p 0.16) |
| P7_lots_by_session | L4_london | P7 | +16.5/-15.8/+26.1/+11.2 | -4.7/-15.8 | +16.4 | -360 | +15.4 | +15.4/+25.1/+10.1 | 22.42 | 0.06 | 0.07 | 1.00 | -3.1 | +1193 / +0.0 | A | LEAD (w20 fails WF-family fails) |
| P7_lots_by_session | L5_london | P7 | +9.3/-4.5/+15.6/+9.4 | -1.1/-9.5 | +8.3 | -297 | +8.4 | +8.4/+14.7/+8.5 | 20.69 | 0.06 | 0.06 | 1.00 | -3.1 | -225 / +0.0 | A | LEAD (w20 fails WF-family fails) |
| P7_lots_by_session | L6_all | P7 | +12.7/+17.7/+14.8/+21.3 | -4.4/-12.8 | +13.4 | -1586 | +7.7 | +7.7/+9.9/+16.7 | 20.55 | 0.18 | 0.01 | 1.00 | -3.1 | -12046 / -1882.7 | A | LEAD (w20 fails WF-family fails) |
| P7_lots_by_session | L6_nyam | P7 | +4.6/+6.1/+3.8/+7.8 | -12.9/-1.8 | +9.1 | +1126 | +8.2 | +8.2/+7.4/+11.3 | 20.65 | 0.03 | 0.01 | 1.00 | -3.1 | -1898 / +0.0 | A | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N30min_f0.0 | P7 | +2.7/-10.7/+4.4/+9.8 | -7.0/-3.8 | +9.3 | +843 | +5.4 | +5.4/+7.1/+12.3 | 20.05 | 0.01 | 0.01 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_lots_by_session | L5_nyam | P7 | +2.1/+6.9/+3.7/+8.0 | -11.4/-1.6 | +8.7 | +734 | +4.5 | +4.5/+6.1/+10.3 | 19.85 | 0.04 | 0.19 | 1.00 | -3.1 | -4299 / +0.0 | A | dd-only (placebo p 0.19) |
| P7_lots_by_session | L6_london | P7 | +6.0/-1.2/+10.5/+4.0 | -5.0/-6.7 | +8.0 | -4 | +6.0 | +6.0/+10.5/+4.0 | 20.18 | 0.06 | 0.20 | 1.00 | -3.1 | +1418 / +0.0 | A | dd-only (placebo p 0.20) |
| P7_after_P7_stop | same_session_N60min_f0.5 | P7 | +1.3/+1.6/+10.5/+2.5 | -3.7/-3.8 | +6.0 | +467 | +2.9 | +2.9/+11.9/+4.0 | 19.53 | 0.01 | 0.03 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N60min_f0.0 | P7 | +6.6/-2.9/+28.7/-0.0 | -8.3/-9.1 | +11.7 | +866 | +9.3 | +9.3/+30.8/+2.9 | 20.91 | 0.01 | 0.04 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N120min_f0.5 | P7 | +1.2/+0.7/+13.5/+1.1 | -3.2/-4.4 | +5.5 | +332 | +2.3 | +2.3/+14.5/+2.2 | 19.42 | 0.01 | 0.02 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N30min_f0.5 | P7 | +0.1/+0.8/+0.2/+6.1 | -3.7/-1.5 | +4.9 | +444 | +1.6 | +1.6/+1.7/+7.5 | 19.27 | 0.01 | 0.03 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N90min_f0.5 | P7 | -1.7/-2.4/+8.8/-0.6 | -3.4/-3.1 | +5.1 | +427 | -0.2 | -0.2/+10.1/+0.9 | 18.93 | 0.01 | 0.08 | 1.00 | -3.1 | +0 / +0.0 | B | no |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_lots_by_session | L4_nyam | P7 | +6.7/+13.1/+7.5/+13.8 | -23.5/-3.4 | +17.1 | +1860 | +12.3 | +12.3/+13.1/+18.9 | 21.62 | 0.04 | 0.04 | 1.00 | -3.1 | -6197 / +0.0 | A | LEAD (w20 fails WF-family fails) |
| P7_after_P7_stop | same_session_N30min_f0.0 | P7 | +2.7/-10.7/+4.4/+9.8 | -7.0/-3.8 | +9.3 | +843 | +5.4 | +5.4/+7.1/+12.3 | 20.05 | 0.01 | 0.01 | 1.00 | -3.1 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| P7_when_others_on | U7_sameside_f0.5 | P7 | +14.7/-4.2/+8.8/-10.3 | -2.3/-6.1 | +15.9 | -371 | +13.6 | +13.6/+7.6/-11.8 | 21.95 | 0.03 | 0.40 | 1.00 | -3.1 | +0 / +0.0 | B | no |
| P7_later_in_session | later_f0.5 | P7 | +13.7/+11.1/+29.1/+6.6 | +11.0/-19.7 | +8.8 | -5213 | -5.1 | -5.1/+13.7/-13.7 | 18.05 | 0.13 | 0.34 | 1.00 | -3.1 | -36947 / -1335.8 | B | no |
| P7_first_in_session | first_f0.5 | P7 | -1.7/+18.3/+1.1/+36.0 | +2.3/-10.7 | -24.2 | -8224 | -41.7 | -41.7/-37.8/+10.8 | 13.39 | 0.10 | 0.89 | 1.00 | -3.1 | +55 / +0.0 | B | no |


## Cells that dominate Q1-A on both mean and maxDD (down-only; L6M, HOLD and PRE; (a) at equal lots)

| technique | params | scope | (a) maxDD cut L6M/HOLD/PRE/X' | worst-20 cut L6M/PRE (a) | Ulcer cut L6M (b) | d mean L6M $/wk | (b) eq-mean maxDD cut L6M | (b) cut L6M/PRE/X' | Calmar L6M | lot-change share | placebo p (joint) | family p own-set | WF fam eq-cut | live d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| newentry_haircut_day_dd | Y6000_f0.0 | P7_sess_nyam | +23.8/+22.1/+15.7/-13.4 | -21.7/-6.5 | +22.1 | +835 | +26.0 | +26.0/+18.0/-10.3 | 25.61 | 0.03 | 0.65 | 1.00 | -24.2 | -9135 / +0.0 | B | no |
| total_lots_cap | cap4_skip | sess_nyam | +21.2/+15.9/+4.0/+31.6 | -37.7/-5.1 | +26.1 | +356 | +22.2 | +22.2/+5.1/+32.4 | 24.37 | 0.06 | 0.16 | 1.00 | -24.2 | -11810 / +0.0 | B | dd-only (placebo p 0.16) |
| total_lots_cap | cap4_skip | P7_sess_nyam | +18.8/+16.4/+5.7/+37.2 | -34.5/-5.2 | +24.1 | +200 | +19.3 | +19.3/+6.3/+37.7 | 23.50 | 0.03 | 0.12 | 1.00 | -24.2 | -12000 / +0.0 | B | dd-only (placebo p 0.12) |
| dayloss_stack$ | X3000_f0.00 | P7_sess_nyam | +16.5/+12.8/+7.9/-41.7 | -14.7/-5.5 | +18.0 | +348 | +17.5 | +17.5/+9.0/-40.0 | 22.98 | 0.02 | 0.96 | 1.00 | +37.2 | +0 / +0.0 | B | no |
| dayloss_stack$ | X3000_f0.00 | sess_nyam | +16.0/+11.1/+7.2/-44.4 | -17.7/-3.0 | +18.1 | +221 | +16.7 | +16.7/+7.9/-43.3 | 22.75 | 0.10 | 0.98 | 1.00 | +37.2 | +0 / +0.0 | B | no |
| total_lots_cap | cap4_trunc | sess_nyam | +14.0/+8.8/+2.2/+24.2 | -22.3/-2.9 | +21.1 | +1577 | +18.4 | +18.4/+7.2/+28.1 | 23.24 | 0.08 | 0.03 | 1.00 | -24.2 | -2210 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| consec_loss | book_k4_f0.00 | M7 | +13.7/+17.0/+15.3/-22.5 | -17.7/-10.5 | +23.5 | +562 | +15.4 | +15.4/+16.9/-20.2 | 22.40 | 0.21 | 0.16 | 1.00 | +37.2 | +0 / +0.0 | B | no |
| consec_loss | book_k2_f0.00 | M7 | +13.7/+17.0/+15.3/-25.7 | -17.7/-10.5 | +23.5 | +562 | +15.4 | +15.4/+16.9/-23.3 | 22.40 | 0.21 | 0.97 | 1.00 | +37.2 | -10660 / +0.0 | B | no |
| consec_loss | book_k5_f0.00 | M7 | +13.7/+17.0/+15.3/-23.5 | -17.7/-10.5 | +23.5 | +562 | +15.4 | +15.4/+16.9/-21.2 | 22.40 | 0.21 | 0.42 | 1.00 | +37.2 | +0 / +0.0 | B | no |
| consec_loss | book_k3_f0.00 | M7 | +13.7/+17.0/+15.3/-26.2 | -17.7/-10.5 | +23.5 | +562 | +15.4 | +15.4/+16.9/-23.8 | 22.40 | 0.21 | 0.99 | 1.00 | +37.2 | -10660 / +0.0 | B | no |
| newentry_haircut_day_dd | Y3000_f0.5 | sess_nyam | +13.5/+10.6/+7.5/-4.5 | -18.4/-4.8 | +15.8 | +1153 | +16.8 | +16.8/+11.1/-0.6 | 22.79 | 0.03 | 0.77 | 1.00 | -24.2 | -6368 / +0.0 | B | dd-only (placebo p 0.77) |
| newentry_haircut_day_dd | Y3000_f0.5 | P7_sess_nyam | +13.5/+10.6/+7.5/-4.5 | -18.4/-4.8 | +15.8 | +1153 | +16.8 | +16.8/+11.1/-0.6 | 22.79 | 0.03 | 0.62 | 1.00 | -24.2 | -6368 / +0.0 | B | dd-only (placebo p 0.62) |
| newentry_haircut_day_dd | Y6000_f0.5 | P7_sess_nyam | +13.5/+10.6/+7.5/-6.1 | -15.5/-4.0 | +15.4 | +1081 | +16.6 | +16.6/+10.8/-2.3 | 22.74 | 0.02 | 0.76 | 1.00 | -24.2 | -4568 / +0.0 | B | dd-only (placebo p 0.76) |
| newentry_haircut_day_dd | Y6000_f0.5 | sess_nyam | +13.5/+10.6/+7.5/-6.1 | -15.5/-4.0 | +15.4 | +1081 | +16.6 | +16.6/+10.8/-2.3 | 22.74 | 0.02 | 0.80 | 1.00 | -24.2 | -4568 / +0.0 | B | dd-only (placebo p 0.80) |
| newentry_haircut_day_dd | Y3000_f0.0 | M7 | +13.0/+16.3/+13.3/-10.9 | -12.5/-7.7 | +14.8 | +22 | +13.1 | +13.1/+13.4/-10.8 | 21.81 | 0.13 | 0.41 | 1.00 | -24.2 | -4265 / +0.0 | B | no |
| total_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+30.7 | -27.3/-3.4 | +26.3 | +2318 | +19.3 | +19.3/+12.7/+35.8 | 23.51 | 0.03 | 0.01 | 1.00 | -24.2 | +715 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| total_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+37.0 | -26.1/-5.3 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+41.6 | 23.49 | 0.02 | 0.01 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9/+14.3/+5.7/+35.4 | -26.1/-4.7 | +25.2 | +2299 | +19.3 | +19.3/+12.6/+40.2 | 23.49 | 0.02 | 0.02 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| same_side_lots_cap | cap6_skip | sess_nyam | +12.9/+14.3/+5.7/+33.0 | -26.5/-4.7 | +25.7 | +2240 | +19.1 | +19.1/+12.4/+37.8 | 23.45 | 0.02 | 0.02 | 1.00 | -24.2 | +0 / +0.0 | B | LEAD (w20 fails WF-family fails) |
| newentry_haircut_day_dd | Y10000_f0.0 | P7_sess_nyam | +12.1/+22.1/+15.7/-18.8 | -15.1/-8.8 | +17.9 | +767 | +14.4 | +14.4/+17.9/-15.7 | 22.15 | 0.02 | 0.64 | 1.00 | -24.2 | -12000 / +0.0 | B | no |


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
| consec_loss | book_k4_f0.00 | sess_london | +6.8 | +1277 | +236 | +10.7 |
| week_loss_stack | X20000_f0.00 | P7_sess_nyam | +10.9 | +2007 | +231 | +16.6 |
| total_lots_cap | cap4_trunc | P7_sess_nyam | +7.9 | +1434 | +228 | +12.2 |
| total_lots_cap | cap6_skip | sess_nyam | +12.9 | +2318 | +225 | +19.3 |
| same_side_lots_cap | cap6_skip | P7_sess_nyam | +12.9 | +2299 | +223 | +19.3 |
| total_lots_cap | cap6_skip | P7_sess_nyam | +12.9 | +2299 | +223 | +19.3 |
| same_side_lots_cap | cap10_skip | sess_london | +8.0 | +1416 | +222 | +12.2 |


## P7 section (K slice, P7 maxDD $0 L6M in the stack list; P7-alone equal-mean frontier = P7-only series scaled to Q1-A P7 L6M mean)

| family | technique | params | scope | P7-alone (a) maxDD cut L6M | P7-alone (b) cut L6M/PRE/X' | P7 d mean L6M | stack (b) cut L6M/PRE/X' | placebo p | label |
|--|--|--|--|--|--|--|--|--|--|
| C | volparity_down | win60_refmin | P7 | +89.2 | +69.9/+12.4/-63.5 | +5075 | -14.3/+6.7/-34.6 | 0.43 | no |
| C | volparity_down | win20_refmin | P7 | +89.2 | +69.9/+12.4/+8.4 | +5075 | -14.3/+6.7/+23.3 | 0.08 | no |
| C | esparity_down | last50tr_refmin | P7 | +89.2 | +69.9/+12.4/+21.7 | +5075 | -14.3/+6.7/+27.9 | 0.13 | no |
| C | volparity_down | win120_refmed | P7 | +89.2 | +69.9/-3.7/-46.6 | +5075 | -14.3/-10.9/-26.8 | 0.22 | no |
| C | volparity_down | win120_refmin | P7 | +89.2 | +69.9/+12.4/-46.6 | +5075 | -14.3/+6.7/-26.8 | 0.29 | no |
| C | esparity_down | last200tr_refmin | P7 | +89.2 | +69.9/+12.4/+14.2 | +5075 | -14.3/+6.7/+21.8 | 0.16 | no |
| C | esparity_down | last100tr_refmin | P7 | +89.2 | +69.9/+12.4/+14.2 | +5075 | -14.3/+6.7/+21.8 | 0.11 | no |
| C | riskcap_per_trade | R$2400 | P7 | +80.3 | +68.2/+33.8/+50.5 | +8790 | +10.6/+17.2/+32.0 | 0.01 | LEAD (w20 fails WF-family fails) |
| C | riskcap_per_trade | R$3600 | P7 | +72.5 | +67.9/+32.7/+40.4 | +12176 | +15.5/+17.6/+19.7 | 0.01 | LEAD (w20 fails WF-family fails) |
| C | volparity_down | win20_refmed | P7 | +88.3 | +67.2/-4.4/-22.5 | +5045 | -21.5/-11.1/+4.6 | 0.16 | no |
| D | eqdd_book_20d_R | Y2R_f0.25_sticky | P7 | +73.3 | +63.3/+36.8/+50.5 | +10319 | +16.3/+25.3/+45.1 | 0.01 | LEAD (w20 fails) |
| E | same_side_lots_cap | cap6_skip | P7 | +69.4 | +62.9/-15.5/+41.8 | +11716 | +9.3/+27.1/+21.4 | 0.01 | LEAD (w20 fails WF-family fails) |
| D | eqdd_book_20d_R | Y4R_f0.25_sticky | P7 | +63.2 | +61.7/+33.9/+53.6 | +13635 | +18.6/+35.7/+45.8 | 0.01 | LEAD (w20 fails) |
| C | volparity_down | win60_refmed | P7 | +85.6 | +58.7/-6.0/-77.1 | +4967 | -15.2/-11.7/-38.8 | 0.43 | no |
| C | riskcap_per_trade | R$4800 | P7 | +60.7 | +57.4/+8.7/+14.2 | +13076 | -3.7/-2.1/-5.6 | 0.19 | no |
| E | total_lots_cap | cap6_skip | P7 | +69.4 | +56.6/-19.1/+37.4 | +10000 | +1.2/+20.7/+15.9 | 0.05 | LEAD (w20 fails WF-family fails) |
| D | week_loss_stack | X20000_f0.00 | P7_sess_nyam | +38.3 | +55.1/+42.1/+6.6 | +19494 | +16.6/+24.3/-20.7 | 0.80 | no |
| E | same_side_lots_cap | cap4_skip | P7 | +79.3 | +54.3/-152.0/+19.8 | +6443 | +3.2/-49.5/-1.5 | 0.36 | no |
| D | eqdd_book_20d_R | Y1R_f0.25_live | P7 | +68.2 | +52.6/-1.6/+21.9 | +9513 | +10.1/+24.6/+13.8 | 0.02 | LEAD (w20 fails) |
| D | week_loss_stack | X10000_f0.00 | P7_sess_nyam | +33.0 | +51.3/+35.0/-3.6 | +19531 | +16.2/+20.7/-36.4 | 0.93 | no |


## Exact-driver finalists (<=12, down-only, by 18:00Z): autopilot/SZ_CDE_FINALISTS.csv (12 rows).


| id | label |
|--|--|
| D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | LEAD (w20 fails) |
| E ; max_books_on ; n1_f0.5 ; sess_london | LEAD (w20 fails WF-family fails) |
| D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | LEAD (w20 fails) |
| C ; riskcap_per_trade ; R$3600 ; P7 | LEAD (w20 fails WF-family fails) |
| D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | LEAD (w20 fails) |
| D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | LEAD (w20 fails) |
| E ; same_side_lots_cap ; cap6_trunc ; sess_london | LEAD (w20 fails WF-family fails) |
| D ; eqdd_stack_20d ; Y30000_f0.25_sticky ; sess_nyam | LEAD (w20 fails) |
| E ; total_lots_cap ; cap6_skip ; sess_nyam | LEAD (w20 fails WF-family fails) |
| E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | LEAD (w20 fails WF-family fails) |
| E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | LEAD (w20 fails WF-family fails) |
| K ; P7_lots_by_session ; L4_nyam ; P7 | LEAD (w20 fails WF-family fails) |


NOT first-order scorable (exact driver only): StackCutPct 0-100 x sessions and StackAsiaOnly variants; lock/give-back values looser than live (win cap 6-8R, give-back arm 3R/keep .3, floor 14-16R); every re-entry-dependent cell needs state_sizer_b-style engine support (the current exact driver patches only the ER lots step: rules D/E need a new engine hook = v1.6-style code, flagged to lead).


M_CDE.npz row alignment spot-check (M x base P&L in C.prepare(C.load_trades) order, maxDD re-derived on L6M/PRE/X' must equal the ledger): C|riskcap_per_trade|R$2400|P7 L6M maxDD 44621 vs ledger 44621 OK; D|week_loss_book_R|X2R_f0.00|P7_sess_london L6M maxDD 71799 vs ledger 71799 OK; K|P7_after_P7_stop|same_session_N120min_f0.5|P7 L6M maxDD 78932 vs ledger 78932 OK. Windows: the COMB list ends with label day 20261030 (2026-10-31 is a Saturday, base_b has no later trade), so L1M-L3M end there and the live weeks 11-01..05 are only in the held-out live-week columns.


## Exact-engine status of the finalists (hook code/th_sz_cde/cde_exact.py; regression month 202304 with a never-firing rule == S1-COMB; 2 workers; order: six best (F00 F01 F03 F11 F02 F04) on L6M, PRE, X', then the other six, HOLD last). EXACT-CONFIRMED = exact maxDD cut > 0 on every window that is complete; a window shown as na is not run yet; every other cell in this page is FIRST-ORDER ONLY.

| set | cell | L6M exact cut / first-order cut | PRE exact / FO | X' exact / FO | L6M d mean exact / FO | HOLD exact / FO | status |
|--|--|--|--|--|--|--|--|
| CDE_F00 | D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | +24.0 / +46.6 | na / na | na / na | -8998.6 / -8535.1 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F01 | E ; max_books_on ; n1_f0.5 ; sess_london | +25.8 / +27.5 | na / na | na / na | +800.3 / +145.4 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F02 | D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | +10.7 / +30.3 | na / na | na / na | -9137.8 / -4178.8 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F03 | C ; riskcap_per_trade ; R$3600 ; P7 | +18.9 / +37.4 | na / na | na / na | -12096.0 / -7558.3 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F04 | D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | +30.2 / +29.8 | na / na | na / na | -1576.1 / +15.5 | na / na | EXACT-CONFIRMED on L6M (partial) |
| CDE_F05 | D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F06 | E ; same_side_lots_cap ; cap6_trunc ; sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F07 | D ; eqdd_stack_20d ; Y30000_f0.25_sticky ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F08 | E ; total_lots_cap ; cap6_skip ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F09 | E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F10 | E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F11 | K ; P7_lots_by_session ; L4_nyam ; P7 | +12.6 / +6.7 | na / na | na / na | +2788.0 / +1860.2 | na / na | EXACT-CONFIRMED on L6M (partial) |


Cross-check vs sz_core (Z.score on the 12 finalists + top 20, M_CDE arrays): maxDD L6M and PRE identical (max abs diff 0 $). Means and equal-mean cuts differ by ~4k $/wk and a few points because this page ends the windows at label day 2026-10-30 (last day of the COMB trade list; 10-31 is a Saturday) while sz_core runs its calendar to 2026-11-05 and counts the empty weeks (zero P&L) in L1M-L6M means. Exact-run cut numbers use this page's windows.


## Exact vs first-order, L6M (first exact result, 2026-11-09 15:35Z; six priority finalists, L6M months 2026-05..10 complete; PRE and X' running)
Survive in the engine (exact L6M maxDD cut about the first-order cut, equal-mean cut positive): E max_books_on n1 f0.5 on the London session (exact +25.8% vs FO +27.5%, d mean +800 $/wk, equal-mean +27.8%); D eqdd_stack_20d Y20000 f0.25 sticky on London (exact +30.2% vs FO +29.8%, d mean -1.6k, equal-mean +26.2%); K P7 lots cap 4 in NYAM (exact +12.6% vs FO +6.7%, d mean +2.8k, equal-mean +20.2%).
Deflate and fail at equal mean: D eqdd_book_20d_R Y1R f0.50 sticky ALL (FO +46.6% -> exact +24.0%; d mean -9.0k; equal-mean -9.9%: the first-order cut was mostly size-down); D eqdd_book_20d_R Y4R f0.25 P7 (FO +30.3% -> +10.7%, equal-mean -30.1%); C riskcap R$3600 on P7 (FO +37.4% -> +18.9%, equal-mean -38.7%).
So the broad/book-level state and risk-cap cells lose half or more of the first-order cut in the engine and do not beat size-down at equal mean; the session-scoped London/NYAM cells survive on L6M only. PRE and X' not yet exact; no cell is a candidate on L6M alone.
