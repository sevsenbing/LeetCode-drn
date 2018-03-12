# Minimum Moves to Equal Array Elements II-drn

## 题目：

Given a non-empty integer array, find the minimum number of moves required to make all array elements equal, where a move is incrementing a selected element by 1 or decrementing a selected element by 1.

You may assume the array's length is at most 10,000.

Example:

Input:
[1,2,3]

Output:
2

Explanation:
Only two moves are needed (remember each move increments or decrements one element):

[1,2,3]  =>  [2,2,3]  =>  [2,2,2]

## 分析：

这道题中只要算出数组中每个数组与最中间的数字的差累加就可以了。<br>
但我竟忘了abs函数，用的三目运算符……<br>

## 代码：
```ruby
class Solution {
public:
    int minMoves2(vector<int>& nums) {
        int l=nums.size()/2,ans=0;
        sort(nums.begin(),nums.end());
        for(int i=0;i<l;++i) ans+=(((nums[i]-nums[l])>0)?(nums[i]-nums[l]):(nums[l]-nums[i]));
        return ans;
    }
};
