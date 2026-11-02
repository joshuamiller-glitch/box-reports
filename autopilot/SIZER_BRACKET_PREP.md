# SIZER_BRACKET_PREP - T-SIZER prep: bracket syntax, entry features, bracket-by-ER cells on V13T_LIVE, sizer x zone overlap (Z1; 2026-11-02 15:21Z). PREP, not the T-SIZER result; POST-HOC, no PASS, Shadow only

Prereg ZONES3_S1_addendum5 (sha eb4bfae9...) in DECISIONS.md before any bracket statistic. Base V13T_LIVE + shipped HALF layer (take lines off, lock none, xcost .80, stopcost 2.45). Windows and PA9 band as DS3_ZONES_3_NOISE_V13T_FINAL.md.

## Answer in one paragraph
Bracket-by-ER does not work on V13T_LIVE: tight brackets for low ER (ER<=0.30 -> 45/45) are worse than the book bracket in L6M/HOLD/MID (cuts -8..-21%) and the wide brackets for high ER (75/75, 90/90) with unchanged lots are catastrophic (maxDD L6M +170%..+260%, X' +300%..+500%) because the risk per lot rises; with risk-parity lots (60/stop) the wide bracket is still worse (L6M -61%..-79%). The only cell beyond the PA9 band anywhere is ER<=0.15 -> 45/45 with parity lots (PRE +26%, phase-averaged +18%) and it fails everything else (L6M -8%, X' -62%, mean -16.6k/wk L6M) and is not distinguishable from chance in PRE (ranks 0.10 / 0.14 / 0.17 against 100 draws per kind). Per book nothing is beyond the band. A wider bracket for trending conditions needs the stop-based lot parity AND a reason to be wider; this ER feature gives none. Sizer x zone overlap: the zone HALF layer acts on 14.2% of live-lot candidate rows; 57.2% of them are also ER x0.5 rows (double-halved, net x0.25), only slightly above the 54.4% independence expectation, so ER x0.5 does not "already cover" the zone halving (the zone rows are not low-ER rows; 42.8% of them are ER x1.5 rows, net x0.75) but where they coincide the lots collapse (7 -> 2, 4 -> 1 under single rounding); 14.9% of all ER x0.5 rows are zone rows.

## 1. Bracket section: syntax and how an override enters V13T_LIVE
* THP_POLICY (THP_POLICY_bracket_section.txt, THP_POLICY_20261029.txt): `bracket <D6 tag> <session|*> [vol >= v] [vol <= v] stop=<pts> target=<2R|3R|OR|PD|VW|pts> time=none lotmult=<x>`; OR / PD / VW = nearest opening-range edge / prior-day high-low / VWAP +-1,2 sd band AHEAD at a distance in [0.5 stop, 6 stop], else 2R; lots = max(1, round(base*60/stop)), lotmult = that / base; first match wins; unmatched rows keep the book bracket. Sections: entry / profit / loss / bracket in THP_POLICY_D7_N.txt (all EMPTY as of the refresh: no line passes on N).
* Features named by the order for the bracket section: atr, atr_ratio, onr, hour, eff120 (THP exit features: pct mins secs_ext dd recov vel30 eff120 delta60). In feat_signal.parquet (/mnt/l2/l2vast/ds3_sizer/, 88,490 rows in d_rows order, tid-tied) the available entry features are er_<tf>m_<n> (live: er_5m_20), ers_*, adx14_{1,5,15}m, chop14_{5,15}m, atr14_5m, atr_ratio_5m, rv_ratio_30m, range_so_far_ratio, delta5/10/30_s, big2_net30_s, imb5_s, imb10_s, tot_rel, ahead_rel, barage_*; NOT built: onr (overnight range ratio), hour is derivable from sig_sec, eff120 is a path feature (not in the file).
* There is no native bracket hook in d7lib / V13T. Mechanism used here (code/zones3/s1/brk.py): wrap the base outcome builder d7lib._compose0, and for the selected d-rows replace the outcome row by poi_sim.run_split(d, 'N', idx, td=target, sd=stop, F=0.7, X=3.0) (plain 70/30 dip-3 split with the new stop and target, basis N), o[:,13]=nan, o[:,14]=0.7; PE-confirmed NY rows keep the PE kernel; lots by the V13T option lots_mult = 60/stop (risk parity) through the ER-multiplier hook with single integer rounding, or unchanged. Limit: the plain split differs from the library split cell (veto v4), so every mask set has a CONTROL (same rows, book default stop/target through run_split): the control alone changes L6M maxDD 151 -> 134k on the ER<=0.30 rows, so cells are read against the control AND the base. The lock engine marks the row with the library stop level / target distance for those rows (sl0, tgl) which is not patched: second-order for per-book locks, stated.

