# DS3_L2SET_LOSS - selective loss-health rule: best settings per book (agent L2SL, 2026-10-30T00:35Z)

Research only; UNTOUCHED never read; no live change. Prereg l2vast/ds3/prereg/L2SET_LOSS_prereg.md (sha256 47f289f8...6821e, logged in DECISIONS.md before any outcome statistic; exactly 7840 cells). Own windows capped at label day 20260206 (NOT s48score.WINMASK / vs_lib.WINS HOLD, which have no upper bound): **2026 = 2026-01-01..02-06, about 5 real weeks (MDE large, nearly uninformative)**; L6M = 2025-08-01..2026-02-06; HOLD = 2025-07-01..2026-02-06; PRE = 2024-02..2025-06; X' = 2023-04..2024-01. MEASURED fills: cut = 1-s path close minus 0.995 pt; tightened stop = stop-market walk (0.85/1.13/1.74/1.71 by year); baseline = hold to the book's own stop/target (stop-out cost inside the base). Numbers are pts/trade vs that baseline, non-firing trades count 0; format `mean [n fired] (MDE)`, MDE = 2.8 SE with day x ENTRY-session clusters.

**Selection disclosure (applies to every published line):** kind RANK = best cell of that group by L6M (n fired >= 30, HOLD tie-break) - the ranking is on already-looked data (L2L and L2H had read the fixed-cut and lead-only loss rules on these same trades) and the recent windows are IN-SAMPLE for it; kind PRE = the cell chosen on PRE only (selection file written and logged before the holdout look), so its HOLD / L6M / 2026 / X' numbers are the single out-of-sample look. D4-D6 (stack engine) exist only for the stack books ST HM WT KB SM PE (engine slot 'PB' carries the PE trades) and for ALL (the pooled cell run on those six books); other books: not evaluated.

## 1. Settings table per book (and pooled), recent windows first

Tiers over the 22 published rows: PASS 0, CANDIDATE 0, CANDIDATE-RECENT 9, DEAD 13. Gates D1 PRE>=0, D2 HOLD>=0, D3 X'>=0, D4 stack maxDD not worse, D5 stack worst-20-weeks not worse, D6 stack weekly SD not worse (PRE+HOLD weeks), D7 placebo (shuffled within day) rank>=0.9 on HOLD, D8 White RC p<=0.05 over all 7840 cells (RANK: on L6M daily sums, PRE: on PRE daily sums), D9 beats same-rate random cuts rank>=0.9 on HOLD.

| group | kind | settings | 2026 | L6M | HOLD | PRE | X' | L6M $/wk (saved / forfeited) | fire % of arm-reach | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | RANK | arm upnl<=-15; z(pulled_sup5s vs 15-min ET bucket) >= 2; imb10<=-0.3; CUT | -0.22 [213] (1.2) | +0.34 [839] (0.6) | +0.30 [857] (0.5) | +0.14 [1418] (0.3) | -0.29 [617] (0.7) | +21,991 (+105,869 / -83,878) | 9 | DEAD | D3_Xp,D4_maxDD,D5_W20,D6_SD |
| ALL | PRE | arm upnl<=-15; pulled_sup10s >= 100x median own-side level; own-side depth<=0.5x norm (wall behind gone); CUT | -0.04 [603] (2.5) | -0.30 [2487] (1.2) | -0.32 [2586] (1.1) | +0.36 [5051] (0.7) | -0.07 [1286] (0.9) | -19,899 (+316,091 / -335,990) | 27 | DEAD | D2_HOLD,D3_Xp,D4_maxDD,D7_placebo |
| ST | RANK | arm upnl<=-30; pulled_sup10s >= 100x median own-side level; new adverse extreme in last 10s; sweep against (10s>=1); tighten stop to MAE+10 | +0.77 [110] (3.4) | +1.47 [517] (1.6) | +1.45 [573] (1.6) | -0.21 [1295] (1.2) | +0.15 [353] (1.9) | +13,199 (+45,896 / -32,697) | 82 NOT SELECTIVE | CANDIDATE-RECENT | D1_PRE |
| ST | PRE | arm upnl<=-15; pulled_sup10s >= 100x median own-side level; own-side depth<=0.5x norm (wall behind gone); CUT | +0.49 [85] (5.0) | +0.01 [371] (2.2) | +0.07 [385] (2.0) | +0.90 [701] (1.3) | -0.26 [158] (1.9) | +108 (+60,751 / -60,643) | 27 | CANDIDATE-RECENT | D3_Xp,D7_placebo |
| HM | RANK | arm upnl<=-15; pulled_sup30s >= 20x median own-side level; new adverse extreme in last 30s; imb10<=-0.3; tighten stop to MAE+5 | +0.12 [28] (3.2) | +1.02 [136] (1.4) | +0.98 [144] (1.3) | +0.03 [401] (1.1) | -0.04 [121] (1.5) | +6,602 (+17,031 / -10,429) | 25 | CANDIDATE-RECENT | D3_Xp,D4_maxDD |
| HM | PRE | arm upnl<=-30; pulled_sup30s >= 100x median own-side level; sweep against (10s>=1); tighten stop to MAE+10 | -2.91 [104] (5.8) | -1.27 [459] (2.6) | -1.16 [513] (2.5) | +1.46 [1117] (1.5) | +0.41 [412] (2.5) | -8,251 (+41,283 / -49,533) | 97 NOT SELECTIVE | DEAD | D2_HOLD,D4_maxDD,D7_placebo,D9_random |
| WT | RANK | arm upnl<=-15; z(pulled_sup30s vs 15-min ET bucket) >= 2; new adverse extreme in last 30s; iceberg against at best; tighten stop to MAE+10 | -0.05 [88] (2.0) | +0.45 [337] (0.8) | +0.49 [354] (0.7) | -0.05 [766] (0.5) | -0.16 [265] (0.9) | +3,864 (+16,883 / -13,019) | 48 | DEAD | D1_PRE,D3_Xp |
| WT | PRE | arm upnl<=-20; pulled_sup30s >= 500x median own-side level; new adverse extreme in last 30s; tighten stop to MAE+5 | -0.84 [99] (2.4) | +0.14 [422] (1.0) | +0.12 [455] (0.9) | +0.32 [997] (0.6) | +0.42 [265] (0.8) | +1,191 (+22,541 / -21,350) | 60 NOT SELECTIVE | DEAD | D4_maxDD,D5_W20,D7_placebo |
| KB | RANK | arm upnl<=-30; pulled_sup5s >= 100x median own-side level; iceberg against at best; tighten stop to MAE+5 | +0.18 [104] (3.8) | +1.22 [473] (1.7) | +1.08 [513] (1.7) | -0.27 [1173] (1.3) | +0.89 [294] (1.7) | +5,681 (+25,306 / -19,625) | 65 NOT SELECTIVE | CANDIDATE-RECENT | D1_PRE,D4_maxDD,D5_W20,D6_SD |
| KB | PRE | arm upnl<=-45; pulled_sup10s >= 20x median own-side level; new adverse extreme in last 10s; sweep against (10s>=1); tighten stop to MAE+5 | -0.14 [110] (2.7) | -0.10 [489] (1.3) | -0.18 [543] (1.3) | +0.58 [1188] (0.7) | +0.40 [456] (1.5) | -480 (+10,915 / -11,396) | 100 NOT SELECTIVE | DEAD | D2_HOLD,D4_maxDD,D5_W20,D6_SD,D7_placebo,D9_random |
| SM | RANK | arm upnl<=-15; pulled_sup5s >= 20x median own-side level; imb10<=-0.3; CUT | +4.49 [24] (9.3) | +2.88 [106] (4.2) | +2.59 [119] (3.9) | -2.28 [335] (3.1) | -0.15 [145] (3.7) | +4,776 (+13,835 / -9,060) | 45 | CANDIDATE-RECENT | D1_PRE,D3_Xp,D5_W20 |
| SM | PRE | arm upnl<=-20; pulled_sup30s >= 500x median own-side level; new adverse extreme in last 30s; iceberg against at best; tighten stop to MAE+10 | +0.58 [22] (8.2) | -0.07 [104] (3.9) | -0.43 [117] (3.7) | +1.10 [264] (2.1) | +1.82 [108] (2.1) | -122 (+8,964 / -9,086) | 59 NOT SELECTIVE | DEAD | D2_HOLD,D4_maxDD,D5_W20,D7_placebo,D9_random |
| PE | RANK | arm upnl<=-15; pulled_sup5s >= 100x median own-side level; new adverse extreme in last 5s; iceberg against at best; CUT | +0.74 [147] (6.1) | +0.93 [597] (2.7) | +0.85 [646] (2.6) | -0.15 [1482] (1.8) | -0.78 [358] (2.5) | +4,421 (+55,486 / -51,065) | 58 NOT SELECTIVE | CANDIDATE-RECENT | D1_PRE,D3_Xp,D5_W20 |
| PE | PRE | arm upnl<=-30; z(pulled_sup30s vs 15-min ET bucket) >= 1; new adverse extreme in last 30s; sweep against (10s>=1); tighten stop to MAE+10 | -0.23 [150] (4.7) | -0.24 [556] (2.2) | -0.04 [597] (2.0) | +0.93 [1269] (1.2) | +0.02 [359] (2.0) | -1,152 (+27,944 / -29,096) | 81 NOT SELECTIVE | DEAD | D2_HOLD,D7_placebo,D9_random |
| PB | RANK | arm upnl<=-30; pulled_sup5s >= 20x median own-side level; own-side depth<=0.5x norm (wall behind gone); tighten stop to MAE+5 | +0.55 [24] (2.1) | +0.59 [105] (1.0) | +0.58 [108] (0.9) | +0.33 [284] (0.7) | -0.07 [64] (0.9) | +3,674 (+9,408 / -5,734) | 25 | CANDIDATE-RECENT | D3_Xp |
| PB | PRE | arm upnl<=-20; pulled_sup10s >= 100x median own-side level; sweep against (10s>=1); tighten stop to MAE+10 | -3.09 [107] (6.9) | -1.13 [436] (3.1) | -0.66 [493] (2.9) | +1.79 [1171] (1.8) | -1.04 [363] (2.9) | -7,003 (+53,433 / -60,435) | 87 NOT SELECTIVE | DEAD | D2_HOLD,D3_Xp,D7_placebo,D9_random |
| DN | RANK | arm upnl<=-30; z(pulled_sup30s vs 15-min ET bucket) >= 2; new adverse extreme in last 30s; sweep against (10s>=1); tighten stop to MAE+5 | -0.51 [34] (4.4) | +1.02 [157] (1.8) | +1.02 [170] (1.7) | -0.91 [420] (1.4) | +0.45 [168] (2.0) | +5,093 (+17,707 / -12,614) | 47 | DEAD | D1_PRE |
| DN | PRE | arm upnl<=-30; pulled_sup10s >= 500x median own-side level; new adverse extreme in last 10s; CUT | -2.79 [32] (6.1) | -1.16 [132] (2.3) | -0.96 [146] (2.1) | +0.74 [241] (0.9) | +0.37 [43] (1.0) | -5,821 (+14,707 / -20,528) | 20 | DEAD | D2_HOLD,D7_placebo,D9_random |
| MV | RANK | arm upnl<=-40; pulled_sup5s share of own-side 10-level depth >= 0.3; new adverse extreme in last 5s; >=2 of {iceberg,sweep,wall gone,imb10}; tighten stop to MAE+10 | +1.24 [90] (1.3) | +0.65 [388] (1.0) | +0.58 [434] (1.0) | -0.03 [939] (0.7) | +0.95 [423] (1.2) | +5,257 (+15,488 / -10,231) | 93 NOT SELECTIVE | CANDIDATE-RECENT | D1_PRE |
| MV | PRE | arm upnl<=-15; pulled_sup10s >= 100x median own-side level; own-side depth<=0.5x norm (wall behind gone); CUT | -0.73 [81] (4.1) | -0.19 [314] (2.2) | -0.44 [328] (2.0) | +0.68 [685] (1.3) | +0.68 [159] (1.7) | -1,513 (+50,277 / -51,790) | 27 | DEAD | D2_HOLD,D7_placebo |
| MA | RANK | arm upnl<=-20; z(pulled_sup30s vs 15-min ET bucket) >= 2; new adverse extreme in last 30s; CUT | +7.57 [33] (8.6) | +3.75 [145] (3.8) | +3.63 [166] (3.5) | -1.20 [398] (2.7) | +1.41 [175] (3.4) | +10,914 (+25,920 / -15,005) | 50 NOT SELECTIVE | CANDIDATE-RECENT | D1_PRE |
| MA | PRE | arm upnl<=-15; pulled_sup30s >= 500x median own-side level; iceberg AND sweep against; tighten stop to MAE+5 | +0.84 [31] (8.4) | -1.43 [153] (4.2) | -1.60 [174] (3.8) | +1.48 [390] (2.4) | +0.52 [167] (3.2) | -4,159 (+20,765 / -24,925) | 63 NOT SELECTIVE | DEAD | D2_HOLD,D7_placebo,D9_random |

