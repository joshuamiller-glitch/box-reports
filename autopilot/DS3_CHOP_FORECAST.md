# DS3_CHOP_FORECAST - W-CH1 (T-CHOP step 1 label, step 2 forecast), first table 2026-11-14 ~19:30Z. No PASS claimed.

VERDICT (data ends 2026-10-30; plain, pass 2 2026-11-14 ~20:15Z): No chop call reaches a stand-down grade: even trained on D7's own rest-of-session dollars the flagged sessions stay net positive on average, the best call is LONDON at the 90-minute clock (flagged mean -$700/-$840 per session vs +$580/+$1,500 unflagged in 2024-07..2026-04, 2025 and L6M, but it does not hold in L3M) and pooled 15-minute (placebo p 0.00-0.10 in every window, flagged mean below unflagged but still positive). PASS-1 verdict follows: the label works (CHOP sessions carry JN05W2 net -$1.85M vs +$3.97M for the rest) but nothing I could build from NQ/ES/RTY 1m bars, calendar, VIX/VVIX/COR, the range forecast and D7's own cut cluster forecasts it with a usable edge yet: best walk-forward calls reach AUC-equivalent lift of only 1.0-1.2 on precision (base rate 33%), the "small forecast range AND low efficiency" call (C) does not beat the benchmarks, and the flagged sessions' remaining D7 dollars are net positive out of sample, so none of these calls is ready to drive a stand-down. mbp-10, options implied move, UW 1-min and megacap proxy inputs are NOT yet tested.

## 1. Label (fixed, DECISIONS.md line sha afc0dbedcbd15899)
Session CHOP = top tercile, within session type, of the mean percentile rank of (low ER, high crossings/hour of the full-session mean, low net/range) on NQ 1m closes (bars1m_NQ, back-adjusted), sessions per GATE0 clock, 2023-04..2026-10 (asia/london/nyam/nypm; pre has no D7 trades). Day label uses the same recipe on the Globex day. Files /mnt/l2/l2vast/_chop/f1/label_sessions.parquet, label_days.parquet, trades_labeled.parquet; code code/th_chop1/ch_label.py.
Dollars (JN05W2 exact, 19,521 trades attributed to entry session): CHOP 5,963 trades net -$1,847,140 (mean -$310); non-CHOP 13,558 trades +$3,967,815 (+$293). Cuts per target: CHOP 1.35 asia / 1.94 london / 2.45 nyam / 2.78 nypm vs 0.72 / 0.99 / 0.86 / 0.86 non-CHOP.
StateCut: 6,070 in history, 2,227 (36.7%) in CHOP sessions; of the 753 StateCuts in the 20 worst weeks 244 are in CHOP sessions.
20 worst weeks (net -$682k): CHOP-session trades net -$397k (58% of set net); share of GROSS loss in CHOP 30.6% (base 35.4%, placebo p95 39.2%, p 0.81: NOT above chance). 40 worst days (net -$869k): CHOP net -$392k (45%), share of gross loss 44.4% (placebo p95 42.1%, p 0.025). Best-5 weeks (+$368k): CHOP trades +$15.5k (293 trades), so standing down in true CHOP costs almost nothing there.
Windows: L3M CHOP -$63k vs non +$336k; L6M -$191k vs +$874k; older -$1.66M vs +$3.09M. Honest caveat: chop explains net expectancy, not the full-stop dollars that dominate gross loss in the worst weeks.
Label variants checked (single metrics, pairs): all similar (CHOP net -1.1M to -1.9M); kept the pre-chosen 3-metric composite.