## 2. Bracket-by-ER cells, ALL six live books (maxDD cut vs the base and vs the control; PA = phase-averaged; band = Z3 PA9 flip-5)
| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| ALL A1 | 1 | base | -10% (-14%) / -2% (-13%) / -2% (-13%) / -8% (-9%) / +4% (+1%) / +1% (+6%) | - | +7% / +3% | -2.1 (9.0) / -1.6 (2.9) | -790>-802 |
| ALL A1 | 1 | control | -11% (-16%) / -1% (-9%) / -1% (-9%) / -8% (-10%) / +4% (+1%) / +1% (+6%) | - | +6% / +3% | -2.1 (9.1) / -1.9 (2.9) | -783>-802 |
| ALL A1 | 60/stop | base | -72% (-80%) / -8% (-28%) / -16% (-35%) / -137% (-82%) / +26% (+18%) / -62% (-50%) | PRE | +19% / +25% | -16.6 (24.7) / -8.1 (10.3) | -790>-746 |
| ALL A1 | 60/stop | control | -74% (-83%) / -8% (-24%) / -15% (-30%) / -138% (-82%) / +26% (+18%) / -63% (-50%) | PRE | +18% / +25% | -16.6 (24.8) / -8.4 (10.3) | -783>-746 |
| ALL A2 | 1 | base | -43% (-48%) / -8% (-21%) / -8% (-21%) / -49% (-38%) / -6% (-2%) / -2% (+9%) | - | +23% / -7% | -1.7 (11.5) / -2.6 (3.9) | -790>-829 |
| ALL A2 | 1 | control | -40% (-49%) / -21% (-33%) / -21% (-31%) / -42% (-36%) / -6% (-2%) / -4% (+8%) | - | +24% / -7% | -2.6 (11.5) / -2.9 (3.9) | -781>-829 |
| ALL A2 | 60/stop | base | -124% (-106%) / -40% (-37%) / -58% (-65%) / -265% (-166%) / -19% (-23%) / -105% (-85%) | - | -41% / -20% | -18.1 (40.1) / -7.5 (12.0) | -790>-832 |
| ALL A2 | 60/stop | control | -119% (-107%) / -57% (-52%) / -77% (-79%) / -247% (-163%) / -19% (-23%) / -109% (-87%) | - | -38% / -20% | -18.9 (40.0) / -7.8 (12.1) | -781>-832 |
| ALL B1 | 1 | base | -218% (-205%) / -170% (-188%) / -170% (-188%) / -138% (-99%) / -70% (-81%) / -295% (-271%) | - | -1% / -72% | -15.3 (27.7) / -2.8 (12.4) | -790>-975 |
| ALL B1 | 1 | control | -234% (-213%) / -179% (-193%) / -179% (-193%) / -143% (-101%) / -71% (-81%) / -335% (-303%) | - | -6% / -75% | -12.1 (26.1) / -3.6 (12.4) | -770>-975 |
| ALL B1 | 60/stop | base | -89% (-90%) / -61% (-68%) / -87% (-92%) / -259% (-141%) / +10% (-5%) / -102% (-104%) | - | +28% / +10% | -22.1 (27.7) / -6.6 (12.6) | -790>-701 |
| ALL B1 | 60/stop | control | -98% (-95%) / -67% (-71%) / -93% (-96%) / -267% (-143%) / +10% (-6%) / -122% (-121%) | - | +24% / +8% | -18.9 (29.1) / -7.4 (12.6) | -770>-701 |
| ALL B2 | 1 | base | -279% (-266%) / -260% (-271%) / -260% (-271%) / -253% (-153%) / -81% (-97%) / -516% (-495%) | - | -19% / -82% | -22.3 (30.4) / -3.9 (18.5) | -790>-1159 |
| ALL B2 | 1 | control | -297% (-276%) / -273% (-278%) / -273% (-278%) / -261% (-156%) / -81% (-97%) / -579% (-546%) | - | -25% / -86% | -19.2 (29.0) / -4.7 (18.4) | -770>-1159 |
| ALL B2 | 60/stop | base | -89% (-85%) / -22% (-38%) / -93% (-97%) / -317% (-181%) / -2% (-5%) / -167% (-152%) | - | +9% / -3% | -23.0 (26.3) / -8.7 (14.5) | -790>-737 |
| ALL B2 | 60/stop | control | -98% (-91%) / -26% (-40%) / -100% (-100%) / -326% (-184%) / -3% (-5%) / -194% (-173%) | - | +4% / -5% | -19.9 (27.0) / -9.5 (14.5) | -770>-737 |
| ALL C1 | 1 | base | -246% (-237%) / -207% (-239%) / -207% (-239%) / -173% (-101%) / -106% (-111%) / -366% (-333%) | - | +5% / -108% | -14.7 (28.5) / -5.4 (13.2) | -790>-1014 |
| ALL C1 | 1 | control | -255% (-251%) / -253% (-275%) / -253% (-269%) / -166% (-101%) / -107% (-112%) / -420% (-376%) | - | +2% / -111% | -15.4 (28.3) / -6.4 (13.3) | -764>-1014 |
| ALL C1 | 60/stop | base | -188% (-183%) / -79% (-107%) / -104% (-118%) / -291% (-194%) / -53% (-65%) / -252% (-231%) | - | -63% / -54% | -29.4 (45.2) / -8.4 (13.9) | -790>-822 |
| ALL C1 | 60/stop | control | -195% (-195%) / -107% (-129%) / -135% (-137%) / -282% (-194%) / -54% (-66%) / -293% (-264%) | - | -67% / -57% | -30.2 (45.2) / -9.4 (14.0) | -764>-822 |
| ALL C2 | 1 | base | -253% (-241%) / -199% (-224%) / -199% (-224%) / -143% (-86%) / -91% (-92%) / -278% (-248%) | - | +5% / -93% | -14.5 (28.7) / -5.0 (13.0) | -790>-1020 |
| ALL C2 | 1 | control | -275% (-255%) / -228% (-236%) / -228% (-236%) / -151% (-89%) / -92% (-92%) / -320% (-278%) | - | -1% / -97% | -11.8 (27.5) / -6.0 (13.1) | -765>-1020 |
| ALL C2 | 60/stop | base | -174% (-185%) / -82% (-116%) / -82% (-116%) / -186% (-127%) / -25% (-31%) / -102% (-91%) | - | +7% / -26% | -24.4 (32.1) / -10.0 (14.1) | -790>-771 |
| ALL C2 | 60/stop | control | -191% (-197%) / -99% (-124%) / -99% (-124%) / -195% (-131%) / -25% (-31%) / -125% (-108%) | - | +2% / -29% | -21.6 (34.0) / -11.0 (14.1) | -765>-771 |

