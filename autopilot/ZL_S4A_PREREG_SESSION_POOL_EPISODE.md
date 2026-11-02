# ZL S4A PRE-REGISTRATION: session-restricted layers, one pooled liquidity-pool rule, mechanical two-episode requirement
Written 2026-11-02 ~12:00Z by S4a BEFORE any statistic of these cells is computed. Base: D7 V13Y (code/d7base/d7_v13y.py), lock=None headline, lock=12 reported beside; re-run of the best 3-4 cells on V13Z when announced. Windows: code/cap/windows.py (L1M L2M view only). All post-hoc, Shadow only. No tuning: every parameter below is fixed here.

## Common definitions
* Mask of a stream line = poi_core fresh-ahead distance af <= D (feature channel 0 on the D7 engine rows, as in DS3_ZONES_3_S4A.md); HALF = planned lots x0.5 on masked rows not already halved by the shipped 7-line layer; SKIP = skip masked rows. Cut = 1 - maxDD(cell)/maxDD(base) of the weekly cumulative total, same phase.
* Phase-averaged (PA) estimate: K=9 lock-reset phases (week key shifted -4..+4 label days), paired with the base at the same phase (Z3 estimator, same code as phasey.py). PA band: Z3 FINAL V13Y band (DS3_ZONES_3_NOISE.md): lock off L6M .157/.199, HOLD .145/.191, MID .261/.366, PRE .114/.174, X' .159/.230 (flip-2 below 1,000 fired rows, flip-5 otherwise); lock 12R L6M .117/.239, HOLD .112/.117, MID .239/.373, PRE .131/.131, X' .100/.145.
* RULE (unchanged): PA cut above band in L6M AND in PRE or X'. NO-HARM: no window among L6M/HOLD/MID/PRE/X' has a PA cut below minus its band, and the PA mean change over ALL is not below minus the paired MDE. PASS = RULE and NO-HARM.
* Placebos (100 draws x 3 kinds A random rows same count per book x session x side x target-half stratum, B same-volume Bernoulli, C circular shift of the fire vector within book x session in time order) are run ONLY for cells that PASS (pre-registered; cells that do not pass are not rescued by placebos); rank = (1+#placebo >= cell)/(1+n) on the mean of the L6M/HOLD/PRE/X' cuts.
* CHANCE BENCHMARK per test (share of random same-volume masks positive in L6M AND PRE AND X'): computed from 100 kind-B draws per benchmark cell as defined in each test, compared with the share of the test's cells positive in the triple.

## T1 Session-restricted layers
* Cells (7 line cells x 2 sessions = 14): lines/actions/D = EQL|EQL_tight|5m D40 skip; SWG|f3L|3m D20 half and D40 half; SWG|f3L|15s D20 half and D40 half; FIB|ote705_dn|15m D20 skip and D40 skip. Sessions = Asia and London (engine session index 0 and 1; row session as in the lot table). Mask = line mask AND row session == s. Nothing else is varied.
* Placebos for T1 passers draw the random masks INSIDE the session (same session rows only).
* Chance benchmark T1: kind-B draws restricted to the session at the volume of EQL D40 / SWG f3L 3m D20 / SWG f3L 15s D40 (6 benchmark cells x 100 draws).

## T2 One pooled liquidity-pool rule
* Pool = union of 30 streams: EQL|{EQH,EQL}_{tight,rel}|{1m,5m,15m} (12) and SWG|{f3L,f5L,f7L}|{1m,2m,3m,5m,10m,15m} (18, fractal lows). Fire = ANY pool stream has a fresh line ahead within D (af <= D).
* 2 cells only: D=20 HALF and D=40 HALF. Chance benchmark T2: kind-B draws at the volume of each cell (2 benchmark cells x 100 draws).

## T3 Mechanical two-episode requirement
* Applied to ALL 24 V13Y finalists (selyn24, lock none series stored in s2yn_res) and to any survivor list another agent hands me as a cell mask file. Episodes = the lock-none top-3 base episodes of DS3_ZONES_EPISODES_V13Y.md (L6M: 202627-202638, 202620-202623, 202640-202642; PRE: 202434-202451, 202505-202520, 202410-202421; X': 202321-202341, start-202316, 202348-end).
* For window w in {L6M, PRE, X'} the CARRYING episode is the base's episode 1 of w. A cell SURVIVES in w if its cut with that episode's weeks removed (from both series) is > 0. TWO-EPISODE-OK = survives in at least 2 of the 3 windows AND the full cut > 0 in those windows; otherwise ONE-EPISODE. Reported with the PA band result; nothing else.
* Chance benchmark T3: share of the kind-B placebo draws already stored for 1138/359/569/1208 (plcyn) that are TWO-EPISODE-OK by the same rule.
