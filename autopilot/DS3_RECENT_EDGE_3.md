# DS3_RECENT_EDGE_3 - T-RECENT-EDGE section 5, re-examination cycles (RE-3). Data to label day 20260206. Written 2026-10-31

Companions: DS3_RECENT_EDGE_FINAL.md (RE-2, first pass), DS3_PERSISTENCE.md (RE-1), DS3_EDGE_MONITOR.md, DS3_RECENT_PORTFOLIO.md. Prereg `l2vast/ds3/prereg/RE3_prereg.md` sha256 bff8afc8504d27339482794110aa001875be7b7e49e061e3815b1f9c23337377 (logged in autopilot/DECISIONS.md before scoring). Code `l2vast/ds3/code/recentedge3/`, outputs `l2vast/ds3/out/recentedge3/`. Masks capped 20260206; UNTOUCHED never read (the 2026-02 depth month and every post-cut table were not loaded). Research only; page is a view; value = shrunk expectation.

## PAGE 1 - the plain answers

**Null result up front.** Fitting every main family only on its last 6 months and trading the winner for the next month, rolled through 2024-01..2026-01 (25 decisions), earns nothing that beats a noise chain: no family clears both its minimum detectable effect (MDE) and the 95th percentile of the time-shuffled twin (the same chain run on a randomly re-ordered calendar). The chain beats a RANDOM rule of the family in most families (not in C2 G1-G4), but that only says the average rule loses; the selection itself adds no skill.

1. **(a) Pure recent-fit chain, every family.** Per planned lot / per fire / per contract / lock-engine stack, with 2,000 random-rule chains and 300 time-shuffled twins per family (table A). Largest numbers: L2SET-joint stack line +13.3k $/wk at one research lot (MDE ~19k, twin 95th 57k/month vs 58k real: rank 0.96, null); EINT1 trend/ER entry-filter family +2,918 pts/month per planned lot summed over the 10 book streams (1.93 pts per base trade, 2.20 per fire; MDE 4,440, twin mean +1,697, rank 0.87, null); 70% take/tighten +412 pts/month (MDE 600, rank 0.78); UF-loss exits +536 (MDE 1,150, rank 0.83). Confirmation (CF-ENG, C2 G1-G5), BARS-ENG and L2SE entry chains are NEGATIVE (-0.07 to -1.1 pts per base trade) and rank at or below their twins (C2 G3/G4 rank 0.02/0.03: the chain is WORSE than noise). On the lock-engine stack (engine multiplier route for every size/skip rule, S73 base): first-stop cut family chain +2,930 research $/wk (+1,247 at live lots; MDE 10.4k; twin 95th 4.7k; fixed cell chosen on the first nine months +5.1k), same-side cap +1,872 (+796 live; MDE 6.1k; rank 0.94), trend ER +/-sizer -2,065, skip-after-loser/first-60 -3,149, book/session on-off-size +523, first-target mirror -15,155; all bank rules pooled -4,578. Nothing is above MDE; the positive chains are what the first-stop family earns in its good half-years, not skill in picking it.
2. **(b) What 2025-26 is, corrected.** RE-2 wrote that 5-minute vol and signals per day doubled. Signals per day did double inside every book (41 to 82; every one of the 10 books is up 1.2-2.0x, so it is not a book-mix effect), but the NQ index level rose 47% (17.9k to 26.3k, so a point is worth less) and percentage volatility is up only 8-22% (daily 5-min realised vol 0.945% in 23H1, peak 1.152% in 25H1, 1.016% in 25H2). The sig_rv_5m doubling is mostly a points-per-index-level effect. What did change materially: (i) the book is thinner - median depth within 10 levels 114-129 contracts in 2023 to 76 in 25H2 (-35%), cumulative size ahead of a limit 57-65 to 38, spread measure 2.1-2.2 to 3.0; (ii) the store's per-trade fill cost 1.2 pts in 2023 to 2.7 pts in 25H2 (2.2x); (iii) ES-NQ 20-minute correlation 0.86 to 0.93; (iv) London share 16% to 22%, NY-PM 21% to 17%; (v) a FIXED 60-point bracket is now 14% of the mean daily range (27% in 23H1) and 0.23% of price (0.34%): the same brackets are half as wide relative to the market, which is why the signal rate doubled. Trend persistence did NOT rise (daily NQ ER 0.081 to 0.073; lag-1 5-minute return autocorrelation -0.006 to -0.001; 30m/5m variance ratio 1.00 to 1.00; Hurst 0.58 flat). Section B has the table.
3. **What each ledger edge bets on (table B2).** For the 69 ON bank edges (cluster-board reps of 2026-02-06) the weekly Spearman correlation of the edge's stack delta with the weekly regime state is about zero on average (range 5-min vol -0.01, daily range -0.02, ER -0.07, ES-NQ corr -0.01, signals/day +0.01, London share -0.00, depth +0.02, fill cost -0.03); a regression of each edge on range and correlation fitted before 2025-10 predicts its 2025-10..2026-02 gain with correlation -0.17. So the edges do NOT load on any measured weekly regime variable; they are a bet that the 2025-26 STATE as a whole (thin book, high fill cost, 60-pt brackets at half relative width, correlated indices) persists, and the half-year library (below) shows that families flip together between such states.
4. **(c) Regime library.** Every ON (L3M>0 and L6M>0) RE-1 pooled series (12242 rules) scored in six half-year regimes. Only 47 are positive in all six; 0.0-7% of any family's ON rules are positive in all five earlier regimes. Whole families move together: 70% take/tighten ON rules were positive in 99% of cases in 23H1, 3% in 23H2, 6% in 24H1, 37% in 24H2, 96% in 25H1; L2SE dip-entry 88% / 8% / 8% / 22% / 99%; EINT2 day-type 73% / 79% / 17% / 21% / 72%. A rule positive in a half-year was positive in the next one 19%/29%/19%/63%/60% of the time against an unconditional 19%/22%/17%/47%/42%: the lift (+7, +2, +16, +18 points) exists only for the two most recent transitions and is a regime effect shared by the whole family, not rule-specific persistence (the 13-week test of DS3_PERSISTENCE.md, where 'positive last 3 and 6 months' persists 41% vs 50%, stands).
5. **(d) The top-30 'stronger evidence' rows.** The ledger column z6 is a PROFILE PROXY (z3 x sqrt 2, no monthly series), not a measured 6-month t. Of the 30 largest distinct streams with z6>=3 (collapsed by program and book from 2,978 rows, 162 streams), only 9 have a stored capped monthly series I could re-read; their real 6-month t is >=3 in 3, and only 0 reach CONFIRMED-RECENT (none: both L2SP profit rows are on the M basis whose target-fill correction is unverified). Status counts: {'UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2)': 17, 'RECENT, weak t': 4, 'RECENT-ONLY': 3, 'UNIT-INFLATED (structure)': 2, 'VOID (look-ahead)': 2, 'RECENT + PRE/X positive, M-basis unverified (shadow)': 2}. Details in section D.
6. **(e) Monitor refresh.** Not done by design: the library tables run to 2026-10-30 but the research masks stay capped at 20260206 and post-cut data was not read, so the board is still the 2026-02-06 board of DS3_EDGE_MONITOR.md. No claim is made about the edges since.
7. **Ledger columns.** RECENT_WINS.md gains two columns (REGIME LIBRARY 23H1..25H2 as +/- per half-year, and RE-3 RE-READ for the top-30 rows); edits are guarded (backups `*.bak_pre_re3_20261031`), the compiler ran clean. Coverage: library string on 2,329 ledger rows (stored monthly series or bank regime library), re-read status on 94 rows (30 distinct streams).