### Per book (lots unchanged; rules A2 ER<=0.30 -> 45/45, B1 ER>0.30 -> 75/75, C1 both)

**K7**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| K7 A2 | 1 | base | +7% (-2%) / -11% (-17%) / -11% (-17%) / -36% (-0%) / +2% (+4%) / +7% (+6%) | - | +9% / +1% | +0.3 (2.9) / +0.2 (1.6) | -790>-771 |
| K7 A2 | 1 | control | +8% (-3%) / -22% (-26%) / -22% (-25%) / -37% (-0%) / +2% (+4%) / +6% (+5%) | - | +11% / +1% | -0.3 (3.1) / -0.1 (1.6) | -786>-771 |
| K7 B1 | 1 | base | +16% (+9%) / -0% (-1%) / -6% (-7%) / -33% (-13%) / -4% (-0%) / +14% (+10%) | - | +16% / -5% | +2.8 (6.5) / +1.4 (2.5) | -790>-787 |
| K7 B1 | 1 | control | +15% (+8%) / -5% (-6%) / -10% (-12%) / -38% (-14%) / -3% (+1%) / +6% (+3%) | - | +15% / -5% | +2.4 (6.3) / +1.0 (2.5) | -776>-787 |
| K7 C1 | 1 | base | +13% (+5%) / -16% (-21%) / -16% (-21%) / -54% (-13%) / -3% (+0%) / +14% (+15%) | - | +13% / -4% | +1.8 (6.9) / +1.1 (2.8) | -790>-756 |
| K7 C1 | 1 | control | +14% (+4%) / -32% (-35%) / -32% (-33%) / -61% (-15%) / -2% (+1%) / +4% (+8%) | - | +14% / -4% | +0.9 (7.1) / +0.6 (2.9) | -774>-756 |

