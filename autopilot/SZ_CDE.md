> **FIRST-ORDER SCREEN ONLY: every number on this page that is not in the "Exact-engine status" table is a first-order screen (pnl per planned lot x new lots, realized-only state); it is NOT a verdict (Addendum 1). Exact-engine rows: six finalists, L6M then PRE, X', HOLD.**

> **TESTING DEFECT FOUND AND FIXED (Addendum 1 c).** The identical-to-the-dollar test between bases flagged 4 cells (D consec_loss, stack level, f=0, k=2..5): maxDD 0 on every base. Cause: my rule's loss counter reset only after a win, so a book or stack that was skipped could never trade or win again (permanent lock-out, all P&L 0 from the first trigger on). It was a rule-semantics bug, not a cached trade list: base lists differ (see base-change proof below). Fix (DECISIONS.md line at 16:2xZ): consecutive-loss and consecutive-win counters reset at the label-day roll. All three bases and this page were re-scored after the fix; the re-run check result is the first line of the base-comparison section.

> **ROLL-EXCL (lead 17:35Z): every first-order and exact number on this page excludes the 31 base trades (of the 33 listed in roll_bracket_trades.csv; 2 listed rows are not in the COMB list) alive across a contract roll (key book + entry second +-2 s); their P&L is zeroed before state and scoring. Engine-internal state of the exact runs (lock/cooldown/equity states) still saw those artifact P&L jumps; the 14 roll days are checked in the lock/cooldown exact runs on the R1 page.**

# SZ-CDE - families C (parity), D (equity-curve/state/locks), E (exposure), K slice (P7)  - 2026-11-10 13:57Z

**Label: first-order on base S1b-COMB (live D7 v1.5 with the seven state-cut lines), 21135 trades 2023-04..2026-10 (last label day 20261030; the 2026-11-01..05 live weeks are not in the list, so L1M/L2M/L3M windows end 2026-10-30); entries not live-matched; in-sample; PRE-PROOF; post-hoc; Shadow only; no PASS claims.** Reference = Q1-A (the base lots). 3274 cells (C 140, D 1980, E 1110, K 44). Prereg: autopilot/SZ_CDE_PREREG.md (sha in DECISIONS.md).

Reading guide: (a) = cell vs Q1-A at equal lots (maxDD cut % = positive is shallower; d mean $/wk L6M). (b) = every cell scaled by one global factor so its L6M mean equals Q1-A (0 $/wk), then maxDD / worst-20 / Ulcer cut vs Q1-A; size-down-everything scores 0 by construction. Class A = lots-only static (first-order valid); B = skips/state (ranking valid, mean not, exact re-run needed for re-entries); C = lock/give-back/week-floor (engine marks open P&L and flattens: first-order is a skip-only proxy ON TOP of the base that already holds the live locks; loosened values and StackCutPct x sessions are exact-driver only). State for D/E = realized P&L of cell-sized trades with exit < signal second (open P&L not in any state). Placebo = donor multipliers reassigned to random trades in the same book x session (100 draws; stat = min of (b) cut over L6M, PRE, X'). Family p = max over the whole CDE set (3274 cells) per draw. WF = monthly 2024-01..2026-10, 26 trailing weeks, 7-day embargo, picks the best trailing equal-mean maxDD cell, OOS maxDD cut at equal mean shown per family.

> **STANDING RULES 2/2a (recents first):** ranking key = 0.5 x L6M + 0.3 x L3M + 0.2 x L1M equal-mean maxDD cut; the bi-weekly re-pick walk-forward (26 weeks train -> next 2 weeks, 7-day purge, sz_core.wf_biweekly) is the primary OOS column; PRE/X' is tolerant (sz_core.prior_info: allowed PRE deepening = min(25, L6M cut + 10)% only when the bi-weekly WF beats live in >= 60% of refit periods, else 15%; PRE mean floor -1k/wk); worse = RECENT-ONLY (reported, never killed). Bi-weekly WF here is per FAMILY (the picker chooses among the family's down-only cells, reference = Q1-A); first-order screen only.

## Headline

- Cells on the bar (CANDIDATE-DD, first-order, all still need the EXACT engine): 7; LEADs (equal-mean maxDD lower on L6M, PRE and X' with placebo p<=.10 but another gate fails): 91. Cells that dominate Q1-A on BOTH mean and maxDD (L6M, HOLD, PRE; down-only): 289.

- WF of the picking procedure (OOS 2024-01..2026-10, 148 weeks): ALL_CDEK: OOS maxDD cut +16% raw / -35% at equal mean (d mean -6331 $/wk); C: OOS maxDD cut +32% raw / +0% at equal mean (d mean -5217 $/wk); D: OOS maxDD cut +36% raw / +16% at equal mean (d mean -4086 $/wk); E: OOS maxDD cut +31% raw / -1% at equal mean (d mean -5231 $/wk); K: OOS maxDD cut +27% raw / +15% at equal mean (d mean -2306 $/wk); D_state_only: OOS maxDD cut +36% raw / +16% at equal mean (d mean -3996 $/wk); E_ALL_scope: OOS maxDD cut +14% raw / -32% at equal mean (d mean -5771 $/wk); D_ALL_scope: OOS maxDD cut +20% raw / -14% at equal mean (d mean -4941 $/wk).

- Live week (frozen file, 180 DS7-book trades): Q1-A total +104810, trade-level maxDD $14,490; the week has no stack losing day, so it cannot separate cells; columns show d total and d trade-level dd vs Q1-A.

- Family C best (down-only, ranked by the joint equal-mean cut): riskcap_per_trade R$3600 on scope P7 cuts L6M maxDD 37% at equal lots (d mean -7611 $/wk) and 15% / 17% / 20% at equal mean on L6M / PRE / X'; placebo p 0.01, family p 1.00; family WF OOS equal-mean cut +0%; LEAD-RECENT (w20 fails ).
- Family D best (down-only, ranked by the joint equal-mean cut): consec_loss stack_k4_f0.00 on scope ALL cuts L6M maxDD 39% at equal lots (d mean -2521 $/wk) and 33% / 20% / -57% at equal mean on L6M / PRE / X'; placebo p 0.71, family p 1.00; family WF OOS equal-mean cut +16%; recent-only dd (placebo p 0.71).
- Family E best (down-only, ranked by the joint equal-mean cut): total_lots_cap cap4_skip on scope sess_london cuts L6M maxDD 39% at equal lots (d mean -3420 $/wk) and 30% / 39% / 1% at equal mean on L6M / PRE / X'; placebo p 0.20, family p 1.00; family WF OOS equal-mean cut -1%; recent-only dd (placebo p 0.20).
- Family K best (down-only, ranked by the joint equal-mean cut): P7_when_others_on U7_sameside_f0.0 on scope P7 cuts L6M maxDD 29% at equal lots (d mean -2012 $/wk) and 24% / 13% / -35% at equal mean on L6M / PRE / X'; placebo p 0.41, family p 1.00; family WF OOS equal-mean cut +15%; recent-only dd (placebo p 0.41).


## C. Equal-risk / parity

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 128 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+37.4/+48.2/+32.1/+39.0/+40.5 | -61.0/-7.9 | +19.0 | -7611 | +15.4/+15.4/+29.9 | +17.5/+19.5 | 22.45 | 0.19 | 0.01 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | -40358 / -3076.2 | A | LEAD-RECENT (w20 fails ) |
| riskcap_per_trade | R$2400 | P7 | +44.2/+44.2/+53.3/+45.3/+48.3/+56.9 | -61.4/-7.5 | +14.0 | -10997 | +10.4/+10.4/+25.1 | +17.1/+30.8 | 21.20 | 0.21 | 0.02 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -48%) [old -1k rule: RECENT-ONLY] | -54807 / -1390.8 | A | LEAD-RECENT (w20 fails ) |
| riskcap_per_trade | R$3600 | ALL | +31.0/+31.0/+49.1/+34.2/+42.1/+49.8 | -52.7/-5.1 | +11.6 | -8566 | +2.3/+2.3/+27.9 | +18.0/+29.0 | 19.44 | 0.22 | 0.01 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -42%) [old -1k rule: RECENT-ONLY] | -38377 / -5021.2 | A | no |
| volparity_down | win120_refmed | ALL | +55.9/+57.6/+74.4/+39.2/+46.4/+40.5 | -56.7/+15.6 | +3.7 | -16626 | -2.6/+1.4/+40.6 | -24.6/-38.3 | 18.52 | 0.30 | 0.36 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -46%) [old -1k rule: RECENT-ONLY] | na / na | A | no |
| volparity_down | win60_refmed | U7 | +7.1/+7.1/+7.9/+4.1/+0.0/-1.6 | +5.3/+4.1 | -2.9 | -1260 | +2.9/+2.9/+3.7 | -4.5/-6.1 | 19.56 | 0.04 | 0.19 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 17%, deeper -0%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| volparity_down | win20_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/-0.4 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+0.6 | 19.59 | 0.03 | 0.19 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| volparity_down | win120_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+1.9 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+2.9 | 19.59 | 0.03 | 0.02 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| volparity_down | win60_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+0.3 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+1.3 | 19.59 | 0.03 | 0.05 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| esparity_down | last100tr_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+0.6 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+1.7 | 19.59 | 0.03 | 0.02 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| esparity_down | last50tr_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+0.6 | -4.9/-4.4 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+1.7 | 19.59 | 0.03 | 0.07 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| esparity_down | last200tr_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+0.6 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+1.7 | 19.59 | 0.03 | 0.07 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| volparity_down | win120_refmed | U7 | +4.1/+4.1/+7.9/+4.9/+1.5/-7.5 | +4.2/+3.7 | -1.4 | -1117 | +0.3/+0.3/+4.2 | -2.4/-11.7 | 19.05 | 0.04 | 0.38 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -1%) [old -1k rule: OK-PRIOR] | na / na | A | no |
| volparity_down | win60_refmed | ALL | +55.7/+59.1/+65.2/+36.2/+49.2/+34.2 | -45.6/+14.9 | -4.3 | -16998 | -6.1/+2.0/+16.6 | -21.6/-57.4 | 17.90 | 0.30 | 0.61 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -49%) [old -1k rule: RECENT-ONLY] | na / na | A | no |
| riskcap_per_trade | R$4800 | ALL | +20.0/+20.0/+37.1/+14.0/+21.2/+19.6 | -50.6/+7.3 | +1.6 | -6711 | -3.9/-3.9/+18.3 | -2.3/-4.4 | 18.28 | 0.08 | 0.14 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -21%) [old -1k rule: RECENT-ONLY] | -27016 / -3162.1 | A | no |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| riskcap_per_trade | R$3600 | P7 | +37.4/+37.4/+48.2/+32.1/+39.0/+40.5 | -61.0/-7.9 | +19.0 | -7611 | +15.4/+15.4/+29.9 | +17.5/+19.5 | 22.45 | 0.19 | 0.01 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | -40358 / -3076.2 | A | LEAD-RECENT (w20 fails ) |
| volparity_down | win120_refmed | ALL | +55.9/+57.6/+74.4/+39.2/+46.4/+40.5 | -56.7/+15.6 | +3.7 | -16626 | -2.6/+1.4/+40.6 | -24.6/-38.3 | 18.52 | 0.30 | 0.36 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -46%) [old -1k rule: RECENT-ONLY] | na / na | A | no |
| esparity_down | last100tr_refmin | M7 | +2.0/+2.0/+1.9/+3.4/+3.6/+0.6 | -4.9/-4.5 | +7.7 | +305 | +3.0/+3.0/+2.9 | +4.6/+1.7 | 19.59 | 0.03 | 0.02 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | na / na | A | no |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| volparity_up | win60_refmed_clip.5-1.5 | ALL | +35.0/+46.1/+51.4/+28.9/+45.3/+21.0 | -30.6/-18.6 | +27.0 | -6463 | +16.5/+30.8/+37.6 | +29.7/-1.5 | 22.76 | 0.39 | 0.30 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -45%) [old -1k rule: OK-PRIOR] | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$2400(up-allowed) | ALL | +14.6/+14.6/+49.5/+15.0/+39.1/+58.6 | -31.8/-13.3 | +8.4 | -5172 | -3.8/-3.8/+38.6 | +26.0/+49.7 | 18.30 | 0.85 | 0.03 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | -31394 / -4663.6 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win120_refmed_clip.5-1.5 | ALL | +35.5/+41.9/+43.8/+32.1/+36.7/+25.1 | -55.2/+5.2 | +3.9 | -10863 | -2.7/+7.4/+10.5 | -0.8/-19.2 | 18.50 | 0.39 | 0.50 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -37%) [old -1k rule: OK-PRIOR] | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$3600(up-allowed) | ALL | -26.5/-26.5/+22.4/-29.0/+8.5/+41.3 | -39.9/-9.5 | +4.4 | +5143 | -7.6/-7.6/+34.0 | +22.2/+50.1 | 17.66 | 0.98 | 0.01 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 15%, deeper -8%) [old -1k rule: OK-PRIOR] | +5643 / +597.1 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmin_clip.5-1.5 | ALL | +47.5/+47.5/+47.4/+43.9/+43.3/+52.7 | -43.5/+12.5 | +1.2 | -14157 | -1.9/-1.9/-2.1 | -10.0/+8.2 | 18.63 | 0.39 | 0.29 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -43%) [old -1k rule: RECENT-ONLY] | na / na | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win60_refmin_clip.5-1.5 | ALL | +47.5/+47.5/+47.4/+43.9/+43.3/+27.8 | -43.5/+12.5 | +1.2 | -14158 | -2.0/-2.0/-2.1 | -10.1/-40.1 | 18.63 | 0.39 | 0.80 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -43%) [old -1k rule: RECENT-ONLY] | na / na | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win120_refmin_clip.5-1.5 | ALL | +47.5/+47.5/+47.4/+43.9/+43.3/+26.0 | -43.5/+12.5 | +1.2 | -14158 | -2.0/-2.0/-2.1 | -10.1/-43.7 | 18.63 | 0.38 | 0.81 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -43%) [old -1k rule: RECENT-ONLY] | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$1200(up-allowed) | ALL | +58.9/+58.9/+72.9/+56.0/+69.3/+80.2 | -54.7/-2.8 | -2.8 | -18661 | -13.9/-13.9/+24.9 | +15.0/+45.0 | 16.67 | 0.42 | 0.06 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 25%, deeper -69%) [old -1k rule: RECENT-ONLY] | -67772 / -9229.3 | A | UP-ALLOWED report row (never promoted) |
| volparity_up | win20_refmed_clip.5-1.5 | ALL | +33.9/+33.9/+33.8/+33.5/+48.7/+39.9 | -47.3/+5.6 | -9.1 | -11625 | -9.9/-9.9/-10.0 | +14.7/+0.2 | 17.29 | 0.39 | 0.43 | 1.00 | +69.0 / -9035 / 97% | OK-PRIOR (allow 25%, deeper -49%) [old -1k rule: RECENT-ONLY] | na / na | A | UP-ALLOWED report row (never promoted) |
| equal_risk_all_books | R$6000(up-allowed) | ALL | -111.9/-111.9/-28.1/-114.0/-52.4/-0.1 | -58.0/+2.9 | -8.7 | +21242 | -22.7/-22.7/+25.9 | +11.8/+42.1 | 15.49 | 0.99 | 0.01 | 1.00 | +69.0 / -9035 / 97% | RECENT-ONLY (allow 15%, deeper +52%) [old -1k rule: RECENT-ONLY] | +79059 / +10423.6 | A | UP-ALLOWED report row (never promoted) |


