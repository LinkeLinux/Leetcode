## 153. [寻找旋转排序数组中的最小值](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)

### 题目描述
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

请找出其中最小的元素。

你可以假设数组中不存在重复元素。


**示例:**
```
示例 1:

输入: [3,4,5,1,2]
输出: 1
示例 2:

输入: [4,5,6,7,0,1,2]
输出: 0
```
### 代码实现
```c

int findMin(int* nums, int numsSize){
    int l =0;
    int r =numsSize-1;
    int mid ;
    while(l <r){
        mid =l +(r -l)/2;
        if (nums[mid] <nums[r]){ //升序排列，最右边的值为最大值，与最大值比，小于最大值，则最大值在中间值得左边。
            r= mid;
        }else{
           l =mid +1;
        }
        
    }
    return nums[l];

}
```