Reading: no row is PASS. A CANDIDATE-RECENT label means only 2026>0 and L6M>0 in-sample for RANK rows; PRE rows are the out-of-sample choice.

## 2. Fire rate of each condition (share of arm-reaching trades that it fires on; computed before any outcome was read; no cell discarded for low fire rate)

Over all 1960 conditions: 1071 fire on >50% of arm-reaching HOLD trades (flagged NOT SELECTIVE); 889 are below. Fire = at least one decision row of the trade satisfies the whole condition (a trade under water for a long time collects many chances, which is why lead-only conditions such as 'iceberg against' fire on ~97% of trades: at the trade level they are not selective even though per row they are rarer). Table: HOLD fire % at arm 15 / 30 / 45 (conditions with no lead, newext no / yes), then lead-only and lead combos by arm 30.

| pulled condition | window | thr | newext=no (A15 / A30 / A45) | newext=yes (A15 / A30 / A45) |
|---|---|---|---|---|
| mult | 5s | 20 | 99* / 99* / 99* | 96* / 97* / 95* |
| mult | 5s | 100 | 74* / 70* / 64* | 62* / 61* / 56* |
| mult | 5s | 500 | 12 / 9 / 5 | 8 / 7 / 4 |
| z | 5s | 1 | 94* / 92* / 87* | 90* / 88* / 82* |
| z | 5s | 2 | 62* / 58* / 48 | 53* / 50 / 41 |
| z | 5s | 3 | 17 / 12 / 8 | 10 / 9 / 6 |
| share | 5s | 0.2 | 100* / 100* / 100* | 99* / 98* / 97* |
| share | 5s | 0.3 | 100* / 100* / 100* | 99* / 98* / 97* |
| share | 5s | 0.5 | 100* / 100* / 100* | 98* / 98* / 96* |
| mult | 10s | 20 | 100* / 100* / 100* | 99* / 99* / 99* |
| mult | 10s | 100 | 91* / 90* / 87* | 85* / 85* / 83* |
| mult | 10s | 500 | 36 / 31 / 23 | 27 / 26 / 20 |
| z | 10s | 1 | 93* / 91* / 87* | 91* / 89* / 85* |
| z | 10s | 2 | 64* / 59* / 51* | 57* / 54* / 47 |
| z | 10s | 3 | 22 / 17 / 10 | 14 / 12 / 9 |
| share | 10s | 0.2 | 100* / 100* / 100* | 99* / 100* / 99* |
| share | 10s | 0.3 | 100* / 100* / 100* | 99* / 100* / 99* |
| share | 10s | 0.5 | 100* / 100* / 100* | 99* / 100* / 99* |
| mult | 30s | 20 | 100* / 100* / 100* | 100* / 100* / 100* |
| mult | 30s | 100 | 98* / 99* / 98* | 98* / 98* / 97* |
| mult | 30s | 500 | 71* / 68* / 63* | 65* / 63* / 60* |
| z | 30s | 1 | 90* / 88* / 82* | 87* / 86* / 81* |
| z | 30s | 2 | 58* / 53* / 45 | 51* / 49 / 43 |
| z | 30s | 3 | 22 / 17 / 13 | 16 / 14 / 12 |
| share | 30s | 0.2 | 100* / 100* / 100* | 100* / 100* / 100* |
| share | 30s | 0.3 | 100* / 100* / 100* | 100* / 100* / 100* |
| share | 30s | 0.5 | 100* / 100* / 100* | 100* / 100* / 100* |

(* = >50% = not selective.)

| lead / combo (arm 30, no pulled condition) | newext=no | newext=yes |
|---|---|---|
| none | 100* | 100* |
| ICE | 99* | 97* |
| SWP | 100* | 99* |
| WG | 30 | 16 |
| IMB | 38 | 11 |
| ICESWP | 98* | 96* |
| K2 | 98* | 97* |

Pulled condition AND a lead (arm 30, newext=no, HOLD fire %) for the most selective pulled thresholds:

| pulled | ICE | SWP | WG | IMB | ICESWP | K2 |
|---|---|---|---|---|---|---|
| mult100@10s | 88 | 90 | 25 | 20 | 87 | 88 |
| mult500@30s | 65 | 66 | 22 | 13 | 64 | 66 |
| z2@5s | 54 | 57 | 11 | 7 | 54 | 54 |
| z2@10s | 57 | 59 | 12 | 9 | 57 | 57 |
| z3@30s | 16 | 17 | 4 | 2 | 16 | 16 |
| z3@10s | 16 | 17 | 3 | 1 | 16 | 16 |

## 3. Families and best-of-N (pooled, all 10 books)

| family | cells | best L6M cell | L6M | 2026 | HOLD | PRE | X' | cells >0 in L6M / in all of L6M,HOLD,PRE,X' |
|---|---|---|---|---|---|---|---|---|
| F0 fixed cut | 40 | A40|none|ne1|none|t10 | -0.02 (0.6) | +0.02 (1.2) | -0.03 (0.6) | +0.01 (0.4) | +0.27 (0.6) | 0 / 0 |
| F1 leads only | 240 | A15|none|ne1|IMB|t10 | +0.15 (0.4) | +0.26 (0.8) | +0.18 (0.4) | -0.08 (0.3) | -0.07 (0.6) | 17 / 3 |
| F2 pulled x median level | 2520 | A15|mult20@30s|ne1|IMB|t10 | +0.14 (0.6) | +0.56 (1.1) | +0.17 (0.5) | -0.09 (0.4) | +0.00 (0.7) | 394 / 182 |
| F3 pulled z-score | 2520 | A15|z2@5s|ne0|IMB|cut | +0.34 (0.6) | -0.22 (1.2) | +0.30 (0.5) | +0.14 (0.3) | -0.29 (0.7) | 489 / 152 |
| F4 pulled share of depth | 2520 | A15|share0.2@30s|ne1|IMB|t10 | +0.15 (0.6) | +0.56 (1.1) | +0.18 (0.5) | -0.09 (0.4) | +0.01 (0.7) | 158 / 18 |

