#### 每次加入一个员工后调用calculateRunway这个函数，并且记录消耗的gas是多少？

| employee | transaction | execution |
| ---------|-------------| ----------|
| 1        | 22966       |   1694    |
| 2        | 23747       |   2475    |
| 3        | 24528       |   3256    |
| 4        | 25309       |   4037    |
| 5        | 26090       |   4818    |
| 6        | 26871       |   5599    |
| 7        | 27652       |   6380    |
| 8        | 28433       |   7161    |
| 9        | 29214       |   7942    |
| 10       | 29995       |   8723    |


#### Gas变化么？如果有,为什么？
gas一直在增大，每增加一名员工，transaction cost 和 execution cost 都增大781。
因为calculateRunway函数会遍历employees,每增加一名员工，循环就要多跑一次，也就是函数的复杂度会增加一些，即运算量增加，需要消耗的gas当然就多。


#### 如何优化calculateRunway这个函数来减少gas的消耗？

把 totalSalary 定义为一个 storage 变量，每次新增、删除员工和更改员工信息的时候，都立即算出当时的totalSalary的变化。这样就不用再用循环遍历 employees 了。