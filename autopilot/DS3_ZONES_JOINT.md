# DS3_ZONES_JOINT - the ZONE layer in the joint stage and the eight-line leave-one-out (T-NEXT B1 + B3; 2026-11-11 08:42Z)

**ROLL-FIXED (ROLLFIX1), PRE-PROOF, post-hoc, Shadow only, NO PASS CLAIMS. Standing rules 1/2/2a: the zone layer stays ON; recents first; bi-weekly WF; PRE tolerance per Z.prior_info.** Exact-queue pause 17:15Z-21:30Z (user order T-TRAIL-L2 v2).

## B3. The eight live lines: leave-one-out (exact, ROLLFIX1; cut vs the live layer on the ROLLFIX1 base; + = the layer is shallower WITHOUT the line, i.e. the line HURTS; - = the line HELPS)

| line left out | months | decisions changed (hook) | L1M/L3M/L6M cut | HOLD cut | PRE cut | X' cut | d mean $/wk L6M/PRE | verdict |
|---|---|---|---|---|---|---|---|---|
| PD_mid | 14 | 31 of 7254 checks | 0/0/0 |  |  |  | 4/ | pending (windows incomplete) |
| RTH_camH3 | 14 | 61 of 7263 checks | -3/-4/-4 |  |  |  | 283/ | pending (windows incomplete) |
| Kijun_1h | 14 | 50 of 7257 checks | -3/-3/-3 |  |  |  | 136/ | pending (windows incomplete) |
| CRT_mid_4h | 14 | 102 of 7241 checks | 0/0/0 |  |  |  | 296/ | pending (windows incomplete) |
| KC_up_4h | 14 | 43 of 7050 checks | 0/0/0 |  |  |  | -53/ | pending (windows incomplete) |
| OTE62_15m | 14 | 477 of 7571 checks | 0/0/0 |  |  |  | -948/ | pending (windows incomplete) |
| OTE705_15m | 14 | 98 of 7252 checks | -5/-7/-7 |  |  |  | -69/ | pending (windows incomplete) |
| OTE79_15m | 14 | 171 of 7235 checks | 0/0/0 |  |  |  | 679/ | pending (windows incomplete) |

**Proposed line set (panel string, v1.6 field NtzLines; v1.5 has the eight lines as PoiSet families):** `NtzLines=`; lines that HURT on the exact windows: none so far. This is advisory: every line stays in the live layer until an exact joint row with the placebo and walk-forward gates beats the full eight-line layer (standing rule: the layer stays ON; no PASS claims).

### B3 FIRST-ORDER fallback (flagged: NOT exact; replay agrees with the live half on ~88% of informative trades; B73 path of OTE-62 not modelled)

| line left out | trades only this line triggers (un-halved) / eligible checks | cut L6M/HOLD/PRE/X' (vs live) | d mean L6M $/wk | reading |
|---|---|---|---|---|
| PD_mid | 42 / 285 | 0/0/0/-0 | -59 | neutral / mixed |
| RTH_camH3 | 139 / 388 | -9/0/0/-12 | 319 | HELPS (removal deepens maxDD) |
| Kijun_1h | 66 / 405 | -3/0/-2/-1 | 127 | HELPS (removal deepens maxDD) |
| CRT_mid_4h | 119 / 522 | 0/2/0/5 | -167 | HURTS (removal shallows maxDD) |
| KC_up_4h | 59 / 229 | 0/0/0/3 | -108 | neutral / mixed |
| OTE62_15m | 29 / 772 | 0/0/-1/0 | -81 | neutral / mixed |
| OTE705_15m | 85 / 757 | -2/-4/0/-5 | -196 | HELPS (removal deepens maxDD) |
| OTE79_15m | 160 / 813 | 0/-3/0/7 | 529 | neutral / mixed |


## Registry (ZONE layer top-K, every candidate; per-trade exact tables in /mnt/l2/l2vast/_th_joint/layers/zone/)