White reality check over all 7840 cells (studentised, 5-day blocks, 2000 reps), pooled: PRE daily sums p = 0.0015; L6M daily sums p = 0.0180. Per book (PRE / L6M): ST 0.003/0.003; HM 0.001/0.001; WT 0.032/0.004; KB 0.001/0.010; SM 0.001/0.000; PE 0.000/0.003; PB 0.000/0.001; DN 0.000/0.015; MV 0.012/0.015; MA 0.009/0.001. Small p here says the best cell of the grid is better than the best of a zero-mean bootstrap, i.e. SOME cells are not noise in the window being searched; it does not say the cell holds out of sample (see section 4, 5).

## 4. Walk-forward 3-month re-fit (fit only on trades closed before the refit; refits 2024-01-01 ... 2026-01-01)

Choice rule: highest mean delta over the fit trades among cells with >= 30 fired fit trades and mean > 0, else hold. Chains: per-book own cell vs one pooled cell, expanding vs trailing-12-month fit window. Out-of-sample deltas (pts/trade, all trades, MDE):

| chain | 2026 | L6M | HOLD | PRE (from 2024-02) | X' |
|---|---|---|---|---|---|
| exp / book | -0.86 (2.1) | -0.60 (1.0) | -0.58 (0.9) | -0.25 (0.7) | n/a (before first refit) |
| exp / pooled | -1.40 (2.6) | -0.44 (1.3) | -0.36 (1.2) | -0.07 (0.6) | n/a (before first refit) |
| t12 / book | -0.63 (2.0) | -0.54 (0.9) | -0.48 (0.8) | +0.01 (0.6) | n/a (before first refit) |
| t12 / pooled | -1.47 (2.5) | -0.93 (0.9) | -0.90 (0.9) | -0.15 (0.7) | n/a (before first refit) |

Last re-fit in full (refit 2026-01-01, tested 2026-01-01..02-06 only); fit window and chosen cell, top-5 fit means (pts per fit trade):

**exp / book**

* ST: arm upnl<=-20; pulled_sup10s >= 100x median own-side level; own-side depth<=0.5x norm (wall behind gone); CUT [A20|mult100@10s|ne0|WG|cut]; fit n=5102 fit mean +0.51 fired 1013; top5 A20|mult100@10s|ne0|WG|cut +0.51; A15|mult20@10s|ne0|WG|t5 +0.50; A15|share0.5@5s|ne0|WG|t5 +0.50; A30|mult100@10s|ne1|none|t5 +0.49; A15|share0.5@10s|ne0|WG|t5 +0.48; 2026 test -0.18 pts/trade (n 288).
* HM: arm upnl<=-30; pulled_sup5s share of own-side 10-level depth >= 0.5; sweep against (10s>=1); tighten stop to MAE+10 [A30|share0.5@5s|ne0|SWP|t10]; fit n=3953 fit mean +0.82 fired 2020; top5 A30|share0.5@5s|ne0|SWP|t10 +0.82; A30|share0.3@30s|ne1|K2|t10 +0.82; A30|share0.5@30s|ne1|K2|t10 +0.82; A30|share0.2@30s|ne1|K2|t10 +0.82; A30|mult20@30s|ne1|K2|t10 +0.82; 2026 test -2.64 pts/trade (n 203).
* WT: arm upnl<=-20; pulled_sup30s >= 500x median own-side level; new adverse extreme in last 30s; tighten stop to MAE+5 [A20|mult500@30s|ne1|none|t5]; fit n=7281 fit mean +0.35 fired 1618; top5 A20|mult500@30s|ne1|none|t5 +0.35; A15|mult100@5s|ne0|none|t10 +0.34; A15|mult500@30s|ne1|none|t10 +0.33; A20|mult500@30s|ne1|ICE|t5 +0.32; A15|mult100@5s|ne0|SWP|t10 +0.32; 2026 test -0.84 pts/trade (n 404).
* KB: arm upnl<=-30; pulled_sup10s >= 100x median own-side level; new adverse extreme in last 10s; >=2 of {iceberg,sweep,wall gone,imb10}; tighten stop to MAE+10 [A30|mult100@10s|ne1|K2|t10]; fit n=5212 fit mean +0.52 fired 2120; top5 A30|mult100@10s|ne1|K2|t10 +0.52; A30|mult100@10s|ne1|ICE|t10 +0.52; A45|mult100@30s|ne0|ICE|t5 +0.52; A30|mult100@10s|ne1|ICESWP|t10 +0.51; A45|mult100@30s|ne1|ICE|t5 +0.50; 2026 test -0.72 pts/trade (n 288).
* SM: arm upnl<=-20; pulled_sup30s >= 500x median own-side level; iceberg AND sweep against; tighten stop to MAE+10 [A20|mult500@30s|ne0|ICESWP|t10]; fit n=1643 fit mean +1.02 fired 494; top5 A20|mult500@30s|ne0|ICESWP|t10 +1.02; A20|mult500@30s|ne0|ICE|t10 +1.01; A20|mult500@30s|ne1|ICE|t10 +0.97; A15|z2@5s|ne1|ICE|t10 +0.96; A20|mult500@30s|ne0|ICE|t5 +0.94; 2026 test +1.23 pts/trade (n 65).
* PE: arm upnl<=-30; z(pulled_sup30s vs 15-min ET bucket) >= 2; new adverse extreme in last 30s; tighten stop to MAE+10 [A30|z2@30s|ne1|none|t10]; fit n=5080 fit mean +0.58 fired 1116; top5 A30|z2@30s|ne1|none|t10 +0.58; A30|z1@30s|ne1|SWP|t10 +0.57; A30|z2@30s|ne1|SWP|t10 +0.56; A30|z1@30s|ne1|none|t10 +0.56; A30|z2@30s|ne0|none|t10 +0.55; 2026 test -0.25 pts/trade (n 281).
* PB: arm upnl<=-30; pulled_sup10s >= 100x median own-side level; new adverse extreme in last 10s; tighten stop to MAE+5 [A30|mult100@10s|ne1|none|t5]; fit n=3854 fit mean +0.86 fired 1714; top5 A30|mult100@10s|ne1|none|t5 +0.86; A20|mult100@10s|ne0|ICESWP|t10 +0.86; A30|mult100@10s|ne1|SWP|t5 +0.84; A20|mult100@10s|ne0|K2|t10 +0.83; A20|mult100@10s|ne0|SWP|t10 +0.82; 2026 test -0.15 pts/trade (n 195).
* DN: arm upnl<=-15; pulled_sup30s >= 500x median own-side level; iceberg AND sweep against; tighten stop to MAE+5 [A15|mult500@30s|ne0|ICESWP|t5]; fit n=3126 fit mean +0.60 fired 1260; top5 A15|mult500@30s|ne0|ICESWP|t5 +0.60; A15|mult500@30s|ne0|ICE|t5 +0.55; A20|mult100@10s|ne1|ICESWP|t10 +0.53; A15|mult500@30s|ne0|K2|t5 +0.53; A20|mult100@10s|ne1|ICE|t10 +0.52; 2026 test -6.80 pts/trade (n 146).
* MV: arm upnl<=-15; pulled_sup10s >= 100x median own-side level; own-side depth<=0.5x norm (wall behind gone); CUT [A15|mult100@10s|ne0|WG|cut]; fit n=4905 fit mean +0.47 fired 1091; top5 A15|mult100@10s|ne0|WG|cut +0.47; A15|mult100@5s|ne0|WG|cut +0.40; A15|mult500@30s|ne0|WG|cut +0.39; A15|share0.5@5s|ne0|WG|cut +0.38; A40|share0.5@5s|ne1|ICESWP|t5 +0.37; 2026 test -0.73 pts/trade (n 272).
* MA: arm upnl<=-15; z(pulled_sup30s vs 15-min ET bucket) >= 2; iceberg against at best; tighten stop to MAE+5 [A15|z2@30s|ne0|ICE|t5]; fit n=2000 fit mean +0.58 fired 689; top5 A15|z2@30s|ne0|ICE|t5 +0.58; A15|mult500@30s|ne0|none|t5 +0.55; A15|mult500@30s|ne0|ICESWP|t5 +0.53; A20|z2@30s|ne1|none|t10 +0.53; A15|mult500@30s|ne0|K2|t5 +0.52; 2026 test +4.92 pts/trade (n 87).

**t12 / book**

