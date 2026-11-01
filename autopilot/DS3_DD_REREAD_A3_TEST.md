# DS3_DD_REREAD_A3 - DEAD-REREAD under DRAWDOWN FIRST, part 3 of 4: ALL SIZING FAMILIES (vol-scaled lots, ER sizers, EQR / lots_factor, TG-1 chop-day and day-type sizers, META sizers) on the one-convention engine. POST-HOC re-scoring, nothing here is a PASS, nothing promoted (Shadow only)

Capped 20260206, no post-cap file opened. Engine DS3_ONE_CONVENTION (oc_lib.py unchanged; dd_lib wrappers; ties to DD-1 exact, max daily diff 0.0 on COMP, ASIS, COMPnf and the 12R/20R/30R locks), live lots, slip +0.25, parity stop, K6 70/30, running max over taken signals, lock OFF headline. Size rules enter ONLY through the engine multiplier route (scenario mer_fn -> m0, integer half-up min-1 lots) and the skip route for META zeros; never pts scaling. Prereg `l2vast/ds3/prereg/DDRR_A3_prereg.md` sha256 89087202a798b6efd8009efc93f38c48e2b35a92a86e4987ecae7b64b0d16763 (in DECISIONS.md before scoring). Code `l2vast/ds3/code/dd_a3/`, outputs `l2vast/ds3/out/dd_reread/a3/` (cells_all.csv = every cell, recent columns POST-HOC for non-selected cells), rows `l2vast/ds3/out/recent_wins/dd_reread_a3.csv`. Windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149 weeks. Units $k.

## Page 1 - coverage, verdict, RISK-KEEP table (top 30, recent-first)

**Coverage.** DEAD_CELLS holds ~1.39M cell rows; ~3,200 are sizing families (EQR 172, RE5_EQRlotsfactor 50, SZR 14, META 2,660, RE5_META 102, SPLIT2 206). Ledger sizing rows are per-trade or old-frame summaries, so a sizer can be scored on drawdown only by RE-RUNNING it. Re-run here on the live-lot composite: **52 vol-scaled-lot cells, 144 ER-sizer cells, 42 day-type/calendar cells, 4876 of 4,876 TG-1 measure-sizer cells (1219 measure columns x 4 shapes; the chop-day sizers are the Chop14 / ER20 / ADX14 columns inside it), 28 META-label sizer cells (the 14 FS1 + 14 FS2 PRE-selected configs), plus 600 fake-measure null cells**; the **156 stored EQR / lots_factor series are re-read from their stored window stats on the OLD frame (Section 7, not the one-convention engine)**. NOT re-scored: SZR Kelly/Sharpe sizers (14 summary rows, no weekly series), the other ~2,630 META configs (only the PRE-selected ones have a defensible selection), RE5_EQR (50 rows, same old frame as Section 7). TG-1 measures cover 94.3% of the composite's TAKEN rows; the A6/PB book (598 taken rows) has no stored measure and keeps multiplier 1.0, as do rows without a stored value. META scores begin in 2024, so X' is untouched by every META cell by construction; the composite's X' maxDD (121k) is weeks 1-7 of the data, i.e. inside the warm-up of every trailing-history rule (vol-scaled lots need L+8 weeks of history), so **the X' half of the PRE/X' agree test cannot be passed by a V or M cell; it is reported, not waived.**

