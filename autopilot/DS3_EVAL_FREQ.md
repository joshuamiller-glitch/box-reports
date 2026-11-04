# DS3_EVAL_FREQ - signal-evaluation-frequency sensitivity (DIS-BG, Z2, 2026-11-04). Descriptive, nothing live, no PASS.
Scope note l2vast/ds3/prereg/DISBG_prereg.md sha256 3cb4bca22a88e20a6029cb596050cb8bfa21d035e680fcfc98a78b6e016abae9 (DECISIONS.md, before any number); ledger DIS_BG (14 cells); DISBG_NTESTED 14. Code l2vast/ds3/code/bg/ (bg_run.py, bg_live.py, bg_pair.py, bg_doc.py), results /mnt/l2/l2vast/ds3_zones3_new/Z2_bg/. dead_lookup: FADE_XI ORBF rows (`entry|fadexi|inst=NQ|book=ORBF|...`, RECENT-POS), FADE_GM / DIS_AG / DIS_AJ ORBF rows, O7 rows INSTR_RF / INSTR_CM / DIS_P (O7 pin DIRECTIVE_O7_PIN_20261104.md); none varies the evaluation granularity.

## Plain sentence
Of the lines in scope only ORBF reads intrabar prices (it fades the first 1-second bin that breaks the 09:30-10:00 range); every other Shadow line, O7 and the six live books' entry signals are evaluated on completed 1-minute bars (the signal second is the minute boundary), so a D7 that can only act at 1-minute closes loses nothing on them. For ORBF, evaluating at the 1-minute bar close instead of per second keeps 38% of the L6M dollars (+$783 vs +$2,053 a week at 2 lots, paired difference CI -$226 to +$2,962) and 50% of HOLD; fading only a 1-minute CLOSE beyond the range (a different, close-confirmed rule) keeps +$1,799 L6M and +$1,957 HOLD (more than per second in HOLD), so if D7 cannot evaluate every second the usable ORBF is the close-confirmed 1-minute version, not the high/low-break version.

