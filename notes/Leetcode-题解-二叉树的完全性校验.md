## [二叉树层次遍历](https://leetcode-cn.com/problems/check-completeness-of-a-binary-tree/)

### 题目描述
给定一个二叉树，确定它是否是一个完全二叉树（参考网络代码）。

**示例:**
```
若设二叉树的深度为 h，除第 h 层外，其它各层 (1～h-1) 的结点数都达到最大个数，第 h 层所有的结点都连续集中在最左边，这就是完全二叉树。（注：第 h 层可能包含 1~ 2h 个节点。）

 

示例 1：
![avatar](./complete-binary-tree-1.png)
<img src="./complete-binary-tree-1.png" style="zoom:70%" />

输入：[1,2,3,4,5,6]
输出：true
解释：最后一层前的每一层都是满的（即，结点值为 {1} 和 {2,3} 的两层），且最后一层中的所有结点（{4,5,6}）都尽可能地向左。
示例 2：
![avatar](./complete-binary-tree-2.png)
<img src="./complete-binary-tree-2.png" style="zoom:70%" />

输入：[1,2,3,4,5,null,7]
输出：false
解释：值为 7 的结点没有尽可能靠向左侧。
 

提示：

树中将会有 1 到 100 个结点。

```
### 代码实现
```c
#define QMAX 200
    
bool isCompleteTree(struct TreeNode* root){
    struct TreeNode *q[QMAX];
    if ( ! root)
        return false;
    int front=-1;
    int rear =-1;
    struct TreeNode *node;
    if( root !=NULL){
        q[++rear]=root;
    }
   while(front <rear){
       node =q[++front];
       if(node !=NULL){
           q[++rear]=node->left;
           q[++rear]=node->right;
       }
       else {
           while(front <rear){
               if(q[++front] !=NULL){
                   return false;
               }
           }
       }
   }
    
    return true;
}
}
```