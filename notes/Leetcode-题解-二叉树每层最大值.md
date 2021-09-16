## 4. [接雨水](https://leetcode-cn.com/problems/trapping-rain-water/)

### 题目描述

给定一棵二叉树的根节点 root ，请找出该二叉树中每一层的最大值。
 



**示例:**
```



示例1：

输入: root = [1,3,2,5,3,null,9]
输出: [1,3,9]
解释:
          1
         / \
        3   2
       / \   \  
      5   3   9 
示例2：

输入: root = [1,2,3]
输出: [1,3]
解释:
          1
         / \
        2   3
示例3：

输入: root = [1]
输出: [1]
示例4：

输入: root = [1,null,2]
输出: [1,2]
解释:      
           1 
            \
             2     
示例5：

输入: root = []
输出: []




```

### 解题思路

```
采用队列，并记录每层的个数循环

```
### 代码实现
```go

func largestValues(root *TreeNode) []int {

    if root == nil{
        return []int{}
    }
    
    queue := []*TreeNode{}
    queue = append(queue,root)
    
    res := []int{}
    levelSize := len(queue)
    for len(queue) > 0 {

        size := 0
        max := queue[0].Val    
        for i := 0; i < levelSize ; i++ {
            
            if max < queue[0].Val{
                max = queue[0].Val
            }
            cur := queue[0] // 获取一个节点
            queue = queue[1:] // 去掉当前节点
            if cur.Left != nil{
                queue = append(queue,cur.Left)
                size++
            }
            if cur.Right != nil{
                queue = append(queue,cur.Right)
                size ++
            }
        }
        levelSize = size
        res = append(res,max)
    }
    return res
}

```
