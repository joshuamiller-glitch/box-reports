# DS3_CONFLUENCE_RESCUE - step 6, first page (W-CF3), SCREEN ONLY

VERDICT (data ends 2026-10-30): on the zero-lot cells (hypothetical bracket outcomes of signals the engine did not take), USER_SET_V0 all-5 picks better-than-average signals in M7 Asia, A7 NY AM and A7 NY PM, but the size of the edge is small (0.06 to 0.08 R per signal on the hypothetical 1-minute bracket) and the outcome is hypothetical, so every cell is "improved but still weak / not yet tested": nothing is rescued and nothing has been run in the exact engine. No PASS claim.

Basis: signals_all.parquet from W-CF1 (191,520 signals; in_pos = 1 rows dropped = real entry opportunities), hypothetical 1m outcome (book/session median target and stop, no live protections, no costs of the live stack): a SCREEN, never a result. Conditions: c_U_1..5 (USER_SET_V0, registered DECISIONS.md sha 13e2d06bd31c20a1) from entry_table_universe.parquet. Control: 300 random subsets of the same size within month (percentile = share of random subsets with a lower mean R). Output /mnt/l2/l2vast/_confl/cf3/rescue_screen_v0.csv; code code/th_confl_cf3/rescue_screen.py. Cells from W-CF1's benched_list.csv ('session lots 0' cells only).

| cell | signals (hyp R mean) | rule | kept | R kept | matched-count pctl | read |
|--|--|--|--|--|--|--|
| M7 Asia (16,747 zero-lot signals) | 17,049 (0.046) | all 5 / >=4 | 3,747 / 11,035 | 0.080 / 0.060 | 0.993 / 1.000 | improved, still weak (4.8 vs 2.8 pts per signal) |
| A7 London | 5,449 (0.041) | all 5 | 1,910 | -0.014 | 0.000 | no checklist helps (the list picks WORSE signals) |
| A7 NY AM | 3,628 (0.030) | all 5 / >=4 | 1,950 / 3,345 | 0.064 / 0.039 | 1.000 / 0.980 | improved, still weak |
| A7 NY PM | 3,988 (-0.005) | all 5 | 2,063 | 0.077 | 1.000 | improved, still weak (all signals about zero) |
| M7 NY PM | 5,009 (0.006) | >=4 | 3,496 | 0.022 | 0.943 | no checklist helps (all-5 0.420) |
| H7 London | 881 (0.049) | any | - | 0.04-0.07 | 0.23-0.75 | no checklist helps |
| M7 pre, A7 pre, H7 pre/NY PM, K7 pre, P7 pre | 220-1,639 each | any | - | zero or negative | mostly <= 0.5 (P7 pre all-5 0.013: worse) | no checklist helps |
| U7 NY PM | 258 (-0.033) | all 5 | 50 | 0.223 | 0.953 | 50 signals: below every floor, ignore |

What is NOT done (and why this is only a first page): the exact engine has no outcome for these cells (zero lots / disabled), so a candidate must go through the injection hook (code/th_uwbooks/uw_inject.py) with real lots to get costs, locks and protection layers; the hypothetical bracket ignores the cut and lock lines; the checklist here is the user's list only, not a searched one (the searched step-4 lists need the skipped-signal universe condition columns for Blocks M/CF2/CF4-CF6, which exist for taken rows only); X1-X8 and S7 never fire a try_entry in the engine pass, X3/X4/X5 (disabled benched books, ~30k/19k/4k signals) are not scored yet; no weak-live-book (H7, A7, O7) taken-signal search beyond the cell results of DS3_CONFLUENCE.md; other instruments, leaderboard rows and 153 families not started. Next: injection runs for M7 Asia all-5 and A7 NY AM / NY PM all-5 (the three cells with percentile >= 0.98), as screens that then need walk-forward and recent / older windows; then X3/X4 with the same list.