**P7**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| P7 A2 | 1 | base | -14% (-17%) / +8% (+3%) / +8% (+3%) / -33% (-34%) / +2% (+0%) / -4% (+6%) | - | +5% / +1% | -2.2 (10.9) / -2.0 (2.6) | -790>-841 |
| P7 A2 | 1 | control | -16% (-19%) / +7% (+3%) / +7% (+3%) / -34% (-35%) / +2% (-0%) / -4% (+6%) | - | +4% / +1% | -2.6 (10.8) / -2.1 (2.6) | -788>-841 |
| P7 B1 | 1 | base | -158% (-145%) / -93% (-100%) / -93% (-100%) / -92% (-63%) / -63% (-65%) / -125% (-109%) | - | -26% / -65% | -10.9 (20.4) / -3.6 (8.9) | -790>-886 |
| P7 B1 | 1 | control | -170% (-152%) / -99% (-103%) / -99% (-103%) / -93% (-63%) / -63% (-65%) / -126% (-110%) | - | -32% / -65% | -7.8 (18.1) / -3.9 (8.8) | -789>-886 |
| P7 C1 | 1 | base | -165% (-149%) / -115% (-129%) / -115% (-129%) / -155% (-84%) / -65% (-66%) / -183% (-163%) | - | -19% / -67% | -10.0 (21.5) / -5.6 (8.9) | -790>-909 |
| P7 C1 | 1 | control | -181% (-159%) / -123% (-135%) / -123% (-135%) / -157% (-86%) / -66% (-67%) / -185% (-164%) | - | -26% / -67% | -10.2 (20.7) / -6.0 (8.8) | -787>-909 |

