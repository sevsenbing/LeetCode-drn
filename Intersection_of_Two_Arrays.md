# Intersection of Two Arrays
## 题目：
```
Given two arrays, write a function to compute their intersection.

Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

Note:
Each element in the result must be unique.
The result can be in any order.
```
## 分析：
可以利用set，用一个数找另一个，若存在，则转换类型输出。
## 代码：
```C++
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        set<int>s(nums1.begin(),nums1.end()),ans;
        for(auto a : nums2) if(s.count(a)) ans.insert(a);
        return vector<int>(ans.begin(),ans.end());
    }
};
