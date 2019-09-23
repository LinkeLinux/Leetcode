二叉树的层次遍历
给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]
#define QMAX 1000// 定义太小有些测试用例过不去
typedef struct Queue{
    
    struct TreeNode *Node[QMAX];// 丢列保存树的节点指针。
    int front;
    int rear;
}Queue;
void Qinit(Queue *q)
{
    q->front = q->rear =0;
 
}
void push(Queue *q,struct TreeNode *node)
{
    if ((q->rear +1)%QMAX==QMAX){
        q->rear =0;
    }
    q->Node[q->rear] =node;
    q->rear =(q->rear+1)%QMAX;
}
struct TreeNode *pop(Queue *q)
{
    struct TreeNode *node;
    node =q->Node[q->front];
    q->front =(q->front +1)%QMAX;
    return node;
}
int len(Queue q)
{
    if (q.rear  >=q.front)
        return q.rear -q.front;
    return q.rear +QMAX - q.front -1;
}
int** levelOrder(struct TreeNode* root, int* returnSize, int** returnColumnSizes)
{
    *returnSize =0;
    if (root ==NULL){
        return NULL;
    }
    int i;
    Queue queue;
    Qinit(&queue);//使用封装的环形队列。
    int *level =(int *)calloc(1,sizeof(int)*QMAX);//每一层节点的个数。
    push(&queue,root);
    int height=0;
    level[height]=1;
    int **bin_paths =(int **)malloc(sizeof(int *)*QMAX);//1000 level.
    while (len(queue) >0) 
    {   
        height ++; 
        bin_paths[height-1] =(int *)malloc(sizeof(int *) * level[height-1]);//每一层的元素。
        for (i=0;i<level[height-1]; i++)
        {   
            root =pop(&queue);
            bin_paths[height-1][i] =root->val;
 
            if (root->left !=NULL){
                push(&queue,root->left);
                level[height]++;
            }
            if (root ->right !=NULL){
                push(&queue,root->right);
                level[height]++;
            }
        }
    }
    *returnColumnSizes =level;//每一列的节点数。
    *returnSize =height;//返回层数。
    //遍历的时候类似于
    //for(i=0;i<returnSize;i++){
    //    for (j=0;j<returnColumnSizes[i];j++){
    //        printf(Order[i][j]);
     //   }
    }
 
    return bin_paths;
}