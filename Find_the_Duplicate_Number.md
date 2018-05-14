# Find the Duplicate Number
## 题目：
Given an array nums containing n + 1 integers where each integer is between 1 and n (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.

Example 1:

Input: [1,3,4,2,2]
Output: 2
Example 2:

Input: [3,1,3,4,2]
Output: 3
## 分析：
排序再遍历。<br>
不过这个肯定是最烂的做法，明天看看有没有什么高级的。<br>
## 代码
```ruby
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int ans=0;
        for(int i=0;i<=nums.size();i++){
            if(nums[i]==nums[i+1]){
                ans=nums[i];
                break;
            
            }
        }
        return ans;
    }
};
