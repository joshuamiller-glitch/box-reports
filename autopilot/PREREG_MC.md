# PREREG W-MC (MAJOR C stack-level risk overlay), 2026-11-17 ~14:40Z
Bases: JL3 (TL3_EV_JL3). Policy hook: code/th_mc/mc_hooks.py (outermost; identity cell TL3_MC_ID = hook active but inert, must equal JL3 trade for trade on 202610 and 202504 before any cell is used).
Grids (frozen in code/th_mc/mc_pol.py and mc_screen.py, 62 cells = F):
 DD  trailing stack drawdown from the W-day peak of the policy's own path: W {60,250} x T {10k,20k,30k,45k} base-lot $; x0.5 at DD >= T, back to x1 when DD < T/2 (8)
 ND  trailing N-day stack P&L (N 5/10/20) vs k x sd120 x sqrt(N), k {0.5,1,1.5}: cut x0.5 below -k (9) and press x1.5 above +k (9)
 VT  vol target: lots x clip(target/trailing-N sd, 0.5, hi), N {10,20,40}, target = 50th/75th pct of the fit-period trailing sd, hi {1.0,1.5} (12)
 SS  per-session loss stop: stop the session (not the day) when the stack's closed P&L of the session instance <= -T base $, T {2.5k,4k,6k,9k}, sessions all four or London/NY only (8)
 CAP same-direction open-lots cap by session beyond London: cap {3,4,6,8} base lots x sessions {Asia, NY, Asia+NY} truncate (12) + skip mode {4,6} Asia+NY (2)
Screen = path arithmetic on the JL3 trade list at live-lot granularity (Ll = max(1,floor(1.75 l+.5)), x m rounded at live-lot level); arithmetic random controls matched on lots removed (tol max(min(.05,.25 share),.002)); own-path state, causal (day e uses days < e).
Finalist rule (FIT = 2023-04..2025-10 ONLY; HOLD / L6M never used): eligible = |share| >= 2% and FIT ulcer ratio < 1 and FIT mean ratio >= 0.5; rank by FIT ulcer ratio / mean ratio; top 2 per family -> exact engine (12 cells).
Engine: month order L6M+HOLD first, then older. Controls (persistent random lot-scale, 30 valid draws, realised lots-removed share within tol) are queued for a family's top cell only when the exact cell's L6M or HOLD ulcer ratio < 1 with ulcer-per-dollar ratio < 1 (so the engine is not spent on cells that are dead on their own path). Windows L6M L3M HOLD GAP PREUW X' pooled; ulcer primary; tiers by cutoffs_ulc.json; walk-forward: choose <= 2025-10 / rolling trailing 12 months.
DISCLOSURE: the screen output (all windows) was read once before this file was written; the finalist rule and the grids were not changed after reading it, the rule only uses FIT.
DAY-DONE settings: not rebuilt, W-DD (DS3_DAYDONE_VARIANTS.md, TL3_DD_*) is the owner; pointer + results only.