**U7**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| U7 A2 | 1 | base | +9% (+8%) / +15% (+15%) / +15% (+12%) / +11% (+6%) / -3% (-1%) / -2% (-1%) | - | +9% / -3% | +0.7 (2.0) / -0.2 (0.9) | -790>-800 |
| U7 A2 | 1 | control | +9% (+7%) / +14% (+14%) / +14% (+12%) / +11% (+6%) / -2% (-1%) / -3% (-1%) | - | +9% / -3% | +0.7 (1.9) / -0.2 (0.9) | -790>-800 |
| U7 B1 | 1 | base | -17% (-15%) / -51% (-50%) / -51% (-50%) / -12% (-11%) / -8% (-1%) / -61% (-53%) | - | -17% / -9% | -3.6 (7.0) / -0.4 (3.5) | -790>-813 |
| U7 B1 | 1 | control | -16% (-15%) / -50% (-49%) / -50% (-49%) / -11% (-11%) / -8% (-2%) / -60% (-52%) | - | -16% / -11% | -3.5 (7.0) / -0.4 (3.5) | -788>-813 |
| U7 C1 | 1 | base | -7% (-6%) / -38% (-38%) / -38% (-38%) / -0% (-5%) / -12% (-3%) / -61% (-54%) | - | -7% / -13% | -3.0 (7.2) / -0.6 (3.5) | -790>-825 |
| U7 C1 | 1 | control | -7% (-6%) / -39% (-38%) / -39% (-38%) / +1% (-5%) / -12% (-3%) / -60% (-53%) | - | -7% / -14% | -3.0 (7.2) / -0.5 (3.5) | -789>-825 |

**H7**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| H7 A2 | 1 | base | -16% (-20%) / -27% (-29%) / -27% (-29%) / -2% (-3%) / -1% (+1%) / -17% (-16%) | - | +1% / -2% | -0.9 (3.1) / +0.1 (1.3) | -790>-788 |
| H7 A2 | 1 | control | -16% (-20%) / -25% (-28%) / -25% (-28%) / -2% (-3%) / -1% (+1%) / -17% (-16%) | - | +0% / -2% | -0.8 (3.1) / +0.1 (1.3) | -788>-788 |
| H7 B1 | 1 | base | +3% (-3%) / -9% (-17%) / -12% (-20%) / -21% (-6%) / -10% (-8%) / +4% (+6%) | - | +19% / -5% | +1.1 (6.4) / +0.7 (2.5) | -790>-831 |
| H7 B1 | 1 | control | +3% (-4%) / -11% (-18%) / -13% (-22%) / -21% (-6%) / -10% (-8%) / +4% (+6%) | - | +19% / -5% | +0.7 (6.4) / +0.6 (2.5) | -787>-831 |
| H7 C1 | 1 | base | -14% (-18%) / -21% (-29%) / -21% (-29%) / +4% (+4%) / -10% (-9%) / -12% (-11%) | - | +17% / -3% | +1.1 (6.6) / +0.9 (2.7) | -790>-815 |
| H7 C1 | 1 | control | -14% (-18%) / -22% (-30%) / -22% (-30%) / +5% (+4%) / -10% (-9%) / -13% (-12%) | - | +17% / -3% | +0.8 (6.7) / +0.9 (2.8) | -785>-815 |

**M7**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| M7 A2 | 1 | base | +1% (+1%) / +17% (+16%) / +15% (+12%) / -2% (-2%) / -2% (-2%) / -0% (+1%) | - | +1% / -1% | +0.8 (2.2) / -0.4 (0.7) | -790>-796 |
| M7 A2 | 1 | control | +4% (+2%) / +16% (+16%) / +14% (+11%) / +3% (+1%) / -2% (-2%) / -1% (+1%) | - | +4% / -1% | +0.9 (2.2) / -0.4 (0.7) | -788>-796 |
| M7 B1 | 1 | base | +4% (-2%) / -4% (-9%) / -4% (-9%) / -18% (-5%) / +2% (+3%) / +15% (+9%) | - | +4% / +1% | -0.2 (4.2) / +0.3 (1.9) | -790>-800 |
| M7 B1 | 1 | control | +5% (-2%) / -1% (-6%) / -1% (-6%) / -17% (-5%) / +1% (+2%) / +14% (+8%) | - | +5% / +1% | -0.1 (4.2) / +0.1 (1.9) | -788>-800 |
| M7 C1 | 1 | base | +5% (+0%) / +2% (-3%) / +2% (-3%) / -9% (-6%) / -1% (+1%) / +17% (+14%) | - | +5% / -2% | +0.5 (4.3) / -0.3 (1.9) | -790>-801 |
| M7 C1 | 1 | control | +7% (+1%) / +4% (-1%) / +4% (-1%) / -3% (-3%) / -2% (-1%) / +15% (+13%) | - | +7% / -2% | +0.8 (4.1) / -0.5 (2.0) | -786>-801 |

