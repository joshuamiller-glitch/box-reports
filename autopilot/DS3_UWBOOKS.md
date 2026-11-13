# DS3_UWBOOKS — lead composite (2026-11-13 ~16:30Z; research only, no PASS claims)
Sources: DS3_UWBOOKS_B1.md (W-UB1: F1 dealer/levels, F2 levels, F6, F7; NQ+ES), DS3_UWBOOKS_B2.md (W-UB2: Tide, flow bursts, dark pool, IV; NQ/ES/RTY), DS3_UWBOOKS_DATA.md. Pages refresh every 3 h (B1 ~18:45Z, B2 ~20:00Z).

## Verdict so far: WEAK TO NONE
- B1: nothing beats the shifted-time null (F1/F2 null matches or beats best recents and Calmar; tolerant-gate pass share below null). F6/F7 pass more often than null but best $/wk inside null range (drift).
- B2: tide nothing; dark-pool/IV Asia "short" cells = one-way drift (unconditional baseline gives the same, PRE-UW negative). One lead: NQ short fading NDX 1-min bullish net-premium burst, NYPM (L6M +1,559/wk, n=116, DD 2,268, WF +651, beats own 10+10 placebos, corr to stack 0.12) but FAILS the family null so far (4 of 8 draws done, all above observed).
- Best per session (B1, all weak, thin n 20-47): asia F2 SPX oi-flip touch_up long NQ; london F1 QQQ g_oi d1_up long ES; pre F1 SPX v_oi lo_d short NQ; nyam F1 QQQ v_dir d15_up short NQ (L6M 3,022, n=27, WF +701); nypm F1 NDX c_dir d1_dn short NQ.
- Caveat: drift (NQ Asia short ~$6.5k/wk unconditional over L6M) inflates any directional cell; compare to the every-day baseline.

## Joint stage: first-order only (weekly corr with live books -0.16..+0.18; exact-engine TL3_UW_ hooks not yet built). Not done: RTY/YM runs, ES/RTY pairs, F4T tape, 0DTE tape, megacap flow, no-UW F6/F7 baseline.
## Assumptions unmeasured: 60-120 s UW delivery lag, ES/RTY/YM slippage and RTY/YM fees.
