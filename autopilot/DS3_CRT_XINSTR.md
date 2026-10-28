# DS3_CRT_XINSTR - CRT family and S3 range-model re-score on ES, RTY, YM, CL, GC, ZN, 6E (NQ alongside) at equal risk, conservative basis (D3CX, 2026-10-28)

Research only; no live, execution-server or chart change; no download or purchase. Prereg: autopilot/DECISIONS.md line 'D3CX PREREG' (master sha256 d7da1cee1d01b167d58c62c0b85691f0c651ca7caf350c8056eb88790c000166; per-group files l2vast/ds3/prereg/D3CX_<SYM>_prereg.md, pre texts D3CX_<SYM>_pretext.md; 8 groups x 18 cells = 144, <=30 per prereg). Holdout: one logged look per group (9 tracks, l2vast/struct48/ledger/holdout_looks.jsonl). Code l2vast/ds3/code/xi/ (xi_core, xi_cells, xi_run, xi_score, xi_prereg, xi_pretext, xi_gross, xi_report); outputs l2vast/ds3/out/xi/.

## Verdict
**0 PASS, 0 CANDIDATE, 144 of 144 registered cells DEAD (and 18 of 18 pooled rows DEAD) on the conservative basis.** No instrument carries a CRT or S3 edge once the tick-cost basis is applied. Best registered cell by WF equal-risk mean: NQ S3_B_N12_tf5m at 584 $/wk (WF MDE 3,340); it fails beats_a, beats_c, cost2x_pre, year_share, hold, best_of_N. Cost-free (gross) R per trade is ~0 in every instrument (medians -0.12 to 0.00 R, table below), so the result is 'no gross edge' and then 'costs finish it', not just 'costs'. The NQ comparator on the same basis is also DEAD (it is the least negative because its stops are 50 ticks, not 5-18). Recommended for Sim: none. Spec for CANDIDATE: none exists (see end).