Recommendation per bet (unchanged by this page): shadow all recent-only edges; the one 'run at 25% size' item of RE-2 (first-stop cut when a book is open on the other side) stays the only candidate; none sized above 25%.

## A. Pure recent-fit chain (fit = last 6 calendar months, test = next month, 2024-01..2026-01)

Method (prereg): per family, eligible rules (>=30 fires in the fit window, 6 finite months), pick the highest 6-month sum, hold for one month; variants top-1, top-5 mean, top-1-if-also-positive-in-last-3-months at half size. Units: pts per planned lot (RE-1 series: S summed over the month; per base trade = sum S / base trades; per fire; per final contract = S/L where L is stored (only EINT1 stores final lots; elsewhere L = fires); dollars = pts x $20 / 4.35 weeks at ONE planned lot per stream, pooled rows add the 10 book streams). Stack rows are lock-engine deltas (RE-2 bank, 163 unique rules per base; ER sizers, book/session size and skip rules entered through the engine multiplier route, not by scaling points); live lots = research / 2.35. Placebos: random chain = a random eligible rule each month (2,000 draws); twin = same chain on a common random permutation of the 34 months (150-300 draws), which preserves the cross-rule structure and destroys time structure, so twin vs real is the value of recency itself. Decision rule: a chain is 'something' only if mean > MDE and > twin 95th.

