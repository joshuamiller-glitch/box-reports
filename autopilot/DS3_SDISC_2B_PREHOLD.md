# DS3_SDISC_2B_PREHOLD - PRE-selected winners (D3SD2B), written BEFORE any HOLD/X number
Prereg l2vast/ds3/prereg/SD2B_prereg.md. PRE-only (2024-02-01..2025-06-30), exact lock engine, MEASURED basis, hybrid books. Rule: largest post-lock PRE in-session weekly mean among the stage-1 top 30 (n_PRE>=100), paired PRE delta vs live > 0. One HOLD look + one X look per row below.

| book | session | winner cfg | PRE in-session mean $/wk | PRE delta vs live $/wk | n PRE trades |
|---|---|---|---|---|---|
| ST | ASIA | ST|per=120,mult=1.0,ema=100 | 7,381 | 6,785 | 740 |
| ST | LONDON | ST|per=30,mult=1.5,ema=200 | 410 | 1,094 | 385 |
| ST | NY-AM | ST|per=120,mult=1.0,ema=200 | 5,462 | 4,917 | 417 |
| ST | NY-PM | ST|per=240,mult=1.0,ema=400 | 2,990 | 2,595 | 251 |
| HM | ASIA | HM|f=15,s=35,ema=100 | 8,473 | 5,412 | 656 |
| HM | LONDON | HM|f=30,s=120,ema=100 | 4,229 | 4,312 | 334 |
| HM | NY-AM | HM|f=20,s=35,ema=100 | 5,841 | 4,828 | 327 |
| HM | NY-PM | HM|f=30,s=55,ema=100 | 577 | 1,534 | 229 |
| WT | ASIA | WT|an=10,mult=1.5,ema=50 | 2,992 | 2,886 | 1002 |
| WT | LONDON | WT|an=10,mult=2.0,ema=200 | -656 | 1,965 | 633 |
| WT | NY-AM | WT|an=40,mult=1.5,ema=50 | 870 | 1,411 | 466 |
| WT | NY-PM | WT|an=20,mult=1.5,ema=200 | -831 | 1,327 | 363 |
| KB | ASIA | KB|k=2,n=30,m=1.5,na=14 | 10,896 | 6,489 | 648 |
| KB | LONDON | KB|k=3,n=8,m=0.5,na=20 | 3,641 | 1,371 | 377 |
| KB | NY-AM | KB|k=10,n=14,m=0.5,na=20 | 4,926 | 3,638 | 198 |
| KB | NY-PM | KB|k=2,n=30,m=2.0,na=20 | 4,447 | 1,530 | 187 |
| SM | ASIA | SM|k=5,n=10,m=5.0 | 4,858 | 62 | 229 |
| SM | LONDON | SM|k=10,n=10,m=3.0 | 3,312 | 3,162 | 258 |
| SM | NY-AM | SM|k=20,n=10,m=2.0 | 4,927 | 2,958 | 140 |
| SM | NY-PM | SM|k=5,n=7,m=3.0 | 1,502 | 2,230 | 187 |
| PE | ASIA | PE|R=3,P=1,ptype=1,ttype=1 | 7,355 | 2,865 | 492 |
| PE | LONDON | PE|R=3,P=1,ptype=1,ttype=0 | 3,548 | 7,951 | 265 |
| PE | NY-AM | PE|R=3,P=1,ptype=0,ttype=0 | 4,811 | 1,919 | 396 |
| PE | NY-PM | PE|R=15,P=1,ptype=0,ttype=0 | 2,892 | 562 | 201 |
| MA | ASIA | MA|k=10,fast=0.5,slow=0.1 | 4,589 | 1,926 | 361 |
| MA | LONDON | MA|k=5,fast=0.25,slow=0.05 | 3,543 | 1,701 | 251 |
| MA | NY-AM | MA|k=10,fast=0.75,slow=0.05 | 6,537 | 3,496 | 222 |
| MA | NY-PM | MA|k=3,fast=0.5,slow=0.02 | 4,189 | 4,935 | 282 |
| MV | ASIA | MV|lbs=(30, 60, 120, 240, 480),thr=0.5,k=3 | 7,433 | 3,415 | 563 |
| MV | LONDON | MV|lbs=(30, 60, 120, 240, 480),thr=1.0,k=5 | 129 | 3,048 | 213 |
| MV | NY-AM | MV|lbs=(5, 10, 20, 40, 80),thr=0.25,k=3 | 7,763 | 2,336 | 492 |
| MV | NY-PM | MV|lbs=(15, 30, 60, 120, 240),thr=0.25,k=4 | 3,567 | 3,925 | 188 |
| DN | ASIA | DN|k=3,n=30 | 9,364 | 5,534 | 632 |
| DN | LONDON | DN|k=5,n=20 | 4,258 | 4,279 | 460 |
| DN | NY-AM | DN|k=10,n=30 | 8,010 | 1,075 | 339 |
| DN | NY-PM | DN|k=10,n=40 | -172 | 1,102 | 144 |
| CR | ASIA | CR|htf=240,etf=5,etype=close,tmode=NB,buf=0 | -459 | 278 | 377 |
| CR | LONDON | CR|htf=240,etf=5,etype=csd,tmode=SO,buf=5 | -810 | 2,235 | 128 |
| CR | NY-AM | CR|htf=240,etf=15,etype=close,tmode=SO,buf=0 | -144 | 2,053 | 181 |
| CR | NY-PM | CR|htf=240,etf=5,etype=close,tmode=NB,buf=0 | 1,165 | 193 | 159 |

No tuned set (live PRE-best or no cell with n_PRE>=100 beating live): 
