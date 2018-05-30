# Find All Numbers Disappeared in an Array
***
## 题目：
Given an array of integers where 1 ≤ a[i] ≤ n (n = size of array), some elements appear twice and others appear once.

Find all the elements of [1, n] inclusive that do not appear in this array.

Could you do it without extra space and in O(n) runtime? You may assume the returned list does not count as extra space.

Example:

Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
## 分析：
这道题让找出数组中缺的元素，利用数组的角标当成计数器。把数组中出现的数反馈到元素位置上，因此若出现i，那么第i个数就成为负的。<br>
## 代码：
```C++
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int> ans;
        for(int i=0;i<nums.size();i++){
            int m=abs(nums[i])-1;
            nums[m]=nums[m]>0?-nums[m]:nums[m];
        }
        for(int i=0;i<nums.size();i++){
            if(nums[i]>0) ans.push_back(i+1);
        }
        return ans;
    }
};
