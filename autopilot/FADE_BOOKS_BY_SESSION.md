# FADE BOOKS BY SESSION (information only; order 1758Z Nov 24, Josh: "have we found any NY AM fade plays? asia fade plays?")

Written 2026-11-24 from results already on disk. No engine runs, no queue rows, no gate or rule change. Sections are saved in this order: ASIA (first, Josh needs it before 23:00Z), then NY AM, London, NY PM.

How triggers are classified (from the trigger DEFINITION in code/th_grid, not from the result; the classifier script is mine and rests on module + variant names):
- WITH THE MOVE: break*, walk*, follow*, cross, momentum, trend, zone_break, mom, brk, nr (narrow-range breakout), bos, round_break, with_X / confirm (other market agrees).
- FADE: false_break, reject, fade*, revert, cross_zone, divergence fade (div_fade), against_X (trade opposite to ANOTHER market's move; NOT a fade of NQ's own price: xm_base.make_own: 'against' = opposite sign of the other market's z-move), diverge, round_reject, structure_breakout.fail.
- PULLBACK / RETEST: retest, pullback, pullback_ema/st/brick, structure_fvg retest.
- OTHER / UNCLASSIFIED: oscillator families (libosc), candle patterns (threebar, engulf, pin), inside/outside bar, choch, confluence_user, limit-order sdx entries (lim_mid, lim_prox), live D7 clones (K7/P7 etc.), flip-after-run. Marked unclassified on purpose.

Two caveats that apply to every table: (1) the "pool" is the book list that passed gates a+b+c+d on the all-new (D8, _CANC) base in W-COMBO's own-checks reading; (2) numbers for books outside the pool come from the older step-2 / aln_state results and are on slightly different bases (named per row).

---

# 1. ASIA

## 1.1 Pool of 87 by trigger style (ALL_NEW_STACK_ASIA.md, pool hash 0d89b81689, unchanged since 06:08Z)

| style | count | book ids |
|---|---|---|
| with-the-move (breakout / momentum / trend / flow-follow) | 79 | L0569b2b6, L130cb48e, L1343f8bd.BRP45, L1525fc29.BRP45, L15f14deb, L1f5315f5.BRF40_80, L294c4530.BRP45, L29b1bc3f, L2aa4f77d.BRP45, L2b152d25.BRP30, L2fbba524.BRP30, L32bc5db3.BRP60, L36523944, L385f4f2e, L385f4f2e.J502, L3a2258bd, L3faac8df, L40bde9ea, L459016c0.BRP30, L47a9c81c, L4aaacdb2.BRP30, L4cdac967.BRP45, L5026acdc.BRF30_90, L5483cb3c.BRP45, L548972b6.BRF40_80, L552f6547.BRF30_90, L578701ed, L578701ed.BRF30_90, L5c493ea5.BRP60, L5dee2059, L64313ba5.BRP30, L65a26c02, L6b373671.BRP60, L6f51709c.BRP45, L7669e599.BRP45, L79fb26c4.BRP45, L7c8c909c.BRP45, L7ea48296, L7ea48296.BRP45, L7f41b347, L82f920bb.BRP30, L92a90948, L973b5c8a, L98c7ae1d.BRF40_80, L9c2622b0.BRP45, L9e3c5607.BRP45, L9e4754b9, L9f09df59.BRF60_120, La010c3eb, La34ff0e1.BRF40_80, La37b0d38.BRP45, La4dd3ce9.BRP45, La776664b, Lac4916e6.BRF40_80, Lb0e6dfa3.BRF40_80, Lb328c0d1.BRP45, Lb3f85ddc.BRF40_80, Lb68a132d, Lbfca747b.BRP45, Lc11f2bcc.BRF30_90, Lc754cf58, Lcbc8a7ec, Lcd4aa7cd.BRP30, Ld3a03a68.BRF30_90, Ld60fb3e3.BRF40_80, Ld8421129.BRP30, Lec335094, Lecb20c2d, Led34741b.BRF80_40, Lf43211b5, Lf99bcea8, Lff52ec0c, M43f2f949, M7ea48296, M817db5df, M86781ac0, Ma010c3eb, Mcae177ba, Mf5f0441a |
| FADE | **1** | **L018fb0c0** (vsess_30 bar, trig_xmarket_rates against_ZB: trade NQ opposite to the 30-year bond's 1-minute move) |
| pullback / retest | 4 | L1edb9fab (pullback_ema depth), L7c368a4f (pullback_ema depth), L36f1a14e.BRF30_90 (fib5 pullback), Le207b901.BRF30_90 (pivot-floor retest) |
| other / unclassified | 3 | L1756b913 (three-bar pattern), M7423c0d9 (inside bar), L9aa7805c (live D7 K7 clone) |

Total 87. So Josh's reading is right: of the 87, 79 trade with the move, and the single fade is a cross-market one (against the bond), not a fade of NQ's own price (no false-break, re-entry, divergence or mean-reversion book is in the pool). The four books of the Asia final (J502 RSI momentum, Lb0e6dfa3 narrow-range breakout, and the stay-power picks) are all with-the-move.

## 1.2 BEST ASIA FADES (two views: the one in the pool, and the strongest outside it)

| | L018fb0c0 (IN the pool of 87) | L11152f7a (NOT in the pool) | L6ab791e1 (NOT in the pool) |
|---|---|---|---|
| bar | vsess_30 (accumulating bar; D8 number = _CANC base) | vol_350 (volume bar, accumulating) | mrenko_10 (median Renko) |
| trigger | xmarket_rates.against_ZB, w=1 min, thr=1.0 (NQ opposite to ZB move) | levels_vwap.reject (tol 1.0, body close): touch-and-reject at VWAP | levels_profile_va.reject_native (tol 1.0): touch-and-reject at the value-area edge |
| bracket | own S15U (stop-only family: S15U); best tested A20U10U | own bracket (not re-read) | own bracket at step 2 |
| bare L6M / L3M $/wk | 617 / 1,606 (A20U10U would be 941 / 2,753) | 1,520 / 2,317 | 1,562 / 1,647 |
| L6M ulcer / max DD / worst wk | 6,610 / -15,162 / -4,854 | not stored in the state read | not stored in the state read |
| trades L6M | 214 | n/a | n/a |
| prior years $/wk 2023 / 24 / 25 | 86 / 510 / 184 | 378 / 248 / 671 | 335 / 94 / 331 |
| persistence | >= 0.58 (passed the pool gate; fixed walk-forward 0.634; rolling 0.54) | 0.63 | 0.62 |
| luck controls (30 date-shift sets, bare) | 27 of 30 (pool gate); after the fit 7 of 30 | 27 of 30 | 1 of 30 |
| status | IN POOL (a+b+c+d pass); fails gate e (not GREEN vs bare D7 in every prior year; 2023 and 2024 RED); fit NOT KEPT (rolling WF 0.54 < 0.58, RED year); bracket refit to A20U10U NOT KEPT (WF 0.529 over 70 periods, prior-year RED); exit tests (flow_v25, flowp_v15_t2, v25_t2, bricks3_v25) all not kept | passes a, b, c and d on the OLD split; out of the pool because the volume bar is "accumulating": BREAKS on _CANR, number is old-split, not D8 (needs a _CANC re-test; first-look reject list shows 712 such rejects) | fails gate d only: 1 of 30 luck controls (needs >= 27), a margin of 26 |
| where it lives | autopilot/BARE_VS_WRAPPER.md; BRACKET_SHAPES_ASIA.md line 18/204/1870; ASIA_STAGE1_FIT.md line 35; ASIA_JOINT_TABLE.md lines 35, 101-102, 265-269; EXIT_WF.md; BRACKET_REFIT_SERIES.md | /mnt/l2/l2vast/_combo/aln_state.json (TL3_ALN_AS_L11152f7a_BASE); ALL_NEW_STACK_ASIA_OLDSPLIT.md (pool of 31, stack step 3) | aln_state.json (TL3_ALN_AS_L6ab791e1_BASE); ASIA_BOOK_STYLES.md section 3b (twin of a counter-trend candidate list) |

Reading: the best gate-passing Asia fade is L018fb0c0, and it is weak: $617/wk over a 6,610 ulcer (0.09 $/wk per unit of ulcer; the J502 final earns about 4.6 per unit). Its trigger is against-another-market (bonds), not a price fade.

Strongest Asia fades by return that did NOT pass (truly bare R0 step-2 results, ASIA_BOOK_STYLES.md section 3b, all failed the prior-year check (b)/(c), L6M / L3M $/wk, ulcer, persistence): Le001fe42 trendline reject_native on mrenko_20: 2,487 / 2,950, ulcer 1,979, persistence 0.66; L1acc170a levels_vwap false_break on kagi_20 (twin L45c6baf5): 2,113 / 1,439, ulcer 2,279, 0.60; L302f2cbb fib60 reject_native on time_m_60: 1,971 / 1,515, ulcer 2,215, 0.59; L051dcad5 piv_wf false_break_native on pnf_14: 1,832 / 1,502, ulcer 2,128, 0.57; L1716c153 book_micro fade on time_m_13: 1,875 / 1,622, ulcer 2,952, 0.56; Lce256a20 xmarket_es revert on dchg_14 (cross-market fade): 2,721 / 1,527, ulcer 4,408, failed luck controls (lost 8 of 30). Their daily correlation with the Asia 5-book stack ranges 0.12 to 0.57 and the sign on the stack's 20 worst days is mixed (five make money: Le001fe42 +$8.3k, L051dcad5 +$7.8k, Le3823c3e +$2.5k, L1716c153 +$7.8k, L6ab791e1 +$8.2k). Numbers are in-sample, bare, 1 lot, and none is a verified diversifier. Exact gate failed: the prior-year check (some prior year negative, or persistence under 0.58); the per-year margin is in firstlook / step2b state (`/mnt/l2/l2vast/_brkt/step2b_state.json`) and was not re-pulled for this page.

Other Asia fades that pass a, b and c on the all-new base but are short on luck controls (aln_state.json): L766edc63 (tape_stoprun fade_native, time_s_5): L6M 1,066, L3M 568, 2023/24/25 221/238/451, persistence 0.60, controls 19 of 30 (fails d by 8); L1760608b (tape_delta fade, tm30): 1,043 / 1,718, 250/1,059/57, 0.58, controls 6 of 30 (fails d by 21).

## 1.3 Add rounds that tried a fade on the Asia stack

- Current rounds (own, stay-power, recent, L3-gate, weighted; pool 87): L018fb0c0 was in the pool of every loop, so every loop could have picked it; none did. The loops stop at J502 alone because every second book fails the return-per-ulcer clause (plus 1%): J502 earns about 4.6 per unit of ulcer, the 15 landed two-book candidates 0.83-1.59. No page lists L018fb0c0 as a chosen add, a swap, or a top-5 second book. No stack with and without a fade has been run on the current Asia final stack STKd8da2eb47b or on J502 alone. Josh's order 1759Z (try the best Asia fades at sizes 0.25 / 0.5 / 1 against STKd8da2eb47b and J502) asks for exactly this and has NOT been run by this page.
- One OLD round did include fades (superseded 11-20, selection by lowest ulcer on an unfitted base, since replaced; autopilot/ALL_NEW_STACK_ASIA_FAILED_STACK_0346Z.md): step 3 stack (Ld3302219 + Lb328c0d1 + L1756b913) L6M ulcer 4,758 / max DD -13,888 / $6,484 per wk; step 4 added L1716c153 (book_micro fade, flow fade): ulcer 5,419 / max DD -16,433 / $7,828 per wk (with the fade: ulcer +661, max DD -2,545 worse, +$1,344 per wk). Step 5 swapped Lb328c0d1 for L191904b3 (levels_vwap reject, a fade): ulcer 5,595, max DD -23,078, worst wk -3,639, $9,586 per wk. That stack was RED in every prior year, persistence 0.44, and both fades failed their luck controls (L1716c153 1 of 30, L191904b3 11 of 30). Daily correlation with the stack was not computed in that round.
- Daily correlation of L018fb0c0 with the current stack: not computed anywhere that I found.

## 1.4 Fade cells through the Asia screen

- First look + step 2 (W-BRKT, truly bare, 17 shapes; ASIA_BOOK_STYLES.md section 4 counts, its own classification): counter-trend (reversal-fade, false-break, flow-fade, cross-market fade) 389 first-look cells (12.7% of 3,058), 269 books at step 2, 173 positive in L6M and L3M at some shape, 126 failed prior years, 33 stopped by luck controls, 14 twins, **0 passed**. Same funnel for continuation: 2,303 cells, 1,559 at step 2, 1,058 positive, 52 passed. Pullback-with-trend: 311 cells, 211 at step 2, 2 passed.
- My own classification of the same 3,058 first-look cells (this page's rule): with-the-move 2,221, FADE 348 (288 distinct books), pullback 311, other 161, live clones 17. 348 of 3,058 is 11.4% of the screen.
- All-new-base gates (a+b+c+d), subset of 1,002 Asia books with state on disk in aln_state.json: with-the-move 726 books, a 510, a+b 349, a+b+c 275, d >= 27 of 30: 29 of 274 run; FADE 104 books, a 78, a+b 38, a+b+c 23, d >= 27: 1 of 23 run (L11152f7a); pullback 117 books, 87/46/31, d 4 of 31; other 49 books, 42/20/16, d 1 of 16. Whole Asia universe (all styles): 1,525 with all 42 months landed, (a) 1,198, (b) 936, (c) 917, (d) 92 of 618 with all 30 controls landed, a+b+c+d = 87.
- Result: fades were searched at about the same width as the others (11-13% of cells and books) and pass the first screens at a similar rate (a: 75% vs 70%), but die at prior years and luck controls (1 of 23 vs 29 of 274 at control stage, small numbers; and 0 of 269 vs 52 of 1,559 in W-BRKT step 2).

---

# 2. NY AM (pool 39, ALL_NEW_STACK_NYAM.md, pool hash 72a34d3135)

## 2.1 Pool by style

| style | count | book ids |
|---|---|---|
| with-the-move | 22 | B3987e3da.BRF60_120, B57507767, B7bfd33b7, Bde046d66.BRF90_30, Be65f7dfd.BRP60, Bf428c4a1.BRS8U, L20d2d063.BRF60_120, L30250fb1.BRF30_90, L39287638.BRF80_40, L4407508c.BRF120_60, L488784d8, L57507767, L5f66d4c6.BRF80_40, L64390867.BRF80_40, L6df41b86, L7693034b.BRF30_90, L7cc56d99, L8816c2ae, L8cfda948.BRF90_30, L9dbacdbe.BRF80_40, Le0da99e2, Lf0346d55.BRP60 |
| FADE | **7** | B15d193ef.BRA15U30U (gaps false_break), B6f77f23d (levels_opens false_break_native), Bace079e3.BRS8U (fibr_on false_break), L43f0cbfb.BRS8U (fibr_on false_break), L9acce162.BRF120_60 (piv_floor false_break), Le4fede95.BRF90_30 (profile_nodes false_break), Lbb254083.BRP45 (renko_80, xmarket_fx against_6J: against another market) |
| pullback / retest | 5 | L05350e98, L6c6a79f5.BRA15U30U, L870542d8.BRF60_120, L8f11883e.BRF30_90, Lbb6282e1.BRF80_40 |
| other / unclassified | 5 | B32cec996 and L32cec996 (choch swing, same book), L6d0d3174.BRF60_120 (aroon), Lee0bf761.BRF40_80 (outside bar), L6547965c (trigger not found in the first-look cell lists: unclassified) |

So NY AM already has fades in its pool (7 of 39) and in its finals: six of the seven are false-break fades of a price level; one is against-another-market (6J).

## 2.2 Best NY AM fades (in the pool)

| | L43f0cbfb.BRS8U | Le4fede95.BRF90_30 | Lbb254083.BRP45 |
|---|---|---|---|
| bar | pnf_14 (point-and-figure) | swing_atr_0.4 (swing-leg bar) | renko_80 |
| trigger | levels_fibr_on false_break (M 3, k 0.5): false break of the overnight-range Fibonacci lines, both sides | levels_profile_nodes false_break_native (M 2, k 0.5): false break of previous-day volume-profile HVN/LVN lines, both sides | xmarket_fx against_6J (w 15, thr 1.5): NQ opposite to the yen's move, both sides |
| bracket | S8U unit rule (events 120/120 pts) | fixed 90/30 | fixed 45/45 (P45) |
| bare L6M / L3M $/wk | 3,886 / 3,186 (book alone, truly bare R0 set TL3_ALN_NY_L43f0cbfb_R0BRS8U) | alone number not stored on the pages (stack step 4 only); base-wrapper numbers 586 / 1,296 (aln_state) | alone number not stored (stack step 4 only); base-wrapper L6M -3 / L3M 578 |
| L6M ulcer / max DD / worst wk | 6,115 / -18,885 / -6,143 (L3M ulcer 4,790, maxDD -9,846) | see stack row | see stack row |
| prior years $/wk 2023 / 24 / 25 | 1,022 / 522 / 1,233 (ulcers 7,710 / 10,312 / 10,500; worst maxDD -32,990) | 841 / 550 / 1,368 (base wrapper) | 414 / 147 / 585 (base wrapper) |
| persistence | 0.61 | 0.59 (base) | 0.57 (base); 0.71 as step 4 of the stack |
| luck controls | pool gate passed (>= 27 of 30); weighted-final stack beats (30, 25, 30) | pool gate passed; 3 of 30 / 23 ulcer-only on the base wrapper | pool gate passed; equal-final stack beats (30, 26, 30) |
| where | ALL_NEW_STACK_NYAM_W_NY_OWN_W.md step 1; D8_BUILD_SPEC.md line 475 (book L43f0cbfb) | D8_BUILD_SPEC.md line 400; D8_PARITY_Le4fede95_*.md | D8_BUILD_SPEC.md line 547; ALL_NEW_STACK_NYAM.md step 4 |

Best fade by raw return per ulcer among the pool fades with a stored bare number: L43f0cbfb (0.64 $/wk per unit of ulcer) ahead of B6f77f23d (levels_opens false break on tm45, bracket A15U30U: L6M 1,393 / L3M 1,214, ulcer 5,356, max DD -12,737, worst wk -6,864, years 619 / 941 / 1,271, persistence 0.65, controls 30 of 30, 0.26 per unit). All gate (e) fail (not GREEN vs bare D7 in every prior year) like the rest of the pool; none of the 39 passes (e).

## 2.3 Add rounds with a fade (they happened, because fades are in the pool and in the finals)

- Equal-weight own-checks round (ALL_NEW_STACK_NYAM.md; final L8cfda948 + Lf0346d55 + L7cc56d99 + Lbb254083 + L8f11883e): step 3 (3 with-the-move books) L6M ulcer 3,851 / max DD -13,416 / worst wk -3,935 / $6,470 per wk; step 4 adds the fade Lbb254083.BRP45 (against 6J): ulcer 3,501 / max DD -12,521 / worst wk -3,040 / $7,181 per wk. L3M: ulcer 3,665 -> 3,363, $5,248 -> $5,587. Prior years $/wk 1,686 / 1,141 / 2,134 -> 1,900 / 1,632 / 2,588 (2025 worst maxDD -49,270 -> -46,153). With the fade, ulcer -9%, max DD -7%, $/wk +11%; passes the add rule. Stack persistence 0.63 -> 0.71. Daily correlation with the stack: not computed.
- Weighted own-checks round (W_NY_OWN_W; final L43f0cbfb x1 + B7bfd33b7 + Bf428c4a1.BRS8U + Le4fede95 + Lf0346d55 x0.5 + L8cfda948 + L4407508c x0.25 + L39287638 x0.25 + L64390867 x0.5): starts with the fade L43f0cbfb; step 3 (L43f0cbfb + B7bfd33b7 + Bf428c4a1) ulcer 4,858 / max DD -15,603 / $7,047 per wk; step 4 adds the fade Le4fede95: ulcer 6,018 / max DD -20,933 / $9,769 per wk (return per ulcer 1.45 -> 1.62, max DD 34% deeper before scaling). 2 of the 9 books are fades.
- Live-state note: D8_BUILD_SPEC.md line 307 lists the NY AM provisional pick as Le4fede95.BRF90_30 + B7bfd33b7 (a fade plus a with-the-move book).

## 2.4 NY AM fade cells through the screen

- First-look cells (5,946, this page's classification): with-the-move 4,024, FADE 1,018 (17.1%; 1,017 distinct books), pullback 659, other 236, live clones 9. Pool of 39: 7 fades (18% of the pool), so fades pass into the pool at the same rate as their share of the cells (17.1% in, 17.9% out); with-the-move 22 of 4,024 cells, 0.5% vs fade 7 of 1,018, 0.7%.
- Subset check (251 NY AM books with state in aln_state.json; old and partial): fade 57 books, a 31, a+b 28, a+b+c 17, controls decided for 17 and only 2 reach >= 27 of 30; with-the-move 159 books, 98 / 88 / 73, 2 of 73. Whole NY AM universe (status 11-24): 1,786 books with a base set, pool 39, 702 failed, 252 waiting on prior years.

---

# 3. LONDON (pool 4, ALL_NEW_STACK_LONDON.md, pool hash 48d36970a8; London first looks still being filled: 36% of the family-bests had been covered at the 11-24 morning step 0)

## 3.1 Pool by style

| style | count | book ids |
|---|---|---|
| with-the-move | 2 | L12842dde.BRP45 (book_imb follow_native on rng_20), L74274eca.BRF120_60 (xmarket_rates with_ZB on vsess_200) |
| FADE | **2** | L19201dfc.BRF90_30 (trend_20 bar) and Lc78f2492.BRF90_30 (renko_20 bar): both xmarket_commod against_CL (NQ against crude oil's move, w 15, thr 2.0) |
| pullback / retest | 0 | |
| other | 0 | |

## 3.2 Best London fade = the London OWN final

L19201dfc.BRF90_30: bar trend_20; trigger xmarket_commod against_CL, w 15 min, thr 2.0 (against another market, not a price fade); bracket F90_30 (stop 90 / target 30), both sides; bare (truly bare R0 set TL3_ALN_LO_L19201dfc_R0BRF90_30): L6M $1,768/wk, L3M $1,643/wk; L6M ulcer 1,273 / max DD -3,809 / worst wk -2,673; L3M ulcer 1,406 / maxDD -3,402; prior years 2023 / 24 / 25 = $273 / 251 / 183 per wk (year ulcers 1,913 / 4,372 / 5,080, max DD -5,238 / -11,780 / -12,803); persistence 0.62; luck controls beaten (L6M drawdown-first / L3M / ulcer-only) 29 / 21 / 30 (passes >= 27 on L6M); fails gate (e) only. Return per ulcer 1.39 (the staying-power London final L74274eca is 0.30, ulcer 5,193, $1,584). The twin trigger on the renko_20 bar (Lc78f2492) is in the pool too (numbers on the London pool page). This is both the best fade and the London final.

## 3.3 Add rounds

The London loops (own, stay, weighted) start from the fade L19201dfc and STOP at one book: no candidate passes the add rule. So a with-the-move book was tried as an add to a fade, not the other way round. No fade was added to a with-the-move stack in London (the stay-power final is the with-the-move L74274eca alone). Daily correlation: not computed.

## 3.4 London fade cells through the screen

First-look cells 808: with-the-move 423, FADE 232 (28.7%, 232 distinct books), pullback 58, other 94, live clone 1. Pool 4 of which 2 fades (50%): fades are over-represented in the London pool (2 of 232 vs 2 of 423 with-the-move; 0 of 58 pullback). Small numbers; London first looks only partly covered (36%).

---

# 4. NY PM (gate page pool 8, ALL_NEW_STACK_NYPM.md; loops ran with 6 to 7 of them; finals_ready_nypm.json updated 16:14Z; pool_hash 94f7f244b6)

## 4.1 Pool by style (the 8 that pass a+b+c+d)

| style | count | book ids |
|---|---|---|
| with-the-move | 4 | L4bdd521a.BRF80_40 (xmarket_ym follow, tm1800), L8e0bf58c.BRS8U (xmarket_rates with_ZN), L5d947160.BRP45 (levels_vwap break_native), L6d238076.BRF90_30 (manual_macd sigcross) |
| FADE | **3** | L2c6916a5.BRP60 (tm15 tape_div div_fade: divergence fade), L7b1adff3.BRP60 (time_s_15 tape_div div_fade), L52359bf4.BRP30 (tm120 bands_atrchan fade_ext: re-entry/fade at the ATR channel extreme) |
| pullback | 0 | |
| other | 1 | L8dff280f.BRP90 (confluence_user u3a: unclassified) |

## 4.2 Best NY PM fade

L7b1adff3.BRP60 (time_s_15 bar, tape_div div_fade N 20 k 0.5, plain stop 60 / target 60, truly bare R0 BRP60), alone: L6M $1,304/wk, L3M $1,263; L6M ulcer 2,893 / max DD -9,413 / worst wk -3,114; L3M ulcer 2,341; prior years $190 / 393 / 35 per wk (year ulcers 8,396 / 6,517 / 8,255; max DD -17,660 / -18,033 / -16,870); persistence 0.61. Its sibling L2c6916a5.BRP60 (same trigger on tm15) replaced it in the weighted final (swap step 3: ulcer 2,941 -> 2,632, max DD -9,382 -> -7,536, $/wk 2,157 -> 2,086; persistence 0.65 -> 0.66; alone numbers of L2c6916a5 not stored on the pages). Luck controls: all 8 pool books passed >= 27 of 30 (gate d, 8 of 8); the stack control counts are not yet posted (controls null on the 16:14Z final). Gate (e): only 1 of 8 passes.

## 4.3 Add rounds

The weighted NY PM round (own-w; final L2c6916a5.BRP60 + L4bdd521a.BRF80_40, tentative): step 1 the fade L7b1adff3 alone (ulcer 2,893, $1,304); step 2 adds the with-the-move L4bdd521a (xmarket_ym follow): ulcer 2,941, max DD -9,382, worst wk -3,114 -> -1,285, $1,304 -> 2,157 per wk; prior years $/wk 190/393/35 -> 816/616/1,142. So here the with-the-move book was added to the fade (the fade is the base). The equal-weight round (ALL_NEW_STACK_NYPM.md) started with the with-the-move L6d238076 (L6M $1,425/wk, ulcer 1,892) and added L8dff280f (unclassified); no fade was added there. Daily correlations: not computed.

## 4.4 NY PM fade cells through the screen

First-look cells 396: with-the-move 190, FADE 144 (36.4%, 144 distinct books), pullback 16, other 45, live clone 1. Pool 8 of 396 cells; 3 of the 8 are fades (fade 3 of 144 cells = 2.1% vs with-the-move 4 of 190 = 2.1%). NY PM first looks covered only 34% of family-bests at the 11-24 morning step 0 (782 missing cells being added), so the NY PM and London counts will move.

---

# 5. ONE-LINE ANSWER PER SESSION

| session | pool by style: with / FADE / pullback / other | best fade | in the final? |
|---|---|---|---|
| Asia | 79 / 1 / 4 / 3 (of 87) | L018fb0c0 (against_ZB, vsess_30, S15U): $617 / $1,606 per wk L6M / L3M, ulcer 6,610: weak; not kept after fit; gate (e) fail | no (final = 4 with-the-move books) |
| NY AM | 22 / 7 / 5 / 5 (of 39) | L43f0cbfb.BRS8U (fib false break): $3,886 / $3,186, ulcer 6,115; Le4fede95 (profile-node false break) and Lbb254083 (against 6J) in finals | yes (Lbb254083 in the equal final; L43f0cbfb and Le4fede95 in the weighted final) |
| London | 2 / 2 / 0 / 0 (of 4) | L19201dfc.BRF90_30 (against_CL): $1,768 / $1,643, ulcer 1,273 | yes, it IS the own final |
| NY PM | 4 / 3 / 0 / 1 (of 8) | L7b1adff3.BRP60 (div_fade): $1,304 / $1,263, ulcer 2,893; L2c6916a5 same trigger | yes (L2c6916a5 in the weighted final) |

Open items I did not do (information-only order): no daily correlation of any fade with the current stacks was computed; no with / without run of an Asia fade on STKd8da2eb47b (order 1759Z asks for it); the alone numbers of Le4fede95, Lbb254083 (NY AM) and L2c6916a5 (NY PM) were not on any page and would need an engine pull.
