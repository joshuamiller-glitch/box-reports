# DS3_REBUILD_S3_ENV - stage 3 brackets by ENVIRONMENT (stop / target / time-stop by session x environment), raw chassis, from the SAME stage 3 grid runs (W-S3). FIRST PASS, PARTIAL. Updated 2026-11-17 18:57Z
> VALIDATION (W-S3, FIRST PASS, 2026-11-17): trials counted = per book 7 schemes x 3 buckets x <= 5 sessions + pooled x 11 candidates (native + 10 priority grid sets), 7 books; the screen is read against 21 shifted-label runs (11/23/37 days) and 3 nonsense 3-bucketings (all counted); correction = walk-forward (one freeze per book on the SEL months landed, then HOLD 2025-11..2026-04 and L6M 2026-05..10 read once) + label nulls; PBO / White RC over the full grid on the stage 3 page; engine-exact assembly and 30 random-bracket controls NOT built yet: nothing here is a tier, missing controls = NOT FINISHED. Numbers shown: SEL-only (no book frozen yet).

VERDICT (data ends 2026-10-30; FIRST PASS, PARTIAL: only the 10-set priority subset of the grid (6 targets at stop 60, 40/40, 40/60, 90/60, 90/90) is used and it is still landing; frozen books none): see five lines below; nothing assembled on the engine, no tier.