* ST: arm upnl<=-30; pulled_sup10s >= 100x median own-side level; iceberg against at best; tighten stop to MAE+5 [A30|mult100@10s|ne0|ICE|t5]; fit n=2493 fit mean +0.70 fired 1245; top5 A30|mult100@10s|ne0|ICE|t5 +0.70; A30|mult100@10s|ne0|none|t5 +0.70; A30|mult100@10s|ne0|SWP|t5 +0.67; A30|mult100@10s|ne0|ICESWP|t5 +0.65; A30|mult100@10s|ne1|none|t5 +0.64; 2026 test -1.18 pts/trade (n 288).
* HM: arm upnl<=-15; pulled_sup30s >= 500x median own-side level; tighten stop to MAE+10 [A15|mult500@30s|ne0|none|t10]; fit n=1818 fit mean +0.80 fired 757; top5 A15|mult500@30s|ne0|none|t10 +0.80; A20|mult500@30s|ne0|none|t10 +0.75; A15|mult100@10s|ne1|K2|t10 +0.72; A30|mult100@10s|ne0|ICESWP|t10 +0.72; A15|mult100@10s|ne1|ICESWP|t10 +0.72; 2026 test -1.36 pts/trade (n 203).
* WT: arm upnl<=-15; pulled_sup10s >= 100x median own-side level; new adverse extreme in last 10s; sweep against (10s>=1); tighten stop to MAE+10 [A15|mult100@10s|ne1|SWP|t10]; fit n=3404 fit mean +0.73 fired 1281; top5 A15|mult100@10s|ne1|SWP|t10 +0.73; A15|mult100@10s|ne1|none|t10 +0.72; A15|mult500@30s|ne1|none|t10 +0.72; A15|mult100@5s|ne0|none|t10 +0.71; A15|mult500@30s|ne0|none|t10 +0.69; 2026 test -1.68 pts/trade (n 404).
* KB: arm upnl<=-30; pulled_sup5s >= 100x median own-side level; new adverse extreme in last 5s; sweep against (10s>=1); tighten stop to MAE+5 [A30|mult100@5s|ne1|SWP|t5]; fit n=2521 fit mean +0.69 fired 940; top5 A30|mult100@5s|ne1|SWP|t5 +0.69; A15|mult500@5s|ne0|K2|t10 +0.65; A30|mult100@5s|ne1|K2|t5 +0.65; A30|mult100@5s|ne1|ICESWP|t5 +0.65; A30|mult100@5s|ne1|none|t5 +0.65; 2026 test -0.09 pts/trade (n 288).
* SM: arm upnl<=-20; pulled_sup5s >= 100x median own-side level; new adverse extreme in last 5s; >=2 of {iceberg,sweep,wall gone,imb10}; tighten stop to MAE+10 [A20|mult100@5s|ne1|K2|t10]; fit n=637 fit mean +1.81 fired 205; top5 A20|mult100@5s|ne1|K2|t10 +1.81; A20|mult100@5s|ne1|ICE|t10 +1.77; A20|mult100@5s|ne1|ICESWP|t10 +1.71; A20|mult500@30s|ne0|ICESWP|t5 +1.60; A20|mult500@30s|ne0|ICESWP|t10 +1.60; 2026 test +1.77 pts/trade (n 65).
* PE: arm upnl<=-15; pulled_sup5s >= 100x median own-side level; new adverse extreme in last 5s; iceberg AND sweep against; CUT [A15|mult100@5s|ne1|ICESWP|cut]; fit n=2476 fit mean +0.89 fired 1287; top5 A15|mult100@5s|ne1|ICESWP|cut +0.89; A15|mult100@5s|ne1|ICE|cut +0.86; A15|mult100@5s|ne1|SWP|cut +0.78; A15|mult100@5s|ne1|K2|cut +0.73; A15|mult100@5s|ne1|none|cut +0.72; 2026 test +0.74 pts/trade (n 281).
* PB: arm upnl<=-15; z(pulled_sup5s vs 15-min ET bucket) >= 2; imb10<=-0.3; CUT [A15|z2@5s|ne0|IMB|cut]; fit n=1773 fit mean +0.62 fired 143; top5 A15|z2@5s|ne0|IMB|cut +0.62; A45|z1@30s|ne0|SWP|t5 +0.53; A40|z2@5s|ne0|SWP|t5 +0.52; A40|z2@5s|ne0|none|t5 +0.50; A40|z2@5s|ne0|K2|t5 +0.49; 2026 test -0.01 pts/trade (n 195).
* DN: arm upnl<=-40; pulled_sup10s >= 100x median own-side level; new adverse extreme in last 10s; tighten stop to MAE+10 [A40|mult100@10s|ne1|none|t10]; fit n=1387 fit mean +0.46 fired 396; top5 A40|mult100@10s|ne1|none|t10 +0.46; A40|mult100@10s|ne1|SWP|t10 +0.44; A40|mult100@10s|ne0|SWP|t10 +0.41; A40|mult100@10s|ne1|ICE|t10 +0.37; A40|mult100@10s|ne0|none|t10 +0.36; 2026 test -2.51 pts/trade (n 146).
* MV: arm upnl<=-20; pulled_sup30s >= 500x median own-side level; imb10<=-0.3; CUT [A20|mult500@30s|ne0|IMB|cut]; fit n=2352 fit mean +0.44 fired 322; top5 A20|mult500@30s|ne0|IMB|cut +0.44; A15|mult500@10s|ne0|WG|t5 +0.39; A20|mult500@5s|ne0|none|t5 +0.32; A20|mult500@5s|ne0|ICE|t5 +0.31; A15|mult500@5s|ne0|none|t5 +0.31; 2026 test -0.89 pts/trade (n 272).
* MA: arm upnl<=-15; z(pulled_sup10s vs 15-min ET bucket) >= 2; new adverse extreme in last 10s; iceberg against at best; CUT [A15|z2@10s|ne1|ICE|cut]; fit n=826 fit mean +1.09 fired 354; top5 A15|z2@10s|ne1|ICE|cut +1.09; A15|z2@30s|ne1|ICE|cut +1.03; A15|z2@10s|ne1|ICESWP|cut +0.99; A15|z2@30s|ne0|ICE|t5 +0.78; A15|z2@30s|ne1|K2|cut +0.77; 2026 test +2.20 pts/trade (n 87).

**exp / pooled**

* ALL: arm upnl<=-15; pulled_sup5s >= 100x median own-side level; iceberg against at best; tighten stop to MAE+10 [A15|mult100@5s|ne0|ICE|t10]; fit n=42156 fit mean +0.30 fired 15673; top5 A15|mult100@5s|ne0|ICE|t10 +0.30; A15|mult100@5s|ne0|ICESWP|t10 +0.28; A15|mult100@5s|ne1|ICE|t10 +0.27; A15|mult100@5s|ne1|ICESWP|t10 +0.27; A15|mult500@30s|ne0|none|t10 +0.27; 2026 test -1.40 pts/trade (n 2229).

**t12 / pooled**

* ALL: arm upnl<=-15; pulled_sup5s >= 100x median own-side level; new adverse extreme in last 5s; iceberg against at best; tighten stop to MAE+10 [A15|mult100@5s|ne1|ICE|t10]; fit n=19687 fit mean +0.34 fired 7261; top5 A15|mult100@5s|ne1|ICE|t10 +0.34; A15|mult100@5s|ne1|ICESWP|t10 +0.33; A15|mult100@5s|ne0|ICE|t10 +0.27; A15|mult100@5s|ne0|ICESWP|t10 +0.26; A15|mult500@30s|ne0|none|t10 +0.25; 2026 test -1.47 pts/trade (n 2229).

## 5. Placebo (shuffled book within day) and same-rate random cuts, published cells

Placebo = the cell's L2 feature block (pulled, z, share, leads, median level) taken from another trade of the same label day (row-aligned); path conditions real; 20 draws. Random = same fire rate among eligible trades, random firing row, 20 draws. Rank = share of draws below the real cell. NOTE: both test the chosen cell, not the search; the search is covered by the RC in section 3.