## D. Equity-curve / state / locks (down-only ranked; up-allowed and anti-martingale in the report rows below)

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1966 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| consec_loss | stack_k4_f0.00 | ALL | +39.0/+88.3/+100.0/-22.6/+26.9/-43.2 | -51.3/-9.6 | +52.5 | -2521 | +33.3/+87.2/+100.0 | +20.0/-56.7 | 28.47 | 0.32 | 0.71 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -27%) [old -1k rule: OK-PRIOR] | -84210 / -2675.0 | B | recent-only dd (placebo p 0.71) |
| consec_loss | stack_k5_f0.00 | ALL | +33.6/+52.3/+100.0/+33.4/+46.8/-42.6 | -44.0/-17.5 | +37.8 | +413 | +34.5/+53.0/+100.0 | +47.5/-40.6 | 29.00 | 0.22 | 0.63 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -47%) [old -1k rule: OK-PRIOR] | -5710 / +0.0 | B | recent-only dd (placebo p 0.63) |
| consec_loss | stack_k2_f0.00 | sess_london | +44.1/+53.6/+53.6/-49.9/+32.0/+8.6 | -3.1/-16.8 | +44.4 | -1673 | +40.7/+50.8/+50.8 | +27.9/+3.0 | 32.03 | 0.16 | 0.22 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -32%) [old -1k rule: OK-PRIOR] | +8860 / +0.0 | B | recent-only dd (placebo p 0.22) |
| consec_loss | stack_k4_f0.00 | sess_london | +39.7/+43.1/+43.0/-20.2/+18.6/-6.4 | -0.4/-6.3 | +44.0 | -422 | +38.8/+42.2/+42.2 | +17.4/-8.0 | 31.04 | 0.09 | 0.26 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -19%) [old -1k rule: OK-PRIOR] | +5150 / +0.0 | B | recent-only dd (placebo p 0.26) |
| week_loss_stack | X20000_f0.00 | ALL | +44.2/+44.2/+46.1/+13.8/+13.9/-39.1 | -4.2/-24.9 | +43.7 | -2097 | +39.9/+39.9/+42.0 | +7.2/-49.9 | 31.61 | 0.24 | 0.38 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -14%) [old -1k rule: RECENT-ONLY] | +0 / +0.0 | B | recent-only dd (placebo p 0.38) |
| consec_loss | stack_k5_f0.00 | sess_london | +31.5/+31.5/+38.1/-6.0/+18.8/-5.2 | -10.4/-10.7 | +42.3 | +1412 | +34.7/+34.7/+41.0 | +22.6/-0.4 | 29.09 | 0.06 | 0.15 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -19%) [old -1k rule: OK-PRIOR] | +5595 / +0.0 | B | recent-only dd (placebo p 0.15) |
| consec_loss | stack_k3_f0.00 | sess_london | +38.2/+44.7/+44.6/-41.7/+12.4/+14.7 | +2.2/-6.8 | +36.1 | -2564 | +32.3/+39.3/+39.3 | +4.0/+6.5 | 28.05 | 0.12 | 0.16 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -12%) [old -1k rule: OK-PRIOR] | +5385 / +0.0 | B | recent-only dd (placebo p 0.16) |
| week_loss_stack | X20000_f0.00 | sess_london | +26.6/+26.6/+38.7/-21.0/+24.8/-8.4 | -25.6/-21.6 | +41.0 | +2815 | +33.1/+33.1/+44.1 | +31.4/+1.1 | 28.38 | 0.05 | 0.05 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -25%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| consec_loss | book_k3_f0.00 | ALL | +35.1/+40.5/+58.8/+26.2/+44.3/-7.3 | -10.8/-11.6 | +24.1 | -3122 | +27.4/+33.4/+53.9 | +37.7/-20.1 | 26.16 | 0.14 | 0.45 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -44%) [old -1k rule: OK-PRIOR] | -72285 / -2365.0 | B | recent-only dd (placebo p 0.45) |
| dayloss_stack$ | X16000_f0.00 | ALL | +29.9/+29.9/+37.5/-8.6/+18.1/+4.1 | -30.6/-10.8 | +35.3 | +498 | +31.1/+31.1/+38.6 | +19.4/+5.7 | 27.58 | 0.09 | 0.03 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -18%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| lock_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +29.6/+29.6/+78.5/+8.2/+38.5/-2.3 | -8.2/-7.5 | +40.7 | -3447 | +20.2/+20.2/+75.6 | +30.2/-16.0 | 23.80 | 0.07 | 0.40 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -38%) [old -1k rule: OK-PRIOR] | -59435 / -5860.0 | C | recent-only dd (placebo p 0.40) |
| dayloss_book_R | X0.5R_f0.00 | sess_london | +29.1/+34.5/+34.5/-46.4/+15.7/-6.1 | -10.8/-15.7 | +23.4 | -558 | +27.7/+33.2/+33.2 | +14.1/-8.2 | 26.27 | 0.10 | 0.32 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -16%) [old -1k rule: OK-PRIOR] | -11020 / +0.0 | B | recent-only dd (placebo p 0.32) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_london | +29.8/+29.8/+29.7/-25.1/+43.4/+12.8 | -16.5/-23.3 | +27.2 | -47 | +29.6/+29.6/+29.6 | +43.3/+12.7 | 27.00 | 0.10 | 0.04 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -43%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| consec_loss | book_k3_f0.00 | P7 | +30.6/+31.8/+47.2/-17.1/+38.6/-6.4 | -4.1/-8.7 | +23.4 | -2200 | +25.0/+26.3/+42.9 | +33.6/-15.1 | 25.32 | 0.03 | 0.34 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | -52215 / +0.0 | B | recent-only dd (placebo p 0.34) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| consec_loss | stack_k4_f0.00 | ALL | +39.0/+88.3/+100.0/-22.6/+26.9/-43.2 | -51.3/-9.6 | +52.5 | -2521 | +33.3/+87.2/+100.0 | +20.0/-56.7 | 28.47 | 0.32 | 0.71 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -27%) [old -1k rule: OK-PRIOR] | -84210 / -2675.0 | B | recent-only dd (placebo p 0.71) |
| week_loss_stack | X20000_f0.00 | ALL | +44.2/+44.2/+46.1/+13.8/+13.9/-39.1 | -4.2/-24.9 | +43.7 | -2097 | +39.9/+39.9/+42.0 | +7.2/-49.9 | 31.61 | 0.24 | 0.38 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -14%) [old -1k rule: RECENT-ONLY] | +0 / +0.0 | B | recent-only dd (placebo p 0.38) |
| dayloss_stack$ | X16000_f0.00 | ALL | +29.9/+29.9/+37.5/-8.6/+18.1/+4.1 | -30.6/-10.8 | +35.3 | +498 | +31.1/+31.1/+38.6 | +19.4/+5.7 | 27.58 | 0.09 | 0.03 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -18%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| lock_combo | win3_loss1_arm1_keep0.5_floor8 | P7 | +29.6/+29.6/+78.5/+8.2/+38.5/-2.3 | -8.2/-7.5 | +40.7 | -3447 | +20.2/+20.2/+75.6 | +30.2/-16.0 | 23.80 | 0.07 | 0.40 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -38%) [old -1k rule: OK-PRIOR] | -59435 / -5860.0 | C | recent-only dd (placebo p 0.40) |
| dayloss_book_R | X0.5R_f0.00 | sess_london | +29.1/+34.5/+34.5/-46.4/+15.7/-6.1 | -10.8/-15.7 | +23.4 | -558 | +27.7/+33.2/+33.2 | +14.1/-8.2 | 26.27 | 0.10 | 0.32 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -16%) [old -1k rule: OK-PRIOR] | -11020 / +0.0 | B | recent-only dd (placebo p 0.32) |
| eqdd_stack_20d | Y20000_f0.25_sticky | sess_london | +29.8/+29.8/+29.7/-25.1/+43.4/+12.8 | -16.5/-23.3 | +27.2 | -47 | +29.6/+29.6/+29.6 | +43.3/+12.7 | 27.00 | 0.10 | 0.04 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -43%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| lock_daycap_loss | loss1R(live2) | P7 | +25.7/+25.7/+39.1/+8.2/+17.0/+6.1 | -22.3/-10.0 | +38.5 | +47 | +25.8/+25.8/+39.2 | +17.1/+6.3 | 25.61 | 0.04 | 0.01 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -17%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | C | LEAD-RECENT (w20 fails ) |
| eqdd_book_20d_R | Y1R_f0.50_sticky | ALL | +46.6/+48.9/+48.9/+40.8/+44.6/+47.4 | -5.3/-16.7 | +26.1 | -8363 | +25.1/+28.4/+28.4 | +22.3/+26.3 | 25.37 | 0.33 | 0.01 | 0.70 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -45%) [old -1k rule: RECENT-ONLY] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| week_loss_book_R | X2R_f0.00 | P7_sess_london | +10.1/+10.1/+10.6/+15.9/+27.9/+11.8 | -12.0/-18.2 | +18.5 | +1072 | +13.3/+13.3/+13.8 | +30.4/+14.9 | 21.92 | 0.01 | 0.01 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 20%, deeper -28%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| lock_giveback | arm1.5R_keep0.7(live2/.5) | ALL | +5.4/+5.4/+8.7/+0.5/+31.2/-0.0 | -8.0/-20.4 | +14.9 | +2242 | +12.1/+12.1/+15.2 | +36.1/+7.1 | 21.61 | 0.02 | 0.04 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper -31%) [old -1k rule: OK-PRIOR] | -16500 / -1800.0 | C | LEAD-RECENT (w20 fails ) |
| week_profit_protect_stack | X60000_f0.50 | P7 | +0.0/+0.0/+0.0/+0.0/+0.0/+0.0 | -6.7/-2.9 | +2.9 | +869 | +2.9/+2.9/+2.9 | +2.9/+2.9 | 19.56 | 0.01 | 0.04 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper -0%) [old -1k rule: OK-PRIOR] | -9235 / +0.0 | B | no |
| lock_daycap_win | win4R(live5) | A7 | +0.0/+0.0/+0.0/+0.0/+0.0/+0.0 | -0.2/-0.1 | +0.1 | +29 | +0.1/+0.1/+0.1 | +0.1/+0.1 | 19.02 | 0.00 | 0.19 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper -0%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | C | no |
| lock_weekfloor | floor16R(live12) | H7 | +0.0/+0.0/+0.0/+0.0/+0.0/+0.0 | +0.0/+0.0 | +0.0 | +0 | +0.0/+0.0/+0.0 | +0.0/+0.0 | 19.00 | 0.00 | 0.01 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper -0%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | C | no |


