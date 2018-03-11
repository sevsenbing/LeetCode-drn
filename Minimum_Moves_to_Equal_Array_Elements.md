# Minimum Moves to Equal Array Elements
## 题目：
Given a non-empty integer array of size n, find the minimum number of moves required to make all array elements equal, where a move is incrementing n - 1 elements by 1.

Example:

Input:
[1,2,3]

Output:
3

Explanation:
Only three moves are needed (remember each move increments two elements):

[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]

## 分析：
这道题有个规律，就是数字之和减去最小值和数组长度的乘积。<br>
查了别人的代码，学到一个关于C++的新语法：<br>
for(int a:b){    } 意思是：从数组b依次取出元素赋值给整形变量a，循环执行for中语句。<br>

## 代码：
```ruby
class Solution {
public:
    int minMoves(vector<int>& nums) {
        int n=INT_MAX,sum=0,ans=0;
        for(int m:nums){
            n=min(n,m);
            sum+=m;
        }
        return sum-n*nums.size();
    }
};