## 2. Inputs, causality and clocks
Call epoch = session start t0 (pre) or t0+60h s (h=15/30/60/90). A 1m bar is used only if bar_ts+60 <= call epoch. Daily Cboe series (VIX, VIX3M, VIX9D, VVIX, COR1M, COR3M, fetched free from cdn.cboe.com into /mnt/l2/l2vast/_calendar/*_History.csv, 2006-2026-11-13) use the last date whose close (16:15 ET) is <= call time. Prior-RTH value area is the 70% volume area of the previous completed 09:30-16:00 ET session. Range forecast = DS3_RANGEUSE fc.parquet read 0, versions a/b/c, causal expanding-rank buckets (only from 2025-03). D7 cluster = cuts / cuts without a target in the last 30/60/120 min from JN05W2 exit epochs <= call epoch. Target for h>0 = CHOP of the REST of the session (ER/crossings/net-range of bars after the call, tercile within session and h).
Not done yet: mbp-10 book balance/cancel rate/quote age, NQ options implied move vs move so far, UW 1-min, megacap proxy, YM (no 1m store found), per-book cluster.

## 3. Single-input results (all in /mnt/l2/l2vast/_chop/f1/eval1.csv; 1,448 session x clock x input rows)
Edge = signed AUC-0.5 with the sign fixed on data to 2026-04-30; windows OLD1 (to 2024-12), OLD2 (2025-01..2026-04), L6M, L3M; shifted-session placebos (3..45 sessions back). Benchmarks AUC are ~0.45-0.62 and unstable (yesterday-chop is BELOW 0.5 in many cells: after a chop day the next same session is slightly LESS likely chop, at 60 min asia/london it flips sign).
Inputs whose lead is positive in OLD2, L6M, L3M (and OLD1 where it exists) with placebo p <= 0.10 (recent) and <= 0.15 (older): 23 of 1,448 cells, which is about what chance plus 1,448 looks gives, so treat as leads not findings:
- nyam 60 min: er_r30 / nr_r30 (efficiency of the last 30 min): HIGH recent efficiency predicts CHOP for the rest (edges +0.055/+0.071/+0.100/+0.084) - an exhaustion/mean-reversion pattern, strongest single lead.
- nypm 15 min: er_prev1, prev_cs, in_rng (opens inside prior RTH range) edges 0.04-0.14 in all windows; nypm 60: cut_120, cut_60 (D7 cut cluster) +0.10/+0.12 in L6M/L3M.
- london 60: prev_cs/er_prev1/prev_chop; london 30/15: COR1M rank/5-day change (lower implied correlation -> chop); london 90: NQ-RTY correlation (low corr -> chop).
- nyam pre: cor_term, cor1m_rank (edge 0.05-0.09); asia pre: event day E_ev_day (event day -> chop).
- range forecast: rfa_q3/q5/q10 (lowest buckets) appear for nypm 15, london 90, asia 90 only; elsewhere the range forecast edge is 0.01-0.06 and its placebo p is 0.2-0.7.
Full list: /mnt/l2/l2vast/_chop/f1/leads_consistent.csv.

## 4. Walk-forward calls (refit every 14 days from 2024-07-01, expanding train, ridge-logistic C=0.03, flag = score >= train 2/3 quantile so flag rate ~33-45%)
Versions: Mh market/calendar/vol/cluster inputs, Rh = M + range forecast a/b/c, Ch = lowest-tercile range forecast AND efficiency-so-far (pre: prior ER) in its past lowest tercile (the addendum's candidate), Rgh = lowest-tercile range forecast alone, Yh = yesterday-chop flag, Ah = lowest-ATR tercile flag (A almost never fires: ATR rank filter too strict, benchmark weak by construction). All sessions pooled, rest_net = JN05W2 net of trades entered after the call.
OOS older 2024-07..2026-04 (n=1,872 sessions, base 33-34%): M: precision 0.332-0.353 (lift 0.99-1.07), dollars share caught 30-49%, flag rate 31-42%. R: lift 0.97-1.07. C: flag 12-15%, precision 0.30-0.38 (lift 0.92-1.16). Y: lift 0.92-1.04.
L6M (n=480): M15 prec 0.339 lift 1.06, M60 0.380 lift 1.12 (hit 0.50), R60 0.363 lift 1.07; C: flag 6-8%, prec 0.26-0.39; Y lift 0.76-0.98.
L3M (n=219): M15 lift 1.23, M60 1.19, R15 1.19, R60 1.11 (hit 0.45-0.53, 'dollars share caught' 0.53-0.67 of CHOP rest-of-session dollars); C60/C90 1.11/1.17 at flag 12-16%.
Dollars: rest-of-session D7 net of FLAGGED sessions is POSITIVE out of sample for almost every version (M60 L6M +$217k, OOS_older +$284k), i.e. standing down on these flags would have cost money; only C0/C60/C90 flagged sets are slightly negative in L6M (C0 -$57k, 7.5% of sessions) and in L3M (-$49k at pre). False-alarm cost on best-5 weeks (rest net of flagged non-CHOP sessions in those weeks): M/R 60 about -$3k to +$20k (near zero in L6M/L3M since few best-5 weeks are in the test span: only 2026 weeks), OOS_older M60 $20k vs M0 $133k.
Range forecast as a chop input (addendum): Rg (lowest tercile alone) lift 0.83-1.05 across clocks; C (range AND low efficiency) no consistent gain over M/benchmarks. The range forecast adds nothing measurable beyond ATR and efficiency for the CHOP label; the one-sided target test needs the bucket file below.

## 5. Best call per session (so far) and what is missing
No call passes: the leading practical candidate is M60 (all sessions, 60-min clock): L6M precision 0.38 lift 1.12 hit 0.50, L3M lift 1.19, OOS_older lift 1.02 -> the lead does NOT hold in older windows. Best single-input leads are nyam@60 er_r30 and nypm@15 er_prev1/in_rng (hold in all four windows, edges 0.05-0.14, AUC <= 0.62). Next: mbp-10/options/UW inputs, D7-dollar target (rest_net<0) instead of the market-shape label, per-session fit.

## 6. Deliverables for W-CH2 (parquet, /mnt/l2/l2vast/_chop/f1/)
calls_<v>.parquet, v in {M,R,C,Rg,Y,A} x {0,15,30,60,90}: columns day, sess, session_start_epoch, session end t1, call_epoch, chop_flag (NaN before 2024-07-01 or where input missing), score, target, rest_net. h=0 is the pre-session version. call_scores.csv has hit/precision/lift/dollars/false-alarm cost per version, session, window. range_forecast_buckets_causal.parquet: per (ld, sess, var a/b/c) pred, rk (expanding past-only percentile), q3/q5/q10 bucket index (0 = lowest), rel; valid from 2025-03 only. Code: code/th_chop1/ch_label.py ch_feat.py ch_eval1.py ch_call.py.

## 7. PASS 2 (lead order 2026-11-14): D7-dollar target, per-session fits, per-book cluster, mbp-10, implied move, megacap, rolling windows, range-forecast addendum
New code: code/th_chop1/ch_mbp.py (per-minute book features from the mbp-10 replica /mnt/l2/l2vast/_hist_replica/days, 978 days, files /mnt/l2/l2vast/_chop/f1/mbp_min), ch_mega.py (UW 7 megacap 1m closes, 2024-10..2026-11), ch_feat2.py (-> features2.parquet, 193 columns), ch_eval2.py, ch_call2.py. Outputs: eval2_<target>.csv, leads2_<target>.csv, call2_scores.csv, calls_DP*.parquet and calls_DS*.parquet.
Targets: tD_q = rest-of-session JN05W2 net (entries after the call) in its worst tercile within (session, clock); tD_neg = rest net < 0; tD_cpt = rest cuts per target in the top tercile. Only sessions with at least one D7 trade after the call (83% of rows).
New inputs, all causal (minute rows need m+60 <= call epoch; cuts need exit_ts <= call epoch): per-book (K7,P7,U7,M7,H7,A7) and stack cut / cut-without-target counts and cuts-per-target at 30/60/120 min; rolling 60/90 min efficiency, crossings, net/range, NQ-ES and NQ-RTY correlation; mbp-10 from the 100 ms book grid: top-5 balance and |balance|, 10-level depth (also vs trailing-20 same-clock median), churn and pull per traded contract (decrease of depth not explained by prints; the replica has no per-order cancels so this is an upper bound of the cancel rate), inside-quote changes per minute and longest unchanged inside quote per minute (quote age), spread; implied move: range so far / (VIX/sqrt(252) or UW NDX sigma, scaled by sqrt(elapsed/24h)); UW megacap (AAPL AMZN GOOGL META MSFT NVDA TSLA) mean pairwise return correlation, dispersion, breadth, equal-weight ER (premarket onward, so not asia). YM: not available for 43 months (tail pull is 2 days, purchase starts 2026-05), so index disagreement uses NQ/ES/RTY only.
Single-input scan (2,744 session x clock x input cells per target; "consistent" = positive edge in OLD2, L6M, L3M, OLD1 where present, placebo p <= 0.10 recent and <= 0.15 older): market label 35 cells; tD_neg 69; tD_q 67; tD_cpt 189 (chance would give roughly 30-60, so tD_cpt and the cluster are the only families clearly above it).
- D7 cut cluster is the strongest family for the dollar targets: cuts in the last 120 min predict more cuts per target and worse rest-of-session net at nyam@15/30/60 and london@60 (edges 0.13-0.18 in L6M, 0.08-0.22 L3M, 0.04-0.07 OLD2); cutratio_120 nyam@60 edge 0.177 L6M / 0.223 L3M / 0.036 OLD2. Per-book (K7 london@60 0.128) is no better than stack-wide.
- Volatility already seen is the next strongest and points OPPOSITE to "small range = chop": london@90 range so far / ATR, volume vs normal, range vs VIX-implied move (imp_vix_ratio 0.184 L6M, 0.226 L3M, 0.067/0.026 older) and asia@60/90 imp_ndx_ratio and overnight range predict MORE cuts per target and worse D7 dollars. Range forecast (a/b/c) at the session start: higher forecast range predicts more cuts per target in asia (AUC 0.61-0.62 L6M, 0.56-0.57 OLD2, 0.56-0.61 L3M; placebo p 0.00), and a small forecast range does NOT forecast chop (market label asia sign is also positive, london/nyam AUC 0.45-0.58 and unstable). So the addendum's candidate "small forecast range AND low efficiency" fails; for D7's dollars the useful direction is the reverse (big expected range = cut-heavy). Lowest-tercile range forecast alone has lift 0.83-1.05 on the market label (pass 1 Rg).
- mbp-10: 416 cells per target; consistent cells 6 (market), 14, 18, 30; the best are mb_imb5 (london@30 tD_q, edge 0.146 L6M, 0.118 L3M, 0.025/0.038 older, sign: net ask-heavy book -> worse), mb_maxage / mb_nchg relative (london@90: longer unchanged inside quote -> worse rest net), dep10 (asia@90 tD_cpt: thinner book -> more cuts per target, edge 0.15-0.19). On the market-shape label the book inputs are at chance (median edge 0.001).
- Implied move vs move so far: market label no lead (best edge 0.10 L6M, older window against), dollar targets yes (above).
- UW megacap proxy on the fixed label: null as W-CH3 found. nypm@30 corr AUC 0.605 L6M but 0.503 older and 0.487 L3M; disp/breadth/ER best cells 0.05-0.09 edge in L6M with older-window placebo p 0.0-0.27. No lead. The purchase case for true breadth is not supported by this proxy.
- Rolling windows beyond 30 min (er/cross/nr/corr r60, r90): er_r60/r90 appear only in a few cells; nyam@60 er_r30 remains the single best market-label lead.
Walk-forward dollar calls (ridge-logistic on all inputs, refit every 14 days from 2024-07-01, target tD_q, flagA = top third of training scores; DP = pooled over sessions with session dummies, DS = a model per session; placebo = the same flags shifted 5..100 sessions back): all-session summary of mean rest-of-session D7 net per flagged vs unflagged session (placebo p = share of shifted flags with flagged net as low):
- DP15: OOS 2024-07..2026-04 $408 vs $913 (p 0.10); 2025 $155 vs $900 (p 0.00); L6M $1,527 vs $1,996 (p 0.00); L3M $1,086 vs $1,646 (p 0.00). Flag rate 36-58%, precision of tD_q 0.33-0.37 (lift 1.07-1.22). Holds in all four windows but flagged sessions still earn money.
- DS15: $181 vs $1,013 older (p 0.05), $374 vs $736 2025 (p 0.10), $1,114 vs $2,258 L6M (p 0.00), $931 vs $1,707 L3M (p 0.15).
- DP90 / DS90, DP60, DP30, DP0: placebo p mostly 0.4-1.0 for older windows; DP90 L6M $394 vs $2,251 (p 0.00) only.
- By session, calls trained pooled: london@90 (DP90) flagged mean -$699 (older), -$804 (2025), -$843 (L6M), +$1,236 (L3M) vs unflagged +$582/+$576/+$1,498/+$992, placebo p 0.00/0.05/0.00/0.40: the best session call so far, lead holds older and L6M, not L3M. nyam@90 flagged -$363/-$520/+$673/+$44 vs -$91/-$250/+$293/-$424: no. nypm@15: flagged -$263/-$201 older/2025 but +$1,376/+$1,009 in L6M/L3M (flips). asia@15: flagged below unflagged in all windows (e.g. L6M $3,779 vs $4,671) but both are large positive: asia is D7's best session, any stand-down there is costly.
- False-alarm cost on best-5 weeks: flagged rest net inside best-5 weeks is +$28k (older, DP15) to +$149k (L6M DP0); it is the dollars given up. DP90 L6M -$13k (no cost) is the only version without forgone profit.
Conclusion: calls identify relatively worse sessions (lift 1.1-1.2, flagged mean about half the unflagged mean) but not net-losing ones, so the actions to test in step 3 should be size reductions (half size, tighter caps, nearer targets) rather than stand-down, triggered by: cut cluster in the last 120 min (nyam, london), range so far / ATR and vs implied move in london@90, and the pooled 15-minute score.
Files for W-CH2 (all in /mnt/l2/l2vast/_chop/f1/): calls_DP{0,15,30,60,90}.parquet and calls_DS{0,15,30,60,90}.parquet with columns day, sess, session_start_epoch, t1, call_epoch, chop_flag (flagA, ~1/3 of training scores), chop_flag_strict (flagB, ~top 20%), score, tD_q, rest_net, rest_cuts, rest_tgts, n_rest. Flags are NaN before 2024-07-01. The earlier calls_M/R/C/Rg/Y/A files (market label) remain.
Still open: per-order cancel rate (needs the MBO store; the replica gives net book decrease only), actual NQ option chain implied move at the clock (raw/NQ_opts is a raw OPRA-style pull, used only through UW NDX sigma and VIX here), YM history, true breadth (not purchased).

## 8. PASS 3 (lead order 2026-11-14 evening): cluster + vol-so-far calls, per session and per book, London at 90, flip-back
Code: code/th_chop1/ch_call3.py (features3.parquet, call3_scores.csv, calls3_*.parquet), ch_flip.py (flip_checkpoints.parquet, flip_scores.csv, flip_calls3_*.parquet). Added clock h=120. Inputs ONLY the consistent families: D7 cut cluster (stack + the book's own, 30/60/120 min, cuts without a target, cuts per target) and volatility so far / prior (range so far over ATR, volume vs normal, points per contract, range vs VIX/NDX implied move, overnight range, prior range/ATR, range forecast a/b/c rank). Targets tD_q (rest net worst tercile) and tD_cpt (rest cuts per target top tercile); per book tq_<book> from that book's own rest-of-session dollars. Ridge-logistic, walk-forward refit every 14 days from 2024-07-01, one model per session for the stack calls, pooled with session dummies for the book calls. Flags at training-score quantiles: f40, f33, f20, f10 = top 40/33/20/10%. Placebo p = flagged net vs the same flags shifted 5..100 sessions back (forward-only).

First call that holds in older, 2025, L6M AND L3M with placebo p <= 0.15 everywhere: LONDON, cut cluster + vol so far, per-session model, target tD_cpt, 90 minutes (S_tD_cpt_90, london):
- f33 (flags 48-69% of London sessions that have a D7 trade after the call): mean rest-of-session D7 net per flagged session -$487 older (n 442, session net -$112k), -$668 in 2025, -$641 L6M (-$49k), -$21 L3M (n 55) vs unflagged +$726 / +$838 / +$2,349 / +$2,623; cuts per target 1.38-1.47 flagged vs 0.95-1.06; placebo p 0.00 in all four windows.
- f40 same picture (-$356/-$520/-$565/+$10 vs +$770/+$867/+$3,318/+$3,294); S_tD_cpt_120 f20: -$93/-$720/-$1,480/-$524 vs +$406/+$582/+$1,661/+$1,504 (p 0.15/0.00/0.00/0.05); S_tD_q_90 f20: -$796/-$1,253/-$1,032/-$69 (p 0.05/0.05/0.00/0.10).
- Cost: flagged London sessions that fall in the best-5 weeks hold +$17k (older) / +$8k (2025) of D7 profit, -$16k in L6M; the best-5 weeks are mostly pre-2026 so the L3M/L6M columns have none.
- Still a stand-down call on London only: flagged mean is about zero to negative, so removing them is worth roughly +$100k per 22 months older and +$49k in L6M at f33; the effect is concentrated, not diffuse (flagged median -$1.4k to -$2.3k against +$0.3k to +$0.8k unflagged in the DP90 version).
Why the pooled DP90 London call failed in L3M (mean +$1,236 flagged): three flagged days (2026-08-03 +$10.3k, 08-10 +$14.6k, 09-15 +$17.0k, each 7-9 targets and 3-5 cuts) carry it; the flagged MEDIAN stays negative in every window (-$1.4k / -$2.3k / -$1.4k vs +$0.3k / +$0.8k / +$0.6k unflagged). Flagged London sessions have range so far 0.68 ATR vs 0.43 (the 90-min window), volume 1.37x vs 0.99x normal, range 1.6x VIX-implied vs 1.03x, 1.56 vs 1.09 cuts in the last 120 min. By weekday flagged Tuesday is -$2,482 (n 47) vs +$1,471 unflagged, Friday +$477; event days (E_ev_day) weaker (-$367 flagged vs +$408), non-event -$784 vs +$1,184; opex week the call does not work (+$494 flagged), outside it -$1,040 vs +$763; by half-year the pooled call flips in 2025H2 (+$1,453 flagged), so it is not year-stable; the per-session cluster+vol call is. 2026-W44 is not in the flagged London set (calls end before it for 90 min), removing it changes nothing.
Other versions that hold older/L6M/L3M with flagged mean negative: B_K7_90 London f33 (K7's own rest net -$372/-$241/-$580/-$633 vs +$233/+$147/+$372/+$579; cuts per target 1.63-1.90 vs 0.91-1.15; p 0.00/0.25/0.00/0.00); B_H7_30 asia f33 (H7 -$310/-$190/+$123/-$791 vs +$548/+$369/+$748/+$355, flips in L6M); B_M7_60 London f40 and B_M7_15 f10 weakly. K7 is the only book whose own cut cluster gives a clean London call. P7, U7, A7: no stable book call.
Stack all-session f33 (any session): DP-style gaps of 0.1 to 0.2 of the unflagged mean; negative flagged mean only in London and nyam subsets (S_tD_q_15/120 nyam f20: -$580/-$199 older, -$524/-$185 L6M, -$233/-$240 L3M).
Flip-back (call turns off) at 15-minute checkpoints, thresholds fixed on days before 2024-07: ER of the last 30 min >= p75 of its session (asia 0.26, london 0.27, nyam 0.28, nypm 0.28) OR last-15-min range >= p90 of (that range / median earlier 15-min range) (1.63, 1.79, 1.25, 1.70). 70-100% of flagged sessions turn off before the end. For S_tD_cpt_90 f33 all sessions: D7 net per trade while the call is on -$63 older / +$46 L6M / -$204 L3M (net -$66k / +$19k / -$28k); after it turns off +$78 / +$115 / +$81 per trade (+$247k / +$195k / +$41k), i.e. trades after the flip behave like normal ones. DP90: on -$68/-$3/-$239, after +$165/+$60/+$256. S_tD_q_90: on +$11/+$52/-$224, after +$120/+$123/+$40. So restoring everything at the flip is supported; the chop mode is only worth running while it is on.
Files for W-CH2 (all /mnt/l2/l2vast/_chop/f1/): calls3_S_<tD_q|tD_cpt>_<h>.parquet (stack, per session model), calls3_B_<book>_<h>.parquet (per book), h in 0,15,30,60,90,120; columns day, sess, call_epoch, h, score, f40, f33, f20, f10 (NaN before 2024-07-01), n_rest/rest_net/cuts/tgts for the target. flip_calls3_*.parquet add off_epoch (NaN = never off) for the f33 flag; flip_calls_DP*/DS* for the pass-2 calls. Exact-engine candidate for step 3: London, flag f33 of S_tD_cpt_90 (and its f20/f40 variants), K7-only variant B_K7_90, with off_epoch for the restore.
CME option-chain implied move from raw/NQ_opts: left to W-R2 (a5fc40b3e78059b7b), no file yet; I used VIX/UW NDX sigma only.


## 9. ADDENDUM GAPS (user, 2026-11-14): standard gauges, HTF context, profile, effort, clock, gamma, sector spread, regime model, combinations (built 23:30Z)
LOT BASIS AND FEES (dollar columns only): every dollar figure in this section is JN05W2 exact-engine BASE lots (live user lots = x1.75), fees per outputs/FEES.md (NQ round trip $4.84 proxy, already inside net_fee). Label unchanged (sha afc0dbedcbd15899); benchmarks "yesterday was chop" (prev_chop) and ATR; shifted-session placebos; walk-forward; no PASS claimed.
Code: code/th_chop1/ch_feat4.py/ch_feat5.py (gauges, HTF, profile, effort, clock, gamma, ETF; clocks now 0,15,30,45,60,75,90,105,120), ch_regime.py (HMM), ch_feat6.py (regime, ZN, clock rates), ch_eval4.py + ch_table.py (single-input table), ch_comb.py (combinations), ch_top10.py. Data: /mnt/l2/l2vast/_chop/f1/features6.parquet (32,643 session-clock rows, 386 columns), eval6_all.parquet, input_table.csv/.md, comb_scores.csv, top10_scores.csv, top10_inputs.txt, regime_5m.parquet. Causality: a 1m bar is used only if bar_ts+60 <= call epoch; gauges use windows [T-30/60/120 min, T) and [session start, T); HTF context uses Globex days before the session day only; gamma and ETF use the previous day / data before T; HMM is fitted on data before each cutoff (2024-07-01, 2025-01-01, 2025-07-01, 2026-01-01, 2026-07-01) and forward-filtered (no smoothing); delta is approximated per 1m bar as volume x (close-open)/range because the 1m store has no signed volume.
Input counts: 352 single inputs per clock (ALL), 281 that D7 can compute itself (OWN); 9 clocks x 4 sessions x 3 targets = 11,364 cells per target scanned.

### 9.1 Which input families forecast (share of session x clock x input cells that hold in older, 2025, L6M and L3M with placebo p <= 0.10/0.15 and a positive edge vs the benchmark)
| family | market-shape label | D7 tD_q (rest net worst tercile) | D7 tD_cpt (cuts per target) |
|--|--|--|--|
| HMM 2/3-state regime P(choppy) | 0.0% | 10.1% | 31.2% |
| implied move ratio (range so far / VIX or NDX implied) | 0.0% | 20.3% | 31.2% |
| range forecast a/b/c | 2.5% | 2.0% | 19.1% |
| VIX / VVIX / implied correlation (Cboe, fetched) | 3.0% | 2.2% | 12.1% |
| standard gauges (ADX/DI, CHOP index, BB/KC width and squeeze, variance ratio, Hurst, lag-1 AC, fractal ER; 1/3/5/15-min bars; sf, 30/60/120) | 0.7% | 6.3% | 10.2% |
| mbp-10 book (balance, depth, pull, quote age) | 0.8% | 4.9% | 10.1% |
| developing profile (VA width, peaks, POC migration, time in VA, rotations) | 2.1% | 2.9% | 8.3% |
| higher-timeframe context (inside day, NR4/NR7, 3/5/10-day position, 5-day VA, daily and 4h ER, days since 2-ATR day) | 2.6% | 1.5% | 6.5% |
| bars / prior day (ER, crossings, volume ratio, NQ-ES-RTY corr) | 2.0% | 2.8% | 5.0% |
| clock + past chop rates (dow, lunch, Friday pm, holiday week, month end) | 3.0% | 5.8% | 4.0% |
| D7 cut cluster (stack and per book) | 0.9% | 1.2% | 3.3% |
| dealer gamma (sign, size rank, distance to flip, 0DTE share) | 4.4% | 4.8% | 3.2% |
| ETF sector spread (QQQ SPY IWM DIA XLE XOP; XLK and SMH are not on the UW plan) | 4.7% | 3.1% | 1.6% |
| effort vs result | 1.4% | 4.5% | 1.4% |
| ZN inactivity (instr_1s, to 2026-10-16) | 1.9% | 0.6% | 1.2% |
| calendar flags | 1.6% | 0.8% | 1.2% |
| UW megacap proxy | 0.8% | 1.6% | 0.0% |
Reading: the market-shape label sits at the 1.5% rate seen for noise, so NO new input forecasts "this session will be an inefficient session" better than chance. The D7-dollar targets are forecast by volatility already seen and regime state (D7 cuts more per target when the session is active, not when it is quiet), the quiet-chop idea is not supported. 2026-W44 is not in any window that matters for the consistent cells.
Specific answers: HMM regime P(choppy state) forecasts D7 cuts per target (asia, mean P since session start at 90 min: edge +0.10 OLD2, +0.16 L6M, +0.21 L3M, placebo p 0.00) and, for the market label, asia at 120 min is positive in OLD2/L6M/L3M (+0.09/+0.17/+0.15) but the regime exists only from 2024-07 so the older-window rule (OLD1) fails it: 0 of 104 market cells pass; gamma sign/size/flip distance: no stand-alone forecast (3-5% of cells, chance level) - input only as ordered; sector spread: chance level (1.6-4.7%); ZN: chance level, the bond-inactivity idea is not supported on the ZN already on the box.

### 9.2 One table: every input (collapsed over bar size/window/clock), per session. A L N P = asia london nyam nypm sessions in which at least one cell forecasts (all four windows, placebo p, positive gain); gain = best L6M edge (AUC-0.5) minus the better of the two benchmark edges (never below 0)
| input (family:name) | market label: sessions that forecast (A L N P) | best gain over benchmark (L6M edge) | D7 tD_q | gain | D7 tD_cpt | gain | best cell (tD_cpt or best) |
|--|--|--|--|--|--|--|--|
| bars:corr_nq_es | .... | - | .L.. | +0.11 | AL.. | +0.14 | tD_cpt london corr_nq_es_sf h90 OLD2 +0.04 L6M +0.14 L3M +0.18 |
| bars:corr_nq_es_r60 | .... | - | .L.. | +0.10 | AL.. | +0.14 | tD_cpt london corr_nq_es_r60 h90 OLD2 +0.02 L6M +0.14 L3M +0.17 |
| bars:corr_nq_es_r90 | .... | - | .L.. | +0.10 | AL.. | +0.14 | tD_cpt london corr_nq_es_r90 h90 OLD2 +0.04 L6M +0.14 L3M +0.18 |
| bars:corr_nq_rty | .L.. | +0.04 | .... | - | .L.. | +0.06 | tD_cpt london corr_nq_rty_sf h105 OLD2 +0.02 L6M +0.07 L3M +0.02 |
| bars:corr_nq_rty_r60 | .L.. | +0.01 | .... | - | .... | - | target london corr_nq_rty_r60 h90 OLD2 +0.05 L6M +0.08 L3M +0.02 |
| bars:corr_nq_rty_r90 | .L.. | +0.02 | .... | - | .... | - | target london corr_nq_rty_r90 h90 OLD2 +0.05 L6M +0.08 L3M +0.04 |
| bars:cross | ...P | +0.01 | A.N. | +0.14 | A... | +0.05 | tD_q nyam cross_r30 h45 OLD2 +0.05 L6M +0.15 L3M +0.12 |
| bars:cross_r60 | .... | - | A... | +0.06 | A... | +0.05 | tD_q asia cross_r60 h105 OLD2 +0.04 L6M +0.09 L3M +0.09 |
| bars:cross_r90 | .... | - | A... | +0.05 | A... | +0.05 | tD_cpt asia cross_r90 h45 OLD2 +0.04 L6M +0.11 L3M +0.08 |
| bars:disp | ...P | +0.04 | .L.. | +0.05 | AL.. | +0.19 | tD_cpt london disp_sf h90 OLD2 +0.04 L6M +0.19 L3M +0.00 |
| bars:er | ..N. | +0.04 | A... | +0.14 | A... | +0.03 | tD_q asia er_sf h45 OLD2 +0.06 L6M +0.14 L3M +0.13 |
| bars:er_r60 | ..N. | +0.08 | A... | +0.14 | AL.. | +0.12 | tD_q asia er_r60 h45 OLD2 +0.06 L6M +0.14 L3M +0.13 |
| bars:er_r90 | .... | - | A... | +0.14 | A... | +0.03 | tD_q asia er_r90 h45 OLD2 +0.06 L6M +0.14 L3M +0.13 |
| bars:nr | ..N. | +0.05 | A... | +0.11 | .... | - | tD_q asia nr_sf h75 OLD2 +0.04 L6M +0.13 L3M +0.23 |
| bars:nr_r60 | ..N. | +0.07 | A... | +0.06 | .L.. | +0.09 | tD_cpt london nr_r60 h75 OLD2 +0.05 L6M +0.11 L3M +0.13 |
| bars:nr_r90 | .... | - | A... | +0.11 | .... | - | tD_q asia nr_r90 h75 OLD2 +0.04 L6M +0.13 L3M +0.23 |
| bars:ppc_ratio | .... | - | ..N. | +0.03 | .... | - | tD_q nyam ppc_ratio h75 OLD2 +0.05 L6M +0.05 L3M +0.10 |
| bars:rng_sf_atr | ..N. | +0.08 | .L.. | +0.11 | AL.. | +0.18 | tD_cpt london rng_sf_atr h90 OLD2 +0.09 L6M +0.18 L3M +0.19 |
| bars:rsflip | ...P | +0.13 | AL.. | +0.11 | AL.. | +0.07 | target nypm rsflip_sf h105 OLD2 +0.02 L6M +0.13 L3M +0.04 |
| bars:vol_ratio | .... | - | .L.. | +0.14 | AL.. | +0.16 | tD_cpt london vol_ratio h90 OLD2 +0.09 L6M +0.16 L3M +0.19 |
| book:aimb5 | ..N. | +0.05 | .... | - | .... | - | target nyam mb_aimb5_sf h15 OLD2 +0.06 L6M +0.08 L3M +0.05 |
| book:churn_tr | .... | - | .... | - | .... | - |  |
| book:churn_tr_r30 | .... | - | .... | - | .L.. | +0.07 | tD_cpt london mb_churn_tr_r30_rel h75 OLD2 +0.02 L6M +0.09 L3M +0.14 |
| book:churn_tr_sf | .... | - | .... | - | .... | - |  |
| book:dep10 | ...P | +0.03 | .LN. | +0.07 | AL.. | +0.07 | tD_cpt asia mb_dep10_r30 h90 OLD2 +0.08 L6M +0.15 L3M +0.19 |
| book:dep10_r30 | .... | - | .L.. | +0.09 | A... | +0.04 | tD_q london mb_dep10_r30_rel h120 OLD2 +0.05 L6M +0.11 L3M +0.05 |
| book:dep10_sf | .... | - | ..N. | +0.04 | A... | +0.02 | tD_q nyam mb_dep10_sf_rel h60 OLD2 +0.02 L6M +0.07 L3M +0.05 |
| book:imb5 | .... | - | ALN. | +0.15 | .... | - | tD_q london mb_imb5_sf h30 OLD2 +0.02 L6M +0.15 L3M +0.12 |
| book:maxage | .... | - | A... | +0.04 | ALN. | +0.06 | tD_cpt asia mb_maxage_r30 h120 OLD2 +0.09 L6M +0.16 L3M +0.19 |
| book:maxage_r30 | .... | - | .L.. | +0.08 | .L.. | +0.10 | tD_cpt london mb_maxage_r30_rel h90 OLD2 +0.08 L6M +0.10 L3M +0.14 |
| book:maxage_sf | .... | - | .L.. | +0.09 | .L.. | +0.12 | tD_cpt london mb_maxage_sf_rel h90 OLD2 +0.10 L6M +0.12 L3M +0.20 |
| book:nchg | .... | - | .LN. | +0.05 | ALN. | +0.08 | tD_cpt london mb_nchg_sf h105 OLD2 +0.08 L6M +0.09 L3M +0.15 |
| book:nchg_r30 | .... | - | .L.. | +0.09 | ALN. | +0.11 | tD_cpt london mb_nchg_r30_rel h105 OLD2 +0.08 L6M +0.12 L3M +0.16 |
| book:nchg_sf | .... | - | .LN. | +0.09 | ALN. | +0.14 | tD_cpt london mb_nchg_sf_rel h90 OLD2 +0.11 L6M +0.14 L3M +0.22 |
| book:pull_tr | ..N. | -0.02 | .... | - | .... | - | target nyam mb_pull_tr_sf h60 OLD2 +0.05 L6M +0.04 L3M +0.10 |
| book:pull_tr_r30 | ..N. | -0.02 | .... | - | .L.. | +0.07 | tD_cpt london mb_pull_tr_r30_rel h75 OLD2 +0.02 L6M +0.09 L3M +0.14 |
| book:pull_tr_sf | ..N. | -0.01 | .... | - | .... | - | target nyam mb_pull_tr_sf_rel h60 OLD2 +0.06 L6M +0.05 L3M +0.06 |
| book:spread | .... | - | .L.. | +0.01 | AL.. | +0.08 | tD_cpt london mb_spread_sf h120 OLD2 +0.08 L6M +0.14 L3M +0.13 |
| calendar:E_earn_prev | .... | - | .... | - | .... | - |  |
| calendar:E_ev_day | A.N. | +0.06 | .... | - | .... | - | target nyam E_ev_day h75 OLD2 +0.04 L6M +0.06 L3M +0.06 |
| calendar:E_hi_day | .... | - | .... | - | .L.. | +0.04 | tD_cpt london E_hi_day h30 OLD2 +0.02 L6M +0.05 L3M +0.06 |
| calendar:cal_fomcish | .... | - | .... | - | .... | - |  |
| calendar:monthend | .... | - | .... | - | .... | - |  |
| calendar:opexday | .... | - | .... | - | .... | - |  |
| calendar:opexweek | ..NP | +0.05 | ..N. | +0.07 | .... | - | tD_q nyam opexweek h45 OLD2 +0.06 L6M +0.08 L3M +0.09 |
| clock:dow | .... | - | .... | - | .... | - |  |
| clock:fripm | .... | - | .... | - | .... | - |  |
| clock:holweek | .... | - | .... | - | .... | - |  |
| clock:lunch | .... | - | .... | - | .... | - |  |
| clock:rate_dow_tD_cpt | .... | - | ..N. | +0.07 | ..N. | +0.05 | tD_q nyam clk_rate_dow_tD_cpt h90 OLD2 +0.03 L6M +0.10 L3M +0.14 |
| clock:rate_dow_tD_q | .... | - | .L.. | +0.11 | ..N. | +0.03 | tD_q london clk_rate_dow_tD_q h75 OLD2 +0.05 L6M +0.11 L3M +0.13 |
| clock:rate_dow_target | ..N. | +0.04 | .... | - | A... | +0.05 | tD_cpt asia clk_rate_dow_target h105 OLD2 +0.02 L6M +0.14 L3M +0.07 |
| clock:rate_hol_tD_cpt | .L.. | -0.00 | ..N. | +0.18 | .LN. | +0.24 | tD_cpt nyam clk_rate_hol_tD_cpt h60 OLD2 +0.07 L6M +0.24 L3M +0.29 |
| clock:rate_hol_tD_q | .... | - | ALN. | +0.16 | ALN. | +0.25 | tD_cpt nyam clk_rate_hol_tD_q h90 OLD2 +0.03 L6M +0.26 L3M +0.26 |
| clock:rate_hol_target | ALNP | +0.12 | .L.. | +0.04 | .... | - | target nyam clk_rate_hol_target h75 OLD2 +0.05 L6M +0.12 L3M +0.19 |
| clock:rate_me_tD_cpt | AL.. | +0.04 | ..N. | +0.17 | ..N. | +0.09 | tD_q nyam clk_rate_me_tD_cpt h75 OLD2 +0.05 L6M +0.19 L3M +0.17 |
| clock:rate_me_tD_q | .... | - | ALN. | +0.15 | A... | +0.15 | tD_q london clk_rate_me_tD_q h0 OLD2 +0.04 L6M +0.15 L3M +0.09 |
| clock:rate_me_target | .LNP | +0.10 | .L.. | +0.04 | A... | +0.02 | target nypm clk_rate_me_target h45 OLD2 +0.06 L6M +0.14 L3M +0.17 |
| clock:tod | .... | - | .... | - | .... | - |  |
| cluster:cut | ...P | +0.08 | .L.. | +0.11 | ALN. | +0.10 | tD_q london cut_120 h60 OLD2 +0.04 L6M +0.11 L3M +0.17 |
| cluster:cut_A7 | .... | - | .... | - | .... | - |  |
| cluster:cut_H7 | .... | - | .... | - | .... | - |  |
| cluster:cut_K7 | .... | - | .... | - | ALN. | +0.10 | tD_cpt nyam cut_K7_120 h75 OLD2 +0.06 L6M +0.10 L3M +0.12 |
| cluster:cut_M7 | ..NP | +0.10 | .L.. | +0.06 | .LN. | +0.04 | target nyam cut_M7_120 h105 OLD2 +0.03 L6M +0.11 L3M +0.09 |
| cluster:cut_P7 | .... | - | .LN. | +0.08 | .LN. | -0.02 | tD_q london cut_P7_120 h15 OLD2 +0.03 L6M +0.08 L3M +0.09 |
| cluster:cut_U7 | .... | - | .... | - | .... | - |  |
| cluster:cutnt | .... | - | .L.. | +0.04 | ALN. | +0.03 | tD_q london cutnt_30 h15 OLD2 +0.03 L6M +0.04 L3M +0.13 |
| cluster:cutnt_A7 | .... | - | .... | - | .... | - |  |
| cluster:cutnt_H7 | .... | - | .... | - | .... | - |  |
| cluster:cutnt_K7 | ..N. | +0.06 | ..N. | +0.06 | A.N. | +0.13 | tD_cpt nyam cutnt_K7_120 h45 OLD2 +0.05 L6M +0.13 L3M +0.11 |
| cluster:cutnt_M7 | ..NP | +0.08 | .L.. | +0.06 | .... | - | target nypm cutnt_M7_120 h60 OLD2 +0.02 L6M +0.10 L3M +0.12 |
| cluster:cutnt_P7 | .... | - | .LN. | +0.05 | .... | - | tD_q nyam cutnt_P7_30 h75 OLD2 +0.04 L6M +0.07 L3M +0.11 |
| cluster:cutnt_U7 | .... | - | .... | - | .... | - |  |
| cluster:cutratio | ..NP | +0.13 | .L.. | +0.04 | ALN. | +0.04 | target nyam cutratio_120 h105 OLD2 +0.02 L6M +0.14 L3M +0.14 |
| effort:adelta_pp | .L.P | +0.05 | A... | +0.07 | .... | - | tD_q asia ef_adelta_pp_15 h90 OLD2 +0.04 L6M +0.10 L3M +0.26 |
| effort:dflip_ph | .L.P | +0.06 | .... | - | .L.. | +0.20 | tD_cpt london ef_dflip_ph h75 OLD2 +0.03 L6M +0.22 L3M +0.24 |
| effort:ext_age | .... | - | A... | +0.12 | .... | - | tD_q asia ef_ext_age h75 OLD2 +0.06 L6M +0.13 L3M +0.24 |
| effort:ext_vol | .... | - | A... | +0.13 | .L.. | +0.09 | tD_q asia ef_ext_vol h60 OLD2 +0.07 L6M +0.14 L3M +0.23 |
| effort:vol_pp | .... | - | AL.. | +0.05 | .L.. | +0.09 | tD_cpt london ef_vol_pp_60 h75 OLD2 +0.05 L6M +0.11 L3M +0.12 |
| gamma:0dte_share | ..N. | +0.13 | AL.. | +0.14 | .L.. | +0.11 | tD_q asia gm_0dte_share h30 OLD2 +0.02 L6M +0.14 L3M +0.21 |
| gamma:dir_sign | .LN. | +0.11 | .L.. | +0.01 | .... | - | target london gm_dir_sign h60 OLD2 +0.04 L6M +0.17 L3M +0.09 |
| gamma:flip_dist | .L.. | +0.06 | ..N. | +0.06 | A... | +0.05 | target london gm_flip_dist h90 OLD2 +0.06 L6M +0.13 L3M +0.06 |
| gamma:gk_net | ..N. | +0.08 | .... | - | .... | - | target nyam gm_gk_net h90 OLD2 +0.03 L6M +0.08 L3M +0.12 |
| gamma:sign | ..N. | +0.05 | .... | - | .... | - | target nyam gm_sign h90 OLD2 +0.02 L6M +0.05 L3M +0.10 |
| gamma:size_rank | ..N. | +0.07 | A... | +0.02 | AL.. | +0.08 | tD_cpt london gm_size_rank h120 OLD2 +0.06 L6M +0.13 L3M +0.18 |
| gamma:zc | A..P | +0.03 | A... | +0.07 | .... | - | tD_q asia gm_zc h120 OLD2 +0.04 L6M +0.11 L3M +0.05 |
| gauge:ac1 | ALN. | +0.09 | A.N. | +0.05 | ALN. | +0.13 | tD_cpt nyam g1_r60_ac1 h90 OLD2 +0.03 L6M +0.14 L3M +0.18 |
| gauge:bbw | ..N. | +0.08 | AL.. | +0.14 | ALN. | +0.19 | tD_cpt london g1_r60_bbw h90 OLD2 +0.04 L6M +0.19 L3M +0.21 |
| gauge:chi | .... | - | AL.. | +0.10 | ALN. | +0.14 | tD_cpt london g5_r120_chi h90 OLD2 +0.03 L6M +0.14 L3M +0.11 |
| gauge:disp | A.N. | +0.01 | ..N. | +0.11 | ALN. | +0.13 | tD_cpt nyam g1_r30_disp h75 OLD2 +0.05 L6M +0.13 L3M +0.24 |
| gauge:dx | ..NP | +0.07 | A.N. | +0.12 | .LN. | +0.10 | tD_q asia g1_sf_dx h45 OLD2 +0.05 L6M +0.13 L3M +0.04 |
| gauge:er | ..N. | +0.08 | A... | +0.14 | ALN. | +0.18 | tD_cpt london g15_sf_er h90 OLD2 +0.04 L6M +0.18 L3M +0.14 |
| gauge:hurst | ALN. | +0.07 | A... | +0.03 | AL.. | +0.06 | target nyam g1_r30_hurst h105 OLD2 +0.02 L6M +0.08 L3M +0.11 |
| gauge:kcw | .... | - | ALN. | +0.09 | AL.. | +0.13 | tD_cpt london g15_sf_kcw h90 OLD2 +0.06 L6M +0.13 L3M +0.22 |
| gauge:sqz | .... | - | AL.. | +0.12 | ALN. | +0.14 | tD_cpt london g5_r120_sqz h90 OLD2 +0.03 L6M +0.14 L3M +0.07 |
| gauge:vr4 | ...P | +0.12 | ALN. | +0.10 | ALN. | +0.14 | tD_cpt london g1_r30_vr4 h90 OLD2 +0.06 L6M +0.14 L3M +0.05 |
| htf:d_er10 | .... | - | .... | - | .... | - |  |
| htf:days_since_big | .... | - | .... | - | .... | - |  |
| htf:h4_er | .... | - | .... | - | ..N. | +0.10 | tD_cpt nyam ctx_h4_er h75 OLD2 +0.03 L6M +0.10 L3M +0.11 |
| htf:in_va5 | .... | - | .... | - | .... | - |  |
| htf:inside_day | .... | - | .... | - | .... | - |  |
| htf:nr4 | .... | - | .... | - | .... | - |  |
| htf:nr7 | .... | - | .... | - | .... | - |  |
| htf:poc5_dist_atr | A... | +0.04 | .... | - | .... | - | target asia ctx_poc5_dist_atr h15 OLD2 +0.02 L6M +0.11 L3M +0.12 |
| htf:pos10d | .L.. | +0.01 | .L.. | +0.07 | AL.. | +0.08 | tD_cpt london ctx_pos10d h105 OLD2 +0.07 L6M +0.08 L3M +0.21 |
| htf:pos3d | .L.. | +0.04 | A.N. | +0.08 | AL.. | +0.11 | tD_cpt asia ctx_pos3d h90 OLD2 +0.09 L6M +0.20 L3M +0.17 |
| htf:pos5d | .L.. | +0.03 | ..N. | +0.05 | AL.. | +0.08 | tD_cpt asia ctx_pos5d h90 OLD2 +0.08 L6M +0.16 L3M +0.14 |
| htf:rng10d_atr | .... | - | .... | - | .... | - |  |
| htf:rng3d_atr | A... | +0.01 | .... | - | .... | - | target asia ctx_rng3d_atr h60 OLD2 +0.06 L6M +0.11 L3M +0.19 |
| htf:rng5d_atr | A... | -0.04 | AL.. | +0.10 | A... | +0.04 | tD_q asia ctx_rng5d_atr h30 OLD2 +0.04 L6M +0.10 L3M +0.09 |
| htf:va5_dist_atr | .... | - | .... | - | ..N. | +0.10 | tD_cpt nyam ctx_va5_dist_atr h75 OLD2 +0.03 L6M +0.10 L3M +0.14 |
| implied:ndx_ratio | .... | - | AL.. | +0.11 | AL.. | +0.16 | tD_cpt london imp_ndx_ratio h90 OLD2 +0.07 L6M +0.16 L3M +0.20 |
| implied:vix_ratio | .... | - | .L.. | +0.08 | AL.. | +0.15 | tD_cpt london imp_vix_ratio h90 OLD2 +0.07 L6M +0.15 L3M +0.21 |
| megacap:breadth | ...P | +0.05 | .... | - | .... | - | target nypm mg_breadth_sf h60 OLD2 +0.04 L6M +0.07 L3M +0.04 |
| megacap:corr | .... | - | ..N. | +0.06 | .... | - | tD_q nyam mg_corr_r30 h105 OLD2 +0.06 L6M +0.09 L3M +0.07 |
| megacap:disp | .... | - | .... | - | .... | - |  |
| megacap:er | .... | - | .... | - | .... | - |  |
| prior:d_poc_atr | .L.. | +0.05 | .... | - | .... | - | target london d_poc_atr h105 OLD2 +0.04 L6M +0.10 L3M +0.07 |
| prior:er_prev | .L.P | +0.05 | .... | - | .... | - | target london er_prev1 h60 OLD2 +0.05 L6M +0.12 L3M +0.14 |
| prior:gap_atr | ..N. | +0.08 | .... | - | .... | - | target nyam gap_atr h120 OLD2 +0.05 L6M +0.08 L3M +0.20 |
| prior:in_rng | ..NP | +0.08 | .... | - | .... | - | target nyam in_rng h120 OLD2 +0.02 L6M +0.08 L3M +0.14 |
| prior:in_va | .... | - | .... | - | .... | - |  |
| prior:latr | .... | - | .... | - | A... | +0.00 | tD_cpt asia latr h90 OLD2 +0.05 L6M +0.08 L3M +0.09 |
| prior:on6_atr | .... | - | .L.. | +0.06 | AL.. | +0.11 | tD_cpt london on6_atr h90 OLD2 +0.06 L6M +0.11 L3M +0.15 |
| prior:prev_big | A... | -0.09 | .... | - | .... | - | target asia prev_big h75 OLD2 +0.02 L6M +0.03 L3M +0.03 |
| prior:prev_chop | .L.P | +0.03 | .... | - | .... | - | target nypm prev_chop3 h120 OLD2 +0.05 L6M +0.12 L3M +0.20 |
| prior:prev_cs | AL.P | +0.07 | .LN. | +0.10 | ..N. | +0.12 | tD_cpt nyam prev_cs h75 OLD2 +0.06 L6M +0.12 L3M +0.11 |
| prior:prev_rng_atr | A... | -0.02 | .... | - | A.N. | +0.05 | tD_cpt asia prev_rng_atr h30 OLD2 +0.03 L6M +0.08 L3M +0.12 |
| profile:in_va | .L.. | +0.10 | .L.. | +0.08 | ..N. | +0.12 | tD_cpt nyam pf_in_va h45 OLD2 +0.06 L6M +0.12 L3M +0.10 |
| profile:npeaks | .... | - | .... | - | .... | - |  |
| profile:poc_mig | A... | +0.03 | .... | - | ..N. | +0.12 | tD_cpt nyam pf_poc_mig h45 OLD2 +0.03 L6M +0.12 L3M +0.15 |
| profile:poc_mig_abs | A.N. | +0.05 | A... | +0.08 | .... | - | tD_q asia pf_poc_mig_abs h45 OLD2 +0.04 L6M +0.09 L3M +0.11 |
| profile:rot | .... | - | .... | - | .L.. | +0.00 | tD_cpt london pf_rot h120 OLD2 +0.03 L6M +0.06 L3M +0.07 |
| profile:rot_ph | .... | - | .... | - | .L.. | +0.00 | tD_cpt london pf_rot_ph h120 OLD2 +0.03 L6M +0.06 L3M +0.07 |
| profile:va_w_atr | ..N. | +0.07 | AL.. | +0.14 | AL.. | +0.21 | tD_cpt london pf_va_w_atr h90 OLD2 +0.08 L6M +0.21 L3M +0.20 |
| profile:va_w_rng | .... | - | .... | - | AL.. | +0.16 | tD_cpt london pf_va_w_rng h90 OLD2 +0.03 L6M +0.16 L3M +0.09 |
| rangefc:rf_pred | A... | -0.05 | .LN. | +0.10 | ALN. | +0.12 | tD_cpt london rfb_pred h105 OLD2 +0.05 L6M +0.12 L3M +0.08 |
| rangefc:rf_q10 | AL.. | -0.02 | AL.. | +0.11 | AL.. | +0.11 | tD_cpt london rfb_q10 h105 OLD2 +0.10 L6M +0.12 L3M +0.09 |
| rangefc:rf_q3 | ...P | -0.03 | .... | - | AL.. | +0.07 | tD_cpt london rfc_q3 h105 OLD2 +0.07 L6M +0.08 L3M +0.12 |
| rangefc:rf_q5 | AL.. | -0.02 | AL.. | +0.10 | AL.. | +0.11 | tD_cpt london rfb_q5 h105 OLD2 +0.09 L6M +0.12 L3M +0.12 |
| rangefc:rf_rk | AL.. | -0.02 | AL.. | +0.10 | AL.. | +0.12 | tD_cpt london rfb_rk h105 OLD2 +0.10 L6M +0.12 L3M +0.08 |
| rangefc:rfa | .L.. | -0.01 | .... | - | A... | +0.02 | tD_cpt asia rfa_rel h15 OLD2 +0.05 L6M +0.05 L3M +0.08 |
| rangefc:rfb | A..P | +0.04 | .... | - | AL.. | +0.11 | tD_cpt london rfb_rel h105 OLD2 +0.06 L6M +0.12 L3M +0.08 |
| rangefc:rfc | .... | - | .... | - | AL.. | +0.08 | tD_cpt london rfc_rel h105 OLD2 +0.07 L6M +0.08 L3M +0.09 |
| regime:rg2_p | .... | - | .L.. | +0.11 | ALN. | +0.09 | tD_q london rg2_p h60 OLD2 +0.09 L6M +0.11 L3M +0.13 |
| regime:rg2_p30 | .... | - | AL.. | +0.09 | AL.. | +0.12 | tD_cpt london rg2_p30 h90 OLD2 +0.04 L6M +0.12 L3M +0.21 |
| regime:rg2_psf | .... | - | .LN. | +0.06 | ALN. | +0.13 | tD_cpt asia rg2_psf h75 OLD2 +0.07 L6M +0.19 L3M +0.28 |
| regime:rg3_p | .... | - | .L.. | +0.13 | A... | +0.08 | tD_q london rg3_p h60 OLD2 +0.08 L6M +0.13 L3M +0.13 |
| regime:rg3_p30 | .... | - | .LN. | +0.08 | ALN. | +0.09 | tD_cpt asia rg3_p30 h75 OLD2 +0.07 L6M +0.16 L3M +0.25 |
| regime:rg3_psf | .... | - | .LN. | +0.07 | ALN. | +0.11 | tD_cpt london rg3_psf h90 OLD2 +0.06 L6M +0.11 L3M +0.18 |
| sector:disp | ..N. | +0.05 | ..N. | +0.06 | .... | - | tD_q nyam sec_disp h15 OLD2 +0.03 L6M +0.12 L3M +0.19 |
| sector:iwm_spy_flips | ..N. | +0.05 | ..N. | +0.05 | ..N. | +0.02 | target nyam sec_iwm_spy_flips h75 OLD2 +0.07 L6M +0.05 L3M +0.05 |
| sector:qqq_spy_flips | .... | - | .... | - | .... | - |  |
| sector:with | ..N. | +0.09 | .... | - | .... | - | target nyam sec_with h90 OLD2 +0.04 L6M +0.09 L3M +0.06 |
| volx:cor1m | .L.. | -0.01 | ..N. | +0.07 | .... | - | tD_q nyam cor1m h105 OLD2 +0.03 L6M +0.10 L3M +0.04 |
| volx:cor1m_chg5 | .LN. | +0.07 | .L.. | +0.06 | AL.. | +0.06 | target nyam cor1m_chg5 h75 OLD2 +0.03 L6M +0.07 L3M +0.15 |
| volx:cor1m_rank | .LN. | +0.02 | ..N. | +0.06 | A... | -0.01 | tD_q nyam cor1m_rank h105 OLD2 +0.03 L6M +0.09 L3M +0.03 |
| volx:cor3m | .... | - | .... | - | .... | - |  |
| volx:cor_term | .LN. | +0.10 | A.N. | +0.07 | .... | - | target london cor_term h120 OLD2 +0.04 L6M +0.11 L3M +0.19 |
| volx:vix | .L.. | +0.04 | .... | - | AL.. | +0.08 | tD_cpt london vix h120 OLD2 +0.03 L6M +0.13 L3M +0.03 |
| volx:vix9_term | .... | - | ..N. | +0.10 | AL.. | +0.11 | tD_cpt london vix9_term h105 OLD2 +0.03 L6M +0.12 L3M +0.04 |
| volx:vix_chg5 | .LN. | +0.10 | .... | - | AL.. | +0.07 | target london vix_chg5 h75 OLD2 +0.04 L6M +0.10 L3M +0.04 |
| volx:vix_rank | .L.. | +0.04 | .... | - | A... | +0.03 | target london vix_rank h75 OLD2 +0.04 L6M +0.04 L3M +0.10 |
| volx:vix_term | .L.. | +0.07 | A... | +0.07 | A.N. | +0.05 | tD_q asia vix_term h75 OLD2 +0.04 L6M +0.08 L3M +0.08 |
| volx:vvix | .... | - | .... | - | A... | +0.03 | tD_cpt asia vvix h120 OLD2 +0.10 L6M +0.13 L3M +0.11 |
| volx:vvix_chg5 | .... | - | .... | - | A... | +0.00 | tD_cpt asia vvix_chg5 h90 OLD2 +0.05 L6M +0.09 L3M +0.14 |
| volx:vvix_rank | ..N. | +0.05 | .... | - | A... | +0.02 | target nyam vvix_rank h45 OLD2 +0.02 L6M +0.09 L3M +0.15 |
| volx:vvix_vix | A... | -0.07 | .... | - | A... | +0.00 | tD_cpt asia vvix_vix h120 OLD2 +0.03 L6M +0.10 L3M +0.04 |
| zn:er | ...P | +0.06 | .... | - | .L.. | +0.05 | target nypm zn_er_sf h60 OLD2 +0.06 L6M +0.08 L3M +0.12 |
| zn:rng | ..N. | +0.06 | .... | - | .... | - | target nyam zn_rng_sf h90 OLD2 +0.05 L6M +0.06 L3M +0.04 |
| zn:rng_sf | ..N. | +0.06 | .L.. | +0.05 | .... | - | target nyam zn_rng_sf_rel h90 OLD2 +0.07 L6M +0.06 L3M +0.07 |
| zn:vol | .... | - | .... | - | A... | +0.00 | tD_cpt asia zn_vol_sf h75 OLD2 +0.04 L6M +0.07 L3M +0.11 |
| zn:vol_sf | .... | - | .... | - | .... | - |  |

### 9.3 Combination models (walk-forward, refit 14 d logistic / 28 d gradient boosting from 2024-07-01, thresholds on training scores, pooled with session dummies unless per-session)
Pooled AUC averaged over the 9 clocks (windows L3M / L6M / 2025 / 2024-07..2026-04):
- tD_cpt: HGB all inputs 0.564 / 0.556 / 0.546 / 0.550, HGB OWN 0.581 / 0.559 / 0.551 / 0.550, ridge-logistic all 0.515 / 0.530 / 0.551 / 0.548, per-session logistic 0.480-0.526. Benchmarks: yesterday-chop 0.512 / 0.516 / 0.479 / 0.483, ATR 0.493 / 0.503 / 0.517 / 0.515.
- tD_q: HGB 0.526 / 0.508 / 0.519 / 0.526 (OWN 0.541 / 0.525 / 0.520 / 0.521); logistic 0.505-0.525; benchmarks 0.48-0.53.
- market-shape label: all models 0.49-0.51 = chance.
Gain of the combination over the best single input (chosen on days before 2024-07 per session, scored out of sample): none. Per-session mean AUC of the combination for tD_cpt is 0.52-0.54 against 0.54-0.57 for the best single input; the best single input is the cut cluster / range-so-far / regime-state type listed in 9.1. The combination is NOT better than one good input; its value is the stable session-by-session ranking and the London result below.
Session-level dollar calls (flag = top third of training score, target tD_cpt or tD_q): 36 of 450 session x clock x model cells have a flagged mean net below the unflagged mean in all four windows and a negative flagged mean in at least three; 24 of them are London, 8 nypm, 4 nyam, none asia. Examples (mean rest-of-session D7 net per flagged session, L3M / L6M / 2025 / older, vs gap to unflagged):
- London, HGB on OWN inputs, tD_cpt, PRE-SESSION (clock 0): -$26 / -$297 / -$586 / -$148; gap +$2,691 / +$2,149 / +$1,302 / +$874.
- London, logistic OWN, tD_cpt, 90 min: -$322 / -$695 / -$171 / -$529; gap +$3,684 / +$3,262 / +$540 / +$1,236.
- London, HGB OWN tD_cpt at 75 min: -$566 / -$715 / -$319 / -$332; gap +$2,962 / +$1,931 / +$712 / +$741; at 90 min -$445 older, -$465 2025, -$383 L6M, +$212 L3M.
- London, HGB ALL tD_q at 60 min: -$359 / -$1,012 / -$134 / -$515 (gap +$2,691 / +$2,470 / +$260 / +$926); at 120 min -$1,341 / -$981 / -$157 / -$276.
- nypm 60 min per-session logistic: -$750 / -$60 / -$606 / -$218; nyam 75 min HGB tD_cpt: mixed (+$481 in L6M).
Pooled across all sessions no model gives a negative flagged mean in every window; London is the session where the call isolates net-losing sessions, consistent with section 8.
Top 10 inputs (permutation importance of the gradient-boosting model fitted before 2025-01-01, scored on 2025-01..2026-04; * = D7 can compute it itself from its own bars, book, trade log, clock):
- tD_cpt at 90 min: on6_atr* (overnight range / ATR), vol_ratio* (volume vs same-clock normal), vvix_rank, corr_nq_es_sf (NQ-ES correlation since session start), g1_sf_sqz* (Bollinger/Keltner squeeze, 1-min), mb_spread_sf*, g3_sf_ac1* (lag-1 AC, 3-min), ctx_pos10d* (position in 10-day range), rg3_p* (HMM P(choppy), needs the fitted HMM), cut_M7_120* (M7 cuts in last 120 min).
- tD_cpt at 60 min: g3_sf_dx* (3-min directional index since start), corr_nq_es_r30, rg2_p*, ef_adelta_pp_15* (abs cum delta per point of progress, 15 min), g1_sf_vr4*, ef_vol_pp_60*, mb_maxage_r30_rel* (longest unchanged inside quote), vvix_chg5, d_poc_atr*, corr_nq_rty_r30.
- tD_q at 60: er_r30*, mb_spread_sf*, mb_imb5_r30*, rg2_p*, imp_vix_ratio, mb_aimb5_r30*, mb_nchg_r30*, g3_r30_bbw*, g1_sf_vr4*.
- market label: nothing stable (er_prev1, ctx_pos5d, gap_atr, g1_r30 gauges at AUC 0.45-0.54).
Small version (ridge-logistic on the 10 best OWN-computable inputs, walk-forward from 2025-01-01; selection data end 2026-04-30 so L6M and L3M are clean; AUC L3M / L6M / 2025 on):
- tD_cpt 90 min: all 352 inputs 0.563 / 0.563 / 0.564; all 281 OWN inputs 0.616 / 0.595 / 0.564; top-10 0.680 / 0.634 / 0.599; top-10 OWN 0.701 / 0.626 / 0.593.
- tD_cpt 60 min: all 0.488 / 0.533 / 0.533; top-10 OWN 0.574 / 0.552 / 0.576. tD_cpt 15 min: all 0.527 / 0.495 / 0.557; top-10 OWN 0.596 / 0.545 / 0.562.
- tD_q: 0.50-0.57 whatever the set (nothing). Market label: 0.45-0.54.
So a small D7-computable version is as good as, or better than, the full model: the best chop (cuts-per-target) call is a ten-input score.

### 9.4 For the live build: what D7 can compute from its own bars and book at the signal second, and what is lost
OWN = NQ 1m bars it already sees (gauges on 1/3/5/15 bars, ER/crossings, volume vs same-clock normal, range so far / ATR, overnight range, prior-day and 3/5/10-day context and 5-day value area from its own history, developing profile, effort vs result), its own DOM (spread, balance, depth, pull, longest unchanged inside quote - the mbp-10 minute features are the replica of the same DOM), its own trade log (cuts in the last 30/60/120 min stack-wide and per book), the clock and the calendar, a past-only chop-rate table, the HMM state probability if the fitted 2-3 state model is shipped. NOT own: ES/RTY/YM (needs other charts: NQ-ES and NQ-RTY correlation and dispersion, which show in the top-10 for tD_cpt), VIX/VVIX/implied correlation (daily external, one number per day), UW gamma, ETF, megacaps, range-forecast versions b/c (UW IV), implied-move ratio.
Loss when restricted to OWN: none measurable. HGB tD_cpt pooled AUC 0.581 / 0.559 / 0.551 / 0.550 OWN vs 0.564 / 0.556 / 0.546 / 0.550 ALL; logistic 0.519 / 0.541 / 0.557 / 0.554 vs 0.515 / 0.530 / 0.551 / 0.548; top-10 OWN vs top-10 any: 0.701 vs 0.680 (L3M), 0.626 vs 0.634 (L6M). The London pre-session and 75-90 minute calls above use OWN inputs only.

### 9.5 Quotes only (nothing bought)
Databento (metadata cost only, GLBX.MDP3, ohlcv-1m, 2023-04-01..2026-11-14): ZN $0.00, ZB $0.00, 6E $0.00 (included in the current plan allowance); DX (ICE US, IFUS.IMPACT) $10.32. ZN is already on the box (instr_1s 1-second bars to 2026-10-16) and was tested: no forecast (chance level, 1-3% of cells); a dollar-index series (6E or DX) was not pulled although the 6E quote is $0.00 - say if you want the pull. News headline-count history: not quoted - Databento has no news dataset and no Benzinga/other price is on the box or reachable without an account; cost UNKNOWN, not bought. What the free calendar and VIX inputs already capture: event days and release times (calendar flags) and VIX/VVIX/COR level, rank and term give 12% of tD_cpt cells but only 3% for the market label, i.e. they carry the same activity information as range-so-far and the HMM state; a headline-count series would be a proxy for event activity that the event calendar already holds, so expect little extra.
Caveats: 11,364 cells per target were scanned, so a few percent pass by chance; the market-shape rate (1.5%) is the empirical chance level and only the D7-dollar targets exceed it. Holiday-week flags use missing-RTH days (21 found; Memorial Day and similar thin-volume days are not all caught).

### 9.6 Files for W-CH2 and W-D10
/mnt/l2/l2vast/_chop/f1/calls6_<HGB|LRp|LRs>_<ALL|OWN>_<target|tD_q|tD_cpt>_<h>.parquet (h = 0,15,30,45,60,75,90,105,120; HGB OWN and logistic ALL/per-session saved): day, sess, call_epoch, score, chop_flag (top third of training scores), the target, rest_net, n_rest. NaN before 2024-07-01. Best candidates for the exact engine: calls6_HGB_OWN_tD_cpt_0 (London pre-session), calls6_LRs_ALL_tD_cpt_90 / calls6_HGB_OWN_tD_cpt_75 (London), with off_epoch from the flip_calls3 files of section 8.


## 10. RESTART RE-STATEMENT 2026-11-15: weekly cluster-robust inputs table, nonsense 99th-percentile bar, bucket call files, per-minute API
Code: code/th_chop1/ch_zw.py, ch_zw_table.py (table), ch_api.py + ch_api_test.py (per-minute entry point); data /mnt/l2/l2vast/_chop/f1/zw_all.parquet, zw_wide_real.parquet, input_table_zw.csv/.md, chop_bucket_calls.parquet. Dollar columns: JN05W2 BASE lots (live x1.75), fee $4.84 NQ RT proxy included in net_fee. FIRST PASS.
Standard applied (replaces the placebo-p screen of sections 3 and 9.1 for every statement about "forecasts"): zw = z of the OLS slope of the 0/1 target on the rank-normalised input with ISO-WEEK cluster-robust (CR0) errors, in three windows OLDER 2023-04..2025-06, RECENT 2025-07..2026-10, L6M 2026-05..2026-10. Nonsense: 200 inputs per session x clock x target cell through the identical pipeline (100 circular shifts of real inputs of that cell, 60-400 sessions, which keeps their autocorrelation and missingness; 100 AR(1) noises, rho 0.5-0.95). Nonsense 99th-percentile |zw| bars: tD_cpt OLDER 3.18 / RECENT 3.57 / L6M 5.47; tD_q 3.14 / 4.18 / 5.85; market label 3.15 / 3.69 / 6.93. PASS = |zw| above the bar in RECENT and OLDER (OLDER skipped if the input did not exist), same sign, and same sign with |zw| > 2 in L6M. Inputs with one value in more than 90% of the sessions (sparse per-book cut counts) are excluded: they gave |zw| of 15-30 purely from tiny support (cut_U7, cut_H7, cut_A7) and are an artifact of CR0 with a handful of non-zero weeks.
Result (352 inputs x 9 clocks x 4 sessions x 3 targets): the nonsense pass rate under this rule is 0.16% (market label), 0.19% (tD_q), 0.16% (tD_cpt). Real inputs pass at 0.31% (market label), 0.15% (tD_q), 1.08% (tD_cpt) before the sparse-support exclusion. After it: 0 cells for the market-shape label, 0 for tD_q, 15 for tD_cpt, all in asia and London. So the earlier "35 / 67 / 189 consistent cells" are mostly NOT surviving: the old screen used a placebo that kept serial correlation out of the tail and ignored week clustering.
What survives for tD_cpt (D7 cuts per target for the rest of the session), zw OLDER / RECENT / L6M: asia Bollinger width 1-min last 30 min at 105 min (+4.7 / +5.6 / +6.2) and Keltner width 3-min last 60 min at 90 min (+4.7 / +4.7 / +6.5); asia implied-move ratio to the NDX sigma at 75 min (+3.3 / +3.7 / +4.7); asia mbp-10 spread since start at 105 min (+4.0 / +3.9 / +3.6) and quote changes per minute (+4.4 / +3.6 / +3.3); asia range-forecast c top bucket at 60 min (RECENT +4.0 / L6M +3.2) and rank at 90 min; London Keltner width 15-min at 120 min (+4.9 / +4.3 / +2.7), Bollinger width since start at 105 min (+4.2 / +3.8 / +2.5), profile value-area width / ATR at 90 min (+3.9 / +3.6 / +3.9), forecast range b top bucket at 120 min (+4.3 / +2.2), HMM P(choppy) since start at 120 min (-3.3 / -4.1 / -2.3, i.e. a higher P(choppy state) means FEWER cuts per target: the HMM "choppy" state is the quiet state). All are the same thing: range/volatility already shown (wide bands, high implied ratio, wide spread, many quote changes) predicts more cuts per target; none is a quiet-chop detector. No cut-cluster, gamma, sector, effort, HTF, calendar, ZN, megacap, clock or Cboe input passes; nothing passes for the market-shape label or tD_q.
Calls under the same standard (flag f33, rest-of-session D7 net regressed on the flag, week clusters, nonsense = the same flag series shifted 5-100 sessions): London S_tD_cpt_90 older beta -$1,212 zw -1.98 (nonsense99 2.48), L6M -$2,990 zw -2.19 (2.72), all 2024-07..2026-10 -$1,476 zw -2.65 (2.47, nonsense max 3.24). London K7 call (B_K7_90) older -$606 zw -2.76 (2.85), L6M -$952 zw -2.81 (2.91), all -$683 zw -3.66 (2.83, nonsense max 2.84). So the London calls clear the nonsense bar only on the pooled 2024-07..2026-10 sample (K7 clearly, the stack call narrowly) and are borderline in each window: lead, not a confirmed result. The exact-engine tests in DS3_CHOP_ACTIONS.md are the judge.
### Input table, weekly cluster-robust (A L N P = asia london nyam nypm sessions with at least one passing cell; last column = strongest passing cell, zw OLDER / RECENT / L6M)
| input (family:name) | market label (A L N P) | D7 tD_q | D7 tD_cpt | best passing cell (target, session, input, clock): zw OLDER / RECENT / L6M |
|--|--|--|--|--|
| bars:corr_nq_es | .... | .... | .... |  |
| bars:corr_nq_es_r60 | .... | .... | .... |  |
| bars:corr_nq_es_r90 | .... | .... | .... |  |
| bars:corr_nq_rty | .... | .... | .... |  |
| bars:corr_nq_rty_r60 | .... | .... | .... |  |
| bars:corr_nq_rty_r90 | .... | .... | .... |  |
| bars:cross | .... | .... | .... |  |
| bars:cross_r60 | .... | .... | .... |  |
| bars:cross_r90 | .... | .... | .... |  |
| bars:disp | .... | .... | .... |  |
| bars:er | .... | .... | .... |  |
| bars:er_r60 | .... | .... | .... |  |
| bars:er_r90 | .... | .... | .... |  |
| bars:nr | .... | .... | .... |  |
| bars:nr_r60 | .... | .... | .... |  |
| bars:nr_r90 | .... | .... | .... |  |
| bars:ppc_ratio | .... | .... | .... |  |
| bars:rng_sf_atr | .... | .... | .... |  |
| bars:rsflip | .... | .... | .... |  |
| bars:vol_ratio | .... | .... | .... |  |
| book:aimb5 | .... | .... | .... |  |
| book:churn_tr | .... | .... | .... |  |
| book:churn_tr_r30 | .... | .... | .... |  |
| book:churn_tr_sf | .... | .... | .... |  |
| book:dep10 | .... | .... | .... |  |
| book:dep10_r30 | .... | .... | .... |  |
| book:dep10_sf | .... | .... | .... |  |
| book:imb5 | .... | .... | .... |  |
| book:maxage | .... | .... | .... |  |
| book:maxage_r30 | .... | .... | .... |  |
| book:maxage_sf | .... | .... | .... |  |
| book:nchg | .... | .... | A... | tD_cpt asia mb_nchg_r30 h105: +4.4 / +3.6 / +3.3 |
| book:nchg_r30 | .... | .... | .... |  |
| book:nchg_sf | .... | .... | .... |  |
| book:pull_tr | .... | .... | .... |  |
| book:pull_tr_r30 | .... | .... | .... |  |
| book:pull_tr_sf | .... | .... | .... |  |
| book:spread | .... | .... | A... | tD_cpt asia mb_spread_sf h105: +4.0 / +3.9 / +3.6 |
| calendar:E_earn_prev | .... | .... | .... |  |
| calendar:E_ev_day | .... | .... | .... |  |
| calendar:E_hi_day | .... | .... | .... |  |
| calendar:monthend | .... | .... | .... |  |
| calendar:opexday | .... | .... | .... |  |
| calendar:opexweek | .... | .... | .... |  |
| clock:fripm | .... | .... | .... |  |
| clock:holweek | .... | .... | .... |  |
| clock:rate_dow_tD_cpt | .... | .... | .... |  |
| clock:rate_dow_tD_q | .... | .... | .... |  |
| clock:rate_dow_target | .... | .... | .... |  |
| clock:rate_hol_tD_cpt | .... | .... | .... |  |
| clock:rate_hol_tD_q | .... | .... | .... |  |
| clock:rate_hol_target | .... | .... | .... |  |
| clock:rate_me_tD_cpt | .... | .... | .... |  |
| clock:rate_me_tD_q | .... | .... | .... |  |
| clock:rate_me_target | .... | .... | .... |  |
| cluster:cut | .... | .... | .... |  |
| cluster:cut_A7 | .... | .... | .... |  |
| cluster:cut_H7 | .... | .... | .... |  |
| cluster:cut_K7 | .... | .... | .... |  |
| cluster:cut_M7 | .... | .... | .... |  |
| cluster:cut_P7 | .... | .... | .... |  |
| cluster:cut_U7 | .... | .... | .... |  |
| cluster:cutnt | .... | .... | .... |  |
| cluster:cutnt_A7 | .... | .... | .... |  |
| cluster:cutnt_H7 | .... | .... | .... |  |
| cluster:cutnt_K7 | .... | .... | .... |  |
| cluster:cutnt_M7 | .... | .... | .... |  |
| cluster:cutnt_P7 | .... | .... | .... |  |
| cluster:cutnt_U7 | .... | .... | .... |  |
| cluster:cutratio | .... | .... | .... |  |
| effort:adelta_pp | .... | .... | .... |  |
| effort:dflip_ph | .... | .... | .... |  |
| effort:ext_age | .... | .... | .... |  |
| effort:ext_vol | .... | .... | .... |  |
| effort:vol_pp | .... | .... | .... |  |
| gamma:0dte_share | .... | .... | .... |  |
| gamma:dir_sign | .... | .... | .... |  |
| gamma:flip_dist | .... | .... | .... |  |
| gamma:gk_net | .... | .... | .... |  |
| gamma:sign | .... | .... | .... |  |
| gamma:size_rank | .... | .... | .... |  |
| gamma:zc | .... | .... | .... |  |
| gauge:ac1 | .... | .... | .... |  |
| gauge:bbw | .... | .... | AL.. | tD_cpt asia g1_r30_bbw h105: +4.7 / +5.6 / +6.2 |
| gauge:chi | .... | .... | .... |  |
| gauge:disp | .... | .... | .... |  |
| gauge:dx | .... | .... | .... |  |
| gauge:er | .... | .... | .... |  |
| gauge:hurst | .... | .... | .... |  |
| gauge:kcw | .... | .... | AL.. | tD_cpt asia g3_r60_kcw h90: +4.7 / +4.7 / +6.5 |
| gauge:sqz | .... | .... | .... |  |
| gauge:vr4 | .... | .... | .... |  |
| htf:d_er10 | .... | .... | .... |  |
| htf:days_since_big | .... | .... | .... |  |
| htf:h4_er | .... | .... | .... |  |
| htf:in_va5 | .... | .... | .... |  |
| htf:inside_day | .... | .... | .... |  |
| htf:nr4 | .... | .... | .... |  |
| htf:nr7 | .... | .... | .... |  |
| htf:poc5_dist_atr | .... | .... | .... |  |
| htf:pos10d | .... | .... | .... |  |
| htf:pos3d | .... | .... | .... |  |
| htf:pos5d | .... | .... | .... |  |
| htf:rng10d_atr | .... | .... | .... |  |
| htf:rng3d_atr | .... | .... | .... |  |
| htf:rng5d_atr | .... | .... | .... |  |
| htf:va5_dist_atr | .... | .... | .... |  |
| implied:ndx_ratio | .... | .... | A... | tD_cpt asia imp_ndx_ratio h75: +3.3 / +3.7 / +4.7 |
| implied:vix_ratio | .... | .... | .... |  |
| megacap:breadth | .... | .... | .... |  |
| megacap:corr | .... | .... | .... |  |
| megacap:disp | .... | .... | .... |  |
| megacap:er | .... | .... | .... |  |
| prior:d_poc_atr | .... | .... | .... |  |
| prior:er_prev | .... | .... | .... |  |
| prior:gap_atr | .... | .... | .... |  |
| prior:in_rng | .... | .... | .... |  |
| prior:in_va | .... | .... | .... |  |
| prior:latr | .... | .... | .... |  |
| prior:on6_atr | .... | .... | .... |  |
| prior:prev_big | .... | .... | .... |  |
| prior:prev_chop | .... | .... | .... |  |
| prior:prev_cs | .... | .... | .... |  |
| prior:prev_rng_atr | .... | .... | .... |  |
| profile:in_va | .... | .... | .... |  |
| profile:npeaks | .... | .... | .... |  |
| profile:poc_mig | .... | .... | .... |  |
| profile:poc_mig_abs | .... | .... | .... |  |
| profile:rot | .... | .... | .... |  |
| profile:rot_ph | .... | .... | .... |  |
| profile:va_w_atr | .... | .... | .L.. | tD_cpt london pf_va_w_atr h90: +3.9 / +3.6 / +3.9 |
| profile:va_w_rng | .... | .... | .... |  |
| rangefc:rf_q10 | .... | .... | AL.. | tD_cpt asia rfc_q10 h60: +nan / +4.0 / +3.2 |
| rangefc:rf_q3 | .... | .... | .... |  |
| rangefc:rf_q5 | .... | .... | AL.. | tD_cpt asia rfc_q5 h60: +nan / +3.7 / +2.5 |
| rangefc:rf_rk | .... | .... | AL.. | tD_cpt asia rfc_rk h90: +nan / +3.6 / +3.7 |
| rangefc:rfa | .... | .... | .... |  |
| rangefc:rfb | .... | .... | .... |  |
| rangefc:rfc | .... | .... | .... |  |
| regime:rg2_p | .... | .... | .... |  |
| regime:rg2_p30 | .... | .... | .... |  |
| regime:rg2_psf | .... | .... | .L.. | tD_cpt london rg2_psf h120: -3.3 / -4.1 / -2.3 |
| regime:rg3_p | .... | .... | .... |  |
| regime:rg3_p30 | .... | .... | .... |  |
| regime:rg3_psf | .... | .... | .... |  |
| sector:disp | .... | .... | .... |  |
| sector:iwm_spy_flips | .... | .... | .... |  |
| sector:qqq_spy_flips | .... | .... | .... |  |
| sector:with | .... | .... | .... |  |
| volx:cor1m | .... | .... | .... |  |
| volx:cor1m_chg5 | .... | .... | .... |  |
| volx:cor1m_rank | .... | .... | .... |  |
| volx:cor3m | .... | .... | .... |  |
| volx:cor_term | .... | .... | .... |  |
| volx:vix | .... | .... | .... |  |
| volx:vix9_term | .... | .... | .... |  |
| volx:vix_chg5 | .... | .... | .... |  |
| volx:vix_rank | .... | .... | .... |  |
| volx:vix_term | .... | .... | .... |  |
| volx:vvix | .... | .... | .... |  |
| volx:vvix_chg5 | .... | .... | .... |  |
| volx:vvix_rank | .... | .... | .... |  |
| volx:vvix_vix | .... | .... | .... |  |
| zn:er | .... | .... | .... |  |
| zn:rng | .... | .... | .... |  |
| zn:rng_sf | .... | .... | .... |  |
| zn:vol | .... | .... | .... |  |
| zn:vol_sf | .... | .... | .... |  |

### 10.1 Bucket for BASIC_TESTS Part 1b ("chop call vs trend call")
File /mnt/l2/l2vast/_chop/f1/chop_bucket_calls.parquet: one row per (day, sess, version): call_epoch, chop_flag (1 = chop call, 0 = trend call; trend_call = 1 - chop_flag), score, off_epoch (flip-back epoch where defined, NaN otherwise), validated (1 = the version/session pair is one of the leads above, 0 = not validated, use only as a labelled bucket). Versions: S_tD_cpt_90_f33 (call at session start + 90 min, flag from calls3_S_tD_cpt_90, off_epoch from the flip rule; validated for London), K7_90_f33 (K7's own rest-of-session book, London), HGB_OWN_tD_cpt_pre (pre-session call, call_epoch = session start, London), LRs_ALL_tD_cpt_90. Use S_tD_cpt_90_f33 as THE chop-vs-trend bucket for London and the pre-session version when the grid needs a call known at the session start. Asia/nyam/nypm rows exist for completeness but no call is validated there (flag rates 22-69% with no stable lead). Flags are NaN before 2024-07-01 (walk-forward start); rows currently end 2026-10-16 (see 10.3).
### 10.2 Per-minute entry point for the minute-grid forecast
code/th_chop1/ch_api.py: `cf = ChopFeatures(); x = cf.at(day, sess, T)` returns every causal feature at epoch T (bars with ts+60 <= T; session sess in asia/london/nyam/nypm of Globex day `day`); `cf.grid(day, sess, step=60, first=900)` returns one row per minute. Families: gauges g{1,3,5,15}_{sf,r30,r60,r120}_*, ctx_* (HTF), pf_* (profile), ef_* (effort vs result), sec_* (ETF), clk_*, gm_* (gamma), rg2_*/rg3_* (HMM), mb_* (mbp-10 minute book), cut_*/cutnt_*/cutratio_*, imp_*. ch_api_test.py compares 2,804 values at random rows to features6.parquet: 0 mismatches. Builders behind it: ch_feat.py (bars/prior), ch_feat2.py (cluster, mbp, implied, megacap), ch_feat4/5.py (gauges, HTF, profile, effort, clock, gamma, ETF), ch_regime.py (HMM fit and forward filter), ch_feat6.py (regime join, ZN, clock rates).

### 10.3 Extension of the calls past 2026-10-16 (done 2026-11-15)
The 1m NQ store ended 2026-10-16; I rebuilt NQ 1m bars for 2026-10-18..2026-11-11 from the mbp-10 replica prints (_hist_replica/days; additive offset 3,732.25 fixed on the 1,380 overlapping minutes of 2026-10-16, volume ratio 1.000, open/high/low max difference 0.5 / 0.0 points) into /mnt/l2/l2vast/_chop/f1ext/bars1m_NQ.npz and ran the whole feature chain on it (CHOP_EXT=1: ch_ext_bars.py, ch_label_ext.py, ch_regime.py, ch_feat/2/5/6). The label is NOT changed: old sessions keep their label; new sessions are ranked against the frozen sample and the frozen 2/3 threshold (ch_label_ext.py, 90 new sessions, 28.9% chop). Old rows reproduce the original features exactly (max difference 0.0). New-day calls come from FIXED models trained on days <= 2026-10-16 (not refitted), file /mnt/l2/l2vast/_chop/f1/chop_bucket_calls_through_20261111.parquet (same schema as chop_bucket_calls.parquet plus `source`).
Coverage and limits: calls now run to 2026-11-11 (last complete replica day). 2026-11-12..11-14 need tape (the replica has 1 hour of 11-12; ohlcv tail pulls have no full sessions); extend when the tape/universe is extended (rerun run_ext.sh and ch_extcalls.py). Cluster-based versions (S_tD_cpt_90_f33, K7_90_f33) are NaN after 2026-10-31 because the exact D7 trade log ends there; the pre-session version HGB_OWN_tD_cpt_pre has no cluster inputs and is complete to 11-11. LRs_ALL_tD_cpt_90 is not extended (ES/RTY bars end 10-16). The flip-back off_epoch is filled for the stack call. WARNING: Oct-Nov 2026 vol-so-far is far above the training mean (London range so far / ATR 0.69 vs 0.52, overnight range / ATR 1.34 vs 0.78, range / VIX-implied 1.79 vs 1.20), so the fixed-threshold stack call flags 90% of London sessions from 2026-10-19 to 2026-10-30 (training flag rate 44%): the thresholds need a rolling re-fit before the extended flags are used for anything but a bucket label.

## 11. FOLLOW-UP 2026-11-15 (lead items): rank-based London call, vol-regime split, planted-edge check, 11-12..11-14
Code: code/th_chop1/ch_rank.py (chop_rank_calls.parquet, chop_rank_scores.csv), the regime-split block in section 11 (chop_regime_split_f33.csv), ch_plant.py (plant_check.csv). Dollar columns JN05W2 BASE lots (live x1.75), fee $4.84; zw = ISO-week cluster-robust z, nonsense bar = 99th percentile of |zw| of the same flag series shifted 5-100 sessions (96 shifts).
(1) Rank-based version (score ranked against the 60 previous same-session scores, flag if rank >= 2/3; r40 and r20 also saved): London K7 older (flagged +$33 vs unflagged +$195, zw -0.79, bar 2.53), L6M -$410 vs +$335 (zw -1.95, bar 2.27), L3M -$633 vs +$579 (zw -1.98, bar 2.55), all 2024-10..2026-10 -$52 vs +$232 (zw -1.56, bar 2.88). London stack: older -$430 vs +$573 (zw -1.61, bar 2.15), L6M -$1,630 vs +$1,152 (zw -2.13, 2.19), L3M -$531 vs +$1,321 (zw -0.86, 3.51), all -$680 vs +$709 (zw -2.43, 2.59). Neither rank version clears the nonsense bar in any window or pooled; the fixed-threshold f33 K7 call (below) is stronger than its rank version. Flag rate of the rank version on 2026-10-19..10-30 (fixed ext model): K7 44%, stack 78% (the join between the walk-forward scores and the fixed-model scores is a scale step; the rank version recovers only part of it). The file /mnt/l2/l2vast/_chop/f1/chop_rank_calls.parquet (all sessions, versions S_tD_cpt_90_f33 and K7_90_f33; columns day, sess, call_epoch, score, rank, r33, r40, r20, rest_net, n_rest, highvol) goes to W-CH2 as a cell candidate; K7 London f33 (threshold, walk-forward) stays the closest to live.
(2) Vol-regime split (high-vol months = top third of months by mean session range: all of 2026-04..2026-11 and 2024-late are high; normal-vol months exist only in the 'older' window). Threshold f33 calls, London, mean rest net flagged vs unflagged, zw vs nonsense99:
- K7_90 high vol: older -$367 vs +$410 (zw -2.66, 2.67), L6M -$580 vs +$372 (-2.81, 2.86), L3M -$633 vs +$579 (-1.98, 2.94), pooled -$452 vs +$394 (-3.84, 2.47). Normal vol (older only): -$377 vs +$134 (-1.57, 2.42). All months pooled -$420 vs +$262 (-3.66, 2.29). Same sign in every regime and window; clears the bar pooled and in high-vol months pooled, borderline per window, fails in normal-vol months alone (n 223, z -1.57).
- Stack S_tD_cpt_90 high vol: older -$42 vs +$1,924 (-1.64, 2.20), L6M -$641 vs +$2,349 (-2.19, 2.82), L3M -$21 vs +$2,623 (-1.42, 4.09), pooled -$296 vs +$2,087 (-2.61, 2.32). Normal vol: -$857 vs +$303 (-1.57, 3.00). All months -$525 vs +$951 (-2.65, 2.17). Same sign everywhere, clears the bar pooled only.
Reading: the K7 London call survives the vol-regime split in direction and, pooled, in significance; neither call is significant inside a single 3-6 month window, which the planted-edge check below says is expected.
(3) Extension 11-12..11-14: asked W-EV where the extended NQ store lands; not on the box yet (replica ends 11-11, one hour of 11-12). Rerun run_ext.sh and ch_extcalls.py when it exists.
(4) Planted-edge check of the zw table (ch_plant.py): in all 108 session x clock x target cells a synthetic input with a known AUC edge (AR(1) noise rho 0.7, 4 reps per level) was pushed through the identical zw pipeline and pass rule. Share of cells where it is recovered, by planted AUC: 0.53 -> 0%; 0.56 -> 0-2%; 0.60 -> 11% (tD_q), 12% (tD_cpt), 19% (market label); 0.65 -> 39% / 56% / 71%; 0.70 -> 74% / 79% / 96%. By session at AUC 0.65: asia 77%, london 64%, nyam 50%, nypm 31%. Median |zw| at AUC 0.60: OLDER 3.8, RECENT 2.9, L6M 1.9. So "nothing passes" means: no single input has a per-cell AUC edge of about 0.62-0.65 or more; edges of 0.55-0.58 (all the combinations and calls here) are below what this pipeline can confirm in one cell. Every table in sections 9-10 that says 'nothing passes' carries this power statement: a call or input with a true edge of 0.56 would be reported as 'not confirmed' 98% of the time.

### 11.1 Extension to 2026-11-13 (W-EV store, done)
W-EV's extended store (days 20261112 and 20261113 under _engvslive/store_1113/days_root) was added: NQ 1m bars rebuilt to 2026-11-13 21:59Z (offset 3,732.25, volume ratio 1.000), label extended with the frozen rule (100 new sessions, 29.0% chop), features, regime, mbp minute table and fixed-model calls rerun. File /mnt/l2/l2vast/_chop/f1/chop_bucket_calls_through_20261113.parquet (same schema). 2026-11-14 is a Saturday (no NQ session). Cluster-based versions stay NaN after 2026-10-31 (exact D7 trade log ends 10-30/31); the pre-session HGB_OWN version is complete to 2026-11-13. Market data end 2026-11-13; exact-engine dollar columns end 2026-10-30.

Note 2026-11-15: W-EV rebuilt NQ_20261112.npz (the first file was out of order); bars, label, mbp minute table, features and calls for 11-12 were regenerated from the corrected file and chop_bucket_calls_through_20261113.parquet rewritten.
