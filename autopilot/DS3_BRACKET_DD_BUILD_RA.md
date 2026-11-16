# DS3_BRACKET_DD_BUILD_RA - M7 London cap 3 on the live-equivalent base JN05W2JL2 (W-RA)

**VERDICT (drawdown first; pass rule = real cell beats ALL its controls on stack max DD in HOLD and L6M and mean not worse than -5%; missing controls = not finished): not finished: HOLD controls 0/7, L6M 0/7. No PASS claim until the controls are in.**

Built epoch 1794846011. Cells: TL3_RA_JL2_M7L_CAP3 (rule: M7, London session 02:00-08:29 ET, block entry once 3 M7 trades closed in the Globex-day session; spec autopilot/SPEC_M7_LONDON_CAP3.md) vs reference TL3_EV_JN05W2JL2. Controls: PL1-3 = random block drawn once per signal second at block rate 0.703 (M7 London, entries with >=1 close); PP1-3 = persistent draw (one draw per session instance and number of closes, so a blocked idea is not redrawn at the next signal; p 0.208 = open-loop keep of cap 3 on the JL2 reference sequence, 0.594). Dollars are base-lot engine net_fee at $1.18/contract RT; columns x175 = live lots; d_mean_484 = mean change repriced at $4.84/contract. Drawdown from cumulative daily P&L of the scope. PATH EFFECT = FREED-BOOK REPLACEMENT (generic): the controls are the baseline.

identity of the placebo branch (PP with p=0, 202610): 642 trades net 27487.58 vs JL2 642 net 27487.58 -> IDENTICAL

Windows landed (cells present / 7) : HOLD 0/7, L6M 0/7, L3M 0/7, GAP 0/7, PREUW 0/7, X' 0/7

## Earlier statements about random placebos (see DS3_REENTRY_ALL.md 5a)
See autopilot/RA_PLACEBO_VOID_LIST.md.
