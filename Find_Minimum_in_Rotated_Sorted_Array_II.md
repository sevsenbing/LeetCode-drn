# Find Minimum in Rotated Sorted Array II
## 题目：
Follow up for "Find Minimum in Rotated Sorted Array":
What if duplicates are allowed?

Would this affect the run-time complexity? How and why?
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).

Find the minimum element.

The array may contain duplicates.

## 分析：
找最小数字，sort排序再返回第一个数就可以了。<br>
## 代码1：
```ruby
class Solution {
public:
    int findMin(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[0];
    }
};
```
居然运行时间也才9ms！我不相信这是hard题……
