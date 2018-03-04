# Single Number II
## 题目：
Given an array of integers, every element appears three times except for one, which appears exactly once. Find that single one.

Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## 分析：
先排序，再遍历。遍历的时候如果哪个数和前后都不相等，就说明是这个了。<br>
唯一需要注意的问题就是边缘的数，第一个和最后一个。<br>

## 代码：
```ruby
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        if(nums[0]!=nums[1]) return nums[0];
        if(nums[nums.size()-1]!=nums[nums.size()-2]) return nums[nums.size()-1];
        for(int i = 1;i<nums.size()-1; i ++){
            if(nums[i] != nums[i-1] && nums[i] != nums[i+1]) return nums[i];
        }
    }
};
```
