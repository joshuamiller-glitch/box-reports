# EXIT_HARNESS - shared scorer for T-EXIT-N (S5 integrator). Code: l2vast/ds3/code/zones3_s5/exit_harness.py
Adopt it or not: it only wraps BASE-4's EXIT_API (V13T.inject + run_v13t_live), so every number is the V13T_LIVE engine result (xcost 0.80, stopcost 2.45, targets nominal, resting add cancelled on any exit, lock none; frame 'ref12' = combined 12R, reference only).
```python
import sys; sys.path.insert(0,'l2vast/ds3/code/zones3_s5'); import exit_harness as H     # python3 -I
S = H.boot()                      # S['d'] engine rows, S['kin'] entry second, S['kout'] library exit second, S['book'], S['sess'], S['day']
rule = H.Rule('cut|a30', 'cut', rows, kx, px)        # kind cut|take|tighten|time|scale_out (+ frac=0.5 or per-row array)
out = H.score(rule, frames=('none',), placebos=0)    # one engine run + equal-risk search (~25 s per run, ~2 min with equal risk)
```
`out['none']`: `table[window]` = base/cell stats (mean, maxdd, w20, sd, ulcer, cvar5, calmar), `cut` (1 - maxDD ratio), `dmean`+`mde` (paired weekly delta, MDE = 2.8 SE), d_w20/d_ulcer/d_cvar/d_calmar; `episode[window]` = carrying week (ISO key), cut without that week, leave-one-week range, ONE-WEEK flag; `equal_risk` = lot scale and paired mean delta per window at equal ALL-window worst-20; `band` + `pass_band` = Z3 phase-averaged band rule (cut > band in L6M AND (PRE or X'); BAND_PA in the file is Z3's FINAL V13T_LIVE PA9 band (n=100, DS3_ZONES_3_NOISE_V13T_FINAL.md)); `no_harm` = PRE and MID cut not worse than -(flip-2 PA band).
Windows: L1M L2M L3M L6M HOLD MID PRE X' F9 ALL (weekly cumulative, label days to 2026-10-30).
## Placebos (same cost model because they go through the same inject path)
P1 random rows with the SAME COUNT PER LABEL DAY; P2 same total volume, random rows over all days; P3 shuffled-day (each real exit moved to a random same-book/same-session row on a different day). Exit offsets (kx - entry second) are resampled from the real rule, exit price = path price at that second, exit bounded before the library exit. Run in parallel processes (<= 3, 8 GB each):
```
python3 -I exit_harness.py placebo rule.npz 0 34 /mnt/l2/.../plc_dir       # draws 0..33  (3 kinds each; resumable)
H.save_rule(rule,'rule.npz')                                               # to write rule.npz
out = H.score(rule, placebos=1, plc_dir='/mnt/l2/.../plc_dir')             # ranks: out['none']['placebo'][P1|P2|P3] = {n, L6M, PRE, X', mean3}  (share of draws with cut >= real; need <= 0.05-0.10)
```
Notes: the base itself moves +-16k maxDD with +-0.22 pt of xcost (BASE-4): judge cuts with the PA band and the placebo ranks, not on the point cut. A rule that fires on a high share of rows is a volume effect unless P2 rank is small.
