# DS3_INSTR2_FINAL: T-INSTR-2 consolidated verdict (S4a, 2026-11-06). Research only, Shadow only, no PASS claims, no purchases.

Built from the per-instrument pages (cited, not repeated): DS3_INSTR2_ES / RTY / YM / GC / CL / 6E / 6J / ZN / ZB / BTC / NKD .md, DS3_INSTR2_NATIVE.md (native books), DS3_INSTR2_ALLINST.md (joint null over all 12 instruments, last block sha256 6d094ebc09bfd02a6dd5f8f444a4a6aab776d479dfb36088794cf467e03c4322), DATA_BAD_PRINTS.md (6E/6J repaired copies) and DS3_FIND_CHARACTER.md (T-FIND maps). MBT has no page of its own: it shares DS3_INSTR2_BTC.md (BTC / MBT own grids) and DS3_INSTR2_NATIVE.md. Bar: tolerant gate, forward-only placebos, family max-stat on the ALLINST hash worlds, own walk-forward, corr to the NQ stack <= .3, stack Calmar up with carry weeks dropped. Joint null: 12 instruments, 2,129,018 eligible cells, joint max median 3.94, p95 4.37.

| instrument | best cell per family / stage | tolerant gate (count of eligible) | family-max p (own; joint) | own walk-forward | corr to NQ stack | stack Calmar carry-dropped | label | 13-year percent-frame record |
|--|--|--|--|--|--|--|--|--|
| ES | Keltner / momentum-vote breakouts, nyam/pre (best tolerant zj 4.26 all-cells, tolerant family p .64) | 8,149 of 456,498 eligible | own .64; joint n/a (ES M.npy is in the joint max, best joint p of any ES tolerant cell not recomputed here) | stage 2 top 30: fail (section 6) | see section 6 | see section 6 | best-of-F / REGIME (28,986 NOW-ONLY) | 13y percent frame run in stage 2 (section 6) |
| RTY | Keltner / momentum-vote breakouts nyam/pre (best tolerant zj 3.40) | 8,490 of 457,338 | own .80 | top 12 fail walk-forward | not a lead: stage 2 stopped | not a lead | best-of-F / REGIME | not run (nothing cleared; data from 2017-07) |
| YM | Keltner / momentum-vote breakouts nyam/pre (best tolerant zj 3.36) | 11,605 of 457,674 | own .88 | top 12 fail walk-forward | not a lead | not a lead | best-of-F / REGIME | not run (nothing cleared) |
| GC | Keltner flip NY-AM / pre 08:30 (1,125 Keltner, 398 Supertrend among 1,756 tolerant); native books (London fix, 08:20 range, gold-yield divergence): 40 of 40 FAIL | generic 1,756 of 141,120; ALLINST 2,111 of 132,304 | own 1.00 (F = 132,286); joint 1.000 | native WF: not run; generic WF in GC_wfres.pkl not yet read | see DS3_INSTR2_GC.md | positive carry-dropped for 2026-only cells, fails family test | REGIME (2026-only) | all 40 finalists negative 2013-2023, 0-6 of 11 pre-2023 years positive (GC page); all 40 native finalists negative over 13y |
| CL | pre/nyam breakouts; 30 finalists, placebo p_book .13-.95 | 7,883 (ALLINST gate) of 64,230 eligible | own .17-1.00; joint 1.000 | 0 of 30 positive at both lookbacks | |r| <= .12 (V0/V2) | none improves stack Calmar | best-of-F / REGIME | not run (nothing cleared) |
| 6E | pre-market (08:30-09:30) 3-5 min Supertrend / Keltner; native none | 2,676 of 63,888 | own .36-1.00; joint 1.000 | 0 of 30 | <= .23 | none improves | REGIME / best-of-F | repaired copy: 0 of 30 positive mean/trade, median -$60 per trade (was -$78); majority-positive-years cells 0 to 1 (DATA_BAD_PRINTS.md). Flag: block B prior-day-break pre-market cells about break-even after repair, REGIME reading withdrawn, verdict unchanged; one evaluate() follow-up open |
| 6J | 30 tolerant finalists small (L6M +$0-120/wk) | 310 of 64,323 | own .39-1.00; joint 1.000 | 2 of 30 positive at both lookbacks | <= .27 | none improves | REGIME / best-of-F | repaired copy: 0 of 30 positive mean/trade (was 1), median -$34 (DATA_BAD_PRINTS.md) |
| ZN | Treasury grid + native event books N1/N2/N3: DEAD; one-tick cost flips the best screen cell | 13 (native books, ALLINST gate); 8 pass stage A screen | joint 1.000 (best tolerant zj 1.07) | no finalist reached it | n/a | n/a | NULL | 0 of 60 tested cells positive in most pre-2023 years |
| ZB | same as ZN: DEAD | 0 tolerant (native, ALLINST gate); 3 pass stage A screen | n/a | n/a | n/a | n/a | NULL | same as ZN |
| BTC | 10-min Keltner flip, 2.5 ATR band, Asia (t about 3.4 against 144,648 cells), plus Supertrend 15m / HMA-VWAP; BTC standard is CAP-BREACH (< 1 contract per 5 min) | 1,723 of 142,121 | joint 0 cells; best tolerant 1.000 | not run (nothing passed family) | 0.0-0.08 | negligible dollars at the cap | best-of-F | data from 2022 only |
| MBT | same signal cluster as BTC on the usable micro leg (cap 1.3-7.4 contracts per 5 min); native books: none clear | 2,120 of 141,449 | best tolerant joint p .995 | not run | 0.0-0.08 | negligible | best-of-F | data from 2022 only |
| NKD | no cell with positive full-sample mean R (median -0.17 R); CAP-BREACH (cap < 1 contract per 5 min in every session) | 102 of 140,961 (all negative over 13y); 0 with persistence | joint 1.000 | n/a | n/a | n/a | NULL | all tolerant cells negative over the full 13 years |

Cells marked "see section" or "n/a" were not produced for that instrument (nothing reached that stage); no number was filled in from memory. The ALLINST tolerant counts use the joint-null tables; the page-level counts (for example GC 1,756 of 141,120) use each page's own gate and may differ slightly.

## T-FIND map sentence per instrument (first sentence of each "Plain paragraph" in DS3_FIND_CHARACTER.md)

