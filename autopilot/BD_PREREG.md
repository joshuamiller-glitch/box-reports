# BD PREREG (W-BD2, T-BRACKET-DD Parts D, C, E), 2026-11-16 ~15:20Z, before any result is scored
Base: TL3_EV_JN05W2JL2 only (43 months). Engine: exact via tp_launch/jn05_run2, hook th_bd/bd_hooks.py, tag BD.
Objective: max DD and worst week, full 43 months AND HOLD (2025-11..2026-04) incl. path 2025-11-17..12-10, mean $/wk not more than 5% below the reference. L3M never ranks.
PART D (screen first on JL2 trade paths offline, then exact): half off at X in 20,30,40 pts; remainder T2 in 58 (own target), 85, or trail 15/20/30 (no target); stop to breakeven yes/no. 15 book x session cells.
PART C: target = min(58, k x distance ahead to nearest of prior-day H/L, overnight H/L, session H/L, VWAP band 2), k 0.6/0.8/1.0, floor 20; and k x (HAR forecast range - range so far), k 0.5/0.75/1.0, floor 20, never beyond the forecast.
PART E: target steps to 40 then 25 after 15/30/60 min; time stop 30/60/90 min when below +5 pts.
Candidate pass (per window HOLD, L6M): real DD cut >= 0 vs reference AND real beats ALL 3 placebos and ALL 3 matched random controls on DD cut and on d mean, d mean >= -5% of reference mean, neighbours (one step in X, T2/trail, BE) also DD cut > 0 in HOLD. Missing control = not finished. Never relaxed.
Placebo = the same rule applied to a pseudo-random subset of ALL signals (every book x session), same expected count as the cell's signals (3 seeds). Matched random control = the same rule on a pseudo-random 50% of the cell's own book x session signals (3 seeds; same book x session x month mix, half the count, read against half the real effect).
Half-lot: base engine lots are 1-2; live = 1.75 x base, so the half is fractional in base lots (a live 2-lot trade splits 1+1); fees per contract unchanged. Lots at live values = rule changes no lots; constant-risk column identical for D/C/E because the stop is unchanged (BE only after the partial).
W44 (2026-W44) removed rows on L3M/L6M. $4.84 column: net - lots x 3.66. Windows: HOLD, L6M, L3M, then GAP, PRE, X'.
