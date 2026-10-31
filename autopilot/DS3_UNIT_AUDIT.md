# DS3_UNIT_AUDIT - UA-1: one table, the same number on every unit and convention, for every Sunday-brief ON / SHADOW candidate (2026-10-31)
Research only; one engine (stack2/s2_lib -> stackpart sp_lib rows + sl_lib exact per-book lock engine, the engine of SP-1 / SPLIT-2 / STACK-2 / KB-REGIME); masks capped 20260206 (windows L3M 20251106-, L6M 20250801-, HOLD 20250701-, PRE 20240201-20250630, X' 20230401-20240131); UNTOUCHED never read; no new search and no selection (every candidate is the cell the Sunday brief / its source report names; honest labels are the source report's). Code `l2vast/ds3/code/unitaudit/`, outputs `l2vast/ds3/out/unitaudit/` (`full_table.csv` = every convention x window x candidate, 3240 rows). $/wk = stack delta of the rule vs the same reference stack on the same convention (research lots unless stated); MDE = 2.8 x week-clustered SE of the weekly delta; CI = 4-week circular block bootstrap (2,000 draws) of the weekly delta.

## KEY POINTS (the 12 points to read before the table)
1. **Nothing flips sign in L6M or HOLD for these: the 70/30 split, the Asia-stopped cut50 (and cut100-Asia, Asia & vol, other-side-open), the 8-line skip at D = 20, the PE 45-s three-bar (market, NY), the KB ER0.2 sizer, the ER20 sizer (L6M/HOLD positive in every cell), stop-join Native.** They are positive in all 20-80 convention cells of the grid in both windows. Positive is not the same as outside MDE: only the split (N basis, research lots: +17.6k vs MDE 16.6k) and the stop-join (+4.1k vs 2.9k) clear their L6M MDE; the rest are inside it.
2. **Sign flips in L6M and/or HOLD (flag):** pooled first-stop cut50 (negative on market x M x live lots: L6M -0.3k, HOLD -1.3k), cut25-Asia (HOLD), cut50 in vol tercile 2 (HOLD, basis M), cut50 with <=2 other books open (L6M and HOLD: S73 research cells), cut50 with ER20>=0.4 (L6M and HOLD, live lots), 8-line skip at D = 15 (L6M and HOLD), HM FVG skip (HOLD negative in 9 of 20 cells, 9 of the 10 live-lot cells), second-signal skip (HOLD -0.0k on S73 N live lots; PRE -3.9k), the ER(20)>=0.3 SKIP (L6M -14.7k and HOLD -9.4k on S73, 8 of 10 S73 cells negative; mixed on market), the ES-lead N1 sizer (equal-risk planned-lot R +7.4k L6M, sized-lot R -1.1k) and the ES lag-z sizer (S73 L6M -0.8k, market +4.7k, and the eslead report's +5.9k is on a different 70/30 base).
3. **The governor question decides every sizer.** ER20 sizer (S73, N, research lots, as coded): planned-lot R +8.5k L6M / +10.1k HOLD / **-9.2k PRE** / +6.5k X'; sized-lot R +37.3k / +32.8k / +11.2k / -0.7k (equal-risk +10.0k planned vs +51.1k sized in L6M). KB ER0.2 sizer: planned +3.1k L6M / PRE -1.6k, sized +8.1k / PRE +3.4k. ES N1 sizer: **planned +7.4k, sized -1.1k** (equal-risk). The brief's "~ +7k or ~ 0" for D6 is real: for the ER sizer it is +8.5k vs +37.3k, for the ES sizers the sign flips the other way.
4. **Re-entry is more than half of the L6M gain (gross re-entry-in share, S2 definition, headline S73):** Asia cut50 71% (net admit 81%; on market 81% / 85%), cut100-Asia 95%, pooled cut 67%, second-signal skip 73%, 8-line skip D=20 85% (D=15 193%), ER20 sizer 200% gross (net 32%), KB ER0.2 sizer 88%, PE 45-s 58% gross / 105% net; split 47% gross / 55% net. Lowest: cut50 vol tercile 2 16%, Asia & vol 31%, other-side-open 34%. The same-trade (pre-lock) dollars of the Asia cut50 are only +3.3k of the +13.2k (25%).
5. **Top-5 weeks:** every candidate has its 5 best weeks above 50% of the L6M gain (split 66%, Asia cut 111%, 8-line 96%, HM FVG 105%, ER sizer 260%, PE 123%). The null expectation for 28 independent weekly deltas with the same mean and SD is 96-170% (column "iid" in section 5: 62% for the split, 96-170% for the rest), so for the signal rows this is what noise looks like and the flag does not separate candidates; only the split (66% vs iid 62%) and the stop-join (43%, a steady cost saving) are not more concentrated than their weekly noise.
6. **Stop-join Native is the one row whose dollars are mostly units, not signal:** +4.1k/wk L6M at research lots (ST 10 + HM 10; week-block CI +2.8k..+6.0k, MDE 2.9k) but **+1.5k/wk at the live lots** (S6 4.26, H6 4/2: CI +0.9k..+2.3k, MDE 1.2k); the brief's "+4.4k at 10 lots" overstates the live dollars about 3x. Positive in every cell; Native-vs-fixed-0.5 gives +7.3k research / +2.7k live.
7. **70/30 split at integer live lots (UF-ENTRY C7 request):** per-book on the C7 series, N basis, research lots, L6M, integer lots + modelled add slippage (+0.25 pt/lot): S6 +3.3k, W6 +3.7k, U6 +3.0k, H6 +0.8k, P6 +0.8k, **K6 -3.0k** (L3M -2.3k, HOLD -2.4k, PRE -3.1k; positive only in X' +1.3k). K6 is the only book negative in four windows in a row; it is a 1/1 split at 2 lots; the ideal 70/30 on K6 is -0.5k with the slippage. **Summed at live lots the split is +8.0k/wk L6M without slippage and +4.8k (N) / +5.3k (LIVE-CAL) with integer lots and the +0.25 pt slippage; +4.7k / +3.7k at the +0.45 stress** (brief: ~ +7.5k). Engine-run live-session lots (sessions of live lot 0 removed): +5.4k N, +4.0k LIVE-CAL, +3.5k with the ST/HM stop at 0.5.
8. **Live-lot dollars (convention B, engine at live lots, sessions of lot 0 dropped) vs /2.35 (A):** split 5.4k vs 7.5k; Asia cut50 9.1k vs 5.6k; ER20 sizer 8.6k vs 3.6k; 8-line skip D=20 3.9k vs 6.6k; HM FVG skip 0.6k vs 3.9k (HM live is Asia 4 / NY-AM 2 only); PE 45-s 2.4k vs 1.3k (P6 7 lots > 5.6 research); KB 1.4k vs 1.3k. A and B differ by 1.6x to 6x on six of these rows, so "live dollars" must say which.
9. **Bases:** every "positive in all cells" row above is also positive on M, LIVE-CAL and both LIVE-JOIN stop-cost variants except the ones listed in point 2 (the pooled cut and cut25-Asia and the vol-tercile cut go negative on basis M; the HM FVG skip and the <=2-books cut on the N/LIVE family). LIVE-JOIN Native/fixed change the split by only -0.5k/-1.6k (L6M, research), because the split is entry geometry and the stop cost hits both arms.
10. **Engine caveat on reproduction:** market-base, cut, split, KB and PE-market numbers reproduce their source reports to the first decimal (section 8). The 70/30 base of the trend / newideas / eslead wrappers (tg_stack "f73/B2") is not the sp_lib S73 line (L6M base stack 72.1k vs 79.1k), so their S73-based sizer figures differ here (ER20 equal-risk planned L6M +10.0k here vs +13.3k reported; ES lag-z S73 -0.8k vs +5.9k); the 8-line skip reported +28.3k on the ZONES addendum engine is +15.4k on this engine. On market bases they match to the dollar.
11. **Mapping (section 4):** K6 = KB, P6 = PE, U6 = SM, H6 = HM, S6 = ST, W6 = WT, MA6 = MA; M6 (MV), A6 (PB7), O6 have no row in the six-book lock engine and are not valued anywhere. The SIZING note says K6/P6/U6 came from the ABR bundle, but the user's THP_POLICY-format directive lists K6 KB, P6 PE, U6 SM, so the mapping is user-sourced; the one risk is P6 (FOLLOWUP_BRIEF writes "PB3B": if P6 were the PB book it is outside the engine).
12. Questions for the user: in MORNING.md only (none blocking; the two that change numbers: D6 governors planned vs sized R; whether P6 is PE).

## PAGE 1 - FLAGS (read this first)
Convention cells per candidate = reference base (S73 live 70/30 line | market) x basis (N | M | LIVE-CAL 2.45 | LIVE-JOIN with ST+HM stop cost Native 1.28 | fixed 0.5) x lots (research | live book-session lots) x governors (planned-lot R | sized-lot R, sizers only) x scale (as coded | equal-risk, sizers only). A sign flip = at least one cell of the grid is negative while another is positive in the same window. "Re-entry share" = lock-engine gain from rows admitted only in the rule world / total gain (the S2 artefact: 76% for the pooled first-stop cut = 17.4k of 23.0k, reproduced here to the dollar); "net admit share" = (re-entry in + admit-out)/total. "Top-5 weeks" = the 5 best weekly deltas / total gain in the window (L6M has 28 weeks).

| candidate | headline L6M | HOLD | PRE | X' | L6M grid min..max | HOLD grid min..max | sign flip L6M | sign flip HOLD | re-entry share L6M (headline / grid max) | net admit share (headline / grid max) | top-5-weeks share L6M (headline / grid max) | FLAGS |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 70/30 split (S73 vs market) | +17.6k | +18.4k | +3.8k | +2.2k | +3.5k..+17.6k | +3.4k..+18.4k | no | no | 47% / 47% | 55% / 55% | 66% / 163% | >50% re-entry/admit (headline net); top-5 weeks > 50% |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | +3.0k | +2.8k | -0.7k | -1.0k | +2.1k..+3.4k | +1.9k..+3.3k | no | no | 58% / 58% | 105% / 254% | 123% / 171% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | +3.6k | +3.3k | -0.4k | -0.6k | +1.0k..+3.6k | +0.9k..+3.3k | no | no | 34% / 34% | 115% / 442% | 104% / 299% | >50% re-entry/admit (headline net); top-5 weeks > 50%; inside MDE |
| PE 45-s three-bar, market, NY, 3-s delay | +3.4k | +3.1k | -0.6k | -0.6k | +1.1k..+3.8k | +1.0k..+3.1k | no | no | 28% / 28% | 107% / 364% | 112% / 294% | >50% re-entry/admit (headline net); top-5 weeks > 50%; inside MDE |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | +8.5k | +10.1k | -9.2k | +6.5k | +8.5k..+63.1k | +8.9k..+54.2k | no | no | 200% / 200% | 32% / 125% | 260% / 273% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | +3.1k | +2.8k | -1.6k | +0.8k | +0.7k..+8.8k | +0.5k..+7.2k | no | no | 88% / 108% | 42% / 72% | 173% / 291% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, stopped book entered in Asia | +13.2k | +11.4k | +2.0k | +2.8k | +4.8k..+20.2k | +4.6k..+16.5k | no | no | 71% / 81% | 81% / 88% | 111% / 161% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, pooled (all sessions) | +6.6k | +4.6k | -6.5k | -0.4k | -0.3k..+23.0k | -1.3k..+19.3k | YES | YES | 67% / 105% | 96% / 138% | 219% / 344% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| first-stop cut 100%, Asia | +11.8k | +9.9k | +5.3k | +2.2k | +2.8k..+15.1k | +2.9k..+13.1k | no | no | 95% / 100% | 56% / 67% | 165% / 359% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| first-stop cut 25%, Asia | +8.8k | +7.6k | -1.2k | +2.6k | +0.2k..+12.8k | -0.3k..+10.2k | no | YES | 65% / 95% | 83% / 95% | 128% / 455% | SIGN FLIP HOLD; >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, entry-day vol tercile 2 | +3.5k | +3.5k | -0.4k | +3.5k | +0.4k..+12.4k | -0.4k..+10.8k | no | YES | 16% / 74% | 51% / 89% | 327% / 546% | SIGN FLIP HOLD; >50% re-entry/admit (headline net); top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, Asia & vol tercile 2 | +6.8k | +6.5k | +4.5k | +4.7k | +3.6k..+12.4k | +3.5k..+10.2k | no | no | 31% / 67% | 48% / 76% | 182% / 317% | >50% re-entry/admit in some cell; top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, <=2 other books open | -0.2k | +0.5k | +1.6k | -1.8k | -2.3k..+11.5k | -1.3k..+11.9k | YES | YES | n/m / 79% | n/m / 108% | n/m / 391% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50% in some cell |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | +0.9k | +0.6k | +3.6k | +0.9k | -0.5k..+7.4k | -0.6k..+5.5k | YES | YES | n/m / 68% | n/m / 71% | 680% / 415% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50%; inside MDE |
| first-stop cut 50%, a book open on the other side | +4.8k | +4.6k | +2.8k | +4.2k | +1.1k..+6.2k | +0.7k..+6.2k | no | no | 34% / 49% | 52% / 63% | 174% / 235% | >50% re-entry/admit (headline net); top-5 weeks > 50%; inside MDE |
| 8-line skip, fresh line within 20 pts (S8) | +15.4k | +12.4k | +1.6k | +4.9k | +2.4k..+28.8k | +2.0k..+25.3k | no | no | 85% / 85% | 22% / 32% | 96% / 269% | >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| 8-line skip, D=15 pts (S8) | +5.2k | +4.7k | +4.3k | +5.4k | -0.5k..+18.8k | -0.8k..+17.7k | YES | YES | 193% / 210% | 5% / 100% | 268% / 488% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | +3.7k | +3.2k | +3.3k | -2.6k | -7.9k..+9.1k | -7.6k..+7.4k | YES | YES | -19% / 83% | 33% / 169% | 249% / 478% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50%; inside MDE |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | -0.8k | -2.1k | +6.5k | +1.6k | -11.6k..+6.0k | -7.5k..+7.5k | YES | YES | n/m / 124% | n/m / 130% | n/m / 470% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50% in some cell |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | +5.6k | +4.5k | -3.9k | -3.0k | +0.6k..+11.3k | -0.0k..+9.5k | no | YES | 73% / 137% | 48% / 149% | 117% / 481% | SIGN FLIP HOLD; >50% re-entry/admit (headline gross); top-5 weeks > 50%; inside MDE |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | +9.3k | +6.5k | -1.3k | -1.6k | +0.2k..+12.4k | -0.4k..+9.7k | no | YES | 49% / 66% | 49% / 59% | 105% / 436% | SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50%; inside MDE |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | +4.1k | +4.1k | +4.7k | +3.0k | +1.5k..+4.7k | +1.5k..+4.3k | no | no | 0% / 10% | 12% / 14% | 43% / 48% | - |
| stop-join: ST+HM stop cost 0.5 (the fix target) | +7.3k | +7.3k | +6.8k | +5.0k | +2.7k..+8.9k | +2.7k..+8.4k | no | no | 17% / 19% | 10% / 20% | 55% / 60% | top-5 weeks > 50% |
| ER(20)>=0.3 as a skip (TG-1) | -14.7k | -9.4k | -19.7k | -9.5k | -14.7k..+17.3k | -9.4k..+21.2k | YES | YES | n/m / 243% | n/m / 193% | n/m / 429% | SIGN FLIP L6M; SIGN FLIP HOLD; >50% re-entry/admit in some cell; top-5 weeks > 50% in some cell |

Headline convention = reference S73 (the live 70/30 line; the split itself and the PE rows vs their stated floors excepted), basis N, research lots (ST 10, HM 10, WT 7, KB 5.2, SM 7.4, PE 5.6), planned-lot-R governors, as coded (no equal-risk rescale). Where the grid min..max straddles zero the row is flagged; the axes that carry the negative cells are listed in section 5.

### Plain sentences (what moves the sign)
* **first-stop cut 50%, pooled (all sessions)**: L6M grid -0.3k..+23.0k (1 of 20 cells negative), HOLD grid -1.3k..+19.3k (1 of 20 negative). Negative cells sit in: ref=MKT (1/10 neg), basis=M (1/4 neg), lots=live (1/10 neg), gov=planned (1/20 neg), scale=raw (1/20 neg).
* **first-stop cut 25%, Asia**: L6M grid +0.2k..+12.8k (0 of 20 cells negative), HOLD grid -0.3k..+10.2k (1 of 20 negative). Negative cells sit in: ref=S73 (1/10 neg), basis=M (1/4 neg), lots=research (1/10 neg), gov=planned (1/20 neg), scale=raw (1/20 neg).
* **first-stop cut 50%, entry-day vol tercile 2**: L6M grid +0.4k..+12.4k (0 of 20 cells negative), HOLD grid -0.4k..+10.8k (2 of 20 negative). Negative cells sit in: ref=S73 (1/10 neg), ref=MKT (1/10 neg), basis=M (2/4 neg), lots=research (1/10 neg), lots=live (1/10 neg), gov=planned (2/20 neg), scale=raw (2/20 neg).
* **first-stop cut 50%, <=2 other books open**: L6M grid -2.3k..+11.5k (4 of 20 cells negative), HOLD grid -1.3k..+11.9k (1 of 20 negative). Negative cells sit in: ref=S73 (4/10 neg), basis=N (1/4 neg), basis=LIVE (1/4 neg), basis=LIVE_native (1/4 neg), basis=LIVE_fixed (1/4 neg), lots=research (4/10 neg), gov=planned (4/20 neg), scale=raw (4/20 neg), ref=S73 (1/10 neg), lots=research (1/10 neg), gov=planned (1/20 neg), scale=raw (1/20 neg).
* **first-stop cut 50%, ER20>=0.4 at the stopped signal**: L6M grid -0.5k..+7.4k (4 of 20 cells negative), HOLD grid -0.6k..+5.5k (4 of 20 negative). Negative cells sit in: ref=S73 (3/10 neg), ref=MKT (1/10 neg), basis=N (1/4 neg), basis=M (1/4 neg), basis=LIVE_native (1/4 neg), basis=LIVE_fixed (1/4 neg), lots=live (4/10 neg), gov=planned (4/20 neg), scale=raw (4/20 neg).
* **8-line skip, D=15 pts (S8)**: L6M grid -0.5k..+18.8k (1 of 20 cells negative), HOLD grid -0.8k..+17.7k (2 of 20 negative). Negative cells sit in: ref=MKT (1/10 neg), basis=LIVE_fixed (1/4 neg), lots=live (1/10 neg), gov=planned (1/20 neg), scale=raw (1/20 neg), ref=S73 (1/10 neg), basis=N (1/4 neg), lots=live (2/10 neg), gov=planned (2/20 neg), scale=raw (2/20 neg).
* **ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5**: L6M grid -7.9k..+9.1k (40 of 80 cells negative), HOLD grid -7.6k..+7.4k (41 of 80 negative). Negative cells sit in: ref=S73 (16/40 neg), ref=MKT (24/40 neg), basis=N (8/16 neg), basis=M (10/16 neg), basis=LIVE (7/16 neg), basis=LIVE_native (7/16 neg), basis=LIVE_fixed (8/16 neg), lots=research (19/40 neg), lots=live (21/40 neg), gov=planned (6/40 neg), gov=sized (34/40 neg), scale=raw (26/40 neg).
* **ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line)**: L6M grid -11.6k..+6.0k (9 of 80 cells negative), HOLD grid -7.5k..+7.5k (18 of 80 negative). Negative cells sit in: ref=S73 (5/40 neg), ref=MKT (4/40 neg), basis=N (2/16 neg), basis=M (7/16 neg), lots=research (6/40 neg), lots=live (3/40 neg), gov=planned (5/40 neg), gov=sized (4/40 neg), scale=raw (6/40 neg), scale=eqr (3/40 neg), ref=S73 (12/40 neg), ref=MKT (6/40 neg).
* **second-signal skip: same-book re-entry <=30 min after a loser (N1 b)**: L6M grid +0.6k..+11.3k (0 of 20 cells negative), HOLD grid -0.0k..+9.5k (1 of 20 negative). Negative cells sit in: ref=S73 (1/10 neg), basis=N (1/4 neg), lots=live (1/10 neg), gov=planned (1/20 neg), scale=raw (1/20 neg).
* **HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1)**: L6M grid +0.2k..+12.4k (0 of 20 cells negative), HOLD grid -0.4k..+9.7k (9 of 20 negative). Negative cells sit in: ref=S73 (5/10 neg), ref=MKT (4/10 neg), basis=N (2/4 neg), basis=M (1/4 neg), basis=LIVE (2/4 neg), basis=LIVE_native (2/4 neg), basis=LIVE_fixed (2/4 neg), lots=live (9/10 neg), gov=planned (9/20 neg), scale=raw (9/20 neg).
* **ER(20)>=0.3 as a skip (TG-1)**: L6M grid -14.7k..+17.3k (12 of 20 cells negative), HOLD grid -9.4k..+21.2k (12 of 20 negative). Negative cells sit in: ref=S73 (8/10 neg), ref=MKT (4/10 neg), basis=N (3/4 neg), basis=LIVE (3/4 neg), basis=LIVE_native (3/4 neg), basis=LIVE_fixed (3/4 neg), lots=research (4/10 neg), lots=live (8/10 neg), gov=planned (12/20 neg), scale=raw (12/20 neg).

