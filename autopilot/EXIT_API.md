# EXIT API for T-EXIT-N on V13T_LIVE (BASE-4, 2026-11-02)
Code: `l2vast/ds3/code/d7base/d7_v13t.py` (python3 -I; `sys.path.insert(0, '.../code/d7base')`).

## Base calls
- `V13T.run_v13t_live(ov=None)` = V13T_LIVE: market exits 0.80 pt, stops 2.45 pt worse than nominal, targets nominal (tshort 0), profit lines EMPTY, lock none (per-book 12R week floor + day give-back 2R/50% + daily max P/L + ER(20)), per-book lock exit-cancel fix (lockfix 'legs'), basis N (nfix), resting 30% cancelled on ANY exit. Returns the usual dict (cube (11,6,ND), total, core, cfg, info...).
- `V13T.run_v13t_live_lock12ref(ov=None)` = same with the combined 12R stack lock (reference only; not live).
- `V13T.run_v13t(ov)` = the building block. Options (popped from ov, the rest goes to V13Z/d7lib): `xcost` (early MARKET exit cost, pts, default 0.995; alias `mktcost`), `stopcost` (baseline stop slippage, pts; None = engine native 1.28; live read 2.45), `tshort` (target-fill shortfall, default 0), `lines` ('empty' default), `lock` (None default; 12 = combined), `lockfix` ('legs' default | 'cancel' | False), `grid` ('10s' default | '1sh'), `extra_skip` / `extra_mult` (d7lib hooks), `lscale`, `inject` (below). Tie-out: `run_v13t(ov={'lockfix':False})` == V13Z lines-empty lock none at 0.0 $; `stopcost=1.28` == default.

## Where each exit takes its cost
| exit path | cost source |
|---|---|
| TH-L2 loss cut (d7lib `th_loss`) | `xcost` (the stored cut delta is priced at 0.995; V13T shifts it by 0.995 - xcost per lot) |
| take / tighten lines (`lines=`) | `xcost` (the kernel's 0.995 / 1.01 are replaced by xcost) |
| `inject(...)` kinds cut / take / tighten / time / scale_out | `xcost` of the run (per-item override `xcost=`) |
| baseline STOP exit | `stopcost` (charged only to rows that still END at the stop: rows converted to a cut/take/time exit are priced at xcost) |
| baseline TARGET exit | nominal (0) unless `tshort` > 0 |
| resting 30% add (generic dip-3 split and OTE-62 B73) | cancelled on ANY exit: injected exits (compose hook), per-book lock exits (lockfix) |

## Generic injection API
```python
import d7_v13t as V13T
D = V13T.D; d = D._d()                      # d.SC = path price per second, d.SS = path seconds, d.side, d.E, d.kin, d.tid, d.book, d.sess ... (88,490 library rows)
it  = V13T.inject(rows, kx, px, kind='take')            # rows: d-row indices; kx: exit SECOND INDEX into the path arrays; px: exit price (d.SC[kx] for a market exit at the path price)
it2 = V13T.inject(rows2, kx2, px2, kind='scale_out', frac=0.5)   # sell `frac` of the position at kx2 (rest runs to its own exit; an unfilled add is cancelled)
r = V13T.run_v13t_live({'inject': [it, it2]})
```
- kinds: `cut`, `take`, `tighten`, `time` = FULL market exit of the position at second `kx` at price `px` (the earliest of several exits on a row wins; loss-cut and injected exits compete, the earlier second applies; an exit at or before the entry second is ignored); `scale_out` = partial (frac may be a scalar or per-row array), only applied if it is strictly before the row's final exit.
- Per-lot delta vs the engine baseline (basis N, original exit at its nominal price): `side*(px - exit_px_lib) - xcost + fill_cost*(original exit was not the target)`; identical to the V13Z take-line delta (verified: inject of the plain-0.70 PE take reproduces the lines kernel at 7e-12 $).
- The resting add: an exit (full or partial) before the add fill cancels the add (70% leg only); an exit after the fill applies to both legs. Handled inside the engine; do not re-implement.
- `px` for a limit-order style exit (e.g. exit AT a target-like level) is your choice; for a marketable exit use the path price at kx (d.SC[kx]) and let the cost model charge xcost. A stop-style exit that fills worse (stopcost) is NOT an injected kind: use `kind='time'` with px = the stop level and xcost=2.45 (item override) if you want a rule's own stop priced like a live stop.
- Combine with placebos by building random `rows/kx/px` sets and passing them through the same `inject` (they then carry the same cost model).
- Costs/phase: per-book locks use the lock engine; `lockfix='legs'` is the only mode that values the 30% from its fill.

## Notes added after the self-tests (EXIT_API_TESTS.md)
- An injected exit COMPETES with the TH-L2 loss cut and with other injected exits on the same row: the EARLIEST second wins and the delta is applied relative to the LIBRARY exit (not to the cut). For a row the cut already exits, the net change from your injection is dN_yours - dN_cut. Check your marginal effect on rows where the base exit is the original stop or target (ty0 != 2).
- Stop-type rows: when your exit replaces an original STOP exit, the engine also removes the stop slippage (stopcost - 1.01 pt per lot, 1.44 at the live 2.45) of the exited lots (the row stops being a stop); scale_out removes it pro rata. This is automatic: the worked examples verify delta = (dN + 1.44) x $/pt for stop rows and delta = dN x $/pt for target rows, with dN = side*(px - exit_px_lib) - xcost + fill_cost*(original exit not the target).
- $/pt per lot of the position = lots x $20 (e.g. 105 $/pt for a 5-lot P6 trade); an exit before the add fills carries the 70% leg only (F x $/pt).
- BUG FIX 2026-11-03 (reported by S4a): with th_loss=False and no profit lines, injected exits were silently ignored (the merge hook was skipped when no TH-L2 part existed). Fixed in d7_v13y._compose_d7y (always merges). Any cell run with th_loss off AND inject before this fix is void.
