## 167. [两数之和II-输入有序数组](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/)

### 题目描述
给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。

说明:

返回的下标值（index1 和 index2）不是从零开始的。
你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。

**示例:**
```
示例:

输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。

```
### 代码实现
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* numbers, int numbersSize, int target, int* returnSize){
    *returnSize=0;
    if (numbers==NULL){
        return NULL;
    }
    int *ret=NULL;
    int start=0;
    int end=numbersSize-1;
    while(start<end){
        if (target - numbers[start]==numbers[end])
        {
            ret=(int *)malloc(2 *sizeof(int));
            *returnSize =2;
            ret[0]=start+1;
            ret[1]=end+1;
            break;
        }else if (target -numbers[start] >numbers[end]){
            start++;
        }else{
           end--;
        }
    }
    return ret;
}


```