## 1. Evaluation granularity per line (from the reference code and specs)
| line | evaluation granularity | where (file / function) | intrabar prices? | affected if D7 acts only at 1-min closes |
|--|--|--|--|--|
| ORBF (NYAM bundle) | 1-second bin: first bin after 10:00 whose high/low breaks the 09:30-10:00 range (range = max/min of the 1-s bins) | nyam_books.py `OrbFade.on_second` (l68); NYAM_SHADOW_SPEC.md sections 2-3 (order: ORBF is tested per second before the minute-boundary books) | YES (bin high/low every second) | YES: becomes ORBF-M; section 2 |
| ONRTH | 1-minute bar close (excursion tracked on completed bars; signal_sec = bar open + 60) | nyam_books.py `OnRthFade.on_minute` (l21) | bar high/low, evaluated at close | no |
| VWAPF | 1-minute bar close (VWAP/dev on completed bars) | nyam_books.py `VwapFade.on_minute` (l52) | bar OHLC at close | no |
| VB2NYPM_T1, VB2NYAM_T3, PDASIA_T2, OR15NYAM_T2 | 1-minute bar close; ATR(5m) as-of | fade_books.py `VB2.on_bar` l86, `PDASIA_T2.on_bar` l119, `OR15NYAM_T2.on_bar` l137; FADE_SHADOW_SPEC.md ("signals only at 1-minute bar closes"; section 4 contract) | bar high/low touch evaluated at the bar close | no; live-equivalent check: rebuilding the bars from the raw 1-s prints with the live definition matches 511/524, 311/317, 888/892, 932/935 research signals, P&L within a few percent (FADE_SHADOW_SPEC.md section 10) |
| Q13GAP_T1, DISB_PREL, DISE_PDF, DISC_SUN30 | 1-minute bar close | shadow2_books.py `on_bar` l54 / l116 / l145 / l169; SHADOW_PACK_2.md section 2 ("signals only at 1-minute bar closes") | no (DISE_PDF additionally needs the L2 refill-failure count per minute from D7's book) | no |
| DISK_BO_CH | 5-minute close beyond the 09:30-10:00 range, taken on the 1-minute bar that closes the 5-minute bucket (signal at a 1-min close) | shadow2_books.py `DISK_BO_CH.on_bar` l93 | no | no, but see section 3: the edge exists only at the 5-minute close |
| N_REL_rev | at the 09:31 close of the 09:30 1-minute bar (08:30 release move reversed) | code/disb/disb_events.py l107-125 | no | no (not yet a Shadow line) |
| O7 (TOPEN B2 DR10m pb1) | 1-minute bars, Calculate = On bar close: drive = close of the 09:39 bar - 09:30 open; pb1 = first 1-min bar from 09:40 whose close is against the drive; entry at that close | DIRECTIVE_O7_PIN_20261104.md; DS3_SPEC_TOPEN_DR10m_pb1_rm0.5_X40_90_SESSION.md ("Chart: 1 Minute bars, Calculate = On bar close") | no (5-min opening range from 1-min highs/lows, stored after the 09:34 bar) | no |
| six live books KB PE SM HM MV PB (entry signal) | 1-minute bar close: the library signal second is the minute boundary for 80-100% of rows; the rest (KB 12.5%, PE 20.5%, SM 21.6%, HM 19.6%, MV 9.2%, PB 0%, all in asia / london) are rows whose boundary second has no print, so the signal second is the first print after the boundary (checked: in 100% of 3,539 non-boundary rows the boundary second is absent from the 1-s path and the signal second is the first path second after it) | d7base lots_ts2.D._d() rows (`sin`), path SS | no | no (section 4: moving those rows to the boundary changes weekly P&L by noise) |
| PE 45-second confirmation | after the 1-minute-close signal the entry waits for a 45-second tape confirmation inside the next minute (entry second = confirmation fill) | d7base lots_ts2.entry_ts() (PE rows use the kernel confirmation second) | YES (intra-minute tape after the signal) | would be affected: needs a seconds clock; ATTRIBUTION: +$4.5k/wk (2026 Shapley), +$0.7k (one-at-a-time), +$0.3k ALL (sign flips by year) |
| exits: TH-L2 loss cut and take lines | L2 grid evaluated every tick, once per second (ThEvalFrequencySecs = 1; user answer DIRECTIVE_USER_ANSWERS_20261102.md) | live D7 | YES (per second) | the user's D7 already evaluates per second for these; the +$18.1k/wk TH-L2 effect depends on it |

## 2. ORBF at 1-s / 1-min / 5-min evaluation (live fill model: first fill B+1 s, resting 60/60, join stop 2.45, time stop 14:00, 914 days max; gate_v3 windows; 2 lots = study size)
ORBF_A reproduces the 914-row corrected study list exactly (same signal seconds) and the MultiHarness live model exactly (L6M +2,053 / HOLD +1,441 / PRE -1,675 at 2 lots); NYAM_SHADOW_SPEC.md quotes +2,103 / +1,490 / -1,622 from an earlier harness version and +770 for ORBF-M (here +783).
Variants: A = first 1-s bin high/low break (the study); B1 = first 1-min bar whose high/low breaks, fade at that bar's close (ORBF-M); B2 = first 1-min CLOSE beyond the range, fade at that close; C1 = first 5-min bar whose high/low breaks, fade at the 5-min close; C2 = first 5-min CLOSE beyond the range.
### 2 lots (study size)
| variant | trades | mean pts/trade L6M | mean pts/trade HOLD | $/wk L6M | HOLD | PRE | MID | X' | maxDD L6M |
|--|--|--|--|--|--|--|--|--|--|
| A 1-s bin high/low (study) | 914 | 10.91 | 7.40 | +2053 | +1441 | -1675 | +1607 | -821 | +11784 |
| B1 1-min bar high/low break (ORBF-M) | 914 | 4.16 | 3.68 | +783 | +717 | -1487 | +1491 | -443 | +18649 |
| B2 1-min close beyond range | 907 | 9.64 | 10.14 | +1799 | +1957 | -1403 | +2988 | -594 | +10964 |
| C1 5-min bar high/low break | 914 | 4.81 | 2.02 | +905 | +392 | -1473 | -1273 | -421 | +18228 |
| C2 5-min close beyond range | 894 | 3.02 | 3.01 | +550 | +569 | -805 | +745 | -345 | +21670 |

### 1 lot (register size)
| variant | trades | mean pts/trade L6M | mean pts/trade HOLD | $/wk L6M | HOLD | PRE | MID | X' | maxDD L6M |
|--|--|--|--|--|--|--|--|--|--|
| A 1-s bin high/low (study) | 914 | 11.18 | 7.66 | +1052 | +745 | -811 | +790 | -406 | +5975 |
| B1 1-min bar high/low break (ORBF-M) | 914 | 4.09 | 3.69 | +385 | +359 | -721 | +791 | -208 | +9508 |
| B2 1-min close beyond range | 907 | 9.75 | 10.21 | +910 | +986 | -686 | +1514 | -284 | +5195 |
| C1 5-min bar high/low break | 914 | 5.12 | 2.19 | +482 | +213 | -716 | -633 | -215 | +9012 |
| C2 5-min close beyond range | 894 | 3.32 | 3.20 | +302 | +303 | -395 | +396 | -174 | +10928 |

### Paired weekly difference, per-second evaluation minus the coarser one (4-week block bootstrap, 2,000 draws; share = difference / per-second $; 'share of the research P&L that exists only under per-second evaluation')
| pair | window | per-second $/wk | coarser $/wk | difference | 95% CI | share |
|--|--|--|--|--|--|--|
| ORBF A-vs-B1 2lot | L6M | +2053 | +783 | +1270 | [-226, +2962] | 62% |
| ORBF A-vs-B1 2lot | HOLD | +1441 | +717 | +724 | [-169, +1862] | 50% |
| ORBF A-vs-B1 2lot | PRE | -1675 | -1487 | -188 | [-621, +186] | 11% |
| ORBF A-vs-B2 2lot | L6M | +2053 | +1799 | +253 | [-1363, +2135] | 12% |
| ORBF A-vs-B2 2lot | HOLD | +1441 | +1957 | -516 | [-1479, +692] | -36% |
| ORBF A-vs-B2 2lot | PRE | -1675 | -1403 | -272 | [-1058, +519] | 16% |
| ORBF A-vs-C1 2lot | L6M | +2053 | +905 | +1148 | [-190, +2769] | 56% |
| ORBF A-vs-C1 2lot | HOLD | +1441 | +392 | +1049 | [-57, +2328] | 73% |
| ORBF A-vs-C1 2lot | PRE | -1675 | -1473 | -201 | [-1074, +747] | 12% |
| ORBF A-vs-C2 2lot | L6M | +2053 | +550 | +1503 | [-1001, +4020] | 73% |
| ORBF A-vs-C2 2lot | HOLD | +1441 | +569 | +872 | [-970, +2266] | 61% |
| ORBF A-vs-C2 2lot | PRE | -1675 | -805 | -869 | [-1636, -66] | 52% |
| ORBF A-vs-B1 1lot | L6M | +1052 | +385 | +667 | [-104, +1559] | 63% |
| ORBF A-vs-B1 1lot | HOLD | +745 | +359 | +386 | [-77, +942] | 52% |
| ORBF A-vs-B1 1lot | PRE | -811 | -721 | -90 | [-320, +114] | 11% |
| ORBF A-vs-B2 1lot | L6M | +1052 | +910 | +141 | [-685, +1159] | 13% |
| ORBF A-vs-B2 1lot | HOLD | +745 | +986 | -240 | [-715, +377] | -32% |
| ORBF A-vs-B2 1lot | PRE | -811 | -686 | -125 | [-512, +231] | 15% |
| ORBF A-vs-C1 1lot | L6M | +1052 | +482 | +570 | [-109, +1418] | 54% |
| ORBF A-vs-C1 1lot | HOLD | +745 | +213 | +532 | [-10, +1185] | 71% |
| ORBF A-vs-C1 1lot | PRE | -811 | -716 | -95 | [-533, +364] | 12% |
| ORBF A-vs-C2 1lot | L6M | +1052 | +302 | +750 | [-618, +2028] | 71% |
| ORBF A-vs-C2 1lot | HOLD | +745 | +303 | +443 | [-438, +1127] | 59% |
| ORBF A-vs-C2 1lot | PRE | -811 | -395 | -416 | [-815, -8] | 51% |

Trade level (2 lots, days where both variants fire): B1 fires on the same 914 days as A, a mean 39 s (median 42 s) later and 0.99 pt worse at the first fill on average (same side on 100% of days); the 1-minute bar-close delay turns 62% of the L6M gain and 50% of the HOLD gain into noise-sized differences (CI includes zero in L6M and HOLD, the lower bound of the PRE difference is -$621). B2 fires on 907 days (7 A-only days), a mean 440 s later (median 60 s), same side on 95% of days, and enters on average 6.5 pt BETTER than A on the days both fire (the close-confirmed break has retraced, so the fade starts from a better price on the days it fires); C1 (5-min high/low) is 207 s later and 1.77 pt worse; C2 (5-min close) fires on 894 days, 1,103 s later, enters 15.7 pt better but on only 91% matching sides. B2 beats A in HOLD (+$1,957 vs +$1,441) and MID, but trails in L6M (+$1,799 vs +$2,053); the paired differences are all inside their bootstrap CI (n = 187 weeks, 27 in L6M), so this is a description of what each rule did, not evidence that B2 is better. PRE is negative in every variant (-$1.4k to -$1.7k/wk; C2 -$0.8k).
Which ORBF would survive the user's stated latency? Only the high/low-break at a 1-minute close (ORBF-M, B1) is the literal version of the live statement ("signal at the 1-min close"): it keeps 38% of L6M and 50% of HOLD and has a larger drawdown (L6M maxDD $18.6k vs $11.8k at 2 lots). The close-confirmed 1-minute rule (B2) is a different rule that keeps L6M +$1,799 / HOLD +$1,957 and the same drawdown as A (L6M $11.0k): if D7 cannot evaluate every second this is the version to register (labelled ORBF-M2); it has not been tested beyond this description, so its p-values are not claimed.

## 3. DISK_BO_CH (COMP_HI nyam breakout-with, 2 lots, 60/60, T3600) at 5-min / 1-min / 1-s closes
The rule uses 5-minute closes, so the sensitivity is toward FINER evaluation. DISK_5 reproduces the 282 rows. (The earlier DIS-K pages ignored the time stop; DS3_DISCOVER2.md correction 23:35Z, rerun conclusion unchanged; the numbers below are the corrected ones.)
| variant | trades | mean pts/trade L6M | mean pts/trade HOLD | $/wk L6M | HOLD | PRE | MID | X' | maxDD L6M |
|--|--|--|--|--|--|--|--|--|--|
| DISK_5 first 5-min close beyond the range (the rule) | 282 | 13.89 | 10.73 | +905 | +644 | +91 | +170 | +18 | +9775 |
| DISK_1 first 1-min close beyond | 291 | -2.93 | -2.61 | -199 | -163 | +64 | +144 | +13 | +15540 |
| DISK_S first 1-s close beyond | 295 | -5.30 | 1.59 | -361 | +101 | +301 | +310 | +24 | +14310 |

The research edge exists only at the 5-minute close: finer evaluation of the same idea (the first 1-minute or 1-second close beyond the range) is negative in L6M (-$199 / -$361 a week) with larger drawdowns (L6M maxDD $15.5k / $14.3k vs $9.8k), the paired differences 5-min minus finer being +$1,105 (1-min) and +$1,266 (1-s) in L6M with CIs [-358, +2,473] and [-436, +2,988]. D7 acting at 1-min closes is not an issue for this line (a 5-minute close is a 1-minute close), but it should NOT be implemented at a finer clock; a faster D7 would make the line worse, not better.

## 4. Six live books: library signal second vs the minute boundary (P3 plain-bracket proxy rows at Q1-A live lots, live fill model; own no-overlap)
| book | rows | non-boundary rows | library trades | $/wk L6M / HOLD / PRE (library) | boundary trades | $/wk L6M / HOLD / PRE (signal at the minute boundary) | paired L6M difference CI |
|--|--|--|--|--|--|--|--|
| L_KB | 8025 | 1002 | 7848 | -759 / -1391 / +1937 | 7851 | -565 / -1371 / +1926 | -194 [-709, +87] |
| L_PE | 6126 | 1255 | 6004 | +7941 / +3269 / +4313 | 6005 | +8703 / +3307 / +4332 | -763 [-3180, +514] |
| L_SM | 1370 | 296 | 1368 | +1487 / +627 / +1805 | 1367 | +1506 / +631 / +1542 | -19 [-71, +12] |
| L_HM | 3304 | 648 | 3259 | +1772 / +4563 / +1350 | 3256 | +2272 / +4788 / +1249 | -499 [-1159, -40] |
| L_MV | 3674 | 338 | 3619 | -530 / +81 / +772 | 3623 | -439 / +194 / +754 | -91 [-310, +133] |
| L_PB | 5403 | 0 | 1167 | +60 / +284 / +1005 | 1167 | +60 / +284 / +1005 | +0 [+0, +0] |

Moving the non-boundary signals to the minute boundary changes the weekly P&L by amounts that are inside the bootstrap noise for every book (L6M differences -$763 to +$0, only L_HM's CI excludes zero at -$499, in the direction of the boundary version being better), so the share of research P&L that exists only under per-second evaluation is ~0 for the live books' entry signals. These are proxy rows (plain 60/60 bracket, no split / PE confirmation / locks), so absolute dollars differ from the live ledger; the non-boundary rows are an artefact of sparse overnight tape (no print in the boundary second), not intrabar logic.

## 5. Share of research P&L that exists only under per-second evaluation, per line
| line | research clock | per-second-only share |
|--|--|--|
| ORBF | 1-s | 62% of L6M, 50% of HOLD, 11% of PRE (negative PRE) at 2 lots vs the 1-min high/low version; CIs include 0 (section 2) |
| ONRTH, VWAPF, VB2NYPM_T1, VB2NYAM_T3, PDASIA_T2, OR15NYAM_T2, Q13GAP_T1, DISB_PREL, DISE_PDF, DISC_SUN30, DISK_BO_CH, N_REL_rev, O7 | 1-min bar (DISK: 5-min) | 0% by construction: the research rows are the bar-close rows (streaming reproduction diff 0 against the research lists in NYAM_SHADOW_SPEC / FADE_SHADOW_SPEC / SHADOW_PACK_2) |
| six live books (entry) | 1-min bar close | ~0 (section 4) |
| PE 45-s confirmation, TH-L2 cuts / take lines | per second (intra-minute tape / L2 grid) | not an entry-evaluation question: these need D7's seconds clock; see section 1 |

## 6. Answer to the decision item "can ORBF be evaluated every second live"
The numbers above are what is at stake: per-second evaluation is worth about +$1.3k/wk in L6M (62% of ORBF's L6M, 2 lots; +$0.7k at the register's 1 lot) and +$0.7k in HOLD, with an L6M maxDD of $11.8k instead of $18.6k at 2 lots, but the difference is not statistically separable from zero with 27 L6M weeks. D7's own tape already supports per-second work (the TH-L2 grid is evaluated every second; NYAM_SHADOW_SPEC.md section 3 has the O(1)-per-second ORBF state), so the question for the user is whether the D7 clock can raise a signal inside a minute (as the L2 grid does) for a Shadow-only log line. If not, register ORBF-M (B1) as the literal 1-minute version or ORBF-M2 (B2) as the close-confirmed version, not the study number.
Everything else in the Shadow set, O7 and the live entry signals is unaffected by a 1-minute-close-only D7 (section 1). No PASS; nothing live; descriptive measurements (no hypothesis test, so no multiplicity charge beyond the 14 cells).
