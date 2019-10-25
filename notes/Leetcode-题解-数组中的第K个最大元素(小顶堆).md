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
//堆实现
void swap(int *nums,int i,int k)
{
    int tmp=nums[i];
    nums[i]=nums[k];
    nums[k]=tmp;
}
void heap(int *nums, int index,int len)
{
    int min=index;
    int l =2*index+1;
    int r =2*index+2;
    if(l <len && nums[min] >nums[l]){
        min =l;
    }
    if(r <len && nums[min]>nums[r]){
        min =r;
    }
    if(min !=index){
        swap(nums,min,index);
        heap(nums,min,len);
    }
}
void buildheap(int *nums,int len)
{
    int i;
    for(i=len/2-1;i>=0;i--){
        heap(nums,i,len);
    }
}
int findKthLargest(int* nums, int numsSize, int k){
    int i;
    buildheap(nums,k);
    for(i=k;i<numsSize;i++){
        if(nums[i]>nums[0]){
            swap(nums,0,i);
            heap(nums,0,k);
        }
    }
    return nums[0];
}
```