| id | kind | exact status | months present | what |
|---|---|---|---|---|
| LIVE_ZONE | state_rule | EXACT, 43 months | 43 | live zone layer = PoiSet HALF D20 (PD_mid RTH_camH3 Kijun_1h CRT_mid_4h KC_up_4h OTE62/705 |
| ZNA_OPEN20 | zone_set | EXACT partial: 14 of 43 months | 14 | HALF cell open20 (no untouched PoiSet line within 20 pts either side -> halve) |
| ZNA_OPEN40 | zone_set | EXACT partial: 14 of 43 months | 14 | HALF cell open40 |
| ZNA_OPEN60 | zone_set | EXACT partial: 13 of 43 months | 13 | HALF cell open60 |
| ZNA_OPENA40 | zone_set | EXACT partial: 13 of 43 months | 13 | HALF cell openA40 (ahead only) |
| ZNA_OPENA60 | zone_set | EXACT partial: 13 of 43 months | 13 | HALF cell openA60 |
| ZNA_SOPEN40 | zone_set | EXACT partial: 13 of 43 months | 13 | HALF cell sopen40 (y = 40*E/20000) |
| ZS_C0 | zone_set | EXACT partial: 39 of 43 months | 39 | ZN-STRUCT swing level skip (London), sw5_5 v23 hw2 pt5 BA |
| ZS_D0 | zone_set | EXACT partial: 39 of 43 months | 39 | ZN-STRUCT bbup_5 quarter London |
| ZS_E0 | zone_set | EXACT partial: 33 of 43 months | 33 | ZN-STRUCT family E top |
| ZNC_A0 | zone_set | EXACT partial: 39 of 43 months | 39 | ZN-CORE family A ldnl skip London |
| ZNC_B0 | zone_set | EXACT partial: 39 of 43 months | 39 | ZN-CORE family B skip London |
| ZNB_F00 | zone_set | QUEUED | 0 | ZN-BOOK ice_w600_n1 quarter PE |
| ZNA_DELAY_A | zone_set | EXACT partial: 3 of 43 months | 3 | delay-until-through, family A level ahead <= 20 pts |
| ZNA_DELAY_B | zone_set | EXACT partial: 3 of 43 months | 3 | delay-until-through, family B |
| ZNA_RET_A | zone_set | EXACT partial: 3 of 43 months | 3 | re-target to level -0.5 (A) |
| ZNA_RET_B | zone_set | EXACT partial: 3 of 43 months | 3 | re-target to level -0.5 (B) |
| ZNA_RETB_A | zone_set | EXACT partial: 3 of 43 months | 3 | re-target beyond level +5 (A) |
| ZNA_STOP_A | zone_set | EXACT partial: 3 of 43 months | 3 | structure stop behind level, equal $ risk (A) |
| ZNA_B73_A | zone_set | EXACT partial: 3 of 43 months | 3 | generalised B73 at level (A) |
| ZNA_COOL_A | zone_set | EXACT partial: 3 of 43 months | 3 | cooldown 15 min after lost level (A) |
| ZNA_L_PD_mid | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line PD_mid left out (leave-one-out) |
| ZNA_L_RTH_camH3 | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line RTH_camH3 left out (leave-one-out) |
| ZNA_L_Kijun_1h | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line Kijun_1h left out (leave-one-out) |
| ZNA_L_CRT_mid_4h | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line CRT_mid_4h left out (leave-one-out) |
| ZNA_L_KC_up_4h | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line KC_up_4h left out (leave-one-out) |
| ZNA_L_OTE62_15m | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line OTE62_15m left out (leave-one-out) |
| ZNA_L_OTE705_15m | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line OTE705_15m left out (leave-one-out) |
| ZNA_L_OTE79_15m | zone_set | EXACT partial: 14 of 43 months | 14 | live layer with line OTE79_15m left out (leave-one-out) |

## B1. Joint stage with ZONE varying

Joint driver: SZ-IJK JointRep (coordinate descent from JN04 and from live on LPB, random stacks); ZN-CORE supplies the registry above and the state-action hooks (code/th_zn_act/zone_hooks.py, composable mixin). Interaction tables ZONE x SIGQ and ZONE x STACK x LOT follow when the exact joint months land. Status: see below (filled by the refresh).


## Caveats

- First-order screens are not evidence; exact rows are. Zone-state actions are exact-only; their level tables are keyed to the base trades (signals created only by the new engine path run live).
- Leave-one-out hook proven: per-line decision counters (zdiff) in the UPDATE section of DS3_ZONES_EXHAUST_FINAL.md; an earlier all-zero pass was an engine load-cache bug (fixed, all ZNA runs redone).
- Engine: ROLLFIX1; stop-fill bias of the replica engine unchanged; NQ only; entries not live-matched.