| group | kind | cell | HOLD real | placebo mean (sd) rank | random mean (sd) rank | L6M real | placebo | random | PRE real | placebo | random |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | RANK | A15|z2@5s|ne0|IMB|cut | +0.30 | -0.01 (0.09) 1.00 | -0.79 (0.14) 1.00 | +0.34 | -0.02 | -0.82 | +0.14 | -0.00 | -0.72 |
| ALL | PRE | A15|mult100@10s|ne0|WG|cut | -0.32 | -0.21 (0.10) 0.10 | -2.35 (0.19) 1.00 | -0.30 | -0.24 | -2.45 | +0.36 | +0.05 | -2.22 |
| ST | RANK | A30|mult100@10s|ne1|SWP|t10 | +1.45 | +0.39 (0.26) 1.00 | -0.01 (0.25) 1.00 | +1.47 | +0.40 | -0.04 | -0.21 | +0.00 | -0.39 |
| ST | PRE | A15|mult100@10s|ne0|WG|cut | +0.07 | -0.26 (0.38) 0.70 | -2.31 (0.77) 1.00 | +0.01 | -0.31 | -2.45 | +0.90 | +0.17 | -2.49 |
| HM | RANK | A15|mult20@30s|ne1|IMB|t5 | +0.98 | -0.11 (0.30) 1.00 | -0.88 (0.47) 1.00 | +1.02 | -0.14 | -1.00 | +0.03 | +0.08 | -0.73 |
| HM | PRE | A30|mult100@30s|ne0|SWP|t10 | -1.16 | -0.40 (0.42) 0.00 | +0.52 (0.37) 0.00 | -1.27 | -0.50 | +0.49 | +1.46 | +0.29 | +0.92 |
| WT | RANK | A15|z2@30s|ne1|ICE|t10 | +0.49 | +0.03 (0.16) 1.00 | -0.16 (0.19) 1.00 | +0.45 | +0.02 | -0.21 | -0.05 | -0.00 | -0.20 |
| WT | PRE | A20|mult500@30s|ne1|none|t5 | +0.12 | +0.10 (0.16) 0.60 | -0.26 (0.21) 0.95 | +0.14 | +0.04 | -0.31 | +0.32 | +0.01 | -0.46 |
| KB | RANK | A30|mult100@5s|ne0|ICE|t5 | +1.08 | +0.21 (0.26) 1.00 | +0.43 (0.28) 1.00 | +1.22 | +0.23 | +0.45 | -0.27 | -0.15 | +0.23 |
| KB | PRE | A45|mult20@10s|ne1|SWP|t5 | -0.18 | +0.10 (0.16) 0.05 | -0.05 (0.24) 0.40 | -0.10 | +0.10 | -0.04 | +0.58 | +0.11 | +0.27 |
| SM | RANK | A15|mult20@5s|ne0|IMB|cut | +2.59 | +0.35 (0.96) 1.00 | -4.06 (1.25) 1.00 | +2.88 | +0.18 | -4.18 | -2.28 | -0.61 | -4.70 |
| SM | PRE | A20|mult500@30s|ne1|ICE|t10 | -0.43 | -0.07 (0.70) 0.30 | -0.62 (0.87) 0.55 | -0.07 | -0.04 | -0.45 | +1.10 | +0.08 | -0.88 |
| PE | RANK | A15|mult100@5s|ne1|ICE|cut | +0.85 | +0.27 (0.50) 0.90 | -6.19 (0.53) 1.00 | +0.93 | +0.26 | -6.29 | -0.15 | -0.14 | -5.90 |
| PE | PRE | A30|z1@30s|ne1|SWP|t10 | -0.04 | +0.09 (0.31) 0.30 | -0.01 (0.38) 0.35 | -0.24 | +0.05 | -0.13 | +0.93 | +0.11 | +0.19 |
| PB | RANK | A30|mult20@5s|ne0|WG|t5 | +0.58 | +0.00 (0.22) 1.00 | +0.01 (0.33) 0.95 | +0.59 | +0.01 | +0.06 | +0.33 | -0.03 | +0.37 |
| PB | PRE | A20|mult100@10s|ne0|SWP|t10 | -0.66 | -0.70 (0.58) 0.55 | -0.26 (0.52) 0.15 | -1.13 | -0.88 | -0.11 | +1.79 | +0.42 | +1.09 |
| DN | RANK | A30|z2@30s|ne1|SWP|t5 | +1.02 | +0.02 (0.32) 1.00 | -0.57 (0.46) 1.00 | +1.02 | +0.01 | -0.69 | -0.91 | -0.08 | -0.64 |
| DN | PRE | A30|mult500@10s|ne1|none|cut | -0.96 | -0.11 (0.28) 0.00 | -1.30 (0.65) 0.60 | -1.16 | -0.11 | -1.38 | +0.74 | +0.05 | -1.31 |
| MV | RANK | A40|share0.3@5s|ne1|K2|t10 | +0.58 | +0.10 (0.12) 1.00 | +0.09 (0.19) 0.95 | +0.65 | +0.11 | +0.06 | -0.03 | -0.00 | -0.03 |
| MV | PRE | A15|mult100@10s|ne0|WG|cut | -0.44 | -0.26 (0.31) 0.30 | -2.65 (0.48) 1.00 | -0.19 | -0.30 | -2.82 | +0.68 | +0.13 | -2.75 |
| MA | RANK | A20|z2@30s|ne1|none|cut | +3.63 | -0.10 (0.71) 1.00 | -4.66 (0.85) 1.00 | +3.75 | -0.07 | -4.48 | -1.20 | -0.05 | -4.91 |
| MA | PRE | A15|mult500@30s|ne0|ICESWP|t5 | -1.60 | -0.77 (0.72) 0.10 | -0.80 (0.87) 0.20 | -1.43 | -0.43 | -0.69 | +1.48 | +0.24 | -0.30 |

## 6. Saved-loss vs forfeited-recovery in dollars per week (live lots), published cells

saved = sum of positive trade deltas (loss avoided), forfeited = sum of negative deltas (recovery given up); $/wk = pts x lots x $20 / weeks in the window.

| group | kind | L6M net (saved / forfeited) | HOLD net (saved / forfeited) | PRE net (saved / forfeited) | 2026 net (saved / forfeited) |
|---|---|---|---|---|---|
| ALL | RANK | +21,991 (+105,869 / -83,878) | +18,884 (+93,970 / -75,085) | +7,327 (+63,400 / -56,073) | -9,096 (+105,786 / -114,881) |
| ALL | PRE | -19,899 (+316,091 / -335,990) | -19,321 (+285,786 / -305,107) | +22,242 (+255,201 / -232,959) | -3,269 (+367,369 / -370,637) |
| ST | RANK | +13,199 (+45,896 / -32,697) | +12,504 (+44,507 / -32,003) | -1,711 (+40,853 / -42,564) | +7,364 (+45,422 / -38,058) |
| ST | PRE | +108 (+60,751 / -60,643) | +563 (+55,283 / -54,719) | +7,254 (+45,358 / -38,104) | +4,732 (+67,963 / -63,231) |
| HM | RANK | +6,602 (+17,031 / -10,429) | +6,143 (+15,895 / -9,752) | +190 (+17,875 / -17,686) | +826 (+15,372 / -14,545) |
| HM | PRE | -8,251 (+41,283 / -49,533) | -7,282 (+40,327 / -47,608) | +8,882 (+40,623 / -31,742) | -19,701 (+44,083 / -63,785) |
| WT | RANK | +3,864 (+16,883 / -13,019) | +4,065 (+15,575 / -11,510) | -424 (+13,832 / -14,256) | -497 (+21,043 / -21,541) |
| WT | PRE | +1,191 (+22,541 / -21,350) | +1,014 (+21,026 / -20,012) | +2,530 (+19,974 / -17,444) | -7,956 (+23,537 / -31,494) |
| KB | RANK | +5,681 (+25,306 / -19,625) | +4,826 (+23,801 / -18,974) | -1,151 (+22,214 / -23,365) | +922 (+24,318 / -23,396) |
| KB | PRE | -480 (+10,915 / -11,396) | -799 (+10,609 / -11,408) | +2,504 (+10,338 / -7,834) | -694 (+11,919 / -12,613) |
| SM | RANK | +4,776 (+13,835 / -9,060) | +4,348 (+13,658 / -9,310) | -4,065 (+13,379 / -17,444) | +7,197 (+15,054 / -7,857) |
| SM | PRE | -122 (+8,964 / -9,086) | -718 (+8,663 / -9,381) | +1,960 (+8,982 / -7,022) | +924 (+8,347 / -7,423) |
| PE | RANK | +4,421 (+55,486 / -51,065) | +3,888 (+52,140 / -48,252) | -678 (+49,467 / -50,144) | +3,874 (+65,152 / -61,278) |
| PE | PRE | -1,152 (+27,944 / -29,096) | -162 (+26,204 / -26,366) | +4,234 (+24,551 / -20,317) | -1,204 (+34,673 / -35,877) |
| PB | RANK | +3,674 (+9,408 / -5,734) | +3,491 (+8,509 / -5,018) | +1,971 (+9,125 / -7,154) | +3,551 (+10,103 / -6,552) |
| PB | PRE | -7,003 (+53,433 / -60,435) | -3,979 (+52,875 / -56,854) | +10,803 (+57,479 / -46,676) | -20,107 (+59,224 / -79,331) |
| DN | RANK | +5,093 (+17,707 / -12,614) | +5,008 (+16,680 / -11,672) | -4,258 (+15,288 / -19,546) | -2,496 (+15,178 / -17,674) |
| DN | PRE | -5,821 (+14,707 / -20,528) | -4,698 (+14,470 / -19,167) | +3,495 (+11,010 / -7,515) | -13,589 (+15,578 / -29,167) |
| MV | RANK | +5,257 (+15,488 / -10,231) | +4,569 (+15,135 / -10,566) | -259 (+14,300 / -14,559) | +11,284 (+15,780 / -4,496) |
| MV | PRE | -1,513 (+50,277 / -51,790) | -3,455 (+44,994 / -48,449) | +5,266 (+43,912 / -38,646) | -6,604 (+58,902 / -65,506) |
| MA | RANK | +10,914 (+25,920 / -15,005) | +10,754 (+25,730 / -14,976) | -3,494 (+21,945 / -25,439) | +21,947 (+33,506 / -11,559) |
| MA | PRE | -4,159 (+20,765 / -24,925) | -4,728 (+20,187 / -24,915) | +4,304 (+22,415 / -18,111) | +2,442 (+21,315 / -18,873) |

## 7. Session (ENTRY), regime (day volatility tercile) and quarterly drift, published cells (pts/trade [n fired] (MDE))

### by ENTRY session, L6M