### A1. RE-1 per-trade families, pooled scope (top-1 variant)
| family | n_rules | pts/month (1 lot/stream) | MDE | $/wk at 1 lot | months +/- | per base trade | per fire | random-rule chain mean | rank vs random | time-shuffled twin mean | twin 95th | rank vs twin |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| exit: 70% take/tighten (L2SET profit) | 23,773 | 412 | 600 | 1,896 | 18/7 | 0.29 | 0.89 | -238 | 1.00 | 224 | 604 | 0.78 |
| exit: loss rules (UF loss) | 2,380 | 536 | 1,150 | 2,466 | 12/13 | 0.37 | 1.40 | -180 | 1.00 | 289 | 700 | 0.83 |
| confirmation: CF-ENG stage 1 | 560 | -371 | 391 | -1,705 | 9/16 | -0.26 | -0.39 | -445 | 0.72 | -234 | -22.29 | 0.14 |
| confirmation: C2 G1 | 2,820 | -845 | 933 | -3,883 | 7/18 | -0.59 | -0.78 | -662 | 0.24 | -582 | -122 | 0.18 |
| confirmation: C2 G2 | 2,368 | -1,444 | 1,251 | -6,640 | 6/19 | -1.01 | -1.45 | -1,376 | 0.42 | -947 | -403 | 0.06 |
| confirmation: C2 G3 | 2,256 | -1,590 | 1,163 | -7,311 | 6/19 | -1.11 | -1.69 | -1,257 | 0.15 | -825 | -278 | 0.02 |
| confirmation: C2 G4 | 1,824 | -1,389 | 1,239 | -6,386 | 5/20 | -0.97 | -1.49 | -863 | 0.04 | -767 | -144 | 0.03 |
| confirmation: C2 G5 | 684 | -458 | 960 | -2,107 | 10/15 | -0.32 | -0.40 | -1,071 | 0.98 | -447 | 31.38 | 0.50 |
| entry structure: BARS-ENG | 7,165 | -286 | 592 | -1,313 | 9/16 |  | -1.71 | -331 | 0.58 | -201 | 94.19 | 0.31 |
| entry filter/sizing: EINT1 trend ER | 389 | 2,918 | 4,440 | 13,416 | 17/8 | 1.93 | 2.20 | 34.97 | 1.00 | 1,697 | 3,416 | 0.87 |
| entry structure: L2SE dip entry | 4,251 | -98.37 | 1,306 | -452 | 14/11 | -0.07 | -0.13 | -535 | 0.92 | -144 | 403 | 0.56 |
| regime: EINT2 day-type (stack $/day) | 4,950 | -38,358 | 122,720 | -8,818 | 11/14 | -1,760 | -1,782 | -2,034 | 0.00 | -82,606 | -9,379 | 0.84 |
| sizing: SPLIT-2 (stack $/day) | 63 | -10,534 | 47,314 | -2,422 | 9/16 | -483 | -490 | -26,987 | 0.86 | -22,828 | -251 | 0.77 |
| stack: L2SET-joint ($/day) | 72 | 57,928 | 84,204 | 13,317 | 16/9 | 2,657 | 2,707 | -34,136 | 1.00 | 21,540 | 57,289 | 0.96 |

### A2. Per live book (scope = one book; top-1; highest twin rank first; live lots KB 2, PE 7, SM 4, HM 3 (4 Asia / 2 NY-AM), MV 2, PB 1)
| source | scope | live_lots | mean_month | mde | pos | neg | rank_rand | rank_perm | per_fire | $/wk at live lots |
|---|---|---|---|---|---|---|---|---|---|---|
| H9_entry | SM | 4 | 30.16 | 241 | 11 | 14 | 0.97 | 0.93 | 0.75 | 555 |
| H4_c2G1 | HM | 3 | -32.96 | 175 | 11 | 14 | 0.91 | 0.90 | -0.34 | -455 |
| H9_entry | PB | 1 | 18.40 | 228 | 12 | 13 | 0.80 | 0.82 | 0.21 | 84.59 |
| H4_c2G1 | PE | 7 | 29.67 | 200 | 12 | 13 | 0.83 | 0.81 | 0.25 | 955 |
| H4_c2G4 | HM | 3 | -117 | 263 | 10 | 15 | 0.59 | 0.75 | -1.66 | -1,613 |
| H1_profit | PB | 1 | 41.03 | 217 | 11 | 14 | 0.64 | 0.73 | 0.59 | 189 |
| H9_entry | KB | 2 | -1.43 | 217 | 12 | 13 | 0.70 | 0.71 | -0.01 | -13.17 |
| H1_profit | SM | 4 | -2.34 | 109 | 13 | 12 | 0.79 | 0.71 | -0.10 | -43.04 |
| H4_c2G4 | PE | 7 | -23.10 | 262 | 12 | 13 | 0.62 | 0.70 | -0.21 | -744 |
| H2_loss | KB | 2 | -12.58 | 200 | 13 | 12 | 0.73 | 0.68 | -0.23 | -116 |
| H9_entry | PE | 7 | -14.55 | 261 | 14 | 11 | 0.56 | 0.56 | -0.12 | -468 |
| H9_entry | HM | 3 | -79.59 | 286 | 11 | 14 | 0.57 | 0.56 | -0.88 | -1,098 |
| H2_loss | PE | 7 | -8.88 | 179 | 11 | 14 | 0.46 | 0.54 | -0.21 | -286 |
| H3_cfeng | HM | 3 | -41.19 | 75.58 | 7 | 18 | 0.81 | 0.51 | -0.56 | -568 |
| H2_loss | HM | 3 | 9.02 | 145 | 15 | 10 | 0.45 | 0.47 | 0.17 | 124 |
| H4_c2G1 | MV | 2 | -53.25 | 267 | 13 | 12 | 0.53 | 0.44 | -0.41 | -490 |
| H4_c2G4 | PB | 1 | -53.72 | 238 | 14 | 11 | 0.55 | 0.42 | -0.68 | -247 |
| H3_cfeng | PE | 7 | -39.06 | 118 | 8 | 17 | 0.48 | 0.37 | -0.36 | -1,257 |
| H3_cfeng | KB | 2 | -29.97 | 115 | 12 | 13 | 0.58 | 0.37 | -0.25 | -276 |
| H1_profit | KB | 2 | -62.54 | 235 | 10 | 15 | 0.78 | 0.34 | -1.04 | -575 |
| H2_loss | PB | 1 | -22.68 | 219 | 12 | 13 | 0.13 | 0.28 | -0.39 | -104 |
| H4_c2G4 | KB | 2 | -88.30 | 291 | 9 | 16 | 0.44 | 0.24 | -0.84 | -812 |
| H1_profit | MV | 2 | 3.68 | 160 | 12 | 13 | 0.52 | 0.23 | 0.05 | 33.82 |
| H3_cfeng | MV | 2 | -42.15 | 128 | 9 | 16 | 0.38 | 0.20 | -0.37 | -388 |

