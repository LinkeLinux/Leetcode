## 21. [合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

### 题目描述
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

**示例:**
```
示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```
### 代码实现
```c
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2){

    if (l1==NULL ){
        return l2;
    }else if (l2 ==NULL){
        return l1;
    }
    struct ListNode *head,*tailhead;
    if (l1->val <= l2->val){
        head =l1;
        l1=l1->next;
    }else {
        head=l2;
        l2=l2->next;
    }
    tailhead=head;
    while(l1 && l2){
        if (l1->val <=l2->val){
            tailhead->next=l1;
            l1=l1->next;
        }else {
            tailhead->next=l2;
            l2=l2->next;
        }
        tailhead=tailhead->next;
    }
    if (l1 ==NULL && l2!=NULL){
        tailhead->next=l2;
    }
    else if (l1!=NULL &&l1 !=NULL){
        tailhead->next=l1;
    }
    return head;
    
}
```
