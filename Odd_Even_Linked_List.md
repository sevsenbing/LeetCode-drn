# Odd Even Linked List
## 题目：
Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes.

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

Example:

Input: 1->2->3->4->5->NULL
Output: 1->3->5->2->4->NULL
Note:

The relative order inside both the even and odd groups should remain as it was in the input.
The first node is considered odd, the second node even and so on ...
## 分析：
这道题要把偶数和奇数分开，用两个指针来做，一个指向奇数，一个指向偶数。
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
    ListNode* oddEvenList(ListNode* head) {
        if(!head||!head->next) return head;
        ListNode*p=head,*cur=head->next;
        while(cur&&cur->next){
            ListNode*temp=p->next;p->next=cur->next;
            cur->next=cur->next->next;
            p->next->next=temp;
            cur=cur->next;p=p->next;
        }
        return head;
    }
};