Reading: the best twin rank in any live-book chain is 0.93 (L2SE entry on SM, +30 pts/month = +555 $/wk at 4 lots against an MDE of 241 pts/month: a coin-flip cell out of 60+). No book chain is above its MDE.

### A3. Lock-engine stack chains (research lots; S73 base; MKT-base file in `chain_stack.csv`)
| family | variant | n_rules | research_per_wk | live_per_wk | mde_research | months_pos | months_neg | rand_mean | rand_p95 | rank_rand | perm_mean | perm_p95 | rank_perm | L6M_research | first9m_fixed_cell |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| first-stop cut (A1-A3,D,E) | top1 | 59 | 2,930 | 1,247 | 10,400 | 15 | 10 | -3,108 | 2,122 | 0.97 | -302 | 4,662 | 0.86 | 8,778 | 5,147 |
| first-stop cut (A1-A3,D,E) | top3 | 59 | 1,095 | 466 | 8,037 | 11 | 14 | -3,141 | 1,927 | 0.91 | -704 | 2,677 | 0.79 | 7,493 | 5,147 |
| first-stop cut (A1-A3,D,E) | top1_on3_half | 59 | 601 | 256 | 5,016 | 10 | 10 | -2,969 | 2,219 | 0.86 | -242 | 1,967 | 0.71 | 2,266 | 5,147 |
| same-side cap (B) | top1 | 48 | 1,872 | 796 | 6,085 | 13 | 11 | -7,644 | -1,184 | 0.99 | -1,831 | 2,059 | 0.94 | 1,235 | 609 |
| same-side cap (B) | top3 | 48 | 1,807 | 769 | 5,318 | 14 | 11 | -7,843 | -914 | 0.99 | -759 | 2,302 | 0.91 | 3,497 | 609 |
| same-side cap (B) | top1_on3_half | 48 | 678 | 289 | 2,895 | 12 | 9 | -7,664 | -1,333 | 0.99 | -772 | 1,099 | 0.90 | -875 | 609 |
| first-target mirror (C) | top1 | 6 | -15,155 | -6,449 | 10,836 | 5 | 20 | -17,536 | -14,500 | 0.90 | -12,961 | -8,499 | 0.19 | -3,133 | -22,155 |
| first-target mirror (C) | top3 | 6 | -15,802 | -6,724 | 12,008 | 5 | 20 | -17,608 | -14,372 | 0.82 | -14,084 | -10,079 | 0.22 | -1,568 | -22,155 |
| first-target mirror (C) | top1_on3_half | 6 | 0.00 | 0.00 | 0.00 | 0 | 0 | -17,632 | -14,487 | 1.00 | -620 | 0.00 | 0.70 | 0.00 | -22,155 |
| trend ER sizer/gate (engine mult) | top1 | 10 | -2,065 | -879 | 24,830 | 11 | 14 | -22,048 | -9,579 | 1.00 | -7,298 | 2,260 | 0.80 | 3,056 | -1,906 |
| trend ER sizer/gate (engine mult) | top3 | 10 | -6,909 | -2,940 | 21,300 | 11 | 14 | -21,913 | -8,621 | 0.97 | -6,375 | 1,366 | 0.46 | 488 | -1,906 |
| trend ER sizer/gate (engine mult) | top1_on3_half | 10 | -1,724 | -734 | 6,269 | 4 | 5 | -22,290 | -9,105 | 1.00 | -1,739 | 2,150 | 0.50 | -5,399 | -1,906 |
| skip-after-loser / first-60 skips (engine mult) | top1 | 10 | -3,149 | -1,340 | 10,823 | 9 | 16 | -13,816 | -4,765 | 0.98 | -8,132 | 107 | 0.83 | 4,560 | -18,493 |
| skip-after-loser / first-60 skips (engine mult) | top3 | 10 | -8,762 | -3,729 | 9,747 | 4 | 21 | -13,876 | -4,735 | 0.82 | -7,104 | -2,238 | 0.25 | -6,344 | -18,493 |
| skip-after-loser / first-60 skips (engine mult) | top1_on3_half | 10 | -935 | -398 | 2,666 | 4 | 7 | -13,758 | -5,045 | 0.99 | -2,682 | 323 | 0.84 | 0.00 | -18,493 |
| book/session on-off-size (engine mult) | top1 | 30 | 523 | 223 | 8,932 | 14 | 11 | -6,413 | -585 | 0.97 | -3,228 | 2,617 | 0.87 | -887 | 2,545 |
| book/session on-off-size (engine mult) | top3 | 30 | -3,528 | -1,501 | 6,058 | 9 | 16 | -6,509 | -414 | 0.80 | -2,962 | 1.93 | 0.38 | -1,785 | 2,545 |
| book/session on-off-size (engine mult) | top1_on3_half | 30 | 741 | 315 | 4,237 | 13 | 10 | -6,538 | -609 | 0.98 | -1,331 | 1,062 | 0.90 | -444 | 2,545 |
| ALL bank rules | top1 | 163 | -4,578 | -1,948 | 10,064 | 12 | 13 | -7,400 | -98.69 | 0.71 | -4,800 | 2,824 | 0.54 | -13,295 | -18,493 |
| ALL bank rules | top3 | 163 | -4,685 | -1,994 | 6,812 | 7 | 18 | -7,363 | 175 | 0.70 | -4,440 | 653 | 0.48 | -7,092 | -18,493 |
| ALL bank rules | top1_on3_half | 163 | -2,125 | -904 | 4,654 | 8 | 12 | -7,351 | -35.45 | 0.88 | -2,074 | 2,376 | 0.50 | -6,648 | -18,493 |