Up-allowed report rows (labelled, never promoted; first-order overstates up-size mean by 10-18k/wk):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| eqdd_stack_UP_at_high | Y20000_f0.50_up1.25 | ALL | +35.8/+40.0/+40.0/+38.8/+40.5/-2.9 | +18.6/-13.4 | +12.5 | -4856 | +22.9/+28.1/+28.0 | +28.6/-23.5 | 24.65 | 0.29 | 0.46 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -40%) [old -1k rule: RECENT-ONLY] | +25118 / +5079.1 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n4_x1.50 | ALL | +4.0/+4.0/+4.1/-0.8/-0.3/-1.9 | +0.1/+0.9 | -0.4 | -300 | +3.0/+3.0/+3.1 | -1.4/-2.9 | 19.58 | 0.02 | 0.09 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +0%) [old -1k rule: OK-PRIOR] | -655 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n4_x1.25 | ALL | +0.0/+0.0/+0.3/-0.8/-0.6/-0.9 | -1.9/+0.3 | -1.6 | -54 | -0.2/-0.2/+0.1 | -0.7/-1.1 | 18.96 | 0.01 | 0.09 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +1%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| eqdd_stack_UP_at_high | Y45000_f0.50_up1.25 | ALL | -13.1/+13.6/+17.0/+9.2/+34.9/-24.2 | +23.0/-0.8 | -43.4 | -4080 | -31.5/-0.4/+3.6 | +24.3/-44.3 | 14.45 | 0.19 | 0.81 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper -35%) [old -1k rule: OK-PRIOR] | +25118 / +5079.1 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.50 | ALL | +4.7/+4.7/+6.9/-2.3/-5.5/-5.4 | -32.3/+25.2 | -16.3 | -5268 | -16.3/-16.3/-13.5 | -28.8/-28.6 | 16.33 | 0.04 | 0.42 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +6%) [old -1k rule: OK-PRIOR] | -3448 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n3_x1.25 | ALL | -3.3/-3.3/+0.1/-0.8/-2.4/-1.4 | -28.9/+28.6 | -31.3 | -6208 | -31.3/-31.3/-26.9 | -30.1/-28.9 | 14.47 | 0.02 | 0.63 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +2%) [old -1k rule: OK-PRIOR] | -2651 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.25 | ALL | -12.8/-7.6/+8.2/+0.9/-9.7/-6.0 | -23.0/+32.0 | -41.8 | -6002 | -42.0/-35.5/-15.6 | -38.1/-33.5 | 13.38 | 0.06 | 0.76 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +10%) [old -1k rule: OK-PRIOR] | -1210 / +1860.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | book_n2_x1.50 | ALL | -31.7/-0.8/+18.0/-5.7/-20.8/-11.8 | -21.2/+33.3 | -55.2 | -5150 | -59.9/-22.4/+0.4 | -46.6/-35.7 | 11.88 | 0.12 | 0.69 | 1.00 | +26.1 / -6591 / 77% | RECENT-ONLY (allow 15%, deeper +21%) [old -1k rule: RECENT-ONLY] | -5591 / +3720.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n4_x1.25 | ALL | -13.0/-8.0/-0.2/-3.6/-6.4/-19.9 | -20.1/+32.3 | -44.7 | -6487 | -45.3/-38.9/-28.8 | -36.9/-54.2 | 13.08 | 0.05 | 0.99 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +6%) [old -1k rule: OK-PRIOR] | -1085 / +0.0 | B | UP-ALLOWED report row (never promoted) |
| antimartingale_UP | stack_n4_x1.50 | ALL | -46.1/-17.2/+8.5/-17.4/-9.9/-47.0 | -13.6/+29.4 | -64.2 | -5155 | -77.5/-42.3/-11.1 | -33.4/-78.6 | 10.70 | 0.11 | 0.95 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 15%, deeper +10%) [old -1k rule: OK-PRIOR] | -4732 / +0.0 | B | UP-ALLOWED report row (never promoted) |