**A6**

| cell | lots | vs | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg in brackets) | beyond PA9 flip-5 band (windows) | carrying episode dropped: L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|---|
| A6 A2 | 1 | base | +2% (-1%) / -4% (-6%) / -4% (-6%) / +5% (+1%) / -2% (+2%) / -2% (-3%) | - | +2% / -3% | -0.3 (1.5) / +0.0 (0.7) | -790>-787 |
| A6 A2 | 1 | control | +2% (-2%) / -5% (-6%) / -5% (-6%) / +5% (+1%) / -2% (+2%) / -2% (-3%) | - | +2% / -2% | -0.3 (1.5) / +0.0 (0.7) | -790>-787 |
| A6 B1 | 1 | base | +5% (-3%) / -7% (-10%) / -7% (-10%) / -13% (-5%) / +1% (+1%) / -16% (-15%) | - | +11% / +6% | -1.1 (3.1) / -0.6 (1.1) | -790>-790 |
| A6 B1 | 1 | control | +5% (-2%) / -5% (-7%) / -5% (-7%) / -13% (-5%) / +1% (+1%) / -15% (-14%) | - | +11% / +6% | -0.5 (2.9) / -0.5 (1.1) | -793>-790 |
| A6 C1 | 1 | base | -7% (-11%) / -14% (-16%) / -14% (-16%) / -8% (-4%) / +4% (+4%) / -17% (-18%) | - | +9% / +3% | -1.2 (3.0) / -0.4 (1.3) | -790>-777 |
| A6 C1 | 1 | control | -8% (-12%) / -13% (-15%) / -13% (-15%) / -8% (-4%) / +4% (+5%) / -16% (-18%) | - | +9% / +3% | -0.9 (3.3) / -0.2 (1.4) | -793>-777 |

### Placebos for the only cell beyond the band (ALL A1 = ER<=0.15 -> 45/45, parity lots), 100 draws per kind
Random same-count rows (A), Bernoulli same-volume rows (B), shuffled-day donor rows (C) given the same bracket and lots; rank = share of draws cutting at least as much vs the base: PRE cut +26.2% ranks 0.099 / 0.139 / 0.168; L6M cut -8.1% ranks 0.81 / 0.88 / 0.75; X' cut -62.0% ranks 0.30 / 0.41 / 0.38. Chance in every window: no lead.

## 3. Sizer x zone-layer interaction (counts on live-lot candidate rows of the shipped stack; candidate = row entering the engine, not the trade-taken subset)
```
LIVE-lot candidate rows 26645 ER x0.5 14485 (54.4%) x1.5 12160
HALF rows 3782 (14.2% of rows) | of those ER x0.5 (double-halved, net x0.25): 2165 = 57.2% (independence 54.4%) | ER x1.5 (net x0.75): 1617 = 42.8%
share of all ER x0.5 rows that are also in the zone layer: 14.9%
      rows  zone  er_low  both  lots  er_low%  both%zone
book                                                    
HM    3304   504    2096   348   2.7     63.4       69.0
KB    8025  1103    5214   804   1.7     65.0       72.9
MV    3674   320    2220   228   1.4     60.4       71.2
PB    5403   989    1620   292   1.0     30.0       29.5
PE    4869   529    2762   357   7.0     56.7       67.5
SM    1370   337     573   136   4.0     41.8       40.4
         rows  zone  er_low  both  lots  er_low%  both%zone
sess                                                       
asia    12400  2310    5658  1099   2.9     45.6       47.6
london   5680   699    3170   450   3.7     55.8       64.4
nyam     6920   601    4568   483   1.9     66.0       80.4
nypm     1645   172    1089   133   2.0     66.2       77.3
planned lots 1 -> ER x0.5 only 1 | zone half only 1 | both single-rounding x0.25 1 | both sequential (zone first)  1
planned lots 2 -> ER x0.5 only 1 | zone half only 1 | both single-rounding x0.25 1 | both sequential (zone first)  1
planned lots 4 -> ER x0.5 only 2 | zone half only 2 | both single-rounding x0.25 1 | both sequential (zone first)  1
planned lots 7 -> ER x0.5 only 4 | zone half only 4 | both single-rounding x0.25 2 | both sequential (zone first)  2
```

