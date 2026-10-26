# REPORT RZ7 - dip-buy with a limit at a structural level (ES, NQ, RTY, YM)

RZ7 tests whether the classic daily dip-buy (RSI(2)<5 or IBS<0.10, close above SMA200) improves when the market-on-close entry is replaced by a next-session buy limit at the prior-day low or the midpoint of the prior-day RTH range (fill only on a one-tick trade-through; no fill = no trade). Stop 3 ADR20 below the limit, exit at the 16:16 ET price three labels after the fill; 1 tick slippage on exits; $4.36 per contract; unit-ADR sizing. 4 cells per instrument, clean-only selection, I9-style sleeve gates, own random-day null (same trade count through the same limit logic). Disclosure: ADR20 is used as the ATR proxy; the bar level is 16:16 close, same as C11.


| instrument | selected cell | eligible | verdict | gates | additive 20% clean/H1/H2 | standalone Sharpe | trades | ERA | own-null rank |
|---|---|---|---|---|---|---|---|---|---|
| ES | none | 0 | NO | - | - | - | - | - | - |
| NQ | none | 0 | NO | - | - | - | - | - | - |
| RTY | none | 0 | NO | - | - | - | - | - | - |
| YM | none | 0 | NO | - | - | - | - | - | - |

Per-instrument reports: REPORT_RZ7_<SYM>.md.

DONE RZ7