## E. Exposure / concentration

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 1110 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| total_lots_cap | cap4_skip | sess_london | +38.6/+58.3/+58.8/-50.6/+46.2/+12.2 | -15.5/-17.5 | +26.0 | -3420 | +30.5/+52.7/+53.3 | +39.0/+0.6 | 27.32 | 0.16 | 0.20 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -46%) [old -1k rule: OK-PRIOR] | +18445 / +0.0 | B | recent-only dd (placebo p 0.20) |
| same_side_lots_cap | cap6_skip | P7 | +34.2/+65.5/+98.2/+42.0/+47.2/+48.3 | -51.6/-14.4 | +42.4 | -8070 | +9.1/+52.3/+97.6 | +27.0/+28.6 | 20.90 | 0.10 | 0.01 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -47%) [old -1k rule: RECENT-ONLY] | -57130 / -3830.0 | B | LEAD-RECENT (w20 fails ) |
| same_side_lots_cap | cap6_skip | ALL | +41.1/+62.8/+100.0/+49.0/+44.8/+59.1 | -51.1/-12.5 | +43.6 | -9667 | +11.9/+44.4/+100.0 | +17.5/+38.8 | 21.57 | 0.15 | 0.01 | 1.00 | +40.5 / -8998 / 89% | RECENT-ONLY (allow 25%, deeper -45%) [old -1k rule: RECENT-ONLY] | -53550 / -4440.0 | B | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 89%) |
| total_lots_cap | cap6_skip | ALL | +41.1/+62.2/+100.0/+52.4/+45.1/+45.7 | -44.8/-5.7 | +39.9 | -10461 | +8.2/+41.1/+100.0 | +14.4/+15.4 | 20.69 | 0.18 | 0.02 | 1.00 | +40.5 / -8998 / 89% | RECENT-ONLY (allow 25%, deeper -45%) [old -1k rule: RECENT-ONLY] | -52835 / -4440.0 | B | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 89%) |
| newentry_haircut_day_dd | Y15000_f0.0 | ALL | +31.0/+41.8/+97.1/-1.4/+38.7/-31.9 | -8.0/-5.1 | +16.7 | -5255 | +15.9/+29.0/+96.4 | +25.2/-60.8 | 22.58 | 0.19 | 0.76 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.76) |
| total_lots_cap | cap4_skip | P7 | +53.0/+66.7/+71.2/+8.6/+38.7/+50.6 | -74.7/-16.5 | +31.6 | -11839 | +21.0/+44.1/+51.5 | -3.1/+16.9 | 24.04 | 0.17 | 0.03 | 1.00 | +40.5 / -8998 / 89% | RECENT-ONLY (allow 25%, deeper -39%) [old -1k rule: RECENT-ONLY] | -73665 / -2215.0 | B | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 89%) |
| total_lots_cap | cap4_trunc | sess_london | +36.5/+36.5/+36.5/-17.6/+46.3/+11.0 | -15.9/-20.9 | +32.7 | -1332 | +33.5/+33.5/+33.4 | +43.7/+6.8 | 28.57 | 0.20 | 0.15 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -46%) [old -1k rule: OK-PRIOR] | +13112 / +0.0 | B | recent-only dd (placebo p 0.15) |
| same_side_lots_cap | cap4_trunc | sess_london | +33.7/+33.7/+33.7/-4.3/+46.5/+10.8 | -8.7/-27.3 | +32.2 | -729 | +32.0/+32.0/+32.0 | +45.1/+8.5 | 27.95 | 0.16 | 0.12 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -46%) [old -1k rule: OK-PRIOR] | +12842 / +0.0 | B | recent-only dd (placebo p 0.12) |
| newentry_haircut_day_dd | Y3000_f0.0 | sess_london | +35.1/+36.3/+52.8/-56.0/+59.9/-8.5 | -1.3/-23.0 | +25.3 | -3097 | +27.4/+28.8/+47.2 | +55.1/-21.3 | 26.15 | 0.21 | 0.50 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -60%) [old -1k rule: OK-PRIOR] | +1900 / +0.0 | B | recent-only dd (placebo p 0.50) |
| total_lots_cap | cap6_skip | P7 | +34.2/+57.3/+98.2/+40.5/+47.2/+49.2 | -41.8/-6.8 | +28.1 | -9787 | +1.1/+35.8/+97.4 | +20.5/+23.6 | 19.20 | 0.11 | 0.06 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -47%) [old -1k rule: RECENT-ONLY] | -57130 / -3830.0 | B | no |
| same_side_lots_cap | cap4_skip | P7 | +47.4/+65.6/+92.5/+14.7/+18.7/+50.0 | -49.7/+4.2 | +20.2 | -13344 | +3.0/+36.7/+86.1 | -49.8/+7.8 | 19.59 | 0.15 | 0.37 | 1.00 | +40.5 / -8998 / 89% | RECENT-ONLY (allow 25%, deeper -19%) [old -1k rule: RECENT-ONLY] | -73770 / -2215.0 | B | no |
| same_side_lots_cap | cap4_skip | sess_london | +38.6/+52.2/+57.2/-27.8/+50.9/+18.2 | -26.1/-11.6 | +17.2 | -7163 | +18.6/+36.6/+43.3 | +35.0/-8.4 | 23.35 | 0.13 | 0.28 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -51%) [old -1k rule: OK-PRIOR] | +18445 / +0.0 | B | recent-only dd (placebo p 0.28) |
| newentry_haircut_day_dd | Y6000_f0.0 | P7_sess_nyam | +23.8/+26.0/+33.8/+22.1/+15.7/-12.2 | -18.3/-9.3 | +22.1 | +835 | +25.9/+28.0/+35.6 | +18.0/-9.1 | 25.65 | 0.03 | 0.62 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -16%) [old -1k rule: OK-PRIOR] | -9135 / +0.0 | B | recent-only dd (placebo p 0.62) |
| total_lots_cap | cap6_trunc | sess_london | +25.2/+25.2/+25.1/+12.4/+24.1/+3.5 | -13.8/-17.1 | +29.0 | +1094 | +27.9/+27.9/+27.8 | +26.8/+7.0 | 26.35 | 0.14 | 0.12 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -24%) [old -1k rule: OK-PRIOR] | +11305 / +0.0 | B | recent-only dd (placebo p 0.12) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| total_lots_cap | cap4_skip | sess_london | +38.6/+58.3/+58.8/-50.6/+46.2/+12.2 | -15.5/-17.5 | +26.0 | -3420 | +30.5/+52.7/+53.3 | +39.0/+0.6 | 27.32 | 0.16 | 0.20 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -46%) [old -1k rule: OK-PRIOR] | +18445 / +0.0 | B | recent-only dd (placebo p 0.20) |
| same_side_lots_cap | cap6_skip | P7 | +34.2/+65.5/+98.2/+42.0/+47.2/+48.3 | -51.6/-14.4 | +42.4 | -8070 | +9.1/+52.3/+97.6 | +27.0/+28.6 | 20.90 | 0.10 | 0.01 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -47%) [old -1k rule: RECENT-ONLY] | -57130 / -3830.0 | B | LEAD-RECENT (w20 fails ) |
| newentry_haircut_day_dd | Y15000_f0.0 | ALL | +31.0/+41.8/+97.1/-1.4/+38.7/-31.9 | -8.0/-5.1 | +16.7 | -5255 | +15.9/+29.0/+96.4 | +25.2/-60.8 | 22.58 | 0.19 | 0.76 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -39%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.76) |
| max_books_on | n1_f0.5 | sess_london | +27.5/+27.5/+27.4/-18.2/+25.6/+16.9 | -11.1/-19.3 | +27.6 | +145 | +27.8/+27.8/+27.8 | +26.0/+17.3 | 26.32 | 0.13 | 0.09 | 0.98 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -26%) [old -1k rule: OK-PRIOR] | +7051 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| corr_same_side | N30min_f0.0_ge1_others | sess_london | +31.6/+44.6/+44.6/-6.6/+38.0/+20.2 | +9.0/-12.4 | +9.2 | -4241 | +20.0/+35.2/+35.1 | +27.5/+6.6 | 23.75 | 0.12 | 0.10 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -38%) [old -1k rule: OK-PRIOR] | -2230 / +0.0 | B | CANDIDATE-RECENT (first-order screen; needs EXACT) |


## K. P7 specific

Top 14 by the joint equal-mean cut (ranked by DRAWDOWN at equal mean, then (a)); 44 down-only cells in the family.

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_when_others_on | U7_sameside_f0.0 | P7 | +29.4/+33.3/+33.2/-4.1/+18.6/-25.8 | -7.6/-3.6 | +21.4 | -2012 | +24.2/+28.3/+28.3 | +12.6/-35.1 | 25.06 | 0.03 | 0.41 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -19%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.41) |
| P7_lots_by_session | L4_london | P7 | +16.5/+16.5/+16.4/+5.5/+26.1/+10.2 | -6.1/-14.8 | +16.4 | -360 | +15.4/+15.4/+15.3 | +25.1/+9.1 | 22.46 | 0.06 | 0.08 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -26%) [old -1k rule: OK-PRIOR] | +1193 / +0.0 | A | LEAD-RECENT (w20 fails ) |
| P7_when_others_on | U7_anyside_f0.0 | P7 | +23.1/+28.8/+28.7/-14.3/+18.6/-42.5 | +1.5/-3.3 | +7.3 | -3638 | +12.1/+18.6/+18.6 | +7.0/-62.7 | 21.62 | 0.04 | 0.72 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -19%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.72) |
| P7_lots_by_session | L4_nyam | P7 | +6.7/+6.7/+14.2/+13.1/+7.5/+12.5 | -16.1/-9.2 | +17.1 | +1860 | +12.3/+12.3/+19.3 | +13.1/+17.7 | 21.65 | 0.04 | 0.04 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 17%, deeper -8%) [old -1k rule: OK-PRIOR] | -6197 / +0.0 | A | LEAD-RECENT (w20 fails ) |
| P7_when_others_on | U7_sameside_f0.5 | P7 | +14.7/+14.7/+14.6/+17.1/+8.8/-9.4 | -3.7/-4.8 | +15.9 | -371 | +13.6/+13.6/+13.5 | +7.6/-10.8 | 21.99 | 0.03 | 0.38 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -9%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.38) |
| P7_lots_by_session | L3_nyam | P7 | +6.9/+6.9/+16.3/+12.7/+7.5/+11.1 | -16.2/-7.3 | +15.3 | +1060 | +10.2/+10.2/+19.2 | +10.7/+14.2 | 21.15 | 0.05 | 0.16 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 17%, deeper -7%) [old -1k rule: RECENT-ONLY] | -9798 / +48.3 | A | recent-only dd (placebo p 0.16) |
| P7_when_others_on | anyother_anyside_f0.0 | P7 | +52.1/+52.1/+58.1/-18.4/+22.8/+13.2 | -17.4/+13.0 | -1.8 | -14062 | +7.6/+7.6/+19.1 | -49.0/-67.4 | 20.56 | 0.18 | 0.52 | 1.00 | +5.4 / -5114 / 73% | RECENT-ONLY (allow 25%, deeper -23%) [old -1k rule: RECENT-ONLY] | -54690 / +40.0 | B | recent-only dd (placebo p 0.52) |
| P7_after_P7_stop | same_session_N60min_f0.0 | P7 | +6.6/+6.6/+6.5/+2.9/+28.7/-0.0 | -5.2/-11.8 | +11.7 | +866 | +9.3/+9.3/+9.2 | +30.8/+2.9 | 20.94 | 0.01 | 0.04 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 17%, deeper -29%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| P7_when_others_on | U7_anyside_f0.5 | P7 | +12.5/+12.5/+12.4/+12.2/+8.8/-15.6 | +0.5/-4.4 | +9.1 | -1134 | +8.9/+8.9/+8.8 | +5.1/-20.3 | 20.86 | 0.04 | 0.67 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 22%, deeper -9%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.67) |
| P7_lots_by_session | L5_london | P7 | +9.3/+9.3/+9.2/+3.1/+15.6/+8.5 | -2.2/-8.6 | +8.3 | -297 | +8.4/+8.4/+8.3 | +14.7/+7.6 | 20.73 | 0.06 | 0.06 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 19%, deeper -16%) [old -1k rule: OK-PRIOR] | -225 / +0.0 | A | LEAD-RECENT (w20 fails ) |
| P7_lots_by_session | L6_nyam | P7 | +4.6/+4.6/+5.3/+6.1/+3.8/+7.1 | -8.7/-5.5 | +9.1 | +1126 | +8.2/+8.2/+8.8 | +7.4/+10.6 | 20.69 | 0.03 | 0.01 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 15%, deeper -4%) [old -1k rule: OK-PRIOR] | -1898 / +0.0 | A | LEAD-RECENT (w20 fails ) |
| P7_lots_by_session | L6_all | P7 | +12.7/+12.7/+12.7/+19.3/+14.8/+20.2 | -10.2/-7.8 | +13.6 | -1536 | +7.9/+7.9/+7.8 | +10.1/+15.8 | 20.63 | 0.18 | 0.01 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 23%, deeper -15%) [old -1k rule: OK-PRIOR] | -12046 / -1882.7 | A | LEAD-RECENT (w20 fails ) |
| P7_after_P7_stop | same_session_N120min_f0.0 | P7 | +5.8/+5.8/+5.7/+2.0/+33.7/-4.6 | -5.3/-12.4 | +10.9 | +592 | +7.7/+7.7/+7.6 | +35.0/-2.5 | 20.58 | 0.01 | 0.10 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 16%, deeper -34%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| P7_when_others_on | K7orU7_sameside_f0.5 | P7 | +22.6/+22.6/+26.9/+21.8/+5.8/-2.1 | -1.6/+7.7 | +6.2 | -5408 | +5.0/+5.0/+10.2 | -15.6/-25.3 | 20.00 | 0.10 | 0.63 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -6%) [old -1k rule: RECENT-ONLY] | -29400 / -702.5 | B | recent-only dd (placebo p 0.63) |