* **ES**: At 1 minute every session has negative autocorrelation (-0.085 to -0.026; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **RTY**: At 1 minute every session has negative autocorrelation (-0.038 to +0.000; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **YM**: At 1 minute every session has negative autocorrelation (-0.039 to -0.011; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **GC**: At 1 minute every session has negative autocorrelation (-0.062 to -0.013; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **CL**: At 1 minute every session has negative autocorrelation (-0.060 to -0.012; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **ZN**: At 1 minute every session has negative autocorrelation (-0.260 to -0.114; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **ZB**: At 1 minute every session has negative autocorrelation (-0.201 to -0.076; bid-ask bounce / last-print noise, not a tradable edge by itself).
* **6E**: 6E (euro FX) is a mean-reverting range instrument from 1 to about 30 minutes in every session and a random walk beyond an hour.
* **6J**: 6J (yen FX) behaves like 6E but weaker above 5 minutes: the lag correlation is negative at 1 and 5 minutes in all six sessions (5-minute -0.018 pre to -0.094 close, NY-PM -0.071; p_family <= .023; same sign in 10-14 of 14 years), at 15 minutes only in Asia (-0.012), NY-PM (-0.028) and the close (-0.026), and absent from 30 minutes on (|corr| <= .037, p_family 0.78-1.0).
* **BTC**: BTC standard (5 BTC, $5 per point; CME) is the CAP-BREACH cross-check of MBT and has the same character: reversion at 1-5 minutes in Asia, London, pre-NY, NY-PM and the close (5-minute -0.024 / -0.045 / -0.061 / -0.031 / -0.057, p_family .003; NY-AM -0.013, p_family .87), nothing at 15 minutes or longer that survives the family correction (a mild +0.08 60-mi
* **MBT**: MBT (micro bitcoin, $0.1 per point; BTC standard $5 per point as the cap-breach cross-check) trades around the clock and reverts at 1-5 minutes in five of six sessions and not in NY-AM: the 5-minute lag correlation is -0.050 (pre-NY hour), -0.038 (London), -0.029 (NY-PM), -0.020 (Asia), -0.044 (close) with p_family .003 (BTC: -0.045 London, -0.061 pre, -0.05
* **NKD**: NKD (Nikkei 225 in USD on CME, $5 per point) is a thin follower of NQ whose range is made in Tokyo hours: 47% of the label day's range forms in the three hours 18:00-21:00 ET (14% / 16% / 17%), the contemporaneous correlation with NQ is 0.41-0.62 on 1-minute returns and 0.56-0.78 on 15-30 minute returns depending on the session, and NQ leads NKD by one minut

## Is there a diversifier yet?
**No.** Across 12 instruments and 2.13 million eligible cells in the joint random-side null, no tolerant cell has a joint family p or a BH q at or below .10, and every best real zj (3.0-4.3) sits inside the null maximum (median 3.94). What passes the tolerant gate is a 2026-only trend regime (breakout and flip books in NY-AM and the 08:30 pre-market on index, gold, euro and crypto series) that is negative or flat in every earlier year wherever 13 years exist (GC, 6E and 6J after repair, NKD, ZN, ZB), fails the placebos and the walk-forward on the stage-2 finalists, and in crypto and NKD the execution cap leaves no dollars. The cells are mostly uncorrelated with the NQ stack (CL, 6E, 6J at most .27), which is the diversification property, but a zero-correlation return stream with no edge adds nothing. What would change this: the one open lead-to-test is the 6E prior-day-high/low break in the 08:30-09:30 pre-market, which the bad-print repair moved from clearly negative to about break-even over 10 years (DATA_BAD_PRINTS.md, Flagged for owners); it needs its own evaluate() run before it can be called anything.

Maintenance: this page is new and append-only; corrections are appended below, not rewritten.

## UPDATE 2026-11-06 (S4a): 6E post-hoc cell and LRS 6E/6J 13-year check
New page DS3_INSTR2_6E_PDHL.md (prereg sha256 95526298b1fb0746198f28675179980e7a8297d19442759a281cbbfa7e921b0a, post-hoc, one test). The 6E prior-day-break pre-market cell that the bad-print repair turned from negative to about break-even is NOT a lead: selection-aware pre-2023 p = 0.50 (best of 90 cells), 297 trades fail the minimum sample, placebo p_book 0.78, family p 1.00, walk-forward negative, no plateau (2 of 5 neighbours positive). The open lead-to-test in the paragraph above is closed: label NULL / best-of-F. The six ZL-1 LRS finalists (6E, 6J) are negative in 7+ of 8 pre-2023 years on the repaired bars (same page). The answer to 'is there a diversifier yet' stays no.

## UPDATE 2026-11-06 (S4a): daily-horizon books (new horizon, page DS3_FIND_DAILY.md, prereg sha256 bf1de6c6902656b32ab9c86981f7b0d3e138ebde062ae719b2ded22839f72129)
408 daily-hold cells (TSMOM, Donchian, MA cross, 1-5 day reversal, night/weekend/day legs) on 11 instruments and an equal-$ portfolio, 2013-2026: 36 tolerant, none with family p <= .10 under both nulls, no LEAD. One watch item (CL Donchian-20 stop-and-reverse: walk-forward p .06, stack Calmar up, corr .03, family p ~1). 'Is there a diversifier yet': still no.
## UPDATE 2026-11-06 (S4a) - COSTCAL: saved frames re-costed with the best MEASURED costs we own (IDEAS_ROUND2 R2)
Prereg l2vast/ds3/prereg/COSTCAL_prereg.md sha256 58cae7b1e04a6dbef3e73c7bea0d255a6b9e9b0cdbbaacbae206cb33d7468fdf (filed before any re-costed statistic); code l2vast/ds3/code/t2s4a/costcal.py, costcal_daily.py; results /mnt/l2/l2vast/ds3_daily/costcal*.pkl; /mnt/l2 only. Scenarios (per lot per round trip): S0 as charged; S1 best estimate = market legs at the measured half-spread (ES 1.00 tick, RTY 2.00, NQ 3.00 quoted spread; every other instrument PROXY 1 tick), non-stop exits 2h + fee, stop exits h + the unchanged stop slip + fee (NQ stop slip = measured +1.44 pt at 10 lots); S2 = 1.5 x S1; S3 = 1.5 x the ORIGINAL cost. The old cost of every trade is recovered exactly from the frame (side x (exit_px - entry_px) x pv - net_usd_1lot is constant by pipeline and exit type, sd 0.0 on all 4775 class A/B frames: ES stop $42.3 / other $29.8 etc.).
### Cost used vs the best measured number we own (per round trip, 1 lot)
| instrument | cost used in the frames ($ RT x frames) | best measured number we own | S1 spread | S1 non-stop / stop RT | plausible range |
|--|--|--|--|--|--|
| ES | $42.3 x814; $17.3 x150 | measured: median quoted spread 1.00 tick, taker RT 1.39 ticks = $17.4 (1-s mbp-10, 2023-08..2026-10, DS3_FIND_CHARACTER 1b-a); stop-market slip unmeasured | spread 1.00 tick(s) | $17.3 / $36.1 | RT non-stop $11.1 - $23.6 (spread +/- 50%) |
| RTY | $19.8 x453; $9.8 x88; $14.8 x66; $24.8 x24 | measured: spread 2.00 ticks, taker RT 2.97 ticks = $14.9 (same source); stop slip unmeasured | spread 2.00 tick(s) | $14.8 / $19.8 | RT non-stop $9.8 - $19.8 (spread +/- 50%) |
| YM | $19.8 x632; $14.8 x10 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $9.8 / $17.3 | RT non-stop $7.3 - $14.8 (spread 0.5-2 ticks) |
| GC | $34.8 x723; $14.8 x38; $24.8 x12 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $14.8 / $29.8 | RT non-stop $9.8 - $24.8 (spread 0.5-2 ticks) |
| CL | $34.8 x503 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $14.8 / $29.8 | RT non-stop $9.8 - $24.8 (spread 0.5-2 ticks) |
| ZN | $51.7 x423 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $20.5 / $43.9 | RT non-stop $12.7 - $36.1 (spread 0.5-2 ticks) |
| ZB | $98.6 x505 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $36.1 / $83.0 | RT non-stop $20.5 - $67.3 (spread 0.5-2 ticks) |
| 6E | $24.0 x15 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $11.6 / $20.9 | RT non-stop $8.4 - $17.8 (spread 0.5-2 ticks) |
| 6J | $25.0 x22; $17.3 x7 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $11.1 / $20.5 | RT non-stop $8.0 - $17.3 (spread 0.5-2 ticks) |
| MBT | $4.3 x20; $3.8 x10 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $2.3 / $3.5 | RT non-stop $2.0 - $2.8 (spread 0.5-2 ticks) |
| NKD | $129.8 x16 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $29.8 / $92.3 | RT non-stop $17.3 - $54.8 (spread 0.5-2 ticks) |
| NQ | $14.8 x130; $19.8 x68; $24.8 x14; $9.8 x4; $44.8 x3 | measured: spread 3.00 ticks, taker RT 3.97 ticks = $19.9; stop-market slip +1.44 pt at 10 lots ($28.8; 1.7 pt recent, DS3_DN_STOPFILL.md) | spread 3.00 tick(s) | $19.8 / $41.1 | RT non-stop $12.3 - $27.3 (spread +/- 50%) |
| BTC | $129.8 x25 | none: PROXY (1-s OHLCV only, no spread) | spread 1.00 tick(s) PROXY | $29.8 / $92.3 | RT non-stop $17.3 - $54.8 (spread 0.5-2 ticks) |
Measured spreads exist only where we own an order-book table (ES, RTY, NQ: mbp-10 1-s 2023-08..2026-10); GC, CL, ZN, 6J and NKD have 1-s OHLCV only and 6E / ZB / YM / MBT / BTC have bars only, so their S1 is a PROXY (1-tick spread, half per leg) with the range shown; the ES $17.3 and NQ / RTY $9.8-$24.8 frames are mostly tick-built 1-s books that already used measured-scale costs (their S1 equals S0 or is slightly dearer).
### Label moves on the 4775 exactly re-costable frames (evaluator gate_v2a = tolerant + minimum sample; counts S0 / S1 / S2 / S3)
| instrument | frames | gate_v2a S0 / S1 / S2 / S3 | strong (v2a and L6M > 0 and HOLD > 0) S0 / S1 / S2 / S3 | frames UP under S1 (also under S2) | frames DOWN under S1 / S2 / S3 | NOW-ONLY S0 / S1 / S2 / S3 |
|--|--|--|--|--|--|--|
| ES | 964 | 6 / 12 / 9 / 3 | 3 / 6 / 5 / 2 | 6 (3) | 0 / 0 / 3 | 104 / 158 / 125 / 72 |
| RTY | 631 | 12 / 15 / 7 / 7 | 7 / 7 / 4 / 4 | 3 (0) | 0 / 5 / 5 | 97 / 101 / 82 / 75 |
| NQ | 219 | 7 / 9 / 6 / 7 | 7 / 9 / 5 / 7 | 2 (0) | 0 / 1 / 0 | 27 / 25 / 22 / 23 |
| YM | 642 | 22 / 30 / 22 / 13 | 16 / 26 / 16 / 10 | 8 (0) | 0 / 0 / 9 | 91 / 118 / 90 / 67 |
| GC | 773 | 53 / 69 / 54 / 38 | 47 / 61 / 46 / 33 | 16 (3) | 0 / 2 / 15 | 190 / 213 / 203 / 147 |
| CL | 503 | 1 / 5 / 2 / 0 | 0 / 3 / 0 / 0 | 4 (1) | 0 / 0 / 1 | 57 / 76 / 63 / 37 |
| ZN | 423 | 0 / 0 / 0 / 0 | 0 / 0 / 0 / 0 | 0 (0) | 0 / 0 / 0 | 2 / 6 / 2 / 1 |
| ZB | 505 | 0 / 0 / 0 / 0 | 0 / 0 / 0 / 0 | 0 (0) | 0 / 0 / 0 | 0 / 5 / 0 / 0 |
| 6E | 15 | 1 / 6 / 3 / 0 | 1 / 6 / 3 / 0 | 5 (2) | 0 / 0 / 1 | 9 / 12 / 10 / 4 |
| 6J | 29 | 7 / 11 / 8 / 0 | 2 / 5 / 2 / 0 | 4 (1) | 0 / 0 / 7 | 15 / 25 / 18 / 0 |
| MBT | 30 | 10 / 10 / 10 / 2 | 9 / 10 / 10 / 1 | 0 (0) | 0 / 0 / 8 | 25 / 27 / 26 / 18 |
| NKD | 16 | 0 / 9 / 7 / 0 | 0 / 9 / 7 / 0 | 9 (7) | 0 / 0 / 0 | 9 / 10 / 10 / 8 |
| BTC | 25 | 3 / 11 / 10 / 2 | 3 / 9 / 8 / 0 | 8 (7) | 0 / 0 / 1 | 13 / 19 / 19 / 9 |
Class C frames (no prices: S4a finalist frames, native books, RV_* pairs; 220 frames) and class E (S4b R-based, 18) are NOT re-costed: their old cost cannot be recovered exactly; a first-pass bound that assumed the whole rt_market_in_stop_out was charged gave implausible revivals (for example the ZN / ZB native books 0 -> 15) and is discarded.
### ES / RTY / NQ (where the measured costs apply)
* **ES** (964 frames): S1 makes non-stop exits 42% cheaper ($29.8 -> $17.3) and stop exits 15% cheaper ($42.3 -> $36.1): gate_v2a frames 6 -> 12 (S2 9, S3 3); 6 frames move up, 3 of them also under S2, none move down. Only 2 become strong (v2a, L6M and HOLD positive) under S1 AND S2: T2F_ES|LRS_nyam_rev_h30|seed0 (n 2,061; L6M +$539 -> +$730 a week, HOLD +$81 -> +$382) and T2F_ES|AC_asia_120m_h21|follow (n 265; L6M +$44 -> +$85, HOLD +$97 -> +$157; published placebo p_book .66, family 1.00). Re-costing does not change the published placebo / family p: those compare the real path with paths that carry the same per-trade cost, so a common cost cut moves both and leaves p where it was. **A cheaper cost lifts the gate flags; it cannot create family-adjusted evidence, so no ES 1-minute label moves toward LEAD.**
* **RTY**: the measured spread (2 ticks) equals the proxy (1 tick per leg): S1 non-stop $14.8 = the proxy, only the frames charged $19.8-$24.8 on non-stop exits gain: gate_v2a 12 -> 15 (S2 7, S3 7); 3 up, 0 down under S1, and under S2 5 of the 12 original gate_v2a frames are lost. RTY is NOT revived: its 1-minute costs were realistic.
* **NQ** (219 frames; 216 are tick-built books that already used measured-scale costs, $9.8-$24.8; 3 are 1-minute LRS frames at $44.8): S1 charges the measured $19.8 round trip and the measured $28.8 stop slip, so it is DEARER than the tick-built frames' own cost; gate_v2a 7 -> 9 only because 2 of the 1-minute LRS frames fall from $44.8 to $19.8, and under S2 it is 6; no NQ label is revived (strong 7 / 9 / 5 / 7).
* **YM, GC, CL, 6E, 6J, MBT, NKD, BTC** (PROXY half-spread): the proxy costs differ most there ($34.8 -> $14.8 for GC / CL non-stop, NKD / BTC $129.8 -> $29.8) and the up-moves are the most numerous (GC 16 up but 3 survive S2; BTC 8 up, 7 survive; NKD 9 up, 7 survive; YM 8 up, 0 survive; CL 4 up, 1 survives) but they rest on an UNMEASURED 1-tick spread and, for NKD / BTC / MBT, on a participation cap below one contract (CAP-BREACH): sensitivities, not revivals.
* **ZN, ZB**: 0 frames gate_v2a at any scenario (ZB $98.6 -> $36.1 does not help: gross is negative).
### FIND_DAILY cells (408 cells through the daily engine; per leg h + fee/2, roll 2h + fee; tolerant yearly gate T1-T4)
Tolerant cells S0 / S1 / S2 / S3 = 36 / 47 / 38 / 30. 11 cells move up under S1: ES day-long book (DAY_L: 13-year net -$10.3k -> +$51.7k, +$8.7k under S2), ES 1-day reversal (MR_k1_th1.5), YM day-long, five NKD cells (day-long, MR_k1_th1, MR_k2_th1.5, TSMOM-252 1-lot and vol), ZN 3 / 5-day reversal (2), MBT weekend long; only 2 are supported under S2 (ES DAY_L, NKD MR_k2_th1.5). Six tolerant cells are lost at 1.5 x the ORIGINAL cost (CL Donchian-20 SAR, CL TSMOM-252 1-lot and vol, GC night long, YM night long, the portfolio MA 20/100); the watch-listed CL Donchian-20 stop-and-reverse cell keeps a positive 13-year net in every scenario (vol lots: $147.9k S1, $146.0k S2, $141.9k S3) but fails the tolerant yearly test at S3. The ES day-long book (09:30 to 15:55 long every day) is equity drift, a beta book, at any cost.
**Plain sentence: the proxy costs were too high for ES (non-stop $29.8 versus a measured $17.3), about right for RTY, probably too high for the unmeasured instruments (by assumption) and too LOW for NQ stops (measured +1.44 pt against 1.0 pt in the proxy). Re-costing lifts the evaluator gate on 6 ES, 16 GC, 8 YM, 8 BTC and 9 NKD frames (6 of 964 ES frames) and drops none under S1, only a few survive the +50% stress, and a common per-trade cost change cannot change placebo or family significance, so NO label moves to LEAD; the substantive changes are (a) the ES 1-minute books are 42% cheaper on non-stop exits, two ES frames (LRS nyam reversal 30 min, AC asia 120 min follow) become gate-clean best-of-F follow-ups, and (b) the NQ stop-market slip should be planned at 1.5-1.7 pt, not 1.0 pt.**
Limits: frames exist only for finalists (cells that never reached a frame cannot be re-costed; a full-grid recost needs the simulators); target exits are costed as market legs (no maker credit; a resting limit target would be cheaper); the stop-exit slip is unmeasured for every instrument except NQ; family p, walk-forward and stack tests are not re-run.
## DAILY-R6 (S4a, 2026-11-06): the FIND_DAILY 34-cell daily-horizon design on the 16 unscored outrights SI HG PL NG RB HO ZF ZT 6B 6A 6C ZC ZS ZW LE HE (IDEAS_ROUND2 R6)
Prereg l2vast/ds3/prereg/DAILY_R6_prereg.md sha256 fb13144effb0b24ed4820c152c333cd3eb8459074d2c558718a517191d776f1b (filed before any statistic; inherits FIND_DAILY bf1de6c6...; per the R5 finding the RANDOM-SIDE null governs trend cells, the shift null is a cross-check). Code l2vast/ds3/code/t2s4a/daily6_lib.py, daily6_run.py, daily6_analyze.py, daily6_follow.py; data /mnt/l2/l2vast/ds3_daily6/ (/mnt/l2 only). Ledger T2F_DAILY6_<SYM> (612 rows), n_tested + 612.
**Set.** The owned 26-outright 1-minute set (data_autopilot/ohlcv1m, .v.0 volume-front with instrument_id, 2013-01..2026-10-14) holds ES NQ RTY YM GC SI HG PL CL NG RB HO ZN ZB ZF ZT 6E 6J 6B 6A 6C ZC ZS ZW LE HE (+ NKD). Already scored in FIND_DAILY: ES RTY YM GC CL ZN ZB 6E 6J NKD; NQ is the live stack. **New: the 16 above; nothing else in the set was uncovered.** Overlap cited, not repeated: T4 Family A (outputs/t4, daily trend book Donchian 20/10-100/50, EMA 20/100, 50/200, 12-month TSMOM, Supertrend on these outrights, sleeve scoring vs the NQ pair), IDEAS50K N7 (weekly-range position, REPORT_N7.md: NO), N10 (cross-sectional daily rank books, candle patterns: 3 gate a-d passes, all one beta bet), N13 (cross-sectional momentum commodities: N13-CSMOM-COMMXX gate a-d True only under an invalid beta null); none of the 34 time-series cells per product is a repeat.
**Repair scan first (DATA_BAD_PRINTS rule).** Bad-bar share by product (max by year): 6A 1.37% (2013), 6C 1.07% (2013), 6B 1.06% (2013), all three below 0.05% from 2016 on (the same early-FX print problem as 6E / 6J, repaired); LE 0.36% (2015) and HE 0.23% (2014); ZW 0.13% (2022); the other ten products at most 0.05% every year. The repaired copy is used. Rolls (volume-front changes, 2013-2026): SI 71, HG 69, PL 55, NG 169, RB 222, HO 179, ZF 57, ZT 55, 6B / 6A / 6C 55 each, ZC 90, ZS 80, ZW 77, LE 121, HE 123.
**Anchors (ET; execution P = open of the anchor bar, signal inputs = bars before it; stated per product) and PROXY specs (not in FEES.md):** SI HG PL 13:25 (COMEX close 13:30; day open Q 08:20); NG RB HO 14:25 (settlement 14:30; Q 09:00); ZF ZT 14:55 (CBOT Treasuries day close 15:00; Q 08:20); 6B 6A 6C 15:55 (24-hour FX; Q 08:20); ZC ZS ZW 14:15 (grain close 14:20; Q 09:30); LE HE 14:00 (livestock close 14:05; Q 09:30). Point value / tick: SI 5000 / 0.005, HG 25000 / 0.0005, PL 50 / 0.1, NG 10000 / 0.001, RB HO 42000 / 0.0001, ZF 1000 / 1/128, ZT 2000 / 1/256, 6B 62500 / 0.0001, 6A 100000 / 0.0001, 6C 100000 / 0.00005, ZC ZS ZW 50 / 0.25, LE HE 400 / 0.025; fee $4.84 RT (PROXY-STD), 1 tick per market leg, roll = 2 slips + one RT fee per held lot. Thin products (PL, LE, HE, ZT) carry a liquidity caveat; margin not in the repository.
**Plain sentence: none of the 16 new outrights yields a daily book: of 578 cells (34 per product x 16 + the 16-product portfolio) 197 are net positive over 13 years, 41 also positive in at least 60% of years, 19 also pass the per-year MDE test and 14 the HOLD test (tolerant: HE 2, HG 1, HO 3, NG 4, SI 1, ZT 1, ZW 1, portfolio 1); the smallest family p of a tolerant cell is 0.78 in the new-set family and 0.92 in the joint family with the 11 earlier instruments (1,000 random-side worlds; the family-maximum null has median 2.90 / 3.03 and p95 3.53 / 3.68), no cell is a LEAD (labels NULL 464, REGIME 130, best-of-F 18 over 612 rows incl. PORT27), and eight of the 13 tolerant instrument cells survive a 1.5x cost stress.**
Funnel and nulls: new-set family 578 cells; random-side maximum z median 2.90, p95 3.53; forward-shift median 2.70, p95 3.47; joint family 1,020 cells (374 earlier + 544 new instrument cells + PORT11 / PORT16 / PORT27): random-side median 3.03, p95 3.68; shift median 2.91, p95 3.65. Truncation audit 0 of 1,296 mismatches.
### Tolerant cells (maxDD first; $ at stated lots, vol lots with 1-lot floor; HOLD $/wk carry-dropped)
| cell | maxDD $ | 13y net $ | years + | HOLD $/wk | z random-side | family p random-side A / B | family p shift A | walk-forward OOS (p) | corr to NQ stack (weekly) | survives 1.5x cost |
|--|--|--|--|--|--|--|--|--|--|--|
| NG MR_k5_th1.5 | 27453 | 69331 | 11/14 | 76 | 2.66 | 0.776 / 0.916 | 0.60 | 45061 (p 0.39) | 0.02 | yes |
| HO NIGHT_L | 56974 | 244468 | 10/14 | 1806 | 2.59 | 0.833 / 0.946 | 1.00 | 114324 (p 0.10) | 0.01 | yes |
| HG TSMOM_L252_vol | 87587 | 114230 | 9/14 | 291 | 1.40 | 1.000 / 1.000 | 1.00 | 33286 (p 0.05) | -0.14 | yes |
| NG TSMOM_L21_1lot | 42301 | 76886 | 9/14 | 102 | 1.30 | 1.000 / 1.000 | 1.00 | 6060 (p 0.49) | 0.00 | yes |
| ZT DON_N100_EX | 36046 | 84139 | 9/14 | 281 | 1.25 | 1.000 / 1.000 | 1.00 | 73591 (p 0.52) | 0.07 | yes |
| ZW MR_k3_th1.5 | 29398 | 8103 | 9/14 | 510 | 1.23 | 1.000 / 1.000 | 1.00 | 7002 (p 0.19) | 0.07 | no |
| HO NIGHT_MOM20 | 60092 | 113942 | 9/14 | 2224 | 1.19 | 1.000 / 1.000 | 1.00 | 114324 (p 0.10) | 0.15 | no |
| SI MR_k1_th1.5 | 69804 | 88594 | 9/14 | 2174 | 1.12 | 1.000 / 1.000 | 1.00 | 50877 (p 0.43) | 0.09 | no |
| NG MR_k2_th1 | 55442 | 35253 | 9/14 | 43 | 1.07 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.03 | no |
| NG MR_k3_th1 | 56052 | 26320 | 9/14 | 111 | 0.94 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.02 | yes |
| HE DON_N40_SAR | 76740 | 52799 | 9/14 | 158 | 0.92 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.04 | no |
| PORT16 MA_50_200 | 548873 | 289523 | 9/14 | 4181 | 0.86 | 1.000 / 1.000 | 1.00 | -167497 (p 0.73) | -0.09 | n/a |
| HE DON_N40_EX | 40490 | 39440 | 10/14 | 232 | 0.82 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.01 | yes |
| HO DON_N100_EX | 139808 | 87274 | 9/14 | 863 | 0.61 | 1.000 / 1.000 | 1.00 | 192586 (p 0.03) | -0.05 | yes |
The portfolio (PORT27 = 11 earlier + 16 new products) has 4 tolerant cells and the 16-product portfolio 1 (MA 50/200, 13-year net $290k, maxDD $549k); the best portfolio family p is 0.15 / 0.26 (PORT27 night long, whose 13-year net is -$4.2M: a cost-eaten leg, below).
### Cross-check with the forward-shift null
Only one of the 612 rows has a shift-null family p <= .10: HE night momentum (z 3.36, p 0.06), with a random-side p of 0.26 and not tolerant; among the tolerant cells the smallest shift p is 0.60. The 6E TSMOM-252 pattern (shift p .005, random-side 1.00) does not recur here, and the random-side null governs.
### Annual-refit walk-forward: 7 of 90 groups positive with p <= .10, none distinguishable from chance after the multiplicity
The 90 groups (16 products + PORT16 + PORT27 x 5 families) are expected to give about 9 with p <= .10; 7 are positive. The smallest p is 0.004, Bonferroni over 90 groups 0.36. Each is dominated by one or two years and has a family p of 1.00 for its cells: p_rand tests whether refit beats a RANDOM parameter pick (many parameter sets in each family lose), not whether the family earns.
| group | OOS total $ | p vs random pick | OOS maxDD $ | OOS Calmar | years + | best year $ | best year share of total | stack dCalmar HOLD / L6M | corr to NQ stack |
|--|--|--|--|--|--|--|--|--|--|
| SI F1 | 182686 | 0.005 | 261083 | 0.07 | 7/10 | 164089 | 0.90 | +0.021 / +0.019 | -0.07 |
| HG F1 | 33286 | 0.046 | 87587 | 0.04 | 6/10 | 35401 | 1.06 | +0.018 / +0.005 | -0.14 |
| NG F3 | 75836 | 0.007 | 61441 | 0.12 | 8/10 | 32283 | 0.43 | +0.000 / +0.000 | +0.05 |
| HO F2 | 192586 | 0.034 | 119920 | 0.16 | 6/10 | 151169 | 0.78 | +0.049 / +0.002 | -0.01 |
| ZF F1 | 93693 | 0.004 | 17482 | 0.54 | 6/10 | 46293 | 0.49 | +0.008 / +0.004 | +0.02 |
| ZT F1 | 86317 | 0.020 | 19691 | 0.44 | 6/10 | 52485 | 0.61 | +0.004 / +0.003 | -0.03 |
| 6B F2 | 6916 | 0.056 | 78300 | 0.01 | 5/10 | 34510 | 4.99 | +0.000 / +0.000 | +0.06 |
ZF and ZT momentum (OOS +$94k and +$86k, maxDD $17-20k, Calmar 0.5) are the best-looking: about half of each comes from 2022 (+$46k and +$52k, the rate sell-off) and 2023-2026 is flat to negative, so they are a one-regime result; SI +$183k is 90% 2025; HO +$193k is 78% 2026.
### Unconditional night / day legs: a real overnight drift in ZS, LE (and mirror cases in HE, 6C) that the costs eat
The random-side null is a gross-drift test for the six constant-sign leg cells (probability 0.5 for the sign). LE night long (z 5.0, family p < .001 in A and B), ZS night long (z 4.3, < .001), 6C night short (z 3.7, 0.03 / 0.06) and HE night long (z 3.4, 0.08 / 0.14) beat the family-maximum null, i.e. the direction of the overnight move is not random, but every one has a NEGATIVE 13-year net at one tick per leg (LE -$68k, ZS -$20k, HE -$107k, 6C -$31k), so none is tolerant. Gross vs net (13 years, vol lots):
| leg | gross $ | net at 1 tick / leg $ | net at 0.5 tick / leg $ (COSTCAL S1 proxy) | cost at 1 tick $ |
|--|--|--|--|--|
| ZS NIGHT_L | +199096 | -19631 | +71994 | +218727 |
| ZS NIGHT_S | -199096 | -417823 | -326198 | +218727 |
| ZS DAY_S | +94082 | -124645 | -33020 | +218727 |
| LE NIGHT_L | +144326 | -68354 | +17266 | +212680 |
| LE NIGHT_S | -144326 | -357006 | -271386 | +212680 |
| LE DAY_S | +92984 | -119696 | -34076 | +212680 |
| HE NIGHT_L | +99200 | -106773 | -23853 | +205973 |
| HE NIGHT_S | -99200 | -305173 | -222253 | +205973 |
| HE DAY_S | +176591 | -29382 | +53538 | +205973 |
| 6C NIGHT_L | -180065 | -391505 | -320265 | +211440 |
| 6C NIGHT_S | +180065 | -31376 | +39864 | +211440 |
| 6C DAY_S | -39440 | -250880 | -179640 | +211440 |
The day leg mirrors the night leg (ZS day short +$94k gross vs night long +$199k; LE +$93k vs +$144k; HE +$177k vs +$99k): the anchor-to-open interval earns, the open-to-anchor interval gives it back. At a half-tick per leg ZS night long would be +$72k over 13 years (about $5.5k a year at 1-2 lots) and LE +$17k: a product-session microstructure effect of a few dollars per lot per day against round-trip costs of $25-30, unmeasured spreads (no order-book table for ZS / LE / HE / 6C), with the ZS evening session as the likely source. Not a book; a candidate for a measured-spread look if 1-s tables for ZS / LE are ever owned.
Limits: costs and specs are PROXY; thin products (PL, LE, HE, ZT) have wider true spreads than one tick; no frames saved (no cell is a lead); the joint family reuses the earlier 1,000-world totals for the 11 instruments (ids 1000-1999, independent of the new ids 2000-2999).
Correction (appended, DAILY-R6): in the unconditional-leg paragraph 'a few dollars per lot per day' should read: gross edge of $30-60 per day at the cells' vol lots (ZS night long $57, LE $42, HE $29) against round-trip costs of $25-30 per lot; and 'the ZS evening session as the likely source' is an untested hypothesis, not a result.
## RATES-MOM STRESS (S4a, 2026-11-06): ZF / ZT daily momentum, stressed like the CL cell - follow-up on best-of-F cells
Prereg l2vast/ds3/prereg/RATES_MOM_STRESS_prereg.md sha256 8ae2c02534d2aeb72d3dd76cb0d02b50ca45f32fd354e27207691822b154fdac (filed before any statistic). Code l2vast/ds3/code/t2s4a/rates_stress.py, rates_stress2.py; results /mnt/l2/l2vast/ds3_daily6/rates_stress_*.pkl, rates_fine.pkl. The engine reproduces the earlier cells (ZF L126 vol 18,713; ZF L252 1-lot 13,402; ZT L252 vol 96,637). Products: ZF, ZT (daily6 builds, anchor 14:55 ET) and ZN, ZB (FIND_DAILY builds, 15:55 ET) as the rates group.
**Plain sentence: the ZF / ZT momentum result is not on a plateau and does not survive the stress: the 13-year profit sits on a narrow band of lookbacks (189-231 days; L = 126, 168 and 252 next to it are flat or weak, and only 2-3 of 8 lookbacks pass the pre-stated Calmar >= 0.10 test, 5 were required), 98-99% of the net of the L189 books comes from their three best trades (the other 74-77 trades sum to about +$1k to +$3k, win rate 29-31%), 76-78% from three years (2022, 2020, 2024 / 2026), the walk-forward OOS drops to +$47k (ZF) and +$34k (ZT) without 2022, and the four rates books are one bet (effective 1.6-1.7 independent bets, P&L correlations 0.4-0.9) whose only significant version (L189, common-flip null p 0.015 before the correction for choosing the best of 8 lookbacks, about 0.12 after) is the post-hoc best lookback. At the lots the vol target implies (5-6 contracts, the cap) the books are worth $0-300 a week against the live stack's $28k, so there is no WATCH spec and nothing for ZL-2 to register.**
### S1 plateau surface (128 cells per product; trailing stop = m x monthly sigma from the best close, flat until the signal flips)
Pre-stated plateau rule on the reference sizing ($1,200 vol lots, no stop): (a) >= 5 of 8 lookbacks with 13-year net > 0 and Calmar >= .10; (b) >= 4 of 8 the same ex-2022; (c) neighbour median Calmar >= 50% of the best cell. Result: ZF a = 2, b = 1, best L189 Calmar 0.34, neighbour median 0.16 (< 0.17): FAIL; ZT a = 3, b = 2, best L189 0.38, neighbours 0.16 (< 0.19): FAIL; ZN a = 2, b = 2, (c) 0.13 vs 0.13 passes but (a) and (b) fail; ZB a = 1, b = 1: FAIL. **No product survives at a plateau.**
**ZF** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.05 | -0.06 | -0.06 |
| 42 | 0.11 | 0.07 | 0.11 | 0.11 |
| 63 | -0.01 | -0.05 | -0.01 | -0.00 |
| 84 | 0.01 | -0.01 | 0.02 | 0.01 |
| 126 | 0.01 | -0.03 | 0.05 | 0.04 |
| 189 | 0.34 | 0.15 | 0.18 | 0.25 |
| 252 | 0.05 | -0.03 | -0.02 | -0.01 |
| 315 | 0.09 | -0.04 | 0.01 | 0.09 |

**ZF** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.05 | -0.06 | -0.06 | -0.06 |
| 42 | 0.11 | 0.11 | 0.10 | 0.09 |
| 63 | -0.01 | -0.01 | -0.02 | -0.02 |
| 84 | 0.01 | 0.01 | 0.00 | 0.00 |
| 126 | 0.02 | 0.01 | 0.02 | 0.02 |
| 189 | 0.31 | 0.34 | 0.44 | 0.44 |
| 252 | 0.02 | 0.05 | 0.08 | 0.08 |
| 315 | 0.08 | 0.09 | 0.14 | 0.14 |

**ZF** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.08 | 0.08 | 0.06 | 0.06 |
| 63 | -0.02 | -0.03 | -0.04 | -0.05 |
| 84 | -0.02 | -0.02 | -0.04 | -0.04 |
| 126 | -0.01 | -0.02 | -0.03 | -0.03 |
| 189 | 0.24 | 0.25 | 0.28 | 0.29 |
| 252 | -0.03 | -0.01 | 0.00 | 0.01 |
| 315 | 0.03 | 0.03 | 0.05 | 0.05 |
**ZT** - Calmar, vol lots $1,200, by trailing stop (columns: none, 1.0, 1.5, 2.0 x monthly sigma):
| L | 0.0 | 1.0 | 1.5 | 2.0 |
|--|--|--|--|--|
| 21 | -0.06 | -0.06 | -0.06 | -0.06 |
| 42 | 0.01 | -0.01 | 0.01 | 0.01 |
| 63 | 0.03 | 0.02 | 0.02 | 0.02 |
| 84 | 0.03 | 0.02 | 0.04 | 0.03 |
| 126 | -0.01 | -0.05 | -0.03 | -0.00 |
| 189 | 0.38 | 0.08 | 0.19 | 0.19 |
| 252 | 0.14 | -0.05 | 0.03 | 0.06 |
| 315 | 0.30 | 0.11 | 0.23 | 0.24 |

**ZT** - Calmar, no stop, by sizing (600 / 1,200 / 2,400 daily-sigma target, 1 lot), full sample:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.06 | -0.06 | -0.06 |
| 42 | -0.02 | 0.01 | 0.03 | 0.03 |
| 63 | 0.03 | 0.03 | 0.01 | 0.00 |
| 84 | 0.00 | 0.03 | 0.04 | 0.05 |
| 126 | -0.01 | -0.01 | -0.00 | -0.00 |
| 189 | 0.34 | 0.38 | 0.40 | 0.40 |
| 252 | 0.13 | 0.14 | 0.17 | 0.18 |
| 315 | 0.28 | 0.30 | 0.32 | 0.33 |

**ZT** - Calmar EX-2022, no stop, by sizing:
| L | 600 | 1200 | 2400 | 1lot |
|--|--|--|--|--|
| 21 | -0.07 | -0.07 | -0.07 | -0.07 |
| 42 | -0.05 | -0.03 | -0.03 | -0.02 |
| 63 | -0.01 | -0.02 | -0.03 | -0.04 |
| 84 | -0.05 | -0.04 | -0.04 | -0.03 |
| 126 | -0.04 | -0.04 | -0.04 | -0.04 |
| 189 | 0.25 | 0.25 | 0.25 | 0.26 |
| 252 | 0.08 | 0.07 | 0.08 | 0.09 |
| 315 | 0.19 | 0.19 | 0.19 | 0.20 |
The trailing stop never helps the L189 cells (ZF Calmar 0.34 -> 0.15 / 0.18 / 0.25, ZT 0.38 -> 0.08 / 0.19 / 0.19), and the Calmar is nearly independent of the sizing target (600 / 1,200 / 2,400 / 1 lot), so the vol scaling is not what drives the result.
**Exploratory finer lookback grid (not part of the pre-stated rule, labelled post-hoc):**
| L | ZF | ZT | ZN | ZB | PORT4 net $k | PORT4 Calmar | PORT4 ex-2022 $k | PORT4 Calmar ex-2022 |
|--|--|--|--|--|--|--|--|--|
| 42 | 0.11 | 0.01 | 0.13 | 0.11 | 299 | 0.12 | 216 | 0.09 |
| 63 | -0.01 | 0.03 | 0.00 | 0.02 | 51 | 0.01 | -35 | -0.01 |
| 84 | 0.01 | 0.03 | 0.00 | 0.02 | 60 | 0.01 | -73 | -0.02 |
| 105 | 0.06 | 0.03 | 0.04 | 0.04 | 194 | 0.04 | 25 | 0.01 |
| 126 | 0.01 | -0.01 | -0.01 | 0.01 | 9 | 0.00 | -160 | -0.03 |
| 147 | 0.06 | 0.05 | 0.06 | 0.07 | 260 | 0.07 | 97 | 0.02 |
| 168 | 0.05 | 0.03 | 0.06 | 0.03 | 181 | 0.05 | 23 | 0.01 |
| 189 | 0.34 | 0.38 | 0.25 | -0.01 | 394 | 0.24 | 253 | 0.17 |
| 210 | 0.22 | 0.37 | 0.15 | -0.01 | 354 | 0.17 | 212 | 0.11 |
| 231 | 0.20 | 0.24 | 0.09 | -0.03 | 250 | 0.10 | 90 | 0.04 |
| 252 | 0.05 | 0.14 | -0.04 | -0.06 | -39 | -0.01 | -201 | -0.05 |
| 273 | 0.03 | 0.09 | -0.04 | -0.05 | -8 | -0.00 | -180 | -0.04 |
| 294 | 0.08 | 0.09 | -0.01 | -0.05 | 81 | 0.02 | -92 | -0.02 |
| 315 | 0.09 | 0.30 | 0.01 | -0.05 | 114 | 0.04 | -58 | -0.02 |
| 378 | 0.07 | 0.17 | 0.02 | 0.00 | 175 | 0.05 | 2 | 0.00 |
The good zone is L = 189-231 for ZF and ZT (ZN positive to 210, ZB never): Calmar 0.2-0.4, flanked by 0.03-0.06 at 168 and 0.05-0.14 at 252; as ONE bet (PORT4 = ZF + ZT + ZN + ZB) Calmar 0.24 / 0.17 / 0.10 at 189 / 210 / 231 and 0.17 / 0.11 / 0.04 ex-2022. It is a band about three lookbacks wide out of fifteen tried, not a plateau.
### S2 per year and regime (reference books, $1,200 vol lots, no stop; $k)
| book | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 | 26 | 13y net | maxDD |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ZF L189 | 3.9 | -11.1 | 11.0 | 4.9 | -19.6 | 13.6 | 17.8 | 35.2 | 9.8 | 46.3 | -1.7 | 27.9 | -12.2 | 15.1 | 140.9 | 29.2 |
| ZF L252 | 0.0 | -11.4 | 8.6 | -15.7 | -14.3 | 2.7 | 10.1 | 35.2 | -7.7 | 46.3 | -0.3 | -2.4 | -23.5 | 10.8 | 38.2 | 57.9 |
| ZT L189 | -1.2 | 6.8 | 6.7 | -5.5 | -0.5 | 5.9 | 5.7 | 26.4 | 1.5 | 52.5 | 2.5 | 20.0 | -9.8 | 24.8 | 135.8 | 25.5 |
| ZT L252 | 0.0 | 6.8 | 5.9 | -1.3 | -1.3 | 4.2 | 1.2 | 27.4 | -0.3 | 52.5 | 2.5 | -7.6 | -18.1 | 24.8 | 96.6 | 49.8 |
| ZN L189 | 3.0 | 4.6 | 0.1 | 4.4 | -24.6 | 23.8 | 26.7 | 21.2 | 12.7 | 33.9 | -7.9 | 22.6 | -3.4 | 15.1 | 132.1 | 36.8 |
Regimes (net $k) 2013-16 / 2017-19 / 2020-22 / 2023-26: ZF L189 8.7 / 11.8 / 91.3 / 29.1; ZF L252 -18.5 / -1.6 / 73.8 / -15.5; ZT L189 6.8 / 11.1 / 80.5 / 37.5; ZT L252 11.3 / 4.1 / 79.6 / 1.6; ZN L189 12.0 / 25.9 / 67.7 / 26.4. The 2013 taper tantrum (May-Sep 2013) is a non-event for L189 / L252 (no position yet: the 189-252 day sign was still flat) and a -$6.8k loss for ZF L126; 2020 pays +$21k to +$35k per book (the COVID rate collapse) and 2022 +$34k to +$53k (the sell-off): 2020-22 is 65-87% of every book's 13-year net.
Ex-2022 and ex-2022-23 (13-year net, Calmar): ZF L189 +$94.6k (0.25) / +$96.3k; ZT L189 +$83.4k (0.25) / +$80.9k; ZN L189 +$98.2k (0.20) / +$106.1k; but ZF L252 -$8.1k, ZF L126 -$27.6k, ZT L252 +$44.2k (0.07), ZT L126 -$65.1k. The walk-forward OOS (annual refit among the 8 TSMOM cells): ZF +$93.7k all years, +$47.4k ex-2022 (Calmar 0.27), +$49.2k ex-2022-23; ZT +$86.3k, +$33.8k ex-2022 (Calmar 0.19), +$31.5k ex-2022-23; the refit picked L126 (ZF, 2018-22) and L252 (ZT) - not the L189 that the surface favours - so the OOS rows and the surface rest on different cells.
### S3 concentration (episodes = runs of constant sign)
| book | episodes | win rate | top-3 trades share of net | net excluding the top 3 | top-3 years share |
|--|--|--|--|--|--|
| ZF L189 | 77 | 29% | 99% | +$1.1k | 78% (2022, 2020, 2024) |
| ZT L189 | 80 | 31% | 98% | +$2.6k | 76% (2022, 2020, 2026) |
| ZT L315 | 54 | 31% | 89% | +$13.4k | 70% |
| ZF L252 | 49 | 27% | 315% | -$83.4k | 242% |
| ZT L252 | 58 | 28% | 127% | -$26.0k | 108% |
### S4 realism: lots, margin, live stack
ZF notional $118k per contract (tick $7.81, daily sigma about $212 per contract); ZT notional $216k per contract (tick $7.81, sigma about $131). The $1,200 daily-sigma target asks for 5.2 ZF and 5.7 ZT contracts on average and sits AT the cap of 6 contracts 58% (ZF) and 82% (ZT) of the days; at $2,400 it is at the cap 97-98% of the days: the 'vol-targeted' books are fixed 6-contract books (ZN 3.6 and ZB 1.6 contracts). Margin is not in the repository: PROXY (T4 assumed ZF $1.5k, ZT $1k per contract, unverified) = $9k and $6k at 6 contracts, notional about $0.7M (ZF) and $1.3M (ZT). Next to the live stack (V2 HOLD $28.2k a week mean, maxDD $91.2k): ZF L189 earns -$73 a week in HOLD, ZT L189 +$162, ZT L252 +$306 (0.6-1.1% of the stack); the stack can absorb k* = 5 books (the search limit) with a Calmar gain of +0.03 to +0.06; weekly correlation to the stack -0.02 to +0.05. Diversifying and immaterial.
### S5 ZF + ZT + ZN + ZB as ONE rates bet
P&L correlations (L189): ZF-ZT 0.77, ZF-ZN 0.84, ZF-ZB 0.58, ZT-ZN 0.61, ZT-ZB 0.39, ZN-ZB 0.75; effective independent bets 1.70 (L189) and 1.59 (L252); the signs agree 87-91% of the days. PORT4 at L189: net $393.9k, maxDD $113.6k, Calmar 0.24, 10 of 14 years positive, +$253.4k ex-2022; at L252: -$39.1k, maxDD $276k. Common-flip null (one shared random sign per calendar month for all four books, 1,000 worlds ids 3000-3999, counts the four as one bet): L189 z 2.14, p 0.015; L252 z 0.22, p 0.40. The L189 result is the best of 8 lookbacks (about 0.12 after the correction) and of a band that the prereg's coarser grid happened to hit.
### S6 regime feature ('momentum works in rates only when the Fed trends')
Causal regime = tercile of |ZT 252-day return| ranked against its own expanding history. P&L by regime tercile (net $k): ZF L189 6.8 (undefined, first 3 years) / 23.8 (low) / 20.7 (mid) / **89.6 (high)**; ZT L189 14.9 / 26.8 / 5.1 / **88.9**; ZN L189 9.1 / 2.0 / 29.1 / **91.8**; ZF L252 2.6 / -24.1 / -28.2 / **+87.9**; ZT L252 16.1 / -2.8 / -7.0 / **+90.4**: 60-100% of every book's profit arrives in the high-trend tercile (1,381 of 3,550 days) - descriptively, the reading holds. It is not usable causally: trading only when the regime is above its expanding median LOWERS the L189 books (ZF 140.9k -> 83.3k, ex-2022 +37.0k with Calmar 0.08; ZT 135.8k -> 86.3k, ex-2022 +33.8k, Calmar 0.07; ZN 132.1k -> 103.5k, ex-2022 Calmar 0.18) because the 252-day filter switches on after the trend began, and helps only the L252 books (ZF 38.2k -> 63.1k, ex-2022 +16.8k; ZT 96.6k -> 89.2k); the walk-forward with the on/off switch as an extra candidate gives no gain (ZF OOS +$118.0k vs +$132.2k without the switch; ZT +$96.1k vs +$96.1k). The pre-stated usability test (conditioned book keeps Calmar >= .10 ex-2022 and the WF OOS ex-2022 stays positive) is met only by ZN. **The regime is a description of where the P&L was, not a feature the walk-forward can use.**
### Verdict and next step
Plateau rule failed for ZF, ZT, ZN and ZB; ex-2022 the surviving cells are the post-hoc L189 band; the one-bet significance (p 0.015) does not survive the choice among 8 lookbacks; the economics are $0-300 a week against a $28k stack. **Label: best-of-F, REGIME-concentrated (2020-22), cells on a narrow ridge. No WATCH_ZF_MOM_SPEC.md is written and ZL-2 has nothing to register.** A genuinely new, separately preregistered test would be the only way to use the L189-231 band (the 2023-2026 years are +$29k to +$38k for the L189 books, so the band is not dead out of sample, but 2023-26 contains the band's own selection).
Corrections (appended, RATES-MOM STRESS): (1) '2020-22 is 65-87% of every book's net' should read 51% (ZN L189), 59% (ZT L189), 65% (ZF L189), 82% (ZT L252), 193% (ZF L252, whose other years net negative). (2) The 2013 taper tantrum cannot be tested for lookbacks >= 189 days: the series starts 2013-01-02, so these books have no signal until about October 2013 (warm-up, not a flat sign); only ZF L126 (-$6.8k, May-Sep 2013) and ZB L42 (-$6.1k) saw it. (3) '60-100% of every book's profit arrives in the high-trend tercile' should read 64% (ZF L189), 65% (ZT L189), 69% (ZN L189), 94% (ZT L252) and 230% (ZF L252). (4) The L189 books' 2023-26 net is +$26k to +$38k (ZN 26.4, ZF 29.1, ZT 37.5).


## REPAIRED-RATES-CRYPTO (ZL-1, 2026-11-06): ZN, ZB, MBT, BTC, NKD (+ the GC block B survivors) re-run on CHAR-C's repaired 1-minute bars (cc_audit v1; paths and sha256 in autopilot/REPAIRED_BARS_PATHS.md)
Method: every pipeline re-run END TO END on repaired copies of its own feed through source copies in l2vast/ds3/code/rr/ (originals, ledgers, trade-frame stores and pages untouched; outputs under /mnt/l2/l2vast/rr_*): LRS (find_lrs_rep), my native books (rr_native_*), BASE-4 block B (rr_base4), Z3 ZN/ZB (rr_z3, own repaired instr2_z3 files: ZN 565 / ZB 583 bad bars, matching the audit), S4b crypto / NKD grids + cluster (rr_t2). Per-cell tables: L6M / HOLD / PRE / X' = $/week at the pipeline's own lots (carry weeks dropped; S4b grids: mean R per trade), original -> repaired.

### Summary per pipeline
| pipeline | what | original | repaired | flips |
|--|--|--|--|--|
| LRS ZN | candidates / best joint z / best p_family / clears | 648 / 2.58 / 0.279 / 0 | 648 / 2.70 / 0.269 / 0 | cell-level z correlation orig vs rep 0.47 (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS ZB | candidates / best joint z / best p_family / clears | 648 / 2.65 / 0.274 / 0 | 648 / 2.52 / 0.378 / 0 | cell-level z correlation orig vs rep 0.52 (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS MBT | candidates / best joint z / best p_family / clears | 648 / 1.97 / 0.836 / 0 | 648 / 1.79 / 0.960 / 0 | cell-level z correlation orig vs rep 0.41 (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS BTC | candidates / best joint z / best p_family / clears | 486 / 0.00 / 1.000 / 0 | 486 / 0.00 / 1.000 / 0 | cell-level z correlation orig vs rep nan (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS NKD | candidates / best joint z / best p_family / clears | 484 / 0.00 / 1.000 / 0 | 486 / 0.00 / 1.000 / 0 | cell-level z correlation orig vs rep nan (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS BTC_CAPBREACH | candidates / best joint z / best p_family / clears | 486 / 2.37 / 0.318 / 0 | 486 / 2.79 / 0.080 / 0 | cell-level z correlation orig vs rep 0.35 (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| LRS NKD_CAPBREACH | candidates / best joint z / best p_family / clears | 484 / 2.14 / 0.542 / 0 | 486 / 2.11 / 0.622 / 0 | cell-level z correlation orig vs rep 0.47 (the learned-rule search is unstable at the cell level to 0.01% bar repairs; family verdict unchanged) |
| native MBT | cells / NOW-ONLY / tolerant / finalists passing the evaluator gate | 2304 / 283 / 134 / 4 | 2304 / 283 / 134 / 4 | tolerant flips 0, NOW-ONLY flips 0 |
| native BTC | cells / NOW-ONLY / tolerant / finalists passing the evaluator gate | 2304 / 453 / 318 / 8 | 2304 / 453 / 318 / 8 | tolerant flips 0, NOW-ONLY flips 0 |
| native NKD | cells / NOW-ONLY / tolerant / finalists passing the evaluator gate | 552 / 126 / 50 / 0 | 552 / 126 / 47 / 0 | tolerant flips 3, NOW-ONLY flips 0 |
| block B MBT_B | scored / tolerant / tolerant with p_book <= .10 / family-surviving | 2052 / 55 / 9 / 0 | 2052 / 57 / 9 / 0 | see survivor table |
| block B GC_B | scored / tolerant / tolerant with p_book <= .10 / family-surviving | 3840 / 392 / 42 / 0 | 3840 / 397 / 35 / 0 | see survivor table |
| Z3 ZN | stage A rows / screen-gate passers / L3M+L6M+HOLD all positive / stage-B gate rows | 5426 / 8 / 57 / 315 | 5426 / 7 / 50 / 333 | 32 finalist cells re-evaluated: 0 gate flips (all FAIL both) |
| Z3 ZB | stage A rows / screen-gate passers / L3M+L6M+HOLD all positive / stage-B gate rows | 5426 / 3 / 30 / 332 | 5426 / 3 / 14 / 339 | 32 finalist cells re-evaluated: 0 gate flips (all FAIL both) |
| S4b MBT grid | cells / tolerant / clear (gate + persistence) | 144396 / 2120 / 102 | 144480 / 2170 / 107 | tolerant flips 132, clear flips 7 |
| S4b BTC grid | cells / tolerant / clear (gate + persistence) | 144480 / 1723 / 25 | 144480 / 1701 / 20 | tolerant flips 114, clear flips 9 |
| S4b BTCM grid | cells / tolerant / clear (gate + persistence) | 144312 / 1359 / 119 | 144312 / 1374 / 118 | tolerant flips 119, clear flips 9 |
| S4b NKD grid | cells / tolerant / clear (gate + persistence) | 144564 / 102 / 0 | 144564 / 102 / 0 | tolerant flips 0, clear flips 0 |

**Plain sentence (REPAIRED-RATES-CRYPTO): re-running every ZN, ZB, MBT, BTC and NKD pipeline of mine / BASE-4 / Z3 / S4b on CHAR-C's repaired bars moves no label, no gate verdict that mattered and no frozen spec: the Z3 rates books stay DEAD (ZN screen-gate passers 8 -> 7, ZB 3 -> 3, all 32 finalist cells FAIL before and after), the native books keep the same tolerant sets (MBT 134 -> 134, BTC 318 -> 318, NKD 50 -> 47) and the same finalists, block B keeps 0 family-surviving cells (MBT_B 9 -> 9 per-cell survivors, GC_B 42 -> 35 per-cell survivors, tolerant 392 -> 397), the S4b crypto grids change by 0-2.4% of their tolerant cells (MBT 2,120 -> 2,170, BTC 1,723 -> 1,701, BTCM 1,359 -> 1,374, NKD 102 -> 102) with the clear-cell sets moving by 7-9 cells each, and the learned-rule search stays at 0 clears in all seven series (BTC CAP-BREACH best p_family .318 -> .080, still no clear); the MBT Asia Keltner spec (WATCH_BTCM_KELTNER_SPEC.md, sha256 b82f1d44533083113644e8f11dc0f9aa19f732df141940a3b59641a2497bb8d9) is untouched: its PRIMARY cell has the same n = 164, net mean R +0.151 (t 2.000 -> 1.999) and identical L6M +0.341, HOLD +0.285, MID +0.184, PRE +0.174, X' -0.108 on the repaired bars (secondary S1 +0.164 -> +0.159, S2 identical, S3 +0.103 -> +0.106).** What does move: (a) the learned-rule search is chaotic at the cell level (cell-level joint-z correlation .35-.52 between the original and repaired runs and the same three finalists lose or gain several hundred dollars per week, e.g. ZN gp h60 pre L6M +155 -> -1,401), a property of the method, not of the bars; (b) GC block B loses 7 of its 42 per-cell survivors (p_book above .10 after repair) and keeps none family-surviving; (c) the GC finding quoted on my GC page (493 -> 475 gate passers, PRE -270 -> -337) is the same effect and stays as reported there.

Full per-cell tables (LRS finalists, block B survivors, Z3 finalists, native finalists, S4b top cells): autopilot/REPAIRED_BARS_RERUN.md, block of the same title. Code: l2vast/ds3/code/rr/ (mk_rr_*.py, run_rr_z3.py, cmp_*.py, assemble_rr.py); outputs /mnt/l2/l2vast/{find_lrs_rep,rr_native_*,rr_base4,rr_z3,rr_t2}/.
