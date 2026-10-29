# DS3 SIZING RECENT - lots re-fitted on the trailing 3 / 6 months, walk-forward monthly, vs the fixed table (D3SZR, T-L2-ENTRY section C)

Research only; no live change; UNTOUCHED never read (every label day <= 2026-02-06; own masks, vs_lib/s48score HOLD/WF/L8W NOT used, see DS3_MASKAUDIT). Prereg `l2vast/ds3/prereg/SZR_prereg.md` sha256 dbbfe08674183752182ff09fa83f5a53cbb428d033357dfcca8a3573cae8fc50 (cell count F = 12: 2 layers x 6 variants; best-of-12 White RC), PREHOLD `autopilot/DS3_SIZING_RECENT_PREHOLD.md` sha256 ecf7f1bdbb09075d5860ad7ab69d2d1a9f10cd881248b533536f0e4838164e3a; one holdout look per group (SZR_D6, SZR_F). Code `l2vast/ds3/code/szr/`. MEASURED basis: exact per-book 1-s lock engine, per-row lot multiplier by (book x ENTRY session), 50-contract cap, sweep cost, $4.84 RT; weekly $ at the 10-lot-scale stack.

## ONE-LINE VERDICTS

**D6 session table (live DS3 stack, exact lock engine)**
- V5 SH6: **DEAD**; L6M -4,252/wk (CI -29,284..+21,565, MDE 37,077), HOLD +1,204 (MDE 33,546), 2026 (~5 real weeks, 6 label-week buckets) -5,242 (MDE 47,153); L6M maxDD 330,875 vs fixed 466,422; failed gates: D1 PRE mean, D3 X' mean, D4 maxDD, D5 worst-20, D7 placebo, D8 RC.
- V4 W6_KELLY: **DEAD**; L6M -11,414/wk (CI -39,972..+20,314, MDE 44,433), HOLD -6,213 (MDE 40,300), 2026 (~5 real weeks, 6 label-week buckets) +25,228 (MDE 81,213); L6M maxDD 362,772 vs fixed 466,422; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D7 placebo, D8 RC.
- V6 SEL: **DEAD**; L6M -19,415/wk (CI -53,915..+12,896, MDE 49,469), HOLD -12,866 (MDE 44,385), 2026 (~5 real weeks, 6 label-week buckets) -54,118 (MDE 73,476); L6M maxDD 558,324 vs fixed 466,422; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D7 placebo, D8 RC.
- V2 W6_MEAN: **DEAD**; L6M -23,055/wk (CI -59,765..+10,495, MDE 52,278), HOLD -16,051 (MDE 46,891), 2026 (~5 real weeks, 6 label-week buckets) -54,118 (MDE 73,476); L6M maxDD 558,324 vs fixed 466,422; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V1 W3_MEAN: **DEAD**; L6M -31,417/wk (CI -69,464..+10,231, MDE 59,493), HOLD -25,497 (MDE 52,974), 2026 (~5 real weeks, 6 label-week buckets) -77,306 (MDE 111,170); L6M maxDD 512,117 vs fixed 466,422; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V3 W3_KELLY: **DEAD**; L6M -37,844/wk (CI -71,043..-4,687, MDE 48,449), HOLD -29,779 (MDE 43,876), 2026 (~5 real weeks, 6 label-week buckets) -38,073 (MDE 120,544); L6M maxDD 411,353 vs fixed 466,422; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D7 placebo, D8 RC.

**T-STACK F layer (A06 x B02 in-engine; HM5R excluded)**
- V5 SH6: **DEAD**; L6M -14,349/wk (CI -39,082..+9,532, MDE 36,034), HOLD -9,512 (MDE 32,377), 2026 (~5 real weeks, 6 label-week buckets) +12,041 (MDE 79,303); L6M maxDD 327,718 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D7 placebo, D8 RC.
- V4 W6_KELLY: **DEAD**; L6M -17,771/wk (CI -44,187..+9,797, MDE 40,660), HOLD -13,456 (MDE 37,119), 2026 (~5 real weeks, 6 label-week buckets) +24,215 (MDE 92,450); L6M maxDD 311,056 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V2 W6_MEAN: **DEAD**; L6M -19,257/wk (CI -50,738..+12,901, MDE 46,613), HOLD -11,704 (MDE 42,550), 2026 (~5 real weeks, 6 label-week buckets) -33,185 (MDE 112,216); L6M maxDD 405,707 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V6 SEL: **DEAD**; L6M -20,602/wk (CI -51,493..+10,809, MDE 46,053), HOLD -12,881 (MDE 42,137), 2026 (~5 real weeks, 6 label-week buckets) -39,460 (MDE 104,706); L6M maxDD 405,707 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V1 W3_MEAN: **DEAD**; L6M -22,536/wk (CI -55,786..+11,164, MDE 49,906), HOLD -16,196 (MDE 44,854), 2026 (~5 real weeks, 6 label-week buckets) -32,971 (MDE 101,408); L6M maxDD 423,023 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC.
- V3 W3_KELLY: **DEAD**; L6M -38,193/wk (CI -68,831..-7,863, MDE 43,518), HOLD -32,996 (MDE 39,167), 2026 (~5 real weeks, 6 label-week buckets) -23,335 (MDE 115,896); L6M maxDD 456,318 vs fixed 384,390; failed gates: D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC.

