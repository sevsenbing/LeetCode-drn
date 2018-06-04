# Jump Game
***
## 题目：
Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.
```
Example 1:

Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: [3,2,1,0,4]
Output: false
```
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
## 分析：
这道题只是题意比较难于理解，只要明白题在说什么，就不难做出。这道题的意思是，每一个元素都代表步数，从最开始的往后走，看看能否走到最后。<br>
## 代码：
```ruby
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int a=nums[0];
        if(!nums.size()) return false;
        for(int i=1;i!=nums.size();i++){
            if(a<i) return false;
            a=max(a,nums[i]+i);
            if(a>=nums.size()-1) return true;
        }
        return a>=nums.size()-1;
    }
};
