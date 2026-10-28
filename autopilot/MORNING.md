
### 00:05Z OVERNIGHT PROGRAM started (DIRECTIVE_OVERNIGHT_20261027.md)
Agents: D3O1 (A, ORbase/DRbase), D3CL1 (B, block 4 + RVW1 robustness), D3DN (C), D3BK (D), D3TH (E), D3SZR (F), D3FW (G), D3BA. A remaining (3.10/3.11 footprint/L2 on top cells, blocks iii/iv) follows D3O1 ORbase. T-CLOSE blocks 1-3: 0 PASS / 1 CANDIDATE / 660 DEAD. RVW1|F30 is execution-fragile (needs resting limit at touch).

### Item G (D3FW) - questions for you
1. ST/HM: DualStrat2 trade file has no trade since Mon 10-26 10:44 ET but a <sim-acct> file shows ST/HM/WT through Tue 15:34. Is the live book halted/locked or the feed stale? (W44 row -$47,620 / 22 trades is a Monday snapshot.)
2. KB_LossExit 10-26 19:57: -13.53 pts but +$10,525 pnlNet - looks like a merged multi-fill row; please confirm.
3. What was the v1.3 deploy time for the DS4/DS5 files (to cut the tick-routing incident)?
4. OK to add the DS5-mix row to paper_all and fix the evaluator (timezone Chicago vs Eastern; PE_/PB_ assignment)?

### Item F (sizing by regime): 0/24 confirmed. Compression, VIX-tercile, day-of-week all DEAD; no rule fixes 2023 (calm trending year, not visible to vol). Only lead: vol-scaled lots (8-wk trailing SD per book, clip 0.5-2): holdout maxDD -$68k, SD -$8.9k, mean +$6k lot-matched; at unmatched lots it is a pure risk trim (mean same, SD -$6..10k). Not live-eligible: failed maxDD/worst-week gate for the 4-wk pick; 8-wk was a post-holdout reading. Follow-up prereg with PB book + size cost queued.

### Item E (Trade Health loss-side): no book is helped. KB/SM/PE/DN NEUTRAL (underpowered, point estimates -1.0..-2.5 pts/trade), MV and MA HURTS-LEAD (not confirmed; 2023 span positive), basket legs NEUTRAL (ES leg -19 pts on HOLD, non-gate). Forward ST/HM: only 7 of 63 cuts replayable (tape ends 10-23); cannot distinguish anything yet (needs ~3,300 cuts for 3 pts). QUESTION: given the data lean against it, do you want to switch the loss-side TH off on DS3 KB/PE/SM/PB in Sim? (Not gate-supported; your call.)

### Item D (block/un-block rules): 0/28 supported. Un-block 09:30-09:59 = +$5.8k/wk only on the existing-row basis (ST+HM carry it); on regenerated rows +$3.1k [-4.4k,+10.4k], MDE 10.4k, 2026 negative, maxDD +$23-77k. 09:00-09:29 and 15:00-16:54 unblocks lose. FOMC-day NY block is the single best-supported change (+$1.1k/wk [-0.9k,+3.4k], consistent signs everywhere) but is 0.35 x MDE - not a live change. Side finding: published live baseline has shadowing; corrected live stack WF 45,947 vs 44,867.
