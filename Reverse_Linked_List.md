# Reverse Linked List
## 题目：
Reverse a singly linked list.
## 分析：
这道题就是把一个链表翻转过来，可以使用递归去做。先从第二个结点到最后都翻转过来，再把第一个结点放在最后。<br>
## 代码：
```ruby
Definition for singly-linked list.
struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(NULL) {}
};
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==NULL||head->next==NULL) return head;
        ListNode *ans=reverseList(head->next);
        head->next->next=head;
        head->next=NULL;
        return ans;
    }
};
