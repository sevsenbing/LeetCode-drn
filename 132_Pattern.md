# 132 Pattern
## 题目：
Given a sequence of n integers a1, a2, ..., an, a 132 pattern is a subsequence ai, aj, ak such that i < j < k and ai < ak < aj. Design an algorithm that takes a list of n numbers as input and checks whether there is a 132 pattern in the list.

Note: n will be less than 15,000.

Example 1:
Input: [1, 2, 3, 4]

Output: False

Explanation: There is no 132 pattern in the sequence.
Example 2:
Input: [3, 1, 4, 2]

Output: True

Explanation: There is a 132 pattern in the sequence: [1, 4, 2].
Example 3:
Input: [-1, 3, 2, 0]

Output: True

Explanation: There are three 132 patterns in the sequence: [-1, 3, 2], [-1, 3, 0] and [-1, 2, 0].

## 分析：
利用栈的特性，找到中间的数。
## 代码：
```ruby
class Solution {
public:
    bool find132pattern(vector<int>& nums) {
        int n=nums.size(),s3=INT_MIN;
        stack<int> s2;            
        for (int i=n-1;i>=0;i--){
            if (nums[i]<s3) return true;
            else while(!s2.empty()&&nums[i]>s2.top()){                
                 s3 = s2.top();
                 s2.pop();
            }
           s2.push(nums[i]);
        }
        return false;
    }
};
