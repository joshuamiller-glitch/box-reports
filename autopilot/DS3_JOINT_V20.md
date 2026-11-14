# DS3_JOINT_V20 - joint of the shelved candidates on JN05W2 (PRIORITY 4) - W-JV

VERDICT_PLACEHOLDER

Generated 2026-11-14 16:13 UTC (epoch 1794672801). Exact engine (TP), base JN05W2 = live panel + F3 + E1 + C22 + BR3S + FLAT45K, all layers ON, measured fills (engine slip 0.8; structure stop 1.4 adverse; $4.84 RT). Shadow only, no PASS claim. Prereg autopilot/JOINTV20_PREREG.md (sha in DECISIONS.md).

Candidates: **A** = SM_A6_halfNP7 (first trade of a book-session lost -> later signals of that book-session at half lots, books K7 M7 U7 H7 A7; P7 untouched). **B** = U7 time stop on fresh entries (at 15:00 after the first fill, if open P&L < -10 pts: market exit, fresh context only). **C** = U7 Keltner-mid structure stop (stop at 5-min EMA20 mid - 2 pts, filled 1.4 pt adverse, lots x 60/stop distance clamped 25..60). Full specs in section 6.

Identity: TL3_JV_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

## 1. Drawdown first: all combinations vs JN05W2 (cut % = max-DD of the weekly series vs JN05W2, + = shallower; worst wk d = change of the worst week; stops/wk; 5 best JN05W2 weeks kept; winning weeks turned losing; d mean $/wk)

## 2. The recent max drawdown is one week (2026-W44): L6M / L3M with W44 removed from both cell and JN05W2

| set | window | maxDD (W44 out) | JN05W2 (W44 out) | cut % | d mean $/wk (W44 out) | cut % with W44 in |
|--|--|--|--|--|--|--|

## 3. Trend-week clause (L6M, program convention: 5 best LPB_BASE weeks) and bi-weekly walk-forward vs JN05W2 (43 months)

| set | 5 best LPB wks $ (cell / JN05W2 / LPB_BASE) | LPB winning wks turned losing | weeks beating JN05W2 (of 26) | WF beat % | WF cut % | WF d mean $/wk |
|--|--|--|--|--|--|--|

## 4. Interaction table (joint vs sum of the singles, L6M and HOLD; d = cell - JN05W2; synergy = joint - sum of singles; DD synergy in cut-% points)

| joint | window | joint DD cut % | sum of singles' cut % | synergy | joint d mean | sum singles d mean | synergy $/wk |
|--|--|--|--|--|--|--|--|

## 5. Exact placebos (A: first-trade-lost read from 11 / 23 / 37 days earlier; B and C: same trigger, exit at a random later second 1..60 min if still open; PLk_ABC = all three placebos together)

| real set | window | real cut % | real d mean | placebo cut % (11/23/37 or seeds 1/2/3) | placebo d mean | real beats all 3 placebos on cut? |
|--|--|--|--|--|--|--|
