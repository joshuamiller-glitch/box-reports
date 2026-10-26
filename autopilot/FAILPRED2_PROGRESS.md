# FAILPRED-2 progress (trackFAILPRED2)
- 17:45Z start. Read directive, Step 1 report. Benchmark reproduced exactly (identity run |x-x0| = 0; WF $24,975/wk SD 104,523 maxDD 401,293).
- 17:53Z PREREG_FAILPRED_STEP2.md frozen (sha in DECISIONS.md). Simulator candsim.py (1-s tick-level fills) + d2mod.py (C0-C3 regen, R11 assembly) + fp2lib.py in l2vast/failpred2/.
- Running: score2.py (candidate sims, D2 engine runs incl. non/ceiling/2x/type, 500-draw placebos).
- 18:25Z DONE. Holdout scored once after non-holdout text (hold2.py). 0/40 pass. Final report autopilot/REPORT_FAILPRED_STEP2.md.