Reading: the ER ladder halves 54.4% of live-lot rows; the zone layer halves 14.2%; the intersection is 57.2% of zone rows (independence expectation 54.4%, book-wise 29-73%, higher in NY-AM/PM 77-80% because NY rows are more often low-ER). Under the live single-rounding rule a double-halved row gets lots x0.25 (e.g. P7 7 -> 2, K7/H7 4 -> 1, 1-2 lot rows stay 1): in lot terms the zone layer adds little on those rows (1-2 lot books are already at the floor of 1 lot) and does real work only on the 42.8% of zone rows with ER x1.5 (x0.75) and on the multi-lot books (P7, U7, H7 Asia). Whether to cap double-halving (min lots after both) is a T-SIZER cell, not decided here.


## UPDATE 15:50Z - official BASE-4 bracket hook (tighter side) supersedes the run_split rows for the low-ER side
Hook: `run_v13t_live({'bracket': (stop_pts, target_pts)})` (EXIT_API.md, CORRECTED blocks of SIZER_HOOK_TESTS.md): arrays over the 88,490 d rows, NaN = library default; ONLY tighter-or-equal brackets are supported (earliest of new stop touch / new target touch / library exit becomes an injected full exit, stop priced at nominal + stopcost 2.45, resting add cancelled on exit, interplay with the TH-L2 cut tested). Cells scored on it (same HALF layer base, lots unchanged or 60/stop through lots_mult; vs the base only, no kernel control needed because no outcome row is rebuilt):

