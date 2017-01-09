# Storage
## Utilization
### System Wide
1. `iostat -xz 1`當中的`%util`欄位，
  * -x: extended statistics
  * -z: 沒有IO變化的storage不顯示
1. `sar -d`當中的`%util`欄位
  * -d: disk, block device

## Saturation
### System Wide
* `iostat -xz 1`當中的`avgqu-sz`欄位 > 1
  * avgrq-sz: average request size
  * avgqu-sz: average queue size
* `sar -d`，條件同上

## Examples
在對硬碟執行dd的時候，可以發現utilization很高、saturation也很高
```console
# iostat -xz -m 1
Device:  rrqm/s   wrqm/s     r/s     w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sdh       21.00 24269.00    3.00  195.00     0.09    95.56   989.37    10.84   54.77   45.67   54.91   4.38  86.80
sdi        0.00 24262.00    0.00  174.00     0.00    86.00  1012.23    18.01   90.05    0.00   90.05   5.33  92.70
sdj        7.00 24255.00    1.00  194.00     0.03    95.50  1003.32    14.44   74.03   77.00   74.01   4.48  87.40
sdk       17.00 24265.00    2.00  195.00     0.07    95.54   994.03    12.31   62.47   76.00   62.33   4.48  88.30
sdl        7.00 24255.00    1.00  194.00     0.03    95.50  1003.32    14.37   73.70   67.00   73.73   4.57  89.20
sdm        7.00 24262.00    1.00  195.00     0.03    95.53   998.53    12.34   62.96   86.00   62.85   4.25  83.30
sdn       31.00 24286.00    3.00  197.00     0.13    95.63   980.64    13.05   65.25   92.33   64.84   4.47  89.50
```