## 1. The table: headline convention, every window, with MDE and week-block CI
| candidate | ref | L3M | L6M [CI] (MDE) | HOLD | PRE | X' | MDE L3M / HOLD / PRE / X' | trades/wk rule vs ref (L6M) | per planned lot L6M (rule-ref, MDE) | per contract of final position L6M rule vs ref (library) | lock-engine pts/contract L6M rule vs ref | $/wk L6M at /2.35 | $/wk L6M live-session lots (engine) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 70/30 split (S73 vs market) | MKT | +20.2k | +17.6k [+8.1k..+27.5k] (+16.6k) | +18.4k | +3.8k | +2.2k | +25.2k / +15.3k / +10.7k / +8.4k | 129 vs 129 | +0.07 (+0.34) | +3.56 vs +3.47 | +4.10 vs +3.21 | +7.5k | +5.4k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | +4.9k | +3.0k [-0.8k..+6.5k] (+7.4k) | +2.8k | -0.7k | -1.0k | +9.9k / +6.7k / +3.5k / +4.6k | 128 vs 129 | +3.16 (+4.91) | +3.46 vs -1.07 | +4.28 vs +4.10 | +1.3k | +2.4k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | +5.4k | +3.6k [-0.4k..+6.7k] (+7.1k) | +3.3k | -0.4k | -0.6k | +9.3k / +6.5k / +3.5k / +4.6k | 127 vs 128 | +3.27 (+4.88) | +3.46 vs -1.18 | +3.98 vs +3.77 | +1.5k | +3.1k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | +3.6k | +3.4k [-1.1k..+7.4k] (+7.5k) | +3.1k | -0.6k | -0.6k | +10.2k / +6.8k / +3.6k / +4.5k | 127 vs 128 | n/a | n/a | +3.97 vs +3.77 | +1.4k | +3.8k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | +28.9k | +8.5k [-16.6k..+35.6k] (+40.5k) | +10.1k | -9.2k | +6.5k | +55.1k / +36.5k / +25.5k / +26.3k | 139 vs 129 | +0.79 raw / +1.40 risk-matched (MDE +1.06) | +4.92 vs +3.56 | +4.70 vs +4.10 | +3.6k | +8.6k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | +8.2k | +3.1k [-4.5k..+11.4k] (+9.4k) | +2.8k | -1.6k | +0.8k | +14.3k / +8.4k / +6.8k / +5.9k | 127 vs 129 | +0.31 raw / +0.27 risk-matched (MDE +0.42) | +3.74 vs +3.56 | +4.25 vs +4.10 | +1.3k | +1.4k |
| first-stop cut 50%, stopped book entered in Asia | S73 | +11.9k | +13.2k [-4.4k..+32.5k] (+23.1k) | +11.4k | +2.0k | +2.8k | +29.0k / +20.8k / +13.9k / +12.9k | 147 vs 129 (14 cuts/wk) | +0.17 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +4.20 vs +4.10 | +5.6k | +9.1k |
| first-stop cut 50%, pooled (all sessions) | S73 | +16.0k | +6.6k [-12.1k..+27.1k] (+26.8k) | +4.6k | -6.5k | -0.4k | +35.1k / +24.0k / +16.0k / +17.6k | 150 vs 129 (15 cuts/wk) | -0.10 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +3.83 vs +4.10 | +2.8k | +4.3k |
| first-stop cut 100%, Asia | S73 | +14.9k | +11.8k [-10.8k..+35.6k] (+34.5k) | +9.9k | +5.3k | +2.2k | +44.3k / +30.6k / +17.9k / +18.1k | 145 vs 129 (13 cuts/wk) | +0.23 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +4.21 vs +4.10 | +5.0k | +5.5k |
| first-stop cut 25%, Asia | S73 | +5.1k | +8.8k [-5.1k..+23.5k] (+18.3k) | +7.6k | -1.2k | +2.6k | +26.2k / +16.6k / +11.6k / +9.8k | 144 vs 129 (14 cuts/wk) | +0.08 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +4.07 vs +4.10 | +3.7k | +7.0k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | +4.5k | +3.5k [-8.7k..+17.9k] (+20.2k) | +3.5k | -0.4k | +3.5k | +26.4k / +17.7k / +9.9k / +11.9k | 141 vs 129 (14 cuts/wk) | +0.01 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +3.93 vs +4.10 | +1.5k | +5.4k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | +5.5k | +6.8k [-6.2k..+21.6k] (+19.7k) | +6.5k | +4.5k | +4.7k | +28.2k / +17.3k / +9.8k / +8.6k | 139 vs 129 (14 cuts/wk) | +0.19 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +4.12 vs +4.10 | +2.9k | +7.7k |
| first-stop cut 50%, <=2 other books open | S73 | +10.8k | -0.2k [-15.4k..+17.0k] (+18.4k) | +0.5k | +1.6k | -1.8k | +30.8k / +16.2k / +9.5k / +7.3k | 140 vs 129 (14 cuts/wk) | +0.01 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +3.78 vs +4.10 | -0.1k | +2.9k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | +0.1k | +0.9k [-5.6k..+7.4k] (+13.7k) | +0.6k | +3.6k | +0.9k | +16.9k / +12.6k / +10.7k / +11.1k | 134 vs 129 (13 cuts/wk) | +0.04 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +3.98 vs +4.10 | +0.4k | -0.2k |
| first-stop cut 50%, a book open on the other side | S73 | +3.3k | +4.8k [-4.4k..+14.2k] (+15.6k) | +4.6k | +2.8k | +4.2k | +16.7k / +14.3k / +9.0k / +12.2k | 135 vs 129 (13 cuts/wk) | +0.13 (same-trade, pre-lock) | n/a (position changes in time; see lock-engine column) | +4.15 vs +4.10 | +2.0k | +3.6k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | +30.1k | +15.4k [-2.8k..+32.1k] (+26.1k) | +12.4k | +1.6k | +4.9k | +31.3k / +29.7k / +20.1k / +22.6k | 119 vs 129 | +0.43 raw / +0.96 risk-matched (MDE +0.91) | +4.64 vs +3.56 | +5.34 vs +4.10 | +6.6k | +3.9k |
| 8-line skip, D=15 pts (S8) | S73 | +17.9k | +5.2k [-15.7k..+25.1k] (+26.3k) | +4.7k | +4.3k | +5.4k | +36.4k / +28.6k / +16.9k / +20.4k | 119 vs 129 | +0.20 raw / +0.54 risk-matched (MDE +0.64) | +4.18 vs +3.56 | +4.76 vs +4.10 | +2.2k | +0.3k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | -0.9k | +3.7k [-7.4k..+14.3k] (+18.3k) | +3.2k | +3.3k | -2.6k | +31.7k / +16.4k / +10.2k / +10.6k | 135 vs 129 | -0.08 raw / +0.05 risk-matched (MDE +0.44) | +3.67 vs +3.56 | +4.27 vs +4.10 | +1.6k | +1.5k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | -9.8k | -0.8k [-14.7k..+14.4k] (+20.6k) | -2.1k | +6.5k | +1.6k | +27.4k / +18.1k / +12.2k / +16.5k | 135 vs 129 | -0.07 raw / -0.05 risk-matched (MDE +0.41) | +3.48 vs +3.56 | +3.94 vs +4.10 | -0.3k | -0.2k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | +4.3k | +5.6k [-2.9k..+14.6k] (+11.4k) | +4.5k | -3.9k | -3.0k | +24.2k / +10.4k / +8.4k / +5.0k | 127 vs 129 | +0.06 raw / +0.34 risk-matched (MDE +0.57) | +3.80 vs +3.56 | +4.46 vs +4.10 | +2.4k | +0.6k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | +18.6k | +9.3k [-1.7k..+19.0k] (+15.6k) | +6.5k | -1.3k | -1.6k | +18.3k / +15.6k / +10.7k / +12.1k | 127 vs 129 | +0.11 raw / +0.21 risk-matched (MDE +0.33) | +3.86 vs +3.56 | +4.68 vs +4.10 | +3.9k | +0.6k |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | S73 | +2.8k | +4.1k [+2.8k..+6.0k] (+2.9k) | +4.1k | +4.7k | +3.0k | +2.5k / +2.5k / +1.8k / +0.5k | 128 vs 129 | n/a (execution cost, no signal change) | n/a | +3.61 vs +3.39 | +1.7k | +1.5k |
| stop-join: ST+HM stop cost 0.5 (the fix target) | S73 | +6.9k | +7.3k [+4.0k..+11.3k] (+5.9k) | +7.3k | +6.8k | +5.0k | +10.8k / +5.2k / +2.1k / +0.8k | 128 vs 129 | n/a (execution cost, no signal change) | n/a | +3.77 vs +3.39 | +3.1k | +2.7k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | +17.6k | -14.7k [-56.3k..+24.0k] (+56.5k) | -9.4k | -19.7k | -9.5k | +69.1k / +57.4k / +33.5k / +32.5k | 73 vs 129 | -0.81 raw / +3.31 risk-matched (MDE +2.20) | +6.77 vs +3.56 | +5.90 vs +4.10 | -6.2k | -7.2k |