**Plain answer.** Does a walk-forward re-fit beat the fixed table >= 0 in the last 6 months on measured fills with the stack tail not worse? NO. Every one of the 12 walk-forward variants is below the fixed table in the last 6 months (L6M delta range D6 -37,844..-4,252, F -38,193..-14,349 $/wk), (several have a lower L6M maxDD, but every one fails the PRE+HOLD tail/SD gates or the mean gates; see gates table). Fixed table stays.

CANDIDATE-RECENT (delta >= 0 in 2026 AND last 6 months; not a V2 tier, gates unchanged): none. 2026 alone is ~5 weeks (MDE 47k..120k $/wk on every line), so a positive 2026 delta carries no weight by itself (D6 V4 and F V4 are the only positive 2026 deltas: +25k / +24k against MDE 81k / 92k, and both are negative in L6M, HOLD, PRE and X').
**Placebo reading.** A random re-allocation of the same lots across cells (same turnover) itself loses -22,219..-15,245 $/wk in L6M vs the fixed table (placebo means: moving to 0 / 2x lots costs diversification, sweep cost above 14 lots and lock nonlinearity). The real chains sit near that null (L6M ranks 0.02..0.88; only D6 V4/V5 reach 0.83-0.88, F V5 0.70), so the information in the trailing fit is worth at most about +10k $/wk over a random shuffle, which does not pay for the loss from leaving the fixed table. CLOSE has no stack entries (15:00-15:15), so its delta is 0 by construction.
Best-of-12 White RC on PRE+HOLD weekly deltas: max t -0.68, p 0.97 (MDE-scale: no variant is distinguishable from zero).
Structural check (chasing recent winners): across the 28 (book x session) cells with enough trades, the correlation of PRE mean weekly $ with HOLD mean weekly $ is Pearson +0.54 / Spearman +0.47 (PRE vs last-6M: +0.61 / +0.56; X' vs PRE over 23 cells: -0.37 / -0.42). PRE-vs-HOLD persistence is POSITIVE here, so the prereg prediction (negative or ~0 correlation) is NOT confirmed for PRE->HOLD; it is negative only for X' vs PRE. The loss vs fixed therefore does not come from reversal of cell ranks between PRE and HOLD; it comes from fit noise (13-26 weeks, 36 cells, LP/Kelly corners at 0 and 2x) and from the cost of concentration - see the placebo.

## RUN-THIS-TONIGHT (one page)

**Recommendation: keep the FIXED table** (every cell = its fixed lots) - no walk-forward variant clears the gates; the re-fit tables below are printed because the order asked for them, they are NOT a tier upgrade and nothing here changes live. Fit as of 2026-02-07 (all weeks to 2026-02-06 closed), integer lots = round(nominal lots x multiplier), cap 2x, floor 0, bold = differs from fixed. KB/SM/PB lots are further multiplied by their live vol weight W_k(t). Sessions by ET entry time: ASIA rest of day, LONDON 02:00-08:30, PRE 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00, CLOSE 15:00-15:15. Cells with < 8 trades in the fit window keep their fixed lots. ST=S6 is disabled in D6, WT=W6 / MA=MA6 / CR=C6 per the user's tags (MA and CR are not in this engine; PB/KB/SM tags K6/P6/U6 are the ABR bundle tags).

### D6 session table (live DS3 stack, exact lock engine) - best by L6M: V5 SH6 (DEAD); last re-fit
| book (D6 tag) | fixed lots | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|---|
| ST (S6) | 10 | **6** | **9** | **0** | **20** | **5** | 10 |
| HM (H6) | 10 | **16** | **0** | **0** | **0** | **0** | 10 |
| WT (W6) | 7 | **12** | **0** | **6** | **10** | **0** | 7 |
| KB (K6) | 10 | **13** | **16** | **0** | **8** | **6** | 10 |
| SM (U6) | 10 | **9** | **4** | **0** | **0** | **2** | 10 |
| PB (P6) | 10 | **16** | **20** | **0** | **7** | **0** | 10 |

Selector (V6) tonight picks **V2 W6_MEAN** (trailing-3-month out-of-sample linear P&L of the previous tables: V1 +451,412, V2 +766,013, V3 +552,952, V4 +693,036):
| book (D6 tag) | fixed lots | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|---|
| ST (S6) | 10 | **20** | **20** | **0** | **20** | **0** | 10 |
| HM (H6) | 10 | **20** | **0** | **0** | **0** | **0** | 10 |
| WT (W6) | 7 | **14** | **0** | **14** | **14** | **0** | 7 |
| KB (K6) | 10 | **20** | **20** | **0** | **20** | **20** | 10 |
| SM (U6) | 10 | **20** | **20** | **0** | **0** | **20** | 10 |
| PB (P6) | 10 | **20** | **20** | **0** | **20** | **0** | 10 |


### T-STACK F layer (A06 x B02 in-engine; HM5R excluded) - best by L6M: V5 SH6 (DEAD); last re-fit
| book (D6 tag) | fixed lots | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|---|
| ST (S6) | 10 | **6** | **13** | **0** | **20** | **1** | 10 |
| HM (H6) | 10 | **19** | **0** | **0** | **0** | **0** | 10 |
| WT (W6) | 7 | **9** | **0** | 7 | **13** | **0** | 7 |
| KB (K6) | 10 | **9** | **11** | **0** | **14** | **9** | 10 |
| SM (U6) | 10 | 10 | **4** | **0** | **0** | **2** | 10 |
| PB (P6) | 10 | **18** | **20** | **0** | **6** | **0** | 10 |

Selector (V6) tonight picks **V1 W3_MEAN** (trailing-3-month out-of-sample linear P&L of the previous tables: V1 +450,317, V2 +432,989, V3 +302,457, V4 +411,534):
| book (D6 tag) | fixed lots | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE |
|---|---|---|---|---|---|---|---|
| ST (S6) | 10 | **20** | **20** | 10 | **20** | **0** | 10 |
| HM (H6) | 10 | **20** | **0** | 10 | **0** | **0** | 10 |
| WT (W6) | 7 | **14** | **14** | **14** | **14** | **0** | 7 |
| KB (K6) | 10 | **0** | **0** | **0** | **0** | **20** | 10 |
| SM (U6) | 10 | **0** | **20** | 10 | **0** | **20** | 10 |
| PB (P6) | 10 | **20** | **20** | 10 | **20** | **0** | 10 |

Fixed table for reference: ST 10, HM 10, WT 7, KB 10, SM 10, PB 10 in every session (F layer: same lots, further halved by A06 in the book's loose half-hour slots and by B02 after 10:30 on ON_085 days).

Nightly re-fit, single command: `python3 -I l2vast/ds3/code/szr/szr_nightly_refit.py --layer D6 --variant V6` (writes `autopilot/SIZING_TABLE_latest.txt`; data hard-capped at 2026-02-06 until the lead lifts CUT in szr_lib.py).

## TABLES, RECENT FIRST (weekly $ at the 10-lot scale; delta = variant - fixed, paired by week; MDE = 2.8 SD(d)/sqrt(n); W20 = sum of the 20 lowest weeks, n/a when < 20 weeks; "L6M W20" sums the 20 lowest of only 28 weeks so it is not a tail measure there)

### D6 session table (live DS3 stack, exact lock engine)

**2026 (20260101..20260206; ~5 real weeks)** (n weeks = 6)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 46,187 | 146,009 | 276,732 | -185,098 | n/a | - | - | - |
| V5 SH6 | 40,944 | 162,035 | 261,421 | -211,421 | n/a | -5,242 [-37,973, +21,867] | 47,153 | - |
| V4 W6_KELLY | 71,415 | 100,856 | 174,041 | -102,075 | n/a | +25,228 [-24,298, +78,408] | 81,213 | - |
| V6 SEL | -7,932 | 114,326 | 334,355 | -198,279 | n/a | -54,118 [-106,973, -15,189] | 73,476 | - |
| V2 W6_MEAN | -7,932 | 114,326 | 334,355 | -198,279 | n/a | -54,118 [-106,973, -15,189] | 73,476 | - |
| V1 W3_MEAN | -31,119 | 178,905 | 512,117 | -298,351 | n/a | -77,306 [-146,832, -4,724] | 111,170 | - |
| V3 W3_KELLY | 8,114 | 125,042 | 343,042 | -215,247 | n/a | -38,073 [-108,248, +44,607] | 120,544 | - |

**LAST 6 MONTHS (20250801..20260206)** (n weeks = 28)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 65,679 | 123,009 | 466,422 | -204,132 | 204,018 | - | - | - |
| V5 SH6 | 61,427 | 120,676 | 330,875 | -211,421 | 31,940 | -4,252 [-29,284, +21,565] | 37,077 | - |
| V4 W6_KELLY | 54,264 | 97,217 | 362,772 | -102,075 | 167,968 | -11,414 [-39,972, +20,314] | 44,433 | - |
| V6 SEL | 46,264 | 113,738 | 558,324 | -198,279 | -147,666 | -19,415 [-53,915, +12,896] | 49,469 | - |
| V2 W6_MEAN | 42,624 | 116,212 | 558,324 | -198,279 | -204,633 | -23,055 [-59,765, +10,495] | 52,278 | - |
| V1 W3_MEAN | 34,261 | 150,547 | 512,117 | -298,351 | -679,198 | -31,417 [-69,464, +10,231] | 59,493 | - |
| V3 W3_KELLY | 27,835 | 108,692 | 411,353 | -215,247 | -409,579 | -37,844 [-71,043, -4,687] | 48,449 | - |

**HOLD (20250701..20260206)** (n weeks = 32)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 52,448 | 151,891 | 601,016 | -318,557 | -742,938 | - | - | - |
| V5 SH6 | 53,652 | 148,476 | 469,679 | -286,185 | -772,839 | +1,204 [-20,909, +25,142] | 33,546 | - |
| V4 W6_KELLY | 46,235 | 139,673 | 564,525 | -292,804 | -702,985 | -6,213 [-32,778, +22,243] | 40,300 | - |
| V6 SEL | 39,581 | 150,131 | 558,324 | -316,264 | -1,053,992 | -12,866 [-45,149, +16,715] | 44,385 | - |
| V2 W6_MEAN | 36,396 | 151,633 | 558,324 | -316,264 | -1,106,439 | -16,051 [-49,419, +14,748] | 46,891 | - |
| V1 W3_MEAN | 26,951 | 176,702 | 606,544 | -316,263 | -1,577,759 | -25,497 [-61,395, +11,561] | 52,974 | - |
| V3 W3_KELLY | 22,668 | 143,963 | 560,893 | -317,157 | -1,244,241 | -29,779 [-59,971, +1,248] | 43,876 | - |

**PRE (20240201..20250630)** (n weeks = 75)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 44,127 | 131,184 | 477,701 | -306,664 | -2,304,797 | - | - | - |
| V5 SH6 | 24,170 | 128,409 | 698,175 | -282,022 | -2,680,652 | -19,957 [-39,471, -478] | 28,883 | - |
| V4 W6_KELLY | 31,137 | 127,880 | 510,985 | -237,872 | -2,432,486 | -12,990 [-36,244, +8,618] | 32,325 | - |
| V6 SEL | 27,693 | 124,619 | 632,155 | -275,317 | -2,607,914 | -16,435 [-37,706, +4,635] | 30,195 | - |
| V2 W6_MEAN | 42,210 | 131,609 | 461,719 | -275,317 | -2,583,371 | -1,917 [-23,097, +18,881] | 30,314 | - |
| V1 W3_MEAN | 32,261 | 132,350 | 394,930 | -314,473 | -2,760,420 | -11,866 [-35,311, +11,888] | 33,852 | - |
| V3 W3_KELLY | 29,871 | 133,966 | 556,212 | -446,708 | -2,596,545 | -14,256 [-41,108, +12,562] | 38,495 | - |

**X' chain-active (20231002..20240131; the chain starts when the first 6-month window closes)** (n weeks = 18)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 56,758 | 89,903 | 172,823 | -69,453 | n/a | - | - | - |
| V5 SH6 | 49,187 | 85,029 | 204,968 | -200,771 | n/a | -7,571 [-46,012, +31,256] | 57,715 | - |
| V4 W6_KELLY | 52,831 | 88,555 | 180,567 | -97,043 | n/a | -3,927 [-41,917, +32,468] | 55,558 | - |
| V6 SEL | 45,736 | 92,056 | 286,121 | -204,667 | n/a | -11,022 [-52,900, +30,826] | 61,924 | - |
| V2 W6_MEAN | 45,736 | 92,056 | 286,121 | -204,667 | n/a | -11,022 [-52,900, +30,826] | 61,924 | - |
| V1 W3_MEAN | 13,633 | 123,535 | 422,786 | -235,185 | n/a | -43,125 [-96,936, +12,063] | 79,688 | - |
| V3 W3_KELLY | 15,365 | 113,610 | 346,891 | -250,482 | n/a | -41,393 [-81,975, -1,727] | 59,301 | - |

**POOLED chain-active (20231002..20260206) - sanity** (n weeks = 123)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 48,858 | 132,512 | 601,016 | -318,557 | -3,081,067 | - | - | - |
| V5 SH6 | 35,894 | 130,144 | 698,175 | -286,185 | -3,299,738 | -12,964 [-27,875, +2,000] | 21,423 | - |
| V4 W6_KELLY | 38,746 | 127,330 | 564,525 | -292,804 | -2,820,363 | -10,112 [-26,597, +6,001] | 23,536 | - |
| V6 SEL | 33,876 | 128,887 | 632,155 | -316,264 | -3,281,476 | -14,981 [-31,877, +1,379] | 23,464 | - |
| V2 W6_MEAN | 41,900 | 133,270 | 558,324 | -316,264 | -3,338,711 | -6,958 [-23,876, +9,616] | 23,891 | - |
| V1 W3_MEAN | 28,678 | 144,388 | 606,544 | -316,263 | -3,852,171 | -20,180 [-39,142, -1,321] | 27,333 | - |
| V3 W3_KELLY | 26,360 | 134,852 | 560,893 | -446,708 | -3,563,248 | -22,498 [-42,178, -3,459] | 27,483 | - |

### T-STACK F layer (A06 x B02 in-engine; HM5R excluded)

**2026 (20260101..20260206; ~5 real weeks)** (n weeks = 6)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 47,628 | 132,390 | 264,456 | -145,346 | n/a | - | - | - |
| V5 SH6 | 59,669 | 115,240 | 207,121 | -100,045 | n/a | +12,041 [-41,849, +58,395] | 79,303 | - |
| V4 W6_KELLY | 71,843 | 135,195 | 220,064 | -157,903 | n/a | +24,215 [-33,128, +80,951] | 92,450 | - |
| V2 W6_MEAN | 14,443 | 171,242 | 401,631 | -304,703 | n/a | -33,185 [-101,983, +33,855] | 112,216 | - |
| V6 SEL | 8,169 | 172,382 | 401,631 | -304,703 | n/a | -39,460 [-105,726, +22,214] | 104,706 | - |
| V1 W3_MEAN | 14,658 | 168,476 | 345,601 | -250,837 | n/a | -32,971 [-95,969, +33,589] | 101,408 | - |
| V3 W3_KELLY | 24,293 | 144,802 | 361,806 | -235,886 | n/a | -23,335 [-92,860, +55,021] | 115,896 | - |

**LAST 6 MONTHS (20250801..20260206)** (n weeks = 28)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 60,375 | 103,873 | 384,390 | -157,499 | 316,883 | - | - | - |
| V5 SH6 | 46,026 | 100,661 | 327,718 | -137,575 | -23,120 | -14,349 [-39,082, +9,532] | 36,034 | - |
| V4 W6_KELLY | 42,605 | 108,484 | 311,056 | -158,221 | -129,218 | -17,771 [-44,187, +9,797] | 40,660 | - |
| V2 W6_MEAN | 41,118 | 127,501 | 405,707 | -304,703 | -172,544 | -19,257 [-50,738, +12,901] | 46,613 | - |
| V6 SEL | 39,773 | 128,103 | 405,707 | -304,703 | -210,192 | -20,602 [-51,493, +10,809] | 46,053 | - |
| V1 W3_MEAN | 37,839 | 130,688 | 423,023 | -250,837 | -402,781 | -22,536 [-55,786, +11,164] | 49,906 | - |
| V3 W3_KELLY | 22,182 | 102,312 | 456,318 | -235,886 | -465,396 | -38,193 [-68,831, -7,863] | 43,518 | - |

**HOLD (20250701..20260206)** (n weeks = 32)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 49,897 | 137,453 | 562,196 | -309,830 | -555,920 | - | - | - |
| V5 SH6 | 40,385 | 128,130 | 458,236 | -249,468 | -795,386 | -9,512 [-32,270, +12,384] | 32,377 | - |
| V4 W6_KELLY | 36,441 | 149,214 | 592,385 | -294,433 | -997,651 | -13,456 [-38,568, +13,162] | 37,119 | - |
| V2 W6_MEAN | 38,193 | 157,107 | 500,355 | -304,703 | -948,285 | -11,704 [-41,364, +19,417] | 42,550 | - |
| V6 SEL | 37,016 | 157,511 | 500,355 | -304,703 | -985,933 | -12,881 [-42,149, +18,509] | 42,137 | - |
| V1 W3_MEAN | 33,701 | 161,412 | 541,199 | -330,187 | -1,187,075 | -16,196 [-46,695, +15,923] | 44,854 | - |
| V3 W3_KELLY | 16,900 | 134,899 | 538,594 | -327,643 | -1,173,804 | -32,996 [-59,502, -5,138] | 39,167 | - |

**PRE (20240201..20250630)** (n weeks = 75)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 54,246 | 118,533 | 378,094 | -239,655 | -1,673,662 | - | - | - |
| V5 SH6 | 30,972 | 118,847 | 469,063 | -232,879 | -2,266,234 | -23,274 [-41,419, -4,686] | 26,655 | - |
| V4 W6_KELLY | 41,817 | 118,302 | 447,252 | -271,930 | -1,968,083 | -12,429 [-30,494, +6,405] | 27,377 | - |
| V2 W6_MEAN | 43,449 | 129,503 | 332,771 | -235,026 | -2,365,873 | -10,797 [-30,754, +8,684] | 28,700 | - |
| V6 SEL | 44,112 | 137,270 | 511,924 | -238,803 | -2,464,121 | -10,134 [-30,543, +9,687] | 29,729 | - |
| V1 W3_MEAN | 49,412 | 133,696 | 511,924 | -238,803 | -2,401,885 | -4,834 [-26,760, +17,400] | 32,170 | - |
| V3 W3_KELLY | 42,780 | 133,130 | 373,499 | -341,555 | -2,508,854 | -11,466 [-33,303, +10,032] | 30,689 | - |

**X' chain-active (20231002..20240131; the chain starts when the first 6-month window closes)** (n weeks = 18)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 45,124 | 76,084 | 152,478 | -68,555 | n/a | - | - | - |
| V5 SH6 | 30,599 | 82,796 | 331,577 | -226,963 | n/a | -14,526 [-46,814, +13,544] | 42,958 | - |
| V4 W6_KELLY | 29,158 | 80,761 | 262,150 | -182,030 | n/a | -15,967 [-47,753, +11,540] | 42,427 | - |
| V2 W6_MEAN | 25,208 | 98,596 | 414,306 | -287,739 | n/a | -19,916 [-61,165, +19,441] | 59,365 | - |
| V6 SEL | 25,208 | 98,596 | 414,306 | -287,739 | n/a | -19,916 [-61,165, +19,441] | 59,365 | - |
| V1 W3_MEAN | 10,626 | 111,993 | 356,898 | -268,759 | n/a | -34,499 [-87,415, +14,516] | 74,112 | - |
| V3 W3_KELLY | 12,648 | 103,004 | 358,090 | -268,759 | n/a | -32,477 [-74,634, +4,234] | 56,945 | - |

**POOLED chain-active (20231002..20260206) - sanity** (n weeks = 123)

| variant | mean/wk | SD | maxDD | worst wk | W20 | delta vs fixed [95% CI] | MDE | CAND-RECENT |
|---|---|---|---|---|---|---|---|---|
| FIXED | 52,662 | 119,127 | 562,196 | -309,830 | -2,554,319 | - | - | - |
| V5 SH6 | 33,870 | 117,989 | 469,063 | -249,468 | -2,893,681 | -18,792 [-32,720, -5,148] | 19,296 | - |
| V4 W6_KELLY | 39,246 | 123,984 | 592,385 | -294,433 | -2,956,082 | -13,416 [-28,302, +1,152] | 20,119 | - |
| V2 W6_MEAN | 40,119 | 134,714 | 500,355 | -304,703 | -3,491,808 | -12,543 [-28,056, +3,490] | 22,353 | - |
| V6 SEL | 40,217 | 139,433 | 511,924 | -304,703 | -3,576,696 | -12,445 [-28,151, +3,929] | 22,797 | - |
| V1 W3_MEAN | 40,452 | 140,438 | 541,199 | -330,187 | -3,589,060 | -12,210 [-29,330, +4,829] | 25,255 | - |
| V3 W3_KELLY | 32,333 | 131,398 | 538,594 | -341,555 | -3,655,307 | -20,328 [-36,194, -4,852] | 22,892 | - |

## PLACEBO (random re-allocation of the same lots across cells, same persistence and turnover) and gates

100 draws per variant; each draw applies ONE random permutation of the 36 cell labels to the whole monthly chain (same multiset of multipliers each month, identical turnover), full exact engine. Rank = share of draws below the real chain; the null MDE is 2.8 x SD of the placebo deltas (a real delta must exceed it to be distinguishable).

| layer | variant | L6M delta | L6M placebo mean [p95] | L6M null MDE | L6M rank | HOLD delta | HOLD placebo mean | HOLD rank | PRE rank | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| D6 | V1 W3_MEAN | -31,417 | -22,100 [-5,077] | 31,472 | 0.21 | -25,497 | -16,978 | 0.21 | 0.62 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| D6 | V2 W6_MEAN | -23,055 | -21,453 [+63] | 31,500 | 0.48 | -16,051 | -16,626 | 0.53 | 0.79 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| D6 | V3 W3_KELLY | -37,844 | -20,352 [-1,902] | 33,888 | 0.06 | -29,779 | -15,215 | 0.11 | 0.60 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D7 placebo, D8 RC |
| D6 | V4 W6_KELLY | -11,414 | -22,219 [-1,004] | 35,443 | 0.83 | -6,213 | -17,154 | 0.82 | 0.56 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D7 placebo, D8 RC |
| D6 | V5 SH6 | -4,252 | -15,245 [+2,130] | 28,098 | 0.88 | +1,204 | -12,089 | 0.91 | 0.45 | **DEAD** | D1 PRE mean, D3 X' mean, D4 maxDD, D5 worst-20, D7 placebo, D8 RC |
| D6 | V6 SEL | -19,415 | -21,821 [-5,030] | 30,498 | 0.55 | -12,866 | -16,290 | 0.66 | 0.25 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D7 placebo, D8 RC |
| F | V1 W3_MEAN | -22,536 | -16,960 [+2,246] | 30,059 | 0.35 | -16,196 | -15,622 | 0.52 | 0.89 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| F | V2 W6_MEAN | -19,257 | -18,888 [+692] | 33,388 | 0.51 | -11,704 | -16,747 | 0.67 | 0.73 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| F | V3 W3_KELLY | -38,193 | -19,308 [-5,806] | 25,330 | 0.02 | -32,996 | -17,510 | 0.03 | 0.77 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| F | V4 W6_KELLY | -17,771 | -19,795 [-1,470] | 36,737 | 0.53 | -13,456 | -18,309 | 0.62 | 0.70 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D4 maxDD, D5 worst-20, D6 SD, D7 placebo, D8 RC |
| F | V5 SH6 | -14,349 | -19,750 [-4,151] | 28,716 | 0.70 | -9,512 | -17,795 | 0.81 | 0.32 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D7 placebo, D8 RC |
| F | V6 SEL | -20,602 | -17,621 [-332] | 33,855 | 0.37 | -12,881 | -15,699 | 0.60 | 0.76 | **DEAD** | D1 PRE mean, D2 HOLD mean, D3 X' mean, D5 worst-20, D6 SD, D7 placebo, D8 RC |

Gates (never softened): D1 PRE delta >= 0; D2 HOLD delta >= 0; D3 X' delta >= 0; D4 maxDD(PRE+HOLD) <= fixed; D5 worst-20 (PRE+HOLD) >= fixed; D6 weekly SD <= fixed; D7 placebo rank >= 0.90 (L6M); D8 best-of-12 White RC p <= 0.05 (p = 0.97). Tier: PASS none failed; CANDIDATE = D1-D3 pass, D4/D5 not both failed, at most one other failure; else DEAD.

## PER-SESSION VERDICT LINES (by ENTRY session; row-attributed delta $/wk of the stack, variant minus fixed; MDE beside)

Attribution: each filled row keeps its entry session; the row P&L (net of locks and sweep) is compared between the variant run and the fixed run, so lock interplay across sessions is allocated to the session of entry. Verdict HELPS / HURTS only when the 95% CI excludes 0, else "inside MDE" with the sign. Windows recent first.

**D6 - V5 SH6**

| session | 2026 d (MDE) | L6M d (MDE) | HOLD d (MDE) | PRE d (MDE) | X' d (MDE) | verdict L6M / HOLD |
|---|---|---|---|---|---|---|
| ASIA | -37,303 (67,894) | -6,571 (22,846) | -2,956 (22,908) | -461 (12,777) | +2,646 (24,905) | inside MDE, - / inside MDE, - |
| LONDON | +19,362 (17,277) | -351 (14,781) | -1,556 (15,575) | -8,279 (17,996) | -36 (21,826) | inside MDE, - / inside MDE, - |
| PRE | +2,622 (14,069) | -133 (6,080) | -904 (5,464) | -705 (4,967) | -6,744 (9,960) | inside MDE, - / inside MDE, - |
| NY-AM | +2,935 (41,485) | -1,535 (16,865) | +155 (15,850) | -11,764 (14,399) | +1,375 (28,384) | inside MDE, - / inside MDE, + |
| NY-PM | +7,142 (36,824) | +4,338 (17,954) | +6,465 (16,234) | +1,251 (9,964) | -4,813 (25,760) | inside MDE, + / inside MDE, + |
| CLOSE | +0 (0) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | inside MDE, + / inside MDE, + |

**D6 - V6 SEL**

| session | 2026 d (MDE) | L6M d (MDE) | HOLD d (MDE) | PRE d (MDE) | X' d (MDE) | verdict L6M / HOLD |
|---|---|---|---|---|---|---|
| ASIA | -43,583 (41,214) | -9,651 (22,996) | -13,096 (23,913) | +12,440 (16,253) | +2,708 (31,143) | inside MDE, - / inside MDE, - |
| LONDON | +1,901 (32,915) | -9,389 (21,512) | -7,160 (19,206) | -13,043 (18,691) | -2,487 (22,081) | inside MDE, - / inside MDE, - |
| PRE | -1,896 (13,856) | -1,652 (5,306) | -121 (5,232) | -2,903 (5,451) | +228 (8,510) | inside MDE, - / inside MDE, - |
| NY-AM | -21,442 (43,041) | -2,167 (20,138) | -91 (18,139) | -9,275 (15,506) | -4,178 (26,620) | inside MDE, - / inside MDE, - |
| NY-PM | +10,900 (29,130) | +3,444 (17,252) | +7,601 (16,274) | -3,653 (11,169) | -7,294 (25,938) | inside MDE, + / inside MDE, + |
| CLOSE | +0 (0) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | inside MDE, + / inside MDE, + |

**F - V5 SH6**

| session | 2026 d (MDE) | L6M d (MDE) | HOLD d (MDE) | PRE d (MDE) | X' d (MDE) | verdict L6M / HOLD |
|---|---|---|---|---|---|---|
| ASIA | -29,049 (83,817) | -4,510 (25,387) | -683 (24,689) | +2,702 (13,315) | -826 (22,266) | inside MDE, - / inside MDE, - |
| LONDON | +22,759 (9,247) | -3,014 (18,852) | -3,219 (17,609) | -9,753 (14,890) | -4,630 (21,062) | inside MDE, - / inside MDE, - |
| PRE | -1,410 (11,561) | -2,135 (5,567) | -2,650 (4,917) | -1,938 (5,381) | -3,448 (9,548) | inside MDE, - / inside MDE, - |
| NY-AM | +2,406 (23,635) | -8,876 (17,016) | -7,261 (15,695) | -8,224 (12,533) | +527 (25,165) | inside MDE, - / inside MDE, - |
| NY-PM | +17,335 (34,050) | +4,185 (11,426) | +4,302 (10,592) | -6,062 (8,904) | -6,148 (20,083) | inside MDE, + / inside MDE, + |
| CLOSE | +0 (0) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | inside MDE, + / inside MDE, + |

**F - V6 SEL**

| session | 2026 d (MDE) | L6M d (MDE) | HOLD d (MDE) | PRE d (MDE) | X' d (MDE) | verdict L6M / HOLD |
|---|---|---|---|---|---|---|
| ASIA | -26,771 (69,687) | -3,489 (25,885) | -5,451 (25,220) | +8,729 (16,300) | -341 (30,221) | inside MDE, - / inside MDE, - |
| LONDON | -10,913 (37,912) | -10,013 (22,159) | -5,847 (20,258) | -7,497 (15,745) | -2,723 (24,644) | inside MDE, - / inside MDE, - |
| PRE | -6,817 (10,193) | -3,376 (5,990) | -2,875 (5,645) | -1,306 (4,600) | -5,061 (11,172) | inside MDE, - / inside MDE, - |
| NY-AM | -3,173 (11,083) | -7,315 (20,490) | -2,161 (19,460) | -2,263 (13,945) | -3,764 (37,626) | inside MDE, - / inside MDE, - |
| NY-PM | +8,214 (30,637) | +3,590 (11,394) | +3,453 (11,838) | -7,796 (7,788) | -8,026 (22,004) | inside MDE, + / inside MDE, + |
| CLOSE | +0 (0) | +0 (0) | +0 (0) | +0 (0) | +0 (0) | inside MDE, + / inside MDE, + |

## DRIFT: which objective/window the selector (V6) chose each month

**D6 session table (live DS3 stack, exact lock engine)**: 202310:W6_MEAN 202311:W6_MEAN 202312:W6_MEAN 202401:W6_MEAN 202402:W6_MEAN 202403:W6_MEAN 202404:W6_MEAN 202405:W6_MEAN 202406:W3_MEAN 202407:W3_MEAN 202408:W3_MEAN 202409:W3_MEAN 202410:W3_MEAN 202411:W3_KELLY 202412:W3_KELLY 202501:W6_MEAN 202502:W6_MEAN 202503:W6_KELLY 202504:W6_KELLY 202505:W6_KELLY 202506:W6_MEAN 202507:W6_MEAN 202508:W6_MEAN 202509:W6_KELLY 202510:W6_MEAN 202511:W6_MEAN 202512:W6_MEAN 202601:W6_MEAN 202602:W6_MEAN
Counts: W3_MEAN 5, W6_MEAN 18, W3_KELLY 2, W6_KELLY 4. By year: 2023: W3_MEAN 0, W6_MEAN 3, W3_KELLY 0, W6_KELLY 0; 2024: W3_MEAN 5, W6_MEAN 5, W3_KELLY 2, W6_KELLY 0; 2025: W3_MEAN 0, W6_MEAN 8, W3_KELLY 0, W6_KELLY 4; 2026: W3_MEAN 0, W6_MEAN 2, W3_KELLY 0, W6_KELLY 0

Share of the 36 cells at the floor (0 lots) / at the 2x cap, mean over refits by year (V1..V5):

| variant | 2023 (3 mo) | 2024 | 2025 | 2026 (2 mo) |
|---|---|---|---|---|
| V1 W3_MEAN | 34% / 44% | 31% / 48% | 25% / 53% | 24% / 46% |
| V2 W6_MEAN | 41% / 38% | 27% / 51% | 24% / 55% | 32% / 46% |
| V3 W3_KELLY | 40% / 34% | 32% / 44% | 30% / 45% | 32% / 33% |
| V4 W6_KELLY | 46% / 28% | 31% / 42% | 29% / 47% | 33% / 42% |
| V5 SH6 | 39% / 19% | 26% / 12% | 22% / 11% | 29% / 10% |

**T-STACK F layer (A06 x B02 in-engine; HM5R excluded)**: 202310:W6_MEAN 202311:W6_MEAN 202312:W6_MEAN 202401:W6_MEAN 202402:W6_MEAN 202403:W6_MEAN 202404:W6_MEAN 202405:W6_KELLY 202406:W3_MEAN 202407:W3_MEAN 202408:W3_MEAN 202409:W3_MEAN 202410:W3_MEAN 202411:W3_MEAN 202412:W6_KELLY 202501:W6_KELLY 202502:W6_KELLY 202503:W3_MEAN 202504:W3_MEAN 202505:W3_MEAN 202506:W6_MEAN 202507:W6_MEAN 202508:W6_MEAN 202509:W6_MEAN 202510:W6_MEAN 202511:W6_MEAN 202512:W6_MEAN 202601:W6_MEAN 202602:W3_MEAN
Counts: W3_MEAN 10, W6_MEAN 15, W3_KELLY 0, W6_KELLY 4. By year: 2023: W3_MEAN 0, W6_MEAN 3, W3_KELLY 0, W6_KELLY 0; 2024: W3_MEAN 6, W6_MEAN 4, W3_KELLY 0, W6_KELLY 2; 2025: W3_MEAN 3, W6_MEAN 7, W3_KELLY 0, W6_KELLY 2; 2026: W3_MEAN 1, W6_MEAN 1, W3_KELLY 0, W6_KELLY 0

Share of the 36 cells at the floor (0 lots) / at the 2x cap, mean over refits by year (V1..V5):

| variant | 2023 (3 mo) | 2024 | 2025 | 2026 (2 mo) |
|---|---|---|---|---|
| V1 W3_MEAN | 41% / 37% | 29% / 50% | 27% / 51% | 26% / 44% |
| V2 W6_MEAN | 43% / 37% | 26% / 53% | 24% / 54% | 31% / 49% |
| V3 W3_KELLY | 42% / 30% | 31% / 46% | 30% / 46% | 29% / 35% |
| V4 W6_KELLY | 48% / 26% | 30% / 47% | 27% / 47% | 32% / 43% |
| V5 SH6 | 43% / 18% | 27% / 12% | 23% / 10% | 29% / 11% |

## NOTES AND CAVEATS
- Chain starts 2023-10-02 (first 6-month window closed); before that all variants = fixed, so X' covers 2023-10..2024-01 only (18 weeks) and "pooled" is 2023-10..2026-02 (123 weeks).
- F layer: HM5R (5-minute HM signal swap, the third admitted rule of T-STACK F) cannot be expressed as engine rows and is excluded; A06 and B02 are applied exactly in the engine (halve, product 0.25 if both). Its fixed table therefore differs from the F report (PRE mean 54,246 here vs 57,026 there, which added approximate weekly deltas).
- Fit data are post-lock weighted row P&L of the fixed table; evaluation re-runs the exact lock engine with the new lots (lock thresholds stay in nominal-lot R), so the linear fit and the engine disagree where locks bind - that is part of the measured result. 50-contract concurrent cap pass active (rows reduced: see out/szr/runs.pkl nred).
- Placebo multipliers are permuted across cells after rounding (not re-rounded to the destination book's lot grid).
- Sharpe-proportional (V5) is lot-matched on the fit window (trade-weighted mean multiplier 1 before the 2x cap); Kelly K = $400,000; LP tail k = max(2, round(20 n/149)) weeks of the window.
- Files: out/szr/{runs.pkl,chains.pkl,final.json,pre.json}, code szr_compute.py / szr_stats.py / szr_report.py / szr_nightly_refit.py.