Best per technique (one row each, by the joint cut):

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| P7_when_others_on | U7_sameside_f0.0 | P7 | +29.4/+33.3/+33.2/-4.1/+18.6/-25.8 | -7.6/-3.6 | +21.4 | -2012 | +24.2/+28.3/+28.3 | +12.6/-35.1 | 25.06 | 0.03 | 0.41 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -19%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.41) |
| P7_lots_by_session | L4_london | P7 | +16.5/+16.5/+16.4/+5.5/+26.1/+10.2 | -6.1/-14.8 | +16.4 | -360 | +15.4/+15.4/+15.3 | +25.1/+9.1 | 22.46 | 0.06 | 0.08 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 25%, deeper -26%) [old -1k rule: OK-PRIOR] | +1193 / +0.0 | A | LEAD-RECENT (w20 fails ) |
| P7_after_P7_stop | same_session_N60min_f0.0 | P7 | +6.6/+6.6/+6.5/+2.9/+28.7/-0.0 | -5.2/-11.8 | +11.7 | +866 | +9.3/+9.3/+9.2 | +30.8/+2.9 | 20.94 | 0.01 | 0.04 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 17%, deeper -29%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| P7_later_in_session | later_f0.5 | P7 | +13.7/+13.7/+38.5/+11.1/+29.1/+6.0 | -8.3/-2.1 | +8.8 | -5213 | -5.0/-5.0/+25.2 | +13.7/-14.4 | 18.09 | 0.13 | 0.41 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 24%, deeper -29%) [old -1k rule: OK-PRIOR] | -36947 / -1335.8 | B | no |
| P7_first_in_session | first_f0.5 | P7 | -1.7/-1.7/-1.8/+18.3/+1.1/+35.4 | -4.5/-4.6 | +4.7 | -1889 | -8.7/-8.7/-8.8 | -5.7/+31.0 | 17.47 | 0.10 | 0.46 | 1.00 | +5.4 / -5114 / 73% | OK-PRIOR (allow 15%, deeper -1%) [old -1k rule: RECENT-ONLY] | +55 / +0.0 | B | no |


## Cells that dominate Q1-A on both mean and maxDD (down-only; L6M, HOLD and PRE; (a) at equal lots)