Reading: the 'rank vs random' column is ~1.0 for most rows only because the average random cell in these families loses 3-22k/wk; the twin column is the honest comparison. Top-1 first-stop chain 2.9k vs twin 95th 4.7k; same-side cap 1.9k vs 2.1k. 'First9m fixed cell' (one cell chosen on 2023-04..2023-12 and held) earns +5.1k for the first-stop family, more than the chain: a cheaper, equally uninformative rule.

Trials added: 14 sources x up to 8 scopes x 3 variants of chains plus 2 bases x 7 families x 3 variants of stack chains (about 450 chain readings, 2,000 random and 150-300 twin draws each); no new strategy cells were scored. UF_TRIALS/DEAD_CELLS were not appended (no new rule cells).

## B. The regime of 2025-26 versus 2023-24, deepened

Sources: trend/flow store at the signal second (44k signals, 10 books), NQ 1-minute bars (daily range, realised vol, efficiency ratio, autocorrelation, variance ratio, volume), dp1m book features at the signal second (depth10 = contracts within 10 levels, cum_ahead10 = size queued ahead, spread; months to 2026-01 only), the store's per-trade fill cost, stop-exit share. Half-years: 23H1 Apr-Sep 2023 ... 25H2 Oct 2025-Feb 6 2026 (depth through Jan 2026).

| measure | 23H1 | 23H2 | 24H1 | 24H2 | 25H1 | 25H2 |
|---|---|---|---|---|---|---|
| signals_per_day | 42.21 | 42.38 | 61.08 | 69.38 | 71.60 | 81.58 |
| NQ_daily_range_pts | 228 | 239 | 331 | 374 | 397 | 431 |
| NQ_rv5_daily_% | 0.94 | 0.89 | 1.07 | 1.10 | 1.15 | 1.02 |
| NQ_day_ER_5m | 0.08 | 0.08 | 0.08 | 0.08 | 0.07 | 0.07 |
| NQ_5m_ret_autocorr | -0.01 | -0.02 | -0.02 | -0.02 | -0.00 | -0.00 |
| NQ_VR6_30m_over_5m | 1.00 | 0.98 | 0.96 | 1.00 | 1.01 | 1.00 |
| NQ_volume_per_day | 589,302 | 616,929 | 582,318 | 532,990 | 502,420 | 543,675 |
| sig_rv_5m | 12.61 | 13.52 | 19.53 | 21.63 | 25.84 | 23.94 |
| 5m.er20 | 0.28 | 0.28 | 0.27 | 0.26 | 0.26 | 0.26 |
| 5m.hurst100 | 0.58 | 0.58 | 0.58 | 0.58 | 0.57 | 0.58 |
| sig_esnq_corr20m | 0.86 | 0.87 | 0.90 | 0.91 | 0.93 | 0.93 |
| abs_imb10 | 0.11 | 0.13 | 0.13 | 0.12 | 0.12 | 0.11 |
| sig_intens_rel | 1.94 | 1.93 | 2.03 | 1.98 | 1.95 | 2.09 |
| share_asia | 0.26 | 0.25 | 0.25 | 0.24 | 0.28 | 0.28 |
| share_london | 0.16 | 0.17 | 0.19 | 0.21 | 0.23 | 0.22 |
| share_pre | 0.06 | 0.07 | 0.07 | 0.06 | 0.05 | 0.05 |
| share_nyam | 0.31 | 0.28 | 0.28 | 0.28 | 0.25 | 0.28 |
| share_nypm | 0.21 | 0.22 | 0.20 | 0.20 | 0.18 | 0.17 |
| fill_cost_pts_mean | 1.19 | 1.23 | 1.26 | 2.10 | 2.64 | 2.72 |
| stop_exit_share | 0.44 | 0.42 | 0.45 | 0.44 | 0.45 | 0.44 |
| depth10_median | 114 | 129 | 99.00 | 87.00 | 78.00 | 76.00 |
| spread_mean | 2.22 | 2.10 | 2.79 | 2.98 | 2.99 | 2.98 |
| cum_ahead10_median | 57.00 | 65.00 | 49.00 | 43.00 | 39.00 | 38.00 |

Additional facts: NQ mean entry level by half 17,928 / 19,472 / 21,379 / 22,651 / 22,661 / 26,291; a 60-point bracket as a share of the mean daily range 0.268 / 0.251 / 0.181 / 0.161 / 0.151 / 0.139; signals per day by book 23H1 -> 25H2: WT 7.2 -> 14.3, KB 4.7 -> 10.6, ST 4.6 -> 10.6, PE 4.7 -> 10.2, MV 4.6 -> 9.6, HM 4.0 -> 7.5, PB 3.8 -> 7.1, DN 3.4 -> 5.8, MA 2.5 -> 3.2, SM 2.0 -> 2.4 (SM, the slowest bar book, barely moves). Stop-exit share is flat (0.44-0.45): a stop is hit as often as before, so the doubled signal rate is more trades with the same win/stop mix, each at a larger per-trade fill cost.

