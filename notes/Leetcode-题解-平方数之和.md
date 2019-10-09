## 633. [平方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers/)

### 题目描述
给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c。

**示例:**
```
示例1:

输入: 5
输出: True
解释: 1 * 1 + 2 * 2 = 5
 

示例2:

输入: 3
输出: False
```
### 代码实现
```c

bool judgeSquareSum(int c){
    int i=0;
    double x =sqrt(c);
    int j=(int)x;
    while(i<=j){
        //num =i * i + j * j;
        if ( (c - i*i) == j*j){//使用减法，避免越界。
            return true;
        }else if (j *j > (c - i *i)){
            j--;
        }else {
            i++;
        }
    }
    return false;
}
```
