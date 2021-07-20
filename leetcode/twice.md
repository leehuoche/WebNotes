###  88

逆向双指针。`tail=max(p1,p2)`注意结束的情况，`p2`可能未完成。

### 134

从头开始跑。如果跑不到起点，则从起点的下一个位置跑。终止条件是起点到达了数组的末尾。

### 15

复杂度为：
$$
O(N^{2}).
$$
因为：双指针情况下，左右指针总共移动N次，因此为`O(N)`. 排序的复杂度为`O(NlogN)`. 所以和为平方。

```c
loop:
	loop:
		//从后往前找一个值，直到三数之和<=0.
```



### 34

left =找到第一个等于target的值。
也就是==target时候做。right=mid-1；


right=找到第一个大于target的值-1；
也就是==target时候做。left=mid+1；
### 179

先排序，再拼接。

排序规则：二者组合，取大者。

### 147

插入排序

```c++
node* new_dum;
new_dum->next=head;

node* pi=head;
node* pj=head->next;
while(pj){
    if(pj->val>=pi->val){
        pi=pi->next;
    }else{
        node* pk=dumy;
        while(pk->next->val <= pj->val){
            pk=pk->next;
        }
        
        node* temp=pj;
        pi->next=pj->next;
        pj=pj->next;
        t->next=pk->next;
        pk->next=t;
    }
    pj=pi->next;
}
```



### 148

归并排序

分治

```c++
//先将两半排序，再将两半合并。

void merge(h1,h2){
    // 合并两个有序链表
}

node* merge_sort(start, end){
    mid;// 用快慢指针找到中点。
    h1=merge_sort(start, mid);
    h2=merge_sort(mid,end);
    merge(h1,h2);
}


```



### 152

动态规划

```c
dp[n] 记作s[0,n]数组的最大连续子数组的和;

fmax[n]=max(num[n],fmax[n-1]*num[n],fmin[n-1]*num[n]);
fmin[n]=min(num[n],fmax[n-1]*num[n],fmin[n-1]*num[n]);
```





### 78

动态规划

```c++
f(n+1)=对于f(n)的所有元素加入num[i];
vector<int> cur(ans[j]);  // 复制ans[j]
```

### 17

动态规划

```c++
f(n+1)=对于f(n)的所有元素加入当前字符串的每个字符;
最后返回指定长度的字符串。
```

### 91

动态规划

```c++
f(n) 记为前n个字符s[0..n]可以组成的解码数.
如果最后一个字符只用了s[n],f(n)=f(n-1);
如果最后一个字符于s[n-1]结成了对子，f[n]=f[n-2];
```



### 48

对角线翻转。+水平翻转

```c
对角线反转：关注下三角
水平反转：关注左半个矩阵即可。
```