## 2. Governors: planned-lot R vs sized-lot R (every sizer; day locks x the book's largest multiplier of the day, week lock x the week's; identity-tested: with all multipliers 1 the sized engine equals the planned engine to the dollar)
Sizer lines, reference S73 (live line), basis N, research lots, $/wk stack delta [windows L3M / L6M / HOLD / PRE / X'] and MDE L6M. Skips and cuts have multiplier 1 on every kept row, so planned = sized by construction (not run). "eqr" = equal-risk rescale (scalar fitted on PRE+X' only so total lots are unchanged); "as coded" = the 1.5/0.5 pair as is (mean lot factor shown).
| sizer | ref | scale | governors | L3M | L6M | HOLD | PRE | X' | MDE L6M | sign-stable L6M+HOLD+PRE+X'? |
|---|---|---|---|---|---|---|---|---|---|---|
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | as coded | planned-lot R | +28.9k | +8.5k | +10.1k | -9.2k | +6.5k | +40.5k | no |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | as coded | sized-lot R | +43.0k | +37.3k | +32.8k | +11.2k | -0.7k | +52.6k | no |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | equal-risk | planned-lot R | +29.2k | +10.0k | +11.9k | -13.0k | +7.3k | +40.2k | no |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | equal-risk | sized-lot R | +51.8k | +51.1k | +44.7k | +19.9k | +1.4k | +58.3k | yes |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | as coded | planned-lot R | +52.7k | +17.3k | +19.8k | -7.4k | +7.5k | +48.3k | no |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | as coded | sized-lot R | +63.9k | +49.8k | +43.3k | +7.1k | +4.5k | +57.6k | yes |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | equal-risk | planned-lot R | +51.4k | +18.4k | +19.2k | -15.3k | +11.5k | +47.9k | no |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | equal-risk | sized-lot R | +72.9k | +63.1k | +54.2k | +14.9k | +7.0k | +63.0k | yes |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | as coded | planned-lot R | +8.2k | +3.1k | +2.8k | -1.6k | +0.8k | +9.4k | no |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | as coded | sized-lot R | +10.9k | +8.1k | +6.5k | +3.4k | +2.3k | +12.2k | yes |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | equal-risk | planned-lot R | +8.1k | +1.7k | +0.8k | -0.3k | +0.6k | +8.9k | no |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | equal-risk | sized-lot R | +10.0k | +6.6k | +5.3k | +2.3k | +2.4k | +11.4k | yes |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | as coded | planned-lot R | +12.2k | +3.5k | +3.3k | -2.9k | +2.3k | +11.6k | no |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | as coded | sized-lot R | +9.2k | +8.0k | +6.4k | +2.5k | +1.9k | +11.7k | yes |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | equal-risk | planned-lot R | +11.2k | +3.2k | +2.3k | -3.1k | +1.6k | +10.4k | no |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | equal-risk | sized-lot R | +8.8k | +6.2k | +5.0k | +1.0k | +1.7k | +11.0k | yes |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | as coded | planned-lot R | -0.9k | +3.7k | +3.2k | +3.3k | -2.6k | +18.3k | no |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | as coded | sized-lot R | -10.9k | -4.4k | -3.7k | +6.9k | -3.6k | +21.1k | no |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | equal-risk | planned-lot R | +0.2k | +7.4k | +6.4k | +1.1k | +0.3k | +18.7k | yes |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | equal-risk | sized-lot R | -10.0k | -1.1k | -0.9k | +9.9k | -2.9k | +21.2k | no |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | as coded | planned-lot R | +0.3k | +1.2k | +2.2k | +2.4k | -0.3k | +17.8k | no |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | as coded | sized-lot R | -7.4k | -6.9k | -4.5k | +5.3k | -1.2k | +19.5k | no |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | equal-risk | planned-lot R | +4.4k | +3.8k | +4.6k | +0.8k | +2.5k | +21.9k | yes |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | equal-risk | sized-lot R | -7.2k | -4.5k | -2.6k | +8.1k | -0.5k | +19.1k | no |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | as coded | planned-lot R | -9.8k | -0.8k | -2.1k | +6.5k | +1.6k | +20.6k | no |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | as coded | sized-lot R | -16.0k | +0.5k | +1.3k | +7.3k | +3.2k | +28.3k | yes |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | equal-risk | planned-lot R | -6.0k | +1.1k | -1.9k | +6.4k | +1.1k | +19.7k | no |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | equal-risk | sized-lot R | -15.8k | +1.8k | +2.4k | +8.5k | +3.6k | +28.8k | yes |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | as coded | planned-lot R | +2.6k | +4.7k | +3.3k | +8.6k | +0.5k | +23.6k | yes |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | as coded | sized-lot R | -7.5k | +3.6k | +6.6k | +7.0k | +2.1k | +28.7k | yes |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | equal-risk | planned-lot R | +6.5k | +5.0k | +3.7k | +5.8k | +1.8k | +24.3k | yes |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | equal-risk | sized-lot R | -7.4k | +4.7k | +7.5k | +8.1k | +2.4k | +29.1k | yes |

Reading: for every sizer the answer depends on the governor definition. The sized-lot-R governor lets the up-sized day run (ER20 sizer: planned L6M +8.5k, sized +37.3k; KB ER0.2: +3.1k vs +8.1k). The same convention question decides the sign of the ES-lead rows. D6 must say which one it implements; until then the planned-lot column is the one that reproduces what the lock engine of every other number in the brief does.

