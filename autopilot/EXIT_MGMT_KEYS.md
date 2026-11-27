# EXIT_MGMT_KEYS - exact definitions of the existing exit-management keys, read from the exact-engine code (W-DYNA for W-SUNDAY / EXIT_MGMT_SUNDAY.md; 2026-11-27 20:30Z)

Keys-page standard: each key = value with the code place; SPEC = read from the code named, READING = my reading, OPEN = to confirm. The factor codes (CU1.., LK1.., TK1.., ...) are the ones of D8_LAYER_KEYS*.md (LOSS.MFn / LOCK.MFn / TAKE.MFn / ZONE.MFn); 'the live file' = DS7.cs v2.0 + THP_POLICY_D7_v2_9.txt for the K7/P7/M7/U7/A7/H7/O7 policy lines and the D8 set strings for the new-book layers. Constants: tick 0.25; engine fill SLIP 0.80 pt (market exits of state rules: par slip), SSLIP 1.4 pt (structure stop fills); LAT_FILL 1.0 s, LAT_CANCEL 0.5 s (replica/sim.py PRM).
Common time base: the STATE TAPE = one mid-price row per closed exchange second (s._sts epoch second, s._smid mid). Rules marked 'state' evaluate row r when the second r has CLOSED (now > row r + 1 s) and act on the NEXT row's mid (r+1): they never use the last print. Rules marked 'print' evaluate on the last print, at most once per second (ThEvalFrequencySecs = 1).