In words: running a recent edge means betting on a market where (1) the book is about a third thinner and fills cost 2x, (2) the same fixed bracket is about half as wide relative to the day, so the strategy trades twice as often, (3) NQ and ES move together more, (4) London matters more, and (5) none of this is more trending per bar. If the state reverts (price level, depth), the 2023 half of the library is the guide, and in it these edges were flat or negative.

### B2. What each ledger edge loads on
Method: weekly stack delta of each of the 69 ON bank cluster representatives (2023-04..2026-01) against the weekly regime frame (`regime_weekly.csv`); Spearman rho, mean delta by tercile of range/rv5/depth, and a two-variable regression fitted to weeks before 2025-10 and used to predict 2025-10 onward. Summary of rho: mean {'rho_rv5': -0.012, 'rho_rng': -0.016, 'rho_er5': -0.067, 'rho_corr': -0.008, 'rho_sig_day': 0.005, 'rho_london': -0.002, 'rho_depth10': 0.024, 'rho_fill': -0.029}. 37 of 69 edges earn more in the high-range tercile than the low one (54%); 49% have a positive mean over the 2023-04..2024-03 weeks (the 'if 2023 returns' weeks). Per-edge numbers: `edge_regime_bets.csv`. Largest loadings are weak (max |rho| 0.27, with ER; book WT x1.5 +0.22 with range and ES-NQ correlation, session pre x0.5 -0.18 with range), so no edge here is a clean vol bet.

## C. Regime library (six half-year regimes, every ON series)

ON = positive in L3M (2025-11..2026-01) and L6M and >=20 fires in L6M. Block sign = sign of the summed delta over the half-year; t uses the trade-level variance (naive, not clustered; sign counts are the primary read). Full per-rule list: `regime_library_re1_ON.csv` (pattern string 23H1..25H2, worked-in list); bank edges: `out/recentedge2/regime_library.csv` (RE-2) and the per-row string now in RECENT_WINS.

### C1. Share of each family's ON rules positive in each regime
| source | rules | ON_L3M_L6M | mean_blocks_pos_of6 | share_pos_all_prior5 | share_pos_23H1 | share_pos_23H2 | share_pos_24H1 | share_pos_24H2 | share_pos_25H1 |
|---|---|---|---|---|---|---|---|---|---|
| H10_eint2 | 4,950 | 1,492 | 3.60 | 0.01 | 0.73 | 0.79 | 0.17 | 0.21 | 0.72 |
| H1_profit | 23,773 | 8,961 | 3.41 | 0.00 | 0.99 | 0.03 | 0.06 | 0.37 | 0.96 |
| H2_loss | 2,380 | 395 | 3.69 | 0.04 | 0.70 | 0.58 | 0.61 | 0.37 | 0.53 |
| H3_cfeng | 560 | 1 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| H4_c2G1 | 2,820 | 7 | 2.86 | 0.00 | 0.43 | 0.86 | 0.14 | 0.00 | 0.71 |
| H4_c2G2 | 2,368 | 1 | 1.00 | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 0.00 |
| H4_c2G3 | 2,256 | 0 |  |  |  |  |  |  |  |
| H4_c2G4 | 1,824 | 0 |  |  |  |  |  |  |  |
| H4_c2G5 | 684 | 4 | 2.00 | 0.00 | 0.25 | 0.00 | 0.00 | 0.00 | 0.75 |
| H5_barseng | 7,165 | 942 | 2.69 | 0.01 | 0.29 | 0.61 | 0.36 | 0.31 | 0.18 |
| H6_eint1 | 389 | 172 | 3.51 | 0.03 | 0.40 | 0.59 | 0.51 | 0.55 | 0.52 |
| H7_split2 | 63 | 10 | 2.50 | 0.00 | 1.00 | 0.20 | 0.00 | 0.00 | 0.30 |
| H7b_l2sj | 72 | 54 | 2.67 | 0.07 | 0.67 | 0.15 | 0.26 | 0.11 | 0.48 |
| H9_entry | 4,251 | 203 | 3.24 | 0.01 | 0.88 | 0.08 | 0.08 | 0.22 | 0.99 |

Most common sign patterns (23H1..25H2) among the ON rules: +---++ (4,924 rules), +--+++ (3,287), ++--++ (917), +-+-++ (356), +----+ (277): the typical ON rule worked in 2023H1, failed through 2024, and came back in 2025.

### C2. Does a positive regime predict the next regime? (all series with >=30 positive rules, pooled over sources)
| block | n_rules_pos | P_next_positive | P_next_unconditional |
|---|---|---|---|
| 23H1 | 37,511 | 0.19 | 0.19 |
| 23H2 | 12,897 | 0.29 | 0.22 |
| 24H1 | 8,042 | 0.19 | 0.17 |
| 24H2 | 7,787 | 0.63 | 0.47 |
| 25H1 | 22,496 | 0.60 | 0.42 |

