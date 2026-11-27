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