| technique | params | scope | (a) maxDD cut L6M/L3M/L1M/HOLD/PRE/X' | worst-20 cut (b) L6M/PRE | Ulcer cut (b) L6M | d mean L6M | (b) eq-mean cut L6M/L3M/L1M | (b) PRE/X' | Calmar L6M | lot-change share | placebo p | family p | bi-weekly WF (maxDD cut / d mean / beats live %) | prior (PRE/X'; mean floor 25% of live PRE mean, old label beside) | live wk d total / d dd | class | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| consec_loss | stack_k5_f0.00 | ALL | +33.6/+52.3/+100.0/+33.4/+46.8/-42.6 | -44.0/-17.5 | +37.8 | +413 | +34.5/+53.0/+100.0 | +47.5/-40.6 | 29.00 | 0.22 | 0.63 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -47%) [old -1k rule: OK-PRIOR] | -5710 / +0.0 | B | recent-only dd (placebo p 0.63) |
| lock_daycap_loss | loss1R(live2) | P7 | +25.7/+25.7/+39.1/+8.2/+17.0/+6.1 | -22.3/-10.0 | +38.5 | +47 | +25.8/+25.8/+39.2 | +17.1/+6.3 | 25.61 | 0.04 | 0.01 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -17%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | C | LEAD-RECENT (w20 fails ) |
| dayloss_book_R | X1.0R_f0.00 | P7 | +25.7/+25.7/+39.1/+8.2/+17.0/+6.1 | -22.3/-10.0 | +38.5 | +47 | +25.8/+25.8/+39.2 | +17.1/+6.3 | 25.61 | 0.04 | 0.06 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -17%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| total_lots_cap | cap6_trunc | sess_london | +25.2/+25.2/+25.1/+12.4/+24.1/+3.5 | -13.8/-17.1 | +29.0 | +1094 | +27.9/+27.9/+27.8 | +26.8/+7.0 | 26.35 | 0.14 | 0.12 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -24%) [old -1k rule: OK-PRIOR] | +11305 / +0.0 | B | recent-only dd (placebo p 0.12) |
| newentry_haircut_day_dd | Y6000_f0.0 | P7_sess_nyam | +23.8/+26.0/+33.8/+22.1/+15.7/-12.2 | -18.3/-9.3 | +22.1 | +835 | +25.9/+28.0/+35.6 | +18.0/-9.1 | 25.65 | 0.03 | 0.62 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -16%) [old -1k rule: OK-PRIOR] | -9135 / +0.0 | B | recent-only dd (placebo p 0.62) |
| total_lots_cap | cap4_skip | sess_nyam | +21.2/+22.1/+27.8/+15.9/+4.0/+30.6 | -36.0/-6.0 | +26.1 | +356 | +22.2/+23.1/+28.7 | +5.1/+31.4 | 24.41 | 0.06 | 0.16 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -4%) [old -1k rule: RECENT-ONLY] | -11810 / +0.0 | B | recent-only dd (placebo p 0.16) |
| week_loss_stack | X10000_f0.50 | sess_london | +21.2/+21.2/+21.1/+9.7/+26.0/-17.9 | -12.4/-15.8 | +27.7 | +1338 | +24.6/+24.6/+24.5 | +29.2/-12.7 | 25.20 | 0.03 | 0.71 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -26%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.71) |
| same_side_lots_cap | cap6_trunc | sess_london | +19.8/+19.8/+19.7/+15.6/+26.7/+10.6 | -10.8/-17.4 | +22.3 | +431 | +21.0/+21.0/+20.9 | +27.7/+11.9 | 24.04 | 0.10 | 0.04 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -27%) [old -1k rule: OK-PRIOR] | +10545 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| total_lots_cap | cap4_skip | P7_sess_nyam | +18.8/+18.8/+28.6/+16.4/+5.7/+39.4 | -33.5/-5.8 | +24.1 | +200 | +19.3/+19.3/+29.0 | +6.3/+39.8 | 23.54 | 0.03 | 0.12 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 25%, deeper -6%) [old -1k rule: RECENT-ONLY] | -12000 / +0.0 | B | recent-only dd (placebo p 0.12) |
| dayloss_stack$ | X3000_f0.00 | P7_sess_nyam | +16.5/+16.5/+29.5/+12.8/+7.9/-37.8 | -13.3/-7.3 | +18.0 | +348 | +17.5/+17.5/+30.3 | +9.0/-36.2 | 23.02 | 0.02 | 0.97 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -8%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.97) |
| dayloss_stack$ | X3000_f0.00 | sess_nyam | +16.0/+16.0/+33.4/+11.1/+7.2/-39.1 | -16.8/-4.4 | +18.1 | +221 | +16.7/+16.7/+33.9 | +7.9/-38.0 | 22.79 | 0.10 | 0.92 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -7%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.92) |
| consec_loss | book_k4_f0.00 | ALL | +15.6/+15.6/+21.5/+15.7/+33.5/+1.1 | -22.6/-11.8 | +26.2 | +183 | +16.1/+16.1/+22.0 | +33.9/+1.7 | 22.64 | 0.06 | 0.07 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 25%, deeper -34%) [old -1k rule: OK-PRIOR] | -9430 / -1800.0 | B | LEAD-RECENT (w20 fails ) |
| total_lots_cap | cap4_trunc | sess_nyam | +14.0/+14.0/+18.0/+8.8/+2.2/+22.0 | -16.1/-7.7 | +21.1 | +1577 | +18.4/+18.4/+22.2 | +7.2/+26.0 | 23.28 | 0.08 | 0.03 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 24%, deeper -2%) [old -1k rule: RECENT-ONLY] | -2210 / +0.0 | B | LEAD-RECENT (w20 fails ) |
| eqdd_stack_20d | Y10000_f0.50_sticky | P7_sess_london | +13.7/+13.7/+13.6/+7.9/+24.5/-1.0 | -10.3/-16.9 | +18.2 | +471 | +15.0/+15.0/+15.0 | +25.7/+0.6 | 22.36 | 0.05 | 0.46 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 24%, deeper -25%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.46) |
| eqdd_stack_20d | Y10000_f0.50_live | P7_sess_london | +13.7/+13.7/+13.6/+7.5/+24.5/-6.0 | -10.6/-15.3 | +17.1 | +388 | +14.8/+14.8/+14.7 | +25.5/-4.6 | 22.30 | 0.05 | 0.55 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 24%, deeper -25%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | recent-only dd (placebo p 0.55) |
| newentry_haircut_day_dd | Y6000_f0.5 | sess_nyam | +13.5/+13.5/+15.0/+10.6/+7.5/-5.5 | -11.4/-7.6 | +15.4 | +1081 | +16.6/+16.6/+18.0 | +10.8/-1.8 | 22.78 | 0.02 | 0.78 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 24%, deeper -8%) [old -1k rule: OK-PRIOR] | -4568 / +0.0 | B | recent-only dd (placebo p 0.78) |
| newentry_haircut_day_dd | Y3000_f0.5 | sess_nyam | +13.5/+13.5/+18.6/+10.6/+7.5/-4.1 | -13.9/-8.5 | +15.8 | +1153 | +16.8/+16.8/+21.7 | +11.1/-0.2 | 22.83 | 0.03 | 0.73 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 24%, deeper -8%) [old -1k rule: OK-PRIOR] | -6368 / +0.0 | B | recent-only dd (placebo p 0.73) |
| newentry_haircut_day_dd | Y6000_f0.5 | P7_sess_nyam | +13.5/+13.5/+15.0/+10.6/+7.5/-5.5 | -11.4/-7.6 | +15.4 | +1081 | +16.6/+16.6/+18.0 | +10.8/-1.8 | 22.78 | 0.02 | 0.75 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 24%, deeper -8%) [old -1k rule: OK-PRIOR] | -4568 / +0.0 | B | recent-only dd (placebo p 0.75) |
| newentry_haircut_day_dd | Y3000_f0.5 | P7_sess_nyam | +13.5/+13.5/+18.6/+10.6/+7.5/-4.1 | -13.9/-8.5 | +15.8 | +1153 | +16.8/+16.8/+21.7 | +11.1/-0.2 | 22.83 | 0.03 | 0.61 | 1.00 | +40.5 / -8998 / 89% | OK-PRIOR (allow 24%, deeper -8%) [old -1k rule: OK-PRIOR] | -6368 / +0.0 | B | recent-only dd (placebo p 0.61) |
| dayloss_stack$ | X16000_f0.00 | sess_london | +13.2/+13.2/+17.0/+14.7/+7.4/+10.8 | -16.4/-9.8 | +20.9 | +1478 | +17.3/+17.3/+21.0 | +11.9/+15.1 | 22.98 | 0.03 | 0.01 | 1.00 | +26.1 / -6591 / 77% | OK-PRIOR (allow 23%, deeper -7%) [old -1k rule: OK-PRIOR] | +0 / +0.0 | B | LEAD-RECENT (w20 fails ) |


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
| C | riskcap_per_trade | R$2400 | P7 | +80.3 | +68.6/+37.0/+51.5 | +8790 | +10.4/+17.1/+30.8 | 0.02 | LEAD-RECENT (w20 fails ) |
| C | riskcap_per_trade | R$3600 | P7 | +72.5 | +68.4/+36.0/+41.9 | +12176 | +15.4/+17.5/+19.5 | 0.01 | LEAD-RECENT (w20 fails ) |
| C | volparity_down | win20_refmed | P7 | +88.3 | +67.6/+0.7/-16.2 | +5045 | -21.7/-11.3/+5.6 | 0.16 | no |
| E | same_side_lots_cap | cap6_skip | P7 | +69.4 | +63.4/-14.1/+45.9 | +11716 | +9.1/+27.0/+28.6 | 0.01 | LEAD-RECENT (w20 fails ) |
| D | eqdd_book_20d_R | Y2R_f0.25_sticky | P7 | +74.4 | +62.4/+33.1/+47.7 | +9522 | +16.6/+25.5/+44.1 | 0.01 | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 77%) |
| D | eqdd_book_20d_R | Y4R_f0.25_sticky | P7 | +63.2 | +62.1/+35.6/+55.0 | +13585 | +19.1/+36.1/+45.8 | 0.01 | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 77%) |
| C | volparity_down | win60_refmed | P7 | +85.6 | +59.3/-0.8/-69.2 | +4967 | -15.4/-11.9/-34.7 | 0.42 | no |
| C | riskcap_per_trade | R$4800 | P7 | +60.7 | +58.0/+9.4/+16.9 | +13076 | -3.9/-2.3/-4.4 | 0.19 | no |
| E | total_lots_cap | cap6_skip | P7 | +69.4 | +57.2/-18.2/+41.8 | +10000 | +1.1/+20.5/+23.6 | 0.06 | no |
| D | week_loss_stack | X20000_f0.00 | P7_sess_nyam | +38.3 | +55.2/+41.8/+8.1 | +19294 | +16.6/+24.3/-18.8 | 0.83 | recent-only dd (placebo p 0.83) |
| E | same_side_lots_cap | cap4_skip | P7 | +79.3 | +55.0/-147.7/+25.0 | +6443 | +3.0/-49.8/+7.8 | 0.37 | no |
| D | eqdd_book_20d_R | Y1R_f0.25_live | P7 | +68.2 | +52.3/-9.5/+17.3 | +9313 | +10.2/+24.6/+9.5 | 0.01 | RECENT-ONLY (prior RECENT-ONLY, allow 25%, WF 77%) |
| D | week_loss_stack | X10000_f0.00 | P7_sess_nyam | +33.0 | +51.5/+35.0/-1.4 | +19331 | +16.2/+20.7/-33.0 | 0.94 | recent-only dd (placebo p 0.94) |


## Bi-weekly re-pick WF per group (primary OOS; first-order screen)

| group | OOS maxDD cut vs Q1-A % | d mean $/wk | refit periods beating live | switches / periods | most picked |
|--|--|--|--|--|--|
| C | 69.0 | -9035 | 97% | 74 / 74 | C;volparity_down;win20_refmin;ALL, C;volparity_down;win20_refmin;P7, C;volparity_down;win20_refmed;ALL |
| D | 26.1 | -6591 | 77% | 74 / 74 | D;eqdd_book_20d_R;Y4R_f0.25_sticky;ALL, D;consec_loss;stack_k2_f0.00;ALL, D;eqdd_book_20d_R;Y2R_f0.25_sticky;ALL |
| E | 40.5 | -8998 | 89% | 74 / 74 | E;same_side_lots_cap;cap4_skip;ALL, E;total_lots_cap;cap4_skip;ALL, E;total_lots_cap;cap6_skip;ALL |
| K | 5.4 | -5114 | 73% | 74 / 74 | K;P7_first_in_session;first_f0.0;P7, K;P7_when_others_on;anyother_sameside_f0.0;P7, K;P7_later_in_session;later_f0.0;P7 |
| ALL | 40.5 | -10244 | 92% | 74 / 74 | C;volparity_down;win20_refmin;ALL, E;same_side_lots_cap;cap4_skip;ALL, E;total_lots_cap;cap4_skip;ALL |


## REFIT 2026-11-22: what the bi-weekly procedure picks today (trailing 26 weeks to 2026-10-30, DD-first picker, reference Q1-A)

| group | pick | live retained | train end | prior label of pick |
|--|--|--|--|--|
| C | C;esparity_down;last100tr_refmin;ALL | False | 2026-11-05 | RECENT-ONLY |
| D | D;eqdd_book_20d_R;Y1R_f0.25_sticky;ALL | False | 2026-11-05 | RECENT-ONLY |
| E | E;total_lots_cap;cap4_skip;ALL | False | 2026-11-05 | RECENT-ONLY |
| K | K;P7_when_others_on;anyother_anyside_f0.0;P7 | False | 2026-11-05 | RECENT-ONLY |

## Exact-driver finalists (<=12, down-only, by 18:00Z): autopilot/SZ_CDE_FINALISTS.csv (12 rows).


| id | label |
|--|--|
| E ; same_side_lots_cap ; cap6_skip ; P7 | LEAD-RECENT (w20 fails ) |
| D ; week_loss_stack ; X20000_f0.00 ; sess_london | LEAD-RECENT (w20 fails ) |
| D ; dayloss_stack$ ; X16000_f0.00 ; ALL | LEAD-RECENT (w20 fails ) |
| D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | LEAD-RECENT (w20 fails ) |
| D ; eqdd_stack_20d ; Y10000_f0.25_sticky ; sess_london | LEAD-RECENT (w20 fails ) |
| D ; dayloss_book_R ; X1.0R_f0.00 ; P7 | LEAD-RECENT (w20 fails ) |
| D ; lock_daycap_loss ; loss1R(live2) ; P7 | LEAD-RECENT (w20 fails ) |
| E ; max_books_on ; n1_f0.5 ; sess_london | LEAD-RECENT (w20 fails ) |
| E ; corr_same_side ; N30min_f0.0_ge1_others ; sess_london | CANDIDATE-RECENT (first-order screen; needs EXACT) |
| D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | LEAD-RECENT (w20 fails ) |
| D ; dayloss_stack$ ; X8000_f0.00 ; P7_sess_london | LEAD-RECENT (w20 fails ) |
| E ; total_lots_cap ; cap6_skip ; sess_nyam | LEAD-RECENT (w20 fails ) |


NOT first-order scorable (exact driver only): StackCutPct 0-100 x sessions and StackAsiaOnly variants; lock/give-back values looser than live (win cap 6-8R, give-back arm 3R/keep .3, floor 14-16R); every re-entry-dependent cell needs state_sizer_b-style engine support (the current exact driver patches only the ER lots step: rules D/E need a new engine hook = v1.6-style code, flagged to lead).


