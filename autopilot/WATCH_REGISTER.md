# WATCH_REGISTER - weekly Shadow watch register (ZL-2; append-only, one dated block per run; Shadow only, nothing live; a status is not a decision)
Design prereg: l2vast/ds3/prereg/WATCH_REGISTER_design_prereg.md. Forward floor: label days >= 2026-11-02 (2026-11-01T23:00Z). Statuses: NO-DATA, SPEC-PENDING, PLUGIN-PENDING, REFUSED-SPEC-CHANGED, ACCUMULATING, KILL-TRIGGERED, PASS-CANDIDATE, NOT-TESTABLE.

## WATCH REGISTER run 2026-11-06T01:58Z
| run (UTC) | watch | spec sha12 | status | forward coverage and note | n_trades | mean net $/trade | cum net $ | mean F (ticks) | next |
|--|--|--|--|--|--|--|--|--|--|
| 2026-11-06T01:58Z | RTY_PREMARKET | c9b8563d51b4 | NO-DATA | no RTY 1-s table row at or after the forward floor 2026-11-01T23:00:00Z (last table second 2026-10-30 21:00:01Z) | 0 | - | - | - | next run |
| 2026-11-06T01:58Z | MONDAY_LONG | 337347600d74 | ACCUMULATING (N=0 of 26; week 1 = Monday 2026-11-09, first read Tuesday 2026-11-10 after the roll) | forward label days >= 20261109, data to 2026-11-05 16:05:00Z; no completed forward Monday yet | 0 | nan | 0.0 | +nan | weekly Mon 14:00Z |
| 2026-11-06T01:58Z | CL_DONCHIAN | ce175343cad5 | NO-DATA | no CL 1-s table row at or after the forward floor 2026-11-01T23:00:00Z (last table second 2026-10-16 20:59:00Z) | 0 | - | - | - | next run |
| 2026-11-06T01:58Z | BTC_MBT_ASIA_KELTNER | - | SPEC-PENDING | spec file WATCH_BTC_MBT_ASIA_KELTNER_SPEC.md not present (owner S4b) | 0 | - | - | - | - |
| 2026-11-06T01:58Z | GC_REGIME | - | SPEC-PENDING | spec file WATCH_GC_REGIME_SPEC.md not present (owner ZL-1) | 0 | - | - | - | - |
(note on the CL_DONCHIAN row above: its spec floor is 2026-10-17 (forward P&L counted from 2026-10-17); the cache_c/CL.npz series ends 2026-10-16, hence NO-DATA; wording fixed in the runner.)

## WATCH REGISTER run 2026-11-06T02:08Z
| run (UTC) | watch | spec sha12 | status | forward coverage and note | n_trades | mean net $/trade | cum net $ | mean F (ticks) | next |
|--|--|--|--|--|--|--|--|--|--|
| 2026-11-06T02:08Z | RTY_PREMARKET | c9b8563d51b4 | NO-DATA | no RTY data at or after the watch floor 2026-11-01T23:00:00Z (last table second 2026-10-30 21:00:01Z) | 0 | - | - | - | next run |
| 2026-11-06T02:08Z | MONDAY_LONG | 337347600d74 | ACCUMULATING (N=0 of 26; week 1 = Monday 2026-11-09, first read Tuesday 2026-11-10 after the roll) | forward label days >= 20261109, data to 2026-11-05 16:05:00Z; no completed forward Monday yet | 0 | nan | 0.0 | +nan | weekly Mon 14:00Z |
| 2026-11-06T02:08Z | CL_DONCHIAN | ce175343cad5 | NO-DATA | no CL data at or after the watch floor 2026-10-17T00:00:00Z (last table second 2026-10-16 20:59:00Z) | 0 | - | - | - | next run |
| 2026-11-06T02:08Z | MBT_ASIA_KELTNER | b82f1d445330 | NO-DATA | no MBT data at or after the watch floor 2026-11-01T00:00:00Z (last table second 2026-10-31 23:43:00Z) | 0 | - | - | - | next run |
| 2026-11-06T02:08Z | GC_REGIME | - | SPEC-PENDING | spec file WATCH_GC_REGIME_SPEC.md not present (owner ZL-1) | 0 | - | - | - | - |
