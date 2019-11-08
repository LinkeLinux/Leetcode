## 633. [平方数之和](https://leetcode-cn.com/problems/sum-of-square-numbers/)

### 题目描述
反转一个单链表。

**示例:**
```
示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```
### 代码实现
```c

struct ListNode* reverseList(struct ListNode* head){
    
    if(head ==NULL || head->next==NULL){
        return head;
    }
    
    struct ListNode *newhead =reverseList(head->next);
    head->next->next=head;
    head ->next=NULL;
    
    return newhead;
    
}

struct ListNode* reverseList(struct ListNode* head){
    if (head ==NULL||head ->next==NULL){
        return head;
    }
    struct ListNode *p=head,*q;
    struct ListNode *r=NULL;
    while(p){
        q=p;
        p=p->next;//保存下一节点，在转指针的指向
        q->next=r;
        r =q;
        
    }
    return r;
}

```