| group | kind | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|---|
| ALL | RANK | +0.86 [484] (1.7) | +0.15 [235] (1.5) | +0.64 [19] (1.4) | +0.06 [20] (0.3) | +0.18 [77] (0.6) | - |
| ALL | PRE | -0.20 [704] (2.1) | -1.42 [634] (2.9) | +0.63 [123] (5.0) | +0.12 [530] (1.9) | -0.15 [486] (2.9) | - |
| ST | RANK | +2.06 [104] (2.4) | -0.31 [86] (4.1) | +4.45 [31] (5.2) | +1.97 [196] (3.0) | +1.27 [98] (4.6) | - |
| ST | PRE | -0.11 [101] (4.9) | -1.56 [85] (5.2) | +0.05 [19] (9.2) | +0.84 [91] (3.1) | +0.31 [74] (5.7) | - |
| HM | RANK | +0.85 [68] (3.9) | +3.34 [36] (1.6) | -0.55 [4] (6.4) | -0.46 [16] (2.5) | +0.74 [12] (1.2) | - |
| HM | PRE | -0.80 [130] (4.9) | +0.65 [111] (5.4) | -3.65 [21] (13.3) | -2.08 [106] (5.1) | -2.66 [91] (5.9) | - |
| WT | RANK | +0.01 [146] (2.1) | +0.25 [96] (1.6) | +1.16 [13] (2.0) | +0.24 [16] (0.5) | +1.49 [64] (1.6) | - |
| WT | PRE | -0.25 [39] (1.0) | -0.83 [68] (1.8) | +0.66 [24] (3.8) | +1.15 [172] (2.3) | +0.34 [117] (3.1) | - |
| KB | RANK | +0.87 [63] (1.9) | -0.87 [66] (4.1) | +6.45 [30] (5.1) | +1.48 [206] (3.9) | +2.08 [106] (4.2) | - |
| KB | PRE | -0.08 [149] (2.8) | -1.51 [91] (3.7) | +2.14 [20] (1.1) | -0.06 [151] (2.0) | +0.63 [78] (2.0) | - |
| SM | RANK | +2.08 [41] (9.2) | +3.47 [34] (8.9) | - | +2.61 [16] (6.1) | - | - |
| SM | PRE | +0.94 [13] (3.5) | -2.31 [19] (6.2) | - | -0.35 [47] (10.5) | - | - |
| PE | RANK | +0.66 [83] (3.7) | -1.51 [78] (5.4) | +0.61 [41] (13.8) | +1.78 [254] (6.0) | +2.28 [140] (6.4) | - |
| PE | PRE | +0.12 [172] (4.4) | -2.63 [113] (6.6) | +1.58 [24] (6.7) | -0.65 [148] (3.5) | +1.61 [98] (3.5) | - |
| PB | RANK | +0.44 [35] (2.2) | +1.23 [35] (2.0) | +0.86 [2] (1.7) | -0.07 [15] (2.0) | +0.90 [18] (2.0) | - |
| PB | PRE | -1.75 [105] (4.8) | -1.23 [93] (6.2) | +1.04 [26] (15.1) | -2.90 [129] (7.6) | +1.74 [83] (6.7) | - |
| DN | RANK | +0.50 [66] (5.2) | +3.16 [50] (4.3) | +2.56 [5] (3.0) | +0.35 [13] (1.5) | +0.25 [22] (4.7) | - |
| DN | PRE | +0.45 [5] (0.6) | -0.41 [20] (3.8) | -6.08 [8] (13.6) | -2.79 [79] (5.9) | +0.10 [20] (4.9) | - |
| MV | RANK | +0.81 [102] (1.9) | +0.76 [76] (2.0) | +2.22 [26] (1.1) | +0.15 [114] (2.1) | +0.62 [70] (2.4) | - |
| MV | PRE | +1.00 [82] (4.0) | -3.07 [82] (5.5) | +1.26 [16] (8.2) | -1.07 [72] (3.5) | +2.13 [60] (5.5) | - |
| MA | RANK | +5.60 [76] (7.6) | +3.05 [38] (8.7) | - | +0.76 [6] (3.6) | +4.62 [17] (8.0) | - |
| MA | PRE | -0.55 [31] (4.4) | +0.40 [27] (7.0) | - | -4.03 [54] (12.7) | -2.74 [29] (13.8) | - |

### by regime (vol tercile 0 low / 1 mid / 2 high), L6M

| group | kind | low | mid | high |
|---|---|---|---|---|
| ALL | RANK | +0.65 [122] (1.0) | +0.44 [128] (1.0) | +0.19 [589] (0.8) |
| ALL | PRE | -0.27 [407] (2.1) | +0.05 [338] (2.5) | -0.44 [1742] (1.6) |
| ST | RANK | +0.32 [103] (3.7) | +1.93 [94] (3.5) | +1.74 [320] (2.1) |
| ST | PRE | -0.20 [62] (4.3) | +0.40 [55] (4.5) | -0.04 [254] (3.0) |
| HM | RANK | -0.67 [32] (3.6) | +0.65 [25] (3.1) | +1.77 [79] (1.6) |
| HM | PRE | -2.99 [119] (6.2) | -2.19 [86] (5.9) | -0.32 [254] (3.2) |
| WT | RANK | +0.75 [58] (1.3) | -0.09 [63] (1.8) | +0.54 [216] (1.0) |
| WT | PRE | +0.62 [84] (1.8) | -0.43 [81] (2.4) | +0.16 [257] (1.3) |
| KB | RANK | +0.51 [86] (3.9) | -0.78 [86] (4.2) | +2.05 [301] (2.1) |
| KB | PRE | -2.01 [100] (3.8) | -0.43 [92] (2.8) | +0.63 [297] (1.4) |
| SM | RANK | +4.41 [30] (8.4) | +4.61 [27] (8.9) | +1.29 [49] (5.8) |
| SM | PRE | -3.23 [28] (7.8) | +0.04 [19] (7.8) | +1.52 [57] (5.4) |
| PE | RANK | -0.20 [128] (5.5) | +0.20 [105] (6.1) | +1.60 [364] (3.6) |
| PE | PRE | -2.00 [113] (4.6) | +1.75 [100] (3.6) | -0.30 [343] (3.0) |
| PB | RANK | +0.47 [17] (1.7) | +0.98 [13] (0.8) | +0.51 [75] (1.6) |
| PB | PRE | -2.55 [94] (7.1) | -1.90 [90] (6.6) | -0.31 [252] (4.0) |
| DN | RANK | -0.51 [31] (4.1) | +1.38 [30] (3.3) | +1.54 [96] (2.5) |
| DN | PRE | -3.84 [24] (5.5) | -2.62 [25] (5.3) | +0.49 [83] (2.8) |
| MV | RANK | +1.46 [89] (1.5) | +0.58 [81] (2.6) | +0.38 [218] (1.4) |
| MV | PRE | +0.50 [60] (4.4) | -1.00 [39] (4.8) | -0.18 [215] (2.9) |
| MA | RANK | +0.15 [29] (7.2) | +3.95 [30] (7.8) | +5.40 [86] (5.3) |
| MA | PRE | -3.00 [37] (7.9) | -4.45 [27] (8.5) | +0.62 [89] (6.0) |

### by ENTRY session, PRE

| group | kind | asia | london | pre | nyam | nypm | close |
|---|---|---|---|---|---|---|---|
| ALL | RANK | -0.02 [802] (0.9) | +0.43 [295] (0.6) | +0.91 [72] (0.9) | -0.05 [46] (0.2) | +0.03 [195] (0.5) | +1.58 [8] (2.1) |
| ALL | PRE | +0.14 [1053] (1.3) | +0.06 [1266] (1.7) | +1.38 [411] (2.8) | +0.69 [1155] (1.0) | +0.08 [1145] (1.5) | +9.12 [21] (7.0) |
| ST | RANK | -0.08 [224] (2.1) | +0.28 [246] (2.3) | +0.99 [104] (5.1) | -0.53 [449] (2.6) | -0.91 [270] (3.2) | - |
| ST | PRE | +0.28 [124] (2.7) | +2.02 [169] (3.3) | +3.12 [62] (4.4) | +0.20 [186] (2.2) | +0.78 [160] (3.4) | - |
| HM | RANK | -0.43 [121] (2.3) | +1.20 [110] (2.5) | +3.38 [27] (3.1) | -1.24 [75] (2.2) | -0.03 [68] (2.1) | - |
| HM | PRE | +1.20 [291] (2.7) | +1.86 [237] (3.1) | +4.92 [73] (4.8) | +0.74 [277] (3.3) | +1.26 [237] (3.1) | - |
| WT | RANK | -0.22 [333] (1.3) | -0.15 [251] (1.2) | +1.10 [42] (1.6) | -0.04 [9] (0.3) | -0.09 [129] (1.0) | - |
| WT | PRE | +0.16 [70] (0.4) | +0.18 [124] (0.8) | +0.69 [93] (2.9) | +0.42 [419] (1.5) | +0.43 [288] (1.5) | - |
| KB | RANK | +0.36 [161] (1.7) | -0.36 [189] (2.9) | +0.60 [95] (6.3) | -1.04 [428] (2.9) | -0.12 [294] (2.7) | - |
| KB | PRE | +0.07 [336] (1.8) | +1.48 [244] (1.4) | +1.84 [65] (2.0) | +0.12 [300] (1.4) | +0.63 [236] (1.4) | - |
| SM | RANK | -4.10 [81] (5.7) | -2.21 [120] (6.4) | +1.92 [30] (12.8) | -2.58 [70] (5.8) | -0.16 [32] (7.2) | - |
| SM | PRE | +0.19 [13] (1.2) | +0.60 [62] (3.0) | +3.02 [37] (11.8) | +1.63 [106] (6.0) | +2.21 [43] (6.3) | - |
| PE | RANK | +0.35 [167] (2.0) | -0.21 [240] (3.4) | +2.10 [113] (8.8) | -1.87 [550] (4.4) | +0.98 [407] (4.0) | - |
| PE | PRE | +1.41 [375] (2.8) | +2.54 [300] (2.5) | +1.89 [61] (3.6) | +0.08 [243] (1.9) | -0.32 [288] (2.7) | - |
| PB | RANK | +0.05 [67] (1.3) | -0.13 [82] (1.8) | -0.37 [23] (3.7) | +0.60 [57] (1.3) | +1.07 [55] (1.2) | - |
| PB | PRE | +1.46 [259] (2.8) | +2.01 [256] (3.8) | +2.92 [72] (7.7) | +1.12 [339] (4.3) | +2.54 [245] (4.0) | - |
| DN | RANK | -1.48 [155] (3.8) | -1.93 [147] (3.7) | -1.04 [15] (4.9) | +0.14 [11] (0.3) | -0.81 [80] (3.3) | - |
| DN | PRE | +0.12 [10] (0.7) | +0.70 [35] (1.5) | +0.95 [28] (5.8) | +0.87 [108] (2.3) | +1.03 [54] (2.3) | - |
| MV | RANK | -0.23 [211] (1.4) | -0.29 [183] (1.9) | -0.55 [76] (3.7) | -0.11 [254] (1.5) | +0.65 [213] (1.3) | - |
| MV | PRE | +1.36 [158] (2.3) | -1.06 [155] (3.2) | +1.31 [70] (6.3) | +1.11 [150] (2.3) | +0.51 [150] (2.8) | - |
| MA | RANK | -3.39 [187] (6.5) | -2.07 [112] (6.1) | +0.58 [20] (10.9) | +0.26 [10] (1.3) | +1.06 [61] (5.1) | - |
| MA | PRE | +0.17 [48] (2.4) | -0.55 [79] (4.9) | +2.94 [43] (14.4) | +2.87 [122] (6.8) | +3.89 [89] (6.0) | - |