## LOSS SIDE (th_ec/ec_hooks.py EcRep.manage_th_l2, lines 85-125; rules are per book tag in par['rules'] in list order)
```
CU<k>   = {kind: flat, p.d = round(f x S0, 1)} f = 0.4 / 0.6 / 0.8 / 1.0 for k = 1..4 (CU4 = at the full stop: no extra cut), S0 = the book's stop pts.   SPEC layer_gen.py L77
  trigger  (state): x_r = side*(mid_r - entry_px) <= -d at ANY closed second since the entry second r_e (x uses the mid, not the last print; entry_px = the trade's average fill)
  action   : ALL lots exit at market 'EarlyCut' at price mid_{r+1} - side*SLIP (0.80 pt), event time max(row r+1, now); stop and target orders cancelled; the rule is done for the trade (S['done'])
  rounding : d rounded to 0.1 pt; the exit price is NOT rounded to the tick in ec_hooks (the engine's exec_exit prices as given)   READING
  lots     : full position at 1 / 2 / 3 / 6 lots (no scaling); 'ge5' / 'lt5' fields can restrict a rule to lots >= 5 / < 5 (not used by CU)
CX<k>   = the same flat rule with ctx ['fresh']: only if the entry context is FRESH; k = 1..3 -> f = 0.4 / 0.6 / 0.8 x S0   SPEC layer_gen.py L78
  context  : ctx = 'chasing' if chase_k(sig second, side) > 1.0 ; else 'fresh' if (n <= 2 and gap >= 30 min) ; else 'reentry'; n = 1 + number of this book's entries since the chase window start t0; gap = minutes since the last exit of this book before the signal (inf if none)   SPEC ec_hooks.py _ec_state
NFT (FR_LOSS7 / 8 = {kind: nft, p.X, p.N}) : at exactly row j = N*60 s after the entry second r_e (a single check, not 'from then on'): x < X pts -> exit all at market (same price rule). FR_LOSS7: X = +10 pts, N = 20 min ; FR_LOSS8: X = +5, N = 20; the W-FASTR pick (X, 20)   SPEC
SCR (FR_LOSS9 / {kind: scratch, p.d, p.s}) : once mae <= -d (the worst x seen since entry, state rows) AND x >= -s now -> exit all at market. FR_LOSS9: d = 45, s = 5. W-SUNDAY's sc50_10 / sc67_10: d = 0.5 / 0.67 x S0, s = 0.1 x S0   SPEC
back0 {Y}: mfe >= Y and x <= 0 -> exit ; rlock {d,a,g}: after mae <= -d and x >= -a armed; exit when x <= -a - g ; partial {d, F}: at x <= -d sell floor(F x lots) lots at market ('EarlyCutScale'), only if lots >= 2 and 1 <= q < lots, then the bracket is re-placed for the rest   SPEC (kinds in the code; not part of the Sunday menu)
order of evaluation inside the hook: rows r = next unprocessed .. last closed; for each row every rule of the book in list order (mae/mfe updated first); the FIRST rule that fires exits the whole trade (S['done'], later rules dropped); a 'partial' does not end the loop
```
## PROFIT SIDE
```
LK<k>   (th_engfix/ev_profit.py, state): locks[tag] = [[pct, X], ...] ; LK1..9 = (50 / 65 / 80 %) x (+0 / +10 / +20 pts): LK1 50%/+0, LK2 50/+10, LK3 50/+20, LK4 65/+0, LK5 65/+10, LK6 65/+20, LK7 80/+0, LK8 80/+10, LK9 80/+20; W-SUNDAY adds 90%.   SPEC
  trigger  : at each CLOSED second r (once per second, only seconds at/after the entry), m = mid_r; pct = side*(m - entry_px) / tgt, tgt = TG[tag] if set (K7 59, P7 58, M7 59.5) else |target_px - entry_px| if a target exists else stop_pts x target_r (the book's bracket target distance); the first time pct >= pct_i the rule i is ARMED (set once per rule)
  level    : lvl = round((entry_px + side*X)*4)/4 (nearest tick, half-even by Python round); several armed rules: the more protective level is kept
  action   : NOT a resting stop order: on the first PRINT touching the level (long: px <= lvl) the hook requests a market exit 'PolicyTrail' for ALL lots (request_exit); engine latency applies (LAT_FILL); the bracket stop/target remain in force
  lots     : whole position at 1 / 2 / 3 / 6 lots
TK<k>   (ev_profit.py, print): takes[tag] = [pct, secs_ext]; TK1..12 = pct {50, 65, 80, 95}% x secs {5, 15, 30}: TK1 50/5, TK2 50/15, TK3 50/30, TK4 65/5, TK5 65/15, TK6 65/30, TK7 80/5, TK8 80/15, TK9 80/30, TK10 95/5, TK11 95/15, TK12 95/30.   SPEC
  trigger  : on a print (<= 1 evaluation per second): pct = (last print - entry)*side / tgt >= pct AND seconds since the favourable extreme (a strictly NEW extreme print resets the clock) >= secs_ext -> market exit ALL lots, exit name 'PolicyTake'. A book's first matching policy rule acts (live policy_poll order: the injected take is prepended to the file's rules)
NRT<k>  (th_nt/wnt_hooks.py, print): latch X x target reached (b.fav_ext = best print) then exit at market ('NtStale' no new extreme for S s | 'NtGive' G pts or givep x target below the extreme | 'NtLock' at entry + L x target); NRT1 X .90 stale 10 s, NRT2 .95 stale 20 s, NRT3 .90 give 8 pts, NRT4 .95 givep .10   SPEC
SHV<k>  (wnt_hooks.py): the resting TARGET limit order sits k ticks nearer the entry (k = 2 / 4 / 8 -> 0.5 / 1.0 / 2.0 pts); b.target_px and every pct denominator stay at the nominal target; the live takes still use the nominal   SPEC
```
## NEW PROFIT KEYS OF THE SUNDAY MENU (th_dynexit/dx_multi.py L119-125; all are RESTING STOP ratchets, evaluated at each print; the stop only tightens; level rounded by SIM.rt to the tick; the stop order price = level - side*(cat if join else 0))
```
PL<a>K<k> peaklock [arm_R, frac] (a = 50 / 70 % of target distance expressed in risk units arm_R = a/100 x T0/S0 ; k = 50 / 67 / 75 %): once best favourable excursion ex >= arm_R x risk the stop sits at entry + frac x ex (ratchet: grows with ex)   SPEC (risk = the trade's stop distance)
NT<p>K<k> neartgt [pct, k_R] (p = 70 / 80 %, k = 15 / 25 % of the target distance = k x T0/S0 in risk units): once ex >= pct x target distance the stop trails at (best - k_R x risk), ratchet; the target stays   SPEC
BE50      be50 [0.5, 0]: once ex >= 0.5 x target distance the stop goes to entry + 0 ticks (0.25 x off ticks)   SPEC
difference to LK: LK is a MARKET exit on touch (state arm + print touch, 'PolicyTrail'), PL/NT/BE50 are a resting stop moved up (a stop fill, 'Stop'); at 2+ lots both act on the whole position
```
## ZONES (th_layers/lay_hooks.py zone; keys ZH = Half, ZS = Skip)
```
ZONE<k>: ZONE1 dist 10 Half, ZONE2 30 Half, ZONE3 50 Half, ZONE4 20 Skip, ZONE5 30 Skip, ZONE6 50 Skip   (W-SUNDAY: ZH<d> = Half at dist d pts, ZS<d> = Skip at dist d)
trigger  : the entry (engine ntz_check) has a point-of-interest within dist points AHEAD of the entry in the trade direction -> act: Skip = the signal is dropped; Half = lots x frac (0.5) rounded HALF UP, minimum 1: 1 lot -> 1 (inert), 2 -> 1, 3 -> 2, 4 -> 2, 5 -> 3, 6 -> 3 ; replaces the engine's own no-trade-set check for that book   SPEC (lay_hooks docstring; 'Half after P1_START' is the engine default)
```
## ORDER OF EVALUATION WITH THE EXISTING RULES (READING: each hook class calls super().manage_th_l2 FIRST, then its own code, so the hooklist order = innermost first)
```
engine base (bracket stop/target, Trade Health policy lines TK-live, loss pulled_mult cuts, session flatten) -> ec_hooks (CU/CX/NFT/SCR/...) -> ev_profit (LK, injected TK) -> nt_hooks (NRT, SHV target) -> lay_hooks (BookLock, zone, stack caps) LAST ; dx_multi recipes (PL/NT/BE50) inside the mf_multi layer. OPEN: confirm the exact hooklist order of a given set in its set JSON (sets/TL3_*.json 'hooklist'); the first rule to request an exit wins (b.exit_pending blocks later ones)
```
## MATCH ROWS FOR THE SUNDAY PICKS
Per bar (state row) match rows for 2 dated trades per book where a new rule fires are produced after W-SUNDAY posts its picks (autopilot/EXIT_MGMT_SUNDAY.md); format: the per-second mid rows from the state tape entry-2 s .. exit+10 s (tables/NQ/1s, bid_px/ask_px midpoint), x_r, mae, mfe, pct, armed flags, level, the first firing row and the fill price per the formulas above.
