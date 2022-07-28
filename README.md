#### dstat is a powerful, flexible and versatile tool for generating Linux system resource statistics

```
root@Tuttu:~# dstat
You did not select any stats, using -cdngy by default.
--total-cpu-usage-- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai stl| read  writ| recv  send|  in   out | int   csw 
  3   3  90   5   0|1030k  293k|   0     0 |   0     0 | 679    18k
 10   2  88   0   0|   0     0 |1073B 2544B|   0     0 |2140  5574 
  6   2  92   0   0|   0     0 | 395B  529B|   0     0 |1683  5256 
  7   4  90   0   0|   0     0 | 593B  811B|   0     0 |1735  5260 
  6   3  90   1   0|   0   116k| 449B 1989B|   0     0 |1695  5189 
  8   2  91   0   0|   0  8192B| 940B 1111B|   0     0 |1776  5370 
  7   2  90   1   0|   0   192k| 492B  623B|   0     0 |1691  5287 
  6   2  91   1   0|   0   224k| 569B  717B|   0     0 |1752  5286 
  7   2  91   0   0|   0     0 | 677B 2075B|   0     0 |2062  6227 
  8   3  89   0   0|   0     0 |1101B 1337B|   0     0 |1772  5158 
  5   3  90   2   0|   0   928k| 395B  572B|   0     0 |1724  4912 
  5   2  71  23   0|   0   132k| 683B 1094B|   0     0 |1599  4964 
  3   2  73  23   0|   0   144k|1598B 3131B|   0     0 |1231  3154 
  1   1  98   0   0|   0     0 |   0     0 |   0     0 | 671  1064 
  1   0  99   0   0|   0     0 |   0     0 |   0     0 | 586   948 
 13   1  86   0   0|   0    16k|   0     0 |   0     0 | 842  1418 
 22   4  74   0   0|   0     0 |   0     0 |   0     0 |1235  2021 
  2   3  87   8   0| 260k  364k|   0     0 |   0     0 | 767  1185 
  1   0  94   5   0|   0   180k|   0     0 |   0     0 | 652  1057 
  1   0  99   0   0|   0     0 |   0     0 |   0     0 | 582   962
  ```
  
 ####  To display stats of process using most of the CPU.
 
 ```
 root@Tuttu:~# dstat -c --top-cpu

--total-cpu-usage-- -most-expensive-
usr sys idl wai stl|  cpu process   
  3   3  90   5   0|plymouthd    1.3
  7   2  91   0   0|chrome       3.8
  6   2  92   0   0|chrome       3.2
  5   2  91   1   0|chrome       2.0
  1   1  95   2   0|Xorg         0.2
  1   1  98   0   0|gnome-termina0.5
  2   1  98   0   0|gnome-shell  1.0
  1   0  99   0   0|Xorg         0.5
  1   0  99   0   0|Xorg         0.5
  1   0  98   1   0|Xorg         0.5
  2   2  91   6   0|Xorg         0.5
  1   1  98   0   0|gnome-shell  0.5
  1   0  99   0   0|Xorg         0.5
  2   1  98   0   0|chrome       0.5
  1   0  98   1   0|gnome-shell  0.5
  1   1  98   0   0|Xorg         0.5
  2   0  95   4   0|Xorg         0.5
  1   1  98   0   0|Xorg         0.2
  2   1  97   0   0|gnome-termina0.2
  ```
  
  #### Show process that will be killed by OOM the first
  
  ```
  root@Tuttu:~# dstat -c --top-oom

--total-cpu-usage-- --out-of-memory---
usr sys idl wai stl|    kill score    
  3   3  90   5   0|chrome        886 
  6   3  91   1   0|chrome        886 
  8   3  90   0   0|chrome        886 
  7   3  91   0   0|chrome        886 
  6   3  91   0   0|chrome        886 
  7   2  91   0   0|chrome        886 
  7   2  90   1   0|chrome        886 
  8   2  91   0   0|chrome        886 
  7   3  91   0   0|chrome        886 
  6   4  90   0   0|chrome        886 
  5   3  92   0   0|chrome        886 
  7   1  91   1   0|chrome        886 
  7   1  92   0   0|chrome        886 
  7   2  86   5   0|chrome        886 
  ```
  
  #### To display stats of process using most of the memory
  
  ```
  root@Tuttu:~# dstat -d --top-mem

-dsk/total- --most-expensive-
 read  writ|  memory process 
 921k  291k|chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   0   148k|chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   0  1116k|chrome       236M
   0   208k|chrome       236M
   0     0 |chrome       236M
   0     0 |chrome       236M
   ```
   
   #### To use the time plugin together with cpu, net, disk, system, load, proc and top_cpu plugins, use:
   
   ```
   root@Tuttu:~# dstat -tcndylp --top-cpu

----system---- --total-cpu-usage-- -net/total- -dsk/total- ---system-- ---load-avg--- ---procs--- -most-expensive-
     time     |usr sys idl wai stl| recv  send| read  writ| int   csw | 1m   5m  15m |run blk new|  cpu process   
28-07 11:55:16|  3   3  89   4   0|   0     0 | 848k  282k| 865    16k|1.13 1.05 0.85|  0   0  35|plymouthd    1.1
28-07 11:55:17|  1   1  98   0   0| 132B  188B|   0     0 | 613   953 |1.13 1.05 0.85|  0   0   0|Xorg         0.5
28-07 11:55:18|  1   1  98   0   0|   0     0 |   0     0 | 634  1024 |1.04 1.03 0.85|  0   0   0|Xorg         0.5
28-07 11:55:19|  1   0  99   0   0|  54B   82B|   0     0 | 559   938 |1.04 1.03 0.85|  0   0   0|Xorg         0.5
28-07 11:55:20|  1   0  99   0   0|   0     0 |   0     0 | 526   872 |1.04 1.03 0.85|  0   0   0|Xorg         0.5
28-07 11:55:21|  2   0  96   2   0|   0     0 |   0    44k| 626  1051 |1.04 1.03 0.85|  0   0   0|gnome-shell  0.8
28-07 11:55:22|  1   0  99   0   0|   0     0 |   0     0 | 544   916 |1.04 1.03 0.85|  0   0   0|Xorg         0.5
28-07 11:55:23|  1   2  96   1   0| 330B  470B|   0   184k| 569   924 |1.04 1.03 0.85|  0   0   0|chrome       0.2
28-07 11:55:24|  1   0  99   0   0|   0     0 |   0     0 | 532   904 |0.96 1.02 0.84|  0   0   0|gnome-shell  0.5
28-07 11:55:25|  1   0  99   0   0|   0     0 |   0     0 | 481   858 |0.96 1.02 0.84|  0   0   0|Xorg         0.8
28-07 11:55:26|  1   0  99   0   0|   0     0 |   0   224k| 535   848 |0.96 1.02 0.84|  0   0   0|gnome-termina0.2
28-07 11:55:27|  1   1  98   0   0|  42B    0 |   0     0 | 556   923 |0.96 1.02 0.84|  0   0   0|Xorg         0.5
28-07 11:55:28|  2   1  95   2   0|   0     0 |   0    56k| 595   933 |0.96 1.02 0.84|  0 1.0   0|Xorg         0.5
28-07 11:55:29|  2   0  97   1   0|  66B  188B|   0  4096B| 593   932 |0.96 1.01 0.84|  0   0   0|Xorg         0.5
28-07 11:55:30|  1   0  97   2   0|  66B    0 |   0    76k| 619   977 |0.96 1.01 0.84|  0 1.0   0|Xorg         0.5
28-07 11:55:31|  2   0  93   5   0| 228B  340B|   0   312k| 666   997 |0.96 1.01 0.84|  0 1.0   0|chrome       0.2
28-07 11:55:32|  1   1  89  10   0|   0     0 |   0  4096B| 601   998 |0.96 1.01 0.84|  0   0   0|Xorg         0.5
28-07 11:55:33|  1   1  99   0   0|   0     0 |   0     0 | 465   810 |0.96 1.01 0.84|  0   0   0|Xorg         0.5
28-07 11:55:34|  1   1  97   0   0|   0     0 |   0     0 | 592   930 |0.88 1.00 0.84|  0   0   0|gnome-termina0.2
```

#### To CPU and memory consuming process in a combined format

```
root@Tuttu:~# dstat --top-mem --top-cpu

--most-expensive- -most-expensive-
  memory process |  cpu process   
chrome       235M|plymouthd    1.0
chrome       235M|Xorg         0.8
chrome       235M|gnome-shell  0.2
chrome       235M|Xorg         0.5
chrome       235M|gnome-termina0.2
chrome       235M|Xorg         0.8
chrome       235M|chrome       0.2
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|gnome-shell  0.5
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|gnome-shell  0.2
chrome       235M|Xorg         0.5
chrome       235M|gnome-shell  0.5
chrome       235M|gnome-termina0.5
chrome       235M|kworker/u8:3-0.2
chrome       235M|Xorg         0.5
chrome       235M|Xorg         0.5
chrome       235M|gnome-shell  0.2
chrome       235M|Xorg         0.5
```


   
  
  