### by regime (vol tercile 0 low / 1 mid / 2 high), PRE

| group | kind | low | mid | high |
|---|---|---|---|---|
| ALL | RANK | +0.23 [331] (0.5) | +0.17 [281] (0.5) | +0.07 [806] (0.5) |
| ALL | PRE | +0.61 [734] (0.9) | +0.39 [950] (1.1) | +0.20 [3367] (1.1) |
| ST | RANK | -0.08 [348] (2.6) | -1.71 [308] (2.6) | +0.46 [639] (1.7) |
| ST | PRE | +1.03 [93] (1.9) | +0.27 [128] (2.3) | +1.14 [480] (2.3) |
| HM | RANK | +1.50 [112] (1.8) | -1.55 [114] (2.6) | +0.03 [175] (1.6) |
| HM | PRE | +2.94 [325] (2.6) | -0.44 [297] (3.4) | +1.62 [495] (2.0) |
| WT | RANK | -0.03 [177] (0.8) | +0.09 [186] (0.9) | -0.15 [403] (0.8) |
| WT | PRE | +0.44 [255] (1.0) | -0.22 [264] (1.2) | +0.54 [478] (0.8) |
| KB | RANK | -1.19 [292] (2.7) | -0.24 [296] (2.6) | +0.16 [585] (1.7) |
| KB | PRE | +0.33 [315] (1.7) | +0.45 [314] (1.5) | +0.77 [559] (0.9) |
| SM | RANK | -2.75 [114] (5.7) | -1.80 [88] (5.7) | -2.25 [133] (4.7) |
| SM | PRE | +0.66 [80] (3.6) | +2.46 [72] (3.7) | +0.51 [112] (3.4) |
| PE | RANK | -0.66 [384] (3.6) | -0.09 [346] (3.7) | +0.08 [752] (2.5) |
| PE | PRE | +1.34 [312] (2.2) | +0.90 [324] (2.5) | +0.73 [633] (1.7) |
| PB | RANK | +0.74 [44] (0.4) | -0.36 [50] (1.4) | +0.46 [190] (1.3) |
| PB | PRE | +2.06 [339] (3.3) | +1.32 [306] (3.6) | +1.90 [526] (2.7) |
| DN | RANK | -0.67 [115] (2.5) | +0.02 [111] (2.6) | -1.58 [194] (2.2) |
| DN | PRE | -0.09 [63] (1.9) | +0.78 [52] (1.6) | +1.23 [126] (1.4) |
| MV | RANK | -0.33 [263] (1.6) | -0.13 [259] (1.6) | +0.16 [417] (1.0) |
| MV | PRE | +1.42 [86] (1.6) | +1.08 [127] (2.3) | +0.10 [472] (2.2) |
| MA | RANK | -2.30 [104] (4.3) | -0.58 [116] (5.3) | -0.76 [178] (4.5) |
| MA | PRE | -1.38 [119] (4.6) | +2.42 [104] (4.4) | +3.05 [167] (3.7) |

### drift by quarter (mean pts/trade; newest first)

| group | kind | 2026Q1 | 2025Q4 | 2025Q3 | 2025Q2 | 2025Q1 | 2024Q4 | 2024Q3 | 2024Q2 | 2024Q1 | 2023Q4 | 2023Q3 | 2023Q2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL | RANK | -0.22 | +0.60 | +0.19 | +0.21 | -0.33 | +0.49 | +0.18 | +0.30 | +0.25 | -0.44 | -0.89 | +0.30 |
| ALL | PRE | -0.04 | +0.22 | -1.34 | +0.80 | +0.05 | +0.49 | +0.44 | -0.32 | +0.31 | -0.05 | +0.15 | -0.44 |
| ST | RANK | +0.77 | +1.93 | +1.12 | +0.18 | -1.17 | -0.34 | +1.22 | -1.12 | -0.59 | -1.46 | +0.23 | +1.65 |
| ST | PRE | +0.49 | +0.44 | -0.85 | +0.29 | +0.80 | +0.69 | +2.51 | -0.81 | +1.17 | -1.06 | +0.03 | +0.31 |
| HM | RANK | +0.12 | +1.26 | +1.09 | -0.74 | +0.05 | +0.86 | -1.74 | +1.44 | +2.10 | +0.51 | -0.44 | -0.31 |
| HM | PRE | -2.91 | -0.18 | -1.51 | +0.81 | +1.92 | +1.81 | +0.90 | +2.78 | +0.54 | +1.37 | -1.40 | +1.70 |
| WT | RANK | -0.05 | +0.89 | +0.25 | +0.04 | -0.03 | -0.09 | +0.36 | -0.79 | -0.01 | -0.84 | -0.05 | +0.16 |
| WT | PRE | -0.84 | +0.37 | +0.40 | +0.91 | +0.69 | -0.81 | +0.55 | -0.11 | +0.29 | +0.74 | +0.10 | +0.19 |
| KB | RANK | +0.18 | +1.94 | +0.28 | +1.06 | -1.43 | -0.68 | +1.42 | -1.83 | -2.35 | +2.90 | +0.77 | -0.50 |
| KB | PRE | -0.14 | +0.22 | -0.88 | +0.49 | -0.61 | +0.49 | +1.59 | +1.01 | +0.21 | +1.84 | -1.32 | +1.71 |
| SM | RANK | +4.49 | +1.93 | +2.44 | -1.30 | -2.03 | -2.28 | -1.25 | -2.41 | -4.16 | -1.74 | +0.43 | +0.81 |
| SM | PRE | +0.58 | -0.65 | -0.64 | +5.01 | +1.64 | +1.18 | -0.19 | +1.25 | -2.70 | +0.87 | +2.35 | +2.15 |
| PE | RANK | +0.74 | +2.18 | -1.30 | +2.27 | -0.87 | -3.08 | +0.64 | -0.85 | -1.09 | -3.67 | +2.85 | -2.82 |
| PE | PRE | -0.23 | +0.22 | -0.33 | +1.87 | -0.58 | +1.35 | +1.66 | -0.02 | +1.16 | -1.55 | +0.26 | +0.44 |
| PB | RANK | +0.55 | +0.57 | +0.62 | +0.91 | -0.38 | +1.30 | +0.17 | +0.28 | -0.47 | +0.15 | +0.05 | -0.65 |
| PB | PRE | -3.09 | -2.56 | +3.59 | +0.22 | -0.15 | +3.69 | +4.02 | +2.46 | +0.63 | -2.57 | +0.17 | -1.28 |
| DN | RANK | -0.51 | +2.35 | -0.11 | -2.32 | -2.16 | +0.46 | +0.45 | -0.90 | +0.25 | +0.03 | +0.98 | +0.18 |
| DN | PRE | -2.79 | -0.38 | -0.79 | +0.17 | -0.36 | +1.76 | +1.94 | -0.07 | +1.24 | +0.72 | +0.10 | +0.10 |
| MV | RANK | +1.24 | +0.20 | +0.72 | -0.20 | -0.63 | +0.02 | -0.17 | +0.69 | +1.32 | +0.89 | +0.35 | +1.65 |
| MV | PRE | -0.73 | +0.80 | -2.23 | +1.02 | +0.18 | +0.69 | +1.37 | -0.70 | +0.97 | +1.08 | -0.66 | +1.97 |
| MA | RANK | +7.57 | +2.04 | +3.57 | -1.35 | -2.30 | -1.87 | +1.72 | -0.13 | -3.15 | -2.37 | +4.33 | +2.12 |
| MA | PRE | +0.84 | -2.82 | -1.36 | +3.55 | +2.44 | -1.92 | +3.32 | +1.08 | -1.42 | +0.65 | +0.70 | +0.20 |

(2026Q1 = 2026-01-01..02-06 only.)

## 8. Stack level (exact per-book 1-s lock engine; cell as the exit stream of the book; $ per week)

Windows recent first. Columns: weekly mean (delta vs the stack as it is, MDE), weekly SD, maxDD, sum of the 20 worst weeks. 'COMBO' = best cells of all six stack books together. Half-cut cells are run with the exit at the baseline exit time and the blended P&L (occupancy conservative).