**Verdict (nothing here is a PASS; all post-hoc).**
1. **The vol-scaled rule the user remembers is DS3_SIZING_REGIME B2 (8-week trailing SD per book, clip 0.5-2.0) on the old D3SL stack. The remembered numbers have the SIGNS FLIPPED:** lot-matched in HOLD it made maxDD **+67,935 (deeper)** and SD **+8,899 (higher)** with mean +5,992; in PRE it was maxDD -54,753 and SD -2,122. It was shelved on the risk gate G3 (maxDD / worst week got worse), not only on the mean. Unmatched (average lots x0.88) it cut SD (-5.6k HOLD, -10.4k PRE) with maxDD +36k / -8k.
2. **Rebuilt on the one-convention engine (multiplier route, live lots, 52 cells + 200-draw random-multiplier placebo), the named rule (L8, 0.5-2.0, per book, multiplier feeding the locks) does not lower the Sunday composite's drawdown where it matters:** L6M maxDD 23->24 (+5%), HOLD 97->81 (-17%), PRE 241->162 (-33%), X' 121->121 (+0%); L6M mean -7.3 (MDE 6.4)*; L6M placebo rank 36% (not better than random multipliers of the same mean and dispersion), PRE placebo rank 0.5% (it DOES beat the placebo in PRE). Label: no. On the as-is stack it is a different animal: L6M maxDD 88->56 (-37%) at mean +1.8 (MDE 10.1), placebo rank 0%, but PRE -11% and X' +1% and its absolute L6M maxDD (56k) is still 2.4x the composite's (23k): **RISK-KEEP (L6M only)** on the as-is frame, and no help to the composite.
2b. **The one vol-scaled variant worth a Shadow slot is the STACK-level one (one multiplier for all books from the total daily P&L SD, L8, 0.5-2.0, feeding the locks):** ALL-period maxDD 241->134 (-45%), PRE 241->134 (-45%) with PRE worst-20 -875->-638 and a PRE placebo rank of 0.0%, ALL mean -2.6k/wk (19.7 vs 22.3), Calmar 0.09->0.15, equal-risk L6M/PRE mean +1.7/+0.6 (c=1.19); but L6M maxDD 23->25 (+8%) with mean -3.9 (MDE 6.3), X' unchanged (warm-up), and the family-wise adjusted PRE p is 0.26 over 52 cells. It addresses the composite's 2024-25 weakness (part B), not the recent windows.
3. **ER sizers: 0 of 144 variants cut maxDD >= 20% in both PRE and X'.** The live piece (thr 0.30, 1.5/0.5, all six books) cuts L6M maxDD 43->23 (-47%) (RISK-KEEP on the L6M definition, placebo rank 1%) but DEEPENS PRE +72% (placebo rank 94%) : **(L6M only)**. KB ER>=0.20 (K6 only) is inside noise everywhere. The lock feed carries the gain: over 72 feed ON/OFF pairs the L6M mean gain is +5.6k with the multiplier feeding the locks vs +1.6k without (60 of 72 pairs larger with the feed; median share of the gain due to the feed 66% where the gain is positive).
4. **Day-type / calendar sizers: 2 of 42 cells eligible on PRE+X'.** TG-1 measure sizers: 458 of 4876 eligible (9.4%), against 9.3% of 600 FAKE measures (the same columns row-shuffled within book): **real measures are not distinguishable from noise** (both-window cut >= 20%: 10.6% real vs 11.8% fake; best PRE+X' score real 0.54 vs fake 0.54). Of the 0 PRE+X'-selected T cells that got the one recent look, 0 carry a RISK-KEEP label, and the bottom-tercile-halving shapes that dominate the eligible set are volume cuts (about one third of rows at x0.5).
5. **META-label sizers: 0 of 28 eligible** (X' is untouched by construction); the PRE cuts that exist (4 cells >= 20%) reverse in L6M (median L6M maxDD change +20%), matching DS3_METALABEL (the learned ranking turned against the signals after mid-2025).
6. **EQR / lots_factor (156 old-frame series, own lots, stored stats): 18 cut L6M maxDD >= 20% with the mean inside its MDE, 7 of those also cut PRE and X' >= 20%** (6 on the optimistic M basis, 1 on the N basis; 3 are L6M-ranked "looked" picks; ids: A|H|P|M, A|H|EP|M, A|B|P|M, A|B|EP|M, A|B|EP|N, C|F|A06+HM5R+B02, C|F|A06+B02). They are exit/entry/profit-take RULES carried as equal-risk lot factors, not sizers (parts A1/A2 own them); the M-basis rows owe part of their cut to the target-fill correction (DS3_EQUAL_RISK). Listed for completeness only.
7. **Net for the user's measure: no sizing family produces a RISK-KEEP that holds in L6M, PRE and X' together and beats the same-volume placebo.** The one sizer that is part of the composite (ER) buys its L6M drawdown cut with a deeper PRE drawdown and about 70% of its mean gain comes from the lock feed; the remembered vol-scaler lowers PRE drawdown on the composite but costs L6M mean beyond MDE and does nothing in L6M. Nothing goes live; Shadow list below.

### Table P1 - RISK-KEEP table (rules that cut L6M maxDD >= 20% with the L6M mean not below -MDE, placebo-checked), top 30, recent-first, one-convention engine, lock OFF

Rows = stage-2 cells (pre-specified + PRE+X'-selected + 10 post-hoc L6M-candidates per wave, all with 200-draw placebo). 16 rows carry a RISK-KEEP label: 0 full RISK-KEEP, 3 (L6M only), 13 (volume effect). F (cells swept) per group: V 52, E 144, D 42, T 4,876, M 28; adj p = min(1, F x placebo rank). "equal-risk" = lots x c via the engine lot table, ALL worst-20 matched to the before-stack, mean change.

| rule | maxDD $k before→after (same lots) | worst-20 $k (tail windows) | mean Δ $k/wk (MDE) | EQUAL-RISK mean Δ $k/wk | placebo (L6M cut; 200 draws; adj p over F cells) | PRE/X' agree | STRICT / TOLERANT / NOW-ONLY | label | session | D6/D7 mapping |
|---|---|---|---|---|---|---|---|---|---|---|
| E thr0.30 1.5/0.5 all feed1 [before=COMPnoER] | L3M 43→21 · L6M 43→23 · HOLD 74→97 · PRE 140→241 · X' 163→121 | PRE -684→-875 · X' -373→-420 · ALL -896→-1098 | L3M +13.4 (24.3) · L6M +13.1 (15.0) · HOLD +12.1 (14.9) · PRE +3.5 (8.7) · X' +2.3 (9.1) | c=0.84 · L3M +7.2 · L6M +6.0 · HOLD +5.6 · PRE +0.2 · X' +1.3 | L6M rank 1% (p5 -17%, med +45%; adj p 1.00) · PRE rank 94.0% (p5 -11%) | DISAGREE (PRE +72%, X' -26%) | STRICT Y / TOL n / NOW Y (TOL-B n, TOL-nc Y) | RISK-KEEP (L6M only) | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| D vix_terc_exp=VIX_high x0.5 [before=COMP] | L3M 21→15 · L6M 23→14 · HOLD 97→97 · PRE 241→156 · X' 121→121 | PRE -875→-720 · X' -420→-404 · ALL -1098→-944 | L3M -3.3 (12.4) · L6M -4.2 (7.8) · HOLD -3.7 (6.9) · PRE -5.6 (7.6) · X' +0.2 (1.5) | c=1.17 · L3M +1.0 · L6M -0.3 · HOLD +0.7 · PRE -2.4 · X' +1.4 | L6M rank 1% (p5 -21%, med +62%; adj p 0.42) · PRE rank 46.5% (p5 -50%) | DISAGREE (PRE -35%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (L6M only) | all sessions | D6 calendar/day-type lot line (needs a day-state table in the D6 log writer); Shadow only |
| V ASIS L8 c0.5-2.0 book feed1 [before=ASIS] | L3M 88→56 · L6M 88→56 · HOLD 144→153 · PRE 162→145 · X' 317→320 | PRE -811→-791 · X' -572→-537 · ALL -1161→-1060 | L3M +1.3 (15.8) · L6M +1.8 (10.1) · HOLD +0.6 (9.0) · PRE -3.5 (7.1) · X' +1.8 (3.9) | c=1.09 · L3M +2.6 · L6M +4.0 · HOLD +2.7 · PRE -2.1 · X' +1.7 | L6M rank 0% (p5 -33%, med -21%; adj p 0.26) · PRE rank 36.5% (p5 -35%) | DISAGREE (PRE -11%, X' +1%) | STRICT n / TOL n / NOW Y (TOL-B Y, TOL-nc n) | RISK-KEEP (L6M only) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-1.0 stack feed0 [before=COMPnf] | L3M 36→30 · L6M 39→20 · HOLD 80→78 · PRE 225→198 · X' 89→89 | PRE -801→-711 · X' -350→-348 · ALL -985→-895 | L3M -0.5 (16.1) · L6M -1.7 (9.2) · HOLD -2.4 (8.2) · PRE -1.0 (6.1) · X' -0.7 (1.7) | c=1.13 · L3M +10.0 · L6M +7.6 · HOLD +6.1 · PRE +0.8 · X' +0.9 | L6M rank 42% (p5 -66%, med -40%; adj p 1.00) · PRE rank 42.5% (p5 -36%) | DISAGREE (PRE -12%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.75-1.33 stack feed0 [before=COMPnf] | L3M 36→30 · L6M 39→20 · HOLD 80→79 · PRE 225→197 · X' 89→89 | PRE -801→-733 · X' -350→-338 · ALL -985→-898 | L3M +2.9 (11.3) · L6M -0.2 (7.3) · HOLD -1.0 (6.7) · PRE +0.7 (6.2) · X' +2.9 (4.6) | c=1.08 · L3M +7.9 · L6M +4.9 · HOLD +3.2 · PRE +1.2 · X' +3.3 | L6M rank 34% (p5 -55%, med -37%; adj p 1.00) · PRE rank 42.5% (p5 -39%) | DISAGREE (PRE -13%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-2.0 stack feed0 [before=COMPnf] | L3M 36→30 · L6M 39→20 · HOLD 80→79 · PRE 225→198 · X' 89→89 | PRE -801→-719 · X' -350→-355 · ALL -985→-903 | L3M -0.5 (16.1) · L6M -1.7 (9.2) · HOLD -2.4 (8.2) · PRE -1.2 (6.6) · X' +3.4 (6.2) | c=1.09 · L3M +8.0 · L6M +5.9 · HOLD +4.4 · PRE +0.2 · X' +2.8 | L6M rank 28% (p5 -61%, med -29%; adj p 1.00) · PRE rank 52.5% (p5 -46%) | DISAGREE (PRE -12%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 session feed0 [before=COMPnf] | L3M 36→7 · L6M 39→20 · HOLD 80→79 · PRE 225→225 · X' 89→89 | PRE -801→-773 · X' -350→-355 · ALL -985→-972 | L3M -0.6 (20.4) · L6M -1.8 (10.4) · HOLD -2.0 (9.1) · PRE +1.8 (6.6) · X' +0.9 (2.1) | c=1.01 · L3M -1.3 · L6M -1.9 · HOLD -2.1 · PRE +2.0 · X' +1.0 | L6M rank 28% (p5 -61%, med -32%; adj p 1.00) · PRE rank 56.5% (p5 -22%) | DISAGREE (PRE -0%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | per book x session | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→37 · L6M 39→24 · HOLD 80→80 · PRE 225→224 · X' 89→89 | PRE -801→-741 · X' -350→-346 · ALL -985→-922 | L3M -0.9 (9.1) · L6M -2.1 (6.6) · HOLD -2.5 (5.9) · PRE +0.6 (6.4) · X' +1.6 (4.3) | c=1.06 · L3M +0.5 · L6M -0.5 · HOLD -1.4 · PRE +1.6 · X' +2.6 | L6M rank 31% (p5 -52%, med -18%; adj p 1.00) · PRE rank 67.5% (p5 -39%) | DISAGREE (PRE -1%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→51 · L6M 39→24 · HOLD 80→75 · PRE 225→222 · X' 89→89 | PRE -801→-782 · X' -350→-373 · ALL -985→-961 | L3M -2.9 (9.0) · L6M -4.2 (6.9) · HOLD -4.6 (6.6) · PRE +0.7 (5.7) · X' -0.5 (1.7) | c=1.03 · L3M -3.9 · L6M -3.1 · HOLD -3.2 · PRE +2.4 · X' -0.2 | L6M rank 53% (p5 -51%, med -37%; adj p 1.00) · PRE rank 55.5% (p5 -20%) | DISAGREE (PRE -2%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-1.0 book feed0 [before=COMPnf] | L3M 36→51 · L6M 39→24 · HOLD 80→75 · PRE 225→222 · X' 89→89 | PRE -801→-783 · X' -350→-366 · ALL -985→-956 | L3M -2.9 (9.0) · L6M -4.1 (7.0) · HOLD -4.5 (6.6) · PRE +0.7 (5.7) · X' -0.3 (1.4) | c=1.04 · L3M -4.3 · L6M -3.4 · HOLD -3.4 · PRE +1.9 · X' +0.1 | L6M rank 60% (p5 -51%, med -40%; adj p 1.00) · PRE rank 52.5% (p5 -19%) | DISAGREE (PRE -2%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.75-1.33 book feed0 [before=COMPnf] | L3M 36→51 · L6M 39→24 · HOLD 80→75 · PRE 225→224 · X' 89→89 | PRE -801→-766 · X' -350→-373 · ALL -985→-947 | L3M -0.2 (8.2) · L6M -2.9 (6.8) · HOLD -3.4 (6.4) · PRE +1.6 (5.7) · X' -0.5 (1.7) | c=1.04 · L3M -1.2 · L6M -1.8 · HOLD -2.2 · PRE +2.6 · X' +0.8 | L6M rank 57% (p5 -51%, med -39%; adj p 1.00) · PRE rank 59.0% (p5 -15%) | DISAGREE (PRE -1%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-1.0 book feed0 [before=COMPnf] | L3M 36→37 · L6M 39→24 · HOLD 80→78 · PRE 225→220 · X' 89→89 | PRE -801→-734 · X' -350→-359 · ALL -985→-931 | L3M -1.3 (9.2) · L6M -2.6 (6.6) · HOLD -2.9 (5.9) · PRE +0.1 (6.3) · X' -0.9 (2.2) | c=1.06 · L3M +0.4 · L6M -1.0 · HOLD -1.4 · PRE +1.5 · X' +0.2 | L6M rank 53% (p5 -54%, med -38%; adj p 1.00) · PRE rank 64.0% (p5 -24%) | DISAGREE (PRE -2%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-2.0 book feed1 [before=COMP] | L3M 21→17 · L6M 23→17 · HOLD 97→75 · PRE 241→186 · X' 121→121 | PRE -875→-777 · X' -420→-420 · ALL -1098→-978 | L3M -5.0 (7.3) · L6M -4.3 (5.2) · HOLD -4.0 (5.6) · PRE -4.2 (4.9) · X' -0.3 (1.3) | c=1.14 · L3M -8.9 · L6M -2.3 · HOLD -1.9 · PRE -0.6 · X' +0.4 | L6M rank 10% (p5 -34%, med +6%; adj p 1.00) · PRE rank 8.5% (p5 -24%) | DISAGREE (PRE -23%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-1.0 book feed1 [before=COMP] | L3M 21→17 · L6M 23→17 · HOLD 97→75 · PRE 241→186 · X' 121→121 | PRE -875→-776 · X' -420→-415 · ALL -1098→-974 | L3M -4.5 (7.5) · L6M -3.9 (5.2) · HOLD -3.7 (5.5) · PRE -4.2 (4.9) · X' -0.5 (1.0) | c=1.15 · L3M -8.8 · L6M -3.3 · HOLD -2.6 · PRE -0.3 · X' +0.0 | L6M rank 8% (p5 -31%, med +3%; adj p 1.00) · PRE rank 7.0% (p5 -23%) | DISAGREE (PRE -23%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| E thr0.30 1.0/0.5 all feed0 [before=COMPnoER] | L3M 43→33 · L6M 43→33 · HOLD 74→74 · PRE 140→140 · X' 163→106 | PRE -684→-588 · X' -373→-276 · ALL -896→-769 | L3M +2.0 (16.8) · L6M -0.9 (10.5) · HOLD -1.3 (9.4) · PRE -3.0 (6.2) · X' -0.2 (5.2) | c=1.16 · L3M +5.4 · L6M +2.7 · HOLD +2.7 · PRE -2.6 · X' +0.1 | L6M rank 18% (p5 -43%, med +6%; adj p 1.00) · PRE rank 77.0% (p5 -28%) | DISAGREE (PRE -0%, X' -35%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.30 1.0/0.5 all feed1 [before=COMPnoER] | L3M 43→33 · L6M 43→33 · HOLD 74→69 · PRE 140→141 · X' 163→106 | PRE -684→-573 · X' -373→-278 · ALL -896→-749 | L3M +0.4 (15.6) · L6M -2.3 (10.1) · HOLD -2.3 (9.1) · PRE -2.4 (5.4) · X' -0.5 (5.3) | c=1.19 · L3M +4.5 · L6M +1.9 · HOLD +2.2 · PRE -3.0 · X' +0.1 | L6M rank 18% (p5 -43%, med +2%; adj p 1.00) · PRE rank 79.5% (p5 -33%) | DISAGREE (PRE +0%, X' -35%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |

### Table P1b - pre-specified / named rules and every other stage-2 cell that is NOT a RISK-KEEP (full lines, one row each)

| rule | maxDD $k before→after (same lots) | worst-20 $k (tail windows) | mean Δ $k/wk (MDE) | EQUAL-RISK mean Δ $k/wk | placebo (L6M cut; 200 draws; adj p over F cells) | PRE/X' agree | STRICT / TOLERANT / NOW-ONLY | label | session | D6/D7 mapping |
|---|---|---|---|---|---|---|---|---|---|---|
| V L8 c0.5-2.0 book feed1 [before=COMP] | L3M 21→23 · L6M 23→24 · HOLD 97→81 · PRE 241→162 · X' 121→121 | PRE -875→-724 · X' -420→-425 · ALL -1098→-946 | L3M -12.4 (11.2)* · L6M -7.3 (6.4)* · HOLD -6.4 (6.2)* · PRE -3.2 (5.1) · X' -1.2 (2.3) | c=1.15 · L3M -5.3 · L6M -0.9 · HOLD -0.6 · PRE -2.5 · X' +0.6 | L6M rank 36% (p5 -28%, med +10%; adj p 1.00) · PRE rank 0.5% (p5 -28%) | DISAGREE (PRE -33%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→53 · L6M 39→37 · HOLD 80→78 · PRE 225→190 · X' 89→89 | PRE -801→-744 · X' -350→-378 · ALL -985→-955 | L3M -4.4 (9.2) · L6M -3.2 (6.6) · HOLD -3.4 (6.0) · PRE +1.0 (5.8) · X' +0.2 (2.2) | c=1.04 · L3M -2.3 · L6M -2.2 · HOLD -2.5 · PRE +2.2 · X' +0.6 | L6M rank 80% (p5 -51%, med -36%; adj p 1.00) · PRE rank 22.5% (p5 -30%) | DISAGREE (PRE -16%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-2.0 book feed1 [before=COMP] | L3M 21→23 · L6M 23→23 · HOLD 97→95 · PRE 241→176 · X' 121→121 | PRE -875→-725 · X' -420→-460 · ALL -1098→-966 | L3M -7.5 (11.3) · L6M -5.9 (6.7) · HOLD -5.5 (6.0) · PRE -2.1 (5.7) · X' -1.4 (2.7) | c=1.11 · L3M -3.9 · L6M -2.6 · HOLD -2.8 · PRE -0.7 · X' -0.8 | L6M rank 38% (p5 -43%, med +10%; adj p 1.00) · PRE rank 8.5% (p5 -30%) | DISAGREE (PRE -27%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 stack feed1 [before=COMP] | L3M 21→23 · L6M 23→25 · HOLD 97→73 · PRE 241→134 · X' 121→121 | PRE -875→-638 · X' -420→-437 · ALL -1098→-889 | L3M -7.0 (11.5) · L6M -3.9 (6.3) · HOLD -3.4 (6.3) · PRE -3.7 (5.7) · X' +0.1 (2.7) | c=1.19 · L3M -4.4 · L6M +1.7 · HOLD +2.2 · PRE +0.6 · X' +0.7 | L6M rank 55% (p5 -45%, med +6%; adj p 1.00) · PRE rank 0.0% (p5 -32%) | DISAGREE (PRE -45%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 stack feed0 [before=COMPnf] | L3M 36→50 · L6M 39→39 · HOLD 80→76 · PRE 225→140 · X' 89→89 | PRE -801→-674 · X' -350→-349 · ALL -985→-870 | L3M -0.2 (7.6) · L6M -1.5 (6.7) · HOLD -2.1 (6.2) · PRE +0.9 (6.6) · X' +1.1 (2.8) | c=1.10 · L3M +3.6 · L6M +5.2 · HOLD +4.1 · PRE +1.7 · X' +1.6 | L6M rank 86% (p5 -55%, med -37%; adj p 1.00) · PRE rank 2.5% (p5 -29%) | DISAGREE (PRE -38%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 session feed1 [before=COMP] | L3M 21→43 · L6M 23→43 · HOLD 97→69 · PRE 241→150 · X' 121→121 | PRE -875→-787 · X' -420→-447 · ALL -1098→-993 | L3M -11.6 (11.7) · L6M -8.1 (7.7)* · HOLD -6.8 (7.3) · PRE -3.1 (6.1) · X' -1.0 (2.4) | c=1.10 · L3M -14.9 · L6M -7.9 · HOLD -6.7 · PRE -1.8 · X' -0.0 | L6M rank 60% (p5 -7%, med +76%; adj p 1.00) · PRE rank 2.5% (p5 -34%) | DISAGREE (PRE -38%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | per book x session | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| E thr0.30 1.5/0.5 all feed0 [before=COMPnoER] | L3M 43→36 · L6M 43→39 · HOLD 74→80 · PRE 140→225 · X' 163→89 | PRE -684→-801 · X' -373→-350 · ALL -896→-985 | L3M +0.4 (20.0) · L6M +4.8 (12.3) · HOLD +5.3 (11.5) · PRE -3.1 (8.7) · X' +2.7 (8.9) | c=0.91 · L3M -6.8 · L6M -2.7 · HOLD -1.8 · PRE -5.1 · X' +1.9 | L6M rank 7% (p5 -16%, med +49%; adj p 1.00) · PRE rank 91.0% (p5 -16%) | DISAGREE (PRE +61%, X' -45%) | STRICT n / TOL n / NOW Y (TOL-B n, TOL-nc n) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.20 1.5/0.5 K feed1 [before=COMPnoER] | L3M 43→45 · L6M 43→45 · HOLD 74→91 · PRE 140→155 · X' 163→172 | PRE -684→-708 · X' -373→-373 · ALL -896→-926 | L3M +1.7 (5.1) · L6M +1.5 (3.7) · HOLD +1.0 (3.3) · PRE +1.0 (2.4) · X' +1.0 (1.8) | c=0.91 · L3M +1.8 · L6M +2.2 · HOLD +1.6 · PRE -1.3 · X' +0.9 | L6M rank 37% (p5 -15%, med +8%; adj p 1.00) · PRE rank 49.0% (p5 +1%) | DISAGREE (PRE +11%, X' +6%) | STRICT Y / TOL n / NOW Y (TOL-B n, TOL-nc Y) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.20 1.5/0.5 K feed0 [before=COMPnoER] | L3M 43→43 · L6M 43→43 · HOLD 74→91 · PRE 140→140 · X' 163→163 | PRE -684→-678 · X' -373→-362 · ALL -896→-903 | L3M +0.7 (4.8) · L6M -0.7 (3.2) · HOLD -1.1 (2.9) · PRE +0.0 (2.4) · X' +1.0 (2.3) | c=0.98 · L3M +3.3 · L6M +0.5 · HOLD -0.0 · PRE -0.8 · X' +0.2 | L6M rank 38% (p5 -16%, med +4%; adj p 1.00) · PRE rank 22.0% (p5 -5%) | DISAGREE (PRE -0%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| D vol_tag_entry_day=0 x0.5 [before=COMP] | L3M 21→20 · L6M 23→20 · HOLD 97→58 · PRE 241→132 · X' 121→73 | PRE -875→-743 · X' -420→-319 · ALL -1098→-869 | L3M +0.6 (10.5) · L6M -2.0 (7.5) · HOLD -1.1 (8.0) · PRE +0.1 (5.6) · X' +2.0 (5.2) | c=1.28 · L3M +10.0 · L6M +7.1 · HOLD +8.2 · PRE +5.1 · X' +2.3 | L6M rank 12% (p5 -27%, med +36%; adj p 1.00) · PRE rank 2.0% (p5 -42%) | agree (PRE -45%, X' -40%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 calendar/day-type lot line (needs a day-state table in the D6 log writer); Shadow only |
| D prev_daytype=trend x0.5 [before=COMP] | L3M 21→29 · L6M 23→30 · HOLD 97→67 · PRE 241→191 · X' 121→64 | PRE -875→-799 · X' -420→-266 · ALL -1098→-964 | L3M -11.5 (14.3) · L6M -9.5 (8.8)* · HOLD -8.2 (9.3) · PRE -2.7 (6.3) · X' -0.4 (6.8) | c=1.15 · L3M -14.2 · L6M -9.3 · HOLD -7.3 · PRE -2.1 · X' -0.1 | L6M rank 34% (p5 -23%, med +59%; adj p 1.00) · PRE rank 85.5% (p5 -47%) | agree (PRE -21%, X' -47%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 calendar/day-type lot line (needs a day-state table in the D6 log writer); Shadow only |

## 1. The vol-scaled lots rule - found, rebuilt, priced in every window

**Where it is.** `autopilot/DS3_SIZING_REGIME.md` (rule B2 = week-constant lots x clip(median-so-far of the book's own trailing daily-P&L SD / current trailing SD, 0.5, 2), 8-week lookback; B1 = 4-week) and its confirmation test `autopilot/DS3_SIZING_VOLSCALE.md` (D3VS, prereg 455b6db1..., 21 cells, DEAD: fails G3 maxDD/worst week, G6, G7). The remembered "holdout maxDD -68k, SD -8.9k" is B2 HOLD lot-matched: maxDD **+67,935** and SD **+8,899** on the stack (positive = worse). It was shelved on the risk gates, not only on the mean gate: lot-matched it earns more (HOLD +5,992/wk, MDE 5,477) because it runs ~12% more lots in calm weeks, and pays for it in tails. The same rule unmatched (avg lots x0.88) keeps the mean and lowers SD (-5.6k / -10.4k) with mixed maxDD. In the old frames it was a leverage-after-calm rule, not a risk cut. The ledger rows (DEAD_CELLS programs D3VS / SIZING-REGIME) carry means only; the weekly paths were re-run here.

**Rebuild (this part).** Same definition on the one-convention engine: per book (or stack-level, or book x session), the multiplier for label week w = clip(median of earlier trailing SDs / the trailing SD over the L weeks before w, lo, hi) from the unscaled composite's DAILY P&L (causal, needs 8 earlier SD values else 1.0), applied as a week-constant per-row multiplier through mer_fn (multiplied into the ER multiplier, integer half-up min-1 lots), feeding the running-max locks (feed ON) or not (feed OFF, before = composite with the ER feed also off, COMPnf). Placebo = the (book,week) multiplier table permuted across weeks within book (same mean and dispersion by construction), 200 draws.

### Table V1 - full risk line, every window (cell = mean / weekly SD / maxDD / worst-20 / Calmar, $k; worst-20 only where the window has >= 20 weeks of tail)

| stack | L3M | L6M | HOLD | PRE | X' | ALL |
|---|---|---|---|---|---|---|
| as-is stack | 12.2/46/88/-/0.14 | 21.7/44/88/-/0.25 | 21.9/54/144/-/0.15 | 18.6/50/162/-811/0.11 | -3.4/29/317/-572/-0.01 | 13.1/47/317/-1161/0.04 |
| Sunday composite (live ER, feed ON) | 34.4/45/21/-/1.61 | 41.1/43/23/-/1.80 | 38.6/52/97/-/0.40 | 23.1/56/241/-875/0.10 | 8.0/33/121/-420/0.07 | 22.3/50/241/-1098/0.09 |
| composite, ER no-feed (COMPnf) | 21.4/37/36/-/0.59 | 32.9/38/39/-/0.85 | 31.8/46/80/-/0.40 | 16.5/47/225/-801/0.07 | 8.4/30/89/-350/0.09 | 17.6/43/225/-985/0.08 |
| composite minus ER sizer | 21.0/37/43/-/0.49 | 28.0/40/43/-/0.65 | 26.5/44/74/-/0.36 | 19.6/45/140/-684/0.14 | 5.6/27/163/-373/0.03 | 17.2/41/163/-896/0.11 |
| V L8 c0.5-2.0 book feed1 (on composite) | 22.0/37/23/-/0.94 | 33.8/39/24/-/1.41 | 32.2/47/81/-/0.40 | 19.8/47/162/-724/0.12 | 6.7/33/121/-425/0.06 | 18.9/44/162/-946/0.12 |
| V L8 c0.5-2.0 book feed0 (on composite) | 17.0/35/53/-/0.32 | 29.7/37/37/-/0.80 | 28.4/44/78/-/0.36 | 17.4/44/190/-744/0.09 | 8.5/31/89/-378/0.10 | 17.4/41/190/-955/0.09 |
| V ASIS L8 c0.5-2.0 book feed1 (on as-is) | 13.5/33/56/-/0.24 | 23.5/40/56/-/0.42 | 22.4/50/153/-/0.15 | 15.1/48/145/-791/0.10 | -1.6/29/320/-537/-0.00 | 11.9/45/320/-1060/0.04 |
| V L4 c0.5-2.0 book feed1 (on composite) | 26.9/39/23/-/1.16 | 35.3/38/23/-/1.52 | 33.0/47/95/-/0.35 | 21.0/48/176/-725/0.12 | 6.6/33/121/-460/0.05 | 19.6/45/176/-966/0.11 |
| V L13 c0.5-2.0 book feed1 (on composite) | 29.4/38/17/-/1.71 | 36.9/36/17/-/2.18 | 34.6/43/75/-/0.46 | 18.9/48/186/-777/0.10 | 7.6/33/121/-420/0.06 | 19.2/44/186/-978/0.10 |
| V L8 c0.5-2.0 stack feed1 (on composite) | 27.4/39/23/-/1.17 | 37.2/38/25/-/1.51 | 35.1/46/73/-/0.48 | 19.4/43/134/-638/0.15 | 8.0/35/121/-437/0.07 | 19.7/43/134/-889/0.15 |
| V L8 c0.5-2.0 session feed1 (on composite) | 22.8/37/43/-/0.53 | 33.0/36/43/-/0.77 | 31.8/44/69/-/0.46 | 20.0/50/150/-787/0.13 | 7.0/33/121/-447/0.06 | 18.9/45/150/-993/0.13 |

### Table V2 - the named rule and its pre-specified siblings (4/8/13-week, stack-level, session, feed ON/OFF, on the composite and on the as-is stack)

| rule | maxDD $k before→after (same lots) | worst-20 $k (tail windows) | mean Δ $k/wk (MDE) | EQUAL-RISK mean Δ $k/wk | placebo (L6M cut; 200 draws; adj p over F cells) | PRE/X' agree | STRICT / TOLERANT / NOW-ONLY | label | session | D6/D7 mapping |
|---|---|---|---|---|---|---|---|---|---|---|
| V L8 c0.5-2.0 book feed1 [before=COMP] | L3M 21→23 · L6M 23→24 · HOLD 97→81 · PRE 241→162 · X' 121→121 | PRE -875→-724 · X' -420→-425 · ALL -1098→-946 | L3M -12.4 (11.2)* · L6M -7.3 (6.4)* · HOLD -6.4 (6.2)* · PRE -3.2 (5.1) · X' -1.2 (2.3) | c=1.15 · L3M -5.3 · L6M -0.9 · HOLD -0.6 · PRE -2.5 · X' +0.6 | L6M rank 36% (p5 -28%, med +10%; adj p 1.00) · PRE rank 0.5% (p5 -28%) | DISAGREE (PRE -33%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→53 · L6M 39→37 · HOLD 80→78 · PRE 225→190 · X' 89→89 | PRE -801→-744 · X' -350→-378 · ALL -985→-955 | L3M -4.4 (9.2) · L6M -3.2 (6.6) · HOLD -3.4 (6.0) · PRE +1.0 (5.8) · X' +0.2 (2.2) | c=1.04 · L3M -2.3 · L6M -2.2 · HOLD -2.5 · PRE +2.2 · X' +0.6 | L6M rank 80% (p5 -51%, med -36%; adj p 1.00) · PRE rank 22.5% (p5 -30%) | DISAGREE (PRE -16%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V ASIS L8 c0.5-2.0 book feed1 [before=ASIS] | L3M 88→56 · L6M 88→56 · HOLD 144→153 · PRE 162→145 · X' 317→320 | PRE -811→-791 · X' -572→-537 · ALL -1161→-1060 | L3M +1.3 (15.8) · L6M +1.8 (10.1) · HOLD +0.6 (9.0) · PRE -3.5 (7.1) · X' +1.8 (3.9) | c=1.09 · L3M +2.6 · L6M +4.0 · HOLD +2.7 · PRE -2.1 · X' +1.7 | L6M rank 0% (p5 -33%, med -21%; adj p 0.26) · PRE rank 36.5% (p5 -35%) | DISAGREE (PRE -11%, X' +1%) | STRICT n / TOL n / NOW Y (TOL-B Y, TOL-nc n) | RISK-KEEP (L6M only) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-2.0 book feed1 [before=COMP] | L3M 21→23 · L6M 23→23 · HOLD 97→95 · PRE 241→176 · X' 121→121 | PRE -875→-725 · X' -420→-460 · ALL -1098→-966 | L3M -7.5 (11.3) · L6M -5.9 (6.7) · HOLD -5.5 (6.0) · PRE -2.1 (5.7) · X' -1.4 (2.7) | c=1.11 · L3M -3.9 · L6M -2.6 · HOLD -2.8 · PRE -0.7 · X' -0.8 | L6M rank 38% (p5 -43%, med +10%; adj p 1.00) · PRE rank 8.5% (p5 -30%) | DISAGREE (PRE -27%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L4 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→37 · L6M 39→24 · HOLD 80→80 · PRE 225→224 · X' 89→89 | PRE -801→-741 · X' -350→-346 · ALL -985→-922 | L3M -0.9 (9.1) · L6M -2.1 (6.6) · HOLD -2.5 (5.9) · PRE +0.6 (6.4) · X' +1.6 (4.3) | c=1.06 · L3M +0.5 · L6M -0.5 · HOLD -1.4 · PRE +1.6 · X' +2.6 | L6M rank 31% (p5 -52%, med -18%; adj p 1.00) · PRE rank 67.5% (p5 -39%) | DISAGREE (PRE -1%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-2.0 book feed1 [before=COMP] | L3M 21→17 · L6M 23→17 · HOLD 97→75 · PRE 241→186 · X' 121→121 | PRE -875→-777 · X' -420→-420 · ALL -1098→-978 | L3M -5.0 (7.3) · L6M -4.3 (5.2) · HOLD -4.0 (5.6) · PRE -4.2 (4.9) · X' -0.3 (1.3) | c=1.14 · L3M -8.9 · L6M -2.3 · HOLD -1.9 · PRE -0.6 · X' +0.4 | L6M rank 10% (p5 -34%, med +6%; adj p 1.00) · PRE rank 8.5% (p5 -24%) | DISAGREE (PRE -23%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L13 c0.5-2.0 book feed0 [before=COMPnf] | L3M 36→51 · L6M 39→24 · HOLD 80→75 · PRE 225→222 · X' 89→89 | PRE -801→-782 · X' -350→-373 · ALL -985→-961 | L3M -2.9 (9.0) · L6M -4.2 (6.9) · HOLD -4.6 (6.6) · PRE +0.7 (5.7) · X' -0.5 (1.7) | c=1.03 · L3M -3.9 · L6M -3.1 · HOLD -3.2 · PRE +2.4 · X' -0.2 | L6M rank 53% (p5 -51%, med -37%; adj p 1.00) · PRE rank 55.5% (p5 -20%) | DISAGREE (PRE -2%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 stack feed1 [before=COMP] | L3M 21→23 · L6M 23→25 · HOLD 97→73 · PRE 241→134 · X' 121→121 | PRE -875→-638 · X' -420→-437 · ALL -1098→-889 | L3M -7.0 (11.5) · L6M -3.9 (6.3) · HOLD -3.4 (6.3) · PRE -3.7 (5.7) · X' +0.1 (2.7) | c=1.19 · L3M -4.4 · L6M +1.7 · HOLD +2.2 · PRE +0.6 · X' +0.7 | L6M rank 55% (p5 -45%, med +6%; adj p 1.00) · PRE rank 0.0% (p5 -32%) | DISAGREE (PRE -45%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 stack feed0 [before=COMPnf] | L3M 36→50 · L6M 39→39 · HOLD 80→76 · PRE 225→140 · X' 89→89 | PRE -801→-674 · X' -350→-349 · ALL -985→-870 | L3M -0.2 (7.6) · L6M -1.5 (6.7) · HOLD -2.1 (6.2) · PRE +0.9 (6.6) · X' +1.1 (2.8) | c=1.10 · L3M +3.6 · L6M +5.2 · HOLD +4.1 · PRE +1.7 · X' +1.6 | L6M rank 86% (p5 -55%, med -37%; adj p 1.00) · PRE rank 2.5% (p5 -29%) | DISAGREE (PRE -38%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 session feed1 [before=COMP] | L3M 21→43 · L6M 23→43 · HOLD 97→69 · PRE 241→150 · X' 121→121 | PRE -875→-787 · X' -420→-447 · ALL -1098→-993 | L3M -11.6 (11.7) · L6M -8.1 (7.7)* · HOLD -6.8 (7.3) · PRE -3.1 (6.1) · X' -1.0 (2.4) | c=1.10 · L3M -14.9 · L6M -7.9 · HOLD -6.7 · PRE -1.8 · X' -0.0 | L6M rank 60% (p5 -7%, med +76%; adj p 1.00) · PRE rank 2.5% (p5 -34%) | DISAGREE (PRE -38%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | per book x session | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |
| V L8 c0.5-2.0 session feed0 [before=COMPnf] | L3M 36→7 · L6M 39→20 · HOLD 80→79 · PRE 225→225 · X' 89→89 | PRE -801→-773 · X' -350→-355 · ALL -985→-972 | L3M -0.6 (20.4) · L6M -1.8 (10.4) · HOLD -2.0 (9.1) · PRE +1.8 (6.6) · X' +0.9 (2.1) | c=1.01 · L3M -1.3 · L6M -1.9 · HOLD -2.1 · PRE +2.0 · X' +1.0 | L6M rank 28% (p5 -61%, med -32%; adj p 1.00) · PRE rank 56.5% (p5 -22%) | DISAGREE (PRE -0%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | RISK-KEEP (volume effect) | per book x session | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot |

### Table V3 - 12R combined-week-lock line for the pre-specified V cells (lock on both arms; L6M / PRE / X' / ALL maxDD $k and mean delta)

| cell | L6M maxDD | L6M mean Δ (MDE) | PRE maxDD | PRE mean Δ (MDE) | X' maxDD | ALL maxDD |
|---|---|---|---|---|---|---|
| V L8 c0.5-2.0 book feed1 | 27→39 | -11.1 (15.4) | 233→175 | -3.7 (4.4) | 120→120 | 233→175 |
| V L8 c0.5-2.0 book feed0 | 29→59 | -5.0 (11.2) | 209→146 | +5.3 (7.2) | 145→129 | 209→146 |
| V ASIS L8 c0.5-2.0 book feed1 | 116→112 | +3.6 (9.9) | 276→332 | -2.3 (6.7) | 436→428 | 436→428 |
| V L4 c0.5-2.0 book feed1 | 27→35 | -10.6 (15.3) | 233→181 | -2.0 (6.4) | 120→120 | 233→181 |
| V L4 c0.5-2.0 book feed0 | 29→58 | -3.4 (10.7) | 209→179 | +4.5 (7.6) | 145→129 | 209→179 |
| V L13 c0.5-2.0 book feed1 | 27→21 | -3.8 (4.6) | 233→177 | -2.7 (4.6) | 120→120 | 233→177 |
| V L13 c0.5-2.0 book feed0 | 29→50 | -5.6 (6.4) | 209→208 | +3.9 (6.2) | 145→145 | 209→208 |
| V L8 c0.5-2.0 stack feed1 | 27→27 | -5.2 (7.4) | 233→190 | -4.0 (4.5) | 120→120 | 233→190 |
| V L8 c0.5-2.0 stack feed0 | 29→59 | -4.1 (11.1) | 209→124 | +4.9 (7.6) | 145→129 | 209→129 |
| V L8 c0.5-2.0 session feed1 | 27→58 | -9.8 (11.2) | 233→192 | -2.0 (5.8) | 120→120 | 233→192 |
| V L8 c0.5-2.0 session feed0 | 29→59 | -3.7 (14.7) | 209→206 | +4.9 (7.5) | 145→129 | 209→206 |

### Table V4 - all 52 variants, selection view (PRE, X' and ALL only; recent windows for these cells are in cells_all.csv as POST-HOC)

| cell | before | PRE maxDD cut | X' maxDD cut | ALL maxDD cut | PRE mean Δ (MDE) | X' mean Δ (MDE) | eligible (cut >= 20% in both, mean >= -MDE) |
|---|---|---|---|---|---|---|---|
| V L13 c0.5-1.0 book feed1 | COMP | -23% | +0% | -23% | -4.2 (4.9) | -0.5 (1.0) | no |
| V L13 c0.5-2.0 stack feed1 | COMP | -35% | +0% | -35% | -3.6 (4.9) | -0.2 (1.4) | no |
| V L4 c0.5-1.0 stack feed1 | COMP | -38% | +0% | -38% | -4.5 (5.6) | -0.9 (1.4) | no |
| V L13 c1.0-2.0 book feed1 | COMP | -0% | +0% | -0% | +0.0 (0.2) | +0.2 (0.7) | no |
| V L8 c0.75-1.33 book feed1 | COMP | -25% | +0% | -25% | -2.8 (4.6) | -1.2 (2.2) | no |
| V L8 c1.0-2.0 stack feed1 | COMP | -0% | +0% | -0% | -0.1 (0.3) | +0.5 (2.6) | no |
| V L4 c1.0-2.0 stack feed1 | COMP | -0% | +0% | -0% | +0.9 (1.9) | +0.3 (3.0) | no |
| V L4 c0.75-1.33 book feed1 | COMP | -22% | +0% | -22% | -1.8 (4.5) | -1.0 (2.5) | no |
| V L8 c0.5-2.0 book feed1 | COMP | -33% | +0% | -33% | -3.2 (5.1) | -1.2 (2.3) | no |
| V L8 c0.75-1.33 stack feed1 | COMP | -28% | +0% | -28% | -3.3 (4.7) | -0.1 (2.4) | no |
| V L8 c0.5-1.0 book feed1 | COMP | -33% | +0% | -33% | -3.5 (5.1) | -1.2 (1.7) | no |
| V L4 c0.75-1.33 stack feed1 | COMP | -32% | +0% | -32% | -1.7 (4.8) | -0.7 (3.1) | no |
| V L4 c1.0-2.0 book feed1 | COMP | -3% | +0% | -3% | +2.1 (2.4) | -0.4 (2.4) | no |
| V L8 c0.5-1.0 stack feed1 | COMP | -45% | +0% | -45% | -3.6 (5.7) | -0.4 (0.8) | no |
| V L8 c1.0-2.0 book feed1 | COMP | -0% | +0% | -0% | +0.3 (0.4) | -0.1 (1.6) | no |
| V L8 c0.5-2.0 stack feed1 | COMP | -45% | +0% | -45% | -3.7 (5.7) | +0.1 (2.7) | no |
| V L4 c0.5-1.0 book feed1 | COMP | -24% | +0% | -24% | -4.2 (5.1) | -1.0 (1.6) | no |
| V L4 c0.5-2.0 stack feed1 | COMP | -38% | +0% | -38% | -3.6 (6.0) | -0.6 (3.4) | no |
| V L13 c0.75-1.33 stack feed1 | COMP | -28% | +0% | -28% | -3.6 (4.8) | -0.2 (1.4) | no |
| V L13 c0.5-2.0 book feed1 | COMP | -23% | +0% | -23% | -4.2 (4.9) | -0.3 (1.3) | no |
| V L13 c1.0-2.0 stack feed1 | COMP | -0% | +0% | -0% | +0.0 (0.0) | +0.3 (1.2) | no |
| V L4 c0.5-2.0 book feed1 | COMP | -27% | +0% | -27% | -2.1 (5.7) | -1.4 (2.7) | no |
| V L13 c0.75-1.33 book feed1 | COMP | -22% | +0% | -22% | -3.3 (4.6) | -0.3 (1.3) | no |
| V L8 c0.5-2.0 session feed1 | COMP | -38% | +0% | -38% | -3.1 (6.1) | -1.0 (2.4) | no |
| V L13 c0.5-1.0 stack feed1 | COMP | -35% | +0% | -35% | -3.6 (4.9) | -0.5 (0.8) | no |
| V L13 c0.5-1.0 book feed0 | COMPnf | -2% | +0% | -2% | +0.7 (5.7) | -0.3 (1.4) | no |
| V L8 c0.5-1.0 book feed0 | COMPnf | -16% | +0% | -16% | +1.1 (5.8) | -0.2 (1.7) | no |
| V L8 c0.75-1.33 stack feed0 | COMPnf | -15% | +0% | -15% | +1.4 (5.7) | +1.5 (3.1) | no |
| V L4 c0.5-1.0 book feed0 | COMPnf | -2% | +0% | -2% | +0.1 (6.3) | -0.9 (2.2) | no |
| V L8 c0.5-2.0 stack feed0 | COMPnf | -38% | +0% | -38% | +0.9 (6.6) | +1.1 (2.8) | no |
| V L13 c0.5-2.0 book feed0 | COMPnf | -2% | +0% | -2% | +0.7 (5.7) | -0.5 (1.7) | no |
| V L8 c1.0-2.0 book feed0 | COMPnf | -0% | +0% | -0% | -0.2 (0.7) | +0.4 (1.4) | no |
| V L8 c0.5-1.0 stack feed0 | COMPnf | -38% | +0% | -38% | +1.0 (6.6) | +0.0 (0.9) | no |
| V L13 c0.75-1.33 stack feed0 | COMPnf | -15% | +0% | -15% | +1.5 (5.9) | +0.4 (1.8) | no |
| V L4 c0.5-2.0 stack feed0 | COMPnf | -12% | +0% | -12% | -1.2 (6.6) | +3.4 (6.2) | no |
| V L13 c0.5-1.0 stack feed0 | COMPnf | -14% | +0% | -14% | +1.3 (6.0) | -0.3 (1.2) | no |
| V L8 c0.5-2.0 book feed0 | COMPnf | -16% | +0% | -16% | +1.0 (5.8) | +0.2 (2.2) | no |
| V L4 c0.5-1.0 stack feed0 | COMPnf | -12% | +0% | -12% | -1.0 (6.1) | -0.7 (1.7) | no |
| V L13 c0.5-2.0 stack feed0 | COMPnf | -14% | +0% | -14% | +1.3 (6.0) | +0.4 (1.8) | no |
| V L8 c0.5-2.0 session feed0 | COMPnf | -0% | +0% | -0% | +1.8 (6.6) | +0.9 (2.1) | no |
| V L13 c1.0-2.0 stack feed0 | COMPnf | -0% | +0% | -0% | +0.0 (0.0) | +0.7 (1.4) | no |
| V L13 c0.75-1.33 book feed0 | COMPnf | -1% | +0% | -1% | +1.6 (5.7) | -0.5 (1.7) | no |
| V L4 c0.5-2.0 book feed0 | COMPnf | -1% | +0% | -1% | +0.6 (6.4) | +1.6 (4.3) | no |
| V L4 c0.75-1.33 stack feed0 | COMPnf | -13% | +0% | -13% | +0.7 (6.2) | +2.9 (4.6) | no |
| V L8 c0.75-1.33 book feed0 | COMPnf | -11% | +0% | -11% | +1.7 (5.8) | +0.2 (2.2) | no |
| V L4 c1.0-2.0 stack feed0 | COMPnf | -0% | +0% | -0% | -0.2 (2.5) | +4.0 (5.9) | no |
| V L8 c1.0-2.0 stack feed0 | COMPnf | -0% | +0% | -0% | -0.1 (0.2) | +1.1 (2.6) | no |
| V L13 c1.0-2.0 book feed0 | COMPnf | -0% | +0% | -0% | +0.0 (0.4) | -0.2 (0.9) | no |
| V ASIS L8 c0.5-2.0 book feed0 | ASIS | -11% | +1% | +1% | -3.5 (7.1) | +1.8 (3.9) | no |
| V ASIS L8 c0.5-2.0 book feed1 | ASIS | -11% | +1% | +1% | -3.5 (7.1) | +1.8 (3.9) | no |
| V L4 c1.0-2.0 book feed0 | COMPnf | +1% | +0% | +1% | +0.5 (1.4) | +2.5 (3.8) | no |
| V L4 c0.75-1.33 book feed0 | COMPnf | +4% | +0% | +4% | +1.4 (5.7) | +0.8 (3.9) | no |

Cells swept F_V = 52; eligible 0 (all feed-OFF cells: their X' cut is the ER no-feed effect on the first 7 weeks, not the vol rule, see "before" column). Family-wise: the best PRE placebo rank in the group is 0.0% x F = 0.00 adjusted (not significant after the sweep, and the L6M leg fails).

## 2. ER sizers (the live piece, shrunk and re-parameterised variants, KB ER >= 0.20) - with and without the lock feed

Before-stack = composite minus the ER sizer (COMPnoER); the live piece is thr 0.30, 1.5/0.5, all six books, feed ON (ties to the composite, max diff 0.004 = float32 storage). 144 cells: thr {0.15..0.40} x (hi,lo) {(1.5,0.5),(1.25,0.75),(1.0,0.5),(1.5,1.0)} x books {all six, P6+K6, K6 only} x feed {ON, OFF}. The persistence-shrunk ER (f = 0.03 / 0.36 on P6+K6) is priced in DS3_DRAWDOWN.md (ERPK rows) and not repeated.

| rule | maxDD $k before→after (same lots) | worst-20 $k (tail windows) | mean Δ $k/wk (MDE) | EQUAL-RISK mean Δ $k/wk | placebo (L6M cut; 200 draws; adj p over F cells) | PRE/X' agree | STRICT / TOLERANT / NOW-ONLY | label | session | D6/D7 mapping |
|---|---|---|---|---|---|---|---|---|---|---|
| E thr0.30 1.5/0.5 all feed1 [before=COMPnoER] | L3M 43→21 · L6M 43→23 · HOLD 74→97 · PRE 140→241 · X' 163→121 | PRE -684→-875 · X' -373→-420 · ALL -896→-1098 | L3M +13.4 (24.3) · L6M +13.1 (15.0) · HOLD +12.1 (14.9) · PRE +3.5 (8.7) · X' +2.3 (9.1) | c=0.84 · L3M +7.2 · L6M +6.0 · HOLD +5.6 · PRE +0.2 · X' +1.3 | L6M rank 1% (p5 -17%, med +45%; adj p 1.00) · PRE rank 94.0% (p5 -11%) | DISAGREE (PRE +72%, X' -26%) | STRICT Y / TOL n / NOW Y (TOL-B n, TOL-nc Y) | RISK-KEEP (L6M only) | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.30 1.5/0.5 all feed0 [before=COMPnoER] | L3M 43→36 · L6M 43→39 · HOLD 74→80 · PRE 140→225 · X' 163→89 | PRE -684→-801 · X' -373→-350 · ALL -896→-985 | L3M +0.4 (20.0) · L6M +4.8 (12.3) · HOLD +5.3 (11.5) · PRE -3.1 (8.7) · X' +2.7 (8.9) | c=0.91 · L3M -6.8 · L6M -2.7 · HOLD -1.8 · PRE -5.1 · X' +1.9 | L6M rank 7% (p5 -16%, med +49%; adj p 1.00) · PRE rank 91.0% (p5 -16%) | DISAGREE (PRE +61%, X' -45%) | STRICT n / TOL n / NOW Y (TOL-B n, TOL-nc n) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.20 1.5/0.5 K feed1 [before=COMPnoER] | L3M 43→45 · L6M 43→45 · HOLD 74→91 · PRE 140→155 · X' 163→172 | PRE -684→-708 · X' -373→-373 · ALL -896→-926 | L3M +1.7 (5.1) · L6M +1.5 (3.7) · HOLD +1.0 (3.3) · PRE +1.0 (2.4) · X' +1.0 (1.8) | c=0.91 · L3M +1.8 · L6M +2.2 · HOLD +1.6 · PRE -1.3 · X' +0.9 | L6M rank 37% (p5 -15%, med +8%; adj p 1.00) · PRE rank 49.0% (p5 +1%) | DISAGREE (PRE +11%, X' +6%) | STRICT Y / TOL n / NOW Y (TOL-B n, TOL-nc Y) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |
| E thr0.20 1.5/0.5 K feed0 [before=COMPnoER] | L3M 43→43 · L6M 43→43 · HOLD 74→91 · PRE 140→140 · X' 163→163 | PRE -684→-678 · X' -373→-362 · ALL -896→-903 | L3M +0.7 (4.8) · L6M -0.7 (3.2) · HOLD -1.1 (2.9) · PRE +0.0 (2.4) · X' +1.0 (2.3) | c=0.98 · L3M +3.3 · L6M +0.5 · HOLD -0.0 · PRE -0.8 · X' +0.2 | L6M rank 38% (p5 -16%, med +4%; adj p 1.00) · PRE rank 22.0% (p5 -5%) | DISAGREE (PRE -0%, X' +0%) | STRICT n / TOL n / NOW n (TOL-B n, TOL-nc n) | no | all sessions | D6 ER-sizer line parameters (thr/hi/lo/books); Shadow only; no D7 slot |

### Table E2 - best 12 ER variants by the PRE+X' selection score (min of the PRE and X' maxDD cuts; nobody is eligible, so this is the closest-miss list; PRE/X'/ALL only)

| cell | PRE cut | X' cut | ALL cut | PRE mean Δ (MDE) | X' mean Δ (MDE) |
|---|---|---|---|---|---|
| E thr0.20 1.0/0.5 all feed0 | -6% | -22% | -19% | +0.0 (5.5) | +1.1 (3.4) |
| E thr0.20 1.0/0.5 all feed1 | -6% | -23% | -19% | +0.4 (5.1) | +0.9 (3.4) |
| E thr0.15 1.0/0.5 all feed1 | -6% | -16% | -16% | -0.1 (4.1) | +0.8 (3.1) |
| E thr0.15 1.0/0.5 all feed0 | -3% | -15% | -15% | -0.6 (4.3) | +0.8 (3.1) |
| E thr0.35 1.5/0.5 K feed0 | -3% | -2% | -2% | -0.4 (2.0) | +0.3 (2.0) |
| E thr0.40 1.0/0.5 all feed0 | -1% | -24% | -15% | -5.2 (7.8) | -0.9 (5.1) |
| E thr0.30 1.0/0.5 PK feed0 | -0% | -35% | -14% | -2.3 (5.2) | -0.2 (4.4) |
| E thr0.30 1.0/0.5 all feed0 | -0% | -35% | -14% | -3.0 (6.2) | -0.2 (5.2) |
| E thr0.20 1.5/0.5 K feed0 | -0% | +0% | +0% | +0.0 (2.4) | +1.0 (2.3) |
| E thr0.30 1.0/0.5 all feed1 | +0% | -35% | -14% | -2.4 (5.4) | -0.5 (5.3) |
| E thr0.30 1.0/0.5 PK feed1 | +1% | -35% | -13% | -1.7 (4.5) | -0.4 (4.4) |
| E thr0.30 1.5/0.5 K feed0 | +1% | -7% | -7% | -0.0 (2.1) | +0.8 (2.1) |

Cells swept F_E = 144; eligible 0. The ER family is a tail-heavy sizer: in PRE the median cut across the 144 cells is +15% (positive = deeper) and in X' -3%.

### Table E3 - does the multiplier need to feed the locks? (V and E cells, feed ON vs OFF, gain = mean of the cell minus the mean of its own before-stack, $k/wk)

| group | pairs | L6M gain feed ON | L6M gain feed OFF | HOLD ON / OFF | PRE ON / OFF | X' ON / OFF | pairs with larger L6M gain when feeding | median share of the L6M gain due to the feed (gain > 0) | L6M maxDD cut ON / OFF (median) |
|---|---|---|---|---|---|---|---|---|---|
| ER variants | 72 | +5.6 | +1.6 | +4.8 / +1.3 | +2.2 / -1.0 | +1.4 / +1.8 | 60 of 72 | 66% (n=58) | -5% / +8% |
| vol-scaled variants | 26 | -3.7 | -1.4 | -3.5 / -1.8 | -2.5 / +0.5 | -0.4 / +0.8 | 3 of 26 | 6% (n=2) | +5% / -3% |

This is the DS3_ER_LOCKS finding on a 144-cell grid: for the ER family most of the L6M gain is the running-max lock widening (the multiplier scales the governor R), not the size change itself; with the locks held at planned-lot R the gain is a fraction, and the drawdown cut mostly disappears too.

## 3. Day-type / calendar sizers (prev-day type, weekday, VIX tercile, event flags, vol tag) on the composite

Each level x {0.5, 1.5}, feed ON; 42 cells; selection on PRE+X' only.

| cell | PRE maxDD cut | X' cut | ALL cut | PRE mean Δ (MDE) | X' mean Δ (MDE) | eligible |
|---|---|---|---|---|---|---|
| D vol_tag_entry_day=0 x0.5 | -45% | -40% | -45% | +0.1 (5.6) | +2.0 (5.2) | yes |
| D prev_daytype=trend x0.5 | -21% | -47% | -21% | -2.7 (6.3) | -0.4 (6.8) | yes |
| D wd=0 x0.5 | -18% | -43% | -18% | -3.4 (5.2) | +0.4 (3.7) | no |
| D wd=2 x0.5 | -17% | -28% | -17% | -1.2 (4.8) | -0.6 (4.8) | no |
| D event=True x0.5 | -12% | -9% | -12% | +0.2 (3.6) | +1.4 (2.8) | no |
| D opexweek=True x0.5 | -6% | -9% | -6% | -2.3 (4.4) | +0.6 (3.1) | no |
| D opexday=True x0.5 | -3% | -9% | -3% | -1.8 (4.1) | -0.4 (2.3) | no |
| D vix_terc_exp=VIX_mid x1.5 | -2% | -12% | -2% | +4.2 (6.5) | +3.5 (4.9) | no |
| D monthend=True x0.5 | -1% | -7% | -1% | -0.9 (3.4) | -1.5 (3.7) | no |
| D vix_terc_exp=VIX_low x0.5 | -0% | -19% | -0% | -1.6 (3.6) | -1.7 (6.2) | no |
| D vix_terc_exp=VIX_high x0.5 | -35% | +0% | -35% | -5.6 (7.6) | +0.2 (1.5) | no |
| D wd=1 x1.5 | +1% | -17% | +1% | +2.8 (5.6) | +1.4 (4.1) | no |
| D fomc=True x0.5 | -4% | +1% | -4% | +0.4 (2.2) | +0.5 (1.4) | no |
| D monthend=True x1.5 | -7% | +6% | -7% | +1.0 (3.7) | +1.6 (3.9) | no |
| D wd=3 x1.5 | +6% | -30% | +6% | +0.8 (4.7) | +2.5 (4.4) | no |
| D cpi=True x0.5 | +7% | -15% | +7% | -0.8 (2.2) | +0.4 (1.6) | no |
| D opexday=True x1.5 | +2% | +7% | +2% | +1.9 (4.2) | +0.6 (2.3) | no |
| D wd=4 x0.5 | -18% | +7% | -18% | -2.3 (5.4) | -1.4 (4.0) | no |
| D prev_daytype=reversal x1.5 | +8% | -4% | +8% | +0.3 (3.6) | -0.4 (3.0) | no |
| D nfp=True x1.5 | +9% | -3% | +9% | +0.1 (1.5) | -0.7 (2.0) | no |
| D fomc=True x1.5 | +3% | +11% | +3% | +0.1 (1.6) | -0.5 (1.3) | no |
| D vol_tag_entry_day=2 x1.5 | -22% | +11% | -22% | +11.6 (8.2) | +4.3 (4.7) | no |
| D prev_daytype=reversal x0.5 | -7% | +12% | -7% | -1.1 (2.7) | +0.4 (2.5) | no |
| D opexweek=True x1.5 | +3% | +14% | +3% | +2.0 (4.1) | -0.5 (2.4) | no |
| D nfp=True x0.5 | -14% | +15% | -14% | +0.6 (1.7) | +0.2 (2.1) | no |
| D wd=4 x1.5 | +16% | -3% | +16% | +2.0 (5.5) | +0.7 (4.3) | no |
| D cpi=True x1.5 | -7% | +17% | -7% | +0.2 (3.8) | -0.5 (1.4) | no |
| D wd=1 x0.5 | -19% | +18% | -19% | -2.2 (5.8) | -0.9 (4.0) | no |
| D vol_tag_entry_day=1 x0.5 | -31% | +21% | -31% | -0.1 (5.8) | -2.6 (4.8) | no |
| D vol_tag_entry_day=2 x0.5 | +9% | +23% | +9% | -13.3 (9.1) | -5.3 (4.9) | no |
| D vix_terc_exp=VIX_low x1.5 | -0% | +25% | -0% | +2.0 (4.0) | +1.4 (6.3) | no |
| D prev_daytype=range x1.5 | +29% | -19% | +29% | +6.7 (9.5) | +4.8 (6.3) | no |
| D vix_terc_exp=VIX_mid x0.5 | -21% | +33% | -21% | -2.1 (6.2) | -4.6 (5.1) | no |
| D event=True x1.5 | +5% | +33% | +5% | +0.4 (4.4) | -1.7 (2.7) | no |
| D wd=3 x0.5 | +0% | +39% | +0% | -3.1 (5.4) | -3.3 (4.4) | no |
| D wd=2 x1.5 | +10% | +43% | +10% | +1.5 (6.5) | -1.1 (5.0) | no |
| D wd=0 x1.5 | +19% | +50% | +19% | +1.7 (6.3) | -0.4 (3.5) | no |
| D vol_tag_entry_day=1 x1.5 | +51% | -22% | +51% | -1.1 (7.1) | +1.5 (5.0) | no |
| D vix_terc_exp=VIX_high x1.5 | +52% | +0% | +52% | +4.7 (7.9) | -0.6 (1.0) | no |
| D vol_tag_entry_day=0 x1.5 | +28% | +83% | +28% | -2.6 (5.8) | -2.6 (5.4) | no |
| D prev_daytype=range x0.5 | -40% | +103% | +1% | -5.2 (7.7) | -5.4 (6.1) | no |
| D prev_daytype=trend x1.5 | +27% | +120% | +27% | +1.4 (6.7) | -0.9 (6.8) | no |

Stage-2 rows for the eligible and the post-hoc candidates are in Table P1 / P1b (D6/D7 mapping column).

## 4. TG-1 measure sizers (chop-day sizers included) - 4,876 cells, PRE+X' selection, fake-measure null

Every one of the 1219 stored TG-1 measure columns (369 base measures x timeframes; ADX/ER/Chop/Hurst/Donchian/Aroon/…) x 4 shapes (SIZE3 0.5/1/1.5, REV3 1.5/1/0.5, BOT-HALF, TOP-HALF) with tercile cuts fixed per book on 20230401..20250630; multiplier route, feed ON. Engine order of run: T was paused while the wave-1 placebos ran (compute only; no effect on any number).

### Table T1 - enrichment against the fake-measure null (150 random measures, the stored column row-shuffled within book, x 4 shapes = 600 cells)

| shape | real cells | real eligible | fake cells | fake eligible | real both-window cut >= 20% | fake both | real L6M cut >= 20% & mean ok | fake | real eligible & L6M cut >= 20% & mean ok | fake |
|---|---|---|---|---|---|---|---|---|---|---|
| SIZE3 | 1219 | 1.3% | 150 | 2.7% | 2.9% | 5.3% | 4.5% | 0.0% | 0.1% | 0.0% |
| REV3 | 1219 | 0.7% | 150 | 0.7% | 0.7% | 0.7% | 1.6% | 0.7% | 0.1% | 0.0% |
| BOTHALF | 1219 | 25.3% | 150 | 18.0% | 28.4% | 24.0% | 6.7% | 3.3% | 0.3% | 1.3% |
| TOPHALF | 1219 | 10.3% | 150 | 16.0% | 10.3% | 17.3% | 12.9% | 6.0% | 0.3% | 1.3% |
| ALL | 4876 | 9.4% | 600 | 9.3% | 10.6% | 11.8% | 6.4% | 2.5% | 0.2% | 0.7% |

Reading: the share of real measures that pass the PRE+X' test equals the share of shuffled ones in every shape; the BOT-HALF / TOP-HALF cells pass because halving a third of the rows is a volume cut (any 1/3 volume cut lowers PRE and X' drawdown), and they fail to carry into the recent windows in the same proportion as the fake ones. A tercile cut fixed in-sample on PRE+X' cannot be read as an out-of-sample cut in those two windows.

### Table T2 - the 20 PRE+X'-selected T cells with the ONE recent look (stage 2: placebo 200 draws, equal-risk, feed twin, 12R)

| rule | maxDD $k before→after (same lots) | worst-20 $k (tail windows) | mean Δ $k/wk (MDE) | EQUAL-RISK mean Δ $k/wk | placebo (L6M cut; 200 draws; adj p over F cells) | PRE/X' agree | STRICT / TOLERANT / NOW-ONLY | label | session | D6/D7 mapping |
|---|---|---|---|---|---|---|---|---|---|---|

### Table T3 - chop-day measures (Chop14 / ER20 / ADX14 columns) - best 10 by the PRE+X' score (PRE / X' / ALL only)

| cell | PRE cut | X' cut | ALL cut | PRE mean Δ (MDE) | X' mean Δ (MDE) | eligible |
|---|---|---|---|---|---|---|
| T 1d.er20 BOTHALF | -42% | -46% | -42% | -0.0 (5.0) | +0.3 (4.5) | yes |
| T 3m.adx14_x_di BOTHALF | -40% | -39% | -40% | -5.8 (8.1) | -1.3 (4.8) | yes |
| T 15m.fisher10 BOTHALF | -35% | -52% | -35% | -2.2 (6.6) | -0.8 (5.9) | yes |
| T 1m.chop28 BOTHALF | -30% | -34% | -30% | -1.3 (7.2) | -1.1 (5.3) | yes |
| T 3m.chop28 BOTHALF | -49% | -30% | -49% | -4.5 (8.5) | -4.3 (5.8) | yes |
| T 5m.adx14_x_di BOTHALF | -34% | -30% | -34% | -5.9 (7.8) | -1.0 (5.4) | yes |
| T 4h.fisher10 BOTHALF | -29% | -29% | -29% | -3.2 (5.8) | -0.9 (4.7) | yes |
| T 30m.fisher10 BOTHALF | -27% | -43% | -27% | -3.1 (7.1) | +0.7 (4.9) | yes |
| T 1d.fisher10 TOPHALF | -26% | -33% | -26% | -2.0 (5.6) | +0.1 (5.4) | yes |
| T 15m.fisher10 TOPHALF | -25% | -25% | -25% | -4.8 (7.5) | -3.8 (5.7) | yes |

Cells swept F_T = 4,876 (288 chop/ER/ADX cells shown from); eligible 458 (9.4%), fake 9.3%. A Bonferroni over F_T makes the smallest attainable adjusted p (1/201 x 4,876) 24 > 1: no T cell can be called significant by a 200-draw placebo; a LEAD at most.

## 5. META-label sizers (PRE-selected configs; skip route for weight 0, multiplier route for weight > 0)

| cell | PRE cut | X' cut | L6M cut | L6M mean Δ (MDE) | ALL cut | eligible |
|---|---|---|---|---|---|---|
| M FS2 TREE_3m P3 nyam | -42% | +0% | -7% | +0.3 (9.0) | -42% | no |
| M FS1 H4_ENS P3 HM-nyam | -7% | +0% | -0% | -0.5 (1.7) | -7% | no |
| M FS2 H3_6m P3 pre | -0% | +0% | +0% | -0.0 (0.0) | -0% | no |
| M FS1 H1_6m P2 pre | -0% | +0% | +0% | -0.0 (0.0) | -0% | no |
| M FS1 TREE_6m P1 MV-london | +2% | +0% | +0% | +0.3 (0.9) | +2% | no |
| M FS1 H1_ENS P1 SM-london | -5% | +0% | +0% | -0.8 (1.7) | -5% | no |
| M FS2 TREE_3m P3 MV-nyam | -7% | +0% | +1% | +0.3 (3.3) | -7% | no |
| M FS2 TREE_3m P2 SM-asia | -1% | +0% | +2% | +0.4 (2.4) | -1% | no |
| M FS1 H4_3m P3 SM-asia | -8% | +0% | +3% | +0.9 (3.0) | -8% | no |
| M FS2 TREE_3m P1 HM-nyam | -5% | +0% | +6% | +0.1 (1.4) | -5% | no |
| M FS1 H4_12m P1 nypm | -3% | +0% | +9% | -0.2 (1.5) | -3% | no |
| M FS2 TREE_3m P3 MV-london | -8% | +0% | +10% | -1.2 (1.8) | -8% | no |
| M FS2 H2_12m P4 HM-asia | -9% | +0% | +11% | +0.0 (2.1) | -9% | no |
| M FS1 H2_ENS P3 HM-asia | -4% | +0% | +17% | +1.8 (4.4) | -4% | no |
| M FS1 H2_12m P5 nyam | -26% | +0% | +22% | -2.1 (5.3) | -26% | no |
| M FS2 H1_6m P5 KB-asia | -2% | +0% | +23% | -0.8 (3.0) | -2% | no |
| M FS1 TREE_12m P2 KB-asia | -3% | +0% | +34% | -0.8 (1.8) | -3% | no |
| M FS2 TREE_12m P5 nypm | -1% | +0% | +34% | +0.5 (1.9) | -1% | no |
| M FS1 H1_ENS P3 MV-nyam | -4% | +0% | +48% | -1.6 (3.0) | -4% | no |
| M FS2 H2_6m P5 asia | -19% | +0% | +61% | -0.8 (9.1) | -19% | no |
| M FS2 H2_ENS P5 SM-london | -13% | +0% | +65% | -1.2 (2.7) | -13% | no |
| M FS1 H1_12m P4 POOLED | -22% | +0% | +98% | -0.7 (10.2) | -22% | no |
| M FS2 H4_ENS P2 POOLED | -33% | +0% | +124% | -1.1 (18.6) | -27% | no |
| M FS1 TREE_6m P1 london | +3% | +0% | +128% | -1.7 (4.7) | +3% | no |
| M FS2 TREE_6m P2 london | -10% | +0% | +166% | -2.0 (7.1) | -10% | no |
| M FS2 TREE_6m P2 PE-london | -13% | +0% | +192% | -0.8 (6.6) | -13% | no |
| M FS1 TREE_6m P2 PE-london | -10% | +0% | +193% | -2.3 (7.3) | -10% | no |
| M FS1 TREE_3m P2 asia | +2% | +0% | +307% | -4.1 (10.8) | +2% | no |

Shown for completeness (the L6M column is a descriptive look at the 28 PRE-selected configs, not a selection); X' is 0% for every cell because META scores start in 2024-02. None is eligible and no META cell was sent to the placebo unless it also appears in Table P1b.

## 6. Lock-feed test for the selected D / T sizers (multiplier feeding the running-max locks vs not; before = COMP resp. COMPnf)

| cell | feed ON: L6M maxDD cut / mean Δ | feed OFF: L6M maxDD cut / mean Δ | feed ON: PRE cut / mean Δ | feed OFF: PRE cut / mean Δ |
|---|---|---|---|---|
| D vol_tag_entry_day=0 x0.5 | -14% / -2.0 | -21% / -2.2 | -45% / +0.1 | -18% / +0.0 |
| D prev_daytype=trend x0.5 | +31% / -9.5 | -19% / -4.9 | -21% / -2.7 | -9% / -2.4 |
| D vix_terc_exp=VIX_high x0.5 | -38% / -4.2 | -53% / -1.5 | -35% / -5.6 | -9% / -4.4 |

## 7. EQR / lots_factor family (156 stored series, OLD frame, own lots; no engine re-run, no new selection)

DS3_EQUAL_RISK (EQR, 2026-10-30) scored 153 rule series as lot factors at equal worst-20; the stored window stats (rule vs the frame's stack, at their own lots) are re-read on drawdown. OLD frame = the pre-one-convention stack (different baseline levels), M basis = market entries with target-fill correction (optimistic), N basis = realistic fills. Windows available in the file: Y26, L6M, HOLD, PRE, X', WF (no L3M). Label = L6M cut >= 20% & mean >= -MDE; no placebo re-run here (EQR carries its own random-skip placebo).

Counts: 156 series; L6M maxDD cut >= 20% & mean inside MDE: 18; PRE and X' both cut >= 20%: 16; both conditions: 7.

| series | family | selection | L6M maxDD cut (before→after $k) | PRE cut | X' cut | L6M mean Δ (MDE) | PRE mean Δ (MDE) | X' mean Δ (MDE) | equal-risk L6M mean Δ | label |
|---|---|---|---|---|---|---|---|---|---|---|
| A|B|EL|N | entry+loss | looked(L6M-ranked) | 372→130 (-65%) | -10% | +16% | +40.5 (48.2) | -42.3 (31.5) | -12.6 (29.8) | +79.7 | RISK-KEEP (old frame; L6M only) |
| A|B|E|M | dip-entry (book-own best) | looked(L6M-ranked) | 608→216 (-64%) | -21% | +31% | +53.0 (46.0) | -11.0 (26.7) | -9.7 (23.9) | +79.3 | RISK-KEEP (old frame; L6M only) |
| A|B|E|N | dip-entry (book-own best) | looked(L6M-ranked) | 372→152 (-59%) | -30% | +18% | +44.6 (45.8) | -22.1 (29.7) | -13.4 (24.2) | +90.3 | RISK-KEEP (old frame; L6M only) |
| A|B|EL|M | entry+loss | looked(L6M-ranked) | 608→262 (-57%) | +4% | +16% | +51.9 (49.1) | -28.3 (27.3) | -8.5 (29.6) | +76.3 | RISK-KEEP (old frame; L6M only) |
| A|B|EPL|M | joint entry+profit+loss | looked(L6M-ranked) | 608→289 (-52%) | -11% | -23% | +53.5 (59.2) | -30.0 (32.7) | -4.4 (32.7) | +81.6 | RISK-KEEP (old frame; L6M only) |
| A|B|EP|M | entry+profit | looked(L6M-ranked) | 608→290 (-52%) | -34% | -31% | +49.4 (57.9) | -11.9 (31.1) | -4.0 (29.8) | +79.3 | RISK-KEEP (old frame; agree) |
| G|ADDUW|B2_PRE#5 | staged under-water adds B2_PRE#5 | PRE-selected | 204→137 (-33%) | +14% | -15% | +6.8 (18.1) | +6.4 (14.7) | +4.3 (9.6) | +11.6 | RISK-KEEP (old frame; L6M only) |
| A|B|EP|N | entry+profit | looked(L6M-ranked) | 372→253 (-32%) | -32% | -21% | +15.4 (56.7) | -36.9 (34.5) | -14.0 (30.3) | +42.6 | RISK-KEEP (old frame; agree) |
| B|EXP2|B_FROZEN_P | EXP2 joint (bracket tilt/TH profit/TH loss) | PRE-selected | 466→317 (-32%) | +4% | -20% | -18.7 (68.3) | -13.8 (36.4) | -4.8 (40.3) | -9.4 | RISK-KEEP (old frame; L6M only) |
| A|B|P|M | profit: plain 70% take | looked(L6M-ranked) | 608→436 (-28%) | -36% | -32% | +26.8 (37.6) | -1.8 (19.2) | +7.6 (20.7) | +34.3 | RISK-KEEP (old frame; agree) |
| A|H|P|M | profit: plain 70% take | PRE-selected | 608→436 (-28%) | -42% | -34% | +29.6 (46.7) | -4.1 (21.6) | +4.5 (26.1) | +39.4 | RISK-KEEP (old frame; agree) |
| C|F|A06+B02 | T-STACK F combine A06+B02 | PRE-picked | 204→147 (-28%) | -30% | -21% | -5.2 (21.6) | +11.0 (14.2) | -6.3 (14.9) | +10.3 | RISK-KEEP (old frame; agree) |
| A|B|EPL|N | joint entry+profit+loss | looked(L6M-ranked) | 372→273 (-27%) | -19% | -13% | +17.1 (59.7) | -55.5 (35.9) | -14.3 (33.0) | +41.2 | RISK-KEEP (old frame; L6M only) |
| A|H|EP|M | entry+profit | PRE-selected | 608→450 (-26%) | -35% | -32% | +32.7 (50.8) | -1.4 (22.6) | +4.2 (26.3) | +43.9 | RISK-KEEP (old frame; agree) |
| C|F|A06+HM5R | T-STACK F combine A06+HM5R | PRE-picked | 204→151 (-26%) | -41% | -3% | -9.6 (36.6) | +12.2 (25.1) | -11.2 (24.9) | +9.4 | RISK-KEEP (old frame; L6M only) |
| G|ADDUW|B2_L6Mrank#4 | staged under-water adds B2_L6Mrank#4 | looked(L6M-ranked) | 204→153 (-25%) | +49% | -0% | +15.6 (18.3) | -0.7 (13.3) | +0.3 (12.8) | +13.1 | RISK-KEEP (old frame; L6M only) |
| A|B|L|M | loss: L2SL cut/tighten | looked(L6M-ranked) | 608→471 (-23%) | -6% | +4% | +24.0 (32.5) | -15.2 (20.1) | -3.1 (17.6) | +25.9 | RISK-KEEP (old frame; L6M only) |
| C|F|A06+HM5R+B02 | T-STACK F combine A06+HM5R+B02 | PRE-picked, HOLD-admitted | 204→161 (-21%) | -45% | -26% | -12.2 (38.8) | +12.3 (25.4) | -9.1 (24.9) | +11.4 | RISK-KEEP (old frame; agree) |
| A|B|PL|M | profit+loss | looked(L6M-ranked) | 608→500 (-18%) | -38% | -28% | +43.5 (47.5) | -17.4 (26.9) | +3.5 (24.5) | +53.0 | PRE/X' cut only (L6M no) |
| A|H|EPL|M | joint entry+profit+loss | PRE-selected | 608→592 (-3%) | -42% | -31% | +25.8 (56.3) | +8.0 (23.6) | +10.8 (26.6) | +38.7 | PRE/X' cut only (L6M no) |
| A|H|PL|M | profit+loss | PRE-selected | 608→601 (-1%) | -44% | -26% | +26.1 (58.0) | +5.0 (23.0) | +10.2 (27.1) | +38.8 | PRE/X' cut only (L6M no) |
| F|CW|ALL6 | cut-and-wait all six PRE-best cells | PRE-selected | 622→699 (+12%) | -22% | -26% | -44.4 (64.6) | -4.7 (37.0) | +3.8 (45.4) | -47.2 | PRE/X' cut only (L6M no) |
| A|B|P|N | profit: plain 70% take | looked(L6M-ranked) | 372→421 (+13%) | -34% | -30% | -4.9 (39.3) | -23.4 (21.1) | +0.2 (20.8) | -0.2 | PRE/X' cut only (L6M no) |
| A|H|P|N | profit: plain 70% take | PRE-selected | 372→429 (+15%) | -41% | -23% | -9.0 (50.0) | -31.7 (24.7) | -6.1 (26.6) | -3.5 | PRE/X' cut only (L6M no) |
| A|H|EP|N | entry+profit | PRE-selected | 372→444 (+19%) | -33% | -22% | -7.5 (51.5) | -29.1 (25.0) | -6.4 (26.9) | -1.5 | PRE/X' cut only (L6M no) |
| A|B|PL|N | profit+loss | looked(L6M-ranked) | 372→469 (+26%) | -40% | -24% | +12.3 (48.2) | -40.3 (29.4) | -3.9 (24.4) | +19.8 | PRE/X' cut only (L6M no) |
| A|H|EPL|N | joint entry+profit+loss | PRE-selected | 372→597 (+61%) | -38% | -20% | -14.6 (60.3) | -19.7 (25.5) | +0.2 (26.8) | -5.9 | PRE/X' cut only (L6M no) |

The series that cut in all three windows are exit/entry/profit-take/loss-cut combinations (plain 70% take, entry+profit, T-STACK F combos): they are the A1/A2 parts' rules priced as lot factors, not sizing rules. Full 156-row table: out/dd_reread/a3/q_oldframe_eqr.csv.

## 8. Shadow list with D6/D7 mapping (nothing is promoted)

Shadow candidates = stage-2 cells whose PRE maxDD cut is >= 20% AND beats the 200-draw placebo in PRE (rank <= 5%) AND whose L6M mean is not beyond -MDE. They are risk hedges against a 2024-25-type regime (the composite's own weakness: PRE maxDD 162k -> 241k vs the as-is), not L6M improvements.

| cell | PRE maxDD before→after | PRE worst-20 | PRE placebo rank | L6M maxDD (same cell) | L6M mean Δ (MDE) | equal-risk L6M / PRE mean Δ | D6/D7 mapping | what would promote it |
|---|---|---|---|---|---|---|---|---|
| V L8 c0.5-2.0 stack feed1 [before=COMP] | 241→134 (-45%) | -875→-638 | 0.0% | 23→25 | -3.9 (6.3) | +1.7 / +0.6 (c=1.19) | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot | a pre-registered forward window (>= 14 weeks) with PRE-type conditions in which it cuts maxDD >= 20% without a beyond-MDE mean cost; the 2024-25 regime signature from part B (state gate) as its switch |
| V L8 c0.5-2.0 stack feed0 [before=COMPnf] | 225→140 (-38%) | -801→-674 | 2.5% | 39→39 | -1.5 (6.7) | +5.2 / +1.7 (c=1.10) | D6 new policy line: weekly per-book lot multiplier (Sunday, from trailing daily-P&L SD), engine multiplier route; Shadow only; no D7 slot | a pre-registered forward window (>= 14 weeks) with PRE-type conditions in which it cuts maxDD >= 20% without a beyond-MDE mean cost; the 2024-25 regime signature from part B (state gate) as its switch |
| D vol_tag_entry_day=0 x0.5 [before=COMP] | 241→132 (-45%) | -875→-743 | 2.0% | 23→20 | -2.0 (7.5) | +7.1 / +5.1 (c=1.28) | D6 calendar/day-type lot line (needs a day-state table in the D6 log writer); Shadow only | a pre-registered forward window (>= 14 weeks) with PRE-type conditions in which it cuts maxDD >= 20% without a beyond-MDE mean cost; the 2024-25 regime signature from part B (state gate) as its switch |

## 9. Integrity, cells swept, corrections, deviations

* **Cells swept per group (F):** V 52, E 144, D 42, T 4,876 (+600 null), M 28; stage-2 (placebo 200 draws) on 27 cells = the pre-specified ones (15), the PRE+X'-selected ones (V 2+D/E/M in wave 1, T 0), and 10 post-hoc L6M-candidates per wave. Family-wise correction shown as adj p = min(1, F x rank) in the placebo column; at 200 draws a rank below 1/201 x F is unreachable for F > 201, so **no T cell and no E/V cell is significant after the sweep.**
* **Selection** used PRE and X' only (maxDD cut >= 20% in BOTH, mean >= -MDE in both), top 10 per group (T: top 20); the ONE recent look is the stage-2 line of those cells. The pre-specified cells (NAMED rule and siblings, live ER, KB ER>=0.20) show every window regardless. The 10 L6M-candidates per wave were chosen on L6M (post-hoc, labelled) only to give the RISK-KEEP label an honest placebo; they do not enter any selection.
* **Top-N by in-sample drawdown is post-hoc.** The Table P1 ordering by L6M cut is a presentation order of already-selected rows.
* **Deviations from the prereg:** (1) V feed-OFF cells use COMPnf (composite with the ER feed also off) as before-stack, so the vol rule is not charged with the ER feed switch (the prereg said COMP; both are in cells_all.csv via the absolute lines; this is stated in the V4 "before" column). (2) T was paused during wave-1 placebos (compute order only). (3) D cells number 42 (21 levels x 2), under the <= 120 bound. (4) Wave-2 post-hoc candidates capped at 10. (5) Equal-risk uses the grid 0.6/0.7/0.8/0.9/1.1/1.25/1.5 plus one verification run at c*.
* **Warm-up caveat:** vol-scaled multipliers are 1.0 until L+8 weeks of history exist (L=8: first 16 weeks), so X' (44 weeks starting 2023-04-03) is 36% neutral and its maxDD episode (weeks 1-7) is untouchable. **META:** scores exist only from 2024-02. **TG-1 measures:** terciles fixed on 20230401..20250630, so PRE and X' are in-sample for T cells and only L3M/L6M/HOLD are out of sample.
* **Ties:** COMP, ASIS, COMPnf, COMPnoER and the 12R/20R/30R locks tie to DD-1 main_*.pkl at max daily diff 0.0; the live ER cell ties to COMP at 0.004 (float32 storage).
* **Files:** code `l2vast/ds3/code/dd_a3/` (a3_lib, a3_cells, a3_run, a3_s2, a3_s2an, a3_an, a3_plan, a3_report, make_doc, a3_q, a3_tc); results `l2vast/ds3/out/dd_reread/a3/` (res_*.pkl, s2_*.pkl, cells_all.csv, cells_N.csv, q_oldframe_eqr.csv, stage2_sets_*.json); rows `l2vast/ds3/out/recent_wins/dd_reread_a3.csv`; DEAD_CELLS +rows program A3SZ (append only).