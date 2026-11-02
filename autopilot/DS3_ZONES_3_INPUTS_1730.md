# DS3_ZONES_3_INPUTS_1730 - Z3 inputs for DS3_ZONES_3.md (V13T_LIVE)

Shadow only. No PASS claims. Z3 (T-ZONES-3 s3), written 2026-11-02 for the 17:30Z checkpoint. Base V13T_LIVE = V13Z with lines empty, lock none (per-book locks only, the headline frame), lockfix legs, xcost 0.80, stopcost 2.45, tshort 0. Cap 2026-10-31. Rank-don't-kill; the user picks.

## 1. One sentence per family
- Zone layer as shipped (8 lines, HALF at D20 on 7 lines, OTE-62 B73 D30): not distinguishable from 100 random same-size half layers in any window (rank .23-.79) and with no equal-risk edge; only PRE is nominally better (+.107 vs band .078, rank .79).
- Actions per line (skip / re-target / half / B73 / WT / delay / rest-behind): 0 of 182 cell-frames pass on the earlier bases (V13Y report); the V13T_LIVE re-run covers the layer, the lead cells and the walk-forward, not the full 182-cell grid.
- Walk-forward (monthly refit, 30 random chains): worse than the fixed layer (WF6 L6M -.59 rank .03, WF12 -.83 rank .00); shrink variants collapse to the shipped layer.
- Skip masks from other programs (EQL_tight, S5 sA40/nA60/rho60, ZL-3 G2, ARR iplFVG): large L6M cuts, carried by W29-W39 and/or harmful in PRE/X'; none survives.
- Half-lot masks (sopen40, SWG f3L/f5L, DEV on_L): volume or episode-carried; SWG f5L 3m is the most consistent lead but is a lead only.
- Layer replacements (Z2 CRT4h 60 fw2 any, camH3, PDmid): sign-consistent, no harm, below band or rank; CRT4h V13T_LIVE reconciliation by Z2 pending (DS3_ZONES_3_S2_CRT4H_V13TLIVE.md) - add when it lands.
- Noise: single-path maxDD cuts of up to +-20-55% arise from information-free perturbations; the phase-averaged band (n=100) is L6M .188/.219 (flip 2%/5%).

