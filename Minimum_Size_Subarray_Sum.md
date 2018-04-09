# Minimum Size Subarray Sum
## 题目：
Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.

For example, given the array [2,3,1,2,4,3] and s = 7,
the subarray [4,3] has the minimal length under the problem constraint.

click to show more practice.

Credits:
Special thanks to @Freezen for adding this problem and creating all test cases.
## 分析：
定义指针left和right，记录子数组的左右的边界，让right向右移，<br>
子数组和大于等于给定值或right达到末尾，则最短距离将left右移一位，<br>
sum中减去移去的值，重复，直到right到达末尾，left到达临界，<br>
## 代码：
```ruby
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        if(nums.empty()) return 0;
        int left=0,right=0,sum=0,ans=nums.size()+1;
        while(right<nums.size()){
            while(sum<s&&right<nums.size()) sum+=nums[right++];
            while(sum>=s){
                ans=min(ans,right-left);
                sum-=nums[left++];
            }
        }
        return ans==nums.size()+1?0:ans;
    }
};
