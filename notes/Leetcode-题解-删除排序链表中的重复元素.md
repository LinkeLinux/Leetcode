## 83. [删除排序链表中的重复元素](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)

### 题目描述
给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

**示例:**
```
示例 1:

输入: 1->1->2
输出: 1->2
示例 2:

输入: 1->1->2->3->3
输出: 1->2->3
```
### 代码实现
```c
/*
struct ListNode* deleteDuplicates(struct ListNode* head){

    if (head ==NULL || head->next==NULL){
        return head;
    }
    struct ListNode *p=head;
    struct ListNode *q;
    while(p){
        q=p->next;
        while(q){
            if(p->val ==q->val){
                q=q->next;
            }else {
                break;
            }
        }        
        p->next=q;
        p=q;
        
    }
    return head;
}
*/
struct ListNode* deleteDuplicates(struct ListNode* head){

    if (head ==NULL || head->next==NULL){
        return head;
    }
    head->next = deleteDuplicates(head->next);
    if(head->val ==head->next->val) head=head->next;
    return head;
}
```
