T-TH-PROFIT ADDENDUM — the ADAPTIVE profit-protection policy: re-fit on recent data, walk-forward, published as a live policy file (2026-10-29)

Research only. No live, execution-server or chart change. UNTOUCHED never read. Same dataset (THP A), same MEASURED fills. This addendum changes the objective of the learned layer (C): the user does not want one fixed rule fitted to 2023-26; he wants a policy that is re-fitted on RECENT data and keeps updating. All classic-rule results (B) stand as the baseline.

1. Walk-forward re-fitting (the honest test of an adaptive policy)

Protocol: at each re-fit date t, fit the policy on the trailing window W ending at t, apply it to the trades of the next step S, then move on. Windows W = 1 / 3 / 6 / 12 months and year-to-date; steps S = 1 day / 1 week / 1 month. The out-of-sample series is the concatenation of every step's applied result — every decision made by a model that never saw that trade. Report that series as the primary number (not PRE/HOLD): paired delta vs hold-to-bracket per trade and per week, by book, by session, by year, with MDE, plus the give-back-saved / upside-forfeited split and the exit rate. Also: the same protocol for the best classic rules (re-select the best rule of the 192 on the trailing window each step) as the simple adaptive baseline, and the live JADE rule as the fixed baseline. Placebo: the same protocol on shuffled labels (within day) and on random exits at the same rate.

2. Models under the protocol (as in C, now re-fitted each step)

Gradient boosting / logistic on the THP A features (path, order book, bars, cross-asset, time, stack) predicting E[remaining pts] and P(target first); optimal-stopping tables; hazard (competing risks); change-point and the flow HMM; quantile regression. Policy actions: hold / tighten (stop to MFE - trail) / take. Report for each model x window x step: the walk-forward delta, and the stability of the policy over time (how much the thresholds move between re-fits; drift). Feature importance per re-fit as a time series: what the policy was keyed on in 2024 vs 2026.

3. Concept drift and the "last 3 months" question

Does recency help? Compare the 3-month window with 12 months and with the full history under the same protocol; report whether short windows beat long ones out of sample or only add noise. Also the regime read: on which weeks the adaptive policy earned its keep (chop vs trend weeks, by VIX tercile), and where the fixed baseline was better.

4. The policy file (what goes live; design it so NT8 needs no model)

Distil each re-fit's policy into a table over <= 4 features that NT8 can compute from ticks and 1-min bars (candidate features: unrealised pts as % of target, seconds since MFE, drawdown from MFE in pts, 60-s aggressor delta or 5-level depth imbalance if the book is used; state which), with actions hold / tighten / take and the trail value, per book (or pooled with a per-book offset). Report how much of the model's walk-forward gain the table keeps (target >= 80%). Specify the file: THP_POLICY.json with version, fit date, window, per-book tables (feature grid breakpoints, action per cell, trail pts), a validity date, and a checksum; written to autopilot/ (the mirror) each re-fit. The NT8 side (my job): D6 reads the file at the 18:00 ET session open, uses it only if valid for the day, falls back to hold-to-bracket if the file is missing or stale. Write the file for the current date from the best walk-forward policy once section 1 shows which one, even if the gain is inside the MDE — label it with the walk-forward number so the user knows what he is running.

5. Report

DS3_THP_WF.md: the walk-forward table (model x window x step), the drift series, the regime read, the distilled policy and its retained gain, and the plain sentence: "re-fitting on the last N months, the policy adds X pts/trade out of sample (MDE Y) on books A, B, C and nothing on the rest" — or that nothing adaptive beats holding. Then THP_POLICY.json. MORNING.md every 2 h. This runs inside the 4-8 hour budget; the learned-layer agents switch to this protocol now.
