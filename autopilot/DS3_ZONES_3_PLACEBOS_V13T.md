# DS3_ZONES_3_PLACEBOS_V13T - V13T_LIVE phase-averaged placebos, equal-risk, carrying-episode drop, 30-chain walk-forward

Shadow only. No PASS claims. Z3, 2026-11-02. Base V13T_LIVE (lock none, xcost 0.80). Table: out/zones3/s3_v13tl/placebos_tl_table.csv; scripts placebos_tl.py, tl_plc_an.py, wf11b.py, wf11b_an.py (l2vast/ds3/code/zones3_s3).

## Method
- 12 leads, each REAL plus 100 stratified same-count random masks (same row count per book x session x td-bin x side stratum; skip -> random skip, half -> random half, layer replacement -> random layer), each run as a full engine composite at 3 week-key shifts (-4,0,4) (K=3, not 5/9, for time), cut vs shipped layer at the same shift, averaged.
- rank = share of the 100 placebo draws strictly beaten by the real PA cut (0.95 needed in L6M and in PRE or X').
- Equal-risk: lot-table scale found so the ALL-window worst-20 equals shipped (gap within 3%); cut then measured at shift 0 against shipped.
- Carrying-episode drop: L6M cut recomputed after removing ISO weeks 202629-202639 (W29-W39) from both series.
- Gates: band = 2%-flip PA9 band (L6M .188, PRE .078, X' .145, MID .212); no-harm = PRE and MID cut >= minus band.
- sopen40 "size-matched null" = the same-count (about 55% of rows) random half-lot mask.

## Results (PA cut vs shipped; rank / placebo mean in brackets)
| lead | L6M | HOLD | MID | PRE | X' | L6M drop W29-39 | ER L6M / PRE / X' | band | no-harm | rank>=.95 |
|---|---|---|---|---|---|---|---|---|---|---|
| EQL_tight 5m D40 skip | .399 (1.00/.037) | .152 (.97) | -.096 | .016 (.66) | -.212 (.09) | -.050 | .278 / -.094 / -.081 | no | yes | no (PRE .66, X' .09) |
| S5 sopen40 half (size-matched null) | .239 (.29/.329) | .161 (.25) | -.010 | .359 (.99/.105) | -.112 | .458 | .068 / .139 / -.163 | yes | yes | no (L6M .29) |
| S5 sA40>=1 skip | .472 (.85/.216) | .472 (.94) | .227 | .145 (.70) | -.619 (.08) | .044 | .378 / .011 / -.434 | yes | yes | no |
| S5 nA60>=1 skip | .473 (.78) | .473 (.92) | .195 | .071 (.52) | -.621 (.12) | .046 | .343 / -.212 / -.839 | no | yes | no |
| S5 rho60>=2 skip | .430 (.84) | .430 (.95) | .288 | -.135 (.18) | .010 | -.032 | .343 / -.234 / .040 | no | no | no |
| ZL-3 G2 TVP-conf skip Dl60 | .509 (.94/.225) | .320 | .420 | -.143 (.18) | .117 (.83) | .116 | .440 / -.122 / .159 | no | no | no |
| SWG f3L 15s D40 half | .234 (.34) | .104 | -.089 | -.040 | -.026 | .377 | .174 / -.280 / .066 | no | yes | no |
| ARR iplFVG 15s D20 skip | .295 (.63) | .241 | -.240 | -.264 (.15) | .008 | -.274 | .233 / -.263 / .001 | no | no | no |
| DEV on_L D20 half | .224 (.78) | .216 (.96) | .312 (.98) | -.095 (.45) | .295 (.97) | .267 | .139 / -.014 / .274 | yes (X') | no (PRE -.095) | no (L6M .78) |
| Z2 CRT4h 60 fw2 any (layer) | .224 (.75/.086) | .208 | .092 | -.003 (.73) | .052 (.35) | .038 | .365 / -.001 / .202 | no | yes | no |
| S4a SWG f5L 3m D20 half | .258 (.66) | .220 | .110 | .116 (.88) | .182 (.81) | .061 | .281 / .074 / .361 | yes | yes | no (L6M .66, PRE .88, X' .81) |
| FIB ret62 15m D20 skip | .161 (.83) | .161 | .302 | .013 | .341 (1.00) | .027 | .153 / -.032 / .416 | no (L6M < .188) | yes | no (L6M .83) |
(Cells in brackets: L6M/PRE/X' show rank/placebo mean where given; full values in the CSV.)

## Reading
- No lead has rank >= 0.95 in L6M together with PRE or X'. Verdict: no survivor, nothing RISK-KEEP (unchanged).
- EQL_tight: L6M rank 1.00 and equal-risk cut +.28, but the cut is carried by W29-W39 (L6M cut after drop -.05) and PRE/X' show nothing (X' -.21): ONE-EPISODE.
- sA40 / nA60: pass the band gate (sA40) and no-harm, but rank .85/.78 and the cut collapses to +.04/.05 without W29-W39, X' -.62: ONE-EPISODE, FRAGILE in X'.
- sopen40: L6M cut .239 is below the same-size random half mask (placebo mean .329, rank .29): VOLUME, as on V13Y. PRE rank .99 but L6M fails.
- SWG f5L 3m D20 half (new): passes band and no-harm, equal-risk positive in all three windows, but rank .66/.88/.81 and drop-W29-39 cut +.06 (from +.26): not distinguished from a random half mask of the same size, and mostly the one episode. Best of the new leads on the sign-consistency criterion; still a lead only.
- FIB ret62 D20 skip (new): X' rank 1.00 (+.34, equal-risk +.42) but L6M +.16 is below band (rank .83) and PRE ~0: X'-ONLY lead.
- Z2 CRT4h 60 fw2 any: L6M +.22 (rank .75, below band for rank), equal-risk L6M +.37, PRE ~0; episode drop +.04: not a survivor; sign-consistent, no harm.
- DEV on_L: rank .78 in L6M, harms PRE (-.095 < -.078): fails no-harm.
- G2: L6M rank .94 (just below .95), but harms PRE (-.143) and no support in PRE: fails no-harm; carrying-episode drop leaves +.12.
- Caveats: K=3 shifts (placebo SD between draws is large; rank resolution .01); the ER cut is at shift 0 only; placebos are count-matched per stratum but not volume- (lot-) matched except sopen40.

## Walk-forward with 30 random chains (V13T_LIVE, lock none)
Cut vs shipped fixed layer: WF6 L6M -.592 (rank 0.03 vs 30 random chains, random mean -.13), WF12 L6M -.831 (rank 0.00); PRE -.078/-.075 (rank .53); WF window -.444/-.661 (rank .03/.00); shrink variants ~0 (collapse to shipped). Monthly refit is worse than the fixed layer and worse than random monthly picks in L6M/HOLD/WF; PRE is no different from random picks. Verdict stands: the refit does not beat the fixed layer.

## 9-shift placebos (appended 2026-11-02 ~17:20Z; K=9 week shifts, 100 stratified draws each)
Script tl_plc9_an.py, table out/zones3/s3_v13tl/placebos_tl9_table.csv. Same method as above with all 9 shifts for the cell and each draw.
| lead | L6M (rank / placebo mean) | HOLD rank | MID (rank) | PRE (rank) | X' (rank) | L6M drop W29-39 | band | no-harm | rank>=.95 |
|---|---|---|---|---|---|---|---|---|---|
| EQL_tight 5m D40 skip | .385 (1.00 / .037) | .242 (1.00) | -.076 (.64) | .051 (.81) | -.184 (.17) | -.047 | no | yes | no |
| S5 sA40>=1 skip | .502 (.85 / .260) | .502 (.93) | -.323 (.52) | .219 (.79) | -.585 (.05) | +.068 | yes | NO (MID -.32) | no |
| S4a SWG f5L 3m D20 half | .282 (.75 / .153) | .256 (.90) | -.125 (.60) | .086 (.83) | .176 (.83) | +.051 | yes | yes | no |
Firmed-up reading (the 3-shift ranks were coarse): ranks move by at most 0.1; no lead reaches .95 together in L6M and PRE/X'. sA40 now fails no-harm at K=9 (MID -.32). EQL_tight keeps L6M/HOLD rank 1.00 but its PRE rank is .81, X' -.18 (rank .17) and the W29-W39 drop makes it -.05: one-episode. SWG f5L 3m keeps all three windows positive (L6M .28, PRE .09, X' .18) but ranks .75/.83/.83 and +.05 without W29-W39: lead only. CRT4h 60 fw2, FIB ret62 and BT swing flip 9-shift placebos are running (placebos_tl9b); results to be appended.