## Five-line summary
1. Tried: every stage 3 trade is tagged at the signal with 7 environment bucketings (atr_rel thirds and live 1.3/1.6 marks, with/against the day 3-of-4 vote, ER30 proxy, range used vs HAR forecast, room to nearest level ahead, fresh/rechase); the best of 11 bracket settings is picked per book x session x bucket on SEL only.
2. Holds / not: the untouched read is in the null table: a real scheme counts only if its holding-pick count is above the three shifted-label runs and the nonsense runs (no book frozen yet).
3. Shape: Table 4 counts cells whose best target moves in the expected direction (nearer against the day / low room / high range used): 0 consistent of 0 cells with a varying pick.
4. DS7 needs: all inputs are own-bar features (atr_rel, day vote, 1-min closes, level distances, HAR range forecast) except the ER ladder (own ER30 proxy used, live ladder not replicated) and the no-trade zones (levels used instead).
5. Next: for any holding rule: exact assembled raw-chassis and JL3 runs with 30 random-bracket controls (not built; needs the lead's queue OK); the stage 3 grid keeps landing.

## THP grammar extension needed in DS7 (parser change for the Table 1 policy lines)
```
bracket <book> <session|*> stop=<pts> target=<pts> [timestop=<minutes>[:<min open profit pts>]] [halfoff=<pts> [be]]
  session: asia | london | nyam | nypm (the existing lines 'bracket K7 * target=59' stay valid; today only target= exists)
  stop=<pts>      initial stop distance in points; lots scale x 60/stop (min 1) as ApplyPolicyBracket does
  timestop=N:M    N minutes after the entry fill, if open profit < M points exit at market (M omitted = unconditional exit at N)
  halfoff=X [be]  at +X points take half (live lots floor, min 1); with 'be' the rest moves to breakeven
```
New parser tokens: stop=, timestop=, halfoff= and a session in the third column of 'bracket'. Everything on these pages is raw-chassis research until the exact JL3 assembly and 30 random-bracket controls (S3J) are scored.

## Table 0 - progress
| book | common SEL months | HOLD+L6M months landed | state |
|--|--|--|--|
| K7 | 3 | 12 / 12 | too few months landed |
| M7 | 3 | 12 / 12 | too few months landed |
| P7 | 3 | 12 / 12 | too few months landed |
| U7 | 3 | 12 / 12 | too few months landed |
| H7 | 3 | 12 / 12 | too few months landed |
| A7 | 3 | 12 / 12 | too few months landed |
| O7 | 1 | 0 / 12 | too few months landed |

Cuts (frozen from native SEL trades): atr_rel thirds [1.0641536788691555, 2.289134438305709], ER30 thirds [0.16943521594684385, 0.28316831683168314].

## Table 2 - the null: how often a pick is made and holds untouched (HOLD and L6M ulcer lower than native, mean within -25%), frozen books only (none)
| scheme | real: picks made / holding untouched | shift 11 | shift 23 | shift 37 | nonsense (3 runs, pooled) |
|--|--|--|--|--|--|
| ATRT | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| ATRL | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| DAY | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| ER | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| RNG | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| ROOM | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |
| FRESH | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 | 0 / 0 |

## Table 1 - picks (non-native) by book x scheme x session x bucket
| book | scheme | session | bucket | SEL n (native) | pick | SEL ulcer native -> pick | HOLD ulcer | HOLD mean $/wk (@4.84) | L6M ulcer | L6M mean $/wk (@4.84) | holds untouched |
|--|--|--|--|--|--|--|--|--|--|--|--|

## Table 4 - shape: best target by bucket (N = native kept; * = time-stop/half-off pick shown at native target) and rank correlation with bucket order
| book | scheme | session | pick target by bucket (low -> high; N = native) | rank corr | expected sign | consistent |
|--|--|--|--|--|--|--|

## Table 5 - simplest rule alone (no selection, arithmetic substitution from the S060 grid sets; stop 60 books; native = fixed 58/60)
not enough grid months landed yet

<!-- MD:APPEND -->
<!-- W-MD section start: written 2026-11-17 19:07Z; sections: UW levels, Size by environment, Own-book walls, one summary table. Source W-MD (MAJOR D addendum 1337Z). FIRST PASS, ARITHMETIC SCREEN (raw-chassis 1-s paths); no engine run yet; nothing assembled. -->

# W-MD sections (appended below the W-S3 ENV page): UW levels as exit levels, size by environment, own-book walls
> VALIDATION (W-MD, FIRST PASS, written 2026-11-17 19:07Z): trials counted in autopilot/TRIALS_LEDGER.csv as MD1 (UW/free-level exit rules: 31 rules x 15 book x session cells = 465 + shape grid 5 targets x 4 dimensions x 15 cells = 300), MD2 (size by environment: 12 dimensions x 15 cells = 180), MD3 (walls: 8 rules x 5 groups = 40); correction: none applied beyond the shifted-label null (11/23/37 trades) and 3 nonsense bucketings; PBO not computed (no fitted portfolio); in-sample = SEL (2023-04..2025-10; UW sets 2024-10..2025-10 only: UW history starts 2024-10-01), walk-forward = frozen pick then HOLD (2025-11..2026-04) and L6M (2026-05..2026-10) untouched; planted-edge check passed (below); data ends 2026-10-30.

## W-MD five-line summary
1. Tried: (1) UW dealer / gamma-wall / max-pain / large-OI levels (prior-day snapshot only) as exit levels: target at the nearest level ahead minus 0/5/10 pts and stop to breakeven or -20 after a rejection, against the box own zones and round numbers, per book x session, frozen on the selection period, read on HOLD and L6M; the UW net-gamma sign and the room to the nearest level as buckets for target distance; (2) size x0.5/x1/x1.5 by 8 environment dimensions + the UW family-7 score; (3) own-book walls from MBO (nearest resting order >= 8/16/32 lots, age >= 30/120 s): target in front of the wall and exit when the wall is pulled.
2. Timing audit (a): n_dl_sp_ahead_60 is NOT a UW column. It is the Dalton single-print flag (TPO of the last 5 completed RTH days, unfilled zones within 60 pts ahead; code/th_confl_cf5/cf5_sess.py) and uses only completed 1-min bars and completed RTH days: timing is clean. It fires on 49 of 1,849 K7 NY AM trades (mean R -0.42 vs +0.02 on the other 1,800, plain two-sample t = -3.4; same sign in every year, n = 15/15/8/11, mean R -0.12/-0.57/-0.37/-0.66, L6M n = 7; P7 and M7 do not show it), so the stage 1 z of -7 comes from a very thin flag counted over weeks, not from a UW level; it is one K7 NY AM cell out of thousands scanned. UW levels are one end-of-day snapshot per date (about 16:14 ET); only the previous date is used: no look-ahead, no intraday history of UW levels exists.
3. What holds / what does not: of the 15 book x session cells, 6 UW-level cell-rules and 6 free-level cell-rules (own zones, round numbers) hold on both untouched windows at the main fill assumption; the shifted-label null produces about as many (table 1b). Two cells hold for UW levels under all three fill assumptions and beat their null (0 of 3 shifted runs): H7 Asia (target at the UW level minus 10 pts, or stop to breakeven after a rejection; ulcer -46% / -33% on HOLD / L6M) and K7 NY PM (NDX-only levels minus 10 pts; ulcer -11% / -7%). LEADs only: both are thin, and a 250-point round-number target also holds in H7 Asia, so UW adds little over free levels there. Net-gamma sign and room buckets show no monotone shape. Sizing by environment: nothing beats the null (table 2). Walls: nothing holds on the 6 covered months; the walk-forward over 2023-2026 runs when the background extraction (3 workers, 11 s per day) finishes (progress 973 of about 965 older days).
4. What it needs in DS7: level exits need the UW gex-levels endpoint (oi and vol; NDX and SPX) plus the oi-per-strike endpoint (max-pain, large-OI strikes) once a day after the 16:15 ET snapshot (Advanced API tier as bought for the trial; about 6 requests a day), a mapping of index level to the traded NQ contract (snapshot basis) and a roll guard; the free-level versions need nothing. Walls need a depth feed (the CQG 20-level book is too shallow to see most walls inside 60 pts; MBO gives full depth).
5. Next: if H7 Asia is kept as a lead, the engine test is an exact hook (target = prior-day UW level minus 10 pts) with an identity cell and 30 persistent random-target controls; it is built and queued by W-MD behind the A/C/E/B/F queues (see queue line below). Everything else is closed at screen level.

## 1. UW levels as exit levels
### 1a. Timing audit (finished)
- n_dl_sp_ahead_60 = "dl" Dalton, "sp" single prints, "ahead" within 60 pts in the trade direction, "n_" named-system column of block B (code/th_confl_cf5/cf5_sess.py lines 90-128, chunk B_sess_named). It does not read any Unusual Whales field. Inputs: 1-min bars with ts+60 <= signal second and the 5 most recent RTH days completed before the signal (16:00 ET); a zone counts only if no completed bar since its day printed through it. Verdict: no look-ahead. It was excluded in stage 1 only because its name contains "ahead".
- Published times of every UW level used (files /mnt/l2/l2vast/uw/...; one file per calendar date, 553 dates 2024-10-01..2026-11-12; 531 dates with a snapshot used here): gex-levels (call wall, put wall, gamma flip, gamma magnet; source oi and vol) carry the vendor time stamp 20:14 (596), 21:14 (318), 20:15 (38) UTC (= 16:14 ET in both summer and winter): one end-of-day snapshot after the cash close, never intraday; spot-exposures/strike and oi-per-strike for a past date are rebuilt from end-of-day data (all strike rows time = close); max-pain and the top-3 large-OI strikes are computed here from oi-per-strike (OI is the previous clearing; the date file is end-of-day, so conservative); net gamma = last 1-min spot-exposure gamma_per_one_percent_move_oi of the date (cash close, about 20:00-20:39Z). greek-exposure (static daily net gamma) exists for NDX/SPX only from 2025-11-13, so the gamma sign uses spot-exposure instead.
- Rule used in every test: a signal of Globex day label L reads the snapshot of the latest date strictly before L (so Asia of date D evening, which opens 18:00 ET, reads the D snapshot taken about 16:14 ET: 1 h 45 min of margin; London/NY read the previous evening). The code asserts snapshot time < signal time for every trade (passed), and drops the trade from level rules when a contract roll falls between the snapshot and the signal (levels are mapped into the raw front-month price frame of the snapshot: level_nq = NQ at the snapshot + (index level - UW spot) x NQ/index ratio at the snapshot; 55 glitch rows (NDX-spot jumps) fall back to the median ratio of the 5 previous dates). Prior-day UW coverage of the raw-chassis trades: 2023: 0%, 2024: 24%, 2025: 99%, 2026: 99%.
- There is no way to test an intraday refresh of the levels: the history has none. The 0DTE/expiry levels would need the live recorder (gex_strike_expiry channel), not started. So everything below is the PRIOR-DAY-CLOSE set.

### 1b. Level sets: how near they are (share of trades with the nearest level ahead within the bucket)
| level set | trades | median room (pts) | < 30 | 30-60 | > 60 or none |
|--|--|--|--|--|--|
| UW all (NDX+SPX gamma walls, flip, magnet, max-pain, top-3 OI strikes) | 14846 | 44.5 | 37% | 14% | 49% |
| UW gamma levels only (NDX+SPX) | 14846 | 42.0 | 34% | 12% | 54% |
| UW NDX only | 14846 | 78.6 | 22% | 11% | 68% |
| UW max-pain + top OI strikes | 14846 | 158.4 | 6% | 6% | 87% |
| own free zones (prior RTH H/L/C/POC/VAH/VAL/open, Globex-day H/L so far) | 21049 | 20.8 | 58% | 18% | 24% |
| round numbers every 250 | 21049 | 125.1 | 12% | 12% | 76% |
| round numbers every 100 | 21049 | 51.2 | 28% | 30% | 41% |

Rules replayed on the 1-s raw-chassis paths (21,049 trades, 7 books alone, native 60/60 stop/target; O7 40/90): T = target at (nearest level ahead - buffer b in 0/5/10 pts, floor 8) when nearer than the native target; S = after price gets within 5 pts of the level and pulls back 10 pts, stop to breakeven (BE) or -20 pts. A rule only changes a trade if it fires before the native exit; a target fires when the 1-s mid is within OFF pts of it (main OFF 1.5: the mid lags the printed fill by a median 1.75 pts on native target exits; OFF 0 conservative, OFF 3 optimistic). Per cell: pick = lowest ulcer on SEL subject to mean not lower, >= 3% ulcer gain, >= 10 fired trades; frozen; "holds" = ulcer lower on HOLD and on L6M with mean change >= -5% of native. Null = the same procedure with the room taken from the trade 11/23/37 places earlier in the cell. "@UWsample" = free levels on the same UW-eligible trades and the same selection window (head-to-head).

**Table 1b - picks made / holding untouched (15 book x session cells), real vs shifted-label null, and the two fill sensitivities**
| rule family | cells | real: picks / holds | null holds (shift 11 / 23 / 37) | null mean picks / holds | OFF 0 (conservative): picks / holds | OFF 3 (optimistic): picks / holds |
|--|--|--|--|--|--|--|
| T_UW | 15 | 5 / 1 | 0 / 1 / 0 | 4.3 / 0.3 | 3 / 2 | 6 / 2 |
| T_UWG | 15 | 5 / 2 | 0 / 0 / 2 | 4.0 / 0.7 | 3 / 1 | 8 / 2 |
| T_UWN | 15 | 3 / 1 | 0 / 0 / 2 | 4.7 / 0.7 | 3 / 1 | 5 / 1 |
| T_UWO | 15 | 5 / 0 | 0 / 0 / 1 | 6.7 / 0.3 | 5 / 0 | 7 / 2 |
| T_OWN | 15 | 4 / 1 | 0 / 3 / 2 | 3.3 / 1.7 | 2 / 0 | 5 / 0 |
| T_R250 | 15 | 6 / 3 | 3 / 2 / 2 | 7.7 / 2.3 | 5 / 1 | 7 / 3 |
| T_R100 | 15 | 5 / 0 | 0 / 0 / 1 | 6.0 / 0.3 | 0 / 0 | 7 / 5 |
| T_OWN@UWsample | 15 | 4 / 1 | 1 / 2 / 1 | 3.7 / 1.3 | 2 / 0 | 5 / 0 |
| T_R250@UWsample | 15 | 7 / 4 | 4 / 2 / 1 | 7.7 / 2.3 | 5 / 1 | 8 / 4 |
| T_R100@UWsample | 15 | 4 / 1 | 2 / 1 / 1 | 6.7 / 1.3 | 1 / 0 | 7 / 4 |
| T_FIXED | 15 | 9 / 0 | 0 / 0 / 0 | 9.0 / 0.0 | 5 / 0 | 12 / 3 |
| S_UW | 15 | 1 / 1 | 0 / 0 / 0 | 2.7 / 0.0 | 1 / 1 | 1 / 1 |
| S_UWG | 15 | 1 / 1 | 0 / 0 / 0 | 1.7 / 0.0 | 2 / 1 | 1 / 1 |
| S_OWN | 15 | 3 / 0 | 1 / 0 / 0 | 1.3 / 0.3 | 2 / 0 | 2 / 0 |
| S_R250 | 15 | 6 / 2 | 1 / 1 / 1 | 4.3 / 1.0 | 5 / 2 | 6 / 2 |
| S_R100 | 15 | 2 / 0 | 0 / 1 / 2 | 4.3 / 1.0 | 3 / 0 | 3 / 0 |
| S_OWN@UWsample | 15 | 2 / 0 | 1 / 0 / 0 | 0.7 / 0.3 | 2 / 0 | 2 / 0 |
| S_R250@UWsample | 15 | 5 / 0 | 2 / 1 / 2 | 7.0 / 1.7 | 4 / 0 | 5 / 1 |
| S_R100@UWsample | 15 | 1 / 0 | 2 / 1 / 1 | 3.0 / 1.3 | 1 / 0 | 2 / 0 |

**Table 1c - the cells that hold untouched (real run, main fill assumption; $/wk at live lots x1.75; ulcer change on HOLD / L6M)**
| rule | cell | pick | fired in SEL | SEL ulcer | HOLD / L6M ulcer | HOLD / L6M mean $/wk | fired HOLD / L6M | other fill assumptions |
|--|--|--|--|--|--|--|--|--|
| S_R250 | A7 Asia | M20 | 47 | -6% | -42% / -17% | 238 / 657 | 17 / 26 | cons:holds, opt:holds |
| S_R250 | H7 Asia | BE | 49 | -19% | -12% / -19% | 769 / 1880 | 7 / 11 | cons:holds, opt:holds |
| S_UW | H7 Asia | BE | 102 | -63% | -47% / -24% | 2004 / 1421 | 38 / 38 | cons:holds, opt:holds |
| S_UWG | H7 Asia | BE | 99 | -62% | -47% / -24% | 2004 / 1789 | 38 / 37 | cons:holds, opt:holds |
| T_HYBN | K7 NY PM | b10 | 277 | -69% | -39% / -39% | 1537 / 295 | 144 / 155 | cons:no, opt:no |
| T_OWN | K7 NY PM | b20 | 579 | -57% | -40% / -63% | 1912 / 732 | 145 / 160 | cons:no, opt:no |
| T_OWN@UWsample | K7 NY PM | b20 | 264 | -52% | -40% / -63% | 1941 / 628 | 142 / 158 | cons:no, opt:no |
| T_R100@UWsample | K7 NY AM | b20 | 318 | -32% | -10% / -71% | 191 / 1778 | 169 / 191 | cons:no, opt:holds |
| T_R250 | H7 Asia | b20 | 111 | -37% | -12% / -7% | 394 / 994 | 20 / 27 | cons:holds, opt:holds |
| T_R250 | M7 London | b20 | 283 | -29% | -42% / -36% | 920 / 2724 | 91 / 123 | cons:no, opt:holds |
| T_R250 | P7 London | b15 | 172 | -25% | -47% / -9% | 1500 / 895 | 55 / 99 | cons:no, opt:holds |
| T_R250@UWsample | H7 Asia | b20 | 53 | -9% | -12% / -8% | 394 / 994 | 20 / 27 | cons:no, opt:no |
| T_R250@UWsample | K7 NY AM | b15 | 130 | -32% | -18% / -31% | 586 / 737 | 64 / 64 | cons:holds, opt:holds |
| T_R250@UWsample | M7 London | b20 | 147 | -20% | -42% / -36% | 739 / 2724 | 90 / 123 | cons:no, opt:holds |
| T_R250@UWsample | P7 London | b15 | 104 | -27% | -49% / -9% | 1107 / 895 | 54 / 99 | cons:no, opt:holds |
| T_UW | H7 Asia | b10 | 124 | -76% | -46% / -33% | 1132 / 2442 | 55 / 50 | cons:holds, opt:holds |
| T_UWG | H7 Asia | b10 | 119 | -74% | -46% / -34% | 1236 / 3446 | 54 / 44 | cons:holds, opt:holds |
| T_UWG | P7 NY AM | b20 | 216 | -44% | -0% / -15% | 1733 / 835 | 98 / 105 | cons:no, opt:no |
| T_UWN | K7 NY PM | b20 | 127 | -28% | -21% / -11% | 610 / 909 | 67 / 57 | cons:holds, opt:holds |

Planted-edge check (before reading "nothing holds"): the same T_UW procedure on a world where every trade the b0 rule fires on really reverses (native -40 pts) finds 15 / 15 picks / holds in 15 cells (null 0-4 picks, 0 holds); the sizing procedure on +$300 per lot on with-the-day trades (0.25 R) holds in 6 of 13 vote cells vs 0-1 in its null. Reading: the screen has power for effects of that size; an effect much smaller than that (like +$40 per lot) is not detectable by ulcer, in any cell.

Reading 1b-1c: UW sets hold in a handful of cells; the same count appears for round numbers and own zones, and the free-level versions are not worse on the UW-eligible sample, so UW levels add nothing that is robust over free levels EXCEPT possibly H7 Asia, where only UW (and 250-round) levels hold and a plain fixed nearer target does not (T_FIXED H7 Asia: HOLD ulcer +56%, L6M -40%). H7 Asia is a thin cell (about 55 + 50 fired trades in HOLD + L6M); K7 NY PM holds for the NDX-only set at some fill assumptions only. Not CONFIRMED; LEAD for an engine test.

### 1c. Shape: best target by room to the nearest UW level (stop native) and by UW net-gamma sign (books pooled per session; mean points per trade, SEL = 2024-10..2025-10; T = fixed target, native = 60)
| session | bucket | n (SEL) | best T on SEL | mean pts at best (SEL) | native (SEL) | best T on HOLD | native on HOLD | best T / native on L6M |
|--|--|--|--|--|--|--|--|--|
| Asia | lt30 | 988 | native | 4.5 | 4.5 | 0.9 | 0.9 | 4.0 / 4.0 |
| Asia | 30-60 | 236 | T30 | 2.5 | 0.8 | 3.5 | 3.1 | 0.9 / -9.9 |
| Asia | gt60 | 522 | T50 | 8.6 | 6.8 | 10.2 | 10.6 | 5.2 / 7.0 |
| London | lt30 | 803 | T50 | 1.7 | 1.0 | 0.1 | 2.2 | 5.7 / 6.3 |
| London | 30-60 | 265 | T40 | 7.0 | 3.8 | 0.1 | -1.2 | 5.2 / 5.2 |
| London | gt60 | 585 | native | 3.0 | 3.0 | -1.0 | -1.0 | -3.2 / -3.2 |
| NY AM | lt30 | 693 | native | 9.8 | 9.8 | 1.1 | 1.1 | -3.3 / -3.3 |
| NY AM | 30-60 | 272 | T20 | 1.2 | -1.7 | 0.8 | 0.7 | 0.8 / -1.9 |
| NY AM | gt60 | 698 | T30 | 2.0 | 0.7 | -0.1 | 1.5 | 1.9 / -0.2 |
| NY PM | lt30 | 159 | T50 | 1.1 | -1.2 | -8.1 | -9.7 | -7.8 / -8.8 |
| NY PM | 30-60 | 85 | T50 | -4.6 | -6.7 | 4.6 | 3.0 | -7.0 / -6.1 |
| NY PM | gt60 | 221 | native | 7.6 | 7.6 | -6.7 | -6.7 | 5.2 / 5.2 |

Same by UW net-gamma sign at the prior close (long / short):
| session | bucket | n (SEL) | best T on SEL | mean pts at best (SEL) | native (SEL) | best T on HOLD | native on HOLD | best T / native on L6M |
|--|--|--|--|--|--|--|--|--|
| Asia | long | 1392 | native | 5.3 | 5.3 | 4.7 | 4.7 | 5.2 / 5.2 |
| Asia | short | 488 | native | 3.9 | 3.9 | -2.0 | -2.0 | -0.5 / -0.5 |
| London | long | 1266 | T40 | 2.5 | 1.3 | 2.0 | 3.3 | -0.2 / 0.6 |
| London | short | 572 | native | 3.6 | 3.6 | -6.0 | -6.0 | -2.6 / -2.6 |
| NY AM | long | 1389 | native | 4.9 | 4.9 | 1.9 | 1.9 | 2.2 / 2.2 |
| NY AM | short | 444 | T20 | 1.8 | 1.5 | -4.3 | -10.4 | 2.0 / -5.8 |
| NY PM | long | 343 | T50 | 2.5 | 1.2 | -6.4 | -6.8 | 0.2 / 2.0 |
| NY PM | short | 169 | T20 | 1.1 | 0.8 | 0.7 | 4.4 | 4.5 / 2.9 |

Reading: the hypothesis "near level = nearer target is better" would show T15/T20/T30 best in the lt30 bucket and T50/native best in gt60; the best fixed target by bucket is not monotone in any session, and "long gamma = nearer target, short gamma = farther" is not borne out (short gamma is worse than long gamma on HOLD in Asia, London and NY AM for every target, not nearer-target specific). Walk-forward pick of a target per bucket (book x session x dimension) and its null:
| dimension | cells | real: picks / holds | null holds (11 / 23 / 37) | |
|--|--|--|--|--|
| roomUW | 15 | 14 / 2 | 3 / 3 / 1 |   |
| gamma | 15 | 10 / 2 | 1 / 3 / 2 |   |
| roomOWN | 15 | 15 / 4 | 3 / 2 / 0 |   |
| roomR100 | 15 | 12 / 1 | 1 / 1 / 3 |   |
| nonsense0 | 15 | 12 / 1 | (nonsense run: itself a null) |   |
| nonsense1 | 15 | 13 / 1 | (nonsense run: itself a null) |   |
| nonsense2 | 15 | 12 / 2 | (nonsense run: itself a null) |   |

### 1d. What each item needs live
- Room to the nearest UW level / target at the level / stop after rejection: GET /api/stock/{NDX|SPX}/gex-levels?source=oi and ?source=vol (call wall, put wall, gamma flip, gamma magnet) and GET /api/stock/{NDX|SPX}/oi-per-strike (max-pain and large-OI strikes are computed from it), once a day after about 16:15 ET (about 6 requests per day); plan tier: the API Advanced month bought for the trial ($375; all the history above was pulled under it; whether a cheaper tier exposes gex-levels and oi-per-strike is NOT established: the API answers 403 advanced_tier_required / missing_access when it does not). D7 additionally needs the index-to-contract mapping (snapshot basis: NQ minus index spot at the snapshot) and the roll guard. Free-level versions (own zones, round numbers): nothing.
- UW net-gamma sign: GET /api/stock/{T}/spot-exposures (1-min, gamma per 1% move, OI based; the last row of the date is used here) or /greek-exposure (daily; docs: use the sign of call_gamma + put_gamma); same tier; the daily sign is available the evening before. No live endpoint is needed for the prior-day versions; the intraday refresh was not testable (no intraday level history).

## 2. Size by environment (raw chassis; lots x0.5 / x1 / x1.5 by bucket; exposure neutral; walk-forward; ulcer first)
Dimensions: atr_rel terciles; atr_rel live marks (<1.3 / 1.3-1.6 / >1.6, literal DS7 JnAtrRel series); with/against the day (>=3 of 4 of: session open, 18:00 open, session VWAP, close 60 min earlier = own proxy of the v2.0 vote); ER60 terciles (own proxy of the ER ladder); range used vs HAR forecast (<50% / 50-100% / >100%); room to nearest own zone and to nearest UW level (<30 / 30-60 / >60); fresh vs rechase (family 9); UW family-7 score (top 5 name-clean J columns per cell chosen on 2024-10..2025-10, score = favourable - unfavourable). Best bucket x1.5, worst x0.5 (SEL mean $/lot), multipliers divided by their SEL mean so the exposure is equal; lot rounding ignored.
| dimension | cells | real holds | null holds (11 / 23 / 37) | median ulcer change HOLD | median ulcer change L6M | planted +0.25 R |
|--|--|--|--|--|--|--|
| atr_terc | 15 | 3 | 1 / 1 / 0 | +1% | +5% |  |
| atr_live | 14 | 2 | 4 / 3 / 1 | +14% | +9% |  |
| vote | 13 | 1 | 2 / 4 / 0 | +14% | +0% | 6 / 13 |
| er60 | 15 | 2 | 2 / 0 / 0 | +7% | +2% |  |
| range_used | 15 | 0 | 1 / 0 / 2 | +2% | +19% |  |
| roomOWN | 15 | 1 | 3 / 1 / 1 | +9% | +1% |  |
| roomUW | 15 | 1 | 0 / 1 / 2 | -1% | +7% |  |
| fresh | 15 | 2 | 1 / 1 / 4 | -2% | +20% |  |
| uwscore | 14 | 0 | 1 / 0 / 0 | +14% | +1% |  |
| nonsense0 | 15 | 1 | - | +10% | +14% |  |
| nonsense1 | 15 | 0 | - | +13% | +25% |  |
| nonsense2 | 15 | 0 | - | +8% | +13% |  |

Cells that hold (real, untouched; $/wk at x1.75):
| dimension | cell | buckets (multiplier) | ulcer HOLD / L6M | mean $/wk change HOLD / L6M |
|--|--|--|--|--|
| atr_live | H7 Asia | lt1.3:1.50;gt1.6:0.50 | -2% / -29% | 364 / 1685 |
| atr_live | P7 NY AM | 1.3-1.6:1.50;gt1.6:0.50 | -6% / -6% | 1526 / 2689 |
| atr_terc | K7 NY AM | t2:1.50;t3:0.50 | -20% / -22% | 776 / 976 |
| atr_terc | M7 NY AM | t3:1.50;t2:0.50 | -14% / -36% | -26 / 545 |
| atr_terc | P7 Asia | t3:1.50;t1:1.00;t2:0.50 | -13% / -19% | 249 / 6122 |
| er60 | K7 NY PM | t3:1.50;t2:1.00;t1:0.50 | -17% / -14% | 1437 / 256 |
| er60 | P7 NY AM | t3:1.50;t2:1.00;t1:0.50 | -25% / -24% | 4163 / 1897 |
| fresh | K7 NY AM | other:1.50;rechase:1.00;fresh:0.50 | -8% / -5% | 127 / 370 |
| fresh | M7 NY AM | other:1.50;rechase:1.00;fresh:0.50 | -10% / -1% | 3 / 197 |
| roomOWN | K7 London | 30-60:1.50;lt30:1.00;gt60:0.50 | -12% / -36% | 647 / 1349 |
| roomUW | P7 NY AM | lt30:1.50;30-60:1.00;gt60:0.50 | -14% / -25% | 1074 / 823 |
| vote | K7 NY PM | with:1.50;mixed:0.50 | -6% / -16% | 352 / 520 |

Reading: a positive median ulcer change on the untouched windows means the tilt made drawdown WORSE out of sample; the real count of holding cells is at or below the shifted-label null for every dimension. A signal too weak to skip on is also too weak to size on at this resolution. Nothing goes to the engine.

## 3. Own-book walls as targets and exits
- What the box has: the per-second mbp-10 state days (2023-04..2026-11) see only the first 10 price levels = 2.25 pts from the touch (median, p10-p90 2.25-2.75; p99 about 37), so a wall within 60 pts cannot be seen in them. Full-depth order-by-order data (MBO) is on the box for the whole of 2023-04..2026-10 (about 190 GB, daily files); per-second wall features (nearest resting order >= 8 lots per side: distance, size, age; large cancels) exist for L6M (158 files). A background extractor (3 workers, nice 15, 11 s per day, STOP file /mnt/l2/l2vast/_major_d/mbo_feat/STOP) is producing the same features for older days, newest first (HOLD months first): 973 of about 965 older days done at 2026-11-17 19:07Z. The scoring (md8_walls.py) automatically switches from split-half to walk-forward (SEL = older days up to 2025-10, HOLD, L6M) once there are at least 4 older months covered.
- Wall definition: the "3x/5x/10x the normal level" cannot be applied to a single order feature; absolute order size is used instead (NQ p99 order = 1 lot, so >= 8 / 16 / 32 lots = 8x / 16x / 32x), age >= 30 s or 120 s, within 60 pts ahead. W1 = target 1 pt in front of the wall (floor 8 pts) when nearer than native. W2 = the trade leans on an own-side order >= 8 or 16 lots within 10 pts and aged >= 30 s; exit next second at the mid - 0.5 when a large own-side cancel occurs and the nearest large order moves >= 2 ticks away.
**Table 3a - what the rules do on the covered span (descriptive; $ at x1.75)**
| rule | fired | covered trades | mean $ per fired trade | total $ change |
|--|--|--|--|--|
| W1 size>=8 age>=30s | 10951 | 19738 | -110 | -1207221 |
| W1 size>=8 age>=120s | 8839 | 19738 | -138 | -1219429 |
| W1 size>=16 age>=30s | 2452 | 19738 | -299 | -732074 |
| W1 size>=16 age>=120s | 2015 | 19738 | -404 | -813162 |
| W1 size>=32 age>=30s | 658 | 19738 | -386 | -253720 |
| W1 size>=32 age>=120s | 552 | 19738 | -426 | -235293 |
| W2 lean>=8 | 2732 | 19738 | -455 | -1244305 |
| W2 lean>=16 | 641 | 19738 | -821 | -526519 |

**Table 3b - walk selection and null on the covered span (pooled books, groups ALL + 4 sessions)**
| rule | mode | groups | real: picks / holds | null mean picks / holds |
|--|--|--|--|--|
| W1 | walk-forward (sampled older days) | 5 | 2 / 0 | 3.7 / 0.3 |
| W2 | walk-forward (sampled older days) | 5 | 0 / 0 | 0.7 / 0.0 |

Reading (covered span only, FIRST PASS): a target placed in front of a resting wall fires on 4-60% of the covered trades (more for the smaller wall class) and loses money on average per fired trade (the native 60-pt target is reached through the wall on many of them), and exiting when a leaned-on wall is pulled costs more than it saves. No rule holds on the covered span. The older-days walk-forward will replace this paragraph.

## Summary table (one row per rule; "where it holds" = book x session cells holding untouched on both HOLD and L6M; ulcer and mean change are for the holding cells only, median ulcer / summed $/wk at x1.75; null = holding picks under the shifted-label procedure, mean of 3)
| rule | where it holds | ulcer change HOLD / L6M | mean $/wk change HOLD / L6M | real holds of picks; null | feed it needs |
|--|--|--|--|--|--|
| T1 target at nearest UW level minus 10/5/0 pts (all UW levels) | H7 Asia | -46% / -33% | 1132 / 2442 | 1 of 5 real; null mean 0.3 | UW gex-levels (oi+vol) NDX+SPX, oi-per-strike (max-pain/top OI), spot at the 16:15 ET snapshot; daily, Advanced tier |
| T2 target at UW gamma level (NDX+SPX walls/flip/magnet) minus buffer | H7 Asia, P7 NY AM | -23% / -25% | 2968 / 4280 | 2 of 5 real; null mean 0.7 | UW gex-levels daily (NDX, SPX), Advanced tier |
| S1 stop to breakeven (or -20) after rejection from a UW level | H7 Asia | -47% / -24% | 2004 / 1421 | 1 of 1 real; null mean 0.0 | UW gex-levels daily + own 1-s price |
| T3 target at own free zones (prior-day H/L/C/POC/VAH/VAL, Globex H/L) | K7 NY PM | -40% / -63% | 1912 / 732 | 1 of 4 real; null mean 1.7 | none (own bars) |
| T4 target at 250-pt round numbers | H7 Asia, M7 London, P7 London | -42% / -9% | 2815 / 4613 | 3 of 6 real; null mean 2.3 | none |
| T5 target at 100-pt round numbers | nowhere | - / - | - / - | 0 of 5 real; null mean 0.3 | none |
| T0 best fixed nearer target (15..50), no level | nowhere | - / - | - / - | 0 of 9 real; null mean 0.0 | none |
| Z atr_terc size x0.5/x1/x1.5 (exposure neutral) | K7 NY AM, M7 NY AM, P7 Asia | -14% / -22% | 1000 / 7643 | 3 of 15 cells; null 1/1/0 | own bars |
| Z atr_live size x0.5/x1/x1.5 (exposure neutral) | H7 Asia, P7 NY AM | -4% / -18% | 1890 / 4374 | 2 of 14 cells; null 4/3/1 | own bars (DS7 atr_rel) |
| Z vote size x0.5/x1/x1.5 (exposure neutral) | K7 NY PM | -6% / -16% | 352 / 520 | 1 of 13 cells; null 2/4/0 | own bars |
| Z er60 size x0.5/x1/x1.5 (exposure neutral) | K7 NY PM, P7 NY AM | -21% / -19% | 5601 / 2153 | 2 of 15 cells; null 2/0/0 | own bars |
| Z range_used size x0.5/x1/x1.5 (exposure neutral) | nowhere | - / - | - / - | 0 of 15 cells; null 1/0/2 | own bars + HAR forecast |
| Z roomOWN size x0.5/x1/x1.5 (exposure neutral) | K7 London | -12% / -36% | 647 / 1349 | 1 of 15 cells; null 3/1/1 | own bars |
| Z roomUW size x0.5/x1/x1.5 (exposure neutral) | P7 NY AM | -14% / -25% | 1074 / 823 | 1 of 15 cells; null 0/1/2 | UW gex-levels daily |
| Z fresh size x0.5/x1/x1.5 (exposure neutral) | K7 NY AM, M7 NY AM | -9% / -3% | 130 / 567 | 2 of 15 cells; null 1/1/4 | D7 own trade log |
| Z uwscore size x0.5/x1/x1.5 (exposure neutral) | nowhere | - / - | - / - | 0 of 14 cells; null 1/0/0 | UW family-7 columns (gamma, walls, flows; Advanced tier) |
| W1 target in front of a resting >=8-lot order within 60 pts | covered span only | see section | see section | 0 / 2 real; null 0.3 | MBO / full-depth book (CQG 20 levels may see only part; MBO feed for exact sizes/ages) |
| W2 exit when the wall the trade leans on is pulled | covered span only | see section | see section | 0 / 0 real; null 0.0 | MBO / full-depth book (CQG 20 levels may see only part; MBO feed for exact sizes/ages) |

### Engine (exact, raw chassis, base lots, $4.84; written 2026-11-17 19:01Z by md_eng_loop)
- Identity (hook present and inert = TL3_RB_S0 trade for trade, 202610 and 202504, H7 and K7): PASSED
| cell | HOLD ulcer / mean $/wk (x1.75) | L6M ulcer / mean $/wk (x1.75) | holds | controls at least as good (of 30) HOLD / L6M |
|--|--|--|--|--|
| H7_TUW10 | -40% / +1623 | -24% / -155 | no | not queued (does not hold on the engine) |
| H7_SUWBE | -22% / +860 | -13% / -920 | no | not queued (does not hold on the engine) |
| K7_TUWN10 | -11% / +635 | +15% / +593 | no | not queued (does not hold on the engine) |
- identity PASSED
- H7_TUW10 real evaluated: holds=False {"HOLD": [-0.401, 927.4], "L6M": [-0.24, -88.3]}
- H7_SUWBE real evaluated: holds=False {"HOLD": [-0.217, 491.3], "L6M": [-0.132, -526.0]}
- K7_TUWN10 real evaluated: holds=False {"HOLD": [-0.11, 362.6], "L6M": [0.145, 338.8]}

Engine status above (if any). Assembly: Candidates for exact engine + 30 persistent random-target controls: H7 Asia T_UW b10 (and S_UW BE), K7 NY PM T_UWN b10. The queue line for MD engine cells is inserted in /mnt/l2/l2vast/_s2/QUEUES.txt before the stage 3 line (after the B/F position); identity cells are queued first; the real cells are queued after identity passes; controls only for cells that hold on the engine (unattended: code/th_md_eng/md_eng_loop.py).

Files: /mnt/l2/l2vast/_major_d/md/ (md_base.parquet rooms and buckets, md_rules*.parquet replay deltas, md5_cells*.csv, md6_*.csv, md7_size*.csv, md8_*.csv); code code/th_md/ (md1_prep, md2_uw, md3_base, md4_replay, md5_score, md6_shape, md7_size, md8_walls, md8_extract, md9_page, md_loop.sh).
<!-- W-MD section end -->
