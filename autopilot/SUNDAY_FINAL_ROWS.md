# SUNDAY FINAL ROWS (W-SUNDAY-MX) 28 Nov 13:54Z

## BE70 VERDICT (read first)
- Asia (a, no late50): BE70 row pending
- Asia (b, with late50): BE70 row pending
- NY PM: BE70 row pending

Exact engine, 42 months (Nov 2025 excluded), p484. Layer dollar caps not re-fitted. Max DD = daily-equity peak to trough, worst week = Monday week.

| session | row | income | max DD | worst week | weekly st.dev | L3M inc | L3M DD | L6M inc | L6M DD | NQ-down wks income |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia | live mix as run | $914,998 | -$67,941 | -$37,409 | $17,867 | $154,302 | -$36,934 | $462,565 | -$36,934 | $378,957 |
| Asia | drift removed (MF4 out) | $909,638 | -$66,365 | -$35,545 | $17,072 | $141,925 | -$34,250 | $458,635 | -$34,250 | $355,436 |
| Asia | drift removed + VWAPBRK tr100 (no BE70, no late) | $1,157,521 | -$60,946 | -$36,691 | $18,820 | $161,182 | -$31,542 | $495,719 | -$31,542 | $467,377 |
| Asia | drift removed + VWAPBRK tr100 + BE70 NR7/RSI (a: no late50) | pending |||||||||
| Asia | drift removed + VWAPBRK tr100 + late50 (no BE70) | $1,064,536 | -$59,783 | -$42,455 | $17,267 | $165,006 | -$31,554 | $452,659 | -$31,554 | $377,658 |
| Asia | drift removed + VWAPBRK tr100 + BE70 NR7/RSI + late50 (b) | pending |||||||||
| NY PM | live mix as run | $1,129,115 | -$134,363 | -$44,139 | $17,638 | $199,258 | -$20,350 | $386,078 | -$30,613 | $535,893 |
| NY PM | drift removed (MF1, MF4 out) | $928,583 | -$55,701 | -$32,018 | $12,299 | $135,645 | -$11,840 | $242,779 | -$33,802 | $469,790 |
| NY PM | drift removed + late50 (no BE70) | $894,829 | -$54,114 | -$31,009 | $11,355 | $130,192 | -$11,657 | $251,457 | -$34,604 | $430,917 |
| NY PM | drift removed + late50 + BE70 on NP-ZN, NP-YM | pending |||||||||
| NY AM | live mix as run | $3,498,291 | -$200,647 | -$110,130 | $49,934 | $506,856 | -$54,493 | $1,463,415 | -$69,974 | $1,348,100 |
| NY AM | drift removed | $2,234,172 | -$217,943 | -$92,427 | $41,861 | $339,389 | -$56,176 | $990,095 | -$79,159 | $1,238,417 |
| NY AM | drift removed + NY-NODE g67a70 (chosen, NY-FIB on its bracket) | $2,450,021 | -$137,104 | -$93,021 | $40,204 | $409,158 | -$43,563 | $1,015,384 | -$95,317 | $1,130,503 |
| NY AM | chosen + NY-FIB g75a30 | pending |||||||||
| NY AM | chosen + NY-FIB g75a70 | pending |||||||||
| London | live mix as run | $913,621 | -$224,333 | -$107,350 | $22,877 | $234,166 | -$39,760 | $528,187 | -$39,760 | $6,885 |
| London | drift at 1 lot + late75 (chosen) | $727,063 | -$128,414 | -$59,316 | $16,920 | $191,895 | -$38,910 | $419,327 | -$38,910 | $238,739 |

## NY-FIB give-back (NY AM, book MF1, all 42 months, engine trades; peak = engine best_px excursion in points, give-back = peak minus realised points, $ at 20 per point x lots, gross before fee)