## 3. Bases N / M / LIVE-CAL / LIVE-JOIN (reference S73 unless stated; research lots; planned-lot R; as coded)
N = no target-fill correction, stop 1.01; M = measured (target-fill corrected, entry cost by year); LIVE-CAL = N with the stop exit at 2.45 pts (live join measured); LIVE-NATIVE = same with ST+HM stops at 1.28 (Native stop-market), other books 2.45; LIVE-FIXED = ST+HM stops at 0.5 (the fix target). For the stop-join rows the "reference" is the join (2.45) and the rule is Native / fixed on the same signals, so only the LIVE basis exists.
| candidate | ref | basis | L3M | L6M | HOLD | PRE | X' | MDE L6M |
|---|---|---|---|---|---|---|---|---|
| 70/30 split (S73 vs market) | MKT | N | +20.2k | +17.6k | +18.4k | +3.8k | +2.2k | +16.6k |
| 70/30 split (S73 vs market) | MKT | M | +9.3k | +13.3k | +11.6k | +7.6k | +2.8k | +14.5k |
| 70/30 split (S73 vs market) | MKT | LIVE | +16.1k | +15.1k | +16.0k | +3.8k | +2.5k | +15.8k |
| 70/30 split (S73 vs market) | MKT | LIVE_native | +13.3k | +14.6k | +15.8k | +3.7k | +2.4k | +17.1k |
| 70/30 split (S73 vs market) | MKT | LIVE_fixed | +11.4k | +13.5k | +14.8k | +3.2k | +2.5k | +19.1k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | N | +4.9k | +3.0k | +2.8k | -0.7k | -1.0k | +7.4k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | M | +6.0k | +3.4k | +3.3k | -0.2k | -0.8k | +6.8k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | LIVE | +3.8k | +2.4k | +2.3k | -0.6k | -1.2k | +7.3k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | LIVE_native | +3.8k | +2.4k | +2.3k | -0.6k | -1.2k | +7.3k |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | LIVE_fixed | +3.8k | +2.4k | +2.3k | -0.6k | -1.2k | +7.3k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | N | +5.4k | +3.6k | +3.3k | -0.4k | -0.6k | +7.1k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | M | +4.8k | +2.6k | +2.6k | -0.1k | -0.5k | +6.7k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | LIVE | +4.3k | +3.0k | +2.8k | -0.3k | -0.8k | +7.1k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | LIVE_native | +4.3k | +3.0k | +2.8k | -0.3k | -0.8k | +7.1k |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | LIVE_fixed | +4.3k | +3.0k | +2.8k | -0.3k | -0.8k | +7.1k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | N | +3.6k | +3.4k | +3.1k | -0.6k | -0.6k | +7.5k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | M | +3.1k | +2.2k | +2.3k | -0.3k | -0.5k | +7.2k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | LIVE | +3.6k | +3.0k | +2.8k | -0.5k | -0.6k | +7.5k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | LIVE_native | +3.6k | +3.0k | +2.8k | -0.5k | -0.6k | +7.5k |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | LIVE_fixed | +3.6k | +3.0k | +2.8k | -0.5k | -0.6k | +7.5k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | N | +28.9k | +8.5k | +10.1k | -9.2k | +6.5k | +40.5k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | M | +40.0k | +13.1k | +15.4k | -3.8k | +7.6k | +43.0k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | LIVE | +37.0k | +14.0k | +15.1k | -8.6k | +7.9k | +41.3k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | LIVE_native | +36.8k | +12.8k | +14.0k | -9.4k | +7.9k | +42.0k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | LIVE_fixed | +34.9k | +11.6k | +12.9k | -9.5k | +7.3k | +41.1k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | N | +52.7k | +17.3k | +19.8k | -7.4k | +7.5k | +48.3k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | M | +43.5k | +17.1k | +17.6k | -2.2k | +9.5k | +44.9k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | LIVE | +53.6k | +17.0k | +19.5k | -8.2k | +9.0k | +47.7k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | LIVE_native | +51.2k | +16.3k | +19.1k | -8.2k | +8.5k | +48.7k |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | MKT | LIVE_fixed | +50.6k | +15.9k | +18.7k | -8.1k | +8.3k | +49.3k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | N | +8.2k | +3.1k | +2.8k | -1.6k | +0.8k | +9.4k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | M | +13.1k | +5.4k | +5.1k | -0.4k | +0.7k | +9.7k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | LIVE | +11.4k | +4.7k | +3.9k | -1.2k | +0.8k | +9.4k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | LIVE_native | +11.4k | +4.7k | +3.9k | -1.2k | +0.8k | +9.4k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | LIVE_fixed | +11.4k | +4.7k | +3.9k | -1.2k | +0.8k | +9.4k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | N | +12.2k | +3.5k | +3.3k | -2.9k | +2.3k | +11.6k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | M | +15.1k | +7.2k | +6.9k | -0.9k | +2.5k | +10.6k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | LIVE | +10.0k | +2.6k | +2.5k | -2.6k | +2.6k | +11.7k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | LIVE_native | +10.0k | +2.6k | +2.5k | -2.6k | +2.6k | +11.7k |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | MKT | LIVE_fixed | +10.0k | +2.6k | +2.5k | -2.6k | +2.6k | +11.7k |
| first-stop cut 50%, stopped book entered in Asia | S73 | N | +11.9k | +13.2k | +11.4k | +2.0k | +2.8k | +23.1k |
| first-stop cut 50%, stopped book entered in Asia | S73 | M | +1.5k | +7.8k | +7.1k | +0.9k | +2.9k | +21.2k |
| first-stop cut 50%, stopped book entered in Asia | S73 | LIVE | +4.6k | +9.0k | +8.3k | +0.7k | +2.1k | +20.5k |
| first-stop cut 50%, stopped book entered in Asia | S73 | LIVE_native | +7.8k | +9.1k | +8.0k | +0.6k | +1.6k | +20.0k |
| first-stop cut 50%, stopped book entered in Asia | S73 | LIVE_fixed | +13.2k | +12.9k | +11.3k | +1.9k | +1.5k | +24.3k |
| first-stop cut 50%, stopped book entered in Asia | MKT | N | +17.5k | +20.2k | +16.5k | +0.9k | +3.7k | +26.3k |
| first-stop cut 50%, stopped book entered in Asia | MKT | M | +6.3k | +11.5k | +8.1k | +2.0k | +4.7k | +19.0k |
| first-stop cut 50%, stopped book entered in Asia | MKT | LIVE | +15.3k | +17.7k | +14.6k | -0.0k | +3.5k | +21.8k |
| first-stop cut 50%, stopped book entered in Asia | MKT | LIVE_native | +13.9k | +17.7k | +14.5k | +0.3k | +3.0k | +23.7k |
| first-stop cut 50%, stopped book entered in Asia | MKT | LIVE_fixed | +15.1k | +19.1k | +15.7k | +0.7k | +1.8k | +25.0k |
| first-stop cut 50%, pooled (all sessions) | S73 | N | +16.0k | +6.6k | +4.6k | -6.5k | -0.4k | +26.8k |
| first-stop cut 50%, pooled (all sessions) | S73 | M | +1.9k | +4.3k | +1.5k | -8.1k | -1.3k | +22.7k |
| first-stop cut 50%, pooled (all sessions) | S73 | LIVE | +13.7k | +6.7k | +5.4k | -6.8k | -0.2k | +23.7k |
| first-stop cut 50%, pooled (all sessions) | S73 | LIVE_native | +14.5k | +4.7k | +3.2k | -6.2k | -1.1k | +24.2k |
| first-stop cut 50%, pooled (all sessions) | S73 | LIVE_fixed | +18.5k | +7.9k | +6.1k | -5.8k | -1.7k | +28.0k |
| first-stop cut 50%, pooled (all sessions) | MKT | N | +35.7k | +23.0k | +19.3k | -8.2k | +0.7k | +28.5k |
| first-stop cut 50%, pooled (all sessions) | MKT | M | +8.6k | +6.8k | +2.1k | -6.6k | +1.2k | +24.0k |
| first-stop cut 50%, pooled (all sessions) | MKT | LIVE | +29.6k | +20.6k | +17.7k | -6.4k | +1.4k | +25.7k |
| first-stop cut 50%, pooled (all sessions) | MKT | LIVE_native | +27.9k | +19.3k | +16.4k | -5.9k | +1.5k | +26.2k |
| first-stop cut 50%, pooled (all sessions) | MKT | LIVE_fixed | +23.2k | +17.0k | +14.4k | -6.2k | +1.0k | +25.6k |
| first-stop cut 100%, Asia | S73 | N | +14.9k | +11.8k | +9.9k | +5.3k | +2.2k | +34.5k |
| first-stop cut 100%, Asia | S73 | M | -1.1k | +2.9k | +2.9k | +6.6k | +1.9k | +31.4k |
| first-stop cut 100%, Asia | S73 | LIVE | +13.5k | +11.5k | +10.6k | +6.6k | +3.1k | +33.7k |
| first-stop cut 100%, Asia | S73 | LIVE_native | +16.0k | +11.9k | +10.4k | +5.7k | +2.6k | +33.5k |
| first-stop cut 100%, Asia | S73 | LIVE_fixed | +19.2k | +13.3k | +11.6k | +6.1k | +2.2k | +33.9k |
| first-stop cut 100%, Asia | MKT | N | +11.1k | +12.5k | +9.8k | +1.4k | +3.0k | +37.1k |
| first-stop cut 100%, Asia | MKT | M | +8.3k | +10.6k | +8.5k | +3.7k | +2.7k | +32.4k |
| first-stop cut 100%, Asia | MKT | LIVE | +12.9k | +15.1k | +13.1k | +3.6k | +4.4k | +36.6k |
| first-stop cut 100%, Asia | MKT | LIVE_native | +10.7k | +13.5k | +11.8k | +1.7k | +4.1k | +37.5k |
| first-stop cut 100%, Asia | MKT | LIVE_fixed | +14.4k | +14.7k | +12.4k | +1.2k | +4.0k | +36.5k |
| first-stop cut 25%, Asia | S73 | N | +5.1k | +8.8k | +7.6k | -1.2k | +2.6k | +18.3k |
| first-stop cut 25%, Asia | S73 | M | -7.0k | +0.2k | -0.3k | -2.0k | +2.1k | +14.4k |
| first-stop cut 25%, Asia | S73 | LIVE | +8.4k | +9.2k | +7.6k | -1.5k | -0.0k | +17.8k |
| first-stop cut 25%, Asia | S73 | LIVE_native | +5.5k | +9.1k | +7.5k | -0.8k | +0.3k | +19.8k |
| first-stop cut 25%, Asia | S73 | LIVE_fixed | +9.0k | +9.5k | +7.9k | -1.4k | +0.4k | +19.5k |
| first-stop cut 25%, Asia | MKT | N | +6.0k | +12.8k | +10.2k | -2.2k | +3.7k | +19.4k |
| first-stop cut 25%, Asia | MKT | M | -0.1k | +6.1k | +3.7k | -0.3k | +3.5k | +16.2k |
| first-stop cut 25%, Asia | MKT | LIVE | +4.7k | +10.6k | +8.1k | +1.2k | +0.1k | +16.2k |
| first-stop cut 25%, Asia | MKT | LIVE_native | +3.5k | +10.4k | +7.9k | -0.2k | +1.1k | +17.0k |
| first-stop cut 25%, Asia | MKT | LIVE_fixed | +2.9k | +11.3k | +8.2k | -0.7k | +2.2k | +16.5k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | N | +4.5k | +3.5k | +3.5k | -0.4k | +3.5k | +20.2k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | M | -1.6k | +1.0k | -0.4k | -0.7k | +2.6k | +19.8k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | LIVE | +3.2k | +1.8k | +2.1k | +0.2k | +2.6k | +17.4k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | LIVE_native | +4.2k | +1.4k | +1.6k | +0.5k | +2.1k | +17.5k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | LIVE_fixed | +6.6k | +3.9k | +3.9k | +0.7k | +1.9k | +22.2k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | N | +16.3k | +12.4k | +10.8k | +0.3k | +4.7k | +19.5k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | M | +0.1k | +4.2k | +1.5k | -1.5k | +4.1k | +14.9k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | LIVE | +8.4k | +8.0k | +6.9k | +0.2k | +4.2k | +16.8k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | LIVE_native | +8.0k | +7.7k | +6.7k | +1.6k | +4.4k | +15.8k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | LIVE_fixed | +3.2k | +5.8k | +5.1k | +1.1k | +4.2k | +16.8k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | N | +5.5k | +6.8k | +6.5k | +4.5k | +4.7k | +19.7k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | M | +2.0k | +5.1k | +4.8k | +5.0k | +4.8k | +19.6k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | LIVE | +2.0k | +4.9k | +4.8k | +3.3k | +4.5k | +18.3k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | LIVE_native | +2.3k | +3.6k | +3.6k | +4.1k | +3.6k | +18.0k |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | LIVE_fixed | +5.8k | +6.5k | +6.2k | +4.3k | +3.2k | +23.0k |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | N | +9.8k | +12.4k | +10.2k | +3.6k | +6.1k | +21.6k |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | M | +5.6k | +8.6k | +6.8k | +3.9k | +6.5k | +14.9k |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | LIVE | +7.8k | +10.2k | +8.3k | +2.1k | +5.8k | +17.4k |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | LIVE_native | +9.0k | +10.9k | +8.9k | +3.0k | +4.8k | +19.1k |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | LIVE_fixed | +7.0k | +10.7k | +8.8k | +3.9k | +3.4k | +21.5k |
| first-stop cut 50%, <=2 other books open | S73 | N | +10.8k | -0.2k | +0.5k | +1.6k | -1.8k | +18.4k |
| first-stop cut 50%, <=2 other books open | S73 | M | +11.0k | +3.6k | +1.9k | -1.7k | -3.0k | +17.1k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE | +4.3k | -0.6k | +0.3k | +1.0k | -2.1k | +16.5k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE_native | +5.0k | -2.3k | -1.3k | +1.2k | -2.4k | +17.4k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE_fixed | +8.9k | -0.5k | +0.3k | +0.7k | -2.4k | +20.9k |
| first-stop cut 50%, <=2 other books open | MKT | N | +22.3k | +11.5k | +11.9k | +2.4k | +1.6k | +19.0k |
| first-stop cut 50%, <=2 other books open | MKT | M | +13.0k | +4.9k | +3.5k | -0.2k | +0.0k | +14.1k |
| first-stop cut 50%, <=2 other books open | MKT | LIVE | +14.3k | +8.3k | +9.0k | +0.2k | -0.2k | +16.0k |
| first-stop cut 50%, <=2 other books open | MKT | LIVE_native | +14.4k | +7.5k | +8.6k | +1.5k | +0.4k | +17.3k |
| first-stop cut 50%, <=2 other books open | MKT | LIVE_fixed | +9.9k | +4.7k | +6.1k | +1.9k | +1.7k | +14.9k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | N | +0.1k | +0.9k | +0.6k | +3.6k | +0.9k | +13.7k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | M | +7.2k | +7.2k | +5.3k | +2.4k | +2.9k | +10.8k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | LIVE | +5.2k | +4.8k | +3.8k | +1.0k | +1.0k | +12.3k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | LIVE_native | +0.6k | +0.8k | +0.6k | +2.8k | +0.9k | +12.8k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | LIVE_fixed | +0.7k | +0.8k | +0.7k | +2.9k | +0.8k | +12.8k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | N | +8.0k | +7.4k | +5.5k | +2.7k | +1.9k | +11.4k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | M | +3.7k | +4.0k | +0.8k | +2.0k | +2.7k | +9.9k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | LIVE | +5.4k | +5.8k | +2.9k | +2.6k | +1.1k | +9.7k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | LIVE_native | +3.7k | +5.3k | +2.8k | +2.4k | +1.5k | +9.8k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | LIVE_fixed | +4.3k | +5.5k | +3.8k | +4.1k | +1.4k | +10.4k |
| first-stop cut 50%, a book open on the other side | S73 | N | +3.3k | +4.8k | +4.6k | +2.8k | +4.2k | +15.6k |
| first-stop cut 50%, a book open on the other side | S73 | M | +4.9k | +6.2k | +5.3k | +1.2k | +4.0k | +11.7k |
| first-stop cut 50%, a book open on the other side | S73 | LIVE | +3.8k | +5.2k | +5.5k | +1.8k | +1.8k | +15.2k |
| first-stop cut 50%, a book open on the other side | S73 | LIVE_native | +3.7k | +4.7k | +4.8k | +0.9k | +3.8k | +15.5k |
| first-stop cut 50%, a book open on the other side | S73 | LIVE_fixed | +5.2k | +5.3k | +5.4k | +1.4k | +4.2k | +15.7k |
| first-stop cut 50%, a book open on the other side | MKT | N | -2.8k | +4.0k | +4.3k | +4.4k | +4.4k | +13.1k |
| first-stop cut 50%, a book open on the other side | MKT | M | +4.3k | +5.7k | +5.3k | +2.9k | +3.6k | +12.5k |
| first-stop cut 50%, a book open on the other side | MKT | LIVE | +1.6k | +6.1k | +6.2k | +2.0k | +2.3k | +13.8k |
| first-stop cut 50%, a book open on the other side | MKT | LIVE_native | -1.0k | +4.9k | +5.4k | +2.1k | +3.1k | +13.0k |
| first-stop cut 50%, a book open on the other side | MKT | LIVE_fixed | +0.8k | +5.8k | +6.2k | +1.8k | +4.6k | +13.3k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | N | +30.1k | +15.4k | +12.4k | +1.6k | +4.9k | +26.1k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | M | +43.2k | +24.8k | +22.5k | +1.9k | +6.1k | +28.6k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | LIVE | +36.8k | +19.8k | +16.4k | +3.4k | +5.9k | +28.2k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | LIVE_native | +33.1k | +17.7k | +14.5k | +2.4k | +5.8k | +26.5k |
| 8-line skip, fresh line within 20 pts (S8) | S73 | LIVE_fixed | +29.9k | +15.9k | +12.9k | +3.1k | +5.5k | +25.9k |
| 8-line skip, fresh line within 20 pts (S8) | MKT | N | +37.8k | +21.9k | +19.0k | +0.9k | +5.2k | +29.9k |
| 8-line skip, fresh line within 20 pts (S8) | MKT | M | +43.3k | +28.8k | +25.3k | +6.2k | +7.5k | +29.7k |
| 8-line skip, fresh line within 20 pts (S8) | MKT | LIVE | +39.4k | +22.4k | +19.4k | +3.3k | +7.0k | +29.2k |
| 8-line skip, fresh line within 20 pts (S8) | MKT | LIVE_native | +36.3k | +21.6k | +18.9k | +1.6k | +6.4k | +29.4k |
| 8-line skip, fresh line within 20 pts (S8) | MKT | LIVE_fixed | +32.0k | +19.2k | +16.8k | +1.1k | +6.2k | +29.0k |
| 8-line skip, D=15 pts (S8) | S73 | N | +17.9k | +5.2k | +4.7k | +4.3k | +5.4k | +26.3k |
| 8-line skip, D=15 pts (S8) | S73 | M | +27.2k | +13.9k | +14.1k | +5.2k | +6.3k | +26.3k |
| 8-line skip, D=15 pts (S8) | S73 | LIVE | +21.7k | +8.3k | +7.6k | +5.5k | +6.2k | +26.8k |
| 8-line skip, D=15 pts (S8) | S73 | LIVE_native | +21.1k | +7.7k | +7.0k | +4.4k | +6.0k | +26.6k |
| 8-line skip, D=15 pts (S8) | S73 | LIVE_fixed | +18.4k | +6.2k | +5.7k | +4.5k | +5.8k | +26.3k |
| 8-line skip, D=15 pts (S8) | MKT | N | +24.8k | +12.3k | +11.9k | +2.3k | +5.1k | +29.0k |
| 8-line skip, D=15 pts (S8) | MKT | M | +27.9k | +18.8k | +17.7k | +5.5k | +7.4k | +25.7k |
| 8-line skip, D=15 pts (S8) | MKT | LIVE | +26.9k | +13.8k | +13.1k | +3.6k | +6.6k | +28.6k |
| 8-line skip, D=15 pts (S8) | MKT | LIVE_native | +23.8k | +11.9k | +11.7k | +2.2k | +6.1k | +29.5k |
| 8-line skip, D=15 pts (S8) | MKT | LIVE_fixed | +19.6k | +9.6k | +9.7k | +1.8k | +5.9k | +29.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | N | -0.9k | +3.7k | +3.2k | +3.3k | -2.6k | +18.3k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | -3.5k | -1.1k | -0.9k | -1.6k | -3.2k | +17.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE | +2.5k | +6.2k | +5.3k | +4.0k | -2.9k | +17.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_native | +3.0k | +5.5k | +4.8k | +3.7k | -2.9k | +17.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_fixed | +0.5k | +3.8k | +3.2k | +3.4k | -2.9k | +17.4k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | +0.3k | +1.2k | +2.2k | +2.4k | -0.3k | +17.8k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | +0.5k | +0.8k | +0.1k | +1.2k | -0.6k | +15.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | +2.3k | +2.7k | +3.2k | +2.8k | -0.3k | +17.0k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | +1.5k | +2.1k | +3.0k | +2.1k | -0.3k | +17.9k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | +0.7k | +1.7k | +2.7k | +2.8k | -0.3k | +17.6k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | N | -9.8k | -0.8k | -2.1k | +6.5k | +1.6k | +20.6k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | -1.4k | +0.7k | -0.2k | +4.9k | +2.7k | +21.4k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE | -4.8k | +3.4k | +1.3k | +8.7k | +2.1k | +20.7k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE_native | -6.0k | +1.1k | -0.8k | +8.0k | +2.1k | +21.0k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE_fixed | -6.9k | +0.5k | -1.3k | +7.5k | +2.5k | +21.1k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | N | +2.6k | +4.7k | +3.3k | +8.6k | +0.5k | +23.6k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | -10.9k | -1.7k | -3.0k | +4.6k | +0.4k | +22.8k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | LIVE | +3.0k | +5.2k | +3.4k | +7.9k | -0.1k | +23.9k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | LIVE_native | +2.1k | +4.6k | +3.2k | +7.6k | -0.1k | +23.8k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | LIVE_fixed | +1.1k | +4.1k | +2.8k | +7.4k | -0.1k | +23.8k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | N | +4.3k | +5.6k | +4.5k | -3.9k | -3.0k | +11.4k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | M | +9.4k | +7.6k | +6.9k | -4.9k | -2.9k | +14.5k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | LIVE | +6.3k | +7.0k | +5.7k | -4.8k | -2.8k | +12.5k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | LIVE_native | +7.0k | +6.4k | +5.2k | -4.1k | -2.8k | +12.5k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | LIVE_fixed | +5.2k | +5.6k | +4.5k | -4.0k | -2.8k | +11.9k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | MKT | N | +14.9k | +11.3k | +9.5k | -5.4k | -2.3k | +15.0k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | MKT | M | +8.0k | +7.0k | +6.3k | -3.0k | -1.0k | +13.7k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | MKT | LIVE | +15.2k | +10.9k | +9.2k | -3.6k | -1.9k | +14.2k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | MKT | LIVE_native | +14.1k | +10.4k | +8.8k | -3.7k | -2.0k | +15.0k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | MKT | LIVE_fixed | +11.3k | +9.0k | +7.5k | -4.1k | -2.0k | +13.7k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | N | +18.6k | +9.3k | +6.5k | -1.3k | -1.6k | +15.6k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | M | +19.1k | +9.3k | +7.3k | +0.6k | -1.9k | +15.7k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE | +18.9k | +9.7k | +6.9k | -0.5k | -1.3k | +15.7k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE_native | +18.7k | +9.3k | +6.5k | -1.3k | -1.5k | +15.6k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE_fixed | +18.7k | +9.3k | +6.4k | -1.5k | -1.7k | +15.6k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | N | +24.8k | +11.8k | +9.1k | -1.6k | -0.4k | +16.0k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | M | +22.2k | +11.5k | +9.1k | -0.5k | +1.1k | +16.5k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE | +26.3k | +12.4k | +9.7k | -0.7k | -0.2k | +16.9k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE_native | +25.7k | +12.3k | +9.6k | -1.2k | -0.4k | +16.3k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE_fixed | +24.7k | +11.7k | +9.0k | -1.7k | -0.5k | +15.9k |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | S73 | LIVE | +2.8k | +4.1k | +4.1k | +4.7k | +3.0k | +2.9k |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | MKT | LIVE | +5.6k | +4.7k | +4.3k | +4.8k | +3.0k | +2.8k |
| stop-join: ST+HM stop cost 0.5 (the fix target) | S73 | LIVE | +6.9k | +7.3k | +7.3k | +6.8k | +5.0k | +5.9k |
| stop-join: ST+HM stop cost 0.5 (the fix target) | MKT | LIVE | +11.6k | +8.9k | +8.4k | +7.5k | +5.0k | +5.3k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | N | +17.6k | -14.7k | -9.4k | -19.7k | -9.5k | +56.5k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | M | +39.0k | +5.9k | +11.7k | -9.1k | -5.2k | +59.9k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE | +26.3k | -7.2k | -2.1k | -14.4k | -5.3k | +57.1k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_native | +27.0k | -8.6k | -3.7k | -16.6k | -6.8k | +58.3k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_fixed | +24.5k | -10.3k | -5.4k | -17.4k | -7.8k | +57.3k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | N | +37.0k | +0.8k | +5.8k | -20.2k | -7.2k | +65.9k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | M | +46.7k | +17.3k | +21.2k | -7.5k | -0.9k | +59.2k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE | +43.3k | +6.4k | +11.2k | -14.6k | -2.6k | +64.0k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE_native | +41.1k | +4.4k | +9.4k | -17.2k | -4.1k | +66.1k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE_fixed | +36.4k | +1.4k | +6.5k | -18.3k | -5.1k | +65.8k |

