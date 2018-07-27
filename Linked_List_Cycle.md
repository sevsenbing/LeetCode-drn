# Linked List Cycle
## 题目
```
Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?
```
## 分析：
两个指针的扣圈问题，运用指针，因为是个圈。
## 代码：
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode *slow=head,*fast=head;
        while(fast&&fast->next){
            slow=slow->next;
            fast=fast->next->next;
            if(slow==fast) return true;
        }
        return false;
    }
};
