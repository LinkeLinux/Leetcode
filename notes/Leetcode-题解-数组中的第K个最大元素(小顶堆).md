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


### 实现思路
```
构造前 k 个最大元素小顶堆，取堆顶
我们也可以通过构造一个前 k 个最大元素小顶堆来解决，小顶堆上的任意节点值都必须小于等于其左右子节点值，即堆顶是最小值。

所以我们可以从数组中取出 k 个元素构造一个小顶堆，然后将其余元素与小顶堆对比，如果大于堆顶则替换堆顶，然后堆化，所有元素遍历完成后，堆中的堆顶即为第 k 个最大值

具体步骤如下：

从数组中取前 k 个数（ 0 到 k-1 位），构造一个小顶堆
从 k 位开始遍历数组，每一个数据都和小顶堆的堆顶元素进行比较，如果小于堆顶元素，则不做任何处理，继续遍历下一元素；如果大于堆顶元素，则将这个元素替换掉堆顶元素，然后再堆化成一个小顶堆。
遍历完成后，堆顶的数据就是第 K 大的数据


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