| run | window | weekly mean | delta vs stack (MDE) | SD | maxDD | worst-20-weeks |
|---|---|---|---|---|---|---|
| BASE | 2026 | +46,187 | - | 146,009 | 276,732 | +277,121 |
| BASE | L6M | +65,679 | - | 123,009 | 466,422 | +204,018 |
| BASE | HOLD | +52,448 | - | 151,891 | 601,016 | -742,938 |
| BASE | PRE | +44,127 | - | 131,184 | 477,701 | -2,304,797 |
| BASE | X' | +20,616 | - | 112,784 | 553,090 | -1,677,814 |
| ALL|RANK | 2026 | +46,013 | -174 (26,033) | 167,130 | 308,447 | +276,080 |
| ALL|RANK | L6M | +77,592 | +11,913 (16,842) | 131,481 | 394,948 | +344,081 |
| ALL|RANK | HOLD | +62,175 | +9,727 (15,108) | 157,915 | 616,556 | -620,576 |
| ALL|RANK | PRE | +38,975 | -5,153 (12,416) | 130,169 | 592,401 | -2,400,229 |
| ALL|RANK | X' | +16,651 | -3,965 (15,045) | 116,340 | 556,219 | -1,766,619 |
| ALL|PRE | 2026 | +65,512 | +19,325 (27,805) | 133,195 | 264,723 | +393,070 |
| ALL|PRE | L6M | +46,797 | -18,882 (31,466) | 114,200 | 488,185 | -194,610 |
| ALL|PRE | HOLD | +34,939 | -17,509 (27,784) | 140,893 | 582,640 | -1,006,392 |
| ALL|PRE | PRE | +34,688 | -9,439 (14,017) | 120,586 | 430,260 | -2,172,922 |
| ALL|PRE | X' | +6,559 | -14,057 (14,864) | 113,178 | 759,225 | -1,881,030 |
| ST|RANK | 2026 | +51,186 | +4,999 (46,658) | 150,144 | 306,968 | +307,117 |
| ST|RANK | L6M | +62,587 | -3,092 (17,651) | 124,459 | 440,026 | +176,853 |
| ST|RANK | HOLD | +50,905 | -1,543 (15,594) | 149,156 | 561,979 | -714,005 |
| ST|RANK | PRE | +39,204 | -4,923 (10,752) | 128,630 | 479,072 | -2,289,257 |
| ST|RANK | X' | +14,758 | -5,858 (7,878) | 115,281 | 543,786 | -1,827,054 |
| ST|PRE | 2026 | +68,971 | +22,785 (44,230) | 140,198 | 261,449 | +413,828 |
| ST|PRE | L6M | +58,716 | -6,963 (20,175) | 116,053 | 534,182 | +105,279 |
| ST|PRE | HOLD | +46,730 | -5,717 (17,697) | 146,795 | 596,365 | -768,778 |
| ST|PRE | PRE | +42,717 | -1,410 (5,877) | 128,827 | 461,081 | -2,261,500 |
| ST|PRE | X' | +14,963 | -5,654 (8,055) | 113,847 | 587,614 | -1,783,477 |
| HM|RANK | 2026 | +53,535 | +7,348 (19,114) | 141,992 | 275,966 | +321,207 |
| HM|RANK | L6M | +73,839 | +8,160 (7,581) | 120,270 | 471,924 | +410,525 |
| HM|RANK | HOLD | +59,158 | +6,710 (6,990) | 151,241 | 606,227 | -553,372 |
| HM|RANK | PRE | +42,860 | -1,267 (7,478) | 121,991 | 465,355 | -2,010,716 |
| HM|RANK | X' | +19,001 | -1,615 (5,805) | 114,717 | 598,823 | -1,720,463 |
| HM|PRE | 2026 | +45,463 | -724 (26,346) | 152,499 | 245,354 | +272,777 |
| HM|PRE | L6M | +63,608 | -2,071 (13,080) | 119,460 | 458,355 | +173,304 |
| HM|PRE | HOLD | +49,322 | -3,125 (12,296) | 154,813 | 670,862 | -755,914 |
| HM|PRE | PRE | +47,621 | +3,494 (9,898) | 122,071 | 512,387 | -2,089,588 |
| HM|PRE | X' | +17,432 | -3,184 (8,672) | 107,679 | 560,574 | -1,665,928 |
| WT|RANK | 2026 | +34,218 | -11,968 (12,324) | 153,702 | 270,845 | +205,311 |
| WT|RANK | L6M | +61,639 | -4,039 (7,030) | 121,361 | 461,440 | +150,532 |
| WT|RANK | HOLD | +48,987 | -3,460 (6,198) | 150,188 | 598,644 | -779,667 |
| WT|RANK | PRE | +41,052 | -3,075 (4,981) | 128,950 | 498,866 | -2,283,458 |
| WT|RANK | X' | +20,044 | -572 (5,493) | 109,862 | 555,224 | -1,612,646 |
| WT|PRE | 2026 | +34,353 | -11,834 (24,627) | 149,396 | 268,481 | +206,116 |
| WT|PRE | L6M | +62,409 | -3,270 (6,022) | 123,688 | 476,069 | +124,218 |
| WT|PRE | HOLD | +49,009 | -3,439 (5,217) | 152,780 | 607,845 | -828,470 |
| WT|PRE | PRE | +40,394 | -3,733 (3,105) | 130,108 | 544,542 | -2,360,553 |
| WT|PRE | X' | +22,597 | +1,981 (2,949) | 114,435 | 554,432 | -1,663,725 |
| KB|RANK | 2026 | +42,207 | -3,980 (9,931) | 148,135 | 277,815 | +253,242 |
| KB|RANK | L6M | +63,861 | -1,817 (3,740) | 123,260 | 469,581 | +155,569 |
| KB|RANK | HOLD | +50,677 | -1,770 (3,311) | 151,857 | 605,080 | -800,340 |
| KB|RANK | PRE | +39,094 | -5,034 (4,262) | 133,924 | 489,757 | -2,431,534 |
| KB|RANK | X' | +21,588 | +972 (4,001) | 111,785 | 546,411 | -1,666,455 |
| KB|PRE | 2026 | +50,136 | +3,949 (6,602) | 147,751 | 281,354 | +300,816 |
| KB|PRE | L6M | +64,072 | -1,606 (5,577) | 124,236 | 476,710 | +127,818 |
| KB|PRE | HOLD | +51,144 | -1,304 (4,952) | 153,240 | 603,390 | -815,131 |
| KB|PRE | PRE | +39,875 | -4,252 (4,081) | 134,159 | 455,302 | -2,419,832 |
| KB|PRE | X' | +18,819 | -1,797 (3,131) | 113,020 | 561,881 | -1,708,954 |
| SM|RANK | 2026 | +51,980 | +5,793 (14,898) | 136,456 | 251,178 | +311,882 |
| SM|RANK | L6M | +69,250 | +3,572 (7,865) | 120,104 | 453,572 | +284,913 |
| SM|RANK | HOLD | +55,824 | +3,376 (7,083) | 148,232 | 578,751 | -621,342 |
| SM|RANK | PRE | +39,012 | -5,115 (5,874) | 129,846 | 451,924 | -2,379,609 |
| SM|RANK | X' | +19,527 | -1,089 (4,911) | 112,948 | 554,507 | -1,663,192 |
| SM|PRE | 2026 | +44,985 | -1,202 (11,626) | 141,755 | 276,464 | +269,912 |
| SM|PRE | L6M | +65,581 | -97 (4,733) | 121,928 | 465,014 | +200,695 |
| SM|PRE | HOLD | +51,996 | -452 (4,226) | 150,604 | 602,940 | -715,252 |
| SM|PRE | PRE | +42,467 | -1,660 (3,782) | 130,787 | 480,956 | -2,357,263 |
| SM|PRE | X' | +22,002 | +1,386 (2,275) | 113,924 | 538,003 | -1,670,660 |
| PE|RANK | 2026 | +45,557 | -629 (13,939) | 139,242 | 258,110 | +273,345 |
| PE|RANK | L6M | +61,395 | -4,283 (7,335) | 119,069 | 454,716 | +175,017 |
| PE|RANK | HOLD | +49,288 | -3,160 (6,688) | 147,383 | 569,791 | -717,364 |
| PE|RANK | PRE | +40,894 | -3,233 (6,084) | 127,235 | 450,541 | -2,378,398 |
| PE|RANK | X' | +19,009 | -1,608 (6,101) | 111,905 | 557,995 | -1,697,166 |
| PE|PRE | 2026 | +41,204 | -4,983 (11,279) | 149,717 | 272,085 | +247,225 |
| PE|PRE | L6M | +60,435 | -5,243 (8,127) | 123,714 | 484,000 | +102,363 |
| PE|PRE | HOLD | +48,352 | -4,096 (7,595) | 151,714 | 589,598 | -806,455 |
| PE|PRE | PRE | +45,945 | +1,818 (5,474) | 129,016 | 446,252 | -2,241,118 |
| PE|PRE | X' | +19,225 | -1,392 (5,627) | 114,009 | 548,295 | -1,720,128 |
| COMBO|RANK | 2026 | +47,750 | +1,563 (33,021) | 134,414 | 236,690 | +286,497 |
| COMBO|RANK | L6M | +64,179 | -1,500 (20,987) | 111,528 | 416,166 | +347,380 |
| COMBO|RANK | HOLD | +52,601 | +153 (19,113) | 137,070 | 515,392 | -471,402 |
| COMBO|RANK | PRE | +21,480 | -22,647 (18,896) | 116,931 | 468,267 | -2,360,244 |
| COMBO|RANK | X' | +10,846 | -9,770 (13,549) | 112,177 | 579,280 | -1,819,884 |
| COMBO|PRE | 2026 | +54,178 | +7,991 (29,340) | 144,602 | 222,427 | +325,069 |
| COMBO|PRE | L6M | +46,429 | -19,250 (23,666) | 111,206 | 546,583 | -120,709 |
| COMBO|PRE | HOLD | +34,314 | -18,134 (21,171) | 148,656 | 665,920 | -1,019,773 |
| COMBO|PRE | PRE | +38,384 | -5,743 (13,812) | 118,366 | 450,398 | -2,198,917 |
| COMBO|PRE | X' | +11,958 | -8,659 (13,985) | 113,145 | 573,922 | -1,859,955 |
