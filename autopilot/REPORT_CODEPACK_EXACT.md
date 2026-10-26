# REPORT_CODEPACK_EXACT (K4-EXACT audit 2026-10-19; K4H excluded)

| pack | verdict | scored OOS Sharpe | live-form OOS Sharpe | gates a-d (live) | best-of-F 1,208/761/594 (live) | lookahead | main flags |
|---|---|---|---|---|---|---|---|
| WT10 | FLAGGED | 1.867 | 2.087 (clock bars 2.050; no locks 1.534) | PASS | FAIL (as scored) | none | blackout 1 min off; row-bars vs clock; target on touch; locks unmapped |
| WT432 | FLAGGED | 1.254 | 1.117 (ATR30 0.967, ATR20 1.004, ATR10 1.132) | PASS combined; ATR20_m4 gate b 0.949 | FAIL (as scored) | none | same + 38/81 cells round to 0 MNQ; MNQ commission decisive (1.711 at <=$1, 0.05 at $4.36) |
| C11DIP | FLAGGED | 1.447 | 1.446 (micro lots raw 1.736) | PASS | FAIL (as scored) | none (fill on decision print, live 16:00 open) | same-print fill; rounding; roll/NT8 not computable |
| CL240 | FLAGGED | 1.669 | 1.643 (1.541 with trade-through + 2 ticks) | PASS | FAIL (as scored) | none | pack says 16:55 flatten, scored 16:59; touch fills; bands 10% high |
| B7X | FLAGGED | 1.44 | 1.45 cost-neutral; -0.53 at $4.36/micro | PASS cost-neutral; FAIL at $4.36/micro | FAIL (as scored) | none | fractional size/commission; GC roll not computable |
| BM13 | FLAGGED | 1.77 | 1.77 (6 cells); 1.92 3-cell pack (selected); 1.44 at $4.36/MNQ | PASS | FAIL (as scored) | none | bands vs pack cells mismatch; VWAP volume |
| BTCWT | FLAGGED | 2.11 headline / 1.81 M2 OOS | 1.56 signal-close fill; -0.19 at $4.36/MBT | PASS (except $4.36/MBT) | FAIL (as scored) | none | optimistic late fills; MBT cost; non-WF headline |

Verdict: no codepack sleeve passes best-of-F in scored or live form; none had lookahead.

## Lookahead found in PAPER-ALL/livepack rows (details AUDIT_LIVEPACK.md)
- N1 engine fills at the signal bar's own print: N1-EN_HO_RB-5m-MR (the only N1 gate a-d passer) 1.83 -> -1.63 with 1-min delay; corrected N1 family = 0 passers. Also marked: N1-MT_SI_PL-5m-MR, N1-RT_ZB_ZT-30m-MR, N1-EQ_RTY_YM-30m-MR, N1-EQ_NKD_NQ-30m-MR, N1-MT_GC_SI-5m-MR (none passed before).
- TINYMERGE:I:market (I9, RW9, I9_IBS_dipbuy): market-on-close at signal close; 2.11 -> 1.74, gates pass, best-of-F fails before and after.
- Daily rows N3-*, N7-*, N8-*, N10-CSMAX-MENR, N10-CSMAX-COMM, N10-CSVOL-MENR, N13-XLEAD-HO: clock mis-described (UTC-midnight bars) and Sunday stub dropped; six of twelve N3/N7/N8 passers lose a gate when the stub is folded in (names in AUDIT_LIVEPACK.md section 7).
- Deferred to K4 agent: SK_K4BOOKS, SK_K4BOOKS_ESHEDGED, TINYMERGE:RW:market, TINYMERGE:L:market.
- Rows with live-form (non-lookahead) differences: WT432:ATR30_m4/ATR20_m4/ATR10_m3 (+ unrescored ATR30_m3, ATR14_m4, ATR10_m2, ATR20_m2, ATR20_m3, ATR14_m3, T3S1_BOOKS_B:B_WT), C11DIP, ESDIP lead, C10S1_CL_240_lr/macd and C10S1_CL:240_*, B7XC, BM13_NQ, BM11_NQ, BM12_NQ, BTCWT, B1leg_BTC, M2 Range/Renko/Dollar/Tick rows.

## Could not be computed
NT8/Rithmic bars, fills and volume; NT8 roll dates and GC roll; real micro-contract fee schedule; DualStrat lock mapping; netted one-account lock variant; tick-bar rebuilds for M2 non-time bars; true 17:00 session bars for 21 of 26 daily-row instruments; BTC/MBT book fills.

Systemic: the ENDI flatten bug (16:59 vs 16:55) also sits in ap_c10_s1_core, ap_c7_p1_core, ap_c5_m1_core, v5_p2_core; all families on them (C10S1_*, C7P1_*) are unrescored.

Files: outputs/codepack/AUDIT_{WT10,WT432,C11DIP,CL240,B7X,BM13,BTCWT,LIVEPACK}.md; code/data in outputs/autopilot/codepack_exact/.