| set | NY-FIB trades | up >= 50 pts at peak and closed at a LOSS: count / $ | largest give-back: pts / $ | trades with peak >= 50 pts | largest single loss $ |
|---|---|---|---|---|---|
| TL3_DX_NY_MIX_c | pending or no best_px in these rows |||||
| TL3_DX_NY_JM_c_node (42/42 months) | 1677 | 227 / -$1,436,595 | 238.7 / $28,645 | 1009 | -$14,455 |
| TL3_DX_NY_FIN_c_nodefib30 | pending or no best_px in these rows |||||
| TL3_DX_NY_FIN_c_nodefib70 | pending or no best_px in these rows |||||

<!-- BUILD-KEYS-BEGIN -->
## SUNDAY BUILD KEYS (W-SUNDAY-MX, from the exact set JSONs, nothing to interpret)
Per row: per book stop / target / lots / Trade Health / exit-manager keys, then session layer keys. "stop pts / target pts" are the event-file medians (range if it varies). lots = event lots per entry BEFORE layers (sizer_hooks, zones, stack caps, daily halts still act). Late rule key LATE50 / LATE75: at the signal, if (planned exit - signal time) < the expanding p50 / p75 of that book's winners holding times (seed pools autopilot/LATE_ENTRY_SEED*.md), lots = max(1, lots // 2); otherwise unchanged. BE70 key: once best open profit >= 70% of the target distance the stop moves to entry + 0 (resting stop, target stays). BE70 REPLACED these live profit-side keys: Asia AS-NR7 (MF1) lock 80% / +10 pt; Asia AS-RSI (MF2) take 95% / 30 s and lock 80% / +0 pt; NY PM NP-ZN (MF2) and NP-YM (MF3) had no live profit-side keys (nothing replaced). AS-VWAPBRK (MF3) live take 50% / 15 s is replaced by tr100.

### ASIA: drift removed + VWAPBRK tr100 + BE70 NR7/RSI, (a) no late50   [set TL3_DX_AS_FIN_c_vwapbe70]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| AS MF1 (AS-NR7) | 40 | 80 | 6 | be=[0.7, 0.0] (rr=2.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| AS MF2 (AS-RSI) | 60 | 60 | 6 | be=[0.7, 0.0] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | scratch {'d': 45, 's': 5} |
| AS MF3 (AS-VWAPBRK) | 45 | none (stop only) [live bracket target was 45] | 6 | tr=[0.5, 1.0] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |

Session layers: zones {'MF1': {'dist': 50.0, 'act': 'Half'}, 'MF3': {'dist': 20.0, 'act': 'Skip'}}; stack_caps {'tags': ['MF1', 'MF2', 'MF3'], 'profit': 0.0, 'loss': 13600.0} | sizer {'thr': 0.4, 'lo': 0.5, 'tags': '*'} | c_gov [{'when': {'sess': [0, 1, 3, 4], 'loss_same_ge': 1, 'noevid': 1}, 'act': 'skip'}] | daily halts {'book': {'X': 2.5, 'mode': 'close', 'pause': 0}} | daily halts {'stack': {'Y': 8000, 'mode': 'close', 'pause': 60}} | daily halts {'consec': {'N': 5, 'pause': 0}} | BookLock/lin {'stackcut_share': None, 'bl': [None, 0.5, None], 'ntz_share': 0.5}

### ASIA: same, (b) with LATE50   [set TL3_DX_AS_FIN_c_vwapbe70late50; LATE50 on every book]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| AS MF1 (AS-NR7) | 40 | 80 | 3,6 | be=[0.7, 0.0] (rr=2.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| AS MF2 (AS-RSI) | 60 | 60 | 3,6 | be=[0.7, 0.0] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | scratch {'d': 45, 's': 5} |
| AS MF3 (AS-VWAPBRK) | 45 | none (stop only) [live bracket target was 45] | 3,6 | tr=[0.5, 1.0] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |

