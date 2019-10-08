## [二叉树所有路径](https://leetcode-cn.com/problems/binary-tree-paths/)

### 题目描述
给定一个二叉树，返回所有从根节点到叶子节点的路径。

说明: 叶子节点是指没有子节点的节点。

**示例:**
```
示例:

输入:

   1
 /   \
2     3
 \
  5

输出: ["1->2->5", "1->3"]

解释: 所有根节点到叶子节点的路径为: 1->2->5, 1->3
```
### 代码实现
```c
void EveryPath(struct TreeNode *root,char **bin_trees,int *path,int depth,int *returnSize)
{
    int i;
    if (root ==NULL)
        return ;
    if (root->left ==NULL && root->right ==NULL){
        path[depth]=root->val;
        bin_trees[*returnSize] =(char *)calloc(1,sizeof(char *) *100);
        for(i=0;i<depth ;i++)
        {
            sprintf(bin_trees[*returnSize],"%s%d->",bin_trees[*returnSize],path[i]);
        }
        sprintf(bin_trees[*returnSize],"%s%d",bin_trees[*returnSize],path[i]);
        *returnSize+=1;
    }else{
        path[depth++]=root->val;//节点开始回溯时，这里依然保存着原先的值
        EveryPath(root->left,bin_trees,path,depth,returnSize);
        EveryPath(root->right,bin_trees,path,depth,returnSize);
    }
}
char ** binaryTreePaths(struct TreeNode* root, int* returnSize){  
    *returnSize =0;
    int path[100]={0};
    char **bin_trees =(char **)malloc(sizeof(char *) *100);
    if (root==NULL)
        return NULL;
    EveryPath(root,bin_trees,path,0,returnSize);
    return bin_trees;
}
```