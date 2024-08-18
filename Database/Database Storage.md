Reading /writing to disk is expensive. So it is importance to manage them carefully so that to avoid large stalls and ppperformance degradation.

Even for the databases with terabyte of data, ideally we would like to give the appearance that everything is in memory, even though it actually isn't. 

Random Access ar disk is slower than sequential Access, so the DBMS will want to maximize sequential access.

As a DBMS, we would like to do everything by ourselves, and rely very less on OS.
# Why Not Use OS?
