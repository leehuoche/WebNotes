


- [258. 各位相加](#258-各位相加)
- [1221. 分割平衡字符串](#1221-分割平衡字符串)
- [1725. 可以形成最大正方形的矩形数目](#1725-可以形成最大正方形的矩形数目)
- [1710. 卡车上的最大单元数](#1710-卡车上的最大单元数)
- [1716.计算力扣银行的钱](#1716计算力扣银行的钱)
- [944. 删列造序](#944-删列造序)
- [1518. 换酒问题](#1518-换酒问题)
- [1046. 最后一块石头的重量](#1046-最后一块石头的重量)
- [860. 柠檬水找零](#860-柠檬水找零)
- [455 分发饼干](#455-分发饼干)
- [392. 判断子序列](#392-判断子序列)

----------------

### 258. 各位相加

循环，判断和是否属于[0,10]

### 1221. 分割平衡字符串

贪心，如果可以分割则分割。` is_right++,is_right-- `

### 1725. 可以形成最大正方形的矩形数目

求出每个矩形的边长最小值，获得maxlen个数。

### 1710. 卡车上的最大单元数

按照能装的最大单元数排序，将单元数由大到小取值。获取总数。

### 1716.计算力扣银行的钱

找规律，直接计算即可。

### 944. 删列造序

贪心，只需要关注当前节点与前置节点即可。

### 1518. 换酒问题

```c++
add=left/numExchange;
left=(left%numExchange+add);
sum+=add;
```

### 1046. 最后一块石头的重量

1. 排序。删除，终止条件为看最前面两个数是否为0，或者增加一个标志，记录当前的数据量。
2. 使用最大堆。如果`a>b`, 则push进入`a-b`. 当队列中元素个数<2时候退出。

### 860. 柠檬水找零

贪心，模拟，找零找最大的面值。

### 455 分发饼干

贪心：排序，大饼干给胃口大的孩子。否则这个孩子得不到饼干。

### 392. 判断子序列

忘记了。待思考



















