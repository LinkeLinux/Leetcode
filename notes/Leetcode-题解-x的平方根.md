## 69 [x的平方根](https://leetcode-cn.com/problems/sqrtx/submissions/)

### 题目描述

实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。


**示例:**
```
示例 1:

输入: 4
输出: 2
示例 2:

输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。


```
### 代码实现
```c
int mySqrt(int x){

    if (x ==0||x==1)
    {
        return x;
    }
    int l=1;
    int r =x/2;
    int mid;
    while(l<r){
        mid =l + (r -l)/2;
        if(mid  > x/mid){
            r=mid;
        }else if (mid  < x/mid){     
            l=mid+1;
        }else 
        {
            return mid;
        }
    }
    if(l >x/l)
        return l-1;
    else 
        return l;
    
}
```