Session layers: zones {'MF1': {'dist': 50.0, 'act': 'Half'}, 'MF3': {'dist': 20.0, 'act': 'Skip'}}; stack_caps {'tags': ['MF1', 'MF2', 'MF3'], 'profit': 0.0, 'loss': 13600.0} | sizer {'thr': 0.4, 'lo': 0.5, 'tags': '*'} | c_gov [{'when': {'sess': [0, 1, 3, 4], 'loss_same_ge': 1, 'noevid': 1}, 'act': 'skip'}] | daily halts {'book': {'X': 2.5, 'mode': 'close', 'pause': 0}} | daily halts {'stack': {'Y': 8000, 'mode': 'close', 'pause': 60}} | daily halts {'consec': {'N': 5, 'pause': 0}} | BookLock/lin {'stackcut_share': None, 'bl': [None, 0.5, None], 'ntz_share': 0.5}

### NY PM: drift removed + LATE50 + BE70 on NP-ZN, NP-YM   [set TL3_DX_NP_FIN_c_be70late50; LATE50 on every book]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| NP MF2 (NP-ZN) | 120 | 120 | 3,6 | BE70 = be50 [0.7, 0] | flat {'d': 96.0}; shave 4 |
| NP MF3 (NP-YM) | 80 | 40 | 3,6 | BE70 = be50 [0.7, 0] | flat {'d': 80.0} |

Session layers: zones {'MF2': {'dist': 10.0, 'act': 'Half'}, 'MF3': {'dist': 30.0, 'act': 'Half'}}; stack_caps {'tags': ['MF2', 'MF3'], 'profit': 11200.0, 'loss': 0.0} | daily halts {'book': {'X': 3, 'mode': 'close', 'pause': 0}} | daily halts {'stack': {'Y': 6000, 'mode': 'new', 'pause': 0}} | sizer {'thr': 0.4, 'lo': 0.5, 'tags': '*'} | BookLock/lin {'stackcut_share': None, 'bl': [3.0, 0.33, -12.0], 'ntz_share': 1.0}

### NY PM: same WITHOUT BE70 (beside it)   [set TL3_DX_NP_JM_c_late50; LATE50 on every book]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| NP MF2 (NP-ZN) | 120 | 120 | 3,6 | bracket (stop + target) | flat {'d': 96.0}; shave 4 |
| NP MF3 (NP-YM) | 80 | 40 | 3,6 | bracket (stop + target) | flat {'d': 80.0} |

Session layers: zones {'MF2': {'dist': 10.0, 'act': 'Half'}, 'MF3': {'dist': 30.0, 'act': 'Half'}}; stack_caps {'tags': ['MF2', 'MF3'], 'profit': 11200.0, 'loss': 0.0} | daily halts {'book': {'X': 3, 'mode': 'close', 'pause': 0}} | daily halts {'stack': {'Y': 6000, 'mode': 'new', 'pause': 0}} | sizer {'thr': 0.4, 'lo': 0.5, 'tags': '*'} | BookLock/lin {'stackcut_share': None, 'bl': [3.0, 0.33, -12.0], 'ntz_share': 1.0}

