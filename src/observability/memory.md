# Memory
## Utilization
#### System-wide
1. `free -m`: `Mem`(main memory), `Swap`(virtual memory)
1. `vmstat 1`: `free`(main memory), `swap`(virtual memory)
1. `sar -r`: `%memused`

#### Per-process
* `top`, `htop`: `RES`(resident main memory), `VIRT`(virtual memory)

## Saturation
#### System Wide
1. `vmstat 1`: `si`/`so`
  * si: memory swapped in from disk
  * so: memory swapped out to disk
1. `sar -B`: `pgscank/s` + `pgscand/s`
1. `sar -W`

## Examples
```console
# free -m
              total        used        free      shared  buff/cache   available
Mem:           3955        2467         254          36        1233        1206
Swap:          4093         333        3760

# vmstat -w 1
procs -----------------------memory---------------------- ---swap-- -----io---- -system-- --------cpu--------
 r  b         swpd         free         buff        cache   si   so    bi    bo   in   cs  us  sy  id  wa  st
 0  0       341000       256236       218864      1046972    1    3     8    19   21   12   1   0  99   1   0
 0  0       341000       256188       218864      1046976    0    0     0     0  365  624   0   0 100   0   0
 0  0       341000       256188       218864      1046976    0    0     0     0  354  684   0   0 100   0   0
 0  0       341000       256188       218864      1046976    0    0     0     0  331  602   1   0  99   0   0
 
# sar -r 1 3
04:01:59 AM kbmemfree kbmemused  %memused kbbuffers  kbcached  kbcommit   %commit  kbactive   kbinact   kbdirty
04:02:00 AM    253760   3796928     93.74    218872    955332   7400864     89.78   2265720   1341288        56
04:02:01 AM    253760   3796928     93.74    218872    955332   7400864     89.78   2265720   1341288        56
04:02:02 AM    253760   3796928     93.74    218872    955332   7400864     89.78   2265720   1341288        56
Average:       253760   3796928     93.74    218872    955332   7400864     89.78   2265720   1341288        56
```