M_CDE.npz row alignment spot-check (M x base P&L in C.prepare(C.load_trades) order, maxDD re-derived on L6M/PRE/X' must equal the ledger): C|riskcap_per_trade|R$2400|P7 L6M maxDD 44621 vs ledger 44621 MISMATCH; D|dayloss_book_R|X0.5R_f0.00|P7_sess_nyam L6M maxDD 70203 vs ledger 70203 MISMATCH; K|P7_lots_by_session|L4_nyam|P7 L6M maxDD 74568 vs ledger 74568 MISMATCH. Windows: the COMB list ends with label day 20261030 (2026-10-31 is a Saturday, base_b has no later trade), so L1M-L3M end there and the live weeks 11-01..05 are only in the held-out live-week columns.


## Exact-engine status of the finalists (hook code/th_sz_cde/cde_exact.py; regression month 202304 with a never-firing rule == S1-COMB; 2 workers; order: six best (F00 F01 F03 F11 F02 F04) on L6M, PRE, X', then the other six, HOLD last). EXACT-CONFIRMED = exact maxDD cut > 0 on every window that is complete; a window shown as na is not run yet; every other cell in this page is FIRST-ORDER ONLY.

| set | cell | L6M exact cut / first-order cut | PRE exact / FO | X' exact / FO | L6M d mean exact / FO | HOLD exact / FO | status |
|--|--|--|--|--|--|--|--|
| CDE_F00 | D ; eqdd_book_20d_R ; Y1R_f0.50_sticky ; ALL | +24.0 / +46.6 | +15.3 / +44.6 | +31.4 / +47.4 | -8807.3 / -8362.9 | na / na | EXACT-CONFIRMED on L6M/PRE/X' |
| CDE_F01 | E ; max_books_on ; n1_f0.5 ; sess_london | +25.8 / +27.5 | +11.8 / +25.6 | +12.1 / +16.9 | +757.0 / +145.4 | -18.3 / -18.2 | EXACT-CONFIRMED on L6M/PRE/X' |
| CDE_F02 | D ; eqdd_book_20d_R ; Y4R_f0.25_sticky ; P7 | +10.7 / +30.3 | +34.8 / +44.9 | +5.3 / +53.2 | -9137.0 / -4029.3 | na / na | EXACT-CONFIRMED on L6M/PRE/X' |
| CDE_F03 | C ; riskcap_per_trade ; R$3600 ; P7 | +18.9 / +37.4 | +18.3 / +39.0 | +53.5 / +40.5 | -12345.8 / -7610.8 | na / na | EXACT-CONFIRMED on L6M/PRE/X' |
| CDE_F04 | D ; eqdd_stack_20d ; Y20000_f0.25_sticky ; sess_london | +30.2 / +29.8 | +36.5 / +43.4 | +4.2 / +12.8 | -1667.8 / -46.8 | -25.3 / -25.1 | EXACT-CONFIRMED on L6M/PRE/X' |
| CDE_F05 | D ; week_loss_book_R ; X2R_f0.00 ; P7_sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F06 | E ; same_side_lots_cap ; cap6_trunc ; sess_london | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F07 | D ; eqdd_stack_20d ; Y30000_f0.25_sticky ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F08 | E ; total_lots_cap ; cap6_skip ; sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F09 | E ; same_side_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F10 | E ; total_lots_cap ; cap6_skip ; P7_sess_nyam | na / na | na / na | na / na | na / na | na / na | no exact window yet |
| CDE_F11 | K ; P7_lots_by_session ; L4_nyam ; P7 | +12.6 / +6.7 | +4.3 / +7.5 | +12.4 / +12.5 | +2788.0 / +1860.2 | na / na | EXACT-CONFIRMED on L6M/PRE/X' |


## Family L (SZ-L cooldowns / chop pauses) top-5 EXACT vs first-order (hook codes 20 chop pause, 21 session-loss in cde_exact.py; windows as on this page, ref = S1-COMB trades; first-order from SZ-L raw_L.parquet whose windows run to 11-05)

| set | cell | technique / params | window | exact maxDD cut | first-order cut | exact d mean | FO d mean | exact equal-mean cut | trades in S1-COMB with no exact counterpart (removed) n / net P&L | exact-only trades (re-entries / shifted) n / net P&L | first-after-removed n / P&L | exact total vs ref total |
|--|--|--|--|--|--|--|--|--|--|--|--|
| CDE_L1 | fbe1c726c9b2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | L6M [ROLL-FIXED] | +18.9 | +21.2 | -2140 | +2735 | +12.4 | 871 / -7568 | 376 / -28795 | 541 / +174089 | +655630 vs +643973 |
| CDE_L1 | fbe1c726c9b2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | PRE [ROLL-FIXED] | +1.3 | +22.8 | -1532 | -3516 | -11.2 | 1353 / +209255 | 651 / +108678 | 868 / +279235 | +943925 vs +1047056 |
| CDE_L1 | fbe1c726c9b2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | X' [ROLL-FIXED] | +54.3 | +24.6 | +1995 | -122 | +75.1 | 537 / -16915 | 311 / +73432 | 357 / +79069 | +146401 vs +55787 |
| CDE_L1 | fbe1c726c9b2 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "exKB"} | HOLD [ROLL-FIXED] | +1.4 | -36.7 | -1403 | -835 | -6.1 | 1529 / +62221 | 669 / -18489 | 955 / +173336 | +921384 vs +971267 |
| CDE_L2 | 6e18cc85a3d6 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | L6M [ROLL-FIXED] | +15.5 | +17.1 | -4188 | +2727 | +1.3 | 1525 / -10372 | 763 / -42124 | 857 / +215721 | +637645 vs +643973 |
| CDE_L2 | 6e18cc85a3d6 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | PRE [ROLL-FIXED] | -0.2 | +32.0 | -1142 | -3757 | -9.3 | 2309 / +248003 | 1234 / +112287 | 1355 / +370767 | +906380 vs +1047056 |
| CDE_L2 | 6e18cc85a3d6 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | X' [ROLL-FIXED] | +45.3 | +23.5 | +1508 | +390 | +66.4 | 827 / -7133 | 542 / +65523 | 515 / +82028 | +125922 vs +55787 |
| CDE_L2 | 6e18cc85a3d6 | L_chop {"H": 30, "M": 1, "N": 2, "cond": "rng60_3.0", "eff": 0.0, "post": 1.0, "scope": "ALL"} | HOLD [ROLL-FIXED] | -6.2 | -15.3 | -1820 | -620 | -16.9 | 2643 / +63509 | 1293 / -43348 | 1511 / +232220 | +883068 vs +971267 |
| CDE_L3 | 21142bd69657 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | L6M [ROLL-FIXED] | +26.6 | +21.9 | -2843 | +1537 | +18.6 | 1066 / +21278 | 228 / +10804 | 401 / +12830 | +624788 vs +643973 |
| CDE_L3 | 21142bd69657 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | PRE [ROLL-FIXED] | +20.9 | +46.5 | -1752 | -1290 | +9.2 | 1068 / +55385 | 193 / -99024 | 527 / +91373 | +897497 vs +1047056 |
| CDE_L3 | 21142bd69657 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | X' [ROLL-FIXED] | +4.8 | +15.1 | +83 | +1034 | +8.0 | 77 / -11318 | 26 / -7462 | 62 / +1972 | +60663 vs +55787 |
| CDE_L3 | 21142bd69657 | L_sessloss {"eff": 0.0, "n": 2, "sess": [1], "state": "stack"} | HOLD [ROLL-FIXED] | -10.9 | -31.8 | -2917 | -1721 | -29.9 | 1776 / +148917 | 352 / +20148 | 693 / -22445 | +832627 vs +971267 |
| CDE_L4 | 953a73f259cd | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | L6M [ROLL-FIXED] | +11.9 | +16.9 | +1889 | +652 | +17.3 | 838 / -71736 | 188 / +31468 | 348 / +24551 | +741216 vs +643973 |
| CDE_L4 | 953a73f259cd | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | PRE [ROLL-FIXED] | +34.5 | +38.4 | -827 | -780 | +30.3 | 756 / +748 | 132 / -78346 | 372 / +59508 | +971004 vs +1047056 |
| CDE_L4 | 953a73f259cd | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | X' [ROLL-FIXED] | +17.0 | +21.8 | +470 | +267 | +30.6 | 37 / -25307 | 11 / -209 | 32 / -5245 | +80884 vs +55787 |
| CDE_L4 | 953a73f259cd | L_sessloss {"eff": 0.0, "n": 3, "sess": [1], "state": "stack"} | HOLD [ROLL-FIXED] | -15.2 | -45.2 | -1256 | -664 | -22.9 | 1435 / +68188 | 286 / +44738 | 604 / -43141 | +930276 vs +971267 |
| CDE_L5 | f5ef3a4814f4 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | L6M [ROLL-FIXED] | -2.4 | +14.9 | -6075 | +1026 | -29.5 | 383 / +17219 | 155 / -30522 | 230 / +119718 | +617537 vs +643973 |
| CDE_L5 | f5ef3a4814f4 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | PRE [ROLL-FIXED] | +37.5 | +33.2 | +2087 | -867 | +45.8 | 522 / -20227 | 207 / +93047 | 333 / +206757 | +1186544 vs +1047056 |
| CDE_L5 | f5ef3a4814f4 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | X' [ROLL-FIXED] | +28.4 | +32.7 | +480 | -880 | +40.3 | 138 / +11870 | 72 / +40096 | 96 / +83485 | +82448 vs +55787 |
| CDE_L5 | f5ef3a4814f4 | L_chop_book {"H": 0, "M": 3, "N": 2, "cond": "rng60_3.5", "eff": 0.0, "post": 1.0, "scope": "PE"} | HOLD [ROLL-FIXED] | +17.7 | -32.3 | -4558 | -2733 | -6.6 | 639 / +78480 | 270 / -2847 | 382 / +110993 | +905109 vs +971267 |

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

## F01 / F04 decision pack (exact, ROLLFIX1; first-order screen numbers only where stated)

### 1. Bi-weekly re-pick WF (Z.wf_biweekly: 26 weeks train -> next 2 weeks, 7-day purge, DD-first picker; the picker chooses between live and the candidate cell(s); uncovered months carry the live series for both so the WF is run only inside contiguous exact blocks)

