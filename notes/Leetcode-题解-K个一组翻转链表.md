## 25. [K个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

### 题目描述
给你一个链表，每 k 个节点一组进行翻转，请你返回翻转后的链表。

k 是一个正整数，它的值小于或等于链表的长度。

如果节点总数不是 k 的整数倍，那么请将最后剩余的节点保持原有顺序。



**示例:**
```
给定这个链表：1->2->3->4->5

当 k = 2 时，应当返回: 2->1->4->3->5

当 k = 3 时，应当返回: 3->2->1->4->5


```
### 代码实现
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode *reverseNode(struct ListNode *head){
    if (head ==NULL ||head->next==NULL)
        return head;
    struct ListNode *new=reverseNode(head->next);
    head->next->next=head;
    return new;
    
}
struct ListNode* reverseKGroup(struct ListNode* head, int k){
    struct ListNode *tmp;
    tmp =head;
    int i;
    for(i=1;i<k &&tmp!=NULL;i++){
        tmp =tmp->next;
    }
    if(tmp ==NULL){
        return head;
    }
    struct ListNode *t2=tmp->next;
    tmp->next=NULL;
    struct ListNode *newhead =reverseNode(head);
    
    struct ListNode *newtmp =reverseKGroup(t2,k);
    
    head->next=newtmp;
    return newhead;
    

}
```