## 4. Lots: research lots vs live lots (two live conventions) - mapping stated and checked
**Book-tag to research-book mapping** (checked against the D6 tag table in the reports and the user's own THP_POLICY format directive): K6 = KB (DS3_KB_REGIME: "K6 = KB", DIRECTIVE_THP_POLICYFMT: "K6 KB"); P6 = PE (THP_POLICYFMT "P6 PE"; DS3_ZONES_2_ADDENDUM, DS3_L2_UF_ENTRY_C7 use P6 = PE 7 lots; FOLLOWUP_BRIEF writes "PB3B"); U6 = SM (THP_POLICYFMT "U6 SM"; ZONES_2 addendum "U6 = SM 4"; FOLLOWUP_BRIEF has "U6=ST10m (SM? check)" which is the same book family: SM is the ST-10-min book); H6 = HM (user-confirmed DS6/H6); S6 = ST and W6 = WT (user-confirmed tags; not live -> research/2.35); MA6 = MA (not live, not in the six-book engine). **M6 = MV, A6 = PB7, O6 = no research book in the six-book lock engine (ST HM WT KB SM PE): they cannot be valued here and are NOT in any live-lot dollar below.** Caveats: the SIZING note in DECISIONS says the K6/P6/U6 list came from the ABR bundle, not from the user's 10-29 tag reply (that gave S6/W6/MA6/C6/H6 only); the later THP_POLICYFMT directive (user) lists K6 KB, P6 PE, U6 SM, so the mapping stands, but it is the one place a wrong tag would silently move live dollars.

| research book | D6 tag | research lots | live lots used by the engine | live sessions (lot 0 elsewhere) | live / research |
|---|---|---|---|---|---|
| ST | S6 | 10 | 4.26 (=10/2.35) | all | 0.43 |
| HM | H6 | 10 | 4 Asia / 2 NY-AM | Asia, NY-AM only | 0.40 / 0.20 |
| WT | W6 | 7 | 2.98 (=7/2.35) | all | 0.43 |
| KB | K6 | 5.2 | 2 | Asia, London, NY-AM, NY-PM | 0.38 |
| SM | U6 | 7.4 | 4 | Asia, London | 0.54 |
| PE | P6 | 5.6 | 7 | Asia, London, NY-AM | 1.25 |

Two live conventions: **A = research / 2.35** (the SP-1 mapping every earlier report used; pure scaling of the research-lot dollars, governors unchanged) and **B = engine run at the live lots** (book lots as above; HM 4 Asia / 2 NY-AM; sessions with live lot 0 dropped from the stack, so the live stack has fewer trades and its own governors in live-lot R; ST and WT at research/2.35 in every session; the base stack is recomputed on the same live convention, so the delta is rule minus base on live lots). B is the ZONES-2-addendum convention. Headline convention otherwise.
| candidate | ref | research L6M / HOLD / PRE / X' | A: /2.35 L6M / HOLD / PRE / X' | B: live-lot engine L6M / HOLD / PRE / X' | MDE (B) L6M | sign flips A->B |
|---|---|---|---|---|---|---|
| 70/30 split (S73 vs market) | MKT | +17.6k / +18.4k / +3.8k / +2.2k | +7.5k / +7.8k / +1.6k / +0.9k | +5.4k / +5.4k / +1.4k / +2.0k | +9.5k | - |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | +3.0k / +2.8k / -0.7k / -1.0k | +1.3k / +1.2k / -0.3k / -0.4k | +2.4k / +1.9k / -0.6k / +0.1k | +6.2k | X |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | +3.6k / +3.3k / -0.4k / -0.6k | +1.5k / +1.4k / -0.2k / -0.3k | +3.1k / +2.6k / -0.4k / +0.1k | +6.1k | X |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | +3.4k / +3.1k / -0.6k / -0.6k | +1.4k / +1.3k / -0.2k / -0.3k | +3.8k / +3.1k / -0.1k / -0.4k | +6.3k | - |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | +8.5k / +10.1k / -9.2k / +6.5k | +3.6k / +4.3k / -3.9k / +2.8k | +8.6k / +9.3k / -4.8k / +1.7k | +19.1k | - |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | +3.1k / +2.8k / -1.6k / +0.8k | +1.3k / +1.2k / -0.7k / +0.3k | +1.4k / +1.1k / -0.5k / +0.9k | +4.0k | - |
| first-stop cut 50%, stopped book entered in Asia | S73 | +13.2k / +11.4k / +2.0k / +2.8k | +5.6k / +4.8k / +0.9k / +1.2k | +9.1k / +9.1k / -0.8k / +2.7k | +14.6k | PRE |
| first-stop cut 50%, pooled (all sessions) | S73 | +6.6k / +4.6k / -6.5k / -0.4k | +2.8k / +2.0k / -2.7k / -0.2k | +4.3k / +4.1k / -3.9k / +1.3k | +16.9k | X |
| first-stop cut 100%, Asia | S73 | +11.8k / +9.9k / +5.3k / +2.2k | +5.0k / +4.2k / +2.3k / +0.9k | +5.5k / +6.3k / +2.3k / +2.4k | +17.4k | - |
| first-stop cut 25%, Asia | S73 | +8.8k / +7.6k / -1.2k / +2.6k | +3.7k / +3.2k / -0.5k / +1.1k | +7.0k / +7.2k / -2.0k / +2.2k | +13.7k | - |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | +3.5k / +3.5k / -0.4k / +3.5k | +1.5k / +1.5k / -0.2k / +1.5k | +5.4k / +4.9k / -1.5k / +2.6k | +13.0k | - |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | +6.8k / +6.5k / +4.5k / +4.7k | +2.9k / +2.7k / +1.9k / +2.0k | +7.7k / +7.2k / -0.3k / +3.1k | +13.0k | PRE |
| first-stop cut 50%, <=2 other books open | S73 | -0.2k / +0.5k / +1.6k / -1.8k | -0.1k / +0.2k / +0.7k / -0.8k | +2.9k / +3.8k / -1.3k / -0.3k | +12.6k | L6M, PRE |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | +0.9k / +0.6k / +3.6k / +0.9k | +0.4k / +0.3k / +1.6k / +0.4k | -0.2k / -0.0k / -0.7k / +2.7k | +7.8k | L6M, HOLD, PRE |
| first-stop cut 50%, a book open on the other side | S73 | +4.8k / +4.6k / +2.8k / +4.2k | +2.0k / +2.0k / +1.2k / +1.8k | +3.6k / +3.3k / +1.0k / +2.1k | +7.5k | - |
| 8-line skip, fresh line within 20 pts (S8) | S73 | +15.4k / +12.4k / +1.6k / +4.9k | +6.6k / +5.3k / +0.7k / +2.1k | +3.9k / +3.3k / +2.5k / +3.1k | +11.2k | - |
| 8-line skip, D=15 pts (S8) | S73 | +5.2k / +4.7k / +4.3k / +5.4k | +2.2k / +2.0k / +1.8k / +2.3k | +0.3k / -0.1k / +1.9k / +0.9k | +10.0k | HOLD |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | +3.7k / +3.2k / +3.3k / -2.6k | +1.6k / +1.4k / +1.4k / -1.1k | +1.5k / +1.0k / +1.5k / -1.7k | +7.8k | - |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | -0.8k / -2.1k / +6.5k / +1.6k | -0.3k / -0.9k / +2.8k / +0.7k | -0.2k / -0.3k / +3.8k / +2.2k | +9.3k | - |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | +5.6k / +4.5k / -3.9k / -3.0k | +2.4k / +1.9k / -1.7k / -1.3k | +0.6k / -0.0k / -1.9k / -1.5k | +5.7k | HOLD |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | +9.3k / +6.5k / -1.3k / -1.6k | +3.9k / +2.7k / -0.6k / -0.7k | +0.6k / -0.2k / -0.2k / +1.4k | +3.2k | HOLD, X |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | S73 | +4.1k / +4.1k / +4.7k / +3.0k | +1.7k / +1.8k / +2.0k / +1.3k | +1.5k / +1.5k / +1.5k / +1.0k | +1.2k | - |
| stop-join: ST+HM stop cost 0.5 (the fix target) | S73 | +7.3k / +7.3k / +6.8k / +5.0k | +3.1k / +3.1k / +2.9k / +2.1k | +2.7k / +2.7k / +2.2k / +1.7k | +2.5k | - |
| ER(20)>=0.3 as a skip (TG-1) | S73 | -14.7k / -9.4k / -19.7k / -9.5k | -6.2k / -4.0k / -8.4k / -4.1k | -7.2k / -5.3k / -8.1k / -5.0k | +27.8k | - |

## 5. Where does the L6M gain come from: re-entry / admit changes vs same-trade P&L, and how many weeks
Lock-engine decomposition of the L6M stack delta, headline convention ($/wk). **same** = rows admitted in both worlds (rule effect + path change on those trades); **re-entry in** = rows the lock engine admits only in the rule world; **out (rule-skipped)** = rows the rule itself removed (direct skip effect, skips only); **out (admit)** = rows admitted in the base but not in the rule world for lock-engine reasons. Re-entry share = re-entry in / total (the S2 number: 76% for the pooled cut, 17.4k of 23.0k); net admit share = (re-entry in + out admit) / total. Top-5 weeks = best 5 weekly deltas / total; "iid" = the same share expected from 28 independent weekly deltas with the same mean and SD (so a share near the iid value is what noise looks like). HOLD alongside.
| candidate | ref | L6M total | same | re-entry in | out (rule-skipped) | out (admit) | re-entry share | net admit share | top-5 weeks share (iid) | HOLD re-entry share / top-5 | grid max re-entry share L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 70/30 split (S73 vs market) | MKT | +17.6k | +8.0k | +8.2k | +0.0k | +1.4k | 47% | 55% | 66% (62%) | 39% / 55% | 47% |
| PE 45-s three-bar, market, NY-AM+NY-PM (in S73 line) | S73 | +3.0k | -0.2k | +1.7k | +0.0k | +1.4k | 58% | 105% | 123% (121%) | 44% / 116% | 58% |
| PE 45-s three-bar, market, NY (vs C2 plain 70/30 floor) | S:cffloor | +3.6k | -0.5k | +1.2k | +0.0k | +2.9k | 34% | 115% | 104% (105%) | 24% / 99% | 34% |
| PE 45-s three-bar, market, NY, 3-s delay | S:cffloor | +3.4k | -0.2k | +1.0k | +0.0k | +2.7k | 28% | 107% | 112% (112%) | 18% / 106% | 28% |
| ER(20) 5-min sizer 1.5/0.5 at 0.3 (ENG6) | S73 | +8.5k | +5.7k | +16.9k | +0.0k | -14.2k | 200% | 32% | 260% (157%) | 145% / 193% | 200% |
| KB ER(20) 5-min sizer 1.5/0.5 at 0.2 (K6) | S73 | +3.1k | +1.8k | +2.7k | +0.0k | -1.4k | 88% | 42% | 173% (135%) | 96% / 169% | 108% |
| first-stop cut 50%, stopped book entered in Asia | S73 | +13.2k | +2.5k | +9.3k | +0.0k | +1.4k | 71% | 81% | 111% (98%) | 63% / 113% | 81% |
| first-stop cut 50%, pooled (all sessions) | S73 | +6.6k | +0.2k | +4.4k | +0.0k | +2.0k | 67% | 96% | 219% (152%) | 61% / 275% | 105% |
| first-stop cut 100%, Asia | S73 | +11.8k | +5.2k | +11.2k | +0.0k | -4.6k | 95% | 56% | 165% (130%) | 81% / 172% | 100% |
| first-stop cut 25%, Asia | S73 | +8.8k | +1.5k | +5.7k | +0.0k | +1.6k | 65% | 83% | 128% (108%) | 59% / 130% | 95% |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | +3.5k | +1.7k | +0.6k | +0.0k | +1.2k | 16% | 51% | 327% (170%) | 8% / 288% | 74% |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | +6.8k | +3.5k | +2.1k | +0.0k | +1.2k | 31% | 48% | 182% (127%) | 28% / 167% | 67% |
| first-stop cut 50%, <=2 other books open | S73 | -0.2k | +0.8k | -1.5k | +0.0k | +0.4k | n/m | n/m | n/m (n/m) | n/m / 1745% | 79% |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | +0.9k | +0.6k | +0.7k | +0.0k | -0.4k | n/m | n/m | 680% (189%) | n/m / 909% | 68% |
| first-stop cut 50%, a book open on the other side | S73 | +4.8k | +2.3k | +1.7k | +0.0k | +0.9k | 34% | 52% | 174% (140%) | 41% / 165% | 49% |
| 8-line skip, fresh line within 20 pts (S8) | S73 | +15.4k | -2.4k | +13.1k | +14.4k | -9.7k | 85% | 22% | 96% (96%) | 81% / 112% | 85% |
| 8-line skip, D=15 pts (S8) | S73 | +5.2k | -0.5k | +10.1k | +5.5k | -9.9k | 193% | 5% | 268% (164%) | 162% / 278% | 210% |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | +3.7k | +2.5k | -0.7k | +0.0k | +2.0k | -19% | 33% | 249% (164%) | -23% / 254% | 83% |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | -0.8k | -0.8k | +2.3k | +0.0k | -2.3k | n/m | n/m | n/m (n/m) | n/m / n/m | 124% |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | +5.6k | +2.3k | +4.1k | +0.6k | -1.4k | 73% | 48% | 117% (109%) | 89% / 129% | 137% |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | +9.3k | -0.8k | +4.6k | +5.5k | -0.0k | 49% | 49% | 105% (96%) | 48% / 132% | 66% |
| stop-join: ST+HM stop exit Native 1.28 instead of join 2.45 (LIVE bases only) | S73 | +4.1k | +3.6k | +0.0k | +0.0k | +0.5k | 0% | 12% | 43% (52%) | 0% / 38% | 10% |
| stop-join: ST+HM stop cost 0.5 (the fix target) | S73 | +7.3k | +6.5k | +1.2k | +0.0k | -0.5k | 17% | 10% | 55% (57%) | 15% / 48% | 19% |
| ER(20)>=0.3 as a skip (TG-1) | S73 | -14.7k | -0.8k | +13.1k | -23.5k | -3.5k | n/m | n/m | n/m (n/m) | n/m / n/m | 243% |

Cut rules, pre-lock view (same trades only, before the lock engine re-admits): headline fires/wk, pre-lock $/wk and pts per planned lot (events with the rule condition true):
| cut variant | ref | fires/wk L6M | pre-lock $/wk L6M | pre-lock $/wk PRE | pts per planned lot L6M | lock-engine $/wk L6M | pre-lock share of lock-engine gain |
|---|---|---|---|---|---|---|---|
| first-stop cut 50%, stopped book entered in Asia | S73 | 6.6 | +3.3k | +1.0k | +0.17 | +13.2k | 25% |
| first-stop cut 50%, stopped book entered in Asia | MKT | 6.6 | +3.5k | +0.7k | +0.18 | +20.2k | 17% |
| first-stop cut 50%, pooled (all sessions) | S73 | 15.0 | -1.8k | -4.9k | -0.10 | +6.6k | -28% |
| first-stop cut 50%, pooled (all sessions) | MKT | 15.2 | +0.0k | -5.4k | +0.00 | +23.0k | 0% |
| first-stop cut 100%, Asia | S73 | 6.2 | +4.4k | +2.7k | +0.23 | +11.8k | 37% |
| first-stop cut 100%, Asia | MKT | 6.1 | +5.2k | +2.7k | +0.27 | +12.5k | 42% |
| first-stop cut 25%, Asia | S73 | 6.5 | +1.5k | +0.7k | +0.08 | +8.8k | 17% |
| first-stop cut 25%, Asia | MKT | 6.5 | +1.6k | +0.4k | +0.08 | +12.8k | 13% |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | 7.5 | +0.2k | -2.7k | +0.01 | +3.5k | 4% |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | 7.6 | +1.0k | -2.7k | +0.05 | +12.4k | 8% |
| first-stop cut 50%, Asia & vol tercile 2 | S73 | 3.8 | +3.6k | +0.1k | +0.19 | +6.8k | 52% |
| first-stop cut 50%, Asia & vol tercile 2 | MKT | 3.8 | +3.9k | +0.1k | +0.20 | +12.4k | 32% |
| first-stop cut 50%, <=2 other books open | S73 | 8.9 | +0.2k | -0.2k | +0.01 | -0.2k | n/m |
| first-stop cut 50%, <=2 other books open | MKT | 8.9 | +1.2k | -0.4k | +0.06 | +11.5k | 10% |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | 3.1 | +0.7k | -0.8k | +0.04 | +0.9k | 80% |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | 3.1 | +1.5k | -0.2k | +0.08 | +7.4k | 20% |
| first-stop cut 50%, a book open on the other side | S73 | 3.2 | +2.5k | +0.3k | +0.13 | +4.8k | 52% |
| first-stop cut 50%, a book open on the other side | MKT | 3.1 | +2.7k | -0.1k | +0.14 | +4.0k | 66% |

## 6. Every negative convention cell in L6M or HOLD (the sign flips, explicitly)
| candidate | ref | basis | lots | governors | scale | L6M | HOLD |
|---|---|---|---|---|---|---|---|
| first-stop cut 50%, pooled (all sessions) | MKT | M | live | planned | raw | -0.3k | -1.3k |
| first-stop cut 25%, Asia | S73 | M | research | planned | raw | +0.2k | -0.3k |
| first-stop cut 50%, entry-day vol tercile 2 | MKT | M | live | planned | raw | +0.4k | -0.4k |
| first-stop cut 50%, entry-day vol tercile 2 | S73 | M | research | planned | raw | +1.0k | -0.4k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE | research | planned | raw | -0.6k | +0.3k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE_fixed | research | planned | raw | -0.5k | +0.3k |
| first-stop cut 50%, <=2 other books open | S73 | LIVE_native | research | planned | raw | -2.3k | -1.3k |
| first-stop cut 50%, <=2 other books open | S73 | N | research | planned | raw | -0.2k | +0.5k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | MKT | M | live | planned | raw | -0.2k | -0.6k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | LIVE_fixed | live | planned | raw | -0.5k | -0.3k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | LIVE_native | live | planned | raw | -0.5k | -0.3k |
| first-stop cut 50%, ER20>=0.4 at the stopped signal | S73 | N | live | planned | raw | -0.2k | -0.0k |
| 8-line skip, D=15 pts (S8) | MKT | LIVE_fixed | live | planned | raw | -0.5k | -0.8k |
| 8-line skip, D=15 pts (S8) | S73 | N | live | planned | raw | +0.3k | -0.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | live | planned | raw | -0.5k | -0.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | live | sized | eqr | -2.1k | -0.9k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | live | sized | raw | -3.3k | -2.0k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | research | sized | eqr | -4.5k | -3.0k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE | research | sized | raw | -6.5k | -4.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | live | planned | raw | -0.6k | -0.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | live | sized | eqr | -1.9k | -0.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | live | sized | raw | -3.2k | -1.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | research | sized | eqr | -4.4k | -2.4k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_fixed | research | sized | raw | -6.7k | -4.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | live | planned | raw | -0.6k | -0.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | live | sized | eqr | -2.1k | -0.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | live | sized | raw | -3.3k | -1.8k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | research | sized | eqr | -4.4k | -2.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | LIVE_native | research | sized | raw | -6.6k | -4.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | live | planned | raw | +0.1k | -0.3k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | live | sized | eqr | -2.9k | -2.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | live | sized | raw | -3.4k | -2.9k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | research | sized | eqr | -7.4k | -7.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | M | research | sized | raw | -7.9k | -7.6k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | live | planned | raw | -0.7k | -0.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | live | sized | eqr | -1.6k | -0.3k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | live | sized | raw | -3.1k | -1.6k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | research | sized | eqr | -4.5k | -2.6k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | MKT | N | research | sized | raw | -6.9k | -4.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE | live | sized | raw | -0.7k | -0.3k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE | research | sized | raw | -2.5k | -2.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_fixed | live | sized | raw | -1.4k | -0.8k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_fixed | research | sized | eqr | -0.8k | -0.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_fixed | research | sized | raw | -3.9k | -3.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_native | live | sized | raw | -0.8k | -0.4k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | LIVE_native | research | sized | raw | -2.6k | -2.2k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | live | planned | raw | -0.4k | -0.5k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | live | sized | eqr | -2.1k | -1.4k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | live | sized | raw | -2.8k | -2.0k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | research | planned | raw | -1.1k | -0.9k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | research | sized | eqr | -5.6k | -5.1k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | M | research | sized | raw | -6.7k | -5.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | N | live | sized | raw | -1.2k | -0.7k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | N | research | sized | eqr | -1.1k | -0.9k |
| ES-lead sizer N1 cell: ES led NQ >=1.5 bp/30 s x1.5, NQ led x0.5 | S73 | N | research | sized | raw | -4.4k | -3.7k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | live | planned | eqr | +0.2k | -0.9k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | live | planned | raw | -1.5k | -2.1k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | research | planned | eqr | +0.7k | -1.7k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | research | planned | raw | -1.7k | -3.0k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | research | sized | eqr | -5.2k | -2.4k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | MKT | M | research | sized | raw | -5.4k | -2.5k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE_fixed | live | planned | raw | +0.1k | -0.1k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE_fixed | research | planned | raw | +0.5k | -1.3k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | LIVE_native | research | planned | raw | +1.1k | -0.8k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | live | planned | eqr | -0.8k | -1.1k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | live | planned | raw | +0.3k | -0.2k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | research | planned | eqr | +0.1k | -1.0k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | research | planned | raw | +0.7k | -0.2k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | research | sized | eqr | -11.3k | -7.3k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | M | research | sized | raw | -11.6k | -7.5k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | N | live | planned | raw | -0.2k | -0.3k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | N | research | planned | eqr | +1.1k | -1.9k |
| ES-NQ lag-z sizer (30 s, ATR14, th 0.5; eslead second pass / D6 es_lead line) | S73 | N | research | planned | raw | -0.8k | -2.1k |
| second-signal skip: same-book re-entry <=30 min after a loser (N1 b) | S73 | N | live | planned | raw | +0.6k | -0.0k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE | live | planned | raw | +0.4k | -0.2k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE_fixed | live | planned | raw | +0.2k | -0.4k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | LIVE_native | live | planned | raw | +0.3k | -0.3k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | MKT | N | live | planned | raw | +0.3k | -0.4k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE | live | planned | raw | +0.7k | -0.1k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE_fixed | live | planned | raw | +0.5k | -0.2k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | LIVE_native | live | planned | raw | +0.6k | -0.2k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | M | live | planned | raw | +0.6k | -0.1k |
| HM FVG skip: unmitigated 15m/1h/4h FVG within 60 pts (NTZ-1) | S73 | N | live | planned | raw | +0.6k | -0.2k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE | live | planned | raw | -2.0k | -0.2k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE_fixed | live | planned | raw | -4.3k | -2.2k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | LIVE_native | live | planned | raw | -3.1k | -1.1k |
| ER(20)>=0.3 as a skip (TG-1) | MKT | N | live | planned | raw | -4.9k | -2.9k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE | live | planned | raw | -3.9k | -2.1k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE | research | planned | raw | -7.2k | -2.1k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_fixed | live | planned | raw | -5.3k | -3.5k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_fixed | research | planned | raw | -10.3k | -5.4k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_native | live | planned | raw | -4.5k | -2.7k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | LIVE_native | research | planned | raw | -8.6k | -3.7k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | N | live | planned | raw | -7.2k | -5.3k |
| ER(20)>=0.3 as a skip (TG-1) | S73 | N | research | planned | raw | -14.7k | -9.4k |

## 7. The 70/30 split at INTEGER live lots, per book, with and without the add slippage (UF-ENTRY cycle 7 request)
Live add contracts = L - round(0.7 L): K6 2 lots -> 1/1 (a 50/50 split), U6 4 -> 3/1, H6 4 -> 3/1 (NY-AM 2 -> 1/1), P6 7 -> 5/2, ST 10 -> 7/3, WT 7 -> 5/2. Source: the stored per-book daily series of `out/uf/entry_c7/stack.pkl` (UF-ENTRY engine, integer split fractions, add slippage +0.25 pt/lot modelled at d=2 s; x1.8 = live-exit calibration stress +0.45) against the market per-book daily recomputed on the same engine (`c7_perbook.py`). $/wk at RESEARCH lots c=1 (not equal-risk), split minus market, basis N and LIVE-CAL; the live-lot dollars use the per-book live/research ratio (HM at the Asia 4-lot ratio; its 2-lot NY-AM trades are over-stated by 2x).
**basis N**
| book | live lots | add slippage | scheme | L3M | L6M [MDE] | HOLD | PRE | X' | L6M at live lots |
|---|---|---|---|---|---|---|---|---|---|
| **K6 (KB)** | 2 (1/1) | none (as simulated) | integer lots | -0.3k | -1.8k [+8.0k] | -1.2k | -3.1k | +0.8k | -0.7k |
| **K6 (KB)** | 2 (1/1) | none (as simulated) | ideal 70/30 | +3.1k | +0.5k [+7.0k] | +0.7k | -1.9k | +0.9k | +0.2k |
| **K6 (KB)** | 2 (1/1) | +0.25 pt/lot modelled | integer lots | -2.3k | -3.0k [+7.6k] | -2.4k | -3.1k | +1.3k | -1.2k |
| **K6 (KB)** | 2 (1/1) | +0.25 pt/lot modelled | ideal 70/30 | +1.2k | -0.5k [+7.6k] | -0.2k | -2.7k | +0.9k | -0.2k |
| **K6 (KB)** | 2 (1/1) | +0.45 pt/lot stress | integer lots | -3.0k | -3.4k [+7.6k] | -2.8k | -2.9k | +1.5k | -1.3k |
| **K6 (KB)** | 2 (1/1) | +0.45 pt/lot stress | ideal 70/30 | +1.4k | -0.5k [+7.3k] | -0.3k | -2.2k | +1.0k | -0.2k |
| U6 (SM) | 4 (3/1) | none (as simulated) | integer lots | +0.8k | +3.0k [+4.7k] | +3.4k | +0.4k | -0.9k | +1.6k |
| U6 (SM) | 4 (3/1) | +0.25 pt/lot modelled | integer lots | +0.7k | +3.0k [+4.7k] | +3.3k | +0.2k | -0.9k | +1.6k |
| U6 (SM) | 4 (3/1) | +0.45 pt/lot stress | integer lots | +0.6k | +2.9k [+4.9k] | +3.2k | +0.2k | -0.9k | +1.6k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | none (as simulated) | integer lots | +4.5k | +2.2k [+7.4k] | +2.6k | +0.8k | -0.0k | +0.9k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | +0.25 pt/lot modelled | integer lots | +1.9k | +0.8k [+7.4k] | +1.4k | +0.2k | -0.1k | +0.3k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | +0.45 pt/lot stress | integer lots | +2.0k | +0.9k [+7.7k] | +1.5k | +0.4k | -0.1k | +0.4k |
| P6 (PE) | 7 (5/2) | none (as simulated) | integer lots | +2.1k | +0.9k [+6.0k] | +0.3k | +1.3k | +2.7k | +1.2k |
| P6 (PE) | 7 (5/2) | +0.25 pt/lot modelled | integer lots | +1.1k | +0.8k [+6.9k] | +0.2k | +1.5k | +2.7k | +1.0k |
| P6 (PE) | 7 (5/2) | +0.45 pt/lot stress | integer lots | -0.0k | +0.2k [+6.4k] | -0.0k | +1.6k | +2.5k | +0.2k |
| S6 (ST) | 4.26 (research/2.35) | none (as simulated) | integer lots | +8.3k | +8.0k [+10.3k] | +8.2k | +1.1k | +0.7k | +3.4k |
| S6 (ST) | 4.26 (research/2.35) | +0.25 pt/lot modelled | integer lots | +3.0k | +3.3k [+8.5k] | +4.1k | -0.1k | +0.7k | +1.4k |
| S6 (ST) | 4.26 (research/2.35) | +0.45 pt/lot stress | integer lots | +6.7k | +5.2k [+10.8k] | +5.6k | -1.5k | +1.0k | +2.2k |
| W6 (WT) | 2.98 (research/2.35) | none (as simulated) | integer lots | +3.7k | +4.1k [+5.6k] | +4.1k | +1.6k | -1.7k | +1.7k |
| W6 (WT) | 2.98 (research/2.35) | +0.25 pt/lot modelled | integer lots | +3.2k | +3.7k [+5.7k] | +3.8k | +1.7k | -1.8k | +1.6k |
| W6 (WT) | 2.98 (research/2.35) | +0.45 pt/lot stress | integer lots | +3.9k | +4.0k [+6.2k] | +3.9k | +1.3k | -2.1k | +1.7k |
| six-book stack | - | none (as simulated) | integer lots | +19.1k | +16.3k [+18.1k] | +17.3k | +2.0k | +1.6k | n/a |
| six-book stack | - | none (as simulated) | ideal 70/30 | +20.2k | +17.6k [+16.6k] | +18.4k | +3.8k | +2.2k | n/a |
| six-book stack | - | +0.25 pt/lot modelled | integer lots | +7.5k | +8.6k [+17.0k] | +10.3k | +0.3k | +1.9k | n/a |
| six-book stack | - | +0.25 pt/lot modelled | ideal 70/30 | +12.0k | +11.6k [+15.9k] | +13.0k | +1.2k | +1.8k | n/a |
| six-book stack | - | +0.45 pt/lot stress | integer lots | +10.2k | +9.7k [+18.4k] | +11.5k | -1.0k | +1.8k | n/a |
| six-book stack | - | +0.45 pt/lot stress | ideal 70/30 | +15.9k | +12.7k [+16.8k] | +13.7k | -0.1k | +1.3k | n/a |

**LIVE-CAL**
| book | live lots | add slippage | scheme | L3M | L6M [MDE] | HOLD | PRE | X' | L6M at live lots |
|---|---|---|---|---|---|---|---|---|---|
| **K6 (KB)** | 2 (1/1) | none (as simulated) | integer lots | -1.9k | -2.3k [+7.3k] | -1.7k | -3.0k | +0.9k | -0.9k |
| **K6 (KB)** | 2 (1/1) | none (as simulated) | ideal 70/30 | +0.2k | -0.5k [+6.8k] | -0.2k | -2.0k | +1.3k | -0.2k |
| **K6 (KB)** | 2 (1/1) | +0.25 pt/lot modelled | integer lots | -2.2k | -2.4k [+7.3k] | -1.8k | -3.8k | +0.8k | -0.9k |
| **K6 (KB)** | 2 (1/1) | +0.25 pt/lot modelled | ideal 70/30 | -0.0k | -0.7k [+6.8k] | -0.4k | -2.9k | +1.1k | -0.3k |
| **K6 (KB)** | 2 (1/1) | +0.45 pt/lot stress | integer lots | -2.0k | -2.7k [+7.2k] | -2.1k | -3.3k | +1.2k | -1.0k |
| **K6 (KB)** | 2 (1/1) | +0.45 pt/lot stress | ideal 70/30 | -0.2k | -0.8k [+6.8k] | -0.5k | -2.9k | +1.1k | -0.3k |
| U6 (SM) | 4 (3/1) | none (as simulated) | integer lots | +0.8k | +3.0k [+4.7k] | +3.4k | +0.4k | -0.9k | +1.6k |
| U6 (SM) | 4 (3/1) | +0.25 pt/lot modelled | integer lots | +0.7k | +3.0k [+4.7k] | +3.3k | +0.2k | -0.9k | +1.6k |
| U6 (SM) | 4 (3/1) | +0.45 pt/lot stress | integer lots | +0.6k | +2.9k [+4.7k] | +3.3k | +0.2k | -0.9k | +1.6k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | none (as simulated) | integer lots | +5.6k | +2.9k [+7.8k] | +3.2k | +1.5k | +0.0k | +1.2k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | +0.25 pt/lot modelled | integer lots | +3.5k | +1.7k [+7.3k] | +2.2k | +0.4k | -0.1k | +0.7k |
| H6 (HM) | 4 Asia (3/1), 2 NY-AM (1/1) | +0.45 pt/lot stress | integer lots | +3.7k | +1.7k [+7.4k] | +2.2k | -0.5k | -0.2k | +0.7k |
| P6 (PE) | 7 (5/2) | none (as simulated) | integer lots | +0.8k | +0.4k [+6.6k] | -0.1k | +1.1k | +3.1k | +0.5k |
| P6 (PE) | 7 (5/2) | +0.25 pt/lot modelled | integer lots | -0.3k | +0.2k [+6.4k] | -0.3k | +1.2k | +3.1k | +0.2k |
| P6 (PE) | 7 (5/2) | +0.45 pt/lot stress | integer lots | -1.2k | -0.3k [+5.8k] | -0.5k | +1.1k | +3.1k | -0.4k |
| S6 (ST) | 4.26 (research/2.35) | none (as simulated) | integer lots | +8.6k | +7.2k [+9.0k] | +7.2k | +1.4k | +0.7k | +3.1k |
| S6 (ST) | 4.26 (research/2.35) | +0.25 pt/lot modelled | integer lots | +9.0k | +6.0k [+8.5k] | +6.1k | +0.3k | +0.8k | +2.5k |
| S6 (ST) | 4.26 (research/2.35) | +0.45 pt/lot stress | integer lots | +5.2k | +4.4k [+8.0k] | +4.6k | -1.4k | +0.8k | +1.9k |
| W6 (WT) | 2.98 (research/2.35) | none (as simulated) | integer lots | +1.3k | +2.7k [+4.2k] | +2.9k | +1.8k | -1.6k | +1.1k |
| W6 (WT) | 2.98 (research/2.35) | +0.25 pt/lot modelled | integer lots | +0.9k | +2.6k [+3.9k] | +2.8k | +1.7k | -1.9k | +1.1k |
| W6 (WT) | 2.98 (research/2.35) | +0.45 pt/lot stress | integer lots | +0.6k | +2.4k [+4.0k] | +2.6k | +1.5k | -2.3k | +1.0k |
| six-book stack | - | none (as simulated) | integer lots | +15.1k | +13.9k [+16.7k] | +14.9k | +3.1k | +2.2k | n/a |
| six-book stack | - | none (as simulated) | ideal 70/30 | +16.1k | +15.1k [+15.8k] | +16.0k | +3.8k | +2.5k | n/a |
| six-book stack | - | +0.25 pt/lot modelled | integer lots | +11.6k | +11.1k [+16.8k] | +12.3k | +0.1k | +1.7k | n/a |
| six-book stack | - | +0.25 pt/lot modelled | ideal 70/30 | +13.6k | +12.7k [+15.9k] | +13.7k | +1.4k | +2.2k | n/a |
| six-book stack | - | +0.45 pt/lot stress | integer lots | +6.8k | +8.3k [+16.5k] | +10.1k | -2.4k | +1.6k | n/a |
| six-book stack | - | +0.45 pt/lot stress | ideal 70/30 | +8.7k | +10.3k [+16.6k] | +11.4k | -1.2k | +1.6k | n/a |

**Live-lot total of the integer-lot split** (sum over the six books of the per-book live-lot dollars above, i.e. K6 2 lots, U6 4, H6 4/2, P6 7, S6/W6 research/2.35; split minus market):
| basis | add slippage | scheme | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| N | none | integer lots | +9.9k | +8.1k | +8.0k | +2.0k | +2.8k |
| N | none | ideal 70/30 | +9.1k | +8.0k | +7.9k | +3.0k | +3.0k |
| N | +0.25 pt/lot | integer lots | +4.2k | +4.8k | +5.0k | +1.5k | +2.9k |
| N | +0.25 pt/lot | ideal 70/30 | +6.3k | +6.1k | +6.1k | +1.8k | +2.8k |
| N | +0.45 pt/lot | integer lots | +4.5k | +4.7k | +5.3k | +1.0k | +2.7k |
| N | +0.45 pt/lot | ideal 70/30 | +7.6k | +6.3k | +6.2k | +1.4k | +2.5k |
| LIVE-CAL | none | integer lots | +7.2k | +6.7k | +6.7k | +2.3k | +3.3k |
| LIVE-CAL | none | ideal 70/30 | +7.4k | +7.1k | +7.0k | +2.6k | +3.4k |
| LIVE-CAL | +0.25 pt/lot | integer lots | +4.8k | +5.3k | +5.4k | +1.2k | +3.1k |
| LIVE-CAL | +0.25 pt/lot | ideal 70/30 | +5.5k | +5.9k | +5.9k | +1.7k | +3.3k |
| LIVE-CAL | +0.45 pt/lot | integer lots | +2.0k | +3.7k | +4.3k | +0.1k | +3.1k |
| LIVE-CAL | +0.45 pt/lot | ideal 70/30 | +3.3k | +4.7k | +4.7k | +0.5k | +3.0k |

**K6 FLAG**: at its live 2 lots the K6 add is 1 contract (a 50/50 split). On basis N the K6 split minus plain market is -2.3k L3M / -3.0k L6M / -2.4k HOLD / -3.1k PRE with the add slippage modelled at +0.25 pt/lot (research lots; -0.3k / -1.8k / -1.2k / -3.1k with no slippage; -3.4k L6M at the +0.45 stress) and +1.3k X' - negative in L3M, L6M, HOLD and PRE, positive only in X' (2023-24); on LIVE-CAL -2.2k / -2.4k / -1.8k / -3.8k (+0.25). At the live 2 lots that is -1.2k per week in L6M. The ideal (non-integer) 70/30 on K6 is already flat to negative once the add costs +0.25 (-0.5k L6M, -2.7k PRE), so rounding to 1/1 makes a thin edge into a loss. MDE L6M is about 7.6k, so every K6 figure is inside noise individually, but it is negative in four windows in a row and the only book of the six where that holds. Recommendation implied by the numbers: market (no add) on K6; keep the add on U6 (+3.0k L6M, MDE 4.7k, robust to slippage) and S6/W6; H6 and P6 about zero after slippage.

## 8. Reconciliation: the number the brief / source report quotes vs the same cell recomputed here (L3M / L6M / HOLD / PRE / X', $k per week)
Same-engine reproductions (market base, cut rules, split, KB, PE market) match the source to the first decimal; the sizers and skips scored on the trend/newideas/eslead wrapper (tg_stack) and the ZONES addendum (de_engine run_rows at EN.LOTS) differ on the 70/30 base (their B2 base stack is 72.1k/wk in L6M vs 79.1k here; the ZONES base 26.4k) and, for sizers, in the lot rescale; on the market base (B1) they reproduce to the dollar. The ES-lead z-sizer is the one whose L6M SIGN depends on that base definition.
| row | source quote | source engine / base | recomputed here (same ref, scale) | match |
|---|---|---|---|---|
| 70/30 split S73 vs market | +20.2 / +17.6 / +18.4 / +3.8 / +2.2 | SPLIT-2 / SP-1 (sp_lib), N | +20.2 / +17.6 / +18.4 / +3.8 / +2.2 | EXACT |
| Asia-stopped cut50 on S73 | +11.9 / +13.2 / +11.4 / +2.0 / +2.8 | STACK-2 (s2_lib), N | +11.9 / +13.2 / +11.4 / +2.0 / +2.8 | EXACT |
| Asia-stopped cut50 on market | +17.5 / +20.2 / +16.5 / +0.9 / +3.7 | STACK-2 | +17.5 / +20.2 / +16.5 / +0.9 / +3.7 | EXACT |
| pooled first-stop cut50 on market | +35.7 / +23.0 / +19.3 / -8.2 / +0.7 | STACK-2 | +35.7 / +23.0 / +19.3 / -8.2 / +0.7 | EXACT |
| pooled first-stop cut50 on S73 | +16.0 / +6.6 / +4.6 / -6.5 / -0.4 | STACK-2 | +16.0 / +6.6 / +4.6 / -6.5 / -0.4 | EXACT |
| cut50 a book open on the other side, S73 | +3.3 / +4.8 / +4.6 / +2.8 / +4.2 | STACK-2 | +3.3 / +4.8 / +4.6 / +2.8 / +4.2 | EXACT |
| cut50 Asia & vol tercile 2, S73 | +5.5 / +6.8 / +6.5 / +4.5 / +4.7 | STACK-2 | +5.5 / +6.8 / +6.5 / +4.5 / +4.7 | EXACT |
| KB ER0.2 sizer, planned-lot R, S73 | +8.2 / +3.1 / +2.8 / -1.6 / +0.8 | KB-REGIME (s2_lib) | +8.2 / +3.1 / +2.8 / -1.6 / +0.8 | EXACT |
| KB ER0.2 sizer, sized-lot R, S73 | +10.9 / +8.1 / +6.5 / +3.4 / +2.3 | KB-REGIME | +10.9 / +8.1 / +6.5 / +3.4 / +2.3 | EXACT |
| ER20 sizer, equal-risk, planned R, S73 | +35.5 / +13.3 / +14.6 / -10.9 / +7.5 | TREND-2 (tg_stack, f73 base) | +29.2 / +10.0 / +11.9 / -13.0 / +7.3 | partial 1/5 |
| second-signal skip on market (B1) | +14.9 / +11.3 / +9.5 / -5.4 / -2.3 | NEW-IDEAS N1 b (tg_stack) | +14.9 / +11.3 / +9.5 / -5.4 / -2.3 | EXACT |
| second-signal skip on S73 (B2) | n/a / +7.7 / +6.7 / -3.8 / -2.9 | NEW-IDEAS N1 b, B2 = f73 base | +4.3 / +5.6 / +4.5 / -3.9 / -3.0 | partial 2/4 |
| ES-lead N1 cell, equal-risk, market (B1) | +4.4 / +3.8 / +4.6 / +0.8 / +2.5 | NEW-IDEAS d / ESLEAD (tg_stack) | +4.4 / +3.8 / +4.6 / +0.8 / +2.5 | EXACT |
| ES-lead lag-z th0.5, as coded, market (B1) | +2.6 / +4.7 / +3.3 / +8.6 / +0.5 | ESLEAD tables.md | +2.6 / +4.7 / +3.3 / +8.6 / +0.5 | EXACT |
| ES-lead lag-z th0.5, as coded, S73 (B2) | -1.2 / +5.9 / +2.9 / +8.0 / +1.7 | ESLEAD tables.md, B2 = f73 base | -9.8 / -0.8 / -2.1 / +6.5 / +1.6 | partial 1/5 |
| 8-line skip D=20, S73, research lots | +44.3 / +28.3 / +25.7 / +1.7 / +6.2 | ZONES-2 addendum (de_engine, EN.LOTS, SPL base) | +30.1 / +15.4 / +12.4 / +1.6 / +4.9 | partial 1/5 |
| HM FVG skip D60 on market (L6M only) | n/a / +11.5 / n/a / n/a / n/a | Sunday brief / NTZ-1 | +24.8 / +11.8 / +9.1 / -1.6 / -0.4 | EXACT |
| PE 45-s three-bar market NY vs C2 floor | n/a / +3.6 / +3.3 / -0.4 / -0.6 | CONFIRM-2 addendum B (cf_engine stack_line) | +5.4 / +3.6 / +3.3 / -0.4 / -0.6 | EXACT |
| stop-join Native vs join, ST+HM, live basis (L6M) | n/a / +4.4 / n/a / n/a / n/a | LIVE_STOP_JOIN (analytic, 10 lots; engine 10+10) | +2.8 / +4.1 / +4.1 / +4.7 / +3.0 | partial 0/1 |

## 9. Methods, definitions and what was NOT done
* Engine: `stack2/s2_lib.py` (sp_lib rows for the market base and the S73 base, `sl_lib` per-book exact lock engine with day entry test +5R/-2R, day arm 2R keep 50%, week floor 12R) plus `unitaudit/ua_lib.py`, which adds (a) the sized-lot-R governor (identical patch to `kbregime/kbr_stack.py`, generalised to all six books; multipliers are the sizer multiplier only, never the live session-lot ratio), (b) live book-session lots with sessions of live lot 0 removed, (c) the ST/HM stop-cost variants on the LIVE basis (p0 and the simulator stop slip), (d) custom entry bases (PE 45-s rows replaced in the C2 floor and in S73; pure-wait rows carry l1 = filled lots, l2 = 0). Sanity: S73 vs market, the Asia / pooled first-stop cuts (all variants) and the KB sizer reproduce STACK-2 / SPLIT-2 / KB-REGIME to the dollar (section 8).
* Row-level inputs are the stored series, not new searches: ER(20) 5-min from the trend-gate store, ES-lead multipliers from `out/eslead/cells_S.pkl` (a3 lag_bp30_th1.5 and a3 lag_z30_th0.5), second-signal skip from `out/newideas/b_cells.pkl` (a1 W30), 8-line (S8, fresh, D = 20 / 15 pts) and HM-FVG (15m+1h+4h, D = 60) fire masks regenerated from the POI store by the ZONES-2 / NTZ-1 code (`prep_zones.py`; 6,690 / 4,950 / 980 signals), PE 45-s market cell regenerated by `confirm2/c2_run.run_one` (`prep_pe45.py`; 1,797 of 2,681 NY PE signals fire), C7 per-book series from `out/uf/entry_c7/stack.pkl`.
* Units: **per planned lot** = library-level points per signal (all ENG6 signals in the window, no lock engine): raw delta per signal ((m-1) y averaged over all signals; skipped signals count 0) and risk-matched (sum m y / sum m - mean y) for sizers; for the cut rules the same-trade pre-lock delta per planned lot (pts); for the split and PE rows the rule-minus-reference points per signal on the same signal set. **Per contract of final position** = library points per final contract (sum w m y / sum w m L_final, w = book lots, L_final = filled lots) rule vs reference, and, separately, lock-engine pts per admitted contract (sum $ / (20 x admitted contracts)) for every row including the cuts. **Stack $/wk** = lock-engine daily series, weekly sum, window mean of the rule-minus-reference weekly delta.
* Equal-risk scale: scalar = (signals in PRE u X') / (sum of multipliers in PRE u X'), within the sizer's scope (KB live sessions for K6), fitted on PRE+X' only. "As coded" keeps 1.5 / 0.5 (mean lot factor is lib_meanm in `full_table.csv`).
* CI: 4-week circular block bootstrap of the weekly delta (2,000 draws); MDE: 2.8 x the week-clustered SE. Neither is multiplicity-adjusted; the source reports' RC / Romano-Wolf / DSR / PBO stand and are not repeated.
* Not done / limits: (1) M6 (MV), A6 (PB7), O6 and N6 have no row in the six-book lock engine, so nothing here values them; (2) the ES-lead rows exist only to 2026-01-31 (no ES after), so Y26 is January only; (3) skip and cut candidates were not run under the sized-R governor (multiplier 1 on every kept row, equal by construction); (4) HM live lots for sessions other than Asia / NY-AM are taken as 0 (the brief lists only those two), so a London / NY-PM HM trade would add live dollars not counted; (5) the integer-lot section is on the UF-ENTRY engine at research lots, not re-run on the sp_lib engine, and its slippage is the C7 state-dependent model, not a measurement; (6) live-session-lot rows drop the sessions of live lot 0 for the base too, so "live B" is a different stack, not a rescaled one; (7) the sign-flip grid mixes bases the source reports label differently; a flip on M or LIVE-JOIN is information about cost assumptions, a flip on governors / lots / reference is information about the unit.