## 2. Every lead on V13T_LIVE (PA cut vs shipped; K=9 for cut and band gate, K=3 for placebo rank, 100 draws)
Band (flip 2%): L6M .188, PRE .078, X' .145, MID .212. no-harm: PRE and MID >= minus band. ER = equal-risk cut at shift 0 (L6M/PRE/X'). Drop = L6M cut without W29-W39.
| lead | L6M | PRE | X' | MID | rank L6M / PRE / X' | ER L6M / PRE / X' | drop W29-39 | band | no-harm | label |
|---|---|---|---|---|---|---|---|---|---|---|
| NONE (layer off) | .024 | -.128 | .009 | .030 | - | - | - | no | no | n/a |
| BT swing flip D40 (ZL-1) | .142 | .066 | .082 | -.089 | not run | - | - | no | yes | NOISE |
| LP_AGAINST natural | -.005 | .012 | -.175 | -.035 | not run | - | - | no | yes | NOISE |
| LP any-side A40 TLP p25 4h | .130 | .030 | -.150 | -.084 | not run | - | - | no | yes | NOISE |
| EQL_tight 5m D40 skip | .385 / .399 | .051 / .016 | -.184 / -.212 | -.076 / -.096 | 1.00 / .66 / .09 | .278 / -.094 / -.081 | -.050 | no (PRE/X') | yes | ONE-EPISODE |
| camH3 40 fw8 any | .036 | -.053 | -.094 | .003 | not run | - | - | no | yes | NOISE |
| PDmid 40 fw1 stk | -.038 | .015 | .093 | -.001 | not run | - | - | no | yes | NOISE |
| S5 sopen40 half | .192 / .239 | .348 / .359 | -.160 / -.112 | -.200 / -.010 | .29 / .99 / .21 | .068 / .139 / -.163 | .458 | yes | yes | VOLUME |
| S5 sA40>=1 skip | .502 / .472 | .219 / .145 | -.585 / -.619 | -.323 / .227 | .85 / .70 / .08 | .378 / .011 / -.434 | .044 | yes | yes (K=3) | ONE-EPISODE |
| S5 nA60>=1 skip | .504 / .473 | .126 / .071 | -.595 / -.621 | -.377 / .195 | .78 / .52 / .12 | .343 / -.212 / -.839 | .046 | yes (K=9) | no (K=9) | ONE-EPISODE / FRAGILE |
| S5 rho60>=2 skip | .469 / .430 | -.045 / -.135 | .025 / .010 | -.176 / .288 | .84 / .18 / .67 | .343 / -.234 / .040 | -.032 | L6M only | no (K=3) | L6M-ONLY |
| ZL-3 G2 TVP-conf skip Dl60 | .525 / .509 | -.071 / -.143 | .092 / .117 | .214 / .420 | .94 / .18 / .83 | .440 / -.122 / .159 | .116 | L6M only | no (K=3) | L6M-ONLY |
| SWG f3L 15s D40 half | .239 / .234 | -.001 / -.040 | -.089 / -.026 | -.041 / -.089 | .34 / .23 / .65 | .174 / -.280 / .066 | .377 | L6M only | yes | VOLUME |
| ARR iplFVG 15s D20 skip | .337 / .295 | -.340 / -.264 | .039 / .008 | -.562 / -.240 | .63 / .15 / .61 | .233 / -.263 / .001 | -.274 | L6M only | no | FRAGILE |
| DEV on_L D20 half | .187 / .224 | -.130 / -.095 | .299 / .295 | .260 / .312 | .78 / .45 / .97 | .139 / -.014 / .274 | .267 | X' only | no | FRAGILE |
| ALL7 skip | .142 | .059 | -.197 | -.694 | not run | - | - | no | no | HARM |
| Z2 CRT4h 60 fw2 any (layer) | .224 | -.003 | .052 | .092 | .75 / .73 / .35 | .365 / -.001 / .202 | .038 | no | yes | LEAD (sign-consistent; Z2 reconciliation pending) |
| S4a SWG f5L 3m D20 half | .258 | .116 | .182 | .110 | .66 / .88 / .81 | .281 / .074 / .361 | .061 | yes | yes | LEAD (best consistency; rank < .95) |
| FIB ret62 15m D20 skip | .161 | .013 | .341 | .302 | .83 / .70 / 1.00 | .153 / -.032 / .416 | .027 | no (L6M) | yes | X'-ONLY LEAD |
Where two numbers are shown: K=9 value / K=3 value. Sources: DS3_ZONES_3_V13T_LIVE.md, DS3_ZONES_3_PLACEBOS_V13T.md, out/zones3/s3_v13tl/{leads_tl_table.csv,placebos_tl_table.csv}.

## 3. Survivors
None. Nothing is RISK-KEEP. No lead has rank >= 0.95 in L6M together with PRE or X' plus band, no-harm and equal-risk. Leads worth keeping in the queue (sign-consistent, no harm): SWG f5L 3m D20 half, Z2 CRT4h 60 fw2 any, FIB ret62 15m D20 skip (X'-only). A 9-shift placebo re-run for sA40, EQL_tight and SWG f5L 3m is in progress (out/zones3/s3_v13tl/placebos_tl9_*.pkl).

## 4. The user's decisions that shape this (relayed by the Lead)
- Cap 2026-10-31 (old-cap results are labelled OLD CAP).
- Base ladder re-based to V13T / V13T_LIVE; earlier bases (v1.2, v1.3-assumed, V13X, V13Y, V13Z) are labelled defect or assumed.
- Headline frame lock none (per-book locks); combined 12R stack lock is reference only, not live.
- Purged walk-forward and the phase-averaged noise band are the headline evidence; rank, don't kill; Shadow only; no PASS claims.

## 5. Changes from V13Y
| item | V13Y | V13T_LIVE |
|---|---|---|
| band PA 2% flip L6M / PRE / X' / HOLD / MID | 15.7 / 11.4 / 15.9 / 14.5 / 26 % | 18.8 / 7.8 / 14.5 / 18.2 / 21.2 % |
| band PA 5% flip | 19.9 / 17.4 / 23.0 / 19.1 / 37 % | 21.9 / 9.9 / 18.2 / 20.5 / 32.2 % |
| shipped layer vs random layers | indistinguishable in L6M/HOLD, better in PRE | indistinguishable everywhere (ranks .23-.79) |
| EQL_tight | X' lead (+26 %, rank .99) | L6M +.40 but one-episode, X' -.21 |
| sopen40 | VOLUME + equal-risk harm | VOLUME (below same-size random half) |
| SWG f3L | VOLUME, PRE +15 % | VOLUME, PRE ~0 |
| walk-forward | fails | fails (30 random chains) |
| survivors | none | none |
Caveat: lead placebos use K=3 shifts; ranks have resolution about .01 but the draw-to-draw SD is large; a 9-shift re-run for three leads is running.
