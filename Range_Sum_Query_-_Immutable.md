# Range Sum Query - Immutable
## 题目：
Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.
```
Example:
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```
Note:
You may assume that the array does not change.
There are many calls to sumRange function.
## 分析：
这道题要找出ij之间的数的和，假设ans[i]是0i区间之和，ans[i,j]就是i到j的和了。之间返回就ok。
## 代码：
```ruby
class NumArray {
private:
    vector<int>ans;
public:
    NumArray(vector<int> nums) {
        ans=nums;
        for(int i=1;i<nums.size();i++) ans[i]+=ans[i-1];
    }
    int sumRange(int a,int b){
        return a==0?ans[b]:ans[b]-ans[a-1];
    }

};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(i,j);
 */
