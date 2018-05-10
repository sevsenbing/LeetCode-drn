# 3Sum
## 题目：
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note:

The solution set must not contain duplicate triplets.

Example:

Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
## 分析：
排序。前面的两个小数和后面的一个大数相加比较，小于0，前面的数前进。大于0，后面的数往前进。前面的数和后面的数相遇，结束。
## 代码：
```ruby
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums){
        sort(nums.begin(),nums.end());
        int i=0,j=0,k=nums.size()-1,num1=0;
        vector<int> t(3);  
        vector<vector<int> > ans;  
        while(i<k-1){  
            num1=0-nums[i];  
            t[0]=nums[i];  
            for(j=i+1,k=nums.size()-1;j<k;){  
                if(nums[j]+nums[k]==num1){  
                    t[1]=nums[j++];  
                    t[2]=nums[k--];  
                    ans.push_back(t);  
                    while(j<k&&nums[j]==nums[j-1]) j++; 
                    while(j<k&&nums[k]==nums[k+1]) k--;  
                }  
                else if(nums[j]+nums[k]<num1) j++;  
                else k--; 
            }  
            i++;  
            while(i<k-1&&nums[i]==nums[i-1]) i++;  
        }
        return ans;  
    }
};
