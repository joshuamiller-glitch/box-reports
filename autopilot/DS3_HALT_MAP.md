# DS3_HALT_MAP - T-HALT-RESUME stage 1: what each live book's losing streaks and losing stretches look like (GOV-1)

Research only; UNTOUCHED never read (capped 20260206). Stream = the D6-faithful lock-engine trades of each live book (integer half-up min-1 lots, live lots, N basis, Native 1.28, all-signal running-max BookR, session-lot R, per-book day/week locks + COMBINED 12R week lock in K6 R; DS3_GOVERNOR_FIDELITY.md). r = trade net $ / the book's planned-lot R (base lots x 60 pt x $20). Streak/regime facts use trades that CLOSED before the signal (causal). Windows by entry label day.

Prereg: the HALT_MAP numbers are descriptive base rates, nothing is selected from them; the rule grid in DS3_HALT_RULES.md is fixed in `autopilot/HALT_RESUME_GOV_prereg.md` (sha256 recorded in DECISIONS.md) before any halt cell is scored.

## 1. Base rates: after N straight losers, the next K trades (per book; L6M | PRE+X' pooled | all)

Entry i has N straight losers just before it. "next 10 mean" = mean r of trades i..i+9; "P(next 10 net<0)" = share of such starts whose next-10 sum is negative; "uncond" = the same over all starts in the window.

| book | window | n trades | mean r | uncond P(next10<0) | N=3: starts, next-10 mean r, P(<0) | N=4: starts, mean, P | N=5: starts, mean, P | N=6: starts, mean, P |
|---|---|---|---|---|---|---|---|---|
| HM | L6M | 274 | +0.127 | 0.34 | 19, +0.165, 0.37 | 7, +0.096, 0.43 | 2, +0.060, 0.50 | 0, +nan, nan |
| HM | PRE+X | 735 | +0.028 | 0.44 | 73, +0.028, 0.47 | 34, +0.025, 0.47 | 17, -0.000, 0.53 | 8, -0.067, 0.62 |
| HM | ALL | 1028 | +0.055 | 0.41 | 95, +0.057, 0.43 | 43, +0.041, 0.44 | 20, +0.011, 0.50 | 8, -0.067, 0.62 |
| KB | L6M | 664 | +0.077 | 0.40 | 60, +0.113, 0.40 | 24, +0.135, 0.38 | 8, +0.082, 0.38 | 4, +0.034, 0.25 |
| KB | PRE+X | 1609 | +0.051 | 0.42 | 160, +0.043, 0.41 | 76, -0.008, 0.51 | 38, -0.066, 0.66 | 21, -0.102, 0.76 |
| KB | ALL | 2310 | +0.059 | 0.41 | 227, +0.059, 0.40 | 105, +0.029, 0.46 | 50, -0.029, 0.56 | 28, -0.058, 0.61 |
| MV | L6M | 347 | +0.017 | 0.51 | 27, +0.042, 0.48 | 8, +0.190, 0.25 | 3, +0.243, 0.00 | 1, +0.302, 0.00 |
| MV | PRE+X | 906 | +0.009 | 0.52 | 95, -0.064, 0.65 | 43, -0.065, 0.65 | 17, -0.068, 0.71 | 7, -0.002, 0.71 |
| MV | ALL | 1277 | +0.013 | 0.52 | 125, -0.038, 0.61 | 52, -0.025, 0.60 | 20, -0.021, 0.60 | 8, +0.036, 0.62 |
| PB | L6M | 422 | +0.231 | 0.29 | 29, +0.295, 0.17 | 13, +0.393, 0.08 | 7, +0.460, 0.00 | 4, +0.541, 0.00 |
| PB | PRE+X | 1303 | +0.052 | 0.47 | 150, +0.096, 0.44 | 75, +0.074, 0.48 | 41, +0.018, 0.54 | 23, -0.071, 0.57 |
| PB | ALL | 1764 | +0.095 | 0.43 | 185, +0.129, 0.40 | 91, +0.119, 0.43 | 49, +0.078, 0.47 | 27, +0.020, 0.48 |
| PE | L6M | 456 | +0.178 | 0.29 | 31, +0.299, 0.26 | 10, +0.376, 0.20 | 2, +0.074, 0.00 | 1, +0.069, 0.00 |
| PE | PRE+X | 1176 | +0.079 | 0.40 | 133, +0.029, 0.44 | 70, -0.020, 0.47 | 40, -0.071, 0.55 | 24, -0.114, 0.58 |
| PE | ALL | 1661 | +0.111 | 0.36 | 165, +0.081, 0.41 | 80, +0.030, 0.44 | 42, -0.064, 0.52 | 25, -0.107, 0.56 |
| SM | L6M | 92 | +0.070 | 0.51 | 7, +0.310, 0.14 | 4, +0.392, 0.00 | 3, +0.437, 0.00 | 2, +0.445, 0.00 |
| SM | PRE+X | 326 | +0.075 | 0.40 | 25, -0.028, 0.36 | 16, -0.033, 0.38 | 9, -0.127, 0.44 | 4, -0.492, 0.75 |
| SM | ALL | 429 | +0.076 | 0.41 | 32, +0.046, 0.31 | 20, +0.052, 0.30 | 12, +0.014, 0.33 | 6, -0.180, 0.50 |

## 2. How long do losing streaks and losing stretches last (all history, trades)

| book | max losing streak | streaks >=3 per 100 trades | mean length of a >=3 streak | rolling-20 sum < -3R: share of trades | mean length (trades) of such stretches |
|---|---|---|---|---|---|
| HM | 8 | 5.1 | 3.8 | 0.111 | 4.6 |
| KB | 10 | 5.3 | 3.9 | 0.157 | 5.2 |
| MV | 6 | 5.7 | 3.7 | 0.235 | 5.6 |
| PB | 10 | 5.4 | 4.0 | 0.209 | 5.0 |
| PE | 11 | 5.1 | 3.9 | 0.139 | 5.8 |
| SM | 8 | 3.0 | 4.5 | 0.177 | 8.4 |

## 3. Losing weeks and days (weekly/daily book P&L in R, all history)

| book | losing-day share | P(day<0 given prev day<0) | P(day<0 given prev 2 days<0) | losing-week share | P(week<0 given prev week<0) | mean week R after a week < -3R |
|---|---|---|---|---|---|---|---|
| HM | 0.50 | 0.53 | 0.57 | 0.52 | 0.56 | +1.02 |
| KB | 0.46 | 0.42 | 0.44 | 0.49 | 0.54 | +1.53 |
| MV | 0.54 | 0.49 | 0.46 | 0.58 | 0.56 | +0.51 |
| PB | 0.44 | 0.45 | 0.52 | 0.53 | 0.49 | +0.89 |
| PE | 0.43 | 0.44 | 0.52 | 0.52 | 0.57 | -0.13 |
| SM | 0.44 | 0.43 | 0.44 | 0.48 | 0.40 | +0.90 |

Plain lines (L6M): see section 1; e.g. the "after 4 straight losers" columns give the next-10 mean r against the unconditional mean r of the same window. A streak rule helps only if the next-10 mean after the trigger is clearly below the unconditional mean; most cells are inside noise (starts overlap: effective n is about starts/10).
