# PLAN_LO_LOG (W-PLAN-LO)
- 04:00Z read orders; no London trades in W-DYNA's path store (Asia/NY only) -> built own London store from the BARE live set + tables/NQ/1s (6,093 trades, 5,918 usable). Code code/th_plan_lo/.
- 04:10Z simulator identity: sim 906k vs engine 946k.
- 04:15Z fixed defaults written (fixed_rules_plan_lo.json) then PA-PE scored: none beats REF.
- 04:18Z attribution: 42 tests, 0 YES. Why plans fail: the trades that lose are not preceded by any detectable flow/book change (d ~ 0), and the winners are the 30/45/60 pt targets themselves.
- 04:25Z grid 130 variants x 3 books; WF at 2/4/13 weeks fails income clause. MF2 trail lead found (DD -75k vs -179k).
- Next idea from MF2: loss comes from 2025 (reversals after reaching +half target); test the same BE trail rule on MF1 (act 0.5 T0 = 15 pt of a 30 pt target gave no gain: MF1 trades rarely reverse after +15) - done within grid, no gain.
