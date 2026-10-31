# EDGE_STATUS_LOG - one line per status transition (data week, rule, old -> new, the number that moved it). Writer: RE-2 (stack-delta bank, weekly; units $/wk research lots; live A = /2.35). Transitions of cluster representatives, last 13 data weeks (2025-11-10..2026-02-02) on first write.

## RE-2 monitor run 2026-10-31T04:23Z (data to 2026-02-06)
2025-11-10 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | RISING -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 3,872 13w -7 26w 3,294 $/wk
2025-11-10 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [S73] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 808 13w 1,034 26w 1,315 $/wk
2025-11-10 | fs|P=50|stoppedSession!=london [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 19,504 13w 16,830 26w 12,833 $/wk
2025-11-10 | cap|live=12|x2.35|mode=room|session=pre|count=both100 [S73] | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.0, 4w 328 13w -254 26w 142 $/wk
2025-11-10 | fs|P=50|others<=2 [MKT] | OFF -> NEW | 13w mean 1,027 26w 3,949 $/wk
2025-11-10 | fs|P=50|asia&er20_5m>=0.4 [MKT] | OFF -> NEW | 13w mean 10,052 26w 417 $/wk
2025-11-10 | cap|live=6|x2.35|mode=skip|session=pre|count=openAll [MKT] | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -696 13w -4,330 26w 419 $/wk
2025-11-10 | fs|P=50|voltercile>=2 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 12,529 13w 9,497 26w 8,846 $/wk
2025-11-10 | fs|P=50|win=60m|ref=stoppedEntry [S73] | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.6, 4w -13,595 13w -1,574 26w -1,446 $/wk
2025-11-10 | fs|P=100|win=30m|ref=stoppedEntry [S73] | FADING -> STOPPED | CUSUM 2.2 sig, z4 -0.8, 4w -17,383 13w -4,532 26w 871 $/wk
2025-11-10 | fs|P=50|er20_5m<0.2 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 6,476 13w 8,094 26w 5,343 $/wk
2025-11-10 | fs|P=25|win=30m|ref=stoppedEntry [S73] | FADING -> STABLE | CUSUM 0.7 sig, z4 -1.2, 4w -10,285 13w 2,952 26w 2,963 $/wk
2025-11-10 | fs|P=50|stoppedSession=asia [S73] | NEW -> STABLE | CUSUM 0.7 sig, z4 -0.2, 4w 6,396 13w 9,040 26w 10,210 $/wk
2025-11-10 | fs|P=50|er20_5m<0.3 [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 37,050 13w 19,328 26w 11,899 $/wk
2025-11-10 | fs|P=50|voltercile>=1 [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.1, 4w 32,115 13w 7,977 26w 11,411 $/wk
2025-11-10 | fs|P=50|block=1800s [MKT] | OFF -> NEW | 13w mean 9,770 26w 602 $/wk
2025-11-10 | session pre x0.5 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 378 13w -1,145 26w 2,010 $/wk
2025-11-10 | fs|P=50|asia&voltercile>=2 [S73] | FADING -> STABLE | CUSUM 0.7 sig, z4 -1.1, 4w -10,675 13w 4,892 26w 5,153 $/wk
2025-11-10 | book WT x1.5 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 7,818 13w 2,257 26w 4,083 $/wk
2025-11-10 | session pre OFF [S73] | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -939 13w -641 26w 4,631 $/wk
2025-11-10 | book WT x1.5 [S73] | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 9,228 13w 3,418 26w 6,549 $/wk
2025-11-10 | fs|P=50|win=30m|ref=stoppedEntry [MKT] | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.5, 4w -1,174 13w 5,902 26w 6,420 $/wk
2025-11-10 | fs|P=50|win=10m|ref=stoppedEntry [MKT] | NEW -> STOPPED | CUSUM 3.3 sig, z4 -1.0, 4w -8,599 13w -3,734 26w -1,358 $/wk
2025-11-17 | book WT x1.5 [S73] | STABLE -> FADING | CUSUM 1.4 sig, z4 -0.7, 4w -2,807 13w 124 26w 4,119 $/wk
2025-11-17 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | FADING -> STOPPED | CUSUM 0.5 sig, z4 -0.4, 4w -1,217 13w -1,373 26w 3,107 $/wk
2025-11-17 | fs|P=50|oppBooks>=1 [S73] | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 1,705 13w 5,041 26w 3,637 $/wk
2025-11-17 | fs|P=50|er20_5m<0.4 [S73] | OFF -> NEW | 13w mean 3,733 26w 1,128 $/wk
2025-11-17 | fs|P=50|er20_5m<0.3 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 12,089 13w 21,364 26w 12,636 $/wk
2025-11-17 | fs|P=25|win=30m|ref=stoppedEntry [S73] | STABLE -> FADING | CUSUM 2.0 sig, z4 -2.1, 4w -21,022 13w 1,536 26w 2,781 $/wk
2025-11-17 | book WT x1.5 [MKT] | STABLE -> FADING | CUSUM 0.4 sig, z4 +0.1, 4w 5,661 13w 936 26w 4,157 $/wk
2025-11-17 | book PE x1.5 [MKT] | RISING -> STABLE | CUSUM 1.1 sig, z4 +0.4, 4w 7,999 13w 13,653 26w 3,786 $/wk
2025-11-17 | fs|P=50|stoppedSession!=london [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.9, 4w -7,427 13w 15,889 26w 12,605 $/wk
2025-11-17 | fs|P=50|others<=2 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +0.3, 4w 7,736 13w -1,012 26w 4,493 $/wk
2025-11-17 | fs|P=50|win=60m|ref=stackFirstEntry [MKT] | NEW -> STOPPED | CUSUM 0.3 sig, z4 -1.8, 4w -22,363 13w -2,089 26w 1,356 $/wk
2025-11-17 | fs|P=50|win=60m|ref=stoppedEntry [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.9, 4w -12,352 13w 5,865 26w 5,394 $/wk
2025-11-24 | fs|P=50|win=60m|ref=stackFirstEntry [MKT] | STOPPED -> NEW | 13w mean 2,761 26w 3,029 $/wk
2025-11-24 | book WT x1.5 [S73] | FADING -> STOPPED | CUSUM 1.3 sig, z4 -1.3, 4w -10,156 13w -228 26w 3,184 $/wk
2025-11-24 | book SM x1.5 [S73] | STABLE -> FADING | CUSUM 0.6 sig, z4 -1.3, 4w -6,387 13w 1,294 26w 4,485 $/wk
2025-11-24 | fs|P=50|er20_5m>=0.2 [MKT] | NEW -> FADING | CUSUM 0.4 sig, z4 -0.3, 4w -2,989 13w 769 26w 2,063 $/wk
2025-12-01 | fs|P=50|stoppedSession=pre [S73] | OFF -> NEW | 13w mean 308 26w 2,315 $/wk
2025-12-01 | fs|P=50|stoppedSession!=asia [MKT] | OFF -> NEW | 13w mean 2,384 26w 742 $/wk
2025-12-01 | fs|P=50|win=5m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 484 26w 769 $/wk
2025-12-01 | fs|P=50|voltercile<2 [MKT] | OFF -> NEW | 13w mean 2,851 26w 185 $/wk
2025-12-01 | fs|P=100|win=30m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 3,162 26w 2,366 $/wk
2025-12-01 | fs|P=50|er20_5m>=0.4 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 4,946 13w 5,033 26w 1,143 $/wk
2025-12-01 | book WT x1.5 [MKT] | FADING -> STABLE | CUSUM 1.7 sig, z4 -0.8, 4w -7,072 13w 1,759 26w 1,468 $/wk
2025-12-01 | fs|P=25|win=30m|ref=stoppedEntry [S73] | FADING -> STABLE | CUSUM 0.8 sig, z4 -0.6, 4w -2,468 13w 2,467 26w 4,117 $/wk
2025-12-01 | cap|live=12|x2.35|mode=room|session=pre|count=both100 [S73] | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w -409 26w 744 $/wk
2025-12-01 | fs|P=50|win=60m|ref=stackFirstEntry [MKT] | NEW -> STOPPED | CUSUM 0.7 sig, z4 -0.6, 4w -5,167 13w -301 26w 3,059 $/wk
2025-12-01 | fs|P=50|stoppedSession=nyam [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 4,678 13w 5,027 26w 1,767 $/wk
2025-12-01 | fs|P=50|er20_5m>=0.2 [MKT] | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -2,055 13w -2,191 26w 3,723 $/wk
2025-12-01 | book WT x1.5 [S73] | STOPPED -> NEW | 13w mean 218 26w 1,643 $/wk
2025-12-01 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | OFF -> NEW | 13w mean 442 26w 4,328 $/wk
2025-12-01 | book PE x1.5 [S73] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 2,578 13w 11,882 26w 6,315 $/wk
2025-12-08 | book WT x0.5 [MKT] | OFF -> NEW | 13w mean 1,941 26w 1,111 $/wk
2025-12-08 | fs|P=50|others<=2 [MKT] | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.6, 4w -3,091 13w -5,211 26w 3,540 $/wk
2025-12-08 | book WT x1.5 [S73] | NEW -> FADING | CUSUM 0.0 sig, z4 -1.5, 4w -12,697 13w 383 26w 2,059 $/wk
2025-12-08 | book SM x1.5 [S73] | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w 917 13w 5,456 26w 5,586 $/wk
2025-12-08 | skip 2nd same-dir signal in same book within 30 min after a LOSER [MKT] | OFF -> NEW | 13w mean 1,917 26w 1,626 $/wk
2025-12-08 | fs|P=50|oppBooks>=1 [S73] | STABLE -> STOPPED | CUSUM 1.7 sig, z4 -1.2, 4w -15,759 13w -524 26w 2,149 $/wk
2025-12-08 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.8, 4w -4,038 13w -777 26w 4,493 $/wk
2025-12-08 | fs|P=50|asia&er20_5m>=0.4 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 -1.1, 4w -10,005 13w 5,306 26w 1,719 $/wk
2025-12-08 | fs|P=25|stoppedSession=asia [MKT] | STABLE -> FADING | CUSUM 1.0 sig, z4 -1.6, 4w -17,775 13w 8,592 26w 8,230 $/wk
2025-12-08 | fs|P=50|stoppedSession=nypm [S73] | STABLE -> STOPPED | CUSUM 0.8 sig, z4 -0.4, 4w -2,110 13w -334 26w -647 $/wk
2025-12-08 | fs|P=50|stoppedSession=pre [S73] | NEW -> FADING | CUSUM 0.0 sig, z4 +0.5, 4w 4,928 13w 614 26w 2,511 $/wk
2025-12-08 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [S73] | STABLE -> STOPPED | CUSUM 0.1 sig, z4 -0.5, 4w -1,198 13w -250 26w 1,733 $/wk
2025-12-08 | fs|P=25|win=30m|ref=stoppedEntry [S73] | STABLE -> FADING | CUSUM 1.2 sig, z4 -1.4, 4w -13,251 13w 704 26w 2,883 $/wk
2025-12-08 | fs|P=25|stopdef=0 [MKT] | STABLE -> FADING | CUSUM 1.4 sig, z4 -1.7, 4w -26,139 13w 960 26w 4,101 $/wk
2025-12-08 | fs|P=50|stoppedSession!=asia [MKT] | NEW -> STOPPED | CUSUM 1.2 sig, z4 -1.0, 4w -17,084 13w -2,941 26w -1,003 $/wk
2025-12-08 | fs|P=50|voltercile<2 [MKT] | NEW -> STOPPED | CUSUM 1.1 sig, z4 -1.0, 4w -17,867 13w -809 26w -982 $/wk
2025-12-08 | fs|P=50|block=1800s [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 10,601 13w 20,831 26w 8,082 $/wk
2025-12-15 | cap|live=12|x2.35|mode=room|session=pre|count=both100 [S73] | OFF -> NEW | 13w mean 1,590 26w 1,125 $/wk
2025-12-15 | fs|P=50|stoppedSession=pre [S73] | FADING -> NEW | CUSUM 0.0 sig, z4 +2.4, 4w 17,416 13w 4,456 26w 4,432 $/wk
2025-12-15 | fs|P=50|others<=3 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 24,602 13w 17,818 26w 13,863 $/wk
2025-12-15 | fs|P=50|er20_5m>=0.4&voltercile>=2 [MKT] | OFF -> NEW | 13w mean 4,131 26w 719 $/wk
2025-12-15 | fs|P=50|block=1800s [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 45,975 13w 32,213 26w 12,021 $/wk
2025-12-15 | fs|P=25|win=30m|ref=stoppedEntry [S73] | FADING -> STOPPED | CUSUM 0.9 sig, z4 -0.4, 4w -4,519 13w -4,088 26w 61 $/wk
2025-12-15 | fs|P=50|others<=2 [MKT] | STOPPED -> NEW | 13w mean 3,453 26w 4,484 $/wk
2025-12-15 | fs|P=50|er20_5m>=0.2 [MKT] | OFF -> NEW | 13w mean 4,589 26w 4,257 $/wk
2025-12-15 | fs|P=50|er20_5m<0.4 [S73] | NEW -> STABLE | CUSUM 0.1 sig, z4 -0.5, 4w -14,302 13w 6,424 26w -3,104 $/wk
2025-12-15 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | STOPPED -> NEW | 13w mean 8,589 26w 6,940 $/wk
2025-12-15 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [S73] | STOPPED -> NEW | 13w mean 5,882 26w 3,694 $/wk
2025-12-15 | session pre OFF [S73] | OFF -> NEW | 13w mean 4,547 26w 8,987 $/wk
2025-12-15 | fs|P=50|oppBooks>=1 [S73] | STOPPED -> NEW | 13w mean 2,641 26w 3,167 $/wk
2025-12-15 | session pre x0.5 [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.4, 4w 23,643 13w 7,950 26w 7,033 $/wk
2025-12-15 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [MKT] | OFF -> NEW | 13w mean 6,431 26w 2,670 $/wk
2025-12-15 | fs|P=25|stopdef=0 [MKT] | FADING -> STOPPED | CUSUM 0.7 sig, z4 -1.2, 4w -18,869 13w -523 26w 1,855 $/wk
2025-12-15 | cap|live=6|x2.35|mode=skip|session=pre|count=openAll [MKT] | OFF -> NEW | 13w mean 7,668 26w 6,980 $/wk
2025-12-15 | fs|P=50|win=30m|ref=stoppedEntry [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 8,721 13w 7,426 26w 5,175 $/wk
2025-12-15 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | OFF -> NEW | 13w mean 1,580 26w 12,164 $/wk
2025-12-15 | book WT x1.5 [S73] | FADING -> NEW | CUSUM 0.0 sig, z4 -0.2, 4w -692 13w 2,324 26w 1,788 $/wk
2025-12-22 | fs|P=50|stoppedSession=nyam [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 9,042 13w 6,305 26w 2,370 $/wk
2025-12-22 | fs|P=50|oppBooks>=1 [S73] | NEW -> FADING | CUSUM 0.0 sig, z4 -0.9, 4w -10,784 13w 998 26w 1,999 $/wk
2025-12-22 | session pre x0.5 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 23,406 13w 8,325 26w 6,476 $/wk
2025-12-22 | book PE x1.5 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 11,119 13w 8,729 26w 5,335 $/wk
2025-12-22 | book WT x1.5 [S73] | NEW -> STOPPED | CUSUM 0.7 sig, z4 -0.4, 4w -4,071 13w -1,024 26w -192 $/wk
2025-12-22 | skip first 60 min of every session [MKT] | OFF -> NEW | 13w mean 3,467 26w 12,511 $/wk
2025-12-22 | ft|MAE+10|others>=1 [MKT] | OFF -> NEW | 13w mean 2,077 26w 897 $/wk
2025-12-22 | skip 2nd same-dir signal in same book within 30 min after a LOSER [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +1.5, 4w 25,963 13w -2,047 26w -204 $/wk
2025-12-22 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +1.4, 4w 65,943 13w -5,116 26w 14,167 $/wk
2025-12-22 | fs|P=50|win=60m|ref=stoppedEntry [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 11,228 13w 10,958 26w 5,974 $/wk
2025-12-29 | fs|P=50|oppBooks>=1 [S73] | FADING -> NEW | CUSUM 0.0 sig, z4 -0.6, 4w -6,370 13w 7,665 26w 2,753 $/wk
2025-12-29 | book PE x1.5 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 3,853 13w 7,940 26w 5,547 $/wk
2025-12-29 | book KB x1.5 [MKT] | OFF -> NEW | 13w mean 4,909 26w 1,685 $/wk
2025-12-29 | book WT x1.5 [S73] | STOPPED -> NEW | 13w mean 646 26w 696 $/wk
2025-12-29 | book WT x1.5 [MKT] | STABLE -> STOPPED | CUSUM 1.3 sig, z4 -0.2, 4w -3,376 13w -913 26w -1,220 $/wk
2025-12-29 | book WT x0.5 [MKT] | NEW -> FADING | CUSUM 0.6 sig, z4 +0.1, 4w 2,274 13w 185 26w 1,170 $/wk
2025-12-29 | fs|P=50|stoppedSession=london [MKT] | OFF -> NEW | 13w mean 4,753 26w 1,501 $/wk
2025-12-29 | session pre x0.5 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.2, 4w 20,515 13w 7,132 26w 5,802 $/wk
2025-12-29 | fs|P=50|stoppedSession!=asia [MKT] | OFF -> NEW | 13w mean 6,222 26w 1,909 $/wk
2025-12-29 | session asia first-60-min skip [MKT] | OFF -> NEW | 13w mean 5,333 26w 7,503 $/wk
2025-12-29 | skip first 60 min of every session [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +0.7, 4w 56,594 13w -2,168 26w 20,187 $/wk
2025-12-29 | cap|live=12|x2.35|mode=room|session=pre|count=both100 [S73] | NEW -> STOPPED | CUSUM 0.7 sig, z4 -0.4, 4w -1,348 13w -314 26w 945 $/wk
2025-12-29 | skip any signal within 30 min after a LOSER in any book [MKT] | OFF -> NEW | 13w mean 3,519 26w 136 $/wk
2025-12-29 | fs|P=25|stopdef=0 [MKT] | OFF -> NEW | 13w mean 1,119 26w 1,851 $/wk
2025-12-29 | fs|P=50|voltercile>=1 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 40,127 13w 30,035 26w 10,351 $/wk
2025-12-29 | fs|P=100|win=30m|ref=stoppedEntry [S73] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 12,981 13w 7,051 26w 1,947 $/wk
2025-12-29 | fs|P=50|stoppedSession=pre [S73] | NEW -> STABLE | CUSUM 0.3 sig, z4 +1.6, 4w 11,427 13w 3,576 26w 3,178 $/wk
2025-12-29 | fs|P=50|voltercile>=2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 21,557 13w 19,054 26w 7,983 $/wk
2025-12-29 | fs|P=50|win=5m|ref=stoppedEntry [S73] | NEW -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 7,138 13w 3,280 26w 638 $/wk
2026-01-05 | fs|P=50|voltercile>=2 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.6, 4w 17,945 13w 18,055 26w 8,795 $/wk
2026-01-05 | fs|P=50|voltercile<2 [MKT] | OFF -> NEW | 13w mean 13,002 26w 4,878 $/wk
2026-01-05 | fs|P=50|stoppedSession!=london [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 31,356 13w 25,987 26w 15,578 $/wk
2026-01-05 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | FADING -> NEW | CUSUM 0.0 sig, z4 +1.0, 4w 52,502 13w 10,172 26w 14,775 $/wk
2026-01-05 | fs|P=25|stoppedSession=asia [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w -4,131 13w 3,278 26w 5,740 $/wk
2026-01-05 | fs|P=50|er20_5m<0.2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 13,289 13w 13,074 26w 6,379 $/wk
2026-01-05 | book WT x0.5 [MKT] | FADING -> STABLE | CUSUM 1.0 sig, z4 -0.7, 4w -6,724 13w 1,156 26w 14 $/wk
2026-01-05 | fs|P=50|er20_5m<0.4 [S73] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 18,699 13w 14,656 26w -1,713 $/wk
2026-01-05 | fs|P=50|stoppedSession=nyam [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 5,721 13w 5,744 26w 2,954 $/wk
2026-01-05 | fs|P=50|er20_5m>=0.3 [S73] | OFF -> NEW | 13w mean 1,704 26w 2,601 $/wk
2026-01-05 | fs|P=50|voltercile<1 [MKT] | OFF -> NEW | 13w mean 948 26w 1,777 $/wk
2026-01-05 | fs|P=50|er20_5m<0.3 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 32,791 13w 29,014 26w 14,453 $/wk
2026-01-05 | book KB x1.5 [S73] | OFF -> NEW | 13w mean 726 26w 346 $/wk
2026-01-05 | fs|P=50|er20_5m>=0.4 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 12,016 13w 7,984 26w 5,038 $/wk
2026-01-05 | ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | OFF -> NEW | 13w mean 1,809 26w 356 $/wk
2026-01-05 | session london first-60-min skip [S73] | OFF -> NEW | 13w mean 3,076 26w 1,070 $/wk
2026-01-12 | ft|MAE+10|others>=1 [MKT] | NEW -> STOPPED | CUSUM 2.1 sig, z4 -0.5, 4w -16,568 13w -1,167 26w -3,316 $/wk
2026-01-12 | fs|P=50|er20_5m<0.3 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 6,673 13w 19,203 26w 13,861 $/wk
2026-01-12 | fs|P=50|stoppedSession=pre [S73] | STABLE -> FADING | CUSUM 1.1 sig, z4 -1.6, 4w -5,983 13w 2,454 26w 2,324 $/wk
2026-01-12 | fs|P=50|er20_5m>=0.4&voltercile>=2 [MKT] | NEW -> STABLE | CUSUM 0.6 sig, z4 -0.4, 4w -1,505 13w 3,965 26w 2,129 $/wk
2026-01-12 | fs|P=50|others<=3 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w 843 13w 15,275 26w 12,043 $/wk
2026-01-12 | fs|P=50|er20_5m>=0.4 [MKT] | RISING -> STABLE | CUSUM 0.3 sig, z4 +0.0, 4w 4,036 13w 6,932 26w 3,933 $/wk
2026-01-12 | fs|P=50|others<=2 [MKT] | NEW -> STABLE | CUSUM 0.2 sig, z4 -0.4, 4w -1,335 13w 7,141 26w 3,747 $/wk
2026-01-12 | session asia first-60-min skip [MKT] | NEW -> STOPPED | CUSUM 0.8 sig, z4 -0.3, 4w -18,994 13w -2,888 26w -5,003 $/wk
2026-01-12 | fs|P=50|win=20m|ref=stoppedEntry [MKT] | OFF -> NEW | 13w mean 1,521 26w 188 $/wk
2026-01-12 | book KB x1.5 [S73] | NEW -> STOPPED | CUSUM 0.6 sig, z4 -0.1, 4w -727 13w -1,117 26w 445 $/wk
2026-01-12 | fs|P=100|win=30m|ref=stoppedEntry [S73] | RISING -> STOPPED | CUSUM 0.6 sig, z4 -0.4, 4w -9,018 13w -7,359 26w -1,149 $/wk
2026-01-12 | fs|P=50|win=30m|ref=stoppedEntry [MKT] | RISING -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 3,925 13w 2,487 26w 7,120 $/wk
2026-01-12 | book SM x1.5 [S73] | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 5,187 13w 3,285 26w 6,809 $/wk
2026-01-12 | session pre OFF [S73] | NEW -> FADING | CUSUM 1.1 sig, z4 -0.6, 4w -5,330 13w 2,484 26w 5,905 $/wk
2026-01-12 | fs|P=25|stoppedSession=asia [MKT] | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.3, 4w 10,961 13w -1,761 26w 6,377 $/wk
2026-01-12 | book PE x1.5 [S73] | STABLE -> FADING | CUSUM 3.3 sig, z4 -1.5, 4w -12,240 13w 29 26w 2,233 $/wk
2026-01-12 | ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | NEW -> STOPPED | CUSUM 0.3 sig, z4 -0.0, 4w -5,457 13w -14,404 26w -5,197 $/wk
2026-01-12 | fs|P=50|win=60m|ref=stoppedEntry [MKT] | RISING -> STABLE | CUSUM 0.2 sig, z4 +0.4, 4w 16,705 13w 6,942 26w 9,029 $/wk
2026-01-12 | fs|P=50|asia&voltercile>=2 [S73] | STABLE -> STOPPED | CUSUM 0.8 sig, z4 -0.4, 4w -4,687 13w -8,338 26w 563 $/wk
2026-01-12 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 6,730 13w -952 26w 11,899 $/wk
2026-01-12 | fs|P=50|oppBooks>=1 [S73] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 14,009 13w 6,300 26w 2,962 $/wk
2026-01-12 | fs|P=50|voltercile>=1 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 17,259 13w 21,387 26w 11,589 $/wk
2026-01-12 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [S73] | NEW -> FADING | CUSUM 2.1 sig, z4 -1.8, 4w -9,259 13w 953 26w 2,450 $/wk
2026-01-12 | book WT x0.5 [MKT] | STABLE -> STOPPED | CUSUM 1.9 sig, z4 -1.5, 4w -14,245 13w -1,499 26w -378 $/wk
2026-01-12 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | NEW -> FADING | CUSUM 1.4 sig, z4 -1.5, 4w -12,808 13w 2,872 26w 4,709 $/wk
2026-01-12 | fs|P=25|stopdef=0 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +1.2, 4w 27,641 13w 2,502 26w 6,624 $/wk
2026-01-12 | book WT x1.5 [MKT] | OFF -> NEW | 13w mean 3,208 26w 2,436 $/wk
2026-01-12 | fs|P=50|stoppedSession!=london [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 12,643 13w 15,974 26w 15,835 $/wk
2026-01-12 | fs|P=50|er20_5m>=0.2 [MKT] | NEW -> RISING | CUSUM 0.4 sig, z4 +1.0, 4w 25,698 13w 11,363 26w 6,646 $/wk
2026-01-12 | cap|live=10|x2.35|mode=room|session=pre|count=openAll [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w -1,007 13w 4,665 26w 2,715 $/wk
2026-01-12 | fs|P=50|er20_5m<0.2 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 5,524 13w 7,415 26w 7,185 $/wk
2026-01-12 | cap|live=6|x2.35|mode=skip|session=pre|count=openAll [MKT] | NEW -> STABLE | CUSUM 0.5 sig, z4 -0.1, 4w 5,790 13w 10,855 26w 7,527 $/wk
2026-01-12 | fs|P=50|stoppedSession=nyam [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 8,224 13w 7,410 26w 3,978 $/wk
2026-01-19 | fs|P=50|er20_5m>=0.2 [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.2, 4w 31,875 13w 10,555 26w 9,012 $/wk
2026-01-19 | fs|P=50|stoppedSession=nyam [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 3,173 13w 8,036 26w 3,971 $/wk
2026-01-19 | fs|P=50|oppBooks>=1 [S73] | RISING -> FADING | CUSUM 0.4 sig, z4 +0.4, 4w 8,607 13w -68 26w 3,035 $/wk
2026-01-19 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.5, 4w 35,546 13w 14,418 26w 15,759 $/wk
2026-01-19 | ER gate: skip 5m ER20<0.2 [MKT] | OFF -> NEW | 13w mean 7,893 26w 7,782 $/wk
2026-01-19 | fs|P=50|voltercile>=1 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 37,497 13w 23,549 26w 14,703 $/wk
2026-01-19 | book KB x1.5 [S73] | STOPPED -> NEW | 13w mean 2,469 26w 3,143 $/wk
2026-01-19 | ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | STOPPED -> NEW | 13w mean 6,752 26w 2,651 $/wk
2026-01-19 | session pre OFF [S73] | FADING -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 17,633 13w 9,452 26w 7,379 $/wk
2026-01-19 | fs|P=50|er20_5m<0.4 [S73] | RISING -> FADING | CUSUM 0.0 sig, z4 +0.8, 4w 15,671 13w -2,411 26w -767 $/wk
2026-01-19 | fs|P=50|others<=2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 23,121 13w 14,580 26w 6,419 $/wk
2026-01-19 | fs|P=50|voltercile<1 [MKT] | NEW -> FADING | CUSUM 0.0 sig, z4 +1.5, 4w 23,467 13w -65 26w 2,724 $/wk
2026-01-19 | ft|MAE+10|others>=1 [MKT] | STOPPED -> NEW | 13w mean 1,585 26w 2,427 $/wk
2026-01-19 | fs|P=75|stopdef=0 [S73] | OFF -> NEW | 13w mean 15,381 26w 3,914 $/wk
2026-01-19 | fs|P=50|stoppedSession=pre [S73] | FADING -> STABLE | CUSUM 0.7 sig, z4 -1.0, 4w -3,060 13w 3,683 26w 2,008 $/wk
2026-01-19 | fs|P=50|win=60m|ref=stoppedEntry [MKT] | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.5, 4w 21,942 13w 5,572 26w 11,791 $/wk
2026-01-19 | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | FADING -> STABLE | CUSUM 1.0 sig, z4 -1.0, 4w -7,375 13w 3,166 26w 4,034 $/wk
2026-01-19 | skip 2nd same-dir signal in same book within 30 min after a LOSER [MKT] | FADING -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 31,139 13w 7,059 26w 3,584 $/wk
2026-01-19 | fs|P=50|voltercile>=2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 26,495 13w 16,249 26w 12,504 $/wk
2026-01-19 | fs|P=50|er20_5m>=0.4&voltercile>=2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 10,675 13w 7,712 26w 4,003 $/wk
2026-01-19 | fs|P=50|stoppedSession=asia [S73] | STABLE -> FADING | CUSUM 0.0 sig, z4 +1.2, 4w 34,471 13w 2,288 26w 9,778 $/wk
2026-01-19 | skip first 60 min of every session [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.1, 4w 65,077 13w 8,446 26w 8,813 $/wk
2026-01-19 | fs|P=50|win=5m|ref=stoppedEntry [S73] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w -3,436 13w 1,139 26w 109 $/wk
2026-01-26 | book KB x1.5 [MKT] | NEW -> RISING | CUSUM 0.8 sig, z4 +0.4, 4w 7,882 13w 6,177 26w 3,941 $/wk
2026-01-26 | book WT x1.5 [S73] | NEW -> STABLE | CUSUM 1.5 sig, z4 +0.9, 4w 12,682 13w 2,035 26w 3,398 $/wk
2026-01-26 | skip any signal within 30 min after a LOSER in any book [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 33,724 13w 10,933 26w 7,084 $/wk
2026-01-26 | fs|P=25|stopdef=0 [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.9, 4w 43,625 13w 6,205 26w 9,868 $/wk
2026-01-26 | session close OFF [MKT] | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 0 26w 83 $/wk
2026-01-26 | skip first 60 min of every session [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 65,072 13w 31,236 26w 18,723 $/wk
2026-01-26 | book HM x0.5 [MKT] | OFF -> NEW | 13w mean 7,685 26w 408 $/wk
2026-01-26 | book SM x1.5 [S73] | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 6,095 13w 3,232 26w 5,413 $/wk
2026-01-26 | book PE x1.5 [S73] | FADING -> STOPPED | CUSUM 2.6 sig, z4 -2.2, 4w -19,108 13w -1,057 26w 2,255 $/wk
2026-01-26 | fs|P=50|voltercile<1 [MKT] | FADING -> NEW | CUSUM 0.0 sig, z4 +1.4, 4w 23,171 13w 4,294 26w 3,763 $/wk
2026-01-26 | session asia first-60-min skip [MKT] | OFF -> NEW | 13w mean 19,307 26w 7,968 $/wk
2026-01-26 | session london x0.5 [MKT] | OFF -> NEW | 13w mean 3,499 26w 178 $/wk
2026-01-26 | ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.7, 4w 87,078 13w 45,874 26w 22,789 $/wk
2026-01-26 | fs|P=50|win=10m|ref=stoppedEntry [MKT] | OFF -> NEW | 13w mean 4,046 26w 1,680 $/wk
2026-01-26 | fs|P=50|win=60m|ref=stackFirstEntry [MKT] | OFF -> NEW | 13w mean 148 26w 3,846 $/wk
2026-01-26 | fs|P=50|others<=3 [S73] | OFF -> NEW | 13w mean 10,394 26w 3,743 $/wk
2026-01-26 | fs|P=50|others<=3 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 40,869 13w 25,356 26w 18,321 $/wk
2026-01-26 | ft|stackBE|others>=2 [MKT] | OFF -> NEW | 13w mean 10,922 26w 2,679 $/wk
2026-01-26 | fs|P=50|stoppedSession!=asia [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 10,590 13w 10,212 26w 4,791 $/wk
2026-01-26 | fs|P=50|stoppedSession=london [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 13,800 13w 7,268 26w 4,796 $/wk
2026-01-26 | fs|P=50|er20_5m<0.4 [S73] | FADING -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 27,860 13w 6,827 26w 2,946 $/wk
2026-01-26 | book PE x1.5 [MKT] | STABLE -> FADING | CUSUM 0.6 sig, z4 -1.3, 4w -9,320 13w 767 26w 4,499 $/wk
2026-01-26 | fs|P=50|er20_5m>=0.2 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 37,034 13w 19,328 26w 11,982 $/wk
2026-01-26 | fs|P=50|oppBooks>=1 [S73] | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.9, 4w 17,215 13w 3,150 26w 4,634 $/wk
2026-01-26 | fs|P=50|win=10m|ref=stackFirstEntry [MKT] | OFF -> NEW | 13w mean 2,859 26w 97 $/wk
2026-01-26 | fs|P=50|stoppedSession=asia [S73] | FADING -> STABLE | CUSUM 0.0 sig, z4 +2.1, 4w 53,839 13w 9,779 26w 12,323 $/wk
2026-01-26 | fs|P=100|win=30m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 5,753 26w 7,789 $/wk
2026-01-26 | fs|P=50|asia&voltercile>=2 [S73] | OFF -> NEW | 13w mean 1,636 26w 4,783 $/wk
2026-01-26 | session pre OFF [S73] | RISING -> STABLE | CUSUM 0.5 sig, z4 -0.1, 4w 3,001 13w 10,789 26w 5,977 $/wk
2026-01-26 | fs|P=50|win=30m|ref=stoppedEntry [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.2, 4w 30,271 13w 8,479 26w 11,715 $/wk
2026-01-26 | skip first 30 min of every session [S73] | OFF -> NEW | 13w mean 3,046 26w 2,795 $/wk
2026-01-26 | fs|P=50|win=60m|ref=stoppedEntry [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.9, 4w 33,441 13w 12,982 26w 16,254 $/wk
2026-02-02 | fs|P=50|stoppedSession=london [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 3,623 13w 9,656 26w 5,574 $/wk
2026-02-02 | fs|P=50|stoppedSession!=london [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 61,342 13w 32,023 26w 24,407 $/wk
2026-02-02 | fs|P=50|voltercile<2 [MKT] | NEW -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 36,825 13w 21,562 26w 11,690 $/wk
2026-02-02 | fs|P=50|er20_5m<0.2 [MKT] | STABLE -> RISING | CUSUM 0.4 sig, z4 +1.0, 4w 23,305 13w 12,729 26w 9,124 $/wk
2026-02-02 | session close OFF [MKT] | STOPPED -> NEW | 13w mean 959 26w 562 $/wk
2026-02-02 | book KB x1.5 [MKT] | RISING -> FADING | CUSUM 2.4 sig, z4 -1.1, 4w -7,526 13w 4,037 26w 3,244 $/wk
2026-02-02 | book KB x1.5 [S73] | NEW -> STOPPED | CUSUM 3.4 sig, z4 -1.2, 4w -13,906 13w -3,765 26w -709 $/wk
2026-02-02 | fs|P=25|stopdef=0 [MKT] | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 40,305 13w 15,385 26w 11,441 $/wk
2026-02-02 | fs|P=50|er20_5m>=0.3 [S73] | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 10,394 13w 10,528 26w 2,772 $/wk
2026-02-02 | fs|P=50|voltercile<1 [MKT] | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 698 13w 4,508 26w 4,173 $/wk
2026-02-02 | fs|P=50|stoppedSession!=asia [MKT] | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 6,876 13w 11,381 26w 5,714 $/wk
2026-02-02 | fs|P=50|win=30m|ref=stackFirstEntry [MKT] | OFF -> NEW | 13w mean 7,863 26w 195 $/wk
2026-02-02 | fs|P=25|win=10m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 6,082 26w 1,204 $/wk
2026-02-02 | fs|P=50|win=5m|ref=stoppedEntry [S73] | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 4,862 13w 3,740 26w 1,020 $/wk
2026-02-02 | fs|P=25|win=30m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 743 26w 2,985 $/wk
2026-02-02 | fs|P=50|stoppedSession=asia [S73] | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.1, 4w 54,649 13w 17,117 26w 13,611 $/wk
2026-02-02 | fs|P=50|win=60m|ref=stoppedEntry [S73] | OFF -> NEW | 13w mean 4,270 26w 4,031 $/wk
2026-02-02 | fs|P=50|win=60m|ref=stackFirstEntry [S73] | OFF -> NEW | 13w mean 8,726 26w 870 $/wk
2026-02-02 | session nypm OFF [MKT] | OFF -> NEW | 13w mean 16,186 26w 3,933 $/wk
2026-02-02 | session london first-60-min skip [S73] | NEW -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 26,724 13w 17,185 26w 4,626 $/wk
2026-02-02 | book SM x1.5 [S73] | STABLE -> FADING | CUSUM 0.6 sig, z4 -1.0, 4w -4,126 13w 1,211 26w 4,228 $/wk
2026-02-02 | fs|P=25|stoppedSession=asia [MKT] | FADING -> STABLE | CUSUM 0.0 sig, z4 +2.2, 4w 47,056 13w 11,036 26w 11,879 $/wk
2026-02-02 | book PE x1.5 [MKT] | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.6, 4w -1,196 13w -650 26w 5,380 $/wk

## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)
- 2026-10-31 | STACK-2 "fs|P=50|stopdef=0" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier CANDIDATE-RECENT, $ live 15,211
- 2026-10-31 | STACK-2 "fs|P=50|stopdef=0" (STACK (6 books)) | NEW? -> NEW | L3M primary nan, tier CANDIDATE-RECENT, $ live 6,809
- 2026-10-31 | STACK-2 "fs|P=50|others<=2" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier LEAD, $ live 9,508
- 2026-10-31 | STACK-2 "fs|P=50|stoppedSession=asia" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 7,431
- 2026-10-31 | STACK-2 "fs|P=50|voltercile>=2" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier LEAD, $ live 6,957
- 2026-10-31 | STACK-2 "fs|P=100|stoppedSession=asia" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier LEAD, $ live 6,356
- 2026-10-31 | STACK-2 "fs|P=50|stoppedSession=asia" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier LEAD, $ live 5,053
- 2026-10-31 | STACK-2 "fs|P=100|stoppedSession=asia" (STACK (6 books)) | NEW? -> RISING | L3M primary nan, tier LEAD, $ live 4,703
- 2026-10-31 | STACK-2 "fs|P=50|asia&voltercile>=2" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 4,173
- 2026-10-31 | STACK-2 "fs|P=50|er20_5m>=0.4" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 3,393
- 2026-10-31 | STACK-2 "fs|P=50|asia&voltercile>=2" (STACK (6 books)) | NEW? -> NEW | L3M primary nan, tier LEAD, $ live 2,355
- 2026-10-31 | STACK-2 "cap|live=10|x2.35|mode=skip|session=pre|count=openAll" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 2,354
- 2026-10-31 | STACK-2 "cap|live=8|x2.35|mode=skip|session=pre|count=openAll" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 1,924
- 2026-10-31 | STACK-2 "fs|P=50|asia&er20_5m>=0.4" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 1,471
- 2026-10-31 | STACK-2 "fs|P=50|oppBooks>=1" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 1,388
- 2026-10-31 | STACK-2 "cap|live=8|x2.35|mode=skip|session=pre|count=both100" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 885
- 2026-10-31 | STACK-2 "fs|P=50|asia&er20_5m>=0.4" (STACK (6 books)) | NEW? -> NEW | L3M primary nan, tier LEAD, $ live 751
- 2026-10-31 | STACK-2 "cap|live=8|x2.35|mode=skip|session=pre|count=openAll" (STACK (6 books)) | NEW? -> FADING | L3M primary nan, tier LEAD, $ live 559
- 2026-10-31 | STACK-2 "cap|live=8|x2.35|mode=skip|session=pre|count=70only" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 457
- 2026-10-31 | STACK-2 "cap|live=6|x2.35|mode=skip|session=pre|count=70only" (STACK (6 books)) | NEW? -> STABLE | L3M primary nan, tier LEAD, $ live 396

## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)

