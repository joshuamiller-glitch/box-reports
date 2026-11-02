# ZONES3_LEAD_REGISTER - every lead ever flagged, status by base (S5 light-job agent; refreshed with the master loop)

V13X = DEFECT BASE (add-fill ordering defect), V13Y = fixed base. S5 rows are read from ZONES3_MASTER_TABLE.csv (lock-off frame); other owners' rows are their last reported status plus the LOMO/bootstrap chain numbers (ZONES3_LEADS_LOMO_BOOT.csv, V13X-era chains) and are marked 'pending V13Y' until the owner republishes.

| lead | owner | definition | status on V13X (defect base) | status on V13Y | final label |
|---|---|---|---|---|---|
| sopen40 half | S5 density (lock-off frame) | halve lots if no fresh set line (either side) within 40*E/20000 pts | L6M +51% PRE +22% X' +11%; VOLUME | L6M +41% PRE +11% X' +21%; NOISE | VOLUME / NOISE, not a lead |
| sA40>=1 skip | S5 density (lock-off frame) | skip if a fresh set line within 40*E/20000 pts ahead | L6M +36% PRE +14% X' +27%; NOISE | L6M +36% PRE +0% X' -5%; NOISE ONE-WEEK | ONE-WEEK, not a lead |
| nA60>=1 skip | S5 density (lock-off frame) | skip if a fresh set line within 60 pts ahead | L6M +38% PRE -6% X' +31%; VOLUME | L6M +36% PRE -36% X' +7%; NOISE ONE-WEEK | ONE-WEEK, not a lead |
| rho60>=2 skip | S5 density (lock-off frame) | skip if (nA60+1)/(nB60+1) >= 2 | L6M +34% PRE +9% X' +32%; VOLUME | L6M +41% PRE +1% X' +36%; VOLUME ONE-WEEK | ONE-WEEK, not a lead |
| openA40 half | S5 density (lock-off frame) | halve lots if no fresh set line ahead within 40 pts | L6M +37% PRE +36% X' +30%; VOLUME | L6M +35% PRE +20% X' +41%; VOLUME | VOLUME / NOISE, not a lead |
| open20 half | S5 density (lock-off frame) | halve lots if no fresh set line within 20 pts either side | L6M +47% PRE +26% X' +1%; VOLUME | L6M +41% PRE +17% X' +9%; VOLUME | VOLUME / NOISE, not a lead |
| nA40>=1 skip (v1.2 assumed) | S5 | skip if a fresh line within 40 pts ahead | v1.2-assumed: L6M +23% ONE-WEEK | V13Y: L6M +5% PRE -5% X' -4%; NOISE | ONE-WEEK |
| PUL k3 1h/4h/24h ahead D20/D30 | ZL-1 | pullback level ahead | chains AH20/AH30/AHA20 PUL AH30: total +124k, P(>0) 0.73, best-month 122%; PUL AH20: total +155k, P(>0) 0.80, best-month 102%; PUL AHA20: total +132k, P(>0) 0.72, best-month 140% | pending V13Y re-run by owner | ONE-MONTH (best month > 100%) |
| G2 TVP-confirmed set-line skip Dl60 | ZL-3 | set line within 60 ahead confirmed by TVP zone: skip; unconfirmed halved | ZL-3 G2 lock12: total +186k, P(>0) 0.75, best-month 52%; ZL-3 G2 lockNone: total -90k, P(>0) 0.38, best-month n/a | pending V13Y | FRAGILE / lock-12-only (lead withdrawn by owner) |
| CRT4h 30pts fw2 solo | Z2 | CRT4h line at D30, fresh <=2h, no other line within 5 pts | Z2 CRT4h30fw2_lock12: total +102k, P(>0) 0.99, best-month 39%; Z2 CRT4h30fw2_lockNone: total +75k, P(>0) 1.00, best-month 20% | pending V13Y | not one-month; needs placebo/noise band on V13Y |
| camH3 40pts fw8 any | Z2 | camH3 line at D40, fresh <= 8h | Z2 camH3_40fw8_lock12: total +88k, P(>0) 0.71, best-month 137%; Z2 camH3_40fw8_lockNone: total +68k, P(>0) 0.92, best-month 29% | pending V13Y | lock-12 frame ONE-MONTH; lock none +68k |
| TVP_poc_day A40 skip | ZL-2 | tape POC (day) ahead within 40: skip | ZL-2 A40__TVP_poc_day__skip: total +157k, P(>0) 0.88, best-month 46% | pending V13Y | owner label pending (chain only) |
| PRF/vwap/day D40 skip | S4a | VWAP-day line ahead within 40: skip | S4A PRF/vwap/day D40 skip: total +191k, P(>0) 0.88, best-month 23% | pending V13Y | owner label pending |
| FIB/ote705_dn D40 skip | S4a | OTE705 down line ahead within 40: skip | S4A FIB/ote705_dn/15m D40 skip: total +23k, P(>0) 0.57, best-month 226% | pending V13Y | ONE-MONTH (best month > 100%) |
| ALL7 skip / camH3 wt / kijun1h wt | Z3 | action table units | ALL7 skip: total +399k, P(>0) 0.98, best-month 38% // camH3 wt: total +301k, P(>0) 0.93, best-month 64% | pending V13Y | kijun1h wt ONE-MONTH; others band-NOISE |