### C3. Rules positive in all six regimes (47) and in at least five (465)
| source | rules positive in all 6 half-years |
|---|---|
| H10_eint2 | 14 |
| H1_profit | 1 |
| H2_loss | 15 |
| H5_barseng | 7 |
| H6_eint1 | 4 |
| H7b_l2sj | 4 |
| H9_entry | 2 || source | positive in >=5 of 6 |
|---|---|
| H10_eint2 | 90 |
| H1_profit | 191 |
| H2_loss | 82 |
| H5_barseng | 51 |
| H6_eint1 | 34 |
| H7b_l2sj | 4 |
| H9_entry | 13 |

The all-six rules are mostly EINT2 day-type lines on KB-Asia (the f.bnd5/bnd10 half-size lines), the L2SET-joint H-set lines, UF-loss D3 cuts, and a few bars-engine streams; they are the library's answer to 'works in every regime', and each is a handful of near-identical variants (the KB-Asia lines are the same stream under 8 names).

## D. The top-30 'stronger evidence' rows re-read

Selection: rows of `all_rows_unified.csv` with z6>=3 and positive, collapsed to the best score-x-live row per (program, book), top 30 (stream count 162, row count 2,978). Capped: windows computed from the capped monthly series (L3M 2025-11..2026-01, L6M 2025-08.., HOLD 2025-07.., PRE 2024-02..2025-06, X' 2023-04..2024-01). Causal: rows built on the same-day vol tag are VOID. Units: pts per planned lot per base trade (or stack $/wk for EINT2/L2SJ), per final contract in the CSV. Status by prereg rule; M-basis profit rules cannot be CONFIRMED until the N-basis target-fill is checked; z6 for matched rows is replaced by the measured monthly t (t6_month).

| program | cell | book | ledger_L3M | ledger_z6_proxy | stored_series | cap_L3M | cap_L6M | cap_HOLD | cap_PRE | cap_X' | t6_month | months_pos_last6 | shrunk_L3M | status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| EQR lots_factor | A|B|E|N @ lots x1.432 | stack | 123,058 | 7.65 | no |  |  |  |  |  |  |  |  | UNIT-INFLATED (structure) |
| THPC2 (profit) | qr_profit|qr|YTD|S1w|reg | ALL books (pooled chain) | 1.58 | 4.48 | no |  |  |  |  |  |  |  |  | VOID (look-ahead) |
| EINT2 | f.exclfirst90.all|STACK6 | STACK6 | 84,840 | 4.89 | H10_eint2 eint2|f.exclfirst90.all|stac | 100,851 | 26,628 | 25,349 | -45,246 | 19,278 | 0.57 | 3.00 | 0.00 | RECENT, weak t |
| EXP1 profit chains (v0, look-ahead vol key) | all|cell|12m|m0.0 | ALL10 profit side | 1.40 | 3.14 | no |  |  |  |  |  |  |  |  | VOID (look-ahead) |
| EINT1 | skipBot3_htf_d_open_atr|ENG | ENG | 78,635 | 3.91 | H6_eint1 skipBot3_htf_d_open_atr scope | 0.88 | 0.36 | 0.38 | -0.35 | 0.02 | 0.32 | 4.00 | 0.00 | RECENT, weak t |
| L2SP profit (THP_POLICY profit) | ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpct0.7|d10 | ST,HM,WT,KB,SM,PE | 1.37 | 3.47 | H1_profit P|sess_tot_ge1.2|armpct0.7|d | 1.18 | 0.99 | 1.03 | 0.32 | 0.41 | 6.40 | 6.00 | 0.69 | RECENT + PRE/X positive, M-basis unverified (shadow) |
| THL2 L2H (hypotheses H1-H12) | H8P|thin0.7|pct0.5|take | 10 static books pooled | 1.24 | 3.21 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| EINT2 | f.exclfirst90.all|HM | HM | 51,157 | 6.52 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| EINT1 | skipBot3_htf_d_open_atr|HM | HM | 41,327 | 7.74 | H6_eint1 skipBot3_htf_d_open_atr scope | 3.90 | 2.55 | 2.31 | -1.52 | -0.19 | 2.78 | 5.00 | 0.00 | RECENT-ONLY |
| CF-B | entry|cfb1|lvl=rnd50|mech=b | ALL | 8.55 | 8.95 | no |  |  |  |  |  |  |  |  | UNIT-INFLATED (structure) |
| META FS2 | H1_6m|P3|POOLED|cfg7 | POOLED | 47,968 | 4.04 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| THP_POLICY joint (L2SE entry / L2SP profit / L2SL loss) | B|E|M | STACK6 | 84,483 | 4.46 | H7b_l2sj l2sj|daily_main|B__E__M scope | 53,627 | 47,147 | 41,999 | -11,161 | -9,792 | 3.76 | 6.00 | 13,223 | RECENT-ONLY |
| UF-LOSS c3 | loss|avoid|cumb_le=0.5 [scope ALL] | ALL | 0.76 | 3.53 | H2_loss D3|loss|avoid|cumb_le=0.5 scop | 0.84 | 0.53 | 0.48 | 0.38 | 0.18 | 1.82 | 5.00 | 0.00 | RECENT, weak t |
| EXP1 profit fixed | F7_take_p90 | ALL10 profit side | 0.57 | 5.39 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| EINT2 | f.exclfirst90.all|HM|asia | HM|asia | 37,207 | 5.62 | H10_eint2 eint2|f.exclfirst90.all|HM a | 33,659 | 9,149 | 5,011 | -656 | 2,946 | 0.82 | 3.00 | 0.00 | RECENT, weak t |
| BARS-ENG | ST unirenko_40_60 90/90 D | ST | 14.27 | 3.54 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| SPLIT 70/30 | fam=F5|F=0.5|X=10|N=0|chase=none|veto=v4 [STACK] | STACK | 35,855 | 3.05 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| CF-ENG | PB|iplFVG 30m c1 | PB | 6.11 | 3.50 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| UF-ENTRY c3 | UF3|PZ|C|half|z1.2 | ref=market | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) | 30,828 | 3.73 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| EINT1 | skipTop3_sig_st1_dist_atr|KB | KB | 26,570 | 7.28 | H6_eint1 skipTop3_sig_st1_dist_atr sco | 1.68 | 0.75 | 0.76 | -0.06 | -1.39 | 0.45 | 4.00 | 0.00 | RECENT-ONLY |
| BARS-ALL BA bracket-assign rows2 | L01686 ba2/ST_t120_s50 | ST | 11.99 | 3.36 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| L2SE entry (THP_POLICY entry) | cid2103|fam=F5|F=0.7|X=10|N=2|chase=none|veto=v4 | STACK6 | 31,904 | 4.28 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| UF-ENTRY c1 | UF1|G3|F=0.7|X1=3|X2=8|N=0 | ref=market | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) | 27,386 | 3.22 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| L2SP profit (THP_POLICY profit) | ST|P|sess_ahead_ge3.0|armpts20|d0|lock5|p70alway | ST | 2.72 | 3.36 | H1_profit P|sess_ahead_ge3.0|armpts20| | 2.56 | 2.67 | 2.68 | 0.01 | -0.11 | 4.77 | 6.00 | 1.50 | RECENT + PRE/X positive, M-basis unverified (shadow) |
| BARS-ALL BA bracket-assign rows2 | L01528 ba2/HM_t120_sst | HM | 9.80 | 3.72 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| UF-ENTRY c4 | UF4|P|S|6m|ce1|fbC | ref=market | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) | 25,511 | 3.30 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| META FS2 | H3_ENS|P2|nyam|cfg436 | nyam | 23,236 | 5.45 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| META FS2 | H2_ENS|P5|asia|cfg134 | asia | 27,112 | 3.10 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| L2SE entry (THP_POLICY entry) | cid1765|fam=F4|X=inf|chase=prt5|stop=orig|KB | KB | 26,214 | 5.03 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |
| UF-ENTRY c2 | UF2|S|agree_nqnow_esdlt30|q0.1|half | ref=market | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) | 22,912 | 3.70 | no |  |  |  |  |  |  |  |  | UNVERIFIED (no stored monthly series; z6 is a proxy = z3*sqrt2) |

