# Kth Largest Element in an Array
## 问题：
Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.
For example,
Given [3,2,1,5,6,4] and k = 2, return 5.
Note: 
You may assume k is always valid, 1 ≤ k ≤ array's length.
Credits:
Special thanks to @mithmatt for adding this problem and creating all test cases.
## 分析：
这道题用sort函数排序之后直接返回就可以了。</br>
## 代码：
```rube
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()-k];
    }
};
