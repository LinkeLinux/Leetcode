## 848. [字母移位](https://leetcode-cn.com/problems/shifting-letters/)

### 题目描述
有一个由小写字母组成的字符串 S，和一个整数数组 shifts。

我们将字母表中的下一个字母称为原字母的 移位（由于字母表是环绕的， 'z' 将会变成 'a'）。

例如·，shift('a') = 'b'， shift('t') = 'u',， 以及 shift('z') = 'a'。

对于每个 shifts[i] = x ， 我们会将 S 中的前 i+1 个字母移位 x 次。

返回将所有这些移位都应用到 S 后最终得到的字符串。




**示例:**
```
示例 1:

输入：S = "abc", shifts = [3,5,9]
输出："rpl"
解释： 
我们以 "abc" 开始。
将 S 中的第 1 个字母移位 3 次后，我们得到 "dbc"。
再将 S 中的前 2 个字母移位 5 次后，我们得到 "igc"。
最后将 S 中的这 3 个字母移位 9 次后，我们得到答案 "rpl"。


```
### 代码实现
```c

int* searchRange(int* nums, int numsSize, int target, int* returnSize){
    
    int *res =(int *)malloc(2*sizeof(int));
    res[0]=res[1]=-1;
    *returnSize =2;
    if (nums ==NULL || numsSize ==0){
        return res;
    }
    int l =0;
    int mid;
    int r =numsSize-1;
    while(l<r){
        mid =l + ((r-l)>>1);
        if(nums[mid]>=target) r =mid;
        else 
            l=mid+1;
    }
    if(target !=nums[l]) 
        return res;
    else 
        res[0]=l;
    r=numsSize;//防止可能越界
    while(l <r){
        mid =l + (r-l)/2;
        if(nums[mid]<=target) 
            l =mid+1;
        else 
            r =mid ;
    }
    
        res[1]=l-1;
    return res;
        
}
```
