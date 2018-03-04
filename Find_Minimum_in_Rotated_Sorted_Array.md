# Find Minimum in Rotated Sorted Array
## 题目：
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

You may assume no duplicate exists in the array.

## 分析：
作为一个不会c++的人，也就在排序的时候会想到C++，sort排序，直接return nums[0]。

## 代码：
```ruby
class Solution {
public:
    int findMin(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[0];
    }
};
```
