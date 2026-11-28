# MGMT_TAPE_REVIEW (W-DYNA, 27 Nov 17:36 UTC; order 1723Z B3 + 1733Z): what the manager did, trade by trade, in plain words - DRY RUN on the MGMT v0 rows (middle design, books alone bare, the (set, month) rows that had finished)

Answer first. How to read: each block is one trade: stem and session, entry time ET, side, lots, entry price, safety stop (1.5 x the book's own stop, the only order at the start), result of the managed trade against the SAME signal under the book's own bracket, MFE / MAE (best and worst open profit in R of the book's own stop, from the 1-s tape), minutes under water, the book's health vote over time (ninth vote: this trade against THIS book's own winners; A = it has been deeper / longer under water than 90% of past winners (causal: only winners that ended before this entry) or has shown less early progress than 75% of winners by that minute; W = better than the median winner; N = nothing; - = fewer than 40 past winners), then one line per manager decision: clock time, price, open R, what it did, the rule and its plain meaning. For the PLAYBOOK rows (PB1) a line 'screens VVVVVVVV' (NQ chart, NQ tape/book, ES/RTY/YM, other markets, TICK, VIX, megacaps/ETF, UW tide; A against / W with / N nothing / - abstains) is written whenever the vote string changes: the v0 MGMT rows carry no votes (their algo_log has only actions), so this dry run shows actions and rules only. Selection per session: the 20 WORST give-backs (largest open profit given back in $), the 20 BEST runners (final R largest among trades that kept at least 80% of a peak of 1 R or more), 50 RANDOM trades (seed 11, sorted by time). Josh: read a block and say 'a professional would / would not do that'.

What the dry run already shows (v0, middle design, not a result; the v0 rows are the first version and carry known issues):
- Losers: in the give-back lists the manager often shows rule L3 ('stuck too long and still not a winner') as the only action on losing trades: it tightened to the own stop and the trade then ended at -1.0 to -1.5 R (NY-FIB: -1.13 R and -1.48 R against -0.97 R under the own bracket): with a wide safety stop (1.5 x) the manager can make a loser WORSE than the bracket.
- Winners: P1 (trail protecting the winner) and P5 (take a part at a level just ahead) fire on the runners; the best-runner blocks show +4 R trades (NY-NODE 2025-04-07: +4.28 R, $+46,253 against +0.33 R / $3,583 under the bracket) that the own bracket cut at +0.33 R.
- The four counts show the same split in numbers: the managed rows win big on losers cut early and give-backs prevented, and lose it back on winners cut short and losers made worse; matched pairs net -$317k (NY AM) and -$599k (Asia).
- Slot effects (no rule 6 in v0): the managed run takes 1,866 entries the own bracket did not (NY AM; net +$352k) and misses 1,409 (net +$323k); Asia 847 (-$50k) and 436 (+$433k).
- Honest limits of this dry run: only the (set, month) rows that finished (NY AM 60 rows, Asia 42); the health vote percentiles come from the own-bracket winners of the same book only; no screen votes in v0 (the generator reads them from the PB1 rows when they land: command in the page footer).


# PART 1: NY AM

# NY AM (NY): managed rows MGMIDL1_A, 4422 trades from 60 finished (set, month) rows, matched to the book's own bracket on 2556 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 198 | +1620900 | 2023 +233955, 2024 +325170, 2025 +222190, 2026 +839585 |
| winners cut short | 740 | -3919230 | 2023 -694170, 2024 -868565, 2025 -317305, 2026 -2039190 |
| losers cut early | 473 | +4208980 | 2023 +790175, 2024 +1090330, 2025 +439700, 2026 +1888775 |
| losers made worse | 327 | -1017915 | 2023 -34435, 2024 -184025, 2025 -163280, 2026 -636175 |
| matched pairs (all) | 2556 | -316515 | 2023 +7240, 2024 +26355, 2025 +115735, 2026 -465845 |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 1866 trades, net $ +351888; entries that exist only under the own bracket in the same months (blocked by a carried trade): 1409 trades, net $ +322618. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## NY AM: the 20 WORST give-backs (largest open profit given back, $)

**NY-NODE (NY AM MF4)** 2025-04-07 10:18:18 ET, SHORT 6 lots at 18187.92, safety stop 18322.92 (1.5 x own stop 90 pts). Result managed +386 pts/lot (+4.28 R, $+46253) ; own bracket result +30 pts (+0.33 R, $+3583). MFE +9.65 R, MAE -0.19 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:19:18  price 17971.92 (open +2.40 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:19:18  price 17971.92 (open +2.40 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:20:03  price 17965.17 (open +2.47 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:20:33  price 17866.62 (open +3.57 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:20:48  price 17827.47 (open +4.00 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:21:03  price 17784.27 (open +4.49 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:22:18  price 17681.67 (open +5.62 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:23:33  price 17607.42 (open +6.45 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:23:48  price 17530.47 (open +7.30 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:18  price 17523.72 (open +7.38 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:33  price 17473.77 (open +7.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:48  price 17430.57 (open +8.42 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:28:48  price 17417.07 (open +8.56 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:29:03  price 17403.57 (open +8.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:29:18  price 17350.92 (open +9.30 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 17802.42

**NY-OFI (NY AM MF5)** 2025-04-07 10:18:41 ET, SHORT 3 lots at 18069.25, safety stop 18159.25 (1.5 x own stop 60 pts). Result managed +233 pts/lot (+3.89 R, $+14001) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +12.49 R, MAE -0.55 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:20:11  price 17947.75 (open +2.03 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  10:20:11  price 17947.75 (open +2.03 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:20:26  price 17820.85 (open +4.14 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:20:56  price 17803.75 (open +4.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:22:11  price 17696.65 (open +6.21 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:22:26  price 17666.05 (open +6.72 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:23:26  price 17639.05 (open +7.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:23:41  price 17576.05 (open +8.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:23:56  price 17558.95 (open +8.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:26  price 17463.55 (open +10.10 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:41  price 17450.05 (open +10.32 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:24:56  price 17453.65 (open +10.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:28:41  price 17411.35 (open +10.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:28:56  price 17407.75 (open +11.02 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:29:11  price 17364.55 (open +11.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:29:26  price 17351.05 (open +11.97 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 17835.83

**NY-FIB (NY AM MF1)** 2025-04-09 10:52:48 ET, SHORT 6 lots at 17280.12, safety stop 17460.12 (1.5 x own stop 120 pts). Result managed -181 pts/lot (-1.51 R, $-21762) ; own bracket result -120 pts (-1.00 R, $-14392). MFE +0.61 R, MAE -1.52 R, 22 min under water (longest 20 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 14m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 17461.42

**NY-FIB (NY AM MF1)** 2026-06-25 09:50:13 ET, LONG 6 lots at 29611.83, safety stop 29431.83 (1.5 x own stop 120 pts). Result managed -180 pts/lot (-1.50 R, $-21617) ; own bracket: not taken (slot effect). MFE +0.52 R, MAE -1.62 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29431.75

**NY-FIB (NY AM MF1)** 2024-08-05 09:41:01 ET, SHORT 6 lots at 17748.92, safety stop 17928.92 (1.5 x own stop 120 pts). Result managed -180 pts/lot (-1.50 R, $-21662) ; own bracket: not taken (slot effect). MFE +0.51 R, MAE -1.44 R, 6 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 5m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 17929.38

**NY-NODE (NY AM MF4)** 2024-12-20 10:24:22 ET, LONG 6 lots at 21377.25, safety stop 21242.25 (1.5 x own stop 90 pts). Result managed +189 pts/lot (+2.10 R, $+22643) ; own bracket result +30 pts (+0.33 R, $+3593). MFE +4.59 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  10:27:07  price 21416.40 (open +0.43 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  10:27:07  price 21416.40 (open +0.43 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:27:22  price 21425.85 (open +0.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:27:37  price 21425.85 (open +0.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:28:22  price 21438.00 (open +0.68 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:28:37  price 21451.50 (open +0.83 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:29:37  price 21459.60 (open +0.92 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:30:07  price 21473.10 (open +1.06 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:30:22  price 21481.20 (open +1.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:30:37  price 21487.95 (open +1.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:30:52  price 21493.35 (open +1.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:32:07  price 21500.10 (open +1.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:32:22  price 21521.70 (open +1.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:32:37  price 21528.45 (open +1.68 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:22  price 21533.85 (open +1.74 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:55:22  price 21550.05 (open +1.92 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:02:22  price 21554.10 (open +1.97 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:02:37  price 21559.50 (open +2.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:02:52  price 21566.25 (open +2.10 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:03:37  price 21578.40 (open +2.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:03:52  price 21579.75 (open +2.25 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:04:22  price 21589.20 (open +2.35 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:04:37  price 21595.95 (open +2.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:05:07  price 21597.30 (open +2.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:05:22  price 21602.70 (open +2.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:05:37  price 21605.40 (open +2.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:05:52  price 21614.85 (open +2.64 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:12:52  price 21622.95 (open +2.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:13:37  price 21624.30 (open +2.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:17:07  price 21628.35 (open +2.79 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:17:37  price 21633.75 (open +2.85 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:17:52  price 21643.20 (open +2.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:18:07  price 21647.25 (open +3.00 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:18:37  price 21651.30 (open +3.04 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:21:52  price 21659.40 (open +3.13 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:22:07  price 21662.10 (open +3.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:22:22  price 21664.80 (open +3.19 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:22:37  price 21667.50 (open +3.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:24:37  price 21671.55 (open +3.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:30:37  price 21670.20 (open +3.25 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 21566.00

**NY-NODE (NY AM MF4)** 2026-06-12 10:29:46 ET, LONG 6 lots at 29537.54, safety stop 29402.54 (1.5 x own stop 90 pts). Result managed -121 pts/lot (-1.35 R, $-14572) ; own bracket: not taken (slot effect). MFE +0.90 R, MAE -1.32 R, 6 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 12m:A
  10:44:47  price 29416.04 (open -1.35 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  10:44:47  price 29416.04 (open -1.35 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: ExAlgoStop_L3 at 29416.17

**NY-FIB (NY AM MF1)** 2026-06-09 11:18:11 ET, SHORT 6 lots at 29192.75, safety stop 29372.75 (1.5 x own stop 120 pts). Result managed +179 pts/lot (+1.49 R, $+21498) ; own bracket result +120 pts (+1.00 R, $+14393). MFE +3.17 R, MAE -0.15 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:22:26  price 29120.75 (open +0.60 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:22:26  price 29120.75 (open +0.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:22:41  price 29106.35 (open +0.72 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:22:56  price 29099.15 (open +0.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:23:41  price 29059.55 (open +1.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:24:26  price 29043.35 (open +1.24 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:24:56  price 29019.95 (open +1.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:25:11  price 29014.55 (open +1.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:26:11  price 29005.55 (open +1.56 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:26:26  price 28983.95 (open +1.74 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:26:41  price 28965.95 (open +1.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:27:26  price 28949.75 (open +2.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:27:41  price 28940.75 (open +2.10 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:28:11  price 28926.35 (open +2.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:28:26  price 28906.55 (open +2.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:28:41  price 28901.15 (open +2.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:28:56  price 28895.75 (open +2.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:29:11  price 28859.75 (open +2.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:35:26  price 28834.55 (open +2.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:38:41  price 28821.95 (open +3.09 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:42:41  price 28920.95 (open +2.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 29013.54

**NY-VALUE (NY AM MF2)** 2026-06-09 10:33:59 ET, SHORT 6 lots at 29430.58, safety stop 29520.58 (1.5 x own stop 60 pts). Result managed +156 pts/lot (+2.59 R, $+18653) ; own bracket result +60 pts (+1.00 R, $+7203). MFE +5.81 R, MAE -0.92 R, 6 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 4m:A
  10:43:44  price 29370.28 (open +1.01 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  10:43:44  price 29370.28 (open +1.01 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:43:59  price 29341.48 (open +1.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:29  price 29305.48 (open +2.08 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:44  price 29282.98 (open +2.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:45:59  price 29266.78 (open +2.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:14  price 29253.28 (open +2.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:29  price 29228.98 (open +3.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:59  price 29209.18 (open +3.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:47:29  price 29185.78 (open +4.08 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:47:59  price 29160.58 (open +4.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:48:14  price 29165.08 (open +4.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:48:44  price 29129.08 (open +5.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:48:59  price 29119.18 (open +5.19 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:49:29  price 29102.08 (open +5.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:54:29  price 29179.48 (open +4.19 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 29275.08

**NY-NODE (NY AM MF4)** 2026-06-25 09:50:03 ET, LONG 6 lots at 29637.62, safety stop 29502.62 (1.5 x own stop 90 pts). Result managed -133 pts/lot (-1.48 R, $-15952) ; own bracket result +30 pts (+0.33 R, $+3608). MFE +0.59 R, MAE -1.47 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29504.75

**NY-FIB (NY AM MF1)** 2026-06-25 09:35:06 ET, SHORT 6 lots at 30077.21, safety stop 30257.21 (1.5 x own stop 120 pts). Result managed +148 pts/lot (+1.24 R, $+17803) ; own bracket result +120 pts (+1.00 R, $+14388). MFE +2.76 R, MAE -0.10 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:37:36  price 30044.81 (open +0.27 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  09:37:36  price 30044.81 (open +0.27 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  09:37:51  price 30044.81 (open +0.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:38:06  price 30023.21 (open +0.45 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:38:21  price 30014.21 (open +0.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:38:36  price 29999.81 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:40:21  price 29978.21 (open +0.83 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:40:51  price 29951.21 (open +1.05 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:41:21  price 29931.41 (open +1.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:41:51  price 29922.41 (open +1.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:06  price 29909.81 (open +1.40 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:21  price 29882.81 (open +1.62 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:36  price 29864.81 (open +1.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:06  price 29839.61 (open +1.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:21  price 29801.81 (open +2.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:51  price 29771.21 (open +2.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:44:51  price 29753.21 (open +2.70 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29928.79

**NY-NODE (NY AM MF4)** 2026-06-09 10:36:19 ET, SHORT 6 lots at 29419.33, safety stop 29554.33 (1.5 x own stop 90 pts). Result managed +163 pts/lot (+1.81 R, $+19533) ; own bracket: not taken (slot effect). MFE +3.79 R, MAE -0.70 R, 6 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  10:43:49  price 29365.33 (open +0.60 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:43:49  price 29365.33 (open +0.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:04  price 29342.38 (open +0.85 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:19  price 29318.08 (open +1.12 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:44:34  price 29287.03 (open +1.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:44:49  price 29287.03 (open +1.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:04  price 29266.78 (open +1.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:19  price 29247.88 (open +1.91 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:46:34  price 29228.98 (open +2.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:47:04  price 29189.83 (open +2.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:47:34  price 29189.83 (open +2.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:47:49  price 29173.63 (open +2.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:48:04  price 29145.28 (open +3.04 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:48:49  price 29120.98 (open +3.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:49:19  price 29112.88 (open +3.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:49:34  price 29103.43 (open +3.51 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:54:34  price 29185.78 (open +2.59 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 29256.50

**NY-VALUE (NY AM MF2)** 2026-07-10 10:32:59 ET, SHORT 6 lots at 29803.38, safety stop 29893.38 (1.5 x own stop 60 pts). Result managed -88 pts/lot (-1.46 R, $-10517) ; own bracket result +60 pts (+1.00 R, $+7178). MFE +1.43 R, MAE -2.22 R, 6 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29890.96

**NY-VALUE (NY AM MF2)** 2026-06-25 10:34:27 ET, SHORT 6 lots at 29644.88, safety stop 29734.88 (1.5 x own stop 60 pts). Result managed -85 pts/lot (-1.42 R, $-10207) ; own bracket result -60 pts (-1.01 R, $-7252). MFE +1.38 R, MAE -1.52 R, 9 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29729.88

**NY-VALUE (NY AM MF2)** 2026-05-15 09:40:24 ET, LONG 6 lots at 29180.12, safety stop 29090.12 (1.5 x own stop 60 pts). Result managed -89 pts/lot (-1.49 R, $-10742) ; own bracket result +60 pts (+1.00 R, $+7208). MFE +1.09 R, MAE -1.47 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29090.67

**NY-VALUE (NY AM MF2)** 2026-06-10 11:48:15 ET, SHORT 6 lots at 28705.50, safety stop 28795.50 (1.5 x own stop 60 pts). Result managed -87 pts/lot (-1.45 R, $-10417) ; own bracket result +60 pts (+1.00 R, $+7193). MFE +1.12 R, MAE -1.69 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 28792.25

**NY-VALUE (NY AM MF2)** 2025-04-07 11:02:13 ET, LONG 6 lots at 17738.42, safety stop 17648.42 (1.5 x own stop 60 pts). Result managed -90 pts/lot (-1.50 R, $-10787) ; own bracket result -56 pts (-0.94 R, $-6762). MFE +1.06 R, MAE -1.55 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 17648.58

**NY-NODE (NY AM MF4)** 2026-06-24 10:48:52 ET, LONG 6 lots at 29852.00, safety stop 29717.00 (1.5 x own stop 90 pts). Result managed -90 pts/lot (-1.00 R, $-10842) ; own bracket result +30 pts (+0.33 R, $+3593). MFE +0.70 R, MAE -0.93 R, 12 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 21m:A
  11:05:22  price 29853.35 (open +0.01 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:05:22  price 29853.35 (open +0.01 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 29761.71

**NY-NODE (NY AM MF4)** 2026-06-25 09:39:03 ET, SHORT 6 lots at 30018.54, safety stop 30153.54 (1.5 x own stop 90 pts). Result managed +122 pts/lot (+1.35 R, $+14573) ; own bracket result +30 pts (+0.33 R, $+3598). MFE +3.04 R, MAE -0.12 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:40:18  price 29979.39 (open +0.43 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  09:40:18  price 29979.39 (open +0.43 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  09:40:33  price 29979.39 (open +0.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:40:48  price 29948.34 (open +0.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:41:18  price 29933.49 (open +0.95 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:41:33  price 29933.49 (open +0.95 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:03  price 29910.54 (open +1.20 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:18  price 29878.14 (open +1.56 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:42:33  price 29864.64 (open +1.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:03  price 29849.79 (open +1.88 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:18  price 29817.39 (open +2.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:33  price 29797.14 (open +2.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:43:48  price 29760.69 (open +2.86 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:44:48  price 29749.89 (open +2.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29897.04

**NY-FIB (NY AM MF1)** 2026-06-12 10:51:33 ET, LONG 6 lots at 29398.17, safety stop 29218.17 (1.5 x own stop 120 pts). Result managed +213 pts/lot (+1.78 R, $+25583) ; own bracket: not taken (slot effect). MFE +3.04 R, MAE -0.10 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:52:48  price 29498.97 (open +0.84 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:52:48  price 29498.97 (open +0.84 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:53:03  price 29534.97 (open +1.14 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:53:18  price 29536.77 (open +1.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:54:33  price 29567.37 (open +1.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:55:03  price 29614.17 (open +1.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:55:18  price 29621.37 (open +1.86 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:56:33  price 29628.57 (open +1.92 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:00:18  price 29644.77 (open +2.06 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:00:48  price 29659.17 (open +2.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:06:18  price 29664.57 (open +2.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:11:04  price 29671.77 (open +2.28 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:33:06  price 29691.57 (open +2.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 29611.42

## NY AM: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**NY-OFI (NY AM MF5)** 2024-08-01 11:28:18 ET, SHORT 3 lots at 19270.00, safety stop 19360.00 (1.5 x own stop 60 pts). Result managed +100 pts/lot (+1.66 R, $+5986) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +2.07 R, MAE -0.23 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W
  11:36:18  price 19227.70 (open +0.70 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:36:18  price 19227.70 (open +0.70 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:36:33  price 19225.00 (open +0.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:37:03  price 19222.30 (open +0.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:40:03  price 19216.90 (open +0.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:40:18  price 19204.30 (open +1.09 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:40:33  price 19189.90 (open +1.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:42:18  price 19172.80 (open +1.62 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:42:33  price 19163.80 (open +1.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:43:18  price 19161.10 (open +1.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:45:03  price 19153.90 (open +1.94 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:52:33  price 19203.40 (open +1.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 19170.17

**NY-VALUE (NY AM MF2)** 2026-06-12 09:40:45 ET, SHORT 6 lots at 29442.50, safety stop 29532.50 (1.5 x own stop 60 pts). Result managed +87 pts/lot (+1.45 R, $+10418) ; own bracket result +60 pts (+1.00 R, $+7193). MFE +1.48 R, MAE -0.21 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:41:45  price 29323.70 (open +1.98 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:41:45  price 29323.70 (open +1.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29355.62

**NY-OFI (NY AM MF5)** 2026-08-05 11:45:21 ET, SHORT 3 lots at 29806.00, safety stop 29896.00 (1.5 x own stop 60 pts). Result managed +75 pts/lot (+1.25 R, $+4496) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +1.53 R, MAE -0.22 R, 2 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 7m:W
  11:56:36  price 29758.30 (open +0.80 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:56:36  price 29758.30 (open +0.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:57:06  price 29744.80 (open +1.02 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:57:21  price 29714.20 (open +1.53 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:57:36  price 29732.20 (open +1.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:59:06  price 29755.60 (open +0.84 R of the book stop): state change RUNNING>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:06  price 29755.60 (open +0.84 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29731.00

**NY-OFI (NY AM MF5)** 2026-06-10 09:47:20 ET, LONG 3 lots at 29076.67, safety stop 28986.67 (1.5 x own stop 60 pts). Result managed +71 pts/lot (+1.18 R, $+4236) ; own bracket result +60 pts (+1.00 R, $+3601). MFE +1.45 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:49:05  price 29160.37 (open +1.40 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  09:49:05  price 29160.37 (open +1.40 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  09:49:20  price 29134.27 (open +0.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29147.33

**NY-VALUE (NY AM MF2)** 2026-07-14 11:11:45 ET, SHORT 6 lots at 29841.67, safety stop 29931.67 (1.5 x own stop 60 pts). Result managed +70 pts/lot (+1.17 R, $+8433) ; own bracket result +60 pts (+1.00 R, $+7183). MFE +1.33 R, MAE -0.93 R, 30 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:49:00  price 29847.97 (open -0.11 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:49:00  price 29847.97 (open -0.11 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  11:51:15  price 29795.77 (open +0.77 R of the book stop): state change DEFENDING>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:51:15  price 29795.77 (open +0.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:52:15  price 29789.47 (open +0.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:52:30  price 29790.37 (open +0.85 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:52:45  price 29782.27 (open +0.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:54:45  price 29772.37 (open +1.16 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:55:00  price 29775.97 (open +1.09 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:59:00  price 29767.87 (open +1.23 R of the book stop): state change RUNNING>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:00  price 29767.87 (open +1.23 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29771.33

**NY-OFI (NY AM MF5)** 2023-10-25 09:31:00 ET, SHORT 3 lots at 14726.75, safety stop 14816.75 (1.5 x own stop 60 pts). Result managed +66 pts/lot (+1.11 R, $+3986) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +1.38 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:32:00  price 14703.35 (open +0.39 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:32:00  price 14703.35 (open +0.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:32:15  price 14688.95 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:32:30  price 14691.65 (open +0.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:32:45  price 14687.15 (open +0.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:33:45  price 14684.45 (open +0.70 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:34:00  price 14684.45 (open +0.70 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:34:30  price 14679.05 (open +0.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:35:00  price 14671.85 (open +0.92 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:35:15  price 14661.95 (open +1.08 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:35:30  price 14654.75 (open +1.20 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:36:00  price 14653.85 (open +1.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:36:30  price 14648.45 (open +1.30 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 14660.25

**NY-FIB (NY AM MF1)** 2026-06-09 11:56:08 ET, SHORT 6 lots at 28824.29, safety stop 29004.29 (1.5 x own stop 120 pts). Result managed +128 pts/lot (+1.07 R, $+15333) ; own bracket: not taken (slot effect). MFE +1.29 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:57:08  price 28736.09 (open +0.73 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:57:08  price 28736.09 (open +0.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:57:23  price 28736.09 (open +0.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:57:38  price 28701.89 (open +1.02 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:58:53  price 28685.69 (open +1.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:59:08  price 28696.49 (open +1.06 R of the book stop): state change RUNNING>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:08  price 28696.49 (open +1.06 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 28696.46

**NY-OFI (NY AM MF5)** 2026-06-29 10:53:32 ET, LONG 3 lots at 29652.25, safety stop 29562.25 (1.5 x own stop 60 pts). Result managed +63 pts/lot (+1.05 R, $+3766) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +1.30 R, MAE -0.25 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:00:32  price 29729.65 (open +1.29 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  11:00:32  price 29729.65 (open +1.29 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:00:47  price 29726.05 (open +1.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29715.08

**NY-OFI (NY AM MF5)** 2023-10-05 09:52:00 ET, SHORT 3 lots at 14834.83, safety stop 14924.83 (1.5 x own stop 60 pts). Result managed +61 pts/lot (+1.02 R, $+3686) ; own bracket result +60 pts (+1.00 R, $+3601). MFE +1.21 R, MAE -0.20 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:N 9m:W
  10:00:15  price 14817.73 (open +0.29 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:00:15  price 14817.73 (open +0.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:00:30  price 14814.13 (open +0.35 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:00:45  price 14810.53 (open +0.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:01:15  price 14809.63 (open +0.42 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:01:30  price 14803.33 (open +0.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:01:45  price 14800.63 (open +0.57 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:00  price 14797.03 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:15  price 14795.23 (open +0.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:30  price 14793.43 (open +0.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:45  price 14789.83 (open +0.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:04:30  price 14791.63 (open +0.72 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:05:15  price 14781.73 (open +0.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:05:30  price 14779.03 (open +0.93 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:05:45  price 14776.33 (open +0.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:06:00  price 14776.33 (open +0.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:06:30  price 14775.43 (open +0.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:07:30  price 14771.83 (open +1.05 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:08:15  price 14768.23 (open +1.11 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:08:30  price 14771.83 (open +1.05 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:15:30  price 14783.53 (open +0.85 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 14773.33

**NY-OFI (NY AM MF5)** 2024-08-29 09:54:05 ET, LONG 3 lots at 19578.17, safety stop 19488.17 (1.5 x own stop 60 pts). Result managed +60 pts/lot (+1.01 R, $+3621) ; own bracket result +60 pts (+1.00 R, $+3601). MFE +1.18 R, MAE -0.21 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  09:56:05  price 19640.27 (open +1.03 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:56:05  price 19640.27 (open +1.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:56:20  price 19645.67 (open +1.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:59:50  price 19639.37 (open +1.02 R of the book stop): state change RUNNING>OUT [S1: travelled most of the way and progress stopped: take it]
  09:59:50  price 19639.37 (open +1.02 R of the book stop): closed everything [S1: travelled most of the way and progress stopped: take it]
  exit: ExAlgoAll_S1 at 19638.58

**NY-OFI (NY AM MF5)** 2026-06-29 11:37:06 ET, LONG 3 lots at 29777.50, safety stop 29687.50 (1.5 x own stop 60 pts). Result managed +57 pts/lot (+0.94 R, $+3396) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +1.13 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:59:08  price 29834.20 (open +0.95 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:08  price 29834.20 (open +0.95 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29834.17

## NY AM: 50 RANDOM trades (seed 11)

**NY-OFI (NY AM MF5)** 2023-09-19 09:59:52 ET, SHORT 3 lots at 15305.50, safety stop 15395.50 (1.5 x own stop 60 pts). Result managed +16 pts/lot (+0.27 R, $+956) ; own bracket result +14 pts (+0.23 R, $+826). MFE +0.53 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:01:37  price 15291.10 (open +0.24 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:01:37  price 15291.10 (open +0.24 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:01:52  price 15290.20 (open +0.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:07  price 15281.20 (open +0.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:22  price 15279.40 (open +0.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:02:52  price 15277.60 (open +0.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:03:37  price 15277.60 (open +0.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:04:07  price 15275.80 (open +0.49 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:04:37  price 15274.90 (open +0.51 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 15289.50

**NY-OFI (NY AM MF5)** 2023-09-21 10:01:56 ET, SHORT 3 lots at 14921.75, safety stop 15011.75 (1.5 x own stop 60 pts). Result managed -89 pts/lot (-1.48 R, $-5334) ; own bracket result -60 pts (-0.99 R, $-3574). MFE +0.03 R, MAE -1.57 R, 38 min under water (longest 37 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 15010.58

**NY-NODE (NY AM MF4)** 2023-10-09 11:58:59 ET, LONG 6 lots at 15040.88, safety stop 14905.88 (1.5 x own stop 90 pts). Result managed +8 pts/lot (+0.09 R, $+993) ; own bracket: not taken (slot effect). MFE +0.11 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:59:59  price 15050.33 (open +0.11 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:59  price 15050.33 (open +0.11 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 15049.21

**NY-OFI (NY AM MF5)** 2023-10-10 09:43:21 ET, LONG 3 lots at 15223.50, safety stop 15133.50 (1.5 x own stop 60 pts). Result managed +0 pts/lot (+0.01 R, $+26) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +0.10 R, MAE -0.45 R, 11 min under water (longest 8 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  09:55:36  price 15226.20 (open +0.04 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  09:55:36  price 15226.20 (open +0.04 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 15224.00

**NY-FIB (NY AM MF1)** 2023-10-13 09:38:11 ET, SHORT 6 lots at 15316.25, safety stop 15496.25 (1.5 x own stop 120 pts). Result managed -1 pts/lot (-0.01 R, $-112) ; own bracket result +108 pts (+0.90 R, $+12953). MFE +0.04 R, MAE -0.32 R, 7 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:45:26  price 15316.25 (open -0.00 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  09:45:26  price 15316.25 (open -0.00 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 15317.12

**NY-FIB (NY AM MF1)** 2023-10-16 09:46:14 ET, SHORT 6 lots at 15206.12, safety stop 15386.12 (1.5 x own stop 120 pts). Result managed +4 pts/lot (+0.03 R, $+483) ; own bracket result -65 pts (-0.54 R, $-7787). MFE +0.07 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:47:14  price 15202.52 (open +0.03 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  09:47:14  price 15202.52 (open +0.03 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 15202.04

**NY-VALUE (NY AM MF2)** 2023-10-16 10:55:34 ET, LONG 6 lots at 15295.38, safety stop 15205.38 (1.5 x own stop 60 pts). Result managed +17 pts/lot (+0.28 R, $+2033) ; own bracket: not taken (slot effect). MFE +0.43 R, MAE -0.07 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 4m:N 5m:W
  11:00:04  price 15316.98 (open +0.36 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:00:04  price 15316.98 (open +0.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:00:19  price 15316.98 (open +0.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:00:34  price 15317.88 (open +0.38 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  exit: Stop at 15312.38

**NY-FIB (NY AM MF1)** 2023-10-19 09:42:56 ET, SHORT 6 lots at 15038.58, safety stop 15218.58 (1.5 x own stop 120 pts). Result managed -2 pts/lot (-0.02 R, $-257) ; own bracket result -0 pts (-0.00 R, $-37). MFE +0.08 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:43:56  price 15040.38 (open -0.01 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  09:43:56  price 15040.38 (open -0.01 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 15040.67

**NY-NODE (NY AM MF4)** 2023-11-16 09:30:42 ET, SHORT 6 lots at 15837.88, safety stop 15972.88 (1.5 x own stop 90 pts). Result managed +0 pts/lot (+0.00 R, $-2) ; own bracket result +30 pts (+0.33 R, $+3578). MFE +0.16 R, MAE -0.16 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 3m:W
  09:33:27  price 15828.42 (open +0.11 R of the book stop): state change PROBE>DEFENDING [P3: other markets turn against the winner: tighten and take a part]
  09:33:27  price 15828.42 (open +0.11 R of the book stop): took a part [P3: other markets turn against the winner: tighten and take a part]
  09:33:42  price 15840.58 (open -0.03 R of the book stop): state change DEFENDING>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:33:42  price 15840.58 (open -0.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 15837.83

**NY-NODE (NY AM MF4)** 2023-11-24 10:53:17 ET, SHORT 6 lots at 15990.71, safety stop 16125.71 (1.5 x own stop 90 pts). Result managed -28 pts/lot (-0.31 R, $-3377) ; own bracket: not taken (slot effect). MFE +0.02 R, MAE -0.39 R, 66 min under water (longest 63 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:51:23  price 16017.71 (open -0.30 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:51:23  price 16017.71 (open -0.30 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: UWTime at 16018.79

**NY-NODE (NY AM MF4)** 2023-11-29 11:11:06 ET, SHORT 6 lots at 16080.46, safety stop 16215.46 (1.5 x own stop 90 pts). Result managed +7 pts/lot (+0.08 R, $+888) ; own bracket result +30 pts (+0.33 R, $+3588). MFE +0.20 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:13:51  price 16065.61 (open +0.17 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:13:51  price 16065.61 (open +0.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 16073.00

**NY-FIB (NY AM MF1)** 2023-12-05 10:03:07 ET, LONG 6 lots at 15907.58, safety stop 15727.58 (1.5 x own stop 120 pts). Result managed -0 pts/lot (-0.00 R, $-17) ; own bracket result -39 pts (-0.33 R, $-4707). MFE +0.17 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:04:07  price 15921.98 (open +0.12 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  10:04:07  price 15921.98 (open +0.12 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 15907.50

**NY-VALUE (NY AM MF2)** 2024-04-08 10:12:40 ET, SHORT 6 lots at 18297.88, safety stop 18387.88 (1.5 x own stop 60 pts). Result managed +0 pts/lot (+0.00 R, $+8) ; own bracket: not taken (slot effect). MFE +0.09 R, MAE -1.33 R, 84 min under water (longest 76 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  11:37:31  price 18296.08 (open +0.03 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  11:37:31  price 18296.08 (open +0.03 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 18297.75

**NY-OFI (NY AM MF5)** 2024-04-08 11:32:53 ET, LONG 3 lots at 18328.58, safety stop 18238.58 (1.5 x own stop 60 pts). Result managed -30 pts/lot (-0.49 R, $-1779) ; own bracket: not taken (slot effect). MFE +0.07 R, MAE -0.85 R, 27 min under water (longest 27 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  (no manager action: the safety stop / session end ended it)
  exit: UWTime at 18299.00

**NY-OFI (NY AM MF5)** 2024-04-22 11:59:33 ET, LONG 3 lots at 17252.33, safety stop 17162.33 (1.5 x own stop 60 pts). Result managed +2 pts/lot (+0.03 R, $+96) ; own bracket result +2 pts (+0.03 R, $+96). MFE +0.05 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 
  (no manager action: the safety stop / session end ended it)
  exit: UWTime at 17254.00

**NY-VALUE (NY AM MF2)** 2024-06-07 11:23:19 ET, LONG 6 lots at 19051.38, safety stop 18961.38 (1.5 x own stop 60 pts). Result managed +18 pts/lot (+0.31 R, $+2193) ; own bracket: not taken (slot effect). MFE +0.60 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 3m:N 7m:W
  11:24:19  price 19056.78 (open +0.09 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  11:24:19  price 19056.78 (open +0.09 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  11:30:20  price 19071.17 (open +0.33 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:30:35  price 19079.28 (open +0.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:31:05  price 19084.67 (open +0.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 19069.71

**NY-VALUE (NY AM MF2)** 2024-06-25 09:42:02 ET, LONG 6 lots at 19827.00, safety stop 19737.00 (1.5 x own stop 60 pts). Result managed -0 pts/lot (-0.00 R, $-17) ; own bracket: not taken (slot effect). MFE +0.15 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:43:02  price 19830.60 (open +0.06 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  09:43:02  price 19830.60 (open +0.06 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 19826.92

**NY-NODE (NY AM MF4)** 2024-06-26 09:53:40 ET, LONG 6 lots at 19989.88, safety stop 19854.88 (1.5 x own stop 90 pts). Result managed +14 pts/lot (+0.15 R, $+1638) ; own bracket result +30 pts (+0.33 R, $+3608). MFE +0.31 R, MAE -0.37 R, 10 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 13m:W
  10:06:41  price 20003.38 (open +0.15 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  10:06:41  price 20003.38 (open +0.15 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:06:56  price 20003.38 (open +0.15 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:08:11  price 20007.42 (open +0.20 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:08:26  price 20012.83 (open +0.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:09:11  price 20014.17 (open +0.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 20003.58

**NY-OFI (NY AM MF5)** 2024-08-01 09:51:15 ET, LONG 3 lots at 19627.00, safety stop 19537.00 (1.5 x own stop 60 pts). Result managed +24 pts/lot (+0.41 R, $+1461) ; own bracket: not taken (slot effect). MFE +0.89 R, MAE -0.50 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:56:15  price 19648.60 (open +0.36 R of the book stop): state change PROBE>DEFENDING [P3: other markets turn against the winner: tighten and take a part]
  09:56:15  price 19648.60 (open +0.36 R of the book stop): took a part [P3: other markets turn against the winner: tighten and take a part]
  09:56:30  price 19654.90 (open +0.46 R of the book stop): state change DEFENDING>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:56:30  price 19654.90 (open +0.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:56:45  price 19664.80 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:57:15  price 19675.60 (open +0.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:57:30  price 19675.60 (open +0.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 19651.42

**NY-FIB (NY AM MF1)** 2024-08-02 09:50:21 ET, LONG 6 lots at 18652.88, safety stop 18472.88 (1.5 x own stop 120 pts). Result managed -179 pts/lot (-1.49 R, $-21532) ; own bracket: not taken (slot effect). MFE +0.10 R, MAE -1.51 R, 16 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18473.50

**NY-OFI (NY AM MF5)** 2024-08-07 10:16:04 ET, LONG 3 lots at 18536.08, safety stop 18446.08 (1.5 x own stop 60 pts). Result managed -89 pts/lot (-1.49 R, $-5369) ; own bracket result -58 pts (-0.97 R, $-3509). MFE +0.01 R, MAE -1.55 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18446.67

**NY-OFI (NY AM MF5)** 2024-08-21 09:46:30 ET, LONG 3 lots at 19866.33, safety stop 19776.33 (1.5 x own stop 60 pts). Result managed +1 pts/lot (+0.02 R, $+71) ; own bracket: not taken (slot effect). MFE +0.10 R, MAE -0.37 R, 8 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  09:55:15  price 19870.83 (open +0.08 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  09:55:15  price 19870.83 (open +0.08 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 19867.58

**NY-OFI (NY AM MF5)** 2024-12-02 09:36:30 ET, LONG 3 lots at 21133.33, safety stop 21043.33 (1.5 x own stop 60 pts). Result managed +13 pts/lot (+0.21 R, $+756) ; own bracket: not taken (slot effect). MFE +0.50 R, MAE -0.54 R, 8 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 7m:A 12m:N 14m:W
  09:50:00  price 21148.63 (open +0.26 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:50:00  price 21148.63 (open +0.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:50:15  price 21156.73 (open +0.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 21146.00

**NY-NODE (NY AM MF4)** 2024-12-16 09:31:31 ET, LONG 6 lots at 21928.42, safety stop 21793.42 (1.5 x own stop 90 pts). Result managed +10 pts/lot (+0.11 R, $+1213) ; own bracket result +30 pts (+0.33 R, $+3603). MFE +0.32 R, MAE -0.27 R, 7 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 3m:N
  09:41:01  price 21950.02 (open +0.24 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:41:01  price 21950.02 (open +0.24 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 21938.58

**NY-FIB (NY AM MF1)** 2024-12-19 09:56:46 ET, LONG 6 lots at 21581.62, safety stop 21401.62 (1.5 x own stop 120 pts). Result managed +28 pts/lot (+0.24 R, $+3383) ; own bracket: not taken (slot effect). MFE +0.50 R, MAE -0.53 R, 11 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 10m:N 17m:W
  10:13:16  price 21621.22 (open +0.33 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:13:16  price 21621.22 (open +0.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:14:01  price 21633.83 (open +0.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 21609.88

**NY-OFI (NY AM MF5)** 2024-12-24 10:20:57 ET, SHORT 3 lots at 21901.58, safety stop 21991.58 (1.5 x own stop 60 pts). Result managed -81 pts/lot (-1.34 R, $-4844) ; own bracket result -58 pts (-0.96 R, $-3464). MFE +0.04 R, MAE -1.42 R, 57 min under water (longest 57 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:18:14  price 21981.68 (open -1.33 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:18:14  price 21981.68 (open -1.33 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: ExAlgoStop_L3 at 21982.25

**NY-NODE (NY AM MF4)** 2025-04-11 10:02:15 ET, SHORT 6 lots at 18472.33, safety stop 18607.33 (1.5 x own stop 90 pts). Result managed -135 pts/lot (-1.50 R, $-16157) ; own bracket result +30 pts (+0.33 R, $+3603). MFE +0.40 R, MAE -1.64 R, 5 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 5m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18606.92

**NY-FIB (NY AM MF1)** 2025-04-17 11:48:14 ET, SHORT 6 lots at 18377.58, safety stop 18557.58 (1.5 x own stop 120 pts). Result managed +20 pts/lot (+0.17 R, $+2453) ; own bracket: not taken (slot effect). MFE +0.21 R, MAE -0.05 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:49:14  price 18355.98 (open +0.18 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:49:14  price 18355.98 (open +0.18 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 18357.08

**NY-FIB (NY AM MF1)** 2025-04-21 10:10:31 ET, SHORT 6 lots at 17967.58, safety stop 18147.58 (1.5 x own stop 120 pts). Result managed +1 pts/lot (+0.01 R, $+98) ; own bracket result +120 pts (+1.00 R, $+14403). MFE +0.11 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:11:31  price 17960.38 (open +0.06 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  10:11:31  price 17960.38 (open +0.06 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 17966.71

**NY-VALUE (NY AM MF2)** 2025-04-29 11:37:08 ET, LONG 6 lots at 19538.17, safety stop 19448.17 (1.5 x own stop 60 pts). Result managed +19 pts/lot (+0.31 R, $+2243) ; own bracket result +0 pts (+0.01 R, $+43). MFE +0.69 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 5m:W
  11:42:39  price 19570.57 (open +0.54 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  11:42:39  price 19570.57 (open +0.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:43:09  price 19575.97 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 19556.92

**NY-OFI (NY AM MF5)** 2026-05-01 10:36:04 ET, SHORT 3 lots at 27791.50, safety stop 27881.50 (1.5 x own stop 60 pts). Result managed +14 pts/lot (+0.24 R, $+851) ; own bracket result -60 pts (-0.99 R, $-3579). MFE +0.45 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:37:49  price 27768.10 (open +0.39 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:37:49  price 27768.10 (open +0.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 27777.25

**NY-OFI (NY AM MF5)** 2026-05-18 09:43:16 ET, SHORT 3 lots at 29203.83, safety stop 29293.83 (1.5 x own stop 60 pts). Result managed +34 pts/lot (+0.56 R, $+2016) ; own bracket result +60 pts (+1.00 R, $+3601). MFE +1.01 R, MAE -0.88 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:44:46  price 29166.93 (open +0.61 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  09:44:46  price 29166.93 (open +0.61 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  09:45:01  price 29164.23 (open +0.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:45:16  price 29144.43 (open +0.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29170.17

**NY-FIB (NY AM MF1)** 2026-06-01 09:31:58 ET, LONG 6 lots at 30359.75, safety stop 30179.75 (1.5 x own stop 120 pts). Result managed +30 pts/lot (+0.25 R, $+3628) ; own bracket result +120 pts (+1.00 R, $+14393). MFE +0.55 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:32:58  price 30397.55 (open +0.32 R of the book stop): state change PROBE>DEFENDING [P3: other markets turn against the winner: tighten and take a part]
  09:32:58  price 30397.55 (open +0.32 R of the book stop): took a part [P3: other markets turn against the winner: tighten and take a part]
  09:33:13  price 30397.55 (open +0.32 R of the book stop): state change DEFENDING>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:33:13  price 30397.55 (open +0.32 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30390.04

**NY-NODE (NY AM MF4)** 2026-06-01 10:31:32 ET, LONG 6 lots at 30395.21, safety stop 30260.21 (1.5 x own stop 90 pts). Result managed +32 pts/lot (+0.35 R, $+3783) ; own bracket: not taken (slot effect). MFE +0.42 R, MAE -0.05 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:42:17  price 30427.61 (open +0.36 R of the book stop): state change PROBE>OUT [S1: travelled most of the way and progress stopped: take it]
  10:42:17  price 30427.61 (open +0.36 R of the book stop): closed everything [S1: travelled most of the way and progress stopped: take it]
  exit: ExAlgoAll_S1 at 30426.79

**NY-NODE (NY AM MF4)** 2026-06-16 09:40:26 ET, SHORT 6 lots at 30494.17, safety stop 30629.17 (1.5 x own stop 90 pts). Result managed +33 pts/lot (+0.37 R, $+3978) ; own bracket: not taken (slot effect). MFE +0.85 R, MAE -0.99 R, 36 min under water (longest 23 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:55:18  price 30572.47 (open -0.87 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  09:55:18  price 30572.47 (open -0.87 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  10:19:21  price 30460.42 (open +0.38 R of the book stop): state change DEFENDING>RUNNING [P5: a liquidity level just ahead: take it there]
  10:19:21  price 30460.42 (open +0.38 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:19:36  price 30446.92 (open +0.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:19:51  price 30426.67 (open +0.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:20:36  price 30418.57 (open +0.84 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30460.96

**NY-NODE (NY AM MF4)** 2026-06-22 11:43:11 ET, LONG 6 lots at 30651.83, safety stop 30516.83 (1.5 x own stop 90 pts). Result managed -91 pts/lot (-1.01 R, $-10942) ; own bracket: not taken (slot effect). MFE +0.23 R, MAE -1.24 R, 11 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:W 6m:A
  11:56:28  price 30582.98 (open -0.77 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:56:28  price 30582.98 (open -0.77 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 30560.71

**NY-OFI (NY AM MF5)** 2026-06-29 11:37:06 ET, LONG 3 lots at 29777.50, safety stop 29687.50 (1.5 x own stop 60 pts). Result managed +57 pts/lot (+0.94 R, $+3396) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +1.13 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:59:08  price 29834.20 (open +0.95 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:59:08  price 29834.20 (open +0.95 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29834.17

**NY-OFI (NY AM MF5)** 2026-07-07 10:14:18 ET, SHORT 3 lots at 29351.00, safety stop 29441.00 (1.5 x own stop 60 pts). Result managed +20 pts/lot (+0.33 R, $+1176) ; own bracket result +60 pts (+1.00 R, $+3596). MFE +0.75 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:15:33  price 29312.30 (open +0.65 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:15:33  price 29312.30 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29331.33

**NY-FIB (NY AM MF1)** 2026-07-08 09:37:44 ET, SHORT 6 lots at 29295.79, safety stop 29475.79 (1.5 x own stop 120 pts). Result managed +34 pts/lot (+0.28 R, $+4048) ; own bracket: not taken (slot effect). MFE +0.44 R, MAE -0.83 R, 31 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  10:12:44  price 29254.39 (open +0.35 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  10:12:44  price 29254.39 (open +0.35 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  10:12:59  price 29252.59 (open +0.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29262.00

**NY-OFI (NY AM MF5)** 2026-07-08 11:04:17 ET, SHORT 3 lots at 29182.33, safety stop 29272.33 (1.5 x own stop 60 pts). Result managed +50 pts/lot (+0.84 R, $+3006) ; own bracket result +60 pts (+1.00 R, $+3601). MFE +1.54 R, MAE -0.63 R, 7 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 8m:W 9m:N 10m:W
  11:16:17  price 29128.33 (open +0.90 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  11:16:17  price 29128.33 (open +0.90 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:16:32  price 29117.53 (open +1.08 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:17:17  price 29105.83 (open +1.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  11:17:32  price 29094.13 (open +1.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29132.17

**NY-VALUE (NY AM MF2)** 2026-07-10 09:42:56 ET, LONG 6 lots at 29868.88, safety stop 29778.88 (1.5 x own stop 60 pts). Result managed +46 pts/lot (+0.76 R, $+5488) ; own bracket result +60 pts (+1.00 R, $+7208). MFE +1.65 R, MAE -0.65 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:N 4m:W
  09:46:41  price 29907.58 (open +0.65 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  09:46:41  price 29907.58 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:46:56  price 29913.88 (open +0.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:49:11  price 29921.08 (open +0.87 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  09:49:26  price 29935.47 (open +1.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  09:49:41  price 29948.97 (open +1.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29914.67

**NY-FIB (NY AM MF1)** 2026-07-16 09:32:30 ET, LONG 6 lots at 29484.75, safety stop 29304.75 (1.5 x own stop 120 pts). Result managed -179 pts/lot (-1.49 R, $-21527) ; own bracket result -119 pts (-0.99 R, $-14332). MFE +0.08 R, MAE -1.56 R, 14 min under water (longest 13 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29305.42

**NY-FIB (NY AM MF1)** 2026-07-28 09:48:11 ET, SHORT 6 lots at 27697.17, safety stop 27877.17 (1.5 x own stop 120 pts). Result managed +43 pts/lot (+0.36 R, $+5198) ; own bracket: not taken (slot effect). MFE +0.77 R, MAE -0.82 R, 16 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  10:14:11  price 27626.97 (open +0.58 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  10:14:11  price 27626.97 (open +0.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:14:26  price 27619.77 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  10:14:41  price 27610.77 (open +0.72 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 27653.79

**NY-OFI (NY AM MF5)** 2026-08-05 11:03:38 ET, SHORT 3 lots at 29839.42, safety stop 29929.42 (1.5 x own stop 60 pts). Result managed +43 pts/lot (+0.72 R, $+2571) ; own bracket result +60 pts (+1.00 R, $+3591). MFE +1.28 R, MAE -0.84 R, 9 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 6m:A
  11:18:38  price 29787.22 (open +0.87 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  11:18:38  price 29787.22 (open +0.87 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:18:53  price 29795.32 (open +0.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29796.50

**NY-NODE (NY AM MF4)** 2026-08-14 09:49:20 ET, LONG 6 lots at 30263.46, safety stop 30128.46 (1.5 x own stop 90 pts). Result managed -90 pts/lot (-1.00 R, $-10797) ; own bracket: not taken (slot effect). MFE +0.10 R, MAE -1.00 R, 28 min under water (longest 13 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:59:50  price 30224.31 (open -0.43 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  09:59:50  price 30224.31 (open -0.43 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 30173.54

**NY-NODE (NY AM MF4)** 2026-09-02 11:51:24 ET, SHORT 6 lots at 29151.33, safety stop 29286.33 (1.5 x own stop 90 pts). Result managed +1 pts/lot (+0.01 R, $+78) ; own bracket: not taken (slot effect). MFE +0.04 R, MAE -0.19 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:53:54  price 29151.33 (open -0.00 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  11:53:54  price 29151.33 (open -0.00 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoStop_S2 at 29150.62

**NY-FIB (NY AM MF1)** 2026-09-17 09:45:04 ET, SHORT 6 lots at 29646.12, safety stop 29826.12 (1.5 x own stop 120 pts). Result managed +6 pts/lot (+0.05 R, $+683) ; own bracket: not taken (slot effect). MFE +0.16 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:46:04  price 29628.12 (open +0.15 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  09:46:04  price 29628.12 (open +0.15 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  09:46:19  price 29637.12 (open +0.08 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 29640.38

**NY-OFI (NY AM MF5)** 2026-09-29 10:25:59 ET, LONG 3 lots at 30683.25, safety stop 30593.25 (1.5 x own stop 60 pts). Result managed -56 pts/lot (-0.94 R, $-3394) ; own bracket: not taken (slot effect). MFE +0.46 R, MAE -0.97 R, 21 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 5m:N 19m:A 32m:N 34m:A
  11:01:29  price 30640.05 (open -0.72 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  11:01:29  price 30640.05 (open -0.72 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 30626.75

**NY-OFI (NY AM MF5)** 2026-09-29 11:08:07 ET, LONG 3 lots at 30612.83, safety stop 30522.83 (1.5 x own stop 60 pts). Result managed +27 pts/lot (+0.45 R, $+1601) ; own bracket result -60 pts (-1.00 R, $-3609). MFE +0.65 R, MAE -0.28 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:N 7m:W
  11:15:22  price 30644.33 (open +0.52 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  11:15:22  price 30644.33 (open +0.52 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  11:15:37  price 30645.23 (open +0.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30639.58

**NY-OFI (NY AM MF5)** 2026-10-29 11:55:18 ET, LONG 3 lots at 29618.92, safety stop 29528.92 (1.5 x own stop 60 pts). Result managed +3 pts/lot (+0.05 R, $+176) ; own bracket result +36 pts (+0.61 R, $+2186). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  11:56:33  price 29626.12 (open +0.12 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  11:56:33  price 29626.12 (open +0.12 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  11:56:48  price 29621.62 (open +0.04 R of the book stop): state change RUNNING>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  11:56:48  price 29621.62 (open +0.04 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29621.92


# PART 2: ASIA

# Asia (AS): managed rows MGMIDL1_A, 2749 trades from 42 finished (set, month) rows, matched to the book's own bracket on 1902 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 275 | +1795480 | 2023 +7980, 2024 +214375, 2025 +233645, 2026 +1339480 |
| winners cut short | 762 | -3332105 | 2023 -237295, 2024 -546820, 2025 -335615, 2026 -2212375 |
| losers cut early | 521 | +3216310 | 2023 +145615, 2024 +515100, 2025 +321580, 2026 +2234015 |
| losers made worse | 260 | -681130 | 2023 -4770, 2024 -61515, 2025 -140040, 2026 -474805 |
| matched pairs (all) | 1902 | -599275 | 2023 -109880, 2024 -64860, 2025 -97510, 2026 -327025 |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 847 trades, net $ -50172; entries that exist only under the own bracket in the same months (blocked by a carried trade): 436 trades, net $ +433238. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## Asia: the 20 WORST give-backs (largest open profit given back, $)

**AS-VWAPBRK (Asia MF3)** 2026-06-07 19:05:33 ET, LONG 6 lots at 28969.38, safety stop 28901.88 (1.5 x own stop 45 pts). Result managed +146 pts/lot (+3.25 R, $+17548) ; own bracket result +45 pts (+1.00 R, $+5408). MFE +7.07 R, MAE -0.69 R, 10 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  19:43:24  price 29005.83 (open +0.81 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  19:43:24  price 29005.83 (open +0.81 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:43:39  price 29013.25 (open +0.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:44:41  price 29021.35 (open +1.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:45:41  price 29044.97 (open +1.68 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:11  price 29046.33 (open +1.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:11  price 29064.55 (open +2.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:41  price 29069.28 (open +2.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:48:26  price 29074.00 (open +2.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:48:42  price 29084.12 (open +2.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:49:12  price 29090.88 (open +2.70 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:57:38  price 29096.28 (open +2.82 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:01:55  price 29101.00 (open +2.92 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:25  price 29102.35 (open +2.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:56  price 29109.78 (open +3.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:11  price 29113.83 (open +3.21 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:26  price 29119.22 (open +3.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:41  price 29123.95 (open +3.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:56  price 29130.70 (open +3.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:04:11  price 29134.08 (open +3.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:09:57  price 29138.12 (open +3.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:12:12  price 29131.38 (open +3.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:16:44  price 29169.85 (open +4.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:17:30  price 29173.90 (open +4.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:18:15  price 29184.70 (open +4.79 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:18:30  price 29184.03 (open +4.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:19:00  price 29192.12 (open +4.95 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:21:15  price 29194.15 (open +5.00 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:24:17  price 29198.88 (open +5.10 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:24:34  price 29200.22 (open +5.13 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:06  price 29206.30 (open +5.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:21  price 29209.67 (open +5.34 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:36  price 29214.40 (open +5.45 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:28:09  price 29217.78 (open +5.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:28:24  price 29225.20 (open +5.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:30:54  price 29230.60 (open +5.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:31:24  price 29238.70 (open +5.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:36:57  price 29243.42 (open +6.09 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:37:12  price 29260.30 (open +6.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:37:42  price 29263.67 (open +6.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29115.67

**AS-NR7 (Asia MF1)** 2026-06-07 19:32:03 ET, LONG 6 lots at 28972.92, safety stop 28912.92 (1.5 x own stop 40 pts). Result managed +147 pts/lot (+3.68 R, $+17678) ; own bracket result +80 pts (+2.00 R, $+9603). MFE +7.84 R, MAE -0.23 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  19:43:39  price 29013.72 (open +1.02 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  19:43:39  price 29013.72 (open +1.02 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:43:54  price 29015.52 (open +1.06 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:44:41  price 29021.52 (open +1.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:45:41  price 29044.92 (open +1.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:11  price 29046.72 (open +1.84 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:11  price 29064.72 (open +2.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:41  price 29068.92 (open +2.40 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:48:26  price 29073.72 (open +2.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:48:42  price 29083.92 (open +2.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:49:12  price 29091.12 (open +2.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:57:38  price 29095.92 (open +3.07 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:01:55  price 29101.32 (open +3.21 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:25  price 29102.52 (open +3.24 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:56  price 29109.72 (open +3.42 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:11  price 29113.92 (open +3.53 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:26  price 29119.32 (open +3.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:41  price 29124.12 (open +3.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:03:56  price 29130.72 (open +3.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:04:11  price 29134.32 (open +4.04 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:09:57  price 29137.92 (open +4.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:12:12  price 29131.32 (open +3.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:16:44  price 29170.32 (open +4.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:17:30  price 29173.92 (open +5.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:18:15  price 29184.72 (open +5.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:18:30  price 29184.12 (open +5.28 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:19:00  price 29191.92 (open +5.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:21:15  price 29194.32 (open +5.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:24:17  price 29199.12 (open +5.66 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:24:34  price 29200.32 (open +5.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:06  price 29206.32 (open +5.83 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:21  price 29209.32 (open +5.91 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:26:36  price 29214.12 (open +6.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:28:09  price 29217.12 (open +6.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:28:24  price 29224.92 (open +6.30 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:30:54  price 29230.32 (open +6.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:31:24  price 29238.12 (open +6.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:36:57  price 29243.52 (open +6.76 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:37:12  price 29259.72 (open +7.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:37:42  price 29263.32 (open +7.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29120.29

**AS-VWAPBRK (Asia MF3)** 2026-07-28 19:34:11 ET, LONG 6 lots at 27900.21, safety stop 27832.71 (1.5 x own stop 45 pts). Result managed +117 pts/lot (+2.61 R, $+14073) ; own bracket result +45 pts (+1.00 R, $+5398). MFE +6.12 R, MAE -0.29 R, 6 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:N 8m:W
  19:44:02  price 27935.98 (open +0.80 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  19:44:02  price 27935.98 (open +0.80 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:44:17  price 27936.66 (open +0.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:44:32  price 27990.66 (open +2.01 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:45:02  price 28007.53 (open +2.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:32  price 28016.31 (open +2.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:47  price 28019.01 (open +2.64 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:17  price 28035.88 (open +3.01 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:47  price 28045.33 (open +3.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:49:47  price 28052.76 (open +3.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:50:32  price 28091.91 (open +4.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:59:37  price 28095.96 (open +4.35 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:00:07  price 28102.71 (open +4.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:01:38  price 28133.08 (open +5.18 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:08  price 28146.58 (open +5.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:06:42  price 28154.01 (open +5.64 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:30  price 28164.13 (open +5.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:45  price 28164.13 (open +5.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 28017.54

**AS-VWAPBRK (Asia MF3)** 2025-04-06 18:00:03 ET, SHORT 6 lots at 17119.88, safety stop 17187.38 (1.5 x own stop 45 pts). Result managed +352 pts/lot (+7.81 R, $+42178) ; own bracket result +45 pts (+1.00 R, $+5378). MFE +11.18 R, MAE -1.93 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  18:10:08  price 16739.17 (open +8.46 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  18:10:08  price 16739.17 (open +8.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:11:08  price 16803.30 (open +7.04 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  18:14:08  price 16710.83 (open +9.09 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:19:10  price 16625.10 (open +11.00 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:51:50  price 16610.92 (open +11.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:07:20  price 16599.45 (open +11.56 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:08:36  price 16577.17 (open +12.06 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:08:51  price 16530.60 (open +13.10 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:10:21  price 16469.17 (open +14.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:10:08  price 16611.60 (open +11.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:11:38  price 16613.62 (open +11.25 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:12:38  price 16592.70 (open +11.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:13:08  price 16589.33 (open +11.79 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:13:23  price 16582.58 (open +11.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:29:16  price 16718.92 (open +8.91 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 16768.33

**AS-RSI (Asia MF2)** 2025-04-13 18:01:41 ET, LONG 6 lots at 19054.50, safety stop 18964.50 (1.5 x own stop 60 pts). Result managed -93 pts/lot (-1.55 R, $-11187) ; own bracket result -53 pts (-0.88 R, $-6377). MFE +0.90 R, MAE -1.60 R, 16 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18961.33

**AS-VWAPBRK (Asia MF3)** 2026-09-13 18:00:08 ET, SHORT 6 lots at 29044.25, safety stop 29111.75 (1.5 x own stop 45 pts). Result managed -46 pts/lot (-1.01 R, $-5482) ; own bracket result -48 pts (-1.06 R, $-5722). MFE +2.22 R, MAE -0.67 R, 5 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:32:36  price 29085.42 (open -0.92 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  18:32:36  price 29085.42 (open -0.92 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 29089.88

**AS-RSI (Asia MF2)** 2025-04-06 20:05:41 ET, SHORT 6 lots at 16622.54, safety stop 16712.54 (1.5 x own stop 60 pts). Result managed -91 pts/lot (-1.51 R, $-10882) ; own bracket result -62 pts (-1.04 R, $-7482). MFE +0.91 R, MAE -1.45 R, 16 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 16713.17

**AS-VWAPBRK (Asia MF3)** 2026-07-19 18:03:21 ET, SHORT 6 lots at 28780.38, safety stop 28847.88 (1.5 x own stop 45 pts). Result managed -64 pts/lot (-1.43 R, $-7712) ; own bracket result +45 pts (+1.00 R, $+5378). MFE +1.62 R, MAE -1.45 R, 17 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 31m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 28844.58

**AS-NR7 (Asia MF1)** 2025-04-06 19:36:03 ET, LONG 6 lots at 16721.88, safety stop 16661.88 (1.5 x own stop 40 pts). Result managed -61 pts/lot (-1.52 R, $-7312) ; own bracket result -36 pts (-0.91 R, $-4362). MFE +1.75 R, MAE -1.65 R, 10 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 16661.00

**AS-VWAPBRK (Asia MF3)** 2026-06-10 20:56:19 ET, LONG 6 lots at 28544.04, safety stop 28476.54 (1.5 x own stop 45 pts). Result managed +92 pts/lot (+2.06 R, $+11093) ; own bracket result +45 pts (+1.00 R, $+5388). MFE +4.94 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  21:02:59  price 28596.69 (open +1.17 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  21:02:59  price 28596.69 (open +1.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:03:14  price 28602.77 (open +1.30 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:04:16  price 28596.02 (open +1.16 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  21:04:31  price 28616.27 (open +1.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:04:46  price 28618.97 (open +1.67 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:05:31  price 28635.17 (open +2.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:09:21  price 28642.59 (open +2.19 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:09:36  price 28647.99 (open +2.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:10:21  price 28658.79 (open +2.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:11:07  price 28666.22 (open +2.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:11:38  price 28678.37 (open +2.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:12:08  price 28693.22 (open +3.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:12:53  price 28697.27 (open +3.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:13:54  price 28700.64 (open +3.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:14:09  price 28713.47 (open +3.76 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:14:54  price 28714.82 (open +3.79 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:15:24  price 28718.19 (open +3.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:19:42  price 28720.89 (open +3.93 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:19:57  price 28722.92 (open +3.97 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:20:12  price 28729.67 (open +4.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:24:46  price 28747.22 (open +4.51 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:28:04  price 28750.59 (open +4.59 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:28:19  price 28756.67 (open +4.72 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:30:10  price 28753.97 (open +4.67 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 28636.54

**AS-RSI (Asia MF2)** 2025-04-08 23:59:34 ET, SHORT 6 lots at 16914.42, safety stop 17004.42 (1.5 x own stop 60 pts). Result managed -89 pts/lot (-1.48 R, $-10642) ; own bracket result -56 pts (-0.93 R, $-6707). MFE +0.60 R, MAE -1.44 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 17003.04

**AS-NR7 (Asia MF1)** 2025-04-06 21:56:03 ET, LONG 6 lots at 16967.33, safety stop 16907.33 (1.5 x own stop 40 pts). Result managed -62 pts/lot (-1.54 R, $-7397) ; own bracket result -33 pts (-0.83 R, $-3992). MFE +1.51 R, MAE -1.50 R, 7 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 16905.75

**AS-NR7 (Asia MF1)** 2026-07-28 19:44:03 ET, LONG 6 lots at 27937.17, safety stop 27877.17 (1.5 x own stop 40 pts). Result managed +122 pts/lot (+3.05 R, $+14623) ; own bracket: not taken (slot effect). MFE +5.99 R, MAE -0.12 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  19:45:03  price 28006.77 (open +1.74 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  19:45:03  price 28006.77 (open +1.74 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:33  price 28018.77 (open +2.04 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:47:03  price 28019.97 (open +2.07 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:18  price 28034.37 (open +2.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:48  price 28046.37 (open +2.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:49:48  price 28055.37 (open +2.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:50:03  price 28069.77 (open +3.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:50:18  price 28075.17 (open +3.45 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:50:33  price 28087.17 (open +3.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:59:37  price 28096.17 (open +3.97 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:00:07  price 28102.77 (open +4.14 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:01:38  price 28132.77 (open +4.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:08  price 28146.57 (open +5.24 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:06:42  price 28154.37 (open +5.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:30  price 28163.97 (open +5.67 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:45  price 28164.57 (open +5.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 28059.08

**AS-NR7 (Asia MF1)** 2024-08-01 22:12:03 ET, SHORT 6 lots at 18877.00, safety stop 18937.00 (1.5 x own stop 40 pts). Result managed +75 pts/lot (+1.88 R, $+9008) ; own bracket: not taken (slot effect). MFE +4.81 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  22:17:00  price 18863.20 (open +0.35 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  22:17:00  price 18863.20 (open +0.35 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  22:17:17  price 18866.20 (open +0.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:17:48  price 18857.80 (open +0.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:18:03  price 18853.60 (open +0.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:18:33  price 18845.20 (open +0.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:18:48  price 18842.80 (open +0.85 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:19:03  price 18826.60 (open +1.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:19:18  price 18815.80 (open +1.53 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:19:48  price 18808.60 (open +1.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:08  price 18776.80 (open +2.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:23  price 18755.80 (open +3.03 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:38  price 18707.80 (open +4.23 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 18801.88

**AS-RSI (Asia MF2)** 2025-04-06 19:55:26 ET, SHORT 6 lots at 16680.92, safety stop 16770.92 (1.5 x own stop 60 pts). Result managed +64 pts/lot (+1.07 R, $+7663) ; own bracket result -62 pts (-1.03 R, $-7427). MFE +3.01 R, MAE -1.41 R, 6 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  20:04:58  price 16525.22 (open +2.59 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  20:04:58  price 16525.22 (open +2.59 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 16617.00

**AS-NR7 (Asia MF1)** 2025-04-02 18:20:03 ET, SHORT 6 lots at 18874.96, safety stop 18934.96 (1.5 x own stop 40 pts). Result managed -58 pts/lot (-1.46 R, $-7002) ; own bracket result -40 pts (-0.99 R, $-4782). MFE +1.41 R, MAE -1.59 R, 5 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18933.25

**AS-NR7 (Asia MF1)** 2026-06-14 18:36:03 ET, SHORT 6 lots at 30039.46, safety stop 30099.46 (1.5 x own stop 40 pts). Result managed -60 pts/lot (-1.51 R, $-7232) ; own bracket result -40 pts (-1.00 R, $-4817). MFE +1.34 R, MAE -1.46 R, 43 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A 4m:W 15m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 30099.67

**AS-NR7 (Asia MF1)** 2025-04-02 19:20:03 ET, SHORT 6 lots at 18888.29, safety stop 18948.29 (1.5 x own stop 40 pts). Result managed -59 pts/lot (-1.49 R, $-7142) ; own bracket result -40 pts (-0.99 R, $-4772). MFE +1.23 R, MAE -1.43 R, 22 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 45m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 18947.75

**AS-VWAPBRK (Asia MF3)** 2026-06-23 18:03:06 ET, SHORT 6 lots at 29763.79, safety stop 29831.29 (1.5 x own stop 45 pts). Result managed +72 pts/lot (+1.61 R, $+8693) ; own bracket result +45 pts (+1.00 R, $+5398). MFE +3.99 R, MAE -0.86 R, 15 min under water (longest 13 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 9m:A
  18:22:16  price 29742.19 (open +0.48 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  18:22:16  price 29742.19 (open +0.48 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  18:22:31  price 29735.44 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:23:01  price 29734.77 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:23:47  price 29723.97 (open +0.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:24:02  price 29719.24 (open +0.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:25:03  price 29711.82 (open +1.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:25:18  price 29705.74 (open +1.29 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:26:50  price 29701.69 (open +1.38 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:33:50  price 29694.27 (open +1.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:34:20  price 29680.09 (open +1.86 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:34:35  price 29674.69 (open +1.98 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:34:50  price 29670.64 (open +2.07 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:35:05  price 29675.37 (open +1.97 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:05:19  price 29602.47 (open +3.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:05:34  price 29595.04 (open +3.75 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:06:20  price 29588.29 (open +3.90 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29691.29

**AS-VWAPBRK (Asia MF3)** 2026-06-28 21:20:53 ET, SHORT 6 lots at 29459.42, safety stop 29526.92 (1.5 x own stop 45 pts). Result managed -67 pts/lot (-1.49 R, $-8047) ; own bracket result -45 pts (-1.01 R, $-5452). MFE +0.87 R, MAE -1.52 R, 15 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29526.42

## Asia: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**AS-VWAPBRK (Asia MF3)** 2026-06-14 18:00:03 ET, LONG 6 lots at 29893.38, safety stop 29825.88 (1.5 x own stop 45 pts). Result managed +240 pts/lot (+5.33 R, $+28763) ; own bracket result +45 pts (+1.00 R, $+5408). MFE +5.10 R, MAE -1.82 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  18:20:09  price 30072.92 (open +3.99 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  18:20:09  price 30072.92 (open +3.99 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  18:20:26  price 30063.47 (open +3.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:22:21  price 30091.15 (open +4.40 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:09:46  price 30125.58 (open +5.16 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:10:01  price 30121.53 (open +5.07 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:10:16  price 30139.08 (open +5.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:11:22  price 30139.75 (open +5.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:11:38  price 30144.47 (open +5.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:13:12  price 30153.25 (open +5.78 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:13:33  price 30155.28 (open +5.82 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:14:06  price 30157.97 (open +5.88 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:20:54  price 30162.70 (open +5.99 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:21:09  price 30168.78 (open +6.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:25:14  price 30170.12 (open +6.15 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:13:01  price 30166.75 (open +6.07 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:13:16  price 30168.10 (open +6.11 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:28:26  price 30170.80 (open +6.17 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:34:44  price 30171.47 (open +6.18 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:37:09  price 30172.83 (open +6.21 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:37:24  price 30178.22 (open +6.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:37:39  price 30177.55 (open +6.31 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:43:16  price 30183.62 (open +6.45 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:43:31  price 30182.95 (open +6.44 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:52:51  price 30184.97 (open +6.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:10:00  price 30179.58 (open +6.36 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:10:30  price 30182.28 (open +6.42 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:11:31  price 30184.97 (open +6.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:11:46  price 30184.30 (open +6.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:12:16  price 30188.35 (open +6.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:12:31  price 30187.00 (open +6.52 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:20:34  price 30189.03 (open +6.57 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:21:30  price 30188.35 (open +6.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:24:07  price 30193.75 (open +6.68 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:24:44  price 30194.42 (open +6.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:26:49  price 30199.83 (open +6.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:27:07  price 30203.20 (open +6.88 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:29:19  price 30206.58 (open +6.96 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:30:07  price 30209.28 (open +7.02 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:30:23  price 30210.62 (open +7.05 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30133.12

## Asia: 50 RANDOM trades (seed 11)

**AS-VWAPBRK (Asia MF3)** 2023-09-07 21:18:44 ET, SHORT 6 lots at 15260.88, safety stop 15328.38 (1.5 x own stop 45 pts). Result managed -0 pts/lot (-0.01 R, $-47) ; own bracket: not taken (slot effect). MFE +0.08 R, MAE -0.07 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W
  21:20:20  price 15260.20 (open +0.01 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  21:20:20  price 15260.20 (open +0.01 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 15261.21

**AS-VWAPBRK (Asia MF3)** 2023-09-10 18:08:59 ET, LONG 6 lots at 15307.33, safety stop 15239.83 (1.5 x own stop 45 pts). Result managed -0 pts/lot (-0.01 R, $-37) ; own bracket result +45 pts (+1.00 R, $+5383). MFE +0.14 R, MAE -0.09 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:N 6m:W 7m:N 14m:W
  18:22:23  price 15308.01 (open +0.01 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  18:22:23  price 15308.01 (open +0.01 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 15307.08

**AS-VWAPBRK (Asia MF3)** 2023-09-17 18:20:35 ET, LONG 6 lots at 15396.58, safety stop 15329.08 (1.5 x own stop 45 pts). Result managed +6 pts/lot (+0.14 R, $+753) ; own bracket result +12 pts (+0.26 R, $+1423). MFE +0.23 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:30:25  price 15402.66 (open +0.14 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  18:30:25  price 15402.66 (open +0.14 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:30:59  price 15403.33 (open +0.15 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:31:35  price 15404.68 (open +0.18 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:32:11  price 15404.01 (open +0.17 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  18:33:00  price 15405.36 (open +0.20 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  18:37:00  price 15406.71 (open +0.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 15402.92

**AS-RSI (Asia MF2)** 2023-09-21 20:31:39 ET, SHORT 6 lots at 14842.54, safety stop 14932.54 (1.5 x own stop 60 pts). Result managed -0 pts/lot (-0.00 R, $-22) ; own bracket result -59 pts (-0.99 R, $-7132). MFE +0.10 R, MAE -0.11 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:-
  20:35:54  price 14841.64 (open +0.01 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  20:35:54  price 14841.64 (open +0.01 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 14842.67

**AS-VWAPBRK (Asia MF3)** 2023-10-16 20:02:16 ET, SHORT 6 lots at 15285.33, safety stop 15352.83 (1.5 x own stop 45 pts). Result managed -1 pts/lot (-0.02 R, $-137) ; own bracket result +6 pts (+0.14 R, $+768). MFE +0.03 R, MAE -0.19 R, 20 min under water (longest 20 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  20:22:16  price 15286.01 (open -0.01 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  20:22:16  price 15286.01 (open -0.01 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 15286.42

**AS-VWAPBRK (Asia MF3)** 2023-10-23 18:14:24 ET, LONG 6 lots at 14744.12, safety stop 14676.62 (1.5 x own stop 45 pts). Result managed +4 pts/lot (+0.08 R, $+428) ; own bracket result +38 pts (+0.84 R, $+4508). MFE +0.18 R, MAE -0.09 R, 19 min under water (longest 9 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 11m:A 13m:N
  19:10:08  price 14749.52 (open +0.12 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  19:10:08  price 14749.52 (open +0.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:12:43  price 14748.17 (open +0.09 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:13:40  price 14749.52 (open +0.12 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:16:10  price 14750.20 (open +0.14 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 14747.75

**AS-NR7 (Asia MF1)** 2023-10-30 22:40:10 ET, SHORT 6 lots at 14372.88, safety stop 14432.88 (1.5 x own stop 40 pts). Result managed -0 pts/lot (-0.01 R, $-57) ; own bracket result +36 pts (+0.90 R, $+4328). MFE +0.02 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  22:41:10  price 14372.88 (open +0.00 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  22:41:10  price 14372.88 (open +0.00 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 14373.29

**AS-NR7 (Asia MF1)** 2023-11-02 18:12:05 ET, SHORT 6 lots at 14935.08, safety stop 14995.08 (1.5 x own stop 40 pts). Result managed -31 pts/lot (-0.78 R, $-3737) ; own bracket result -31 pts (-0.78 R, $-3737). MFE +0.03 R, MAE -0.79 R, 468 min under water (longest 466 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: UWTime at 14966.17

**AS-NR7 (Asia MF1)** 2023-12-10 18:56:03 ET, LONG 6 lots at 16104.54, safety stop 16044.54 (1.5 x own stop 40 pts). Result managed -0 pts/lot (-0.01 R, $-62) ; own bracket result -40 pts (-1.00 R, $-4812). MFE +0.06 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:57:03  price 16105.74 (open +0.03 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  18:57:03  price 16105.74 (open +0.03 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 16104.08

**AS-NR7 (Asia MF1)** 2023-12-13 21:00:03 ET, LONG 6 lots at 16878.54, safety stop 16818.54 (1.5 x own stop 40 pts). Result managed +1 pts/lot (+0.02 R, $+68) ; own bracket result -2 pts (-0.05 R, $-262). MFE +0.05 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  21:01:03  price 16879.74 (open +0.03 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  21:01:03  price 16879.74 (open +0.03 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 16879.17

**AS-VWAPBRK (Asia MF3)** 2024-04-25 01:31:06 ET, SHORT 6 lots at 17430.54, safety stop 17498.04 (1.5 x own stop 45 pts). Result managed -0 pts/lot (-0.00 R, $-22) ; own bracket result +7 pts (+0.16 R, $+883). MFE +0.06 R, MAE -0.16 R, 20 min under water (longest 20 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  01:52:24  price 17430.54 (open +0.00 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:52:24  price 17430.54 (open +0.00 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 17430.67

**AS-VWAPBRK (Asia MF3)** 2024-04-29 00:06:14 ET, LONG 6 lots at 17898.88, safety stop 17831.38 (1.5 x own stop 45 pts). Result managed +1 pts/lot (+0.03 R, $+168) ; own bracket: not taken (slot effect). MFE +0.07 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  00:07:20  price 17900.90 (open +0.04 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  00:07:20  price 17900.90 (open +0.04 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 17900.33

**AS-VWAPBRK (Asia MF3)** 2024-06-13 19:51:25 ET, LONG 6 lots at 19617.12, safety stop 19549.62 (1.5 x own stop 45 pts). Result managed -1 pts/lot (-0.03 R, $-157) ; own bracket result +29 pts (+0.63 R, $+3418). MFE +0.02 R, MAE -0.04 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  19:53:59  price 19616.45 (open -0.01 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  19:53:59  price 19616.45 (open -0.01 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoStop_S2 at 19615.88

**AS-NR7 (Asia MF1)** 2024-06-23 18:32:07 ET, LONG 6 lots at 20021.12, safety stop 19961.12 (1.5 x own stop 40 pts). Result managed +0 pts/lot (+0.01 R, $+33) ; own bracket result -40 pts (-1.00 R, $-4817). MFE +0.04 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:33:09  price 20022.33 (open +0.03 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  18:33:09  price 20022.33 (open +0.03 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 20021.46

**AS-NR7 (Asia MF1)** 2024-07-31 22:20:06 ET, LONG 6 lots at 19637.96, safety stop 19577.96 (1.5 x own stop 40 pts). Result managed +15 pts/lot (+0.38 R, $+1808) ; own bracket: not taken (slot effect). MFE +0.58 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  22:21:06  price 19642.16 (open +0.11 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  22:21:06  price 19642.16 (open +0.11 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  22:22:07  price 19651.76 (open +0.35 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:40  price 19657.16 (open +0.48 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  22:22:55  price 19653.56 (open +0.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:28:42  price 19658.36 (open +0.51 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 19653.08

**AS-NR7 (Asia MF1)** 2024-08-29 22:56:06 ET, SHORT 6 lots at 19461.58, safety stop 19521.58 (1.5 x own stop 40 pts). Result managed -1 pts/lot (-0.02 R, $-92) ; own bracket result -0 pts (-0.01 R, $-37). MFE +0.05 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  22:57:28  price 19461.58 (open +0.00 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  22:57:28  price 19461.58 (open +0.00 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 19462.29

**AS-NR7 (Asia MF1)** 2024-12-30 20:20:04 ET, LONG 6 lots at 21399.25, safety stop 21339.25 (1.5 x own stop 40 pts). Result managed -0 pts/lot (-0.00 R, $-22) ; own bracket: not taken (slot effect). MFE +0.04 R, MAE -0.04 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  20:21:19  price 21399.85 (open +0.01 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  20:21:19  price 21399.85 (open +0.01 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 21399.12

**AS-NR7 (Asia MF1)** 2025-04-06 19:28:03 ET, LONG 6 lots at 16669.29, safety stop 16609.29 (1.5 x own stop 40 pts). Result managed -60 pts/lot (-1.51 R, $-7237) ; own bracket result -39 pts (-0.97 R, $-4647). MFE +0.07 R, MAE -1.54 R, 4 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 16609.04

**AS-VWAPBRK (Asia MF3)** 2025-04-08 21:22:09 ET, SHORT 6 lots at 16924.08, safety stop 16991.58 (1.5 x own stop 45 pts). Result managed +37 pts/lot (+0.83 R, $+4478) ; own bracket result +45 pts (+1.00 R, $+5403). MFE +1.77 R, MAE -0.12 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  21:23:54  price 16891.01 (open +0.73 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  21:23:54  price 16891.01 (open +0.73 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:25:14  price 16887.63 (open +0.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:25:59  price 16880.88 (open +0.96 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  21:26:15  price 16895.06 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:27:02  price 16870.76 (open +1.19 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:27:17  price 16867.38 (open +1.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 16886.71

**AS-NR7 (Asia MF1)** 2025-04-13 19:32:03 ET, SHORT 6 lots at 19014.00, safety stop 19074.00 (1.5 x own stop 40 pts). Result managed -60 pts/lot (-1.50 R, $-7202) ; own bracket result -35 pts (-0.88 R, $-4227). MFE +0.76 R, MAE -1.48 R, 20 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 37m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 19073.96

**AS-VWAPBRK (Asia MF3)** 2026-05-10 22:48:36 ET, LONG 6 lots at 29343.92, safety stop 29276.42 (1.5 x own stop 45 pts). Result managed -34 pts/lot (-0.75 R, $-4072) ; own bracket: not taken (slot effect). MFE +0.29 R, MAE -1.00 R, 70 min under water (longest 32 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:W 26m:N 74m:A
  23:34:12  price 29330.42 (open -0.30 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  23:34:12  price 29330.42 (open -0.30 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 29310.04

**AS-VWAPBRK (Asia MF3)** 2026-05-20 00:11:41 ET, LONG 6 lots at 28918.42, safety stop 28850.92 (1.5 x own stop 45 pts). Result managed +15 pts/lot (+0.33 R, $+1793) ; own bracket: not taken (slot effect). MFE +0.73 R, MAE -0.27 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 3m:W
  00:14:57  price 28940.02 (open +0.48 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  00:14:57  price 28940.02 (open +0.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  00:16:34  price 28947.44 (open +0.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 28933.42

**AS-VWAPBRK (Asia MF3)** 2026-05-25 18:40:38 ET, SHORT 6 lots at 29907.62, safety stop 29975.12 (1.5 x own stop 45 pts). Result managed +16 pts/lot (+0.35 R, $+1873) ; own bracket: not taken (slot effect). MFE +0.61 R, MAE -0.21 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  18:56:03  price 29887.38 (open +0.45 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  18:56:03  price 29887.38 (open +0.45 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  18:56:18  price 29893.45 (open +0.32 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29891.96

**AS-VWAPBRK (Asia MF3)** 2026-05-27 19:16:27 ET, SHORT 6 lots at 30060.17, safety stop 30127.67 (1.5 x own stop 45 pts). Result managed +15 pts/lot (+0.34 R, $+1808) ; own bracket result +45 pts (+1.00 R, $+5383). MFE +0.74 R, MAE -0.41 R, 4 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A 5m:W
  19:21:16  price 30045.32 (open +0.33 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  19:21:16  price 30045.32 (open +0.33 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:21:31  price 30040.59 (open +0.43 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:22:21  price 30041.94 (open +0.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:22:51  price 30032.49 (open +0.61 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30045.04

**AS-NR7 (Asia MF1)** 2026-05-31 22:44:08 ET, SHORT 6 lots at 30553.25, safety stop 30613.25 (1.5 x own stop 40 pts). Result managed +5 pts/lot (+0.13 R, $+608) ; own bracket: not taken (slot effect). MFE +0.29 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  22:45:12  price 30549.65 (open +0.09 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  22:45:12  price 30549.65 (open +0.09 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  22:55:49  price 30546.05 (open +0.18 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 30548.12

**AS-VWAPBRK (Asia MF3)** 2026-06-08 00:53:00 ET, LONG 6 lots at 29129.79, safety stop 29062.29 (1.5 x own stop 45 pts). Result managed -62 pts/lot (-1.38 R, $-7442) ; own bracket result -44 pts (-0.98 R, $-5277). MFE +0.38 R, MAE -1.48 R, 20 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29067.83

**AS-VWAPBRK (Asia MF3)** 2026-06-09 18:39:39 ET, SHORT 6 lots at 29010.62, safety stop 29078.12 (1.5 x own stop 45 pts). Result managed -68 pts/lot (-1.50 R, $-8107) ; own bracket result -20 pts (-0.45 R, $-2457). MFE +0.64 R, MAE -1.63 R, 16 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29078.12

**AS-NR7 (Asia MF1)** 2026-06-09 19:48:03 ET, LONG 6 lots at 29029.21, safety stop 28969.21 (1.5 x own stop 40 pts). Result managed +13 pts/lot (+0.33 R, $+1553) ; own bracket: not taken (slot effect). MFE +0.93 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  19:55:09  price 29059.81 (open +0.77 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  19:55:09  price 29059.81 (open +0.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:55:42  price 29062.21 (open +0.83 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29042.21

**AS-NR7 (Asia MF1)** 2026-06-12 01:04:10 ET, SHORT 6 lots at 29528.54, safety stop 29588.54 (1.5 x own stop 40 pts). Result managed +2 pts/lot (+0.04 R, $+183) ; own bracket: not taken (slot effect). MFE +0.14 R, MAE -0.10 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  01:05:10  price 29525.54 (open +0.08 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:05:10  price 29525.54 (open +0.08 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29526.96

**AS-VWAPBRK (Asia MF3)** 2026-06-16 20:07:29 ET, LONG 6 lots at 30373.79, safety stop 30306.29 (1.5 x own stop 45 pts). Result managed +70 pts/lot (+1.55 R, $+8348) ; own bracket result +45 pts (+1.00 R, $+5388). MFE +2.05 R, MAE -0.34 R, 9 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 5m:W 6m:N 9m:W 61m:N
  20:51:49  price 30370.42 (open -0.08 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  20:51:49  price 30370.42 (open -0.08 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  21:56:02  price 30442.64 (open +1.53 R of the book stop): state change DEFENDING>RUNNING [P5: a liquidity level just ahead: take it there]
  21:56:02  price 30442.64 (open +1.53 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  21:56:17  price 30444.67 (open +1.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:10:04  price 30448.04 (open +1.65 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:10:19  price 30446.02 (open +1.60 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:11:42  price 30450.07 (open +1.69 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:12:48  price 30450.74 (open +1.71 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:14:08  price 30453.44 (open +1.77 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:14:27  price 30454.79 (open +1.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:21:16  price 30454.79 (open +1.80 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:07  price 30457.49 (open +1.86 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:22  price 30457.49 (open +1.86 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:37  price 30458.84 (open +1.89 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:22:52  price 30458.17 (open +1.88 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:26:30  price 30460.87 (open +1.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:28:25  price 30460.87 (open +1.94 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  22:33:13  price 30443.32 (open +1.54 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: ExAlgoStop_P1 at 30443.42

**AS-RSI (Asia MF2)** 2026-07-13 18:55:11 ET, SHORT 6 lots at 29405.62, safety stop 29495.62 (1.5 x own stop 60 pts). Result managed +21 pts/lot (+0.35 R, $+2508) ; own bracket result +60 pts (+1.00 R, $+7178). MFE +0.65 R, MAE -0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  19:04:09  price 29376.83 (open +0.48 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  19:04:09  price 29376.83 (open +0.48 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:05:10  price 29380.42 (open +0.42 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:12:20  price 29375.03 (open +0.51 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:12:36  price 29372.33 (open +0.55 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29384.67

**AS-NR7 (Asia MF1)** 2026-07-16 00:00:03 ET, LONG 6 lots at 29744.88, safety stop 29684.88 (1.5 x own stop 40 pts). Result managed -0 pts/lot (-0.01 R, $-37) ; own bracket: not taken (slot effect). MFE +0.16 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  00:01:06  price 29744.88 (open +0.00 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  00:01:06  price 29744.88 (open +0.00 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 29744.62

**AS-VWAPBRK (Asia MF3)** 2026-07-28 19:34:11 ET, LONG 6 lots at 27900.21, safety stop 27832.71 (1.5 x own stop 45 pts). Result managed +117 pts/lot (+2.61 R, $+14073) ; own bracket result +45 pts (+1.00 R, $+5398). MFE +6.12 R, MAE -0.29 R, 6 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:N 8m:W
  19:44:02  price 27935.98 (open +0.80 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  19:44:02  price 27935.98 (open +0.80 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  19:44:17  price 27936.66 (open +0.81 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:44:32  price 27990.66 (open +2.01 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:45:02  price 28007.53 (open +2.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:32  price 28016.31 (open +2.58 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:46:47  price 28019.01 (open +2.64 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:17  price 28035.88 (open +3.01 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:47:47  price 28045.33 (open +3.22 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:49:47  price 28052.76 (open +3.39 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:50:32  price 28091.91 (open +4.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  19:59:37  price 28095.96 (open +4.35 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:00:07  price 28102.71 (open +4.50 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:01:38  price 28133.08 (open +5.18 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:02:08  price 28146.58 (open +5.47 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:06:42  price 28154.01 (open +5.64 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:30  price 28164.13 (open +5.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:08:45  price 28164.13 (open +5.87 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 28017.54

**AS-NR7 (Asia MF1)** 2026-07-29 18:28:03 ET, SHORT 6 lots at 27417.75, safety stop 27477.75 (1.5 x own stop 40 pts). Result managed -60 pts/lot (-1.51 R, $-7267) ; own bracket result -39 pts (-0.98 R, $-4697). MFE +0.61 R, MAE -1.49 R, 15 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 9m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 27478.25

**AS-NR7 (Asia MF1)** 2026-07-30 00:40:03 ET, SHORT 6 lots at 27492.12, safety stop 27552.12 (1.5 x own stop 40 pts). Result managed +19 pts/lot (+0.47 R, $+2238) ; own bracket: not taken (slot effect). MFE +0.74 R, MAE -0.30 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  00:44:15  price 27464.53 (open +0.69 R of the book stop): state change PROBE>RUNNING [P5: a liquidity level just ahead: take it there]
  00:44:15  price 27464.53 (open +0.69 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  00:44:30  price 27473.53 (open +0.46 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 27473.42

**AS-NR7 (Asia MF1)** 2026-08-09 21:00:03 ET, SHORT 6 lots at 29803.08, safety stop 29863.08 (1.5 x own stop 40 pts). Result managed -61 pts/lot (-1.52 R, $-7282) ; own bracket result -40 pts (-1.00 R, $-4792). MFE +0.22 R, MAE -1.58 R, 15 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29863.71

**AS-NR7 (Asia MF1)** 2026-08-17 23:40:04 ET, LONG 6 lots at 29889.67, safety stop 29829.67 (1.5 x own stop 40 pts). Result managed +8 pts/lot (+0.20 R, $+948) ; own bracket: not taken (slot effect). MFE +0.56 R, MAE -0.15 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  23:54:09  price 29905.87 (open +0.41 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  23:54:09  price 29905.87 (open +0.41 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29897.62

**AS-VWAPBRK (Asia MF3)** 2026-08-25 19:51:45 ET, SHORT 6 lots at 29219.00, safety stop 29286.50 (1.5 x own stop 45 pts). Result managed +12 pts/lot (+0.28 R, $+1493) ; own bracket result +45 pts (+1.00 R, $+5393). MFE +0.80 R, MAE -0.12 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:W
  20:00:36  price 29190.65 (open +0.63 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  20:00:36  price 29190.65 (open +0.63 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29206.50

**AS-VWAPBRK (Asia MF3)** 2026-08-31 20:46:49 ET, SHORT 6 lots at 29502.29, safety stop 29569.79 (1.5 x own stop 45 pts). Result managed +16 pts/lot (+0.35 R, $+1873) ; own bracket: not taken (slot effect). MFE +0.62 R, MAE -0.30 R, 25 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 4m:W 5m:N 6m:W 7m:N 39m:W
  21:19:26  price 29512.42 (open -0.22 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  21:19:26  price 29512.42 (open -0.22 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  21:25:58  price 29483.39 (open +0.42 R of the book stop): state change DEFENDING>RUNNING [P5: a liquidity level just ahead: take it there]
  21:25:58  price 29483.39 (open +0.42 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  21:26:13  price 29480.02 (open +0.49 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:30:36  price 29476.64 (open +0.57 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29486.62

**AS-VWAPBRK (Asia MF3)** 2026-09-01 18:47:49 ET, SHORT 6 lots at 29121.92, safety stop 29189.42 (1.5 x own stop 45 pts). Result managed +6 pts/lot (+0.14 R, $+743) ; own bracket: not taken (slot effect). MFE +0.36 R, MAE -0.58 R, 77 min under water (longest 42 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 61m:N
  19:20:23  price 29130.02 (open -0.18 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  19:20:23  price 29130.02 (open -0.18 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  20:06:48  price 29110.44 (open +0.26 R of the book stop): state change DEFENDING>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  20:06:48  price 29110.44 (open +0.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  20:07:03  price 29110.44 (open +0.26 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 29115.67

**AS-RSI (Asia MF2)** 2026-09-06 23:42:30 ET, LONG 6 lots at 29605.33, safety stop 29515.33 (1.5 x own stop 60 pts). Result managed -1 pts/lot (-0.02 R, $-122) ; own bracket: not taken (slot effect). MFE +0.00 R, MAE -0.59 R, 102 min under water (longest 102 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  01:25:03  price 29605.33 (open +0.00 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:25:03  price 29605.33 (open +0.00 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29604.38

**AS-NR7 (Asia MF1)** 2026-09-11 01:56:03 ET, LONG 6 lots at 29235.21, safety stop 29175.21 (1.5 x own stop 40 pts). Result managed +1 pts/lot (+0.03 R, $+128) ; own bracket result -4 pts (-0.11 R, $-512). MFE +0.08 R, MAE -0.21 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N
  01:58:05  price 29235.81 (open +0.01 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:58:05  price 29235.81 (open +0.01 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29236.33

**AS-VWAPBRK (Asia MF3)** 2026-09-15 00:56:27 ET, LONG 6 lots at 29073.08, safety stop 29005.58 (1.5 x own stop 45 pts). Result managed -0 pts/lot (-0.01 R, $-42) ; own bracket: not taken (slot effect). MFE +0.08 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  00:57:36  price 29074.43 (open +0.03 R of the book stop): state change PROBE>RUNNING [S2: the bell is near and the distance wanted is large: take the profit now]
  00:57:36  price 29074.43 (open +0.03 R of the book stop): moved the stop closer [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: Stop at 29072.79

**AS-VWAPBRK (Asia MF3)** 2026-09-22 01:21:33 ET, SHORT 6 lots at 30793.58, safety stop 30861.08 (1.5 x own stop 45 pts). Result managed +1 pts/lot (+0.02 R, $+88) ; own bracket result -39 pts (-0.86 R, $-4647). MFE +0.17 R, MAE -0.28 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  01:24:50  price 30792.23 (open +0.03 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:24:50  price 30792.23 (open +0.03 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 30792.79

**AS-VWAPBRK (Asia MF3)** 2026-09-29 19:06:42 ET, SHORT 6 lots at 30677.04, safety stop 30744.54 (1.5 x own stop 45 pts). Result managed -45 pts/lot (-1.00 R, $-5392) ; own bracket result -45 pts (-1.00 R, $-5392). MFE +0.17 R, MAE -0.98 R, 39 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:N 31m:A
  19:39:18  price 30702.02 (open -0.55 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  19:39:18  price 30702.02 (open -0.55 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 30721.92

**AS-VWAPBRK (Asia MF3)** 2026-09-29 21:01:58 ET, SHORT 6 lots at 30656.29, safety stop 30723.79 (1.5 x own stop 45 pts). Result managed +8 pts/lot (+0.17 R, $+923) ; own bracket result +45 pts (+1.00 R, $+5398). MFE +0.41 R, MAE -0.23 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 5m:W
  21:08:30  price 30641.44 (open +0.33 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  21:08:30  price 30641.44 (open +0.33 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  21:09:17  price 30645.49 (open +0.24 R of the book stop): took a part [P5: a liquidity level just ahead: take it there]
  exit: Stop at 30648.54

**AS-VWAPBRK (Asia MF3)** 2026-10-07 23:17:04 ET, SHORT 6 lots at 31389.92, safety stop 31457.42 (1.5 x own stop 45 pts). Result managed +6 pts/lot (+0.13 R, $+713) ; own bracket result +45 pts (+1.00 R, $+5383). MFE +0.34 R, MAE -0.61 R, 23 min under water (longest 17 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 26m:N
  23:43:29  price 31377.77 (open +0.27 R of the book stop): state change PROBE>RUNNING [P1: the trade is a winner: trail protecting it behind price]
  23:43:29  price 31377.77 (open +0.27 R of the book stop): moved the stop closer [P1: the trade is a winner: trail protecting it behind price]
  exit: Stop at 31383.92

**AS-NR7 (Asia MF1)** 2026-10-22 01:44:03 ET, SHORT 6 lots at 29533.17, safety stop 29593.17 (1.5 x own stop 40 pts). Result managed +3 pts/lot (+0.07 R, $+343) ; own bracket result -11 pts (-0.28 R, $-1337). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  01:45:03  price 29526.57 (open +0.17 R of the book stop): state change PROBE>OUT [S2: the bell is near and the distance wanted is large: take the profit now]
  01:45:03  price 29526.57 (open +0.17 R of the book stop): closed everything [S2: the bell is near and the distance wanted is large: take the profit now]
  exit: ExAlgoAll_S2 at 29530.25

**AS-NR7 (Asia MF1)** 2026-10-25 23:20:06 ET, SHORT 6 lots at 29071.54, safety stop 29131.54 (1.5 x own stop 40 pts). Result managed -60 pts/lot (-1.49 R, $-7182) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  (no manager action: the safety stop / session end ended it)
  exit: Stop at 29131.33

**AS-VWAPBRK (Asia MF3)** 2026-10-26 23:40:10 ET, LONG 6 lots at 29447.33, safety stop 29379.83 (1.5 x own stop 45 pts). Result managed -45 pts/lot (-1.01 R, $-5447) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  00:09:37  price 29433.16 (open -0.32 R of the book stop): state change PROBE>DEFENDING [L3: stuck too long and still not a winner: stop waiting]
  00:09:37  price 29433.16 (open -0.32 R of the book stop): moved the stop closer [L3: stuck too long and still not a winner: stop waiting]
  exit: Stop at 29402.00

---
Generator: code/th_dynexit/tape_review.py (server C; reads attrib/tape_review/rows/ copies of runs_rf trades): `python3 -I tape_review.py SESSION[,SESSION] DESIGNSUFFIX VARIANT OUT.md`, e.g. `NY MGMIDL1 A` for the v0 middle design; for the playbook rows use the set suffix of TL3_DX_<S>_<tag>_PB1_<A|M> and the generator prints the 'screens' lines from algo_log items 'sec:vote:VVVVVVVV:openR'. Own-bracket reference sets TL3_DX_<S>_<tag>_fix_A. Prices on the tape are the back-adjusted instr_1s series: excursions are relative to the tape close of the entry second, prices shown are entry price + the managed R path.


---
# DK22 (DESK v0.2.2 MAIN) TAPE REVIEW, appended 2026-11-28 02:43Z (order 0240Z). Same format as above. Rows: TL3_DX_<S>_<MF>_DK22MAIN_A (alone bare, desk manager v0.2.2) matched on book+signal time to TL3_DX_<S>_<MF>_fix_A (the book on its own fixed bracket). WINDOW = the months the DK22 set has: Asia and London 2023-09..2026-10 (37 months), NY AM and NY PM 2024-10..2026-10 (24 months), Nov 2025 excluded; the own-bracket rows are cut to the same months by the matching. The "no rule 6 / PB1 rows have not run yet" sentence under each count table is carried over from the generator text and does not apply to DK22; the slot lines are net_fee dollars ($1.18/lot) here, the DESK_V022_SCORECARD.md page uses p484 ($4.84/lot) so slot dollars differ a little, the four counts are the same. S0 (the book stop used for R) = median stop distance of the book on fix_A (generator patched because attrib/paths2/meta.parquet no longer exists). Safety stop shown = 1.5 x S0.

# DK22 PART: NY

# NY AM (NY): managed rows DK22MAIN_A, 7618 trades from 96 finished (set, month) rows, matched to the book's own bracket on 4655 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 466 | +3624215 | 2024 +297635, 2025 +1421885, 2026 +1904695 |
| winners cut short | 1624 | -8323975 | 2024 -759415, 2025 -3294735, 2026 -4269825 |
| losers cut early | 1108 | +8080470 | 2024 +746105, 2025 +3185195, 2026 +4149170 |
| losers made worse | 272 | -799405 | 2024 -47940, 2025 -263915, 2026 -487550 |
| matched pairs (all) | 4655 | -1127155 | 2024 -89865, 2025 -382275, 2026 -655015 |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 2963 trades, net $ -80490; entries that exist only under the own bracket in the same months (blocked by a carried trade): 2131 trades, net $ +61106. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## NY AM: the 20 WORST give-backs (largest open profit given back, $)

**NY-NODE (NY AM MF4)** 2025-04-07 10:22:24 ET, LONG 6 lots at 17678.79, safety stop 17544.92 (1.5 x own stop 89.25 pts). Result managed -132 pts/lot (-1.48 R, $-15897) ; own bracket: not taken (slot effect). MFE +1.51 R, MAE -1.37 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:22:25  price 17653.36 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:23:24  price 17635.95 (open -0.48 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  exit: Stop at 17546.38

**NY-FIB (NY AM MF1)** 2025-04-11 10:46:42 ET, LONG 6 lots at 18507.83, safety stop 18329.33 (1.5 x own stop 119 pts). Result managed -155 pts/lot (-1.30 R, $-18592) ; own bracket result -119 pts (-1.00 R, $-14287). MFE +0.57 R, MAE -1.53 R, 29 min under water (longest 18 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 7m:A
  10:46:43  price 18507.83 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:48:12  price 18518.54 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:50:12  price 18498.91 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:51:12  price 18454.28 (open -0.45 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:52:12  price 18464.99 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:53:42  price 18447.14 (open -0.51 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:54:12  price 18441.79 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:56:12  price 18441.79 (open -0.55 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:57:12  price 18488.20 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:59:42  price 18415.01 (open -0.78 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:00:12  price 18564.95 (open +0.48 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:00:27  price 18534.61 (open +0.22 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:03:27  price 18391.81 (open -0.98 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:08:12  price 18377.53 (open -1.09 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  11:08:12  price 18377.53 (open -1.09 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  11:08:12  price 18377.53 (open -1.09 R of the book stop): took a part [DF: DF]
  11:09:12  price 18411.44 (open -0.81 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:10:12  price 18434.65 (open -0.61 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  11:11:12  price 18397.16 (open -0.93 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:15:27  price 18343.61 (open -1.38 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:15:42  price 18375.74 (open -1.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:18:12  price 18343.61 (open -1.38 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  exit: Stop at 18352.96

**NY-FIB (NY AM MF1)** 2026-07-10 10:22:49 ET, SHORT 6 lots at 29881.67, safety stop 30060.17 (1.5 x own stop 119 pts). Result managed +21 pts/lot (+0.18 R, $+2553) ; own bracket: not taken (slot effect). MFE +1.76 R, MAE -0.61 R, 8 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 5m:N
  10:22:50  price 29885.24 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:24:04  price 29904.87 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:27:04  price 29901.30 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:28:04  price 29924.51 (open -0.36 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:29:04  price 29933.43 (open -0.43 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:30:34  price 29917.37 (open -0.30 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:30:34  price 29917.37 (open -0.30 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:30:34  price 29917.37 (open -0.30 R of the book stop): took a part [DF: DF]
  10:31:19  price 29920.94 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:31:49  price 29928.08 (open -0.39 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:32:04  price 29926.29 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:32:19  price 29938.79 (open -0.48 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:32:51  price 29890.59 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:33:06  price 29731.73 (open +1.26 R of the book stop): state change desk [NORMAL/WNWNAA: NORMAL/WNWNAA]
  10:33:06  price 29731.73 (open +1.26 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  10:33:06  price 29731.73 (open +1.26 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 29860.33

**NY-NODE (NY AM MF4)** 2026-06-25 09:59:38 ET, SHORT 6 lots at 29344.25, safety stop 29478.12 (1.5 x own stop 89.25 pts). Result managed -135 pts/lot (-1.51 R, $-16222) ; own bracket result +30 pts (+0.34 R, $+3593). MFE +0.56 R, MAE -1.50 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:59:39  price 29349.60 (open -0.06 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  10:00:38  price 29381.74 (open -0.42 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:02:08  price 29409.85 (open -0.73 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  exit: Stop at 29479.38

**NY-VALUE (NY AM MF2)** 2026-07-10 10:32:59 ET, SHORT 6 lots at 29803.38, safety stop 29892.38 (1.5 x own stop 59.3333 pts). Result managed -88 pts/lot (-1.48 R, $-10517) ; own bracket result +60 pts (+1.01 R, $+7178). MFE +1.45 R, MAE -2.24 R, 6 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  10:33:00  price 29761.55 (open +0.70 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:33:59  price 29826.51 (open -0.39 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:34:14  price 29846.09 (open -0.72 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:35:14  price 29856.77 (open -0.90 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:36:29  price 29871.90 (open -1.16 R of the book stop): state change desk [PRESS/NNNWWN: PRESS/NNNWWN]
  10:36:44  price 29857.66 (open -0.92 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:37:14  price 29862.11 (open -0.99 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:38:14  price 29865.67 (open -1.05 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:38:44  price 29887.03 (open -1.41 R of the book stop): state change desk [PRESS/NNNWWN: PRESS/NNNWWN]
  exit: Stop at 29890.96

**NY-NODE (NY AM MF4)** 2026-06-03 09:49:25 ET, SHORT 6 lots at 30532.00, safety stop 30665.88 (1.5 x own stop 89.25 pts). Result managed -118 pts/lot (-1.32 R, $-14167) ; own bracket result +30 pts (+0.34 R, $+3593). MFE +0.52 R, MAE -1.40 R, 21 min under water (longest 21 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  09:49:26  price 30542.71 (open -0.12 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  09:50:25  price 30517.27 (open +0.17 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:50:40  price 30530.66 (open +0.01 R of the book stop): state change desk [PRESS/WNNNWW: PRESS/WNNNWW]
  09:51:10  price 30566.81 (open -0.39 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  09:52:10  price 30592.24 (open -0.68 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:53:25  price 30597.60 (open -0.73 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:53:40  price 30612.33 (open -0.90 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:54:40  price 30584.21 (open -0.58 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:54:55  price 30578.86 (open -0.52 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:55:10  price 30590.90 (open -0.66 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:55:25  price 30590.90 (open -0.66 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  09:55:40  price 30570.82 (open -0.43 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:56:10  price 30582.87 (open -0.57 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  09:57:10  price 30564.13 (open -0.36 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:57:25  price 30566.81 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:57:40  price 30552.08 (open -0.22 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:59:10  price 30584.21 (open -0.58 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:59:25  price 30580.19 (open -0.54 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:59:55  price 30566.81 (open -0.39 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  10:00:10  price 30570.82 (open -0.43 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:00:25  price 30586.89 (open -0.61 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:01:10  price 30592.24 (open -0.68 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  10:01:40  price 30609.65 (open -0.87 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:02:40  price 30631.07 (open -1.11 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  10:03:10  price 30640.44 (open -1.22 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:04:10  price 30632.41 (open -1.12 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:04:10  price 30632.41 (open -1.12 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:04:10  price 30632.41 (open -1.12 R of the book stop): took a part [DF: DF]
  10:05:10  price 30623.03 (open -1.02 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:06:55  price 30637.76 (open -1.19 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  10:07:10  price 30627.05 (open -1.06 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:07:40  price 30600.28 (open -0.77 R of the book stop): state change desk [NORMAL/WNNAWN: NORMAL/WNNAWN]
  10:07:55  price 30605.63 (open -0.83 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:08:10  price 30604.29 (open -0.81 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:08:25  price 30623.03 (open -1.02 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:11:10  price 30649.81 (open -1.32 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:11:25  price 30655.17 (open -1.38 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:12:10  price 30661.86 (open -1.46 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  exit: Stop at 30650.00

**NY-FIB (NY AM MF1)** 2026-06-25 09:50:13 ET, LONG 6 lots at 29611.83, safety stop 29433.33 (1.5 x own stop 119 pts). Result managed -92 pts/lot (-0.77 R, $-11032) ; own bracket: not taken (slot effect). MFE +0.53 R, MAE -1.64 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  09:50:14  price 29620.76 (open +0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:51:13  price 29610.05 (open -0.01 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  09:51:13  price 29610.05 (open -0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:51:13  price 29610.05 (open -0.01 R of the book stop): took a part [DF: DF]
  09:51:43  price 29547.57 (open -0.54 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  09:52:28  price 29529.72 (open -0.69 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  09:52:43  price 29492.24 (open -1.01 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  09:53:13  price 29552.93 (open -0.49 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:53:28  price 29495.81 (open -0.98 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  09:54:13  price 29460.11 (open -1.27 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  exit: Stop at 29519.96

**NY-VALUE (NY AM MF2)** 2025-04-11 10:15:35 ET, LONG 6 lots at 18518.92, safety stop 18429.92 (1.5 x own stop 59.3333 pts). Result managed -80 pts/lot (-1.35 R, $-9612) ; own bracket result +60 pts (+1.01 R, $+7203). MFE +1.07 R, MAE -1.58 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  10:15:36  price 18521.59 (open +0.04 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:16:35  price 18534.94 (open +0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:19:05  price 18449.50 (open -1.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:19:20  price 18462.85 (open -0.95 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:19:35  price 18443.27 (open -1.27 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:19:35  price 18443.27 (open -1.27 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:19:35  price 18443.27 (open -1.27 R of the book stop): took a part [DF: DF]
  exit: Stop at 18438.88

**NY-FIB (NY AM MF1)** 2026-07-14 10:04:44 ET, LONG 6 lots at 29700.25, safety stop 29521.75 (1.5 x own stop 119 pts). Result managed +2 pts/lot (+0.02 R, $+263) ; own bracket: not taken (slot effect). MFE +1.20 R, MAE -1.09 R, 27 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  10:04:45  price 29696.68 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:05:44  price 29675.26 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:16:14  price 29584.22 (open -0.98 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:16:14  price 29584.22 (open -0.98 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:16:14  price 29584.22 (open -0.98 R of the book stop): took a part [DF: DF]
  10:18:14  price 29591.37 (open -0.92 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:22:14  price 29680.62 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:22:29  price 29696.68 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:23:59  price 29684.19 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:24:29  price 29685.97 (open -0.12 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:24:44  price 29666.33 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:25:14  price 29659.19 (open -0.35 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:26:14  price 29675.26 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:30:14  price 29694.90 (open -0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:30:44  price 29680.62 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:30:59  price 29687.76 (open -0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:31:14  price 29684.19 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:32:59  price 29730.60 (open +0.26 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:32:59  price 29730.60 (open +0.26 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  10:32:59  price 29730.60 (open +0.26 R of the book stop): moved the stop closer [OB1: OB1]
  10:34:14  price 29823.42 (open +1.03 R of the book stop): state change RUNNER>OUT [DV: DV]
  10:34:14  price 29823.42 (open +1.03 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29702.50

**NY-VALUE (NY AM MF2)** 2026-06-29 09:30:18 ET, SHORT 6 lots at 29598.17, safety stop 29687.17 (1.5 x own stop 59.3333 pts). Result managed -88 pts/lot (-1.48 R, $-10577) ; own bracket result -60 pts (-1.01 R, $-7182). MFE +0.65 R, MAE -1.58 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:30:19  price 29595.50 (open +0.04 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  09:31:18  price 29606.18 (open -0.14 R of the book stop): state change desk [PRESS/NNNWW-: PRESS/NNNWW-]
  exit: Stop at 29686.25

**NY-VALUE (NY AM MF2)** 2026-06-24 09:43:02 ET, SHORT 6 lots at 29621.21, safety stop 29710.21 (1.5 x own stop 59.3333 pts). Result managed -90 pts/lot (-1.52 R, $-10852) ; own bracket result -47 pts (-0.80 R, $-5672). MFE +0.61 R, MAE -1.22 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:43:03  price 29639.90 (open -0.32 R of the book stop): state change desk [PRESS/WNWANW: PRESS/WNWANW]
  09:44:02  price 29635.45 (open -0.24 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:44:17  price 29661.26 (open -0.68 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  09:44:32  price 29646.13 (open -0.42 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:44:47  price 29648.80 (open -0.46 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  09:45:02  price 29668.38 (open -0.80 R of the book stop): state change desk [PRESS/WNAWNW: PRESS/WNAWNW]
  09:45:32  price 29698.64 (open -1.30 R of the book stop): state change desk [NORMAL/NAAWNW: NORMAL/NAAWNW]
  exit: Stop at 29711.58

**NY-VALUE (NY AM MF2)** 2026-06-29 10:48:36 ET, SHORT 6 lots at 29530.25, safety stop 29619.25 (1.5 x own stop 59.3333 pts). Result managed -91 pts/lot (-1.53 R, $-10917) ; own bracket result -60 pts (-1.00 R, $-7152). MFE +0.56 R, MAE -1.58 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:48:37  price 29530.25 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:50:06  price 29578.31 (open -0.81 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  exit: Stop at 29621.17

**NY-VALUE (NY AM MF2)** 2026-02-17 09:32:35 ET, SHORT 6 lots at 24679.71, safety stop 24768.71 (1.5 x own stop 59.3333 pts). Result managed -91 pts/lot (-1.53 R, $-10872) ; own bracket result -55 pts (-0.93 R, $-6627). MFE +0.54 R, MAE -1.56 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  09:32:36  price 24685.05 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  09:33:35  price 24693.95 (open -0.24 R of the book stop): state change desk [NORMAL/ANWNN-: NORMAL/ANWNN-]
  09:34:05  price 24704.63 (open -0.42 R of the book stop): state change desk [NORMAL/ANWNNA: NORMAL/ANWNNA]
  09:35:05  price 24747.35 (open -1.14 R of the book stop): state change desk [NORMAL/ANWANN: NORMAL/ANWANN]
  exit: Stop at 24770.25

**NY-VALUE (NY AM MF2)** 2025-04-11 11:00:03 ET, SHORT 6 lots at 18446.71, safety stop 18535.71 (1.5 x own stop 59.3333 pts). Result managed -88 pts/lot (-1.49 R, $-10612) ; own bracket: not taken (slot effect). MFE +0.57 R, MAE -0.52 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 
  11:00:04  price 18510.79 (open -1.08 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  exit: Stop at 18535.08

**NY-VALUE (NY AM MF2)** 2026-07-31 10:19:49 ET, SHORT 6 lots at 28181.58, safety stop 28270.58 (1.5 x own stop 59.3333 pts). Result managed -90 pts/lot (-1.52 R, $-10837) ; own bracket result -59 pts (-0.99 R, $-7072). MFE +0.54 R, MAE -1.40 R, 9 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  10:19:50  price 28187.81 (open -0.11 R of the book stop): state change desk [PRESS/WNWWNW: PRESS/WNWWNW]
  10:20:49  price 28228.75 (open -0.80 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:21:04  price 28231.42 (open -0.84 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  10:21:34  price 28184.25 (open -0.04 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  10:21:49  price 28203.83 (open -0.38 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  10:22:04  price 28206.50 (open -0.42 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:24:19  price 28175.35 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:26:04  price 28189.59 (open -0.14 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:30:49  price 28256.34 (open -1.26 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  exit: Stop at 28271.83

**NY-VALUE (NY AM MF2)** 2026-02-09 09:30:56 ET, SHORT 6 lots at 24971.83, safety stop 25060.83 (1.5 x own stop 59.3333 pts). Result managed -88 pts/lot (-1.48 R, $-10517) ; own bracket result -57 pts (-0.96 R, $-6812). MFE +0.53 R, MAE -1.31 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  09:30:57  price 24986.96 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:31:56  price 25007.43 (open -0.60 R of the book stop): state change desk [NORMAL/WNAAN-: NORMAL/WNAAN-]
  09:32:11  price 25006.54 (open -0.58 R of the book stop): state change desk [NORMAL/WANAN-: NORMAL/WANAN-]
  09:32:41  price 25010.99 (open -0.66 R of the book stop): state change desk [NORMAL/WNWAN-: NORMAL/WNWAN-]
  09:32:56  price 25032.35 (open -1.02 R of the book stop): state change desk [NORMAL/WNNAN-: NORMAL/WNNAN-]
  09:33:11  price 25022.56 (open -0.85 R of the book stop): state change desk [PRESS/WNNWN-: PRESS/WNNWN-]
  09:33:41  price 25037.69 (open -1.11 R of the book stop): state change desk [NORMAL/WANWN-: NORMAL/WANWN-]
  09:33:56  price 25049.26 (open -1.30 R of the book stop): state change desk [NORMAL/NNNWN-: NORMAL/NNNWN-]
  exit: Stop at 25059.42

**NY-NODE (NY AM MF4)** 2026-06-25 09:50:03 ET, LONG 6 lots at 29637.62, safety stop 29503.75 (1.5 x own stop 89.25 pts). Result managed -66 pts/lot (-0.74 R, $-7927) ; own bracket result +30 pts (+0.34 R, $+3608). MFE +0.59 R, MAE -1.48 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  09:50:04  price 29628.25 (open -0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:51:03  price 29638.96 (open +0.01 R of the book stop): state change desk [DEFEND/ANWANA: DEFEND/ANWANA]
  09:51:03  price 29638.96 (open +0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:51:03  price 29638.96 (open +0.01 R of the book stop): took a part [DF: DF]
  09:51:18  price 29598.80 (open -0.43 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  09:51:48  price 29563.99 (open -0.83 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  09:52:03  price 29549.27 (open -0.99 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  09:52:33  price 29522.49 (open -1.29 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  exit: Stop at 29571.62

**NY-VALUE (NY AM MF2)** 2025-03-11 10:04:15 ET, SHORT 6 lots at 19394.08, safety stop 19483.08 (1.5 x own stop 59.3333 pts). Result managed -86 pts/lot (-1.45 R, $-10312) ; own bracket result -58 pts (-0.99 R, $-7022). MFE +0.55 R, MAE -1.66 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  10:04:16  price 19385.18 (open +0.15 R of the book stop): state change desk [PRESS/NNWNWN: PRESS/NNWNWN]
  10:05:15  price 19402.09 (open -0.14 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:06:00  price 19402.98 (open -0.15 R of the book stop): state change desk [NORMAL/WNNWNA: NORMAL/WNNWNA]
  10:06:15  price 19426.12 (open -0.54 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  10:07:00  price 19471.51 (open -1.30 R of the book stop): state change desk [NORMAL/NNAWAN: NORMAL/NNAWAN]
  exit: Stop at 19479.96

**NY-VALUE (NY AM MF2)** 2026-09-09 10:30:08 ET, LONG 6 lots at 29530.33, safety stop 29441.33 (1.5 x own stop 59.3333 pts). Result managed -75 pts/lot (-1.26 R, $-8952) ; own bracket: not taken (slot effect). MFE +0.56 R, MAE -1.51 R, 31 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 31m:N 36m:A
  10:30:09  price 29530.33 (open -0.00 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:31:08  price 29519.65 (open -0.18 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:33:08  price 29516.09 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:37:38  price 29498.29 (open -0.54 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:38:08  price 29503.63 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:38:53  price 29498.29 (open -0.54 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:39:23  price 29509.86 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:43:53  price 29531.22 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:44:23  price 29528.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:50:08  price 29536.56 (open +0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:51:38  price 29520.54 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:54:08  price 29505.41 (open -0.42 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:54:23  price 29510.75 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:54:53  price 29507.19 (open -0.39 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:55:08  price 29521.43 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:55:38  price 29508.97 (open -0.36 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:55:53  price 29509.86 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:59:08  price 29535.67 (open +0.09 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:59:23  price 29533.89 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:00:53  price 29552.58 (open +0.38 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:01:23  price 29534.78 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:02:08  price 29512.53 (open -0.30 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  11:02:23  price 29519.65 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:02:38  price 29508.08 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  11:03:08  price 29493.84 (open -0.61 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:03:23  price 29492.06 (open -0.65 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:05:08  price 29503.63 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  11:05:23  price 29495.62 (open -0.58 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  11:05:38  price 29500.96 (open -0.49 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  11:05:53  price 29484.94 (open -0.77 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  11:06:53  price 29477.82 (open -0.89 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  11:07:08  price 29469.81 (open -1.02 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  11:07:53  price 29480.49 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  11:08:08  price 29472.48 (open -0.98 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  11:08:08  price 29472.48 (open -0.98 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  11:08:08  price 29472.48 (open -0.98 R of the book stop): took a part [DF: DF]
  11:08:23  price 29478.71 (open -0.87 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  11:08:38  price 29468.92 (open -1.03 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  11:09:08  price 29462.69 (open -1.14 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  exit: Stop at 29455.79

**NY-NODE (NY AM MF4)** 2025-04-07 10:16:53 ET, LONG 6 lots at 18245.12, safety stop 18111.25 (1.5 x own stop 89.25 pts). Result managed +23 pts/lot (+0.26 R, $+2733) ; own bracket result +30 pts (+0.34 R, $+3608). MFE +1.43 R, MAE -0.18 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:16:54  price 18233.08 (open -0.14 R of the book stop): state change desk [PRESS/WNWWAW: PRESS/WNWWAW]
  10:17:53  price 18289.30 (open +0.49 R of the book stop): state change desk [PRESS/WNWWWW: PRESS/WNWWWW]
  10:17:53  price 18289.30 (open +0.49 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:17:53  price 18289.30 (open +0.49 R of the book stop): took a part [OB1: OB1]
  10:18:08  price 18255.83 (open +0.12 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:18:08  price 18255.83 (open +0.12 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18267.96

## NY AM: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**NY-VALUE (NY AM MF2)** 2025-08-22 10:00:03 ET, LONG 6 lots at 23291.88, safety stop 23202.88 (1.5 x own stop 59.3333 pts). Result managed +193 pts/lot (+3.25 R, $+23153) ; own bracket result +60 pts (+1.01 R, $+7208). MFE +3.23 R, MAE -0.16 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:00:04  price 23307.90 (open +0.27 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  10:01:03  price 23472.54 (open +3.04 R of the book stop): state change desk [NORMAL/WNWAAN: NORMAL/WNWAAN]
  10:01:03  price 23472.54 (open +3.04 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:01:03  price 23472.54 (open +3.04 R of the book stop): took a part [OB1: OB1]
  10:01:18  price 23486.78 (open +3.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:01:18  price 23486.78 (open +3.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23484.88

**NY-VALUE (NY AM MF2)** 2026-02-20 10:00:58 ET, LONG 6 lots at 24927.21, safety stop 24838.21 (1.5 x own stop 59.3333 pts). Result managed +138 pts/lot (+2.33 R, $+16583) ; own bracket result +60 pts (+1.01 R, $+7198). MFE +2.59 R, MAE -0.40 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:00:59  price 24928.99 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:01:58  price 25064.27 (open +2.31 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  10:01:58  price 25064.27 (open +2.31 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:01:58  price 25064.27 (open +2.31 R of the book stop): took a part [OB1: OB1]
  10:02:13  price 25071.39 (open +2.43 R of the book stop): state change desk [PRESS/WNWNWN: PRESS/WNWNWN]
  10:02:13  price 25071.39 (open +2.43 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:02:13  price 25071.39 (open +2.43 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25065.46

**NY-VALUE (NY AM MF2)** 2026-06-12 09:40:45 ET, SHORT 6 lots at 29442.50, safety stop 29531.50 (1.5 x own stop 59.3333 pts). Result managed +118 pts/lot (+2.00 R, $+14203) ; own bracket result +60 pts (+1.01 R, $+7193). MFE +1.50 R, MAE -0.21 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:40:47  price 29412.24 (open +0.51 R of the book stop): state change desk [PRESS/WNWNN-: PRESS/WNWNN-]
  09:41:45  price 29325.02 (open +1.98 R of the book stop): state change desk [PRESS/WNWNAW: PRESS/WNWNAW]
  09:41:45  price 29325.02 (open +1.98 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:41:45  price 29325.02 (open +1.98 R of the book stop): took a part [OB1: OB1]
  09:42:00  price 29341.04 (open +1.71 R of the book stop): state change desk [NORMAL/WNWAAW: NORMAL/WNWAAW]
  09:42:00  price 29341.04 (open +1.71 R of the book stop): state change DEFENDING>FREE [NB: NB]
  09:42:00  price 29341.04 (open +1.71 R of the book stop): moved the stop closer [NB: NB]
  09:42:15  price 29323.24 (open +2.01 R of the book stop): state change FREE>OUT [OB2: OB2]
  09:42:15  price 29323.24 (open +2.01 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29324.08

**NY-OFI (NY AM MF5)** 2025-04-07 10:28:20 ET, SHORT 3 lots at 17478.00, safety stop 17566.75 (1.5 x own stop 59.1667 pts). Result managed +111 pts/lot (+1.87 R, $+6631) ; own bracket result +60 pts (+1.01 R, $+3596). MFE +2.20 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:28:21  price 17470.01 (open +0.14 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  10:29:20  price 17350.20 (open +2.16 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  10:29:20  price 17350.20 (open +2.16 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:29:20  price 17350.20 (open +2.16 R of the book stop): took a part [OB1: OB1]
  10:29:35  price 17395.46 (open +1.40 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:29:35  price 17395.46 (open +1.40 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 17367.42

**NY-NODE (NY AM MF4)** 2025-04-07 10:15:28 ET, LONG 6 lots at 18030.54, safety stop 17896.67 (1.5 x own stop 89.25 pts). Result managed +150 pts/lot (+1.68 R, $+17998) ; own bracket result +30 pts (+0.34 R, $+3588). MFE +1.88 R, MAE -0.11 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:15:29  price 18043.93 (open +0.15 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:16:28  price 18205.92 (open +1.97 R of the book stop): state change desk [PRESS/WNWWAW: PRESS/WNWWAW]
  10:16:28  price 18205.92 (open +1.97 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:16:28  price 18205.92 (open +1.97 R of the book stop): took a part [OB1: OB1]
  10:16:43  price 18160.40 (open +1.46 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:16:43  price 18160.40 (open +1.46 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18180.58

**NY-VALUE (NY AM MF2)** 2025-04-07 10:23:48 ET, SHORT 6 lots at 17549.92, safety stop 17638.92 (1.5 x own stop 59.3333 pts). Result managed +85 pts/lot (+1.43 R, $+10178) ; own bracket result +60 pts (+1.01 R, $+7183). MFE +1.23 R, MAE -1.41 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  10:23:49  price 17502.75 (open +0.80 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  10:24:48  price 17432.44 (open +1.98 R of the book stop): state change desk [PRESS/NNWWWA: PRESS/NNWWWA]
  10:24:48  price 17432.44 (open +1.98 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:24:48  price 17432.44 (open +1.98 R of the book stop): took a part [OB1: OB1]
  10:25:03  price 17479.61 (open +1.19 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  10:25:03  price 17479.61 (open +1.19 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:25:03  price 17479.61 (open +1.19 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 17465.04

**NY-OFI (NY AM MF5)** 2026-06-25 10:15:35 ET, SHORT 3 lots at 29573.50, safety stop 29662.25 (1.5 x own stop 59.1667 pts). Result managed +84 pts/lot (+1.42 R, $+5041) ; own bracket result +60 pts (+1.01 R, $+3596). MFE +1.65 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:15:36  price 29574.39 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:16:35  price 29495.40 (open +1.32 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:16:35  price 29495.40 (open +1.32 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:16:35  price 29495.40 (open +1.32 R of the book stop): took a part [OB1: OB1]
  10:16:50  price 29485.64 (open +1.48 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:16:50  price 29485.64 (open +1.48 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29489.42

**NY-VALUE (NY AM MF2)** 2026-06-29 09:56:09 ET, SHORT 6 lots at 29688.21, safety stop 29777.21 (1.5 x own stop 59.3333 pts). Result managed +80 pts/lot (+1.35 R, $+9578) ; own bracket result +60 pts (+1.01 R, $+7188). MFE +1.60 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:56:10  price 29689.99 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  09:57:09  price 29637.48 (open +0.85 R of the book stop): state change desk [PRESS/NNWNWN: PRESS/NNWNWN]
  09:57:09  price 29637.48 (open +0.85 R of the book stop): state change PROBE>FREE [NB: NB]
  09:57:09  price 29637.48 (open +0.85 R of the book stop): moved the stop closer [NB: NB]
  09:57:24  price 29606.33 (open +1.38 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:57:24  price 29606.33 (open +1.38 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  09:57:24  price 29606.33 (open +1.38 R of the book stop): took a part [OB1: OB1]
  09:57:39  price 29609.89 (open +1.32 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:57:39  price 29609.89 (open +1.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29608.33

**NY-VALUE (NY AM MF2)** 2026-06-09 10:43:46 ET, SHORT 6 lots at 29364.62, safety stop 29453.62 (1.5 x own stop 59.3333 pts). Result managed +77 pts/lot (+1.29 R, $+9183) ; own bracket result +60 pts (+1.01 R, $+7178). MFE +1.54 R, MAE -0.05 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:43:47  price 29362.85 (open +0.03 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  10:44:46  price 29281.86 (open +1.40 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:44:46  price 29281.86 (open +1.40 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:44:46  price 29281.86 (open +1.40 R of the book stop): took a part [OB1: OB1]
  10:45:01  price 29294.32 (open +1.19 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:45:01  price 29294.32 (open +1.19 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29288.04

**NY-OFI (NY AM MF5)** 2025-12-18 09:50:05 ET, LONG 3 lots at 25197.42, safety stop 25108.67 (1.5 x own stop 59.1667 pts). Result managed +76 pts/lot (+1.28 R, $+4531) ; own bracket: not taken (slot effect). MFE +1.47 R, MAE -0.33 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:50:06  price 25189.43 (open -0.14 R of the book stop): state change desk [NORMAL/WNNNN-: NORMAL/WNNNN-]
  09:51:05  price 25179.67 (open -0.30 R of the book stop): state change desk [NORMAL/NNNNN-: NORMAL/NNNNN-]
  09:52:05  price 25213.39 (open +0.27 R of the book stop): state change desk [NORMAL/NNWNN-: NORMAL/NNWNN-]
  09:52:50  price 25226.70 (open +0.49 R of the book stop): state change PROBE>FREE [NB: NB]
  09:52:50  price 25226.70 (open +0.49 R of the book stop): moved the stop closer [NB: NB]
  09:53:05  price 25238.24 (open +0.69 R of the book stop): moved the stop closer [NB: NB]
  09:53:20  price 25246.23 (open +0.83 R of the book stop): state change desk [PRESS/WNWNN-: PRESS/WNWNN-]
  09:53:20  price 25246.23 (open +0.83 R of the book stop): moved the stop closer [NB: NB]
  09:53:35  price 25254.22 (open +0.96 R of the book stop): moved the stop closer [NB: NB]
  09:54:35  price 25255.99 (open +0.99 R of the book stop): moved the stop closer [NB: NB]
  09:54:50  price 25261.32 (open +1.08 R of the book stop): moved the stop closer [NB: NB]
  09:56:05  price 25261.32 (open +1.08 R of the book stop): state change desk [PRESS/WNWWN-: PRESS/WNWWN-]
  09:57:50  price 25269.30 (open +1.22 R of the book stop): moved the stop closer [NB: NB]
  09:58:05  price 25271.08 (open +1.24 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  09:58:05  price 25271.08 (open +1.24 R of the book stop): took a part [OB1: OB1]
  09:58:20  price 25273.74 (open +1.29 R of the book stop): state change desk [PRESS/NNWWN-: PRESS/NNWWN-]
  09:58:20  price 25273.74 (open +1.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:58:20  price 25273.74 (open +1.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25273.00

**NY-OFI (NY AM MF5)** 2026-02-09 09:30:11 ET, SHORT 3 lots at 25044.00, safety stop 25132.75 (1.5 x own stop 59.1667 pts). Result managed +72 pts/lot (+1.22 R, $+4316) ; own bracket result +60 pts (+1.01 R, $+3596). MFE +1.28 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:30:12  price 25031.58 (open +0.21 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:31:11  price 24963.24 (open +1.36 R of the book stop): state change desk [NORMAL/WNWAN-: NORMAL/WNWAN-]
  09:31:11  price 24963.24 (open +1.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:31:11  price 24963.24 (open +1.36 R of the book stop): took a part [OB1: OB1]
  09:31:26  price 24992.53 (open +0.87 R of the book stop): state change desk [NORMAL/WAWAN-: NORMAL/WAWAN-]
  09:31:26  price 24992.53 (open +0.87 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:31:26  price 24992.53 (open +0.87 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24972.00

**NY-OFI (NY AM MF5)** 2025-04-07 09:59:08 ET, LONG 3 lots at 17269.92, safety stop 17181.17 (1.5 x own stop 59.1667 pts). Result managed +71 pts/lot (+1.21 R, $+4281) ; own bracket result +60 pts (+1.02 R, $+3601). MFE +1.41 R, MAE -0.49 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:59:09  price 17271.69 (open +0.03 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  10:00:08  price 17261.04 (open -0.15 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  10:00:23  price 17338.25 (open +1.16 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:00:23  price 17338.25 (open +1.16 R of the book stop): took a part [OB1: OB1]
  10:00:38  price 17352.45 (open +1.40 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:00:38  price 17352.45 (open +1.40 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 17341.33

**NY-VALUE (NY AM MF2)** 2026-06-11 10:57:11 ET, SHORT 6 lots at 28681.54, safety stop 28770.54 (1.5 x own stop 59.3333 pts). Result managed +71 pts/lot (+1.19 R, $+8468) ; own bracket result +60 pts (+1.01 R, $+7198). MFE +1.29 R, MAE -0.26 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:57:12  price 28682.43 (open -0.01 R of the book stop): state change desk [NORMAL/ANNWNW: NORMAL/ANNWNW]
  10:58:11  price 28690.44 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:58:26  price 28680.65 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:58:56  price 28613.01 (open +1.16 R of the book stop): state change PROBE>OUT [DV: DV]
  10:58:56  price 28613.01 (open +1.16 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28610.92

**NY-FIB (NY AM MF1)** 2026-02-20 09:47:47 ET, LONG 6 lots at 24923.67, safety stop 24745.17 (1.5 x own stop 119 pts). Result managed +140 pts/lot (+1.17 R, $+16758) ; own bracket: not taken (slot effect). MFE +1.36 R, MAE -0.56 R, 13 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 14m:W
  09:47:48  price 24918.31 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:48:47  price 24914.74 (open -0.08 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:49:02  price 24911.17 (open -0.11 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  09:50:02  price 24898.68 (open -0.21 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:51:02  price 24879.04 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:51:47  price 24862.98 (open -0.51 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:52:17  price 24868.33 (open -0.46 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:53:02  price 24855.84 (open -0.57 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:56:02  price 24873.69 (open -0.42 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:57:02  price 24870.12 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:59:32  price 24900.46 (open -0.20 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:59:47  price 24898.68 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:00:32  price 24914.74 (open -0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:01:17  price 25020.06 (open +0.81 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  10:01:17  price 25020.06 (open +0.81 R of the book stop): state change PROBE>RUNNER [RT: RT]
  10:01:17  price 25020.06 (open +0.81 R of the book stop): moved the stop closer [RT: RT]
  10:01:32  price 25027.20 (open +0.87 R of the book stop): moved the stop closer [RT: RT]
  10:01:47  price 25055.76 (open +1.11 R of the book stop): state change RUNNER>DEFENDING [OB1: OB1]
  10:01:47  price 25055.76 (open +1.11 R of the book stop): took a part [OB1: OB1]
  10:02:02  price 25073.61 (open +1.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:02:02  price 25073.61 (open +1.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25063.38

**NY-VALUE (NY AM MF2)** 2026-02-02 09:35:38 ET, LONG 6 lots at 25643.33, safety stop 25554.33 (1.5 x own stop 59.3333 pts). Result managed +66 pts/lot (+1.12 R, $+7948) ; own bracket: not taken (slot effect). MFE +1.11 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:35:39  price 25647.78 (open +0.08 R of the book stop): state change desk [PRESS/WNWWNA: PRESS/WNWWNA]
  09:36:38  price 25708.30 (open +1.09 R of the book stop): state change desk [NORMAL/WNNWNA: NORMAL/WNNWNA]
  09:36:38  price 25708.30 (open +1.09 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:36:38  price 25708.30 (open +1.09 R of the book stop): took a part [OB1: OB1]
  09:36:53  price 25710.97 (open +1.14 R of the book stop): state change desk [PRESS/WNWWNA: PRESS/WNWWNA]
  09:36:53  price 25710.97 (open +1.14 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:36:53  price 25710.97 (open +1.14 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25709.62

**NY-OFI (NY AM MF5)** 2026-06-08 09:33:08 ET, SHORT 3 lots at 29492.92, safety stop 29581.67 (1.5 x own stop 59.1667 pts). Result managed +63 pts/lot (+1.06 R, $+3751) ; own bracket result +60 pts (+1.01 R, $+3591). MFE +1.31 R, MAE -0.18 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:33:09  price 29490.25 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:34:08  price 29452.09 (open +0.69 R of the book stop): state change desk [PRESS/NNWWNW: PRESS/NNWWNW]
  09:34:08  price 29452.09 (open +0.69 R of the book stop): state change PROBE>FREE [NB: NB]
  09:34:08  price 29452.09 (open +0.69 R of the book stop): moved the stop closer [NB: NB]
  09:34:23  price 29436.12 (open +0.96 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  09:34:23  price 29436.12 (open +0.96 R of the book stop): took a part [OB1: OB1]
  09:34:38  price 29439.67 (open +0.90 R of the book stop): state change DEFENDING>FREE [NB: NB]
  09:34:38  price 29439.67 (open +0.90 R of the book stop): moved the stop closer [NB: NB]
  09:34:53  price 29423.69 (open +1.17 R of the book stop): state change FREE>OUT [OB2: OB2]
  09:34:53  price 29423.69 (open +1.17 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29430.33

**NY-VALUE (NY AM MF2)** 2025-02-07 10:30:03 ET, SHORT 6 lots at 21733.00, safety stop 21822.00 (1.5 x own stop 59.3333 pts). Result managed +62 pts/lot (+1.05 R, $+7473) ; own bracket result -57 pts (-0.97 R, $-6897). MFE +1.29 R, MAE -1.13 R, 23 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  10:30:04  price 21736.56 (open -0.06 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  10:31:03  price 21752.58 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:32:48  price 21737.45 (open -0.08 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:33:03  price 21743.68 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:34:18  price 21735.67 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:34:33  price 21749.02 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:38:03  price 21790.85 (open -0.98 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:38:18  price 21793.52 (open -1.02 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:40:03  price 21769.49 (open -0.61 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  10:41:03  price 21774.83 (open -0.70 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:42:03  price 21773.05 (open -0.68 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:43:33  price 21759.70 (open -0.45 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:43:48  price 21758.81 (open -0.43 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:44:18  price 21749.91 (open -0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:44:33  price 21751.69 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:45:48  price 21742.79 (open -0.17 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:46:18  price 21749.02 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:50:03  price 21773.05 (open -0.68 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:50:48  price 21785.51 (open -0.89 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:52:03  price 21790.85 (open -0.98 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:53:03  price 21799.75 (open -1.12 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  10:53:18  price 21756.14 (open -0.39 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  10:53:33  price 21668.92 (open +1.08 R of the book stop): state change PROBE>OUT [DV: DV]
  10:53:33  price 21668.92 (open +1.08 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 21670.67

**NY-VALUE (NY AM MF2)** 2026-09-03 09:36:51 ET, LONG 6 lots at 29220.04, safety stop 29131.04 (1.5 x own stop 59.3333 pts). Result managed +62 pts/lot (+1.04 R, $+7423) ; own bracket result +60 pts (+1.01 R, $+7188). MFE +1.28 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:36:52  price 29217.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:37:51  price 29251.19 (open +0.52 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:37:51  price 29251.19 (open +0.52 R of the book stop): state change PROBE>FREE [NB: NB]
  09:37:51  price 29251.19 (open +0.52 R of the book stop): moved the stop closer [NB: NB]
  09:38:06  price 29256.53 (open +0.61 R of the book stop): state change desk [PRESS/NNWWNW: PRESS/NNWWNW]
  09:38:06  price 29256.53 (open +0.61 R of the book stop): moved the stop closer [NB: NB]
  09:38:21  price 29272.55 (open +0.89 R of the book stop): state change desk [PRESS/WNWWNW: PRESS/WNWWNW]
  09:38:21  price 29272.55 (open +0.89 R of the book stop): moved the stop closer [NB: NB]
  09:38:36  price 29278.78 (open +0.99 R of the book stop): moved the stop closer [NB: NB]
  09:38:51  price 29277.00 (open +0.96 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  09:38:51  price 29277.00 (open +0.96 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  09:38:51  price 29277.00 (open +0.96 R of the book stop): took a part [OB1: OB1]
  09:39:06  price 29286.79 (open +1.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:39:06  price 29286.79 (open +1.12 R of the book stop): state change DEFENDING>OUT [DV: DV]
  09:39:06  price 29286.79 (open +1.12 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29281.96

**NY-OFI (NY AM MF5)** 2025-03-06 10:24:03 ET, SHORT 3 lots at 20470.67, safety stop 20559.42 (1.5 x own stop 59.1667 pts). Result managed +58 pts/lot (+0.99 R, $+3501) ; own bracket result +60 pts (+1.01 R, $+3591). MFE +1.16 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:24:04  price 20470.67 (open +0.00 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:25:03  price 20452.92 (open +0.30 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  10:25:48  price 20437.83 (open +0.55 R of the book stop): state change PROBE>FREE [NB: NB]
  10:25:48  price 20437.83 (open +0.55 R of the book stop): moved the stop closer [NB: NB]
  10:26:03  price 20446.70 (open +0.41 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:26:18  price 20440.49 (open +0.51 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  10:26:33  price 20417.42 (open +0.90 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  10:26:33  price 20417.42 (open +0.90 R of the book stop): took a part [OB1: OB1]
  10:26:48  price 20416.53 (open +0.92 R of the book stop): state change DEFENDING>FREE [NB: NB]
  10:26:48  price 20416.53 (open +0.92 R of the book stop): moved the stop closer [NB: NB]
  10:27:03  price 20405.88 (open +1.09 R of the book stop): state change FREE>OUT [OB2: OB2]
  10:27:03  price 20405.88 (open +1.09 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 20412.25

**NY-VALUE (NY AM MF2)** 2026-06-09 10:31:47 ET, LONG 6 lots at 29390.38, safety stop 29301.38 (1.5 x own stop 59.3333 pts). Result managed +57 pts/lot (+0.96 R, $+6818) ; own bracket result +60 pts (+1.01 R, $+7208). MFE +1.19 R, MAE -0.20 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:31:48  price 29393.94 (open +0.06 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:32:47  price 29448.22 (open +0.98 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:32:47  price 29448.22 (open +0.98 R of the book stop): state change PROBE>OUT [DV: DV]
  10:32:47  price 29448.22 (open +0.98 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29447.25

## NY AM: 50 RANDOM trades (seed 11)

**NY-NODE (NY AM MF4)** 2024-10-08 09:40:44 ET, SHORT 6 lots at 20082.71, safety stop 20216.58 (1.5 x own stop 89.25 pts). Result managed -76 pts/lot (-0.85 R, $-9142) ; own bracket result -89 pts (-1.00 R, $-10702). MFE +0.13 R, MAE -1.48 R, 54 min under water (longest 49 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 6m:N 14m:A
  09:40:45  price 20082.71 (open -0.00 R of the book stop): state change desk [NORMAL/WNAWNA: NORMAL/WNAWNA]
  09:41:44  price 20097.43 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  09:43:14  price 20102.79 (open -0.22 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  09:43:14  price 20102.79 (open -0.22 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:43:14  price 20102.79 (open -0.22 R of the book stop): took a part [DF: DF]
  09:43:59  price 20089.40 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:44:14  price 20094.76 (open -0.14 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:44:29  price 20096.10 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:44:44  price 20106.81 (open -0.27 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:45:44  price 20088.06 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:46:44  price 20088.06 (open -0.06 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:46:59  price 20094.76 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:47:14  price 20092.08 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:49:14  price 20090.74 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:49:59  price 20105.47 (open -0.26 R of the book stop): state change desk [NORMAL/ANNWNN: NORMAL/ANNWNN]
  09:50:14  price 20105.47 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:50:29  price 20096.10 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:50:59  price 20104.13 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:51:44  price 20094.76 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:52:14  price 20106.81 (open -0.27 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:53:14  price 20122.87 (open -0.45 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  09:54:14  price 20126.89 (open -0.49 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:55:14  price 20137.60 (open -0.61 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  09:56:14  price 20137.60 (open -0.61 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  09:58:29  price 20149.65 (open -0.75 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  09:59:14  price 20145.63 (open -0.70 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  10:01:14  price 20185.79 (open -1.16 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  10:03:14  price 20189.81 (open -1.20 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  10:05:29  price 20185.79 (open -1.16 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  10:08:14  price 20181.78 (open -1.11 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  10:09:14  price 20189.81 (open -1.20 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:10:14  price 20196.50 (open -1.27 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  10:11:14  price 20180.44 (open -1.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:14:44  price 20177.76 (open -1.06 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:14:59  price 20181.78 (open -1.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:15:14  price 20177.76 (open -1.06 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:15:29  price 20181.78 (open -1.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:15:59  price 20167.05 (open -0.95 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:16:14  price 20173.74 (open -1.02 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:21:44  price 20165.71 (open -0.93 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  exit: ExAlgoAll_AB at 20158.83

**NY-NODE (NY AM MF4)** 2024-12-26 10:06:31 ET, SHORT 6 lots at 21969.96, safety stop 22103.83 (1.5 x own stop 89.25 pts). Result managed +31 pts/lot (+0.34 R, $+3668) ; own bracket result +30 pts (+0.34 R, $+3588). MFE +0.50 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:06:32  price 21972.64 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:07:31  price 21968.62 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:09:01  price 21949.88 (open +0.22 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:09:16  price 21944.52 (open +0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:09:31  price 21943.18 (open +0.30 R of the book stop): state change PROBE>FREE [NB: NB]
  10:09:31  price 21943.18 (open +0.30 R of the book stop): moved the stop closer [NB: NB]
  10:10:01  price 21929.80 (open +0.45 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:12:01  price 21940.51 (open +0.33 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  10:12:46  price 21944.52 (open +0.29 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  10:13:01  price 21943.18 (open +0.30 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:13:16  price 21945.86 (open +0.27 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:15:31  price 21943.18 (open +0.30 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  10:15:31  price 21943.18 (open +0.30 R of the book stop): took a part [OB1: OB1]
  10:16:17  price 21933.81 (open +0.41 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:16:17  price 21933.81 (open +0.41 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21939.33

**NY-OFI (NY AM MF5)** 2025-01-10 11:01:34 ET, SHORT 3 lots at 20955.83, safety stop 21044.58 (1.5 x own stop 59.1667 pts). Result managed +17 pts/lot (+0.28 R, $+991) ; own bracket result +60 pts (+1.02 R, $+3601). MFE +0.36 R, MAE -0.39 R, 5 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N
  11:01:35  price 20957.61 (open -0.03 R of the book stop): state change desk [NORMAL/ANNWNN: NORMAL/ANNWNN]
  11:02:34  price 20960.27 (open -0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:02:49  price 20964.71 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:03:49  price 20959.38 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:04:04  price 20964.71 (open -0.15 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  11:05:04  price 20960.27 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:11:19  price 20938.97 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  11:11:19  price 20938.97 (open +0.29 R of the book stop): took a part [OB1: OB1]
  11:11:34  price 20938.08 (open +0.30 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  11:11:34  price 20938.08 (open +0.30 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 20939.25

**NY-VALUE (NY AM MF2)** 2025-01-30 10:55:22 ET, SHORT 6 lots at 21491.08, safety stop 21580.08 (1.5 x own stop 59.3333 pts). Result managed +33 pts/lot (+0.56 R, $+3983) ; own bracket: not taken (slot effect). MFE +0.80 R, MAE -0.25 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 4m:W
  10:55:23  price 21489.30 (open +0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:56:22  price 21489.30 (open +0.03 R of the book stop): state change desk [PRESS/WNNNWN: PRESS/WNNNWN]
  10:56:37  price 21480.40 (open +0.18 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  10:56:52  price 21480.40 (open +0.18 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:57:07  price 21483.96 (open +0.12 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  10:57:37  price 21493.75 (open -0.04 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:58:07  price 21480.40 (open +0.18 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  10:59:22  price 21468.83 (open +0.38 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:59:22  price 21468.83 (open +0.38 R of the book stop): took a part [OB1: OB1]
  11:00:07  price 21466.16 (open +0.42 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:00:22  price 21477.73 (open +0.22 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:01:52  price 21445.69 (open +0.77 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:01:52  price 21445.69 (open +0.77 R of the book stop): state change DEFENDING>OUT [DV: DV]
  11:01:52  price 21445.69 (open +0.77 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 21457.83

**NY-OFI (NY AM MF5)** 2025-02-25 09:51:28 ET, SHORT 3 lots at 21257.58, safety stop 21346.33 (1.5 x own stop 59.1667 pts). Result managed +30 pts/lot (+0.50 R, $+1771) ; own bracket result +60 pts (+1.02 R, $+3601). MFE +0.71 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:51:29  price 21262.02 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:52:28  price 21228.30 (open +0.49 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  09:52:28  price 21228.30 (open +0.49 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:52:28  price 21228.30 (open +0.49 R of the book stop): took a part [OB1: OB1]
  09:52:43  price 21227.41 (open +0.51 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:52:43  price 21227.41 (open +0.51 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21228.00

**NY-NODE (NY AM MF4)** 2025-04-02 10:17:52 ET, SHORT 6 lots at 19558.92, safety stop 19692.79 (1.5 x own stop 89.25 pts). Result managed -57 pts/lot (-0.64 R, $-6877) ; own bracket: not taken (slot effect). MFE +0.13 R, MAE -0.78 R, 39 min under water (longest 30 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 3m:N 15m:A
  10:17:53  price 19561.59 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  10:18:52  price 19568.29 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:20:37  price 19562.93 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:20:52  price 19577.66 (open -0.21 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:21:22  price 19568.29 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:23:37  price 19585.69 (open -0.30 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:25:52  price 19573.64 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:31:07  price 19591.05 (open -0.36 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:31:22  price 19597.74 (open -0.43 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:31:52  price 19608.45 (open -0.55 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:31:52  price 19608.45 (open -0.55 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:31:52  price 19608.45 (open -0.55 R of the book stop): took a part [DF: DF]
  10:33:07  price 19605.77 (open -0.52 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:33:52  price 19595.06 (open -0.41 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:34:07  price 19599.08 (open -0.45 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:34:22  price 19595.06 (open -0.41 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:39:07  price 19570.97 (open -0.14 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:40:07  price 19584.35 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:47:07  price 19611.13 (open -0.58 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:47:22  price 19605.77 (open -0.52 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:50:07  price 19604.43 (open -0.51 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:51:22  price 19616.48 (open -0.65 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:51:37  price 19611.13 (open -0.58 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:57:08  price 19611.13 (open -0.58 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  10:57:53  price 19620.50 (open -0.69 R of the book stop): state change desk [ABORT/AAANNA: ABORT/AAANNA]
  10:57:53  price 19620.50 (open -0.69 R of the book stop): state change DEFENDING>OUT [AB: AB]
  10:57:53  price 19620.50 (open -0.69 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 19616.17

**NY-FIB (NY AM MF1)** 2025-04-07 10:18:47 ET, SHORT 6 lots at 18073.50, safety stop 18252.00 (1.5 x own stop 119 pts). Result managed +131 pts/lot (+1.10 R, $+15678) ; own bracket: not taken (slot effect). MFE +1.43 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:18:48  price 18059.22 (open +0.12 R of the book stop): state change desk [PRESS/WNWWNW: PRESS/WNWWNW]
  10:19:47  price 17982.47 (open +0.77 R of the book stop): state change desk [NORMAL/NNWAWA: NORMAL/NNWAWA]
  10:19:47  price 17982.47 (open +0.77 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:19:47  price 17982.47 (open +0.77 R of the book stop): took a part [OB1: OB1]
  10:20:02  price 17977.11 (open +0.81 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  10:20:02  price 17977.11 (open +0.81 R of the book stop): state change DEFENDING>FREE [NB: NB]
  10:20:02  price 17977.11 (open +0.81 R of the book stop): moved the stop closer [NB: NB]
  10:20:17  price 17907.49 (open +1.40 R of the book stop): state change desk [NORMAL/NNWAWA: NORMAL/NNWAWA]
  10:20:17  price 17907.49 (open +1.40 R of the book stop): state change FREE>OUT [OB2: OB2]
  10:20:17  price 17907.49 (open +1.40 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 17942.79

**NY-FIB (NY AM MF1)** 2025-04-11 10:21:51 ET, SHORT 6 lots at 18363.17, safety stop 18541.67 (1.5 x own stop 119 pts). Result managed +39 pts/lot (+0.33 R, $+4698) ; own bracket result -114 pts (-0.96 R, $-13687). MFE +0.46 R, MAE -0.11 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:21:52  price 18366.74 (open -0.03 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:22:51  price 18327.47 (open +0.30 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  10:22:51  price 18327.47 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:22:51  price 18327.47 (open +0.30 R of the book stop): took a part [OB1: OB1]
  10:23:06  price 18325.68 (open +0.32 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:23:06  price 18325.68 (open +0.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18323.96

**NY-NODE (NY AM MF4)** 2025-04-30 11:24:33 ET, LONG 6 lots at 19412.42, safety stop 19278.54 (1.5 x own stop 89.25 pts). Result managed +25 pts/lot (+0.28 R, $+2943) ; own bracket result +30 pts (+0.34 R, $+3603). MFE +0.39 R, MAE -0.40 R, 13 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 5m:N 12m:W 17m:N 20m:W
  11:24:34  price 19413.76 (open +0.01 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  11:25:33  price 19381.63 (open -0.35 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:28:03  price 19397.69 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:29:03  price 19421.79 (open +0.11 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  11:31:03  price 19417.77 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:32:18  price 19423.13 (open +0.12 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:32:33  price 19421.79 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:43:03  price 19405.72 (open -0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:44:18  price 19440.53 (open +0.32 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  11:44:18  price 19440.53 (open +0.32 R of the book stop): took a part [OB1: OB1]
  11:44:33  price 19435.18 (open +0.26 R of the book stop): state change DEFENDING>FREE [NB: NB]
  11:44:33  price 19435.18 (open +0.26 R of the book stop): moved the stop closer [NB: NB]
  11:46:48  price 19432.50 (open +0.22 R of the book stop): state change FREE>OUT [OB2: OB2]
  11:46:48  price 19432.50 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19437.00

**NY-OFI (NY AM MF5)** 2025-05-05 09:40:18 ET, SHORT 3 lots at 20005.17, safety stop 20093.92 (1.5 x own stop 59.1667 pts). Result managed -54 pts/lot (-0.91 R, $-3249) ; own bracket result -60 pts (-1.01 R, $-3579). MFE +0.41 R, MAE -1.46 R, 17 min under water (longest 17 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 9m:A
  09:40:19  price 20008.72 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:41:18  price 19998.07 (open +0.12 R of the book stop): state change desk [NORMAL/WNWANN: NORMAL/WNWANN]
  09:41:33  price 20009.60 (open -0.08 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  09:41:48  price 20001.62 (open +0.06 R of the book stop): state change desk [NORMAL/WNWANN: NORMAL/WNWANN]
  09:42:03  price 19998.07 (open +0.12 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  09:42:33  price 19994.52 (open +0.18 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  09:42:48  price 20002.50 (open +0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:43:03  price 20009.60 (open -0.08 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:43:48  price 20030.02 (open -0.42 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  09:44:03  price 20037.12 (open -0.54 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  09:44:33  price 20032.68 (open -0.46 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:45:03  price 20041.55 (open -0.61 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  09:45:48  price 20040.67 (open -0.60 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:46:03  price 20037.12 (open -0.54 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:46:18  price 20030.90 (open -0.43 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  09:46:33  price 20041.55 (open -0.61 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:46:48  price 20041.55 (open -0.61 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  09:47:03  price 20043.33 (open -0.65 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:48:03  price 20040.67 (open -0.60 R of the book stop): state change desk [NORMAL/NNWANN: NORMAL/NNWANN]
  09:49:03  price 20038.89 (open -0.57 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:49:33  price 20058.42 (open -0.90 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  09:49:33  price 20058.42 (open -0.90 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:49:33  price 20058.42 (open -0.90 R of the book stop): took a part [DF: DF]
  09:49:48  price 20045.99 (open -0.69 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:51:03  price 20022.03 (open -0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:51:18  price 20026.47 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:52:03  price 20017.59 (open -0.21 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  09:52:33  price 20026.47 (open -0.36 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:52:48  price 20016.70 (open -0.20 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  09:53:03  price 20024.69 (open -0.33 R of the book stop): state change desk [PRESS/NNWNWN: PRESS/NNWNWN]
  09:53:18  price 20014.93 (open -0.17 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  09:53:33  price 20022.92 (open -0.30 R of the book stop): state change desk [PRESS/NNWNWN: PRESS/NNWNWN]
  09:54:03  price 20021.14 (open -0.27 R of the book stop): state change desk [PRESS/NNWWWW: PRESS/NNWWWW]
  09:54:18  price 20016.70 (open -0.20 R of the book stop): state change desk [PRESS/WNWWNW: PRESS/WNWWNW]
  09:54:33  price 20031.79 (open -0.45 R of the book stop): state change desk [PRESS/NNWWNW: PRESS/NNWWNW]
  09:55:03  price 20041.55 (open -0.61 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  09:55:18  price 20037.12 (open -0.54 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:56:03  price 20048.65 (open -0.73 R of the book stop): state change desk [NORMAL/ANNWNW: NORMAL/ANNWNW]
  09:56:33  price 20043.33 (open -0.65 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  09:56:48  price 20049.54 (open -0.75 R of the book stop): state change desk [NORMAL/ANNWNW: NORMAL/ANNWNW]
  exit: Stop at 20059.25

**NY-NODE (NY AM MF4)** 2025-05-15 09:53:40 ET, LONG 6 lots at 21288.00, safety stop 21154.12 (1.5 x own stop 89.25 pts). Result managed +33 pts/lot (+0.37 R, $+3963) ; own bracket: not taken (slot effect). MFE +0.55 R, MAE -0.09 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:53:41  price 21286.66 (open -0.01 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  09:54:40  price 21302.73 (open +0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:56:10  price 21285.32 (open -0.03 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:56:55  price 21300.05 (open +0.14 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  09:57:10  price 21298.71 (open +0.12 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:57:55  price 21281.31 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:58:10  price 21285.32 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:59:10  price 21289.34 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:59:40  price 21298.71 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:00:10  price 21301.39 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:00:55  price 21316.11 (open +0.32 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:00:55  price 21316.11 (open +0.32 R of the book stop): took a part [OB1: OB1]
  10:01:10  price 21322.81 (open +0.39 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:01:10  price 21322.81 (open +0.39 R of the book stop): state change DEFENDING>FREE [NB: NB]
  10:01:10  price 21322.81 (open +0.39 R of the book stop): moved the stop closer [NB: NB]
  10:01:25  price 21328.16 (open +0.45 R of the book stop): state change FREE>OUT [OB2: OB2]
  10:01:25  price 21328.16 (open +0.45 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21321.08

**NY-FIB (NY AM MF1)** 2025-05-22 09:36:28 ET, LONG 6 lots at 21164.21, safety stop 20985.71 (1.5 x own stop 119 pts). Result managed +29 pts/lot (+0.24 R, $+3443) ; own bracket result +120 pts (+1.01 R, $+14398). MFE +0.29 R, MAE -0.26 R, 4 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 4m:A
  09:36:29  price 21167.78 (open +0.03 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:37:28  price 21149.93 (open -0.12 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:38:13  price 21153.50 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:39:13  price 21144.57 (open -0.17 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:40:13  price 21160.64 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:41:43  price 21185.63 (open +0.18 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:41:58  price 21196.34 (open +0.27 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  09:41:58  price 21196.34 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:41:58  price 21196.34 (open +0.27 R of the book stop): took a part [OB1: OB1]
  09:42:13  price 21189.20 (open +0.21 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  09:42:13  price 21189.20 (open +0.21 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:42:13  price 21189.20 (open +0.21 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21192.96

**NY-NODE (NY AM MF4)** 2025-07-02 11:30:27 ET, SHORT 6 lots at 22810.12, safety stop 22944.00 (1.5 x own stop 89.25 pts). Result managed -8 pts/lot (-0.09 R, $-1007) ; own bracket: not taken (slot effect). MFE +0.07 R, MAE -0.18 R, 9 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:30:28  price 22811.46 (open -0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  11:31:27  price 22812.80 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  11:32:12  price 22818.16 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:34:12  price 22816.82 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:34:42  price 22818.16 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:35:12  price 22820.83 (open -0.12 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  11:35:27  price 22820.83 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:37:28  price 22824.85 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  11:37:43  price 22826.19 (open -0.18 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  11:37:43  price 22826.19 (open -0.18 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  11:37:43  price 22826.19 (open -0.18 R of the book stop): took a part [DF: DF]
  11:37:58  price 22824.85 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  11:38:13  price 22819.50 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:42:28  price 22810.12 (open +0.00 R of the book stop): state change DEFENDING>OUT [CL: CL]
  11:42:28  price 22810.12 (open +0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 22818.46

**NY-VALUE (NY AM MF2)** 2025-07-10 09:33:43 ET, SHORT 6 lots at 23032.92, safety stop 23121.92 (1.5 x own stop 59.3333 pts). Result managed +23 pts/lot (+0.38 R, $+2703) ; own bracket result +60 pts (+1.01 R, $+7183). MFE +0.45 R, MAE -0.22 R, 9 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A 15m:N
  09:33:44  price 23029.36 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:34:43  price 23024.02 (open +0.15 R of the book stop): state change desk [PRESS/WNWWNA: PRESS/WNWWNA]
  09:34:58  price 23031.14 (open +0.03 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:35:43  price 23036.48 (open -0.06 R of the book stop): state change desk [NORMAL/NAAWNN: NORMAL/NAAWNN]
  09:35:58  price 23038.26 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:37:13  price 23037.37 (open -0.08 R of the book stop): state change desk [NORMAL/NNAWNA: NORMAL/NNAWNA]
  09:37:28  price 23038.26 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:37:43  price 23037.37 (open -0.08 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:37:58  price 23037.37 (open -0.08 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  09:38:13  price 23030.25 (open +0.04 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:39:28  price 23039.15 (open -0.11 R of the book stop): state change desk [NORMAL/ANNWNN: NORMAL/ANNWNN]
  09:39:43  price 23038.26 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:40:13  price 23036.48 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:41:13  price 23032.92 (open -0.00 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:41:28  price 23033.81 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:41:43  price 23028.47 (open +0.08 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:41:58  price 23026.69 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:44:13  price 23032.03 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:45:13  price 23029.36 (open +0.06 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:45:43  price 23020.46 (open +0.21 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  09:46:13  price 23024.02 (open +0.15 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:47:13  price 23024.02 (open +0.15 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:47:28  price 23025.80 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:48:28  price 23018.68 (open +0.24 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:48:43  price 23015.12 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:48:43  price 23015.12 (open +0.30 R of the book stop): took a part [OB1: OB1]
  09:48:58  price 23005.33 (open +0.46 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:48:58  price 23005.33 (open +0.46 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23010.33

**NY-VALUE (NY AM MF2)** 2025-07-10 09:50:02 ET, SHORT 6 lots at 22991.92, safety stop 23080.92 (1.5 x own stop 59.3333 pts). Result managed +13 pts/lot (+0.22 R, $+1538) ; own bracket: not taken (slot effect). MFE +0.35 R, MAE -0.36 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 4m:W
  09:50:03  price 22989.25 (open +0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  09:51:02  price 23005.27 (open -0.22 R of the book stop): state change desk [PRESS/WNNWAW: PRESS/WNNWAW]
  09:51:17  price 23007.05 (open -0.26 R of the book stop): state change desk [NORMAL/WNAWAW: NORMAL/WNAWAW]
  09:51:47  price 23007.94 (open -0.27 R of the book stop): state change desk [NORMAL/NNAWAW: NORMAL/NNAWAW]
  09:52:02  price 23004.38 (open -0.21 R of the book stop): state change desk [NORMAL/WNAWAW: NORMAL/WNAWAW]
  09:52:47  price 22991.92 (open -0.00 R of the book stop): state change desk [PRESS/WNNWAW: PRESS/WNNWAW]
  09:53:02  price 22982.13 (open +0.17 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:53:17  price 22975.01 (open +0.29 R of the book stop): state change desk [NORMAL/WNNNAW: NORMAL/WNNNAW]
  09:54:02  price 22984.80 (open +0.12 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  09:54:32  price 22978.57 (open +0.22 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:54:32  price 22978.57 (open +0.22 R of the book stop): took a part [OB1: OB1]
  09:54:47  price 22979.46 (open +0.21 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:54:47  price 22979.46 (open +0.21 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 22979.04

**NY-FIB (NY AM MF1)** 2025-07-16 09:36:01 ET, SHORT 6 lots at 23036.62, safety stop 23215.12 (1.5 x own stop 119 pts). Result managed +15 pts/lot (+0.13 R, $+1838) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -0.08 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  09:36:02  price 23040.19 (open -0.03 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  09:37:01  price 23043.76 (open -0.06 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:38:01  price 23025.92 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:38:46  price 23034.84 (open +0.01 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  09:39:01  price 23034.84 (open +0.01 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  09:39:01  price 23034.84 (open +0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:39:01  price 23034.84 (open +0.01 R of the book stop): took a part [DF: DF]
  09:39:31  price 23038.41 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:39:46  price 23043.76 (open -0.06 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:40:16  price 23034.84 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:41:01  price 23022.35 (open +0.12 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  09:42:01  price 23016.99 (open +0.17 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:45:16  price 23004.49 (open +0.27 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  09:45:16  price 23004.49 (open +0.27 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  09:45:16  price 23004.49 (open +0.27 R of the book stop): moved the stop closer [OB1: OB1]
  09:45:31  price 23006.28 (open +0.26 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  09:45:31  price 23006.28 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23021.25

**NY-VALUE (NY AM MF2)** 2025-07-16 11:16:15 ET, SHORT 6 lots at 23001.08, safety stop 23090.08 (1.5 x own stop 59.3333 pts). Result managed +30 pts/lot (+0.51 R, $+3633) ; own bracket: not taken (slot effect). MFE +0.76 R, MAE -0.21 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  11:16:16  price 22990.40 (open +0.18 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:17:15  price 22955.69 (open +0.77 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  11:17:15  price 22955.69 (open +0.77 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  11:17:15  price 22955.69 (open +0.77 R of the book stop): took a part [OB1: OB1]
  11:17:30  price 22986.84 (open +0.24 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  11:17:30  price 22986.84 (open +0.24 R of the book stop): state change DEFENDING>FREE [NB: NB]
  11:17:30  price 22986.84 (open +0.24 R of the book stop): moved the stop closer [NB: NB]
  exit: ExAlgoStop_NB at 22970.75

**NY-NODE (NY AM MF4)** 2025-07-31 11:16:01 ET, SHORT 6 lots at 23495.29, safety stop 23629.17 (1.5 x own stop 89.25 pts). Result managed -75 pts/lot (-0.84 R, $-8972) ; own bracket result -88 pts (-0.98 R, $-10512). MFE +0.18 R, MAE -0.96 R, 40 min under water (longest 34 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 9m:N 17m:A
  11:16:02  price 23499.31 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:17:01  price 23488.60 (open +0.08 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  11:17:16  price 23495.29 (open +0.00 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:18:46  price 23508.68 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:24:01  price 23499.31 (open -0.04 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  11:25:01  price 23496.63 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:26:16  price 23500.65 (open -0.06 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:26:31  price 23510.02 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:29:01  price 23534.12 (open -0.43 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:31:01  price 23538.13 (open -0.48 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  11:33:01  price 23556.87 (open -0.69 R of the book stop): state change desk [DEFEND/ANAANW: DEFEND/ANAANW]
  11:33:01  price 23556.87 (open -0.69 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  11:33:01  price 23556.87 (open -0.69 R of the book stop): took a part [DF: DF]
  11:33:16  price 23552.86 (open -0.65 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  11:35:01  price 23546.16 (open -0.57 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  11:36:01  price 23552.86 (open -0.65 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:36:46  price 23560.89 (open -0.73 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:37:01  price 23554.20 (open -0.66 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:39:46  price 23570.26 (open -0.84 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  11:40:16  price 23572.94 (open -0.87 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:42:46  price 23570.26 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:43:01  price 23570.26 (open -0.84 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:47:46  price 23570.26 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:48:16  price 23574.28 (open -0.89 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:48:31  price 23572.94 (open -0.87 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:49:01  price 23576.96 (open -0.92 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:49:16  price 23571.60 (open -0.85 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:49:31  price 23571.60 (open -0.85 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:49:46  price 23566.25 (open -0.80 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:50:16  price 23567.58 (open -0.81 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:50:31  price 23559.55 (open -0.72 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:51:16  price 23564.91 (open -0.78 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  11:55:01  price 23566.25 (open -0.80 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  11:56:01  price 23567.58 (open -0.81 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:57:46  price 23576.96 (open -0.92 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  exit: UWTime at 23570.00

**NY-OFI (NY AM MF5)** 2025-08-01 09:48:44 ET, SHORT 3 lots at 22888.67, safety stop 22977.42 (1.5 x own stop 59.1667 pts). Result managed +18 pts/lot (+0.30 R, $+1051) ; own bracket result +60 pts (+1.01 R, $+3591). MFE +0.29 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:48:45  price 22882.45 (open +0.11 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  09:49:44  price 22872.69 (open +0.27 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:49:59  price 22868.25 (open +0.35 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:49:59  price 22868.25 (open +0.35 R of the book stop): took a part [OB1: OB1]
  09:50:14  price 22875.35 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:50:14  price 22875.35 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 22871.08

**NY-VALUE (NY AM MF2)** 2025-08-14 09:55:12 ET, SHORT 6 lots at 23917.92, safety stop 24006.92 (1.5 x own stop 59.3333 pts). Result managed -27 pts/lot (-0.45 R, $-3197) ; own bracket: not taken (slot effect). MFE +0.47 R, MAE -1.55 R, 84 min under water (longest 67 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:N 11m:A
  09:55:13  price 23915.25 (open +0.04 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  09:56:12  price 23903.68 (open +0.24 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:59:42  price 23934.83 (open -0.29 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:00:12  price 23935.72 (open -0.30 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  10:00:27  price 23931.27 (open -0.22 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  10:00:42  price 23935.72 (open -0.30 R of the book stop): state change desk [NORMAL/ANNWNW: NORMAL/ANNWNW]
  10:01:12  price 23935.72 (open -0.30 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:01:27  price 23933.94 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:02:12  price 23925.93 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:07:29  price 23931.27 (open -0.22 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:07:44  price 23929.49 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:08:14  price 23928.60 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:08:29  price 23934.83 (open -0.29 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:08:44  price 23929.49 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:15:44  price 23924.15 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:16:29  price 23923.26 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:16:44  price 23925.93 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:16:59  price 23922.37 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:17:14  price 23924.15 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  10:22:14  price 23936.61 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:23:14  price 23940.17 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:27:14  price 23942.84 (open -0.42 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:29:14  price 23954.41 (open -0.61 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:30:29  price 23956.19 (open -0.65 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:30:44  price 23954.41 (open -0.61 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:30:59  price 23961.53 (open -0.73 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:34:14  price 23972.21 (open -0.92 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:39:59  price 23982.89 (open -1.09 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:40:44  price 23978.44 (open -1.02 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:41:29  price 23980.22 (open -1.05 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:41:44  price 23974.88 (open -0.96 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:46:14  price 23987.34 (open -1.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:47:14  price 23995.35 (open -1.30 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  10:47:14  price 23995.35 (open -1.30 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:47:14  price 23995.35 (open -1.30 R of the book stop): took a part [DF: DF]
  10:51:14  price 23987.34 (open -1.17 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:51:44  price 23982.00 (open -1.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:52:44  price 23987.34 (open -1.17 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:53:14  price 23987.34 (open -1.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:53:44  price 23985.56 (open -1.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  exit: ExAlgoAll_OB2 at 23944.50

**NY-OFI (NY AM MF5)** 2025-08-20 10:03:53 ET, SHORT 3 lots at 23196.50, safety stop 23285.25 (1.5 x own stop 59.1667 pts). Result managed +30 pts/lot (+0.50 R, $+1771) ; own bracket result +60 pts (+1.01 R, $+3596). MFE +0.79 R, MAE -0.15 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:03:54  price 23194.72 (open +0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:04:53  price 23175.20 (open +0.36 R of the book stop): state change desk [NORMAL/NNNAAW: NORMAL/NNNAAW]
  10:04:53  price 23175.20 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:04:53  price 23175.20 (open +0.36 R of the book stop): took a part [OB1: OB1]
  10:05:08  price 23174.31 (open +0.38 R of the book stop): state change desk [NORMAL/NNWANW: NORMAL/NNWANW]
  10:05:23  price 23153.90 (open +0.72 R of the book stop): state change desk [PRESS/WNWANW: PRESS/WNWANW]
  10:05:23  price 23153.90 (open +0.72 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:05:23  price 23153.90 (open +0.72 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23166.92

**NY-OFI (NY AM MF5)** 2025-10-30 09:50:35 ET, LONG 3 lots at 26095.42, safety stop 26006.67 (1.5 x own stop 59.1667 pts). Result managed +16 pts/lot (+0.27 R, $+966) ; own bracket result +60 pts (+1.02 R, $+3601). MFE +0.44 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:50:36  price 26093.64 (open -0.03 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  09:51:35  price 26106.07 (open +0.18 R of the book stop): state change desk [NORMAL/NNNWAA: NORMAL/NNNWAA]
  09:51:50  price 26100.74 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:52:35  price 26109.62 (open +0.24 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  09:52:35  price 26109.62 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:52:35  price 26109.62 (open +0.24 R of the book stop): took a part [OB1: OB1]
  09:52:50  price 26116.72 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:52:50  price 26116.72 (open +0.36 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 26111.58

**NY-NODE (NY AM MF4)** 2025-12-05 09:30:59 ET, LONG 6 lots at 25727.96, safety stop 25594.08 (1.5 x own stop 89.25 pts). Result managed +35 pts/lot (+0.39 R, $+4198) ; own bracket result +30 pts (+0.34 R, $+3598). MFE +0.46 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:31:00  price 25733.31 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:31:59  price 25762.77 (open +0.39 R of the book stop): state change desk [PRESS/WNWWN-: PRESS/WNWWN-]
  09:31:59  price 25762.77 (open +0.39 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:31:59  price 25762.77 (open +0.39 R of the book stop): took a part [OB1: OB1]
  09:32:14  price 25765.44 (open +0.42 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:32:14  price 25765.44 (open +0.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25763.00

**NY-VALUE (NY AM MF2)** 2026-01-06 11:07:43 ET, SHORT 6 lots at 25646.29, safety stop 25735.29 (1.5 x own stop 59.3333 pts). Result managed -49 pts/lot (-0.82 R, $-5837) ; own bracket result -59 pts (-1.00 R, $-7097). MFE +0.01 R, MAE -1.05 R, 52 min under water (longest 52 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:07:44  price 25644.51 (open +0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:08:43  price 25656.08 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:22:43  price 25686.34 (open -0.68 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:23:13  price 25693.46 (open -0.80 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:23:43  price 25694.35 (open -0.81 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:24:43  price 25698.80 (open -0.89 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:44:14  price 25661.42 (open -0.26 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:45:44  price 25667.65 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:50:30  price 25695.24 (open -0.83 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:52:00  price 25693.46 (open -0.80 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:52:30  price 25698.80 (open -0.89 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:53:00  price 25696.13 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:53:15  price 25696.13 (open -0.84 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:54:15  price 25696.13 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:54:30  price 25698.80 (open -0.89 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  11:54:45  price 25694.35 (open -0.81 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  11:55:30  price 25671.21 (open -0.42 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:56:00  price 25670.32 (open -0.41 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  exit: UWTime at 25694.88

**NY-OFI (NY AM MF5)** 2026-01-14 10:20:58 ET, LONG 3 lots at 25659.75, safety stop 25571.00 (1.5 x own stop 59.1667 pts). Result managed +18 pts/lot (+0.30 R, $+1071) ; own bracket result -59 pts (-1.00 R, $-3559). MFE +0.46 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:20:59  price 25659.75 (open +0.00 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  10:21:58  price 25671.29 (open +0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:22:13  price 25682.83 (open +0.39 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:22:13  price 25682.83 (open +0.39 R of the book stop): took a part [OB1: OB1]
  10:22:28  price 25669.51 (open +0.17 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:22:28  price 25669.51 (open +0.17 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25677.67

**NY-VALUE (NY AM MF2)** 2026-01-29 10:33:04 ET, SHORT 6 lots at 25687.92, safety stop 25776.92 (1.5 x own stop 59.3333 pts). Result managed +19 pts/lot (+0.32 R, $+2293) ; own bracket result +60 pts (+1.01 R, $+7183). MFE +0.49 R, MAE -0.33 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:N
  10:33:05  price 25690.59 (open -0.04 R of the book stop): state change desk [DEFEND/AAAANW: DEFEND/AAAANW]
  10:34:04  price 25688.81 (open -0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  10:34:19  price 25705.72 (open -0.30 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  10:34:34  price 25700.38 (open -0.21 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  10:35:04  price 25693.26 (open -0.09 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  10:35:34  price 25688.81 (open -0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  10:36:04  price 25688.81 (open -0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:36:34  price 25666.56 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:36:34  price 25666.56 (open +0.36 R of the book stop): took a part [OB1: OB1]
  10:36:49  price 25672.79 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:36:49  price 25672.79 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25668.75

**NY-FIB (NY AM MF1)** 2026-02-09 09:34:17 ET, LONG 6 lots at 25048.58, safety stop 24870.08 (1.5 x own stop 119 pts). Result managed +20 pts/lot (+0.17 R, $+2453) ; own bracket result +120 pts (+1.01 R, $+14383). MFE +0.38 R, MAE -0.29 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:34:18  price 25046.80 (open -0.01 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  09:35:17  price 25028.95 (open -0.17 R of the book stop): state change desk [NORMAL/NNWANN: NORMAL/NNWANN]
  09:35:32  price 25025.38 (open -0.20 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:36:02  price 25048.58 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:36:47  price 25034.30 (open -0.12 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  09:37:02  price 25050.37 (open +0.01 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  09:37:02  price 25050.37 (open +0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:37:02  price 25050.37 (open +0.01 R of the book stop): took a part [DF: DF]
  09:37:17  price 25071.79 (open +0.20 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:38:02  price 25082.50 (open +0.29 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  09:38:02  price 25082.50 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  09:38:02  price 25082.50 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  09:38:17  price 25086.07 (open +0.32 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  09:38:17  price 25086.07 (open +0.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25069.08

**NY-NODE (NY AM MF4)** 2026-02-10 09:30:08 ET, SHORT 6 lots at 25365.25, safety stop 25499.12 (1.5 x own stop 89.25 pts). Result managed +11 pts/lot (+0.12 R, $+1328) ; own bracket result +30 pts (+0.34 R, $+3593). MFE +0.92 R, MAE -0.32 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:30:09  price 25381.31 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:31:08  price 25402.74 (open -0.42 R of the book stop): state change desk [DEFEND/NAANN-: DEFEND/NAANN-]
  09:31:08  price 25402.74 (open -0.42 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:31:08  price 25402.74 (open -0.42 R of the book stop): took a part [DF: DF]
  09:31:23  price 25379.98 (open -0.17 R of the book stop): state change desk [NORMAL/NNANN-: NORMAL/NNANN-]
  09:31:38  price 25366.59 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNN-: NORMAL/NNNNN-]
  09:32:08  price 25375.96 (open -0.12 R of the book stop): state change desk [NORMAL/NNANN-: NORMAL/NNANN-]
  09:32:23  price 25369.27 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNN-: NORMAL/NNNNN-]
  09:32:53  price 25386.67 (open -0.24 R of the book stop): state change desk [NORMAL/NNANN-: NORMAL/NNANN-]
  09:33:08  price 25379.98 (open -0.17 R of the book stop): state change desk [NORMAL/NNNWN-: NORMAL/NNNWN-]
  09:34:08  price 25370.60 (open -0.06 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:34:38  price 25358.56 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:34:53  price 25353.20 (open +0.14 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  09:35:08  price 25363.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:35:23  price 25367.93 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:35:38  price 25366.59 (open -0.01 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  09:36:08  price 25365.25 (open +0.00 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  09:36:23  price 25350.52 (open +0.17 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  09:36:23  price 25350.52 (open +0.17 R of the book stop): moved the stop closer [OB1: OB1]
  09:36:53  price 25327.76 (open +0.42 R of the book stop): state change desk [PRESS/WNAWNW: PRESS/WNAWNW]
  09:36:53  price 25327.76 (open +0.42 R of the book stop): state change RUNNER>FREE [NB: NB]
  09:36:53  price 25327.76 (open +0.42 R of the book stop): moved the stop closer [NB: NB]
  09:37:08  price 25321.07 (open +0.49 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:37:08  price 25321.07 (open +0.49 R of the book stop): moved the stop closer [NB: NB]
  09:37:23  price 25318.39 (open +0.52 R of the book stop): state change desk [PRESS/WNAWNW: PRESS/WNAWNW]
  09:37:23  price 25318.39 (open +0.52 R of the book stop): moved the stop closer [NB: NB]
  09:37:53  price 25310.36 (open +0.61 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:37:53  price 25310.36 (open +0.61 R of the book stop): moved the stop closer [NB: NB]
  09:38:08  price 25300.99 (open +0.72 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:38:08  price 25300.99 (open +0.72 R of the book stop): state change FREE>OUT [DV: DV]
  09:38:08  price 25300.99 (open +0.72 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 25354.12

**NY-NODE (NY AM MF4)** 2026-02-23 09:55:42 ET, SHORT 6 lots at 24914.54, safety stop 25048.42 (1.5 x own stop 89.25 pts). Result managed +46 pts/lot (+0.52 R, $+5528) ; own bracket: not taken (slot effect). MFE +0.52 R, MAE -0.48 R, 7 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 4m:N 5m:W
  09:55:43  price 24909.19 (open +0.06 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  09:56:42  price 24913.20 (open +0.01 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:57:12  price 24930.61 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:57:57  price 24922.57 (open -0.09 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:59:12  price 24910.53 (open +0.04 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  10:00:12  price 24898.48 (open +0.18 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  10:04:27  price 24871.70 (open +0.48 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  10:04:27  price 24871.70 (open +0.48 R of the book stop): state change PROBE>FREE [NB: NB]
  10:04:27  price 24871.70 (open +0.48 R of the book stop): moved the stop closer [NB: NB]
  10:04:42  price 24869.02 (open +0.51 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  10:04:42  price 24869.02 (open +0.51 R of the book stop): took a part [OB1: OB1]
  10:04:57  price 24867.69 (open +0.52 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:04:57  price 24867.69 (open +0.52 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24868.42

**NY-OFI (NY AM MF5)** 2026-02-26 11:12:14 ET, LONG 3 lots at 25042.42, safety stop 24953.67 (1.5 x own stop 59.1667 pts). Result managed +19 pts/lot (+0.33 R, $+1151) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.36 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  11:12:15  price 25044.19 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  11:15:44  price 25061.94 (open +0.33 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  11:15:44  price 25061.94 (open +0.33 R of the book stop): took a part [OB1: OB1]
  11:15:59  price 25061.94 (open +0.33 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  11:15:59  price 25061.94 (open +0.33 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25061.67

**NY-VALUE (NY AM MF2)** 2026-03-02 09:34:32 ET, LONG 6 lots at 24823.88, safety stop 24734.88 (1.5 x own stop 59.3333 pts). Result managed +26 pts/lot (+0.43 R, $+3053) ; own bracket result +60 pts (+1.01 R, $+7208). MFE +0.51 R, MAE -0.10 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:35:32  price 24834.56 (open +0.18 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  09:36:02  price 24851.47 (open +0.46 R of the book stop): state change desk [PRESS/WNWWNW: PRESS/WNWWNW]
  09:36:02  price 24851.47 (open +0.46 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:36:02  price 24851.47 (open +0.46 R of the book stop): took a part [OB1: OB1]
  09:36:17  price 24847.01 (open +0.39 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:36:17  price 24847.01 (open +0.39 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24849.38

**NY-FIB (NY AM MF1)** 2026-03-12 09:35:04 ET, LONG 6 lots at 24809.33, safety stop 24630.83 (1.5 x own stop 119 pts). Result managed -39 pts/lot (-0.33 R, $-4732) ; own bracket: not taken (slot effect). MFE +0.18 R, MAE -0.54 R, 6 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 4m:W 5m:N
  09:35:05  price 24812.90 (open +0.03 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  09:36:04  price 24821.83 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:36:34  price 24816.47 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:37:04  price 24802.19 (open -0.06 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  09:37:19  price 24818.26 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  09:38:19  price 24827.18 (open +0.15 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  09:38:49  price 24827.18 (open +0.15 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  09:39:04  price 24807.55 (open -0.01 R of the book stop): state change desk [PRESS/NNWWNW: PRESS/NNWWNW]
  09:40:04  price 24805.76 (open -0.03 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  09:41:04  price 24811.12 (open +0.01 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  09:42:04  price 24786.13 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:42:19  price 24791.48 (open -0.15 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:42:19  price 24791.48 (open -0.15 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:42:19  price 24791.48 (open -0.15 R of the book stop): took a part [DF: DF]
  09:42:49  price 24786.13 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:43:04  price 24773.63 (open -0.30 R of the book stop): state change desk [NORMAL/ANWNNA: NORMAL/ANWNNA]
  09:44:34  price 24766.49 (open -0.36 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:45:04  price 24754.00 (open -0.46 R of the book stop): state change desk [ABORT/AANANA: ABORT/AANANA]
  09:45:04  price 24754.00 (open -0.46 R of the book stop): state change DEFENDING>OUT [AB: AB]
  09:45:04  price 24754.00 (open -0.46 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 24769.96

**NY-FIB (NY AM MF1)** 2026-03-13 10:42:53 ET, SHORT 6 lots at 24624.75, safety stop 24803.25 (1.5 x own stop 119 pts). Result managed +37 pts/lot (+0.31 R, $+4388) ; own bracket: not taken (slot effect). MFE +0.35 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:42:54  price 24628.32 (open -0.03 R of the book stop): state change desk [NORMAL/NNWNAW: NORMAL/NNWNAW]
  10:43:53  price 24617.61 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:44:23  price 24606.90 (open +0.15 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  10:44:38  price 24608.69 (open +0.14 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:44:53  price 24601.54 (open +0.20 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  10:45:08  price 24589.05 (open +0.30 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:45:08  price 24589.05 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:45:08  price 24589.05 (open +0.30 R of the book stop): took a part [OB1: OB1]
  10:45:53  price 24587.26 (open +0.32 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:45:53  price 24587.26 (open +0.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24588.12

**NY-OFI (NY AM MF5)** 2026-04-02 09:31:37 ET, LONG 3 lots at 23814.25, safety stop 23725.50 (1.5 x own stop 59.1667 pts). Result managed -64 pts/lot (-1.08 R, $-3829) ; own bracket result -60 pts (-1.02 R, $-3609). MFE +0.05 R, MAE -1.52 R, 7 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  09:31:38  price 23811.59 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:32:37  price 23778.75 (open -0.60 R of the book stop): state change desk [NORMAL/NNAWN-: NORMAL/NNAWN-]
  09:33:52  price 23784.96 (open -0.49 R of the book stop): state change desk [NORMAL/NNNWN-: NORMAL/NNNWN-]
  09:34:07  price 23780.53 (open -0.57 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  09:35:07  price 23763.66 (open -0.85 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:35:07  price 23763.66 (open -0.85 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:35:07  price 23763.66 (open -0.85 R of the book stop): took a part [DF: DF]
  09:35:22  price 23760.11 (open -0.92 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  09:35:37  price 23759.23 (open -0.93 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:35:52  price 23744.14 (open -1.19 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  09:36:07  price 23752.13 (open -1.05 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  09:36:52  price 23730.83 (open -1.41 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  09:37:07  price 23752.13 (open -1.05 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  09:38:07  price 23744.14 (open -1.19 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  exit: Stop at 23750.50

**NY-FIB (NY AM MF1)** 2026-05-13 10:36:46 ET, LONG 6 lots at 29263.79, safety stop 29085.29 (1.5 x own stop 119 pts). Result managed +31 pts/lot (+0.26 R, $+3683) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.38 R, 9 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A 16m:N
  10:36:47  price 29263.79 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:37:46  price 29256.65 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:39:01  price 29238.80 (open -0.21 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:39:46  price 29235.23 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:40:01  price 29240.59 (open -0.20 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  10:41:16  price 29247.73 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:52:16  price 29281.64 (open +0.15 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:53:01  price 29294.14 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:53:01  price 29294.14 (open +0.26 R of the book stop): took a part [OB1: OB1]
  10:53:16  price 29297.71 (open +0.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:53:16  price 29297.71 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29294.54

**NY-FIB (NY AM MF1)** 2026-05-18 09:30:45 ET, SHORT 6 lots at 29330.21, safety stop 29508.71 (1.5 x own stop 119 pts). Result managed +39 pts/lot (+0.33 R, $+4663) ; own bracket result +120 pts (+1.01 R, $+14388). MFE +0.42 R, MAE -0.25 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:30:46  price 29326.64 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:31:45  price 29315.93 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNN-: NORMAL/NNNNN-]
  09:33:00  price 29296.29 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:33:00  price 29296.29 (open +0.29 R of the book stop): took a part [OB1: OB1]
  09:33:15  price 29289.15 (open +0.35 R of the book stop): state change desk [NORMAL/NNWNN-: NORMAL/NNWNN-]
  09:33:15  price 29289.15 (open +0.35 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:33:15  price 29289.15 (open +0.35 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29291.29

**NY-NODE (NY AM MF4)** 2026-05-27 09:44:17 ET, SHORT 6 lots at 29991.75, safety stop 30125.62 (1.5 x own stop 89.25 pts). Result managed +31 pts/lot (+0.34 R, $+3663) ; own bracket result +30 pts (+0.34 R, $+3593). MFE +0.46 R, MAE -0.46 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:44:18  price 29990.41 (open +0.01 R of the book stop): state change desk [NORMAL/WNNANW: NORMAL/WNNANW]
  09:45:17  price 29995.77 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  09:45:47  price 30025.22 (open -0.38 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  09:46:02  price 30027.90 (open -0.41 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  09:46:17  price 29993.09 (open -0.01 R of the book stop): state change desk [PRESS/WNNWWW: PRESS/WNNWWW]
  09:47:02  price 29967.65 (open +0.27 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:47:02  price 29967.65 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:47:02  price 29967.65 (open +0.27 R of the book stop): took a part [OB1: OB1]
  09:47:17  price 29959.62 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:47:17  price 29959.62 (open +0.36 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29961.17

**NY-FIB (NY AM MF1)** 2026-06-12 09:53:24 ET, LONG 6 lots at 29340.08, safety stop 29161.58 (1.5 x own stop 119 pts). Result managed +32 pts/lot (+0.27 R, $+3848) ; own bracket: not taken (slot effect). MFE +0.35 R, MAE -0.46 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 4m:W
  09:53:25  price 29341.87 (open +0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  09:54:24  price 29297.24 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  09:57:09  price 29379.35 (open +0.33 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:57:09  price 29379.35 (open +0.33 R of the book stop): took a part [OB1: OB1]
  09:57:24  price 29366.86 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:57:24  price 29366.86 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29372.21

**NY-FIB (NY AM MF1)** 2026-06-12 10:57:04 ET, LONG 6 lots at 29600.83, safety stop 29422.33 (1.5 x own stop 119 pts). Result managed +33 pts/lot (+0.28 R, $+3928) ; own bracket: not taken (slot effect). MFE +0.38 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:57:05  price 29599.05 (open -0.01 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  10:58:04  price 29620.47 (open +0.17 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  10:59:19  price 29627.61 (open +0.22 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:59:49  price 29632.96 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:59:49  price 29632.96 (open +0.27 R of the book stop): took a part [OB1: OB1]
  11:00:04  price 29636.53 (open +0.30 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  11:00:04  price 29636.53 (open +0.30 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29633.62

**NY-NODE (NY AM MF4)** 2026-06-29 10:21:21 ET, LONG 6 lots at 29386.29, safety stop 29252.42 (1.5 x own stop 89.25 pts). Result managed +38 pts/lot (+0.42 R, $+4498) ; own bracket result +30 pts (+0.34 R, $+3588). MFE +0.55 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:21:22  price 29387.63 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:22:21  price 29419.76 (open +0.38 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:22:21  price 29419.76 (open +0.38 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:22:21  price 29419.76 (open +0.38 R of the book stop): took a part [OB1: OB1]
  10:22:36  price 29429.13 (open +0.48 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:22:36  price 29429.13 (open +0.48 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29423.83

**NY-FIB (NY AM MF1)** 2026-07-02 09:50:04 ET, LONG 6 lots at 30166.29, safety stop 29987.79 (1.5 x own stop 119 pts). Result managed +45 pts/lot (+0.38 R, $+5378) ; own bracket result +120 pts (+1.01 R, $+14388). MFE +0.42 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  09:50:05  price 30169.86 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:51:04  price 30209.13 (open +0.36 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  09:51:04  price 30209.13 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  09:51:04  price 30209.13 (open +0.36 R of the book stop): took a part [OB1: OB1]
  09:51:19  price 30216.27 (open +0.42 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  09:51:19  price 30216.27 (open +0.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30211.17

**NY-OFI (NY AM MF5)** 2026-07-02 10:44:35 ET, LONG 3 lots at 29822.00, safety stop 29733.25 (1.5 x own stop 59.1667 pts). Result managed +19 pts/lot (+0.32 R, $+1141) ; own bracket result -59 pts (-0.99 R, $-3529). MFE +0.53 R, MAE -0.44 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:44:36  price 29822.89 (open +0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:45:35  price 29842.41 (open +0.35 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  10:45:35  price 29842.41 (open +0.35 R of the book stop): state change PROBE>OUT [OB: OB]
  10:45:35  price 29842.41 (open +0.35 R of the book stop): closed everything [OB: OB]
  exit: ExAlgoAll_OB at 29841.08

**NY-OFI (NY AM MF5)** 2026-07-24 10:34:18 ET, SHORT 3 lots at 28323.83, safety stop 28412.58 (1.5 x own stop 59.1667 pts). Result managed +24 pts/lot (+0.41 R, $+1466) ; own bracket result +60 pts (+1.02 R, $+3601). MFE +0.85 R, MAE -0.33 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  10:34:19  price 28324.72 (open -0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:35:33  price 28327.38 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  10:39:18  price 28306.08 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:39:18  price 28306.08 (open +0.30 R of the book stop): took a part [OB1: OB1]
  10:39:33  price 28285.67 (open +0.65 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:39:33  price 28285.67 (open +0.65 R of the book stop): state change DEFENDING>OUT [DV: DV]
  10:39:33  price 28285.67 (open +0.65 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28299.33

**NY-VALUE (NY AM MF2)** 2026-08-05 10:37:07 ET, LONG 6 lots at 29893.75, safety stop 29804.75 (1.5 x own stop 59.3333 pts). Result managed -66 pts/lot (-1.11 R, $-7917) ; own bracket: not taken (slot effect). MFE +0.26 R, MAE -1.46 R, 16 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  10:37:08  price 29890.19 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:38:07  price 29851.03 (open -0.72 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  10:38:07  price 29851.03 (open -0.72 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  10:38:07  price 29851.03 (open -0.72 R of the book stop): took a part [DF: DF]
  10:38:37  price 29858.15 (open -0.60 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:39:07  price 29873.28 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:40:07  price 29839.46 (open -0.92 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  10:40:22  price 29847.47 (open -0.78 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:40:37  price 29838.57 (open -0.93 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  10:41:07  price 29832.34 (open -1.03 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  10:41:22  price 29835.90 (open -0.98 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  10:41:52  price 29841.24 (open -0.89 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:49:37  price 29896.42 (open +0.04 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:49:52  price 29904.43 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:50:07  price 29904.43 (open +0.18 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  10:50:37  price 29885.74 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:52:37  price 29829.67 (open -1.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  exit: Stop at 29827.83

**NY-OFI (NY AM MF5)** 2026-08-13 11:42:15 ET, LONG 3 lots at 30170.83, safety stop 30082.08 (1.5 x own stop 59.1667 pts). Result managed -0 pts/lot (-0.00 R, $-19) ; own bracket result -59 pts (-1.00 R, $-3539). MFE +0.09 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  11:42:16  price 30169.95 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:43:15  price 30170.83 (open +0.00 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  11:43:15  price 30170.83 (open +0.00 R of the book stop): state change PROBE>OUT [CL: CL]
  11:43:15  price 30170.83 (open +0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 30170.58

**NY-VALUE (NY AM MF2)** 2026-08-26 10:37:12 ET, LONG 6 lots at 29224.75, safety stop 29135.75 (1.5 x own stop 59.3333 pts). Result managed +19 pts/lot (+0.33 R, $+2308) ; own bracket: not taken (slot effect). MFE +0.50 R, MAE -0.29 R, 5 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 9m:A 11m:N
  10:37:13  price 29223.86 (open -0.01 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  10:38:12  price 29226.53 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:39:12  price 29214.96 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  10:39:27  price 29215.85 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:43:13  price 29216.74 (open -0.14 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  10:44:14  price 29218.52 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:46:00  price 29209.62 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  10:46:15  price 29219.41 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:49:30  price 29237.21 (open +0.21 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:49:30  price 29237.21 (open +0.21 R of the book stop): took a part [OB1: OB1]
  10:50:45  price 29250.56 (open +0.43 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:50:45  price 29250.56 (open +0.43 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29244.04

**NY-NODE (NY AM MF4)** 2026-09-09 11:12:45 ET, SHORT 6 lots at 29402.33, safety stop 29536.21 (1.5 x own stop 89.25 pts). Result managed +27 pts/lot (+0.30 R, $+3248) ; own bracket result +30 pts (+0.34 R, $+3603). MFE +0.24 R, MAE -0.69 R, 10 min under water (longest 8 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  11:12:46  price 29392.96 (open +0.11 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  11:13:45  price 29406.35 (open -0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:16:00  price 29406.35 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  11:22:00  price 29421.08 (open -0.21 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  11:22:45  price 29400.99 (open +0.01 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  11:23:00  price 29396.98 (open +0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  11:23:30  price 29376.90 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  11:23:30  price 29376.90 (open +0.29 R of the book stop): took a part [OB1: OB1]
  11:23:45  price 29374.22 (open +0.32 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  11:23:45  price 29374.22 (open +0.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29375.21

**NY-VALUE (NY AM MF2)** 2026-09-25 10:15:07 ET, SHORT 6 lots at 30709.58, safety stop 30798.58 (1.5 x own stop 59.3333 pts). Result managed +14 pts/lot (+0.24 R, $+1708) ; own bracket result -57 pts (-0.96 R, $-6877). MFE +0.35 R, MAE -0.77 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N
  10:15:08  price 30706.91 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  10:17:07  price 30700.68 (open +0.15 R of the book stop): state change desk [PRESS/WNNWAW: PRESS/WNNWAW]
  10:17:22  price 30687.33 (open +0.38 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:17:22  price 30687.33 (open +0.38 R of the book stop): took a part [OB1: OB1]
  10:17:37  price 30697.12 (open +0.21 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:17:37  price 30697.12 (open +0.21 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30695.29

**NY-OFI (NY AM MF5)** 2026-10-13 09:35:10 ET, SHORT 3 lots at 30634.92, safety stop 30723.67 (1.5 x own stop 59.1667 pts). Result managed -32 pts/lot (-0.54 R, $-1934) ; own bracket result -60 pts (-1.01 R, $-3594). MFE +0.29 R, MAE -1.41 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  09:35:11  price 30644.68 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  09:36:10  price 30638.47 (open -0.06 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  09:36:10  price 30638.47 (open -0.06 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  09:36:10  price 30638.47 (open -0.06 R of the book stop): took a part [DF: DF]
  09:36:55  price 30660.65 (open -0.43 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  09:37:10  price 30676.63 (open -0.70 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  09:37:40  price 30685.50 (open -0.85 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  09:37:55  price 30688.17 (open -0.90 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  09:38:10  price 30720.12 (open -1.44 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  exit: Stop at 30667.08

**NY-NODE (NY AM MF4)** 2026-10-23 10:37:16 ET, LONG 6 lots at 29171.00, safety stop 29037.12 (1.5 x own stop 89.25 pts). Result managed +22 pts/lot (+0.25 R, $+2693) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  10:37:17  price 29172.34 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  10:38:16  price 29195.10 (open +0.27 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  10:38:16  price 29195.10 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  10:38:16  price 29195.10 (open +0.27 R of the book stop): took a part [OB1: OB1]
  10:38:31  price 29191.08 (open +0.22 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  10:38:31  price 29191.08 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  10:38:31  price 29191.08 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29193.50

# DK22 PART: AS

# Asia (AS): managed rows DK22MAIN_A, 4924 trades from 110 finished (set, month) rows, matched to the book's own bracket on 0 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 0 | +0 |  |
| winners cut short | 0 | +0 |  |
| losers cut early | 0 | +0 |  |
| losers made worse | 0 | +0 |  |
| matched pairs (all) | 0 | +0 |  |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 4924 trades, net $ -84787; entries that exist only under the own bracket in the same months (blocked by a carried trade): 4937 trades, net $ +2030666. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## Asia: the 20 WORST give-backs (largest open profit given back, $)

**AS-VWAPBRK (Asia MF3)** 2026-04-07 18:32:47 ET, SHORT 6 lots at 24585.75, safety stop 24652.94 (1.5 x own stop 44.7917 pts). Result managed -67 pts/lot (-1.50 R, $-8062) ; own bracket: not taken (slot effect). MFE +3.17 R, MAE -3.50 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 
  18:32:49  price 24500.42 (open +1.91 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  exit: Stop at 24652.88

**AS-RSI (Asia MF2)** 2025-04-13 18:01:41 ET, LONG 6 lots at 19054.50, safety stop 18965.06 (1.5 x own stop 59.625 pts). Result managed -93 pts/lot (-1.56 R, $-11187) ; own bracket: not taken (slot effect). MFE +0.91 R, MAE -1.61 R, 16 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  18:01:42  price 19052.71 (open -0.03 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:20:14  price 19014.25 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:25:45  price 18980.27 (open -1.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 18961.33

**AS-VWAPBRK (Asia MF3)** 2025-04-06 20:04:40 ET, SHORT 6 lots at 16570.92, safety stop 16638.10 (1.5 x own stop 44.7917 pts). Result managed -68 pts/lot (-1.53 R, $-8212) ; own bracket: not taken (slot effect). MFE +1.57 R, MAE -1.42 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 
  20:04:41  price 16583.01 (open -0.27 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: Stop at 16639.29

**AS-NR7 (Asia MF1)** 2026-04-07 18:24:03 ET, LONG 6 lots at 24617.21, safety stop 24557.65 (1.5 x own stop 39.7083 pts). Result managed -9 pts/lot (-0.23 R, $-1082) ; own bracket: not taken (slot effect). MFE +3.19 R, MAE -0.60 R, 8 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:W
  18:24:05  price 24616.02 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:32:41  price 24620.19 (open +0.08 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:32:41  price 24620.19 (open +0.08 R of the book stop): state change PROBE>OUT [DV: DV]
  18:32:41  price 24620.19 (open +0.08 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 24608.25

**AS-VWAPBRK (Asia MF3)** 2026-04-19 18:00:06 ET, SHORT 6 lots at 26583.54, safety stop 26650.73 (1.5 x own stop 44.7917 pts). Result managed -66 pts/lot (-1.47 R, $-7917) ; own bracket: not taken (slot effect). MFE +1.45 R, MAE -1.33 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:07  price 26598.32 (open -0.33 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: Stop at 26649.46

**AS-VWAPBRK (Asia MF3)** 2025-06-22 18:00:03 ET, SHORT 6 lots at 21638.79, safety stop 21705.98 (1.5 x own stop 44.7917 pts). Result managed -70 pts/lot (-1.57 R, $-8447) ; own bracket: not taken (slot effect). MFE +1.23 R, MAE -1.96 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  18:00:04  price 21621.99 (open +0.38 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  exit: Stop at 21709.12

**AS-VWAPBRK (Asia MF3)** 2026-05-03 18:00:05 ET, LONG 6 lots at 27886.33, safety stop 27819.15 (1.5 x own stop 44.7917 pts). Result managed -66 pts/lot (-1.48 R, $-7942) ; own bracket: not taken (slot effect). MFE +1.03 R, MAE -1.36 R, 70 min under water (longest 66 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 22m:A
  18:00:06  price 27882.97 (open -0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:12  price 27872.90 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  18:21:27  price 27862.82 (open -0.52 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:21:42  price 27862.15 (open -0.54 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  18:24:01  price 27841.99 (open -0.99 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  18:24:16  price 27845.35 (open -0.92 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  18:26:35  price 27849.38 (open -0.83 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:29:33  price 27842.66 (open -0.98 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  18:29:49  price 27844.01 (open -0.95 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:00:12  price 27846.69 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  19:00:28  price 27846.02 (open -0.90 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:00:43  price 27846.02 (open -0.90 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  19:01:51  price 27854.08 (open -0.72 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:03:08  price 27849.38 (open -0.83 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  19:03:57  price 27848.71 (open -0.84 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:07:55  price 27846.69 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  19:11:02  price 27837.29 (open -1.09 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  exit: Stop at 27820.21

**AS-VWAPBRK (Asia MF3)** 2026-06-10 20:17:39 ET, LONG 6 lots at 28537.12, safety stop 28469.94 (1.5 x own stop 44.7917 pts). Result managed -68 pts/lot (-1.51 R, $-8112) ; own bracket: not taken (slot effect). MFE +0.79 R, MAE -1.52 R, 8 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  20:17:40  price 28533.77 (open -0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:18:39  price 28533.09 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:21:10  price 28498.83 (open -0.85 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:26:28  price 28476.66 (open -1.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 28469.58

**AS-VWAPBRK (Asia MF3)** 2024-11-03 18:00:03 ET, SHORT 6 lots at 20113.12, safety stop 20180.31 (1.5 x own stop 44.7917 pts). Result managed -53 pts/lot (-1.18 R, $-6362) ; own bracket: not taken (slot effect). MFE +1.05 R, MAE -1.46 R, 145 min under water (longest 144 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 32m:A
  18:00:04  price 20121.19 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:00  price 20109.77 (open +0.08 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:20:15  price 20113.80 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:24:38  price 20123.88 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:24:54  price 20122.53 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:25:10  price 20123.88 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:25:25  price 20120.52 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:26:42  price 20127.91 (open -0.33 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:35:08  price 20140.00 (open -0.60 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:36:00  price 20142.02 (open -0.65 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:36:15  price 20141.34 (open -0.63 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:37:20  price 20150.08 (open -0.83 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:37:35  price 20148.06 (open -0.78 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:37:50  price 20150.75 (open -0.84 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:39:09  price 20144.70 (open -0.70 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:41:12  price 20151.42 (open -0.85 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:41:27  price 20151.42 (open -0.85 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:41:57  price 20156.80 (open -0.98 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:42:12  price 20153.44 (open -0.90 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:42:59  price 20151.42 (open -0.85 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:43:14  price 20152.77 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:43:30  price 20154.78 (open -0.93 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:44:01  price 20153.44 (open -0.90 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:44:20  price 20155.45 (open -0.95 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:44:36  price 20152.77 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:45:37  price 20147.39 (open -0.77 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:45:52  price 20146.72 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:48:50  price 20146.72 (open -0.75 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:49:05  price 20146.05 (open -0.73 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:49:20  price 20145.38 (open -0.72 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:50:25  price 20148.73 (open -0.80 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:52:56  price 20146.72 (open -0.75 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:53:18  price 20146.72 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:01:05  price 20127.23 (open -0.32 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:01:50  price 20127.23 (open -0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:03:09  price 20125.22 (open -0.27 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:03:24  price 20125.22 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:04:13  price 20124.55 (open -0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:04:28  price 20125.22 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:24:36  price 20142.69 (open -0.66 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 20166.08

**AS-VWAPBRK (Asia MF3)** 2024-08-11 18:03:04 ET, LONG 6 lots at 18630.83, safety stop 18563.65 (1.5 x own stop 44.7917 pts). Result managed -68 pts/lot (-1.51 R, $-8132) ; own bracket: not taken (slot effect). MFE +0.71 R, MAE -1.64 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 11m:A
  18:03:05  price 18626.80 (open -0.09 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  exit: Stop at 18563.12

**AS-VWAPBRK (Asia MF3)** 2025-06-15 18:00:03 ET, SHORT 6 lots at 21547.75, safety stop 21614.94 (1.5 x own stop 44.7917 pts). Result managed -66 pts/lot (-1.47 R, $-7902) ; own bracket: not taken (slot effect). MFE +0.64 R, MAE -1.10 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  18:00:04  price 21567.91 (open -0.45 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: Stop at 21613.54

**AS-VWAPBRK (Asia MF3)** 2024-09-29 18:00:03 ET, SHORT 6 lots at 20196.58, safety stop 20263.77 (1.5 x own stop 44.7917 pts). Result managed -62 pts/lot (-1.38 R, $-7407) ; own bracket: not taken (slot effect). MFE +0.73 R, MAE -1.70 R, 102 min under water (longest 100 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:W 11m:A
  18:00:04  price 20191.88 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:09  price 20223.46 (open -0.60 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:27:42  price 20230.85 (open -0.77 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:30:11  price 20232.19 (open -0.80 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:30:26  price 20234.88 (open -0.85 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:30:42  price 20232.86 (open -0.81 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:33:21  price 20232.86 (open -0.81 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:33:57  price 20234.21 (open -0.84 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:34:12  price 20237.57 (open -0.92 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:37:00  price 20236.90 (open -0.90 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:39:12  price 20239.58 (open -0.96 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:40:13  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:40:59  price 20236.22 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:41:52  price 20236.22 (open -0.89 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:42:17  price 20235.55 (open -0.87 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:42:55  price 20234.21 (open -0.84 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:43:13  price 20236.22 (open -0.89 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:43:30  price 20236.90 (open -0.90 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:43:46  price 20238.91 (open -0.95 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:45:00  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:45:18  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:46:59  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:47:14  price 20240.93 (open -0.99 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:47:48  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:48:03  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:48:22  price 20237.57 (open -0.92 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:49:11  price 20238.91 (open -0.95 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:49:53  price 20237.57 (open -0.92 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:50:08  price 20238.24 (open -0.93 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:51:11  price 20238.91 (open -0.95 R of the book stop): state change desk [NORMAL/NN--N-: NORMAL/NN--N-]
  18:51:29  price 20237.57 (open -0.92 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:54:30  price 20240.93 (open -0.99 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:54:47  price 20238.91 (open -0.95 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:56:09  price 20240.26 (open -0.98 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:57:51  price 20240.93 (open -0.99 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:58:12  price 20239.58 (open -0.96 R of the book stop): state change desk [NORMAL/NN--N-: NORMAL/NN--N-]
  18:58:34  price 20239.58 (open -0.96 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:58:49  price 20239.58 (open -0.96 R of the book stop): state change desk [NORMAL/NN--N-: NORMAL/NN--N-]
  18:59:05  price 20241.60 (open -1.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:59:40  price 20243.61 (open -1.05 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 20258.25

**AS-VWAPBRK (Asia MF3)** 2025-10-30 00:37:07 ET, LONG 6 lots at 26284.42, safety stop 26217.23 (1.5 x own stop 44.7917 pts). Result managed -66 pts/lot (-1.48 R, $-7962) ; own bracket: not taken (slot effect). MFE +0.54 R, MAE -1.46 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  00:37:08  price 26283.74 (open -0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  00:38:07  price 26284.42 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: Stop at 26218.12

**AS-VWAPBRK (Asia MF3)** 2025-05-11 18:00:03 ET, LONG 6 lots at 20467.08, safety stop 20399.90 (1.5 x own stop 44.7917 pts). Result managed -67 pts/lot (-1.49 R, $-8022) ; own bracket: not taken (slot effect). MFE +0.51 R, MAE -1.36 R, 30 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  18:00:04  price 20454.99 (open -0.27 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:10:14  price 20434.83 (open -0.72 R of the book stop): state change desk [NORMAL/NN----: NORMAL/NN----]
  18:20:17  price 20446.93 (open -0.45 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: Stop at 20400.29

**AS-RSI (Asia MF2)** 2025-06-18 21:04:44 ET, SHORT 6 lots at 21826.62, safety stop 21916.06 (1.5 x own stop 59.625 pts). Result managed -53 pts/lot (-0.89 R, $-6377) ; own bracket: not taken (slot effect). MFE +0.59 R, MAE -0.94 R, 170 min under water (longest 113 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  21:04:45  price 21829.31 (open -0.04 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  21:05:44  price 21856.14 (open -0.49 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  21:06:14  price 21838.25 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:09:53  price 21837.36 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:18:40  price 21848.98 (open -0.38 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:19:13  price 21847.20 (open -0.35 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:45:01  price 21836.46 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:57:25  price 21840.04 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:57:45  price 21839.15 (open -0.21 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:58:00  price 21840.04 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:58:16  price 21839.15 (open -0.21 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:58:48  price 21840.04 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:59:41  price 21838.25 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:59:57  price 21838.25 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:08:23  price 21833.78 (open -0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:09:56  price 21838.25 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:29:19  price 21853.46 (open -0.45 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:35:55  price 21857.03 (open -0.51 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:36:27  price 21851.67 (open -0.42 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:38:03  price 21851.67 (open -0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:49:46  price 21856.14 (open -0.49 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:50:01  price 21855.24 (open -0.48 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:50:49  price 21853.46 (open -0.45 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  23:01:58  price 21855.24 (open -0.48 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:04:15  price 21863.29 (open -0.61 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  23:05:32  price 21866.87 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:05:47  price 21867.77 (open -0.69 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  23:06:59  price 21865.08 (open -0.65 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:10:06  price 21871.34 (open -0.75 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:11:39  price 21870.45 (open -0.73 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:12:02  price 21871.34 (open -0.75 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:12:27  price 21872.24 (open -0.77 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:12:43  price 21874.92 (open -0.81 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:13:14  price 21877.60 (open -0.85 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:16:34  price 21872.24 (open -0.77 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:17:13  price 21871.34 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:17:31  price 21872.24 (open -0.77 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:17:52  price 21872.24 (open -0.77 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:20:35  price 21874.03 (open -0.80 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:21:07  price 21875.82 (open -0.83 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 21879.71

**AS-NR7 (Asia MF1)** 2025-04-02 18:40:03 ET, SHORT 6 lots at 18905.17, safety stop 18964.73 (1.5 x own stop 39.7083 pts). Result managed -60 pts/lot (-1.51 R, $-7192) ; own bracket: not taken (slot effect). MFE +0.61 R, MAE -1.42 R, 10 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 9m:A
  18:40:04  price 18909.93 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: Stop at 18965.04

**AS-VWAPBRK (Asia MF3)** 2026-05-05 18:52:14 ET, LONG 6 lots at 28380.83, safety stop 28313.65 (1.5 x own stop 44.7917 pts). Result managed -23 pts/lot (-0.52 R, $-2812) ; own bracket: not taken (slot effect). MFE +1.26 R, MAE -0.82 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  18:52:16  price 28357.99 (open -0.51 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:53:14  price 28338.51 (open -0.95 R of the book stop): state change desk [DEFEND/WAA-A-: DEFEND/WAA-A-]
  18:53:14  price 28338.51 (open -0.95 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  18:53:14  price 28338.51 (open -0.95 R of the book stop): took a part [DF: DF]
  18:53:29  price 28332.46 (open -1.08 R of the book stop): state change desk [NORMAL/WNA-A-: NORMAL/WNA-A-]
  18:55:00  price 28377.47 (open -0.08 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  18:55:00  price 28377.47 (open -0.08 R of the book stop): state change DEFENDING>OUT [DV: DV]
  18:55:00  price 28377.47 (open -0.08 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28357.46

**AS-VWAPBRK (Asia MF3)** 2026-03-08 18:00:03 ET, SHORT 6 lots at 24446.50, safety stop 24513.69 (1.5 x own stop 44.7917 pts). Result managed +166 pts/lot (+3.70 R, $+19898) ; own bracket: not taken (slot effect). MFE +5.46 R, MAE -0.12 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:04  price 24469.34 (open -0.51 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:11  price 24289.95 (open +3.50 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  18:20:11  price 24289.95 (open +3.50 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:20:11  price 24289.95 (open +3.50 R of the book stop): took a part [OB1: OB1]
  18:20:26  price 24289.95 (open +3.50 R of the book stop): state change DEFENDING>FREE [NB: NB]
  18:20:26  price 24289.95 (open +3.50 R of the book stop): moved the stop closer [NB: NB]
  18:21:44  price 24296.00 (open +3.36 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:24:02  price 24283.23 (open +3.65 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  18:24:17  price 24280.55 (open +3.71 R of the book stop): moved the stop closer [NB: NB]
  18:24:32  price 24265.77 (open +4.04 R of the book stop): moved the stop closer [NB: NB]
  18:26:05  price 24270.47 (open +3.93 R of the book stop): state change FREE>OUT [OB2: OB2]
  18:26:05  price 24270.47 (open +3.93 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24280.62

**AS-VWAPBRK (Asia MF3)** 2026-08-30 18:00:13 ET, LONG 6 lots at 29503.88, safety stop 29436.69 (1.5 x own stop 44.7917 pts). Result managed -41 pts/lot (-0.93 R, $-4982) ; own bracket: not taken (slot effect). MFE +0.83 R, MAE -1.28 R, 32 min under water (longest 32 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  18:00:14  price 29503.20 (open -0.01 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:20:14  price 29487.75 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:34:44  price 29464.23 (open -0.89 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  18:34:44  price 29464.23 (open -0.89 R of the book stop): state change PROBE>OUT [AB: AB]
  18:34:44  price 29464.23 (open -0.89 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 29462.42

**AS-VWAPBRK (Asia MF3)** 2025-08-25 20:03:38 ET, SHORT 6 lots at 23480.42, safety stop 23547.60 (1.5 x own stop 44.7917 pts). Result managed +2 pts/lot (+0.05 R, $+238) ; own bracket: not taken (slot effect). MFE +1.63 R, MAE -0.27 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  20:03:39  price 23482.43 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:04:38  price 23472.35 (open +0.18 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  20:05:53  price 23483.78 (open -0.08 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  20:06:08  price 23478.40 (open +0.04 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  20:06:38  price 23484.45 (open -0.09 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  20:07:08  price 23480.42 (open -0.00 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:07:08  price 23480.42 (open -0.00 R of the book stop): took a part [OB1: OB1]
  20:08:10  price 23474.37 (open +0.14 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  20:08:56  price 23474.37 (open +0.14 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  20:09:11  price 23475.04 (open +0.12 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:09:11  price 23475.04 (open +0.12 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23478.38

## Asia: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**AS-VWAPBRK (Asia MF3)** 2025-04-06 18:00:03 ET, SHORT 6 lots at 17119.88, safety stop 17187.06 (1.5 x own stop 44.7917 pts). Result managed +367 pts/lot (+8.18 R, $+43973) ; own bracket: not taken (slot effect). MFE +9.22 R, MAE -1.94 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:10  price 17050.00 (open +1.56 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:10:08  price 16740.94 (open +8.46 R of the book stop): state change desk [NORMAL/NN----: NORMAL/NN----]
  18:10:08  price 16740.94 (open +8.46 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:10:08  price 16740.94 (open +8.46 R of the book stop): took a part [OB1: OB1]
  18:10:23  price 16762.44 (open +7.98 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:10:23  price 16762.44 (open +7.98 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 16753.38

**AS-VWAPBRK (Asia MF3)** 2026-06-14 18:00:03 ET, LONG 6 lots at 29893.38, safety stop 29826.19 (1.5 x own stop 44.7917 pts). Result managed +177 pts/lot (+3.95 R, $+21213) ; own bracket: not taken (slot effect). MFE +2.15 R, MAE -1.83 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:06  price 29908.16 (open +0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:09  price 30072.09 (open +3.99 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  18:20:09  price 30072.09 (open +3.99 R of the book stop): state change PROBE>OUT [DV: DV]
  18:20:09  price 30072.09 (open +3.99 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 30070.21

**AS-VWAPBRK (Asia MF3)** 2025-05-25 18:03:32 ET, LONG 6 lots at 20993.96, safety stop 20926.77 (1.5 x own stop 44.7917 pts). Result managed +146 pts/lot (+3.27 R, $+17563) ; own bracket: not taken (slot effect). MFE +3.36 R, MAE -0.26 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:03:33  price 20997.32 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:12  price 21139.08 (open +3.24 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  18:20:12  price 21139.08 (open +3.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:20:12  price 21139.08 (open +3.24 R of the book stop): took a part [OB1: OB1]
  18:20:27  price 21143.11 (open +3.33 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:20:27  price 21143.11 (open +3.33 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21140.38

**AS-VWAPBRK (Asia MF3)** 2025-10-12 18:00:03 ET, LONG 6 lots at 24582.00, safety stop 24514.81 (1.5 x own stop 44.7917 pts). Result managed +121 pts/lot (+2.70 R, $+14513) ; own bracket: not taken (slot effect). MFE +1.06 R, MAE -2.00 R, 12 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:A
  18:00:10  price 24699.58 (open +2.62 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:20:01  price 24707.64 (open +2.81 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:01  price 24707.64 (open +2.81 R of the book stop): state change PROBE>OUT [DV: DV]
  18:20:01  price 24707.64 (open +2.81 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 24703.00

**AS-VWAPBRK (Asia MF3)** 2025-06-19 18:00:04 ET, LONG 6 lots at 21763.00, safety stop 21695.81 (1.5 x own stop 44.7917 pts). Result managed +62 pts/lot (+1.39 R, $+7448) ; own bracket: not taken (slot effect). MFE +1.64 R, MAE -0.14 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:05  price 21771.06 (open +0.18 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:10:06  price 21824.14 (open +1.36 R of the book stop): state change desk [NORMAL/NN----: NORMAL/NN----]
  18:10:06  price 21824.14 (open +1.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:10:06  price 21824.14 (open +1.36 R of the book stop): took a part [OB1: OB1]
  18:10:21  price 21826.16 (open +1.41 R of the book stop): state change DEFENDING>FREE [NB: NB]
  18:10:21  price 21826.16 (open +1.41 R of the book stop): moved the stop closer [NB: NB]
  18:10:36  price 21829.52 (open +1.48 R of the book stop): state change FREE>OUT [OB2: OB2]
  18:10:36  price 21829.52 (open +1.48 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21825.12

**AS-VWAPBRK (Asia MF3)** 2026-04-22 20:15:31 ET, SHORT 6 lots at 26921.42, safety stop 26988.60 (1.5 x own stop 44.7917 pts). Result managed +59 pts/lot (+1.33 R, $+7118) ; own bracket: not taken (slot effect). MFE +1.53 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  20:15:32  price 26923.43 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  20:16:31  price 26864.31 (open +1.27 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  20:16:31  price 26864.31 (open +1.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:16:31  price 26864.31 (open +1.27 R of the book stop): took a part [OB1: OB1]
  20:16:46  price 26857.59 (open +1.42 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:16:46  price 26857.59 (open +1.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 26862.04

**AS-VWAPBRK (Asia MF3)** 2024-03-31 18:00:03 ET, LONG 6 lots at 18514.29, safety stop 18447.10 (1.5 x own stop 44.7917 pts). Result managed +58 pts/lot (+1.30 R, $+6968) ; own bracket: not taken (slot effect). MFE +1.59 R, MAE -0.25 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:20:05  price 18572.74 (open +1.30 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:20:05  price 18572.74 (open +1.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:20:05  price 18572.74 (open +1.30 R of the book stop): took a part [OB1: OB1]
  18:20:20  price 18572.07 (open +1.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:20:20  price 18572.07 (open +1.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18572.42

**AS-VWAPBRK (Asia MF3)** 2026-05-24 18:00:03 ET, LONG 6 lots at 29719.92, safety stop 29652.73 (1.5 x own stop 44.7917 pts). Result managed +57 pts/lot (+1.28 R, $+6883) ; own bracket: not taken (slot effect). MFE +1.37 R, MAE -0.23 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:04  price 29719.92 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:05  price 29778.37 (open +1.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:05  price 29778.37 (open +1.30 R of the book stop): state change PROBE>OUT [DV: DV]
  18:20:05  price 29778.37 (open +1.30 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29777.33

**AS-NR7 (Asia MF1)** 2025-01-26 18:04:04 ET, SHORT 6 lots at 21701.21, safety stop 21760.77 (1.5 x own stop 39.7083 pts). Result managed +48 pts/lot (+1.20 R, $+5728) ; own bracket: not taken (slot effect). MFE +1.33 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:04:05  price 21703.00 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:03  price 21654.75 (open +1.17 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  18:20:03  price 21654.75 (open +1.17 R of the book stop): state change PROBE>OUT [DV: DV]
  18:20:03  price 21654.75 (open +1.17 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 21653.42

**AS-NR7 (Asia MF1)** 2026-06-21 19:00:04 ET, SHORT 6 lots at 30515.62, safety stop 30575.19 (1.5 x own stop 39.7083 pts). Result managed +46 pts/lot (+1.16 R, $+5498) ; own bracket: not taken (slot effect). MFE +1.36 R, MAE -0.18 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  19:00:05  price 30513.24 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:01:04  price 30490.01 (open +0.65 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:01:04  price 30490.01 (open +0.65 R of the book stop): state change PROBE>FREE [NB: NB]
  19:01:04  price 30490.01 (open +0.65 R of the book stop): moved the stop closer [NB: NB]
  19:01:34  price 30470.95 (open +1.12 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  19:01:34  price 30470.95 (open +1.12 R of the book stop): took a part [OB1: OB1]
  19:01:49  price 30467.98 (open +1.20 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:01:49  price 30467.98 (open +1.20 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30469.75

**AS-VWAPBRK (Asia MF3)** 2026-10-11 18:01:17 ET, LONG 6 lots at 31138.62, safety stop 31071.44 (1.5 x own stop 44.7917 pts). Result managed +45 pts/lot (+1.01 R, $+5408) ; own bracket: not taken (slot effect). MFE +1.13 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:01:18  price 31137.28 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:00  price 31184.31 (open +1.02 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:00  price 31184.31 (open +1.02 R of the book stop): state change PROBE>OUT [DV: DV]
  18:20:00  price 31184.31 (open +1.02 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 31183.75

**AS-VWAPBRK (Asia MF3)** 2024-07-28 18:00:06 ET, LONG 6 lots at 19178.12, safety stop 19110.94 (1.5 x own stop 44.7917 pts). Result managed +45 pts/lot (+1.00 R, $+5378) ; own bracket: not taken (slot effect). MFE +1.11 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:07  price 19183.50 (open +0.12 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  18:20:07  price 19225.16 (open +1.05 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:20:07  price 19225.16 (open +1.05 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:20:07  price 19225.16 (open +1.05 R of the book stop): took a part [OB1: OB1]
  18:20:22  price 19221.12 (open +0.96 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:20:22  price 19221.12 (open +0.96 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19223.00

**AS-VWAPBRK (Asia MF3)** 2025-02-23 18:00:08 ET, LONG 6 lots at 21699.25, safety stop 21632.06 (1.5 x own stop 44.7917 pts). Result managed +42 pts/lot (+0.94 R, $+5058) ; own bracket: not taken (slot effect). MFE +1.11 R, MAE -0.56 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:00:09  price 21702.61 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:20:00  price 21743.59 (open +0.99 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:20:00  price 21743.59 (open +0.99 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:20:00  price 21743.59 (open +0.99 R of the book stop): took a part [OB1: OB1]
  18:20:17  price 21740.23 (open +0.92 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:20:17  price 21740.23 (open +0.92 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21741.46

**AS-VWAPBRK (Asia MF3)** 2026-07-12 20:06:07 ET, LONG 6 lots at 29960.46, safety stop 29893.27 (1.5 x own stop 44.7917 pts). Result managed +41 pts/lot (+0.92 R, $+4953) ; own bracket: not taken (slot effect). MFE +1.09 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  20:06:08  price 29959.11 (open -0.03 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  20:07:07  price 30002.11 (open +0.93 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:07:07  price 30002.11 (open +0.93 R of the book stop): state change PROBE>OUT [DV: DV]
  20:07:07  price 30002.11 (open +0.93 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 30001.79

**AS-VWAPBRK (Asia MF3)** 2026-06-10 19:20:05 ET, SHORT 6 lots at 28359.04, safety stop 28426.23 (1.5 x own stop 44.7917 pts). Result managed +38 pts/lot (+0.86 R, $+4613) ; own bracket: not taken (slot effect). MFE +1.06 R, MAE -0.83 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  19:20:06  price 28358.37 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  19:21:05  price 28317.39 (open +0.93 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:21:05  price 28317.39 (open +0.93 R of the book stop): state change PROBE>OUT [DV: DV]
  19:21:05  price 28317.39 (open +0.93 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28320.54

## Asia: 50 RANDOM trades (seed 11)

**AS-RSI (Asia MF2)** 2023-10-03 01:09:13 ET, SHORT 6 lots at 14945.88, safety stop 15035.31 (1.5 x own stop 59.625 pts). Result managed -5 pts/lot (-0.08 R, $-572) ; own bracket: not taken (slot effect). MFE +0.03 R, MAE -0.21 R, 28 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:-
  01:10:13  price 14947.66 (open -0.03 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  01:10:30  price 14947.66 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:12:05  price 14953.03 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  01:12:20  price 14953.92 (open -0.14 R of the book stop): state change desk [DEFEND/NAA-N-: DEFEND/NAA-N-]
  01:12:20  price 14953.92 (open -0.14 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  01:12:20  price 14953.92 (open -0.14 R of the book stop): took a part [DF: DF]
  01:12:36  price 14954.82 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  01:14:49  price 14951.24 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:15:05  price 14953.03 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  01:17:12  price 14951.24 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:17:42  price 14947.66 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:20:30  price 14950.35 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:24:12  price 14947.66 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:30:31  price 14948.56 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:30:46  price 14947.66 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:31:53  price 14949.45 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:32:47  price 14951.24 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  01:33:33  price 14950.35 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:38:04  price 14951.24 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:41:22  price 14945.88 (open -0.00 R of the book stop): state change DEFENDING>OUT [CL: CL]
  01:41:22  price 14945.88 (open -0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 14950.58

**AS-NR7 (Asia MF1)** 2023-11-21 18:04:03 ET, SHORT 6 lots at 15959.88, safety stop 16019.44 (1.5 x own stop 39.7083 pts). Result managed +10 pts/lot (+0.25 R, $+1183) ; own bracket: not taken (slot effect). MFE +0.34 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:04:04  price 15961.66 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:05:03  price 15959.28 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  18:06:07  price 15956.30 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:15:40  price 15950.94 (open +0.22 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:15:40  price 15950.94 (open +0.22 R of the book stop): took a part [OB1: OB1]
  18:15:55  price 15948.56 (open +0.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:15:55  price 15948.56 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 15949.96

**AS-VWAPBRK (Asia MF3)** 2024-01-11 20:07:16 ET, SHORT 6 lots at 16927.33, safety stop 16994.52 (1.5 x own stop 44.7917 pts). Result managed -25 pts/lot (-0.56 R, $-3007) ; own bracket: not taken (slot effect). MFE +0.17 R, MAE -0.79 R, 334 min under water (longest 325 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 6m:N 8m:W 11m:N 68m:A
  20:07:17  price 16928.01 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:08:17  price 16930.02 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:08:33  price 16928.68 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:08:48  price 16931.36 (open -0.09 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  20:09:06  price 16931.36 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:09:41  price 16929.35 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:31:01  price 16925.99 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:36:03  price 16929.35 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:36:19  price 16929.35 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:45:11  price 16939.43 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:48:07  price 16940.77 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:49:11  price 16942.11 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:50:15  price 16944.80 (open -0.39 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:51:01  price 16945.47 (open -0.41 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:51:01  price 16945.47 (open -0.41 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  20:51:01  price 16945.47 (open -0.41 R of the book stop): took a part [DF: DF]
  20:51:50  price 16943.46 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:52:05  price 16941.44 (open -0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:00:59  price 16945.47 (open -0.41 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  21:01:14  price 16946.82 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:02:16  price 16947.49 (open -0.45 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:04:04  price 16946.82 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:14:17  price 16949.51 (open -0.49 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:15:03  price 16952.86 (open -0.57 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:17:11  price 16946.82 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:17:58  price 16948.16 (open -0.46 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  21:18:16  price 16947.49 (open -0.45 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:22:58  price 16950.18 (open -0.51 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:24:04  price 16950.85 (open -0.52 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:25:31  price 16950.18 (open -0.51 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:26:07  price 16950.85 (open -0.52 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:26:23  price 16950.18 (open -0.51 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:26:38  price 16950.85 (open -0.52 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:27:02  price 16950.18 (open -0.51 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:29:14  price 16953.54 (open -0.58 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:29:29  price 16952.19 (open -0.55 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:29:44  price 16952.86 (open -0.57 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:31:13  price 16952.19 (open -0.55 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:32:00  price 16954.21 (open -0.60 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  21:33:10  price 16954.21 (open -0.60 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  exit: UWTime at 16952.33

**AS-NR7 (Asia MF1)** 2024-03-05 18:32:03 ET, SHORT 6 lots at 17958.08, safety stop 18017.65 (1.5 x own stop 39.7083 pts). Result managed +11 pts/lot (+0.27 R, $+1273) ; own bracket: not taken (slot effect). MFE +0.35 R, MAE -0.21 R, 44 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 18m:N
  18:32:04  price 17958.08 (open +0.00 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  18:33:03  price 17960.47 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:37:13  price 17965.23 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:37:28  price 17965.23 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:40:12  price 17962.85 (open -0.12 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:40:28  price 17962.25 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:14:07  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:14:39  price 17956.89 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:15:13  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:15:45  price 17956.30 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:17:09  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:17:25  price 17956.30 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:18:01  price 17955.11 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:18:33  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:19:05  price 17955.11 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:19:24  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:19:39  price 17954.51 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:24:54  price 17956.89 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:25:34  price 17956.89 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:26:06  price 17957.49 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:28:14  price 17959.87 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:29:03  price 17960.47 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:30:38  price 17962.85 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:30:53  price 17961.66 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:39:43  price 17960.47 (open -0.06 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  19:40:00  price 17959.87 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:44:24  price 17955.11 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:45:00  price 17955.11 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:47:00  price 17954.51 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:47:15  price 17955.70 (open +0.06 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  19:47:31  price 17953.91 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:49:01  price 17946.17 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  19:49:01  price 17946.17 (open +0.30 R of the book stop): took a part [OB1: OB1]
  19:49:31  price 17947.96 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:49:31  price 17947.96 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 17947.42

**AS-VWAPBRK (Asia MF3)** 2024-03-26 21:19:19 ET, LONG 6 lots at 18488.88, safety stop 18421.69 (1.5 x own stop 44.7917 pts). Result managed +11 pts/lot (+0.24 R, $+1268) ; own bracket: not taken (slot effect). MFE +0.29 R, MAE -0.16 R, 26 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 7m:W 10m:N 32m:A 38m:N 55m:A 61m:N
  21:19:20  price 18488.88 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:20:19  price 18487.53 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:22:15  price 18484.84 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:23:58  price 18488.20 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:25:10  price 18487.53 (open -0.03 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  21:25:29  price 18488.88 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:26:01  price 18492.23 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:28:31  price 18489.55 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:29:59  price 18490.89 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:30:14  price 18488.88 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:32:00  price 18490.22 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:33:24  price 18488.88 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:33:43  price 18490.22 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:34:52  price 18489.55 (open +0.01 R of the book stop): state change desk [NORMAL/WAN-N-: NORMAL/WAN-N-]
  21:35:07  price 18489.55 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:36:26  price 18488.20 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:37:39  price 18486.86 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:37:58  price 18486.86 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:38:15  price 18484.17 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:41:04  price 18483.50 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:44:25  price 18486.86 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:44:40  price 18484.84 (open -0.09 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  21:44:55  price 18485.52 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:47:17  price 18487.53 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:51:13  price 18486.86 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:51:57  price 18486.86 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:10:20  price 18488.20 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:11:30  price 18488.88 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:13:10  price 18490.89 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:17:01  price 18490.89 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:22:24  price 18491.56 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:22:56  price 18489.55 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  22:23:13  price 18490.89 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:24:24  price 18494.25 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:25:02  price 18492.91 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:25:39  price 18494.25 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:26:11  price 18493.58 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:27:24  price 18494.25 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:29:35  price 18495.59 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:31:08  price 18497.61 (open +0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: ExAlgoAll_OB2 at 18499.50

**AS-VWAPBRK (Asia MF3)** 2024-05-15 19:28:21 ET, LONG 6 lots at 18719.33, safety stop 18652.15 (1.5 x own stop 44.7917 pts). Result managed +9 pts/lot (+0.21 R, $+1128) ; own bracket: not taken (slot effect). MFE +0.36 R, MAE -0.04 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 6m:N 7m:W 29m:N 34m:W
  19:28:22  price 18719.33 (open +0.00 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  19:29:24  price 18718.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:31:06  price 18718.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:33:08  price 18719.33 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:34:29  price 18723.36 (open +0.09 R of the book stop): state change desk [NORMAL/WAN-N-: NORMAL/WAN-N-]
  19:34:47  price 18722.02 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:35:02  price 18722.02 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:37:28  price 18722.69 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:38:13  price 18724.04 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:38:34  price 18724.04 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:38:55  price 18724.04 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:39:11  price 18722.69 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:39:46  price 18726.72 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:40:16  price 18724.04 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:44:59  price 18722.69 (open +0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:45:14  price 18722.02 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:47:36  price 18720.01 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:47:54  price 18720.68 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:01:35  price 18725.38 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:01:51  price 18724.71 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:11  price 18724.71 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:02:42  price 18730.76 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:02:42  price 18730.76 (open +0.26 R of the book stop): took a part [OB1: OB1]
  20:06:34  price 18728.07 (open +0.20 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:06:34  price 18728.07 (open +0.20 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18728.79

**AS-NR7 (Asia MF1)** 2024-06-06 18:32:03 ET, LONG 6 lots at 19073.12, safety stop 19013.56 (1.5 x own stop 39.7083 pts). Result managed +10 pts/lot (+0.25 R, $+1173) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.14 R, 32 min under water (longest 12 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 7m:W 35m:N
  18:32:05  price 19073.12 (open -0.00 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:33:11  price 19073.12 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:34:00  price 19072.53 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:34:26  price 19073.12 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:38:39  price 19077.29 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:39:46  price 19076.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:40:09  price 19076.10 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:41:21  price 19077.29 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:42:21  price 19078.49 (open +0.14 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:42:48  price 19078.49 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:45:25  price 19078.49 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:47:53  price 19076.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:48:25  price 19076.70 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:48:52  price 19076.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:49:13  price 19076.10 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:49:28  price 19076.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:52:37  price 19077.89 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:54:45  price 19079.08 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:55:01  price 19079.08 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:58:35  price 19079.08 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:59:50  price 19079.68 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:00:06  price 19077.89 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  19:00:21  price 19078.49 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:00:36  price 19078.49 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  19:00:55  price 19079.08 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:02:22  price 19073.72 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:05:01  price 19076.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:14:47  price 19077.89 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:15:31  price 19077.29 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:16:26  price 19077.89 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:16:52  price 19076.70 (open +0.09 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:17:34  price 19077.29 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:18:03  price 19077.29 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:18:39  price 19076.70 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:18:59  price 19077.29 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:20:16  price 19079.08 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:23:26  price 19076.70 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:24:00  price 19077.29 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:25:36  price 19077.29 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  19:25:54  price 19077.29 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_OB2 at 19082.96

**AS-VWAPBRK (Asia MF3)** 2024-07-22 20:09:49 ET, SHORT 6 lots at 19961.58, safety stop 20028.77 (1.5 x own stop 44.7917 pts). Result managed +11 pts/lot (+0.24 R, $+1308) ; own bracket: not taken (slot effect). MFE +0.27 R, MAE -0.04 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  20:09:50  price 19962.26 (open -0.01 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:10:55  price 19962.26 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:12:06  price 19960.24 (open +0.03 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:12:22  price 19958.22 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  20:12:59  price 19958.22 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:15:27  price 19956.21 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:16:14  price 19958.90 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:22:08  price 19960.24 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:28:16  price 19950.83 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:28:16  price 19950.83 (open +0.24 R of the book stop): took a part [OB1: OB1]
  20:35:08  price 19950.16 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:35:08  price 19950.16 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19950.62

**AS-VWAPBRK (Asia MF3)** 2024-08-11 18:17:19 ET, SHORT 6 lots at 18550.21, safety stop 18617.40 (1.5 x own stop 44.7917 pts). Result managed +11 pts/lot (+0.25 R, $+1333) ; own bracket: not taken (slot effect). MFE +0.58 R, MAE -0.35 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:17:20  price 18550.21 (open -0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  18:20:11  price 18558.94 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:21:47  price 18537.44 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:21:47  price 18537.44 (open +0.29 R of the book stop): took a part [OB1: OB1]
  18:26:16  price 18538.11 (open +0.27 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:26:16  price 18538.11 (open +0.27 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18539.04

**AS-VWAPBRK (Asia MF3)** 2024-08-18 18:24:43 ET, LONG 6 lots at 19629.29, safety stop 19562.10 (1.5 x own stop 44.7917 pts). Result managed +7 pts/lot (+0.15 R, $+798) ; own bracket: not taken (slot effect). MFE +0.37 R, MAE -0.21 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:24:44  price 19628.62 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:25:46  price 19629.96 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:28:01  price 19636.68 (open +0.17 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:28:01  price 19636.68 (open +0.17 R of the book stop): took a part [OB1: OB1]
  18:29:28  price 19638.70 (open +0.21 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:29:28  price 19638.70 (open +0.21 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:29:28  price 19638.70 (open +0.21 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19636.00

**AS-VWAPBRK (Asia MF3)** 2024-09-08 18:32:58 ET, LONG 6 lots at 18422.75, safety stop 18355.56 (1.5 x own stop 44.7917 pts). Result managed +12 pts/lot (+0.26 R, $+1413) ; own bracket: not taken (slot effect). MFE +0.38 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:32:59  price 18420.73 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:36:15  price 18425.44 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  18:36:30  price 18426.11 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:38:43  price 18438.88 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:38:43  price 18438.88 (open +0.36 R of the book stop): took a part [OB1: OB1]
  18:38:58  price 18432.83 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:38:58  price 18432.83 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18434.58

**AS-VWAPBRK (Asia MF3)** 2024-09-29 20:00:27 ET, LONG 6 lots at 20280.67, safety stop 20213.48 (1.5 x own stop 44.7917 pts). Result managed -50 pts/lot (-1.12 R, $-6007) ; own bracket: not taken (slot effect). MFE +0.03 R, MAE -1.17 R, 60 min under water (longest 60 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  20:00:28  price 20280.67 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:01:27  price 20272.60 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:30  price 20273.95 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  20:02:45  price 20274.62 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:03:00  price 20273.28 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  20:03:16  price 20273.28 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:05:49  price 20265.89 (open -0.33 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  20:06:04  price 20265.89 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:10:24  price 20278.65 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:11:14  price 20274.62 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:18:04  price 20271.93 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:18:53  price 20269.24 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:19:08  price 20261.85 (open -0.42 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:19:23  price 20279.99 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:21:00  price 20273.28 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:24:05  price 20268.57 (open -0.27 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:24:54  price 20266.56 (open -0.32 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:26:03  price 20264.54 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:26:19  price 20263.87 (open -0.38 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:26:54  price 20262.53 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:28:59  price 20254.46 (open -0.58 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:30:17  price 20259.84 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:34:05  price 20263.87 (open -0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:34:23  price 20263.20 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:43:23  price 20265.21 (open -0.35 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:43:55  price 20262.53 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:52:17  price 20259.84 (open -0.46 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:52:51  price 20255.81 (open -0.55 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:53:07  price 20260.51 (open -0.45 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:53:37  price 20255.81 (open -0.55 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:54:07  price 20250.43 (open -0.68 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:54:39  price 20252.45 (open -0.63 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:54:54  price 20250.43 (open -0.68 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:58:04  price 20249.76 (open -0.69 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:00:15  price 20230.28 (open -1.12 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  21:00:15  price 20230.28 (open -1.12 R of the book stop): state change PROBE>OUT [AB: AB]
  21:00:15  price 20230.28 (open -1.12 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 20230.67

**AS-VWAPBRK (Asia MF3)** 2024-10-01 18:51:04 ET, SHORT 6 lots at 19915.83, safety stop 19983.02 (1.5 x own stop 44.7917 pts). Result managed +14 pts/lot (+0.31 R, $+1653) ; own bracket: not taken (slot effect). MFE +0.46 R, MAE -0.55 R, 31 min under water (longest 16 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 9m:N 11m:A 34m:N 35m:W
  18:51:07  price 19915.83 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:52:04  price 19918.52 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:06:21  price 19915.83 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:07:57  price 19920.54 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:22:12  price 19918.52 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:22:27  price 19921.21 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:22:59  price 19917.18 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:23:32  price 19917.85 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:23:52  price 19915.16 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:24:08  price 19912.47 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:24:36  price 19914.49 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:25:25  price 19913.15 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:26:12  price 19903.07 (open +0.29 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:26:12  price 19903.07 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  19:26:12  price 19903.07 (open +0.29 R of the book stop): took a part [OB1: OB1]
  19:26:27  price 19899.71 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:26:27  price 19899.71 (open +0.36 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19902.00

**AS-NR7 (Asia MF1)** 2024-10-08 18:32:04 ET, SHORT 6 lots at 20277.62, safety stop 20337.19 (1.5 x own stop 39.7083 pts). Result managed +2 pts/lot (+0.05 R, $+228) ; own bracket: not taken (slot effect). MFE +0.48 R, MAE -0.52 R, 116 min under water (longest 22 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 4m:W 9m:N 31m:A 61m:N
  18:32:05  price 20275.84 (open +0.04 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:33:05  price 20275.84 (open +0.04 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:33:21  price 20275.84 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:33:39  price 20277.03 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:34:04  price 20276.43 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:34:21  price 20277.62 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:35:00  price 20276.43 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:35:15  price 20275.84 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:35:30  price 20273.46 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:36:16  price 20277.03 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:36:48  price 20275.24 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:37:20  price 20274.05 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:45:17  price 20273.46 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:48:19  price 20276.43 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:50:17  price 20275.24 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:50:39  price 20276.43 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:55:55  price 20284.18 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:59:04  price 20285.37 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:59:22  price 20287.15 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:00:07  price 20292.52 (open -0.38 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:00:07  price 20292.52 (open -0.38 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  19:00:07  price 20292.52 (open -0.38 R of the book stop): took a part [DF: DF]
  19:03:02  price 20291.32 (open -0.35 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:05:55  price 20284.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:14:44  price 20277.62 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:19:00  price 20279.41 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:32:04  price 20275.24 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:33:46  price 20277.62 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:34:16  price 20277.03 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:34:57  price 20277.62 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:35:12  price 20277.03 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:35:52  price 20277.62 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:37:28  price 20278.82 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:37:45  price 20280.01 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:38:00  price 20280.60 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:38:24  price 20280.60 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:46:09  price 20277.03 (open +0.01 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  19:46:37  price 20275.84 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:51:05  price 20278.22 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:52:42  price 20275.84 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: ExAlgoAll_OB2 at 20275.67

**AS-VWAPBRK (Asia MF3)** 2024-12-10 18:02:06 ET, LONG 6 lots at 21433.79, safety stop 21366.60 (1.5 x own stop 44.7917 pts). Result managed -1 pts/lot (-0.02 R, $-137) ; own bracket: not taken (slot effect). MFE +0.16 R, MAE -0.54 R, 397 min under water (longest 131 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 5m:A 61m:N 94m:A
  18:02:09  price 21431.78 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:03:10  price 21430.43 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:06:49  price 21429.76 (open -0.09 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:06:49  price 21429.76 (open -0.09 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  18:06:49  price 21429.76 (open -0.09 R of the book stop): took a part [DF: DF]
  18:07:19  price 21425.73 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:08:06  price 21426.40 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:08:37  price 21425.73 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:12:17  price 21424.39 (open -0.21 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:13:11  price 21427.07 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:13:43  price 21424.39 (open -0.21 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:15:37  price 21426.40 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:20:11  price 21423.71 (open -0.22 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:20:26  price 21424.39 (open -0.21 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:20:41  price 21423.71 (open -0.22 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:21:17  price 21424.39 (open -0.21 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:22:08  price 21423.04 (open -0.24 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:30:13  price 21420.35 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:34:51  price 21425.06 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:35:12  price 21425.06 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:35:46  price 21425.06 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:37:42  price 21426.40 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:38:34  price 21425.06 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:38:56  price 21425.06 (open -0.20 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:39:41  price 21425.73 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:40:01  price 21424.39 (open -0.21 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:42:51  price 21420.35 (open -0.30 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:43:06  price 21420.35 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:46:37  price 21426.40 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:04:01  price 21421.70 (open -0.27 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:04:37  price 21421.03 (open -0.29 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:05:07  price 21420.35 (open -0.30 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:06:38  price 21421.03 (open -0.29 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:06:55  price 21421.03 (open -0.29 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:07:25  price 21420.35 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:07:46  price 21418.34 (open -0.35 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:08:03  price 21417.67 (open -0.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:09:26  price 21418.34 (open -0.35 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:09:44  price 21418.34 (open -0.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:11:00  price 21416.32 (open -0.39 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  exit: ExAlgoAll_CL at 21432.71

**AS-NR7 (Asia MF1)** 2024-12-12 18:16:06 ET, LONG 6 lots at 21731.71, safety stop 21672.15 (1.5 x own stop 39.7083 pts). Result managed +9 pts/lot (+0.23 R, $+1103) ; own bracket: not taken (slot effect). MFE +0.28 R, MAE -0.11 R, 7 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 11m:N 13m:W
  18:16:07  price 21731.11 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:20:08  price 21731.71 (open +0.00 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:20:23  price 21732.30 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:35:11  price 21741.24 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:35:11  price 21741.24 (open +0.24 R of the book stop): took a part [OB1: OB1]
  18:35:26  price 21741.24 (open +0.24 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:35:26  price 21741.24 (open +0.24 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21740.96

**AS-NR7 (Asia MF1)** 2025-01-19 18:36:03 ET, SHORT 6 lots at 21538.17, safety stop 21597.73 (1.5 x own stop 39.7083 pts). Result managed -43 pts/lot (-1.08 R, $-5162) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -1.27 R, 415 min under water (longest 354 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:W 61m:N 88m:A
  18:36:16  price 21539.36 (open -0.03 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  18:37:05  price 21538.17 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:42:05  price 21545.31 (open -0.18 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:42:20  price 21545.91 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:47:03  price 21533.40 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:00:12  price 21551.27 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:00:42  price 21544.12 (open -0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:02:13  price 21541.74 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:30:36  price 21545.31 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:33:16  price 21547.70 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:33:33  price 21545.91 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:36:22  price 21551.87 (open -0.35 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:49:03  price 21538.76 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:50:57  price 21545.91 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:52:15  price 21542.34 (open -0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:52:30  price 21544.72 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:55:15  price 21550.67 (open -0.32 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:55:35  price 21548.89 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:55:50  price 21551.87 (open -0.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:56:05  price 21554.25 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:04:14  price 21566.76 (open -0.72 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:06:31  price 21564.97 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:10:12  price 21569.14 (open -0.78 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:12:38  price 21567.95 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:16:55  price 21560.20 (open -0.55 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:21:41  price 21545.31 (open -0.18 R of the book stop): state change desk [NORMAL/WAN-N-: NORMAL/WAN-N-]
  20:21:56  price 21544.72 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:23:11  price 21550.08 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:28:19  price 21547.70 (open -0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:33:35  price 21550.08 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:34:21  price 21556.04 (open -0.45 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:40:10  price 21564.37 (open -0.66 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:48:38  price 21567.95 (open -0.75 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:50:06  price 21571.52 (open -0.84 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:50:06  price 21571.52 (open -0.84 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  20:50:06  price 21571.52 (open -0.84 R of the book stop): took a part [DF: DF]
  20:50:24  price 21570.33 (open -0.81 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:51:00  price 21570.33 (open -0.81 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:51:15  price 21568.54 (open -0.77 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:51:35  price 21566.76 (open -0.72 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 21581.12

**AS-NR7 (Asia MF1)** 2025-02-02 18:32:03 ET, LONG 6 lots at 21100.21, safety stop 21040.65 (1.5 x own stop 39.7083 pts). Result managed +21 pts/lot (+0.54 R, $+2558) ; own bracket: not taken (slot effect). MFE +0.77 R, MAE -0.96 R, 13 min under water (longest 8 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  18:33:03  price 21093.06 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:45:28  price 21114.50 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:45:28  price 21114.50 (open +0.36 R of the book stop): took a part [OB1: OB1]
  18:45:43  price 21130.59 (open +0.77 R of the book stop): state change DEFENDING>OUT [DV: DV]
  18:45:43  price 21130.59 (open +0.77 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 21121.58

**AS-VWAPBRK (Asia MF3)** 2025-03-09 21:49:07 ET, LONG 6 lots at 20104.00, safety stop 20036.81 (1.5 x own stop 44.7917 pts). Result managed +12 pts/lot (+0.28 R, $+1473) ; own bracket: not taken (slot effect). MFE +0.50 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  21:49:08  price 20101.31 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:50:07  price 20101.31 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:50:22  price 20099.97 (open -0.09 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  21:50:40  price 20099.97 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:53:23  price 20115.42 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  21:53:23  price 20115.42 (open +0.26 R of the book stop): took a part [OB1: OB1]
  21:54:46  price 20116.77 (open +0.29 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:55:16  price 20118.78 (open +0.33 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  21:55:16  price 20118.78 (open +0.33 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 20116.33

**AS-NR7 (Asia MF1)** 2025-03-19 18:48:38 ET, LONG 6 lots at 19813.21, safety stop 19753.65 (1.5 x own stop 39.7083 pts). Result managed +9 pts/lot (+0.22 R, $+1018) ; own bracket: not taken (slot effect). MFE +0.37 R, MAE -0.37 R, 47 min under water (longest 43 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 27m:N
  18:48:40  price 19812.02 (open -0.03 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:51:07  price 19815.00 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:51:45  price 19817.38 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:52:04  price 19812.02 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:55:46  price 19807.85 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:57:02  price 19809.04 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:57:19  price 19807.25 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:57:37  price 19807.85 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:59:14  price 19803.68 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:00:05  price 19804.87 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:06:32  price 19801.30 (open -0.30 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:06:48  price 19803.68 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:16:09  price 19803.68 (open -0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:17:01  price 19800.10 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:25:59  price 19808.44 (open -0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:26:44  price 19806.66 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:31:07  price 19806.06 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:31:23  price 19804.87 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:33:34  price 19806.06 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:33:51  price 19806.06 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:38:16  price 19806.06 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:56:12  price 19816.19 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:56:48  price 19816.78 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:57:46  price 19822.74 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  19:57:46  price 19822.74 (open +0.24 R of the book stop): took a part [OB1: OB1]
  19:58:28  price 19822.14 (open +0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:59:25  price 19823.33 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:59:25  price 19823.33 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19821.75

**AS-NR7 (Asia MF1)** 2025-05-06 18:32:03 ET, LONG 6 lots at 20076.58, safety stop 20017.02 (1.5 x own stop 39.7083 pts). Result managed -59 pts/lot (-1.47 R, $-7032) ; own bracket: not taken (slot effect). MFE +0.03 R, MAE -1.46 R, 5 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  18:32:05  price 20073.01 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:33:04  price 20067.65 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: Stop at 20018.04

**AS-VWAPBRK (Asia MF3)** 2025-06-01 22:22:30 ET, SHORT 6 lots at 21266.58, safety stop 21333.77 (1.5 x own stop 44.7917 pts). Result managed -0 pts/lot (-0.01 R, $-42) ; own bracket: not taken (slot effect). MFE +0.39 R, MAE -0.32 R, 30 min under water (longest 18 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 37m:N
  22:22:32  price 21267.93 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:23:31  price 21271.29 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:24:01  price 21271.29 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:24:17  price 21273.97 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:25:38  price 21271.29 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:31:13  price 21269.27 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:32:45  price 21271.29 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:33:06  price 21267.26 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:34:18  price 21269.94 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:35:19  price 21269.94 (open -0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:36:01  price 21271.96 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:38:00  price 21277.33 (open -0.24 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  22:38:00  price 21277.33 (open -0.24 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  22:38:00  price 21277.33 (open -0.24 R of the book stop): took a part [DF: DF]
  22:39:06  price 21278.01 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:39:36  price 21274.65 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:39:53  price 21277.33 (open -0.24 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:40:57  price 21276.66 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:42:04  price 21278.01 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:42:20  price 21276.66 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:43:26  price 21278.01 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:44:08  price 21277.33 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:46:12  price 21275.32 (open -0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:46:46  price 21278.68 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:47:03  price 21280.02 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  22:48:08  price 21278.01 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:52:33  price 21267.26 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  23:02:06  price 21253.15 (open +0.30 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  23:02:06  price 21253.15 (open +0.30 R of the book stop): moved the stop closer [OB1: OB1]
  23:02:21  price 21255.83 (open +0.24 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  23:02:21  price 21255.83 (open +0.24 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21266.88

**AS-NR7 (Asia MF1)** 2025-06-22 18:40:03 ET, LONG 6 lots at 21781.25, safety stop 21721.69 (1.5 x own stop 39.7083 pts). Result managed -53 pts/lot (-1.33 R, $-6352) ; own bracket: not taken (slot effect). MFE +0.14 R, MAE -1.33 R, 85 min under water (longest 85 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  18:40:04  price 21771.12 (open -0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:41:03  price 21766.96 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:10:01  price 21735.98 (open -1.14 R of the book stop): state change desk [DEFEND/NAA-N-: DEFEND/NAA-N-]
  19:10:01  price 21735.98 (open -1.14 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  19:10:01  price 21735.98 (open -1.14 R of the book stop): took a part [DF: DF]
  19:10:16  price 21738.96 (open -1.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:11:36  price 21740.15 (open -1.03 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:11:55  price 21747.90 (open -0.84 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:27:19  price 21747.90 (open -0.84 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  19:27:44  price 21748.49 (open -0.83 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:30:09  price 21756.23 (open -0.63 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:30:41  price 21751.47 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:32:00  price 21756.83 (open -0.61 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:35:35  price 21751.47 (open -0.75 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:49:13  price 21757.42 (open -0.60 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:55:39  price 21756.23 (open -0.63 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:56:27  price 21761.59 (open -0.49 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:58:04  price 21762.79 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:01:47  price 21734.79 (open -1.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:02:19  price 21733.00 (open -1.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:34  price 21735.98 (open -1.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 21728.38

**AS-VWAPBRK (Asia MF3)** 2025-07-10 20:27:27 ET, SHORT 6 lots at 22861.92, safety stop 22929.10 (1.5 x own stop 44.7917 pts). Result managed +8 pts/lot (+0.18 R, $+938) ; own bracket: not taken (slot effect). MFE +0.64 R, MAE -0.97 R, 17 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:A
  20:27:28  price 22860.57 (open +0.03 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:28:27  price 22872.67 (open -0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:30:28  price 22842.43 (open +0.43 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:30:28  price 22842.43 (open +0.43 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:30:28  price 22842.43 (open +0.43 R of the book stop): took a part [OB1: OB1]
  20:30:43  price 22845.79 (open +0.36 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:31:28  price 22876.70 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:34:58  price 22885.43 (open -0.52 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  20:35:13  price 22888.79 (open -0.60 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:36:16  price 22901.56 (open -0.89 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:37:17  price 22892.15 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:37:47  price 22887.45 (open -0.57 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  20:38:02  price 22887.45 (open -0.57 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:39:19  price 22882.07 (open -0.45 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:39:34  price 22885.43 (open -0.52 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:40:36  price 22878.71 (open -0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:42:07  price 22880.73 (open -0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:44:08  price 22878.71 (open -0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:45:09  price 22857.89 (open +0.09 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:45:09  price 22857.89 (open +0.09 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 22854.04

**AS-VWAPBRK (Asia MF3)** 2025-08-05 20:00:38 ET, SHORT 6 lots at 23059.83, safety stop 23127.02 (1.5 x own stop 44.7917 pts). Result managed -29 pts/lot (-0.65 R, $-3527) ; own bracket: not taken (slot effect). MFE +0.07 R, MAE -0.73 R, 31 min under water (longest 30 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A
  20:00:39  price 23061.85 (open -0.04 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  20:01:38  price 23061.18 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:09  price 23067.90 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:02:24  price 23067.90 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:03:13  price 23073.27 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:10:39  price 23085.36 (open -0.57 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:10:39  price 23085.36 (open -0.57 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  20:10:39  price 23085.36 (open -0.57 R of the book stop): took a part [DF: DF]
  20:10:56  price 23079.99 (open -0.45 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:19:14  price 23071.93 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:20:20  price 23073.27 (open -0.30 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:20:40  price 23073.27 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:23:02  price 23082.68 (open -0.51 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:26:03  price 23079.32 (open -0.43 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:27:12  price 23080.66 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:28:03  price 23084.69 (open -0.55 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:30:15  price 23076.63 (open -0.38 R of the book stop): state change desk [NORMAL/WNA-N-: NORMAL/WNA-N-]
  20:30:30  price 23075.29 (open -0.35 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:31:01  price 23077.30 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:32:08  price 23092.76 (open -0.73 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  20:32:08  price 23092.76 (open -0.73 R of the book stop): state change DEFENDING>OUT [AB: AB]
  20:32:08  price 23092.76 (open -0.73 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 23089.17

**AS-NR7 (Asia MF1)** 2025-08-14 18:36:08 ET, LONG 6 lots at 23886.75, safety stop 23827.19 (1.5 x own stop 39.7083 pts). Result managed +9 pts/lot (+0.22 R, $+1043) ; own bracket: not taken (slot effect). MFE +0.27 R, MAE -0.11 R, 6 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 6m:N 23m:W
  18:36:09  price 23886.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:58:33  price 23893.90 (open +0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:59:03  price 23894.49 (open +0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:59:52  price 23896.28 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:59:52  price 23896.28 (open +0.24 R of the book stop): took a part [OB1: OB1]
  19:00:26  price 23895.68 (open +0.22 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:00:26  price 23895.68 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:00:26  price 23895.68 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23895.50

**AS-RSI (Asia MF2)** 2025-09-10 20:55:01 ET, LONG 6 lots at 23903.04, safety stop 23813.60 (1.5 x own stop 59.625 pts). Result managed -2 pts/lot (-0.03 R, $-187) ; own bracket: not taken (slot effect). MFE +0.28 R, MAE -0.53 R, 113 min under water (longest 103 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 7m:N 260m:A
  20:55:05  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:56:03  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:58:02  price 23901.25 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  20:58:21  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:01:24  price 23900.36 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:01:39  price 23901.25 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:01:56  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  21:02:11  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:06:28  price 23906.62 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:06:48  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:09:13  price 23908.41 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:15:56  price 23904.83 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:16:16  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:18:33  price 23904.83 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:18:48  price 23906.62 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:22:37  price 23904.83 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:25:51  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:26:12  price 23906.62 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  21:27:14  price 23910.20 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:27:30  price 23911.99 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:28:03  price 23911.99 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  21:28:41  price 23910.20 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:28:59  price 23910.20 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  21:30:09  price 23911.09 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:31:00  price 23913.77 (open +0.18 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  21:32:05  price 23913.77 (open +0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:39:25  price 23911.09 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:44:50  price 23912.88 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:45:09  price 23911.09 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:49:18  price 23906.62 (open +0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  21:50:25  price 23904.83 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:55:09  price 23909.30 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:55:28  price 23908.41 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:58:11  price 23906.62 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:02:13  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:02:29  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:03:06  price 23905.72 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:06:15  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  22:06:31  price 23902.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:15:07  price 23904.83 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: UWTime at 23901.54

**AS-NR7 (Asia MF1)** 2025-09-25 18:24:15 ET, SHORT 6 lots at 24648.25, safety stop 24707.81 (1.5 x own stop 39.7083 pts). Result managed +12 pts/lot (+0.30 R, $+1443) ; own bracket: not taken (slot effect). MFE +0.52 R, MAE -0.37 R, 19 min under water (longest 13 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A 8m:N 11m:W 17m:N 28m:W
  18:24:19  price 24650.04 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:25:15  price 24651.82 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:48:08  price 24646.46 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:48:25  price 24648.25 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:49:45  price 24644.68 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:50:32  price 24644.68 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:52:01  price 24639.91 (open +0.21 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:52:18  price 24641.70 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:52:53  price 24639.32 (open +0.22 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:52:53  price 24639.32 (open +0.22 R of the book stop): took a part [OB1: OB1]
  18:53:09  price 24635.74 (open +0.32 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:53:26  price 24631.57 (open +0.42 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:53:26  price 24631.57 (open +0.42 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:53:26  price 24631.57 (open +0.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24636.17

**AS-VWAPBRK (Asia MF3)** 2025-09-29 23:45:37 ET, LONG 6 lots at 24850.08, safety stop 24782.90 (1.5 x own stop 44.7917 pts). Result managed -13 pts/lot (-0.29 R, $-1562) ; own bracket: not taken (slot effect). MFE +0.01 R, MAE -0.74 R, 134 min under water (longest 134 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 61m:N 73m:A
  23:45:44  price 24849.41 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  23:46:40  price 24848.07 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:46:55  price 24848.07 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:47:12  price 24848.07 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:48:22  price 24846.72 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:50:03  price 24846.72 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:50:20  price 24845.38 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:54:11  price 24845.38 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:54:29  price 24842.69 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:56:20  price 24844.71 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:57:09  price 24842.69 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:57:45  price 24844.04 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:58:57  price 24842.69 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  23:59:17  price 24844.04 (open -0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:00:10  price 24843.36 (open -0.15 R of the book stop): state change desk [NORMAL/WNA-N-: NORMAL/WNA-N-]
  00:01:15  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:02:58  price 24838.66 (open -0.26 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  00:02:58  price 24838.66 (open -0.26 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  00:02:58  price 24838.66 (open -0.26 R of the book stop): took a part [DF: DF]
  00:03:20  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:05:01  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:05:20  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:05:41  price 24840.01 (open -0.22 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:06:17  price 24841.35 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:07:55  price 24844.04 (open -0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:08:15  price 24844.71 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:09:49  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:10:14  price 24841.35 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:12:29  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:13:49  price 24841.35 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:15:20  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:16:16  price 24842.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:16:37  price 24840.01 (open -0.22 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:17:01  price 24840.68 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  00:28:08  price 24836.65 (open -0.30 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  00:31:01  price 24830.60 (open -0.43 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:33:04  price 24827.91 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  00:33:38  price 24827.91 (open -0.49 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  00:34:20  price 24825.90 (open -0.54 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  00:35:13  price 24826.57 (open -0.52 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  exit: UWTime at 24837.12

**AS-NR7 (Asia MF1)** 2025-10-05 20:00:03 ET, SHORT 6 lots at 25068.83, safety stop 25128.40 (1.5 x own stop 39.7083 pts). Result managed +12 pts/lot (+0.31 R, $+1453) ; own bracket: not taken (slot effect). MFE +0.40 R, MAE -0.17 R, 10 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 21m:N 24m:W
  20:00:04  price 25067.64 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:01:03  price 25065.26 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:01:55  price 25067.64 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:27  price 25065.86 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:03:45  price 25062.88 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  20:04:01  price 25064.07 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:06:52  price 25070.62 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:08:36  price 25068.83 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:08:54  price 25068.24 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:10:43  price 25062.88 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:11:01  price 25065.26 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:11:32  price 25062.28 (open +0.17 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  20:12:17  price 25064.66 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:15:39  price 25072.41 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:15:55  price 25070.62 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:16:10  price 25071.81 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:17:49  price 25072.41 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:21:30  price 25065.26 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:23:45  price 25058.11 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:23:45  price 25058.11 (open +0.27 R of the book stop): took a part [OB1: OB1]
  20:25:52  price 25060.49 (open +0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:26:07  price 25057.52 (open +0.29 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:26:39  price 25055.73 (open +0.33 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:26:58  price 25057.52 (open +0.29 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:27:13  price 25058.11 (open +0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:31:19  price 25060.49 (open +0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:31:38  price 25059.30 (open +0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:33:56  price 25053.94 (open +0.38 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:33:56  price 25053.94 (open +0.38 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25056.67

**AS-VWAPBRK (Asia MF3)** 2025-10-13 00:53:41 ET, LONG 6 lots at 24820.83, safety stop 24753.65 (1.5 x own stop 44.7917 pts). Result managed -5 pts/lot (-0.10 R, $-567) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.39 R, 17 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 3m:A 6m:N 7m:A 22m:N 24m:W 27m:N 30m:W
  00:53:42  price 24819.49 (open -0.03 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  00:54:44  price 24818.82 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  00:57:17  price 24816.80 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:02:16  price 24808.07 (open -0.29 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:02:31  price 24806.72 (open -0.32 R of the book stop): state change desk [DEFEND/NNA-A-: DEFEND/NNA-A-]
  01:02:31  price 24806.72 (open -0.32 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  01:02:31  price 24806.72 (open -0.32 R of the book stop): took a part [DF: DF]
  01:03:01  price 24803.36 (open -0.39 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  01:03:34  price 24806.05 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:05:02  price 24808.07 (open -0.29 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:05:35  price 24813.44 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:07:25  price 24816.80 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:07:41  price 24814.11 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:07:56  price 24814.11 (open -0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:08:43  price 24816.13 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:08:59  price 24819.49 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:09:14  price 24821.51 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  01:10:15  price 24819.49 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:11:17  price 24814.11 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:11:36  price 24812.77 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:13:17  price 24816.80 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  01:13:59  price 24819.49 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:15:00  price 24823.52 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  01:17:27  price 24826.88 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:19:02  price 24816.80 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  01:19:24  price 24815.46 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  01:19:40  price 24822.18 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  01:20:00  price 24823.52 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  01:22:49  price 24830.91 (open +0.22 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  01:22:49  price 24830.91 (open +0.22 R of the book stop): moved the stop closer [OB1: OB1]
  01:24:03  price 24830.91 (open +0.22 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  exit: Stop at 24816.17

**AS-NR7 (Asia MF1)** 2026-01-15 20:04:03 ET, LONG 6 lots at 25764.46, safety stop 25704.90 (1.5 x own stop 39.7083 pts). Result managed +9 pts/lot (+0.23 R, $+1083) ; own bracket: not taken (slot effect). MFE +0.32 R, MAE -0.08 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:W
  20:04:04  price 25763.86 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:05:03  price 25764.46 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:07:20  price 25766.25 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:07:51  price 25768.63 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:08:06  price 25768.63 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:08:21  price 25773.99 (open +0.24 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:08:37  price 25773.99 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:08:37  price 25773.99 (open +0.24 R of the book stop): took a part [OB1: OB1]
  20:09:08  price 25773.39 (open +0.22 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:09:08  price 25773.39 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:09:08  price 25773.39 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25773.54

**AS-VWAPBRK (Asia MF3)** 2026-02-04 23:49:39 ET, LONG 6 lots at 25008.92, safety stop 24941.73 (1.5 x own stop 44.7917 pts). Result managed +16 pts/lot (+0.36 R, $+1943) ; own bracket: not taken (slot effect). MFE +0.47 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  23:49:40  price 25005.56 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  23:50:54  price 25025.71 (open +0.38 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  23:50:54  price 25025.71 (open +0.38 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  23:50:54  price 25025.71 (open +0.38 R of the book stop): took a part [OB1: OB1]
  23:51:10  price 25024.37 (open +0.35 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  23:51:10  price 25024.37 (open +0.35 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25025.17

**AS-NR7 (Asia MF1)** 2026-03-23 18:48:03 ET, LONG 6 lots at 24449.50, safety stop 24389.94 (1.5 x own stop 39.7083 pts). Result managed +12 pts/lot (+0.30 R, $+1408) ; own bracket: not taken (slot effect). MFE +0.47 R, MAE -0.08 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:48:04  price 24449.50 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:49:03  price 24451.29 (open +0.04 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:49:38  price 24448.31 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:52:03  price 24460.22 (open +0.27 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:52:03  price 24460.22 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:52:03  price 24460.22 (open +0.27 R of the book stop): took a part [OB1: OB1]
  18:53:08  price 24463.79 (open +0.36 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:53:08  price 24463.79 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:53:08  price 24463.79 (open +0.36 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24461.29

**AS-VWAPBRK (Asia MF3)** 2026-03-24 19:10:19 ET, SHORT 6 lots at 24419.42, safety stop 24486.60 (1.5 x own stop 44.7917 pts). Result managed -6 pts/lot (-0.12 R, $-667) ; own bracket: not taken (slot effect). MFE +0.41 R, MAE -0.55 R, 28 min under water (longest 25 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:W 5m:N 27m:A 32m:N
  19:10:21  price 24419.42 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:11:22  price 24421.43 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:22:11  price 24436.89 (open -0.39 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:22:26  price 24436.21 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:25:14  price 24440.92 (open -0.48 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:25:14  price 24440.92 (open -0.48 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  19:25:14  price 24440.92 (open -0.48 R of the book stop): took a part [DF: DF]
  19:25:31  price 24439.57 (open -0.45 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:25:47  price 24438.90 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:26:03  price 24440.24 (open -0.46 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:26:19  price 24441.59 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:26:34  price 24441.59 (open -0.49 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:27:07  price 24437.56 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:27:53  price 24441.59 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:28:09  price 24440.92 (open -0.48 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:28:25  price 24438.23 (open -0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:38:15  price 24436.89 (open -0.39 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  19:38:51  price 24430.84 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:00:59  price 24405.31 (open +0.32 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  20:00:59  price 24405.31 (open +0.32 R of the book stop): moved the stop closer [OB1: OB1]
  20:01:14  price 24407.32 (open +0.27 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  20:01:14  price 24407.32 (open +0.27 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24424.92

**AS-VWAPBRK (Asia MF3)** 2026-04-09 19:46:34 ET, SHORT 6 lots at 25219.79, safety stop 25286.98 (1.5 x own stop 44.7917 pts). Result managed -2 pts/lot (-0.04 R, $-247) ; own bracket: not taken (slot effect). MFE +0.28 R, MAE -0.43 R, 15 min under water (longest 13 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 14m:N 18m:W 19m:N
  19:46:39  price 25219.12 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  19:47:34  price 25226.51 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:47:50  price 25227.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:48:05  price 25233.23 (open -0.30 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:48:05  price 25233.23 (open -0.30 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  19:48:05  price 25233.23 (open -0.30 R of the book stop): took a part [DF: DF]
  19:48:20  price 25231.21 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:48:51  price 25227.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:49:07  price 25227.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:50:31  price 25227.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:50:46  price 25231.21 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:51:18  price 25227.85 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:55:19  price 25231.21 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:55:42  price 25229.20 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:56:32  price 25233.23 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  19:56:47  price 25232.56 (open -0.29 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  19:57:11  price 25231.89 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:00:30  price 25214.42 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:00:45  price 25217.78 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:03  price 25213.07 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:02:18  price 25218.45 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:02:33  price 25218.45 (open +0.03 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  20:02:52  price 25219.79 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:04:11  price 25209.04 (open +0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:05:43  price 25217.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:07:19  price 25212.40 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:07:35  price 25213.74 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:07:50  price 25209.04 (open +0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:07:50  price 25209.04 (open +0.24 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  20:07:50  price 25209.04 (open +0.24 R of the book stop): moved the stop closer [OB1: OB1]
  20:08:25  price 25209.71 (open +0.22 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  20:08:25  price 25209.71 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25221.79

**AS-NR7 (Asia MF1)** 2026-04-19 18:40:04 ET, LONG 6 lots at 26645.42, safety stop 26585.85 (1.5 x own stop 39.7083 pts). Result managed +7 pts/lot (+0.17 R, $+823) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -0.14 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:W
  18:40:05  price 26644.23 (open -0.03 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  18:41:04  price 26639.46 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:44:19  price 26654.95 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:44:19  price 26654.95 (open +0.24 R of the book stop): took a part [OB1: OB1]
  18:44:34  price 26651.37 (open +0.15 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:44:34  price 26651.37 (open +0.15 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 26652.33

**AS-VWAPBRK (Asia MF3)** 2026-05-03 20:01:28 ET, SHORT 6 lots at 27812.79, safety stop 27879.98 (1.5 x own stop 44.7917 pts). Result managed -59 pts/lot (-1.32 R, $-7122) ; own bracket: not taken (slot effect). MFE +0.13 R, MAE -1.48 R, 53 min under water (longest 33 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 5m:A
  20:01:29  price 27812.79 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:07:45  price 27862.51 (open -1.11 R of the book stop): state change desk [DEFEND/NAA-N-: DEFEND/NAA-N-]
  20:07:45  price 27862.51 (open -1.11 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  20:07:45  price 27862.51 (open -1.11 R of the book stop): took a part [DF: DF]
  20:08:00  price 27861.84 (open -1.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:08:15  price 27858.48 (open -1.02 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:09:32  price 27865.87 (open -1.19 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:10:18  price 27863.18 (open -1.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:17:43  price 27834.29 (open -0.48 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:22:04  price 27810.78 (open +0.04 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  20:22:35  price 27814.81 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:28:31  price 27841.68 (open -0.65 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:30:21  price 27834.96 (open -0.49 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:31:10  price 27843.03 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:37:19  price 27838.32 (open -0.57 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:38:22  price 27843.70 (open -0.69 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:42:03  price 27859.15 (open -1.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:46:19  price 27861.17 (open -1.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:46:34  price 27871.24 (open -1.30 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:51:03  price 27871.24 (open -1.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:53:42  price 27873.93 (open -1.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:54:12  price 27872.59 (open -1.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:55:36  price 27875.95 (open -1.41 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 27872.08

**AS-VWAPBRK (Asia MF3)** 2026-05-31 18:10:03 ET, SHORT 6 lots at 30379.50, safety stop 30446.69 (1.5 x own stop 44.7917 pts). Result managed -60 pts/lot (-1.33 R, $-7167) ; own bracket: not taken (slot effect). MFE +0.15 R, MAE -1.49 R, 32 min under water (longest 32 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 4m:A
  18:20:05  price 30411.08 (open -0.70 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:20:20  price 30400.33 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:22:20  price 30417.12 (open -0.84 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:22:36  price 30417.80 (open -0.85 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:23:08  price 30416.45 (open -0.83 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:23:23  price 30415.78 (open -0.81 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:23:58  price 30424.52 (open -1.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:24:47  price 30429.89 (open -1.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:25:03  price 30427.88 (open -1.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:25:55  price 30431.23 (open -1.16 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:25:55  price 30431.23 (open -1.16 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  18:25:55  price 30431.23 (open -1.16 R of the book stop): took a part [DF: DF]
  18:27:07  price 30431.23 (open -1.16 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:27:29  price 30431.91 (open -1.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:30:39  price 30440.64 (open -1.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:31:14  price 30437.95 (open -1.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:32:02  price 30432.58 (open -1.19 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:32:48  price 30437.95 (open -1.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:34:06  price 30431.91 (open -1.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:34:36  price 30437.95 (open -1.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  18:35:14  price 30435.27 (open -1.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:36:21  price 30440.64 (open -1.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:36:37  price 30439.97 (open -1.35 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:36:56  price 30439.30 (open -1.33 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:37:12  price 30436.61 (open -1.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:40:39  price 30440.64 (open -1.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:41:12  price 30439.30 (open -1.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:41:29  price 30439.97 (open -1.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  18:42:00  price 30444.00 (open -1.44 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  18:42:00  price 30444.00 (open -1.44 R of the book stop): state change DEFENDING>OUT [AB: AB]
  18:42:00  price 30444.00 (open -1.44 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 30439.17

**AS-NR7 (Asia MF1)** 2026-06-07 21:44:03 ET, LONG 6 lots at 29142.17, safety stop 29082.60 (1.5 x own stop 39.7083 pts). Result managed +20 pts/lot (+0.51 R, $+2403) ; own bracket: not taken (slot effect). MFE +0.66 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  21:44:05  price 29144.55 (open +0.06 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  21:45:03  price 29163.61 (open +0.54 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  21:45:03  price 29163.61 (open +0.54 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  21:45:03  price 29163.61 (open +0.54 R of the book stop): took a part [OB1: OB1]
  21:45:18  price 29164.80 (open +0.57 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  21:45:18  price 29164.80 (open +0.57 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29162.25

**AS-VWAPBRK (Asia MF3)** 2026-06-10 20:01:44 ET, LONG 6 lots at 28403.21, safety stop 28336.02 (1.5 x own stop 44.7917 pts). Result managed -65 pts/lot (-1.45 R, $-7802) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -1.48 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  20:01:46  price 28400.52 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:04:31  price 28358.86 (open -0.99 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  exit: Stop at 28338.25

**AS-VWAPBRK (Asia MF3)** 2026-06-22 18:39:09 ET, SHORT 6 lots at 30587.71, safety stop 30654.90 (1.5 x own stop 44.7917 pts). Result managed +14 pts/lot (+0.30 R, $+1628) ; own bracket: not taken (slot effect). MFE +0.51 R, MAE -0.16 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  18:39:10  price 30592.41 (open -0.11 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  18:40:09  price 30587.71 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:40:56  price 30586.36 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:44:16  price 30576.29 (open +0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  18:44:16  price 30576.29 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:44:16  price 30576.29 (open +0.26 R of the book stop): took a part [OB1: OB1]
  18:44:46  price 30571.58 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:44:46  price 30571.58 (open +0.36 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30574.08

**AS-VWAPBRK (Asia MF3)** 2026-06-25 20:16:43 ET, LONG 6 lots at 29739.88, safety stop 29672.69 (1.5 x own stop 44.7917 pts). Result managed +21 pts/lot (+0.48 R, $+2548) ; own bracket: not taken (slot effect). MFE +0.65 R, MAE -0.17 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  20:16:44  price 29737.86 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:17:43  price 29761.38 (open +0.48 R of the book stop): state change PROBE>OUT [DV: DV]
  20:17:43  price 29761.38 (open +0.48 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29761.17

**AS-NR7 (Asia MF1)** 2026-06-28 19:32:05 ET, LONG 6 lots at 29660.00, safety stop 29600.44 (1.5 x own stop 39.7083 pts). Result managed +6 pts/lot (+0.16 R, $+763) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  19:32:07  price 29657.62 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  19:35:19  price 29667.74 (open +0.20 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  19:35:19  price 29667.74 (open +0.20 R of the book stop): took a part [OB1: OB1]
  19:35:35  price 29667.15 (open +0.18 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  19:35:35  price 29667.15 (open +0.18 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29666.42

**AS-VWAPBRK (Asia MF3)** 2026-07-28 18:27:04 ET, SHORT 6 lots at 27931.46, safety stop 27998.65 (1.5 x own stop 44.7917 pts). Result managed +24 pts/lot (+0.55 R, $+2923) ; own bracket: not taken (slot effect). MFE +1.09 R, MAE -0.26 R, 5 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 5m:W
  18:27:05  price 27933.47 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:32:09  price 27915.33 (open +0.36 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  18:32:09  price 27915.33 (open +0.36 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:32:09  price 27915.33 (open +0.36 R of the book stop): took a part [OB1: OB1]
  18:32:24  price 27891.82 (open +0.89 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:32:24  price 27891.82 (open +0.89 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 27907.04

**AS-VWAPBRK (Asia MF3)** 2026-08-03 18:07:54 ET, LONG 6 lots at 28942.25, safety stop 28875.06 (1.5 x own stop 44.7917 pts). Result managed +10 pts/lot (+0.23 R, $+1218) ; own bracket: not taken (slot effect). MFE +0.43 R, MAE -0.39 R, 4 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 4m:W 13m:N 27m:W
  18:07:55  price 28939.56 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:11:08  price 28946.95 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  18:11:28  price 28948.30 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:13:59  price 28932.84 (open -0.21 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  18:14:14  price 28928.14 (open -0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  18:39:23  price 28953.67 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  18:39:23  price 28953.67 (open +0.26 R of the book stop): took a part [OB1: OB1]
  18:39:38  price 28953.00 (open +0.24 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  18:39:38  price 28953.00 (open +0.24 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 28952.46

**AS-NR7 (Asia MF1)** 2026-09-03 22:12:03 ET, LONG 6 lots at 29549.96, safety stop 29490.40 (1.5 x own stop 39.7083 pts). Result managed +11 pts/lot (+0.28 R, $+1343) ; own bracket: not taken (slot effect). MFE +0.43 R, MAE -0.08 R, 4 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 19m:W
  22:12:05  price 29549.36 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:28:13  price 29553.53 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:28:48  price 29553.53 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:29:05  price 29553.53 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:29:20  price 29552.94 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  22:29:56  price 29554.72 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  22:30:26  price 29560.08 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  22:30:26  price 29560.08 (open +0.26 R of the book stop): took a part [OB1: OB1]
  22:31:28  price 29563.06 (open +0.33 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  22:31:28  price 29563.06 (open +0.33 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29561.21

**AS-NR7 (Asia MF1)** 2026-10-11 20:44:03 ET, LONG 6 lots at 31254.50, safety stop 31194.94 (1.5 x own stop 39.7083 pts). Result managed -30 pts/lot (-0.76 R, $-3617) ; own bracket: not taken (slot effect). MFE +0.01 R, MAE -1.08 R, 8 min under water (longest 8 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  20:44:05  price 31254.50 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:45:04  price 31247.35 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:45:56  price 31247.35 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:47:24  price 31247.35 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:49:30  price 31238.42 (open -0.41 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:49:45  price 31236.63 (open -0.45 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:49:45  price 31236.63 (open -0.45 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  20:49:45  price 31236.63 (open -0.45 R of the book stop): took a part [DF: DF]
  20:50:00  price 31234.84 (open -0.49 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  20:51:00  price 31221.15 (open -0.84 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  20:52:00  price 31212.81 (open -1.05 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  20:52:00  price 31212.81 (open -1.05 R of the book stop): state change DEFENDING>OUT [AB: AB]
  20:52:00  price 31212.81 (open -1.05 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 31224.42

**AS-VWAPBRK (Asia MF3)** 2026-10-12 20:11:18 ET, SHORT 6 lots at 30774.58, safety stop 30841.77 (1.5 x own stop 44.7917 pts). Result managed +4 pts/lot (+0.10 R, $+523) ; own bracket: not taken (slot effect). MFE +0.35 R, MAE -0.73 R, 5 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  20:11:20  price 30774.58 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  20:12:18  price 30763.16 (open +0.26 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  20:12:18  price 30763.16 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  20:12:18  price 30763.16 (open +0.26 R of the book stop): took a part [OB1: OB1]
  20:12:48  price 30769.21 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  20:13:03  price 30778.61 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:14:03  price 30791.38 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  20:14:33  price 30794.74 (open -0.45 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:15:18  price 30797.43 (open -0.51 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  20:16:18  price 30786.68 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  20:17:35  price 30775.26 (open -0.01 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  20:17:35  price 30775.26 (open -0.01 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30770.17

**AS-NR7 (Asia MF1)** 2026-10-20 21:48:03 ET, LONG 6 lots at 29991.75, safety stop 29932.19 (1.5 x own stop 39.7083 pts). Result managed +7 pts/lot (+0.16 R, $+778) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  21:48:04  price 29987.58 (open -0.11 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  21:49:04  price 29986.39 (open -0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:49:19  price 29983.41 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:50:20  price 29989.96 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  21:50:50  price 29989.37 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  21:57:18  price 29998.90 (open +0.18 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  21:57:18  price 29998.90 (open +0.18 R of the book stop): took a part [OB1: OB1]
  21:57:33  price 29998.90 (open +0.18 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  21:57:33  price 29998.90 (open +0.18 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29998.29

# DK22 PART: LO

# London (LO): managed rows DK22MAIN_A, 4172 trades from 74 finished (set, month) rows, matched to the book's own bracket on 2126 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 2 | +6210 | 2024 +1290, 2026 +4920 |
| winners cut short | 537 | -1797060 | 2023 -123135, 2024 -458060, 2025 -598260, 2026 -617605 |
| losers cut early | 336 | +1778470 | 2023 +74635, 2024 +444090, 2025 +550410, 2026 +709335 |
| losers made worse | 8 | -39275 | 2024 -15375, 2025 -11190, 2026 -12710 |
| matched pairs (all) | 2126 | -477295 | 2023 -71155, 2024 -164245, 2025 -185055, 2026 -56840 |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 2046 trades, net $ -118173; entries that exist only under the own bracket in the same months (blocked by a carried trade): 636 trades, net $ +25855. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## London: the 20 WORST give-backs (largest open profit given back, $)

**LO-CRUDE (London MF1)** 2025-04-09 07:41:14 ET, LONG 8 lots at 16931.81, safety stop 16797.52 (1.5 x own stop 89.5312 pts). Result managed +88 pts/lot (+0.98 R, $+14101) ; own bracket result +30 pts (+0.33 R, $+4781). MFE +2.33 R, MAE -0.63 R, 6 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  07:41:15  price 16923.75 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:42:14  price 16904.95 (open -0.30 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:43:14  price 16922.41 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:44:29  price 16896.90 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:44:44  price 16894.21 (open -0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:44:59  price 16914.35 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:45:14  price 16876.75 (open -0.61 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:47:59  price 16911.67 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:48:14  price 16939.87 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:48:34  price 17119.83 (open +2.10 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  07:48:34  price 17119.83 (open +2.10 R of the book stop): state change PROBE>RUNNER [RT: RT]
  07:48:34  price 17119.83 (open +2.10 R of the book stop): moved the stop closer [RT: RT]
  exit: Stop at 17020.00

**LO-CRUDE (London MF1)** 2024-10-04 08:24:31 ET, LONG 8 lots at 20074.56, safety stop 19940.27 (1.5 x own stop 89.5312 pts). Result managed -14 pts/lot (-0.16 R, $-2289) ; own bracket result -14 pts (-0.16 R, $-2289). MFE +0.86 R, MAE -0.16 R, 5 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  08:24:32  price 20071.88 (open -0.03 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  08:25:32  price 20065.16 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  08:26:56  price 20065.16 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:27:11  price 20065.16 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  08:27:33  price 20069.19 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:28:37  price 20066.50 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: UWTime at 20060.31

**LO-CRUDE (London MF1)** 2025-04-09 07:01:04 ET, LONG 8 lots at 17037.94, safety stop 16903.64 (1.5 x own stop 89.5312 pts). Result managed -19 pts/lot (-0.22 R, $-3109) ; own bracket result +30 pts (+0.34 R, $+4801). MFE +0.69 R, MAE -1.22 R, 5 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  07:01:05  price 17056.74 (open +0.21 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:02:04  price 17046.00 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:02:19  price 17004.36 (open -0.38 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:02:34  price 17007.05 (open -0.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:02:49  price 16961.39 (open -0.85 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:02:49  price 16961.39 (open -0.85 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:02:49  price 16961.39 (open -0.85 R of the book stop): took a part [DF: DF]
  07:03:34  price 16993.62 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  07:03:49  price 17048.68 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:04:19  price 17017.79 (open -0.22 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  07:05:04  price 17023.16 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:06:19  price 16996.31 (open -0.46 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  07:06:34  price 17031.22 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:07:04  price 17083.60 (open +0.51 R of the book stop): state change DEFENDING>OUT [DV: DV]
  07:07:04  price 17083.60 (open +0.51 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 17018.56

**LO-CRUDE (London MF1)** 2026-06-08 04:32:12 ET, LONG 8 lots at 29253.19, safety stop 29118.89 (1.5 x own stop 89.5312 pts). Result managed +1 pts/lot (+0.02 R, $+221) ; own bracket result -91 pts (-1.02 R, $-14559). MFE +0.91 R, MAE -1.20 R, 152 min under water (longest 119 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 3m:W 8m:A
  04:32:13  price 29253.19 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:13  price 29249.16 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:35:32  price 29245.13 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:39:36  price 29220.96 (open -0.36 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:40:53  price 29204.84 (open -0.54 R of the book stop): state change desk [NORMAL/AAN-W-: NORMAL/AAN-W-]
  04:41:08  price 29202.15 (open -0.57 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:41:08  price 29202.15 (open -0.57 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:41:08  price 29202.15 (open -0.57 R of the book stop): took a part [DF: DF]
  04:41:23  price 29200.81 (open -0.58 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  04:41:38  price 29192.75 (open -0.68 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:43:10  price 29195.44 (open -0.65 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:43:55  price 29206.18 (open -0.52 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:44:12  price 29202.15 (open -0.57 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:44:42  price 29199.47 (open -0.60 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:47:15  price 29168.58 (open -0.95 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:47:30  price 29173.95 (open -0.89 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:47:45  price 29165.89 (open -0.98 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:49:01  price 29191.41 (open -0.69 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:51:02  price 29173.95 (open -0.89 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  04:51:17  price 29175.30 (open -0.87 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:58:08  price 29175.30 (open -0.87 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:09:17  price 29155.15 (open -1.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:10:48  price 29164.55 (open -0.99 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:12:03  price 29171.27 (open -0.92 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:14:56  price 29187.38 (open -0.73 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:16:30  price 29192.75 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:16:45  price 29196.78 (open -0.63 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:18:39  price 29194.10 (open -0.66 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:21:13  price 29214.24 (open -0.43 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:28:35  price 29191.41 (open -0.69 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:28:50  price 29194.10 (open -0.66 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:30:08  price 29192.75 (open -0.68 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:30:40  price 29194.10 (open -0.66 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:30:58  price 29191.41 (open -0.69 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:35:39  price 29169.92 (open -0.93 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:36:09  price 29167.24 (open -0.96 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:37:24  price 29226.33 (open -0.30 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:37:40  price 29208.87 (open -0.49 R of the book stop): state change desk [NORMAL/WAN-N-: NORMAL/WAN-N-]
  05:37:55  price 29206.18 (open -0.52 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:39:13  price 29206.18 (open -0.52 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: ExAlgoAll_DV at 29254.62

**LO-CRUDE (London MF1)** 2026-07-08 07:44:12 ET, LONG 8 lots at 29117.75, safety stop 28983.45 (1.5 x own stop 89.5312 pts). Result managed -5 pts/lot (-0.06 R, $-829) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.71 R, MAE -0.63 R, 21 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  07:44:13  price 29111.04 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:45:12  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:47:47  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:48:02  price 29069.40 (open -0.54 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:48:47  price 29090.89 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:49:02  price 29097.61 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:49:17  price 29094.92 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:49:32  price 29086.86 (open -0.35 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:49:47  price 29078.80 (open -0.43 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): took a part [DF: DF]
  07:50:32  price 29062.69 (open -0.61 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:51:33  price 29065.37 (open -0.58 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:52:03  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:52:18  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:53:34  price 29080.15 (open -0.42 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:54:07  price 29094.92 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:57:25  price 29084.18 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:58:28  price 29078.80 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:59:32  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:59:47  price 29081.49 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:00:17  price 29065.37 (open -0.58 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  08:01:32  price 29072.09 (open -0.51 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  08:01:48  price 29082.83 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:02:03  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:02:56  price 29088.20 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:07:03  price 29145.95 (open +0.32 R of the book stop): state change DEFENDING>FREE [NB: NB]
  08:07:03  price 29145.95 (open +0.32 R of the book stop): moved the stop closer [NB: NB]
  08:07:33  price 29167.44 (open +0.55 R of the book stop): state change FREE>OUT [DV: DV]
  08:07:33  price 29167.44 (open +0.55 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29112.62

**LO-CRUDE (London MF1)** 2026-03-02 02:08:30 ET, SHORT 8 lots at 24554.00, safety stop 24688.30 (1.5 x own stop 89.5312 pts). Result managed -4 pts/lot (-0.05 R, $-699) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.59 R, MAE -0.31 R, 29 min under water (longest 8 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  02:09:30  price 24541.91 (open +0.14 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:09:45  price 24539.23 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:10:00  price 24541.91 (open +0.14 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:10:15  price 24543.26 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:10:30  price 24547.29 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:10:45  price 24563.40 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:11:15  price 24555.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:12:01  price 24563.40 (open -0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:12:36  price 24568.77 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:13:51  price 24568.77 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:14:07  price 24560.71 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:16:23  price 24568.77 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:16:55  price 24566.09 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:17:10  price 24575.49 (open -0.24 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:17:58  price 24560.71 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:18:46  price 24544.60 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:19:16  price 24545.94 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:20:50  price 24533.86 (open +0.22 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:21:52  price 24551.31 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:22:07  price 24555.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:22:22  price 24564.74 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:22:37  price 24571.46 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:22:52  price 24568.77 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  02:23:07  price 24580.86 (open -0.30 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:23:22  price 24579.52 (open -0.29 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  02:23:37  price 24582.20 (open -0.32 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  02:23:37  price 24582.20 (open -0.32 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  02:23:37  price 24582.20 (open -0.32 R of the book stop): took a part [DF: DF]
  02:24:37  price 24576.83 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:25:07  price 24574.14 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:25:53  price 24586.23 (open -0.36 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  02:26:08  price 24576.83 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:26:23  price 24583.55 (open -0.33 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:26:38  price 24578.17 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:30:46  price 24556.69 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:31:17  price 24558.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:35:05  price 24552.66 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:39:44  price 24564.74 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:51:13  price 24559.37 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:00:27  price 24515.05 (open +0.43 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  exit: Stop at 24558.31

**LO-CRUDE (London MF1)** 2026-02-02 04:00:10 ET, LONG 8 lots at 25400.56, safety stop 25266.27 (1.5 x own stop 89.5312 pts). Result managed +4 pts/lot (+0.05 R, $+656) ; own bracket result +30 pts (+0.33 R, $+4781). MFE +0.63 R, MAE -0.48 R, 18 min under water (longest 18 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 7m:A
  04:00:11  price 25400.56 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:01:10  price 25395.19 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:01:25  price 25392.50 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:02:26  price 25387.13 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:03:41  price 25387.13 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:12  price 25376.39 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:05:27  price 25381.76 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:59  price 25376.39 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): took a part [DF: DF]
  04:07:48  price 25368.33 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:08:37  price 25362.96 (open -0.42 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:09:22  price 25372.36 (open -0.32 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:10:10  price 25384.45 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:14:31  price 25375.05 (open -0.29 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:14:48  price 25388.48 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:19:10  price 25403.25 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:21:28  price 25434.14 (open +0.38 R of the book stop): state change DEFENDING>FREE [NB: NB]
  04:21:28  price 25434.14 (open +0.38 R of the book stop): moved the stop closer [NB: NB]
  04:21:43  price 25439.51 (open +0.43 R of the book stop): state change FREE>RUNNER [OB1: OB1]
  04:21:43  price 25439.51 (open +0.43 R of the book stop): moved the stop closer [OB1: OB1]
  04:22:13  price 25451.60 (open +0.57 R of the book stop): state change RUNNER>OUT [DV: DV]
  04:22:13  price 25451.60 (open +0.57 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 25404.72

**LO-CRUDE (London MF1)** 2026-10-15 04:41:46 ET, SHORT 8 lots at 29812.25, safety stop 29946.55 (1.5 x own stop 89.5312 pts). Result managed -2 pts/lot (-0.03 R, $-379) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.55 R, MAE -0.97 R, 123 min under water (longest 121 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 3m:N 7m:A
  04:41:47  price 29812.25 (open -0.00 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  04:43:02  price 29817.62 (open -0.06 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  04:43:49  price 29809.56 (open +0.03 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  04:44:04  price 29816.28 (open -0.04 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  04:48:24  price 29849.85 (open -0.42 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  04:53:02  price 29863.28 (open -0.57 R of the book stop): state change desk [DEFEND/ANA---: DEFEND/ANA---]
  04:53:02  price 29863.28 (open -0.57 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:53:02  price 29863.28 (open -0.57 R of the book stop): took a part [DF: DF]
  04:53:17  price 29861.94 (open -0.55 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  04:55:38  price 29870.00 (open -0.65 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:01:04  price 29845.82 (open -0.38 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:01:19  price 29844.48 (open -0.36 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:04:38  price 29865.97 (open -0.60 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  05:05:11  price 29855.22 (open -0.48 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:07:37  price 29868.65 (open -0.63 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  05:07:54  price 29861.94 (open -0.55 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:09:57  price 29880.74 (open -0.77 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  05:10:12  price 29887.46 (open -0.84 R of the book stop): state change desk [DEFEND/ANA---: DEFEND/ANA---]
  05:14:35  price 29891.49 (open -0.89 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  05:15:35  price 29880.74 (open -0.77 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:16:20  price 29863.28 (open -0.57 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:17:41  price 29868.65 (open -0.63 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:19:18  price 29868.65 (open -0.63 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:23:15  price 29857.91 (open -0.51 R of the book stop): state change desk [NORMAL/WAN---: NORMAL/WAN---]
  05:23:30  price 29856.57 (open -0.49 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:35:38  price 29857.91 (open -0.51 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:36:09  price 29856.57 (open -0.49 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:36:25  price 29859.25 (open -0.52 R of the book stop): state change desk [NORMAL/ANN---: NORMAL/ANN---]
  05:36:43  price 29856.57 (open -0.49 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:41:19  price 29857.91 (open -0.51 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:42:27  price 29857.91 (open -0.51 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:44:03  price 29855.22 (open -0.48 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:50:22  price 29829.71 (open -0.20 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:50:38  price 29837.77 (open -0.29 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:54:01  price 29853.88 (open -0.46 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:57:30  price 29857.91 (open -0.51 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:58:16  price 29851.20 (open -0.43 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:00:04  price 29851.20 (open -0.43 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:02:43  price 29839.11 (open -0.30 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:03:15  price 29843.14 (open -0.35 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  exit: ExAlgoAll_DV at 29814.56

**LO-CRUDE (London MF1)** 2026-10-05 06:57:39 ET, LONG 8 lots at 31024.00, safety stop 30889.70 (1.5 x own stop 89.5312 pts). Result managed -2 pts/lot (-0.02 R, $-289) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.53 R, MAE -0.41 R, 23 min under water (longest 19 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 5m:N 30m:W
  06:57:41  price 31022.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:00:27  price 31001.17 (open -0.26 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  07:00:27  price 31001.17 (open -0.26 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:00:27  price 31001.17 (open -0.26 R of the book stop): took a part [DF: DF]
  07:00:42  price 31002.51 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:01:12  price 31011.91 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  07:01:44  price 31015.94 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:02:16  price 31005.20 (open -0.21 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:04:16  price 31001.17 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:05:03  price 30993.11 (open -0.35 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:05:18  price 30995.80 (open -0.32 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:05:34  price 30999.83 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:09:04  price 30989.08 (open -0.39 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:10:20  price 30991.77 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:10:36  price 30989.08 (open -0.39 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:11:07  price 30990.43 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:27:19  price 31060.26 (open +0.41 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  07:27:19  price 31060.26 (open +0.41 R of the book stop): state change DEFENDING>FREE [NB: NB]
  07:27:19  price 31060.26 (open +0.41 R of the book stop): moved the stop closer [NB: NB]
  07:27:49  price 31054.89 (open +0.35 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:28:04  price 31044.14 (open +0.22 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:28:19  price 31038.77 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:28:34  price 31042.80 (open +0.21 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:28:49  price 31049.52 (open +0.29 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:28:49  price 31049.52 (open +0.29 R of the book stop): state change FREE>RUNNER [OB1: OB1]
  07:28:49  price 31049.52 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 31022.25

**LO-CRUDE (London MF1)** 2025-12-10 05:34:13 ET, LONG 8 lots at 25645.47, safety stop 25511.17 (1.5 x own stop 89.5312 pts). Result managed -1 pts/lot (-0.01 R, $-174) ; own bracket result +30 pts (+0.34 R, $+4796). MFE +0.53 R, MAE -0.07 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 10m:W
  05:34:14  price 25646.81 (open +0.01 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:35:13  price 25646.81 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:35:29  price 25648.15 (open +0.03 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  05:36:20  price 25648.15 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:39:47  price 25650.84 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:40:19  price 25648.15 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:41:23  price 25649.50 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:41:38  price 25645.47 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:41:53  price 25649.50 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:43:32  price 25650.84 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:43:51  price 25650.84 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:46:11  price 25646.81 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:46:28  price 25646.81 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:47:01  price 25645.47 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:47:18  price 25648.15 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:00:12  price 25646.81 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:00:27  price 25685.76 (open +0.45 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  06:00:27  price 25685.76 (open +0.45 R of the book stop): state change PROBE>FREE [NB: NB]
  06:00:27  price 25685.76 (open +0.45 R of the book stop): moved the stop closer [NB: NB]
  06:00:42  price 25664.27 (open +0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:01:12  price 25653.53 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:01:27  price 25661.58 (open +0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:01:42  price 25656.21 (open +0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:01:57  price 25658.90 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:02:27  price 25650.84 (open +0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: Stop at 25644.44

**LO-CRUDE (London MF1)** 2024-03-01 04:07:19 ET, SHORT 8 lots at 18117.91, safety stop 18252.20 (1.5 x own stop 89.5312 pts). Result managed +29 pts/lot (+0.33 R, $+4656) ; own bracket result +30 pts (+0.33 R, $+4776). MFE +0.85 R, MAE -0.31 R, 63 min under water (longest 56 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 61m:N
  04:08:20  price 18121.94 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:09:05  price 18125.96 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:09:20  price 18127.31 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:09:35  price 18129.99 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:09:35  price 18129.99 (open -0.14 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:09:35  price 18129.99 (open -0.14 R of the book stop): took a part [DF: DF]
  04:09:50  price 18129.99 (open -0.14 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:10:05  price 18131.34 (open -0.15 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:10:20  price 18127.31 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:10:37  price 18129.99 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:10:52  price 18132.68 (open -0.17 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  04:11:07  price 18132.68 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:11:52  price 18128.65 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:12:54  price 18127.31 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:13:09  price 18127.31 (open -0.11 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  04:13:28  price 18127.31 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:15:15  price 18131.34 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:16:02  price 18134.02 (open -0.18 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:16:35  price 18135.36 (open -0.20 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:19:41  price 18135.36 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:19:57  price 18136.71 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:22:32  price 18138.05 (open -0.22 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  04:24:54  price 18140.74 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:25:24  price 18139.39 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  04:25:56  price 18140.74 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:26:11  price 18138.05 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:01  price 18132.68 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:31:17  price 18134.02 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:32  price 18132.68 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:33:04  price 18135.36 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:20  price 18134.02 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:33:35  price 18136.71 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:34:06  price 18134.02 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:34:39  price 18135.36 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:35:58  price 18140.74 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:38:00  price 18139.39 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:38:15  price 18140.74 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:38:31  price 18140.74 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:38:46  price 18143.42 (open -0.29 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:40:07  price 18142.08 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_OB2 at 18088.75

**LO-CRUDE (London MF1)** 2026-02-17 04:23:31 ET, SHORT 8 lots at 24648.09, safety stop 24782.39 (1.5 x own stop 89.5312 pts). Result managed +1 pts/lot (+0.01 R, $+76) ; own bracket: not taken (slot effect). MFE +0.52 R, MAE -0.54 R, 68 min under water (longest 53 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  04:23:38  price 24649.44 (open -0.01 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  04:24:31  price 24656.15 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:24:47  price 24658.84 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:25:18  price 24666.90 (open -0.21 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:28:36  price 24666.90 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:29:44  price 24672.27 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:32:37  price 24673.61 (open -0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:32:55  price 24676.30 (open -0.32 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:33:36  price 24674.95 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:52  price 24678.98 (open -0.35 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:34:07  price 24674.95 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:34:23  price 24676.30 (open -0.32 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:34:38  price 24669.58 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:35:26  price 24684.35 (open -0.41 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:38:13  price 24691.07 (open -0.48 R of the book stop): state change desk [DEFEND/NAA-N-: DEFEND/NAA-N-]
  04:38:13  price 24691.07 (open -0.48 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:38:13  price 24691.07 (open -0.48 R of the book stop): took a part [DF: DF]
  04:38:29  price 24689.73 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:39:39  price 24692.41 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:39:54  price 24688.38 (open -0.45 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:48:38  price 24678.98 (open -0.35 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:49:43  price 24683.01 (open -0.39 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:50:13  price 24681.67 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:53:34  price 24687.04 (open -0.43 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:54:00  price 24687.04 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:54:56  price 24688.38 (open -0.45 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:57:43  price 24689.73 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:20  price 24689.73 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:00:35  price 24688.38 (open -0.45 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:50  price 24691.07 (open -0.48 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:01:19  price 24685.70 (open -0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:01:34  price 24692.41 (open -0.49 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:04:39  price 24691.07 (open -0.48 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:09:13  price 24676.30 (open -0.32 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:09:43  price 24678.98 (open -0.35 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:10:29  price 24669.58 (open -0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:11:27  price 24670.92 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:12:01  price 24668.24 (open -0.22 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:23:10  price 24664.21 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:24:32  price 24661.52 (open -0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: ExAlgoAll_DV at 24647.56

**LO-CRUDE (London MF1)** 2026-05-06 04:51:16 ET, LONG 8 lots at 28432.72, safety stop 28298.42 (1.5 x own stop 89.5312 pts). Result managed +42 pts/lot (+0.47 R, $+6771) ; own bracket result +30 pts (+0.34 R, $+4796). MFE +0.98 R, MAE -0.25 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  04:51:17  price 28430.03 (open -0.03 R of the book stop): state change desk [NORMAL/WAW-N-: NORMAL/WAW-N-]
  04:52:16  price 28434.06 (open +0.01 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:52:46  price 28440.78 (open +0.09 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  04:53:31  price 28443.46 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:53:46  price 28447.49 (open +0.17 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  04:54:01  price 28444.81 (open +0.14 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:54:16  price 28455.55 (open +0.26 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:54:16  price 28455.55 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:54:16  price 28455.55 (open +0.26 R of the book stop): took a part [OB1: OB1]
  04:54:31  price 28459.58 (open +0.30 R of the book stop): state change DEFENDING>FREE [NB: NB]
  04:54:31  price 28459.58 (open +0.30 R of the book stop): moved the stop closer [NB: NB]
  04:55:01  price 28460.92 (open +0.32 R of the book stop): state change desk [NORMAL/WAW-N-: NORMAL/WAW-N-]
  04:55:16  price 28468.98 (open +0.41 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:55:31  price 28486.44 (open +0.60 R of the book stop): moved the stop closer [NB: NB]
  04:55:46  price 28511.95 (open +0.89 R of the book stop): moved the stop closer [NB: NB]
  04:56:01  price 28502.55 (open +0.78 R of the book stop): state change desk [NORMAL/WAW-A-: NORMAL/WAW-A-]
  04:56:16  price 28507.92 (open +0.84 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  04:56:46  price 28501.21 (open +0.77 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:57:01  price 28497.18 (open +0.72 R of the book stop): state change FREE>OUT [OB2: OB2]
  04:57:01  price 28497.18 (open +0.72 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 28475.09

**LO-CRUDE (London MF1)** 2025-06-11 05:04:17 ET, LONG 8 lots at 21940.09, safety stop 21805.80 (1.5 x own stop 89.5312 pts). Result managed +9 pts/lot (+0.10 R, $+1376) ; own bracket result +30 pts (+0.33 R, $+4776). MFE +0.59 R, MAE -0.65 R, 173 min under water (longest 142 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 4m:N 18m:A 61m:N 83m:A
  05:04:18  price 21940.09 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:05:17  price 21938.75 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:05:33  price 21936.06 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:06:43  price 21940.09 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:07:31  price 21938.75 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:25:09  price 21940.09 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:28:42  price 21936.06 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:29:24  price 21938.75 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:31:07  price 21940.09 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:35:00  price 21933.38 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:35:34  price 21934.72 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:35:52  price 21933.38 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:36:08  price 21933.38 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:36:23  price 21933.38 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:36:39  price 21933.38 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:37:14  price 21930.69 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:38:39  price 21932.04 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:43:19  price 21925.32 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:43:34  price 21926.66 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:47:38  price 21926.66 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:47:57  price 21926.66 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:50:21  price 21925.32 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:50:37  price 21923.98 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:50:52  price 21923.98 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:51:24  price 21918.61 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  05:51:55  price 21919.95 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:52:10  price 21917.26 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  05:52:28  price 21919.95 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:52:58  price 21918.61 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  05:53:34  price 21918.61 (open -0.24 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:53:53  price 21919.95 (open -0.22 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  05:54:22  price 21919.95 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:58:49  price 21915.92 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  05:59:36  price 21918.61 (open -0.24 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:02:15  price 21914.58 (open -0.29 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  06:02:30  price 21910.55 (open -0.33 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  06:02:48  price 21911.89 (open -0.32 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:02:48  price 21911.89 (open -0.32 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  06:02:48  price 21911.89 (open -0.32 R of the book stop): took a part [DF: DF]
  06:03:03  price 21914.58 (open -0.29 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: ExAlgoAll_DV at 21948.75

**LO-CRUDE (London MF1)** 2025-04-04 06:05:12 ET, SHORT 8 lots at 18571.25, safety stop 18705.55 (1.5 x own stop 89.5312 pts). Result managed +32 pts/lot (+0.35 R, $+5041) ; own bracket: not taken (slot effect). MFE +0.84 R, MAE -0.16 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  06:05:13  price 18576.62 (open -0.06 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  06:06:12  price 18556.48 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:06:27  price 18539.02 (open +0.36 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  06:06:27  price 18539.02 (open +0.36 R of the book stop): state change PROBE>FREE [NB: NB]
  06:06:27  price 18539.02 (open +0.36 R of the book stop): moved the stop closer [NB: NB]
  06:06:42  price 18510.82 (open +0.68 R of the book stop): moved the stop closer [NB: NB]
  exit: Stop at 18539.69

**LO-CRUDE (London MF1)** 2026-06-30 04:16:01 ET, SHORT 8 lots at 30077.88, safety stop 30212.17 (1.5 x own stop 89.5312 pts). Result managed +10 pts/lot (+0.11 R, $+1606) ; own bracket result +30 pts (+0.33 R, $+4771). MFE +0.60 R, MAE -0.60 R, 17 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 10m:A
  04:16:02  price 30079.22 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:17:01  price 30084.59 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:17:20  price 30080.56 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:17:36  price 30080.56 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:18:22  price 30083.25 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:19:27  price 30085.93 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:20:03  price 30092.65 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:20:34  price 30093.99 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:20:49  price 30099.36 (open -0.24 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  04:21:20  price 30104.73 (open -0.30 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  04:21:20  price 30104.73 (open -0.30 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:21:20  price 30104.73 (open -0.30 R of the book stop): took a part [DF: DF]
  04:21:36  price 30106.08 (open -0.32 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  04:23:16  price 30110.11 (open -0.36 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:26:30  price 30118.16 (open -0.45 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:28:24  price 30122.19 (open -0.49 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:28:56  price 30122.19 (open -0.49 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:30:04  price 30127.56 (open -0.55 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:31:08  price 30108.76 (open -0.35 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:31:23  price 30110.11 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:39:17  price 30048.33 (open +0.33 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:39:17  price 30048.33 (open +0.33 R of the book stop): state change DEFENDING>FREE [NB: NB]
  04:39:17  price 30048.33 (open +0.33 R of the book stop): moved the stop closer [NB: NB]
  04:39:32  price 30048.33 (open +0.33 R of the book stop): state change FREE>RUNNER [OB1: OB1]
  04:39:32  price 30048.33 (open +0.33 R of the book stop): moved the stop closer [OB1: OB1]
  04:40:17  price 30030.87 (open +0.52 R of the book stop): state change RUNNER>OUT [DV: DV]
  04:40:17  price 30030.87 (open +0.52 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 30067.78

**LO-CRUDE (London MF1)** 2026-06-05 04:29:10 ET, LONG 8 lots at 30208.69, safety stop 30074.39 (1.5 x own stop 89.5312 pts). Result managed +7 pts/lot (+0.08 R, $+1166) ; own bracket result +30 pts (+0.34 R, $+4801). MFE +0.57 R, MAE -0.67 R, 41 min under water (longest 34 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 16m:A
  04:29:12  price 30207.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:30:10  price 30219.43 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:30:25  price 30218.09 (open +0.11 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  04:30:40  price 30204.66 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:42  price 30208.69 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:31:57  price 30208.69 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:32:42  price 30215.40 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:33:12  price 30214.06 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:42:11  price 30180.49 (open -0.32 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:46:04  price 30179.14 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:52:50  price 30167.06 (open -0.46 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:55:11  price 30167.06 (open -0.46 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:57:34  price 30159.00 (open -0.55 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:59:08  price 30160.34 (open -0.54 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:59:26  price 30157.65 (open -0.57 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:59:59  price 30159.00 (open -0.55 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:03:41  price 30156.31 (open -0.58 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:03:57  price 30160.34 (open -0.54 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:08:34  price 30154.97 (open -0.60 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:09:05  price 30161.68 (open -0.52 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:09:20  price 30152.28 (open -0.63 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:10:00  price 30154.97 (open -0.60 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  05:10:16  price 30154.97 (open -0.60 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:10:31  price 30157.65 (open -0.57 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:11:19  price 30154.97 (open -0.60 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:12:06  price 30156.31 (open -0.58 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:13:14  price 30214.06 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:13:29  price 30227.49 (open +0.21 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:13:44  price 30220.77 (open +0.14 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  05:13:44  price 30220.77 (open +0.14 R of the book stop): took a part [OB1: OB1]
  05:13:59  price 30253.01 (open +0.49 R of the book stop): state change DEFENDING>FREE [NB: NB]
  05:13:59  price 30253.01 (open +0.49 R of the book stop): moved the stop closer [NB: NB]
  exit: Stop at 30216.03

**LO-CRUDE (London MF1)** 2025-04-04 08:16:19 ET, SHORT 8 lots at 18120.97, safety stop 18255.27 (1.5 x own stop 89.5312 pts). Result managed +6 pts/lot (+0.06 R, $+906) ; own bracket result +30 pts (+0.33 R, $+4786). MFE +0.52 R, MAE -0.39 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  08:16:20  price 18125.00 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:17:19  price 18125.00 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:20:21  price 18110.22 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:20:36  price 18090.08 (open +0.35 R of the book stop): state change PROBE>FREE [NB: NB]
  08:20:36  price 18090.08 (open +0.35 R of the book stop): moved the stop closer [NB: NB]
  08:20:51  price 18092.77 (open +0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:21:06  price 18106.20 (open +0.17 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  08:21:06  price 18106.20 (open +0.17 R of the book stop): took a part [OB1: OB1]
  exit: Stop at 18115.25

**LO-CRUDE (London MF1)** 2025-04-04 03:55:17 ET, LONG 8 lots at 18592.69, safety stop 18458.39 (1.5 x own stop 89.5312 pts). Result managed +13 pts/lot (+0.14 R, $+2031) ; own bracket result +30 pts (+0.34 R, $+4801). MFE +0.58 R, MAE -0.26 R, 12 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  03:55:18  price 18590.00 (open -0.03 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:56:17  price 18600.75 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:56:32  price 18595.37 (open +0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:58:48  price 18592.69 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:59:18  price 18581.94 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:59:48  price 18580.60 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:00:03  price 18579.26 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:00:18  price 18581.94 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:01:18  price 18580.60 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:01:33  price 18581.94 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:50  price 18576.57 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:06:05  price 18571.20 (open -0.24 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:06:05  price 18571.20 (open -0.24 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:06:05  price 18571.20 (open -0.24 R of the book stop): took a part [DF: DF]
  04:06:53  price 18575.23 (open -0.20 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:07:38  price 18571.20 (open -0.24 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:08:09  price 18579.26 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:08:24  price 18577.91 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:08:39  price 18577.91 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:08:56  price 18583.29 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:09:11  price 18591.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:14:59  price 18584.63 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:15:14  price 18590.00 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:16:15  price 18583.29 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:16:45  price 18587.32 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:17:16  price 18580.60 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:18:01  price 18587.32 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:19:34  price 18604.77 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:20:04  price 18616.86 (open +0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:20:19  price 18622.23 (open +0.33 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  04:20:19  price 18622.23 (open +0.33 R of the book stop): moved the stop closer [OB1: OB1]
  04:20:34  price 18634.32 (open +0.46 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:20:49  price 18641.03 (open +0.54 R of the book stop): state change RUNNER>OUT [DV: DV]
  04:20:49  price 18641.03 (open +0.54 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 18605.44

**LO-CRUDE (London MF1)** 2026-03-30 07:27:04 ET, LONG 8 lots at 23474.22, safety stop 23339.92 (1.5 x own stop 89.5312 pts). Result managed +7 pts/lot (+0.08 R, $+1091) ; own bracket result +30 pts (+0.34 R, $+4796). MFE +0.51 R, MAE -0.32 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  07:27:05  price 23474.22 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:28:04  price 23468.85 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:28:19  price 23458.10 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:28:34  price 23472.88 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:29:04  price 23483.62 (open +0.11 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:29:19  price 23474.22 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:29:34  price 23478.25 (open +0.04 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:30:04  price 23502.42 (open +0.32 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  07:30:04  price 23502.42 (open +0.32 R of the book stop): state change PROBE>FREE [NB: NB]
  07:30:04  price 23502.42 (open +0.32 R of the book stop): moved the stop closer [NB: NB]
  07:30:19  price 23488.99 (open +0.17 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:30:34  price 23491.68 (open +0.20 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  07:30:34  price 23491.68 (open +0.20 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  07:30:34  price 23491.68 (open +0.20 R of the book stop): took a part [OB1: OB1]
  07:30:49  price 23479.59 (open +0.06 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  exit: Stop at 23481.09

## London: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**LO-CRUDE (London MF1)** 2026-03-23 07:06:03 ET, LONG 8 lots at 24332.50, safety stop 24198.20 (1.5 x own stop 89.5312 pts). Result managed +257 pts/lot (+2.87 R, $+41096) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +3.17 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  07:06:04  price 24333.84 (open +0.01 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  07:07:03  price 24505.74 (open +1.94 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  07:07:03  price 24505.74 (open +1.94 R of the book stop): state change PROBE>FREE [NB: NB]
  07:07:03  price 24505.74 (open +1.94 R of the book stop): moved the stop closer [NB: NB]
  07:07:18  price 24574.23 (open +2.70 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  07:07:18  price 24574.23 (open +2.70 R of the book stop): took a part [OB1: OB1]
  07:07:33  price 24606.47 (open +3.06 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  07:07:33  price 24606.47 (open +3.06 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24589.41

**LO-ZB (London MF3)** 2026-03-23 07:06:03 ET, LONG 2 lots at 24330.00, safety stop 24151.12 (1.5 x own stop 119.25 pts). Result managed +260 pts/lot (+2.18 R, $+10383) ; own bracket result +60 pts (+0.50 R, $+2398). MFE +2.38 R, MAE -0.06 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  07:06:04  price 24333.58 (open +0.03 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  07:07:03  price 24505.30 (open +1.47 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  07:07:03  price 24505.30 (open +1.47 R of the book stop): state change PROBE>FREE [NB: NB]
  07:07:03  price 24505.30 (open +1.47 R of the book stop): moved the stop closer [NB: NB]
  07:07:18  price 24573.27 (open +2.04 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  07:07:18  price 24573.27 (open +2.04 R of the book stop): took a part [OB1: OB1]
  07:07:33  price 24605.47 (open +2.31 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  07:07:33  price 24605.47 (open +2.31 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24589.62

**LO-CRUDE (London MF1)** 2026-03-23 07:24:06 ET, SHORT 8 lots at 24558.31, safety stop 24692.61 (1.5 x own stop 89.5312 pts). Result managed +77 pts/lot (+0.87 R, $+12386) ; own bracket result +30 pts (+0.34 R, $+4801). MFE +1.00 R, MAE -0.59 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:A
  07:24:07  price 24558.31 (open +0.00 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  07:25:06  price 24575.77 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:27:36  price 24559.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:28:06  price 24495.19 (open +0.70 R of the book stop): state change PROBE>OUT [DV: DV]
  07:28:06  price 24495.19 (open +0.70 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 24480.84

## London: 50 RANDOM trades (seed 11)

**LO-ZB (London MF3)** 2023-10-26 03:12:17 ET, LONG 2 lots at 14288.25, safety stop 14109.38 (1.5 x own stop 119.25 pts). Result managed +14 pts/lot (+0.11 R, $+543) ; own bracket: not taken (slot effect). MFE +0.43 R, MAE -0.27 R, 34 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 6m:A 35m:N 36m:W 61m:N
  03:12:18  price 14288.25 (open +0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  03:13:17  price 14282.88 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  03:13:32  price 14290.04 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:14:02  price 14286.46 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  03:15:34  price 14284.67 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:19:54  price 14281.09 (open -0.06 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  03:20:39  price 14277.52 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:21:24  price 14273.94 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:21:24  price 14273.94 (open -0.12 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:21:24  price 14273.94 (open -0.12 R of the book stop): took a part [DF: DF]
  03:21:39  price 14270.36 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:22:09  price 14284.67 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:23:10  price 14279.31 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:23:25  price 14284.67 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:24:25  price 14279.31 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:25:11  price 14277.52 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:25:43  price 14275.73 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:29:46  price 14272.15 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:30:16  price 14266.78 (open -0.18 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:34:02  price 14261.42 (open -0.22 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:34:17  price 14263.21 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:34:32  price 14266.78 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:34:47  price 14263.21 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:35:18  price 14263.21 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:37:21  price 14268.57 (open -0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:37:52  price 14266.78 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:07  price 14272.15 (open -0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:39:40  price 14272.15 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:55  price 14273.94 (open -0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:41:26  price 14272.15 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:41:41  price 14272.15 (open -0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:48:32  price 14306.14 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:49:02  price 14302.56 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  03:49:17  price 14304.35 (open +0.14 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  03:49:32  price 14298.98 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  03:49:47  price 14304.35 (open +0.14 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:50:02  price 14304.35 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:50:32  price 14302.56 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:50:47  price 14302.56 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:51:02  price 14304.35 (open +0.14 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  exit: ExAlgoAll_OB2 at 14301.88

**LO-ZB (London MF3)** 2023-11-24 02:13:35 ET, SHORT 2 lots at 16038.00, safety stop 16216.88 (1.5 x own stop 119.25 pts). Result managed -10 pts/lot (-0.09 R, $-422) ; own bracket result +3 pts (+0.02 R, $+108). MFE +0.10 R, MAE -0.28 R, 146 min under water (longest 138 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 33m:N 187m:A
  02:13:37  price 16038.00 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:14:36  price 16036.21 (open +0.01 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:15:07  price 16036.21 (open +0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:17:22  price 16032.63 (open +0.04 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:20:23  price 16030.84 (open +0.06 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:20:41  price 16030.84 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:21:26  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:23:53  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:25:20  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:25:35  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:29:06  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:29:21  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:29:52  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NN--N-: NORMAL/NN--N-]
  02:30:13  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:31:21  price 16030.84 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:31:37  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:31:52  price 16030.84 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:32:07  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:32:41  price 16030.84 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:32:56  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:35:05  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:43:15  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:43:33  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:43:51  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:45:58  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:46:20  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:54:12  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:55:13  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:55:51  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:56:22  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:57:39  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:58:11  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:58:36  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:59:27  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:59:42  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:59:59  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:00:14  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:01:01  price 16034.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:02:17  price 16032.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:03:35  price 16030.84 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 16048.50

**LO-ZB (London MF3)** 2023-12-27 08:01:14 ET, LONG 2 lots at 17091.25, safety stop 16912.38 (1.5 x own stop 119.25 pts). Result managed +1 pts/lot (+0.01 R, $+48) ; own bracket: not taken (slot effect). MFE +0.03 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  08:01:15  price 17091.25 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:02:14  price 17093.04 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:02:14  price 17093.04 (open +0.01 R of the book stop): state change PROBE>OUT [CL: CL]
  08:02:14  price 17093.04 (open +0.01 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 17092.50

**LO-ZB (London MF3)** 2024-03-19 02:03:23 ET, SHORT 2 lots at 18197.25, safety stop 18376.12 (1.5 x own stop 119.25 pts). Result managed +20 pts/lot (+0.16 R, $+778) ; own bracket result +60 pts (+0.50 R, $+2398). MFE +0.32 R, MAE -0.03 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 61m:N
  02:03:28  price 18197.25 (open -0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  02:04:23  price 18193.67 (open +0.03 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:07:48  price 18179.36 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:08:03  price 18182.94 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:10:34  price 18177.57 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:11:04  price 18182.94 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:20:39  price 18188.31 (open +0.08 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  02:21:26  price 18186.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:23:05  price 18188.31 (open +0.08 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  02:23:37  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/AAW-N-: NORMAL/AAW-N-]
  02:23:57  price 18186.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:30:29  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:30:59  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:33:11  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:33:42  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:34:18  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:34:35  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:35:28  price 18191.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:37:04  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:37:36  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:41:11  price 18186.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:41:27  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:41:46  price 18186.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:43:07  price 18184.73 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:44:16  price 18184.73 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:45:11  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:46:34  price 18188.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:46:49  price 18190.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:47:09  price 18188.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:47:59  price 18188.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:50:51  price 18186.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:52:09  price 18182.94 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:54:19  price 18184.73 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:54:34  price 18184.73 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:54:57  price 18182.94 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:55:18  price 18182.94 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:55:36  price 18182.94 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:56:03  price 18182.94 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:59:18  price 18184.73 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:01:47  price 18172.21 (open +0.21 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  exit: ExAlgoAll_OB2 at 18177.75

**LO-CRUDE (London MF1)** 2024-03-20 06:56:11 ET, LONG 8 lots at 18291.06, safety stop 18156.77 (1.5 x own stop 89.5312 pts). Result managed +21 pts/lot (+0.24 R, $+3401) ; own bracket: not taken (slot effect). MFE +0.27 R, MAE -0.07 R, 5 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A 7m:W
  06:56:12  price 18291.06 (open -0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  06:57:11  price 18289.72 (open -0.01 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  06:57:27  price 18289.72 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:59:28  price 18288.38 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:59:47  price 18289.72 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:00:02  price 18288.38 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:01:04  price 18289.72 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:01:20  price 18287.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:02:23  price 18292.41 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:02:38  price 18296.43 (open +0.06 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:02:54  price 18295.09 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:03:13  price 18292.41 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:03:29  price 18295.09 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:06:00  price 18296.43 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:06:16  price 18296.43 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:06:31  price 18296.43 (open +0.06 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:07:05  price 18297.78 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:07:35  price 18300.46 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:07:50  price 18305.84 (open +0.17 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:09:22  price 18305.84 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:12:47  price 18312.55 (open +0.24 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:13:02  price 18313.89 (open +0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:13:02  price 18313.89 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  07:13:02  price 18313.89 (open +0.26 R of the book stop): took a part [OB1: OB1]
  07:13:17  price 18311.21 (open +0.22 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  07:13:17  price 18311.21 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18312.38

**LO-ZB (London MF3)** 2024-03-25 02:30:12 ET, LONG 2 lots at 18541.00, safety stop 18362.12 (1.5 x own stop 119.25 pts). Result managed -15 pts/lot (-0.13 R, $-602) ; own bracket result -59 pts (-0.49 R, $-2352). MFE +0.20 R, MAE -0.13 R, 41 min under water (longest 18 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 6m:A 15m:N
  02:30:13  price 18541.00 (open +0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  02:31:17  price 18541.00 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:31:47  price 18541.00 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:32:03  price 18541.00 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:42:04  price 18535.63 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:42:41  price 18535.63 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:57:24  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:57:40  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:58:16  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:00:14  price 18548.15 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:00:47  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:01:02  price 18549.94 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:01:18  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:08:54  price 18539.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:16:25  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:16:48  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:18:25  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:18:57  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:23:49  price 18544.58 (open +0.03 R of the book stop): state change desk [NORMAL/NN--N-: NORMAL/NN--N-]
  03:24:07  price 18544.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:26:50  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:27:56  price 18544.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:31:50  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:33:57  price 18544.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:44:57  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:45:12  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:45:50  price 18548.15 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:47:23  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:49:52  price 18542.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:52:00  price 18544.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:56:01  price 18548.15 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:56:17  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:56:34  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:56:53  price 18546.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:37  price 18555.31 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:06:57  price 18551.73 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:07:32  price 18549.94 (open +0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:07:48  price 18553.52 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:08:50  price 18555.31 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:10:06  price 18560.68 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  exit: ExAlgoAll_AB at 18526.00

**LO-ZB (London MF3)** 2024-05-03 02:16:52 ET, SHORT 2 lots at 17743.25, safety stop 17922.12 (1.5 x own stop 119.25 pts). Result managed -6 pts/lot (-0.05 R, $-252) ; own bracket result -13 pts (-0.11 R, $-512). MFE +0.19 R, MAE -0.16 R, 37 min under water (longest 17 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 30m:N 45m:W 61m:N
  02:16:54  price 17743.25 (open +0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  02:17:52  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:18:07  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:19:45  price 17745.04 (open -0.01 R of the book stop): state change desk [NORMAL/WNA-A-: NORMAL/WNA-A-]
  02:20:01  price 17741.46 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:21:19  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:21:36  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:21:51  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:22:26  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:22:41  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:22:56  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  02:23:13  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:25:09  price 17732.52 (open +0.09 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:25:24  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:25:56  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:27:15  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:27:32  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:28:03  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:29:00  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:32:18  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:33:09  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:34:16  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:34:33  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:36:57  price 17741.46 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:37:13  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:38:17  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:38:33  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:39:34  price 17739.67 (open +0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:40:29  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:49:19  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:49:35  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:53:10  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:53:42  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:54:02  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:54:21  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:55:38  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:55:57  price 17737.88 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:56:42  price 17736.10 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:58:07  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:59:24  price 17734.31 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  exit: ExAlgoAll_AB at 17749.50

**LO-ZB (London MF3)** 2024-06-05 07:39:35 ET, SHORT 2 lots at 18798.00, safety stop 18976.88 (1.5 x own stop 119.25 pts). Result managed -2 pts/lot (-0.02 R, $-77) ; own bracket: not taken (slot effect). MFE +0.06 R, MAE -0.15 R, 39 min under water (longest 39 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  07:39:37  price 18798.00 (open -0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  07:40:35  price 18806.94 (open -0.08 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:40:35  price 18806.94 (open -0.08 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:40:35  price 18806.94 (open -0.08 R of the book stop): took a part [DF: DF]
  07:41:52  price 18801.58 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:42:24  price 18799.79 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:42:39  price 18805.15 (open -0.06 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:43:39  price 18803.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:43:55  price 18803.37 (open -0.04 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:44:25  price 18801.58 (open -0.03 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:44:40  price 18799.79 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:46:58  price 18805.15 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:47:14  price 18806.94 (open -0.08 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:47:31  price 18805.15 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:48:17  price 18806.94 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:48:47  price 18806.94 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:49:04  price 18806.94 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:49:20  price 18808.73 (open -0.09 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:50:07  price 18810.52 (open -0.11 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  07:50:22  price 18812.31 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:51:55  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:52:25  price 18812.31 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:52:55  price 18814.10 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:54:59  price 18812.31 (open -0.12 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  07:55:14  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:57:19  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  07:57:34  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:03:30  price 18810.52 (open -0.11 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  08:03:45  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:09:29  price 18805.15 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:09:44  price 18806.94 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:10:14  price 18806.94 (open -0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:12:09  price 18803.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:12:40  price 18803.37 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:13:25  price 18803.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:15:26  price 18812.31 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:15:41  price 18808.73 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:16:11  price 18810.52 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:16:28  price 18808.73 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:16:43  price 18810.52 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: ExAlgoAll_CL at 18799.88

**LO-ZB (London MF3)** 2024-06-07 08:04:47 ET, SHORT 2 lots at 19095.00, safety stop 19273.88 (1.5 x own stop 119.25 pts). Result managed +4 pts/lot (+0.03 R, $+143) ; own bracket: not taken (slot effect). MFE +0.04 R, MAE -0.01 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  08:04:51  price 19093.21 (open +0.01 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  08:05:47  price 19091.42 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:05:47  price 19091.42 (open +0.03 R of the book stop): state change PROBE>OUT [CL: CL]
  08:05:47  price 19091.42 (open +0.03 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 19091.38

**LO-ZB (London MF3)** 2024-06-21 03:19:49 ET, LONG 2 lots at 20039.00, safety stop 19860.12 (1.5 x own stop 119.25 pts). Result managed -27 pts/lot (-0.23 R, $-1082) ; own bracket: not taken (slot effect). MFE +0.04 R, MAE -0.34 R, 50 min under water (longest 25 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 26m:N 33m:A
  03:19:50  price 20039.00 (open -0.00 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  03:20:49  price 20035.42 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:21:04  price 20033.63 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  03:21:51  price 20033.63 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:22:55  price 20031.85 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:23:10  price 20028.27 (open -0.09 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  03:23:26  price 20024.69 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:26:00  price 20030.06 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:30:17  price 20024.69 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:30:47  price 20024.69 (open -0.12 R of the book stop): state change desk [DEFEND/NNA-A-: DEFEND/NNA-A-]
  03:30:47  price 20024.69 (open -0.12 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:30:47  price 20024.69 (open -0.12 R of the book stop): took a part [DF: DF]
  03:31:17  price 20019.32 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  03:31:47  price 20017.53 (open -0.18 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  03:32:17  price 20010.38 (open -0.24 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  03:32:47  price 20013.96 (open -0.21 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  03:34:19  price 20008.59 (open -0.26 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  03:37:25  price 20008.59 (open -0.26 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:37:41  price 20006.80 (open -0.27 R of the book stop): state change desk [DEFEND/ANA-A-: DEFEND/ANA-A-]
  03:38:58  price 20015.75 (open -0.20 R of the book stop): state change desk [DEFEND/NNA-A-: DEFEND/NNA-A-]
  03:40:00  price 20022.90 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:40:45  price 20033.63 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:43:18  price 20037.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:43:33  price 20037.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:44:04  price 20039.00 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:45:21  price 20040.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:45:36  price 20042.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:46:06  price 20042.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:46:51  price 20039.00 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:47:08  price 20040.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:48:54  price 20030.06 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:49:12  price 20030.06 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:49:44  price 20026.48 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:51:00  price 20026.48 (open -0.11 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  03:51:16  price 20028.27 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:53:36  price 20026.48 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:54:06  price 20022.90 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:56:55  price 20024.69 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:01:00  price 20035.42 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:02:01  price 20028.27 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 20012.00

**LO-ZB (London MF3)** 2024-07-10 07:37:15 ET, SHORT 2 lots at 20744.25, safety stop 20923.12 (1.5 x own stop 119.25 pts). Result managed -10 pts/lot (-0.08 R, $-382) ; own bracket: not taken (slot effect). MFE +0.02 R, MAE -0.14 R, 27 min under water (longest 25 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 14m:A
  07:37:16  price 20746.04 (open -0.01 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  07:38:16  price 20742.46 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:40:53  price 20746.04 (open -0.01 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:40:53  price 20746.04 (open -0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:40:53  price 20746.04 (open -0.01 R of the book stop): took a part [DF: DF]
  07:41:41  price 20746.04 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:42:31  price 20744.25 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:42:46  price 20746.04 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:44:10  price 20746.04 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:44:25  price 20746.04 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:44:43  price 20747.83 (open -0.03 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:44:58  price 20747.83 (open -0.03 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:47:02  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:47:38  price 20753.19 (open -0.08 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:49:11  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:50:12  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:50:29  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:51:47  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:53:17  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:54:04  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:54:19  price 20754.98 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:54:51  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:55:06  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:58:52  price 20749.62 (open -0.04 R of the book stop): state change desk [NORMAL/WNA-N-: NORMAL/WNA-N-]
  07:59:44  price 20749.62 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  08:00:30  price 20749.62 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:00:45  price 20749.62 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  08:01:19  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/WNA-N-: NORMAL/WNA-N-]
  08:01:35  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  08:01:50  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  08:03:04  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:03:19  price 20751.40 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  08:04:06  price 20754.98 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:04:21  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  08:04:37  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  08:04:52  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  08:05:14  price 20753.19 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  08:05:29  price 20754.98 (open -0.09 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  08:05:47  price 20754.98 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  08:06:02  price 20756.77 (open -0.11 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  exit: ExAlgoAll_AB at 20753.75

**LO-ZB (London MF3)** 2024-07-23 03:24:11 ET, LONG 2 lots at 19892.88, safety stop 19714.00 (1.5 x own stop 119.25 pts). Result managed -13 pts/lot (-0.11 R, $-507) ; own bracket result +60 pts (+0.50 R, $+2403). MFE +0.23 R, MAE -0.19 R, 19 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 10m:N 14m:W
  03:24:13  price 19891.09 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:25:13  price 19894.66 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:26:28  price 19878.56 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:26:28  price 19878.56 (open -0.12 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:26:28  price 19878.56 (open -0.12 R of the book stop): took a part [DF: DF]
  03:26:43  price 19873.20 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:27:45  price 19876.78 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:29:00  price 19878.56 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:29:16  price 19876.78 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:31:18  price 19878.56 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:31:33  price 19882.14 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:32:19  price 19887.51 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:33:06  price 19891.09 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:33:36  price 19880.35 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:33:51  price 19885.72 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:34:38  price 19883.93 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:35:40  price 19891.09 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:37:13  price 19894.66 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:37:32  price 19894.66 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:37:47  price 19896.45 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:38:33  price 19901.82 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:39:20  price 19898.24 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:37  price 19898.24 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:40:41  price 19896.45 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:42:46  price 19910.76 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:43:16  price 19908.97 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:44:32  price 19908.97 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:45:19  price 19910.76 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:45:35  price 19910.76 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:47:42  price 19916.13 (open +0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:49:02  price 19912.55 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:49:17  price 19912.55 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:50:07  price 19903.61 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:51:07  price 19901.82 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:51:43  price 19898.24 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:53:35  price 19901.82 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:53:50  price 19898.24 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:54:30  price 19898.24 (open +0.04 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  03:54:48  price 19900.03 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  03:55:05  price 19894.66 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 19880.25

**LO-ZB (London MF3)** 2024-07-25 03:22:15 ET, LONG 2 lots at 19201.12, safety stop 19022.25 (1.5 x own stop 119.25 pts). Result managed -26 pts/lot (-0.22 R, $-1037) ; own bracket: not taken (slot effect). MFE +0.21 R, MAE -0.26 R, 16 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  03:22:16  price 19197.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  03:23:15  price 19185.03 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:23:15  price 19185.03 (open -0.14 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:23:15  price 19185.03 (open -0.14 R of the book stop): took a part [DF: DF]
  03:23:45  price 19195.76 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:24:33  price 19192.18 (open -0.08 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:24:48  price 19199.34 (open -0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:25:33  price 19192.18 (open -0.08 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:27:33  price 19185.03 (open -0.14 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:28:03  price 19190.39 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:34:22  price 19190.39 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:34:53  price 19193.97 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:35:41  price 19217.22 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:35:56  price 19211.86 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:36:11  price 19213.65 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:36:47  price 19211.86 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:38:49  price 19215.44 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:40:21  price 19213.65 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:40:52  price 19206.49 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:46:13  price 19193.97 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:50:36  price 19179.66 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:51:07  price 19185.03 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:51:37  price 19181.45 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:52:52  price 19168.93 (open -0.27 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  03:52:52  price 19168.93 (open -0.27 R of the book stop): state change DEFENDING>OUT [AB: AB]
  03:52:52  price 19168.93 (open -0.27 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 19175.25

**LO-CRUDE (London MF1)** 2024-07-30 07:19:05 ET, LONG 8 lots at 19248.28, safety stop 19113.98 (1.5 x own stop 89.5312 pts). Result managed +20 pts/lot (+0.22 R, $+3141) ; own bracket result +30 pts (+0.33 R, $+4786). MFE +0.27 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  07:19:07  price 19245.60 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:20:05  price 19248.28 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:24:18  price 19256.34 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:24:36  price 19253.65 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:31:05  price 19261.71 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:32:27  price 19261.71 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:35:08  price 19263.05 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:35:38  price 19269.77 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  07:35:38  price 19269.77 (open +0.24 R of the book stop): took a part [OB1: OB1]
  07:36:10  price 19267.08 (open +0.21 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  07:36:10  price 19267.08 (open +0.21 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19267.97

**LO-ZB (London MF3)** 2024-09-17 03:21:04 ET, SHORT 2 lots at 19486.12, safety stop 19665.00 (1.5 x own stop 119.25 pts). Result managed -27 pts/lot (-0.22 R, $-1072) ; own bracket: not taken (slot effect). MFE +0.09 R, MAE -0.57 R, 242 min under water (longest 242 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 24m:N 136m:A
  03:21:10  price 19484.34 (open +0.01 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  03:22:06  price 19482.55 (open +0.03 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:24:58  price 19480.76 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:25:13  price 19480.76 (open +0.04 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:25:45  price 19482.55 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:27:00  price 19478.97 (open +0.06 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:27:20  price 19478.97 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:28:09  price 19484.34 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  03:30:10  price 19491.49 (open -0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:33:19  price 19491.49 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:34:45  price 19495.07 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:40:17  price 19504.01 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:43:17  price 19507.59 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:44:33  price 19511.17 (open -0.21 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:44:33  price 19511.17 (open -0.21 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:44:33  price 19511.17 (open -0.21 R of the book stop): took a part [DF: DF]
  03:45:10  price 19509.38 (open -0.20 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:45:27  price 19505.80 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:45:57  price 19504.01 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:46:28  price 19505.80 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:52:32  price 19498.65 (open -0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:52:54  price 19498.65 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:53:28  price 19493.28 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:56:09  price 19496.86 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:59:12  price 19500.44 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:01:46  price 19500.44 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:09:10  price 19509.38 (open -0.20 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:15:01  price 19512.96 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:29:15  price 19496.86 (open -0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:29:33  price 19498.65 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:17  price 19504.01 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:34:48  price 19502.22 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:43:42  price 19505.80 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:44:02  price 19504.01 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:44:47  price 19505.80 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:46:37  price 19504.01 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:54:36  price 19511.17 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:59:09  price 19507.59 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:04:38  price 19516.53 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:07:37  price 19525.48 (open -0.33 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  exit: ExAlgoAll_AB at 19512.88

**LO-CRUDE (London MF1)** 2024-09-30 04:07:51 ET, SHORT 8 lots at 20195.00, safety stop 20329.30 (1.5 x own stop 89.5312 pts). Result managed +20 pts/lot (+0.23 R, $+3271) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.27 R, MAE -0.18 R, 19 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 5m:A 8m:W 61m:N
  04:07:52  price 20193.66 (open +0.01 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  04:08:51  price 20196.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:09:36  price 20196.34 (open -0.01 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:10:06  price 20199.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:10:38  price 20205.74 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  04:10:56  price 20201.71 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:11:11  price 20200.37 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:11:27  price 20197.69 (open -0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:11:44  price 20199.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:11:59  price 20199.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:13:02  price 20199.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:13:32  price 20196.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:13:49  price 20197.69 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:15:24  price 20188.29 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:17:14  price 20182.91 (open +0.14 R of the book stop): state change desk [NORMAL/WAN-N-: NORMAL/WAN-N-]
  04:17:30  price 20184.26 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:20:24  price 20181.57 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:26:08  price 20207.09 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:27:44  price 20203.06 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:28:53  price 20205.74 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:29:12  price 20204.40 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:18  price 20185.60 (open +0.11 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:31:33  price 20186.94 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:31:48  price 20184.26 (open +0.12 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:33:54  price 20186.94 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:34:24  price 20184.26 (open +0.12 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:34:59  price 20182.91 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:35:45  price 20188.29 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:39:16  price 20193.66 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:42:04  price 20197.69 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:44:49  price 20196.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:45:05  price 20192.31 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:49:10  price 20188.29 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:58:40  price 20199.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:23  price 20190.97 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:01:14  price 20188.29 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:03:36  price 20180.23 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:04:24  price 20184.26 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:10:06  price 20189.63 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:18:13  price 20173.51 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  exit: ExAlgoAll_OB2 at 20174.50

**LO-ZB (London MF3)** 2024-10-01 08:09:54 ET, SHORT 2 lots at 20276.50, safety stop 20455.38 (1.5 x own stop 119.25 pts). Result managed -0 pts/lot (-0.00 R, $-22) ; own bracket: not taken (slot effect). MFE +0.01 R, MAE -0.03 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  08:09:55  price 20276.50 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:10:54  price 20276.50 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:10:54  price 20276.50 (open -0.00 R of the book stop): state change PROBE>OUT [CL: CL]
  08:10:54  price 20276.50 (open -0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 20277.00

**LO-ZB (London MF3)** 2024-10-11 03:08:22 ET, SHORT 2 lots at 20408.75, safety stop 20587.62 (1.5 x own stop 119.25 pts). Result managed +23 pts/lot (+0.19 R, $+923) ; own bracket result +19 pts (+0.16 R, $+753). MFE +0.32 R, MAE -0.05 R, 6 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A 7m:W
  03:08:23  price 20410.54 (open -0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:09:22  price 20414.12 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:11:17  price 20410.54 (open -0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:11:32  price 20414.12 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:12:22  price 20412.33 (open -0.03 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:12:40  price 20410.54 (open -0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:12:59  price 20410.54 (open -0.01 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:13:14  price 20410.54 (open -0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:13:29  price 20412.33 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:13:45  price 20414.12 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  03:14:46  price 20408.75 (open -0.00 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  03:15:01  price 20410.54 (open -0.01 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  03:16:01  price 20396.23 (open +0.11 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:20:56  price 20392.65 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:21:11  price 20390.86 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:22:14  price 20389.07 (open +0.17 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:22:29  price 20385.50 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:22:44  price 20387.28 (open +0.18 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:23:47  price 20385.50 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:24:18  price 20374.76 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  03:24:18  price 20374.76 (open +0.29 R of the book stop): took a part [OB1: OB1]
  03:27:15  price 20392.65 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:27:30  price 20392.65 (open +0.14 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:28:24  price 20392.65 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:28:56  price 20394.44 (open +0.12 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  03:30:42  price 20392.65 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:30:57  price 20394.44 (open +0.12 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  03:31:12  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:34:06  price 20389.07 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  03:35:40  price 20387.28 (open +0.18 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:39:08  price 20394.44 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:25  price 20392.65 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:40:48  price 20398.02 (open +0.09 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  03:41:04  price 20398.02 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:41:20  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:41:55  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:42:11  price 20398.02 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:42:26  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:42:42  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:43:00  price 20396.23 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  exit: ExAlgoAll_OB2 at 20385.62

**LO-CRUDE (London MF1)** 2024-11-12 02:17:26 ET, SHORT 8 lots at 21223.81, safety stop 21358.11 (1.5 x own stop 89.5312 pts). Result managed +21 pts/lot (+0.23 R, $+3301) ; own bracket result +30 pts (+0.34 R, $+4801). MFE +0.49 R, MAE -0.05 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:W
  02:17:30  price 21225.16 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:18:26  price 21226.50 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:18:41  price 21226.50 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  02:19:53  price 21225.16 (open -0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:20:08  price 21219.78 (open +0.04 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:20:46  price 21218.44 (open +0.06 R of the book stop): state change desk [PRESS/NNW-W-: PRESS/NNW-W-]
  02:21:02  price 21217.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:23:08  price 21217.10 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:23:56  price 21215.75 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:25:07  price 21207.70 (open +0.18 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:25:22  price 21202.33 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  02:25:22  price 21202.33 (open +0.24 R of the book stop): took a part [OB1: OB1]
  02:25:37  price 21198.30 (open +0.29 R of the book stop): state change DEFENDING>FREE [NB: NB]
  02:25:37  price 21198.30 (open +0.29 R of the book stop): moved the stop closer [NB: NB]
  02:30:35  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:30:50  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  02:31:06  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:31:41  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:32:30  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  02:33:40  price 21200.98 (open +0.26 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:33:56  price 21196.95 (open +0.30 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  02:34:11  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:34:56  price 21195.61 (open +0.32 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  02:35:12  price 21196.95 (open +0.30 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:35:29  price 21198.30 (open +0.29 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:35:47  price 21199.64 (open +0.27 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:36:06  price 21199.64 (open +0.27 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:38:17  price 21191.58 (open +0.36 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:42:10  price 21190.24 (open +0.38 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:42:42  price 21194.27 (open +0.33 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:42:57  price 21194.27 (open +0.33 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:43:14  price 21196.95 (open +0.30 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:43:29  price 21196.95 (open +0.30 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:44:14  price 21200.98 (open +0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:45:17  price 21199.64 (open +0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:45:35  price 21199.64 (open +0.27 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:47:16  price 21203.67 (open +0.22 R of the book stop): state change FREE>OUT [OB2: OB2]
  02:47:16  price 21203.67 (open +0.22 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21203.12

**LO-ZB (London MF3)** 2024-12-19 02:01:11 ET, SHORT 2 lots at 21490.62, safety stop 21669.50 (1.5 x own stop 119.25 pts). Result managed -59 pts/lot (-0.49 R, $-2352) ; own bracket result -120 pts (-1.01 R, $-4812). MFE +0.07 R, MAE -0.91 R, 191 min under water (longest 190 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 14m:N 19m:A
  02:01:12  price 21488.84 (open +0.01 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:02:14  price 21490.62 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:02:45  price 21487.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:03:00  price 21483.47 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:03:15  price 21490.62 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:03:30  price 21487.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:04:02  price 21487.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:07:14  price 21499.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:07:29  price 21497.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:07:44  price 21497.78 (open -0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:08:16  price 21499.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:08:32  price 21504.94 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  02:08:32  price 21504.94 (open -0.12 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  02:08:32  price 21504.94 (open -0.12 R of the book stop): took a part [DF: DF]
  02:10:04  price 21503.15 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:10:34  price 21499.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:10:49  price 21503.15 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:11:07  price 21503.15 (open -0.11 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  02:11:22  price 21497.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:11:55  price 21495.99 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:12:11  price 21497.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:13:13  price 21494.20 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:13:28  price 21495.99 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:14:16  price 21499.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:15:18  price 21504.94 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:15:34  price 21508.51 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:15:50  price 21506.72 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:16:05  price 21506.72 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:16:37  price 21512.09 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  02:16:53  price 21513.88 (open -0.20 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:18:25  price 21512.09 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  02:18:40  price 21512.09 (open -0.18 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:18:56  price 21512.09 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  02:19:12  price 21515.67 (open -0.21 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:19:29  price 21515.67 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  02:19:44  price 21528.19 (open -0.32 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:24:50  price 21546.08 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  02:26:05  price 21551.44 (open -0.51 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  02:29:37  price 21556.81 (open -0.55 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  02:29:52  price 21556.81 (open -0.55 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  exit: ExAlgoAll_AB at 21549.38

**LO-CRUDE (London MF1)** 2025-03-10 05:11:29 ET, SHORT 8 lots at 19969.72, safety stop 20104.02 (1.5 x own stop 89.5312 pts). Result managed -68 pts/lot (-0.76 R, $-10864) ; own bracket result +30 pts (+0.33 R, $+4786). MFE +0.22 R, MAE -0.91 R, 32 min under water (longest 32 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 11m:A
  05:11:30  price 19969.72 (open -0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:12:29  price 19965.69 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:13:30  price 19965.69 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:13:45  price 19961.66 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:14:00  price 19956.29 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:14:15  price 19954.95 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:14:32  price 19957.63 (open +0.14 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  05:15:03  price 19958.97 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:17:50  price 19989.86 (open -0.22 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  05:18:05  price 19988.52 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:18:20  price 19993.89 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:19:20  price 19995.24 (open -0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:19:36  price 19999.26 (open -0.33 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:20:07  price 19997.92 (open -0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:20:55  price 19996.58 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:27:21  price 20022.09 (open -0.58 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  05:27:21  price 20022.09 (open -0.58 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  05:27:21  price 20022.09 (open -0.58 R of the book stop): took a part [DF: DF]
  05:27:36  price 20016.72 (open -0.52 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:33:58  price 20026.12 (open -0.63 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  05:34:13  price 20023.44 (open -0.60 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:43:51  price 20042.24 (open -0.81 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  05:44:06  price 20039.55 (open -0.78 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:46:24  price 20044.92 (open -0.84 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  05:47:41  price 20051.64 (open -0.92 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  05:47:41  price 20051.64 (open -0.92 R of the book stop): state change DEFENDING>OUT [AB: AB]
  05:47:41  price 20051.64 (open -0.92 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 20037.56

**LO-CRUDE (London MF1)** 2025-03-12 06:05:47 ET, SHORT 8 lots at 19541.09, safety stop 19675.39 (1.5 x own stop 89.5312 pts). Result managed -55 pts/lot (-0.61 R, $-8784) ; own bracket: not taken (slot effect). MFE +0.19 R, MAE -1.38 R, 113 min under water (longest 106 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 57m:A
  06:05:54  price 19542.44 (open -0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:06:49  price 19541.09 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:14:33  price 19531.69 (open +0.11 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:14:49  price 19534.38 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:16:24  price 19527.66 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:17:28  price 19529.01 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:17:46  price 19527.66 (open +0.15 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:18:17  price 19531.69 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  06:18:34  price 19531.69 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:20:39  price 19530.35 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:20:55  price 19531.69 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:30:15  price 19533.04 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:30:31  price 19530.35 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:31:33  price 19531.69 (open +0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:31:48  price 19529.01 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:32:03  price 19530.35 (open +0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:32:19  price 19529.01 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:33:31  price 19530.35 (open +0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:35:15  price 19529.01 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:38:07  price 19537.06 (open +0.04 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:42:16  price 19543.78 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:42:31  price 19547.81 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:43:02  price 19545.12 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:48:16  price 19549.15 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:49:29  price 19547.81 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:49:45  price 19551.84 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:54:13  price 19554.52 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:55:00  price 19558.55 (open -0.20 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:56:03  price 19555.87 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:56:35  price 19557.21 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:57:10  price 19554.52 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:00:39  price 19561.24 (open -0.22 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:06:11  price 19569.30 (open -0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:08:17  price 19574.67 (open -0.38 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:08:32  price 19573.33 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:09:02  price 19574.67 (open -0.38 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:09:17  price 19567.95 (open -0.30 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:13:03  price 19577.35 (open -0.41 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:13:48  price 19576.01 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:14:03  price 19577.35 (open -0.41 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  exit: UWTime at 19595.94

**LO-CRUDE (London MF1)** 2025-05-12 04:22:22 ET, LONG 8 lots at 20818.34, safety stop 20684.05 (1.5 x own stop 89.5312 pts). Result managed +17 pts/lot (+0.19 R, $+2666) ; own bracket result +30 pts (+0.33 R, $+4776). MFE +0.30 R, MAE -0.17 R, 4 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  04:22:23  price 20815.66 (open -0.03 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  04:23:22  price 20812.97 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:35:05  price 20831.77 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:38:25  price 20841.17 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:38:25  price 20841.17 (open +0.26 R of the book stop): took a part [OB1: OB1]
  04:39:41  price 20833.12 (open +0.17 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  04:39:41  price 20833.12 (open +0.17 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 20835.06

**LO-ZB (London MF3)** 2025-08-21 02:02:03 ET, LONG 2 lots at 23339.12, safety stop 23160.25 (1.5 x own stop 119.25 pts). Result managed -46 pts/lot (-0.38 R, $-1822) ; own bracket result -111 pts (-0.93 R, $-4432). MFE +0.25 R, MAE -0.38 R, 50 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 9m:W 61m:N
  02:02:07  price 23337.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:03:08  price 23339.12 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:03:25  price 23339.12 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:03:40  price 23340.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:03:56  price 23339.12 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:04:31  price 23339.12 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:05:20  price 23337.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:10:12  price 23344.49 (open +0.04 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:14:30  price 23353.44 (open +0.12 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:14:45  price 23353.44 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:15:46  price 23358.80 (open +0.17 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:16:51  price 23358.80 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:17:36  price 23362.38 (open +0.20 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:17:53  price 23362.38 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:18:11  price 23362.38 (open +0.20 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:18:27  price 23360.59 (open +0.18 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:19:20  price 23364.17 (open +0.21 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:19:38  price 23365.96 (open +0.22 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:20:10  price 23365.96 (open +0.22 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:20:25  price 23365.96 (open +0.22 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:21:18  price 23364.17 (open +0.21 R of the book stop): state change desk [PRESS/WNW-W-: PRESS/WNW-W-]
  02:21:52  price 23360.59 (open +0.18 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  02:23:37  price 23360.59 (open +0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:28:04  price 23346.28 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:29:41  price 23353.44 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:30:13  price 23351.65 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:32:20  price 23358.80 (open +0.17 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  02:33:07  price 23358.80 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:36:36  price 23365.96 (open +0.22 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:36:51  price 23364.17 (open +0.21 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:37:51  price 23365.96 (open +0.22 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  02:38:06  price 23362.38 (open +0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:42:23  price 23355.22 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:42:55  price 23355.22 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:43:13  price 23353.44 (open +0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:44:21  price 23355.22 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:47:52  price 23349.86 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:48:13  price 23348.07 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:49:23  price 23348.07 (open +0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  02:49:42  price 23348.07 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: ExAlgoAll_AB at 23293.62

**LO-ZB (London MF3)** 2025-09-10 04:21:07 ET, SHORT 2 lots at 23912.00, safety stop 24090.88 (1.5 x own stop 119.25 pts). Result managed +6 pts/lot (+0.05 R, $+238) ; own bracket: not taken (slot effect). MFE +0.25 R, MAE -0.06 R, 7 min under water (longest 5 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 9m:A 10m:N 11m:W 61m:N
  04:21:08  price 23912.00 (open -0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  04:22:07  price 23913.79 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:25:37  price 23917.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:26:12  price 23919.15 (open -0.06 R of the book stop): state change desk [DEFEND/ANN-A-: DEFEND/ANN-A-]
  04:26:12  price 23919.15 (open -0.06 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:26:12  price 23919.15 (open -0.06 R of the book stop): took a part [DF: DF]
  04:26:27  price 23917.37 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:27:02  price 23919.15 (open -0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:27:19  price 23919.15 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:25  price 23906.63 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:31:55  price 23904.85 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:32:43  price 23903.06 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:33:00  price 23903.06 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:38:26  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:41:12  price 23897.69 (open +0.12 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:48:55  price 23901.27 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:49:10  price 23901.27 (open +0.09 R of the book stop): state change desk [NORMAL/ANW-N-: NORMAL/ANW-N-]
  04:50:26  price 23901.27 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:53:42  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:53:57  price 23894.11 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:55:16  price 23895.90 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:55:43  price 23894.11 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:55:59  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:58:12  price 23894.11 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:59:17  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:59:32  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:07  price 23895.90 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:00:26  price 23897.69 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:56  price 23895.90 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:02:01  price 23890.53 (open +0.18 R of the book stop): state change desk [NORMAL/WAW-N-: NORMAL/WAW-N-]
  05:02:16  price 23892.32 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:02:31  price 23890.53 (open +0.18 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:05:55  price 23894.11 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:06:10  price 23892.32 (open +0.17 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:06:44  price 23892.32 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:07:57  price 23888.75 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:08:17  price 23890.53 (open +0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:12:50  price 23894.11 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:13:05  price 23890.53 (open +0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:13:48  price 23894.11 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  exit: Stop at 23906.00

**LO-ZB (London MF3)** 2025-09-12 04:44:56 ET, LONG 2 lots at 23999.00, safety stop 23820.12 (1.5 x own stop 119.25 pts). Result managed +42 pts/lot (+0.35 R, $+1683) ; own bracket: not taken (slot effect). MFE +0.42 R, MAE -0.04 R, 8 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 5m:A 16m:N 31m:A 57m:N 58m:A 61m:N
  04:44:57  price 23999.00 (open -0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:45:56  price 23999.00 (open +0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:49:40  price 23997.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:49:55  price 23997.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:50:59  price 23995.42 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:51:21  price 23997.21 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:58:35  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:58:55  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:59:11  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:04:33  price 24004.37 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:04:52  price 24002.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:05:27  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:16:17  price 24002.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:17:22  price 24002.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:17:39  price 24002.58 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:20:30  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:20:45  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:21:20  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:22:26  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:22:46  price 23999.00 (open +0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:24:06  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:24:21  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:24:38  price 24000.79 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:54:11  price 24015.10 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:54:26  price 24015.10 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:55:21  price 24016.89 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:55:37  price 24015.10 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:58:34  price 24009.73 (open +0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:59:23  price 24009.73 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:23:09  price 24015.10 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:23:24  price 24011.52 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:29:54  price 24015.10 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:39:40  price 24016.89 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:40:40  price 24018.68 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:42:01  price 24018.68 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:45:00  price 24018.68 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:53:33  price 24018.68 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:53:52  price 24018.68 (open +0.17 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:54:43  price 24016.89 (open +0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:55:04  price 24016.89 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  exit: ExAlgoAll_OB2 at 24041.12

**LO-ZB (London MF3)** 2025-10-24 07:21:46 ET, LONG 2 lots at 25367.12, safety stop 25188.25 (1.5 x own stop 119.25 pts). Result managed +8 pts/lot (+0.06 R, $+303) ; own bracket: not taken (slot effect). MFE +0.16 R, MAE -0.03 R, 7 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 6m:N 18m:A 19m:N 34m:W
  07:21:47  price 25367.12 (open +0.00 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  07:22:46  price 25365.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:23:01  price 25367.12 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:26:05  price 25368.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:27:57  price 25370.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:28:12  price 25370.70 (open +0.03 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:28:44  price 25370.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:29:30  price 25370.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:40:26  price 25372.49 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:43:10  price 25370.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:46:12  price 25374.28 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:48:19  price 25368.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:48:34  price 25370.70 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:50:38  price 25376.07 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:51:42  price 25372.49 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:52:14  price 25374.28 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:59:19  price 25372.49 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:00:06  price 25376.07 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  08:00:06  price 25376.07 (open +0.08 R of the book stop): state change PROBE>OUT [CL: CL]
  08:00:06  price 25376.07 (open +0.08 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 25374.75

**LO-CRUDE (London MF1)** 2025-10-29 05:46:08 ET, SHORT 8 lots at 26227.34, safety stop 26361.64 (1.5 x own stop 89.5312 pts). Result managed -30 pts/lot (-0.34 R, $-4819) ; own bracket result -37 pts (-0.42 R, $-5994). MFE +0.01 R, MAE -0.40 R, 40 min under water (longest 40 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  05:46:09  price 26228.69 (open -0.01 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:47:08  price 26235.40 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:47:23  price 26236.74 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:50:36  price 26236.74 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:51:23  price 26238.09 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:57:23  price 26238.09 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:57:40  price 26236.74 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:58:12  price 26239.43 (open -0.14 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  05:58:44  price 26236.74 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:06:56  price 26243.46 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:07:26  price 26242.12 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:07:42  price 26243.46 (open -0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:09:03  price 26250.17 (open -0.26 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:09:03  price 26250.17 (open -0.26 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  06:09:03  price 26250.17 (open -0.26 R of the book stop): took a part [DF: DF]
  06:09:34  price 26251.52 (open -0.27 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:10:05  price 26242.12 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:18:32  price 26250.17 (open -0.26 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:18:47  price 26250.17 (open -0.26 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:20:26  price 26258.23 (open -0.35 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:25:51  price 26262.26 (open -0.39 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  06:25:51  price 26262.26 (open -0.39 R of the book stop): state change DEFENDING>OUT [AB: AB]
  06:25:51  price 26262.26 (open -0.39 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 26257.41

**LO-ZB (London MF3)** 2025-12-03 07:31:05 ET, LONG 2 lots at 25650.38, safety stop 25471.50 (1.5 x own stop 119.25 pts). Result managed +6 pts/lot (+0.05 R, $+233) ; own bracket: not taken (slot effect). MFE +0.12 R, MAE -0.03 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 4m:N 5m:W 29m:N
  07:31:06  price 25648.59 (open -0.01 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  07:32:05  price 25645.01 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:32:37  price 25646.80 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:32:53  price 25646.80 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:35:26  price 25655.74 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:35:41  price 25657.53 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:35:57  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  07:36:15  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:36:31  price 25657.53 (open +0.06 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:37:04  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:37:55  price 25659.32 (open +0.08 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  07:38:47  price 25661.11 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:39:35  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:44:03  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:44:19  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:47:58  price 25661.11 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  07:48:19  price 25661.11 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:51:05  price 25662.90 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:52:12  price 25659.32 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:53:39  price 25661.11 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:54:46  price 25659.32 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:55:34  price 25659.32 (open +0.08 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  07:55:50  price 25657.53 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:56:36  price 25659.32 (open +0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:57:27  price 25659.32 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:00:14  price 25655.74 (open +0.04 R of the book stop): state change PROBE>OUT [CL: CL]
  08:00:14  price 25655.74 (open +0.04 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 25656.25

**LO-CRUDE (London MF1)** 2026-02-02 04:00:10 ET, LONG 8 lots at 25400.56, safety stop 25266.27 (1.5 x own stop 89.5312 pts). Result managed +4 pts/lot (+0.05 R, $+656) ; own bracket result +30 pts (+0.33 R, $+4781). MFE +0.63 R, MAE -0.48 R, 18 min under water (longest 18 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 7m:A
  04:00:11  price 25400.56 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:01:10  price 25395.19 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:01:25  price 25392.50 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:02:26  price 25387.13 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:03:41  price 25387.13 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:12  price 25376.39 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:05:27  price 25381.76 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:05:59  price 25376.39 (open -0.27 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  04:07:00  price 25361.62 (open -0.43 R of the book stop): took a part [DF: DF]
  04:07:48  price 25368.33 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:08:37  price 25362.96 (open -0.42 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  04:09:22  price 25372.36 (open -0.32 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:10:10  price 25384.45 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:14:31  price 25375.05 (open -0.29 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:14:48  price 25388.48 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:19:10  price 25403.25 (open +0.03 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:21:28  price 25434.14 (open +0.38 R of the book stop): state change DEFENDING>FREE [NB: NB]
  04:21:28  price 25434.14 (open +0.38 R of the book stop): moved the stop closer [NB: NB]
  04:21:43  price 25439.51 (open +0.43 R of the book stop): state change FREE>RUNNER [OB1: OB1]
  04:21:43  price 25439.51 (open +0.43 R of the book stop): moved the stop closer [OB1: OB1]
  04:22:13  price 25451.60 (open +0.57 R of the book stop): state change RUNNER>OUT [DV: DV]
  04:22:13  price 25451.60 (open +0.57 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 25404.72

**LO-ZB (London MF3)** 2026-02-12 08:24:10 ET, LONG 2 lots at 25329.75, safety stop 25150.88 (1.5 x own stop 119.25 pts). Result managed +0 pts/lot (+0.00 R, $+13) ; own bracket: not taken (slot effect). MFE +0.03 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  08:24:11  price 25327.96 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:25:10  price 25327.96 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:25:41  price 25329.75 (open +0.00 R of the book stop): state change PROBE>OUT [CL: CL]
  08:25:41  price 25329.75 (open +0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 25330.12

**LO-CRUDE (London MF1)** 2026-03-09 05:30:48 ET, LONG 8 lots at 24394.50, safety stop 24260.20 (1.5 x own stop 89.5312 pts). Result managed +49 pts/lot (+0.55 R, $+7896) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.99 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  05:30:49  price 24390.47 (open -0.04 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  05:31:49  price 24413.30 (open +0.21 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  05:32:04  price 24414.64 (open +0.22 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  05:32:04  price 24414.64 (open +0.22 R of the book stop): took a part [OB1: OB1]
  05:32:22  price 24414.64 (open +0.22 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:32:37  price 24449.56 (open +0.61 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  05:32:37  price 24449.56 (open +0.61 R of the book stop): state change DEFENDING>FREE [NB: NB]
  05:32:37  price 24449.56 (open +0.61 R of the book stop): moved the stop closer [NB: NB]
  05:32:52  price 24458.96 (open +0.72 R of the book stop): moved the stop closer [NB: NB]
  05:33:07  price 24473.74 (open +0.89 R of the book stop): state change FREE>OUT [OB2: OB2]
  05:33:07  price 24473.74 (open +0.89 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24443.91

**LO-ZB (London MF3)** 2026-03-13 04:18:12 ET, LONG 2 lots at 24423.25, safety stop 24244.38 (1.5 x own stop 119.25 pts). Result managed +46 pts/lot (+0.39 R, $+1858) ; own bracket: not taken (slot effect). MFE +0.57 R, MAE -0.13 R, 4 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 5m:W
  04:18:14  price 24421.46 (open -0.01 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  04:19:12  price 24419.67 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:25:52  price 24419.67 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:26:07  price 24425.04 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:27:45  price 24414.31 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:30:03  price 24419.67 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:31:23  price 24432.19 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:37:01  price 24453.66 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:37:01  price 24453.66 (open +0.26 R of the book stop): took a part [OB1: OB1]
  04:39:02  price 24473.33 (open +0.42 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  04:39:17  price 24480.49 (open +0.48 R of the book stop): state change DEFENDING>FREE [NB: NB]
  04:39:17  price 24480.49 (open +0.48 R of the book stop): moved the stop closer [NB: NB]
  04:41:37  price 24475.12 (open +0.43 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:43:00  price 24469.76 (open +0.39 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:43:31  price 24473.33 (open +0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:43:47  price 24475.12 (open +0.43 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:44:02  price 24478.70 (open +0.46 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  04:44:51  price 24473.33 (open +0.42 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:45:41  price 24464.39 (open +0.35 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:48:51  price 24469.76 (open +0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:49:21  price 24484.07 (open +0.51 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:49:21  price 24484.07 (open +0.51 R of the book stop): state change FREE>OUT [DV: DV]
  04:49:21  price 24484.07 (open +0.51 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 24469.75

**LO-ZB (London MF3)** 2026-03-23 07:17:04 ET, LONG 2 lots at 24618.62, safety stop 24439.75 (1.5 x own stop 119.25 pts). Result managed +60 pts/lot (+0.51 R, $+2408) ; own bracket result +60 pts (+0.50 R, $+2403). MFE +0.64 R, MAE -0.09 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  07:17:05  price 24634.72 (open +0.14 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  07:18:04  price 24675.87 (open +0.48 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:18:04  price 24675.87 (open +0.48 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  07:18:04  price 24675.87 (open +0.48 R of the book stop): took a part [OB1: OB1]
  07:18:19  price 24688.39 (open +0.58 R of the book stop): state change DEFENDING>OUT [DV: DV]
  07:18:19  price 24688.39 (open +0.58 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 24678.88

**LO-CRUDE (London MF1)** 2026-04-01 02:21:37 ET, LONG 8 lots at 24108.31, safety stop 23974.02 (1.5 x own stop 89.5312 pts). Result managed +36 pts/lot (+0.40 R, $+5731) ; own bracket result +30 pts (+0.33 R, $+4781). MFE +0.46 R, MAE -0.11 R, 5 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 8m:W
  02:22:38  price 24101.60 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:22:54  price 24098.91 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  02:23:09  price 24102.94 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:23:26  price 24102.94 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  02:23:41  price 24100.25 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:23:56  price 24104.28 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  02:25:14  price 24106.97 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  02:28:08  price 24108.31 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  02:28:38  price 24116.37 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:29:08  price 24121.74 (open +0.15 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:29:53  price 24119.06 (open +0.12 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  02:30:23  price 24127.11 (open +0.21 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  02:31:08  price 24145.92 (open +0.42 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  02:31:08  price 24145.92 (open +0.42 R of the book stop): took a part [OB1: OB1]
  02:31:23  price 24145.92 (open +0.42 R of the book stop): state change DEFENDING>FREE [NB: NB]
  02:31:23  price 24145.92 (open +0.42 R of the book stop): moved the stop closer [NB: NB]
  02:31:38  price 24144.57 (open +0.41 R of the book stop): state change FREE>OUT [OB2: OB2]
  02:31:38  price 24144.57 (open +0.41 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24144.19

**LO-ZB (London MF3)** 2026-04-22 03:17:07 ET, SHORT 2 lots at 26827.50, safety stop 27006.38 (1.5 x own stop 119.25 pts). Result managed -22 pts/lot (-0.19 R, $-902) ; own bracket result -38 pts (-0.31 R, $-1502). MFE +0.01 R, MAE -0.29 R, 26 min under water (longest 24 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A
  03:17:08  price 26829.29 (open -0.01 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  03:18:08  price 26829.29 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:22:22  price 26836.44 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:22:37  price 26843.60 (open -0.14 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  03:23:08  price 26838.23 (open -0.09 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:23:08  price 26838.23 (open -0.09 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  03:23:08  price 26838.23 (open -0.09 R of the book stop): took a part [DF: DF]
  03:23:23  price 26838.23 (open -0.09 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:23:54  price 26836.44 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:24:17  price 26840.02 (open -0.11 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:24:32  price 26840.02 (open -0.11 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:24:48  price 26841.81 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  03:25:03  price 26841.81 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:25:36  price 26845.39 (open -0.15 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  03:25:51  price 26847.18 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:27:00  price 26841.81 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:28:09  price 26847.18 (open -0.17 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  03:29:49  price 26848.97 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:31:33  price 26847.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:31:49  price 26848.97 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:34:39  price 26847.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:34:54  price 26850.75 (open -0.20 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:37:13  price 26852.54 (open -0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:37:28  price 26852.54 (open -0.21 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:37:43  price 26848.97 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:00  price 26850.75 (open -0.20 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:39:31  price 26850.75 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:39:47  price 26848.97 (open -0.18 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  03:40:02  price 26847.18 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:43:56  price 26861.49 (open -0.29 R of the book stop): state change desk [ABORT/AAN-N-: ABORT/AAN-N-]
  03:43:56  price 26861.49 (open -0.29 R of the book stop): state change DEFENDING>OUT [AB: AB]
  03:43:56  price 26861.49 (open -0.29 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 26850.00

**LO-ZB (London MF3)** 2026-05-06 06:42:13 ET, LONG 2 lots at 28569.50, safety stop 28390.62 (1.5 x own stop 119.25 pts). Result managed +33 pts/lot (+0.28 R, $+1328) ; own bracket: not taken (slot effect). MFE +0.38 R, MAE -0.07 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  06:42:14  price 28569.50 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:43:29  price 28580.23 (open +0.09 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:43:44  price 28583.81 (open +0.12 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  06:43:59  price 28578.44 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:44:14  price 28587.39 (open +0.15 R of the book stop): state change desk [NORMAL/WNW-A-: NORMAL/WNW-A-]
  06:44:29  price 28587.39 (open +0.15 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  06:44:44  price 28585.60 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  06:44:59  price 28583.81 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:45:14  price 28585.60 (open +0.14 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:46:44  price 28590.97 (open +0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:48:45  price 28598.12 (open +0.24 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:49:00  price 28598.12 (open +0.24 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:49:16  price 28598.12 (open +0.24 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:53:34  price 28592.75 (open +0.20 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  06:54:04  price 28603.49 (open +0.29 R of the book stop): state change desk [NORMAL/NNW-A-: NORMAL/NNW-A-]
  06:54:19  price 28607.06 (open +0.32 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  06:54:19  price 28607.06 (open +0.32 R of the book stop): took a part [OB1: OB1]
  06:54:34  price 28601.70 (open +0.27 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  06:54:49  price 28599.91 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  06:54:49  price 28599.91 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 28602.75

**LO-ZB (London MF3)** 2026-05-11 06:00:18 ET, SHORT 2 lots at 29322.62, safety stop 29501.50 (1.5 x own stop 119.25 pts). Result managed +26 pts/lot (+0.22 R, $+1048) ; own bracket result +17 pts (+0.15 R, $+693). MFE +0.27 R, MAE -0.08 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 3m:N 4m:W
  06:00:20  price 29322.62 (open -0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:01:18  price 29329.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:01:35  price 29333.36 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  06:02:23  price 29327.99 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:25:00  price 29306.53 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:25:20  price 29306.53 (open +0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:25:54  price 29311.89 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:26:24  price 29311.89 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:31:53  price 29308.31 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:32:10  price 29306.53 (open +0.14 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  06:32:31  price 29310.10 (open +0.11 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:32:46  price 29308.31 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:33:01  price 29311.89 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:33:35  price 29313.68 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:34:41  price 29304.74 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:35:33  price 29308.31 (open +0.12 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  06:36:07  price 29306.53 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:39:34  price 29294.01 (open +0.24 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  06:39:34  price 29294.01 (open +0.24 R of the book stop): took a part [OB1: OB1]
  06:40:37  price 29301.16 (open +0.18 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  06:40:37  price 29301.16 (open +0.18 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29296.38

**LO-ZB (London MF3)** 2026-05-12 04:17:15 ET, LONG 2 lots at 29195.12, safety stop 29016.25 (1.5 x own stop 119.25 pts). Result managed +20 pts/lot (+0.17 R, $+813) ; own bracket: not taken (slot effect). MFE +0.27 R, MAE -0.10 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 4m:W
  04:17:18  price 29193.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:18:18  price 29186.18 (open -0.08 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  04:18:34  price 29191.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:21:38  price 29198.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:22:08  price 29202.28 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:22:24  price 29205.86 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:25:04  price 29189.76 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:26:21  price 29196.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  04:27:09  price 29202.28 (open +0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:53  price 29209.44 (open +0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:34:57  price 29214.80 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:35:29  price 29213.01 (open +0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:35:44  price 29216.59 (open +0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:39:44  price 29218.38 (open +0.20 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:39:44  price 29218.38 (open +0.20 R of the book stop): took a part [OB1: OB1]
  04:41:20  price 29213.01 (open +0.15 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  04:41:20  price 29213.01 (open +0.15 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29215.50

**LO-ZB (London MF3)** 2026-05-20 04:39:04 ET, LONG 2 lots at 29119.12, safety stop 28940.25 (1.5 x own stop 119.25 pts). Result managed +30 pts/lot (+0.25 R, $+1198) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.44 R, 66 min under water (longest 59 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 8m:W 36m:N
  04:39:05  price 29119.12 (open +0.00 R of the book stop): state change desk [ABORT/AAA-N-: ABORT/AAA-N-]
  04:40:04  price 29119.12 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:40:19  price 29113.76 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:40:56  price 29117.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:41:27  price 29115.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:44:40  price 29117.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:45:10  price 29117.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:46:27  price 29137.01 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:48:58  price 29122.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:53:11  price 29120.91 (open +0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:53:27  price 29117.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:53:42  price 29115.55 (open -0.03 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:53:57  price 29115.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:54:13  price 29117.34 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:54:47  price 29113.76 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:56:43  price 29101.24 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:57:00  price 29101.24 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:57:15  price 29099.45 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:58:34  price 29101.24 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:59:21  price 29099.45 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:59:38  price 29097.66 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:00:10  price 29094.08 (open -0.21 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:00:43  price 29095.87 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:04:07  price 29097.66 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  05:04:40  price 29097.66 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:09:57  price 29083.35 (open -0.30 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:10:14  price 29086.93 (open -0.27 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:12:09  price 29097.66 (open -0.18 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:12:24  price 29085.14 (open -0.29 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  05:12:42  price 29085.14 (open -0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:15:20  price 29070.83 (open -0.41 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  05:17:28  price 29074.41 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:26:13  price 29074.41 (open -0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  05:37:31  price 29088.72 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:37:51  price 29088.72 (open -0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:02:39  price 29149.53 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  06:02:39  price 29149.53 (open +0.26 R of the book stop): took a part [OB1: OB1]
  06:06:14  price 29149.53 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  06:06:14  price 29149.53 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29149.12

**LO-ZB (London MF3)** 2026-05-26 07:27:08 ET, LONG 2 lots at 29860.62, safety stop 29681.75 (1.5 x own stop 119.25 pts). Result managed -3 pts/lot (-0.02 R, $-117) ; own bracket: not taken (slot effect). MFE +0.11 R, MAE -0.36 R, 18 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 6m:W 16m:N
  07:27:09  price 29860.62 (open -0.00 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  07:28:09  price 29862.41 (open +0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:32:47  price 29873.15 (open +0.11 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:33:03  price 29871.36 (open +0.09 R of the book stop): state change desk [NORMAL/WNN-A-: NORMAL/WNN-A-]
  07:33:33  price 29871.36 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-A-: NORMAL/NNN-A-]
  07:34:20  price 29844.53 (open -0.14 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:34:35  price 29849.89 (open -0.09 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  07:34:35  price 29849.89 (open -0.09 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:34:35  price 29849.89 (open -0.09 R of the book stop): took a part [DF: DF]
  07:35:50  price 29824.85 (open -0.30 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  07:36:05  price 29830.22 (open -0.26 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:38:07  price 29840.95 (open -0.17 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:38:37  price 29842.74 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:38:52  price 29842.74 (open -0.15 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:40:56  price 29846.31 (open -0.12 R of the book stop): state change desk [NORMAL/WNA-W-: NORMAL/WNA-W-]
  07:41:12  price 29851.68 (open -0.08 R of the book stop): state change desk [PRESS/WNN-W-: PRESS/WNN-W-]
  07:42:13  price 29851.68 (open -0.08 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:42:43  price 29849.89 (open -0.09 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:42:59  price 29849.89 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:43:14  price 29851.68 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:43:33  price 29853.47 (open -0.06 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:44:35  price 29855.26 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:47:41  price 29858.84 (open -0.01 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  07:47:59  price 29860.62 (open -0.00 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:52:04  price 29865.99 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  08:00:11  price 29865.99 (open +0.04 R of the book stop): state change DEFENDING>OUT [CL: CL]
  08:00:11  price 29865.99 (open +0.04 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 29857.75

**LO-ZB (London MF3)** 2026-06-04 08:21:10 ET, LONG 2 lots at 30238.88, safety stop 30060.00 (1.5 x own stop 119.25 pts). Result managed +8 pts/lot (+0.07 R, $+318) ; own bracket: not taken (slot effect). MFE +0.10 R, MAE -0.12 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  08:21:11  price 30238.88 (open +0.00 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  08:22:10  price 30228.14 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:23:55  price 30247.82 (open +0.08 R of the book stop): state change PROBE>OUT [CL: CL]
  08:23:55  price 30247.82 (open +0.08 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 30246.88

**LO-CRUDE (London MF1)** 2026-06-05 05:23:27 ET, LONG 8 lots at 30197.00, safety stop 30062.70 (1.5 x own stop 89.5312 pts). Result managed +15 pts/lot (+0.17 R, $+2421) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.45 R, MAE -0.26 R, 25 min under water (longest 19 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 5m:N 21m:A 28m:N 29m:W 51m:N 59m:W 61m:N
  05:23:28  price 30195.66 (open -0.01 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  05:24:27  price 30195.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:27:50  price 30188.94 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:28:05  price 30191.63 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:29:37  price 30180.88 (open -0.18 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:29:52  price 30182.23 (open -0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  05:30:07  price 30184.91 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  05:32:12  price 30179.54 (open -0.20 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:23:43  price 30226.55 (open +0.33 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:23:43  price 30226.55 (open +0.33 R of the book stop): state change PROBE>FREE [NB: NB]
  06:23:43  price 30226.55 (open +0.33 R of the book stop): moved the stop closer [NB: NB]
  06:24:28  price 30225.20 (open +0.32 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:25:30  price 30230.57 (open +0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:26:19  price 30229.23 (open +0.36 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:30:15  price 30230.57 (open +0.38 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:31:16  price 30227.89 (open +0.35 R of the book stop): state change FREE>DEFENDING [OB1: OB1]
  06:31:16  price 30227.89 (open +0.35 R of the book stop): took a part [OB1: OB1]
  06:32:18  price 30222.52 (open +0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:32:34  price 30225.20 (open +0.32 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:35:42  price 30226.55 (open +0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:35:57  price 30227.89 (open +0.35 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:36:30  price 30222.52 (open +0.29 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:38:50  price 30213.12 (open +0.18 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:39:07  price 30215.80 (open +0.21 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:55:42  price 30198.34 (open +0.01 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  06:55:42  price 30198.34 (open +0.01 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30212.19

**LO-ZB (London MF3)** 2026-06-10 04:26:12 ET, SHORT 2 lots at 28873.88, safety stop 29052.75 (1.5 x own stop 119.25 pts). Result managed +33 pts/lot (+0.27 R, $+1303) ; own bracket: not taken (slot effect). MFE +0.31 R, MAE -0.12 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  04:26:13  price 28873.88 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:27:14  price 28859.56 (open +0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:27:44  price 28850.62 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:28:14  price 28855.99 (open +0.15 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:28:30  price 28850.62 (open +0.20 R of the book stop): state change desk [PRESS/WNW-N-: PRESS/WNW-N-]
  04:28:46  price 28857.78 (open +0.14 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:29:31  price 28854.20 (open +0.17 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:33:19  price 28868.51 (open +0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:33:34  price 28863.14 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:36:25  price 28881.03 (open -0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  04:36:40  price 28882.82 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:37:28  price 28879.24 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  04:37:44  price 28875.66 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:41:26  price 28843.47 (open +0.26 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:41:41  price 28838.10 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:41:41  price 28838.10 (open +0.30 R of the book stop): took a part [OB1: OB1]
  04:42:12  price 28839.89 (open +0.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  04:42:12  price 28839.89 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 28841.25

**LO-CRUDE (London MF1)** 2026-07-08 07:44:12 ET, LONG 8 lots at 29117.75, safety stop 28983.45 (1.5 x own stop 89.5312 pts). Result managed -5 pts/lot (-0.06 R, $-829) ; own bracket result +30 pts (+0.34 R, $+4791). MFE +0.71 R, MAE -0.63 R, 21 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  07:44:13  price 29111.04 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:45:12  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:47:47  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:48:02  price 29069.40 (open -0.54 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:48:47  price 29090.89 (open -0.30 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:49:02  price 29097.61 (open -0.22 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:49:17  price 29094.92 (open -0.26 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:49:32  price 29086.86 (open -0.35 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:49:47  price 29078.80 (open -0.43 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): state change desk [DEFEND/AAA-W-: DEFEND/AAA-W-]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  07:50:17  price 29060.00 (open -0.65 R of the book stop): took a part [DF: DF]
  07:50:32  price 29062.69 (open -0.61 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  07:51:33  price 29065.37 (open -0.58 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:52:03  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:52:18  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:53:34  price 29080.15 (open -0.42 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  07:54:07  price 29094.92 (open -0.26 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:57:25  price 29084.18 (open -0.38 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:58:28  price 29078.80 (open -0.43 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:59:32  price 29085.52 (open -0.36 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:59:47  price 29081.49 (open -0.41 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:00:17  price 29065.37 (open -0.58 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  08:01:32  price 29072.09 (open -0.51 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  08:01:48  price 29082.83 (open -0.39 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:02:03  price 29076.12 (open -0.46 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  08:02:56  price 29088.20 (open -0.33 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  08:07:03  price 29145.95 (open +0.32 R of the book stop): state change DEFENDING>FREE [NB: NB]
  08:07:03  price 29145.95 (open +0.32 R of the book stop): moved the stop closer [NB: NB]
  08:07:33  price 29167.44 (open +0.55 R of the book stop): state change FREE>OUT [DV: DV]
  08:07:33  price 29167.44 (open +0.55 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29112.62

**LO-ZB (London MF3)** 2026-08-10 03:49:23 ET, LONG 2 lots at 29944.25, safety stop 29765.38 (1.5 x own stop 119.25 pts). Result managed +33 pts/lot (+0.28 R, $+1323) ; own bracket result -120 pts (-1.00 R, $-4782). MFE +0.31 R, MAE -0.07 R, 3 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 4m:N 9m:W
  03:49:24  price 29944.25 (open +0.00 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:50:23  price 29937.10 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  03:55:27  price 29949.62 (open +0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  03:56:00  price 29953.19 (open +0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:00:04  price 29953.19 (open +0.08 R of the book stop): state change desk [NORMAL/NAN-N-: NORMAL/NAN-N-]
  04:00:19  price 29954.98 (open +0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  04:02:11  price 29967.50 (open +0.20 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  04:04:04  price 29978.24 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  04:04:04  price 29978.24 (open +0.29 R of the book stop): took a part [OB1: OB1]
  04:04:20  price 29978.24 (open +0.29 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  04:04:20  price 29978.24 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29977.38

**LO-ZB (London MF3)** 2026-08-31 06:18:30 ET, SHORT 2 lots at 29448.38, safety stop 29627.25 (1.5 x own stop 119.25 pts). Result managed -10 pts/lot (-0.08 R, $-382) ; own bracket: not taken (slot effect). MFE +0.12 R, MAE -0.19 R, 65 min under water (longest 41 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A 48m:N 55m:A 58m:N
  06:18:31  price 29448.38 (open -0.00 R of the book stop): state change desk [NORMAL/NNW-N-: NORMAL/NNW-N-]
  06:19:30  price 29453.74 (open -0.04 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:19:45  price 29450.16 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:20:16  price 29455.53 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:20:31  price 29460.90 (open -0.11 R of the book stop): state change desk [DEFEND/NAA-N-: DEFEND/NAA-N-]
  06:20:31  price 29460.90 (open -0.11 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  06:20:31  price 29460.90 (open -0.11 R of the book stop): took a part [DF: DF]
  06:20:46  price 29462.69 (open -0.12 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:21:02  price 29462.69 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:21:19  price 29462.69 (open -0.12 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:21:49  price 29464.47 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:22:04  price 29464.47 (open -0.14 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:22:19  price 29464.47 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:25:28  price 29464.47 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:26:14  price 29460.90 (open -0.11 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:27:54  price 29466.26 (open -0.15 R of the book stop): state change desk [DEFEND/ANA-N-: DEFEND/ANA-N-]
  06:28:12  price 29462.69 (open -0.12 R of the book stop): state change desk [NORMAL/NNA-N-: NORMAL/NNA-N-]
  06:30:08  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:34:07  price 29453.74 (open -0.04 R of the book stop): state change desk [NORMAL/WNN-N-: NORMAL/WNN-N-]
  06:35:02  price 29453.74 (open -0.04 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:39:24  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:39:40  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:40:10  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:40:48  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:47:48  price 29455.53 (open -0.06 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:50:06  price 29455.53 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:50:30  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:50:46  price 29455.53 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:52:05  price 29457.32 (open -0.08 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  06:52:36  price 29468.05 (open -0.17 R of the book stop): state change desk [NORMAL/ANA-W-: NORMAL/ANA-W-]
  06:53:06  price 29466.26 (open -0.15 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  06:54:49  price 29462.69 (open -0.12 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  06:55:04  price 29460.90 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  06:55:19  price 29460.90 (open -0.11 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:55:52  price 29464.47 (open -0.14 R of the book stop): state change desk [NORMAL/ANN-W-: NORMAL/ANN-W-]
  06:56:32  price 29464.47 (open -0.14 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  06:58:47  price 29459.11 (open -0.09 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  07:01:05  price 29450.16 (open -0.01 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  07:01:51  price 29455.53 (open -0.06 R of the book stop): state change desk [NORMAL/NNA-W-: NORMAL/NNA-W-]
  07:02:07  price 29444.80 (open +0.03 R of the book stop): state change desk [NORMAL/NNN-W-: NORMAL/NNN-W-]
  exit: ExAlgoAll_AB at 29457.88

**LO-ZB (London MF3)** 2026-10-26 02:11:50 ET, SHORT 2 lots at 29149.25, safety stop 29328.12 (1.5 x own stop 119.25 pts). Result managed +57 pts/lot (+0.48 R, $+2278) ; own bracket result +60 pts (+0.50 R, $+2398). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  02:11:54  price 29151.04 (open -0.01 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  02:15:45  price 29159.98 (open -0.09 R of the book stop): state change desk [NORMAL/NNA---: NORMAL/NNA---]
  02:17:00  price 29149.25 (open -0.00 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  02:19:04  price 29138.52 (open +0.09 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  02:19:19  price 29138.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  02:20:34  price 29127.78 (open +0.18 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  02:22:06  price 29133.15 (open +0.14 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  02:22:21  price 29126.00 (open +0.20 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  02:23:21  price 29118.84 (open +0.26 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  02:23:51  price 29111.69 (open +0.32 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  02:23:51  price 29111.69 (open +0.32 R of the book stop): took a part [OB1: OB1]
  02:25:15  price 29090.22 (open +0.49 R of the book stop): state change DEFENDING>FREE [NB: NB]
  02:25:15  price 29090.22 (open +0.49 R of the book stop): moved the stop closer [NB: NB]
  02:25:30  price 29086.64 (open +0.52 R of the book stop): state change FREE>RUNNER [RT: RT]
  02:25:30  price 29086.64 (open +0.52 R of the book stop): moved the stop closer [RT: RT]
  02:25:45  price 29084.85 (open +0.54 R of the book stop): moved the stop closer [RT: RT]
  02:26:30  price 29081.28 (open +0.57 R of the book stop): moved the stop closer [RT: RT]
  02:27:00  price 29079.49 (open +0.58 R of the book stop): moved the stop closer [RT: RT]
  02:27:15  price 29077.70 (open +0.60 R of the book stop): moved the stop closer [RT: RT]
  02:28:47  price 29074.12 (open +0.63 R of the book stop): moved the stop closer [RT: RT]
  02:29:02  price 29065.18 (open +0.70 R of the book stop): moved the stop closer [RT: RT]
  02:29:17  price 29072.33 (open +0.65 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  02:29:17  price 29072.33 (open +0.65 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29092.25

**LO-ZB (London MF3)** 2026-10-28 05:41:26 ET, LONG 2 lots at 29924.12, safety stop 29745.25 (1.5 x own stop 119.25 pts). Result managed +6 pts/lot (+0.05 R, $+223) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  05:41:27  price 29922.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:42:26  price 29913.39 (open -0.09 R of the book stop): state change desk [NORMAL/WNA---: NORMAL/WNA---]
  05:42:41  price 29918.76 (open -0.04 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:44:21  price 29925.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:44:36  price 29927.70 (open +0.03 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:44:51  price 29927.70 (open +0.03 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:46:43  price 29933.07 (open +0.08 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:47:39  price 29931.28 (open +0.06 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:56:52  price 29940.22 (open +0.14 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:57:07  price 29936.65 (open +0.11 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:58:26  price 29940.22 (open +0.14 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:00:20  price 29950.96 (open +0.22 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:03:13  price 29947.38 (open +0.20 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:04:32  price 29945.59 (open +0.18 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:06:51  price 29924.12 (open +0.00 R of the book stop): state change desk [ABORT/AAN---: ABORT/AAN---]
  06:06:51  price 29924.12 (open +0.00 R of the book stop): state change PROBE>OUT [AB: AB]
  06:06:51  price 29924.12 (open +0.00 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 29929.75

**LO-ZB (London MF3)** 2026-10-30 05:24:21 ET, SHORT 2 lots at 28910.62, safety stop 29089.50 (1.5 x own stop 119.25 pts). Result managed +46 pts/lot (+0.38 R, $+1823) ; own bracket: not taken (slot effect). MFE +nan R, MAE +nan R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  05:24:22  price 28910.62 (open -0.00 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  05:25:21  price 28919.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:33:13  price 28899.89 (open +0.09 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:33:28  price 28907.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:38:36  price 28932.09 (open -0.18 R of the book stop): state change desk [NORMAL/ANN---: NORMAL/ANN---]
  05:38:52  price 28928.51 (open -0.15 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:39:07  price 28935.67 (open -0.21 R of the book stop): state change desk [NORMAL/ANN---: NORMAL/ANN---]
  05:39:22  price 28935.67 (open -0.21 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:45:03  price 28905.26 (open +0.04 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:47:19  price 28880.22 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  05:47:19  price 28880.22 (open +0.26 R of the book stop): took a part [OB1: OB1]
  05:57:49  price 28885.58 (open +0.21 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  05:58:22  price 28882.01 (open +0.24 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  05:58:53  price 28883.79 (open +0.22 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:00:30  price 28883.79 (open +0.22 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:01:46  price 28858.75 (open +0.43 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:02:01  price 28864.12 (open +0.39 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:02:46  price 28860.54 (open +0.42 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:03:01  price 28865.91 (open +0.38 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:03:31  price 28856.96 (open +0.45 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:03:31  price 28856.96 (open +0.45 R of the book stop): state change DEFENDING>FREE [NB: NB]
  06:03:31  price 28856.96 (open +0.45 R of the book stop): moved the stop closer [NB: NB]
  06:04:47  price 28865.91 (open +0.38 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:05:02  price 28880.22 (open +0.26 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:07:02  price 28880.22 (open +0.26 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:08:18  price 28878.43 (open +0.27 R of the book stop): state change desk [NORMAL/NNN---: NORMAL/NNN---]
  06:08:48  price 28880.22 (open +0.26 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:11:21  price 28860.54 (open +0.42 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:12:23  price 28862.33 (open +0.41 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:13:42  price 28856.96 (open +0.45 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:13:57  price 28856.96 (open +0.45 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:14:12  price 28851.60 (open +0.49 R of the book stop): state change desk [PRESS/WNW---: PRESS/WNW---]
  06:14:12  price 28851.60 (open +0.49 R of the book stop): state change FREE>RUNNER [RT: RT]
  06:14:12  price 28851.60 (open +0.49 R of the book stop): moved the stop closer [RT: RT]
  06:14:28  price 28856.96 (open +0.45 R of the book stop): state change desk [NORMAL/WNN---: NORMAL/WNN---]
  06:16:46  price 28849.81 (open +0.51 R of the book stop): state change RUNNER>OUT [DV: DV]
  06:16:46  price 28849.81 (open +0.51 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28865.00

# DK22 PART: NP

# NY PM (NP): managed rows DK22MAIN_A, 1359 trades from 48 finished (set, month) rows, matched to the book's own bracket on 1037 signals

## Four counts (managed vs the same signal under the book's own bracket; a change is counted when the managed R differs by >= 0.25 R)

| count | trades | net $ managed minus own | by year |
|---|---|---|---|
| big give-backs prevented | 43 | +517485 | 2024 +24510, 2025 +247340, 2026 +245635 |
| winners cut short | 359 | -2273650 | 2024 -243500, 2025 -1021680, 2026 -1008470 |
| losers cut early | 227 | +1974410 | 2024 +209280, 2025 +896230, 2026 +868900 |
| losers made worse | 8 | -35210 | 2025 -7650, 2026 -27560 |
| matched pairs (all) | 1037 | -403435 | 2024 -26780, 2025 -199480, 2026 -177175 |

Slot effects (no rule 6 in the v0 rows): entries that exist only under the managed run (a freed slot): 322 trades, net $ -102045; entries that exist only under the own bracket in the same months (blocked by a carried trade): 103 trades, net $ +167951. WITH rule 6 (playbook re-entry gate): the PB1 rows have not run yet; the same table is produced when they land.

## NY PM: the 20 WORST give-backs (largest open profit given back, $)

**NP-ZN (NY PM MF2)** 2026-04-07 14:32:13 ET, LONG 6 lots at 24188.75, safety stop 24009.94 (1.5 x own stop 119.208 pts). Result managed +6 pts/lot (+0.05 R, $+668) ; own bracket result +120 pts (+1.01 R, $+14393). MFE +0.92 R, MAE -0.94 R, 41 min under water (longest 38 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 11m:N 22m:A
  14:32:14  price 24188.75 (open -0.00 R of the book stop): state change desk [ABORT/AANANN: ABORT/AANANN]
  14:33:13  price 24194.11 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:40:58  price 24170.87 (open -0.15 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:43:13  price 24158.35 (open -0.26 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:43:13  price 24158.35 (open -0.26 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:43:13  price 24158.35 (open -0.26 R of the book stop): took a part [DF: DF]
  14:43:58  price 24167.29 (open -0.18 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:45:13  price 24160.14 (open -0.24 R of the book stop): state change desk [DEFEND/NANANN: DEFEND/NANANN]
  14:45:28  price 24156.56 (open -0.27 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:46:13  price 24160.14 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:48:13  price 24147.62 (open -0.35 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:49:28  price 24145.83 (open -0.36 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:49:58  price 24147.62 (open -0.35 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  14:50:14  price 24145.83 (open -0.36 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:50:29  price 24147.62 (open -0.35 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  14:50:44  price 24145.83 (open -0.36 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:53:01  price 24133.32 (open -0.46 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  14:57:01  price 24095.77 (open -0.78 R of the book stop): state change desk [DEFEND/ANAAWA: DEFEND/ANAAWA]
  14:58:46  price 24108.28 (open -0.68 R of the book stop): state change desk [DEFEND/NNAAWA: DEFEND/NNAAWA]
  14:59:01  price 24101.13 (open -0.73 R of the book stop): state change desk [DEFEND/ANAAWA: DEFEND/ANAAWA]
  14:59:16  price 24099.34 (open -0.75 R of the book stop): state change desk [DEFEND/NNAAWA: DEFEND/NNAAWA]
  15:01:01  price 24097.56 (open -0.77 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:03:01  price 24119.01 (open -0.58 R of the book stop): state change desk [NORMAL/WNANWA: NORMAL/WNANWA]
  15:03:31  price 24117.23 (open -0.60 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:05:01  price 24110.07 (open -0.66 R of the book stop): state change desk [NORMAL/NNAWWA: NORMAL/NNAWWA]
  15:06:01  price 24097.56 (open -0.77 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:06:16  price 24092.19 (open -0.81 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  15:06:31  price 24097.56 (open -0.77 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:07:16  price 24090.40 (open -0.83 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  15:08:16  price 24122.59 (open -0.55 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:08:31  price 24097.56 (open -0.77 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  15:08:46  price 24101.13 (open -0.73 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:10:01  price 24102.92 (open -0.72 R of the book stop): state change desk [DEFEND/NNAAWA: DEFEND/NNAAWA]
  15:11:01  price 24117.23 (open -0.60 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:11:47  price 24129.74 (open -0.49 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  15:12:02  price 24120.80 (open -0.57 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:12:17  price 24126.17 (open -0.52 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  15:13:17  price 24119.01 (open -0.58 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  15:14:03  price 24126.17 (open -0.52 R of the book stop): state change desk [NORMAL/NNAWWA: NORMAL/NNAWWA]
  15:14:18  price 24133.32 (open -0.46 R of the book stop): state change desk [NORMAL/NNNWWA: NORMAL/NNNWWA]
  exit: Stop at 24194.38

**NP-ZN (NY PM MF2)** 2026-06-17 13:48:59 ET, SHORT 6 lots at 30391.79, safety stop 30570.60 (1.5 x own stop 119.208 pts). Result managed +35 pts/lot (+0.29 R, $+4208) ; own bracket result +120 pts (+1.01 R, $+14398). MFE +1.13 R, MAE -0.77 R, 11 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  13:49:00  price 30393.58 (open -0.01 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  13:49:59  price 30411.46 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:50:14  price 30409.67 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:50:29  price 30406.10 (open -0.12 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:50:44  price 30402.52 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:50:59  price 30413.25 (open -0.18 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:54:00  price 30457.95 (open -0.55 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:54:15  price 30454.38 (open -0.52 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:56:00  price 30436.49 (open -0.38 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  13:56:00  price 30436.49 (open -0.38 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:56:00  price 30436.49 (open -0.38 R of the book stop): took a part [DF: DF]
  13:57:00  price 30449.01 (open -0.48 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  13:57:15  price 30445.44 (open -0.45 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  13:58:03  price 30440.07 (open -0.41 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:00:06  price 30373.91 (open +0.15 R of the book stop): state change desk [NORMAL/WNNNAN: NORMAL/WNNNAN]
  14:00:36  price 30368.55 (open +0.20 R of the book stop): state change desk [NORMAL/WNWNAN: NORMAL/WNWNAN]
  14:00:51  price 30334.57 (open +0.48 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:00:51  price 30334.57 (open +0.48 R of the book stop): moved the stop closer [OB1: OB1]
  14:01:06  price 30332.78 (open +0.49 R of the book stop): state change desk [NORMAL/WAWNAN: NORMAL/WAWNAN]
  14:01:06  price 30332.78 (open +0.49 R of the book stop): moved the stop closer [RT: RT]
  14:01:21  price 30343.51 (open +0.41 R of the book stop): state change desk [NORMAL/WNWNAN: NORMAL/WNWNAN]
  14:01:36  price 30332.78 (open +0.49 R of the book stop): moved the stop closer [RT: RT]
  14:02:21  price 30320.27 (open +0.60 R of the book stop): moved the stop closer [RT: RT]
  14:02:36  price 30300.60 (open +0.77 R of the book stop): moved the stop closer [RT: RT]
  14:02:51  price 30271.99 (open +1.01 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  14:02:51  price 30271.99 (open +1.01 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30356.67

**NP-ZN (NY PM MF2)** 2025-03-19 12:14:15 ET, LONG 6 lots at 19692.17, safety stop 19513.35 (1.5 x own stop 119.208 pts). Result managed -23 pts/lot (-0.20 R, $-2822) ; own bracket result -112 pts (-0.94 R, $-13507). MFE +0.52 R, MAE -1.19 R, 119 min under water (longest 90 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 9m:N 29m:A
  12:14:16  price 19692.17 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:15:15  price 19686.80 (open -0.04 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:17:15  price 19685.01 (open -0.06 R of the book stop): state change desk [NORMAL/NNNAAW: NORMAL/NNNAAW]
  12:17:30  price 19683.23 (open -0.08 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:18:02  price 19683.23 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:19:03  price 19686.80 (open -0.04 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:20:03  price 19690.38 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:23:00  price 19695.74 (open +0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:31:24  price 19688.59 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:33:47  price 19679.65 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:35:03  price 19683.23 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:35:33  price 19688.59 (open -0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:35:52  price 19685.01 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:40:25  price 19663.56 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:40:40  price 19670.71 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:44:27  price 19665.34 (open -0.22 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:44:45  price 19670.71 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:52:18  price 19659.98 (open -0.27 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  12:52:33  price 19663.56 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:52:48  price 19663.56 (open -0.24 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  12:53:03  price 19668.92 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:54:04  price 19679.65 (open -0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:54:19  price 19679.65 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:54:34  price 19685.01 (open -0.06 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:55:40  price 19679.65 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:55:57  price 19679.65 (open -0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:57:05  price 19668.92 (open -0.20 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  12:58:08  price 19658.19 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:00:00  price 19672.50 (open -0.17 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:01:00  price 19677.86 (open -0.12 R of the book stop): state change desk [PRESS/WNNNWW: PRESS/WNNNWW]
  13:01:15  price 19679.65 (open -0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:05:28  price 19658.19 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:05:43  price 19652.83 (open -0.33 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:07:47  price 19649.25 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:08:02  price 19642.10 (open -0.42 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  13:08:33  price 19645.68 (open -0.39 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:09:03  price 19640.31 (open -0.43 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:09:18  price 19634.95 (open -0.48 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:09:34  price 19640.31 (open -0.43 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:10:05  price 19636.73 (open -0.46 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  exit: ExAlgoAll_OB2 at 19668.71

**NP-YM (NY PM MF3)** 2026-07-20 12:00:03 ET, SHORT 6 lots at 29048.88, safety stop 29168.00 (1.5 x own stop 79.4167 pts). Result managed +7 pts/lot (+0.09 R, $+808) ; own bracket result +40 pts (+0.50 R, $+4778). MFE +1.15 R, MAE -0.82 R, 36 min under water (longest 30 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 8m:A
  12:00:04  price 29053.64 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:01:03  price 29058.40 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:01:18  price 29063.17 (open -0.18 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  12:01:33  price 29066.74 (open -0.22 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  12:02:03  price 29046.49 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:02:48  price 29032.20 (open +0.21 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  12:06:48  price 29094.14 (open -0.57 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): took a part [DF: DF]
  12:08:34  price 29098.91 (open -0.63 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:08:49  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  12:09:04  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:09:19  price 29100.10 (open -0.65 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  12:09:34  price 29100.10 (open -0.65 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:09:49  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:10:34  price 29110.82 (open -0.78 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:16:05  price 29086.99 (open -0.48 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:25:11  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:25:26  price 29098.91 (open -0.63 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:34:57  price 29047.68 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:35:57  price 29056.02 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): state change desk [NORMAL/WNNNAA: NORMAL/WNNNAA]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): state change DEFENDING>OUT [DV: DV]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29042.08

**NP-YM (NY PM MF3)** 2026-10-01 13:30:03 ET, SHORT 6 lots at 30810.96, safety stop 30930.08 (1.5 x own stop 79.4167 pts). Result managed -42 pts/lot (-0.53 R, $-5062) ; own bracket result +40 pts (+0.50 R, $+4788). MFE +0.50 R, MAE -0.29 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  13:31:03  price 30850.27 (open -0.49 R of the book stop): state change desk [ABORT/AAANNA: ABORT/AAANNA]
  13:31:03  price 30850.27 (open -0.49 R of the book stop): state change PROBE>OUT [AB: AB]
  13:31:03  price 30850.27 (open -0.49 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 30853.08

**NP-ZN (NY PM MF2)** 2026-10-08 12:02:09 ET, LONG 6 lots at 31193.17, safety stop 31014.35 (1.5 x own stop 119.208 pts). Result managed +36 pts/lot (+0.30 R, $+4293) ; own bracket result -120 pts (-1.00 R, $-14372). MFE +0.95 R, MAE -0.22 R, 8 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 8m:N
  12:02:10  price 31191.38 (open -0.01 R of the book stop): state change desk [PRESS/NNNWWN: PRESS/NNNWWN]
  12:03:09  price 31182.44 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:04:24  price 31166.34 (open -0.22 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:04:24  price 31166.34 (open -0.22 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:04:24  price 31166.34 (open -0.22 R of the book stop): took a part [DF: DF]
  12:04:39  price 31175.29 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:05:09  price 31168.13 (open -0.21 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:05:24  price 31173.50 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:05:55  price 31175.29 (open -0.15 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:06:10  price 31178.86 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:09:25  price 31200.32 (open +0.06 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:09:40  price 31196.74 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:09:55  price 31198.53 (open +0.04 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:12:10  price 31200.32 (open +0.06 R of the book stop): state change desk [NORMAL/NNWNAA: NORMAL/NNWNAA]
  12:12:25  price 31196.74 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:12:40  price 31202.11 (open +0.08 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:13:55  price 31193.17 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:15:11  price 31193.17 (open -0.00 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:15:57  price 31191.38 (open -0.01 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  12:16:12  price 31191.38 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:16:27  price 31186.01 (open -0.06 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:16:42  price 31191.38 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:17:16  price 31218.20 (open +0.21 R of the book stop): state change desk [NORMAL/WNWNAA: NORMAL/WNWNAA]
  12:17:16  price 31218.20 (open +0.21 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:17:16  price 31218.20 (open +0.21 R of the book stop): moved the stop closer [OB1: OB1]
  12:17:31  price 31270.06 (open +0.65 R of the book stop): moved the stop closer [RT: RT]
  12:17:46  price 31291.51 (open +0.83 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  12:17:46  price 31291.51 (open +0.83 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 31229.00

**NP-ZN (NY PM MF2)** 2026-06-09 12:20:40 ET, SHORT 6 lots at 28408.83, safety stop 28587.65 (1.5 x own stop 119.208 pts). Result managed +56 pts/lot (+0.47 R, $+6713) ; own bracket result -117 pts (-0.98 R, $-14067). MFE +1.09 R, MAE -1.39 R, 17 min under water (longest 17 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  12:20:41  price 28415.99 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:21:40  price 28476.78 (open -0.57 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  12:23:10  price 28491.09 (open -0.69 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:23:55  price 28469.63 (open -0.51 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:24:10  price 28498.24 (open -0.75 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:27:10  price 28500.03 (open -0.77 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  12:29:10  price 28534.00 (open -1.05 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:29:40  price 28521.49 (open -0.95 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:30:40  price 28464.27 (open -0.46 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:31:10  price 28457.11 (open -0.41 R of the book stop): state change desk [NORMAL/WNNANW: NORMAL/WNNANW]
  12:32:10  price 28517.91 (open -0.92 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:32:25  price 28542.94 (open -1.12 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:33:55  price 28517.91 (open -0.92 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  12:34:55  price 28485.72 (open -0.65 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:35:10  price 28491.09 (open -0.69 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:35:25  price 28494.66 (open -0.72 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  12:36:10  price 28528.64 (open -1.01 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:37:40  price 28489.30 (open -0.68 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:37:55  price 28507.18 (open -0.83 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:38:10  price 28428.50 (open -0.17 R of the book stop): state change desk [NORMAL/WNNAAW: NORMAL/WNNAAW]
  12:38:26  price 28348.04 (open +0.51 R of the book stop): state change PROBE>OUT [DV: DV]
  12:38:26  price 28348.04 (open +0.51 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 28352.83

**NP-ZN (NY PM MF2)** 2026-10-16 15:01:08 ET, LONG 6 lots at 29343.38, safety stop 29164.56 (1.5 x own stop 119.208 pts). Result managed +5 pts/lot (+0.04 R, $+568) ; own bracket result +31 pts (+0.26 R, $+3768). MFE +0.65 R, MAE -0.57 R, 8 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 7m:A
  15:01:09  price 29338.01 (open -0.04 R of the book stop): state change desk [DEFEND/ANNN-A: DEFEND/ANNN-A]
  15:02:08  price 29339.80 (open -0.03 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:03:08  price 29348.74 (open +0.04 R of the book stop): state change desk [NORMAL/NNNW-A: NORMAL/NNNW-A]
  15:04:08  price 29325.49 (open -0.15 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:04:53  price 29320.13 (open -0.20 R of the book stop): state change desk [DEFEND/ANNN-A: DEFEND/ANNN-A]
  15:04:53  price 29320.13 (open -0.20 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  15:04:53  price 29320.13 (open -0.20 R of the book stop): took a part [DF: DF]
  15:05:08  price 29318.34 (open -0.21 R of the book stop): state change desk [NORMAL/NNNW-A: NORMAL/NNNW-A]
  15:05:38  price 29316.55 (open -0.22 R of the book stop): state change desk [NORMAL/ANNW-A: NORMAL/ANNW-A]
  15:06:08  price 29341.59 (open -0.01 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:06:38  price 29304.04 (open -0.33 R of the book stop): state change desk [DEFEND/ANNN-A: DEFEND/ANNN-A]
  15:08:23  price 29275.43 (open -0.57 R of the book stop): state change desk [DEFEND/ANAN-A: DEFEND/ANAN-A]
  15:08:38  price 29284.37 (open -0.49 R of the book stop): state change desk [DEFEND/ANNN-A: DEFEND/ANNN-A]
  15:09:23  price 29304.04 (open -0.33 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:10:08  price 29305.82 (open -0.32 R of the book stop): state change desk [DEFEND/NNNA-A: DEFEND/NNNA-A]
  15:11:08  price 29318.34 (open -0.21 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:13:38  price 29380.93 (open +0.32 R of the book stop): state change desk [NORMAL/NNWN-A: NORMAL/NNWN-A]
  15:13:53  price 29377.35 (open +0.29 R of the book stop): state change desk [NORMAL/NNNN-A: NORMAL/NNNN-A]
  15:14:08  price 29380.93 (open +0.32 R of the book stop): state change desk [NORMAL/NNNW-A: NORMAL/NNNW-A]
  15:14:23  price 29386.29 (open +0.36 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  15:14:23  price 29386.29 (open +0.36 R of the book stop): moved the stop closer [OB1: OB1]
  15:14:38  price 29391.65 (open +0.41 R of the book stop): state change desk [NORMAL/NNWW-A: NORMAL/NNWW-A]
  15:15:38  price 29407.75 (open +0.54 R of the book stop): moved the stop closer [RT: RT]
  exit: Stop at 29348.17

**NP-ZN (NY PM MF2)** 2026-04-09 13:35:50 ET, SHORT 6 lots at 25225.54, safety stop 25404.35 (1.5 x own stop 119.208 pts). Result managed +4 pts/lot (+0.03 R, $+418) ; own bracket: not taken (slot effect). MFE +0.64 R, MAE -0.25 R, 17 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 26m:N 27m:W
  13:35:51  price 25227.33 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:36:50  price 25232.69 (open -0.06 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:38:05  price 25236.27 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:38:20  price 25241.63 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:38:50  price 25252.36 (open -0.22 R of the book stop): state change desk [DEFEND/AAANWN: DEFEND/AAANWN]
  13:38:50  price 25252.36 (open -0.22 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:38:50  price 25252.36 (open -0.22 R of the book stop): took a part [DF: DF]
  13:39:05  price 25252.36 (open -0.22 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  13:39:20  price 25250.58 (open -0.21 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:39:35  price 25250.58 (open -0.21 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  13:39:50  price 25250.58 (open -0.21 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:40:05  price 25247.00 (open -0.18 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:41:05  price 25250.58 (open -0.21 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:41:20  price 25247.00 (open -0.18 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:41:50  price 25247.00 (open -0.18 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:42:05  price 25247.00 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:43:05  price 25243.42 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:44:06  price 25241.63 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:46:07  price 25238.06 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:47:07  price 25234.48 (open -0.08 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:49:07  price 25239.85 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:00:17  price 25229.12 (open -0.03 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  14:00:32  price 25227.33 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:02:32  price 25196.93 (open +0.24 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:03:32  price 25191.57 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:03:32  price 25191.57 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  14:03:47  price 25182.63 (open +0.36 R of the book stop): state change desk [NORMAL/WNWNAN: NORMAL/WNWNAN]
  14:04:17  price 25159.38 (open +0.55 R of the book stop): moved the stop closer [RT: RT]
  14:05:02  price 25175.47 (open +0.42 R of the book stop): state change desk [PRESS/WNWWAN: PRESS/WNWWAN]
  14:05:32  price 25173.69 (open +0.43 R of the book stop): state change desk [PRESS/WNWWNN: PRESS/WNWWNN]
  14:06:17  price 25191.57 (open +0.29 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  exit: Stop at 25222.00

**NP-ZN (NY PM MF2)** 2026-06-09 12:09:45 ET, LONG 6 lots at 28617.79, safety stop 28438.98 (1.5 x own stop 119.208 pts). Result managed -6 pts/lot (-0.05 R, $-677) ; own bracket result -120 pts (-1.01 R, $-14447). MFE +0.51 R, MAE -0.23 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  12:09:46  price 28608.85 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:10:45  price 28583.82 (open -0.29 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:10:45  price 28583.82 (open -0.29 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:10:45  price 28583.82 (open -0.29 R of the book stop): took a part [DF: DF]
  12:11:00  price 28598.12 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  12:11:15  price 28639.25 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:12:15  price 28664.28 (open +0.39 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:12:15  price 28664.28 (open +0.39 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 28612.21

**NP-YM (NY PM MF3)** 2025-04-30 14:00:03 ET, LONG 6 lots at 19482.58, safety stop 19363.46 (1.5 x own stop 79.4167 pts). Result managed +36 pts/lot (+0.46 R, $+4363) ; own bracket result +40 pts (+0.50 R, $+4783). MFE +1.27 R, MAE -0.31 R, 7 min under water (longest 7 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 7m:W
  14:00:04  price 19480.20 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:01:03  price 19467.10 (open -0.20 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  14:02:48  price 19469.48 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:03:03  price 19473.05 (open -0.12 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:04:03  price 19464.71 (open -0.22 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:06:03  price 19470.67 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:07:03  price 19518.32 (open +0.45 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:07:03  price 19518.32 (open +0.45 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  14:07:03  price 19518.32 (open +0.45 R of the book stop): took a part [OB1: OB1]
  14:07:18  price 19558.82 (open +0.96 R of the book stop): state change desk [PRESS/WNWNWN: PRESS/WNWNWN]
  14:07:18  price 19558.82 (open +0.96 R of the book stop): state change DEFENDING>FREE [NB: NB]
  14:07:18  price 19558.82 (open +0.96 R of the book stop): moved the stop closer [NB: NB]
  exit: Stop at 19519.00

**NP-ZN (NY PM MF2)** 2026-07-29 14:12:05 ET, LONG 6 lots at 27852.42, safety stop 27673.60 (1.5 x own stop 119.208 pts). Result managed -2 pts/lot (-0.02 R, $-282) ; own bracket: not taken (slot effect). MFE +0.51 R, MAE -1.23 R, 27 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  14:12:06  price 27855.99 (open +0.03 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  14:13:05  price 27823.81 (open -0.24 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  14:13:20  price 27834.54 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:13:35  price 27814.87 (open -0.32 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  14:15:05  price 27805.93 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNAW: NORMAL/NNNNAW]
  14:15:50  price 27829.17 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:16:05  price 27829.17 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:17:05  price 27811.29 (open -0.35 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): took a part [DF: DF]
  14:17:35  price 27782.68 (open -0.58 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:18:05  price 27786.26 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:18:20  price 27766.59 (open -0.72 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:18:50  price 27775.53 (open -0.65 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:19:05  price 27764.80 (open -0.73 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:19:35  price 27770.16 (open -0.69 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:20:05  price 27766.59 (open -0.72 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:20:20  price 27771.95 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:21:35  price 27737.98 (open -0.96 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:21:50  price 27752.28 (open -0.84 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:22:35  price 27743.34 (open -0.92 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:23:05  price 27759.43 (open -0.78 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:27:05  price 27746.92 (open -0.89 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:28:05  price 27752.28 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:30:05  price 27793.41 (open -0.49 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:31:35  price 27759.43 (open -0.78 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  14:31:50  price 27789.83 (open -0.52 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:32:05  price 27736.19 (open -0.98 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:32:35  price 27755.86 (open -0.81 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:32:50  price 27736.19 (open -0.98 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:33:35  price 27768.37 (open -0.70 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:36:20  price 27737.98 (open -0.96 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:36:50  price 27775.53 (open -0.65 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:37:05  price 27793.41 (open -0.49 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:38:05  price 27834.54 (open -0.15 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  14:39:05  price 27857.78 (open +0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:40:20  price 27893.54 (open +0.35 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:40:20  price 27893.54 (open +0.35 R of the book stop): moved the stop closer [OB1: OB1]
  14:40:50  price 27911.42 (open +0.49 R of the book stop): state change RUNNER>OUT [DV: DV]
  exit: ExAlgoAll_DV at 27850.12

**NP-ZN (NY PM MF2)** 2026-05-11 12:31:16 ET, SHORT 6 lots at 29473.88, safety stop 29652.69 (1.5 x own stop 119.208 pts). Result managed +46 pts/lot (+0.39 R, $+5513) ; own bracket result +45 pts (+0.38 R, $+5368). MFE +0.89 R, MAE -0.02 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 3m:W
  12:31:17  price 29473.88 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:35:16  price 29464.93 (open +0.08 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  12:35:16  price 29464.93 (open +0.08 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:35:16  price 29464.93 (open +0.08 R of the book stop): took a part [DF: DF]
  12:36:47  price 29459.57 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:37:02  price 29457.78 (open +0.14 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  12:37:17  price 29459.57 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:39:33  price 29438.11 (open +0.30 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:39:33  price 29438.11 (open +0.30 R of the book stop): moved the stop closer [OB1: OB1]
  12:40:03  price 29436.32 (open +0.32 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  12:40:18  price 29438.11 (open +0.30 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:41:18  price 29432.75 (open +0.35 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  12:42:03  price 29411.29 (open +0.52 R of the book stop): state change desk [NORMAL/NNWWAA: NORMAL/NNWWAA]
  12:42:03  price 29411.29 (open +0.52 R of the book stop): state change RUNNER>FREE [NB: NB]
  12:42:03  price 29411.29 (open +0.52 R of the book stop): moved the stop closer [NB: NB]
  12:42:18  price 29389.83 (open +0.70 R of the book stop): state change desk [NORMAL/NAWWAA: NORMAL/NAWWAA]
  12:42:18  price 29389.83 (open +0.70 R of the book stop): state change FREE>OUT [OB2: OB2]
  12:42:18  price 29389.83 (open +0.70 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29427.88

**NP-ZN (NY PM MF2)** 2026-05-21 13:23:06 ET, SHORT 6 lots at 29418.79, safety stop 29597.60 (1.5 x own stop 119.208 pts). Result managed +30 pts/lot (+0.25 R, $+3578) ; own bracket: not taken (slot effect). MFE +0.75 R, MAE -1.08 R, 79 min under water (longest 74 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 19m:A
  13:23:07  price 29425.94 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:24:06  price 29400.91 (open +0.15 R of the book stop): state change desk [DEFEND/NNWAAA: DEFEND/NNWAAA]
  13:24:06  price 29400.91 (open +0.15 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:24:06  price 29400.91 (open +0.15 R of the book stop): took a part [DF: DF]
  13:24:21  price 29404.49 (open +0.12 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  13:24:36  price 29413.43 (open +0.04 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  13:25:06  price 29424.16 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:28:07  price 29409.85 (open +0.08 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  13:30:07  price 29418.79 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:30:37  price 29431.31 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  13:31:07  price 29431.31 (open -0.11 R of the book stop): state change desk [DEFEND/ANNAWA: DEFEND/ANNAWA]
  13:32:07  price 29449.19 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  13:32:22  price 29442.04 (open -0.20 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:33:37  price 29424.16 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:35:37  price 29459.92 (open -0.35 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:38:07  price 29454.55 (open -0.30 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:39:54  price 29458.13 (open -0.33 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:42:54  price 29483.16 (open -0.54 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  13:43:09  price 29477.80 (open -0.49 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:44:09  price 29481.38 (open -0.52 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  13:44:24  price 29484.95 (open -0.55 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  13:44:54  price 29488.53 (open -0.58 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  13:45:09  price 29492.10 (open -0.61 R of the book stop): state change desk [DEFEND/ANAAWA: DEFEND/ANAAWA]
  13:45:24  price 29493.89 (open -0.63 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  13:45:39  price 29488.53 (open -0.58 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  13:45:54  price 29479.59 (open -0.51 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  13:46:09  price 29481.38 (open -0.52 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:46:24  price 29483.16 (open -0.54 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  13:46:40  price 29479.59 (open -0.51 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:46:55  price 29484.95 (open -0.55 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  13:47:10  price 29486.74 (open -0.57 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:49:25  price 29493.89 (open -0.63 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  13:49:40  price 29502.83 (open -0.70 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  13:49:55  price 29495.68 (open -0.65 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  13:50:10  price 29499.26 (open -0.68 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  13:50:25  price 29492.10 (open -0.61 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  13:51:10  price 29504.62 (open -0.72 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  13:52:10  price 29515.35 (open -0.81 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  13:55:10  price 29543.96 (open -1.05 R of the book stop): state change desk [DEFEND/ANAAWA: DEFEND/ANAAWA]
  13:56:10  price 29538.60 (open -1.01 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  exit: ExAlgoAll_OB2 at 29388.92

**NP-ZN (NY PM MF2)** 2025-04-30 14:17:38 ET, SHORT 6 lots at 19536.58, safety stop 19715.40 (1.5 x own stop 119.208 pts). Result managed +15 pts/lot (+0.13 R, $+1793) ; own bracket result -119 pts (-1.00 R, $-14252). MFE +0.62 R, MAE -0.12 R, 3 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W
  14:17:39  price 19536.58 (open -0.00 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:18:38  price 19536.58 (open +0.00 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  14:18:38  price 19536.58 (open +0.00 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:18:38  price 19536.58 (open +0.00 R of the book stop): took a part [DF: DF]
  14:19:23  price 19529.43 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:19:38  price 19527.64 (open +0.08 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  14:24:23  price 19529.43 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:26:39  price 19538.37 (open -0.01 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:27:09  price 19534.80 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:27:24  price 19536.58 (open +0.00 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:27:54  price 19527.64 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:31:39  price 19502.61 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:31:39  price 19502.61 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 19521.58

**NP-ZN (NY PM MF2)** 2026-03-31 12:37:36 ET, LONG 6 lots at 23567.96, safety stop 23389.15 (1.5 x own stop 119.208 pts). Result managed +79 pts/lot (+0.66 R, $+9503) ; own bracket: not taken (slot effect). MFE +1.15 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  12:37:37  price 23567.96 (open -0.00 R of the book stop): state change desk [ABORT/AANNNA: ABORT/AANNNA]
  12:38:36  price 23594.78 (open +0.22 R of the book stop): state change desk [PRESS/WNWNAW: PRESS/WNWNAW]
  12:38:51  price 23600.14 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  12:38:51  price 23600.14 (open +0.27 R of the book stop): took a part [OB1: OB1]
  12:39:36  price 23630.54 (open +0.52 R of the book stop): state change DEFENDING>FREE [NB: NB]
  12:39:36  price 23630.54 (open +0.52 R of the book stop): moved the stop closer [NB: NB]
  12:39:51  price 23646.64 (open +0.66 R of the book stop): moved the stop closer [NB: NB]
  12:40:06  price 23689.55 (open +1.02 R of the book stop): state change FREE>OUT [OB2: OB2]
  12:40:06  price 23689.55 (open +1.02 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 23647.21

**NP-ZN (NY PM MF2)** 2025-04-09 14:07:50 ET, SHORT 6 lots at 18829.75, safety stop 19008.56 (1.5 x own stop 119.208 pts). Result managed +30 pts/lot (+0.25 R, $+3573) ; own bracket result -108 pts (-0.90 R, $-12937). MFE +0.73 R, MAE -0.05 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  14:07:51  price 18833.33 (open -0.03 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:08:50  price 18765.38 (open +0.54 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:08:50  price 18765.38 (open +0.54 R of the book stop): state change PROBE>OUT [DV: DV]
  14:08:50  price 18765.38 (open +0.54 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 18799.92

**NP-YM (NY PM MF3)** 2025-02-28 13:30:03 ET, SHORT 6 lots at 20586.88, safety stop 20706.00 (1.5 x own stop 79.4167 pts). Result managed -16 pts/lot (-0.20 R, $-1902) ; own bracket result +40 pts (+0.50 R, $+4778). MFE +0.52 R, MAE -1.10 R, 27 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  13:30:04  price 20578.54 (open +0.11 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:31:03  price 20605.94 (open -0.24 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:31:18  price 20602.36 (open -0.20 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:31:33  price 20608.32 (open -0.27 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:32:18  price 20594.02 (open -0.09 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:34:33  price 20617.85 (open -0.39 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:35:03  price 20620.23 (open -0.42 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:40:03  price 20640.48 (open -0.68 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  13:40:03  price 20640.48 (open -0.68 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:40:03  price 20640.48 (open -0.68 R of the book stop): took a part [DF: DF]
  13:42:03  price 20629.76 (open -0.54 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:43:18  price 20621.42 (open -0.43 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:44:18  price 20638.10 (open -0.65 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:46:18  price 20632.14 (open -0.57 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:47:03  price 20642.86 (open -0.70 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:47:18  price 20634.53 (open -0.60 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  13:48:18  price 20635.72 (open -0.61 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:52:18  price 20650.01 (open -0.80 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:52:48  price 20640.48 (open -0.68 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:53:03  price 20650.01 (open -0.80 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:53:18  price 20642.86 (open -0.70 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:56:03  price 20597.60 (open -0.14 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:56:18  price 20607.13 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:56:33  price 20584.49 (open +0.03 R of the book stop): state change desk [PRESS/WNNNWN: PRESS/WNNNWN]
  13:58:03  price 20569.01 (open +0.22 R of the book stop): state change desk [PRESS/WNNWWN: PRESS/WNNWWN]
  13:58:18  price 20557.09 (open +0.38 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  13:58:18  price 20557.09 (open +0.38 R of the book stop): moved the stop closer [OB1: OB1]
  13:59:33  price 20541.61 (open +0.57 R of the book stop): moved the stop closer [RT: RT]
  14:00:33  price 20564.24 (open +0.29 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  14:00:33  price 20564.24 (open +0.29 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  14:00:33  price 20564.24 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 20602.67

**NP-ZN (NY PM MF2)** 2024-10-07 12:10:18 ET, SHORT 6 lots at 20118.88, safety stop 20297.69 (1.5 x own stop 119.208 pts). Result managed +18 pts/lot (+0.15 R, $+2178) ; own bracket result +120 pts (+1.01 R, $+14378). MFE +0.63 R, MAE -0.40 R, 116 min under water (longest 43 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 8m:A 61m:N
  12:10:19  price 20120.66 (open -0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:11:18  price 20124.24 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:11:33  price 20124.24 (open -0.04 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:11:48  price 20126.03 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:12:18  price 20126.03 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:13:33  price 20131.39 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:15:03  price 20138.54 (open -0.17 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:16:03  price 20143.91 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:17:18  price 20151.06 (open -0.27 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:17:18  price 20151.06 (open -0.27 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:17:18  price 20151.06 (open -0.27 R of the book stop): took a part [DF: DF]
  12:18:03  price 20158.21 (open -0.33 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:19:03  price 20160.00 (open -0.35 R of the book stop): state change desk [DEFEND/NAAANN: DEFEND/NAAANN]
  12:19:18  price 20158.21 (open -0.33 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:21:03  price 20160.00 (open -0.35 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  12:21:18  price 20165.37 (open -0.39 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  12:21:33  price 20161.79 (open -0.36 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  12:22:03  price 20163.58 (open -0.38 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:23:03  price 20167.15 (open -0.41 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:23:18  price 20163.58 (open -0.38 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:30:37  price 20152.85 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:32:07  price 20136.76 (open -0.15 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:32:52  price 20138.54 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:33:07  price 20136.76 (open -0.15 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:33:22  price 20143.91 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:34:08  price 20145.70 (open -0.22 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:34:38  price 20136.76 (open -0.15 R of the book stop): state change desk [NORMAL/WNNWNA: NORMAL/WNNWNA]
  12:35:08  price 20140.33 (open -0.18 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:36:08  price 20143.91 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:39:11  price 20145.70 (open -0.22 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:43:11  price 20131.39 (open -0.11 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:43:26  price 20134.97 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:43:41  price 20133.18 (open -0.12 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:44:11  price 20131.39 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:45:43  price 20122.45 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:45:58  price 20126.03 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:46:14  price 20122.45 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:46:29  price 20120.66 (open -0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:46:44  price 20122.45 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:46:59  price 20120.66 (open -0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  exit: ExAlgoAll_OB2 at 20100.67

**NP-ZN (NY PM MF2)** 2026-09-08 12:11:30 ET, SHORT 6 lots at 29581.38, safety stop 29760.19 (1.5 x own stop 119.208 pts). Result managed +5 pts/lot (+0.04 R, $+558) ; own bracket result +39 pts (+0.33 R, $+4703). MFE +0.51 R, MAE -0.51 R, 127 min under water (longest 95 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A 5m:N 9m:W 12m:N 40m:A 48m:N 98m:A
  12:11:31  price 29581.38 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:13:00  price 29579.59 (open +0.01 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  12:15:00  price 29588.53 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:15:30  price 29586.74 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:15:45  price 29581.38 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:25:30  price 29602.83 (open -0.18 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:26:15  price 29592.10 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:26:45  price 29586.74 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:27:00  price 29583.16 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:27:15  price 29583.16 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:27:30  price 29583.16 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:27:45  price 29581.38 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:31:01  price 29567.07 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:31:16  price 29568.86 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:33:48  price 29576.01 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:48:22  price 29590.32 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:48:53  price 29590.32 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:50:38  price 29604.62 (open -0.20 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:53:09  price 29590.32 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:53:54  price 29601.04 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:54:24  price 29597.47 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:01:10  price 29601.04 (open -0.17 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:01:25  price 29608.20 (open -0.22 R of the book stop): state change desk [NORMAL/ANNWNN: NORMAL/ANNWNN]
  13:02:10  price 29618.93 (open -0.32 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:03:10  price 29617.14 (open -0.30 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:04:10  price 29618.93 (open -0.32 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:04:10  price 29618.93 (open -0.32 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:04:10  price 29618.93 (open -0.32 R of the book stop): took a part [DF: DF]
  13:06:55  price 29638.60 (open -0.48 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:07:10  price 29636.81 (open -0.46 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:09:10  price 29618.93 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:22:27  price 29613.56 (open -0.27 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:22:42  price 29615.35 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:32:43  price 29624.29 (open -0.36 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:33:13  price 29624.29 (open -0.36 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:33:28  price 29624.29 (open -0.36 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:36:15  price 29624.29 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:38:01  price 29629.65 (open -0.41 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:38:48  price 29624.29 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:47:07  price 29606.41 (open -0.21 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  exit: ExAlgoAll_OB at 29576.67

## NY PM: the 20 BEST runners (largest final R among trades that kept at least 80% of their peak)

**NP-YM (NY PM MF3)** 2025-04-16 13:30:03 ET, SHORT 6 lots at 18594.62, safety stop 18713.75 (1.5 x own stop 79.4167 pts). Result managed +89 pts/lot (+1.13 R, $+10728) ; own bracket result +40 pts (+0.50 R, $+4778). MFE +1.26 R, MAE -0.25 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  13:30:04  price 18573.18 (open +0.27 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  13:31:03  price 18531.49 (open +0.80 R of the book stop): state change desk [NORMAL/WNWAAW: NORMAL/WNWAAW]
  13:31:03  price 18531.49 (open +0.80 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  13:31:03  price 18531.49 (open +0.80 R of the book stop): took a part [OB1: OB1]
  13:31:18  price 18524.34 (open +0.89 R of the book stop): state change DEFENDING>FREE [NB: NB]
  13:31:18  price 18524.34 (open +0.89 R of the book stop): moved the stop closer [NB: NB]
  13:31:33  price 18493.37 (open +1.27 R of the book stop): moved the stop closer [NB: NB]
  13:31:48  price 18477.88 (open +1.47 R of the book stop): state change FREE>OUT [OB2: OB2]
  13:31:48  price 18477.88 (open +1.47 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18505.17

**NP-ZN (NY PM MF2)** 2025-04-09 13:34:16 ET, LONG 6 lots at 18663.50, safety stop 18484.69 (1.5 x own stop 119.208 pts). Result managed +126 pts/lot (+1.05 R, $+15063) ; own bracket result +120 pts (+1.01 R, $+14393). MFE +1.31 R, MAE -0.14 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  13:34:17  price 18677.81 (open +0.12 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  13:35:16  price 18752.91 (open +0.75 R of the book stop): state change desk [PRESS/WNWAWW: PRESS/WNWAWW]
  13:35:16  price 18752.91 (open +0.75 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  13:35:16  price 18752.91 (open +0.75 R of the book stop): took a part [OB1: OB1]
  13:35:31  price 18829.80 (open +1.40 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  13:35:31  price 18829.80 (open +1.40 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 18789.08

## NY PM: 50 RANDOM trades (seed 11)

**NP-YM (NY PM MF3)** 2024-10-02 13:30:03 ET, SHORT 6 lots at 20012.75, safety stop 20131.88 (1.5 x own stop 79.4167 pts). Result managed +16 pts/lot (+0.20 R, $+1918) ; own bracket result +40 pts (+0.50 R, $+4793). MFE +0.57 R, MAE -0.08 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  13:30:04  price 20012.75 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:31:03  price 20000.84 (open +0.15 R of the book stop): state change desk [NORMAL/NNWAWN: NORMAL/NNWAWN]
  13:31:18  price 20004.41 (open +0.11 R of the book stop): state change desk [NORMAL/ANNAWN: NORMAL/ANNAWN]
  13:31:33  price 20007.99 (open +0.06 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:31:33  price 20007.99 (open +0.06 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:31:33  price 20007.99 (open +0.06 R of the book stop): took a part [DF: DF]
  13:32:03  price 20002.03 (open +0.14 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  13:32:18  price 19999.65 (open +0.17 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:33:03  price 19992.50 (open +0.26 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  13:33:18  price 19990.12 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  13:33:18  price 19990.12 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  13:35:03  price 19975.82 (open +0.46 R of the book stop): state change desk [PRESS/NNWWNW: PRESS/NNWWNW]
  13:35:33  price 19971.06 (open +0.52 R of the book stop): state change RUNNER>FREE [NB: NB]
  13:35:33  price 19971.06 (open +0.52 R of the book stop): moved the stop closer [NB: NB]
  13:36:03  price 19985.35 (open +0.35 R of the book stop): state change FREE>OUT [OB2: OB2]
  13:36:03  price 19985.35 (open +0.35 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19996.71

**NP-YM (NY PM MF3)** 2024-10-14 13:00:03 ET, LONG 6 lots at 20603.92, safety stop 20484.79 (1.5 x own stop 79.4167 pts). Result managed +2 pts/lot (+0.02 R, $+173) ; own bracket result +40 pts (+0.50 R, $+4803). MFE +0.30 R, MAE -0.13 R, 17 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 3m:W 21m:N
  13:00:04  price 20603.92 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:01:03  price 20605.11 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:02:50  price 20614.64 (open +0.14 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:03:05  price 20613.45 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:03:50  price 20618.21 (open +0.18 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:06:51  price 20615.83 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:07:06  price 20609.87 (open +0.08 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  13:07:21  price 20611.06 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:20:30  price 20596.77 (open -0.09 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:20:45  price 20600.34 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:25:31  price 20609.87 (open +0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:25:46  price 20611.06 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:26:16  price 20611.06 (open +0.09 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:27:33  price 20608.68 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:30:09  price 20606.30 (open +0.03 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:30:39  price 20605.11 (open +0.01 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:31:11  price 20608.68 (open +0.06 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  13:32:27  price 20601.53 (open -0.03 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:32:42  price 20603.92 (open +0.00 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  13:33:12  price 20601.53 (open -0.03 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:33:57  price 20600.34 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:34:12  price 20597.96 (open -0.08 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:34:42  price 20595.58 (open -0.11 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:34:42  price 20595.58 (open -0.11 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:34:42  price 20595.58 (open -0.11 R of the book stop): took a part [DF: DF]
  13:34:57  price 20597.96 (open -0.08 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  13:35:42  price 20600.34 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:37:01  price 20602.73 (open -0.01 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:38:01  price 20611.06 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:38:16  price 20612.26 (open +0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:40:47  price 20608.68 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:44:04  price 20609.87 (open +0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:45:04  price 20611.06 (open +0.09 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:47:50  price 20606.30 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:48:20  price 20608.68 (open +0.06 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:48:35  price 20607.49 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:48:51  price 20608.68 (open +0.06 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:50:07  price 20612.26 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:54:14  price 20612.26 (open +0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:57:18  price 20608.68 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  exit: Stop at 20605.42

**NP-YM (NY PM MF3)** 2024-11-04 15:30:03 ET, LONG 6 lots at 20112.88, safety stop 19993.75 (1.5 x own stop 79.4167 pts). Result managed -13 pts/lot (-0.17 R, $-1597) ; own bracket result -26 pts (-0.32 R, $-3102). MFE +0.06 R, MAE -0.56 R, 29 min under water (longest 29 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:A
  15:30:04  price 20114.07 (open +0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  15:31:03  price 20112.88 (open -0.00 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  15:31:03  price 20112.88 (open -0.00 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  15:31:03  price 20112.88 (open -0.00 R of the book stop): took a part [DF: DF]
  15:35:03  price 20097.39 (open -0.20 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  15:39:19  price 20087.86 (open -0.32 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  15:39:34  price 20085.48 (open -0.35 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  15:40:19  price 20085.48 (open -0.35 R of the book stop): state change desk [DEFEND/NNAANA: DEFEND/NNAANA]
  15:41:19  price 20103.35 (open -0.12 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  15:42:04  price 20105.73 (open -0.09 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  15:43:04  price 20096.20 (open -0.21 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  15:43:19  price 20098.58 (open -0.18 R of the book stop): state change desk [NORMAL/WNNWNA: NORMAL/WNNWNA]
  15:45:49  price 20098.58 (open -0.18 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  15:46:34  price 20090.24 (open -0.29 R of the book stop): state change desk [NORMAL/ANNWNA: NORMAL/ANNWNA]
  15:46:49  price 20100.96 (open -0.15 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  15:48:04  price 20106.92 (open -0.08 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  15:48:19  price 20105.73 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:50:04  price 20091.43 (open -0.27 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  15:51:20  price 20086.67 (open -0.33 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  15:53:05  price 20090.24 (open -0.29 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  15:53:50  price 20098.58 (open -0.18 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  15:54:05  price 20097.39 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:55:05  price 20085.48 (open -0.35 R of the book stop): state change desk [DEFEND/NAANNA: DEFEND/NAANNA]
  15:55:20  price 20086.67 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:55:35  price 20081.90 (open -0.39 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  15:55:50  price 20087.86 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:56:05  price 20079.52 (open -0.42 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  15:59:20  price 20085.48 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:59:35  price 20083.09 (open -0.38 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  exit: UWTime at 20099.62

**NP-ZN (NY PM MF2)** 2024-11-21 15:17:19 ET, SHORT 6 lots at 20873.71, safety stop 21052.52 (1.5 x own stop 119.208 pts). Result managed +2 pts/lot (+0.02 R, $+263) ; own bracket: not taken (slot effect). MFE +0.12 R, MAE -0.04 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 8m:W
  15:17:22  price 20873.71 (open -0.00 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  15:18:20  price 20871.92 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:20:20  price 20873.71 (open -0.00 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  15:20:20  price 20873.71 (open -0.00 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  15:20:20  price 20873.71 (open -0.00 R of the book stop): took a part [DF: DF]
  15:20:50  price 20868.34 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:25:36  price 20866.56 (open +0.06 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:28:07  price 20861.19 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:28:37  price 20868.34 (open +0.04 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:29:52  price 20870.13 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:30:07  price 20868.34 (open +0.04 R of the book stop): state change DEFENDING>OUT [CL: CL]
  15:30:07  price 20868.34 (open +0.04 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 20871.46

**NP-YM (NY PM MF3)** 2024-11-25 14:30:03 ET, SHORT 6 lots at 20851.67, safety stop 20970.79 (1.5 x own stop 79.4167 pts). Result managed -19 pts/lot (-0.24 R, $-2332) ; own bracket: not taken (slot effect). MFE +0.24 R, MAE -0.28 R, 6 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 18m:N
  14:30:05  price 20852.86 (open -0.01 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  14:31:03  price 20837.37 (open +0.18 R of the book stop): state change desk [NORMAL/NNWANN: NORMAL/NNWANN]
  14:31:18  price 20838.56 (open +0.17 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:32:03  price 20840.95 (open +0.14 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:32:33  price 20842.14 (open +0.12 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  14:32:48  price 20843.33 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:33:03  price 20840.95 (open +0.14 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:33:19  price 20838.56 (open +0.17 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  14:33:34  price 20840.95 (open +0.14 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:34:04  price 20838.56 (open +0.17 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  14:34:19  price 20842.14 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:34:35  price 20838.56 (open +0.17 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  14:34:50  price 20839.75 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:35:05  price 20842.14 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:36:05  price 20845.71 (open +0.08 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:37:06  price 20844.52 (open +0.09 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  14:38:22  price 20843.33 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:38:39  price 20843.33 (open +0.11 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  14:39:09  price 20844.52 (open +0.09 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:39:54  price 20843.33 (open +0.11 R of the book stop): state change desk [PRESS/NNWNWN: PRESS/NNWNWN]
  14:40:24  price 20842.14 (open +0.12 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:41:24  price 20846.90 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:42:54  price 20856.43 (open -0.06 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:43:09  price 20854.05 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:43:39  price 20857.62 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:46:39  price 20861.20 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:47:09  price 20863.58 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:48:09  price 20871.92 (open -0.26 R of the book stop): state change desk [ABORT/AANANN: ABORT/AANANN]
  14:48:09  price 20871.92 (open -0.26 R of the book stop): state change PROBE>OUT [AB: AB]
  14:48:09  price 20871.92 (open -0.26 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 20871.04

**NP-YM (NY PM MF3)** 2024-12-19 12:30:03 ET, LONG 6 lots at 21460.42, safety stop 21341.29 (1.5 x own stop 79.4167 pts). Result managed +7 pts/lot (+0.09 R, $+868) ; own bracket result +40 pts (+0.50 R, $+4803). MFE +0.43 R, MAE -0.45 R, 22 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 7m:A 11m:N 25m:A 26m:N 27m:W
  12:30:04  price 21467.56 (open +0.09 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:31:03  price 21462.80 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:31:18  price 21456.84 (open -0.04 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:32:03  price 21446.12 (open -0.18 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  12:32:18  price 21436.59 (open -0.30 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  12:32:18  price 21436.59 (open -0.30 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:32:18  price 21436.59 (open -0.30 R of the book stop): took a part [DF: DF]
  12:32:33  price 21446.12 (open -0.18 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:32:48  price 21442.55 (open -0.22 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  12:33:03  price 21446.12 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:34:03  price 21461.61 (open +0.01 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:35:03  price 21450.89 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:35:33  price 21463.99 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:35:48  price 21452.08 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:36:18  price 21449.70 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  12:37:03  price 21449.70 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:42:19  price 21440.17 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:42:34  price 21447.31 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:47:19  price 21471.14 (open +0.14 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  12:47:34  price 21474.71 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:50:49  price 21449.70 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:51:04  price 21455.65 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:51:19  price 21453.27 (open -0.09 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:54:19  price 21456.84 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:55:04  price 21468.76 (open +0.11 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:56:04  price 21481.86 (open +0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:57:04  price 21494.96 (open +0.43 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:57:04  price 21494.96 (open +0.43 R of the book stop): moved the stop closer [OB1: OB1]
  12:57:19  price 21499.73 (open +0.49 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  12:57:19  price 21499.73 (open +0.49 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21467.71

**NP-YM (NY PM MF3)** 2024-12-31 12:30:03 ET, LONG 6 lots at 21260.25, safety stop 21141.12 (1.5 x own stop 79.4167 pts). Result managed +9 pts/lot (+0.11 R, $+1038) ; own bracket result +40 pts (+0.50 R, $+4793). MFE +0.35 R, MAE -0.65 R, 23 min under water (longest 23 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 6m:N 9m:A
  12:30:04  price 21259.06 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:31:03  price 21259.06 (open -0.01 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  12:31:33  price 21265.01 (open +0.06 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:31:33  price 21265.01 (open +0.06 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:31:33  price 21265.01 (open +0.06 R of the book stop): took a part [DF: DF]
  12:32:33  price 21248.34 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:32:48  price 21245.96 (open -0.18 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:33:03  price 21241.19 (open -0.24 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:33:18  price 21242.38 (open -0.22 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:33:33  price 21236.42 (open -0.30 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:34:03  price 21237.62 (open -0.29 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  12:34:18  price 21244.76 (open -0.20 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:35:18  price 21244.76 (open -0.20 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  12:36:03  price 21240.00 (open -0.26 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:36:33  price 21236.42 (open -0.30 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  12:37:03  price 21229.28 (open -0.39 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:39:04  price 21216.17 (open -0.55 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  12:40:04  price 21218.56 (open -0.52 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:42:04  price 21224.51 (open -0.45 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  12:43:04  price 21225.70 (open -0.43 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:44:04  price 21234.04 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:50:07  price 21223.32 (open -0.46 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:51:07  price 21230.47 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:54:37  price 21255.49 (open -0.06 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  12:57:07  price 21276.93 (open +0.21 R of the book stop): state change desk [PRESS/WNWWNA: PRESS/WNWWNA]
  12:57:07  price 21276.93 (open +0.21 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:57:07  price 21276.93 (open +0.21 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 21268.96

**NP-ZN (NY PM MF2)** 2025-01-21 12:48:29 ET, SHORT 6 lots at 21719.83, safety stop 21898.65 (1.5 x own stop 119.208 pts). Result managed -34 pts/lot (-0.28 R, $-4072) ; own bracket result +2 pts (+0.02 R, $+213). MFE +0.01 R, MAE -0.43 R, 28 min under water (longest 27 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  12:48:30  price 21719.83 (open -0.00 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:49:29  price 21721.62 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:56:14  price 21737.71 (open -0.15 R of the book stop): state change desk [DEFEND/NANNNA: DEFEND/NANNNA]
  12:56:14  price 21737.71 (open -0.15 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:56:14  price 21737.71 (open -0.15 R of the book stop): took a part [DF: DF]
  12:56:29  price 21739.50 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:05:15  price 21744.87 (open -0.21 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:05:30  price 21739.50 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:10:47  price 21744.87 (open -0.21 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:12:02  price 21737.71 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:12:17  price 21741.29 (open -0.18 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:13:02  price 21744.87 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:13:32  price 21752.02 (open -0.27 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:16:47  price 21769.90 (open -0.42 R of the book stop): state change desk [ABORT/AANNNA: ABORT/AANNNA]
  13:16:47  price 21769.90 (open -0.42 R of the book stop): state change DEFENDING>OUT [AB: AB]
  13:16:47  price 21769.90 (open -0.42 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 21753.71

**NP-ZN (NY PM MF2)** 2025-01-29 14:41:49 ET, LONG 6 lots at 21555.46, safety stop 21376.65 (1.5 x own stop 119.208 pts). Result managed +34 pts/lot (+0.29 R, $+4073) ; own bracket: not taken (slot effect). MFE +0.33 R, MAE -0.80 R, 38 min under water (longest 24 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 6m:W 18m:N 23m:A
  14:41:50  price 21559.03 (open +0.03 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  14:42:49  price 21534.00 (open -0.18 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  14:44:04  price 21546.52 (open -0.08 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:44:19  price 21519.70 (open -0.30 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  14:45:04  price 21535.79 (open -0.17 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:45:19  price 21516.12 (open -0.33 R of the book stop): state change desk [NORMAL/NNAWNW: NORMAL/NNAWNW]
  14:46:04  price 21535.79 (open -0.17 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:47:04  price 21544.73 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:48:04  price 21567.98 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:49:04  price 21534.00 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:50:04  price 21551.88 (open -0.03 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:51:04  price 21548.31 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:51:49  price 21560.82 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:54:04  price 21551.88 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:54:34  price 21559.03 (open +0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:55:19  price 21555.46 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:57:04  price 21514.33 (open -0.35 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  14:57:19  price 21525.06 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:57:49  price 21560.82 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:58:04  price 21553.67 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:59:04  price 21539.37 (open -0.14 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  15:00:04  price 21535.79 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  15:00:19  price 21550.09 (open -0.04 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  15:02:20  price 21532.21 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  15:03:05  price 21519.70 (open -0.30 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  15:04:05  price 21496.45 (open -0.49 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  15:04:35  price 21503.60 (open -0.43 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  15:04:50  price 21492.87 (open -0.52 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  15:05:50  price 21517.91 (open -0.32 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  15:06:05  price 21516.12 (open -0.33 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  15:08:05  price 21505.39 (open -0.42 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  15:13:21  price 21503.60 (open -0.43 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  15:13:36  price 21517.91 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  15:17:36  price 21471.42 (open -0.70 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  15:18:06  price 21480.36 (open -0.63 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  15:18:21  price 21485.72 (open -0.58 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  15:18:51  price 21480.36 (open -0.63 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  15:19:06  price 21489.30 (open -0.55 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  15:21:06  price 21508.97 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:23:06  price 21553.67 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  exit: ExAlgoAll_OB2 at 21589.46

**NP-YM (NY PM MF3)** 2025-02-11 15:30:03 ET, LONG 6 lots at 21807.92, safety stop 21688.79 (1.5 x own stop 79.4167 pts). Result managed -1 pts/lot (-0.01 R, $-97) ; own bracket result -13 pts (-0.16 R, $-1512). MFE +0.05 R, MAE -0.04 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N
  15:30:04  price 21806.73 (open -0.01 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  15:31:03  price 21807.92 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:31:03  price 21807.92 (open -0.00 R of the book stop): state change PROBE>OUT [CL: CL]
  15:31:03  price 21807.92 (open -0.00 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 21807.17

**NP-ZN (NY PM MF2)** 2025-03-21 14:26:48 ET, SHORT 6 lots at 19839.58, safety stop 20018.40 (1.5 x own stop 119.208 pts). Result managed -14 pts/lot (-0.12 R, $-1712) ; own bracket result -120 pts (-1.01 R, $-14397). MFE +0.21 R, MAE -0.43 R, 45 min under water (longest 36 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 44m:N 60m:A 61m:N
  14:26:49  price 19837.80 (open +0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  14:27:48  price 19841.37 (open -0.01 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:28:03  price 19843.16 (open -0.03 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:29:03  price 19846.74 (open -0.06 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  14:29:33  price 19844.95 (open -0.04 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:30:03  price 19841.37 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:31:03  price 19855.68 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:31:48  price 19861.04 (open -0.18 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:32:48  price 19859.25 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:37:49  price 19871.77 (open -0.27 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:37:49  price 19871.77 (open -0.27 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:37:49  price 19871.77 (open -0.27 R of the book stop): took a part [DF: DF]
  14:44:05  price 19880.71 (open -0.35 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:44:35  price 19884.29 (open -0.38 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:45:06  price 19886.07 (open -0.39 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:45:36  price 19878.92 (open -0.33 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:45:51  price 19877.13 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:49:06  price 19853.89 (open -0.12 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:53:06  price 19850.31 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:56:51  price 19869.98 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:57:06  price 19864.62 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:57:21  price 19869.98 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:57:36  price 19868.19 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:57:51  price 19875.35 (open -0.30 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:59:21  price 19864.62 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:00:06  price 19853.89 (open -0.12 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  15:00:21  price 19850.31 (open -0.09 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  15:01:06  price 19846.74 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:02:06  price 19850.31 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:02:36  price 19848.52 (open -0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:03:06  price 19837.80 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  15:05:07  price 19841.37 (open -0.01 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  15:07:08  price 19839.58 (open +0.00 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:08:08  price 19827.07 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:10:08  price 19821.70 (open +0.15 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:10:23  price 19821.70 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:10:38  price 19818.13 (open +0.18 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:12:38  price 19818.13 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:13:08  price 19821.70 (open +0.15 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:15:08  price 19834.22 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  exit: ExAlgoAll_CL at 19853.79

**NP-YM (NY PM MF3)** 2025-03-31 15:00:03 ET, LONG 6 lots at 19347.88, safety stop 19228.75 (1.5 x own stop 79.4167 pts). Result managed +50 pts/lot (+0.63 R, $+5958) ; own bracket result +40 pts (+0.51 R, $+4808). MFE +0.73 R, MAE +0.00 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  15:00:04  price 19349.07 (open +0.01 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  15:01:03  price 19374.08 (open +0.33 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  15:03:03  price 19381.23 (open +0.42 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  15:04:18  price 19384.80 (open +0.46 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  15:05:18  price 19380.04 (open +0.41 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  15:06:33  price 19389.57 (open +0.52 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  15:06:33  price 19389.57 (open +0.52 R of the book stop): took a part [OB1: OB1]
  15:06:48  price 19396.72 (open +0.61 R of the book stop): state change DEFENDING>FREE [NB: NB]
  15:06:48  price 19396.72 (open +0.61 R of the book stop): moved the stop closer [NB: NB]
  15:07:03  price 19405.06 (open +0.72 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  15:07:03  price 19405.06 (open +0.72 R of the book stop): state change FREE>OUT [OB2: OB2]
  15:07:03  price 19405.06 (open +0.72 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 19397.58

**NP-YM (NY PM MF3)** 2025-04-07 14:30:03 ET, LONG 6 lots at 17608.92, safety stop 17489.79 (1.5 x own stop 79.4167 pts). Result managed +45 pts/lot (+0.57 R, $+5408) ; own bracket result +40 pts (+0.50 R, $+4803). MFE +0.67 R, MAE -0.16 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  14:30:04  price 17612.49 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:31:03  price 17601.77 (open -0.09 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:32:03  price 17660.14 (open +0.65 R of the book stop): state change PROBE>OUT [DV: DV]
  14:32:03  price 17660.14 (open +0.65 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 17654.04

**NP-ZN (NY PM MF2)** 2025-04-11 12:36:22 ET, SHORT 6 lots at 18705.21, safety stop 18884.02 (1.5 x own stop 119.208 pts). Result managed -34 pts/lot (-0.29 R, $-4107) ; own bracket result -115 pts (-0.96 R, $-13792). MFE +0.05 R, MAE -0.35 R, 2 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N
  12:36:23  price 18708.78 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:37:22  price 18728.45 (open -0.20 R of the book stop): state change desk [DEFEND/ANAANA: DEFEND/ANAANA]
  12:37:22  price 18728.45 (open -0.20 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:37:22  price 18728.45 (open -0.20 R of the book stop): took a part [DF: DF]
  12:38:52  price 18746.34 (open -0.35 R of the book stop): state change desk [ABORT/AAAANA: ABORT/AAAANA]
  12:38:52  price 18746.34 (open -0.35 R of the book stop): state change DEFENDING>OUT [AB: AB]
  12:38:52  price 18746.34 (open -0.35 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 18739.38

**NP-ZN (NY PM MF2)** 2025-05-14 12:13:59 ET, LONG 6 lots at 21386.33, safety stop 21207.52 (1.5 x own stop 119.208 pts). Result managed -46 pts/lot (-0.39 R, $-5517) ; own bracket result +3 pts (+0.02 R, $+343). MFE +0.27 R, MAE -0.59 R, 54 min under water (longest 38 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:A 19m:W 34m:N 63m:A
  12:14:00  price 21386.33 (open +0.00 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  12:14:59  price 21388.12 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:19:01  price 21377.39 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:32:27  price 21397.06 (open +0.09 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:36:12  price 21411.37 (open +0.21 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  12:36:57  price 21406.00 (open +0.17 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  12:38:12  price 21391.70 (open +0.04 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  12:38:27  price 21389.91 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:40:42  price 21370.24 (open -0.14 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:41:12  price 21364.88 (open -0.18 R of the book stop): state change desk [DEFEND/ANAANW: DEFEND/ANAANW]
  12:41:12  price 21364.88 (open -0.18 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:41:12  price 21364.88 (open -0.18 R of the book stop): took a part [DF: DF]
  12:41:57  price 21368.45 (open -0.15 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  12:42:12  price 21377.39 (open -0.08 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:42:27  price 21372.03 (open -0.12 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:42:42  price 21375.60 (open -0.09 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:42:57  price 21373.82 (open -0.11 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:46:13  price 21380.97 (open -0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:48:43  price 21368.45 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:48:58  price 21370.24 (open -0.14 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:49:13  price 21368.45 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:50:44  price 21370.24 (open -0.14 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:52:00  price 21373.82 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:55:00  price 21373.82 (open -0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:57:17  price 21370.24 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:57:47  price 21372.03 (open -0.12 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:58:17  price 21366.66 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:01:18  price 21357.72 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:01:48  price 21357.72 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:02:03  price 21354.15 (open -0.27 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:02:18  price 21357.72 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:02:33  price 21357.72 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:02:48  price 21363.09 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:06:49  price 21348.78 (open -0.32 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  13:07:04  price 21348.78 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:13:36  price 21339.84 (open -0.39 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:14:07  price 21338.05 (open -0.41 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:14:37  price 21341.63 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:16:07  price 21341.63 (open -0.38 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  13:16:37  price 21332.69 (open -0.45 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  exit: ExAlgoAll_AB at 21340.42

**NP-ZN (NY PM MF2)** 2025-05-16 13:06:58 ET, SHORT 6 lots at 21439.12, safety stop 21617.94 (1.5 x own stop 119.208 pts). Result managed -39 pts/lot (-0.33 R, $-4692) ; own bracket result -62 pts (-0.52 R, $-7477). MFE +0.09 R, MAE -0.56 R, 154 min under water (longest 98 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 4m:W 5m:N 20m:A 61m:N 117m:A
  13:06:59  price 21439.12 (open -0.00 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  13:07:58  price 21433.76 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:13:18  price 21442.70 (open -0.03 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  13:13:33  price 21446.28 (open -0.06 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:13:48  price 21448.07 (open -0.08 R of the book stop): state change desk [NORMAL/AANNNW: NORMAL/AANNNW]
  13:14:03  price 21448.07 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:16:19  price 21457.01 (open -0.15 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:19:07  price 21458.79 (open -0.17 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:20:22  price 21460.58 (open -0.18 R of the book stop): state change desk [DEFEND/ANAANW: DEFEND/ANAANW]
  13:20:22  price 21460.58 (open -0.18 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:20:22  price 21460.58 (open -0.18 R of the book stop): took a part [DF: DF]
  13:20:52  price 21458.79 (open -0.17 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:21:07  price 21458.79 (open -0.17 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:23:07  price 21453.43 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:29:42  price 21458.79 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:29:57  price 21457.01 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:30:12  price 21458.79 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:31:42  price 21465.95 (open -0.22 R of the book stop): state change desk [DEFEND/AAANNW: DEFEND/AAANNW]
  13:31:57  price 21464.16 (open -0.21 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:32:27  price 21469.52 (open -0.26 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:32:58  price 21465.95 (open -0.22 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:33:29  price 21467.74 (open -0.24 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:33:45  price 21467.74 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:34:00  price 21471.31 (open -0.27 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:34:15  price 21469.52 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  13:34:45  price 21471.31 (open -0.27 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:36:00  price 21474.89 (open -0.30 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:36:15  price 21473.10 (open -0.29 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:36:30  price 21469.52 (open -0.26 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:37:00  price 21467.74 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:38:00  price 21467.74 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:42:01  price 21455.22 (open -0.14 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:44:02  price 21455.22 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:47:03  price 21453.43 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:50:35  price 21448.07 (open -0.08 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:51:35  price 21448.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:52:20  price 21442.70 (open -0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:52:50  price 21448.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:53:05  price 21446.28 (open -0.06 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  13:54:06  price 21444.49 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  exit: ExAlgoAll_AB at 21478.17

**NP-YM (NY PM MF3)** 2025-05-29 12:00:03 ET, LONG 6 lots at 21344.71, safety stop 21225.58 (1.5 x own stop 79.4167 pts). Result managed -7 pts/lot (-0.09 R, $-862) ; own bracket result +40 pts (+0.50 R, $+4798). MFE +0.29 R, MAE -0.60 R, 4 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  12:00:04  price 21348.28 (open +0.04 R of the book stop): state change desk [ABORT/AAAANN: ABORT/AAAANN]
  12:01:03  price 21317.31 (open -0.35 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  12:01:03  price 21317.31 (open -0.35 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:01:03  price 21317.31 (open -0.35 R of the book stop): took a part [DF: DF]
  12:01:18  price 21336.37 (open -0.11 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  12:03:03  price 21328.03 (open -0.21 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  12:03:18  price 21329.22 (open -0.20 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:05:03  price 21351.86 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:08:03  price 21367.34 (open +0.29 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  12:08:03  price 21367.34 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  12:08:03  price 21367.34 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  exit: Stop at 21337.58

**NP-YM (NY PM MF3)** 2025-05-29 14:00:03 ET, LONG 6 lots at 21376.12, safety stop 21257.00 (1.5 x own stop 79.4167 pts). Result managed +22 pts/lot (+0.27 R, $+2588) ; own bracket result +40 pts (+0.51 R, $+4808). MFE +0.37 R, MAE -0.08 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  14:00:04  price 21374.93 (open -0.01 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  14:01:03  price 21386.85 (open +0.14 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:01:33  price 21382.08 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:05:48  price 21396.38 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  14:05:48  price 21396.38 (open +0.26 R of the book stop): took a part [OB1: OB1]
  14:06:49  price 21396.38 (open +0.26 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:09:05  price 21396.38 (open +0.26 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:10:05  price 21393.99 (open +0.22 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  14:11:06  price 21390.42 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:13:23  price 21382.08 (open +0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:13:38  price 21388.04 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:14:23  price 21401.14 (open +0.32 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  14:14:23  price 21401.14 (open +0.32 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21397.75

**NP-ZN (NY PM MF2)** 2025-06-05 14:17:11 ET, LONG 6 lots at 21624.50, safety stop 21445.69 (1.5 x own stop 119.208 pts). Result managed +30 pts/lot (+0.25 R, $+3608) ; own bracket result -119 pts (-1.00 R, $-14327). MFE +0.49 R, MAE -0.02 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  14:17:12  price 21620.92 (open -0.03 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:18:11  price 21633.44 (open +0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:18:11  price 21633.44 (open +0.08 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:18:11  price 21633.44 (open +0.08 R of the book stop): took a part [DF: DF]
  14:18:41  price 21642.38 (open +0.15 R of the book stop): state change desk [NORMAL/ANWNNA: NORMAL/ANWNNA]
  14:18:56  price 21645.96 (open +0.18 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:19:11  price 21644.17 (open +0.17 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  14:19:26  price 21662.05 (open +0.32 R of the book stop): state change desk [NORMAL/ANWAWA: NORMAL/ANWAWA]
  14:19:26  price 21662.05 (open +0.32 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:19:26  price 21662.05 (open +0.32 R of the book stop): moved the stop closer [OB1: OB1]
  14:19:41  price 21667.42 (open +0.36 R of the book stop): state change desk [NORMAL/NNWAWA: NORMAL/NNWAWA]
  14:20:41  price 21667.42 (open +0.36 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  14:21:11  price 21674.57 (open +0.42 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  14:21:11  price 21674.57 (open +0.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 21654.62

**NP-YM (NY PM MF3)** 2025-06-13 12:00:03 ET, SHORT 6 lots at 21834.58, safety stop 21953.71 (1.5 x own stop 79.4167 pts). Result managed -7 pts/lot (-0.09 R, $-842) ; own bracket result +40 pts (+0.50 R, $+4803). MFE +0.24 R, MAE -0.19 R, 4 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  12:00:04  price 21834.58 (open +0.00 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  12:01:03  price 21825.05 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:08:05  price 21833.39 (open +0.01 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  12:08:05  price 21833.39 (open +0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:08:05  price 21833.39 (open +0.01 R of the book stop): took a part [DF: DF]
  12:14:08  price 21848.88 (open -0.18 R of the book stop): state change desk [ABORT/AANNNA: ABORT/AANNNA]
  12:14:08  price 21848.88 (open -0.18 R of the book stop): state change DEFENDING>OUT [AB: AB]
  12:14:08  price 21848.88 (open -0.18 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 21841.54

**NP-YM (NY PM MF3)** 2025-07-08 12:30:03 ET, LONG 6 lots at 22949.83, safety stop 22830.71 (1.5 x own stop 79.4167 pts). Result managed -61 pts/lot (-0.77 R, $-7342) ; own bracket result -57 pts (-0.71 R, $-6792). MFE +0.04 R, MAE -0.86 R, 48 min under water (longest 46 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  12:30:04  price 22949.83 (open +0.00 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  12:31:03  price 22946.26 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:32:18  price 22946.26 (open -0.04 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  12:33:03  price 22931.96 (open -0.22 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:33:33  price 22922.43 (open -0.35 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  12:33:48  price 22924.82 (open -0.32 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:36:03  price 22892.65 (open -0.72 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  12:36:03  price 22892.65 (open -0.72 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:36:03  price 22892.65 (open -0.72 R of the book stop): took a part [DF: DF]
  12:38:33  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:40:03  price 22914.10 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:40:33  price 22911.71 (open -0.48 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:41:33  price 22916.48 (open -0.42 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:43:19  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:44:04  price 22924.82 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:45:34  price 22914.10 (open -0.45 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:45:49  price 22914.10 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:48:05  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:49:21  price 22923.63 (open -0.33 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:49:36  price 22927.20 (open -0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:49:51  price 22921.24 (open -0.36 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:50:06  price 22924.82 (open -0.32 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  12:50:21  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:50:51  price 22920.05 (open -0.38 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:51:06  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:51:36  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  12:51:51  price 22926.01 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:52:06  price 22923.63 (open -0.33 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  12:53:06  price 22917.67 (open -0.41 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  12:54:06  price 22916.48 (open -0.42 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:54:51  price 22923.63 (open -0.33 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  12:55:36  price 22921.24 (open -0.36 R of the book stop): state change desk [NORMAL/NAANNW: NORMAL/NAANNW]
  12:55:51  price 22924.82 (open -0.32 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  12:56:06  price 22918.86 (open -0.39 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:57:51  price 22923.63 (open -0.33 R of the book stop): state change desk [NORMAL/WNANNW: NORMAL/WNANNW]
  12:58:21  price 22921.24 (open -0.36 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:00:21  price 22912.90 (open -0.46 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:00:36  price 22914.10 (open -0.45 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:00:51  price 22910.52 (open -0.49 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:01:06  price 22915.29 (open -0.43 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  exit: ExAlgoAll_AB at 22888.71

**NP-ZN (NY PM MF2)** 2025-07-08 12:48:24 ET, SHORT 6 lots at 22925.42, safety stop 23104.23 (1.5 x own stop 119.208 pts). Result managed +24 pts/lot (+0.20 R, $+2908) ; own bracket: not taken (slot effect). MFE +0.42 R, MAE -0.06 R, 2 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 6m:W 16m:N 18m:W 25m:N 29m:W
  12:48:25  price 22927.20 (open -0.01 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:49:25  price 22923.63 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:49:55  price 22920.05 (open +0.04 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:50:10  price 22925.42 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:52:10  price 22925.42 (open -0.00 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:52:40  price 22921.84 (open +0.03 R of the book stop): state change desk [NORMAL/NNWNAN: NORMAL/NNWNAN]
  12:53:41  price 22916.48 (open +0.08 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:54:11  price 22918.26 (open +0.06 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:57:56  price 22923.63 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:58:26  price 22916.48 (open +0.08 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:58:41  price 22918.26 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:59:41  price 22912.90 (open +0.11 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  12:59:56  price 22916.48 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:00:11  price 22914.69 (open +0.09 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  13:00:41  price 22914.69 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:02:56  price 22912.90 (open +0.11 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:03:11  price 22916.48 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:06:56  price 22903.96 (open +0.18 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:07:42  price 22909.32 (open +0.14 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:08:12  price 22902.17 (open +0.20 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:08:27  price 22903.96 (open +0.18 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:10:12  price 22903.96 (open +0.18 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:11:12  price 22916.48 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:16:47  price 22900.38 (open +0.21 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:17:02  price 22902.17 (open +0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:17:17  price 22896.81 (open +0.24 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:17:32  price 22893.23 (open +0.27 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  13:17:32  price 22893.23 (open +0.27 R of the book stop): took a part [OB1: OB1]
  13:18:02  price 22886.08 (open +0.33 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  13:20:02  price 22895.02 (open +0.26 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:22:02  price 22893.23 (open +0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:22:17  price 22886.08 (open +0.33 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  13:23:17  price 22893.23 (open +0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:23:32  price 22900.38 (open +0.21 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:23:47  price 22907.54 (open +0.15 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  13:23:47  price 22907.54 (open +0.15 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 22901.12

**NP-ZN (NY PM MF2)** 2025-08-12 13:34:48 ET, SHORT 6 lots at 23906.12, safety stop 24084.94 (1.5 x own stop 119.208 pts). Result managed -4 pts/lot (-0.04 R, $-547) ; own bracket result -32 pts (-0.27 R, $-3902). MFE +0.08 R, MAE -0.22 R, 88 min under water (longest 60 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 18m:A 61m:N
  13:34:49  price 23906.12 (open -0.00 R of the book stop): state change desk [ABORT/AAANNN: ABORT/AAANNN]
  13:35:48  price 23904.34 (open +0.01 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:36:48  price 23900.76 (open +0.04 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  13:37:03  price 23902.55 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:38:03  price 23904.34 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:43:08  price 23906.12 (open -0.00 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:43:08  price 23906.12 (open -0.00 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:43:08  price 23906.12 (open -0.00 R of the book stop): took a part [DF: DF]
  13:43:38  price 23904.34 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:46:08  price 23904.34 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:46:23  price 23907.91 (open -0.01 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:48:08  price 23907.91 (open -0.01 R of the book stop): state change desk [NORMAL/ANWNNN: NORMAL/ANWNNN]
  13:48:23  price 23909.70 (open -0.03 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:50:08  price 23911.49 (open -0.04 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:51:08  price 23913.28 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:54:12  price 23915.07 (open -0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:54:27  price 23913.28 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:57:46  price 23915.07 (open -0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:58:01  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:00:02  price 23915.07 (open -0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:00:32  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:00:47  price 23916.85 (open -0.09 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:02:47  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:03:32  price 23915.07 (open -0.08 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:04:03  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:07:52  price 23916.85 (open -0.09 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  14:08:22  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:08:37  price 23915.07 (open -0.08 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  14:10:25  price 23911.49 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:12:58  price 23916.85 (open -0.09 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:16:00  price 23916.85 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:18:03  price 23918.64 (open -0.11 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:19:18  price 23922.22 (open -0.14 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  14:22:33  price 23918.64 (open -0.11 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  14:23:18  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:30:09  price 23922.22 (open -0.14 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:30:25  price 23916.85 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:31:55  price 23909.70 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  14:32:10  price 23915.07 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:40:46  price 23911.49 (open -0.04 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  exit: ExAlgoAll_AB at 23910.62

**NP-YM (NY PM MF3)** 2025-10-01 12:00:03 ET, SHORT 6 lots at 24933.38, safety stop 25052.50 (1.5 x own stop 79.4167 pts). Result managed -40 pts/lot (-0.51 R, $-4852) ; own bracket result -79 pts (-0.99 R, $-9472). MFE +0.07 R, MAE -0.61 R, 70 min under water (longest 30 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 61m:N 77m:A
  12:01:03  price 24938.14 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNAN: NORMAL/NNNNAN]
  12:01:33  price 24935.76 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:01:48  price 24938.14 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNAN: NORMAL/NNNNAN]
  12:03:48  price 24935.76 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:04:03  price 24932.18 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNAN: NORMAL/NNNNAN]
  12:04:18  price 24934.57 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:07:04  price 24941.71 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:09:49  price 24940.52 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:11:05  price 24945.29 (open -0.15 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:11:20  price 24942.90 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:11:35  price 24945.29 (open -0.15 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:11:50  price 24945.29 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:17:08  price 24948.86 (open -0.20 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:17:38  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:18:38  price 24946.48 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:18:53  price 24946.48 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:19:08  price 24940.52 (open -0.09 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:19:38  price 24938.14 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:20:08  price 24936.95 (open -0.04 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:24:08  price 24930.99 (open +0.03 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  12:25:38  price 24939.33 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:25:53  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:26:08  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/ANNWNW: NORMAL/ANNWNW]
  12:26:53  price 24945.29 (open -0.15 R of the book stop): state change desk [PRESS/NNNWNW: PRESS/NNNWNW]
  12:27:08  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:27:23  price 24942.90 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:28:10  price 24942.90 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:29:10  price 24942.90 (open -0.12 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:29:25  price 24942.90 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:30:40  price 24948.86 (open -0.20 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:31:10  price 24948.86 (open -0.20 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:32:10  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:32:25  price 24947.67 (open -0.18 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:32:56  price 24944.10 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:34:41  price 24950.05 (open -0.21 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:35:41  price 24947.67 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:36:42  price 24950.05 (open -0.21 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:36:57  price 24950.05 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:37:27  price 24947.67 (open -0.18 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  12:37:42  price 24947.67 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  exit: ExAlgoAll_AB at 24973.75

**NP-YM (NY PM MF3)** 2025-10-07 12:00:03 ET, SHORT 6 lots at 25029.04, safety stop 25148.17 (1.5 x own stop 79.4167 pts). Result managed +14 pts/lot (+0.18 R, $+1688) ; own bracket result -20 pts (-0.25 R, $-2427). MFE +0.39 R, MAE -0.79 R, 40 min under water (longest 29 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 8m:N 15m:W 17m:N 20m:W 35m:A
  12:00:04  price 25029.04 (open +0.00 R of the book stop): state change desk [PRESS/WNWNNW: PRESS/WNWNNW]
  12:01:03  price 25052.87 (open -0.30 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  12:02:48  price 25040.95 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:03:03  price 25046.91 (open -0.22 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:05:03  price 25054.06 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:06:03  price 25046.91 (open -0.22 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:06:48  price 25030.23 (open -0.01 R of the book stop): state change desk [NORMAL/WNNANW: NORMAL/WNNANW]
  12:07:03  price 25025.47 (open +0.04 R of the book stop): state change desk [PRESS/WNNAWW: PRESS/WNNAWW]
  12:07:48  price 25019.51 (open +0.12 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:08:03  price 25026.66 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:08:48  price 25025.47 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:10:03  price 25031.42 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:10:18  price 25025.47 (open +0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:10:33  price 25031.42 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:11:18  price 25020.70 (open +0.11 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:11:48  price 25027.85 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:14:03  price 25017.13 (open +0.15 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:19:33  price 25005.22 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  12:19:33  price 25005.22 (open +0.30 R of the book stop): took a part [OB1: OB1]
  12:24:18  price 25030.23 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:24:33  price 25027.85 (open +0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  12:25:18  price 25035.00 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:28:03  price 25046.91 (open -0.22 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  12:29:03  price 25039.76 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:30:03  price 25040.95 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  12:31:03  price 25049.29 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  12:34:03  price 25065.97 (open -0.46 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  12:35:18  price 25069.54 (open -0.51 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:36:03  price 25069.54 (open -0.51 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  12:37:33  price 25083.84 (open -0.69 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  12:38:03  price 25086.22 (open -0.72 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  12:38:33  price 25088.60 (open -0.75 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:47:04  price 25062.40 (open -0.42 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:52:04  price 25035.00 (open -0.08 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  12:53:04  price 25040.95 (open -0.15 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:59:49  price 25024.28 (open +0.06 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  12:59:49  price 25024.28 (open +0.06 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25014.92

**NP-ZN (NY PM MF2)** 2025-10-10 13:52:55 ET, SHORT 6 lots at 24663.62, safety stop 24842.44 (1.5 x own stop 119.208 pts). Result managed +28 pts/lot (+0.24 R, $+3363) ; own bracket result +120 pts (+1.01 R, $+14378). MFE +0.41 R, MAE -0.44 R, 27 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 20m:N 53m:W
  13:52:56  price 24665.41 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:53:55  price 24668.99 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:10:10  price 24668.99 (open -0.04 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:11:10  price 24676.14 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:11:25  price 24660.05 (open +0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:13:10  price 24660.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:15:25  price 24701.18 (open -0.32 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  14:15:40  price 24694.02 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:16:10  price 24694.02 (open -0.26 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  14:16:25  price 24701.18 (open -0.32 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  14:17:10  price 24704.75 (open -0.35 R of the book stop): state change desk [NORMAL/ANNANW: NORMAL/ANNANW]
  14:17:25  price 24695.81 (open -0.27 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:18:10  price 24663.62 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:18:25  price 24668.99 (open -0.04 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  14:18:55  price 24654.68 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:19:10  price 24665.41 (open -0.01 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:19:40  price 24672.57 (open -0.08 R of the book stop): state change desk [NORMAL/NNNAWW: NORMAL/NNNAWW]
  14:19:55  price 24667.20 (open -0.03 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:20:10  price 24686.87 (open -0.20 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  14:20:25  price 24688.66 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:20:40  price 24688.66 (open -0.21 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  14:20:55  price 24706.54 (open -0.36 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:21:10  price 24713.69 (open -0.42 R of the book stop): state change desk [NORMAL/NANNWW: NORMAL/NANNWW]
  14:21:25  price 24704.75 (open -0.35 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  14:22:55  price 24717.27 (open -0.45 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:25:10  price 24706.54 (open -0.36 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:26:11  price 24701.18 (open -0.32 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  14:28:11  price 24697.60 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:29:11  price 24681.51 (open -0.15 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:32:11  price 24665.41 (open -0.01 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  14:33:26  price 24670.78 (open -0.06 R of the book stop): state change desk [PRESS/WNNWNN: PRESS/WNNWNN]
  14:34:11  price 24667.20 (open -0.03 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  14:35:11  price 24654.68 (open +0.08 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:36:11  price 24651.11 (open +0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:37:11  price 24649.32 (open +0.12 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:46:58  price 24649.32 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:46:58  price 24649.32 (open +0.12 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  14:46:58  price 24649.32 (open +0.12 R of the book stop): took a part [OB1: OB1]
  14:47:13  price 24640.38 (open +0.20 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:48:13  price 24620.71 (open +0.36 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  exit: ExAlgoAll_OB2 at 24635.54

**NP-YM (NY PM MF3)** 2025-10-28 14:30:03 ET, SHORT 6 lots at 26180.46, safety stop 26299.58 (1.5 x own stop 79.4167 pts). Result managed -11 pts/lot (-0.14 R, $-1377) ; own bracket: not taken (slot effect). MFE +0.05 R, MAE -0.21 R, 31 min under water (longest 14 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  14:30:04  price 26181.65 (open -0.01 R of the book stop): state change desk [ABORT/AANNNA: ABORT/AANNNA]
  14:31:03  price 26184.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:31:18  price 26182.84 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  14:31:33  price 26181.65 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:40:05  price 26180.46 (open -0.00 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  14:41:05  price 26180.46 (open +0.00 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:41:20  price 26178.08 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:48:20  price 26187.61 (open -0.09 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:48:20  price 26187.61 (open -0.09 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:48:20  price 26187.61 (open -0.09 R of the book stop): took a part [DF: DF]
  14:48:35  price 26184.03 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:50:37  price 26191.18 (open -0.14 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:52:08  price 26191.18 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:55:08  price 26185.22 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:59:08  price 26193.56 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:00:23  price 26187.61 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:05:39  price 26195.94 (open -0.20 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  15:05:39  price 26195.94 (open -0.20 R of the book stop): state change DEFENDING>OUT [AB: AB]
  15:05:39  price 26195.94 (open -0.20 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 26191.88

**NP-ZN (NY PM MF2)** 2025-12-09 14:11:27 ET, LONG 6 lots at 25702.75, safety stop 25523.94 (1.5 x own stop 119.208 pts). Result managed -4 pts/lot (-0.03 R, $-472) ; own bracket: not taken (slot effect). MFE +0.12 R, MAE -0.17 R, 45 min under water (longest 15 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 8m:W 11m:N 30m:A 61m:N
  14:11:28  price 25702.75 (open +0.00 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  14:12:27  price 25700.96 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  14:12:58  price 25700.96 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:19:00  price 25715.27 (open +0.11 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  14:19:30  price 25709.90 (open +0.06 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:19:45  price 25711.69 (open +0.08 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  14:20:00  price 25711.69 (open +0.08 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:20:15  price 25715.27 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:20:46  price 25715.27 (open +0.11 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:21:47  price 25713.48 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:22:02  price 25713.48 (open +0.09 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:22:17  price 25709.90 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:28:07  price 25709.90 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:32:12  price 25715.27 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:33:12  price 25713.48 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:37:01  price 25702.75 (open -0.00 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  14:37:16  price 25706.33 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:38:01  price 25702.75 (open +0.00 R of the book stop): state change desk [NORMAL/ANNNNW: NORMAL/ANNNNW]
  14:38:16  price 25702.75 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:39:04  price 25704.54 (open +0.01 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:41:04  price 25700.96 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:42:05  price 25699.17 (open -0.03 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:43:05  price 25697.39 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:44:21  price 25693.81 (open -0.08 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:46:06  price 25690.23 (open -0.11 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  14:46:21  price 25695.60 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  14:46:36  price 25695.60 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:47:07  price 25695.60 (open -0.06 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  14:47:07  price 25695.60 (open -0.06 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:47:07  price 25695.60 (open -0.06 R of the book stop): took a part [DF: DF]
  14:49:09  price 25695.60 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:50:24  price 25702.75 (open +0.00 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  14:50:54  price 25700.96 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:51:09  price 25700.96 (open -0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  14:51:24  price 25702.75 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:52:24  price 25704.54 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  14:53:09  price 25699.17 (open -0.03 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:53:54  price 25704.54 (open +0.01 R of the book stop): state change desk [NORMAL/WNWNNA: NORMAL/WNWNNA]
  14:54:09  price 25702.75 (open +0.00 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:55:10  price 25704.54 (open +0.01 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  exit: ExAlgoAll_CL at 25698.88

**NP-ZN (NY PM MF2)** 2025-12-10 14:36:59 ET, SHORT 6 lots at 25718.08, safety stop 25896.90 (1.5 x own stop 119.208 pts). Result managed +57 pts/lot (+0.48 R, $+6878) ; own bracket: not taken (slot effect). MFE +0.89 R, MAE -0.29 R, 3 min under water (longest 2 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  14:37:00  price 25718.08 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:37:59  price 25705.57 (open +0.11 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  14:38:14  price 25741.33 (open -0.20 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  14:38:59  price 25721.66 (open -0.03 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  14:39:14  price 25735.96 (open -0.15 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:39:44  price 25744.91 (open -0.22 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:40:14  price 25712.72 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:40:44  price 25687.69 (open +0.26 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  14:40:44  price 25687.69 (open +0.26 R of the book stop): took a part [OB1: OB1]
  14:40:59  price 25662.65 (open +0.46 R of the book stop): state change desk [NORMAL/NNWNAN: NORMAL/NNWNAN]
  14:41:14  price 25659.08 (open +0.49 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:41:29  price 25648.35 (open +0.58 R of the book stop): state change desk [NORMAL/NNWNAN: NORMAL/NNWNAN]
  14:41:29  price 25648.35 (open +0.58 R of the book stop): state change DEFENDING>FREE [NB: NB]
  14:41:29  price 25648.35 (open +0.58 R of the book stop): moved the stop closer [NB: NB]
  14:42:14  price 25632.25 (open +0.72 R of the book stop): moved the stop closer [NB: NB]
  14:42:29  price 25630.47 (open +0.73 R of the book stop): state change FREE>OUT [OB2: OB2]
  14:42:29  price 25630.47 (open +0.73 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 25660.71

**NP-YM (NY PM MF3)** 2026-01-07 14:00:03 ET, LONG 6 lots at 25954.38, safety stop 25835.25 (1.5 x own stop 79.4167 pts). Result managed -23 pts/lot (-0.29 R, $-2747) ; own bracket result -80 pts (-1.00 R, $-9562). MFE +0.02 R, MAE -0.52 R, 10 min under water (longest 6 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  14:00:04  price 25954.38 (open -0.00 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  14:01:03  price 25953.18 (open -0.01 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:02:18  price 25946.04 (open -0.11 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:02:18  price 25946.04 (open -0.11 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:02:18  price 25946.04 (open -0.11 R of the book stop): took a part [DF: DF]
  14:02:33  price 25947.23 (open -0.09 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:03:03  price 25953.18 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:08:20  price 25941.27 (open -0.17 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:08:35  price 25944.85 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:09:20  price 25936.51 (open -0.22 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:10:35  price 25917.45 (open -0.46 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  14:10:35  price 25917.45 (open -0.46 R of the book stop): state change DEFENDING>OUT [AB: AB]
  14:10:35  price 25917.45 (open -0.46 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 25931.54

**NP-ZN (NY PM MF2)** 2026-01-30 13:17:57 ET, LONG 6 lots at 25649.17, safety stop 25470.35 (1.5 x own stop 119.208 pts). Result managed -33 pts/lot (-0.28 R, $-4012) ; own bracket: not taken (slot effect). MFE +0.26 R, MAE -0.69 R, 13 min under water (longest 9 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  13:17:58  price 25650.95 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  13:18:57  price 25625.92 (open -0.20 R of the book stop): state change desk [NORMAL/ANANNW: NORMAL/ANANNW]
  13:19:12  price 25624.13 (open -0.21 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  13:19:12  price 25624.13 (open -0.21 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:19:12  price 25624.13 (open -0.21 R of the book stop): took a part [DF: DF]
  13:21:12  price 25591.95 (open -0.48 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  13:21:27  price 25590.16 (open -0.49 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  13:23:57  price 25599.10 (open -0.42 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  13:24:27  price 25609.83 (open -0.33 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:26:12  price 25633.07 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:28:12  price 25663.47 (open +0.12 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:29:27  price 25672.41 (open +0.20 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  13:30:12  price 25649.17 (open -0.00 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:32:57  price 25629.50 (open -0.17 R of the book stop): state change desk [NORMAL/ANNWNN: NORMAL/ANNWNN]
  13:33:12  price 25627.71 (open -0.18 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:33:57  price 25618.77 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:34:12  price 25608.04 (open -0.35 R of the book stop): state change desk [ABORT/AANNNN: ABORT/AANNNN]
  13:34:12  price 25608.04 (open -0.35 R of the book stop): state change DEFENDING>OUT [AB: AB]
  13:34:12  price 25608.04 (open -0.35 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 25615.79

**NP-ZN (NY PM MF2)** 2026-02-16 12:02:54 ET, LONG 6 lots at 24737.71, safety stop 24558.90 (1.5 x own stop 119.208 pts). Result managed +10 pts/lot (+0.09 R, $+1213) ; own bracket result +5 pts (+0.04 R, $+598). MFE +0.10 R, MAE -0.20 R, 25 min under water (longest 22 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  12:03:00  price 24737.71 (open -0.00 R of the book stop): state change desk [NORMAL/WANNNN: NORMAL/WANNNN]
  12:03:56  price 24730.56 (open -0.06 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  12:07:37  price 24718.04 (open -0.17 R of the book stop): state change desk [NORMAL/ANN-N-: NORMAL/ANN-N-]
  12:08:22  price 24719.83 (open -0.15 R of the book stop): state change desk [NORMAL/NNN-N-: NORMAL/NNN-N-]
  12:30:05  price 24748.44 (open +0.09 R of the book stop): state change PROBE>OUT [CL: CL]
  12:30:05  price 24748.44 (open +0.09 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 24747.88

**NP-ZN (NY PM MF2)** 2026-02-18 15:03:43 ET, LONG 6 lots at 24914.67, safety stop 24735.85 (1.5 x own stop 119.208 pts). Result managed -6 pts/lot (-0.05 R, $-732) ; own bracket: not taken (slot effect). MFE +0.09 R, MAE -0.50 R, 31 min under water (longest 31 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:A
  15:03:44  price 24916.45 (open +0.01 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  15:04:43  price 24905.73 (open -0.08 R of the book stop): state change desk [NORMAL/NNNWAN: NORMAL/NNNWAN]
  15:04:58  price 24902.15 (open -0.11 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:06:28  price 24896.79 (open -0.15 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  15:07:28  price 24889.63 (open -0.21 R of the book stop): state change desk [NORMAL/ANAWNN: NORMAL/ANAWNN]
  15:07:58  price 24905.73 (open -0.08 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:08:13  price 24902.15 (open -0.11 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:08:43  price 24893.21 (open -0.18 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:08:43  price 24893.21 (open -0.18 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  15:08:43  price 24893.21 (open -0.18 R of the book stop): took a part [DF: DF]
  15:09:43  price 24889.63 (open -0.21 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:10:13  price 24884.27 (open -0.26 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:10:43  price 24889.63 (open -0.21 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:11:43  price 24873.54 (open -0.35 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:12:28  price 24878.90 (open -0.30 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:12:43  price 24869.96 (open -0.38 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:14:13  price 24878.90 (open -0.30 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:15:13  price 24877.12 (open -0.32 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  15:15:28  price 24868.18 (open -0.39 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  15:16:13  price 24859.23 (open -0.46 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:17:43  price 24871.75 (open -0.36 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:18:43  price 24886.06 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:19:13  price 24886.06 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:19:28  price 24880.69 (open -0.29 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:19:43  price 24886.06 (open -0.24 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:19:58  price 24877.12 (open -0.32 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:20:13  price 24871.75 (open -0.36 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:23:13  price 24871.75 (open -0.36 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:24:13  price 24877.12 (open -0.32 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  15:25:13  price 24882.48 (open -0.27 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:25:43  price 24889.63 (open -0.21 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:25:58  price 24880.69 (open -0.29 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:26:58  price 24887.84 (open -0.22 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:27:13  price 24889.63 (open -0.21 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:27:28  price 24886.06 (open -0.24 R of the book stop): state change desk [NORMAL/WNANNN: NORMAL/WNANNN]
  15:27:43  price 24884.27 (open -0.26 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:28:44  price 24882.48 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:28:59  price 24877.12 (open -0.32 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:29:14  price 24884.27 (open -0.26 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:29:59  price 24877.12 (open -0.32 R of the book stop): state change desk [NORMAL/NNAWNN: NORMAL/NNAWNN]
  exit: ExAlgoAll_CL at 24908.62

**NP-ZN (NY PM MF2)** 2026-03-02 15:21:08 ET, LONG 6 lots at 24990.58, safety stop 24811.77 (1.5 x own stop 119.208 pts). Result managed +2 pts/lot (+0.01 R, $+173) ; own bracket: not taken (slot effect). MFE +0.11 R, MAE -0.25 R, 10 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 10m:N
  15:21:09  price 24994.16 (open +0.03 R of the book stop): state change desk [ABORT/AAAANN: ABORT/AAAANN]
  15:22:08  price 24987.01 (open -0.03 R of the book stop): state change desk [PRESS/NNNWWN: PRESS/NNNWWN]
  15:22:53  price 24999.52 (open +0.08 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:23:53  price 24990.58 (open -0.00 R of the book stop): state change desk [PRESS/NNNWWN: PRESS/NNNWWN]
  15:24:08  price 24995.95 (open +0.04 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  15:24:38  price 24992.37 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:25:08  price 24978.07 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  15:25:23  price 24985.22 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:26:08  price 24983.43 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  15:26:23  price 24981.64 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:26:38  price 24974.49 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  15:27:08  price 24965.55 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:32:54  price 24994.16 (open +0.03 R of the book stop): state change PROBE>OUT [CL: CL]
  15:32:54  price 24994.16 (open +0.03 R of the book stop): closed everything [CL: CL]
  exit: ExAlgoAll_CL at 24992.08

**NP-ZN (NY PM MF2)** 2026-04-29 14:17:00 ET, LONG 6 lots at 27217.12, safety stop 27038.31 (1.5 x own stop 119.208 pts). Result managed +15 pts/lot (+0.13 R, $+1818) ; own bracket: not taken (slot effect). MFE +0.40 R, MAE -0.33 R, 10 min under water (longest 9 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 16m:N
  14:17:01  price 27218.91 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:18:00  price 27226.07 (open +0.08 R of the book stop): state change desk [PRESS/NNWWNN: PRESS/NNWWNN]
  14:18:46  price 27227.85 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:21:01  price 27235.01 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:22:02  price 27227.85 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  14:24:03  price 27227.85 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:25:04  price 27218.91 (open +0.01 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  14:25:19  price 27218.91 (open +0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:26:04  price 27209.97 (open -0.06 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:27:19  price 27215.34 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:28:05  price 27213.55 (open -0.03 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:28:05  price 27213.55 (open -0.03 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:28:05  price 27213.55 (open -0.03 R of the book stop): took a part [DF: DF]
  14:28:35  price 27213.55 (open -0.03 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:28:50  price 27213.55 (open -0.03 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:29:05  price 27209.97 (open -0.06 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:30:05  price 27209.97 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:30:20  price 27202.82 (open -0.12 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:31:05  price 27183.15 (open -0.29 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:31:20  price 27186.73 (open -0.26 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  14:32:20  price 27188.51 (open -0.24 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:33:05  price 27204.61 (open -0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:36:20  price 27251.10 (open +0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:36:20  price 27251.10 (open +0.29 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:36:20  price 27251.10 (open +0.29 R of the book stop): moved the stop closer [OB1: OB1]
  14:36:35  price 27245.74 (open +0.24 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:36:50  price 27251.10 (open +0.29 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:36:50  price 27251.10 (open +0.29 R of the book stop): state change RUNNER>OUT [OB2: OB2]
  14:36:50  price 27251.10 (open +0.29 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 27232.33

**NP-ZN (NY PM MF2)** 2026-05-07 13:34:21 ET, SHORT 6 lots at 28628.62, safety stop 28807.44 (1.5 x own stop 119.208 pts). Result managed -28 pts/lot (-0.24 R, $-3392) ; own bracket result -51 pts (-0.42 R, $-6072). MFE +0.40 R, MAE -0.75 R, 63 min under water (longest 48 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 14m:A 15m:N 17m:W 22m:N 26m:A
  13:34:22  price 28630.41 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:35:21  price 28625.05 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:36:36  price 28655.45 (open -0.22 R of the book stop): state change desk [NORMAL/NAANNW: NORMAL/NAANNW]
  13:36:51  price 28653.66 (open -0.21 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  13:37:36  price 28651.87 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:38:06  price 28671.54 (open -0.36 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  13:38:51  price 28659.02 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:39:06  price 28667.96 (open -0.33 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  13:40:06  price 28664.39 (open -0.30 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:40:21  price 28676.90 (open -0.41 R of the book stop): state change desk [NORMAL/ANANWW: NORMAL/ANANWW]
  13:40:36  price 28676.90 (open -0.41 R of the book stop): state change desk [NORMAL/ANNNWW: NORMAL/ANNNWW]
  13:40:51  price 28673.33 (open -0.38 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:41:06  price 28673.33 (open -0.38 R of the book stop): state change desk [NORMAL/NNNAWW: NORMAL/NNNAWW]
  13:41:21  price 28676.90 (open -0.41 R of the book stop): state change desk [NORMAL/NNAAWW: NORMAL/NNAAWW]
  13:41:36  price 28676.90 (open -0.41 R of the book stop): state change desk [NORMAL/NNNAWW: NORMAL/NNNAWW]
  13:43:06  price 28646.51 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:44:06  price 28653.66 (open -0.21 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:45:06  price 28648.29 (open -0.17 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:45:51  price 28635.78 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:47:21  price 28635.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:49:06  price 28628.62 (open -0.00 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:50:06  price 28625.05 (open +0.03 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  13:50:36  price 28619.68 (open +0.08 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:55:21  price 28635.78 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:56:36  price 28669.75 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  13:56:51  price 28651.87 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:57:06  price 28667.96 (open -0.33 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:57:21  price 28667.96 (open -0.33 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  13:57:51  price 28667.96 (open -0.33 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:59:06  price 28682.27 (open -0.45 R of the book stop): state change desk [NORMAL/ANNAWN: NORMAL/ANNAWN]
  14:00:21  price 28696.57 (open -0.57 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:00:21  price 28696.57 (open -0.57 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:00:21  price 28696.57 (open -0.57 R of the book stop): took a part [DF: DF]
  14:00:51  price 28693.00 (open -0.54 R of the book stop): state change desk [NORMAL/ANNAWN: NORMAL/ANNAWN]
  14:01:36  price 28684.06 (open -0.46 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:01:51  price 28687.63 (open -0.49 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:02:06  price 28689.42 (open -0.51 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:04:06  price 28687.63 (open -0.49 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:07:06  price 28705.51 (open -0.65 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:09:51  price 28669.75 (open -0.35 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  exit: ExAlgoStop_OB1 at 28656.83

**NP-YM (NY PM MF3)** 2026-06-03 13:00:03 ET, SHORT 6 lots at 30605.54, safety stop 30724.67 (1.5 x own stop 79.4167 pts). Result managed +33 pts/lot (+0.41 R, $+3938) ; own bracket result +40 pts (+0.50 R, $+4798). MFE +0.35 R, MAE -0.08 R, 1 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W
  13:00:04  price 30597.20 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:01:03  price 30596.01 (open +0.12 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  13:01:18  price 30597.20 (open +0.11 R of the book stop): state change desk [NORMAL/NNNAWN: NORMAL/NNNAWN]
  13:01:33  price 30588.86 (open +0.21 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  13:02:33  price 30573.38 (open +0.41 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  13:02:33  price 30573.38 (open +0.41 R of the book stop): took a part [OB1: OB1]
  13:03:33  price 30572.19 (open +0.42 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  13:03:33  price 30572.19 (open +0.42 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  13:03:33  price 30572.19 (open +0.42 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30572.67

**NP-YM (NY PM MF3)** 2026-06-09 13:00:03 ET, SHORT 6 lots at 28499.75, safety stop 28618.88 (1.5 x own stop 79.4167 pts). Result managed -119 pts/lot (-1.50 R, $-14337) ; own bracket result -80 pts (-1.00 R, $-9552). MFE +0.39 R, MAE -1.65 R, 4 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:A
  13:00:04  price 28490.22 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:01:03  price 28511.66 (open -0.15 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:02:33  price 28560.50 (open -0.77 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  13:02:48  price 28562.89 (open -0.80 R of the book stop): state change desk [NORMAL/NNNANW: NORMAL/NNNANW]
  13:03:33  price 28587.90 (open -1.11 R of the book stop): state change desk [NORMAL/NNAANW: NORMAL/NNAANW]
  exit: Stop at 28619.17

**NP-ZN (NY PM MF2)** 2026-06-11 15:31:25 ET, LONG 6 lots at 29511.42, safety stop 29332.60 (1.5 x own stop 119.208 pts). Result managed +18 pts/lot (+0.15 R, $+2203) ; own bracket result -50 pts (-0.42 R, $-5952). MFE +0.34 R, MAE -0.15 R, 1 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  15:31:26  price 29502.48 (open -0.08 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  15:32:25  price 29509.63 (open -0.01 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  15:33:10  price 29498.90 (open -0.11 R of the book stop): state change desk [PRESS/WNNWWW: PRESS/WNNWWW]
  15:33:40  price 29500.69 (open -0.09 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  15:34:10  price 29532.87 (open +0.18 R of the book stop): state change desk [PRESS/WNNNNW: PRESS/WNNNNW]
  15:34:10  price 29532.87 (open +0.18 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  15:34:10  price 29532.87 (open +0.18 R of the book stop): took a part [OB1: OB1]
  15:35:10  price 29531.09 (open +0.17 R of the book stop): state change desk [PRESS/WNNWNW: PRESS/WNNWNW]
  15:35:25  price 29525.72 (open +0.12 R of the book stop): state change desk [NORMAL/NANWNW: NORMAL/NANWNW]
  15:35:25  price 29525.72 (open +0.12 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  15:35:25  price 29525.72 (open +0.12 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 29529.83

**NP-YM (NY PM MF3)** 2026-06-12 12:00:03 ET, LONG 6 lots at 29429.42, safety stop 29310.29 (1.5 x own stop 79.4167 pts). Result managed +45 pts/lot (+0.57 R, $+5383) ; own bracket result +40 pts (+0.50 R, $+4803). MFE +0.79 R, MAE -0.15 R, 0 min under water (longest 0 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W
  12:00:04  price 29418.70 (open -0.14 R of the book stop): state change desk [NORMAL/ANWAWN: NORMAL/ANWAWN]
  12:01:03  price 29479.45 (open +0.63 R of the book stop): state change desk [NORMAL/NNWANA: NORMAL/NNWANA]
  12:01:03  price 29479.45 (open +0.63 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  12:01:03  price 29479.45 (open +0.63 R of the book stop): took a part [OB1: OB1]
  12:01:18  price 29467.54 (open +0.48 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:01:18  price 29467.54 (open +0.48 R of the book stop): state change DEFENDING>FREE [NB: NB]
  12:01:18  price 29467.54 (open +0.48 R of the book stop): moved the stop closer [NB: NB]
  12:01:33  price 29479.45 (open +0.63 R of the book stop): state change FREE>OUT [DV: DV]
  12:01:33  price 29479.45 (open +0.63 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29474.33

**NP-YM (NY PM MF3)** 2026-06-15 13:30:03 ET, SHORT 6 lots at 30578.25, safety stop 30697.38 (1.5 x own stop 79.4167 pts). Result managed +22 pts/lot (+0.28 R, $+2628) ; own bracket result +40 pts (+0.50 R, $+4793). MFE +0.34 R, MAE -0.13 R, 6 min under water (longest 1 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:N 3m:W 15m:N 26m:W
  13:30:06  price 30578.25 (open -0.00 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  13:31:03  price 30584.21 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  13:31:18  price 30585.40 (open -0.09 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  13:31:33  price 30583.01 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:32:48  price 30568.72 (open +0.12 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  13:34:21  price 30569.91 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:36:10  price 30580.63 (open -0.03 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:37:14  price 30585.40 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:38:14  price 30579.44 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  13:38:48  price 30578.25 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:45:42  price 30561.57 (open +0.21 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:45:57  price 30566.34 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:49:54  price 30574.68 (open +0.04 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:50:09  price 30569.91 (open +0.11 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:50:40  price 30566.34 (open +0.15 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  13:53:16  price 30572.29 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:53:31  price 30577.06 (open +0.01 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:54:32  price 30571.10 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:55:49  price 30555.62 (open +0.29 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  13:55:49  price 30555.62 (open +0.29 R of the book stop): took a part [OB1: OB1]
  13:59:01  price 30558.00 (open +0.26 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  13:59:01  price 30558.00 (open +0.26 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30556.29

**NP-YM (NY PM MF3)** 2026-06-17 12:00:03 ET, SHORT 6 lots at 30452.96, safety stop 30572.08 (1.5 x own stop 79.4167 pts). Result managed +16 pts/lot (+0.20 R, $+1873) ; own bracket result +40 pts (+0.50 R, $+4788). MFE +0.43 R, MAE -0.20 R, 12 min under water (longest 4 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 2m:N 6m:W 11m:N 12m:W
  12:00:04  price 30456.53 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:01:03  price 30468.44 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  12:11:51  price 30429.13 (open +0.30 R of the book stop): state change PROBE>DEFENDING [OB1: OB1]
  12:11:51  price 30429.13 (open +0.30 R of the book stop): took a part [OB1: OB1]
  12:20:08  price 30455.34 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:20:23  price 30458.91 (open -0.08 R of the book stop): state change desk [DEFEND/NANNNA: DEFEND/NANNNA]
  12:20:38  price 30455.34 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:24:13  price 30455.34 (open -0.03 R of the book stop): state change desk [DEFEND/NNNANA: DEFEND/NNNANA]
  12:25:13  price 30454.15 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:37:15  price 30444.62 (open +0.11 R of the book stop): state change DEFENDING>OUT [OB2: OB2]
  12:37:15  price 30444.62 (open +0.11 R of the book stop): closed everything [OB2: OB2]
  exit: ExAlgoAll_OB2 at 30437.29

**NP-ZN (NY PM MF2)** 2026-06-17 15:27:33 ET, LONG 6 lots at 30185.25, safety stop 30006.44 (1.5 x own stop 119.208 pts). Result managed -132 pts/lot (-1.10 R, $-15802) ; own bracket result -120 pts (-1.01 R, $-14467). MFE +0.09 R, MAE -1.45 R, 11 min under water (longest 10 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:W 3m:N 4m:A
  15:27:34  price 30176.31 (open -0.08 R of the book stop): state change desk [PRESS/WNWNNN: PRESS/WNWNNN]
  15:28:33  price 30151.28 (open -0.29 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:30:33  price 30129.82 (open -0.46 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:31:33  price 30153.06 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:32:18  price 30103.00 (open -0.69 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:32:18  price 30103.00 (open -0.69 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  15:32:18  price 30103.00 (open -0.69 R of the book stop): took a part [DF: DF]
  15:32:48  price 30090.48 (open -0.80 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:33:03  price 30069.02 (open -0.98 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:33:18  price 30095.84 (open -0.75 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:33:33  price 30101.21 (open -0.70 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:34:33  price 30077.96 (open -0.90 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:35:03  price 30058.29 (open -1.06 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:35:18  price 30070.81 (open -0.96 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:35:33  price 30097.63 (open -0.73 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:35:48  price 30074.39 (open -0.93 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  15:36:03  price 30076.17 (open -0.92 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:36:33  price 30077.96 (open -0.90 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:36:48  price 30097.63 (open -0.73 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:38:18  price 30049.35 (open -1.14 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:38:48  price 30015.38 (open -1.42 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  exit: Stop at 30053.62

**NP-YM (NY PM MF3)** 2026-07-20 12:00:03 ET, SHORT 6 lots at 29048.88, safety stop 29168.00 (1.5 x own stop 79.4167 pts). Result managed +7 pts/lot (+0.09 R, $+808) ; own bracket result +40 pts (+0.50 R, $+4778). MFE +1.15 R, MAE -0.82 R, 36 min under water (longest 30 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 2m:W 8m:A
  12:00:04  price 29053.64 (open -0.06 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  12:01:03  price 29058.40 (open -0.12 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:01:18  price 29063.17 (open -0.18 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  12:01:33  price 29066.74 (open -0.22 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  12:02:03  price 29046.49 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:02:48  price 29032.20 (open +0.21 R of the book stop): state change desk [NORMAL/NNNNWA: NORMAL/NNNNWA]
  12:06:48  price 29094.14 (open -0.57 R of the book stop): state change desk [NORMAL/ANNNWA: NORMAL/ANNNWA]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  12:07:18  price 29098.91 (open -0.63 R of the book stop): took a part [DF: DF]
  12:08:34  price 29098.91 (open -0.63 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:08:49  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANWA: DEFEND/ANANWA]
  12:09:04  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:09:19  price 29100.10 (open -0.65 R of the book stop): state change desk [NORMAL/NNANWA: NORMAL/NNANWA]
  12:09:34  price 29100.10 (open -0.65 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:09:49  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  12:10:34  price 29110.82 (open -0.78 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:16:05  price 29086.99 (open -0.48 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:25:11  price 29102.48 (open -0.68 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  12:25:26  price 29098.91 (open -0.63 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:34:57  price 29047.68 (open +0.01 R of the book stop): state change desk [NORMAL/WNNNNA: NORMAL/WNNNNA]
  12:35:57  price 29056.02 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): state change desk [NORMAL/WNNNAA: NORMAL/WNNNAA]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): state change DEFENDING>OUT [DV: DV]
  12:41:27  price 28973.83 (open +0.95 R of the book stop): closed everything [DV: DV]
  exit: ExAlgoAll_DV at 29042.08

**NP-ZN (NY PM MF2)** 2026-07-29 14:12:05 ET, LONG 6 lots at 27852.42, safety stop 27673.60 (1.5 x own stop 119.208 pts). Result managed -2 pts/lot (-0.02 R, $-282) ; own bracket: not taken (slot effect). MFE +0.51 R, MAE -1.23 R, 27 min under water (longest 26 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  14:12:06  price 27855.99 (open +0.03 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  14:13:05  price 27823.81 (open -0.24 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  14:13:20  price 27834.54 (open -0.15 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:13:35  price 27814.87 (open -0.32 R of the book stop): state change desk [NORMAL/NNANNW: NORMAL/NNANNW]
  14:15:05  price 27805.93 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNAW: NORMAL/NNNNAW]
  14:15:50  price 27829.17 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  14:16:05  price 27829.17 (open -0.20 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:17:05  price 27811.29 (open -0.35 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:17:20  price 27791.62 (open -0.51 R of the book stop): took a part [DF: DF]
  14:17:35  price 27782.68 (open -0.58 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:18:05  price 27786.26 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:18:20  price 27766.59 (open -0.72 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:18:50  price 27775.53 (open -0.65 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:19:05  price 27764.80 (open -0.73 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:19:35  price 27770.16 (open -0.69 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:20:05  price 27766.59 (open -0.72 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:20:20  price 27771.95 (open -0.68 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:21:35  price 27737.98 (open -0.96 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:21:50  price 27752.28 (open -0.84 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  14:22:35  price 27743.34 (open -0.92 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:23:05  price 27759.43 (open -0.78 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:27:05  price 27746.92 (open -0.89 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:28:05  price 27752.28 (open -0.84 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:30:05  price 27793.41 (open -0.49 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:31:35  price 27759.43 (open -0.78 R of the book stop): state change desk [NORMAL/NANNNN: NORMAL/NANNNN]
  14:31:50  price 27789.83 (open -0.52 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:32:05  price 27736.19 (open -0.98 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:32:35  price 27755.86 (open -0.81 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:32:50  price 27736.19 (open -0.98 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:33:35  price 27768.37 (open -0.70 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:36:20  price 27737.98 (open -0.96 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:36:50  price 27775.53 (open -0.65 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:37:05  price 27793.41 (open -0.49 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:38:05  price 27834.54 (open -0.15 R of the book stop): state change desk [NORMAL/WNNANN: NORMAL/WNNANN]
  14:39:05  price 27857.78 (open +0.04 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  14:40:20  price 27893.54 (open +0.35 R of the book stop): state change DEFENDING>RUNNER [OB1: OB1]
  14:40:20  price 27893.54 (open +0.35 R of the book stop): moved the stop closer [OB1: OB1]
  14:40:50  price 27911.42 (open +0.49 R of the book stop): state change RUNNER>OUT [DV: DV]
  exit: ExAlgoAll_DV at 27850.12

**NP-ZN (NY PM MF2)** 2026-08-11 14:42:12 ET, SHORT 6 lots at 29545.79, safety stop 29724.60 (1.5 x own stop 119.208 pts). Result managed -65 pts/lot (-0.55 R, $-7847) ; own bracket: not taken (slot effect). MFE +0.02 R, MAE -0.96 R, 78 min under water (longest 78 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A
  14:42:13  price 29545.79 (open +0.00 R of the book stop): state change desk [ABORT/AAANNN: ABORT/AAANNN]
  14:43:12  price 29549.37 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:44:12  price 29558.31 (open -0.11 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:44:27  price 29552.94 (open -0.06 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:44:42  price 29552.94 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNWN: NORMAL/NNNNWN]
  14:45:12  price 29554.73 (open -0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:45:27  price 29554.73 (open -0.08 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:49:14  price 29576.19 (open -0.26 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:49:14  price 29576.19 (open -0.26 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:49:14  price 29576.19 (open -0.26 R of the book stop): took a part [DF: DF]
  14:50:14  price 29585.13 (open -0.33 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:51:14  price 29581.55 (open -0.30 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:51:29  price 29585.13 (open -0.33 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:52:00  price 29585.13 (open -0.33 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:52:45  price 29590.49 (open -0.38 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:53:00  price 29592.28 (open -0.39 R of the book stop): state change desk [NORMAL/NNANNN: NORMAL/NNANNN]
  14:54:01  price 29594.07 (open -0.41 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:55:16  price 29590.49 (open -0.38 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:55:31  price 29592.28 (open -0.39 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:56:01  price 29592.28 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:58:01  price 29592.28 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:00:01  price 29581.55 (open -0.30 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:03:47  price 29592.28 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:04:02  price 29588.71 (open -0.36 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:05:03  price 29592.28 (open -0.39 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:05:19  price 29588.71 (open -0.36 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:07:07  price 29576.19 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:08:52  price 29574.40 (open -0.24 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:09:07  price 29576.19 (open -0.26 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:09:22  price 29572.61 (open -0.22 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  15:09:52  price 29583.34 (open -0.32 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:13:23  price 29601.22 (open -0.46 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:14:08  price 29610.16 (open -0.54 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:14:23  price 29608.38 (open -0.52 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:16:09  price 29603.01 (open -0.48 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:24:10  price 29611.95 (open -0.55 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:28:11  price 29615.53 (open -0.58 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:30:11  price 29626.26 (open -0.68 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  15:33:11  price 29629.83 (open -0.70 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:34:56  price 29636.99 (open -0.77 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  exit: UWTime at 29611.12

**NP-YM (NY PM MF3)** 2026-08-27 13:30:03 ET, LONG 6 lots at 29642.88, safety stop 29523.75 (1.5 x own stop 79.4167 pts). Result managed -43 pts/lot (-0.54 R, $-5167) ; own bracket result -79 pts (-0.99 R, $-9457). MFE +0.23 R, MAE -1.44 R, 128 min under water (longest 122 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 3m:W 11m:N 32m:A
  13:30:05  price 29640.49 (open -0.03 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:31:03  price 29642.88 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:31:33  price 29636.92 (open -0.08 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  13:31:48  price 29638.11 (open -0.06 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:32:03  price 29640.49 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:33:03  price 29652.40 (open +0.12 R of the book stop): state change desk [PRESS/NNWNNW: PRESS/NNWNNW]
  13:33:18  price 29648.83 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:39:24  price 29633.35 (open -0.12 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  13:39:39  price 29635.73 (open -0.09 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:44:40  price 29632.15 (open -0.14 R of the book stop): state change desk [NORMAL/NANNNW: NORMAL/NANNNW]
  13:44:55  price 29628.58 (open -0.18 R of the book stop): state change desk [NORMAL/NNNNNW: NORMAL/NNNNNW]
  13:45:25  price 29630.96 (open -0.15 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:46:40  price 29617.86 (open -0.32 R of the book stop): state change desk [NORMAL/ANNNWW: NORMAL/ANNNWW]
  13:47:10  price 29625.01 (open -0.22 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:48:10  price 29617.86 (open -0.32 R of the book stop): state change desk [NORMAL/ANNNWW: NORMAL/ANNNWW]
  13:49:55  price 29617.86 (open -0.32 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:50:26  price 29615.48 (open -0.35 R of the book stop): state change desk [NORMAL/ANNNWW: NORMAL/ANNNWW]
  13:50:41  price 29615.48 (open -0.35 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:51:11  price 29611.90 (open -0.39 R of the book stop): state change desk [NORMAL/NNAAWW: NORMAL/NNAAWW]
  13:51:56  price 29616.67 (open -0.33 R of the book stop): state change desk [NORMAL/NNNAWW: NORMAL/NNNAWW]
  13:52:11  price 29615.48 (open -0.35 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:54:11  price 29622.62 (open -0.26 R of the book stop): state change desk [NORMAL/NNNAWW: NORMAL/NNNAWW]
  13:56:11  price 29617.86 (open -0.32 R of the book stop): state change desk [PRESS/NNNNWW: PRESS/NNNNWW]
  13:58:27  price 29610.71 (open -0.41 R of the book stop): state change desk [NORMAL/NNANWW: NORMAL/NNANWW]
  14:01:27  price 29603.56 (open -0.49 R of the book stop): state change desk [NORMAL/ANANWW: NORMAL/ANANWW]
  14:04:12  price 29580.93 (open -0.78 R of the book stop): state change desk [NORMAL/ANAAWW: NORMAL/ANAAWW]
  14:06:57  price 29588.08 (open -0.69 R of the book stop): state change desk [NORMAL/NNAAWW: NORMAL/NNAAWW]
  14:07:12  price 29590.46 (open -0.66 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  14:09:12  price 29577.36 (open -0.83 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:13:57  price 29569.02 (open -0.93 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:14:27  price 29574.97 (open -0.85 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:16:12  price 29576.17 (open -0.84 R of the book stop): state change desk [NORMAL/NNAAWN: NORMAL/NNAAWN]
  14:17:12  price 29572.59 (open -0.89 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:18:59  price 29583.31 (open -0.75 R of the book stop): state change desk [NORMAL/WNANWN: NORMAL/WNANWN]
  14:19:14  price 29584.50 (open -0.73 R of the book stop): state change desk [PRESS/WNNNWN: PRESS/WNNNWN]
  14:19:44  price 29577.36 (open -0.83 R of the book stop): state change desk [NORMAL/WNANWN: NORMAL/WNANWN]
  14:20:14  price 29582.12 (open -0.77 R of the book stop): state change desk [PRESS/WNNNWN: PRESS/WNNNWN]
  14:20:59  price 29579.74 (open -0.80 R of the book stop): state change desk [NORMAL/WNANWN: NORMAL/WNANWN]
  14:21:59  price 29576.17 (open -0.84 R of the book stop): state change desk [NORMAL/NNANWN: NORMAL/NNANWN]
  14:22:14  price 29580.93 (open -0.78 R of the book stop): state change desk [NORMAL/WNANWN: NORMAL/WNANWN]
  exit: ExAlgoAll_CL at 29599.88

**NP-ZN (NY PM MF2)** 2026-08-31 13:19:34 ET, SHORT 6 lots at 29410.92, safety stop 29589.73 (1.5 x own stop 119.208 pts). Result managed -34 pts/lot (-0.28 R, $-4052) ; own bracket: not taken (slot effect). MFE +0.20 R, MAE -0.37 R, 17 min under water (longest 11 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:A 7m:N 10m:W 19m:N
  13:19:35  price 29410.92 (open -0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:24:05  price 29421.65 (open -0.09 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:25:07  price 29418.07 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:27:23  price 29400.19 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNAN: NORMAL/NNNNAN]
  13:27:38  price 29403.76 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:30:08  price 29396.61 (open +0.12 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:30:53  price 29393.04 (open +0.15 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:31:08  price 29393.04 (open +0.15 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  13:33:08  price 29400.19 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:36:08  price 29396.61 (open +0.12 R of the book stop): state change desk [NORMAL/WNNNNN: NORMAL/WNNNNN]
  13:36:38  price 29401.98 (open +0.08 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:36:53  price 29409.13 (open +0.01 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:37:08  price 29407.34 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:37:38  price 29410.92 (open -0.00 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:37:53  price 29410.92 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:39:54  price 29410.92 (open -0.00 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:42:11  price 29432.37 (open -0.18 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:42:11  price 29432.37 (open -0.18 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:42:11  price 29432.37 (open -0.18 R of the book stop): took a part [DF: DF]
  13:43:11  price 29427.01 (open -0.14 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:44:11  price 29435.95 (open -0.21 R of the book stop): state change desk [DEFEND/ANNANN: DEFEND/ANNANN]
  13:45:11  price 29437.74 (open -0.22 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  13:46:11  price 29437.74 (open -0.22 R of the book stop): state change desk [DEFEND/ANNANA: DEFEND/ANNANA]
  13:47:11  price 29435.95 (open -0.21 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:48:12  price 29437.74 (open -0.22 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  13:48:27  price 29435.95 (open -0.21 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:49:12  price 29443.10 (open -0.27 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  13:49:59  price 29437.74 (open -0.22 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:50:14  price 29441.31 (open -0.26 R of the book stop): state change desk [DEFEND/ANANNA: DEFEND/ANANNA]
  13:50:44  price 29455.62 (open -0.38 R of the book stop): state change desk [ABORT/AAANNA: ABORT/AAANNA]
  13:50:44  price 29455.62 (open -0.38 R of the book stop): state change DEFENDING>OUT [AB: AB]
  13:50:44  price 29455.62 (open -0.38 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 29444.62

**NP-YM (NY PM MF3)** 2026-09-14 13:00:03 ET, SHORT 6 lots at 29256.54, safety stop 29375.67 (1.5 x own stop 79.4167 pts). Result managed -9 pts/lot (-0.11 R, $-1102) ; own bracket result +40 pts (+0.50 R, $+4798). MFE +0.31 R, MAE -0.24 R, 12 min under water (longest 3 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 4m:W 7m:N 9m:W 12m:N
  13:00:04  price 29257.73 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  13:01:03  price 29261.31 (open -0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:01:18  price 29255.35 (open +0.01 R of the book stop): state change desk [DEFEND/NNNNAA: DEFEND/NNNNAA]
  13:01:18  price 29255.35 (open +0.01 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  13:01:18  price 29255.35 (open +0.01 R of the book stop): took a part [DF: DF]
  13:02:05  price 29251.78 (open +0.06 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:03:35  price 29247.01 (open +0.12 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:04:05  price 29249.39 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:12:18  price 29270.84 (open -0.18 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:13:03  price 29267.26 (open -0.14 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:16:06  price 29255.35 (open +0.01 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:16:21  price 29254.16 (open +0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:18:21  price 29243.44 (open +0.17 R of the book stop): state change desk [NORMAL/NNWNNA: NORMAL/NNWNNA]
  13:19:06  price 29243.44 (open +0.17 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:20:06  price 29248.20 (open +0.11 R of the book stop): state change desk [NORMAL/NNWWNA: NORMAL/NNWWNA]
  13:20:21  price 29249.39 (open +0.09 R of the book stop): state change desk [NORMAL/NNNWNA: NORMAL/NNNWNA]
  13:20:36  price 29258.92 (open -0.03 R of the book stop): state change desk [NORMAL/ANNWNA: NORMAL/ANNWNA]
  13:21:06  price 29257.73 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:22:53  price 29258.92 (open -0.03 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:23:08  price 29257.73 (open -0.01 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:23:23  price 29260.12 (open -0.04 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:25:55  price 29258.92 (open -0.03 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:26:41  price 29263.69 (open -0.09 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:27:11  price 29260.12 (open -0.04 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  13:28:33  price 29268.45 (open -0.15 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  13:29:33  price 29275.60 (open -0.24 R of the book stop): state change desk [ABORT/AANNNA: ABORT/AANNNA]
  13:29:33  price 29275.60 (open -0.24 R of the book stop): state change DEFENDING>OUT [AB: AB]
  13:29:33  price 29275.60 (open -0.24 R of the book stop): closed everything [AB: AB]
  exit: ExAlgoAll_AB at 29265.67

**NP-YM (NY PM MF3)** 2026-09-29 14:30:03 ET, SHORT 6 lots at 30598.83, safety stop 30717.96 (1.5 x own stop 79.4167 pts). Result managed -42 pts/lot (-0.53 R, $-5087) ; own bracket result -17 pts (-0.22 R, $-2072). MFE +0.23 R, MAE -0.78 R, 76 min under water (longest 69 min).
Health vote (A = against / W = with / N = nothing / - = no history, vs this book's own winners): 1m:N 2m:W 11m:A
  14:30:04  price 30598.83 (open +0.00 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:31:33  price 30588.11 (open +0.14 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:32:18  price 30591.69 (open +0.09 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:34:19  price 30585.73 (open +0.17 R of the book stop): state change desk [NORMAL/NNWNNN: NORMAL/NNWNNN]
  14:34:34  price 30589.30 (open +0.12 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:38:21  price 30613.13 (open -0.18 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:38:36  price 30625.04 (open -0.33 R of the book stop): state change desk [NORMAL/ANNNWN: NORMAL/ANNNWN]
  14:39:06  price 30633.38 (open -0.43 R of the book stop): state change desk [NORMAL/ANANWN: NORMAL/ANANWN]
  14:41:06  price 30651.25 (open -0.66 R of the book stop): state change desk [DEFEND/ANAAWN: DEFEND/ANAAWN]
  14:41:06  price 30651.25 (open -0.66 R of the book stop): state change PROBE>DEFENDING [DF: DF]
  14:41:06  price 30651.25 (open -0.66 R of the book stop): took a part [DF: DF]
  14:43:21  price 30636.95 (open -0.48 R of the book stop): state change desk [DEFEND/ANAANN: DEFEND/ANAANN]
  14:43:36  price 30640.53 (open -0.52 R of the book stop): state change desk [DEFEND/NNAANN: DEFEND/NNAANN]
  14:45:06  price 30640.53 (open -0.52 R of the book stop): state change desk [NORMAL/NNNANN: NORMAL/NNNANN]
  14:46:06  price 30642.91 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:51:22  price 30645.29 (open -0.58 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:51:37  price 30642.91 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:51:52  price 30644.10 (open -0.57 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:52:38  price 30644.10 (open -0.57 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:52:53  price 30648.87 (open -0.63 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  14:54:38  price 30642.91 (open -0.55 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  14:55:08  price 30638.14 (open -0.49 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  14:59:09  price 30653.63 (open -0.69 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  14:59:39  price 30644.10 (open -0.57 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:00:25  price 30651.25 (open -0.66 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  15:00:40  price 30650.06 (open -0.65 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:03:41  price 30648.87 (open -0.63 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:03:56  price 30646.48 (open -0.60 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:04:41  price 30647.67 (open -0.61 R of the book stop): state change desk [DEFEND/NNANNA: DEFEND/NNANNA]
  15:05:11  price 30651.25 (open -0.66 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:06:42  price 30654.82 (open -0.70 R of the book stop): state change desk [DEFEND/ANANNN: DEFEND/ANANNN]
  15:06:57  price 30651.25 (open -0.66 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:09:12  price 30646.48 (open -0.60 R of the book stop): state change desk [NORMAL/NNNNNA: NORMAL/NNNNNA]
  15:11:14  price 30639.34 (open -0.51 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:15:00  price 30622.66 (open -0.30 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:16:00  price 30620.28 (open -0.27 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:18:00  price 30623.85 (open -0.32 R of the book stop): state change desk [NORMAL/NNNWNN: NORMAL/NNNWNN]
  15:19:00  price 30628.61 (open -0.38 R of the book stop): state change desk [NORMAL/NNNNNN: NORMAL/NNNNNN]
  15:21:45  price 30631.00 (open -0.41 R of the book stop): state change desk [NORMAL/ANNNNN: NORMAL/ANNNNN]
  15:22:00  price 30633.38 (open -0.43 R of the book stop): state change desk [DEFEND/ANNNNA: DEFEND/ANNNNA]
  exit: ExAlgoAll_AB at 30641.17