### NY AM chosen: drift removed + NY-NODE g67a70 (no late)   [set TL3_DX_NY_JM_c_node]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| NY MF1 (NY-FIB) | 120 (median; 72 to 120) | 120 (median; 72 to 120) | 6 | bracket (stop + target) | none |
| NY MF2 (NY-VALUE) | 60 | 60 | 6 | bracket (stop + target) | none |
| NY MF4 (NY-NODE) | 90 | none (stop only) [live bracket target was 30] | 6 | gb=[0.7, 0.67] (rr=0.333333; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| NY MF5 (NY-OFI) | 60 | 60 | 3 | bracket (stop + target) | none |

Session layers: zones None; stack_caps {'tags': ['MF1', 'MF2', 'MF4', 'MF5'], 'profit': 0.0, 'loss': 28800.0} | sizer {'thr': 0.3, 'lo': 0.5, 'tags': '*'} | c_gov [{'when': {'sess': [0, 1, 3, 4], 'loss_same_ge': 2, 'noevid': 1}, 'act': 'skip'}] | BookLock/lin {'stackcut_share': None, 'bl': [2.0, 0.67, -12.0], 'ntz_share': 1.0, 'ntz': 'off'}

### NY AM + NY-FIB g75a30   [set TL3_DX_NY_FIN_c_nodefib30]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| NY MF1 (NY-FIB) | 120 (median; 72 to 120) | none (stop only) [live bracket target was 120 (median; 72 to 120)] | 6 | gb=[0.3, 0.75] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| NY MF2 (NY-VALUE) | 60 | 60 | 6 | bracket (stop + target) | none |
| NY MF4 (NY-NODE) | 90 | none (stop only) [live bracket target was 30] | 6 | gb=[0.7, 0.67] (rr=0.333333; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| NY MF5 (NY-OFI) | 60 | 60 | 3 | bracket (stop + target) | none |

Session layers: zones None; stack_caps {'tags': ['MF1', 'MF2', 'MF4', 'MF5'], 'profit': 0.0, 'loss': 28800.0} | sizer {'thr': 0.3, 'lo': 0.5, 'tags': '*'} | c_gov [{'when': {'sess': [0, 1, 3, 4], 'loss_same_ge': 2, 'noevid': 1}, 'act': 'skip'}] | BookLock/lin {'stackcut_share': None, 'bl': [2.0, 0.67, -12.0], 'ntz_share': 1.0, 'ntz': 'off'}

### NY AM + NY-FIB g75a70   [set TL3_DX_NY_FIN_c_nodefib70]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| NY MF1 (NY-FIB) | 120 (median; 72 to 120) | none (stop only) [live bracket target was 120 (median; 72 to 120)] | 6 | gb=[0.7, 0.75] (rr=1.0; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| NY MF2 (NY-VALUE) | 60 | 60 | 6 | bracket (stop + target) | none |
| NY MF4 (NY-NODE) | 90 | none (stop only) [live bracket target was 30] | 6 | gb=[0.7, 0.67] (rr=0.333333; gb [a, keep]: stop keeps `keep` of the peak once peak >= a x old target; tr [a, k]: trail k x stop distance behind best once best >= a x old target; be [pct, off]: stop to entry + off once pct of target covered) | none |
| NY MF5 (NY-OFI) | 60 | 60 | 3 | bracket (stop + target) | none |

Session layers: zones None; stack_caps {'tags': ['MF1', 'MF2', 'MF4', 'MF5'], 'profit': 0.0, 'loss': 28800.0} | sizer {'thr': 0.3, 'lo': 0.5, 'tags': '*'} | c_gov [{'when': {'sess': [0, 1, 3, 4], 'loss_same_ge': 2, 'noevid': 1}, 'act': 'skip'}] | BookLock/lin {'stackcut_share': None, 'bl': [2.0, 0.67, -12.0], 'ntz_share': 1.0, 'ntz': 'off'}

### LONDON chosen: drift at 1 lot (MF2 at 1 lot) + LATE75   [set TL3_DX_LO_JM_d_late75; LATE75 on every book]
| book | stop pts | target pts | lots (event) | exit-management key | Trade Health keys (live as run) |
|---|---|---|---|---|---|
| LO MF1 (LO-CRUDE) | 90 | 30 | 4,8 | bracket (stop + target) | none |
| LO MF2 (LO MF2) | 45 | 45 | 1 | bracket (stop + target) | none |
| LO MF3 (LO-ZB) | 120 | 60 | 1,2 | bracket (stop + target) | none |

Session layers:  | BookLock/lin {'stackcut_share': None, 'bl': [None, 0.5, None], 'ntz_share': 1.0}

<!-- BUILD-KEYS-END -->
