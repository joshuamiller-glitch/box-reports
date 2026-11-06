# PE-BUSY-THINNING (ZL-1, 2026-11-06) - blind-week defect #2: gen_core2 thins signals against the NOMINAL library trade
Prereg l2vast/ds3/prereg/PE_BUSY_THINNING_prereg.md sha256 bfb468e59a4fe2578e412b234217a907f1399e09aa25fd8b78a10e7ef50e2d5b (logged before any statistic). Research only, Shadow only, no PASS claim. The variant of Part 4 is POST-HOC (made after live was seen) and never replaces the sealed prediction. The seal incident that happened during this job is in SEAL_INCIDENT_20261106_ZL1.md (restored cache + tie-out on a private tree).

## Mechanism
gen_core2 (and R2.gen / ba_rows2.gen) skip a raw pullback event while `bar <= busy`, busy = nominal library exit (60-pt stop / 1R target / structure exit) of the previous ACCEPTED row. The engine (oc_lib run_book4 via d7_v13t._book4_t: okp / busy = fin[j]) and live apply the same one-position rule with the ENGINE exit (cut, target, lock). A row that the engine cuts early, or never trades, still blocks the library generator until its nominal exit, so the next raw events never become rows. The engine already has the exit-aware rule; it is starved of rows.

## Part 1 - size on the PE history (pb3 tape starts 2023-02-10: PE history is 2023-04..2026-11-05, not 13 years; the 13-year NQ tape is not the PE tape)
R = unthinned generator rows (busy=-1, BASE-4 tree pe_nobusy), T = thinned rows (the sealed chain), E = engine P6 trades of the REDO history ledger (P2 config), A = exit-aware scan lower bound (busy until the ENGINE exit when the engine traded the old row, until the nominal exit for new rows - upper bound on busy - and flat when the engine did not trade the old row). Code code/pe_busy/pe_busy_hist.py; tables /mnt/l2/l2vast/ds3_base4/pe_busy_hist_tab.pkl.
| year | raw events R | thinned rows T | dropped by nominal busy | engine trades E | A: old rows taken | A: NEW rows taken | new rows nominal target / stop |
|---|---|---|---|---|---|---|---|
| 2023 | 12,486 | 888 | 92.9% | 486 | 271 | 626 | 330 / 295 |
| 2024 | 16,607 | 1,715 | 89.7% | 927 | 531 | 1,139 | 616 / 522 |
| 2025 | 16,358 | 2,476 | 84.9% | 1,298 | 829 | 1,424 | 738 / 685 |
| 2026 (to 11-05) | 13,966 | 3,203 | 77.1% | 1,567 | 1,278 | 1,607 | 825 / 782 |
| all | 59,417 | 8,282 | 86.1% | 4,280 | 2,909 | 4,796 | |
Reading: the library generator keeps 14% of the raw PE events. An exit-aware rule (engine exits) would take about 7,705 PE trades over the history (lower bound: new rows are assumed busy to their nominal exit and the engine's own blocks are kept), versus 4,280 engine trades today, i.e. 1.8x the PE trade count. The newly recoverable rows are nominally about 51% targets, 49% stops (library outcome); the indicative nominal dollar value of the new rows (x mean engine lots 5.6, 3.5-pt cost, NO cuts, NO L2) is -$21k (2023), +$205k (2024), -$233k (2025), -$296k (2026): not engine P&L, sign flips by year, do not use. Their real value depends on cuts (engine cuts 27-32 of the 43-63 PE trades in the blind week) which only exist after Part 3.

## Part 2 - exit-aware generator
code/pb3/pb3_core2_exitaware.py (pb3_core2.py untouched): gen_core2_ea = gen_core2 source with `busy=xb` replaced by `busy=REL.get((bar,side),xb)`; REL maps (entry bar, side) -> bar of the engine exit; exit_sec_to_bar helper. Tie-out (pb3_core2_exitaware_test.py): REL={} gives 8,497 rows, identical to gen_core2. The fixed-point loop (generate, engine, exits, regenerate) is not needed in practice: the engine applies the one-position rule itself with its own exits, so giving it the UNTHINNED rows is the exit-aware result in one pass (what Part 4 does).

## Part 3 - L2 loss rows for the new ids
code/blind/cell_run_nb.py (tag pe_nb): PE rows = sealed thinned rows everywhere + ALL unthinned rows with entry after the old cap (label day > 2026-02-06; 12,252 rows, 9,330 of them new, kept ids before the cap stable: 5,361 old PE ids unchanged). Before the cap the unthinned extras (41.8k rows) are NOT added (that would need 2023-2026-02 THP/L2 builds), so the history before 2026-02-07 stays thinned. Chain with ZL-2's UNCHANGED builders (thp_build loss rows ldp10s for PE months 2026-02..11, l2feat_blind_build dp10s, trades_arm, blind_c3_path, blind_l2s_rows, universe_er, poi_feats, masks) in private dirs (out/pe_nb, ds3_thp_pe_nb, ds3_l2feat_pe_nb, out/l2set_pe_nb, out/thp_pe_nb); builders were patched only to restrict thp_build/l2feat to PE and to skip profit-mode 1-s tables. Result: l2set_pe_nb/loss/rows.parquet 26.27M rows (sealed 23.62M), tidx_cut 76,044 trades (66,714), 12,252 post-cap PE ids with loss rows. Build 164 s with 5 workers. (gen_poi / POI streams were not rebuilt: the zone layer reads the sealed streams; stated limitation.)

## Part 4 - blind week re-run with cuts ON (separate variant, POST-HOC)
Recipe = the sealed one (var_run.py, SLOTS=1 NOX=1, per-period configs P0/P1/P2) on tree pe_nb. Tie-out of the recipe on a private copy of the sealed tree with the restored cache: +34,878.54 / 182 trades exactly. In the variant every non-PE book is identical to the sealed list (A6 9,067, H6 9,266, K6 10,319, M6 2,490, U6 6,675, X3 -6,215, X4 -1,517, X5 2,390), so the change is isolated to P6.
| | sealed | variant pe_nb | live |
|---|---|---|---|
| total net | +34,879 (182 tr) | +69,582 (202 tr) | +104,095 (187 tr) |
| P7 (engine P6) net | +2,404 (43 tr, 206 lots) | +37,107 (63 tr, 297 lots; 32 TH-L2 cuts, 26 targets, 4 other, 1 lock) | +86,010 (53 tr, 247 lots) |
Frozen compare tool (config sha 1b92b848..., criteria unchanged; output BLIND_COMPARE_PE_NB.md): matched/union 50.8% (+-2 s 49.6%; +-60 s 50.2%; +-120 s 50.8%), net gap +34,513 (33%), 202 vs 187 trades, live-only 56 (+56,260), engine-only 71 (-46,495), exit-type agreement below threshold, NOT faithful (all four criteria still fail). P7 alone: 41 matched pairs (matched/union 54.7%), exit-type agreement 63%, matched engine +16.9k vs live +46.2k; live-only 12 (+39.8k), engine-only 22 (+20.2k). Before: 21 live-only P7 trades, 16 of them behind the thinning. Reading: the row set was the main cause of the missing P7 re-entries (P7 model from 2.8% to 43% of live P7; total from 33% to 67% of live), but the engine is still not faithful: 22 P7 trades the engine takes and live does not (+20k), 63% exit agreement on matched P7 (the 8 false cuts are an open defect, not touched here), and the remaining $49k P7 gap is mostly sizing/exit type on matched trades and the 12 live-only trades. A one-week post-hoc result: no edge claim.

## Part 5 - which earlier conclusions change if the PE row set is larger
Every statement here is qualitative except where Part 1/4 give numbers; none is re-run.
1. PE trade counts and P&L in every table built from gen_core2 / R2.gen rows (pb3_eval2, pb3_dbuild, pb3_final_md, pbx_ent, x_pb3, x_pb3_sig, p9_heavy, sb2/pb3_trades + repro_text, stk_e/stke_lib, t4/t4_lib, find_c/bd_ev, cap/redo_pe, blind_pe, the PE page chain): the library row set is a 14% sample of raw events; any count (trades per year, per day, lots per day), any total (PE net, PE share of the stack), any per-trade statistic computed on rows is biased by the thinning - per-trade averages are for the first signal after each nominal exit, not for every signal. Direction of the totals: up if per-trade engine expectancy after cuts is positive (blind week: +$37k vs +$2k on 63 vs 43 trades), unknown otherwise (nominal outcome flips sign by year).
2. Stack Calmar / drawdown: PE would carry about 1.8x its trade count (Part 1) with many more simultaneous cut/stop exits; the stack drawdown profile and day-correlation with the other books change (more PE exposure on trend-reversal days). Calmar can move either way; the 13-year stack tables do not contain PE before 2023 anyway.
3. Sizer / lots (equal-risk, ER sizer, Shadow lot table): lot rules were fitted on the thinned row set (P6 lots per trade, ER bins); with more rows, the per-trade risk bins, daily lot totals and the lot caps (max lots / locks, per-book day/week locks R scaled by lots) would bind more often; the 'P6 lots' column of the Shadow lot table is a per-trade lot, still valid per trade, but the expected daily PE lots are about 1.8x and the day-lock hit rate changes. Re-fit needed only if the unthinned rows are adopted for research.
4. PE sizing and PE locks: sized on rows with first-signal-after-nominal-exit; the unthinned set adds re-entries after early exits (cut re-entry, target re-entry), which the live strategy already takes; so the live PE sizing risk is understated by research tables.
5. Other books on R2.gen (ST/HM/KB/SM and the chain): the same busy line exists; the effect size is unmeasured here; BASE-4 reported the cell variant for PE only. Stated as open.
6. The blind-week comparison itself: sealed 'engine faithful' verdict stands for the sealed prediction; the post-hoc variant shows defect #2 explains roughly $34.7k of the $86k P7 gap and does not change the verdict.
Limitations: history before 2026-02-07 not extended (needs THP/L2 builds for ~42k more trades; the history count A is a scan, not an engine run); POI streams not rebuilt; one week.

Files: code/pe_busy/pe_busy_hist.py, code/pb3/pb3_core2_exitaware.py (+_test.py), code/blind/cell_run_nb.py, var pkl /mnt/l2/l2vast/ds3_base4/defects/var_zl1_pe_nb.pkl (+ log), pred csv .../pe_nb_pred.csv, BLIND_COMPARE_PE_NB.md.


## OTHER BOOKS (ZL-1, 2026-11-06; prereg l2vast/ds3/prereg/OTHER_BOOKS_BUSY_prereg.md sha256 8dc0075ff25d496239601c87f2156a592e8b1a19cd116ac05d908cadb70fa43d)
Code: code/pe_busy/ob_rows.py (busy=-1 exec patch of ba_rows2.gen, old module untouched), ob_hist.py, ob_week.py; outputs /mnt/l2/l2vast/ds3_base4/otherbooks/. Tie-out: the thinned rows regenerated by ob_rows equal the sealed rows (ei, side, pts identical) for ST, HM, KB, SM. The sealed prediction used below is the private-tree reproduction (+34,878.54 / 182); no sealed file was opened for this block.

### Safety audit (done first)
Every derived script (code/blind/chain_cells/*/, cell_run_nb.py) was grepped for sealed-tree names. The only derived script that wrote to the sealed tree through an un-rewritten string was my blind_c3_path.py (incident note). Two latent hazards for BASE-4: (a) the *L replicate cells (kbL, hmL, smL, pbL) keep `THP = OUTD + 'thp_blind/'` in their derived thp_common.py, so their thp_index step writes the sealed out/thp_blind/trade_index.parquet (identical content by construction, the cell is a live replicate); (b) every cell's derived thp_common keeps DATA/AUX = ds3_thp_blind/..., harmless only because no cell runs thp_build. Nothing here wrote outside /mnt/l2/l2vast/ds3_base4/otherbooks and autopilot (append).

### Families that carry the busy gate (static scan of the code)
D7 book map (d7lib BKT): KB=K6/K7, PE=P6/P7, SM=U6/U7, HM=H6/H7, MV=M6/M7, PB=A6/A7; ST is not a D7 book. Generators with the nominal-exit busy gate:
- ba_rows2.gen (R2.gen): ST, HM, KB, SM (the sealed base rows for K7, U7, H7 and the ST row set) and EM, PE-base. Consumers: cap/redo_rows_base, blind_rows_base, ba_stage2, ba_prereg2, ba_rows3, t4_lib, sd56_validate, bars_cand/bc_lib+bc_cells, recent_wins_redo/D4/s_d6_ba, pb3_eval2.
- pb3_core2.gen_core2: PE (P7).
- blind_be_lib (pb7 engine): A6/A7 ('one position per engine and bar type ... busy rule', nominal bracket exit). Not measured here (no raw-event store).
- tr2_lib (DN, CR), x_tr1 (MV/MA = M7, not verified in code), te_core, ab_core, pb2_lib, tr4_lib, sd56_lib: research libraries with the same `busy=xb` line.
- g3seq.py and cw_lib.py / bk_lib.py are the exception: g3seq re-simulates the sequence so that an early exit frees the book and later raw signals are taken; cw_lib is a sequence chain; bk_lib regenerates rows with a busy chain. Research that ran through those (cut-wait, block/un-block, knock-on studies) already contains part of the knock-on; research that used the stored base rows (R2.gen output) directly did not. I did not audit which pages used which; open item.

### Part 2 - history (2023-04-03..2026-11-05; R = valid raw events as rows with busy=-1, T = sealed thinned rows, E = engine trades in the REDO history ledger P2 config, A = exit-aware lower bound with the PE recipe)
| book (D7) | year | R | T | dropped | E | A old | A new | A total |
|---|---|---|---|---|---|---|---|---|
| ST (no D7 book) | all | 33,528 | 8,260 | 75.4% | - | - | - | - |
| HM (H7) | 2023 | 4,129 | 757 | 81.7% | 354 | 317 | 410 | 727 |
| HM | 2024 | 5,465 | 1,377 | 74.8% | 630 | 569 | 669 | 1,238 |
| HM | 2025 | 5,420 | 1,818 | 66.5% | 749 | 673 | 818 | 1,491 |
| HM | 2026 | 4,749 | 2,293 | 51.7% | 987 | 901 | 848 | 1,749 |
| HM | all | 19,763 | 6,245 | 68.4% | 2,721 | 2,460 | 2,745 | 5,205 |
| KB (K7) | 2023 | 8,632 | 913 | 89.4% | 710 | 478 | 561 | 1,039 |
| KB | 2024 | 11,305 | 1,777 | 84.3% | 1,388 | 984 | 927 | 1,911 |
| KB | 2025 | 11,250 | 2,521 | 77.6% | 1,945 | 1,467 | 1,240 | 2,707 |
| KB | 2026 | 9,804 | 3,344 | 65.9% | 2,475 | 1,905 | 1,422 | 3,327 |
| KB | all | 40,991 | 8,555 | 79.1% | 6,520 | 4,834 | 4,150 | 8,984 |
| SM (U7) | 2023 | 651 | 390 | 40.1% | 202 | 198 | 76 | 274 |
| SM | 2024 | 880 | 615 | 30.1% | 339 | 332 | 100 | 432 |
| SM | 2025 | 791 | 637 | 19.5% | 366 | 359 | 65 | 424 |
| SM | 2026 | 736 | 700 | 4.9% | 459 | 457 | 26 | 483 |
| SM | all | 3,058 | 2,342 | 23.4% | 1,370 | 1,346 | 267 | 1,613 |
| PE (P7, earlier block) | all | 59,417 | 8,282 | 86.1% | 4,280 | 2,909 | 4,796 | 7,705 |
ST per year: 7,041/877 (2023), 9,316/1,731, 9,238/2,493, 7,933/3,159 (dropped 87.5%, 81.4%, 73.0%, 60.2%). Exit-aware lower bound on trade count vs the engine's current count: HM 1.9x, KB 1.4x, SM 1.2x, PE 1.8x. The dropped share falls every year because the signal rate stays flat while the number of rows rises (later years have shorter nominal blockers relative to the event rate?): not analysed further. The A new rows are nominal trades without cuts: no dollar value is given (the PE experience shows the nominal value is not the engine value).
Why SM differs: few raw events, long gaps; HM and KB are event-dense. The engine trades fewer rows than T (KB 6,520 of 8,555) because of the engine's own blocks and zero-lot rows, so A old < E is possible (a new row can occupy the slot an old row used).

### Part 3 - blind week vs live (sealed prediction reproduction vs StratTrades_DS7_<acct>.csv; match = same book and side, signal second +-150 s, greedy nearest)
| D7 book | live n | engine n | matched | live-only n / net | engine-only n / net |
|---|---|---|---|---|---|
| K7 | 64 | 61 | 48 | 16 / +7,340 | 13 / +5,859 |
| H7 | 3 | 19 | 0 | 3 / -770 | 19 / +9,266 |
| U7 | 6 | 7 | 5 | 1 / +2,400 | 2 / +7,346 |
| M7 | 28 | 29 | 20 | 8 / +5,690 | 9 / +1,782 |
| A7 | 23 | 18 | 15 | 8 / -1,620 | 3 / +1,136 |
| P7 | 53 | 43 | 32 | 21 / +53,565 | 11 / +3,625 |
| O7 + X3-X5 | 12 | 6 | 3 | 10 / +3,400 | 4 / +873 |
| all | 187 | 182 | 122 | 65 / +70,005 | 60 / +29,887 (live minus engine contribution -29,887) |
(The quoted -29.0k / +66.6k came from another tolerance; at +-150 s the totals are +70,005 and -29,887.)
Class of each live-only trade (raw-event store available for K7, H7, U7 only):
- K7 (16, +7,340): 10 trades (+865) have a valid raw KB event and NO sealed row = thinned by the busy gate; 5 trades (+7,100) have a sealed row the engine did not trade (engine block/skip/lots 0, not thinning); 1 (-625) no raw event.
- H7 (3, -770) and U7 (1, +2,400): no raw event at all (not the thinning; H7 is the open HM-silence item, 19 engine-only H7 trades +9,266 are the mirror of it).
- M7 (8, +5,690), A7 (8, -1,620), P7 (21, +53,565, 16 of them thinned per BASE-4): no raw-event store for MV and PB7, not classified here.
Engine-only trades (60, +29.9k): the mirror mechanism needs the live book to be in a position at the engine's signal second (live later exit -> live cannot enter). It applies to 9 of the 60 trades (-2,762 $ net): K7 3, M7 2, P7 4; at +300 s after a live exit 11 trades (-6,546). The large engine-only blocks are H7 19 (+9.3k; HM silence in live) and K7 13 (+5.9k, no live position open on 10 of them).
Verdict: the thinning mechanism explains the P7 live-only block (16 of 21 trades, +35.9k) and 10 K7 trades (+0.9k); it does NOT explain the engine-only side (9 of 60 trades) and does not explain the H7/U7 live-only trades. For KB, ST, HM, SM in the blind week the busy gate is a minor part of the live-only/engine-only split (K7 net +0.9k thinned); what drives the rest is HM silence, engine skips (5 K7, +7.1k), TH-L2 false cuts, and sizing.

### Part 4 - cost of a full exit-aware rebuild (not done)
New trade ids needed (R minus T over the history): KB 32.4k, HM 13.5k, SM 0.7k, PE 41.8k before the cap (post-cap 9.3k already built), total 88.4k for the four engine books (+ ST 25.3k if it were an engine book), against 66.7k trade ids in the sealed c3 index (44.4k old + 22.3k new). Measured on the PE post-cap build (12,252 ids, 5 workers, 10 months): thp_build loss rows 32 s, l2feat dp10s 46-54 s, l2s_rows 32 s, c3 path 14-19 s, universe/POI/masks ~10 s: 164 s wall in all. Per id about 20 KB of ldp10s, 20 KB of l2feat ldp10s, 21 KB of c3 path (mean 5,340 s x 4 B), and about 215 loss rows (+26.3M rows for 12.3k ids) in l2set: roughly 85 KB per id, so the 88k ids need about 7.5 GB (l2set rows.parquet grows from 0.8 GB to about 3 GB; /mnt/l2 has 2.0 TB free; root fs has 18 GB free and is not used). Compute for the whole history: 43 months instead of 10 gives about 30-60 min wall with 5-6 workers (thp_build, l2feat, l2s_rows, c3), plus the engine runs (about 1 minute per period config on the history). The real cost is not hours of compute; it is (i) the tid renumbering (thp_index assigns ids by time order within each book, so ids shift; the engine's old-prefix assumption (NOLD=44,385 old ids) must be replaced by a full rebuild of the c3 / l2set stores for the four books and every tid-keyed store: streams.pkl, lgb_pred, tidx_cut), (ii) re-fitting anything fitted on the thinned rows (ER bins, lots, locks), and (iii) the tie-out against all earlier headline numbers. Estimate: 1 working day with tie-outs; the compute itself under 2 hours.

### What this means for headline stack numbers
Both defects change the row set the engine trades from: PE (14% kept) and KB (21% kept), HM (32% kept) are thin samples of what live trades; SM is not (77% kept). The exit-aware trade count would be about 1.4-1.9x for PE/KB/HM. Direction of $ unknown without the history rebuild (blind week PE: +$34.7k from 20 more trades with cuts; K7: only +$0.9k of live-only trades are thinned). Not quantified for A6 and M6 (their generators carry the same gate; BASE-4 asked for a PB7 cuts variant, separate job).
