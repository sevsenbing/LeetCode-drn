# Missing Number
## 题目：
Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

Example 1

Input: [3,0,1]
Output: 2
Example 2

Input: [9,6,4,2,3,5,7,0,1]
Output: 8

Note:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?

## 分析：
用sort排序，然后遍历。<br>

##代码：
```ruby
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int i;
        for(i=0;i<nums.size();i++){
            if(nums[i]!=i) break;
        }
        return i;
    }
};
```