Reading: 9 of 30 rows have a stored series. Measured 6-month t is 0.3-2.8 for the six EINT1/EINT2/UF-loss rows (below the ledger proxy of 3.9-7.7 in each) and 6.4 / 4.8 / 3.8 for the two L2SP profit rows and the THP joint line. EINT2 'exclude first 90 min' is +100.9k $/wk in L3M, -45.2k in PRE, +19.3k in X', t6 0.57 (RECENT, weak t); EINT1 skipBot3_htf_d_open_atr on HM is RECENT-ONLY (+3.9 pts L3M vs -1.5 PRE); the THP joint B|E|M stack line is RECENT-ONLY (+53.6k L3M, -11.2k PRE, -9.8k X'). The 17 rows without a stored monthly series stay UNVERIFIED (shadow); EQR lots_factor and CF-B are unit-inflated by construction (extra lots; per-contract); THPC2/EXP1 rows with regime/vol keys are VOID until the causal tag is applied. None is promoted.

## E. Disclosures and limits
* Re-reads of stored series only; no new strategy cells, no lock-engine re-run this cycle (stack chains use RE-2's stored bank).
* RE-1 series are pooled over books at one planned lot each; stack $ conversions for pooled rows are not live-lot dollars.
* Chain eligibility and the 6-month fit are fixed by prereg; the twin permutes whole months across rules, so serial dependence inside the 6-month fit window is also destroyed (it makes the twin a fair 'no time structure' null).
* The regime association (B2) is weekly and in-sample for the pre-2025-10 fit; two regressors only. Depth is measured at signal seconds (selection by when books signal), through January 2026.
* The per-trade fill cost in the store is the store's own modelled/measured entry cost (pts), not the live-cal exit fills of LIVE_CAL_SUMMARY.md.
* Monitor (section 4) not refreshed past 2026-02-06 (cap).
* Question: none.

## Files
Code `l2vast/ds3/code/recentedge3/` (r3a_chain, r3a2_stackchain, r3b_regime, r3b2_regime, r3b3_edgebets, r3c_library, r3d_top30, r3_report, r3_assemble); outputs `l2vast/ds3/out/recentedge3/` (chain_series.csv, chain_stack.csv, regime_halfyear.csv, regime_monthly.csv, regime_weekly.csv, regime_nq_daily.csv, edge_regime_bets.csv, regime_library_re1_*.csv, top30_reread.csv, report_tables.md). Edited with backups: `code/recentedge/edge_columns.py`, `code/recent_wins/compile_recent_wins.py`.
