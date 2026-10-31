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


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)


## RE-6 monitor run 2026-10-31T16:13Z (data to 2026-02-06; rows scored after the RE-2 run: NTE-2 / GOV-1 / GOV-2; units $/wk live lots on the D6-faithful composite; edge cluster representatives only, last 13 data weeks; full log out/recentedge6/monitor6_log_last13w.csv)
2025-11-10 | C|3|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 380 26w 245 $/wk
2025-11-10 | D|673|x1.5 | NEW -> FADING | CUSUM 1.0 sig, z4 +0.6, 4w 914 13w 89 26w 309 $/wk
2025-11-10 | C|723|x0.5 | STOPPED -> NEW | 13w mean 6 26w 89 $/wk
2025-11-10 | C|192|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.6, 4w 384 13w 551 26w 1,412 $/wk
2025-11-10 | D|657|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 613 13w 381 26w 237 $/wk
2025-11-10 | D|656|x1.5 | NEW -> STOPPED | CUSUM 3.3 sig, z4 -1.7, 4w -2,102 13w -730 26w -129 $/wk
2025-11-10 | C|746|skip | NEW -> STOPPED | CUSUM 1.5 sig, z4 -0.5, 4w -804 13w -173 26w -268 $/wk
2025-11-10 | D|655|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.2, 4w 193 13w -146 26w -21 $/wk
2025-11-10 | D|588|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 61 13w 250 26w 455 $/wk
2025-11-10 | C|751|skip | NEW -> STOPPED | CUSUM 2.4 sig, z4 -1.0, 4w -3,100 13w -704 26w -455 $/wk
2025-11-10 | C|195|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -38 13w -12 26w 42 $/wk
2025-11-10 | C|72|skip | OFF -> NEW | 13w mean 2,218 26w 573 $/wk
2025-11-10 | C|68|x0.5 | OFF -> NEW | 13w mean 54 26w 175 $/wk
2025-11-10 | D|463|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 2,151 13w 1,984 26w 3,928 $/wk
2025-11-10 | C|872|x0.5 | STABLE -> FADING | CUSUM 2.0 sig, z4 -1.3, 4w -299 13w 1 26w 12 $/wk
2025-11-10 | D|457|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 3,557 13w 1,542 26w 717 $/wk
2025-11-10 | D|451|x1.5 | STOPPED -> NEW | 13w mean 1,198 26w 879 $/wk
2025-11-10 | C|885|x0.5 | FADING -> STABLE | CUSUM 1.6 sig, z4 -1.3, 4w -598 13w 171 26w 1 $/wk
2025-11-10 | D|434|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w -1,088 13w 1,750 26w 2,045 $/wk
2025-11-10 | C|762|skip | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.9, 4w -1,098 13w -218 26w 108 $/wk
2025-11-10 | C|31|x0.5 | STOPPED -> NEW | 13w mean 260 26w 633 $/wk
2025-11-10 | D|677|x1.5 | RISING -> STABLE | CUSUM 0.9 sig, z4 -0.2, 4w -1 13w 483 26w 140 $/wk
2025-11-10 | D|712|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 688 13w 377 26w 828 $/wk
2025-11-10 | C|368|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 3,897 13w -547 26w 1,886 $/wk
2025-11-10 | C|243|x0.5 | STABLE -> FADING | CUSUM 1.7 sig, z4 -1.8, 4w -383 13w 202 26w 101 $/wk
2025-11-10 | D|705|x1.5 | NEW -> STOPPED | CUSUM 2.9 sig, z4 -0.3, 4w -657 13w -7 26w -233 $/wk
2025-11-10 | C|467|skip | STOPPED -> NEW | 13w mean 135 26w 273 $/wk
2025-11-10 | C|243|skip | STABLE -> FADING | CUSUM 2.2 sig, z4 -2.3, 4w -1,552 13w 657 26w 329 $/wk
2025-11-10 | C|478|skip | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w -99 26w 173 $/wk
2025-11-10 | HR|book|AND:z20_1.5:map_vol|ses|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2025-11-10 | C|237|x0.5 | OFF -> NEW | 13w mean 274 26w 88 $/wk
2025-11-10 | C|499|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 1,145 13w -970 26w 592 $/wk
2025-11-10 | D|694|x1.5 | STABLE -> FADING | CUSUM 1.1 sig, z4 +0.6, 4w 1,473 13w -11 26w 290 $/wk
2025-11-10 | C|501|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 631 13w 201 26w -3 $/wk
2025-11-10 | C|506|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 650 13w -47 26w -169 $/wk
2025-11-10 | HR|book|L:sh2:0.65|mem|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w -0 $/wk
2025-11-10 | HR|book|AND:streak4:map_vol|day|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 0 13w 0 26w -280 $/wk
2025-11-10 | D|686|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.9, 4w 5,891 13w 1,617 26w 1,289 $/wk
2025-11-10 | D|697|x1.5 | STOPPED -> NEW | 13w mean 575 26w 388 $/wk
2025-11-10 | D|431|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 3,863 13w 5,493 26w 3,852 $/wk
2025-11-10 | D|560|take | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -448 13w -1,199 26w 63 $/wk
2025-11-10 | L|H6|M|ls|6|q10|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -133 13w 528 26w 406 $/wk
2025-11-10 | L|K6|M|ls|6|q30|x0.5 | OFF -> NEW | 13w mean 66 26w 107 $/wk
2025-11-10 | L|K6|M|fs|1|q10|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 287 26w 5 $/wk
2025-11-10 | C|18|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 571 26w 285 $/wk
2025-11-10 | D|318|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 1,979 13w 2,420 26w 587 $/wk
2025-11-10 | C|16|skip | STOPPED -> NEW | 13w mean 636 26w 686 $/wk
2025-11-10 | C|15|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 285 26w 142 $/wk
2025-11-10 | D|150|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 6,747 13w 9,893 26w 7,536 $/wk
2025-11-10 | L|P6|M|ls|5|q10|skip | STOPPED -> NEW | 13w mean 2,361 26w 2,060 $/wk
2025-11-10 | C|20|skip | OFF -> NEW | 13w mean 524 26w 17 $/wk
2025-11-10 | C|14|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 597 13w 1,334 26w 748 $/wk
2025-11-10 | L|M6|M|ls|1|q10|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w -0 26w 0 $/wk
2025-11-10 | GOV2|ew3|cNone | OFF -> NEW | 13w mean 654 26w 1,638 $/wk
2025-11-10 | L|M6|M|ls|5|q10|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.9, 4w -614 13w 1,284 26w 667 $/wk
2025-11-10 | D|255|x1.5 | STOPPED -> NEW | 13w mean 88 26w 487 $/wk
2025-11-10 | D|162|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 13,492 13w 11,190 26w 8,268 $/wk
2025-11-10 | C|357|skip | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.9, 4w -4,302 13w -983 26w -123 $/wk
2025-11-10 | C|30|x0.5 | FADING -> STOPPED | CUSUM 1.8 sig, z4 -0.6, 4w -1,984 13w -479 26w 523 $/wk
2025-11-10 | D|88|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 671 13w 667 26w 322 $/wk
2025-11-10 | C|21|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 279 26w 140 $/wk
2025-11-10 | C|21|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 92 26w 46 $/wk
2025-11-10 | L|A6|M|real|0|q30|skip | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.4, 4w -299 13w -7 26w 223 $/wk
2025-11-10 | L|A6|M|fs|3|q30|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 58 13w 232 26w 34 $/wk
2025-11-10 | D|402|x1.5 | STABLE -> STOPPED | CUSUM 2.1 sig, z4 -0.7, 4w -1,779 13w -232 26w 307 $/wk
2025-11-10 | C|28|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 0 13w 1,424 26w 804 $/wk
2025-11-17 | HR|book|AND:rs10_3:map_vol|mem|0 | OFF -> NEW | 13w mean 254 26w 175 $/wk
2025-11-17 | C|878|skip | OFF -> NEW | 13w mean 15 26w 70 $/wk
2025-11-17 | GOV2|ew3|cNone | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 6,711 13w 250 26w 1,028 $/wk
2025-11-17 | D|701|x1.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.0, 4w 888 13w 1,110 26w 918 $/wk
2025-11-17 | HR|book|AND:wk2_3:map_vol|ses|0 | OFF -> NEW | 13w mean 368 26w 138 $/wk
2025-11-17 | D|460|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w -1,325 13w 1,130 26w 1,860 $/wk
2025-11-17 | D|106|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w -22 13w 753 26w 11 $/wk
2025-11-17 | D|434|x1.5 | STABLE -> FADING | CUSUM 0.5 sig, z4 -0.6, 4w -2,251 13w 585 26w 1,416 $/wk
2025-11-17 | D|279|take | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.5, 4w 3,099 13w 813 26w 1,368 $/wk
2025-11-17 | D|708|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 920 13w 764 26w 180 $/wk
2025-11-17 | D|712|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 1,600 13w 659 26w 734 $/wk
2025-11-17 | C|360|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 1,232 13w 785 26w 1,175 $/wk
2025-11-17 | D|162|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 8,737 13w 9,096 26w 8,200 $/wk
2025-11-17 | C|501|x0.5 | RISING -> STOPPED | CUSUM 0.5 sig, z4 -0.0, 4w -214 13w -56 26w -178 $/wk
2025-11-17 | D|410|x1.5 | FADING -> STOPPED | CUSUM 0.8 sig, z4 -0.7, 4w -1,366 13w -420 26w 676 $/wk
2025-11-17 | D|655|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.1, 4w 193 13w 44 26w 56 $/wk
2025-11-17 | D|657|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 311 13w 287 26w 237 $/wk
2025-11-17 | D|663|x1.5 | STABLE -> STOPPED | CUSUM 1.5 sig, z4 -1.1, 4w -1,530 13w -183 26w 45 $/wk
2025-11-17 | D|402|x1.5 | STOPPED -> NEW | 13w mean 929 26w 638 $/wk
2025-11-17 | C|723|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.2, 4w 334 13w 13 26w 140 $/wk
2025-11-17 | C|723|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.6, 4w -276 13w 295 26w 657 $/wk
2025-11-17 | D|667|x1.5 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 603 13w 571 26w 260 $/wk
2025-11-17 | D|668|x1.5 | FADING -> STOPPED | CUSUM 3.7 sig, z4 -2.2, 4w -3,380 13w -178 26w -428 $/wk
2025-11-17 | D|130|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,509 13w 1,212 26w 618 $/wk
2025-11-17 | D|421|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 229 26w 554 $/wk
2025-11-17 | D|88|x1.5 | RISING -> STABLE | CUSUM 0.2 sig, z4 -0.2, 4w -510 13w 589 26w 94 $/wk
2025-11-17 | D|715|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 894 13w 738 26w 496 $/wk
2025-11-17 | D|547|x1.5 | STABLE -> FADING | CUSUM 0.5 sig, z4 -1.7, 4w -620 13w 748 26w 713 $/wk
2025-11-17 | D|466|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 155 13w 630 26w 714 $/wk
2025-11-17 | D|694|x1.5 | FADING -> RISING | CUSUM 0.0 sig, z4 +1.9, 4w 4,526 13w 646 26w 497 $/wk
2025-11-17 | HR|book|AND:z20_1.5:map_dow|day|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 9 26w 5 $/wk
2025-11-17 | C|21|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 926 13w 377 26w 189 $/wk
2025-11-17 | L|A6|M|fs|3|q30|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 356 13w 232 26w 34 $/wk
2025-11-17 | C|30|x0.5 | STOPPED -> NEW | 13w mean 832 26w 707 $/wk
2025-11-17 | L|A6|M|fs|1|q30|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 267 26w 130 $/wk
2025-11-17 | L|A6|M|ls|6|q20|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.4, 4w -299 13w -84 26w -42 $/wk
2025-11-17 | C|227|x0.5 | OFF -> NEW | 13w mean 8 26w 4 $/wk
2025-11-17 | D|819|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 1,262 13w 1,155 26w 807 $/wk
2025-11-17 | L|POOL6|Q|ls|3|q20|skip | OFF -> NEW | 13w mean 118 26w 296 $/wk
2025-11-17 | HR|book|AND:rs10_3:map_vol|ses|0 | OFF -> NEW | 13w mean 178 26w 138 $/wk
2025-11-17 | D|974|x1.5 | OFF -> NEW | 13w mean 408 26w 204 $/wk
2025-11-17 | C|223|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w -0 26w 24 $/wk
2025-11-17 | C|52|x0.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.2, 4w 831 13w 337 26w 408 $/wk
2025-11-17 | C|196|skip | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.4, 4w -160 13w -48 26w 243 $/wk
2025-11-17 | L|U6|M|ls|6|q30|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,410 13w 259 26w 469 $/wk
2025-11-17 | C|195|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 1,166 13w 699 26w 539 $/wk
2025-11-17 | L|U6|M|fs|3|q10|x0.5 | OFF -> NEW | 13w mean 95 26w 47 $/wk
2025-11-17 | C|190|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 0 13w 236 26w 118 $/wk
2025-11-17 | C|21|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 917 13w 561 26w 281 $/wk
2025-11-17 | L|U6|M|fs|3|q30|x0.5 | OFF -> NEW | 13w mean 382 26w 233 $/wk
2025-11-17 | C|68|x0.5 | NEW -> STOPPED | CUSUM 2.0 sig, z4 -0.4, 4w -1,358 13w -942 26w -323 $/wk
2025-11-17 | D|716|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +2.2, 4w 4,134 13w 1,142 26w 952 $/wk
2025-11-17 | C|195|x0.5 | STOPPED -> NEW | 13w mean 83 26w 89 $/wk
2025-11-17 | C|241|x0.5 | RISING -> STABLE | CUSUM 0.7 sig, z4 -0.6, 4w -353 13w 242 26w 119 $/wk
2025-11-17 | C|5|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -185 13w 580 26w 123 $/wk
2025-11-17 | L|H6|M|ls|5|q20|x0.5 | OFF -> NEW | 13w mean 561 26w 261 $/wk
2025-11-17 | L|M6|M|ls|4|q30|x0.5 | NEW -> STOPPED | CUSUM 0.2 sig, z4 -0.2, 4w -228 13w -39 26w -42 $/wk
2025-11-17 | D|718|x1.5 | FADING -> STABLE | CUSUM 0.9 sig, z4 -1.3, 4w -1,065 13w 1,321 26w 1,349 $/wk
2025-11-17 | L|P6|M|ls|6|q20|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 4,713 13w 8,232 26w 2,714 $/wk
2025-11-17 | C|8|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 7,421 13w 4,377 26w 2,188 $/wk
2025-11-17 | HR|book|AND:z20_1.5:map_vol|w2|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2025-11-17 | L|U6|M|fs|3|q20|x0.5 | OFF -> NEW | 13w mean 95 26w 275 $/wk
2025-11-17 | C|20|skip | NEW -> STOPPED | CUSUM 4.2 sig, z4 -0.6, 4w -677 13w -64 26w -229 $/wk
2025-11-24 | D|466|x1.5 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -31 13w -477 26w 664 $/wk
2025-11-24 | D|172|x1.5 | RISING -> STABLE | CUSUM 0.9 sig, z4 +0.1, 4w 14,970 13w 17,350 26w 13,027 $/wk
2025-11-24 | L|P6|M|ls|6|q20|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 12,346 13w 7,747 26w 3,416 $/wk
2025-11-24 | D|585|take | FADING -> STOPPED | CUSUM 0.7 sig, z4 -0.5, 4w -1,019 13w -485 26w 608 $/wk
2025-11-24 | L|M6|M|ls|3|q10|x0.5 | OFF -> NEW | 13w mean 25 26w 12 $/wk
2025-11-24 | D|588|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 900 13w -33 26w 456 $/wk
2025-11-24 | C|190|skip | OFF -> NEW | 13w mean 75 26w 1 $/wk
2025-11-24 | GOV2|ew3|cNone | FADING -> NEW | CUSUM 0.0 sig, z4 +0.8, 4w 15,030 13w 3,306 26w 3,226 $/wk
2025-11-24 | C|735|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 935 13w 572 26w 4 $/wk
2025-11-24 | D|660|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +1.7, 4w 2,825 13w 702 26w 633 $/wk
2025-11-24 | C|190|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.0, 4w 857 13w 500 26w 250 $/wk
2025-11-24 | D|663|x1.5 | STOPPED -> NEW | 13w mean 11 26w 327 $/wk
2025-11-24 | L|K6|M|real|0|q30|skip | OFF -> NEW | 13w mean 61 26w 488 $/wk
2025-11-24 | D|334|x1.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.4, 4w 2,150 13w 6,493 26w 3,432 $/wk
2025-11-24 | D|460|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.4, 4w -1,187 13w 30 26w 1,354 $/wk
2025-11-24 | C|872|x0.5 | FADING -> STOPPED | CUSUM 1.1 sig, z4 -1.3, 4w -299 13w -92 26w 12 $/wk
2025-11-24 | D|108|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 6,777 13w 11,968 26w 6,310 $/wk
2025-11-24 | D|134|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -1.0, 4w -2,006 13w 276 26w 697 $/wk
2025-11-24 | D|413|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 282 13w -470 26w 524 $/wk
2025-11-24 | D|319|x1.5 | STABLE -> FADING | CUSUM 0.7 sig, z4 -1.6, 4w -4,084 13w 2,552 26w 1,763 $/wk
2025-11-24 | C|31|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 772 13w 192 26w 478 $/wk
2025-11-24 | C|723|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w -276 13w 295 26w 445 $/wk
2025-11-24 | D|434|x1.5 | FADING -> STOPPED | CUSUM 0.1 sig, z4 -1.0, 4w -4,119 13w -450 26w 1,410 $/wk
2025-11-24 | HR|book|AND:z20_1.5:map_vol|w2|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 962 13w 296 26w 148 $/wk
2025-11-24 | D|436|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w -0 26w 486 $/wk
2025-11-24 | C|47|x0.5 | OFF -> NEW | 13w mean 382 26w 14 $/wk
2025-11-24 | D|449|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w -87 26w 572 $/wk
2025-11-24 | C|878|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 308 13w 15 26w 156 $/wk
2025-11-24 | L|POOL6|Q|ls|3|q10|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 445 13w 422 26w 211 $/wk
2025-11-24 | D|451|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 2,319 13w 653 26w 1,690 $/wk
2025-11-24 | D|290|take | OFF -> NEW | 13w mean 1,080 26w 458 $/wk
2025-11-24 | C|874|x0.5 | STABLE -> STOPPED | CUSUM 0.3 sig, z4 -1.1, 4w -299 13w -18 26w 96 $/wk
2025-11-24 | D|106|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 4,055 13w 2,287 26w 778 $/wk
2025-11-24 | D|402|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.7, 4w -1,464 13w 68 26w 640 $/wk
2025-11-24 | C|52|x0.5 | NEW -> STABLE | CUSUM 0.2 sig, z4 -0.3, 4w -392 13w 766 26w 290 $/wk
2025-11-24 | D|290|x1.5 | NEW -> STABLE | CUSUM 0.5 sig, z4 -0.4, 4w -55 13w 822 26w 427 $/wk
2025-11-24 | D|716|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +3.1, 4w 5,795 13w 1,668 26w 1,263 $/wk
2025-11-24 | L|U6|M|ls|6|q30|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,858 13w 259 26w -407 $/wk
2025-11-24 | C|243|x0.5 | FADING -> STABLE | CUSUM 0.8 sig, z4 -0.7, 4w -78 13w 202 26w 101 $/wk
2025-11-24 | HR|book|rs5_5|ses|2 | OFF -> NEW | 13w mean 1,873 26w 194 $/wk
2025-11-24 | D|694|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.7, 4w 4,677 13w 1,083 26w 938 $/wk
2025-11-24 | HR|book|L:sh1:0.65|mem|0 | OFF -> NEW | 13w mean 285 26w 119 $/wk
2025-11-24 | D|682|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w -242 13w 19 26w 271 $/wk
2025-11-24 | C|243|skip | FADING -> STABLE | CUSUM 1.4 sig, z4 -0.8, 4w -329 13w 562 26w 282 $/wk
2025-11-24 | C|241|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 1,710 13w 769 26w 382 $/wk
2025-11-24 | C|509|skip | FADING -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 620 13w 385 26w 291 $/wk
2025-11-24 | D|686|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +3.2, 4w 9,707 13w 2,057 26w 1,721 $/wk
2025-11-24 | C|478|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 4 13w 88 26w 172 $/wk
2025-11-24 | D|692|x1.5 | STABLE -> STOPPED | CUSUM 0.3 sig, z4 -0.8, 4w -1,057 13w -244 26w 329 $/wk
2025-11-24 | C|241|skip | OFF -> NEW | 13w mean 351 26w 110 $/wk
2025-11-24 | C|504|x0.5 | STABLE -> FADING | CUSUM 1.5 sig, z4 -1.3, 4w -903 13w 32 26w 265 $/wk
2025-11-24 | D|677|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 610 13w 483 26w 276 $/wk
2025-11-24 | D|673|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +1.4, 4w 1,826 13w 182 26w 349 $/wk
2025-11-24 | D|676|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +2.5, 4w 4,650 13w 1,612 26w 808 $/wk
2025-11-24 | C|360|x0.5 | OFF -> NEW | 13w mean 106 26w 259 $/wk
2025-11-24 | D|713|x1.5 | OFF -> NEW | 13w mean 31 26w 386 $/wk
2025-12-01 | L|M6|M|ls|1|q10|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.0, 4w -0 13w -0 26w 0 $/wk
2025-12-01 | L|K6|M|real|0|q20|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.9, 4w 1,956 13w 262 26w 588 $/wk
2025-12-01 | L|H6|M|ls|1|q30|x0.5 | OFF -> NEW | 13w mean 292 26w 76 $/wk
2025-12-01 | HR|book|z10_2.0|w3|0 | OFF -> NEW | 13w mean 1,405 26w 4 $/wk
2025-12-01 | L|K6|M|real|0|q30|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.8, 4w 2,532 13w -79 26w 796 $/wk
2025-12-01 | C|467|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +1.1, 4w 2,554 13w 56 26w 176 $/wk
2025-12-01 | HR|book|rs5_5|p5|0 | OFF -> NEW | 13w mean 2,074 26w 285 $/wk
2025-12-01 | D|713|x1.5 | NEW -> FADING | CUSUM 0.2 sig, z4 +0.6, 4w 1,126 13w -184 26w 369 $/wk
2025-12-01 | D|402|x1.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.9, 4w -1,796 13w -71 26w 640 $/wk
2025-12-01 | D|403|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 304 13w 300 26w -483 $/wk
2025-12-01 | D|88|x1.5 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.4, 4w -1,181 13w -14 26w 94 $/wk
2025-12-01 | D|695|x1.5 | NEW -> STABLE | CUSUM 0.8 sig, z4 -0.7, 4w -912 13w 1,794 26w 293 $/wk
2025-12-01 | C|499|skip | FADING -> STOPPED | CUSUM 0.4 sig, z4 -0.6, 4w -2,354 13w -763 26w -83 $/wk
2025-12-01 | HR|book|AND:wk2_3:reg_ci_60|day|0 | FADING -> STABLE | CUSUM 0.0 sig, z4 +2.1, 4w 1,222 13w 376 26w 377 $/wk
2025-12-01 | D|421|x1.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.2, 4w -0 13w -1 26w 321 $/wk
2025-12-01 | D|279|take | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.0, 4w 1,319 13w -174 26w 1,203 $/wk
2025-12-01 | L|K6|M|ls|6|q20|skip | OFF -> NEW | 13w mean 65 26w 309 $/wk
2025-12-01 | L|P6|M|ls|6|q20|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 5,841 13w 6,055 26w 2,878 $/wk
2025-12-01 | D|711|x1.5 | STABLE -> STOPPED | CUSUM 2.0 sig, z4 -1.3, 4w -1,435 13w -47 26w 193 $/wk
2025-12-01 | C|368|skip | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -0 13w -788 26w 551 $/wk
2025-12-01 | L|M6|M|ls|4|q20|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 927 13w 805 26w 170 $/wk
2025-12-01 | L|K6|Q|real|0|q10|x0.5 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.2, 4w -0 13w -0 26w 188 $/wk
2025-12-01 | L|K6|Q|real|0|q10|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 280 13w -8 26w 151 $/wk
2025-12-01 | D|706|x1.5 | RISING -> STABLE | CUSUM 0.6 sig, z4 -1.3, 4w -2,480 13w 672 26w 275 $/wk
2025-12-01 | L|U6|M|ls|1|q20|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -0 13w -0 26w 135 $/wk
2025-12-01 | D|319|x1.5 | FADING -> STABLE | CUSUM 0.5 sig, z4 -1.4, 4w -3,123 13w 2,037 26w 1,912 $/wk
2025-12-01 | D|134|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 546 13w 468 26w 676 $/wk
2025-12-01 | D|712|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 1,534 13w 1,037 26w 727 $/wk
2025-12-01 | HR|book|wk4_5|day|0 | OFF -> NEW | 13w mean 448 26w 136 $/wk
2025-12-01 | HR|book|ddd5_8|w3|0 | OFF -> NEW | 13w mean 1,468 26w 36 $/wk
2025-12-01 | C|360|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,232 13w 1,158 26w 654 $/wk
2025-12-01 | L|M6|M|ls|5|q10|x0.5 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -0 13w -26 26w 28 $/wk
2025-12-01 | C|397|x0.5 | NEW -> STABLE | CUSUM 0.3 sig, z4 -0.8, 4w -2,992 13w 1,455 26w -259 $/wk
2025-12-01 | D|130|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 307 13w 1,023 26w 618 $/wk
2025-12-01 | D|466|x1.5 | STOPPED -> NEW | 13w mean 573 26w 983 $/wk
2025-12-01 | C|515|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,618 13w 1,864 26w 1,217 $/wk
2025-12-01 | D|547|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w -0 13w 655 26w 574 $/wk
2025-12-01 | D|563|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 1,197 13w 1,027 26w 1,233 $/wk
2025-12-01 | C|770|x0.5 | OFF -> NEW | 13w mean 315 26w 66 $/wk
2025-12-01 | C|229|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 1,210 13w 781 26w 523 $/wk
2025-12-01 | D|958|take | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,366 13w 819 26w 699 $/wk
2025-12-01 | D|678|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 132 13w 997 26w 291 $/wk
2025-12-01 | D|677|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -7 13w 483 26w 276 $/wk
2025-12-01 | D|588|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.6, 4w 1,309 13w 600 26w 612 $/wk
2025-12-01 | C|527|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 894 13w 311 26w 6 $/wk
2025-12-01 | D|666|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 1,558 13w 479 26w 650 $/wk
2025-12-01 | D|663|x1.5 | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.7, 4w -673 13w -15 26w 314 $/wk
2025-12-01 | D|673|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 295 13w 372 26w 349 $/wk
2025-12-01 | C|52|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 2,732 13w 1,760 26w 758 $/wk
2025-12-01 | C|735|skip | RISING -> STABLE | CUSUM 0.1 sig, z4 +0.2, 4w 379 13w 401 26w 59 $/wk
2025-12-01 | HR|book|AND:wk2_3:reg_ci_60|w2|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +2.9, 4w 1,529 13w 470 26w 253 $/wk
2025-12-01 | D|676|x1.5 | RISING -> STABLE | CUSUM 0.8 sig, z4 -0.2, 4w 374 13w 1,518 26w 666 $/wk
2025-12-01 | D|655|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w -0 13w 424 26w 50 $/wk
2025-12-01 | HR|book|AND:wk2_3:reg_er_60|day|0 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 5,495 13w 3,545 26w 1,709 $/wk
2025-12-01 | C|613|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 308 13w 126 26w 148 $/wk
2025-12-01 | D|460|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w -406 13w 1,222 26w 1,673 $/wk
2025-12-01 | D|449|x1.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.2, 4w -0 13w -87 26w 572 $/wk
2025-12-01 | L|POOL6|Q|ls|3|q10|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 445 13w 137 26w 211 $/wk
2025-12-01 | C|885|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 395 13w 315 26w 97 $/wk
2025-12-01 | D|436|x1.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -0 13w -0 26w 486 $/wk
2025-12-01 | C|223|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.0, 4w -0 13w -0 26w 24 $/wk
2025-12-01 | D|686|x1.5 | STABLE -> RISING | CUSUM 0.3 sig, z4 +1.3, 4w 4,801 13w 2,153 26w 1,531 $/wk
2025-12-01 | C|874|x0.5 | STOPPED -> NEW | 13w mean 74 26w 96 $/wk
2025-12-01 | C|878|skip | FADING -> NEW | CUSUM 0.0 sig, z4 +1.6, 4w 873 13w 189 26w 243 $/wk
2025-12-01 | HR|book|L:sh2:0.65|mem|0 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2025-12-08 | D|819|x1.5 | RISING -> STABLE | CUSUM 0.8 sig, z4 +0.4, 4w 1,227 13w 966 26w 809 $/wk
2025-12-08 | D|676|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 3,534 13w 2,300 26w 1,187 $/wk
2025-12-08 | D|403|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w -0 13w 300 26w -483 $/wk
2025-12-08 | D|446|x1.5 | OFF -> NEW | 13w mean 2,129 26w 230 $/wk
2025-12-08 | L|A6|M|fs|3|q30|x0.5 | RISING -> STABLE | CUSUM 0.7 sig, z4 -0.0, 4w 9 13w 140 26w 35 $/wk
2025-12-08 | D|711|x1.5 | STOPPED -> NEW | 13w mean 310 26w 372 $/wk
2025-12-08 | D|656|x1.5 | OFF -> NEW | 13w mean 432 26w 446 $/wk
2025-12-08 | L|P6|M|ls|6|q20|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 10,741 13w 6,781 26w 3,475 $/wk
2025-12-08 | D|434|x1.5 | OFF -> NEW | 13w mean 1,030 26w 2,330 $/wk
2025-12-08 | D|668|x1.5 | OFF -> NEW | 13w mean 302 26w 42 $/wk
2025-12-08 | D|659|x1.5 | OFF -> NEW | 13w mean 353 26w 147 $/wk
2025-12-08 | D|410|x1.5 | OFF -> NEW | 13w mean 99 26w 429 $/wk
2025-12-08 | D|696|x1.5 | OFF -> NEW | 13w mean 167 26w 633 $/wk
2025-12-08 | L|P6|M|ls|5|q10|skip | NEW -> FADING | CUSUM 0.4 sig, z4 -0.9, 4w -4,052 13w 824 26w 1,742 $/wk
2025-12-08 | D|436|x1.5 | STOPPED -> NEW | 13w mean 610 26w 791 $/wk
2025-12-08 | D|712|x1.5 | RISING -> STABLE | CUSUM 0.6 sig, z4 +0.1, 4w 906 13w 847 26w 715 $/wk
2025-12-08 | D|666|x1.5 | STABLE -> FADING | CUSUM 1.3 sig, z4 -1.5, 4w -1,194 13w 212 26w 516 $/wk
2025-12-08 | D|413|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 1,983 13w 696 26w 829 $/wk
2025-12-08 | GOV2|ew3|cNone | NEW -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 24,172 13w 6,586 26w 4,392 $/wk
2025-12-08 | D|663|x1.5 | STOPPED -> NEW | 13w mean 690 26w 759 $/wk
2025-12-08 | D|673|x1.5 | STABLE -> FADING | CUSUM 1.0 sig, z4 -0.1, 4w 295 13w 182 26w 384 $/wk
2025-12-08 | T|U6|q20|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 924 13w 569 26w 379 $/wk
2025-12-08 | D|319|x1.5 | STABLE -> FADING | CUSUM 0.5 sig, z4 -1.7, 4w -4,360 13w 1,831 26w 1,815 $/wk
2025-12-08 | D|563|x1.5 | STABLE -> FADING | CUSUM 3.0 sig, z4 -1.3, 4w -1,576 13w 174 26w 667 $/wk
2025-12-08 | D|562|x1.5 | STABLE -> STOPPED | CUSUM 5.5 sig, z4 -2.1, 4w -1,859 13w 653 26w 184 $/wk
2025-12-08 | L|K6|M|ls|6|q30|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,860 13w 684 26w 393 $/wk
2025-12-08 | D|334|x1.5 | STABLE -> FADING | CUSUM 0.6 sig, z4 -2.0, 4w -4,314 13w 3,826 26w 3,068 $/wk
2025-12-08 | D|457|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -154 13w 1,107 26w 539 $/wk
2025-12-08 | D|682|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.5, 4w 2,292 13w 724 26w 624 $/wk
2025-12-08 | D|463|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 1,021 13w 1,624 26w 3,336 $/wk
2025-12-08 | L|K6|M|real|0|q30|skip | FADING -> NEW | CUSUM 0.0 sig, z4 +1.4, 4w 4,142 13w 607 26w 929 $/wk
2025-12-08 | L|K6|M|real|0|q20|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +2.0, 4w 3,569 13w 758 26w 625 $/wk
2025-12-08 | D|451|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 4,679 13w 1,837 26w 2,789 $/wk
2025-12-08 | T|K6|q20|skip | OFF -> NEW | 13w mean 86 26w 797 $/wk
2025-12-08 | D|692|x1.5 | OFF -> NEW | 13w mean 244 26w 757 $/wk
2025-12-08 | D|804|take | RISING -> STABLE | CUSUM 1.5 sig, z4 -1.4, 4w -1,925 13w 129 26w 166 $/wk
2025-12-08 | D|707|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.1, 4w 2,742 13w 1,379 26w 887 $/wk
2025-12-08 | D|677|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.8, 4w 2,192 13w 970 26w 519 $/wk
2025-12-08 | D|697|x1.5 | NEW -> FADING | CUSUM 0.2 sig, z4 -0.1, 4w 450 13w 132 26w 549 $/wk
2025-12-08 | D|449|x1.5 | STOPPED -> NEW | 13w mean 610 26w 877 $/wk
2025-12-08 | D|678|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 1,885 13w 1,485 26w 665 $/wk
2025-12-08 | D|705|x1.5 | OFF -> NEW | 13w mean 1,076 26w 311 $/wk
2025-12-08 | U|H6|x2 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.3, 4w 12,246 13w 5,296 26w 5,644 $/wk
2025-12-08 | L|K6|M|fs|3|q10|skip | OFF -> NEW | 13w mean 35 26w 160 $/wk
2025-12-08 | L|U6|M|ls|6|q30|skip | RISING -> STABLE | CUSUM 0.5 sig, z4 +0.0, 4w -319 13w 158 26w -364 $/wk
2025-12-08 | D|88|x1.5 | STOPPED -> NEW | 13w mean 505 26w 353 $/wk
2025-12-08 | C|368|skip | STOPPED -> NEW | 13w mean 3,507 26w 799 $/wk
2025-12-08 | C|371|skip | OFF -> NEW | 13w mean 129 26w 1,697 $/wk
2025-12-08 | C|229|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 1,297 13w 868 26w 709 $/wk
2025-12-08 | C|14|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,759 13w 1,305 26w 969 $/wk
2025-12-08 | C|237|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w -310 13w 151 26w 89 $/wk
2025-12-08 | C|354|x0.5 | OFF -> NEW | 13w mean 879 26w 47 $/wk
2025-12-08 | C|20|skip | OFF -> NEW | 13w mean 28 26w 4 $/wk
2025-12-08 | C|62|skip | OFF -> NEW | 13w mean 157 26w 20 $/wk
2025-12-08 | C|874|x0.5 | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.1, 4w -0 13w -52 26w 51 $/wk
2025-12-08 | C|16|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 959 13w 931 26w 834 $/wk
2025-12-08 | C|193|x0.5 | OFF -> NEW | 13w mean 41 26w 20 $/wk
2025-12-08 | C|338|x0.5 | OFF -> NEW | 13w mean 478 26w 466 $/wk
2025-12-08 | C|72|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,622 13w 2,867 26w -36 $/wk
2025-12-08 | C|764|skip | OFF -> NEW | 13w mean 85 26w 82 $/wk
2025-12-08 | C|243|x0.5 | STABLE -> FADING | CUSUM 1.2 sig, z4 -0.9, 4w -148 13w 34 26w 78 $/wk
2025-12-08 | C|719|x0.5 | OFF -> NEW | 13w mean 69 26w 40 $/wk
2025-12-08 | C|735|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 1,416 13w 716 26w 265 $/wk
2025-12-08 | D|255|x1.5 | NEW -> STOPPED | CUSUM 0.5 sig, z4 -0.4, 4w -625 13w -70 26w 371 $/wk
2025-12-08 | D|156|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 16,235 13w 15,960 26w 12,928 $/wk
2025-12-08 | C|888|x0.5 | OFF -> NEW | 13w mean 227 26w 18 $/wk
2025-12-08 | C|504|x0.5 | FADING -> STOPPED | CUSUM 2.7 sig, z4 -2.2, 4w -1,884 13w -271 26w 114 $/wk
2025-12-08 | D|104|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,514 13w 447 26w 588 $/wk
2025-12-15 | D|334|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w 1,570 13w 5,233 26w 3,817 $/wk
2025-12-15 | L|U6|M|fs|3|q30|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -303 13w 755 26w -6 $/wk
2025-12-15 | D|108|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 10,854 13w 10,267 26w 7,890 $/wk
2025-12-15 | C|526|skip | OFF -> NEW | 13w mean 774 26w 15 $/wk
2025-12-15 | C|195|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 617 13w 273 26w 184 $/wk
2025-12-15 | L|U6|M|fs|3|q20|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 0 13w 95 26w -56 $/wk
2025-12-15 | HR|book|AND:streak4:map_vol|day|0 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 0 $/wk
2025-12-15 | L|U6|M|fs|3|q10|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 95 26w 47 $/wk
2025-12-15 | C|192|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 24 13w 553 26w 720 $/wk
2025-12-15 | HR|book|wk4_5|day|0 | NEW -> STOPPED | CUSUM 0.5 sig, z4 -0.3, 4w -3,972 13w -1,248 26w -712 $/wk
2025-12-15 | C|864|skip | OFF -> NEW | 13w mean 337 26w 118 $/wk
2025-12-15 | C|227|x0.5 | NEW -> RISING | CUSUM 0.5 sig, z4 +1.7, 4w 1,376 13w 431 26w 216 $/wk
2025-12-15 | D|402|x1.5 | OFF -> NEW | 13w mean 571 26w 736 $/wk
2025-12-15 | L|H6|M|ls|6|q10|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 926 13w 675 26w 337 $/wk
2025-12-15 | D|457|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 2,196 13w 1,969 26w 971 $/wk
2025-12-15 | C|501|x0.5 | OFF -> NEW | 13w mean 12 26w 367 $/wk
2025-12-15 | HR|book|AND:rs10_3:reg_ci_60|mem|0 | OFF -> NEW | 13w mean 0 26w 157 $/wk
2025-12-15 | C|878|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 565 13w 189 26w 243 $/wk
2025-12-15 | D|695|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 4,088 13w 3,337 26w 1,657 $/wk
2025-12-15 | C|885|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 132 13w 315 26w 56 $/wk
2025-12-15 | C|504|x0.5 | STOPPED -> NEW | 13w mean 7 26w 114 $/wk
2025-12-15 | HR|book|AND:rs10_3:map_vol|mem|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 156 26w 175 $/wk
2025-12-15 | D|434|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.6, 4w 5,890 13w 715 26w 2,490 $/wk
2025-12-15 | HR|book|AND:wk2_3:map_vol|ses|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -580 13w 184 26w 49 $/wk
2025-12-15 | HR|book|ddd5_8|mon|0 | OFF -> NEW | 13w mean 1,122 26w 636 $/wk
2025-12-15 | C|895|skip | OFF -> NEW | 13w mean 728 26w 364 $/wk
2025-12-15 | T|K6|q20|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +2.3, 4w 4,079 13w -50 26w 52 $/wk
2025-12-15 | D|410|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 1,687 13w 99 26w 429 $/wk
2025-12-15 | D|716|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 2,017 13w 1,577 26w 1,374 $/wk
2025-12-15 | C|509|skip | RISING -> STOPPED | CUSUM 0.1 sig, z4 -0.4, 4w -603 13w -370 26w 198 $/wk
2025-12-15 | D|86|x1.5 | OFF -> NEW | 13w mean 210 26w 349 $/wk
2025-12-15 | HR|book|reg_ci_30|rev|0 | OFF -> NEW | 13w mean 282 26w 184 $/wk
2025-12-15 | C|371|skip | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 1,269 13w -897 26w 1,697 $/wk
2025-12-15 | D|453|x1.5 | OFF -> NEW | 13w mean 982 26w 847 $/wk
2025-12-15 | D|463|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 4,973 13w 2,687 26w 3,798 $/wk
2025-12-15 | C|719|skip | OFF -> NEW | 13w mean 197 26w 98 $/wk
2025-12-15 | C|8|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 1,248 13w 4,761 26w 2,381 $/wk
2025-12-15 | L|K6|M|fs|3|q10|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 717 13w -60 26w 160 $/wk
2025-12-15 | L|P6|M|ls|5|q10|skip | FADING -> STABLE | CUSUM 0.1 sig, z4 -1.0, 4w -4,685 13w 824 26w 1,553 $/wk
2025-12-15 | C|18|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 925 13w 856 26w 428 $/wk
2025-12-15 | D|586|take | OFF -> NEW | 13w mean 489 26w 403 $/wk
2025-12-15 | HR|book|AND:streak4:map_vol|w2|0 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-15 | D|588|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 1,613 13w 699 26w 519 $/wk
2025-12-15 | D|562|x1.5 | STOPPED -> NEW | 13w mean 653 26w 184 $/wk
2025-12-15 | D|673|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 2 13w 373 26w 479 $/wk
2025-12-15 | HR|book|rs30_5|n2|0 | OFF -> NEW | 13w mean 2,043 26w 59 $/wk
2025-12-15 | D|585|take | OFF -> NEW | 13w mean 218 26w 1,179 $/wk
2025-12-15 | HR|book|rs30_5|ses|0 | OFF -> NEW | 13w mean 1,176 26w 10 $/wk
2025-12-15 | L|H6|M|ls|5|q20|x0.5 | NEW -> STABLE | CUSUM 0.1 sig, z4 -0.6, 4w -612 13w 656 26w 92 $/wk
2025-12-15 | L|H6|M|ls|4|q10|x0.5 | OFF -> NEW | 13w mean 283 26w 2 $/wk
2025-12-15 | D|572|take | OFF -> NEW | 13w mean 128 26w 113 $/wk
2025-12-15 | C|5|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 581 13w 317 26w 159 $/wk
2025-12-15 | D|565|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.4, 4w 0 13w 127 26w 437 $/wk
2025-12-15 | L|M6|M|ls|4|q30|x0.5 | OFF -> NEW | 13w mean 93 26w 47 $/wk
2025-12-15 | L|M6|M|ls|4|q20|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -306 13w 710 26w 76 $/wk
2025-12-15 | C|7|skip | STABLE -> FADING | CUSUM 1.0 sig, z4 -0.6, 4w -786 13w 211 26w 512 $/wk
2025-12-15 | D|255|x1.5 | STOPPED -> NEW | 13w mean 319 26w 471 $/wk
2025-12-15 | D|563|take | OFF -> NEW | 13w mean 1,185 26w 44 $/wk
2025-12-15 | C|761|x0.5 | OFF -> NEW | 13w mean 229 26w 165 $/wk
2025-12-15 | L|P6|M|ls|6|q20|skip | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.6, 4w -2,107 13w 6,037 26w 2,974 $/wk
2025-12-15 | HR|book|AND:wk2_3:reg_er_60|day|0 | RISING -> STABLE | CUSUM 0.9 sig, z4 -0.2, 4w 61 13w 1,803 26w 1,445 $/wk
2025-12-15 | C|735|skip | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.2, 4w -251 13w 495 26w 201 $/wk
2025-12-15 | HR|book|AND:wk2_3:reg_ci_60|day|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.6, 4w 1,222 13w 376 26w 180 $/wk
2025-12-15 | C|845|skip | OFF -> NEW | 13w mean 108 26w 157 $/wk
2025-12-15 | D|319|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 630 13w 1,752 26w 2,090 $/wk
2025-12-15 | L|U6|M|fs|1|q30|x0.5 | OFF -> NEW | 13w mean 1,014 26w 47 $/wk
2025-12-15 | C|72|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 5,085 13w 2,718 26w 170 $/wk
2025-12-15 | D|666|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 667 13w 591 26w 702 $/wk
2025-12-15 | D|974|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w 0 13w 408 26w 204 $/wk
2025-12-15 | C|723|skip | STABLE -> FADING | CUSUM 0.1 sig, z4 -0.5, 4w -390 13w 175 26w 385 $/wk
2025-12-15 | L|U6|M|ls|2|q10|x0.5 | OFF -> NEW | 13w mean 284 26w 3 $/wk
2025-12-15 | HR|book|z20_2.0|n5|0 | OFF -> NEW | 13w mean 651 26w 431 $/wk
2025-12-15 | C|31|x0.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 893 13w 372 26w 613 $/wk
2025-12-15 | L|POOL6|Q|ls|3|q20|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 1,249 13w 786 26w 251 $/wk
2025-12-15 | C|30|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 2,671 13w 1,919 26w 369 $/wk
2025-12-15 | D|156|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 22,067 13w 19,026 26w 14,534 $/wk
2025-12-15 | D|660|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 810 13w 702 26w 538 $/wk
2025-12-15 | HR|book|AND:rs10_3:map_vol|ses|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 172 26w 138 $/wk
2025-12-15 | C|723|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.2, 4w -200 13w -49 26w 61 $/wk
2025-12-22 | U|H6|x2 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 8,685 13w 8,029 26w 6,411 $/wk
2025-12-22 | C|527|x0.5 | RISING -> FADING | CUSUM 0.0 sig, z4 +0.7, 4w 1,867 13w 218 26w 606 $/wk
2025-12-22 | C|502|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.6, 4w 0 13w -2 26w 716 $/wk
2025-12-22 | C|513|skip | OFF -> NEW | 13w mean 1,041 26w 154 $/wk
2025-12-22 | D|581|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 162 26w 385 $/wk
2025-12-22 | D|589|x1.5 | STABLE -> FADING | CUSUM 2.4 sig, z4 -1.3, 4w -1,859 13w 279 26w 116 $/wk
2025-12-22 | D|588|x1.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 +0.7, 4w 1,315 13w 511 26w 472 $/wk
2025-12-22 | D|676|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 2,534 13w 2,582 26w 1,376 $/wk
2025-12-22 | C|723|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -82 13w 365 26w 432 $/wk
2025-12-22 | D|660|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 0 13w 702 26w 492 $/wk
2025-12-22 | HR|book|L:sh1:0.65|mem|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 285 26w 119 $/wk
2025-12-22 | D|667|x1.5 | RISING -> STABLE | CUSUM 1.4 sig, z4 -0.8, 4w -731 13w 255 26w 290 $/wk
2025-12-22 | C|731|x0.5 | OFF -> NEW | 13w mean 0 26w 316 $/wk
2025-12-22 | C|504|x0.5 | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.6, 4w -378 13w -558 26w 207 $/wk
2025-12-22 | C|506|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 2,234 13w 416 26w 800 $/wk
2025-12-22 | C|517|skip | OFF -> NEW | 13w mean 628 26w 236 $/wk
2025-12-22 | D|691|x1.5 | RISING -> STABLE | CUSUM 0.4 sig, z4 +0.3, 4w 3,447 13w 4,017 26w 2,765 $/wk
2025-12-22 | C|515|skip | RISING -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w 97 13w 386 26w 1,320 $/wk
2025-12-22 | L|U6|M|fs|3|q30|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w -303 13w 1 26w 98 $/wk
2025-12-22 | C|499|skip | OFF -> NEW | 13w mean 186 26w 428 $/wk
2025-12-22 | L|U6|M|ls|2|q20|x0.5 | OFF -> NEW | 13w mean 379 26w 50 $/wk
2025-12-22 | L|A6|M|fs|1|q20|x0.5 | OFF -> NEW | 13w mean 0 26w 1 $/wk
2025-12-22 | L|A6|M|fs|3|q30|x0.5 | STABLE -> STOPPED | CUSUM 0.9 sig, z4 -0.6, 4w -290 13w -72 26w 35 $/wk
2025-12-22 | L|A6|M|real|0|q30|skip | OFF -> NEW | 13w mean 79 26w 392 $/wk
2025-12-22 | C|47|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w -309 13w 287 26w -34 $/wk
2025-12-22 | C|20|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | L|K6|M|real|0|q30|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +1.4, 4w 3,650 13w 437 26w 374 $/wk
2025-12-22 | L|U6|M|ls|1|q20|x0.5 | OFF -> NEW | 13w mean 0 26w 47 $/wk
2025-12-22 | L|K6|M|ls|6|q30|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 130 13w 941 26w 440 $/wk
2025-12-22 | L|K6|Q|real|0|q10|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 308 13w 86 26w 151 $/wk
2025-12-22 | L|K6|Q|real|0|q10|x0.5 | OFF -> NEW | 13w mean 0 26w 188 $/wk
2025-12-22 | HR|book|AND:z20_1.5:map_vol|w2|0 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 296 26w 148 $/wk
2025-12-22 | L|U6|M|ls|1|q10|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | C|7|skip | FADING -> STABLE | CUSUM 0.7 sig, z4 -0.7, 4w -1,087 13w 617 26w 369 $/wk
2025-12-22 | L|M6|M|ls|1|q10|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | L|M6|M|ls|3|q10|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 49 26w 12 $/wk
2025-12-22 | L|U6|M|real|0|q20|x0.5 | OFF -> NEW | 13w mean 0 26w 29 $/wk
2025-12-22 | L|U6|M|real|0|q10|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | L|H6|M|ls|1|q20|x0.5 | OFF -> NEW | 13w mean 312 26w 17 $/wk
2025-12-22 | C|20|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 300 13w -21 26w 4 $/wk
2025-12-22 | C|501|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.6, 4w 1,792 13w 102 26w 665 $/wk
2025-12-22 | D|958|take | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 1,294 13w 1,119 26w 735 $/wk
2025-12-22 | HR|book|AND:rs10_3:reg_ci_60|mem|0 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.6, 4w 0 13w 0 26w 157 $/wk
2025-12-22 | D|697|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 215 13w 579 26w 628 $/wk
2025-12-22 | C|397|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,882 13w 1,416 26w 1,087 $/wk
2025-12-22 | C|396|x0.5 | OFF -> NEW | 13w mean 1,416 26w 895 $/wk
2025-12-22 | D|706|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 2,965 13w 1,969 26w 1,270 $/wk
2025-12-22 | D|707|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 2,100 13w 876 26w 727 $/wk
2025-12-22 | C|362|x0.5 | OFF -> NEW | 13w mean 2,251 26w 1,116 $/wk
2025-12-22 | C|360|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 2,771 13w 1,146 26w 401 $/wk
2025-12-22 | HR|book|reg_xasset_120|day|0 | OFF -> NEW | 13w mean 415 26w 671 $/wk
2025-12-22 | T|U6|q20|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 0 13w 569 26w 379 $/wk
2025-12-22 | C|241|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 1,538 13w 1,142 26w 378 $/wk
2025-12-22 | L|U6|Q|real|0|q10|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | C|227|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.8, 4w -334 13w 431 26w 216 $/wk
2025-12-22 | C|223|x0.5 | OFF -> NEW | 13w mean 0 26w 72 $/wk
2025-12-22 | C|196|x0.5 | OFF -> NEW | 13w mean 0 26w 0 $/wk
2025-12-22 | C|190|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.8, 4w 0 13w 594 26w 250 $/wk
2025-12-22 | L|U6|M|fs|2|q10|skip | OFF -> NEW | 13w mean 190 26w 95 $/wk
2025-12-22 | C|190|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 454 13w 686 26w 107 $/wk
2025-12-22 | D|686|x1.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.1, 4w 2,184 13w 3,801 26w 2,444 $/wk
2025-12-22 | D|415|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 94 26w 193 $/wk
2025-12-22 | HR|book|rs30_5|ses|2 | OFF -> NEW | 13w mean 1,930 26w 397 $/wk
2025-12-22 | HR|book|rs5_5|ses|2 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 128 13w -127 26w 858 $/wk
2025-12-22 | D|319|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.8, 4w -906 13w 1,013 26w 2,091 $/wk
2025-12-22 | D|562|x1.5 | NEW -> STOPPED | CUSUM 0.0 sig, z4 -3.0, 4w -2,772 13w -191 26w 184 $/wk
2025-12-22 | D|453|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +1.6, 4w 9,160 13w 169 26w 888 $/wk
2025-12-22 | D|279|take | FADING -> STOPPED | CUSUM 0.3 sig, z4 -1.3, 4w -3,368 13w -73 26w 1,343 $/wk
2025-12-22 | D|156|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 21,342 13w 18,276 26w 14,773 $/wk
2025-12-22 | D|403|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 1,518 13w 767 26w -121 $/wk
2025-12-22 | D|86|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.7, 4w 2,167 13w 135 26w 349 $/wk
2025-12-22 | D|560|take | OFF -> NEW | 13w mean 297 26w 519 $/wk
2025-12-22 | D|290|take | NEW -> FADING | CUSUM 0.9 sig, z4 -0.8, 4w -2,409 13w 322 26w 992 $/wk
2025-12-22 | C|901|x0.5 | OFF -> NEW | 13w mean 180 26w 8 $/wk
2025-12-22 | D|452|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 3,713 13w 1,699 26w 798 $/wk
2025-12-22 | D|108|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 12,509 13w 9,778 26w 8,928 $/wk
2025-12-22 | D|106|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w -265 13w 1,973 26w 1,296 $/wk
2025-12-22 | HR|book|rs5_5|p5|0 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w -329 13w 32 26w 802 $/wk
2025-12-22 | HR|book|ddd5_8|n5|0 | OFF -> NEW | 13w mean 1,657 26w 730 $/wk
2025-12-22 | HR|book|z10_2.0|n5|0 | OFF -> NEW | 13w mean 1,853 26w 1,163 $/wk
2025-12-22 | D|402|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.3, 4w 2,086 13w 571 26w 1,206 $/wk
2025-12-29 | L|POOL6|Q|ls|3|q20|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w -0 13w 786 26w 109 $/wk
2025-12-29 | C|613|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 31 26w 152 $/wk
2025-12-29 | D|713|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -225 13w 130 26w 67 $/wk
2025-12-29 | D|676|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 3,458 13w 2,582 26w 1,346 $/wk
2025-12-29 | HR|book|AND:wk2_3:reg_ci_60|w2|0 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 470 26w 96 $/wk
2025-12-29 | C|888|x0.5 | NEW -> FADING | CUSUM 2.0 sig, z4 +0.5, 4w 101 13w 135 26w -28 $/wk
2025-12-29 | L|A6|M|real|0|q30|skip | NEW -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 79 26w 379 $/wk
2025-12-29 | L|U6|M|ls|1|q20|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 47 $/wk
2025-12-29 | D|86|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +1.0, 4w 3,095 13w 386 26w 648 $/wk
2025-12-29 | T|U6|q20|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 924 13w 853 26w 474 $/wk
2025-12-29 | L|K6|M|real|0|q30|skip | STABLE -> FADING | CUSUM 0.2 sig, z4 +0.3, 4w 1,151 13w 55 26w 417 $/wk
2025-12-29 | C|357|skip | OFF -> NEW | 13w mean 1,780 26w 274 $/wk
2025-12-29 | C|52|x0.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 +0.1, 4w 868 13w 1,609 26w 603 $/wk
2025-12-29 | HR|book|AND:wk2_3:reg_ci_60|day|0 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 376 26w 180 $/wk
2025-12-29 | D|958|take | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.4, 4w -238 13w 917 26w 646 $/wk
2025-12-29 | L|A6|M|real|0|q30|x0.5 | OFF -> NEW | 13w mean 88 26w 58 $/wk
2025-12-29 | C|190|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 1,072 13w 781 26w 155 $/wk
2025-12-29 | C|871|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 0 26w 84 $/wk
2025-12-29 | D|452|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.2, 4w 3,713 13w 963 26w 798 $/wk
2025-12-29 | C|72|skip | RISING -> STABLE | CUSUM 0.4 sig, z4 +0.3, 4w 1,403 13w 3,328 26w -59 $/wk
2025-12-29 | C|397|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 740 13w 823 26w 1,106 $/wk
2025-12-29 | D|453|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +1.7, 4w 9,333 13w 711 26w 811 $/wk
2025-12-29 | D|466|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 4,768 13w 2,173 26w 1,293 $/wk
2025-12-29 | D|150|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 12,782 13w 9,209 26w 7,315 $/wk
2025-12-29 | L|A6|M|fs|1|q20|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 1 $/wk
2025-12-29 | D|319|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 891 13w 1,592 26w 2,176 $/wk
2025-12-29 | D|694|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 2,858 13w 1,969 26w 1,499 $/wk
2025-12-29 | C|30|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -439 13w 1,476 26w 662 $/wk
2025-12-29 | HR|book|z10_2.0|w3|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w -1,729 13w 725 26w 434 $/wk
2025-12-29 | L|K6|M|ls|6|q20|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -374 13w 1,062 26w 440 $/wk
2025-12-29 | C|723|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 227 13w 175 26w 527 $/wk
2025-12-29 | HR|book|AND:z20_1.5:reg_xasset_60|mem|0 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w -1 26w 135 $/wk
2025-12-29 | D|402|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.4, 4w 2,086 13w 571 26w 918 $/wk
2025-12-29 | C|243|x0.5 | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.9, 4w -148 13w -69 26w 78 $/wk
2025-12-29 | C|737|skip | OFF -> NEW | 13w mean 1,663 26w 177 $/wk
2025-12-29 | HR|book|ddd5_8|w3|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w -59 13w 1,450 26w 718 $/wk
2025-12-29 | C|196|skip | OFF -> NEW | 13w mean 46 26w 442 $/wk
2025-12-29 | D|716|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -1.6, 4w -1,348 13w 1,545 26w 1,027 $/wk
2025-12-29 | D|279|take | STOPPED -> NEW | 13w mean 359 26w 1,391 $/wk
2025-12-29 | C|241|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 933 13w 1,332 26w 473 $/wk
2025-12-29 | D|589|x1.5 | FADING -> STOPPED | CUSUM 2.2 sig, z4 -1.6, 4w -2,159 13w -98 26w 191 $/wk
2025-12-29 | C|243|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 89 13w -70 26w 343 $/wk
2025-12-29 | L|M6|M|ls|1|q10|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 0 $/wk
2025-12-29 | GOV2|ew3|cNone | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.8, 4w -10,715 13w 1,931 26w 1,023 $/wk
2025-12-29 | C|241|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 673 13w 1,378 26w 699 $/wk
2025-12-29 | D|581|take | OFF -> NEW | 13w mean 2,261 26w 176 $/wk
2025-12-29 | D|584|take | OFF -> NEW | 13w mean 987 26w 156 $/wk
2025-12-29 | C|242|x0.5 | STABLE -> FADING | CUSUM 0.3 sig, z4 -0.5, 4w -9 13w 166 26w 501 $/wk
2025-12-29 | L|K6|M|fs|3|q10|skip | FADING -> NEW | CUSUM 0.0 sig, z4 +0.7, 4w 1,026 13w 79 26w 65 $/wk
2025-12-29 | C|770|x0.5 | NEW -> RISING | CUSUM 0.1 sig, z4 +0.8, 4w 875 13w 488 26w 152 $/wk
2025-12-29 | L|K6|Q|real|0|q10|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 0 26w 236 $/wk
2025-12-29 | D|410|x1.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.8, 4w 3,056 13w 520 26w 640 $/wk
2025-12-29 | C|223|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 0 26w 72 $/wk
2025-12-29 | HR|book|rs5_5|p5|0 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w -9 13w 489 26w 802 $/wk
2025-12-29 | D|567|take | OFF -> NEW | 13w mean 1,085 26w 114 $/wk
2025-12-29 | C|731|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 0 26w 316 $/wk
2025-12-29 | L|K6|Q|real|0|q10|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 86 26w 293 $/wk
2025-12-29 | C|14|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 383 13w 1,016 26w 748 $/wk
2025-12-29 | D|581|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 914 13w 443 26w 555 $/wk
2025-12-29 | C|14|x0.5 | OFF -> NEW | 13w mean 82 26w 67 $/wk
2025-12-29 | L|H6|M|ls|1|q30|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 1,148 13w 550 26w 75 $/wk
2026-01-05 | D|434|x1.5 | FADING -> STOPPED | CUSUM 1.1 sig, z4 -1.2, 4w -5,455 13w -396 26w 1,314 $/wk
2026-01-05 | C|888|x0.5 | FADING -> STABLE | CUSUM 1.6 sig, z4 -1.1, 4w -299 13w 135 26w -28 $/wk
2026-01-05 | D|705|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 789 26w 407 $/wk
2026-01-05 | C|196|skip | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 309 13w 141 26w 442 $/wk
2026-01-05 | C|397|x0.5 | STABLE -> STOPPED | CUSUM 0.9 sig, z4 -1.1, 4w -2,956 13w -688 26w 816 $/wk
2026-01-05 | C|764|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -696 13w 127 26w -133 $/wk
2026-01-05 | D|410|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 1,368 13w 520 26w 640 $/wk
2026-01-05 | D|716|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w 185 13w 1,827 26w 1,168 $/wk
2026-01-05 | C|354|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 616 13w 1,929 26w -33 $/wk
2026-01-05 | D|958|take | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.4, 4w 1,484 13w -415 26w 581 $/wk
2026-01-05 | C|190|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 308 13w 781 26w 155 $/wk
2026-01-05 | C|338|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 946 13w 1,142 26w 517 $/wk
2026-01-05 | D|714|x1.5 | RISING -> STABLE | CUSUM 0.4 sig, z4 +0.0, 4w 2,005 13w 2,674 26w 1,927 $/wk
2026-01-05 | D|713|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.6, 4w 919 13w 34 26w 115 $/wk
2026-01-05 | D|86|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +1.0, 4w 3,305 13w 400 26w 843 $/wk
2026-01-05 | C|360|skip | RISING -> STABLE | CUSUM 1.3 sig, z4 -1.2, 4w -2,427 13w 2,320 26w 1,061 $/wk
2026-01-05 | C|243|x0.5 | STOPPED -> NEW | 13w mean 26 26w 126 $/wk
2026-01-05 | C|360|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.7, 4w -1,213 13w 982 26w 401 $/wk
2026-01-05 | D|711|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +1.9, 4w 3,671 13w 951 26w 1,123 $/wk
2026-01-05 | C|368|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 3,487 13w 3,774 26w 1,079 $/wk
2026-01-05 | C|193|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 41 26w 20 $/wk
2026-01-05 | D|88|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,368 13w 691 26w 564 $/wk
2026-01-05 | D|319|x1.5 | STABLE -> FADING | CUSUM 0.2 sig, z4 -0.5, 4w 508 13w 839 26w 2,318 $/wk
2026-01-05 | D|708|x1.5 | RISING -> STABLE | CUSUM 0.2 sig, z4 -0.1, 4w 492 13w 1,026 26w 820 $/wk
2026-01-05 | C|371|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 391 26w 65 $/wk
2026-01-05 | D|699|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.0, 4w 4,493 13w 2,128 26w 1,592 $/wk
2026-01-05 | C|62|skip | NEW -> STOPPED | CUSUM 1.9 sig, z4 -1.3, 4w -931 13w -27 26w 90 $/wk
2026-01-05 | L|K6|M|fs|3|q10|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 309 13w 361 26w 65 $/wk
2026-01-05 | HR|book|AND:wk2_3:reg_er_60|day|0 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.8, 4w -5,671 13w -444 26w 1,310 $/wk
2026-01-05 | C|723|x0.5 | OFF -> NEW | 13w mean 93 26w 109 $/wk
2026-01-05 | D|663|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 3,060 13w 1,807 26w 1,307 $/wk
2026-01-05 | C|723|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,137 13w 460 26w 669 $/wk
2026-01-05 | D|466|x1.5 | RISING -> STABLE | CUSUM 1.0 sig, z4 -0.4, 4w -1,595 13w 1,800 26w 924 $/wk
2026-01-05 | D|666|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 2,284 13w 1,006 26w 803 $/wk
2026-01-05 | C|719|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +2.8, 4w 1,701 13w 617 26w 296 $/wk
2026-01-05 | D|668|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +1.0, 4w 1,837 13w 585 26w 499 $/wk
2026-01-05 | C|885|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 32 26w 148 $/wk
2026-01-05 | L|U6|M|ls|1|q20|x0.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.6, 4w 813 13w 250 26w 173 $/wk
2026-01-05 | C|527|x0.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 5 13w 287 26w 486 $/wk
2026-01-05 | D|460|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 6,573 13w 4,752 26w 3,547 $/wk
2026-01-05 | D|676|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 915 13w 2,583 26w 1,346 $/wk
2026-01-05 | D|659|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 921 13w 637 26w 460 $/wk
2026-01-05 | D|560|take | NEW -> FADING | CUSUM 0.4 sig, z4 +0.1, 4w 290 13w -251 26w -457 $/wk
2026-01-05 | D|656|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 619 13w 623 26w 542 $/wk
2026-01-05 | L|P6|M|ls|5|q10|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 684 26w 1,397 $/wk
2026-01-05 | C|5|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 2,173 13w 1,152 26w 652 $/wk
2026-01-05 | L|M6|M|ls|5|q10|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 1,242 13w 954 26w 711 $/wk
2026-01-05 | C|770|x0.5 | RISING -> STABLE | CUSUM 0.3 sig, z4 -1.0, 4w -816 13w 487 26w 152 $/wk
2026-01-05 | D|290|take | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w -416 13w 984 26w 758 $/wk
2026-01-05 | L|M6|M|ls|4|q20|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,854 13w 1,375 26w 408 $/wk
2026-01-05 | L|U6|M|real|0|q30|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 824 13w 538 26w 316 $/wk
2026-01-05 | D|588|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w -3 13w 325 26w 652 $/wk
2026-01-05 | C|7|skip | STABLE -> STOPPED | CUSUM 1.0 sig, z4 -1.3, 4w -2,326 13w -49 26w 226 $/wk
2026-01-05 | D|279|take | NEW -> FADING | CUSUM 0.0 sig, z4 -0.4, 4w -706 13w 294 26w 918 $/wk
2026-01-05 | D|655|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 914 13w 257 26w 67 $/wk
2026-01-05 | HR|book|AND:z20_1.5:map_dow|ses|0 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 5 $/wk
2026-01-05 | D|586|take | NEW -> STOPPED | CUSUM 0.8 sig, z4 +0.0, 4w -101 13w -572 26w -172 $/wk
2026-01-05 | L|A6|M|fs|3|q30|x0.5 | OFF -> NEW | 13w mean 23 26w 119 $/wk
2026-01-05 | D|152|x1.5 | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.6, 4w 3,004 13w 9,182 26w 6,621 $/wk
2026-01-05 | C|499|skip | NEW -> STOPPED | CUSUM 1.2 sig, z4 +0.1, 4w -85 13w -600 26w -384 $/wk
2026-01-05 | D|150|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 12,376 13w 7,842 26w 8,598 $/wk
2026-01-05 | D|695|x1.5 | RISING -> STABLE | CUSUM 0.6 sig, z4 -0.8, 4w 306 13w 2,296 26w 1,657 $/wk
2026-01-05 | C|509|skip | OFF -> NEW | 13w mean 189 26w 8 $/wk
2026-01-05 | D|446|x1.5 | NEW -> STABLE | CUSUM 1.6 sig, z4 -0.8, 4w -4,916 13w 608 26w -350 $/wk
2026-01-05 | D|692|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +1.2, 4w 3,745 13w 1,575 26w 1,458 $/wk
2026-01-05 | D|452|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 4,542 13w 1,218 26w 944 $/wk
2026-01-05 | D|677|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 619 13w 971 26w 741 $/wk
2026-01-05 | D|449|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 610 26w 877 $/wk
2026-01-05 | D|678|x1.5 | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.5, 4w 311 13w 1,388 26w 878 $/wk
2026-01-05 | D|436|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 610 26w 791 $/wk
2026-01-05 | HR|book|AND:z20_1.5:map_dow|day|0 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 5 $/wk
2026-01-05 | C|31|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 434 13w 325 26w 229 $/wk
2026-01-05 | D|451|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 6,086 13w 4,456 26w 3,203 $/wk
2026-01-05 | D|696|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 2,160 13w 1,499 26w 1,178 $/wk
2026-01-05 | D|694|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 1,217 13w 2,247 26w 1,452 $/wk
2026-01-12 | D|255|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 460 13w 190 26w 770 $/wk
2026-01-12 | D|974|x1.5 | STABLE -> STOPPED | CUSUM 6.0 sig, z4 -3.2, 4w -1,097 13w 70 26w 35 $/wk
2026-01-12 | C|68|x0.5 | OFF -> NEW | 13w mean 616 26w 3 $/wk
2026-01-12 | C|5|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 308 13w 317 26w 254 $/wk
2026-01-12 | D|290|take | STABLE -> STOPPED | CUSUM 1.1 sig, z4 -0.4, 4w -1,767 13w -616 26w 121 $/wk
2026-01-12 | C|195|skip | RISING -> STABLE | CUSUM 0.3 sig, z4 -1.0, 4w -396 13w 997 26w 763 $/wk
2026-01-12 | D|312|x1.5 | OFF -> NEW | 13w mean 1,116 26w 298 $/wk
2026-01-12 | C|195|x0.5 | RISING -> STABLE | CUSUM 0.3 sig, z4 -0.5, 4w -314 13w 177 26w 136 $/wk
2026-01-12 | L|M6|M|ls|4|q30|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 466 13w 281 26w 71 $/wk
2026-01-12 | HR|book|AND:streak4:map_daytype|ses|0 | OFF -> NEW | 13w mean 284 26w 189 $/wk
2026-01-12 | L|M6|M|ls|5|q10|skip | RISING -> FADING | CUSUM 0.0 sig, z4 +0.6, 4w 1,548 13w -139 26w 711 $/wk
2026-01-12 | L|M6|M|ls|5|q10|x0.5 | OFF -> NEW | 13w mean 3 26w 36 $/wk
2026-01-12 | L|H6|M|ls|6|q10|skip | RISING -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 106 26w 337 $/wk
2026-01-12 | C|5|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.6, 4w 1,550 13w 867 26w 700 $/wk
2026-01-12 | L|H6|M|ls|4|q10|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 283 26w 2 $/wk
2026-01-12 | D|958|take | FADING -> STOPPED | CUSUM 1.4 sig, z4 -1.1, 4w -2,031 13w -475 26w 363 $/wk
2026-01-12 | C|193|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 133 13w 81 26w 41 $/wk
2026-01-12 | D|279|take | FADING -> STOPPED | CUSUM 1.0 sig, z4 -0.9, 4w -3,105 13w -1,100 26w 220 $/wk
2026-01-12 | C|7|skip | STOPPED -> NEW | 13w mean 122 26w 454 $/wk
2026-01-12 | L|A6|M|fs|3|q30|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 9 13w 23 26w 119 $/wk
2026-01-12 | L|U6|M|ls|1|q30|x0.5 | OFF -> NEW | 13w mean 93 26w 47 $/wk
2026-01-12 | C|21|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 819 26w 549 $/wk
2026-01-12 | C|21|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w 0 13w 556 26w 324 $/wk
2026-01-12 | C|28|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 617 13w -73 26w 676 $/wk
2026-01-12 | D|156|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -1.6, 4w 495 13w 18,113 26w 15,580 $/wk
2026-01-12 | HR|book|rs30_5|n2|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -1,695 13w 1,285 26w 288 $/wk
2026-01-12 | L|U6|M|ls|2|q10|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 284 26w 142 $/wk
2026-01-12 | C|31|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w -758 13w 374 26w 183 $/wk
2026-01-12 | C|18|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 285 26w 428 $/wk
2026-01-12 | L|K6|M|fs|1|q10|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 0 26w 144 $/wk
2026-01-12 | C|16|skip | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -375 13w -223 26w 684 $/wk
2026-01-12 | C|192|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w 0 13w 121 26w 720 $/wk
2026-01-12 | L|U6|M|fs|1|q30|x0.5 | NEW -> STABLE | CUSUM 0.3 sig, z4 -0.2, 4w -285 13w 458 26w 1 $/wk
2026-01-12 | L|K6|M|fs|3|q10|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 617 13w 456 26w 113 $/wk
2026-01-12 | HR|book|rs30_5|ses|0 | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -2,575 13w -126 26w -87 $/wk
2026-01-12 | L|A6|M|fs|1|q20|x0.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.1, 4w 0 13w 0 26w -46 $/wk
2026-01-12 | C|764|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 787 13w 610 26w 81 $/wk
2026-01-12 | D|585|take | NEW -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,269 13w 987 26w 645 $/wk
2026-01-12 | D|457|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 1,512 13w 2,283 26w 1,508 $/wk
2026-01-12 | D|104|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 3,382 13w 1,486 26w 838 $/wk
2026-01-12 | U|H6|x2 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 7,841 13w 9,861 26w 7,440 $/wk
2026-01-12 | D|563|x1.5 | FADING -> STOPPED | CUSUM 1.4 sig, z4 -0.2, 4w -308 13w -19 26w 65 $/wk
2026-01-12 | D|453|x1.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 4,661 13w 2,552 26w 1,215 $/wk
2026-01-12 | D|563|take | NEW -> STABLE | CUSUM 1.2 sig, z4 -0.6, 4w -3,309 13w 1,201 26w -687 $/wk
2026-01-12 | D|588|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 908 13w 794 26w 792 $/wk
2026-01-12 | HR|book|reg_ci_30|rev|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w -396 13w 184 26w 190 $/wk
2026-01-12 | C|513|skip | NEW -> STOPPED | CUSUM 1.9 sig, z4 -1.2, 4w -5,465 13w -533 26w -726 $/wk
2026-01-12 | D|451|x1.5 | RISING -> STABLE | CUSUM 0.2 sig, z4 -0.1, 4w 2,315 13w 3,850 26w 2,672 $/wk
2026-01-12 | C|501|x0.5 | FADING -> STOPPED | CUSUM 0.5 sig, z4 -0.4, 4w -582 13w -170 26w 63 $/wk
2026-01-12 | D|696|x1.5 | RISING -> STABLE | CUSUM 0.4 sig, z4 -0.4, 4w 299 13w 1,303 26w 915 $/wk
2026-01-12 | C|478|skip | STABLE -> FADING | CUSUM 0.2 sig, z4 -0.3, 4w -607 13w 4 26w 55 $/wk
2026-01-12 | HR|book|ddd5_8|mon|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 1,122 26w 636 $/wk
2026-01-12 | C|467|skip | FADING -> STABLE | CUSUM 0.3 sig, z4 -0.2, 4w -138 13w 202 26w 244 $/wk
2026-01-12 | C|895|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w 0 13w 822 26w 364 $/wk
2026-01-12 | D|421|x1.5 | OFF -> NEW | 13w mean 84 26w 363 $/wk
2026-01-12 | C|761|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 338 13w 379 26w 214 $/wk
2026-01-12 | C|872|x0.5 | OFF -> NEW | 13w mean 3 26w 95 $/wk
2026-01-12 | C|864|skip | NEW -> STABLE | CUSUM 1.1 sig, z4 -1.0, 4w -456 13w 475 26w 140 $/wk
2026-01-12 | C|526|skip | NEW -> STABLE | CUSUM 1.6 sig, z4 -0.6, 4w -1,185 13w 1,107 26w 297 $/wk
2026-01-12 | D|589|x1.5 | OFF -> NEW | 13w mean 417 26w 784 $/wk
2026-01-12 | C|746|skip | OFF -> NEW | 13w mean 84 26w 9 $/wk
2026-01-12 | D|560|take | FADING -> STOPPED | CUSUM 1.2 sig, z4 -0.5, 4w -3,331 13w -786 26w -863 $/wk
2026-01-12 | D|655|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 151 26w 67 $/wk
2026-01-12 | HR|book|AND:streak4:map_vol|w2|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-12 | C|735|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,870 13w 976 26w 536 $/wk
2026-01-12 | D|659|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 302 13w 720 26w 321 $/wk
2026-01-12 | C|845|skip | NEW -> FADING | CUSUM 0.6 sig, z4 -0.3, 4w -149 13w 77 26w 189 $/wk
2026-01-12 | D|547|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.3, 4w 302 13w 275 26w 560 $/wk
2026-01-12 | HR|book|AND:wk2_3:reg_er_60|day|0 | STOPPED -> NEW | 13w mean 404 26w 998 $/wk
2026-01-12 | C|750|skip | OFF -> NEW | 13w mean 1,719 26w 169 $/wk
2026-01-12 | D|663|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 1,523 13w 1,995 26w 1,180 $/wk
2026-01-12 | HR|book|z20_2.0|n5|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 392 26w 335 $/wk
2026-01-12 | D|666|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,053 13w 1,290 26w 708 $/wk
2026-01-12 | C|719|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 490 13w 712 26w 343 $/wk
2026-01-12 | C|719|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 482 13w 749 26w 172 $/wk
2026-01-12 | D|463|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.7, 4w -1,686 13w 1,416 26w 3,669 $/wk
2026-01-12 | C|613|x0.5 | FADING -> STABLE | CUSUM 0.8 sig, z4 -0.8, 4w -314 13w 214 26w 104 $/wk
2026-01-12 | HR|book|L:sh2:0.6|mem|0 | OFF -> NEW | 13w mean 676 26w 250 $/wk
2026-01-12 | D|706|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.6, 4w 2,932 13w 2,956 26w 1,594 $/wk
2026-01-12 | D|452|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 3,439 13w 1,386 26w 1,397 $/wk
2026-01-12 | D|713|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.1, 4w 1,829 13w 409 26w 443 $/wk
2026-01-12 | D|804|take | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.4, 4w -448 13w 34 26w 155 $/wk
2026-01-12 | D|402|x1.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 2,210 13w 1,251 26w 1,096 $/wk
2026-01-12 | C|243|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.7, 4w 309 13w -68 26w 126 $/wk
2026-01-12 | D|715|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 910 13w 1,248 26w 913 $/wk
2026-01-12 | D|88|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,305 13w 764 26w 554 $/wk
2026-01-12 | D|572|take | NEW -> STABLE | CUSUM 0.7 sig, z4 -0.3, 4w -1,388 13w 442 26w -229 $/wk
2026-01-12 | C|338|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 1,552 13w 1,142 26w 517 $/wk
2026-01-12 | HR|book|map_dow|mem|0 | OFF -> NEW | 13w mean 1,457 26w 304 $/wk
2026-01-12 | L|U6|M|fs|3|q30|x0.5 | FADING -> STOPPED | CUSUM 0.1 sig, z4 -0.2, 4w -161 13w -48 26w 73 $/wk
2026-01-12 | C|229|x0.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.9, 4w -805 13w 307 26w 657 $/wk
2026-01-12 | D|86|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.7, 4w 2,779 13w 864 26w 936 $/wk
2026-01-19 | D|667|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 1,819 13w 708 26w 547 $/wk
2026-01-19 | L|U6|M|real|0|q20|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.1, 4w 824 13w 253 26w 127 $/wk
2026-01-19 | C|719|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 1,672 13w 1,211 26w 403 $/wk
2026-01-19 | D|463|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w -311 13w 3,212 26w 4,169 $/wk
2026-01-19 | D|158|x1.5 | STABLE -> FADING | CUSUM 1.8 sig, z4 -1.2, 4w -4,554 13w 2,618 26w 6,334 $/wk
2026-01-19 | C|20|skip | FADING -> STOPPED | CUSUM 0.8 sig, z4 -0.7, 4w -443 13w -252 26w 31 $/wk
2026-01-19 | D|290|x1.5 | STABLE -> FADING | CUSUM 0.1 sig, z4 -0.3, 4w 220 13w 87 26w 608 $/wk
2026-01-19 | D|403|x1.5 | RISING -> STABLE | CUSUM 0.2 sig, z4 +0.1, 4w 386 13w 679 26w 242 $/wk
2026-01-19 | HR|book|z10_2.0|n5|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w -295 13w 1,051 26w 679 $/wk
2026-01-19 | L|U6|M|ls|1|q20|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 813 13w 250 26w 173 $/wk
2026-01-19 | D|673|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,205 13w 933 26w 510 $/wk
2026-01-19 | C|20|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 309 13w 95 26w 47 $/wk
2026-01-19 | L|A6|M|fs|3|q30|x0.5 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.4, 4w 308 13w 115 26w 119 $/wk
2026-01-19 | D|586|take | OFF -> NEW | 13w mean 131 26w 467 $/wk
2026-01-19 | C|517|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 510 13w 2,112 26w 493 $/wk
2026-01-19 | HR|book|AND:wk2_3:reg_er_60|day|0 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.0, 4w 1,378 13w 373 26w 976 $/wk
2026-01-19 | D|706|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 4,550 13w 2,956 26w 1,877 $/wk
2026-01-19 | D|588|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,580 13w 1,168 26w 709 $/wk
2026-01-19 | D|589|take | OFF -> NEW | 13w mean 1,714 26w 800 $/wk
2026-01-19 | D|104|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 3,382 13w 831 26w 838 $/wk
2026-01-19 | C|746|skip | NEW -> FADING | CUSUM 0.4 sig, z4 +1.6, 4w 1,679 13w -103 26w -66 $/wk
2026-01-19 | L|U6|M|ls|1|q10|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 813 13w 250 26w 125 $/wk
2026-01-19 | L|P6|M|ls|6|q20|skip | STABLE -> STOPPED | CUSUM 0.9 sig, z4 -0.5, 4w -1,395 13w -1 26w 2,663 $/wk
2026-01-19 | D|88|x1.5 | RISING -> STABLE | CUSUM 0.5 sig, z4 -0.2, 4w -238 13w 289 26w 317 $/wk
2026-01-19 | C|7|skip | NEW -> STOPPED | CUSUM 0.0 sig, z4 -0.3, 4w -110 13w -81 26w 399 $/wk
2026-01-19 | D|655|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 299 13w 243 26w 113 $/wk
2026-01-19 | L|P6|M|ls|5|q10|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 1,223 13w 1,060 26w 1,917 $/wk
2026-01-19 | L|U6|Q|real|0|q10|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.9, 4w 824 13w 253 26w 127 $/wk
2026-01-19 | C|735|skip | RISING -> STABLE | CUSUM 0.5 sig, z4 -0.1, 4w 304 13w 683 26w 437 $/wk
2026-01-19 | C|196|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-19 | C|229|x0.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.8, 4w -645 13w 356 26w 681 $/wk
2026-01-19 | C|731|x0.5 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-19 | C|5|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 617 13w 317 26w 210 $/wk
2026-01-19 | L|K6|M|fs|3|q10|skip | RISING -> STABLE | CUSUM 0.8 sig, z4 -0.2, 4w -307 13w 172 26w -30 $/wk
2026-01-19 | C|845|skip | FADING -> STOPPED | CUSUM 0.2 sig, z4 -0.3, 4w -149 13w -15 26w 189 $/wk
2026-01-19 | D|108|x1.5 | STABLE -> FADING | CUSUM 3.0 sig, z4 -1.8, 4w -12,995 13w 4,792 26w 6,897 $/wk
2026-01-19 | D|678|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 2,356 13w 2,113 26w 1,196 $/wk
2026-01-19 | C|338|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 1,142 26w 508 $/wk
2026-01-19 | HR|book|ddd5_8|n5|0 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 1,657 26w 730 $/wk
2026-01-19 | C|5|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.1, 4w 2,173 13w 773 26w 515 $/wk
2026-01-19 | C|47|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 308 13w 191 26w 144 $/wk
2026-01-19 | D|694|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,884 13w 3,527 26w 1,841 $/wk
2026-01-19 | D|695|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 3,280 13w 3,221 26w 2,260 $/wk
2026-01-19 | L|U6|M|real|0|q10|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 824 13w 253 26w 127 $/wk
2026-01-19 | C|52|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 2,243 13w 2,048 26w 839 $/wk
2026-01-19 | D|438|x1.5 | OFF -> NEW | 13w mean 274 26w 377 $/wk
2026-01-19 | D|711|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +3.5, 4w 6,933 13w 2,706 26w 1,997 $/wk
2026-01-19 | C|362|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 875 13w 2,738 26w 1,190 $/wk
2026-01-19 | HR|book|rs30_5|ses|2 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w -4,269 13w 106 26w -239 $/wk
2026-01-19 | D|974|x1.5 | STOPPED -> NEW | 13w mean 70 26w 35 $/wk
2026-01-19 | C|480|x0.5 | OFF -> NEW | 13w mean 597 26w 373 $/wk
2026-01-19 | D|569|take | OFF -> NEW | 13w mean 213 26w 81 $/wk
2026-01-19 | C|62|skip | OFF -> NEW | 13w mean 22 26w 114 $/wk
2026-01-19 | L|U6|M|ls|6|q30|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 642 13w 530 26w 268 $/wk
2026-01-19 | D|708|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.1, 4w 3,891 13w 2,024 26w 1,352 $/wk
2026-01-19 | D|421|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w 272 13w 84 26w 363 $/wk
2026-01-19 | C|396|x0.5 | NEW -> STABLE | CUSUM 0.4 sig, z4 -0.7, 4w -2,245 13w 560 26w 819 $/wk
2026-01-19 | C|901|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 308 13w 275 26w 8 $/wk
2026-01-19 | L|H6|M|ls|1|q20|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 217 26w 17 $/wk
2026-01-19 | D|572|take | STABLE -> STOPPED | CUSUM 0.9 sig, z4 -1.1, 4w -4,555 13w -504 26w -436 $/wk
2026-01-19 | C|368|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 4,668 13w 3,997 26w 1,427 $/wk
2026-01-19 | L|M6|M|ls|5|q10|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.3, 4w 159 13w 3 26w 36 $/wk
2026-01-19 | D|290|take | STOPPED -> NEW | 13w mean 585 26w 270 $/wk
2026-01-19 | D|585|take | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 1,882 13w 1,168 26w 1,020 $/wk
2026-01-19 | HR|book|reg_xasset_120|day|0 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.5, 4w 6,992 13w 887 26w 2,306 $/wk
2026-01-19 | D|109|x1.5 | STABLE -> FADING | CUSUM 0.5 sig, z4 -0.6, 4w -216 13w 324 26w 4,634 $/wk
2026-01-19 | C|872|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +1.1, 4w 308 13w 3 26w 48 $/wk
2026-01-19 | L|A6|M|fs|1|q20|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 308 13w 95 26w 1 $/wk
2026-01-19 | D|715|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 1,820 13w 1,530 26w 1,053 $/wk
2026-01-19 | D|453|x1.5 | RISING -> STABLE | CUSUM 1.5 sig, z4 -0.2, 4w -400 13w 1,081 26w 616 $/wk
2026-01-19 | L|M6|M|ls|1|q10|x0.5 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 309 13w 95 26w 48 $/wk
2026-01-19 | L|U6|M|fs|2|q10|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w -607 13w 3 26w 1 $/wk
2026-01-19 | D|150|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w 3,810 13w 4,438 26w 8,890 $/wk
2026-01-19 | C|874|x0.5 | OFF -> NEW | 13w mean 33 26w 100 $/wk
2026-01-19 | L|U6|M|ls|2|q20|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 379 26w 50 $/wk
2026-01-19 | L|A6|M|ls|6|q20|x0.5 | OFF -> NEW | 13w mean 3 26w 5 $/wk
2026-01-26 | HR|stack|wk4_2|hi|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|AND:streak4:map_vol|mem|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|AND:z20_1.5:reg_xasset_60|mem|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 1,525 13w 469 26w 282 $/wk
2026-01-26 | HR|stack|wk4_5|p5|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|AND:streak4:map_vol|w2|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | T|K6|q20|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 456 13w 556 26w 512 $/wk
2026-01-26 | HR|book|wk4_5|day|0 | OFF -> NEW | 13w mean 296 26w 135 $/wk
2026-01-26 | T|U6|q20|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 813 13w 1,103 26w 599 $/wk
2026-01-26 | L|U6|M|fs|1|q30|x0.5 | STABLE -> FADING | CUSUM 0.8 sig, z4 -1.1, 4w -1,200 13w 10 26w 326 $/wk
2026-01-26 | HR|book|AND:z20_1.5:reg_xasset_60|day|0 | OFF -> NEW | 13w mean 469 26w 69 $/wk
2026-01-26 | HR|book|AND:streak4:map_vol|day|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|stack|wk4_2|w2|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|stack|wk4_2|day|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | L|U6|M|ls|6|q30|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 642 13w 668 26w 268 $/wk
2026-01-26 | HR|book|OR:z20_1.5:map_dow|day|0 | OFF -> NEW | 13w mean 2,136 26w 212 $/wk
2026-01-26 | HR|book|ddd5_8|mon|0 | STABLE -> FADING | CUSUM 2.3 sig, z4 -1.4, 4w -3,159 13w 150 26w 150 $/wk
2026-01-26 | L|U6|M|ls|2|q20|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 924 13w 664 26w 192 $/wk
2026-01-26 | HR|book|AND:streak4:map_vol|ses|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|reg_ci_30|rev|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 1,717 13w 754 26w 380 $/wk
2026-01-26 | HR|book|rs30_5|n2|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 2,013 13w 1,916 26w 1,019 $/wk
2026-01-26 | HR|book|L:sh2:0.65|mem|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | U|H6|x2 | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.0, 4w 19,485 13w 11,777 26w 9,061 $/wk
2026-01-26 | HR|book|AND:z20_1.5:map_vol|ses|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|AND:wk2_3:reg_er_60|day|0 | FADING -> NEW | CUSUM 0.0 sig, z4 +0.2, 4w 3,231 13w 943 26w 1,261 $/wk
2026-01-26 | HR|book|z10_2.0|n5|0 | STABLE -> FADING | CUSUM 0.8 sig, z4 -0.7, 4w -3,186 13w 71 26w 189 $/wk
2026-01-26 | HR|book|AND:z20_1.5:reg_ci_60|w2|0 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-01-26 | HR|book|rs30_5|ses|0 | OFF -> NEW | 13w mean 417 26w 371 $/wk
2026-01-26 | HR|book|reg_xasset_120|day|0 | FADING -> STABLE | CUSUM 1.2 sig, z4 -0.1, 4w 532 13w 2,014 26w 1,363 $/wk
2026-01-26 | D|584|take | NEW -> RISING | CUSUM 0.3 sig, z4 +0.3, 4w 880 13w 454 26w 243 $/wk
2026-01-26 | D|677|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.7, 4w 2,765 13w 1,715 26w 1,099 $/wk
2026-01-26 | D|559|take | OFF -> NEW | 13w mean 935 26w 1 $/wk
2026-01-26 | C|845|skip | STOPPED -> NEW | 13w mean 79 26w 150 $/wk
2026-01-26 | C|762|skip | OFF -> NEW | 13w mean 280 26w 80 $/wk
2026-01-26 | D|562|x1.5 | OFF -> NEW | 13w mean 7 26w 616 $/wk
2026-01-26 | D|563|x1.5 | OFF -> NEW | 13w mean 258 26w 250 $/wk
2026-01-26 | C|746|skip | FADING -> NEW | CUSUM 0.0 sig, z4 +2.2, 4w 2,606 13w 278 26w 171 $/wk
2026-01-26 | D|567|take | NEW -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 1,627 13w 764 26w 36 $/wk
2026-01-26 | C|737|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,496 13w 2,301 26w 1,021 $/wk
2026-01-26 | D|581|take | NEW -> STABLE | CUSUM 0.2 sig, z4 -0.6, 4w -3,548 13w 1,510 26w 35 $/wk
2026-01-26 | D|586|take | NEW -> FADING | CUSUM 0.0 sig, z4 -0.6, 4w -2,142 13w 240 26w 545 $/wk
2026-01-26 | D|656|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 1,537 13w 1,534 26w 547 $/wk
2026-01-26 | D|659|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 1,839 13w 1,738 26w 560 $/wk
2026-01-26 | D|660|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 2,812 13w 1,735 26w 878 $/wk
2026-01-26 | D|664|x1.5 | OFF -> NEW | 13w mean 78 26w 421 $/wk
2026-01-26 | C|519|x0.5 | OFF -> NEW | 13w mean 228 26w 197 $/wk
2026-01-26 | D|676|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.6, 4w 4,635 13w 3,637 26w 2,015 $/wk
2026-01-26 | D|150|x1.5 | FADING -> STABLE | CUSUM 0.8 sig, z4 -0.8, 4w -1,044 13w 3,553 26w 6,952 $/wk
2026-01-26 | D|682|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 2,230 13w 1,697 26w 1,095 $/wk
2026-01-26 | C|515|skip | FADING -> STOPPED | CUSUM 2.7 sig, z4 -2.0, 4w -4,261 13w -925 26w 699 $/wk
2026-01-26 | D|691|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 5,527 13w 4,780 26w 3,490 $/wk
2026-01-26 | C|506|x0.5 | STABLE -> FADING | CUSUM 2.3 sig, z4 -1.2, 4w -1,880 13w 495 26w 555 $/wk
2026-01-26 | C|874|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +0.9, 4w 405 13w 33 26w 100 $/wk
2026-01-26 | D|156|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.4, 4w 11,005 13w 20,489 26w 15,295 $/wk
2026-01-26 | D|158|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.6, 4w 1,934 13w 5,089 26w 7,067 $/wk
2026-01-26 | D|255|x1.5 | FADING -> STABLE | CUSUM 0.8 sig, z4 -0.7, 4w -976 13w 690 26w 573 $/wk
2026-01-26 | D|108|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.5, 4w 3,168 13w 6,801 26w 8,397 $/wk
2026-01-26 | D|86|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +2.0, 4w 6,207 13w 1,621 26w 1,198 $/wk
2026-01-26 | C|888|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 308 13w 230 26w 19 $/wk
2026-01-26 | C|878|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.8, 4w 923 13w 553 26w 199 $/wk
2026-01-26 | D|415|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 603 13w 185 26w 285 $/wk
2026-01-26 | D|452|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 1,613 13w 1,439 26w 814 $/wk
2026-01-26 | C|502|x0.5 | FADING -> STOPPED | CUSUM 1.0 sig, z4 -1.1, 4w -914 13w -186 26w 470 $/wk
2026-01-26 | C|357|skip | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.0, 4w 1,478 13w 1,956 26w 1,342 $/wk
2026-01-26 | C|30|x0.5 | STABLE -> STOPPED | CUSUM 0.0 sig, z4 -0.2, 4w -242 13w -203 26w 370 $/wk
2026-01-26 | L|A6|M|real|0|q30|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.3, 4w 853 13w 341 26w 510 $/wk
2026-01-26 | C|397|x0.5 | OFF -> NEW | 13w mean 550 26w 772 $/wk
2026-01-26 | C|368|skip | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 3,456 13w 3,624 26w 1,241 $/wk
2026-01-26 | L|A6|M|fs|3|q20|skip | OFF -> NEW | 13w mean 144 26w 25 $/wk
2026-01-26 | C|243|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.5, 4w 912 13w 302 26w 530 $/wk
2026-01-26 | D|958|take | OFF -> NEW | 13w mean 114 26w 501 $/wk
2026-01-26 | D|974|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 -3.2, 4w -1,097 13w 70 26w 35 $/wk
2026-01-26 | C|20|skip | STOPPED -> NEW | 13w mean 286 26w 300 $/wk
2026-01-26 | L|A6|M|real|0|q30|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 273 13w 172 26w 100 $/wk
2026-01-26 | D|707|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 3,207 13w 1,681 26w 1,306 $/wk
2026-01-26 | D|712|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 2,750 13w 1,654 26w 922 $/wk
2026-01-26 | D|713|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.3, 4w 2,154 13w 1,033 26w 431 $/wk
2026-01-26 | D|714|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.5, 4w 5,910 13w 4,822 26w 2,783 $/wk
2026-01-26 | C|7|skip | STOPPED -> NEW | 13w mean 14 26w 397 $/wk
2026-01-26 | C|14|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.1, 4w 329 13w 222 26w 140 $/wk
2026-01-26 | C|192|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 1,105 13w 670 26w 994 $/wk
2026-01-26 | D|804|take | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 242 26w 155 $/wk
2026-01-26 | L|P6|M|ls|6|q20|skip | STOPPED -> NEW | 13w mean 2,160 26w 3,254 $/wk
2026-01-26 | C|19|skip | FADING -> STOPPED | CUSUM 0.0 sig, z4 -0.7, 4w -598 13w -65 26w 678 $/wk
2026-02-02 | D|130|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.8, 4w -286 13w 289 26w 749 $/wk
2026-02-02 | C|5|skip | RISING -> STABLE | CUSUM 0.6 sig, z4 -0.3, 4w 9 13w 640 26w 468 $/wk
2026-02-02 | HR|book|AND:ddt20_5:reg_ci_60|ses|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-02-02 | D|109|x1.5 | FADING -> STABLE | CUSUM 0.1 sig, z4 +0.1, 4w 6,259 13w 3,257 26w 5,813 $/wk
2026-02-02 | C|885|x0.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 288 13w 210 26w 190 $/wk
2026-02-02 | C|72|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.4, 4w 3,040 13w 2,917 26w 842 $/wk
2026-02-02 | C|47|x0.5 | RISING -> FADING | CUSUM 0.0 sig, z4 +0.3, 4w 923 13w 95 26w 286 $/wk
2026-02-02 | C|5|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 309 13w 369 26w 210 $/wk
2026-02-02 | HR|book|ddd5_8|mon|0 | FADING -> STABLE | CUSUM 2.0 sig, z4 -1.4, 4w -3,159 13w 150 26w 150 $/wk
2026-02-02 | D|88|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.5, 4w -1,301 13w 177 26w 393 $/wk
2026-02-02 | D|97|x1.5 | STABLE -> FADING | CUSUM 2.9 sig, z4 -2.4, 4w -11,130 13w 1,095 26w 3,020 $/wk
2026-02-02 | C|19|skip | STOPPED -> NEW | 13w mean 492 26w 264 $/wk
2026-02-02 | C|7|skip | NEW -> FADING | CUSUM 0.0 sig, z4 +0.2, 4w 806 13w 14 26w 397 $/wk
2026-02-02 | HR|book|AND:rs10_3:reg_ci_60|ses|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-02-02 | C|31|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 1,253 13w 853 26w 356 $/wk
2026-02-02 | C|30|x0.5 | STOPPED -> NEW | 13w mean 2,149 26w 806 $/wk
2026-02-02 | C|16|skip | OFF -> NEW | 13w mean 3,318 26w 1,517 $/wk
2026-02-02 | D|104|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,952 13w 1,506 26w 838 $/wk
2026-02-02 | C|502|x0.5 | STOPPED -> NEW | 13w mean 236 26w 682 $/wk
2026-02-02 | C|504|x0.5 | OFF -> NEW | 13w mean 80 26w 243 $/wk
2026-02-02 | C|506|x0.5 | FADING -> STABLE | CUSUM 1.4 sig, z4 -0.6, 4w -742 13w 728 26w 531 $/wk
2026-02-02 | C|507|skip | OFF -> NEW | 13w mean 1,763 26w 153 $/wk
2026-02-02 | C|509|skip | NEW -> RISING | CUSUM 0.0 sig, z4 +1.8, 4w 4,789 13w 1,478 26w 743 $/wk
2026-02-02 | C|513|skip | OFF -> NEW | 13w mean 1,349 26w 581 $/wk
2026-02-02 | C|499|skip | OFF -> NEW | 13w mean 11 26w 130 $/wk
2026-02-02 | C|515|skip | STOPPED -> NEW | 13w mean 725 26w 1,430 $/wk
2026-02-02 | C|517|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.8, 4w 8,688 13w 4,351 26w 1,733 $/wk
2026-02-02 | C|489|skip | OFF -> NEW | 13w mean 991 26w 311 $/wk
2026-02-02 | HR|book|AND:rs10_3:reg_ci_60|mem|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-02-02 | C|526|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,602 13w 2,430 26w 1,033 $/wk
2026-02-02 | C|478|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.0, 4w 3,186 13w 1,171 26w 1,010 $/wk
2026-02-02 | C|527|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 2,816 13w 1,712 26w 1,066 $/wk
2026-02-02 | C|613|x0.5 | STABLE -> STOPPED | CUSUM 0.8 sig, z4 -1.3, 4w -633 13w -100 26w 7 $/wk
2026-02-02 | C|196|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 46 26w 23 $/wk
2026-02-02 | C|472|skip | OFF -> NEW | 13w mean 847 26w 319 $/wk
2026-02-02 | C|719|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.4, 4w 1,230 13w 1,092 26w 485 $/wk
2026-02-02 | C|723|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.6, 4w 1,837 13w 1,216 26w 766 $/wk
2026-02-02 | C|467|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 2,436 13w 1,689 26w 614 $/wk
2026-02-02 | C|723|x0.5 | NEW -> RISING | CUSUM 0.0 sig, z4 +0.7, 4w 905 13w 510 26w 210 $/wk
2026-02-02 | C|737|skip | RISING -> STABLE | CUSUM 0.1 sig, z4 +0.1, 4w 1,397 13w 2,787 26w 1,055 $/wk
2026-02-02 | C|739|skip | OFF -> NEW | 13w mean 1,033 26w 334 $/wk
2026-02-02 | C|397|x0.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +1.4, 4w 6,299 13w 479 26w 1,189 $/wk
2026-02-02 | C|751|skip | OFF -> NEW | 13w mean 946 26w 461 $/wk
2026-02-02 | C|760|skip | OFF -> NEW | 13w mean 1,251 26w 404 $/wk
2026-02-02 | C|357|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 5,697 13w 3,254 26w 1,657 $/wk
2026-02-02 | C|501|x0.5 | OFF -> NEW | 13w mean 168 26w 184 $/wk
2026-02-02 | HR|book|z10_2.0|n5|0 | FADING -> STABLE | CUSUM 0.5 sig, z4 -0.6, 4w -3,186 13w 344 26w -122 $/wk
2026-02-02 | C|354|x0.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 3,255 13w 2,814 26w 654 $/wk
2026-02-02 | HR|book|AND:rs20_3:reg_ci_60|day|0 | FADING -> RISING | CUSUM 0.0 sig, z4 +0.0, 4w 0 13w 0 26w 0 $/wk
2026-02-02 | L|H6|M|ls|6|q10|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 294 26w 337 $/wk
2026-02-02 | D|402|x1.5 | STABLE -> FADING | CUSUM 1.5 sig, z4 -0.9, 4w -2,040 13w 141 26w 469 $/wk
2026-02-02 | D|150|x1.5 | STABLE -> FADING | CUSUM 1.5 sig, z4 -1.2, 4w -5,170 13w 1,844 26w 6,736 $/wk
2026-02-02 | L|U6|M|fs|3|q30|x0.5 | OFF -> NEW | 13w mean 236 26w 262 $/wk
2026-02-02 | D|804|take | STABLE -> STOPPED | CUSUM 0.5 sig, z4 -0.5, 4w -611 13w -136 26w 109 $/wk
2026-02-02 | L|U6|Q|real|0|q10|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 253 26w 127 $/wk
2026-02-02 | D|706|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.3, 4w 4,660 13w 2,041 26w 1,831 $/wk
2026-02-02 | D|696|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.7, 4w 4,165 13w 3,082 26w 1,238 $/wk
2026-02-02 | D|695|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +2.6, 4w 7,764 13w 3,176 26w 3,045 $/wk
2026-02-02 | D|692|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 3,681 13w 3,231 26w 1,823 $/wk
2026-02-02 | L|U6|M|ls|6|q30|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.1, 4w 642 13w 99 26w 268 $/wk
2026-02-02 | L|M6|M|fs|3|q10|skip | OFF -> NEW | 13w mean 115 26w 57 $/wk
2026-02-02 | L|U6|M|real|0|q10|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.3, 4w 0 13w 253 26w 127 $/wk
2026-02-02 | L|M6|M|ls|4|q30|x0.5 | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.2, 4w -150 13w 112 26w 95 $/wk
2026-02-02 | L|M6|M|ls|4|q20|skip | RISING -> STABLE | CUSUM 0.1 sig, z4 -0.7, 4w -1,083 13w 522 26w 521 $/wk
2026-02-02 | L|U6|M|real|0|q20|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 308 13w 348 26w 174 $/wk
2026-02-02 | L|M6|M|ls|1|q10|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.4, 4w 309 13w 95 26w 95 $/wk
2026-02-02 | L|U6|M|real|0|q30|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 308 13w 348 26w 364 $/wk
2026-02-02 | L|P6|M|ls|6|q20|skip | NEW -> FADING | CUSUM 0.0 sig, z4 -1.0, 4w -7,270 13w 378 26w 1,562 $/wk
2026-02-02 | L|U6|M|ls|1|q10|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 0 13w 250 26w 125 $/wk
2026-02-02 | L|K6|M|real|0|q30|skip | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 880 13w 1,829 26w 892 $/wk
2026-02-02 | L|A6|M|real|0|q30|skip | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.5, 4w 853 13w 341 26w 213 $/wk
2026-02-02 | L|U6|M|ls|1|q20|x0.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.1, 4w 0 13w 250 26w 125 $/wk
2026-02-02 | L|A6|M|fs|3|q30|x0.5 | NEW -> STABLE | CUSUM 0.0 sig, z4 +0.2, 4w 252 13w 83 26w 158 $/wk
2026-02-02 | L|A6|M|fs|1|q30|skip | STABLE -> FADING | CUSUM 0.0 sig, z4 -0.0, 4w 94 13w 29 26w 100 $/wk
2026-02-02 | L|A6|M|ls|6|q30|skip | OFF -> NEW | 13w mean 167 26w 80 $/wk
2026-02-02 | D|691|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.7, 4w 7,452 13w 4,521 26w 3,863 $/wk
2026-02-02 | D|686|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.7, 4w 7,434 13w 4,933 26w 3,271 $/wk
2026-02-02 | D|446|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.2, 4w 9,554 13w 3,530 26w 2,015 $/wk
2026-02-02 | D|434|x1.5 | OFF -> NEW | 13w mean 1,043 26w 1,132 $/wk
2026-02-02 | D|410|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.3, 4w 1,369 13w 941 26w 471 $/wk
2026-02-02 | D|403|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.8, 4w 1,571 13w 1,044 26w 625 $/wk
2026-02-02 | L|M6|M|fs|3|q10|x0.5 | OFF -> NEW | 13w mean 49 26w 24 $/wk
2026-02-02 | D|319|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +1.6, 4w 8,182 13w 1,452 26w 2,226 $/wk
2026-02-02 | D|290|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 -0.2, 4w 445 13w 385 26w 715 $/wk
2026-02-02 | D|452|x1.5 | RISING -> STABLE | CUSUM 0.9 sig, z4 -0.5, 4w -364 13w 990 26w 790 $/wk
2026-02-02 | D|460|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +0.1, 4w 3,241 13w 4,245 26w 2,598 $/wk
2026-02-02 | D|466|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.2, 4w 1,381 13w 850 26w 204 $/wk
2026-02-02 | D|547|x1.5 | FADING -> STABLE | CUSUM 0.0 sig, z4 +0.8, 4w 1,213 13w 467 26w 607 $/wk
2026-02-02 | D|678|x1.5 | RISING -> STABLE | CUSUM 0.0 sig, z4 +1.8, 4w 3,893 13w 1,822 26w 1,622 $/wk
2026-02-02 | D|674|x1.5 | STABLE -> FADING | CUSUM 0.0 sig, z4 +0.0, 4w 307 13w 32 26w 306 $/wk
2026-02-02 | D|668|x1.5 | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.7, 4w 3,418 13w 1,909 26w 1,053 $/wk
2026-02-02 | D|586|take | FADING -> NEW | CUSUM 0.0 sig, z4 +0.7, 4w 4,179 13w 2,506 26w 931 $/wk
2026-02-02 | D|134|x1.5 | STABLE -> FADING | CUSUM 1.2 sig, z4 -1.5, 4w -2,893 13w 1,686 26w 1,230 $/wk
2026-02-02 | D|585|take | STABLE -> RISING | CUSUM 0.0 sig, z4 +1.0, 4w 5,019 13w 2,698 26w 1,599 $/wk
2026-02-02 | D|567|take | RISING -> STABLE | CUSUM 0.0 sig, z4 -0.0, 4w 0 13w 764 26w 36 $/wk
2026-02-02 | D|563|take | STABLE -> RISING | CUSUM 0.0 sig, z4 +0.9, 4w 5,859 13w 4,086 26w 1,321 $/wk
2026-02-02 | D|562|x1.5 | NEW -> FADING | CUSUM 0.0 sig, z4 +1.3, 4w 1,882 13w 7 26w 616 $/wk
2026-02-02 | D|560|take | OFF -> NEW | 13w mean 1,850 26w 1,030 $/wk
2026-02-02 | D|572|take | OFF -> NEW | 13w mean 2,187 26w 562 $/wk
2026-02-02 | HR|book|L:sh2:0.6|mem|0 | NEW -> FADING | CUSUM 0.0 sig, z4 -0.1, 4w -150 13w 61 26w 369 $/wk

## RE-1 ledger run 2026-10-31 (rows of RECENT_WINS.md: NEW/RISING/STABLE/FADING from the ledger; one line per transition since the previous compile)