| cell (official bracket hook, tighter side) | lots | maxDD cut L3M / L6M / HOLD / MID / PRE / X' (phase-avg) | beyond PA9 band | episode dropped L6M / PRE | mean d $k/wk (MDE) L6M / PRE | worst-20 PRE b>a |
|---|---|---|---|---|---|---|
| ALL ER<=0.15 -> 45/45 | 1 | +3% (-5%) / -5% (-12%) / -5% (-12%) / +27% (+16%) / -1% (-1%) / -2% (+4%) | - | +3% / +3% | -2.0 (5.2) / -1.0 (2.2) | -790>-823 |
| ALL ER<=0.15 -> 45/45 | 60/stop | -23% (-33%) / -1% (-16%) / -2% (-20%) / -109% (-59%) / +4% (+2%) / -43% (-30%) | - | +38% / +3% | -14.5 (20.0) / -4.8 (9.3) | -790>-748 |
| ALL ER<=0.15 -> 30/30 | 1 | -11% (-19%) / +18% (-2%) / +16% (-3%) / +14% (+13%) / +2% (+1%) / +4% (+10%) | - | -11% / +3% | -1.7 (6.7) / -2.1 (3.7) | -790>-869 |
| ALL ER<=0.15 -> 30/30 | 60/stop | -41% (-58%) / +4% (-18%) / -111% (-125%) / -296% (-198%) / +12% (+8%) / -3% (-2%) | - | +27% / +11% | -5.6 (21.3) / -9.3 (10.3) | -790>-870 |
| ALL ER<=0.30 -> 45/45 | 1 | -10% (-15%) / -25% (-36%) / -25% (-36%) / +28% (+16%) / +4% (+2%) / +15% (+16%) | - | +9% / +6% | -4.7 (5.9) / -1.1 (3.3) | -790>-783 |
| ALL ER<=0.30 -> 45/45 | 60/stop | -17% (-22%) / +18% (+5%) / -32% (-36%) / -192% (-107%) / -3% (-0%) / -39% (-27%) | - | +29% / -4% | -13.9 (21.5) / -5.7 (11.0) | -790>-809 |
| ALL ER<=0.30 -> 30/30 | 1 | -16% (-38%) / -20% (-37%) / -20% (-37%) / +25% (+15%) / -2% (-3%) / +3% (+13%) | - | -1% / +4% | -4.7 (10.2) / -3.7 (4.2) | -790>-774 |
| ALL ER<=0.30 -> 30/30 | 60/stop | -99% (-102%) / -24% (-40%) / -108% (-119%) / -323% (-188%) / -17% (-21%) / -54% (-37%) | - | +27% / -18% | -11.8 (26.9) / -14.2 (14.2) | -790>-1162 |
| K7 ER<=0.30 -> 45/45 | 1 | +5% (+5%) / -3% (-7%) / -3% (-7%) / +28% (+11%) / +1% (+3%) / +7% (+4%) | - | +5% / +0% | +0.1 (2.3) / +0.5 (1.0) | -790>-785 |
| P7 ER<=0.30 -> 45/45 | 1 | -6% (-11%) / -12% (-15%) / -12% (-15%) / -21% (-7%) / +1% (-0%) / +13% (+16%) | - | +1% / +1% | -3.9 (5.4) / -1.7 (3.0) | -790>-804 |
| U7 ER<=0.30 -> 45/45 | 1 | +5% (+3%) / +6% (+5%) / +6% (+5%) / +12% (+6%) / -2% (-3%) / -3% (-2%) | - | +5% / +1% | +0.2 (1.0) / -0.0 (0.6) | -790>-791 |
| H7 ER<=0.30 -> 45/45 | 1 | -4% (-8%) / -15% (-16%) / -15% (-16%) / +12% (+6%) / +2% (+2%) / -0% (-1%) | - | -4% / +2% | -1.0 (1.5) / -0.0 (0.7) | -790>-783 |
| M7 ER<=0.30 -> 45/45 | 1 | +1% (-2%) / -1% (-3%) / -1% (-3%) / -4% (-0%) / -2% (-2%) / -2% (-1%) | - | +1% / +3% | +0.0 (1.3) / +0.1 (0.5) | -790>-782 |
| A6 ER<=0.30 -> 45/45 | 1 | +0% (+0%) / +0% (+0%) / +0% (+0%) / +0% (+0%) / +0% (+0%) / +0% (+0%) | - | +0% / +0% | +0.0 (0.0) / +0.0 (0.0) | -790>-790 |

Reading: with the official hook no low-ER tightening (ER<=0.15 or ER<=0.30; stop/target 45 or 30; lots unchanged or risk-parity; ALL books or per book) is beyond the PA9 band in any window; the best cells are MID-only (ER<=0.30 -> 45/45 MID +28% but L6M -25%, mean -4.7k/wk) and ER<=0.15 -> 30/30 (L6M +18% single, PRE +2%). Parity lots (60/stop) make drawdown much worse in MID and X'. A6 has no ER<=0.30 rows with a library bracket >= 45 (no effect). So the low-ER tight-bracket idea is DEAD on V13T_LIVE with the official hook, agreeing with the run_split rows above (which stay as indicative cross-check only).
HIGH-ER WIDER BRACKETS: NOT TESTABLE with the official hook (it only injects exits no later than the library exit; a wider stop/target needs the 1-s path beyond the library exit and a different exit kernel). The run_split-based B1/B2/C1/C2 rows above rebuilt the whole outcome with the plain 70/30 split (differs from the library cell by the veto, see the control rows) and are INDICATIVE ONLY; they say that wider brackets with unchanged lots raise drawdown mechanically and that parity lots do not rescue them, but they are not a V13T_LIVE measurement. If T-SIZER needs a measured wider-bracket test, BASE-4 must extend the exit kernel (asked).