| block | cells | OOS maxDD cut vs live % | d mean $/wk | refit periods beating live | switches / periods |
|--|--|--|--|--|--|
| X-prime+PRE (202304-202506, contiguous) | CDE_F01+CDE_F04 | 31.2 | -860 | 49% | 33 of 43 |
| X-prime+PRE (202304-202506, contiguous) | CDE_F01 alone vs live | 11.8 | -1120 | 47% | 30 of 43 |
| X-prime+PRE (202304-202506, contiguous) | CDE_F04 alone vs live | 31.2 | -178 | 26% | 21 of 43 |
| HOLD+L6M (202511-202610, contiguous) | CDE_F01+CDE_F04 | 0.0 | -636 | 0% | 1 of 12 |
| HOLD+L6M (202511-202610, contiguous) | CDE_F01 alone vs live | 0.0 | -73 | 8% | 1 of 12 |
| HOLD+L6M (202511-202610, contiguous) | CDE_F04 alone vs live | 0.0 | -636 | 0% | 1 of 12 |

### 2. Rule 2a label (Z.prior_info: allowed PRE deepening = min(25, L6M cut + 10)% only if the bi-weekly WF beats live in >= 60% of periods else 15%; PRE mean floor -1k/wk of live)

| cell | L6M cut (exact) | PRE maxDD cut (exact) | PRE d mean | bi-weekly WF beats live % (block X-prime+PRE, cell alone) | label | allowance % | PRE deeper % |
|--|--|--|--|--|--|--|--|
| CDE_F01 | +25.8 | +11.8 | -1490 | 47 | **OK-PRIOR** (old -1k rule: RECENT-ONLY) | 15 | -11.8 |
| CDE_F04 | +30.2 | +36.5 | -462 | 26 | **OK-PRIOR** (old -1k rule: OK-PRIOR) | 15 | -36.5 |

HOLD exact (2025-11..2026-10, ROLL-FIXED): CDE_F01 maxDD 117669 vs live 99496 (cut -18.3%, d mean -1439 $/wk, equal-mean -15.3%); CDE_F04 maxDD 124680 vs live 99496 (cut -25.3%, d mean -1541 $/wk, equal-mean -32.9%). Both are DEEPER than live on HOLD: the cut is concentrated in L6M, PRE and X-prime and the 2025-11..2026-04 months get worse; the HOLD+L6M bi-weekly WF picks live in 11 of 12 periods and beats live in 0% / 8% of periods.


Mean floor rule: since 2026-11-10 13:45Z the PRE mean floor is 25% of the live PRE mean (about -3.5k/wk), not the old fixed -1k; the old label is shown beside the new one.

### 3. Placebo and family p (first-order screen nulls; 100 draws; same-count random removals within book x session; joint stat = min of L6M, PRE, X-prime equal-mean cut; own = this cell, family = max over the E grid / the D grid / the whole CDE set)

| cell | own-draw p | family p (own family grid) | family p (whole CDE set) |
|--|--|--|--|
| CDE_F01 | 0.09 | 0.80 | 0.98 |
| CDE_F04 | 0.04 | 1.00 | 1.00 |

Both clear the own-draw bar on the first-order screen (p <= .10) but not the family bar: they are own-draw only.

### 4. What they remove (exact; trades in the patched live list with no exact counterpart within 5 s = removed; exact-only = re-entries / shifted trades; first-after = first surviving trade of a book after a removed one). Net P&L columns are the reliable ones (see the churn caveat in the cooldown section).

| cell | window | exact trades vs live | lots ratio | removed n / net P&L | by book (n / P&L) | by session (n / P&L) | exact-only n / net P&L | first-after n / P&L | London trades live -> cell | London lots live -> cell | London net live -> cell |
|--|--|--|--|--|--|--|--|--|--|--|--|
| CDE_F01 | L6M [ROLL-FIXED] | 4987 vs 4861 | 0.930 | 26 / +1668 | K7 12 / +4286; M7 2 / +158; P7 12 / -2777 | london 9 / +5948; nyam 13 / -5794; nypm 4 / +1514 | 152 / +9361 | 16 / +1033 | 1703 -> 1752 | 3636 -> 2741 | +43589 -> +30626 |
| CDE_F01 | PRE [ROLL-FIXED] | 8016 vs 7923 | 0.912 | 44 / +30410 | K7 10 / +2059; M7 17 / +7398; P7 17 / +20954 | asia 2 / -169; london 27 / +21521; nyam 12 / +8463; nypm 3 / +595 | 137 / -19439 | 27 / -10706 | 2562 -> 2585 | 5583 -> 4003 | +30535 -> -71194 |
| CDE_F01 | X' [ROLL-FIXED] | 3007 vs 2995 | 0.917 | 8 / -727 | K7 4 / -3592; M7 2 / +1635; P7 2 / +1229 | london 4 / +2865; nyam 1 / -1191; nypm 3 / -2401 | 20 / +113 | 5 / -1296 | 771 -> 775 | 1659 -> 1147 | +17619 -> +5985 |
| CDE_F04 | L6M [ROLL-FIXED] | 4949 vs 4861 | 0.924 | 19 / -6378 | K7 12 / +3218; M7 1 / +2398; P7 6 / -11994 | london 9 / -6382; nyam 5 / -170; nypm 5 / +175 | 107 / -20714 | 12 / -1524 | 1703 -> 1734 | 3636 -> 2721 | +43589 -> +46270 |
| CDE_F04 | PRE [ROLL-FIXED] | 8015 vs 7923 | 0.902 | 33 / -21502 | K7 9 / +511; M7 7 / +155; P7 16 / -20661; U7 1 / -1506 | asia 2 / -169; london 25 / -28462; nyam 2 / +7198; nypm 4 / -69 | 125 / -16086 | 21 / +8379 | 2562 -> 2583 | 5583 -> 3818 | +30535 -> +16554 |
| CDE_F04 | X' [ROLL-FIXED] | 3011 vs 2995 | 0.911 | 4 / +3656 | M7 2 / +1635; P7 2 / +2020 | london 4 / +3656 | 20 / +3266 | 4 / -6297 | 771 -> 775 | 1659 -> 1100 | +17619 -> +8627 |

Reading: the equal-mean cut (L6M +27.7% F01, +26.0% F04) already says the drawdown cut is more than the size reduction would give; the trade/lot counts above show how much London activity is removed.

### 5. Registry and panel lines
- F01 (max books on = 1 in London at half lots, i.e. a London signal arriving while any other book holds a position is taken at x0.5, rounded, min 1): no D7 v1.5 panel field exists for it (the nearest existing fields are the session lot tables and StackCutPct/StackAsiaOnly, which act on STOPS, not on entry exposure) -> v1.6 code: a per-signal open-books count and a London-only x0.5 entry multiplier. Registered in layers/stack_exposure/topK.json with the live setting (no exposure rule) as the live row.
- F04 (stack equity-DD size-down: when the stack equity is >= $20k below its 20-label-day high, London entries at x0.25 until the high is regained): no D7 v1.5 field (the existing locks work per book on day/week P&L, not on a stack equity high) -> v1.6 code: stack realized-equity high-water over 20 days, a London size multiplier, sticky release at the old high. Registered in layers/sizer_state/topK.json with the live Q1-A sizer as the live row.


## Exact vs first-order, L6M (first exact result, 2026-11-09 15:35Z; six priority finalists, L6M months 2026-05..10 complete; PRE and X' running)
Survive in the engine (exact L6M maxDD cut about the first-order cut, equal-mean cut positive): E max_books_on n1 f0.5 on the London session (exact +25.8% vs FO +27.5%, d mean +800 $/wk, equal-mean +27.8%); D eqdd_stack_20d Y20000 f0.25 sticky on London (exact +30.2% vs FO +29.8%, d mean -1.6k, equal-mean +26.2%); K P7 lots cap 4 in NYAM (exact +12.6% vs FO +6.7%, d mean +2.8k, equal-mean +20.2%).
Deflate and fail at equal mean: D eqdd_book_20d_R Y1R f0.50 sticky ALL (FO +46.6% -> exact +24.0%; d mean -9.0k; equal-mean -9.9%: the first-order cut was mostly size-down); D eqdd_book_20d_R Y4R f0.25 P7 (FO +30.3% -> +10.7%, equal-mean -30.1%); C riskcap R$3600 on P7 (FO +37.4% -> +18.9%, equal-mean -38.7%).
So the broad/book-level state and risk-cap cells lose half or more of the first-order cut in the engine and do not beat size-down at equal mean; the session-scoped London/NYAM cells survive on L6M only. PRE and X' not yet exact; no cell is a candidate on L6M alone.

Keying check (lead, 17:00Z): cde_exact.py uses NO multiplier table keyed on a time or row. Every D/E/K rule and the L cooldown rules (codes 20, 21) compute the multiplier directly from the engine's own state at the decision call inside ntz_check (realized P&L, open lots, equity history, loss counts keyed by trade sig_ns session instance, chop flags looked up by searchsorted on the decision second); the decision second is the engine's arm time of the signal, which is the signal second (l2arm is called at the signal). The first-order path (cde_kernel.py) is sequential on sig_ts and M_CDE.npz rows were verified to the dollar against the ledger. Firing is visible in the exact output (CDE_L2 202605: 603 trades vs 672 in S1-COMB). No void needed.

## Family L: plain sentences (exact L6M, first-order frozen week)
Exact (S1b engine, L6M, 6 months): the session-loss rule "2 stack losses in London -> London off for the rest of that session" (CDE_L3) keeps its cut (+26.6% maxDD vs +21.9% first-order, equal-mean +18.1%, d mean -3.0k/wk); the 3-loss version (CDE_L4) +11.9% at +1.9k/wk, equal-mean +17.2%; the chop pauses (CDE_L1 exKB +18.9%, equal-mean +12.1%; CDE_L2 all books +15.5%, equal-mean +0.8%, d mean -4.3k/wk) cut drawdown mostly by trading less; the P7-only chop pause (CDE_L5) fails exact (-2.4%, equal-mean -10.3%). PRE and X' exact months are still running; nothing is a candidate on L6M alone. Caution on the removed/first-after columns: after a pause the engine re-enters at different seconds, so "no counterpart within 5 s" counts churn, not only skipped signals; read the net P&L columns and the exact total vs ref total, not the gross counts.
Frozen live week (first-order, SZ-L): none of the five removes last week's P7 Asia/London losses (-67,980) without also removing winners: CDE_L5 (P7 chop pause) removes +22,445 of P7 loss P&L and 90,020 of winner P&L; L3 (London stack-loss) removes 19,165 of losses and 41,640 of winners; L4 13,765 / 22,445; L1 15,870 / 60,770; L2 15,870 / 79,305. M7's cut losses (-13,615): removed 0 to 7,160. So no cooldown here is selective for the chop losses; the best ratio is the London stack-loss rule (about 0.46 of losses per winner dollar removed vs 0.26 for L5).