## Basis, labels and deviations (read first)
- **Replay class R2, conservative mapped, labelled.** Checked INSTRUMENT_INVENTORY.md and data/databento/*: ES, RTY, YM, CL, GC, ZN, 6E have 1-min OHLCV only (no tick, no L2/MBO raw; only NQ has l2/), so no direct replay was possible. 6B is on disk (1-min) but was not in the directive list and has no FEES.md line: not scored (NEEDS line below if wanted).
- **Fill basis (replaces raw+0.5+min(corr,0))**: that NQ mapping is calibrated on NQ L2 60-pt brackets (target corrections -1.5..-4.3 NQ pt) and is not portable to a 5-tick ZN stop. Used instead, identically for all eight instruments including NQ: market entry +1 tick adverse; stop fills at the stop (bar open if gapped) then 2 ticks adverse; limit targets fill only on a 1-tick trade-through (no credit); flat at the 16:54 ET minute close (1 tick adverse) or any >30-min data gap; stop tested first in a minute; no stop-join credit. This is the open2 basis-T analogue. Library NQ conservative reference for CRT_H4_M5_close (10 lots, DS3 lock engine): WF -1,627 $/wk, HOLD -4,219; here NQ is on $1,000-risk lots so the dollars are not comparable, the sign is (also negative).
- **Equal risk**: every trade sized to $1000 at the stop, fractional lots (fees x lots). Windows/filters scale NQ constants by k = median 5-min range ratio on the 2022-06..2023-02-09 warm-up only (k: NQ 1, ES 0.2553, RTY 0.1277, YM 1.787, CL 0.01362, GC 0.08511, ZN 0.00266, 6E 3.83e-05), with floors of 4 ticks (stop, first target), 8 ticks (S3 box), 1 tick buffer. Share of trades with lots<1 is 0-2 percent.
- **Fees**: ES 4.84 (NT-published); RTY, YM, CL, GC, ZN 4.84 = WEAK proxy (ES); 6E 5.30 (NT lifetime addendum, third-party exchange fee WEAK); NQ 4.84 proxy. Verdicts on the six WEAK instruments and pooled cap at CANDIDATE (moot: none reached it).
- **Signals are independent numba ports**, not the NQ library: CRT_H4_M5_close on NQ reproduces the x_crt replay entries 3,589/3,589 with 99.8 percent of points within 0.5 pt (frictionless run); the S3 cells have no replay identity (NQ trades/wk 6.6-40 vs library 6.5-36; the library applies the DS3 lock engine and windows, mine does not). No per-book lock engine, no DS3 stack-add gate (NQ book engine): replaced by the NQ correlation columns.
- **Deviation (disclosed in DECISIONS.md before any result)**: placebo (b) shift for H1 candles drawn from 10..50 min (prereg 30..P-30 is empty for P=60); H4 30..210. Year-share gate is computed on WFPRE in both stages. Daily $ credited to the exit label day; early-close days not modelled (data-gap flat); data end 2026-10-16.
- **Placebos** (20 draws each): (a) timing destroyed (random other label day, same clock minute/side/distances), (b) same rule at a random clock origin (CRT candle grid shifted; S3 session boundary or 15-min grid shifted), (c) random-in-regime (random minute on the same label day). Effect = real minus mean draw, WFPRE weekly $; CI = week bootstrap; rank = share of draws below. Best-of-N primary: family-wise null over all 144 registered (b) effects (p95 3,400 $/wk); secondary per-bracket-class null in the table (CRT_H1 3,400; CRT_H1_ib 2,683; CRT_H4 2,325; CRT_H4_ib 1,933; S3_A 2,019; S3_B 1,857 $/wk). Per-class null never decides a tier.

## Top 10 registered cells by WF equal-risk mean (regardless of verdict)
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | S3_B_N12_tf5m | 2535 | 17.9 | 569 | 584 [-1,754;2,922] | 3,340 | 592 | 636 | +0.033 | 1,472 / 0.95 / MDE 1,746 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,year_share,hold,best_of_N |
| NQ | S3_B_N24_tf5m | 1850 | 13.0 | 666 | 567 [-1,897;3,031] | 3,520 | 449 | 1,178 | +0.043 | 1,120 / 1.00 / MDE 1,682 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,best_of_N |
| ZN | CRT_H4_M1_close_ib | 14 | 0.1 | 74 | 27 [-44;98] | 101 | -26 | -122 | +0.273 | 79 / 1.00 / MDE 131 | 3,400 / 1,933 | DEAD | min_n,beats_b,year_share,hold,span2,best_of_N |
| GC | S3_B_prior_tf5m | 803 | 5.7 | -953 | -110 [-2,532;2,312] | 3,460 | 821 | -3,309 | -0.019 | 2,097 / 1.00 / MDE 3,334 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H1_M1_close_ib | 27 | 0.2 | -99 | -142 [-237;-47] | 136 | -187 | -89 | -0.745 | -19 / 0.45 / MDE 138 | 3,400 / 2,683 | DEAD | min_n,mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M5_close_ib | 38 | 0.3 | -91 | -168 [-295;-41] | 181 | -250 | -461 | -0.627 | 14 / 0.70 / MDE 220 | 3,400 / 1,933 | DEAD | min_n,mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M15_close_ib | 111 | 0.8 | -648 | -475 [-717;-234] | 345 | -278 | -588 | -0.608 | -308 / 0.00 / MDE 458 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_A_prior_tf5m | 1223 | 8.6 | -849 | -534 [-1,756;688] | 1,746 | -178 | 950 | -0.062 | 492 / 0.75 / MDE 2,033 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N |
| ZN | CRT_H1_M5_close_ib | 86 | 0.6 | -566 | -558 [-817;-299] | 370 | -540 | -797 | -0.921 | -152 / 0.00 / MDE 505 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M1_close | 155 | 1.1 | -579 | -558 [-852;-264] | 420 | -526 | -1,276 | -0.511 | -25 / 0.50 / MDE 621 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |

Reading: besides one 14-trade ZN cell (+27 $/wk, under min_n), only NQ S3_B_N12/N24 are positive in WF (+584/+567 $/wk, far below their WF MDE of 3.3-3.5k). They are the only cells with mean>0 that also beat the random-clock placebo (b) in WFPRE (rank 0.95/1.00, CI>0), and HOLD and X are positive too, so they are leads on NQ only (consistent with the library S3_B_N12 PASS, here on a harsher basis); they fail the timing placebo (a), the same-day random-minute placebo (c), cost-x2 and the 144-cell best-of-N, and none of the six other instruments replicates them (ES/RTY/YM/CL/GC/ZN/6E S3_B cells are negative or empty of (b) support). ZN rows have 14-155 WF trades (ZN scaled windows collapse to 4-tick stops) so ZN positives are under min_n. Fewest-gate-failure cells are listed under 'Closest to a CANDIDATE'.

## Closest to a CANDIDATE (fewest failed gates)
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | S3_B_N24_tf5m | 1850 | 13.0 | 666 | 567 [-1,897;3,031] | 3,520 | 449 | 1,178 | +0.043 | 1,120 / 1.00 / MDE 1,682 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,best_of_N |
| NQ | S3_B_N12_tf5m | 2535 | 17.9 | 569 | 584 [-1,754;2,922] | 3,340 | 592 | 636 | +0.033 | 1,472 / 0.95 / MDE 1,746 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,year_share,hold,best_of_N |
| ZN | CRT_H4_M1_close_ib | 14 | 0.1 | 74 | 27 [-44;98] | 101 | -26 | -122 | +0.273 | 79 / 1.00 / MDE 131 | 3,400 / 1,933 | DEAD | min_n,beats_b,year_share,hold,span2,best_of_N |
| NQ | S3_A_prior_tf5m | 1223 | 8.6 | -849 | -534 [-1,756;688] | 1,746 | -178 | 950 | -0.062 | 492 / 0.75 / MDE 2,033 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N |
| YM | S3_A_prior_tf5m | 1124 | 7.9 | -1,350 | -677 [-1,956;602] | 1,827 | 75 | -2,592 | -0.086 | -67 / 0.45 / MDE 1,467 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,span2,best_of_N |

No cell has fewer than 4 failed gates (NQ S3_B_N24 has 4), so no CANDIDATE spec is written.

## NQ (comparator, same basis)
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | CRT_H4_M5_close | 2672 | 18.8 | -1,264 | -1,822 [-3,368;-276] | 2,209 | -2,410 | -835 | -0.097 | 880 / 0.85 / MDE 2,581 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H4_M5_close_ib | 1139 | 8.0 | -827 | -630 [-1,769;509] | 1,628 | -403 | -858 | -0.079 | 1,176 / 1.00 / MDE 2,105 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H4_M1_close | 2519 | 17.7 | -3,981 | -3,473 [-5,491;-1,454] | 2,883 | -2,861 | -976 | -0.196 | -1,055 / 0.15 / MDE 3,398 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H4_M1_close_ib | 820 | 5.8 | -1,934 | -1,538 [-2,591;-485] | 1,504 | -1,079 | -760 | -0.266 | -343 / 0.35 / MDE 1,869 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H1_M5_close | 7938 | 55.9 | -3,497 | -3,907 [-6,144;-1,670] | 3,196 | -4,301 | -8,248 | -0.070 | 1,236 / 0.80 / MDE 3,620 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H1_M5_close_ib | 4387 | 30.9 | -3,189 | -3,468 [-5,103;-1,833] | 2,335 | -3,725 | -4,851 | -0.112 | 58 / 0.60 / MDE 2,975 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H1_M1_close | 7760 | 54.6 | -7,119 | -8,525 [-11,275;-5,775] | 3,929 | -9,950 | -8,083 | -0.156 | 534 / 0.60 / MDE 3,983 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H1_M1_close_ib | 3114 | 21.9 | -4,997 | -4,612 [-6,372;-2,852] | 2,514 | -4,121 | -2,677 | -0.210 | -850 / 0.10 / MDE 2,778 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H4_M15_close | 2281 | 16.1 | -701 | -1,601 [-2,871;-330] | 1,815 | -2,570 | -1,264 | -0.100 | 628 / 0.90 / MDE 2,218 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | CRT_H4_M15_close_ib | 1201 | 8.5 | -276 | -816 [-1,779;147] | 1,376 | -1,400 | -600 | -0.096 | 394 / 0.75 / MDE 1,724 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_A_prior_tf5m | 1223 | 8.6 | -849 | -534 [-1,756;688] | 1,746 | -178 | 950 | -0.062 | 492 / 0.75 / MDE 2,033 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N |
| NQ | S3_A_N12_tf5m | 5706 | 40.2 | -3,250 | -4,197 [-6,206;-2,187] | 2,871 | -5,179 | -2,871 | -0.104 | -666 / 0.05 / MDE 1,605 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_A_N24_tf5m | 4357 | 30.7 | -2,810 | -3,187 [-5,390;-983] | 3,148 | -3,556 | -2,176 | -0.104 | -348 / 0.25 / MDE 1,501 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_A_dev_tf5m | 4960 | 34.9 | -1,903 | -3,044 [-5,463;-625] | 3,456 | -4,257 | -5,174 | -0.087 | 486 / 0.70 / MDE 2,646 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_B_prior_tf5m | 963 | 6.8 | -195 | -1,081 [-3,164;1,003] | 2,976 | -2,041 | -1,686 | -0.159 | 605 / 0.70 / MDE 3,353 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| NQ | S3_B_N12_tf5m | 2535 | 17.9 | 569 | 584 [-1,754;2,922] | 3,340 | 592 | 636 | +0.033 | 1,472 / 0.95 / MDE 1,746 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,year_share,hold,best_of_N |
| NQ | S3_B_N24_tf5m | 1850 | 13.0 | 666 | 567 [-1,897;3,031] | 3,520 | 449 | 1,178 | +0.043 | 1,120 / 1.00 / MDE 1,682 | 3,400 / 1,857 | DEAD | beats_a,beats_c,cost2x_pre,best_of_N |
| NQ | S3_B_dev_tf5m | 1682 | 11.8 | -2,816 | -1,642 [-3,593;309] | 2,787 | -324 | -1,028 | -0.139 | -2,317 / 0.00 / MDE 2,026 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## ES
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ES | CRT_H4_M5_close | 2594 | 18.3 | -5,723 | -6,489 [-7,960;-5,019] | 2,101 | -7,239 | -6,092 | -0.355 | 705 / 0.75 / MDE 2,600 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H4_M5_close_ib | 857 | 6.0 | -1,808 | -2,228 [-3,105;-1,350] | 1,254 | -2,658 | -79 | -0.369 | 675 / 0.90 / MDE 1,679 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H4_M1_close | 2231 | 15.7 | -4,079 | -5,834 [-7,944;-3,724] | 3,014 | -7,684 | -4,286 | -0.371 | 1,755 / 1.00 / MDE 4,138 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H4_M1_close_ib | 516 | 3.6 | -1,171 | -1,113 [-2,150;-77] | 1,481 | -1,033 | -146 | -0.306 | 895 / 1.00 / MDE 2,183 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H1_M5_close | 7088 | 49.9 | -16,389 | -16,705 [-18,631;-14,780] | 2,751 | -16,808 | -15,296 | -0.335 | 31 / 0.55 / MDE 3,728 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H1_M5_close_ib | 3033 | 21.4 | -7,123 | -7,438 [-8,870;-6,006] | 2,045 | -7,676 | -6,148 | -0.348 | 467 / 0.85 / MDE 2,362 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H1_M1_close | 6265 | 44.1 | -18,854 | -20,749 [-23,252;-18,247] | 3,575 | -22,534 | -15,692 | -0.470 | -656 / 0.25 / MDE 4,043 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H1_M1_close_ib | 1656 | 11.7 | -6,274 | -6,506 [-7,661;-5,351] | 1,650 | -6,666 | -3,941 | -0.558 | -269 / 0.35 / MDE 2,048 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H4_M15_close | 2388 | 16.8 | -3,531 | -4,374 [-5,624;-3,123] | 1,787 | -5,239 | -5,039 | -0.260 | 408 / 0.65 / MDE 2,027 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | CRT_H4_M15_close_ib | 1063 | 7.5 | -1,962 | -2,482 [-3,304;-1,661] | 1,174 | -3,020 | -2,494 | -0.332 | 352 / 0.45 / MDE 1,394 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_A_prior_tf5m | 1221 | 8.6 | -973 | -1,720 [-2,937;-504] | 1,738 | -2,520 | -3,517 | -0.200 | 551 / 0.85 / MDE 1,887 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_A_N12_tf5m | 4795 | 33.8 | -7,761 | -8,100 [-10,069;-6,132] | 2,812 | -8,356 | -10,563 | -0.240 | 684 / 1.00 / MDE 1,599 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_A_N24_tf5m | 3795 | 26.7 | -6,101 | -6,293 [-8,250;-4,336] | 2,796 | -6,412 | -6,660 | -0.235 | 258 / 0.55 / MDE 1,756 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_A_dev_tf5m | 3910 | 27.5 | -5,454 | -6,276 [-8,410;-4,143] | 3,048 | -7,092 | -8,831 | -0.228 | -1,723 / 0.10 / MDE 2,278 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_B_prior_tf5m | 907 | 6.4 | -601 | -2,214 [-3,905;-523] | 2,415 | -3,961 | -4,342 | -0.347 | 719 / 0.70 / MDE 3,058 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_B_N12_tf5m | 2471 | 17.4 | -7,414 | -7,054 [-9,245;-4,864] | 3,129 | -6,553 | -7,945 | -0.405 | 296 / 0.95 / MDE 1,439 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_B_N24_tf5m | 1806 | 12.7 | -4,702 | -4,382 [-6,402;-2,363] | 2,885 | -3,965 | -7,238 | -0.345 | 867 / 1.00 / MDE 1,728 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ES | S3_B_dev_tf5m | 1555 | 11.0 | -4,429 | -3,870 [-5,803;-1,938] | 2,761 | -3,197 | -5,880 | -0.353 | -169 / 0.45 / MDE 2,440 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## RTY
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RTY | CRT_H4_M5_close | 2621 | 18.5 | -5,302 | -4,434 [-6,153;-2,715] | 2,455 | -3,412 | -4,403 | -0.240 | -49 / 0.45 / MDE 2,773 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H4_M5_close_ib | 939 | 6.6 | -1,585 | -1,315 [-2,374;-256] | 1,513 | -998 | -1,663 | -0.199 | -363 / 0.35 / MDE 1,464 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H4_M1_close | 2241 | 15.8 | -6,903 | -5,522 [-7,502;-3,542] | 2,829 | -3,917 | -4,364 | -0.350 | -1,924 / 0.00 / MDE 2,812 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H4_M1_close_ib | 602 | 4.2 | -2,289 | -1,842 [-2,718;-967] | 1,251 | -1,323 | -1,323 | -0.435 | -1,175 / 0.00 / MDE 1,421 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H1_M5_close | 7304 | 51.4 | -11,981 | -13,251 [-15,522;-10,980] | 3,245 | -14,457 | -13,531 | -0.258 | 1,902 / 1.00 / MDE 3,068 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H1_M5_close_ib | 3438 | 24.2 | -5,617 | -5,887 [-7,506;-4,267] | 2,314 | -6,097 | -6,138 | -0.243 | -648 / 0.15 / MDE 2,408 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H1_M1_close | 6306 | 44.4 | -14,745 | -16,354 [-19,100;-13,607] | 3,923 | -17,887 | -12,132 | -0.368 | 974 / 0.75 / MDE 4,433 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H1_M1_close_ib | 1988 | 14.0 | -5,828 | -6,321 [-7,825;-4,817] | 2,149 | -6,772 | -1,751 | -0.452 | -1,386 / 0.00 / MDE 2,619 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H4_M15_close | 2328 | 16.4 | -3,406 | -3,296 [-4,593;-1,999] | 1,853 | -3,127 | -3,299 | -0.201 | 338 / 0.70 / MDE 2,115 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | CRT_H4_M15_close_ib | 1159 | 8.2 | -1,191 | -1,784 [-2,779;-788] | 1,422 | -2,412 | -1,735 | -0.219 | 536 / 0.70 / MDE 1,797 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_A_prior_tf5m | 1089 | 7.7 | -1,286 | -1,011 [-2,198;175] | 1,695 | -694 | -1,475 | -0.132 | -203 / 0.30 / MDE 1,659 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_A_N12_tf5m | 5165 | 36.4 | -7,370 | -8,448 [-10,373;-6,522] | 2,751 | -9,512 | -9,846 | -0.232 | 596 / 0.90 / MDE 1,744 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_A_N24_tf5m | 4047 | 28.5 | -3,658 | -6,225 [-8,108;-4,343] | 2,689 | -8,966 | -5,282 | -0.218 | 1,179 / 1.00 / MDE 1,815 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_A_dev_tf5m | 4458 | 31.4 | -3,353 | -6,422 [-8,332;-4,513] | 2,727 | -9,714 | -6,393 | -0.205 | -35 / 0.50 / MDE 1,969 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_B_prior_tf5m | 779 | 5.5 | -2,949 | -2,852 [-4,276;-1,429] | 2,033 | -2,704 | 495 | -0.520 | -535 / 0.05 / MDE 2,199 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| RTY | S3_B_N12_tf5m | 2395 | 16.9 | -6,860 | -6,275 [-8,213;-4,338] | 2,768 | -5,538 | -1,306 | -0.372 | -401 / 0.30 / MDE 1,761 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| RTY | S3_B_N24_tf5m | 1713 | 12.1 | -5,100 | -5,036 [-6,732;-3,339] | 2,424 | -4,891 | 961 | -0.417 | -577 / 0.25 / MDE 1,242 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| RTY | S3_B_dev_tf5m | 1555 | 11.0 | -4,472 | -4,361 [-5,940;-2,782] | 2,256 | -4,173 | -1,195 | -0.398 | -64 / 0.55 / MDE 1,876 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## YM
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| YM | CRT_H4_M5_close | 2491 | 17.5 | -4,827 | -4,170 [-5,624;-2,716] | 2,077 | -3,385 | -493 | -0.238 | -1,511 / 0.05 / MDE 2,221 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H4_M5_close_ib | 855 | 6.0 | -1,733 | -1,576 [-2,531;-620] | 1,365 | -1,378 | 1,096 | -0.262 | -485 / 0.15 / MDE 1,497 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| YM | CRT_H4_M1_close | 1994 | 14.0 | -3,886 | -4,008 [-5,808;-2,208] | 2,572 | -4,083 | 26 | -0.285 | -1,194 / 0.15 / MDE 2,481 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| YM | CRT_H4_M1_close_ib | 510 | 3.6 | -1,278 | -1,322 [-2,171;-474] | 1,212 | -1,352 | 881 | -0.368 | -737 / 0.05 / MDE 1,479 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| YM | CRT_H1_M5_close | 6794 | 47.8 | -7,313 | -8,919 [-10,713;-7,124] | 2,563 | -10,558 | -9,265 | -0.186 | 1,198 / 1.00 / MDE 3,347 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H1_M5_close_ib | 3192 | 22.5 | -2,824 | -4,189 [-5,603;-2,775] | 2,020 | -5,633 | -3,829 | -0.186 | 1,018 / 0.95 / MDE 2,897 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H1_M1_close | 5520 | 38.9 | -8,589 | -9,820 [-11,822;-7,818] | 2,860 | -11,034 | -8,735 | -0.253 | 705 / 0.70 / MDE 4,537 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H1_M1_close_ib | 1745 | 12.3 | -3,538 | -3,611 [-4,895;-2,327] | 1,834 | -3,638 | -2,878 | -0.294 | -974 / 0.25 / MDE 2,519 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H4_M15_close | 2274 | 16.0 | -2,716 | -2,748 [-4,045;-1,450] | 1,853 | -2,742 | -1,143 | -0.172 | 141 / 0.50 / MDE 2,388 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | CRT_H4_M15_close_ib | 1062 | 7.5 | -1,549 | -1,052 [-1,920;-184] | 1,240 | -488 | 323 | -0.141 | -30 / 0.50 / MDE 1,476 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,best_of_N |
| YM | S3_A_prior_tf5m | 1124 | 7.9 | -1,350 | -677 [-1,956;602] | 1,827 | 75 | -2,592 | -0.086 | -67 / 0.45 / MDE 1,467 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,span2,best_of_N |
| YM | S3_A_N12_tf5m | 5072 | 35.7 | -6,420 | -6,104 [-7,836;-4,372] | 2,474 | -5,665 | -5,582 | -0.171 | -22 / 0.40 / MDE 1,470 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_A_N24_tf5m | 4098 | 28.9 | -4,087 | -4,258 [-6,322;-2,194] | 2,949 | -4,384 | -3,765 | -0.148 | 106 / 0.55 / MDE 1,386 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_A_dev_tf5m | 4487 | 31.6 | -5,097 | -4,972 [-7,035;-2,909] | 2,947 | -4,761 | -4,030 | -0.157 | -2,336 / 0.05 / MDE 2,330 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_B_prior_tf5m | 723 | 5.1 | 632 | -593 [-2,220;1,034] | 2,324 | -1,936 | -2,902 | -0.116 | 1,340 / 0.90 / MDE 2,926 | 3,400 / 1,857 | DEAD | beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_B_N12_tf5m | 2290 | 16.1 | -3,064 | -2,676 [-4,560;-791] | 2,692 | -2,208 | -5,559 | -0.166 | 495 / 0.85 / MDE 1,873 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_B_N24_tf5m | 1659 | 11.7 | -2,746 | -2,540 [-4,451;-630] | 2,729 | -2,276 | -4,468 | -0.217 | -166 / 0.30 / MDE 1,632 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| YM | S3_B_dev_tf5m | 1480 | 10.4 | -1,784 | -1,652 [-3,671;367] | 2,884 | -1,483 | -5,588 | -0.159 | 78 / 0.60 / MDE 1,859 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## CL
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CL | CRT_H4_M5_close | 2332 | 16.4 | -5,434 | -5,746 [-6,942;-4,550] | 1,708 | -6,006 | -5,981 | -0.350 | -843 / 0.00 / MDE 1,826 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H4_M5_close_ib | 777 | 5.5 | -2,155 | -2,199 [-2,957;-1,442] | 1,082 | -2,215 | -2,223 | -0.402 | -848 / 0.00 / MDE 1,080 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H4_M1_close | 1693 | 11.9 | -5,818 | -5,393 [-6,707;-4,080] | 1,877 | -4,846 | -5,634 | -0.452 | -1,768 / 0.00 / MDE 1,907 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H4_M1_close_ib | 465 | 3.3 | -1,641 | -1,189 [-2,172;-205] | 1,405 | -673 | -873 | -0.363 | -860 / 0.00 / MDE 853 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H1_M5_close | 5838 | 41.1 | -9,452 | -9,668 [-11,295;-8,041] | 2,324 | -9,764 | -13,787 | -0.235 | 1,268 / 0.95 / MDE 2,993 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H1_M5_close_ib | 2506 | 17.6 | -4,921 | -5,133 [-6,222;-4,044] | 1,555 | -5,292 | -5,273 | -0.291 | -685 / 0.00 / MDE 1,835 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H1_M1_close | 4427 | 31.2 | -9,051 | -9,910 [-11,818;-8,002] | 2,726 | -10,711 | -13,266 | -0.318 | 173 / 0.50 / MDE 3,177 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H1_M1_close_ib | 1323 | 9.3 | -2,366 | -3,063 [-4,251;-1,875] | 1,697 | -3,786 | -2,884 | -0.329 | -98 / 0.45 / MDE 1,650 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H4_M15_close | 2359 | 16.6 | -4,398 | -4,495 [-5,589;-3,401] | 1,563 | -4,537 | -4,638 | -0.271 | -777 / 0.05 / MDE 1,908 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | CRT_H4_M15_close_ib | 987 | 7.0 | -2,600 | -2,042 [-2,799;-1,285] | 1,081 | -1,396 | -2,101 | -0.294 | -1,205 / 0.00 / MDE 1,064 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_A_prior_tf5m | 1251 | 8.8 | -1,725 | -1,869 [-3,123;-615] | 1,791 | -2,000 | 720 | -0.212 | -184 / 0.35 / MDE 1,484 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,best_of_N |
| CL | S3_A_N12_tf5m | 4396 | 31.0 | -5,872 | -5,511 [-7,120;-3,903] | 2,298 | -5,033 | -7,962 | -0.178 | 1,115 / 1.00 / MDE 1,612 | 3,400 / 2,019 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_A_N24_tf5m | 3629 | 25.6 | -6,239 | -5,112 [-6,712;-3,511] | 2,286 | -3,793 | -7,097 | -0.200 | 992 / 1.00 / MDE 1,636 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_A_dev_tf5m | 3591 | 25.3 | -7,091 | -5,628 [-7,185;-4,071] | 2,224 | -3,932 | -7,781 | -0.223 | -864 / 0.20 / MDE 1,407 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_B_prior_tf5m | 770 | 5.4 | -1,995 | -1,655 [-2,994;-317] | 1,912 | -1,256 | -1,627 | -0.305 | 720 / 0.85 / MDE 1,780 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_B_N12_tf5m | 2012 | 14.2 | -5,924 | -4,896 [-6,634;-3,158] | 2,483 | -3,690 | -8,282 | -0.346 | 4 / 0.45 / MDE 1,184 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| CL | S3_B_N24_tf5m | 1516 | 10.7 | -4,323 | -2,156 [-4,151;-161] | 2,850 | 266 | -6,790 | -0.202 | 2 / 0.50 / MDE 1,058 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,span2,best_of_N |
| CL | S3_B_dev_tf5m | 1289 | 9.1 | -3,203 | -2,226 [-3,948;-504] | 2,460 | -1,116 | -5,741 | -0.245 | 160 / 0.50 / MDE 1,326 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## GC
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GC | CRT_H4_M5_close | 2334 | 16.4 | -3,843 | -3,457 [-5,025;-1,889] | 2,240 | -2,980 | -6,680 | -0.210 | 2,102 / 1.00 / MDE 2,939 | 3,400 / 2,325 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H4_M5_close_ib | 1109 | 7.8 | -2,035 | -2,330 [-3,556;-1,104] | 1,751 | -2,622 | -2,495 | -0.298 | 976 / 1.00 / MDE 2,411 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H4_M1_close | 2885 | 20.3 | -6,431 | -5,486 [-7,876;-3,095] | 3,415 | -4,363 | -6,233 | -0.270 | 3,130 / 1.00 / MDE 3,858 | 3,400 / 2,325 | DEAD | mean_up,beats_a,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H4_M1_close_ib | 998 | 7.0 | -2,040 | -1,611 [-3,384;163] | 2,533 | -1,113 | -1,185 | -0.229 | 1,078 / 1.00 / MDE 2,567 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H1_M5_close | 7647 | 53.9 | -19,000 | -13,463 [-15,923;-11,002] | 3,515 | -7,158 | -21,061 | -0.250 | -937 / 0.30 / MDE 3,715 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H1_M5_close_ib | 4095 | 28.8 | -10,016 | -8,085 [-9,969;-6,200] | 2,692 | -5,836 | -10,433 | -0.280 | 1,467 / 0.95 / MDE 2,834 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H1_M1_close | 9459 | 66.6 | -25,826 | -22,378 [-25,944;-18,813] | 5,094 | -18,246 | -24,068 | -0.336 | 2,430 / 0.90 / MDE 5,437 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H1_M1_close_ib | 3537 | 24.9 | -8,874 | -8,827 [-11,289;-6,365] | 3,517 | -8,645 | -5,784 | -0.354 | 2,405 / 0.95 / MDE 3,557 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H4_M15_close | 1691 | 11.9 | -2,515 | -2,146 [-3,354;-938] | 1,726 | -1,707 | -4,278 | -0.180 | 1,346 / 0.85 / MDE 2,571 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | CRT_H4_M15_close_ib | 963 | 6.8 | -1,654 | -1,452 [-2,433;-471] | 1,402 | -1,208 | -2,126 | -0.214 | 1,220 / 1.00 / MDE 2,081 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_A_prior_tf5m | 841 | 5.9 | -1,805 | -1,396 [-2,442;-350] | 1,494 | -924 | -2,334 | -0.236 | -115 / 0.50 / MDE 1,352 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_A_N12_tf5m | 4369 | 30.8 | -8,279 | -6,116 [-8,047;-4,185] | 2,758 | -3,641 | -8,938 | -0.199 | 60 / 0.55 / MDE 1,612 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_A_N24_tf5m | 3183 | 22.4 | -7,904 | -5,408 [-7,453;-3,363] | 2,922 | -2,575 | -5,577 | -0.241 | 48 / 0.40 / MDE 1,580 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_A_dev_tf5m | 3365 | 23.7 | -9,967 | -6,894 [-8,712;-5,076] | 2,597 | -3,403 | -6,499 | -0.291 | -3,399 / 0.00 / MDE 2,444 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_B_prior_tf5m | 803 | 5.7 | -953 | -110 [-2,532;2,312] | 3,460 | 821 | -3,309 | -0.019 | 2,097 / 1.00 / MDE 3,334 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_B_N12_tf5m | 2492 | 17.5 | -8,874 | -6,019 [-8,234;-3,803] | 3,165 | -2,781 | -6,031 | -0.343 | -1,381 / 0.00 / MDE 1,728 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_B_N24_tf5m | 1696 | 11.9 | -5,717 | -4,108 [-6,080;-2,135] | 2,818 | -2,272 | -123 | -0.344 | -181 / 0.50 / MDE 1,932 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| GC | S3_B_dev_tf5m | 1576 | 11.1 | -5,274 | -3,871 [-5,699;-2,044] | 2,610 | -2,267 | -4,362 | -0.349 | -792 / 0.15 / MDE 2,425 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## ZN
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ZN | CRT_H4_M5_close | 355 | 2.5 | -2,033 | -1,660 [-2,101;-1,219] | 631 | -1,224 | -3,113 | -0.664 | -321 / 0.00 / MDE 806 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M5_close_ib | 38 | 0.3 | -91 | -168 [-295;-41] | 181 | -250 | -461 | -0.627 | 14 / 0.70 / MDE 220 | 3,400 / 1,933 | DEAD | min_n,mean_up,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M1_close | 155 | 1.1 | -579 | -558 [-852;-264] | 420 | -526 | -1,276 | -0.511 | -25 / 0.50 / MDE 621 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M1_close_ib | 14 | 0.1 | 74 | 27 [-44;98] | 101 | -26 | -122 | +0.273 | 79 / 1.00 / MDE 131 | 3,400 / 1,933 | DEAD | min_n,beats_b,year_share,hold,span2,best_of_N |
| ZN | CRT_H1_M5_close | 463 | 3.3 | -3,354 | -2,579 [-3,252;-1,907] | 960 | -1,688 | -4,097 | -0.791 | -399 / 0.00 / MDE 968 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H1_M5_close_ib | 86 | 0.6 | -566 | -558 [-817;-299] | 370 | -540 | -797 | -0.921 | -152 / 0.00 / MDE 505 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H1_M1_close | 167 | 1.2 | -951 | -838 [-1,138;-539] | 428 | -702 | -1,208 | -0.713 | -67 / 0.25 / MDE 668 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H1_M1_close_ib | 27 | 0.2 | -99 | -142 [-237;-47] | 136 | -187 | -89 | -0.745 | -19 / 0.45 / MDE 138 | 3,400 / 2,683 | DEAD | min_n,mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M15_close | 578 | 4.1 | -2,676 | -2,250 [-2,768;-1,731] | 741 | -1,747 | -4,752 | -0.553 | -16 / 0.50 / MDE 1,037 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | CRT_H4_M15_close_ib | 111 | 0.8 | -648 | -475 [-717;-234] | 345 | -278 | -588 | -0.608 | -308 / 0.00 / MDE 458 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_A_prior_tf5m | 471 | 3.3 | -2,039 | -1,415 [-1,991;-838] | 824 | -705 | -2,636 | -0.426 | -39 / 0.30 / MDE 880 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_A_N12_tf5m | 581 | 4.1 | -2,768 | -2,420 [-2,985;-1,855] | 807 | -2,001 | -3,700 | -0.591 | -38 / 0.45 / MDE 650 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_A_N24_tf5m | 624 | 4.4 | -2,735 | -2,446 [-3,020;-1,872] | 820 | -2,092 | -2,789 | -0.557 | -210 / 0.30 / MDE 622 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_A_dev_tf5m | 485 | 3.4 | -1,788 | -1,963 [-2,460;-1,466] | 710 | -2,126 | -2,320 | -0.575 | -81 / 0.15 / MDE 397 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_B_prior_tf5m | 233 | 1.6 | -1,713 | -1,460 [-1,848;-1,072] | 555 | -1,160 | -1,902 | -0.890 | -99 / 0.45 / MDE 842 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_B_N12_tf5m | 468 | 3.3 | -3,493 | -2,906 [-3,549;-2,264] | 918 | -2,216 | -5,058 | -0.882 | 72 / 0.80 / MDE 445 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_B_N24_tf5m | 427 | 3.0 | -2,924 | -2,408 [-2,973;-1,844] | 807 | -1,804 | -4,512 | -0.801 | 101 / 1.00 / MDE 447 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| ZN | S3_B_dev_tf5m | 323 | 2.3 | -2,061 | -1,776 [-2,337;-1,214] | 802 | -1,435 | -3,708 | -0.781 | 221 / 1.00 / MDE 611 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## 6E
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 6E | CRT_H4_M5_close | 2261 | 15.9 | -7,001 | -7,558 [-8,924;-6,192] | 1,951 | -8,061 | -10,808 | -0.475 | 919 / 0.65 / MDE 2,664 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H4_M5_close_ib | 506 | 3.6 | -1,732 | -1,760 [-2,557;-963] | 1,139 | -1,764 | -3,010 | -0.494 | 190 / 0.80 / MDE 1,391 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H4_M1_close | 1541 | 10.9 | -7,782 | -7,340 [-8,680;-6,000] | 1,915 | -6,744 | -9,027 | -0.676 | 63 / 0.50 / MDE 2,885 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H4_M1_close_ib | 231 | 1.6 | -1,054 | -850 [-1,472;-228] | 889 | -612 | -387 | -0.522 | 175 / 0.70 / MDE 1,167 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H1_M5_close | 5401 | 38.0 | -20,571 | -20,257 [-22,229;-18,285] | 2,817 | -19,614 | -24,487 | -0.533 | 85 / 0.35 / MDE 3,290 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H1_M5_close_ib | 1821 | 12.8 | -7,552 | -7,225 [-8,265;-6,185] | 1,485 | -6,758 | -8,287 | -0.563 | -757 / 0.05 / MDE 1,917 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H1_M1_close | 3473 | 24.5 | -18,809 | -17,259 [-19,400;-15,119] | 3,057 | -15,296 | -19,625 | -0.706 | 334 / 0.60 / MDE 3,382 | 3,400 / 3,400 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H1_M1_close_ib | 663 | 4.7 | -3,656 | -2,919 [-3,688;-2,150] | 1,099 | -2,063 | -3,746 | -0.625 | -289 / 0.35 / MDE 1,274 | 3,400 / 2,683 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H4_M15_close | 2309 | 16.3 | -5,905 | -6,737 [-7,891;-5,582] | 1,649 | -7,556 | -7,522 | -0.414 | 589 / 0.40 / MDE 1,967 | 3,400 / 2,325 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | CRT_H4_M15_close_ib | 826 | 5.8 | -2,028 | -2,322 [-3,200;-1,445] | 1,254 | -2,613 | -3,431 | -0.399 | 534 / 0.65 / MDE 1,795 | 3,400 / 1,933 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_A_prior_tf5m | 1060 | 7.5 | -2,212 | -2,257 [-3,219;-1,296] | 1,373 | -2,274 | -2,388 | -0.302 | 180 / 0.55 / MDE 1,251 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_A_N12_tf5m | 3852 | 27.1 | -9,647 | -10,375 [-11,807;-8,942] | 2,046 | -11,025 | -10,771 | -0.382 | 75 / 0.35 / MDE 1,381 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_A_N24_tf5m | 3132 | 22.1 | -7,794 | -8,049 [-9,359;-6,739] | 1,872 | -8,212 | -8,461 | -0.365 | -61 / 0.40 / MDE 1,621 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_A_dev_tf5m | 2956 | 20.8 | -6,601 | -8,016 [-9,399;-6,632] | 1,976 | -9,457 | -8,100 | -0.385 | -741 / 0.20 / MDE 1,420 | 3,400 / 2,019 | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_B_prior_tf5m | 770 | 5.4 | -3,247 | -3,444 [-4,778;-2,110] | 1,906 | -3,611 | -3,234 | -0.635 | 197 / 0.50 / MDE 2,056 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_B_N12_tf5m | 2168 | 15.3 | -9,659 | -10,846 [-12,537;-9,156] | 2,415 | -11,996 | -10,615 | -0.710 | -470 / 0.30 / MDE 1,473 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_B_N24_tf5m | 1552 | 10.9 | -7,380 | -8,267 [-9,892;-6,641] | 2,322 | -9,123 | -9,292 | -0.756 | -193 / 0.30 / MDE 1,094 | 3,400 / 1,857 | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| 6E | S3_B_dev_tf5m | 1356 | 9.5 | -3,922 | -6,164 [-7,645;-4,683] | 2,116 | -8,545 | -8,932 | -0.645 | 1,127 / 1.00 / MDE 1,914 | 3,400 / 1,857 | DEAD | mean_up,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## POOLED (sum of the 7 non-NQ instruments, each at $1,000 risk per trade; N=18 for its best-of-N)
| inst | cell | n WF | tr/wk | WFPRE $/wk | WF $/wk [95% CI] | WF MDE | HOLD $/wk | X(2023-04..2024-01) $/wk | WF R/trade | (b) effect / rank / MDE (WFPRE) | best-of-N p95 primary / class | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| POOL | CRT_H4_M5_close | 14988 | 105.5 | -34,162 | -33,515 [-37,640;-29,389] | 5,893 | -32,308 | -37,571 | -0.318 | 1,003 / 0.75 / MDE 6,449 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H4_M5_close_ib | 5081 | 35.8 | -11,139 | -11,575 [-14,156;-8,994] | 3,687 | -11,885 | -8,837 | -0.323 | 159 / 0.45 / MDE 4,812 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H4_M1_close | 12740 | 89.7 | -35,479 | -34,141 [-39,032;-29,250] | 6,987 | -32,164 | -30,794 | -0.381 | 37 / 0.40 / MDE 8,295 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H4_M1_close_ib | 3336 | 23.5 | -9,398 | -7,901 [-10,368;-5,433] | 3,525 | -6,133 | -3,155 | -0.336 | -546 / 0.30 / MDE 4,344 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H1_M5_close | 40535 | 285.5 | -88,060 | -84,843 [-90,145;-79,540] | 7,575 | -80,047 | -101,523 | -0.297 | 3,148 / 0.85 / MDE 9,869 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H1_M5_close_ib | 18171 | 128.0 | -38,620 | -38,514 [-42,218;-34,810] | 5,291 | -37,832 | -40,906 | -0.301 | 710 / 0.70 / MDE 6,372 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H1_M1_close | 35617 | 250.8 | -96,826 | -97,309 [-103,409;-91,209] | 8,714 | -96,411 | -94,727 | -0.388 | 3,895 / 0.90 / MDE 10,953 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H1_M1_close_ib | 10939 | 77.0 | -30,636 | -31,389 [-35,154;-27,624] | 5,379 | -31,758 | -21,072 | -0.407 | -629 / 0.35 / MDE 6,262 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H4_M15_close | 13927 | 98.1 | -25,146 | -26,045 [-29,524;-22,566] | 4,970 | -26,654 | -30,671 | -0.266 | 2,030 / 0.85 / MDE 5,768 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | CRT_H4_M15_close_ib | 6171 | 43.5 | -11,632 | -11,610 [-13,900;-9,320] | 3,271 | -11,415 | -12,150 | -0.267 | 1,098 / 0.85 / MDE 3,906 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_A_prior_tf5m | 7057 | 49.7 | -11,390 | -10,346 [-13,661;-7,031] | 4,736 | -9,042 | -14,222 | -0.208 | 123 / 0.55 / MDE 3,632 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_A_N12_tf5m | 28230 | 198.8 | -48,117 | -47,074 [-52,054;-42,095] | 7,114 | -45,233 | -57,361 | -0.237 | 2,471 / 1.00 / MDE 3,887 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_A_N24_tf5m | 22508 | 158.5 | -38,518 | -37,792 [-43,290;-32,293] | 7,855 | -36,435 | -39,632 | -0.238 | 2,312 / 1.00 / MDE 3,974 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_A_dev_tf5m | 23252 | 163.7 | -39,351 | -40,171 [-45,250;-35,092] | 7,255 | -40,486 | -43,954 | -0.245 | -9,179 / 0.00 / MDE 4,945 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_B_prior_tf5m | 4985 | 35.1 | -10,825 | -12,329 [-16,823;-7,835] | 6,420 | -13,807 | -16,820 | -0.351 | 4,440 / 1.00 / MDE 6,263 | 5,592 /  | DEAD | mean_up,beats_a,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_B_N12_tf5m | 14296 | 100.7 | -45,288 | -40,672 [-46,625;-34,719] | 8,504 | -34,983 | -44,796 | -0.404 | -1,386 / 0.15 / MDE 4,629 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_B_N24_tf5m | 10369 | 73.0 | -32,893 | -28,897 [-34,275;-23,519] | 7,683 | -24,065 | -31,463 | -0.396 | -147 / 0.45 / MDE 3,815 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |
| POOL | S3_B_dev_tf5m | 9134 | 64.3 | -25,145 | -23,920 [-29,138;-18,702] | 7,454 | -22,217 | -35,406 | -0.372 | 562 / 0.65 / MDE 5,066 | 5,592 /  | DEAD | mean_up,beats_a,beats_b,beats_c,cost2x_pre,year_share,hold,span2,best_of_N |

## Cost-free diagnostic (WF, per instrument median over the 18 cells)
Cost-free = no slippage, no fee (targets still need a 1-tick trade-through). Net R/trade = after the tick basis and fees. Stop ticks = median stop distance in ticks; slippage is 3 ticks round trip plus fee, so tight stops are structurally unpayable.
| inst | cost-free R/trade | net R/trade | median stop (ticks) | median lots at $1,000 risk | fee RT |
|---|---|---|---|---|---|
| NQ | -0.031 | -0.102 | 49.5 | 4.0 | 4.84 (PROXY (ES value; comparator)) |
| ES | -0.041 | -0.346 | 11.5 | 7.0 | 4.84 (NT-published) |
| RTY | -0.024 | -0.250 | 15.0 | 13.3 | 4.84 (WEAK proxy (ES)) |
| YM | +0.000 | -0.179 | 18.5 | 10.8 | 4.84 (WEAK proxy (ES)) |
| CL | -0.022 | -0.292 | 12.0 | 8.3 | 4.84 (WEAK proxy (ES)) |
| GC | -0.040 | -0.260 | 17.5 | 5.7 | 4.84 (WEAK proxy (ES)) |
| ZN | -0.120 | -0.646 | 5.0 | 12.8 | 4.84 (WEAK proxy (ES)) |
| 6E | -0.037 | -0.527 | 7.0 | 22.9 | 5.3 (WEAK (NT lifetime addendum, third-party exchange fee)) |

## Correlation with the NQ CRT cell (weekly equal-risk $, 2023-02-10..2026-10-16, FINAL stage after the look)
Columns: same cell on NQ / NQ CRT_H4_M5_close (the published DS3 candidate). Every correlation is of two negative-mean series; read as co-movement of the rule's P&L, not of an edge.
| cell | ES | RTY | YM | CL | GC | ZN | 6E | POOL |
|---|---|---|---|---|---|---|---|---|
| CRT_H4_M5_close | +0.31 / +0.31 | +0.05 / +0.05 | +0.02 / +0.02 | -0.00 / -0.00 | +0.06 / +0.06 | -0.09 / -0.09 | -0.02 / -0.02 | +0.14 / +0.14 |
| CRT_H4_M5_close_ib | +0.22 / +0.23 | +0.11 / +0.10 | +0.07 / +0.10 | +0.03 / -0.10 | +0.04 / +0.07 | -0.02 / -0.03 | +0.07 / +0.03 | +0.19 / +0.17 |
| CRT_H4_M1_close | +0.25 / +0.24 | +0.05 / +0.03 | -0.01 / -0.01 | +0.16 / -0.05 | -0.04 / +0.11 | -0.03 / -0.01 | +0.04 / -0.02 | +0.17 / +0.15 |
| CRT_H4_M1_close_ib | +0.25 / +0.13 | +0.04 / +0.09 | +0.01 / +0.05 | +0.03 / +0.06 | -0.07 / -0.03 | +0.01 / +0.09 | +0.12 / -0.04 | +0.11 / +0.10 |
| CRT_H1_M5_close | +0.15 / +0.02 | +0.16 / +0.08 | +0.01 / -0.04 | +0.06 / +0.01 | +0.08 / +0.07 | +0.02 / -0.07 | +0.02 / -0.00 | +0.19 / +0.05 |
| CRT_H1_M5_close_ib | +0.16 / -0.02 | -0.03 / +0.11 | +0.11 / +0.04 | +0.02 / -0.00 | +0.12 / +0.07 | -0.07 / -0.05 | -0.07 / +0.05 | +0.12 / +0.10 |
| CRT_H1_M1_close | +0.09 / +0.13 | +0.12 / +0.05 | -0.05 / +0.07 | -0.01 / -0.02 | +0.02 / +0.00 | +0.04 / +0.05 | +0.03 / +0.03 | +0.10 / +0.10 |
| CRT_H1_M1_close_ib | +0.02 / +0.16 | +0.03 / +0.14 | +0.01 / -0.03 | +0.05 / -0.02 | -0.01 / -0.07 | +0.11 / -0.06 | -0.03 / +0.00 | +0.03 / +0.04 |
| CRT_H4_M15_close | +0.41 / +0.32 | +0.17 / +0.07 | +0.11 / +0.09 | +0.05 / +0.06 | +0.13 / +0.11 | -0.05 / -0.02 | -0.01 / -0.06 | +0.31 / +0.22 |
| CRT_H4_M15_close_ib | +0.26 / +0.27 | +0.16 / +0.12 | +0.06 / +0.11 | +0.06 / -0.01 | +0.13 / +0.17 | +0.02 / +0.01 | -0.15 / -0.00 | +0.19 / +0.26 |
| S3_A_prior_tf5m | +0.39 / -0.07 | +0.22 / -0.01 | +0.04 / +0.01 | +0.06 / +0.05 | -0.07 / -0.03 | -0.02 / +0.09 | -0.10 / -0.02 | +0.20 / -0.01 |
| S3_A_N12_tf5m | +0.40 / +0.12 | +0.07 / +0.02 | +0.13 / +0.03 | -0.02 / -0.00 | +0.03 / +0.02 | -0.08 / -0.05 | +0.08 / +0.08 | +0.24 / +0.08 |
| S3_A_N24_tf5m | +0.37 / +0.20 | +0.08 / +0.04 | +0.06 / +0.05 | -0.01 / +0.05 | +0.16 / +0.03 | -0.00 / -0.07 | +0.12 / +0.10 | +0.26 / +0.14 |
| S3_A_dev_tf5m | +0.36 / +0.07 | +0.05 / +0.08 | +0.06 / +0.01 | -0.01 / +0.02 | +0.01 / +0.02 | -0.06 / +0.02 | +0.04 / +0.05 | +0.19 / +0.09 |
| S3_B_prior_tf5m | +0.19 / -0.07 | +0.01 / +0.02 | +0.03 / +0.01 | -0.05 / -0.04 | +0.07 / +0.04 | -0.07 / +0.11 | +0.03 / -0.06 | +0.11 / -0.01 |
| S3_B_N12_tf5m | +0.09 / -0.11 | +0.08 / -0.02 | +0.08 / -0.12 | +0.01 / -0.06 | -0.02 / +0.03 | +0.11 / +0.02 | +0.00 / +0.00 | +0.09 / -0.09 |
| S3_B_N24_tf5m | +0.25 / -0.09 | -0.01 / +0.11 | +0.10 / -0.11 | +0.07 / -0.02 | -0.01 / +0.08 | +0.03 / +0.03 | +0.05 / -0.01 | +0.16 / -0.00 |
| S3_B_dev_tf5m | +0.11 / -0.20 | +0.16 / +0.01 | +0.00 / +0.06 | +0.04 / -0.07 | -0.07 / +0.05 | +0.01 / +0.02 | +0.03 / +0.01 | +0.09 / -0.05 |

Mean same-cell correlation with NQ: CRT cells ES +0.21, RTY +0.09, YM +0.03, CL +0.05, GC +0.05, ZN -0.01, 6E +0.00; S3 cells ES +0.27, RTY +0.08, YM +0.06, CL +0.01, GC +0.01, ZN -0.01, 6E +0.03.

## Paired per-trade tests and MDE (WFPRE; full per-cell values in l2vast/ds3/prereg/D3CX_<SYM>_pretext.md)
Real minus placebo trade built from the same event, R per trade with 95% t-CI and MDE. The (c) pairing is positive for S3_A and the CRT H4/H1_M5 close cells on NQ (+0.1 to +0.4 R per trade over a random minute on the same day) but negative for S3_B; the real series is itself negative in most of these, so the placebo is worse, not the real good. (a) pairing is ~0 with MDE 0.08-0.6 R: the clock/day of the signal adds nothing detectable. See per-group pre texts.

## Answers to the directive
1. Per instrument and pooled: all DEAD; tables above. 2. Cross-instrument correlation: table above. 3. Same random-clock-offset placebo: (b) is in every row; 7 of 144 cells beat it (rank >= .95 and CI > 0) but only NQ S3_B_N12/N24 do so with mean>0 on the conservative basis; no ES/RTY/YM/CL/GC/ZN/6E cell does. Gate counts across 144: mean_up 4, beats_a 3, beats_b 7, beats_c 51.

## NEEDS (not done; no purchase or download made)
- NEEDS: one NT statement line for a round trip in RTY, YM, CL, GC, ZN and 6E (exchange+NFA) to lift the WEAK cap; with no CANDIDATE it is moot for these cells.
- NEEDS: tick or L2/MBO raw for ES, RTY, YM, CL, GC, ZN, 6E (paid Databento pull, not made) before any direct replay; not justified by this result (cost-free R is ~0).
- NEEDS (optional): a FEES.md line for 6B if 6B should be added (data is on disk).

## Spec for CANDIDATE
None: there is no CANDIDATE. Nothing to hand to the Sim leader from D3CX.
