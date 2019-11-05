## 34. [在排序数组中查找元素的第一个和最后一个位置](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### 题目描述
给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。

你的算法时间复杂度必须是 O(log n) 级别。

如果数组中不存在目标值，返回 [-1, -1]。



**示例:**
```
示例 1:

输入: nums = [5,7,7,8,8,10], target = 8
输出: [3,4]
示例 2:

输入: nums = [5,7,7,8,8,10], target = 6
输出: [-1,-1]

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
