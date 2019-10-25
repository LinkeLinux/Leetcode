## 215. [数组中的第K个最大元素](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)

### 题目描述
在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

**示例:**
```
示例 1:

输入: [3,2,1,5,6,4] 和 k = 2
输出: 5
示例 2:

输入: [3,2,3,1,2,4,5,5,6] 和 k = 4
输出: 4

```
### 代码实现
```c
//快速排序
void Qsort(int *nums,int left,int right){
    if(left >right)
        return ;
    if(left <=right){
        int index =partion(nums,left,right);
        Qsort(nums,left,index-1);
        Qsort(nums,index+1,right);
    }
}
int partion(int *nums,int left,int right){
    int t =nums[left];
    while(left <right){
        while(left <right && t <nums[right]) right--;
        nums[left]=nums[right];
        while(left <right && t>=nums[left]) left++;
        nums[right]=nums[left];
    }
    nums[left] =t;
    return left;
}
int findKthLargest(int* nums, int numsSize, int k){
    Qsort(nums,0,numsSize-1);
    return nums[numsSize -k];
}
```
